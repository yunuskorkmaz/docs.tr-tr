---
title: 4209 - TimeoutOpeningSqlConnection
ms.date: 03/30/2017
ms.assetid: f0e56518-9758-41dc-a760-50d1a10fba6e
ms.openlocfilehash: 9aa8cdffebb0cdf8b1e8225a394edf78ecf032b9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96238684"
---
# <a name="4209---timeoutopeningsqlconnection"></a><span data-ttu-id="57ca4-102">4209 - TimeoutOpeningSqlConnection</span><span class="sxs-lookup"><span data-stu-id="57ca4-102">4209 - TimeoutOpeningSqlConnection</span></span>

## <a name="properties"></a><span data-ttu-id="57ca4-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="57ca4-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="57ca4-104">ID</span><span class="sxs-lookup"><span data-stu-id="57ca4-104">ID</span></span>|<span data-ttu-id="57ca4-105">4209</span><span class="sxs-lookup"><span data-stu-id="57ca4-105">4209</span></span>|  
|<span data-ttu-id="57ca4-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="57ca4-106">Keywords</span></span>|<span data-ttu-id="57ca4-107">Wfınstancestore</span><span class="sxs-lookup"><span data-stu-id="57ca4-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="57ca4-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="57ca4-108">Level</span></span>|<span data-ttu-id="57ca4-109">Hata</span><span class="sxs-lookup"><span data-stu-id="57ca4-109">Error</span></span>|  
|<span data-ttu-id="57ca4-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="57ca4-110">Channel</span></span>|<span data-ttu-id="57ca4-111">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="57ca4-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="57ca4-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="57ca4-112">Description</span></span>  

 <span data-ttu-id="57ca4-113">Bir SQL bağlantısı açılmaya çalışılırken zaman aşımıyla karşılaşıldı.</span><span class="sxs-lookup"><span data-stu-id="57ca4-113">Indicates a timeout was encountered when trying to open a SQL connection.</span></span>  
  
## <a name="message"></a><span data-ttu-id="57ca4-114">İleti</span><span class="sxs-lookup"><span data-stu-id="57ca4-114">Message</span></span>  

 <span data-ttu-id="57ca4-115">SQL bağlantısı açılmaya çalışılırken zaman aşımı oluştu.</span><span class="sxs-lookup"><span data-stu-id="57ca4-115">Timeout trying to open a SQL connection.</span></span> <span data-ttu-id="57ca4-116">İşlem ayrılan %1 zaman aşımı süresi içinde tamamlanmadı.</span><span class="sxs-lookup"><span data-stu-id="57ca4-116">The operation did not complete within the allotted timeout of %1.</span></span> <span data-ttu-id="57ca4-117">Bu işlem için ayrılan süre daha uzun bir zaman aşımı değerinin bir bölümü olabilir.</span><span class="sxs-lookup"><span data-stu-id="57ca4-117">The time allotted to this operation may have been a portion of a longer timeout.</span></span>  
  
## <a name="details"></a><span data-ttu-id="57ca4-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="57ca4-118">Details</span></span>  
  
|<span data-ttu-id="57ca4-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="57ca4-119">Data Item Name</span></span>|<span data-ttu-id="57ca4-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="57ca4-120">Data Item Type</span></span>|<span data-ttu-id="57ca4-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="57ca4-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="57ca4-122">Zaman aşımı</span><span class="sxs-lookup"><span data-stu-id="57ca4-122">Timeout</span></span>|<span data-ttu-id="57ca4-123">xs: String</span><span class="sxs-lookup"><span data-stu-id="57ca4-123">xs:string</span></span>|<span data-ttu-id="57ca4-124">SQL bağlantısını açmak için zaman aşımı değeri.</span><span class="sxs-lookup"><span data-stu-id="57ca4-124">The timeout value for opening the SQL connection.</span></span>|  
|<span data-ttu-id="57ca4-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="57ca4-125">AppDomain</span></span>|<span data-ttu-id="57ca4-126">xs: String</span><span class="sxs-lookup"><span data-stu-id="57ca4-126">xs:string</span></span>|<span data-ttu-id="57ca4-127">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="57ca4-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
