---
name: abap-vscode-pce
description: ADT VSCode guidance for agents working on ABAP code and Repository Objects in VS Code with the virtual ABAP workspace folder, where uri starts with abap:/ For S/4HANA Private Cloud Edition (PCE).
license: MIT
---

# ABAP VSCode PCE

This skill applies to agents working on ABAP source in Visual Studio Code when the workspace folders use the virtual ABAP filesystem (URIs that start with `abap:/`).

## General

- Use cloud-compliant ABAP syntax and public cloud APIs when possible. When not possible, add a comment at the place of call: "TO-DO: non-cloud-compliant API, refactor when cloud-compliant APIs become available"
- The package `$tmp` is used for local development; no transports are required for such work.
- Use the `com.sap.adt/mcp` MCP server for creating new ABAP development objects when available.
- You MUST adjust the file search because the ABAP VSCode extension uses the virtual file system as a workspace folder. Always search via the directory first!
- Always add and edit source code via the VS Code editor. If needed open the editor first via the provided file paths.

## Testing instructions

- Run available unit tests after changing source code or adding new tests.
- When asked to add unit tests, you MUST add them to the testclass include file, which is a dedicated file whose filename ends with `.testclasses.abap`.

## Notes

- Treat `abap:/` URIs as the authoritative source for file locations in the workspace.
- Prefer lightweight, surgical edits and keep changes scoped to the minimum necessary files and includes.

## VS Code detection and usage example


- Always open files by `abap:/` URI using `vscode.workspace.openTextDocument` and `vscode.window.showTextDocument` before making edits. Use `vscode.WorkspaceEdit` to apply changes so the ABAP extension handles sync/activation.

