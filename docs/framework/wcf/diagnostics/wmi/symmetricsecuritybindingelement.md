---
title: SymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: b2e182b6-c041-4d80-a926-6058068d9f79
ms.openlocfilehash: c618b5b41790b04a84b4c50fe47baa2c0cb05ab2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96274107"
---
# <a name="symmetricsecuritybindingelement"></a><span data-ttu-id="a2769-102">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="a2769-102">SymmetricSecurityBindingElement</span></span>

<span data-ttu-id="a2769-103">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="a2769-103">SymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2769-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="a2769-104">Syntax</span></span>  
  
```csharp
class SymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="a2769-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a2769-105">Methods</span></span>  

 <span data-ttu-id="a2769-106">SymmetricSecurityBindingElement sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="a2769-106">The SymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="a2769-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="a2769-107">Properties</span></span>  

 <span data-ttu-id="a2769-108">SymmetricSecurityBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="a2769-108">The SymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="a2769-109">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="a2769-109">MessageProtectionOrder</span></span>  

 <span data-ttu-id="a2769-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="a2769-110">Data type: string</span></span>  
  
 <span data-ttu-id="a2769-111">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="a2769-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a2769-112">Bu bağlama için ileti şifreleme ve imzalama sırası.</span><span class="sxs-lookup"><span data-stu-id="a2769-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="a2769-113">RequireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="a2769-113">RequireSignatureConfirmation</span></span>  

 <span data-ttu-id="a2769-114">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="a2769-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="a2769-115">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="a2769-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a2769-116">Bağlamanın imza onayını gerektirip gerektirmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a2769-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2769-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a2769-117">Requirements</span></span>  
  
|<span data-ttu-id="a2769-118">MOF</span><span class="sxs-lookup"><span data-stu-id="a2769-118">MOF</span></span>|<span data-ttu-id="a2769-119">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a2769-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="a2769-120">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="a2769-120">Namespace</span></span>|<span data-ttu-id="a2769-121">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="a2769-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a2769-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a2769-122">See also</span></span>

- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
