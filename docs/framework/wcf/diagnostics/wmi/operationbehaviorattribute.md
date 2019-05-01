---
title: OperationBehaviorAttribute
ms.date: 03/30/2017
ms.assetid: 8c9b0755-9e83-411f-bdcb-61a586022797
ms.openlocfilehash: 79601308c66abe43dd5a7f72bd2a05b9d2346c2b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61963053"
---
# <a name="operationbehaviorattribute"></a><span data-ttu-id="38b3f-102">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="38b3f-102">OperationBehaviorAttribute</span></span>
<span data-ttu-id="38b3f-103">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="38b3f-103">OperationBehaviorAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38b3f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="38b3f-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="38b3f-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="38b3f-105">Methods</span></span>  
 <span data-ttu-id="38b3f-106">OperationBehaviorAttribute sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="38b3f-106">The OperationBehaviorAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="38b3f-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="38b3f-107">Properties</span></span>  
 <span data-ttu-id="38b3f-108">OperationBehaviorAttribute sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="38b3f-108">The OperationBehaviorAttribute class has the following properties:</span></span>  
  
### <a name="autodisposeparameters"></a><span data-ttu-id="38b3f-109">AutoDisposeParameters</span><span class="sxs-lookup"><span data-stu-id="38b3f-109">AutoDisposeParameters</span></span>  
 <span data-ttu-id="38b3f-110">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="38b3f-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="38b3f-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="38b3f-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="38b3f-112">Parametreler için dispose otomatik özellik durumu.</span><span class="sxs-lookup"><span data-stu-id="38b3f-112">The state of the auto-dispose feature for parameters.</span></span>  
  
### <a name="impersonation"></a><span data-ttu-id="38b3f-113">Kimliğe bürünme</span><span class="sxs-lookup"><span data-stu-id="38b3f-113">Impersonation</span></span>  
 <span data-ttu-id="38b3f-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="38b3f-114">Data type: string</span></span>  
  
 <span data-ttu-id="38b3f-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="38b3f-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="38b3f-116">Destekleyen işlemi çağıranın kimliğe bürünme düzeyini gösterir.</span><span class="sxs-lookup"><span data-stu-id="38b3f-116">Indicates the level of caller impersonation that the operation supports.</span></span>  
  
### <a name="releaseinstancemode"></a><span data-ttu-id="38b3f-117">OperationBehaviorAttribute üstündeki ReleaseInstanceMode</span><span class="sxs-lookup"><span data-stu-id="38b3f-117">ReleaseInstanceMode</span></span>  
 <span data-ttu-id="38b3f-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="38b3f-118">Data type: string</span></span>  
  
 <span data-ttu-id="38b3f-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="38b3f-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="38b3f-120">Nesne geri dönüştürmek için bir işlemi başlatılması sırasında gösterir.</span><span class="sxs-lookup"><span data-stu-id="38b3f-120">Indicates when in the course of an operation invocation to recycle the object.</span></span>  
  
### <a name="transactionautocomplete"></a><span data-ttu-id="38b3f-121">TransactionAutoComplete</span><span class="sxs-lookup"><span data-stu-id="38b3f-121">TransactionAutoComplete</span></span>  
 <span data-ttu-id="38b3f-122">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="38b3f-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="38b3f-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="38b3f-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="38b3f-124">İşlenmeyen özel durumlar oluşursa otomatik olarak geçerli hareketi tamamlamak görüntülenip görüntülenmeyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="38b3f-124">Indicates whether to automatically commit the current transaction if no unhandled exceptions occur.</span></span>  
  
### <a name="transactionscoperequired"></a><span data-ttu-id="38b3f-125">TransactionScopeRequired</span><span class="sxs-lookup"><span data-stu-id="38b3f-125">TransactionScopeRequired</span></span>  
 <span data-ttu-id="38b3f-126">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="38b3f-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="38b3f-127">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="38b3f-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="38b3f-128">İşlemi bir işlem gerekli olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="38b3f-128">Indicates whether the operation requires a transaction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38b3f-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="38b3f-129">Requirements</span></span>  
  
|<span data-ttu-id="38b3f-130">MOF</span><span class="sxs-lookup"><span data-stu-id="38b3f-130">MOF</span></span>|<span data-ttu-id="38b3f-131">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="38b3f-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="38b3f-132">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="38b3f-132">Namespace</span></span>|<span data-ttu-id="38b3f-133">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="38b3f-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="38b3f-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="38b3f-134">See also</span></span>

- <xref:System.ServiceModel.OperationBehaviorAttribute>
