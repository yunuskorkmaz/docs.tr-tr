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
ms.openlocfilehash: ab341f55947bfcfbc776143e3bbc33e125da89c8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="symmetricsecuritybindingelement"></a><span data-ttu-id="ffcf6-102">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="ffcf6-102">SymmetricSecurityBindingElement</span></span>
<span data-ttu-id="ffcf6-103">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="ffcf6-103">SymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffcf6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ffcf6-104">Syntax</span></span>  
  
```  
class SymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="ffcf6-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ffcf6-105">Methods</span></span>  
 <span data-ttu-id="ffcf6-106">SymmetricSecurityBindingElement sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="ffcf6-106">The SymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ffcf6-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="ffcf6-107">Properties</span></span>  
 <span data-ttu-id="ffcf6-108">SymmetricSecurityBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="ffcf6-108">The SymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="ffcf6-109">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="ffcf6-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="ffcf6-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="ffcf6-110">Data type: string</span></span>  
  
 <span data-ttu-id="ffcf6-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="ffcf6-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ffcf6-112">İleti şifreleme ve bu bağlama için imzalama sırası.</span><span class="sxs-lookup"><span data-stu-id="ffcf6-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="ffcf6-113">RequireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="ffcf6-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="ffcf6-114">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="ffcf6-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="ffcf6-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="ffcf6-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ffcf6-116">Olup bağlama imza onayı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ffcf6-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffcf6-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ffcf6-117">Requirements</span></span>  
  
|<span data-ttu-id="ffcf6-118">MOF</span><span class="sxs-lookup"><span data-stu-id="ffcf6-118">MOF</span></span>|<span data-ttu-id="ffcf6-119">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="ffcf6-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ffcf6-120">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="ffcf6-120">Namespace</span></span>|<span data-ttu-id="ffcf6-121">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ffcf6-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ffcf6-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ffcf6-122">See Also</span></span>  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
