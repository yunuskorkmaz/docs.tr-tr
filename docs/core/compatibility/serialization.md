---
title: Son değişiklikleri serileştirme
description: .NET Core ve .NET 5,0 ve sonraki sürümlerde serileştirme kategorisindeki son değişiklikleri listeler.
ms.date: 07/30/2020
ms.openlocfilehash: 65006e6fb45ed2d54699c9972e0489e3ac5ac8bc
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2020
ms.locfileid: "91955348"
---
# <a name="serialization-breaking-changes"></a>Son değişiklikleri serileştirme

Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:

| Son değişiklik | Tanıtılan sürüm |
| - | - |
| [JsonSerializer. Serialize, tür parametresi null olduğunda ArgumentNullException oluşturur](#jsonserializerserialize-throws-argumentnullexception-when-type-parameter-is-null) | 5.0 |
| [JsonSerializer. serisini kaldırma tek karakterlik dize gerektirir](#jsonserializerdeserialize-requires-single-character-string) | 5.0 |
| [BinaryFormatter. serisini kaldırma, SerializationException içindeki bazı özel durumları yeniden kaydırır](#binaryformatterdeserialize-rewraps-some-exceptions-in-serializationexception) | 5.0 |

## <a name="net-50"></a>.NET 5,0

[!INCLUDE [jsonserializer-serialize-throws-argumentnullexception-for-null-type](../../../includes/core-changes/serialization/5.0/jsonserializer-serialize-throws-argumentnullexception-for-null-type.md)]

***

[!INCLUDE [deserializing-json-into-char-requires-single-character](../../../includes/core-changes/serialization/5.0/deserializing-json-into-char-requires-single-character.md)]

***

[!INCLUDE [binaryformatter-deserialize-rewraps-exceptions](../../../includes/core-changes/serialization/5.0/binaryformatter-deserialize-rewraps-exceptions.md)]

***
