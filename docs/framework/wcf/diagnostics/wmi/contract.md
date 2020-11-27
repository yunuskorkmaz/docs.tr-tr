---
title: Anlaşma
ms.date: 03/30/2017
ms.assetid: aa00f6b3-7e1f-4213-841a-206463fca20b
ms.openlocfilehash: 0df39bbd0b273f1e898ccbe585be288cc245b7f5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96274146"
---
# <a name="contract"></a><span data-ttu-id="6a748-102">Anlaşma</span><span class="sxs-lookup"><span data-stu-id="6a748-102">Contract</span></span>

<span data-ttu-id="6a748-103">Anlaşma</span><span class="sxs-lookup"><span data-stu-id="6a748-103">Contract</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a748-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="6a748-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="6a748-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6a748-105">Methods</span></span>  

 <span data-ttu-id="6a748-106">Anlaşma sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="6a748-106">The Contract class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="6a748-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="6a748-107">Properties</span></span>  

 <span data-ttu-id="6a748-108">Sözleşme sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="6a748-108">The Contract class has the following properties:</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="6a748-109">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="6a748-109">AppDomainId</span></span>  

 <span data-ttu-id="6a748-110">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="6a748-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="6a748-111">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="6a748-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6a748-112">Sözleşmeyi barındıran AppDomain 'in AppDomain kimliği.</span><span class="sxs-lookup"><span data-stu-id="6a748-112">The appdomain id of the appdomain that hosts the contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="6a748-113">Davranışlar</span><span class="sxs-lookup"><span data-stu-id="6a748-113">Behaviors</span></span>  

 <span data-ttu-id="6a748-114">Veri türü: davranış dizisi</span><span class="sxs-lookup"><span data-stu-id="6a748-114">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="6a748-115">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="6a748-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6a748-116">Bu sözleşmeyle ilişkilendirilen davranışlar.</span><span class="sxs-lookup"><span data-stu-id="6a748-116">The behaviors associated with this contract.</span></span>  
  
### <a name="name"></a><span data-ttu-id="6a748-117">Adı</span><span class="sxs-lookup"><span data-stu-id="6a748-117">Name</span></span>  

 <span data-ttu-id="6a748-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="6a748-118">Data type: string</span></span>  
  
 <span data-ttu-id="6a748-119">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="6a748-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6a748-120">WSDL 'deki sözleşmenin adı.</span><span class="sxs-lookup"><span data-stu-id="6a748-120">The name of the contract in WSDL.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="6a748-121">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="6a748-121">Namespace</span></span>  

 <span data-ttu-id="6a748-122">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="6a748-122">Data type: string</span></span>  
  
 <span data-ttu-id="6a748-123">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="6a748-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6a748-124">`portType`WSDL içindeki öğenin ad alanı.</span><span class="sxs-lookup"><span data-stu-id="6a748-124">The namespace of the `portType` element in WSDL.</span></span>  
  
### <a name="operations"></a><span data-ttu-id="6a748-125">İşlemler</span><span class="sxs-lookup"><span data-stu-id="6a748-125">Operations</span></span>  

 <span data-ttu-id="6a748-126">Veri türü: Işlem dizisi</span><span class="sxs-lookup"><span data-stu-id="6a748-126">Data type: Operation array</span></span>  
  
 <span data-ttu-id="6a748-127">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="6a748-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6a748-128">Bu sözleşmenin işlemleri.</span><span class="sxs-lookup"><span data-stu-id="6a748-128">The operations of this contract.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="6a748-129">Işlem</span><span class="sxs-lookup"><span data-stu-id="6a748-129">ProcessId</span></span>  

 <span data-ttu-id="6a748-130">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="6a748-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="6a748-131">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="6a748-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6a748-132">Sözleşmeyi barındıran işlemin işlem kimliği.</span><span class="sxs-lookup"><span data-stu-id="6a748-132">The process Id of the process that hosts the contract.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="6a748-133">ref</span><span class="sxs-lookup"><span data-stu-id="6a748-133">ref</span></span>  

 <span data-ttu-id="6a748-134">Veri türü: sözleşme</span><span class="sxs-lookup"><span data-stu-id="6a748-134">Data type: Contract</span></span>  
  
 <span data-ttu-id="6a748-135">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="6a748-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6a748-136">Anlaşma bir çift yönlü sözleşme olduğunda geri çağırma türü.</span><span class="sxs-lookup"><span data-stu-id="6a748-136">The type of callback when the contract is a duplex contract.</span></span>  
  
### <a name="sessionmode"></a><span data-ttu-id="6a748-137">SessionMode</span><span class="sxs-lookup"><span data-stu-id="6a748-137">SessionMode</span></span>  

 <span data-ttu-id="6a748-138">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="6a748-138">Data type: string</span></span>  
  
 <span data-ttu-id="6a748-139">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="6a748-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6a748-140">Sözleşmenin Bu sözleşmeyle ilişkili bağlamanın kanal oturumlarını kullanmasını gerektirip gerektirmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6a748-140">Indicates whether the contract requires the binding associated with this contract to use channel sessions.</span></span>  
  
### <a name="type"></a><span data-ttu-id="6a748-141">Tür</span><span class="sxs-lookup"><span data-stu-id="6a748-141">Type</span></span>  

 <span data-ttu-id="6a748-142">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="6a748-142">Data type: string</span></span>  
  
 <span data-ttu-id="6a748-143">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="6a748-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6a748-144">Sözleşmenin türü.</span><span class="sxs-lookup"><span data-stu-id="6a748-144">The type of the contract.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a748-145">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6a748-145">Requirements</span></span>  
  
|<span data-ttu-id="6a748-146">MOF</span><span class="sxs-lookup"><span data-stu-id="6a748-146">MOF</span></span>|<span data-ttu-id="6a748-147">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6a748-147">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="6a748-148">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="6a748-148">Namespace</span></span>|<span data-ttu-id="6a748-149">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="6a748-149">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6a748-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a748-150">See also</span></span>

- <xref:System.ServiceModel.Description.ContractDescription>
