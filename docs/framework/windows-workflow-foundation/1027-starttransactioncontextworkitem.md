---
title: 1027 - StartTransactionContextWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 116ae5ec-b9d5-4231-824e-270d00eea7b8
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: be35a4d478f4f2af0921cac942ebb95d6aed38d7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="1027---starttransactioncontextworkitem"></a><span data-ttu-id="c8fb9-102">1027 - StartTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="c8fb9-102">1027 - StartTransactionContextWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="c8fb9-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="c8fb9-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c8fb9-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="c8fb9-104">ID</span></span>|<span data-ttu-id="c8fb9-105">1027</span><span class="sxs-lookup"><span data-stu-id="c8fb9-105">1027</span></span>|  
|<span data-ttu-id="c8fb9-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="c8fb9-106">Keywords</span></span>|<span data-ttu-id="c8fb9-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="c8fb9-107">WFRuntime</span></span>|  
|<span data-ttu-id="c8fb9-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="c8fb9-108">Level</span></span>|<span data-ttu-id="c8fb9-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="c8fb9-109">Verbose</span></span>|  
|<span data-ttu-id="c8fb9-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="c8fb9-110">Channel</span></span>|<span data-ttu-id="c8fb9-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="c8fb9-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c8fb9-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c8fb9-112">Description</span></span>  
 <span data-ttu-id="c8fb9-113">Bir TransactionContextWorkItem yürütme başlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c8fb9-113">Indicates a TransactionContextWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c8fb9-114">İleti</span><span class="sxs-lookup"><span data-stu-id="c8fb9-114">Message</span></span>  
 <span data-ttu-id="c8fb9-115">'%1', DisplayName etkinliğinin TransactionContextWorkItem yürütülmesi başlatılıyor: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="c8fb9-115">Starting execution of a TransactionContextWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c8fb9-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="c8fb9-116">Details</span></span>  
  
|<span data-ttu-id="c8fb9-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="c8fb9-117">Data Item Name</span></span>|<span data-ttu-id="c8fb9-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="c8fb9-118">Data Item Type</span></span>|<span data-ttu-id="c8fb9-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c8fb9-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c8fb9-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="c8fb9-120">Activity</span></span>|<span data-ttu-id="c8fb9-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="c8fb9-121">xs:string</span></span>|<span data-ttu-id="c8fb9-122">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="c8fb9-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="c8fb9-123">Görünen adı</span><span class="sxs-lookup"><span data-stu-id="c8fb9-123">DisplayName</span></span>|<span data-ttu-id="c8fb9-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="c8fb9-124">xs:string</span></span>|<span data-ttu-id="c8fb9-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="c8fb9-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="c8fb9-126">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="c8fb9-126">InstanceId</span></span>|<span data-ttu-id="c8fb9-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="c8fb9-127">xs:string</span></span>|<span data-ttu-id="c8fb9-128">Etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="c8fb9-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="c8fb9-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c8fb9-129">AppDomain</span></span>|<span data-ttu-id="c8fb9-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="c8fb9-130">xs:string</span></span>|<span data-ttu-id="c8fb9-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="c8fb9-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
