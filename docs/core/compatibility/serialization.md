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
# <a name="serialization-breaking-changes"></a><span data-ttu-id="94e1d-103">Son değişiklikleri serileştirme</span><span class="sxs-lookup"><span data-stu-id="94e1d-103">Serialization breaking changes</span></span>

<span data-ttu-id="94e1d-104">Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="94e1d-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="94e1d-105">Son değişiklik</span><span class="sxs-lookup"><span data-stu-id="94e1d-105">Breaking change</span></span> | <span data-ttu-id="94e1d-106">Tanıtılan sürüm</span><span class="sxs-lookup"><span data-stu-id="94e1d-106">Introduced version</span></span> |
| - | - |
| [<span data-ttu-id="94e1d-107">JsonSerializer. serisini kaldırma tek karakterlik dize gerektirir</span><span class="sxs-lookup"><span data-stu-id="94e1d-107">JsonSerializer.Deserialize requires single-character string</span></span>](#jsonserializerdeserialize-requires-single-character-string) | <span data-ttu-id="94e1d-108">5.0</span><span class="sxs-lookup"><span data-stu-id="94e1d-108">5.0</span></span> |
| [<span data-ttu-id="94e1d-109">BinaryFormatter. serisini kaldırma, SerializationException içindeki bazı özel durumları yeniden kaydırır</span><span class="sxs-lookup"><span data-stu-id="94e1d-109">BinaryFormatter.Deserialize rewraps some exceptions in SerializationException</span></span>](#binaryformatterdeserialize-rewraps-some-exceptions-in-serializationexception) | <span data-ttu-id="94e1d-110">5.0</span><span class="sxs-lookup"><span data-stu-id="94e1d-110">5.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="94e1d-111">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="94e1d-111">.NET 5.0</span></span>

[!INCLUDE [deserializing-json-into-char-requires-single-character](../../../includes/core-changes/serialization/5.0/deserializing-json-into-char-requires-single-character.md)]

***

[!INCLUDE [binaryformatter-deserialize-rewraps-exceptions](../../../includes/core-changes/serialization/5.0/binaryformatter-deserialize-rewraps-exceptions.md)]

***
