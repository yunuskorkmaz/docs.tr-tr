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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f74a133a685699bcefc014269a9ecb3ebea4e505
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="1018---startcancelactivityworkitem"></a><span data-ttu-id="d0e5d-102">1018 - StartCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="d0e5d-102">1018 - StartCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="d0e5d-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="d0e5d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d0e5d-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="d0e5d-104">ID</span></span>|<span data-ttu-id="d0e5d-105">1018</span><span class="sxs-lookup"><span data-stu-id="d0e5d-105">1018</span></span>|  
|<span data-ttu-id="d0e5d-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="d0e5d-106">Keywords</span></span>|<span data-ttu-id="d0e5d-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="d0e5d-107">WFRuntime</span></span>|  
|<span data-ttu-id="d0e5d-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="d0e5d-108">Level</span></span>|<span data-ttu-id="d0e5d-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="d0e5d-109">Verbose</span></span>|  
|<span data-ttu-id="d0e5d-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="d0e5d-110">Channel</span></span>|<span data-ttu-id="d0e5d-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="d0e5d-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d0e5d-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d0e5d-112">Description</span></span>  
 <span data-ttu-id="d0e5d-113">Bir CancelActivityWorkItem yürütme başlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d0e5d-113">Indicates a CancelActivityWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d0e5d-114">İleti</span><span class="sxs-lookup"><span data-stu-id="d0e5d-114">Message</span></span>  
 <span data-ttu-id="d0e5d-115">'%1', DisplayName etkinliğinin CancelActivityWorkItem yürütülmesi başlatılıyor: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="d0e5d-115">Starting execution of a CancelActivityWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d0e5d-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="d0e5d-116">Details</span></span>  
  
|<span data-ttu-id="d0e5d-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="d0e5d-117">Data Item Name</span></span>|<span data-ttu-id="d0e5d-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="d0e5d-118">Data Item Type</span></span>|<span data-ttu-id="d0e5d-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d0e5d-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d0e5d-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="d0e5d-120">Activity</span></span>|<span data-ttu-id="d0e5d-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="d0e5d-121">xs:string</span></span>|<span data-ttu-id="d0e5d-122">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="d0e5d-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="d0e5d-123">Görünen adı</span><span class="sxs-lookup"><span data-stu-id="d0e5d-123">DisplayName</span></span>|<span data-ttu-id="d0e5d-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="d0e5d-124">xs:string</span></span>|<span data-ttu-id="d0e5d-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="d0e5d-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="d0e5d-126">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="d0e5d-126">InstanceId</span></span>|<span data-ttu-id="d0e5d-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="d0e5d-127">xs:string</span></span>|<span data-ttu-id="d0e5d-128">Etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="d0e5d-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="d0e5d-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="d0e5d-129">AppDomain</span></span>|<span data-ttu-id="d0e5d-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="d0e5d-130">xs:string</span></span>|<span data-ttu-id="d0e5d-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="d0e5d-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
