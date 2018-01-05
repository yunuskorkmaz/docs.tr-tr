---
title: SymmetricSecurityBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b2e182b6-c041-4d80-a926-6058068d9f79
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 7960ae9972490f2363b0f6f9942e947677c7d299
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="symmetricsecuritybindingelement"></a><span data-ttu-id="eb0f2-102">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="eb0f2-102">SymmetricSecurityBindingElement</span></span>
<span data-ttu-id="eb0f2-103">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="eb0f2-103">SymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb0f2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eb0f2-104">Syntax</span></span>  
  
```  
class SymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="eb0f2-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="eb0f2-105">Methods</span></span>  
 <span data-ttu-id="eb0f2-106">SymmetricSecurityBindingElement sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="eb0f2-106">The SymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="eb0f2-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="eb0f2-107">Properties</span></span>  
 <span data-ttu-id="eb0f2-108">SymmetricSecurityBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="eb0f2-108">The SymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="eb0f2-109">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="eb0f2-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="eb0f2-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="eb0f2-110">Data type: string</span></span>  
  
 <span data-ttu-id="eb0f2-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="eb0f2-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="eb0f2-112">İleti şifreleme ve bu bağlama için imzalama sırası.</span><span class="sxs-lookup"><span data-stu-id="eb0f2-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="eb0f2-113">RequireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="eb0f2-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="eb0f2-114">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="eb0f2-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="eb0f2-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="eb0f2-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="eb0f2-116">Olup bağlama imza onayı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="eb0f2-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb0f2-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eb0f2-117">Requirements</span></span>  
  
|<span data-ttu-id="eb0f2-118">MOF</span><span class="sxs-lookup"><span data-stu-id="eb0f2-118">MOF</span></span>|<span data-ttu-id="eb0f2-119">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="eb0f2-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="eb0f2-120">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="eb0f2-120">Namespace</span></span>|<span data-ttu-id="eb0f2-121">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="eb0f2-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="eb0f2-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="eb0f2-122">See Also</span></span>  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
