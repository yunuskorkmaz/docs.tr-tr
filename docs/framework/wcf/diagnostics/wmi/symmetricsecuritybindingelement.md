---
title: SymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: b2e182b6-c041-4d80-a926-6058068d9f79
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 7fc720f4f0be25a0cec25d979942af8472efa4ee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485062"
---
# <a name="symmetricsecuritybindingelement"></a><span data-ttu-id="11cce-102">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="11cce-102">SymmetricSecurityBindingElement</span></span>
<span data-ttu-id="11cce-103">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="11cce-103">SymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11cce-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="11cce-104">Syntax</span></span>  
  
```  
class SymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="11cce-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="11cce-105">Methods</span></span>  
 <span data-ttu-id="11cce-106">SymmetricSecurityBindingElement sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="11cce-106">The SymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="11cce-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="11cce-107">Properties</span></span>  
 <span data-ttu-id="11cce-108">SymmetricSecurityBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="11cce-108">The SymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="11cce-109">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="11cce-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="11cce-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="11cce-110">Data type: string</span></span>  
  
 <span data-ttu-id="11cce-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="11cce-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="11cce-112">İleti şifreleme ve bu bağlama için imzalama sırası.</span><span class="sxs-lookup"><span data-stu-id="11cce-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="11cce-113">RequireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="11cce-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="11cce-114">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="11cce-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="11cce-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="11cce-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="11cce-116">Olup bağlama imza onayı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="11cce-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11cce-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="11cce-117">Requirements</span></span>  
  
|<span data-ttu-id="11cce-118">MOF</span><span class="sxs-lookup"><span data-stu-id="11cce-118">MOF</span></span>|<span data-ttu-id="11cce-119">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="11cce-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="11cce-120">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="11cce-120">Namespace</span></span>|<span data-ttu-id="11cce-121">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="11cce-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="11cce-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="11cce-122">See Also</span></span>  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
