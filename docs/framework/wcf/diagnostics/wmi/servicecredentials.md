---
title: ServiceCredentials
ms.date: 03/30/2017
ms.assetid: 9c780793-4785-46f7-add9-ac1ebeadb614
ms.openlocfilehash: bf906e09ae71d26f8e95877f1c545c0724d57b9f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485771"
---
# <a name="servicecredentials"></a><span data-ttu-id="aba9c-102">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="aba9c-102">ServiceCredentials</span></span>
<span data-ttu-id="aba9c-103">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="aba9c-103">ServiceCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aba9c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aba9c-104">Syntax</span></span>  
  
```  
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
  
## <a name="methods"></a><span data-ttu-id="aba9c-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="aba9c-105">Methods</span></span>  
 <span data-ttu-id="aba9c-106">ServiceCredentials sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="aba9c-106">The ServiceCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="aba9c-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="aba9c-107">Properties</span></span>  
 <span data-ttu-id="aba9c-108">ServiceCredentials sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="aba9c-108">The ServiceCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="aba9c-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="aba9c-109">ClientCertificate</span></span>  
 <span data-ttu-id="aba9c-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="aba9c-110">Data type: string</span></span>  
  
 <span data-ttu-id="aba9c-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="aba9c-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aba9c-112">Sertifika kimlik doğrulaması ve sağlama için istemci ayarlarını bu hizmet.</span><span class="sxs-lookup"><span data-stu-id="aba9c-112">The client certificate authentication and provisioning settings for this service.</span></span>  
  
### <a name="issuedtokenauthentication"></a><span data-ttu-id="aba9c-113">IssuedTokenAuthentication</span><span class="sxs-lookup"><span data-stu-id="aba9c-113">IssuedTokenAuthentication</span></span>  
 <span data-ttu-id="aba9c-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="aba9c-114">Data type: string</span></span>  
  
 <span data-ttu-id="aba9c-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="aba9c-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aba9c-116">Geçerli belirteç kimlik doğrulama ayarlarını bu hizmet için verilmiş.</span><span class="sxs-lookup"><span data-stu-id="aba9c-116">The current issued token authentication settings for this service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="aba9c-117">Eş</span><span class="sxs-lookup"><span data-stu-id="aba9c-117">Peer</span></span>  
 <span data-ttu-id="aba9c-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="aba9c-118">Data type: string</span></span>  
  
 <span data-ttu-id="aba9c-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="aba9c-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aba9c-120">Geçerli kimlik doğrulama ve eş aktarım uç noktaları tarafından kullanılacak ayarları sağlama kimlik bilgileri.</span><span class="sxs-lookup"><span data-stu-id="aba9c-120">The current credential authentication and provisioning settings to be used by peer transport endpoints.</span></span>  
  
### <a name="secureconversationauthentication"></a><span data-ttu-id="aba9c-121">Servicecredential</span><span class="sxs-lookup"><span data-stu-id="aba9c-121">SecureConversationAuthentication</span></span>  
 <span data-ttu-id="aba9c-122">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="aba9c-122">Data type: string</span></span>  
  
 <span data-ttu-id="aba9c-123">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="aba9c-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aba9c-124">Geçerli güvenli konuşma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="aba9c-124">Specifies the current secure conversation settings.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="aba9c-125">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="aba9c-125">ServiceCertificate</span></span>  
 <span data-ttu-id="aba9c-126">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="aba9c-126">Data type: string</span></span>  
  
 <span data-ttu-id="aba9c-127">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="aba9c-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aba9c-128">Bu hizmet ile ilişkili sertifika.</span><span class="sxs-lookup"><span data-stu-id="aba9c-128">The certificate associated with this service.</span></span>  
  
### <a name="usernameauthentication"></a><span data-ttu-id="aba9c-129">UserNameAuthentication</span><span class="sxs-lookup"><span data-stu-id="aba9c-129">UserNameAuthentication</span></span>  
 <span data-ttu-id="aba9c-130">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="aba9c-130">Data type: string</span></span>  
  
 <span data-ttu-id="aba9c-131">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="aba9c-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aba9c-132">Bu hizmet için kullanıcı adı/parola ayarları.</span><span class="sxs-lookup"><span data-stu-id="aba9c-132">The username/password settings for this service.</span></span>  
  
### <a name="windowsauthentication"></a><span data-ttu-id="aba9c-133">WindowsAuthentication</span><span class="sxs-lookup"><span data-stu-id="aba9c-133">WindowsAuthentication</span></span>  
 <span data-ttu-id="aba9c-134">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="aba9c-134">Data type: string</span></span>  
  
 <span data-ttu-id="aba9c-135">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="aba9c-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aba9c-136">Bu hizmet Windows kimlik doğrulama ayarları.</span><span class="sxs-lookup"><span data-stu-id="aba9c-136">The Windows authentication settings for this service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aba9c-137">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aba9c-137">Requirements</span></span>  
  
|<span data-ttu-id="aba9c-138">MOF</span><span class="sxs-lookup"><span data-stu-id="aba9c-138">MOF</span></span>|<span data-ttu-id="aba9c-139">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="aba9c-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="aba9c-140">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="aba9c-140">Namespace</span></span>|<span data-ttu-id="aba9c-141">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="aba9c-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="aba9c-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="aba9c-142">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceCredentials>
