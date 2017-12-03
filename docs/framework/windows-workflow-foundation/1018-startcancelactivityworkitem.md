---
title: 1018 - StartCancelActivityWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68b4fa1d-eee6-4a2a-8c16-7e9d89f08ab9
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b64ea860e9881ed31aa0d8e78dec55f329cc6fad
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="1018---startcancelactivityworkitem"></a><span data-ttu-id="f6107-102">1018 - StartCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="f6107-102">1018 - StartCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="f6107-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="f6107-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f6107-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="f6107-104">ID</span></span>|<span data-ttu-id="f6107-105">1018</span><span class="sxs-lookup"><span data-stu-id="f6107-105">1018</span></span>|  
|<span data-ttu-id="f6107-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="f6107-106">Keywords</span></span>|<span data-ttu-id="f6107-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="f6107-107">WFRuntime</span></span>|  
|<span data-ttu-id="f6107-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="f6107-108">Level</span></span>|<span data-ttu-id="f6107-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="f6107-109">Verbose</span></span>|  
|<span data-ttu-id="f6107-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="f6107-110">Channel</span></span>|<span data-ttu-id="f6107-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="f6107-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f6107-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f6107-112">Description</span></span>  
 <span data-ttu-id="f6107-113">Bir CancelActivityWorkItem yürütme başlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f6107-113">Indicates a CancelActivityWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f6107-114">İleti</span><span class="sxs-lookup"><span data-stu-id="f6107-114">Message</span></span>  
 <span data-ttu-id="f6107-115">'%1', DisplayName etkinliğinin CancelActivityWorkItem yürütülmesi başlatılıyor: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="f6107-115">Starting execution of a CancelActivityWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f6107-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="f6107-116">Details</span></span>  
  
|<span data-ttu-id="f6107-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="f6107-117">Data Item Name</span></span>|<span data-ttu-id="f6107-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="f6107-118">Data Item Type</span></span>|<span data-ttu-id="f6107-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f6107-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f6107-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="f6107-120">Activity</span></span>|<span data-ttu-id="f6107-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="f6107-121">xs:string</span></span>|<span data-ttu-id="f6107-122">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="f6107-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="f6107-123">Görünen adı</span><span class="sxs-lookup"><span data-stu-id="f6107-123">DisplayName</span></span>|<span data-ttu-id="f6107-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="f6107-124">xs:string</span></span>|<span data-ttu-id="f6107-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="f6107-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="f6107-126">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="f6107-126">InstanceId</span></span>|<span data-ttu-id="f6107-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="f6107-127">xs:string</span></span>|<span data-ttu-id="f6107-128">Etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="f6107-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="f6107-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f6107-129">AppDomain</span></span>|<span data-ttu-id="f6107-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="f6107-130">xs:string</span></span>|<span data-ttu-id="f6107-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="f6107-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
