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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 044d67bc2b721451ade04947484899266d288d8c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="3502---inferredoperationdescription"></a><span data-ttu-id="f51ca-102">3502 - InferredOperationDescription</span><span class="sxs-lookup"><span data-stu-id="f51ca-102">3502 - InferredOperationDescription</span></span>
## <a name="properties"></a><span data-ttu-id="f51ca-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="f51ca-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f51ca-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="f51ca-104">ID</span></span>|<span data-ttu-id="f51ca-105">3502</span><span class="sxs-lookup"><span data-stu-id="f51ca-105">3502</span></span>|  
|<span data-ttu-id="f51ca-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="f51ca-106">Keywords</span></span>|<span data-ttu-id="f51ca-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="f51ca-107">WFServices</span></span>|  
|<span data-ttu-id="f51ca-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="f51ca-108">Level</span></span>|<span data-ttu-id="f51ca-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="f51ca-109">Information</span></span>|  
|<span data-ttu-id="f51ca-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="f51ca-110">Channel</span></span>|<span data-ttu-id="f51ca-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="f51ca-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f51ca-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f51ca-112">Description</span></span>  
 <span data-ttu-id="f51ca-113">Bir OperationDescription WorkflowService ortaya çıkan gösterir.</span><span class="sxs-lookup"><span data-stu-id="f51ca-113">Indicates an OperationDescription has been inferred from WorkflowService.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f51ca-114">İleti</span><span class="sxs-lookup"><span data-stu-id="f51ca-114">Message</span></span>  
 <span data-ttu-id="f51ca-115">OperationDescription ada sahip '%1' = '%2' WorkflowService sözleşmede çıkarımı yapılan.</span><span class="sxs-lookup"><span data-stu-id="f51ca-115">OperationDescription with Name='%1' in contract '%2' has been inferred from WorkflowService.</span></span> <span data-ttu-id="f51ca-116">IsOneWay = %3.</span><span class="sxs-lookup"><span data-stu-id="f51ca-116">IsOneWay=%3.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f51ca-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="f51ca-117">Details</span></span>  
  
|<span data-ttu-id="f51ca-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="f51ca-118">Data Item Name</span></span>|<span data-ttu-id="f51ca-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="f51ca-119">Data Item Type</span></span>|<span data-ttu-id="f51ca-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f51ca-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f51ca-121">OperationName</span><span class="sxs-lookup"><span data-stu-id="f51ca-121">OperationName</span></span>|<span data-ttu-id="f51ca-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="f51ca-122">xs:string</span></span>|<span data-ttu-id="f51ca-123">İşlemin adı.</span><span class="sxs-lookup"><span data-stu-id="f51ca-123">The name of the operation.</span></span>|  
|<span data-ttu-id="f51ca-124">ContractName</span><span class="sxs-lookup"><span data-stu-id="f51ca-124">ContractName</span></span>|<span data-ttu-id="f51ca-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="f51ca-125">xs:string</span></span>|<span data-ttu-id="f51ca-126">Anlaşma adı.</span><span class="sxs-lookup"><span data-stu-id="f51ca-126">The name of the contract.</span></span>|  
|<span data-ttu-id="f51ca-127">IsOneWay</span><span class="sxs-lookup"><span data-stu-id="f51ca-127">IsOneWay</span></span>|<span data-ttu-id="f51ca-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="f51ca-128">xs:string</span></span>|<span data-ttu-id="f51ca-129">TRUE veya false değerini Sözleşme tek yönlü olup olmadığını belirten.</span><span class="sxs-lookup"><span data-stu-id="f51ca-129">True or False indicating if the contract is one-way.</span></span>|  
|<span data-ttu-id="f51ca-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f51ca-130">AppDomain</span></span>|<span data-ttu-id="f51ca-131">xs: String</span><span class="sxs-lookup"><span data-stu-id="f51ca-131">xs:string</span></span>|<span data-ttu-id="f51ca-132">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="f51ca-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
