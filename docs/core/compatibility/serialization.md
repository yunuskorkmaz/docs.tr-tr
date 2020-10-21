---
title: Son değişiklikleri serileştirme
description: .NET Core ve .NET 5,0 ve sonraki sürümlerde serileştirme kategorisindeki son değişiklikleri listeler.
ms.date: 07/30/2020
ms.openlocfilehash: 67608c8e7a9745c060b7eb179fe5a956ede9f80f
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/21/2020
ms.locfileid: "92332892"
---
# <a name="serialization-breaking-changes"></a><span data-ttu-id="658ca-103">Son değişiklikleri serileştirme</span><span class="sxs-lookup"><span data-stu-id="658ca-103">Serialization breaking changes</span></span>

<span data-ttu-id="658ca-104">Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="658ca-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="658ca-105">Son değişiklik</span><span class="sxs-lookup"><span data-stu-id="658ca-105">Breaking change</span></span> | <span data-ttu-id="658ca-106">Tanıtılan sürüm</span><span class="sxs-lookup"><span data-stu-id="658ca-106">Introduced version</span></span> |
| - | - |
| [<span data-ttu-id="658ca-107">ASP.NET Core uygulamalar, tırnak işaretli sayıların serisini kaldırmada izin veriyor</span><span class="sxs-lookup"><span data-stu-id="658ca-107">ASP.NET Core apps allow deserializing quoted numbers</span></span>](#aspnet-core-apps-allow-deserializing-quoted-numbers) | <span data-ttu-id="658ca-108">5.0</span><span class="sxs-lookup"><span data-stu-id="658ca-108">5.0</span></span> |
| [<span data-ttu-id="658ca-109">Anahtar-değer çiftlerini serileştirmek ve seri durumdan çıkarılırken PropertyNamingPolicy, Propertynamecaseduyarsız ve kodlayıcı seçenekleri kabul edilir</span><span class="sxs-lookup"><span data-stu-id="658ca-109">PropertyNamingPolicy, PropertyNameCaseInsensitive, and Encoder options are honored when serializing and deserializing key-value pairs</span></span>](#propertynamingpolicy-propertynamecaseinsensitive-and-encoder-options-are-honored-when-serializing-and-deserializing-key-value-pairs) | <span data-ttu-id="658ca-110">5.0</span><span class="sxs-lookup"><span data-stu-id="658ca-110">5.0</span></span> |
| [<span data-ttu-id="658ca-111">Seri durumdan çıkarma için ortak olmayan, parametresiz oluşturucular kullanılmıyor</span><span class="sxs-lookup"><span data-stu-id="658ca-111">Non-public, parameterless constructors not used for deserialization</span></span>](#non-public-parameterless-constructors-not-used-for-deserialization) | <span data-ttu-id="658ca-112">5.0</span><span class="sxs-lookup"><span data-stu-id="658ca-112">5.0</span></span> |
| [<span data-ttu-id="658ca-113">JsonSerializer. Serialize, tür parametresi null olduğunda ArgumentNullException oluşturur</span><span class="sxs-lookup"><span data-stu-id="658ca-113">JsonSerializer.Serialize throws ArgumentNullException when type parameter is null</span></span>](#jsonserializerserialize-throws-argumentnullexception-when-type-parameter-is-null) | <span data-ttu-id="658ca-114">5.0</span><span class="sxs-lookup"><span data-stu-id="658ca-114">5.0</span></span> |
| [<span data-ttu-id="658ca-115">JsonSerializer. serisini kaldırma tek karakterlik dize gerektirir</span><span class="sxs-lookup"><span data-stu-id="658ca-115">JsonSerializer.Deserialize requires single-character string</span></span>](#jsonserializerdeserialize-requires-single-character-string) | <span data-ttu-id="658ca-116">5.0</span><span class="sxs-lookup"><span data-stu-id="658ca-116">5.0</span></span> |
| [<span data-ttu-id="658ca-117">BinaryFormatter. serisini kaldırma, SerializationException içindeki bazı özel durumları yeniden kaydırır</span><span class="sxs-lookup"><span data-stu-id="658ca-117">BinaryFormatter.Deserialize rewraps some exceptions in SerializationException</span></span>](#binaryformatterdeserialize-rewraps-some-exceptions-in-serializationexception) | <span data-ttu-id="658ca-118">5.0</span><span class="sxs-lookup"><span data-stu-id="658ca-118">5.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="658ca-119">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="658ca-119">.NET 5.0</span></span>

[!INCLUDE [jsonserializer-allows-reading-numbers-as-strings](../../../includes/core-changes/serialization/5.0/jsonserializer-allows-reading-numbers-as-strings.md)]

***

[!INCLUDE [options-honored-when-serializing-key-value-pairs](../../../includes/core-changes/serialization/5.0/options-honored-when-serializing-key-value-pairs.md)]

<span data-ttu-id="658ca-120">\*\*_</span><span class="sxs-lookup"><span data-stu-id="658ca-120">\*\*_</span></span>

[!INCLUDE [non-public-parameterless-constructors-not-used-for-deserialization](../../../includes/core-changes/serialization/5.0/non-public-parameterless-constructors-not-used-for-deserialization.md)]

_*_

[!INCLUDE [jsonserializer-serialize-throws-argumentnullexception-for-null-type](../../../includes/core-changes/serialization/5.0/jsonserializer-serialize-throws-argumentnullexception-for-null-type.md)]

_*_

[!INCLUDE [deserializing-json-into-char-requires-single-character](../../../includes/core-changes/serialization/5.0/deserializing-json-into-char-requires-single-character.md)]

_*_

[!INCLUDE [binaryformatter-deserialize-rewraps-exceptions](../../../includes/core-changes/serialization/5.0/binaryformatter-deserialize-rewraps-exceptions.md)]

<span data-ttu-id="658ca-121">_\*\*</span><span class="sxs-lookup"><span data-stu-id="658ca-121">_\*\*</span></span>
