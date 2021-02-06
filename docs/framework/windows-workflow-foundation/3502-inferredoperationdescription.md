---
description: 'Hakkında daha fazla bilgi edinin: 3502-ınınredoperationdescription'
title: 3502 - InferredOperationDescription
ms.date: 03/30/2017
ms.assetid: 6aebb614-3c72-4537-ba11-3cc7200ef1f1
ms.openlocfilehash: 5068a3553484b38242951ef985886190f8027035
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631495"
---
# <a name="3502---inferredoperationdescription"></a><span data-ttu-id="04074-103">3502 - InferredOperationDescription</span><span class="sxs-lookup"><span data-stu-id="04074-103">3502 - InferredOperationDescription</span></span>

## <a name="properties"></a><span data-ttu-id="04074-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="04074-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="04074-105">ID</span><span class="sxs-lookup"><span data-stu-id="04074-105">ID</span></span>|<span data-ttu-id="04074-106">3502</span><span class="sxs-lookup"><span data-stu-id="04074-106">3502</span></span>|  
|<span data-ttu-id="04074-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="04074-107">Keywords</span></span>|<span data-ttu-id="04074-108">WFServices</span><span class="sxs-lookup"><span data-stu-id="04074-108">WFServices</span></span>|  
|<span data-ttu-id="04074-109">Level</span><span class="sxs-lookup"><span data-stu-id="04074-109">Level</span></span>|<span data-ttu-id="04074-110">Bilgi</span><span class="sxs-lookup"><span data-stu-id="04074-110">Information</span></span>|  
|<span data-ttu-id="04074-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="04074-111">Channel</span></span>|<span data-ttu-id="04074-112">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="04074-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="04074-113">Description</span><span class="sxs-lookup"><span data-stu-id="04074-113">Description</span></span>  

 <span data-ttu-id="04074-114">WorkflowService 'dan bir OperationDescription 'in çıkartılan olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="04074-114">Indicates an OperationDescription has been inferred from WorkflowService.</span></span>  
  
## <a name="message"></a><span data-ttu-id="04074-115">İleti</span><span class="sxs-lookup"><span data-stu-id="04074-115">Message</span></span>  

 <span data-ttu-id="04074-116">' %2 ' sözleşmesindeki Name = ' %1 ' olan OperationDescription WorkflowService 'dan çıkarsandı.</span><span class="sxs-lookup"><span data-stu-id="04074-116">OperationDescription with Name='%1' in contract '%2' has been inferred from WorkflowService.</span></span> <span data-ttu-id="04074-117">IsOneWay = %3.</span><span class="sxs-lookup"><span data-stu-id="04074-117">IsOneWay=%3.</span></span>  
  
## <a name="details"></a><span data-ttu-id="04074-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="04074-118">Details</span></span>  
  
|<span data-ttu-id="04074-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="04074-119">Data Item Name</span></span>|<span data-ttu-id="04074-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="04074-120">Data Item Type</span></span>|<span data-ttu-id="04074-121">Description</span><span class="sxs-lookup"><span data-stu-id="04074-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="04074-122">OperationName</span><span class="sxs-lookup"><span data-stu-id="04074-122">OperationName</span></span>|<span data-ttu-id="04074-123">xs: String</span><span class="sxs-lookup"><span data-stu-id="04074-123">xs:string</span></span>|<span data-ttu-id="04074-124">İşlemin adı.</span><span class="sxs-lookup"><span data-stu-id="04074-124">The name of the operation.</span></span>|  
|<span data-ttu-id="04074-125">ContractName</span><span class="sxs-lookup"><span data-stu-id="04074-125">ContractName</span></span>|<span data-ttu-id="04074-126">xs: String</span><span class="sxs-lookup"><span data-stu-id="04074-126">xs:string</span></span>|<span data-ttu-id="04074-127">Sözleşmenin adı.</span><span class="sxs-lookup"><span data-stu-id="04074-127">The name of the contract.</span></span>|  
|<span data-ttu-id="04074-128">IsOneWay</span><span class="sxs-lookup"><span data-stu-id="04074-128">IsOneWay</span></span>|<span data-ttu-id="04074-129">xs: String</span><span class="sxs-lookup"><span data-stu-id="04074-129">xs:string</span></span>|<span data-ttu-id="04074-130">Sözleşmenin tek yönlü olup olmadığını belirten doğru veya yanlış.</span><span class="sxs-lookup"><span data-stu-id="04074-130">True or False indicating if the contract is one-way.</span></span>|  
|<span data-ttu-id="04074-131">AppDomain</span><span class="sxs-lookup"><span data-stu-id="04074-131">AppDomain</span></span>|<span data-ttu-id="04074-132">xs: String</span><span class="sxs-lookup"><span data-stu-id="04074-132">xs:string</span></span>|<span data-ttu-id="04074-133">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="04074-133">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
