---
title: OperationBehaviorAttribute
ms.date: 03/30/2017
ms.assetid: 8c9b0755-9e83-411f-bdcb-61a586022797
ms.openlocfilehash: 6266713307846ab953299370835726958196fac1
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185345"
---
# <a name="operationbehaviorattribute"></a><span data-ttu-id="aa958-102">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="aa958-102">OperationBehaviorAttribute</span></span>
<span data-ttu-id="aa958-103">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="aa958-103">OperationBehaviorAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa958-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aa958-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="aa958-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="aa958-105">Methods</span></span>  
 <span data-ttu-id="aa958-106">OperationBehaviorAttribute sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="aa958-106">The OperationBehaviorAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="aa958-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="aa958-107">Properties</span></span>  
 <span data-ttu-id="aa958-108">OperationBehaviorAttribute sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="aa958-108">The OperationBehaviorAttribute class has the following properties:</span></span>  
  
### <a name="autodisposeparameters"></a><span data-ttu-id="aa958-109">AutoDisposeParameters</span><span class="sxs-lookup"><span data-stu-id="aa958-109">AutoDisposeParameters</span></span>  
 <span data-ttu-id="aa958-110">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="aa958-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="aa958-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="aa958-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aa958-112">Parametreler için dispose otomatik özellik durumu.</span><span class="sxs-lookup"><span data-stu-id="aa958-112">The state of the auto-dispose feature for parameters.</span></span>  
  
### <a name="impersonation"></a><span data-ttu-id="aa958-113">Kimliğe bürünme</span><span class="sxs-lookup"><span data-stu-id="aa958-113">Impersonation</span></span>  
 <span data-ttu-id="aa958-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="aa958-114">Data type: string</span></span>  
  
 <span data-ttu-id="aa958-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="aa958-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aa958-116">Destekleyen işlemi çağıranın kimliğe bürünme düzeyini gösterir.</span><span class="sxs-lookup"><span data-stu-id="aa958-116">Indicates the level of caller impersonation that the operation supports.</span></span>  
  
### <a name="releaseinstancemode"></a><span data-ttu-id="aa958-117">OperationBehaviorAttribute üstündeki ReleaseInstanceMode</span><span class="sxs-lookup"><span data-stu-id="aa958-117">ReleaseInstanceMode</span></span>  
 <span data-ttu-id="aa958-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="aa958-118">Data type: string</span></span>  
  
 <span data-ttu-id="aa958-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="aa958-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aa958-120">Nesne geri dönüştürmek için bir işlemi başlatılması sırasında gösterir.</span><span class="sxs-lookup"><span data-stu-id="aa958-120">Indicates when in the course of an operation invocation to recycle the object.</span></span>  
  
### <a name="transactionautocomplete"></a><span data-ttu-id="aa958-121">TransactionAutoComplete</span><span class="sxs-lookup"><span data-stu-id="aa958-121">TransactionAutoComplete</span></span>  
 <span data-ttu-id="aa958-122">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="aa958-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="aa958-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="aa958-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aa958-124">İşlenmeyen özel durumlar oluşursa otomatik olarak geçerli hareketi tamamlamak görüntülenip görüntülenmeyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="aa958-124">Indicates whether to automatically commit the current transaction if no unhandled exceptions occur.</span></span>  
  
### <a name="transactionscoperequired"></a><span data-ttu-id="aa958-125">TransactionScopeRequired</span><span class="sxs-lookup"><span data-stu-id="aa958-125">TransactionScopeRequired</span></span>  
 <span data-ttu-id="aa958-126">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="aa958-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="aa958-127">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="aa958-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aa958-128">İşlemi bir işlem gerekli olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="aa958-128">Indicates whether the operation requires a transaction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa958-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aa958-129">Requirements</span></span>  
  
|<span data-ttu-id="aa958-130">MOF</span><span class="sxs-lookup"><span data-stu-id="aa958-130">MOF</span></span>|<span data-ttu-id="aa958-131">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="aa958-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="aa958-132">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="aa958-132">Namespace</span></span>|<span data-ttu-id="aa958-133">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="aa958-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="aa958-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="aa958-134">See Also</span></span>  
 <xref:System.ServiceModel.OperationBehaviorAttribute>
