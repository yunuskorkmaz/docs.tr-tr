---
description: 'Daha fazla bilgi edinin: ServiceCredentials'
title: ServiceCredentials
ms.date: 03/30/2017
ms.assetid: 9c780793-4785-46f7-add9-ac1ebeadb614
ms.openlocfilehash: bfd025a8f671a3c5aea537059cde0e751cfa9bb9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715554"
---
# <a name="servicecredentials"></a><span data-ttu-id="25aaf-103">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="25aaf-103">ServiceCredentials</span></span>

<span data-ttu-id="25aaf-104">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="25aaf-104">ServiceCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25aaf-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="25aaf-105">Syntax</span></span>  
  
```csharp
class ServiceCredentials : Behavior  
{  
  string ClientCertificate;  
  string IssuedTokenAuthentication;  
  string Peer;  
  string SecureConversationAuthentication;  
  string ServiceCertificate;  
  string UserNameAuthentication;  
  string WindowsAuthentication;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="25aaf-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="25aaf-106">Methods</span></span>  

 <span data-ttu-id="25aaf-107">ServiceCredentials sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="25aaf-107">The ServiceCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="25aaf-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="25aaf-108">Properties</span></span>  

 <span data-ttu-id="25aaf-109">ServiceCredentials sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="25aaf-109">The ServiceCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="25aaf-110">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="25aaf-110">ClientCertificate</span></span>  

 <span data-ttu-id="25aaf-111">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="25aaf-111">Data type: string</span></span>  
  
 <span data-ttu-id="25aaf-112">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="25aaf-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="25aaf-113">Bu hizmet için istemci sertifikası kimlik doğrulaması ve sağlama ayarları.</span><span class="sxs-lookup"><span data-stu-id="25aaf-113">The client certificate authentication and provisioning settings for this service.</span></span>  
  
### <a name="issuedtokenauthentication"></a><span data-ttu-id="25aaf-114">IssuedTokenAuthentication</span><span class="sxs-lookup"><span data-stu-id="25aaf-114">IssuedTokenAuthentication</span></span>  

 <span data-ttu-id="25aaf-115">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="25aaf-115">Data type: string</span></span>  
  
 <span data-ttu-id="25aaf-116">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="25aaf-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="25aaf-117">Bu hizmet için geçerli verilen belirteç kimlik doğrulama ayarları.</span><span class="sxs-lookup"><span data-stu-id="25aaf-117">The current issued token authentication settings for this service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="25aaf-118">Eşdüzey hizmet sağlayıcı</span><span class="sxs-lookup"><span data-stu-id="25aaf-118">Peer</span></span>  

 <span data-ttu-id="25aaf-119">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="25aaf-119">Data type: string</span></span>  
  
 <span data-ttu-id="25aaf-120">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="25aaf-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="25aaf-121">Eş aktarım noktaları tarafından kullanılacak geçerli kimlik bilgisi kimlik doğrulaması ve sağlama ayarları.</span><span class="sxs-lookup"><span data-stu-id="25aaf-121">The current credential authentication and provisioning settings to be used by peer transport endpoints.</span></span>  
  
### <a name="secureconversationauthentication"></a><span data-ttu-id="25aaf-122">Servicecredential</span><span class="sxs-lookup"><span data-stu-id="25aaf-122">SecureConversationAuthentication</span></span>  

 <span data-ttu-id="25aaf-123">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="25aaf-123">Data type: string</span></span>  
  
 <span data-ttu-id="25aaf-124">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="25aaf-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="25aaf-125">Geçerli güvenli konuşma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="25aaf-125">Specifies the current secure conversation settings.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="25aaf-126">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="25aaf-126">ServiceCertificate</span></span>  

 <span data-ttu-id="25aaf-127">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="25aaf-127">Data type: string</span></span>  
  
 <span data-ttu-id="25aaf-128">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="25aaf-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="25aaf-129">Bu hizmetle ilişkili sertifika.</span><span class="sxs-lookup"><span data-stu-id="25aaf-129">The certificate associated with this service.</span></span>  
  
### <a name="usernameauthentication"></a><span data-ttu-id="25aaf-130">UserNameAuthentication</span><span class="sxs-lookup"><span data-stu-id="25aaf-130">UserNameAuthentication</span></span>  

 <span data-ttu-id="25aaf-131">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="25aaf-131">Data type: string</span></span>  
  
 <span data-ttu-id="25aaf-132">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="25aaf-132">Access type: Read-only</span></span>  
  
 <span data-ttu-id="25aaf-133">Bu hizmetin Kullanıcı adı/parola ayarları.</span><span class="sxs-lookup"><span data-stu-id="25aaf-133">The username/password settings for this service.</span></span>  
  
### <a name="windowsauthentication"></a><span data-ttu-id="25aaf-134">WindowsAuthentication</span><span class="sxs-lookup"><span data-stu-id="25aaf-134">WindowsAuthentication</span></span>  

 <span data-ttu-id="25aaf-135">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="25aaf-135">Data type: string</span></span>  
  
 <span data-ttu-id="25aaf-136">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="25aaf-136">Access type: Read-only</span></span>  
  
 <span data-ttu-id="25aaf-137">Bu hizmet için Windows kimlik doğrulama ayarları.</span><span class="sxs-lookup"><span data-stu-id="25aaf-137">The Windows authentication settings for this service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25aaf-138">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="25aaf-138">Requirements</span></span>  
  
|<span data-ttu-id="25aaf-139">MOF</span><span class="sxs-lookup"><span data-stu-id="25aaf-139">MOF</span></span>|<span data-ttu-id="25aaf-140">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="25aaf-140">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="25aaf-141">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="25aaf-141">Namespace</span></span>|<span data-ttu-id="25aaf-142">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="25aaf-142">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="25aaf-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="25aaf-143">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceCredentials>
