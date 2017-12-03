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
ms.openlocfilehash: da0bc2ac9a4283ec9b23a1d4767f664de071ef47
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="operationbehaviorattribute"></a><span data-ttu-id="8bb47-102">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="8bb47-102">OperationBehaviorAttribute</span></span>
<span data-ttu-id="8bb47-103">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="8bb47-103">OperationBehaviorAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bb47-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8bb47-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="8bb47-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8bb47-105">Methods</span></span>  
 <span data-ttu-id="8bb47-106">OperationBehaviorAttribute sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="8bb47-106">The OperationBehaviorAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="8bb47-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="8bb47-107">Properties</span></span>  
 <span data-ttu-id="8bb47-108">OperationBehaviorAttribute sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="8bb47-108">The OperationBehaviorAttribute class has the following properties:</span></span>  
  
### <a name="autodisposeparameters"></a><span data-ttu-id="8bb47-109">AutoDisposeParameters</span><span class="sxs-lookup"><span data-stu-id="8bb47-109">AutoDisposeParameters</span></span>  
 <span data-ttu-id="8bb47-110">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="8bb47-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="8bb47-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="8bb47-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8bb47-112">Parametreler için otomatik dispose özellik durumu.</span><span class="sxs-lookup"><span data-stu-id="8bb47-112">The state of the auto-dispose feature for parameters.</span></span>  
  
### <a name="impersonation"></a><span data-ttu-id="8bb47-113">Kimliğe bürünme</span><span class="sxs-lookup"><span data-stu-id="8bb47-113">Impersonation</span></span>  
 <span data-ttu-id="8bb47-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="8bb47-114">Data type: string</span></span>  
  
 <span data-ttu-id="8bb47-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="8bb47-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8bb47-116">İşlemin desteklediği arayan kimliğe bürünme düzeyini gösterir.</span><span class="sxs-lookup"><span data-stu-id="8bb47-116">Indicates the level of caller impersonation that the operation supports.</span></span>  
  
### <a name="releaseinstancemode"></a><span data-ttu-id="8bb47-117">OperationBehaviorAttribute üstündeki ReleaseInstanceMode</span><span class="sxs-lookup"><span data-stu-id="8bb47-117">ReleaseInstanceMode</span></span>  
 <span data-ttu-id="8bb47-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="8bb47-118">Data type: string</span></span>  
  
 <span data-ttu-id="8bb47-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="8bb47-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8bb47-120">Nesne geri dönüştürmek için bir işlemi başlatılması sırasında gösterir.</span><span class="sxs-lookup"><span data-stu-id="8bb47-120">Indicates when in the course of an operation invocation to recycle the object.</span></span>  
  
### <a name="transactionautocomplete"></a><span data-ttu-id="8bb47-121">TransactionAutoComplete</span><span class="sxs-lookup"><span data-stu-id="8bb47-121">TransactionAutoComplete</span></span>  
 <span data-ttu-id="8bb47-122">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="8bb47-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="8bb47-123">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="8bb47-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8bb47-124">İşlenmeyen özel durumlar oluşursa geçerli işlem otomatik olarak gerçekleştirmeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="8bb47-124">Indicates whether to automatically commit the current transaction if no unhandled exceptions occur.</span></span>  
  
### <a name="transactionscoperequired"></a><span data-ttu-id="8bb47-125">TransactionScopeRequired</span><span class="sxs-lookup"><span data-stu-id="8bb47-125">TransactionScopeRequired</span></span>  
 <span data-ttu-id="8bb47-126">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="8bb47-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="8bb47-127">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="8bb47-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8bb47-128">İşlemi bir işlem gerekli olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8bb47-128">Indicates whether the operation requires a transaction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8bb47-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8bb47-129">Requirements</span></span>  
  
|<span data-ttu-id="8bb47-130">MOF</span><span class="sxs-lookup"><span data-stu-id="8bb47-130">MOF</span></span>|<span data-ttu-id="8bb47-131">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="8bb47-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="8bb47-132">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="8bb47-132">Namespace</span></span>|<span data-ttu-id="8bb47-133">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="8bb47-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8bb47-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8bb47-134">See Also</span></span>  
 <xref:System.ServiceModel.OperationBehaviorAttribute>
