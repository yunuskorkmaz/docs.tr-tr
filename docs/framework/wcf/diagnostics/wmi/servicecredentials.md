---
title: ServiceCredentials
ms.date: 03/30/2017
ms.assetid: 9c780793-4785-46f7-add9-ac1ebeadb614
ms.openlocfilehash: d7e89acedc8fc1004b0198172e58813944df85f3
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262313"
---
# <a name="servicecredentials"></a><span data-ttu-id="6d08b-102">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="6d08b-102">ServiceCredentials</span></span>

<span data-ttu-id="6d08b-103">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="6d08b-103">ServiceCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d08b-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="6d08b-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="6d08b-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6d08b-105">Methods</span></span>  

 <span data-ttu-id="6d08b-106">ServiceCredentials sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="6d08b-106">The ServiceCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="6d08b-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="6d08b-107">Properties</span></span>  

 <span data-ttu-id="6d08b-108">ServiceCredentials sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="6d08b-108">The ServiceCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="6d08b-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="6d08b-109">ClientCertificate</span></span>  

 <span data-ttu-id="6d08b-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="6d08b-110">Data type: string</span></span>  
  
 <span data-ttu-id="6d08b-111">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="6d08b-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6d08b-112">Bu hizmet için istemci sertifikası kimlik doğrulaması ve sağlama ayarları.</span><span class="sxs-lookup"><span data-stu-id="6d08b-112">The client certificate authentication and provisioning settings for this service.</span></span>  
  
### <a name="issuedtokenauthentication"></a><span data-ttu-id="6d08b-113">IssuedTokenAuthentication</span><span class="sxs-lookup"><span data-stu-id="6d08b-113">IssuedTokenAuthentication</span></span>  

 <span data-ttu-id="6d08b-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="6d08b-114">Data type: string</span></span>  
  
 <span data-ttu-id="6d08b-115">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="6d08b-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6d08b-116">Bu hizmet için geçerli verilen belirteç kimlik doğrulama ayarları.</span><span class="sxs-lookup"><span data-stu-id="6d08b-116">The current issued token authentication settings for this service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="6d08b-117">Eşdüzey hizmet sağlayıcı</span><span class="sxs-lookup"><span data-stu-id="6d08b-117">Peer</span></span>  

 <span data-ttu-id="6d08b-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="6d08b-118">Data type: string</span></span>  
  
 <span data-ttu-id="6d08b-119">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="6d08b-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6d08b-120">Eş aktarım noktaları tarafından kullanılacak geçerli kimlik bilgisi kimlik doğrulaması ve sağlama ayarları.</span><span class="sxs-lookup"><span data-stu-id="6d08b-120">The current credential authentication and provisioning settings to be used by peer transport endpoints.</span></span>  
  
### <a name="secureconversationauthentication"></a><span data-ttu-id="6d08b-121">Servicecredential</span><span class="sxs-lookup"><span data-stu-id="6d08b-121">SecureConversationAuthentication</span></span>  

 <span data-ttu-id="6d08b-122">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="6d08b-122">Data type: string</span></span>  
  
 <span data-ttu-id="6d08b-123">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="6d08b-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6d08b-124">Geçerli güvenli konuşma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6d08b-124">Specifies the current secure conversation settings.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="6d08b-125">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="6d08b-125">ServiceCertificate</span></span>  

 <span data-ttu-id="6d08b-126">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="6d08b-126">Data type: string</span></span>  
  
 <span data-ttu-id="6d08b-127">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="6d08b-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6d08b-128">Bu hizmetle ilişkili sertifika.</span><span class="sxs-lookup"><span data-stu-id="6d08b-128">The certificate associated with this service.</span></span>  
  
### <a name="usernameauthentication"></a><span data-ttu-id="6d08b-129">UserNameAuthentication</span><span class="sxs-lookup"><span data-stu-id="6d08b-129">UserNameAuthentication</span></span>  

 <span data-ttu-id="6d08b-130">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="6d08b-130">Data type: string</span></span>  
  
 <span data-ttu-id="6d08b-131">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="6d08b-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6d08b-132">Bu hizmetin Kullanıcı adı/parola ayarları.</span><span class="sxs-lookup"><span data-stu-id="6d08b-132">The username/password settings for this service.</span></span>  
  
### <a name="windowsauthentication"></a><span data-ttu-id="6d08b-133">WindowsAuthentication</span><span class="sxs-lookup"><span data-stu-id="6d08b-133">WindowsAuthentication</span></span>  

 <span data-ttu-id="6d08b-134">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="6d08b-134">Data type: string</span></span>  
  
 <span data-ttu-id="6d08b-135">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="6d08b-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6d08b-136">Bu hizmet için Windows kimlik doğrulama ayarları.</span><span class="sxs-lookup"><span data-stu-id="6d08b-136">The Windows authentication settings for this service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d08b-137">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6d08b-137">Requirements</span></span>  
  
|<span data-ttu-id="6d08b-138">MOF</span><span class="sxs-lookup"><span data-stu-id="6d08b-138">MOF</span></span>|<span data-ttu-id="6d08b-139">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6d08b-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="6d08b-140">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="6d08b-140">Namespace</span></span>|<span data-ttu-id="6d08b-141">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="6d08b-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6d08b-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6d08b-142">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceCredentials>
