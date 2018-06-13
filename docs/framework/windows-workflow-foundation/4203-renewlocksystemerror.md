---
title: 4203 - RenewLockSystemError
ms.date: 03/30/2017
ms.assetid: 6ec9ec6f-4ae2-45cf-b99b-02cdb9dc9ec9
ms.openlocfilehash: 984f7ddae8797cba17753a618d0820d21bde5eef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33513935"
---
# <a name="4203---renewlocksystemerror"></a><span data-ttu-id="aad91-102">4203 - RenewLockSystemError</span><span class="sxs-lookup"><span data-stu-id="aad91-102">4203 - RenewLockSystemError</span></span>
## <a name="properties"></a><span data-ttu-id="aad91-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="aad91-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="aad91-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="aad91-104">ID</span></span>|<span data-ttu-id="aad91-105">4203</span><span class="sxs-lookup"><span data-stu-id="aad91-105">4203</span></span>|  
|<span data-ttu-id="aad91-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="aad91-106">Keywords</span></span>|<span data-ttu-id="aad91-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="aad91-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="aad91-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="aad91-108">Level</span></span>|<span data-ttu-id="aad91-109">Hata</span><span class="sxs-lookup"><span data-stu-id="aad91-109">Error</span></span>|  
|<span data-ttu-id="aad91-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="aad91-110">Channel</span></span>|<span data-ttu-id="aad91-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="aad91-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="aad91-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aad91-112">Description</span></span>  
 <span data-ttu-id="aad91-113">SQL sağlayıcısı kilitleme sona ermesi zaten geçirilen ya da kilitleme sona erme nedeniyle genişletmek başarısız oldu veya kilit sahibi silindi gösterir.</span><span class="sxs-lookup"><span data-stu-id="aad91-113">Indicates SQL provider has failed to extend lock expiration due to either lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="aad91-114">SqlWorkflowInstanceStore iptal edilecek.</span><span class="sxs-lookup"><span data-stu-id="aad91-114">The SqlWorkflowInstanceStore will be aborted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="aad91-115">İleti</span><span class="sxs-lookup"><span data-stu-id="aad91-115">Message</span></span>  
 <span data-ttu-id="aad91-116">Kilitleme sona erme genişletmek için başarısız oldu, zaten kilitleme sona erme geçirilen veya kilit sahibi silindi.</span><span class="sxs-lookup"><span data-stu-id="aad91-116">Failed to extend lock expiration, lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="aad91-117">SqlWorkflowInstanceStore durduruluyor.</span><span class="sxs-lookup"><span data-stu-id="aad91-117">Aborting SqlWorkflowInstanceStore.</span></span>  
  
## <a name="details"></a><span data-ttu-id="aad91-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="aad91-118">Details</span></span>  
  
|<span data-ttu-id="aad91-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="aad91-119">Data Item Name</span></span>|<span data-ttu-id="aad91-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="aad91-120">Data Item Type</span></span>|<span data-ttu-id="aad91-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aad91-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="aad91-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="aad91-122">AppDomain</span></span>|<span data-ttu-id="aad91-123">xs: String</span><span class="sxs-lookup"><span data-stu-id="aad91-123">xs:string</span></span>|<span data-ttu-id="aad91-124">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="aad91-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
