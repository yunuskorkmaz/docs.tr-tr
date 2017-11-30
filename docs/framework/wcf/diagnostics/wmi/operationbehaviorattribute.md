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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: fd01c5c4d37f5c0ec5673dc9aa4a47cb8affbc29
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="operationbehaviorattribute"></a><span data-ttu-id="cab7a-102">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="cab7a-102">OperationBehaviorAttribute</span></span>
<span data-ttu-id="cab7a-103">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="cab7a-103">OperationBehaviorAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cab7a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cab7a-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="cab7a-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="cab7a-105">Methods</span></span>  
 <span data-ttu-id="cab7a-106">OperationBehaviorAttribute sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="cab7a-106">The OperationBehaviorAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="cab7a-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="cab7a-107">Properties</span></span>  
 <span data-ttu-id="cab7a-108">OperationBehaviorAttribute sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="cab7a-108">The OperationBehaviorAttribute class has the following properties:</span></span>  
  
### <a name="autodisposeparameters"></a><span data-ttu-id="cab7a-109">AutoDisposeParameters</span><span class="sxs-lookup"><span data-stu-id="cab7a-109">AutoDisposeParameters</span></span>  
 <span data-ttu-id="cab7a-110">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="cab7a-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="cab7a-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="cab7a-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cab7a-112">Parametreler için otomatik dispose özellik durumu.</span><span class="sxs-lookup"><span data-stu-id="cab7a-112">The state of the auto-dispose feature for parameters.</span></span>  
  
### <a name="impersonation"></a><span data-ttu-id="cab7a-113">Kimliğe bürünme</span><span class="sxs-lookup"><span data-stu-id="cab7a-113">Impersonation</span></span>  
 <span data-ttu-id="cab7a-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="cab7a-114">Data type: string</span></span>  
  
 <span data-ttu-id="cab7a-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="cab7a-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cab7a-116">İşlemin desteklediği arayan kimliğe bürünme düzeyini gösterir.</span><span class="sxs-lookup"><span data-stu-id="cab7a-116">Indicates the level of caller impersonation that the operation supports.</span></span>  
  
### <a name="releaseinstancemode"></a><span data-ttu-id="cab7a-117">OperationBehaviorAttribute üstündeki ReleaseInstanceMode</span><span class="sxs-lookup"><span data-stu-id="cab7a-117">ReleaseInstanceMode</span></span>  
 <span data-ttu-id="cab7a-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="cab7a-118">Data type: string</span></span>  
  
 <span data-ttu-id="cab7a-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="cab7a-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cab7a-120">Nesne geri dönüştürmek için bir işlemi başlatılması sırasında gösterir.</span><span class="sxs-lookup"><span data-stu-id="cab7a-120">Indicates when in the course of an operation invocation to recycle the object.</span></span>  
  
### <a name="transactionautocomplete"></a><span data-ttu-id="cab7a-121">TransactionAutoComplete</span><span class="sxs-lookup"><span data-stu-id="cab7a-121">TransactionAutoComplete</span></span>  
 <span data-ttu-id="cab7a-122">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="cab7a-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="cab7a-123">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="cab7a-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cab7a-124">İşlenmeyen özel durumlar oluşursa geçerli işlem otomatik olarak gerçekleştirmeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="cab7a-124">Indicates whether to automatically commit the current transaction if no unhandled exceptions occur.</span></span>  
  
### <a name="transactionscoperequired"></a><span data-ttu-id="cab7a-125">TransactionScopeRequired</span><span class="sxs-lookup"><span data-stu-id="cab7a-125">TransactionScopeRequired</span></span>  
 <span data-ttu-id="cab7a-126">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="cab7a-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="cab7a-127">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="cab7a-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cab7a-128">İşlemi bir işlem gerekli olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="cab7a-128">Indicates whether the operation requires a transaction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cab7a-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cab7a-129">Requirements</span></span>  
  
|<span data-ttu-id="cab7a-130">MOF</span><span class="sxs-lookup"><span data-stu-id="cab7a-130">MOF</span></span>|<span data-ttu-id="cab7a-131">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="cab7a-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="cab7a-132">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="cab7a-132">Namespace</span></span>|<span data-ttu-id="cab7a-133">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="cab7a-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cab7a-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cab7a-134">See Also</span></span>  
 <xref:System.ServiceModel.OperationBehaviorAttribute>
