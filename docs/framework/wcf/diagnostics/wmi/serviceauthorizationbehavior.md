---
title: ServiceAuthorizationBehavior
ms.date: 03/30/2017
ms.assetid: 77dad8e8-fea4-4d1c-b366-2f01a2a87f78
ms.openlocfilehash: d3625865484568746888ef0638d9a8501e610bef
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273210"
---
# <a name="serviceauthorizationbehavior"></a><span data-ttu-id="47e2c-102">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="47e2c-102">ServiceAuthorizationBehavior</span></span>

<span data-ttu-id="47e2c-103">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="47e2c-103">ServiceAuthorizationBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47e2c-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="47e2c-104">Syntax</span></span>  
  
```csharp
class ServiceAuthorizationBehavior : Behavior  
{  
  boolean ImpersonateCallerForAllOperations;  
  string PrincipalPermissionMode;  
  string RoleProvider;  
  string ServiceAuthorizationManager;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="47e2c-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="47e2c-105">Methods</span></span>  

 <span data-ttu-id="47e2c-106">ServiceAuthorizationBehavior sınıfı herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="47e2c-106">The ServiceAuthorizationBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="47e2c-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="47e2c-107">Properties</span></span>  

 <span data-ttu-id="47e2c-108">ServiceAuthorizationBehavior sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="47e2c-108">The ServiceAuthorizationBehavior class has the following properties:</span></span>  
  
### <a name="impersonatecallerforalloperations"></a><span data-ttu-id="47e2c-109">ImpersonateCallerForAllOperations</span><span class="sxs-lookup"><span data-stu-id="47e2c-109">ImpersonateCallerForAllOperations</span></span>  

 <span data-ttu-id="47e2c-110">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="47e2c-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="47e2c-111">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="47e2c-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="47e2c-112">Hizmetin, gelen ileti tarafından belirtilen kimlik bilgilerini kullanarak kimliğe bürünmeye çalışıp çalışmadığını denetleyen bir değer.</span><span class="sxs-lookup"><span data-stu-id="47e2c-112">A value that controls whether the service attempts to impersonate using the credentials provided by the incoming message.</span></span>  
  
### <a name="principalpermissionmode"></a><span data-ttu-id="47e2c-113">PrincipalPermissionMode</span><span class="sxs-lookup"><span data-stu-id="47e2c-113">PrincipalPermissionMode</span></span>  

 <span data-ttu-id="47e2c-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="47e2c-114">Data type: string</span></span>  
  
 <span data-ttu-id="47e2c-115">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="47e2c-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="47e2c-116">Sunucuda işlemleri yürütmek için kullanılan sorumlu.</span><span class="sxs-lookup"><span data-stu-id="47e2c-116">The principal used to carry out operations on the server.</span></span>  
  
### <a name="roleprovider"></a><span data-ttu-id="47e2c-117">RoleProvider</span><span class="sxs-lookup"><span data-stu-id="47e2c-117">RoleProvider</span></span>  

 <span data-ttu-id="47e2c-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="47e2c-118">Data type: string</span></span>  
  
 <span data-ttu-id="47e2c-119">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="47e2c-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="47e2c-120">ASP.NET rol sağlayıcısının adı.</span><span class="sxs-lookup"><span data-stu-id="47e2c-120">The name of the ASP.NET role provider.</span></span>  
  
### <a name="serviceauthorizationmanager"></a><span data-ttu-id="47e2c-121">ServiceAuthorizationManager</span><span class="sxs-lookup"><span data-stu-id="47e2c-121">ServiceAuthorizationManager</span></span>  

 <span data-ttu-id="47e2c-122">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="47e2c-122">Data type: string</span></span>  
  
 <span data-ttu-id="47e2c-123">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="47e2c-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="47e2c-124">Özel yetkilendirme için kullanılan Yetkilendirme Yöneticisi.</span><span class="sxs-lookup"><span data-stu-id="47e2c-124">The authorization manager used for custom authorization.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47e2c-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="47e2c-125">Requirements</span></span>  
  
|<span data-ttu-id="47e2c-126">MOF</span><span class="sxs-lookup"><span data-stu-id="47e2c-126">MOF</span></span>|<span data-ttu-id="47e2c-127">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="47e2c-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="47e2c-128">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="47e2c-128">Namespace</span></span>|<span data-ttu-id="47e2c-129">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="47e2c-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="47e2c-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="47e2c-130">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
