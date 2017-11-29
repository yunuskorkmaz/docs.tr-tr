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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f87e99585ccbdf3b89653f026860e7b66dc6c9b6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="4209---timeoutopeningsqlconnection"></a><span data-ttu-id="c77be-102">4209 - TimeoutOpeningSqlConnection</span><span class="sxs-lookup"><span data-stu-id="c77be-102">4209 - TimeoutOpeningSqlConnection</span></span>
## <a name="properties"></a><span data-ttu-id="c77be-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="c77be-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c77be-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="c77be-104">ID</span></span>|<span data-ttu-id="c77be-105">4209</span><span class="sxs-lookup"><span data-stu-id="c77be-105">4209</span></span>|  
|<span data-ttu-id="c77be-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="c77be-106">Keywords</span></span>|<span data-ttu-id="c77be-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="c77be-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="c77be-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="c77be-108">Level</span></span>|<span data-ttu-id="c77be-109">Hata</span><span class="sxs-lookup"><span data-stu-id="c77be-109">Error</span></span>|  
|<span data-ttu-id="c77be-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="c77be-110">Channel</span></span>|<span data-ttu-id="c77be-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="c77be-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c77be-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c77be-112">Description</span></span>  
 <span data-ttu-id="c77be-113">SQL bağlantısı açılmaya çalışırken zaman aşımı oluştu gösterir.</span><span class="sxs-lookup"><span data-stu-id="c77be-113">Indicates a timeout was encountered when trying to open a SQL connection.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c77be-114">İleti</span><span class="sxs-lookup"><span data-stu-id="c77be-114">Message</span></span>  
 <span data-ttu-id="c77be-115">SQL bağlantısı açılmaya çalışılırken zaman aşımı.</span><span class="sxs-lookup"><span data-stu-id="c77be-115">Timeout trying to open a SQL connection.</span></span> <span data-ttu-id="c77be-116">İşlemi %1 ' ayrılan süre içinde tamamlanmadı.</span><span class="sxs-lookup"><span data-stu-id="c77be-116">The operation did not complete within the allotted timeout of %1.</span></span> <span data-ttu-id="c77be-117">Bu işlem için ayrılan süre daha uzun bir süre bir kısmı olabilir.</span><span class="sxs-lookup"><span data-stu-id="c77be-117">The time allotted to this operation may have been a portion of a longer timeout.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c77be-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="c77be-118">Details</span></span>  
  
|<span data-ttu-id="c77be-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="c77be-119">Data Item Name</span></span>|<span data-ttu-id="c77be-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="c77be-120">Data Item Type</span></span>|<span data-ttu-id="c77be-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c77be-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c77be-122">Zaman aşımı</span><span class="sxs-lookup"><span data-stu-id="c77be-122">Timeout</span></span>|<span data-ttu-id="c77be-123">xs: String</span><span class="sxs-lookup"><span data-stu-id="c77be-123">xs:string</span></span>|<span data-ttu-id="c77be-124">SQL Bağlantısı açmak için zaman aşımı değeri.</span><span class="sxs-lookup"><span data-stu-id="c77be-124">The timeout value for opening the SQL connection.</span></span>|  
|<span data-ttu-id="c77be-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c77be-125">AppDomain</span></span>|<span data-ttu-id="c77be-126">xs: String</span><span class="sxs-lookup"><span data-stu-id="c77be-126">xs:string</span></span>|<span data-ttu-id="c77be-127">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="c77be-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
