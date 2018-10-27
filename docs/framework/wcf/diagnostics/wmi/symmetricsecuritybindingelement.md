---
title: SymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: b2e182b6-c041-4d80-a926-6058068d9f79
ms.openlocfilehash: 618899c80d1b22aaabc3c13fe1079137eaf10a93
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50182508"
---
# <a name="symmetricsecuritybindingelement"></a><span data-ttu-id="8d684-102">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="8d684-102">SymmetricSecurityBindingElement</span></span>
<span data-ttu-id="8d684-103">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="8d684-103">SymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d684-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8d684-104">Syntax</span></span>  
  
```csharp
class SymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="8d684-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8d684-105">Methods</span></span>  
 <span data-ttu-id="8d684-106">SymmetricSecurityBindingElement sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="8d684-106">The SymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="8d684-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="8d684-107">Properties</span></span>  
 <span data-ttu-id="8d684-108">SymmetricSecurityBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="8d684-108">The SymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="8d684-109">messageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="8d684-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="8d684-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="8d684-110">Data type: string</span></span>  
  
 <span data-ttu-id="8d684-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="8d684-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8d684-112">İleti şifreleme ve imzalama için bu bağlama sırası.</span><span class="sxs-lookup"><span data-stu-id="8d684-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="8d684-113">requireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="8d684-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="8d684-114">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="8d684-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="8d684-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="8d684-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8d684-116">Bağlama imza onayı gerektirip.</span><span class="sxs-lookup"><span data-stu-id="8d684-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d684-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8d684-117">Requirements</span></span>  
  
|<span data-ttu-id="8d684-118">MOF</span><span class="sxs-lookup"><span data-stu-id="8d684-118">MOF</span></span>|<span data-ttu-id="8d684-119">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="8d684-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="8d684-120">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="8d684-120">Namespace</span></span>|<span data-ttu-id="8d684-121">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="8d684-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8d684-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8d684-122">See Also</span></span>  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
