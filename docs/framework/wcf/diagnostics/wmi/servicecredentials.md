---
title: ServiceCredentials
ms.date: 03/30/2017
ms.assetid: 9c780793-4785-46f7-add9-ac1ebeadb614
ms.openlocfilehash: d9563bd3bfe067ad83bfa03e7c6375a9db933f14
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59772108"
---
# <a name="servicecredentials"></a><span data-ttu-id="96122-102">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="96122-102">ServiceCredentials</span></span>
<span data-ttu-id="96122-103">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="96122-103">ServiceCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96122-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="96122-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="96122-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="96122-105">Methods</span></span>  
 <span data-ttu-id="96122-106">ServiceCredentials sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="96122-106">The ServiceCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="96122-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="96122-107">Properties</span></span>  
 <span data-ttu-id="96122-108">ServiceCredentials sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="96122-108">The ServiceCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="96122-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="96122-109">ClientCertificate</span></span>  
 <span data-ttu-id="96122-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="96122-110">Data type: string</span></span>  
  
 <span data-ttu-id="96122-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="96122-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="96122-112">İstemci sertifikası kimlik doğrulaması ve sağlama ayarlarını bu hizmet için.</span><span class="sxs-lookup"><span data-stu-id="96122-112">The client certificate authentication and provisioning settings for this service.</span></span>  
  
### <a name="issuedtokenauthentication"></a><span data-ttu-id="96122-113">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="96122-113">IssuedTokenAuthentication</span></span>  
 <span data-ttu-id="96122-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="96122-114">Data type: string</span></span>  
  
 <span data-ttu-id="96122-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="96122-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="96122-116">Geçerli belirteç kimlik doğrulaması ayarlarını bu hizmet için verilmiş.</span><span class="sxs-lookup"><span data-stu-id="96122-116">The current issued token authentication settings for this service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="96122-117">Eş</span><span class="sxs-lookup"><span data-stu-id="96122-117">Peer</span></span>  
 <span data-ttu-id="96122-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="96122-118">Data type: string</span></span>  
  
 <span data-ttu-id="96122-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="96122-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="96122-120">Geçerli kimlik doğrulama ve hazırlama ayarları eş aktarım uç noktaları tarafından kullanılmak üzere kimlik bilgileri.</span><span class="sxs-lookup"><span data-stu-id="96122-120">The current credential authentication and provisioning settings to be used by peer transport endpoints.</span></span>  
  
### <a name="secureconversationauthentication"></a><span data-ttu-id="96122-121">Servicecredential</span><span class="sxs-lookup"><span data-stu-id="96122-121">SecureConversationAuthentication</span></span>  
 <span data-ttu-id="96122-122">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="96122-122">Data type: string</span></span>  
  
 <span data-ttu-id="96122-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="96122-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="96122-124">Geçerli bir güvenli konuşma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="96122-124">Specifies the current secure conversation settings.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="96122-125">serviceCertificate</span><span class="sxs-lookup"><span data-stu-id="96122-125">ServiceCertificate</span></span>  
 <span data-ttu-id="96122-126">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="96122-126">Data type: string</span></span>  
  
 <span data-ttu-id="96122-127">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="96122-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="96122-128">Bu hizmetle ilişkili sertifika.</span><span class="sxs-lookup"><span data-stu-id="96122-128">The certificate associated with this service.</span></span>  
  
### <a name="usernameauthentication"></a><span data-ttu-id="96122-129">UserNameAuthentication</span><span class="sxs-lookup"><span data-stu-id="96122-129">UserNameAuthentication</span></span>  
 <span data-ttu-id="96122-130">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="96122-130">Data type: string</span></span>  
  
 <span data-ttu-id="96122-131">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="96122-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="96122-132">Bu hizmet için kullanıcı adı/parola ayarlar.</span><span class="sxs-lookup"><span data-stu-id="96122-132">The username/password settings for this service.</span></span>  
  
### <a name="windowsauthentication"></a><span data-ttu-id="96122-133">WindowsAuthentication</span><span class="sxs-lookup"><span data-stu-id="96122-133">WindowsAuthentication</span></span>  
 <span data-ttu-id="96122-134">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="96122-134">Data type: string</span></span>  
  
 <span data-ttu-id="96122-135">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="96122-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="96122-136">Bu hizmet Windows kimlik doğrulama ayarları.</span><span class="sxs-lookup"><span data-stu-id="96122-136">The Windows authentication settings for this service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96122-137">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="96122-137">Requirements</span></span>  
  
|<span data-ttu-id="96122-138">MOF</span><span class="sxs-lookup"><span data-stu-id="96122-138">MOF</span></span>|<span data-ttu-id="96122-139">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="96122-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="96122-140">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="96122-140">Namespace</span></span>|<span data-ttu-id="96122-141">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="96122-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="96122-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="96122-142">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceCredentials>
