---
description: 'Daha fazla bilgi edinin: ServiceAuthorizationBehavior'
title: ServiceAuthorizationBehavior
ms.date: 03/30/2017
ms.assetid: 77dad8e8-fea4-4d1c-b366-2f01a2a87f78
ms.openlocfilehash: dc398621103774a04934aa23ae3d7208f4389717
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715593"
---
# <a name="serviceauthorizationbehavior"></a><span data-ttu-id="ca940-103">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="ca940-103">ServiceAuthorizationBehavior</span></span>

<span data-ttu-id="ca940-104">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="ca940-104">ServiceAuthorizationBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca940-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ca940-105">Syntax</span></span>  
  
```csharp
class ServiceAuthorizationBehavior : Behavior  
{  
  boolean ImpersonateCallerForAllOperations;  
  string PrincipalPermissionMode;  
  string RoleProvider;  
  string ServiceAuthorizationManager;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="ca940-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ca940-106">Methods</span></span>  

 <span data-ttu-id="ca940-107">ServiceAuthorizationBehavior sınıfı herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="ca940-107">The ServiceAuthorizationBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ca940-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="ca940-108">Properties</span></span>  

 <span data-ttu-id="ca940-109">ServiceAuthorizationBehavior sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="ca940-109">The ServiceAuthorizationBehavior class has the following properties:</span></span>  
  
### <a name="impersonatecallerforalloperations"></a><span data-ttu-id="ca940-110">ImpersonateCallerForAllOperations</span><span class="sxs-lookup"><span data-stu-id="ca940-110">ImpersonateCallerForAllOperations</span></span>  

 <span data-ttu-id="ca940-111">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="ca940-111">Data type: boolean</span></span>  
  
 <span data-ttu-id="ca940-112">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="ca940-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ca940-113">Hizmetin, gelen ileti tarafından belirtilen kimlik bilgilerini kullanarak kimliğe bürünmeye çalışıp çalışmadığını denetleyen bir değer.</span><span class="sxs-lookup"><span data-stu-id="ca940-113">A value that controls whether the service attempts to impersonate using the credentials provided by the incoming message.</span></span>  
  
### <a name="principalpermissionmode"></a><span data-ttu-id="ca940-114">PrincipalPermissionMode</span><span class="sxs-lookup"><span data-stu-id="ca940-114">PrincipalPermissionMode</span></span>  

 <span data-ttu-id="ca940-115">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="ca940-115">Data type: string</span></span>  
  
 <span data-ttu-id="ca940-116">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="ca940-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ca940-117">Sunucuda işlemleri yürütmek için kullanılan sorumlu.</span><span class="sxs-lookup"><span data-stu-id="ca940-117">The principal used to carry out operations on the server.</span></span>  
  
### <a name="roleprovider"></a><span data-ttu-id="ca940-118">RoleProvider</span><span class="sxs-lookup"><span data-stu-id="ca940-118">RoleProvider</span></span>  

 <span data-ttu-id="ca940-119">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="ca940-119">Data type: string</span></span>  
  
 <span data-ttu-id="ca940-120">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="ca940-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ca940-121">ASP.NET rol sağlayıcısının adı.</span><span class="sxs-lookup"><span data-stu-id="ca940-121">The name of the ASP.NET role provider.</span></span>  
  
### <a name="serviceauthorizationmanager"></a><span data-ttu-id="ca940-122">ServiceAuthorizationManager</span><span class="sxs-lookup"><span data-stu-id="ca940-122">ServiceAuthorizationManager</span></span>  

 <span data-ttu-id="ca940-123">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="ca940-123">Data type: string</span></span>  
  
 <span data-ttu-id="ca940-124">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="ca940-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ca940-125">Özel yetkilendirme için kullanılan Yetkilendirme Yöneticisi.</span><span class="sxs-lookup"><span data-stu-id="ca940-125">The authorization manager used for custom authorization.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca940-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ca940-126">Requirements</span></span>  
  
|<span data-ttu-id="ca940-127">MOF</span><span class="sxs-lookup"><span data-stu-id="ca940-127">MOF</span></span>|<span data-ttu-id="ca940-128">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ca940-128">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ca940-129">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="ca940-129">Namespace</span></span>|<span data-ttu-id="ca940-130">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="ca940-130">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ca940-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ca940-131">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
