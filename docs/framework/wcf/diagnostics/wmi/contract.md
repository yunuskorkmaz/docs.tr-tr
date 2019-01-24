---
title: Contract1
ms.date: 03/30/2017
ms.assetid: aa00f6b3-7e1f-4213-841a-206463fca20b
ms.openlocfilehash: c602ea2b708fced37c5b309596fe2312be21e741
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54603570"
---
# <a name="contract"></a><span data-ttu-id="9fc3e-102">Daralma</span><span class="sxs-lookup"><span data-stu-id="9fc3e-102">Contract</span></span>
<span data-ttu-id="9fc3e-103">Daralma</span><span class="sxs-lookup"><span data-stu-id="9fc3e-103">Contract</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fc3e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9fc3e-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="9fc3e-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="9fc3e-105">Methods</span></span>  
 <span data-ttu-id="9fc3e-106">Sözleşme sınıfı herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="9fc3e-106">The Contract class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="9fc3e-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="9fc3e-107">Properties</span></span>  
 <span data-ttu-id="9fc3e-108">Sözleşme sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="9fc3e-108">The Contract class has the following properties:</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="9fc3e-109">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="9fc3e-109">AppDomainId</span></span>  
 <span data-ttu-id="9fc3e-110">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="9fc3e-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="9fc3e-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="9fc3e-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9fc3e-112">Sözleşme barındıran appdomain kimliği.</span><span class="sxs-lookup"><span data-stu-id="9fc3e-112">The appdomain id of the appdomain that hosts the contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="9fc3e-113">Davranışlar</span><span class="sxs-lookup"><span data-stu-id="9fc3e-113">Behaviors</span></span>  
 <span data-ttu-id="9fc3e-114">Veri türü: Davranış dizi</span><span class="sxs-lookup"><span data-stu-id="9fc3e-114">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="9fc3e-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="9fc3e-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9fc3e-116">Bu sözleşme ile ilişkili davranışlar.</span><span class="sxs-lookup"><span data-stu-id="9fc3e-116">The behaviors associated with this contract.</span></span>  
  
### <a name="name"></a><span data-ttu-id="9fc3e-117">Ad</span><span class="sxs-lookup"><span data-stu-id="9fc3e-117">Name</span></span>  
 <span data-ttu-id="9fc3e-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="9fc3e-118">Data type: string</span></span>  
  
 <span data-ttu-id="9fc3e-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="9fc3e-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9fc3e-120">WSDL sözleşmede adı.</span><span class="sxs-lookup"><span data-stu-id="9fc3e-120">The name of the contract in WSDL.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="9fc3e-121">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="9fc3e-121">Namespace</span></span>  
 <span data-ttu-id="9fc3e-122">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="9fc3e-122">Data type: string</span></span>  
  
 <span data-ttu-id="9fc3e-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="9fc3e-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9fc3e-124">Ad alanı `portType` WSDL öğesinde.</span><span class="sxs-lookup"><span data-stu-id="9fc3e-124">The namespace of the `portType` element in WSDL.</span></span>  
  
### <a name="operations"></a><span data-ttu-id="9fc3e-125">İşlemler</span><span class="sxs-lookup"><span data-stu-id="9fc3e-125">Operations</span></span>  
 <span data-ttu-id="9fc3e-126">Veri türü: İşlem dizisi</span><span class="sxs-lookup"><span data-stu-id="9fc3e-126">Data type: Operation array</span></span>  
  
 <span data-ttu-id="9fc3e-127">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="9fc3e-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9fc3e-128">Operace tohoto kontraktu.</span><span class="sxs-lookup"><span data-stu-id="9fc3e-128">The operations of this contract.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="9fc3e-129">İşlem kimliği</span><span class="sxs-lookup"><span data-stu-id="9fc3e-129">ProcessId</span></span>  
 <span data-ttu-id="9fc3e-130">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="9fc3e-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="9fc3e-131">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="9fc3e-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9fc3e-132">İşlem anlaşması barındıran işlem kimliği.</span><span class="sxs-lookup"><span data-stu-id="9fc3e-132">The process Id of the process that hosts the contract.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="9fc3e-133">ref</span><span class="sxs-lookup"><span data-stu-id="9fc3e-133">ref</span></span>  
 <span data-ttu-id="9fc3e-134">Veri türü: Daralma</span><span class="sxs-lookup"><span data-stu-id="9fc3e-134">Data type: Contract</span></span>  
  
 <span data-ttu-id="9fc3e-135">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="9fc3e-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9fc3e-136">Sözleşme çift yönlü sözleşme olduğunda geri çağırma türü.</span><span class="sxs-lookup"><span data-stu-id="9fc3e-136">The type of callback when the contract is a duplex contract.</span></span>  
  
### <a name="sessionmode"></a><span data-ttu-id="9fc3e-137">Sessionmode'u</span><span class="sxs-lookup"><span data-stu-id="9fc3e-137">SessionMode</span></span>  
 <span data-ttu-id="9fc3e-138">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="9fc3e-138">Data type: string</span></span>  
  
 <span data-ttu-id="9fc3e-139">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="9fc3e-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9fc3e-140">Sözleşme kanal oturumları kullanmak için bu Sözleşmesi ile ilişkili bağlama gerekli olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9fc3e-140">Indicates whether the contract requires the binding associated with this contract to use channel sessions.</span></span>  
  
### <a name="type"></a><span data-ttu-id="9fc3e-141">Tür</span><span class="sxs-lookup"><span data-stu-id="9fc3e-141">Type</span></span>  
 <span data-ttu-id="9fc3e-142">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="9fc3e-142">Data type: string</span></span>  
  
 <span data-ttu-id="9fc3e-143">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="9fc3e-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9fc3e-144">Sözleşme türü.</span><span class="sxs-lookup"><span data-stu-id="9fc3e-144">The type of the contract.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fc3e-145">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9fc3e-145">Requirements</span></span>  
  
|<span data-ttu-id="9fc3e-146">MOF</span><span class="sxs-lookup"><span data-stu-id="9fc3e-146">MOF</span></span>|<span data-ttu-id="9fc3e-147">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="9fc3e-147">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="9fc3e-148">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="9fc3e-148">Namespace</span></span>|<span data-ttu-id="9fc3e-149">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="9fc3e-149">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9fc3e-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9fc3e-150">See also</span></span>
- <xref:System.ServiceModel.Description.ContractDescription>
