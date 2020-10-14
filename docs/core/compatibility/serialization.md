---
title: Son değişiklikleri serileştirme
description: .NET Core ve .NET 5,0 ve sonraki sürümlerde serileştirme kategorisindeki son değişiklikleri listeler.
ms.date: 07/30/2020
ms.openlocfilehash: bb6bd650afeba426edc6e102076f05f97f8e0598
ms.sourcegitcommit: 39b1d5f2978be15409c189a66ab30781d9082cd8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/14/2020
ms.locfileid: "92050486"
---
# <a name="serialization-breaking-changes"></a><span data-ttu-id="8ee19-103">Son değişiklikleri serileştirme</span><span class="sxs-lookup"><span data-stu-id="8ee19-103">Serialization breaking changes</span></span>

<span data-ttu-id="8ee19-104">Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="8ee19-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="8ee19-105">Son değişiklik</span><span class="sxs-lookup"><span data-stu-id="8ee19-105">Breaking change</span></span> | <span data-ttu-id="8ee19-106">Tanıtılan sürüm</span><span class="sxs-lookup"><span data-stu-id="8ee19-106">Introduced version</span></span> |
| - | - |
| [<span data-ttu-id="8ee19-107">Anahtar-değer çiftlerini serileştirmek ve seri durumdan çıkarılırken PropertyNamingPolicy, Propertynamecaseduyarsız ve kodlayıcı seçenekleri kabul edilir</span><span class="sxs-lookup"><span data-stu-id="8ee19-107">PropertyNamingPolicy, PropertyNameCaseInsensitive, and Encoder options are honored when serializing and deserializing key-value pairs</span></span>](#propertynamingpolicy-propertynamecaseinsensitive-and-encoder-options-are-honored-when-serializing-and-deserializing-key-value-pairs) | <span data-ttu-id="8ee19-108">5.0</span><span class="sxs-lookup"><span data-stu-id="8ee19-108">5.0</span></span> |
| [<span data-ttu-id="8ee19-109">Seri durumdan çıkarma için ortak olmayan, parametresiz oluşturucular kullanılmıyor</span><span class="sxs-lookup"><span data-stu-id="8ee19-109">Non-public, parameterless constructors not used for deserialization</span></span>](#non-public-parameterless-constructors-not-used-for-deserialization) | <span data-ttu-id="8ee19-110">5.0</span><span class="sxs-lookup"><span data-stu-id="8ee19-110">5.0</span></span> |
| [<span data-ttu-id="8ee19-111">JsonSerializer. Serialize, tür parametresi null olduğunda ArgumentNullException oluşturur</span><span class="sxs-lookup"><span data-stu-id="8ee19-111">JsonSerializer.Serialize throws ArgumentNullException when type parameter is null</span></span>](#jsonserializerserialize-throws-argumentnullexception-when-type-parameter-is-null) | <span data-ttu-id="8ee19-112">5.0</span><span class="sxs-lookup"><span data-stu-id="8ee19-112">5.0</span></span> |
| [<span data-ttu-id="8ee19-113">JsonSerializer. serisini kaldırma tek karakterlik dize gerektirir</span><span class="sxs-lookup"><span data-stu-id="8ee19-113">JsonSerializer.Deserialize requires single-character string</span></span>](#jsonserializerdeserialize-requires-single-character-string) | <span data-ttu-id="8ee19-114">5.0</span><span class="sxs-lookup"><span data-stu-id="8ee19-114">5.0</span></span> |
| [<span data-ttu-id="8ee19-115">BinaryFormatter. serisini kaldırma, SerializationException içindeki bazı özel durumları yeniden kaydırır</span><span class="sxs-lookup"><span data-stu-id="8ee19-115">BinaryFormatter.Deserialize rewraps some exceptions in SerializationException</span></span>](#binaryformatterdeserialize-rewraps-some-exceptions-in-serializationexception) | <span data-ttu-id="8ee19-116">5.0</span><span class="sxs-lookup"><span data-stu-id="8ee19-116">5.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="8ee19-117">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="8ee19-117">.NET 5.0</span></span>

[!INCLUDE [options-honored-when-serializing-key-value-pairs](../../../includes/core-changes/serialization/5.0/options-honored-when-serializing-key-value-pairs.md)]

***

[!INCLUDE [non-public-parameterless-constructors-not-used-for-deserialization](../../../includes/core-changes/serialization/5.0/non-public-parameterless-constructors-not-used-for-deserialization.md)]

***

[!INCLUDE [jsonserializer-serialize-throws-argumentnullexception-for-null-type](../../../includes/core-changes/serialization/5.0/jsonserializer-serialize-throws-argumentnullexception-for-null-type.md)]

***

[!INCLUDE [deserializing-json-into-char-requires-single-character](../../../includes/core-changes/serialization/5.0/deserializing-json-into-char-requires-single-character.md)]

***

[!INCLUDE [binaryformatter-deserialize-rewraps-exceptions](../../../includes/core-changes/serialization/5.0/binaryformatter-deserialize-rewraps-exceptions.md)]

***
