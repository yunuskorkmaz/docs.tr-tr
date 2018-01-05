---
title: AsymmetricSecurityBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7bd3b6be-8f77-4927-93ae-6fa371893cca
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 82e5365a440d103727f354e682d0ebecb5f46a46
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="asymmetricsecuritybindingelement"></a><span data-ttu-id="d0b18-102">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="d0b18-102">AsymmetricSecurityBindingElement</span></span>
<span data-ttu-id="d0b18-103">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="d0b18-103">AsymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0b18-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d0b18-104">Syntax</span></span>  
  
```  
class AsymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="d0b18-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d0b18-105">Methods</span></span>  
 <span data-ttu-id="d0b18-106">AsymmetricSecurityBindingElement sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="d0b18-106">The AsymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d0b18-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="d0b18-107">Properties</span></span>  
 <span data-ttu-id="d0b18-108">AsymmetricSecurityBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="d0b18-108">The AsymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="d0b18-109">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="d0b18-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="d0b18-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="d0b18-110">Data type: string</span></span>  
  
 <span data-ttu-id="d0b18-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d0b18-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d0b18-112">İleti şifreleme ve bu bağlama için imzalama sırası.</span><span class="sxs-lookup"><span data-stu-id="d0b18-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="d0b18-113">RequireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="d0b18-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="d0b18-114">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="d0b18-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="d0b18-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d0b18-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d0b18-116">Olup bağlama imza onayı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d0b18-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0b18-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d0b18-117">Requirements</span></span>  
  
|<span data-ttu-id="d0b18-118">MOF</span><span class="sxs-lookup"><span data-stu-id="d0b18-118">MOF</span></span>|<span data-ttu-id="d0b18-119">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="d0b18-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="d0b18-120">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="d0b18-120">Namespace</span></span>|<span data-ttu-id="d0b18-121">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d0b18-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d0b18-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d0b18-122">See Also</span></span>  
 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
