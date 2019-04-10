---
title: SymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: b2e182b6-c041-4d80-a926-6058068d9f79
ms.openlocfilehash: f6effd533a205d0e8fd1421119e325f06b340dd1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59206804"
---
# <a name="symmetricsecuritybindingelement"></a><span data-ttu-id="e5f65-102">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="e5f65-102">SymmetricSecurityBindingElement</span></span>
<span data-ttu-id="e5f65-103">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="e5f65-103">SymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5f65-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e5f65-104">Syntax</span></span>  
  
```csharp
class SymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e5f65-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e5f65-105">Methods</span></span>  
 <span data-ttu-id="e5f65-106">SymmetricSecurityBindingElement sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="e5f65-106">The SymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e5f65-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e5f65-107">Properties</span></span>  
 <span data-ttu-id="e5f65-108">SymmetricSecurityBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="e5f65-108">The SymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="e5f65-109">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="e5f65-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="e5f65-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="e5f65-110">Data type: string</span></span>  
  
 <span data-ttu-id="e5f65-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e5f65-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e5f65-112">İleti şifreleme ve imzalama için bu bağlama sırası.</span><span class="sxs-lookup"><span data-stu-id="e5f65-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="e5f65-113">requireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="e5f65-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="e5f65-114">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="e5f65-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="e5f65-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e5f65-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e5f65-116">Bağlama imza onayı gerektirip.</span><span class="sxs-lookup"><span data-stu-id="e5f65-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5f65-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e5f65-117">Requirements</span></span>  
  
|<span data-ttu-id="e5f65-118">MOF</span><span class="sxs-lookup"><span data-stu-id="e5f65-118">MOF</span></span>|<span data-ttu-id="e5f65-119">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="e5f65-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e5f65-120">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="e5f65-120">Namespace</span></span>|<span data-ttu-id="e5f65-121">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e5f65-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e5f65-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5f65-122">See also</span></span>

- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
