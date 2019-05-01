---
title: Contract1
ms.date: 03/30/2017
ms.assetid: aa00f6b3-7e1f-4213-841a-206463fca20b
ms.openlocfilehash: 10789f9a2940c239ae20c8fd1e9d48bca0e820ed
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61963702"
---
# <a name="contract"></a><span data-ttu-id="54d22-102">Sözleşme</span><span class="sxs-lookup"><span data-stu-id="54d22-102">Contract</span></span>
<span data-ttu-id="54d22-103">Sözleşme</span><span class="sxs-lookup"><span data-stu-id="54d22-103">Contract</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54d22-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="54d22-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="54d22-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="54d22-105">Methods</span></span>  
 <span data-ttu-id="54d22-106">Sözleşme sınıfı herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="54d22-106">The Contract class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="54d22-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="54d22-107">Properties</span></span>  
 <span data-ttu-id="54d22-108">Sözleşme sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="54d22-108">The Contract class has the following properties:</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="54d22-109">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="54d22-109">AppDomainId</span></span>  
 <span data-ttu-id="54d22-110">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="54d22-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="54d22-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="54d22-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="54d22-112">Sözleşme barındıran appdomain kimliği.</span><span class="sxs-lookup"><span data-stu-id="54d22-112">The appdomain id of the appdomain that hosts the contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="54d22-113">Davranışlar</span><span class="sxs-lookup"><span data-stu-id="54d22-113">Behaviors</span></span>  
 <span data-ttu-id="54d22-114">Veri türü: Davranış dizi</span><span class="sxs-lookup"><span data-stu-id="54d22-114">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="54d22-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="54d22-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="54d22-116">Bu sözleşme ile ilişkili davranışlar.</span><span class="sxs-lookup"><span data-stu-id="54d22-116">The behaviors associated with this contract.</span></span>  
  
### <a name="name"></a><span data-ttu-id="54d22-117">Ad</span><span class="sxs-lookup"><span data-stu-id="54d22-117">Name</span></span>  
 <span data-ttu-id="54d22-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="54d22-118">Data type: string</span></span>  
  
 <span data-ttu-id="54d22-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="54d22-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="54d22-120">WSDL sözleşmede adı.</span><span class="sxs-lookup"><span data-stu-id="54d22-120">The name of the contract in WSDL.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="54d22-121">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="54d22-121">Namespace</span></span>  
 <span data-ttu-id="54d22-122">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="54d22-122">Data type: string</span></span>  
  
 <span data-ttu-id="54d22-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="54d22-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="54d22-124">Ad alanı `portType` WSDL öğesinde.</span><span class="sxs-lookup"><span data-stu-id="54d22-124">The namespace of the `portType` element in WSDL.</span></span>  
  
### <a name="operations"></a><span data-ttu-id="54d22-125">İşlemler</span><span class="sxs-lookup"><span data-stu-id="54d22-125">Operations</span></span>  
 <span data-ttu-id="54d22-126">Veri türü: İşlem dizisi</span><span class="sxs-lookup"><span data-stu-id="54d22-126">Data type: Operation array</span></span>  
  
 <span data-ttu-id="54d22-127">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="54d22-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="54d22-128">Operace tohoto kontraktu.</span><span class="sxs-lookup"><span data-stu-id="54d22-128">The operations of this contract.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="54d22-129">İşlem kimliği</span><span class="sxs-lookup"><span data-stu-id="54d22-129">ProcessId</span></span>  
 <span data-ttu-id="54d22-130">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="54d22-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="54d22-131">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="54d22-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="54d22-132">İşlem anlaşması barındıran işlem kimliği.</span><span class="sxs-lookup"><span data-stu-id="54d22-132">The process Id of the process that hosts the contract.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="54d22-133">ref</span><span class="sxs-lookup"><span data-stu-id="54d22-133">ref</span></span>  
 <span data-ttu-id="54d22-134">Veri türü: Sözleşme</span><span class="sxs-lookup"><span data-stu-id="54d22-134">Data type: Contract</span></span>  
  
 <span data-ttu-id="54d22-135">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="54d22-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="54d22-136">Sözleşme çift yönlü sözleşme olduğunda geri çağırma türü.</span><span class="sxs-lookup"><span data-stu-id="54d22-136">The type of callback when the contract is a duplex contract.</span></span>  
  
### <a name="sessionmode"></a><span data-ttu-id="54d22-137">Sessionmode'u</span><span class="sxs-lookup"><span data-stu-id="54d22-137">SessionMode</span></span>  
 <span data-ttu-id="54d22-138">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="54d22-138">Data type: string</span></span>  
  
 <span data-ttu-id="54d22-139">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="54d22-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="54d22-140">Sözleşme kanal oturumları kullanmak için bu Sözleşmesi ile ilişkili bağlama gerekli olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="54d22-140">Indicates whether the contract requires the binding associated with this contract to use channel sessions.</span></span>  
  
### <a name="type"></a><span data-ttu-id="54d22-141">Tür</span><span class="sxs-lookup"><span data-stu-id="54d22-141">Type</span></span>  
 <span data-ttu-id="54d22-142">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="54d22-142">Data type: string</span></span>  
  
 <span data-ttu-id="54d22-143">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="54d22-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="54d22-144">Sözleşme türü.</span><span class="sxs-lookup"><span data-stu-id="54d22-144">The type of the contract.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54d22-145">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="54d22-145">Requirements</span></span>  
  
|<span data-ttu-id="54d22-146">MOF</span><span class="sxs-lookup"><span data-stu-id="54d22-146">MOF</span></span>|<span data-ttu-id="54d22-147">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="54d22-147">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="54d22-148">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="54d22-148">Namespace</span></span>|<span data-ttu-id="54d22-149">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="54d22-149">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="54d22-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="54d22-150">See also</span></span>

- <xref:System.ServiceModel.Description.ContractDescription>
