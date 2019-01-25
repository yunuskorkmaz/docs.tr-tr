---
title: ServiceCredentials
ms.date: 03/30/2017
ms.assetid: 9c780793-4785-46f7-add9-ac1ebeadb614
ms.openlocfilehash: 18100ac36b5116c2373171ff795fc23b75bbd6f4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54572126"
---
# <a name="servicecredentials"></a><span data-ttu-id="81a5c-102">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="81a5c-102">ServiceCredentials</span></span>
<span data-ttu-id="81a5c-103">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="81a5c-103">ServiceCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81a5c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="81a5c-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="81a5c-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="81a5c-105">Methods</span></span>  
 <span data-ttu-id="81a5c-106">ServiceCredentials sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="81a5c-106">The ServiceCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="81a5c-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="81a5c-107">Properties</span></span>  
 <span data-ttu-id="81a5c-108">ServiceCredentials sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="81a5c-108">The ServiceCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="81a5c-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="81a5c-109">ClientCertificate</span></span>  
 <span data-ttu-id="81a5c-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="81a5c-110">Data type: string</span></span>  
  
 <span data-ttu-id="81a5c-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="81a5c-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="81a5c-112">İstemci sertifikası kimlik doğrulaması ve sağlama ayarlarını bu hizmet için.</span><span class="sxs-lookup"><span data-stu-id="81a5c-112">The client certificate authentication and provisioning settings for this service.</span></span>  
  
### <a name="issuedtokenauthentication"></a><span data-ttu-id="81a5c-113">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="81a5c-113">IssuedTokenAuthentication</span></span>  
 <span data-ttu-id="81a5c-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="81a5c-114">Data type: string</span></span>  
  
 <span data-ttu-id="81a5c-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="81a5c-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="81a5c-116">Geçerli belirteç kimlik doğrulaması ayarlarını bu hizmet için verilmiş.</span><span class="sxs-lookup"><span data-stu-id="81a5c-116">The current issued token authentication settings for this service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="81a5c-117">Eş</span><span class="sxs-lookup"><span data-stu-id="81a5c-117">Peer</span></span>  
 <span data-ttu-id="81a5c-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="81a5c-118">Data type: string</span></span>  
  
 <span data-ttu-id="81a5c-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="81a5c-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="81a5c-120">Geçerli kimlik doğrulama ve hazırlama ayarları eş aktarım uç noktaları tarafından kullanılmak üzere kimlik bilgileri.</span><span class="sxs-lookup"><span data-stu-id="81a5c-120">The current credential authentication and provisioning settings to be used by peer transport endpoints.</span></span>  
  
### <a name="secureconversationauthentication"></a><span data-ttu-id="81a5c-121">Servicecredential</span><span class="sxs-lookup"><span data-stu-id="81a5c-121">SecureConversationAuthentication</span></span>  
 <span data-ttu-id="81a5c-122">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="81a5c-122">Data type: string</span></span>  
  
 <span data-ttu-id="81a5c-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="81a5c-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="81a5c-124">Geçerli bir güvenli konuşma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="81a5c-124">Specifies the current secure conversation settings.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="81a5c-125">serviceCertificate</span><span class="sxs-lookup"><span data-stu-id="81a5c-125">ServiceCertificate</span></span>  
 <span data-ttu-id="81a5c-126">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="81a5c-126">Data type: string</span></span>  
  
 <span data-ttu-id="81a5c-127">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="81a5c-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="81a5c-128">Bu hizmetle ilişkili sertifika.</span><span class="sxs-lookup"><span data-stu-id="81a5c-128">The certificate associated with this service.</span></span>  
  
### <a name="usernameauthentication"></a><span data-ttu-id="81a5c-129">UserNameAuthentication</span><span class="sxs-lookup"><span data-stu-id="81a5c-129">UserNameAuthentication</span></span>  
 <span data-ttu-id="81a5c-130">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="81a5c-130">Data type: string</span></span>  
  
 <span data-ttu-id="81a5c-131">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="81a5c-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="81a5c-132">Bu hizmet için kullanıcı adı/parola ayarlar.</span><span class="sxs-lookup"><span data-stu-id="81a5c-132">The username/password settings for this service.</span></span>  
  
### <a name="windowsauthentication"></a><span data-ttu-id="81a5c-133">WindowsAuthentication</span><span class="sxs-lookup"><span data-stu-id="81a5c-133">WindowsAuthentication</span></span>  
 <span data-ttu-id="81a5c-134">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="81a5c-134">Data type: string</span></span>  
  
 <span data-ttu-id="81a5c-135">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="81a5c-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="81a5c-136">Bu hizmet Windows kimlik doğrulama ayarları.</span><span class="sxs-lookup"><span data-stu-id="81a5c-136">The Windows authentication settings for this service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81a5c-137">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="81a5c-137">Requirements</span></span>  
  
|<span data-ttu-id="81a5c-138">MOF</span><span class="sxs-lookup"><span data-stu-id="81a5c-138">MOF</span></span>|<span data-ttu-id="81a5c-139">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="81a5c-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="81a5c-140">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="81a5c-140">Namespace</span></span>|<span data-ttu-id="81a5c-141">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="81a5c-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="81a5c-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="81a5c-142">See also</span></span>
- <xref:System.ServiceModel.Description.ServiceCredentials>
