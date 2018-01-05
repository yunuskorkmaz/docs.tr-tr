---
title: 1012 - StartExecuteActivityWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 29e9b1c6-c5d7-4b58-b59d-a06a923d3c80
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6a3b03e8ac24bc1652b88b71e8c25862a07c194f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="1012---startexecuteactivityworkitem"></a><span data-ttu-id="6a60b-102">1012 - StartExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="6a60b-102">1012 - StartExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="6a60b-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="6a60b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6a60b-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="6a60b-104">ID</span></span>|<span data-ttu-id="6a60b-105">1012</span><span class="sxs-lookup"><span data-stu-id="6a60b-105">1012</span></span>|  
|<span data-ttu-id="6a60b-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="6a60b-106">Keywords</span></span>|<span data-ttu-id="6a60b-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="6a60b-107">WFRuntime</span></span>|  
|<span data-ttu-id="6a60b-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="6a60b-108">Level</span></span>|<span data-ttu-id="6a60b-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="6a60b-109">Verbose</span></span>|  
|<span data-ttu-id="6a60b-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="6a60b-110">Channel</span></span>|<span data-ttu-id="6a60b-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="6a60b-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="6a60b-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6a60b-112">Description</span></span>  
 <span data-ttu-id="6a60b-113">Bir ExecuteActivityWorkItem yürütme başlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6a60b-113">Indicates an ExecuteActivityWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="6a60b-114">İleti</span><span class="sxs-lookup"><span data-stu-id="6a60b-114">Message</span></span>  
 <span data-ttu-id="6a60b-115">'%1', DisplayName etkinliği için bir ExecuteActivityWorkItem yürütülmesi başlatılıyor: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="6a60b-115">Starting execution of an ExecuteActivityWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="6a60b-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="6a60b-116">Details</span></span>  
  
|<span data-ttu-id="6a60b-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="6a60b-117">Data Item Name</span></span>|<span data-ttu-id="6a60b-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="6a60b-118">Data Item Type</span></span>|<span data-ttu-id="6a60b-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6a60b-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="6a60b-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="6a60b-120">Activity</span></span>|<span data-ttu-id="6a60b-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="6a60b-121">xs:string</span></span>|<span data-ttu-id="6a60b-122">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="6a60b-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="6a60b-123">Görünen adı</span><span class="sxs-lookup"><span data-stu-id="6a60b-123">DisplayName</span></span>|<span data-ttu-id="6a60b-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="6a60b-124">xs:string</span></span>|<span data-ttu-id="6a60b-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="6a60b-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="6a60b-126">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="6a60b-126">InstanceId</span></span>|<span data-ttu-id="6a60b-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="6a60b-127">xs:string</span></span>|<span data-ttu-id="6a60b-128">Etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="6a60b-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="6a60b-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="6a60b-129">AppDomain</span></span>|<span data-ttu-id="6a60b-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="6a60b-130">xs:string</span></span>|<span data-ttu-id="6a60b-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="6a60b-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
