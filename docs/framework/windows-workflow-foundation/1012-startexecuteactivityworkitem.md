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
ms.openlocfilehash: 6a06cec1ab251b8f7e82aef71589bd56e5f55f2e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="1012---startexecuteactivityworkitem"></a><span data-ttu-id="2848c-102">1012 - StartExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="2848c-102">1012 - StartExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="2848c-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="2848c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2848c-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="2848c-104">ID</span></span>|<span data-ttu-id="2848c-105">1012</span><span class="sxs-lookup"><span data-stu-id="2848c-105">1012</span></span>|  
|<span data-ttu-id="2848c-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="2848c-106">Keywords</span></span>|<span data-ttu-id="2848c-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="2848c-107">WFRuntime</span></span>|  
|<span data-ttu-id="2848c-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="2848c-108">Level</span></span>|<span data-ttu-id="2848c-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="2848c-109">Verbose</span></span>|  
|<span data-ttu-id="2848c-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="2848c-110">Channel</span></span>|<span data-ttu-id="2848c-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="2848c-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2848c-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2848c-112">Description</span></span>  
 <span data-ttu-id="2848c-113">Bir ExecuteActivityWorkItem yürütme başlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2848c-113">Indicates an ExecuteActivityWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2848c-114">İleti</span><span class="sxs-lookup"><span data-stu-id="2848c-114">Message</span></span>  
 <span data-ttu-id="2848c-115">'%1', DisplayName etkinliği için bir ExecuteActivityWorkItem yürütülmesi başlatılıyor: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="2848c-115">Starting execution of an ExecuteActivityWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2848c-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="2848c-116">Details</span></span>  
  
|<span data-ttu-id="2848c-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="2848c-117">Data Item Name</span></span>|<span data-ttu-id="2848c-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="2848c-118">Data Item Type</span></span>|<span data-ttu-id="2848c-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2848c-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2848c-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="2848c-120">Activity</span></span>|<span data-ttu-id="2848c-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="2848c-121">xs:string</span></span>|<span data-ttu-id="2848c-122">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="2848c-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="2848c-123">Görünen adı</span><span class="sxs-lookup"><span data-stu-id="2848c-123">DisplayName</span></span>|<span data-ttu-id="2848c-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="2848c-124">xs:string</span></span>|<span data-ttu-id="2848c-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="2848c-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="2848c-126">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="2848c-126">InstanceId</span></span>|<span data-ttu-id="2848c-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="2848c-127">xs:string</span></span>|<span data-ttu-id="2848c-128">Etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="2848c-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="2848c-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2848c-129">AppDomain</span></span>|<span data-ttu-id="2848c-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="2848c-130">xs:string</span></span>|<span data-ttu-id="2848c-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="2848c-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
