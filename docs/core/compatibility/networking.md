---
title: Ağ bozan değişiklikler
description: .NET Core 2,0 ve 3,0 ' de ağ üzerindeki son değişiklikleri listeler.
ms.date: 05/05/2020
ms.openlocfilehash: 761c6481888bcb8e91f7b4212355aca067632495
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95689218"
---
# <a name="networking-breaking-changes-in-net-core-20-and-30"></a><span data-ttu-id="7a274-103">.NET Core 2,0 ve 3,0 ' de ağ bozan değişiklikler</span><span class="sxs-lookup"><span data-stu-id="7a274-103">Networking breaking changes in .NET Core 2.0 and 3.0</span></span>

<span data-ttu-id="7a274-104">Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="7a274-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="7a274-105">Son değişiklik</span><span class="sxs-lookup"><span data-stu-id="7a274-105">Breaking change</span></span> | <span data-ttu-id="7a274-106">Tanıtılan sürüm</span><span class="sxs-lookup"><span data-stu-id="7a274-106">Introduced version</span></span> |
| - | - |
| [<span data-ttu-id="7a274-107">HttpRequestMessage. Version öğesinin varsayılan değeri 1,1 olarak değiştirildi</span><span class="sxs-lookup"><span data-stu-id="7a274-107">Default value of HttpRequestMessage.Version changed to 1.1</span></span>](#default-value-of-httprequestmessageversion-changed-to-11) | <span data-ttu-id="7a274-108">3,0</span><span class="sxs-lookup"><span data-stu-id="7a274-108">3.0</span></span> |
| [<span data-ttu-id="7a274-109">WebClient. Iptallasync her zaman hemen iptal etmez</span><span class="sxs-lookup"><span data-stu-id="7a274-109">WebClient.CancelAsync doesn't always cancel immediately</span></span>](#webclientcancelasync-doesnt-always-cancel-immediately) | <span data-ttu-id="7a274-110">2,0</span><span class="sxs-lookup"><span data-stu-id="7a274-110">2.0</span></span> |

## <a name="net-core-30"></a><span data-ttu-id="7a274-111">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="7a274-111">.NET Core 3.0</span></span>

[!INCLUDE[Default value of HttpRequestMessage.Version changed to 1.1](~/includes/core-changes/networking/3.0/httprequestmessage-version-change.md)]

***

## <a name="net-core-20"></a><span data-ttu-id="7a274-112">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="7a274-112">.NET Core 2.0</span></span>

[!INCLUDE [behavior-change-webclient-cancelasync](../../../includes/core-changes/networking/2.0/behavior-change-webclient-cancelasync.md)]

***
