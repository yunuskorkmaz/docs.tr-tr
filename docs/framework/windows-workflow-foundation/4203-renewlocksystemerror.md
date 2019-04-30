---
title: 4203 - RenewLockSystemError
ms.date: 03/30/2017
ms.assetid: 6ec9ec6f-4ae2-45cf-b99b-02cdb9dc9ec9
ms.openlocfilehash: 984f7ddae8797cba17753a618d0820d21bde5eef
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774354"
---
# <a name="4203---renewlocksystemerror"></a><span data-ttu-id="40870-102">4203 - RenewLockSystemError</span><span class="sxs-lookup"><span data-stu-id="40870-102">4203 - RenewLockSystemError</span></span>
## <a name="properties"></a><span data-ttu-id="40870-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="40870-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="40870-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="40870-104">ID</span></span>|<span data-ttu-id="40870-105">4203</span><span class="sxs-lookup"><span data-stu-id="40870-105">4203</span></span>|  
|<span data-ttu-id="40870-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="40870-106">Keywords</span></span>|<span data-ttu-id="40870-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="40870-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="40870-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="40870-108">Level</span></span>|<span data-ttu-id="40870-109">Hata</span><span class="sxs-lookup"><span data-stu-id="40870-109">Error</span></span>|  
|<span data-ttu-id="40870-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="40870-110">Channel</span></span>|<span data-ttu-id="40870-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="40870-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="40870-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40870-112">Description</span></span>  
 <span data-ttu-id="40870-113">SQL sağlayıcısı zaten geçirilen ya da kilit zaman aşımı nedeniyle kilit zaman aşımı genişletmek başarısız oldu veya kilit sahibi silindi gösterir.</span><span class="sxs-lookup"><span data-stu-id="40870-113">Indicates SQL provider has failed to extend lock expiration due to either lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="40870-114">SqlWorkflowInstanceStore iptal edilecek.</span><span class="sxs-lookup"><span data-stu-id="40870-114">The SqlWorkflowInstanceStore will be aborted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="40870-115">İleti</span><span class="sxs-lookup"><span data-stu-id="40870-115">Message</span></span>  
 <span data-ttu-id="40870-116">Kilit zaman aşımı genişletmek için başarısız oldu, kilit zaman aşımı zaten geçirildi veya kilit sahibi silindi.</span><span class="sxs-lookup"><span data-stu-id="40870-116">Failed to extend lock expiration, lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="40870-117">SqlWorkflowInstanceStore durduruluyor.</span><span class="sxs-lookup"><span data-stu-id="40870-117">Aborting SqlWorkflowInstanceStore.</span></span>  
  
## <a name="details"></a><span data-ttu-id="40870-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="40870-118">Details</span></span>  
  
|<span data-ttu-id="40870-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="40870-119">Data Item Name</span></span>|<span data-ttu-id="40870-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="40870-120">Data Item Type</span></span>|<span data-ttu-id="40870-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40870-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="40870-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="40870-122">AppDomain</span></span>|<span data-ttu-id="40870-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="40870-123">xs:string</span></span>|<span data-ttu-id="40870-124">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="40870-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
