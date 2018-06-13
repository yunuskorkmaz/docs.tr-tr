---
title: ServiceAuthorizationBehavior
ms.date: 03/30/2017
ms.assetid: 77dad8e8-fea4-4d1c-b366-2f01a2a87f78
ms.openlocfilehash: e03f83927ec5aef7f916b2262c9c8cff1db68ac9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486479"
---
# <a name="serviceauthorizationbehavior"></a><span data-ttu-id="5a5e3-102">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="5a5e3-102">ServiceAuthorizationBehavior</span></span>
<span data-ttu-id="5a5e3-103">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="5a5e3-103">ServiceAuthorizationBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a5e3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5a5e3-104">Syntax</span></span>  
  
```  
class ServiceAuthorizationBehavior : Behavior  
{  
  boolean ImpersonateCallerForAllOperations;  
  string PrincipalPermissionMode;  
  string RoleProvider;  
  string ServiceAuthorizationManager;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="5a5e3-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="5a5e3-105">Methods</span></span>  
 <span data-ttu-id="5a5e3-106">ServiceAuthorizationBehavior sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="5a5e3-106">The ServiceAuthorizationBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="5a5e3-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="5a5e3-107">Properties</span></span>  
 <span data-ttu-id="5a5e3-108">ServiceAuthorizationBehavior sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="5a5e3-108">The ServiceAuthorizationBehavior class has the following properties:</span></span>  
  
### <a name="impersonatecallerforalloperations"></a><span data-ttu-id="5a5e3-109">impersonateCallerForAllOperations</span><span class="sxs-lookup"><span data-stu-id="5a5e3-109">ImpersonateCallerForAllOperations</span></span>  
 <span data-ttu-id="5a5e3-110">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="5a5e3-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="5a5e3-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="5a5e3-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5a5e3-112">Hizmet gelen ileti tarafından sağlanan kimlik bilgilerini kullanarak kimliğe bürünmeye çalışıp çalışmayacağını denetleyen bir değer.</span><span class="sxs-lookup"><span data-stu-id="5a5e3-112">A value that controls whether the service attempts to impersonate using the credentials provided by the incoming message.</span></span>  
  
### <a name="principalpermissionmode"></a><span data-ttu-id="5a5e3-113">PrincipalPermissionMode</span><span class="sxs-lookup"><span data-stu-id="5a5e3-113">PrincipalPermissionMode</span></span>  
 <span data-ttu-id="5a5e3-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="5a5e3-114">Data type: string</span></span>  
  
 <span data-ttu-id="5a5e3-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="5a5e3-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5a5e3-116">Sunucu üzerinde işlemler gerçekleştirmek için kullanılan kural.</span><span class="sxs-lookup"><span data-stu-id="5a5e3-116">The principal used to carry out operations on the server.</span></span>  
  
### <a name="roleprovider"></a><span data-ttu-id="5a5e3-117">RoleProvider</span><span class="sxs-lookup"><span data-stu-id="5a5e3-117">RoleProvider</span></span>  
 <span data-ttu-id="5a5e3-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="5a5e3-118">Data type: string</span></span>  
  
 <span data-ttu-id="5a5e3-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="5a5e3-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5a5e3-120">ASP.NET rol sağlayıcısı adı.</span><span class="sxs-lookup"><span data-stu-id="5a5e3-120">The name of the ASP.NET role provider.</span></span>  
  
### <a name="serviceauthorizationmanager"></a><span data-ttu-id="5a5e3-121">ServiceAuthorizationManager</span><span class="sxs-lookup"><span data-stu-id="5a5e3-121">ServiceAuthorizationManager</span></span>  
 <span data-ttu-id="5a5e3-122">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="5a5e3-122">Data type: string</span></span>  
  
 <span data-ttu-id="5a5e3-123">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="5a5e3-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5a5e3-124">Yetkilendirme Yöneticisi özel yetkilendirme için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5a5e3-124">The authorization manager used for custom authorization.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a5e3-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5a5e3-125">Requirements</span></span>  
  
|<span data-ttu-id="5a5e3-126">MOF</span><span class="sxs-lookup"><span data-stu-id="5a5e3-126">MOF</span></span>|<span data-ttu-id="5a5e3-127">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="5a5e3-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="5a5e3-128">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="5a5e3-128">Namespace</span></span>|<span data-ttu-id="5a5e3-129">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="5a5e3-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5a5e3-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5a5e3-130">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
