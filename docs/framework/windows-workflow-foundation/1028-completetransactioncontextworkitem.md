---
title: 1028 - CompleteTransactionContextWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95423f9d-d29a-460e-bcd8-096e80af5bd0
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3cd2ee443d6c521f168a170a1079eb4e9657e2dc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="1028---completetransactioncontextworkitem"></a><span data-ttu-id="9bf7b-102">1028 - CompleteTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="9bf7b-102">1028 - CompleteTransactionContextWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="9bf7b-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="9bf7b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9bf7b-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="9bf7b-104">ID</span></span>|<span data-ttu-id="9bf7b-105">1028</span><span class="sxs-lookup"><span data-stu-id="9bf7b-105">1028</span></span>|  
|<span data-ttu-id="9bf7b-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="9bf7b-106">Keywords</span></span>|<span data-ttu-id="9bf7b-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="9bf7b-107">WFRuntime</span></span>|  
|<span data-ttu-id="9bf7b-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="9bf7b-108">Level</span></span>|<span data-ttu-id="9bf7b-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="9bf7b-109">Verbose</span></span>|  
|<span data-ttu-id="9bf7b-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="9bf7b-110">Channel</span></span>|<span data-ttu-id="9bf7b-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="9bf7b-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9bf7b-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9bf7b-112">Description</span></span>  
 <span data-ttu-id="9bf7b-113">Bir TransactionContextWorkItem tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9bf7b-113">Indicates a TransactionContextWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9bf7b-114">İleti</span><span class="sxs-lookup"><span data-stu-id="9bf7b-114">Message</span></span>  
 <span data-ttu-id="9bf7b-115">'%1', DisplayName etkinliği için bir TransactionContextWorkItem tamamlandı: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="9bf7b-115">A TransactionContextWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9bf7b-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="9bf7b-116">Details</span></span>  
  
|<span data-ttu-id="9bf7b-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="9bf7b-117">Data Item Name</span></span>|<span data-ttu-id="9bf7b-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="9bf7b-118">Data Item Type</span></span>|<span data-ttu-id="9bf7b-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9bf7b-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9bf7b-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="9bf7b-120">Activity</span></span>|<span data-ttu-id="9bf7b-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="9bf7b-121">xs:string</span></span>|<span data-ttu-id="9bf7b-122">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="9bf7b-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="9bf7b-123">Görünen adı</span><span class="sxs-lookup"><span data-stu-id="9bf7b-123">DisplayName</span></span>|<span data-ttu-id="9bf7b-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="9bf7b-124">xs:string</span></span>|<span data-ttu-id="9bf7b-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="9bf7b-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="9bf7b-126">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="9bf7b-126">InstanceId</span></span>|<span data-ttu-id="9bf7b-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="9bf7b-127">xs:string</span></span>|<span data-ttu-id="9bf7b-128">Etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="9bf7b-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="9bf7b-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9bf7b-129">AppDomain</span></span>|<span data-ttu-id="9bf7b-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="9bf7b-130">xs:string</span></span>|<span data-ttu-id="9bf7b-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="9bf7b-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
