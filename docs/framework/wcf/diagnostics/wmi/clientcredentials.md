---
title: ClientCredentials
ms.date: 03/30/2017
ms.assetid: 41dffd6b-8f14-4fed-aefb-2a1bb168efb3
ms.openlocfilehash: 8b6200f84f352d49cf142d9c8b97d1c2b36149b2
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50180906"
---
# <a name="clientcredentials"></a><span data-ttu-id="a6300-102">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="a6300-102">ClientCredentials</span></span>
<span data-ttu-id="a6300-103">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="a6300-103">ClientCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6300-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a6300-104">Syntax</span></span>  
  
```csharp
class ClientCredentials : Behavior  
{  
  string ClientCertificate;  
  string HttpDigest;  
  string IssuedToken;  
  string Peer;  
  string ServiceCertificate;  
  boolean SupportInteractive;  
  string UserName;  
  string Windows;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="a6300-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a6300-105">Methods</span></span>  
 <span data-ttu-id="a6300-106">ClientCredentials sınıfı herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="a6300-106">The ClientCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="a6300-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="a6300-107">Properties</span></span>  
 <span data-ttu-id="a6300-108">ClientCredentials sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="a6300-108">The ClientCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="a6300-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="a6300-109">ClientCertificate</span></span>  
 <span data-ttu-id="a6300-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="a6300-110">Data type: string</span></span>  
  
 <span data-ttu-id="a6300-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="a6300-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a6300-112">Hizmetinde kimlik doğrulaması için istemci X.509 sertifikası kullanır.</span><span class="sxs-lookup"><span data-stu-id="a6300-112">The X.509 certificate the client uses to authenticate to the service.</span></span>  
  
### <a name="httpdigest"></a><span data-ttu-id="a6300-113">HttpDigest</span><span class="sxs-lookup"><span data-stu-id="a6300-113">HttpDigest</span></span>  
 <span data-ttu-id="a6300-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="a6300-114">Data type: string</span></span>  
  
 <span data-ttu-id="a6300-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="a6300-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a6300-116">Geçerli Http Digest kimlik bilgisi.</span><span class="sxs-lookup"><span data-stu-id="a6300-116">The current Http Digest credential.</span></span>  
  
### <a name="issuedtoken"></a><span data-ttu-id="a6300-117">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="a6300-117">IssuedToken</span></span>  
 <span data-ttu-id="a6300-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="a6300-118">Data type: string</span></span>  
  
 <span data-ttu-id="a6300-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="a6300-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a6300-120">Yerel güvenlik belirteci hizmeti ile iletişim kurmada kullanılan bağlama ve uç nokta adresi.</span><span class="sxs-lookup"><span data-stu-id="a6300-120">The endpoint address and binding used to contact the local security token service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="a6300-121">Eş</span><span class="sxs-lookup"><span data-stu-id="a6300-121">Peer</span></span>  
 <span data-ttu-id="a6300-122">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="a6300-122">Data type: string</span></span>  
  
 <span data-ttu-id="a6300-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="a6300-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a6300-124">Eşdüzey düğümündeki diğer düğümlere kafes kendi kimliğini doğrulamak için kullandığı kimlik bilgileri.</span><span class="sxs-lookup"><span data-stu-id="a6300-124">The credentials that the peer node uses to authenticate itself to other nodes in the mesh.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="a6300-125">serviceCertificate</span><span class="sxs-lookup"><span data-stu-id="a6300-125">ServiceCertificate</span></span>  
 <span data-ttu-id="a6300-126">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="a6300-126">Data type: string</span></span>  
  
 <span data-ttu-id="a6300-127">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="a6300-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a6300-128">Hizmetin X.509 sertifikası.</span><span class="sxs-lookup"><span data-stu-id="a6300-128">The service's X.509 certificate.</span></span>  
  
### <a name="supportinteractive"></a><span data-ttu-id="a6300-129">SupportInteractive</span><span class="sxs-lookup"><span data-stu-id="a6300-129">SupportInteractive</span></span>  
 <span data-ttu-id="a6300-130">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="a6300-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="a6300-131">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="a6300-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a6300-132">Kimlik bilgisi etkileşimli anlaşma destekleyip desteklemediğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="a6300-132">A Boolean value that specifies whether the credential supports interactive negotiation.</span></span>  
  
### <a name="username"></a><span data-ttu-id="a6300-133">UserName</span><span class="sxs-lookup"><span data-stu-id="a6300-133">UserName</span></span>  
 <span data-ttu-id="a6300-134">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="a6300-134">Data type: string</span></span>  
  
 <span data-ttu-id="a6300-135">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="a6300-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a6300-136">Kullanıcı adı ve parola İstemcinin hizmete kendi kimliğini doğrulamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="a6300-136">The username and password the client uses to authenticate itself to the service.</span></span>  
  
### <a name="windows"></a><span data-ttu-id="a6300-137">Windows</span><span class="sxs-lookup"><span data-stu-id="a6300-137">Windows</span></span>  
 <span data-ttu-id="a6300-138">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="a6300-138">Data type: string</span></span>  
  
 <span data-ttu-id="a6300-139">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="a6300-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a6300-140">Windows kimlik bilgileri hizmete kendi kimliğini doğrulamak için istemci kullanır.</span><span class="sxs-lookup"><span data-stu-id="a6300-140">The windows credentials the client uses to authenticate itself to the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6300-141">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a6300-141">Requirements</span></span>  
  
|<span data-ttu-id="a6300-142">MOF</span><span class="sxs-lookup"><span data-stu-id="a6300-142">MOF</span></span>|<span data-ttu-id="a6300-143">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="a6300-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="a6300-144">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="a6300-144">Namespace</span></span>|<span data-ttu-id="a6300-145">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a6300-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a6300-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a6300-146">See Also</span></span>  
 <xref:System.ServiceModel.Description.ClientCredentials>
