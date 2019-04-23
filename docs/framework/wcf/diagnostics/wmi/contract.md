---
title: Contract1
ms.date: 03/30/2017
ms.assetid: aa00f6b3-7e1f-4213-841a-206463fca20b
ms.openlocfilehash: 10789f9a2940c239ae20c8fd1e9d48bca0e820ed
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59773005"
---
# <a name="contract"></a><span data-ttu-id="e7ca1-102">Sözleşme</span><span class="sxs-lookup"><span data-stu-id="e7ca1-102">Contract</span></span>
<span data-ttu-id="e7ca1-103">Sözleşme</span><span class="sxs-lookup"><span data-stu-id="e7ca1-103">Contract</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7ca1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e7ca1-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="e7ca1-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e7ca1-105">Methods</span></span>  
 <span data-ttu-id="e7ca1-106">Sözleşme sınıfı herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="e7ca1-106">The Contract class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e7ca1-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e7ca1-107">Properties</span></span>  
 <span data-ttu-id="e7ca1-108">Sözleşme sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="e7ca1-108">The Contract class has the following properties:</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="e7ca1-109">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="e7ca1-109">AppDomainId</span></span>  
 <span data-ttu-id="e7ca1-110">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="e7ca1-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="e7ca1-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e7ca1-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e7ca1-112">Sözleşme barındıran appdomain kimliği.</span><span class="sxs-lookup"><span data-stu-id="e7ca1-112">The appdomain id of the appdomain that hosts the contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="e7ca1-113">Davranışlar</span><span class="sxs-lookup"><span data-stu-id="e7ca1-113">Behaviors</span></span>  
 <span data-ttu-id="e7ca1-114">Veri türü: Davranış dizi</span><span class="sxs-lookup"><span data-stu-id="e7ca1-114">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="e7ca1-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e7ca1-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e7ca1-116">Bu sözleşme ile ilişkili davranışlar.</span><span class="sxs-lookup"><span data-stu-id="e7ca1-116">The behaviors associated with this contract.</span></span>  
  
### <a name="name"></a><span data-ttu-id="e7ca1-117">Ad</span><span class="sxs-lookup"><span data-stu-id="e7ca1-117">Name</span></span>  
 <span data-ttu-id="e7ca1-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="e7ca1-118">Data type: string</span></span>  
  
 <span data-ttu-id="e7ca1-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e7ca1-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e7ca1-120">WSDL sözleşmede adı.</span><span class="sxs-lookup"><span data-stu-id="e7ca1-120">The name of the contract in WSDL.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="e7ca1-121">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="e7ca1-121">Namespace</span></span>  
 <span data-ttu-id="e7ca1-122">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="e7ca1-122">Data type: string</span></span>  
  
 <span data-ttu-id="e7ca1-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e7ca1-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e7ca1-124">Ad alanı `portType` WSDL öğesinde.</span><span class="sxs-lookup"><span data-stu-id="e7ca1-124">The namespace of the `portType` element in WSDL.</span></span>  
  
### <a name="operations"></a><span data-ttu-id="e7ca1-125">İşlemler</span><span class="sxs-lookup"><span data-stu-id="e7ca1-125">Operations</span></span>  
 <span data-ttu-id="e7ca1-126">Veri türü: İşlem dizisi</span><span class="sxs-lookup"><span data-stu-id="e7ca1-126">Data type: Operation array</span></span>  
  
 <span data-ttu-id="e7ca1-127">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e7ca1-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e7ca1-128">Operace tohoto kontraktu.</span><span class="sxs-lookup"><span data-stu-id="e7ca1-128">The operations of this contract.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="e7ca1-129">İşlem kimliği</span><span class="sxs-lookup"><span data-stu-id="e7ca1-129">ProcessId</span></span>  
 <span data-ttu-id="e7ca1-130">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="e7ca1-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="e7ca1-131">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e7ca1-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e7ca1-132">İşlem anlaşması barındıran işlem kimliği.</span><span class="sxs-lookup"><span data-stu-id="e7ca1-132">The process Id of the process that hosts the contract.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="e7ca1-133">ref</span><span class="sxs-lookup"><span data-stu-id="e7ca1-133">ref</span></span>  
 <span data-ttu-id="e7ca1-134">Veri türü: Sözleşme</span><span class="sxs-lookup"><span data-stu-id="e7ca1-134">Data type: Contract</span></span>  
  
 <span data-ttu-id="e7ca1-135">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e7ca1-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e7ca1-136">Sözleşme çift yönlü sözleşme olduğunda geri çağırma türü.</span><span class="sxs-lookup"><span data-stu-id="e7ca1-136">The type of callback when the contract is a duplex contract.</span></span>  
  
### <a name="sessionmode"></a><span data-ttu-id="e7ca1-137">Sessionmode'u</span><span class="sxs-lookup"><span data-stu-id="e7ca1-137">SessionMode</span></span>  
 <span data-ttu-id="e7ca1-138">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="e7ca1-138">Data type: string</span></span>  
  
 <span data-ttu-id="e7ca1-139">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e7ca1-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e7ca1-140">Sözleşme kanal oturumları kullanmak için bu Sözleşmesi ile ilişkili bağlama gerekli olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e7ca1-140">Indicates whether the contract requires the binding associated with this contract to use channel sessions.</span></span>  
  
### <a name="type"></a><span data-ttu-id="e7ca1-141">Tür</span><span class="sxs-lookup"><span data-stu-id="e7ca1-141">Type</span></span>  
 <span data-ttu-id="e7ca1-142">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="e7ca1-142">Data type: string</span></span>  
  
 <span data-ttu-id="e7ca1-143">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e7ca1-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e7ca1-144">Sözleşme türü.</span><span class="sxs-lookup"><span data-stu-id="e7ca1-144">The type of the contract.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7ca1-145">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e7ca1-145">Requirements</span></span>  
  
|<span data-ttu-id="e7ca1-146">MOF</span><span class="sxs-lookup"><span data-stu-id="e7ca1-146">MOF</span></span>|<span data-ttu-id="e7ca1-147">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="e7ca1-147">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e7ca1-148">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="e7ca1-148">Namespace</span></span>|<span data-ttu-id="e7ca1-149">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e7ca1-149">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e7ca1-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e7ca1-150">See also</span></span>

- <xref:System.ServiceModel.Description.ContractDescription>
