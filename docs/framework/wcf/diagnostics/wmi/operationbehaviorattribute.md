---
description: 'Şu konuda daha fazla bilgi edinin: OperationBehaviorAttribute'
title: OperationBehaviorAttribute
ms.date: 03/30/2017
ms.assetid: 8c9b0755-9e83-411f-bdcb-61a586022797
ms.openlocfilehash: c1f1b80134163ee65d5015e52017f5bb455aeac7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803067"
---
# <a name="operationbehaviorattribute"></a><span data-ttu-id="67b40-103">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="67b40-103">OperationBehaviorAttribute</span></span>

<span data-ttu-id="67b40-104">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="67b40-104">OperationBehaviorAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67b40-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="67b40-105">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="67b40-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="67b40-106">Methods</span></span>  

 <span data-ttu-id="67b40-107">OperationBehaviorAttribute sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="67b40-107">The OperationBehaviorAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="67b40-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="67b40-108">Properties</span></span>  

 <span data-ttu-id="67b40-109">OperationBehaviorAttribute sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="67b40-109">The OperationBehaviorAttribute class has the following properties:</span></span>  
  
### <a name="autodisposeparameters"></a><span data-ttu-id="67b40-110">Oto Disposeparameters</span><span class="sxs-lookup"><span data-stu-id="67b40-110">AutoDisposeParameters</span></span>  

 <span data-ttu-id="67b40-111">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="67b40-111">Data type: boolean</span></span>  
  
 <span data-ttu-id="67b40-112">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="67b40-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="67b40-113">Parametrelerin otomatik atımı özelliğinin durumu.</span><span class="sxs-lookup"><span data-stu-id="67b40-113">The state of the auto-dispose feature for parameters.</span></span>  
  
### <a name="impersonation"></a><span data-ttu-id="67b40-114">Kimliğe bürünme</span><span class="sxs-lookup"><span data-stu-id="67b40-114">Impersonation</span></span>  

 <span data-ttu-id="67b40-115">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="67b40-115">Data type: string</span></span>  
  
 <span data-ttu-id="67b40-116">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="67b40-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="67b40-117">İşlemin desteklediği çağıran kimliğe bürünme düzeyini gösterir.</span><span class="sxs-lookup"><span data-stu-id="67b40-117">Indicates the level of caller impersonation that the operation supports.</span></span>  
  
### <a name="releaseinstancemode"></a><span data-ttu-id="67b40-118">ReleaseInstanceMode</span><span class="sxs-lookup"><span data-stu-id="67b40-118">ReleaseInstanceMode</span></span>  

 <span data-ttu-id="67b40-119">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="67b40-119">Data type: string</span></span>  
  
 <span data-ttu-id="67b40-120">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="67b40-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="67b40-121">Nesnenin geri dönüştürülmesinin ne zaman bir işlem çağrısı olduğu gösterilir.</span><span class="sxs-lookup"><span data-stu-id="67b40-121">Indicates when in the course of an operation invocation to recycle the object.</span></span>  
  
### <a name="transactionautocomplete"></a><span data-ttu-id="67b40-122">TransactionAutoComplete</span><span class="sxs-lookup"><span data-stu-id="67b40-122">TransactionAutoComplete</span></span>  

 <span data-ttu-id="67b40-123">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="67b40-123">Data type: boolean</span></span>  
  
 <span data-ttu-id="67b40-124">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="67b40-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="67b40-125">İşlenmeyen özel durumlar oluşursa geçerli işlemin otomatik olarak kaydedilip edilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="67b40-125">Indicates whether to automatically commit the current transaction if no unhandled exceptions occur.</span></span>  
  
### <a name="transactionscoperequired"></a><span data-ttu-id="67b40-126">TransactionScopeRequired</span><span class="sxs-lookup"><span data-stu-id="67b40-126">TransactionScopeRequired</span></span>  

 <span data-ttu-id="67b40-127">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="67b40-127">Data type: boolean</span></span>  
  
 <span data-ttu-id="67b40-128">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="67b40-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="67b40-129">İşlemin bir işlem gerektirip gerektirmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="67b40-129">Indicates whether the operation requires a transaction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67b40-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="67b40-130">Requirements</span></span>  
  
|<span data-ttu-id="67b40-131">MOF</span><span class="sxs-lookup"><span data-stu-id="67b40-131">MOF</span></span>|<span data-ttu-id="67b40-132">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="67b40-132">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="67b40-133">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="67b40-133">Namespace</span></span>|<span data-ttu-id="67b40-134">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="67b40-134">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="67b40-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="67b40-135">See also</span></span>

- <xref:System.ServiceModel.OperationBehaviorAttribute>
