# ai-sdk

## docs
- https://ai-sdk.dev/docs



## Reference

<details><summary>Click to expand..</summary>

# `embedMany`



# 🧠 `embedMany()` – Mehrere Werte einbetten

Funktion zum gleichzeitigen Einbetten mehrerer Werte über ein Embedding-Modell.

> **Auto-Splitting**: Große Mengen werden automatisch in kleinere Chunks aufgeteilt, falls das Modell eine Begrenzung pro Call hat.

---

## ✅ Beispiel

```ts
import { openai } from '@ai-sdk/openai';
import { embedMany } from 'ai';

const { embeddings } = await embedMany({
  model: openai.embedding('text-embedding-3-small'),
  values: [
    'sunny day at the beach',
    'rainy afternoon in the city',
    'snowy night in the mountains',
  ],
});
```

---

## 📦 Import

```ts
import { embedMany } from "ai";
```

---

## 🧾 API-Signatur

```ts
embedMany({
  model: EmbeddingModel,
  values: Array<VALUE>,
  maxRetries?: number,
  abortSignal?: AbortSignal,
  headers?: Record<string, string>,
  experimental_telemetry?: TelemetrySettings
}): Promise<{
  values: Array<VALUE>,
  embeddings: number[][],
  usage: EmbeddingTokenUsage
}>
```

---

## 📥 Parameter

| Name                             | Typ                      | Beschreibung                                                        |
| -------------------------------- | ------------------------ | ------------------------------------------------------------------- |
| `model`                          | `EmbeddingModel`         | Das zu verwendende Embedding-Modell (z. B. `openai.embedding(...)`) |
| `values`                         | `Array<VALUE>`           | Werte, die eingebettet werden sollen (Typ modellabhängig)           |
| `maxRetries` *(opt)*             | `number`                 | Max. Anzahl an automatischen Retries (Default: `2`)                 |
| `abortSignal` *(opt)*            | `AbortSignal`            | Ermöglicht das Abbrechen des Requests                               |
| `headers` *(opt)*                | `Record<string, string>` | Zusätzliche HTTP-Header (nur für HTTP-Provider relevant)            |
| `experimental_telemetry` *(opt)* | `TelemetrySettings`      | Experimentelle Telemetrie-Konfiguration                             |

---

## 📊 `TelemetrySettings` (experimentell)

| Name            | Typ           | Beschreibung                                        |
| --------------- | ------------- | --------------------------------------------------- |
| `isEnabled`     | `boolean`     | Aktiviert/Deaktiviert Telemetrie (Default: `false`) |
| `recordInputs`  | `boolean`     | Speichert Eingaben (Default: `true`)                |
| `recordOutputs` | `boolean`     | Speichert Ausgaben (Default: `true`)                |
| `functionId`    | `string`      | Funktions-ID zur Gruppierung                        |
| `metadata`      | `Record<...>` | Zusätzliche Telemetrie-Metadaten                    |

---

## 📤 Rückgabewert

```ts
{
  values: Array<VALUE>,
  embeddings: number[][],
  usage: {
    tokens: number
  }
}
```

| Feld         | Typ                   | Beschreibung                                    |
| ------------ | --------------------- | ----------------------------------------------- |
| `values`     | `Array<VALUE>`        | Originalwerte                                   |
| `embeddings` | `number[][]`          | Embeddings im gleichen Reihenfolge wie `values` |
| `usage`      | `EmbeddingTokenUsage` | Tokenverbrauch für die Anfrage                  |


</details>

