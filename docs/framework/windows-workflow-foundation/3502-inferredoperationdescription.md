---
title: 3502 - InferredOperationDescription
ms.date: 03/30/2017
ms.assetid: 6aebb614-3c72-4537-ba11-3cc7200ef1f1
ms.openlocfilehash: 752cd73066c3c15ecbb36c40c417ee84b3fcf184
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512011"
---
# <a name="3502---inferredoperationdescription"></a><span data-ttu-id="4b571-102">3502 - InferredOperationDescription</span><span class="sxs-lookup"><span data-stu-id="4b571-102">3502 - InferredOperationDescription</span></span>
## <a name="properties"></a><span data-ttu-id="4b571-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="4b571-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4b571-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="4b571-104">ID</span></span>|<span data-ttu-id="4b571-105">3502</span><span class="sxs-lookup"><span data-stu-id="4b571-105">3502</span></span>|  
|<span data-ttu-id="4b571-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="4b571-106">Keywords</span></span>|<span data-ttu-id="4b571-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="4b571-107">WFServices</span></span>|  
|<span data-ttu-id="4b571-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="4b571-108">Level</span></span>|<span data-ttu-id="4b571-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="4b571-109">Information</span></span>|  
|<span data-ttu-id="4b571-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="4b571-110">Channel</span></span>|<span data-ttu-id="4b571-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="4b571-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4b571-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4b571-112">Description</span></span>  
 <span data-ttu-id="4b571-113">Bir OperationDescription WorkflowService ortaya çıkan gösterir.</span><span class="sxs-lookup"><span data-stu-id="4b571-113">Indicates an OperationDescription has been inferred from WorkflowService.</span></span>  
  
## <a name="message"></a><span data-ttu-id="4b571-114">İleti</span><span class="sxs-lookup"><span data-stu-id="4b571-114">Message</span></span>  
 <span data-ttu-id="4b571-115">OperationDescription ada sahip '%1' = '%2' WorkflowService sözleşmede çıkarımı yapılan.</span><span class="sxs-lookup"><span data-stu-id="4b571-115">OperationDescription with Name='%1' in contract '%2' has been inferred from WorkflowService.</span></span> <span data-ttu-id="4b571-116">IsOneWay = %3.</span><span class="sxs-lookup"><span data-stu-id="4b571-116">IsOneWay=%3.</span></span>  
  
## <a name="details"></a><span data-ttu-id="4b571-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="4b571-117">Details</span></span>  
  
|<span data-ttu-id="4b571-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="4b571-118">Data Item Name</span></span>|<span data-ttu-id="4b571-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="4b571-119">Data Item Type</span></span>|<span data-ttu-id="4b571-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4b571-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4b571-121">OperationName</span><span class="sxs-lookup"><span data-stu-id="4b571-121">OperationName</span></span>|<span data-ttu-id="4b571-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="4b571-122">xs:string</span></span>|<span data-ttu-id="4b571-123">İşlemin adı.</span><span class="sxs-lookup"><span data-stu-id="4b571-123">The name of the operation.</span></span>|  
|<span data-ttu-id="4b571-124">ContractName</span><span class="sxs-lookup"><span data-stu-id="4b571-124">ContractName</span></span>|<span data-ttu-id="4b571-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="4b571-125">xs:string</span></span>|<span data-ttu-id="4b571-126">Anlaşma adı.</span><span class="sxs-lookup"><span data-stu-id="4b571-126">The name of the contract.</span></span>|  
|<span data-ttu-id="4b571-127">IsOneWay</span><span class="sxs-lookup"><span data-stu-id="4b571-127">IsOneWay</span></span>|<span data-ttu-id="4b571-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="4b571-128">xs:string</span></span>|<span data-ttu-id="4b571-129">TRUE veya false değerini Sözleşme tek yönlü olup olmadığını belirten.</span><span class="sxs-lookup"><span data-stu-id="4b571-129">True or False indicating if the contract is one-way.</span></span>|  
|<span data-ttu-id="4b571-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="4b571-130">AppDomain</span></span>|<span data-ttu-id="4b571-131">xs: String</span><span class="sxs-lookup"><span data-stu-id="4b571-131">xs:string</span></span>|<span data-ttu-id="4b571-132">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="4b571-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
