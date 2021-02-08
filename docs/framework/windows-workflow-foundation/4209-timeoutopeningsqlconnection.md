---
description: 'Hakkında daha fazla bilgi edinin: 4209-TimeoutOpeningSqlConnection'
title: 4209 - TimeoutOpeningSqlConnection
ms.date: 03/30/2017
ms.assetid: f0e56518-9758-41dc-a760-50d1a10fba6e
ms.openlocfilehash: 9c7540e328530fdc01b9f065dfb75b92c467bd43
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788000"
---
# <a name="4209---timeoutopeningsqlconnection"></a><span data-ttu-id="03bc3-103">4209 - TimeoutOpeningSqlConnection</span><span class="sxs-lookup"><span data-stu-id="03bc3-103">4209 - TimeoutOpeningSqlConnection</span></span>

## <a name="properties"></a><span data-ttu-id="03bc3-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="03bc3-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="03bc3-105">ID</span><span class="sxs-lookup"><span data-stu-id="03bc3-105">ID</span></span>|<span data-ttu-id="03bc3-106">4209</span><span class="sxs-lookup"><span data-stu-id="03bc3-106">4209</span></span>|  
|<span data-ttu-id="03bc3-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="03bc3-107">Keywords</span></span>|<span data-ttu-id="03bc3-108">Wfınstancestore</span><span class="sxs-lookup"><span data-stu-id="03bc3-108">WFInstanceStore</span></span>|  
|<span data-ttu-id="03bc3-109">Level</span><span class="sxs-lookup"><span data-stu-id="03bc3-109">Level</span></span>|<span data-ttu-id="03bc3-110">Hata</span><span class="sxs-lookup"><span data-stu-id="03bc3-110">Error</span></span>|  
|<span data-ttu-id="03bc3-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="03bc3-111">Channel</span></span>|<span data-ttu-id="03bc3-112">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="03bc3-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="03bc3-113">Description</span><span class="sxs-lookup"><span data-stu-id="03bc3-113">Description</span></span>  

 <span data-ttu-id="03bc3-114">Bir SQL bağlantısı açılmaya çalışılırken zaman aşımıyla karşılaşıldı.</span><span class="sxs-lookup"><span data-stu-id="03bc3-114">Indicates a timeout was encountered when trying to open a SQL connection.</span></span>  
  
## <a name="message"></a><span data-ttu-id="03bc3-115">İleti</span><span class="sxs-lookup"><span data-stu-id="03bc3-115">Message</span></span>  

 <span data-ttu-id="03bc3-116">SQL bağlantısı açılmaya çalışılırken zaman aşımı oluştu.</span><span class="sxs-lookup"><span data-stu-id="03bc3-116">Timeout trying to open a SQL connection.</span></span> <span data-ttu-id="03bc3-117">İşlem ayrılan %1 zaman aşımı süresi içinde tamamlanmadı.</span><span class="sxs-lookup"><span data-stu-id="03bc3-117">The operation did not complete within the allotted timeout of %1.</span></span> <span data-ttu-id="03bc3-118">Bu işlem için ayrılan süre daha uzun bir zaman aşımı değerinin bir bölümü olabilir.</span><span class="sxs-lookup"><span data-stu-id="03bc3-118">The time allotted to this operation may have been a portion of a longer timeout.</span></span>  
  
## <a name="details"></a><span data-ttu-id="03bc3-119">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="03bc3-119">Details</span></span>  
  
|<span data-ttu-id="03bc3-120">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="03bc3-120">Data Item Name</span></span>|<span data-ttu-id="03bc3-121">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="03bc3-121">Data Item Type</span></span>|<span data-ttu-id="03bc3-122">Description</span><span class="sxs-lookup"><span data-stu-id="03bc3-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="03bc3-123">Zaman aşımı</span><span class="sxs-lookup"><span data-stu-id="03bc3-123">Timeout</span></span>|<span data-ttu-id="03bc3-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="03bc3-124">xs:string</span></span>|<span data-ttu-id="03bc3-125">SQL bağlantısını açmak için zaman aşımı değeri.</span><span class="sxs-lookup"><span data-stu-id="03bc3-125">The timeout value for opening the SQL connection.</span></span>|  
|<span data-ttu-id="03bc3-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="03bc3-126">AppDomain</span></span>|<span data-ttu-id="03bc3-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="03bc3-127">xs:string</span></span>|<span data-ttu-id="03bc3-128">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="03bc3-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
