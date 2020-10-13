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
# <a name="serialization-breaking-changes"></a><span data-ttu-id="60e04-103">Son değişiklikleri serileştirme</span><span class="sxs-lookup"><span data-stu-id="60e04-103">Serialization breaking changes</span></span>

<span data-ttu-id="60e04-104">Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="60e04-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="60e04-105">Son değişiklik</span><span class="sxs-lookup"><span data-stu-id="60e04-105">Breaking change</span></span> | <span data-ttu-id="60e04-106">Tanıtılan sürüm</span><span class="sxs-lookup"><span data-stu-id="60e04-106">Introduced version</span></span> |
| - | - |
| [<span data-ttu-id="60e04-107">Seri durumdan çıkarma için ortak olmayan, parametresiz oluşturucular kullanılmıyor</span><span class="sxs-lookup"><span data-stu-id="60e04-107">Non-public, parameterless constructors not used for deserialization</span></span>](#non-public-parameterless-constructors-not-used-for-deserialization) | <span data-ttu-id="60e04-108">5.0</span><span class="sxs-lookup"><span data-stu-id="60e04-108">5.0</span></span> |
| [<span data-ttu-id="60e04-109">JsonSerializer. Serialize, tür parametresi null olduğunda ArgumentNullException oluşturur</span><span class="sxs-lookup"><span data-stu-id="60e04-109">JsonSerializer.Serialize throws ArgumentNullException when type parameter is null</span></span>](#jsonserializerserialize-throws-argumentnullexception-when-type-parameter-is-null) | <span data-ttu-id="60e04-110">5.0</span><span class="sxs-lookup"><span data-stu-id="60e04-110">5.0</span></span> |
| [<span data-ttu-id="60e04-111">JsonSerializer. serisini kaldırma tek karakterlik dize gerektirir</span><span class="sxs-lookup"><span data-stu-id="60e04-111">JsonSerializer.Deserialize requires single-character string</span></span>](#jsonserializerdeserialize-requires-single-character-string) | <span data-ttu-id="60e04-112">5.0</span><span class="sxs-lookup"><span data-stu-id="60e04-112">5.0</span></span> |
| [<span data-ttu-id="60e04-113">BinaryFormatter. serisini kaldırma, SerializationException içindeki bazı özel durumları yeniden kaydırır</span><span class="sxs-lookup"><span data-stu-id="60e04-113">BinaryFormatter.Deserialize rewraps some exceptions in SerializationException</span></span>](#binaryformatterdeserialize-rewraps-some-exceptions-in-serializationexception) | <span data-ttu-id="60e04-114">5.0</span><span class="sxs-lookup"><span data-stu-id="60e04-114">5.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="60e04-115">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="60e04-115">.NET 5.0</span></span>

[!INCLUDE [non-public-parameterless-constructors-not-used-for-deserialization](../../../includes/core-changes/serialization/5.0/non-public-parameterless-constructors-not-used-for-deserialization.md)]

***

[!INCLUDE [jsonserializer-serialize-throws-argumentnullexception-for-null-type](../../../includes/core-changes/serialization/5.0/jsonserializer-serialize-throws-argumentnullexception-for-null-type.md)]

***

[!INCLUDE [deserializing-json-into-char-requires-single-character](../../../includes/core-changes/serialization/5.0/deserializing-json-into-char-requires-single-character.md)]

***

[!INCLUDE [binaryformatter-deserialize-rewraps-exceptions](../../../includes/core-changes/serialization/5.0/binaryformatter-deserialize-rewraps-exceptions.md)]

***
