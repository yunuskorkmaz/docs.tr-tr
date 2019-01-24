---
title: SymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: b2e182b6-c041-4d80-a926-6058068d9f79
ms.openlocfilehash: 7b979a6872da15c4130e580a3f7327802f42db18
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54701397"
---
# <a name="symmetricsecuritybindingelement"></a><span data-ttu-id="9584c-102">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="9584c-102">SymmetricSecurityBindingElement</span></span>
<span data-ttu-id="9584c-103">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="9584c-103">SymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9584c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9584c-104">Syntax</span></span>  
  
```csharp
class SymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="9584c-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="9584c-105">Methods</span></span>  
 <span data-ttu-id="9584c-106">SymmetricSecurityBindingElement sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="9584c-106">The SymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="9584c-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="9584c-107">Properties</span></span>  
 <span data-ttu-id="9584c-108">SymmetricSecurityBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="9584c-108">The SymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="9584c-109">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="9584c-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="9584c-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="9584c-110">Data type: string</span></span>  
  
 <span data-ttu-id="9584c-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="9584c-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9584c-112">İleti şifreleme ve imzalama için bu bağlama sırası.</span><span class="sxs-lookup"><span data-stu-id="9584c-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="9584c-113">requireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="9584c-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="9584c-114">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="9584c-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="9584c-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="9584c-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9584c-116">Bağlama imza onayı gerektirip.</span><span class="sxs-lookup"><span data-stu-id="9584c-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9584c-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9584c-117">Requirements</span></span>  
  
|<span data-ttu-id="9584c-118">MOF</span><span class="sxs-lookup"><span data-stu-id="9584c-118">MOF</span></span>|<span data-ttu-id="9584c-119">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="9584c-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="9584c-120">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="9584c-120">Namespace</span></span>|<span data-ttu-id="9584c-121">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="9584c-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9584c-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9584c-122">See also</span></span>
- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
