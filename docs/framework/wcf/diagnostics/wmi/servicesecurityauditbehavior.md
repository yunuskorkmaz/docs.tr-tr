---
title: ServiceSecurityAuditBehavior
ms.date: 03/30/2017
ms.assetid: 2c5809e7-5364-44ce-bc71-848be4672e2a
author: BrucePerlerMS
ms.openlocfilehash: 8f43ee752830d95db6bbbdbe311b6d77735e31b5
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47070155"
---
# <a name="servicesecurityauditbehavior"></a><span data-ttu-id="44acd-102">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="44acd-102">ServiceSecurityAuditBehavior</span></span>
<span data-ttu-id="44acd-103">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="44acd-103">ServiceSecurityAuditBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44acd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="44acd-104">Syntax</span></span>  
  
```  
class ServiceSecurityAuditBehavior : Behavior  
{  
  string AuditLogLocation;  
  string MessageAuthenticationAuditLevel;  
  string ServiceAuthorizationAuditLevel;  
  boolean SuppressAuditFailure;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="44acd-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="44acd-105">Methods</span></span>  
 <span data-ttu-id="44acd-106">ServiceSecurityAuditBehavior sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="44acd-106">The ServiceSecurityAuditBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="44acd-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="44acd-107">Properties</span></span>  
 <span data-ttu-id="44acd-108">ServiceSecurityAuditBehavior sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="44acd-108">The ServiceSecurityAuditBehavior class has the following properties:</span></span>  
  
### <a name="auditloglocation"></a><span data-ttu-id="44acd-109">auditLogLocation</span><span class="sxs-lookup"><span data-stu-id="44acd-109">AuditLogLocation</span></span>  
 <span data-ttu-id="44acd-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="44acd-110">Data type: string</span></span>  
  
 <span data-ttu-id="44acd-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="44acd-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="44acd-112">Denetim günlük dosyasının konumu.</span><span class="sxs-lookup"><span data-stu-id="44acd-112">The location of the audit log.</span></span>  
  
### <a name="messageauthenticationauditlevel"></a><span data-ttu-id="44acd-113">messageAuthenticationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="44acd-113">MessageAuthenticationAuditLevel</span></span>  
 <span data-ttu-id="44acd-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="44acd-114">Data type: string</span></span>  
  
 <span data-ttu-id="44acd-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="44acd-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="44acd-116">Denetim olaylarını günlüğe kaydedecek şekilde kullanılan ileti kimlik doğrulama düzeyi türü.</span><span class="sxs-lookup"><span data-stu-id="44acd-116">The type of message authentication level that is used to log audit events.</span></span>  
  
### <a name="serviceauthorizationauditlevel"></a><span data-ttu-id="44acd-117">serviceAuthorizationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="44acd-117">ServiceAuthorizationAuditLevel</span></span>  
 <span data-ttu-id="44acd-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="44acd-118">Data type: string</span></span>  
  
 <span data-ttu-id="44acd-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="44acd-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="44acd-120">Denetim günlüğüne kaydedilen yetkilendirme olay türlerini.</span><span class="sxs-lookup"><span data-stu-id="44acd-120">The types of authorization events that are recorded in the audit log.</span></span>  
  
### <a name="suppressauditfailure"></a><span data-ttu-id="44acd-121">suppressAuditFailure</span><span class="sxs-lookup"><span data-stu-id="44acd-121">SuppressAuditFailure</span></span>  
 <span data-ttu-id="44acd-122">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="44acd-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="44acd-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="44acd-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="44acd-124">Denetim günlüğüne yazma başarısızlıklarını gösterme/gizleme davranışını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="44acd-124">A boolean value that specifies the behavior for suppressing failures of writing to the audit log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44acd-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="44acd-125">Requirements</span></span>  
  
|<span data-ttu-id="44acd-126">MOF</span><span class="sxs-lookup"><span data-stu-id="44acd-126">MOF</span></span>|<span data-ttu-id="44acd-127">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="44acd-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="44acd-128">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="44acd-128">Namespace</span></span>|<span data-ttu-id="44acd-129">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="44acd-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="44acd-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="44acd-130">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
