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
# <a name="serialization-breaking-changes"></a><span data-ttu-id="36bde-103">Son değişiklikleri serileştirme</span><span class="sxs-lookup"><span data-stu-id="36bde-103">Serialization breaking changes</span></span>

<span data-ttu-id="36bde-104">Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="36bde-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="36bde-105">Son değişiklik</span><span class="sxs-lookup"><span data-stu-id="36bde-105">Breaking change</span></span> | <span data-ttu-id="36bde-106">Tanıtılan sürüm</span><span class="sxs-lookup"><span data-stu-id="36bde-106">Introduced version</span></span> |
| - | - |
| [<span data-ttu-id="36bde-107">JsonSerializer. Serialize, tür parametresi null olduğunda ArgumentNullException oluşturur</span><span class="sxs-lookup"><span data-stu-id="36bde-107">JsonSerializer.Serialize throws ArgumentNullException when type parameter is null</span></span>](#jsonserializerserialize-throws-argumentnullexception-when-type-parameter-is-null) | <span data-ttu-id="36bde-108">5.0</span><span class="sxs-lookup"><span data-stu-id="36bde-108">5.0</span></span> |
| [<span data-ttu-id="36bde-109">JsonSerializer. serisini kaldırma tek karakterlik dize gerektirir</span><span class="sxs-lookup"><span data-stu-id="36bde-109">JsonSerializer.Deserialize requires single-character string</span></span>](#jsonserializerdeserialize-requires-single-character-string) | <span data-ttu-id="36bde-110">5.0</span><span class="sxs-lookup"><span data-stu-id="36bde-110">5.0</span></span> |
| [<span data-ttu-id="36bde-111">BinaryFormatter. serisini kaldırma, SerializationException içindeki bazı özel durumları yeniden kaydırır</span><span class="sxs-lookup"><span data-stu-id="36bde-111">BinaryFormatter.Deserialize rewraps some exceptions in SerializationException</span></span>](#binaryformatterdeserialize-rewraps-some-exceptions-in-serializationexception) | <span data-ttu-id="36bde-112">5.0</span><span class="sxs-lookup"><span data-stu-id="36bde-112">5.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="36bde-113">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="36bde-113">.NET 5.0</span></span>

[!INCLUDE [jsonserializer-serialize-throws-argumentnullexception-for-null-type](../../../includes/core-changes/serialization/5.0/jsonserializer-serialize-throws-argumentnullexception-for-null-type.md)]

***

[!INCLUDE [deserializing-json-into-char-requires-single-character](../../../includes/core-changes/serialization/5.0/deserializing-json-into-char-requires-single-character.md)]

***

[!INCLUDE [binaryformatter-deserialize-rewraps-exceptions](../../../includes/core-changes/serialization/5.0/binaryformatter-deserialize-rewraps-exceptions.md)]

***
