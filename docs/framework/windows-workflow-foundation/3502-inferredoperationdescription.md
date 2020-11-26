---
title: 3502 - InferredOperationDescription
ms.date: 03/30/2017
ms.assetid: 6aebb614-3c72-4537-ba11-3cc7200ef1f1
ms.openlocfilehash: 05278067e3f86612ee4aafbe7d5eb66dc934cb85
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242116"
---
# <a name="3502---inferredoperationdescription"></a><span data-ttu-id="70297-102">3502 - InferredOperationDescription</span><span class="sxs-lookup"><span data-stu-id="70297-102">3502 - InferredOperationDescription</span></span>

## <a name="properties"></a><span data-ttu-id="70297-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="70297-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="70297-104">ID</span><span class="sxs-lookup"><span data-stu-id="70297-104">ID</span></span>|<span data-ttu-id="70297-105">3502</span><span class="sxs-lookup"><span data-stu-id="70297-105">3502</span></span>|  
|<span data-ttu-id="70297-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="70297-106">Keywords</span></span>|<span data-ttu-id="70297-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="70297-107">WFServices</span></span>|  
|<span data-ttu-id="70297-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="70297-108">Level</span></span>|<span data-ttu-id="70297-109">Bilgi</span><span class="sxs-lookup"><span data-stu-id="70297-109">Information</span></span>|  
|<span data-ttu-id="70297-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="70297-110">Channel</span></span>|<span data-ttu-id="70297-111">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="70297-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="70297-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="70297-112">Description</span></span>  

 <span data-ttu-id="70297-113">WorkflowService 'dan bir OperationDescription 'in çıkartılan olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="70297-113">Indicates an OperationDescription has been inferred from WorkflowService.</span></span>  
  
## <a name="message"></a><span data-ttu-id="70297-114">İleti</span><span class="sxs-lookup"><span data-stu-id="70297-114">Message</span></span>  

 <span data-ttu-id="70297-115">' %2 ' sözleşmesindeki Name = ' %1 ' olan OperationDescription WorkflowService 'dan çıkarsandı.</span><span class="sxs-lookup"><span data-stu-id="70297-115">OperationDescription with Name='%1' in contract '%2' has been inferred from WorkflowService.</span></span> <span data-ttu-id="70297-116">IsOneWay = %3.</span><span class="sxs-lookup"><span data-stu-id="70297-116">IsOneWay=%3.</span></span>  
  
## <a name="details"></a><span data-ttu-id="70297-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="70297-117">Details</span></span>  
  
|<span data-ttu-id="70297-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="70297-118">Data Item Name</span></span>|<span data-ttu-id="70297-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="70297-119">Data Item Type</span></span>|<span data-ttu-id="70297-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="70297-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="70297-121">OperationName</span><span class="sxs-lookup"><span data-stu-id="70297-121">OperationName</span></span>|<span data-ttu-id="70297-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="70297-122">xs:string</span></span>|<span data-ttu-id="70297-123">İşlemin adı.</span><span class="sxs-lookup"><span data-stu-id="70297-123">The name of the operation.</span></span>|  
|<span data-ttu-id="70297-124">ContractName</span><span class="sxs-lookup"><span data-stu-id="70297-124">ContractName</span></span>|<span data-ttu-id="70297-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="70297-125">xs:string</span></span>|<span data-ttu-id="70297-126">Sözleşmenin adı.</span><span class="sxs-lookup"><span data-stu-id="70297-126">The name of the contract.</span></span>|  
|<span data-ttu-id="70297-127">IsOneWay</span><span class="sxs-lookup"><span data-stu-id="70297-127">IsOneWay</span></span>|<span data-ttu-id="70297-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="70297-128">xs:string</span></span>|<span data-ttu-id="70297-129">Sözleşmenin tek yönlü olup olmadığını belirten doğru veya yanlış.</span><span class="sxs-lookup"><span data-stu-id="70297-129">True or False indicating if the contract is one-way.</span></span>|  
|<span data-ttu-id="70297-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="70297-130">AppDomain</span></span>|<span data-ttu-id="70297-131">xs: String</span><span class="sxs-lookup"><span data-stu-id="70297-131">xs:string</span></span>|<span data-ttu-id="70297-132">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="70297-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
