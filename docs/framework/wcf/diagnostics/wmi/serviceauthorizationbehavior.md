---
title: ServiceAuthorizationBehavior
ms.date: 03/30/2017
ms.assetid: 77dad8e8-fea4-4d1c-b366-2f01a2a87f78
ms.openlocfilehash: c916d0820a1eae333384deab7b0619abfbdc8167
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/26/2018
ms.locfileid: "49415386"
---
# <a name="serviceauthorizationbehavior"></a><span data-ttu-id="8bc58-102">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="8bc58-102">ServiceAuthorizationBehavior</span></span>
<span data-ttu-id="8bc58-103">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="8bc58-103">ServiceAuthorizationBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bc58-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8bc58-104">Syntax</span></span>  
  
```csharp
class ServiceAuthorizationBehavior : Behavior  
{  
  boolean ImpersonateCallerForAllOperations;  
  string PrincipalPermissionMode;  
  string RoleProvider;  
  string ServiceAuthorizationManager;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="8bc58-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8bc58-105">Methods</span></span>  
 <span data-ttu-id="8bc58-106">ServiceAuthorizationBehavior sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="8bc58-106">The ServiceAuthorizationBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="8bc58-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="8bc58-107">Properties</span></span>  
 <span data-ttu-id="8bc58-108">ServiceAuthorizationBehavior sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="8bc58-108">The ServiceAuthorizationBehavior class has the following properties:</span></span>  
  
### <a name="impersonatecallerforalloperations"></a><span data-ttu-id="8bc58-109">ImpersonateCallerForAllOperations</span><span class="sxs-lookup"><span data-stu-id="8bc58-109">ImpersonateCallerForAllOperations</span></span>  
 <span data-ttu-id="8bc58-110">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="8bc58-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="8bc58-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="8bc58-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8bc58-112">Hizmet gelen ileti tarafından sağlanan kimlik bilgilerini kullanarak bürünülecek deneyip denemeyeceğini denetleyen değeri.</span><span class="sxs-lookup"><span data-stu-id="8bc58-112">A value that controls whether the service attempts to impersonate using the credentials provided by the incoming message.</span></span>  
  
### <a name="principalpermissionmode"></a><span data-ttu-id="8bc58-113">PrincipalPermissionMode</span><span class="sxs-lookup"><span data-stu-id="8bc58-113">PrincipalPermissionMode</span></span>  
 <span data-ttu-id="8bc58-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="8bc58-114">Data type: string</span></span>  
  
 <span data-ttu-id="8bc58-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="8bc58-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8bc58-116">Sunucu üzerinde işlem gerçekleştirmek için kullanılan kural.</span><span class="sxs-lookup"><span data-stu-id="8bc58-116">The principal used to carry out operations on the server.</span></span>  
  
### <a name="roleprovider"></a><span data-ttu-id="8bc58-117">RoleProvider</span><span class="sxs-lookup"><span data-stu-id="8bc58-117">RoleProvider</span></span>  
 <span data-ttu-id="8bc58-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="8bc58-118">Data type: string</span></span>  
  
 <span data-ttu-id="8bc58-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="8bc58-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8bc58-120">ASP.NET rol sağlayıcıyı adı.</span><span class="sxs-lookup"><span data-stu-id="8bc58-120">The name of the ASP.NET role provider.</span></span>  
  
### <a name="serviceauthorizationmanager"></a><span data-ttu-id="8bc58-121">ServiceAuthorizationManager</span><span class="sxs-lookup"><span data-stu-id="8bc58-121">ServiceAuthorizationManager</span></span>  
 <span data-ttu-id="8bc58-122">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="8bc58-122">Data type: string</span></span>  
  
 <span data-ttu-id="8bc58-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="8bc58-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8bc58-124">Özel yetkilendirme için kullanılan Yetkilendirme Yöneticisi.</span><span class="sxs-lookup"><span data-stu-id="8bc58-124">The authorization manager used for custom authorization.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8bc58-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8bc58-125">Requirements</span></span>  
  
|<span data-ttu-id="8bc58-126">MOF</span><span class="sxs-lookup"><span data-stu-id="8bc58-126">MOF</span></span>|<span data-ttu-id="8bc58-127">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="8bc58-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="8bc58-128">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="8bc58-128">Namespace</span></span>|<span data-ttu-id="8bc58-129">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="8bc58-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8bc58-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8bc58-130">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
