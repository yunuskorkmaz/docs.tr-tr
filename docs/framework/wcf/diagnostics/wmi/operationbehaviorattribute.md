---
title: OperationBehaviorAttribute
ms.date: 03/30/2017
ms.assetid: 8c9b0755-9e83-411f-bdcb-61a586022797
ms.openlocfilehash: 79601308c66abe43dd5a7f72bd2a05b9d2346c2b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59975162"
---
# <a name="operationbehaviorattribute"></a><span data-ttu-id="e23df-102">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="e23df-102">OperationBehaviorAttribute</span></span>
<span data-ttu-id="e23df-103">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="e23df-103">OperationBehaviorAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e23df-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e23df-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="e23df-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e23df-105">Methods</span></span>  
 <span data-ttu-id="e23df-106">OperationBehaviorAttribute sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="e23df-106">The OperationBehaviorAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e23df-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e23df-107">Properties</span></span>  
 <span data-ttu-id="e23df-108">OperationBehaviorAttribute sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="e23df-108">The OperationBehaviorAttribute class has the following properties:</span></span>  
  
### <a name="autodisposeparameters"></a><span data-ttu-id="e23df-109">AutoDisposeParameters</span><span class="sxs-lookup"><span data-stu-id="e23df-109">AutoDisposeParameters</span></span>  
 <span data-ttu-id="e23df-110">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="e23df-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="e23df-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e23df-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e23df-112">Parametreler için dispose otomatik özellik durumu.</span><span class="sxs-lookup"><span data-stu-id="e23df-112">The state of the auto-dispose feature for parameters.</span></span>  
  
### <a name="impersonation"></a><span data-ttu-id="e23df-113">Kimliğe bürünme</span><span class="sxs-lookup"><span data-stu-id="e23df-113">Impersonation</span></span>  
 <span data-ttu-id="e23df-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="e23df-114">Data type: string</span></span>  
  
 <span data-ttu-id="e23df-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e23df-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e23df-116">Destekleyen işlemi çağıranın kimliğe bürünme düzeyini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e23df-116">Indicates the level of caller impersonation that the operation supports.</span></span>  
  
### <a name="releaseinstancemode"></a><span data-ttu-id="e23df-117">OperationBehaviorAttribute üstündeki ReleaseInstanceMode</span><span class="sxs-lookup"><span data-stu-id="e23df-117">ReleaseInstanceMode</span></span>  
 <span data-ttu-id="e23df-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="e23df-118">Data type: string</span></span>  
  
 <span data-ttu-id="e23df-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e23df-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e23df-120">Nesne geri dönüştürmek için bir işlemi başlatılması sırasında gösterir.</span><span class="sxs-lookup"><span data-stu-id="e23df-120">Indicates when in the course of an operation invocation to recycle the object.</span></span>  
  
### <a name="transactionautocomplete"></a><span data-ttu-id="e23df-121">TransactionAutoComplete</span><span class="sxs-lookup"><span data-stu-id="e23df-121">TransactionAutoComplete</span></span>  
 <span data-ttu-id="e23df-122">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="e23df-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="e23df-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e23df-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e23df-124">İşlenmeyen özel durumlar oluşursa otomatik olarak geçerli hareketi tamamlamak görüntülenip görüntülenmeyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e23df-124">Indicates whether to automatically commit the current transaction if no unhandled exceptions occur.</span></span>  
  
### <a name="transactionscoperequired"></a><span data-ttu-id="e23df-125">TransactionScopeRequired</span><span class="sxs-lookup"><span data-stu-id="e23df-125">TransactionScopeRequired</span></span>  
 <span data-ttu-id="e23df-126">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="e23df-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="e23df-127">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e23df-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e23df-128">İşlemi bir işlem gerekli olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e23df-128">Indicates whether the operation requires a transaction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e23df-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e23df-129">Requirements</span></span>  
  
|<span data-ttu-id="e23df-130">MOF</span><span class="sxs-lookup"><span data-stu-id="e23df-130">MOF</span></span>|<span data-ttu-id="e23df-131">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="e23df-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e23df-132">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="e23df-132">Namespace</span></span>|<span data-ttu-id="e23df-133">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e23df-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e23df-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e23df-134">See also</span></span>

- <xref:System.ServiceModel.OperationBehaviorAttribute>
