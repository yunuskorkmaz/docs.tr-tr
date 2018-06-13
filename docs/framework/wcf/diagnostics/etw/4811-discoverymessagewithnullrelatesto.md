---
title: 4811 - DiscoveryMessageWithNullRelatesTo
ms.date: 03/30/2017
ms.assetid: dab901e8-a2b3-41c1-a76b-bcd8b3c7c29a
ms.openlocfilehash: 74ce12656d0cfd994cb3b0ea1021405a89a30751
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33469742"
---
# <a name="4811---discoverymessagewithnullrelatesto"></a><span data-ttu-id="31bf0-102">4811 - DiscoveryMessageWithNullRelatesTo</span><span class="sxs-lookup"><span data-stu-id="31bf0-102">4811 - DiscoveryMessageWithNullRelatesTo</span></span>
## <a name="properties"></a><span data-ttu-id="31bf0-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="31bf0-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="31bf0-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="31bf0-104">ID</span></span>|<span data-ttu-id="31bf0-105">4811</span><span class="sxs-lookup"><span data-stu-id="31bf0-105">4811</span></span>|  
|<span data-ttu-id="31bf0-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="31bf0-106">Keywords</span></span>|<span data-ttu-id="31bf0-107">Bulma</span><span class="sxs-lookup"><span data-stu-id="31bf0-107">Discovery</span></span>|  
|<span data-ttu-id="31bf0-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="31bf0-108">Level</span></span>|<span data-ttu-id="31bf0-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="31bf0-109">Warning</span></span>|  
|<span data-ttu-id="31bf0-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="31bf0-110">Channel</span></span>|<span data-ttu-id="31bf0-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="31bf0-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="31bf0-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="31bf0-112">Description</span></span>  
 <span data-ttu-id="31bf0-113">İleti üstbilgisi gerekli RelatesTo özelliği içermediğinden bulma ileti DiscoveryClient tarafından bırakıldı olduğunda bu olay yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="31bf0-113">This event is emitted when the discovery message was dropped by the DiscoveryClient because the message header did not contain the required RelatesTo property.</span></span>  
  
## <a name="message"></a><span data-ttu-id="31bf0-114">İleti</span><span class="sxs-lookup"><span data-stu-id="31bf0-114">Message</span></span>  
 <span data-ttu-id="31bf0-115">MessageID ile bir %1 ileti = '%2', DiscoveryClient tarafından bırakıldı, çünkü ileti üstbilgisi gerekli RelatesTo özelliği içermiyordu.</span><span class="sxs-lookup"><span data-stu-id="31bf0-115">A %1 message with messageId='%2' was dropped by the DiscoveryClient because the message header did not contain the required RelatesTo property.</span></span>  
  
## <a name="details"></a><span data-ttu-id="31bf0-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="31bf0-116">Details</span></span>
