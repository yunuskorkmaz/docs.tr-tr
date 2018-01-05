---
title: ServiceAuthorizationBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77dad8e8-fea4-4d1c-b366-2f01a2a87f78
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 62f3e32e886f49ac8dde6af5c37a4e57373c9576
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="serviceauthorizationbehavior"></a><span data-ttu-id="ef263-102">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="ef263-102">ServiceAuthorizationBehavior</span></span>
<span data-ttu-id="ef263-103">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="ef263-103">ServiceAuthorizationBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef263-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ef263-104">Syntax</span></span>  
  
```  
class ServiceAuthorizationBehavior : Behavior  
{  
  boolean ImpersonateCallerForAllOperations;  
  string PrincipalPermissionMode;  
  string RoleProvider;  
  string ServiceAuthorizationManager;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="ef263-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ef263-105">Methods</span></span>  
 <span data-ttu-id="ef263-106">ServiceAuthorizationBehavior sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="ef263-106">The ServiceAuthorizationBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ef263-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="ef263-107">Properties</span></span>  
 <span data-ttu-id="ef263-108">ServiceAuthorizationBehavior sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="ef263-108">The ServiceAuthorizationBehavior class has the following properties:</span></span>  
  
### <a name="impersonatecallerforalloperations"></a><span data-ttu-id="ef263-109">impersonateCallerForAllOperations</span><span class="sxs-lookup"><span data-stu-id="ef263-109">ImpersonateCallerForAllOperations</span></span>  
 <span data-ttu-id="ef263-110">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="ef263-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="ef263-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="ef263-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ef263-112">Hizmet gelen ileti tarafından sağlanan kimlik bilgilerini kullanarak kimliğe bürünmeye çalışıp çalışmayacağını denetleyen bir değer.</span><span class="sxs-lookup"><span data-stu-id="ef263-112">A value that controls whether the service attempts to impersonate using the credentials provided by the incoming message.</span></span>  
  
### <a name="principalpermissionmode"></a><span data-ttu-id="ef263-113">PrincipalPermissionMode</span><span class="sxs-lookup"><span data-stu-id="ef263-113">PrincipalPermissionMode</span></span>  
 <span data-ttu-id="ef263-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="ef263-114">Data type: string</span></span>  
  
 <span data-ttu-id="ef263-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="ef263-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ef263-116">Sunucu üzerinde işlemler gerçekleştirmek için kullanılan kural.</span><span class="sxs-lookup"><span data-stu-id="ef263-116">The principal used to carry out operations on the server.</span></span>  
  
### <a name="roleprovider"></a><span data-ttu-id="ef263-117">RoleProvider</span><span class="sxs-lookup"><span data-stu-id="ef263-117">RoleProvider</span></span>  
 <span data-ttu-id="ef263-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="ef263-118">Data type: string</span></span>  
  
 <span data-ttu-id="ef263-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="ef263-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ef263-120">ASP.NET rol sağlayıcısı adı.</span><span class="sxs-lookup"><span data-stu-id="ef263-120">The name of the ASP.NET role provider.</span></span>  
  
### <a name="serviceauthorizationmanager"></a><span data-ttu-id="ef263-121">ServiceAuthorizationManager</span><span class="sxs-lookup"><span data-stu-id="ef263-121">ServiceAuthorizationManager</span></span>  
 <span data-ttu-id="ef263-122">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="ef263-122">Data type: string</span></span>  
  
 <span data-ttu-id="ef263-123">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="ef263-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ef263-124">Yetkilendirme Yöneticisi özel yetkilendirme için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ef263-124">The authorization manager used for custom authorization.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef263-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ef263-125">Requirements</span></span>  
  
|<span data-ttu-id="ef263-126">MOF</span><span class="sxs-lookup"><span data-stu-id="ef263-126">MOF</span></span>|<span data-ttu-id="ef263-127">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="ef263-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ef263-128">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="ef263-128">Namespace</span></span>|<span data-ttu-id="ef263-129">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ef263-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ef263-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ef263-130">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
