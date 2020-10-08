---
title: Son değişiklikleri serileştirme
description: .NET Core ve .NET 5,0 ve sonraki sürümlerde serileştirme kategorisindeki son değişiklikleri listeler.
ms.date: 07/30/2020
ms.openlocfilehash: d68bb95f4ee2b21a5a5bf002a46a3904543cd4a7
ms.sourcegitcommit: a6bd4cad438fe479cbd112eae10f2cd449f06e40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/08/2020
ms.locfileid: "91844517"
---
# <a name="serialization-breaking-changes"></a>Son değişiklikleri serileştirme

Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:

| Son değişiklik | Tanıtılan sürüm |
| - | - |
| [JsonSerializer. serisini kaldırma tek karakterlik dize gerektirir](#jsonserializerdeserialize-requires-single-character-string) | 5.0 |
| [BinaryFormatter. serisini kaldırma, SerializationException içindeki bazı özel durumları yeniden kaydırır](#binaryformatterdeserialize-rewraps-some-exceptions-in-serializationexception) | 5.0 |

## <a name="net-50"></a>.NET 5,0

[!INCLUDE [deserializing-json-into-char-requires-single-character](../../../includes/core-changes/serialization/5.0/deserializing-json-into-char-requires-single-character.md)]

***

[!INCLUDE [binaryformatter-deserialize-rewraps-exceptions](../../../includes/core-changes/serialization/5.0/binaryformatter-deserialize-rewraps-exceptions.md)]

***
