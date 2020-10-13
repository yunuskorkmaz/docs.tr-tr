---
title: Son değişiklikleri serileştirme
description: .NET Core ve .NET 5,0 ve sonraki sürümlerde serileştirme kategorisindeki son değişiklikleri listeler.
ms.date: 07/30/2020
ms.openlocfilehash: 6902ef8eb2dc23610ef532ff57b755456648ffb0
ms.sourcegitcommit: e078b7540a8293ca1b604c9c0da1ff1506f0170b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2020
ms.locfileid: "91997727"
---
# <a name="serialization-breaking-changes"></a>Son değişiklikleri serileştirme

Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:

| Son değişiklik | Tanıtılan sürüm |
| - | - |
| [Seri durumdan çıkarma için ortak olmayan, parametresiz oluşturucular kullanılmıyor](#non-public-parameterless-constructors-not-used-for-deserialization) | 5.0 |
| [JsonSerializer. Serialize, tür parametresi null olduğunda ArgumentNullException oluşturur](#jsonserializerserialize-throws-argumentnullexception-when-type-parameter-is-null) | 5.0 |
| [JsonSerializer. serisini kaldırma tek karakterlik dize gerektirir](#jsonserializerdeserialize-requires-single-character-string) | 5.0 |
| [BinaryFormatter. serisini kaldırma, SerializationException içindeki bazı özel durumları yeniden kaydırır](#binaryformatterdeserialize-rewraps-some-exceptions-in-serializationexception) | 5.0 |

## <a name="net-50"></a>.NET 5,0

[!INCLUDE [non-public-parameterless-constructors-not-used-for-deserialization](../../../includes/core-changes/serialization/5.0/non-public-parameterless-constructors-not-used-for-deserialization.md)]

***

[!INCLUDE [jsonserializer-serialize-throws-argumentnullexception-for-null-type](../../../includes/core-changes/serialization/5.0/jsonserializer-serialize-throws-argumentnullexception-for-null-type.md)]

***

[!INCLUDE [deserializing-json-into-char-requires-single-character](../../../includes/core-changes/serialization/5.0/deserializing-json-into-char-requires-single-character.md)]

***

[!INCLUDE [binaryformatter-deserialize-rewraps-exceptions](../../../includes/core-changes/serialization/5.0/binaryformatter-deserialize-rewraps-exceptions.md)]

***
