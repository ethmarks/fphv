<script>
    import { sha256 } from "./lib/sha256";

    const MIN_MATCH_LENGTH = 4;

    let input = "";
    let output = "";

    function findMatch(hash, text) {
        // Start with longest possible prefix and work down
        for (let len = hash.length; len >= MIN_MATCH_LENGTH; len--) {
            const prefix = hash.substring(0, len);
            if (text.toLowerCase().includes(prefix)) {
                return prefix;
            }
        }
        return "";
    }

    async function handleInput() {
        if (input.trim() === "") {
            output = "";
            return;
        }

        const hash = await sha256(input);
        const match = findMatch(hash, input);

        if (match !== "") {
            output = hash + "\n" + match + " ✔";
        } else {
            output = hash;
        }
    }
</script>

<main>
    <h1>Verify Fixed-Point Hash String</h1>
    <div id="textareas">
        <label for="input">String</label>
        <textarea
            id="input"
            bind:value={input}
            on:input={handleInput}
            placeholder="The SHA-256 hash of this sentence begins with b43c8b9."
        ></textarea>
        <label for="output">SHA-256 Hash</label>
        <textarea
            id="output"
            bind:value={output}
            disabled
            placeholder="b43c8b96f151033a566e148d45c43aa84ba153ff9407397f23d5eb43112bb5e1"
        ></textarea>
    </div>
</main>

<style>
    #textareas {
        display: flex;
        flex-direction: column;
    }
</style>
