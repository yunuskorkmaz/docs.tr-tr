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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 77ef22bd29c167b5be26ceb5360397d38c547c22
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="1028---completetransactioncontextworkitem"></a><span data-ttu-id="c29ed-102">1028 - CompleteTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="c29ed-102">1028 - CompleteTransactionContextWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="c29ed-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="c29ed-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c29ed-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="c29ed-104">ID</span></span>|<span data-ttu-id="c29ed-105">1028</span><span class="sxs-lookup"><span data-stu-id="c29ed-105">1028</span></span>|  
|<span data-ttu-id="c29ed-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="c29ed-106">Keywords</span></span>|<span data-ttu-id="c29ed-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="c29ed-107">WFRuntime</span></span>|  
|<span data-ttu-id="c29ed-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="c29ed-108">Level</span></span>|<span data-ttu-id="c29ed-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="c29ed-109">Verbose</span></span>|  
|<span data-ttu-id="c29ed-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="c29ed-110">Channel</span></span>|<span data-ttu-id="c29ed-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="c29ed-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c29ed-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c29ed-112">Description</span></span>  
 <span data-ttu-id="c29ed-113">Bir TransactionContextWorkItem tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c29ed-113">Indicates a TransactionContextWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c29ed-114">İleti</span><span class="sxs-lookup"><span data-stu-id="c29ed-114">Message</span></span>  
 <span data-ttu-id="c29ed-115">'%1', DisplayName etkinliği için bir TransactionContextWorkItem tamamlandı: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="c29ed-115">A TransactionContextWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c29ed-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="c29ed-116">Details</span></span>  
  
|<span data-ttu-id="c29ed-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="c29ed-117">Data Item Name</span></span>|<span data-ttu-id="c29ed-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="c29ed-118">Data Item Type</span></span>|<span data-ttu-id="c29ed-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c29ed-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c29ed-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="c29ed-120">Activity</span></span>|<span data-ttu-id="c29ed-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="c29ed-121">xs:string</span></span>|<span data-ttu-id="c29ed-122">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="c29ed-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="c29ed-123">Görünen adı</span><span class="sxs-lookup"><span data-stu-id="c29ed-123">DisplayName</span></span>|<span data-ttu-id="c29ed-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="c29ed-124">xs:string</span></span>|<span data-ttu-id="c29ed-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="c29ed-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="c29ed-126">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="c29ed-126">InstanceId</span></span>|<span data-ttu-id="c29ed-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="c29ed-127">xs:string</span></span>|<span data-ttu-id="c29ed-128">Etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="c29ed-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="c29ed-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c29ed-129">AppDomain</span></span>|<span data-ttu-id="c29ed-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="c29ed-130">xs:string</span></span>|<span data-ttu-id="c29ed-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="c29ed-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
