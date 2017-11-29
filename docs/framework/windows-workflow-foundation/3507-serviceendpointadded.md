---
title: 3507 - ServiceEndpointAdded
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c068fc0e-07ee-4551-9824-ea7216e1fe37
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 463482bbcc659c6dba15b854ff06f41754f63ccc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="3507---serviceendpointadded"></a><span data-ttu-id="2225e-102">3507 - ServiceEndpointAdded</span><span class="sxs-lookup"><span data-stu-id="2225e-102">3507 - ServiceEndpointAdded</span></span>
## <a name="properties"></a><span data-ttu-id="2225e-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="2225e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2225e-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="2225e-104">ID</span></span>|<span data-ttu-id="2225e-105">3507</span><span class="sxs-lookup"><span data-stu-id="2225e-105">3507</span></span>|  
|<span data-ttu-id="2225e-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="2225e-106">Keywords</span></span>|<span data-ttu-id="2225e-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="2225e-107">WFServices</span></span>|  
|<span data-ttu-id="2225e-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="2225e-108">Level</span></span>|<span data-ttu-id="2225e-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="2225e-109">Information</span></span>|  
|<span data-ttu-id="2225e-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="2225e-110">Channel</span></span>|<span data-ttu-id="2225e-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="2225e-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2225e-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2225e-112">Description</span></span>  
 <span data-ttu-id="2225e-113">Hizmet uç noktası eklenen gösterir.</span><span class="sxs-lookup"><span data-stu-id="2225e-113">Indicates a service endpoint has been added.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2225e-114">İleti</span><span class="sxs-lookup"><span data-stu-id="2225e-114">Message</span></span>  
 <span data-ttu-id="2225e-115">Hizmet uç noktası adresi '%1', '%2' bağlama ve Sözleşme '%3' için eklendi.</span><span class="sxs-lookup"><span data-stu-id="2225e-115">A service endpoint has been added for address '%1', binding '%2', and contract '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2225e-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="2225e-116">Details</span></span>  
  
|<span data-ttu-id="2225e-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="2225e-117">Data Item Name</span></span>|<span data-ttu-id="2225e-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="2225e-118">Data Item Type</span></span>|<span data-ttu-id="2225e-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2225e-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2225e-120">Adres</span><span class="sxs-lookup"><span data-stu-id="2225e-120">Address</span></span>|<span data-ttu-id="2225e-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="2225e-121">xs:string</span></span>|<span data-ttu-id="2225e-122">Uç nokta adresi.</span><span class="sxs-lookup"><span data-stu-id="2225e-122">The address of the endpoint.</span></span>|  
|<span data-ttu-id="2225e-123">Bağlama</span><span class="sxs-lookup"><span data-stu-id="2225e-123">Binding</span></span>|<span data-ttu-id="2225e-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="2225e-124">xs:string</span></span>|<span data-ttu-id="2225e-125">Uç nokta bağlama.</span><span class="sxs-lookup"><span data-stu-id="2225e-125">The binding of the endpoint.</span></span>|  
|<span data-ttu-id="2225e-126">Daralma</span><span class="sxs-lookup"><span data-stu-id="2225e-126">Contract</span></span>|<span data-ttu-id="2225e-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="2225e-127">xs:string</span></span>|<span data-ttu-id="2225e-128">Uç nokta sözleşme.</span><span class="sxs-lookup"><span data-stu-id="2225e-128">The contract of the endpoint.</span></span>|  
|<span data-ttu-id="2225e-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2225e-129">AppDomain</span></span>|<span data-ttu-id="2225e-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="2225e-130">xs:string</span></span>|<span data-ttu-id="2225e-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="2225e-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
