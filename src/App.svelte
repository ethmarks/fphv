<main>
    <h1>Verify Fixed-Point Hash String</h1>
    <div id="textareas">
        <label for="input">String</label>
        <textarea
            id="input"
            placeholder="The SHA-256 hash of this sentence begins with b43c8b9."
        ></textarea>
        <label for="output">SHA-256 Hash</label>
        <textarea
            id="output"
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
