---
title: 4209 - TimeoutOpeningSqlConnection
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0e56518-9758-41dc-a760-50d1a10fba6e
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7528c967cbd88f00af448d6163c10e807f603bc6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="4209---timeoutopeningsqlconnection"></a><span data-ttu-id="3d608-102">4209 - TimeoutOpeningSqlConnection</span><span class="sxs-lookup"><span data-stu-id="3d608-102">4209 - TimeoutOpeningSqlConnection</span></span>
## <a name="properties"></a><span data-ttu-id="3d608-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="3d608-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3d608-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="3d608-104">ID</span></span>|<span data-ttu-id="3d608-105">4209</span><span class="sxs-lookup"><span data-stu-id="3d608-105">4209</span></span>|  
|<span data-ttu-id="3d608-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="3d608-106">Keywords</span></span>|<span data-ttu-id="3d608-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="3d608-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="3d608-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="3d608-108">Level</span></span>|<span data-ttu-id="3d608-109">Hata</span><span class="sxs-lookup"><span data-stu-id="3d608-109">Error</span></span>|  
|<span data-ttu-id="3d608-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="3d608-110">Channel</span></span>|<span data-ttu-id="3d608-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="3d608-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3d608-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3d608-112">Description</span></span>  
 <span data-ttu-id="3d608-113">SQL bağlantısı açılmaya çalışırken zaman aşımı oluştu gösterir.</span><span class="sxs-lookup"><span data-stu-id="3d608-113">Indicates a timeout was encountered when trying to open a SQL connection.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3d608-114">İleti</span><span class="sxs-lookup"><span data-stu-id="3d608-114">Message</span></span>  
 <span data-ttu-id="3d608-115">SQL bağlantısı açılmaya çalışılırken zaman aşımı.</span><span class="sxs-lookup"><span data-stu-id="3d608-115">Timeout trying to open a SQL connection.</span></span> <span data-ttu-id="3d608-116">İşlemi %1 ' ayrılan süre içinde tamamlanmadı.</span><span class="sxs-lookup"><span data-stu-id="3d608-116">The operation did not complete within the allotted timeout of %1.</span></span> <span data-ttu-id="3d608-117">Bu işlem için ayrılan süre daha uzun bir süre bir kısmı olabilir.</span><span class="sxs-lookup"><span data-stu-id="3d608-117">The time allotted to this operation may have been a portion of a longer timeout.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3d608-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="3d608-118">Details</span></span>  
  
|<span data-ttu-id="3d608-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="3d608-119">Data Item Name</span></span>|<span data-ttu-id="3d608-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="3d608-120">Data Item Type</span></span>|<span data-ttu-id="3d608-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3d608-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3d608-122">Zaman aşımı</span><span class="sxs-lookup"><span data-stu-id="3d608-122">Timeout</span></span>|<span data-ttu-id="3d608-123">xs: String</span><span class="sxs-lookup"><span data-stu-id="3d608-123">xs:string</span></span>|<span data-ttu-id="3d608-124">SQL Bağlantısı açmak için zaman aşımı değeri.</span><span class="sxs-lookup"><span data-stu-id="3d608-124">The timeout value for opening the SQL connection.</span></span>|  
|<span data-ttu-id="3d608-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="3d608-125">AppDomain</span></span>|<span data-ttu-id="3d608-126">xs: String</span><span class="sxs-lookup"><span data-stu-id="3d608-126">xs:string</span></span>|<span data-ttu-id="3d608-127">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="3d608-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
