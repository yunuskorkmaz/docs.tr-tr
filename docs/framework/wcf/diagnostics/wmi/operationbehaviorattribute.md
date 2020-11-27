---
title: OperationBehaviorAttribute
ms.date: 03/30/2017
ms.assetid: 8c9b0755-9e83-411f-bdcb-61a586022797
ms.openlocfilehash: 76cc619aed4ba2b944a8d11dc454a40368a4068c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96269086"
---
# <a name="operationbehaviorattribute"></a><span data-ttu-id="95a9d-102">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="95a9d-102">OperationBehaviorAttribute</span></span>

<span data-ttu-id="95a9d-103">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="95a9d-103">OperationBehaviorAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95a9d-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="95a9d-104">Syntax</span></span>  
  
```csharp
class OperationBehaviorAttribute : Behavior  
{  
  boolean AutoDisposeParameters;  
  string Impersonation;  
  string ReleaseInstanceMode;  
  boolean TransactionAutoComplete;  
  boolean TransactionScopeRequired;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="95a9d-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="95a9d-105">Methods</span></span>  

 <span data-ttu-id="95a9d-106">OperationBehaviorAttribute sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="95a9d-106">The OperationBehaviorAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="95a9d-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="95a9d-107">Properties</span></span>  

 <span data-ttu-id="95a9d-108">OperationBehaviorAttribute sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="95a9d-108">The OperationBehaviorAttribute class has the following properties:</span></span>  
  
### <a name="autodisposeparameters"></a><span data-ttu-id="95a9d-109">Oto Disposeparameters</span><span class="sxs-lookup"><span data-stu-id="95a9d-109">AutoDisposeParameters</span></span>  

 <span data-ttu-id="95a9d-110">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="95a9d-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="95a9d-111">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="95a9d-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="95a9d-112">Parametrelerin otomatik atımı özelliğinin durumu.</span><span class="sxs-lookup"><span data-stu-id="95a9d-112">The state of the auto-dispose feature for parameters.</span></span>  
  
### <a name="impersonation"></a><span data-ttu-id="95a9d-113">Kimliğe bürünme</span><span class="sxs-lookup"><span data-stu-id="95a9d-113">Impersonation</span></span>  

 <span data-ttu-id="95a9d-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="95a9d-114">Data type: string</span></span>  
  
 <span data-ttu-id="95a9d-115">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="95a9d-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="95a9d-116">İşlemin desteklediği çağıran kimliğe bürünme düzeyini gösterir.</span><span class="sxs-lookup"><span data-stu-id="95a9d-116">Indicates the level of caller impersonation that the operation supports.</span></span>  
  
### <a name="releaseinstancemode"></a><span data-ttu-id="95a9d-117">ReleaseInstanceMode</span><span class="sxs-lookup"><span data-stu-id="95a9d-117">ReleaseInstanceMode</span></span>  

 <span data-ttu-id="95a9d-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="95a9d-118">Data type: string</span></span>  
  
 <span data-ttu-id="95a9d-119">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="95a9d-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="95a9d-120">Nesnenin geri dönüştürülmesinin ne zaman bir işlem çağrısı olduğu gösterilir.</span><span class="sxs-lookup"><span data-stu-id="95a9d-120">Indicates when in the course of an operation invocation to recycle the object.</span></span>  
  
### <a name="transactionautocomplete"></a><span data-ttu-id="95a9d-121">TransactionAutoComplete</span><span class="sxs-lookup"><span data-stu-id="95a9d-121">TransactionAutoComplete</span></span>  

 <span data-ttu-id="95a9d-122">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="95a9d-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="95a9d-123">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="95a9d-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="95a9d-124">İşlenmeyen özel durumlar oluşursa geçerli işlemin otomatik olarak kaydedilip edilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="95a9d-124">Indicates whether to automatically commit the current transaction if no unhandled exceptions occur.</span></span>  
  
### <a name="transactionscoperequired"></a><span data-ttu-id="95a9d-125">TransactionScopeRequired</span><span class="sxs-lookup"><span data-stu-id="95a9d-125">TransactionScopeRequired</span></span>  

 <span data-ttu-id="95a9d-126">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="95a9d-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="95a9d-127">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="95a9d-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="95a9d-128">İşlemin bir işlem gerektirip gerektirmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="95a9d-128">Indicates whether the operation requires a transaction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95a9d-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="95a9d-129">Requirements</span></span>  
  
|<span data-ttu-id="95a9d-130">MOF</span><span class="sxs-lookup"><span data-stu-id="95a9d-130">MOF</span></span>|<span data-ttu-id="95a9d-131">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="95a9d-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="95a9d-132">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="95a9d-132">Namespace</span></span>|<span data-ttu-id="95a9d-133">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="95a9d-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="95a9d-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="95a9d-134">See also</span></span>

- <xref:System.ServiceModel.OperationBehaviorAttribute>
