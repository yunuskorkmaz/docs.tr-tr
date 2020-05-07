---
title: Ağ bozan değişiklikler
description: .NET Core 'da ağ üzerindeki son değişiklikleri listeler.
ms.date: 05/05/2020
ms.openlocfilehash: 07e0b2e062ce244cd6312bbe08bcc63db4c74347
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82859626"
---
# <a name="networking-breaking-changes"></a><span data-ttu-id="2cb51-103">Ağ bozan değişiklikler</span><span class="sxs-lookup"><span data-stu-id="2cb51-103">Networking breaking changes</span></span>

<span data-ttu-id="2cb51-104">Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="2cb51-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="2cb51-105">Son değişiklik</span><span class="sxs-lookup"><span data-stu-id="2cb51-105">Breaking change</span></span> | <span data-ttu-id="2cb51-106">Tanıtılan sürüm</span><span class="sxs-lookup"><span data-stu-id="2cb51-106">Introduced version</span></span> |
| - | - |
| [<span data-ttu-id="2cb51-107">HttpRequestMessage. Version öğesinin varsayılan değeri 1,1 olarak değiştirildi</span><span class="sxs-lookup"><span data-stu-id="2cb51-107">Default value of HttpRequestMessage.Version changed to 1.1</span></span>](#default-value-of-httprequestmessageversion-changed-to-11) | <span data-ttu-id="2cb51-108">3,0</span><span class="sxs-lookup"><span data-stu-id="2cb51-108">3.0</span></span> |
| [<span data-ttu-id="2cb51-109">WebClient. Iptallasync her zaman hemen iptal etmez</span><span class="sxs-lookup"><span data-stu-id="2cb51-109">WebClient.CancelAsync doesn't always cancel immediately</span></span>](#webclientcancelasync-doesnt-always-cancel-immediately) | <span data-ttu-id="2cb51-110">2,0</span><span class="sxs-lookup"><span data-stu-id="2cb51-110">2.0</span></span> |

## <a name="net-core-30"></a><span data-ttu-id="2cb51-111">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="2cb51-111">.NET Core 3.0</span></span>

[!INCLUDE[Default value of HttpRequestMessage.Version changed to 1.1](~/includes/core-changes/networking/3.0/httprequestmessage-version-change.md)]

***

## <a name="net-core-20"></a><span data-ttu-id="2cb51-112">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="2cb51-112">.NET Core 2.0</span></span>

[!INCLUDE [behavior-change-webclient-cancelasync](../../../includes/core-changes/networking/2.0/behavior-change-webclient-cancelasync.md)]

***
