# headshots-inbox

Drop box for speaker headshots made with the hidden `/headshots/` tool on sreday.com, llmday.com, platformday.com and
promptengineering.rocks. The tool's "Push to site" button commits finished PNGs here, into the folder of its site:

    sreday/       -> sreday/sreday                                         speakers/
    llmday/       -> sreday/llmday                                         speakers/
    platformday/  -> sreday/platformday                                    speakers/
    pec/          -> Prompt-Engineering-Conference/2026.promptengineering.rocks  speakers/

Every site repo runs `.github/workflows/import-headshots.yml` every 15 minutes: it takes the files added or changed here
since its last import, accepts only valid 1000x1000 RGBA PNGs with a safe name (anything else is skipped and logged),
copies them to its `speakers/` folder, commits and starts its build.

Why a separate repo: the token pasted into the tool only has access to this repo, so even a leaked token can at most
add images here; it can never change a site's pages, forms, data, settings or workflows.
