---
title: 3502 - InferredOperationDescription
ms.date: 03/30/2017
ms.assetid: 6aebb614-3c72-4537-ba11-3cc7200ef1f1
ms.openlocfilehash: 752cd73066c3c15ecbb36c40c417ee84b3fcf184
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61756097"
---
# <a name="3502---inferredoperationdescription"></a><span data-ttu-id="87c7c-102">3502 - InferredOperationDescription</span><span class="sxs-lookup"><span data-stu-id="87c7c-102">3502 - InferredOperationDescription</span></span>
## <a name="properties"></a><span data-ttu-id="87c7c-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="87c7c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="87c7c-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="87c7c-104">ID</span></span>|<span data-ttu-id="87c7c-105">3502</span><span class="sxs-lookup"><span data-stu-id="87c7c-105">3502</span></span>|  
|<span data-ttu-id="87c7c-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="87c7c-106">Keywords</span></span>|<span data-ttu-id="87c7c-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="87c7c-107">WFServices</span></span>|  
|<span data-ttu-id="87c7c-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="87c7c-108">Level</span></span>|<span data-ttu-id="87c7c-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="87c7c-109">Information</span></span>|  
|<span data-ttu-id="87c7c-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="87c7c-110">Channel</span></span>|<span data-ttu-id="87c7c-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="87c7c-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="87c7c-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="87c7c-112">Description</span></span>  
 <span data-ttu-id="87c7c-113">Bir OperationDescription WorkflowService ortaya çıkan gösterir.</span><span class="sxs-lookup"><span data-stu-id="87c7c-113">Indicates an OperationDescription has been inferred from WorkflowService.</span></span>  
  
## <a name="message"></a><span data-ttu-id="87c7c-114">İleti</span><span class="sxs-lookup"><span data-stu-id="87c7c-114">Message</span></span>  
 <span data-ttu-id="87c7c-115">Adlı OperationDescription '%1' = '%2' WorkflowService sözleşmede ortaya çıkan.</span><span class="sxs-lookup"><span data-stu-id="87c7c-115">OperationDescription with Name='%1' in contract '%2' has been inferred from WorkflowService.</span></span> <span data-ttu-id="87c7c-116">IsOneWay = %3.</span><span class="sxs-lookup"><span data-stu-id="87c7c-116">IsOneWay=%3.</span></span>  
  
## <a name="details"></a><span data-ttu-id="87c7c-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="87c7c-117">Details</span></span>  
  
|<span data-ttu-id="87c7c-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="87c7c-118">Data Item Name</span></span>|<span data-ttu-id="87c7c-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="87c7c-119">Data Item Type</span></span>|<span data-ttu-id="87c7c-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="87c7c-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="87c7c-121">OperationName</span><span class="sxs-lookup"><span data-stu-id="87c7c-121">OperationName</span></span>|<span data-ttu-id="87c7c-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="87c7c-122">xs:string</span></span>|<span data-ttu-id="87c7c-123">İşlemin adı.</span><span class="sxs-lookup"><span data-stu-id="87c7c-123">The name of the operation.</span></span>|  
|<span data-ttu-id="87c7c-124">ContractName</span><span class="sxs-lookup"><span data-stu-id="87c7c-124">ContractName</span></span>|<span data-ttu-id="87c7c-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="87c7c-125">xs:string</span></span>|<span data-ttu-id="87c7c-126">Sözleşme adı.</span><span class="sxs-lookup"><span data-stu-id="87c7c-126">The name of the contract.</span></span>|  
|<span data-ttu-id="87c7c-127">IsOneWay</span><span class="sxs-lookup"><span data-stu-id="87c7c-127">IsOneWay</span></span>|<span data-ttu-id="87c7c-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="87c7c-128">xs:string</span></span>|<span data-ttu-id="87c7c-129">TRUE veya false değerini tek yönlü sözleşme olup olmadığını belirten.</span><span class="sxs-lookup"><span data-stu-id="87c7c-129">True or False indicating if the contract is one-way.</span></span>|  
|<span data-ttu-id="87c7c-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="87c7c-130">AppDomain</span></span>|<span data-ttu-id="87c7c-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="87c7c-131">xs:string</span></span>|<span data-ttu-id="87c7c-132">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="87c7c-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
