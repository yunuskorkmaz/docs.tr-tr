---
description: 'Daha fazla bilgi edinin: anlaşma'
title: Anlaşma
ms.date: 03/30/2017
ms.assetid: aa00f6b3-7e1f-4213-841a-206463fca20b
ms.openlocfilehash: 3443a7d2eed1a34f07495bd3ceb98c1ba997fabf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757559"
---
# <a name="contract"></a><span data-ttu-id="18005-103">Anlaşma</span><span class="sxs-lookup"><span data-stu-id="18005-103">Contract</span></span>

<span data-ttu-id="18005-104">Anlaşma</span><span class="sxs-lookup"><span data-stu-id="18005-104">Contract</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18005-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="18005-105">Syntax</span></span>  
  
```csharp
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
  
## <a name="methods"></a><span data-ttu-id="18005-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="18005-106">Methods</span></span>  

 <span data-ttu-id="18005-107">Anlaşma sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="18005-107">The Contract class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="18005-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="18005-108">Properties</span></span>  

 <span data-ttu-id="18005-109">Sözleşme sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="18005-109">The Contract class has the following properties:</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="18005-110">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="18005-110">AppDomainId</span></span>  

 <span data-ttu-id="18005-111">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="18005-111">Data type: sint32</span></span>  
  
 <span data-ttu-id="18005-112">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="18005-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="18005-113">Sözleşmeyi barındıran AppDomain 'in AppDomain kimliği.</span><span class="sxs-lookup"><span data-stu-id="18005-113">The appdomain id of the appdomain that hosts the contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="18005-114">Davranışlar</span><span class="sxs-lookup"><span data-stu-id="18005-114">Behaviors</span></span>  

 <span data-ttu-id="18005-115">Veri türü: davranış dizisi</span><span class="sxs-lookup"><span data-stu-id="18005-115">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="18005-116">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="18005-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="18005-117">Bu sözleşmeyle ilişkilendirilen davranışlar.</span><span class="sxs-lookup"><span data-stu-id="18005-117">The behaviors associated with this contract.</span></span>  
  
### <a name="name"></a><span data-ttu-id="18005-118">Name</span><span class="sxs-lookup"><span data-stu-id="18005-118">Name</span></span>  

 <span data-ttu-id="18005-119">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="18005-119">Data type: string</span></span>  
  
 <span data-ttu-id="18005-120">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="18005-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="18005-121">WSDL 'deki sözleşmenin adı.</span><span class="sxs-lookup"><span data-stu-id="18005-121">The name of the contract in WSDL.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="18005-122">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="18005-122">Namespace</span></span>  

 <span data-ttu-id="18005-123">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="18005-123">Data type: string</span></span>  
  
 <span data-ttu-id="18005-124">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="18005-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="18005-125">`portType`WSDL içindeki öğenin ad alanı.</span><span class="sxs-lookup"><span data-stu-id="18005-125">The namespace of the `portType` element in WSDL.</span></span>  
  
### <a name="operations"></a><span data-ttu-id="18005-126">Operations</span><span class="sxs-lookup"><span data-stu-id="18005-126">Operations</span></span>  

 <span data-ttu-id="18005-127">Veri türü: Işlem dizisi</span><span class="sxs-lookup"><span data-stu-id="18005-127">Data type: Operation array</span></span>  
  
 <span data-ttu-id="18005-128">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="18005-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="18005-129">Bu sözleşmenin işlemleri.</span><span class="sxs-lookup"><span data-stu-id="18005-129">The operations of this contract.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="18005-130">Işlem</span><span class="sxs-lookup"><span data-stu-id="18005-130">ProcessId</span></span>  

 <span data-ttu-id="18005-131">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="18005-131">Data type: sint32</span></span>  
  
 <span data-ttu-id="18005-132">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="18005-132">Access type: Read-only</span></span>  
  
 <span data-ttu-id="18005-133">Sözleşmeyi barındıran işlemin işlem kimliği.</span><span class="sxs-lookup"><span data-stu-id="18005-133">The process Id of the process that hosts the contract.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="18005-134">ref</span><span class="sxs-lookup"><span data-stu-id="18005-134">ref</span></span>  

 <span data-ttu-id="18005-135">Veri türü: sözleşme</span><span class="sxs-lookup"><span data-stu-id="18005-135">Data type: Contract</span></span>  
  
 <span data-ttu-id="18005-136">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="18005-136">Access type: Read-only</span></span>  
  
 <span data-ttu-id="18005-137">Anlaşma bir çift yönlü sözleşme olduğunda geri çağırma türü.</span><span class="sxs-lookup"><span data-stu-id="18005-137">The type of callback when the contract is a duplex contract.</span></span>  
  
### <a name="sessionmode"></a><span data-ttu-id="18005-138">SessionMode</span><span class="sxs-lookup"><span data-stu-id="18005-138">SessionMode</span></span>  

 <span data-ttu-id="18005-139">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="18005-139">Data type: string</span></span>  
  
 <span data-ttu-id="18005-140">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="18005-140">Access type: Read-only</span></span>  
  
 <span data-ttu-id="18005-141">Sözleşmenin Bu sözleşmeyle ilişkili bağlamanın kanal oturumlarını kullanmasını gerektirip gerektirmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="18005-141">Indicates whether the contract requires the binding associated with this contract to use channel sessions.</span></span>  
  
### <a name="type"></a><span data-ttu-id="18005-142">Tür</span><span class="sxs-lookup"><span data-stu-id="18005-142">Type</span></span>  

 <span data-ttu-id="18005-143">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="18005-143">Data type: string</span></span>  
  
 <span data-ttu-id="18005-144">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="18005-144">Access type: Read-only</span></span>  
  
 <span data-ttu-id="18005-145">Sözleşmenin türü.</span><span class="sxs-lookup"><span data-stu-id="18005-145">The type of the contract.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18005-146">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="18005-146">Requirements</span></span>  
  
|<span data-ttu-id="18005-147">MOF</span><span class="sxs-lookup"><span data-stu-id="18005-147">MOF</span></span>|<span data-ttu-id="18005-148">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="18005-148">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="18005-149">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="18005-149">Namespace</span></span>|<span data-ttu-id="18005-150">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="18005-150">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="18005-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="18005-151">See also</span></span>

- <xref:System.ServiceModel.Description.ContractDescription>
