---
title: OperationBehaviorAttribute
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8c9b0755-9e83-411f-bdcb-61a586022797
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 63824ae2171053bee2af204e748a6fa811f2ba82
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="operationbehaviorattribute"></a><span data-ttu-id="be4c5-102">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="be4c5-102">OperationBehaviorAttribute</span></span>
<span data-ttu-id="be4c5-103">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="be4c5-103">OperationBehaviorAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be4c5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="be4c5-104">Syntax</span></span>  
  
```  
class OperationBehaviorAttribute : Behavior  
{  
  boolean AutoDisposeParameters;  
  string Impersonation;  
  string ReleaseInstanceMode;  
  boolean TransactionAutoComplete;  
  boolean TransactionScopeRequired;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="be4c5-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="be4c5-105">Methods</span></span>  
 <span data-ttu-id="be4c5-106">OperationBehaviorAttribute sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="be4c5-106">The OperationBehaviorAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="be4c5-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="be4c5-107">Properties</span></span>  
 <span data-ttu-id="be4c5-108">OperationBehaviorAttribute sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="be4c5-108">The OperationBehaviorAttribute class has the following properties:</span></span>  
  
### <a name="autodisposeparameters"></a><span data-ttu-id="be4c5-109">AutoDisposeParameters</span><span class="sxs-lookup"><span data-stu-id="be4c5-109">AutoDisposeParameters</span></span>  
 <span data-ttu-id="be4c5-110">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="be4c5-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="be4c5-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="be4c5-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="be4c5-112">Parametreler için otomatik dispose özellik durumu.</span><span class="sxs-lookup"><span data-stu-id="be4c5-112">The state of the auto-dispose feature for parameters.</span></span>  
  
### <a name="impersonation"></a><span data-ttu-id="be4c5-113">Kimliğe bürünme</span><span class="sxs-lookup"><span data-stu-id="be4c5-113">Impersonation</span></span>  
 <span data-ttu-id="be4c5-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="be4c5-114">Data type: string</span></span>  
  
 <span data-ttu-id="be4c5-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="be4c5-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="be4c5-116">İşlemin desteklediği arayan kimliğe bürünme düzeyini gösterir.</span><span class="sxs-lookup"><span data-stu-id="be4c5-116">Indicates the level of caller impersonation that the operation supports.</span></span>  
  
### <a name="releaseinstancemode"></a><span data-ttu-id="be4c5-117">OperationBehaviorAttribute üstündeki ReleaseInstanceMode</span><span class="sxs-lookup"><span data-stu-id="be4c5-117">ReleaseInstanceMode</span></span>  
 <span data-ttu-id="be4c5-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="be4c5-118">Data type: string</span></span>  
  
 <span data-ttu-id="be4c5-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="be4c5-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="be4c5-120">Nesne geri dönüştürmek için bir işlemi başlatılması sırasında gösterir.</span><span class="sxs-lookup"><span data-stu-id="be4c5-120">Indicates when in the course of an operation invocation to recycle the object.</span></span>  
  
### <a name="transactionautocomplete"></a><span data-ttu-id="be4c5-121">TransactionAutoComplete</span><span class="sxs-lookup"><span data-stu-id="be4c5-121">TransactionAutoComplete</span></span>  
 <span data-ttu-id="be4c5-122">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="be4c5-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="be4c5-123">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="be4c5-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="be4c5-124">İşlenmeyen özel durumlar oluşursa geçerli işlem otomatik olarak gerçekleştirmeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="be4c5-124">Indicates whether to automatically commit the current transaction if no unhandled exceptions occur.</span></span>  
  
### <a name="transactionscoperequired"></a><span data-ttu-id="be4c5-125">TransactionScopeRequired</span><span class="sxs-lookup"><span data-stu-id="be4c5-125">TransactionScopeRequired</span></span>  
 <span data-ttu-id="be4c5-126">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="be4c5-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="be4c5-127">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="be4c5-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="be4c5-128">İşlemi bir işlem gerekli olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="be4c5-128">Indicates whether the operation requires a transaction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be4c5-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="be4c5-129">Requirements</span></span>  
  
|<span data-ttu-id="be4c5-130">MOF</span><span class="sxs-lookup"><span data-stu-id="be4c5-130">MOF</span></span>|<span data-ttu-id="be4c5-131">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="be4c5-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="be4c5-132">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="be4c5-132">Namespace</span></span>|<span data-ttu-id="be4c5-133">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="be4c5-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="be4c5-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="be4c5-134">See Also</span></span>  
 <xref:System.ServiceModel.OperationBehaviorAttribute>
