---
title: Sözleşme
ms.date: 03/30/2017
ms.assetid: aa00f6b3-7e1f-4213-841a-206463fca20b
ms.openlocfilehash: e4a21e95a6f1f1860ed36c968d17bb8ac8465dce
ms.sourcegitcommit: 9ee6cd851b6e176a5811ea28ed0d5935c71950f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68868439"
---
# <a name="contract"></a><span data-ttu-id="02085-102">Sözleşme</span><span class="sxs-lookup"><span data-stu-id="02085-102">Contract</span></span>
<span data-ttu-id="02085-103">Sözleşme</span><span class="sxs-lookup"><span data-stu-id="02085-103">Contract</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02085-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="02085-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="02085-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="02085-105">Methods</span></span>  
 <span data-ttu-id="02085-106">Anlaşma sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="02085-106">The Contract class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="02085-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="02085-107">Properties</span></span>  
 <span data-ttu-id="02085-108">Sözleşme sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="02085-108">The Contract class has the following properties:</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="02085-109">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="02085-109">AppDomainId</span></span>  
 <span data-ttu-id="02085-110">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="02085-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="02085-111">Erişim türü: Salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="02085-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="02085-112">Sözleşmeyi barındıran AppDomain 'in AppDomain kimliği.</span><span class="sxs-lookup"><span data-stu-id="02085-112">The appdomain id of the appdomain that hosts the contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="02085-113">Davranışlar</span><span class="sxs-lookup"><span data-stu-id="02085-113">Behaviors</span></span>  
 <span data-ttu-id="02085-114">Veri türü: Davranış dizisi</span><span class="sxs-lookup"><span data-stu-id="02085-114">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="02085-115">Erişim türü: Salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="02085-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="02085-116">Bu sözleşmeyle ilişkilendirilen davranışlar.</span><span class="sxs-lookup"><span data-stu-id="02085-116">The behaviors associated with this contract.</span></span>  
  
### <a name="name"></a><span data-ttu-id="02085-117">Ad</span><span class="sxs-lookup"><span data-stu-id="02085-117">Name</span></span>  
 <span data-ttu-id="02085-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="02085-118">Data type: string</span></span>  
  
 <span data-ttu-id="02085-119">Erişim türü: Salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="02085-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="02085-120">WSDL 'deki sözleşmenin adı.</span><span class="sxs-lookup"><span data-stu-id="02085-120">The name of the contract in WSDL.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="02085-121">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="02085-121">Namespace</span></span>  
 <span data-ttu-id="02085-122">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="02085-122">Data type: string</span></span>  
  
 <span data-ttu-id="02085-123">Erişim türü: Salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="02085-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="02085-124">WSDL içindeki `portType` öğenin ad alanı.</span><span class="sxs-lookup"><span data-stu-id="02085-124">The namespace of the `portType` element in WSDL.</span></span>  
  
### <a name="operations"></a><span data-ttu-id="02085-125">İşlemler</span><span class="sxs-lookup"><span data-stu-id="02085-125">Operations</span></span>  
 <span data-ttu-id="02085-126">Veri türü: İşlem dizisi</span><span class="sxs-lookup"><span data-stu-id="02085-126">Data type: Operation array</span></span>  
  
 <span data-ttu-id="02085-127">Erişim türü: Salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="02085-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="02085-128">Bu sözleşmenin işlemleri.</span><span class="sxs-lookup"><span data-stu-id="02085-128">The operations of this contract.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="02085-129">İşlem kimliği</span><span class="sxs-lookup"><span data-stu-id="02085-129">ProcessId</span></span>  
 <span data-ttu-id="02085-130">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="02085-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="02085-131">Erişim türü: Salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="02085-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="02085-132">Sözleşmeyi barındıran işlemin işlem kimliği.</span><span class="sxs-lookup"><span data-stu-id="02085-132">The process Id of the process that hosts the contract.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="02085-133">ref</span><span class="sxs-lookup"><span data-stu-id="02085-133">ref</span></span>  
 <span data-ttu-id="02085-134">Veri türü: Sözleşme</span><span class="sxs-lookup"><span data-stu-id="02085-134">Data type: Contract</span></span>  
  
 <span data-ttu-id="02085-135">Erişim türü: Salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="02085-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="02085-136">Anlaşma bir çift yönlü sözleşme olduğunda geri çağırma türü.</span><span class="sxs-lookup"><span data-stu-id="02085-136">The type of callback when the contract is a duplex contract.</span></span>  
  
### <a name="sessionmode"></a><span data-ttu-id="02085-137">SessionMode</span><span class="sxs-lookup"><span data-stu-id="02085-137">SessionMode</span></span>  
 <span data-ttu-id="02085-138">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="02085-138">Data type: string</span></span>  
  
 <span data-ttu-id="02085-139">Erişim türü: Salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="02085-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="02085-140">Sözleşmenin Bu sözleşmeyle ilişkili bağlamanın kanal oturumlarını kullanmasını gerektirip gerektirmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="02085-140">Indicates whether the contract requires the binding associated with this contract to use channel sessions.</span></span>  
  
### <a name="type"></a><span data-ttu-id="02085-141">Tür</span><span class="sxs-lookup"><span data-stu-id="02085-141">Type</span></span>  
 <span data-ttu-id="02085-142">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="02085-142">Data type: string</span></span>  
  
 <span data-ttu-id="02085-143">Erişim türü: Salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="02085-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="02085-144">Sözleşmenin türü.</span><span class="sxs-lookup"><span data-stu-id="02085-144">The type of the contract.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02085-145">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="02085-145">Requirements</span></span>  
  
|<span data-ttu-id="02085-146">MOF</span><span class="sxs-lookup"><span data-stu-id="02085-146">MOF</span></span>|<span data-ttu-id="02085-147">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="02085-147">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="02085-148">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="02085-148">Namespace</span></span>|<span data-ttu-id="02085-149">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="02085-149">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="02085-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="02085-150">See also</span></span>

- <xref:System.ServiceModel.Description.ContractDescription>
