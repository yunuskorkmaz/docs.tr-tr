---
title: ServiceAuthorizationBehavior
ms.date: 03/30/2017
ms.assetid: 77dad8e8-fea4-4d1c-b366-2f01a2a87f78
ms.openlocfilehash: 51555e3357b8c33a53261c4894d97798b0a05656
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61957061"
---
# <a name="serviceauthorizationbehavior"></a><span data-ttu-id="5c0eb-102">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="5c0eb-102">ServiceAuthorizationBehavior</span></span>
<span data-ttu-id="5c0eb-103">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="5c0eb-103">ServiceAuthorizationBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c0eb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5c0eb-104">Syntax</span></span>  
  
```csharp
class ServiceAuthorizationBehavior : Behavior  
{  
  boolean ImpersonateCallerForAllOperations;  
  string PrincipalPermissionMode;  
  string RoleProvider;  
  string ServiceAuthorizationManager;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="5c0eb-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="5c0eb-105">Methods</span></span>  
 <span data-ttu-id="5c0eb-106">ServiceAuthorizationBehavior sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="5c0eb-106">The ServiceAuthorizationBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="5c0eb-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="5c0eb-107">Properties</span></span>  
 <span data-ttu-id="5c0eb-108">ServiceAuthorizationBehavior sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="5c0eb-108">The ServiceAuthorizationBehavior class has the following properties:</span></span>  
  
### <a name="impersonatecallerforalloperations"></a><span data-ttu-id="5c0eb-109">ImpersonateCallerForAllOperations</span><span class="sxs-lookup"><span data-stu-id="5c0eb-109">ImpersonateCallerForAllOperations</span></span>  
 <span data-ttu-id="5c0eb-110">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="5c0eb-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="5c0eb-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="5c0eb-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5c0eb-112">Hizmet gelen ileti tarafından sağlanan kimlik bilgilerini kullanarak bürünülecek deneyip denemeyeceğini denetleyen değeri.</span><span class="sxs-lookup"><span data-stu-id="5c0eb-112">A value that controls whether the service attempts to impersonate using the credentials provided by the incoming message.</span></span>  
  
### <a name="principalpermissionmode"></a><span data-ttu-id="5c0eb-113">PrincipalPermissionMode</span><span class="sxs-lookup"><span data-stu-id="5c0eb-113">PrincipalPermissionMode</span></span>  
 <span data-ttu-id="5c0eb-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="5c0eb-114">Data type: string</span></span>  
  
 <span data-ttu-id="5c0eb-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="5c0eb-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5c0eb-116">Sunucu üzerinde işlem gerçekleştirmek için kullanılan kural.</span><span class="sxs-lookup"><span data-stu-id="5c0eb-116">The principal used to carry out operations on the server.</span></span>  
  
### <a name="roleprovider"></a><span data-ttu-id="5c0eb-117">RoleProvider</span><span class="sxs-lookup"><span data-stu-id="5c0eb-117">RoleProvider</span></span>  
 <span data-ttu-id="5c0eb-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="5c0eb-118">Data type: string</span></span>  
  
 <span data-ttu-id="5c0eb-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="5c0eb-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5c0eb-120">ASP.NET rol sağlayıcıyı adı.</span><span class="sxs-lookup"><span data-stu-id="5c0eb-120">The name of the ASP.NET role provider.</span></span>  
  
### <a name="serviceauthorizationmanager"></a><span data-ttu-id="5c0eb-121">ServiceAuthorizationManager</span><span class="sxs-lookup"><span data-stu-id="5c0eb-121">ServiceAuthorizationManager</span></span>  
 <span data-ttu-id="5c0eb-122">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="5c0eb-122">Data type: string</span></span>  
  
 <span data-ttu-id="5c0eb-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="5c0eb-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5c0eb-124">Özel yetkilendirme için kullanılan Yetkilendirme Yöneticisi.</span><span class="sxs-lookup"><span data-stu-id="5c0eb-124">The authorization manager used for custom authorization.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c0eb-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5c0eb-125">Requirements</span></span>  
  
|<span data-ttu-id="5c0eb-126">MOF</span><span class="sxs-lookup"><span data-stu-id="5c0eb-126">MOF</span></span>|<span data-ttu-id="5c0eb-127">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="5c0eb-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="5c0eb-128">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="5c0eb-128">Namespace</span></span>|<span data-ttu-id="5c0eb-129">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="5c0eb-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5c0eb-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c0eb-130">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
