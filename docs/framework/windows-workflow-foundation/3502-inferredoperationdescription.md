---
title: 3502 - InferredOperationDescription
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6aebb614-3c72-4537-ba11-3cc7200ef1f1
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e2c2464cd8c6f0c16946847a5503270453d5b019
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="3502---inferredoperationdescription"></a><span data-ttu-id="eedad-102">3502 - InferredOperationDescription</span><span class="sxs-lookup"><span data-stu-id="eedad-102">3502 - InferredOperationDescription</span></span>
## <a name="properties"></a><span data-ttu-id="eedad-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="eedad-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="eedad-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="eedad-104">ID</span></span>|<span data-ttu-id="eedad-105">3502</span><span class="sxs-lookup"><span data-stu-id="eedad-105">3502</span></span>|  
|<span data-ttu-id="eedad-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="eedad-106">Keywords</span></span>|<span data-ttu-id="eedad-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="eedad-107">WFServices</span></span>|  
|<span data-ttu-id="eedad-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="eedad-108">Level</span></span>|<span data-ttu-id="eedad-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="eedad-109">Information</span></span>|  
|<span data-ttu-id="eedad-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="eedad-110">Channel</span></span>|<span data-ttu-id="eedad-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="eedad-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="eedad-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eedad-112">Description</span></span>  
 <span data-ttu-id="eedad-113">Bir OperationDescription WorkflowService ortaya çıkan gösterir.</span><span class="sxs-lookup"><span data-stu-id="eedad-113">Indicates an OperationDescription has been inferred from WorkflowService.</span></span>  
  
## <a name="message"></a><span data-ttu-id="eedad-114">İleti</span><span class="sxs-lookup"><span data-stu-id="eedad-114">Message</span></span>  
 <span data-ttu-id="eedad-115">OperationDescription ada sahip '%1' = '%2' WorkflowService sözleşmede çıkarımı yapılan.</span><span class="sxs-lookup"><span data-stu-id="eedad-115">OperationDescription with Name='%1' in contract '%2' has been inferred from WorkflowService.</span></span> <span data-ttu-id="eedad-116">IsOneWay = %3.</span><span class="sxs-lookup"><span data-stu-id="eedad-116">IsOneWay=%3.</span></span>  
  
## <a name="details"></a><span data-ttu-id="eedad-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="eedad-117">Details</span></span>  
  
|<span data-ttu-id="eedad-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="eedad-118">Data Item Name</span></span>|<span data-ttu-id="eedad-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="eedad-119">Data Item Type</span></span>|<span data-ttu-id="eedad-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eedad-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="eedad-121">OperationName</span><span class="sxs-lookup"><span data-stu-id="eedad-121">OperationName</span></span>|<span data-ttu-id="eedad-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="eedad-122">xs:string</span></span>|<span data-ttu-id="eedad-123">İşlemin adı.</span><span class="sxs-lookup"><span data-stu-id="eedad-123">The name of the operation.</span></span>|  
|<span data-ttu-id="eedad-124">ContractName</span><span class="sxs-lookup"><span data-stu-id="eedad-124">ContractName</span></span>|<span data-ttu-id="eedad-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="eedad-125">xs:string</span></span>|<span data-ttu-id="eedad-126">Anlaşma adı.</span><span class="sxs-lookup"><span data-stu-id="eedad-126">The name of the contract.</span></span>|  
|<span data-ttu-id="eedad-127">IsOneWay</span><span class="sxs-lookup"><span data-stu-id="eedad-127">IsOneWay</span></span>|<span data-ttu-id="eedad-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="eedad-128">xs:string</span></span>|<span data-ttu-id="eedad-129">TRUE veya false değerini Sözleşme tek yönlü olup olmadığını belirten.</span><span class="sxs-lookup"><span data-stu-id="eedad-129">True or False indicating if the contract is one-way.</span></span>|  
|<span data-ttu-id="eedad-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="eedad-130">AppDomain</span></span>|<span data-ttu-id="eedad-131">xs: String</span><span class="sxs-lookup"><span data-stu-id="eedad-131">xs:string</span></span>|<span data-ttu-id="eedad-132">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="eedad-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
