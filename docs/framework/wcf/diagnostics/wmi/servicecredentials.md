---
title: ServiceCredentials
ms.date: 03/30/2017
ms.assetid: 9c780793-4785-46f7-add9-ac1ebeadb614
ms.openlocfilehash: d9563bd3bfe067ad83bfa03e7c6375a9db933f14
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59230934"
---
# <a name="servicecredentials"></a><span data-ttu-id="195fd-102">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="195fd-102">ServiceCredentials</span></span>
<span data-ttu-id="195fd-103">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="195fd-103">ServiceCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="195fd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="195fd-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="195fd-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="195fd-105">Methods</span></span>  
 <span data-ttu-id="195fd-106">ServiceCredentials sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="195fd-106">The ServiceCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="195fd-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="195fd-107">Properties</span></span>  
 <span data-ttu-id="195fd-108">ServiceCredentials sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="195fd-108">The ServiceCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="195fd-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="195fd-109">ClientCertificate</span></span>  
 <span data-ttu-id="195fd-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="195fd-110">Data type: string</span></span>  
  
 <span data-ttu-id="195fd-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="195fd-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="195fd-112">İstemci sertifikası kimlik doğrulaması ve sağlama ayarlarını bu hizmet için.</span><span class="sxs-lookup"><span data-stu-id="195fd-112">The client certificate authentication and provisioning settings for this service.</span></span>  
  
### <a name="issuedtokenauthentication"></a><span data-ttu-id="195fd-113">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="195fd-113">IssuedTokenAuthentication</span></span>  
 <span data-ttu-id="195fd-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="195fd-114">Data type: string</span></span>  
  
 <span data-ttu-id="195fd-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="195fd-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="195fd-116">Geçerli belirteç kimlik doğrulaması ayarlarını bu hizmet için verilmiş.</span><span class="sxs-lookup"><span data-stu-id="195fd-116">The current issued token authentication settings for this service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="195fd-117">Eş</span><span class="sxs-lookup"><span data-stu-id="195fd-117">Peer</span></span>  
 <span data-ttu-id="195fd-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="195fd-118">Data type: string</span></span>  
  
 <span data-ttu-id="195fd-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="195fd-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="195fd-120">Geçerli kimlik doğrulama ve hazırlama ayarları eş aktarım uç noktaları tarafından kullanılmak üzere kimlik bilgileri.</span><span class="sxs-lookup"><span data-stu-id="195fd-120">The current credential authentication and provisioning settings to be used by peer transport endpoints.</span></span>  
  
### <a name="secureconversationauthentication"></a><span data-ttu-id="195fd-121">Servicecredential</span><span class="sxs-lookup"><span data-stu-id="195fd-121">SecureConversationAuthentication</span></span>  
 <span data-ttu-id="195fd-122">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="195fd-122">Data type: string</span></span>  
  
 <span data-ttu-id="195fd-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="195fd-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="195fd-124">Geçerli bir güvenli konuşma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="195fd-124">Specifies the current secure conversation settings.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="195fd-125">serviceCertificate</span><span class="sxs-lookup"><span data-stu-id="195fd-125">ServiceCertificate</span></span>  
 <span data-ttu-id="195fd-126">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="195fd-126">Data type: string</span></span>  
  
 <span data-ttu-id="195fd-127">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="195fd-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="195fd-128">Bu hizmetle ilişkili sertifika.</span><span class="sxs-lookup"><span data-stu-id="195fd-128">The certificate associated with this service.</span></span>  
  
### <a name="usernameauthentication"></a><span data-ttu-id="195fd-129">UserNameAuthentication</span><span class="sxs-lookup"><span data-stu-id="195fd-129">UserNameAuthentication</span></span>  
 <span data-ttu-id="195fd-130">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="195fd-130">Data type: string</span></span>  
  
 <span data-ttu-id="195fd-131">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="195fd-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="195fd-132">Bu hizmet için kullanıcı adı/parola ayarlar.</span><span class="sxs-lookup"><span data-stu-id="195fd-132">The username/password settings for this service.</span></span>  
  
### <a name="windowsauthentication"></a><span data-ttu-id="195fd-133">WindowsAuthentication</span><span class="sxs-lookup"><span data-stu-id="195fd-133">WindowsAuthentication</span></span>  
 <span data-ttu-id="195fd-134">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="195fd-134">Data type: string</span></span>  
  
 <span data-ttu-id="195fd-135">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="195fd-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="195fd-136">Bu hizmet Windows kimlik doğrulama ayarları.</span><span class="sxs-lookup"><span data-stu-id="195fd-136">The Windows authentication settings for this service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="195fd-137">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="195fd-137">Requirements</span></span>  
  
|<span data-ttu-id="195fd-138">MOF</span><span class="sxs-lookup"><span data-stu-id="195fd-138">MOF</span></span>|<span data-ttu-id="195fd-139">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="195fd-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="195fd-140">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="195fd-140">Namespace</span></span>|<span data-ttu-id="195fd-141">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="195fd-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="195fd-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="195fd-142">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceCredentials>
