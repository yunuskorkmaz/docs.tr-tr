---
title: Contract1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa00f6b3-7e1f-4213-841a-206463fca20b
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 04a5cb87b9ed61fd278ce0f2e05e5f1c954de5b7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="contract"></a><span data-ttu-id="03bd7-102">Daralma</span><span class="sxs-lookup"><span data-stu-id="03bd7-102">Contract</span></span>
<span data-ttu-id="03bd7-103">Daralma</span><span class="sxs-lookup"><span data-stu-id="03bd7-103">Contract</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03bd7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="03bd7-104">Syntax</span></span>  
  
```  
class Contract  
{  
  sint32 AppDomainId;  
  Behavior Behaviors[];  
  string Name;  
  string Namespace;  
  Operation Operations[];  
  sint32 ProcessId;  
  Contract ref;  
  string SessionMode;  
  string Type;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="03bd7-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="03bd7-105">Methods</span></span>  
 <span data-ttu-id="03bd7-106">Sözleşme sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="03bd7-106">The Contract class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="03bd7-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="03bd7-107">Properties</span></span>  
 <span data-ttu-id="03bd7-108">Sözleşme sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="03bd7-108">The Contract class has the following properties:</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="03bd7-109">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="03bd7-109">AppDomainId</span></span>  
 <span data-ttu-id="03bd7-110">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="03bd7-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="03bd7-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="03bd7-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="03bd7-112">Sözleşme barındıran appdomain kimliği.</span><span class="sxs-lookup"><span data-stu-id="03bd7-112">The appdomain id of the appdomain that hosts the contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="03bd7-113">Davranışlar</span><span class="sxs-lookup"><span data-stu-id="03bd7-113">Behaviors</span></span>  
 <span data-ttu-id="03bd7-114">Veri türü: davranış dizisi</span><span class="sxs-lookup"><span data-stu-id="03bd7-114">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="03bd7-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="03bd7-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="03bd7-116">Bu sözleşme ile ilişkilendirilen davranışlar.</span><span class="sxs-lookup"><span data-stu-id="03bd7-116">The behaviors associated with this contract.</span></span>  
  
### <a name="name"></a><span data-ttu-id="03bd7-117">Ad</span><span class="sxs-lookup"><span data-stu-id="03bd7-117">Name</span></span>  
 <span data-ttu-id="03bd7-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="03bd7-118">Data type: string</span></span>  
  
 <span data-ttu-id="03bd7-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="03bd7-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="03bd7-120">WSDL içindeki sözleşme adı.</span><span class="sxs-lookup"><span data-stu-id="03bd7-120">The name of the contract in WSDL.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="03bd7-121">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="03bd7-121">Namespace</span></span>  
 <span data-ttu-id="03bd7-122">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="03bd7-122">Data type: string</span></span>  
  
 <span data-ttu-id="03bd7-123">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="03bd7-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="03bd7-124">Ad alanı `portType` WSDL öğesinde.</span><span class="sxs-lookup"><span data-stu-id="03bd7-124">The namespace of the `portType` element in WSDL.</span></span>  
  
### <a name="operations"></a><span data-ttu-id="03bd7-125">İşlemler</span><span class="sxs-lookup"><span data-stu-id="03bd7-125">Operations</span></span>  
 <span data-ttu-id="03bd7-126">Veri türü: işlem dizisi</span><span class="sxs-lookup"><span data-stu-id="03bd7-126">Data type: Operation array</span></span>  
  
 <span data-ttu-id="03bd7-127">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="03bd7-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="03bd7-128">Bu sözleşme işlemleri.</span><span class="sxs-lookup"><span data-stu-id="03bd7-128">The operations of this contract.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="03bd7-129">İşlem kimliği</span><span class="sxs-lookup"><span data-stu-id="03bd7-129">ProcessId</span></span>  
 <span data-ttu-id="03bd7-130">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="03bd7-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="03bd7-131">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="03bd7-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="03bd7-132">İşlemin işlem kimliği Sözleşmeyi barındıran.</span><span class="sxs-lookup"><span data-stu-id="03bd7-132">The process Id of the process that hosts the contract.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="03bd7-133">ref</span><span class="sxs-lookup"><span data-stu-id="03bd7-133">ref</span></span>  
 <span data-ttu-id="03bd7-134">Veri türü: Sözleşme</span><span class="sxs-lookup"><span data-stu-id="03bd7-134">Data type: Contract</span></span>  
  
 <span data-ttu-id="03bd7-135">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="03bd7-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="03bd7-136">Sözleşme çift yönlü sözleşme olduğunda geri çağırma türü.</span><span class="sxs-lookup"><span data-stu-id="03bd7-136">The type of callback when the contract is a duplex contract.</span></span>  
  
### <a name="sessionmode"></a><span data-ttu-id="03bd7-137">SessionMode</span><span class="sxs-lookup"><span data-stu-id="03bd7-137">SessionMode</span></span>  
 <span data-ttu-id="03bd7-138">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="03bd7-138">Data type: string</span></span>  
  
 <span data-ttu-id="03bd7-139">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="03bd7-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="03bd7-140">Sözleşme kanal oturumları kullanmak için bu sözleşmeyle ilişkili bağlama gerekli olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="03bd7-140">Indicates whether the contract requires the binding associated with this contract to use channel sessions.</span></span>  
  
### <a name="type"></a><span data-ttu-id="03bd7-141">Tür</span><span class="sxs-lookup"><span data-stu-id="03bd7-141">Type</span></span>  
 <span data-ttu-id="03bd7-142">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="03bd7-142">Data type: string</span></span>  
  
 <span data-ttu-id="03bd7-143">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="03bd7-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="03bd7-144">Sözleşme türü.</span><span class="sxs-lookup"><span data-stu-id="03bd7-144">The type of the contract.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03bd7-145">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="03bd7-145">Requirements</span></span>  
  
|<span data-ttu-id="03bd7-146">MOF</span><span class="sxs-lookup"><span data-stu-id="03bd7-146">MOF</span></span>|<span data-ttu-id="03bd7-147">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="03bd7-147">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="03bd7-148">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="03bd7-148">Namespace</span></span>|<span data-ttu-id="03bd7-149">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="03bd7-149">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="03bd7-150">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="03bd7-150">See Also</span></span>  
 <xref:System.ServiceModel.Description.ContractDescription>
