---
title: ClientCredentials
ms.date: 03/30/2017
ms.assetid: 41dffd6b-8f14-4fed-aefb-2a1bb168efb3
ms.openlocfilehash: c3adc675bb6c1e9011459a88fd7dc8e8cf63a880
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59771211"
---
# <a name="clientcredentials"></a><span data-ttu-id="307b6-102">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="307b6-102">ClientCredentials</span></span>
<span data-ttu-id="307b6-103">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="307b6-103">ClientCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="307b6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="307b6-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="307b6-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="307b6-105">Methods</span></span>  
 <span data-ttu-id="307b6-106">ClientCredentials sınıfı herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="307b6-106">The ClientCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="307b6-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="307b6-107">Properties</span></span>  
 <span data-ttu-id="307b6-108">ClientCredentials sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="307b6-108">The ClientCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="307b6-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="307b6-109">ClientCertificate</span></span>  
 <span data-ttu-id="307b6-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="307b6-110">Data type: string</span></span>  
  
 <span data-ttu-id="307b6-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="307b6-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="307b6-112">Hizmetinde kimlik doğrulaması için istemci X.509 sertifikası kullanır.</span><span class="sxs-lookup"><span data-stu-id="307b6-112">The X.509 certificate the client uses to authenticate to the service.</span></span>  
  
### <a name="httpdigest"></a><span data-ttu-id="307b6-113">HttpDigest</span><span class="sxs-lookup"><span data-stu-id="307b6-113">HttpDigest</span></span>  
 <span data-ttu-id="307b6-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="307b6-114">Data type: string</span></span>  
  
 <span data-ttu-id="307b6-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="307b6-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="307b6-116">Geçerli Http Digest kimlik bilgisi.</span><span class="sxs-lookup"><span data-stu-id="307b6-116">The current Http Digest credential.</span></span>  
  
### <a name="issuedtoken"></a><span data-ttu-id="307b6-117">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="307b6-117">IssuedToken</span></span>  
 <span data-ttu-id="307b6-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="307b6-118">Data type: string</span></span>  
  
 <span data-ttu-id="307b6-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="307b6-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="307b6-120">Yerel güvenlik belirteci hizmeti ile iletişim kurmada kullanılan bağlama ve uç nokta adresi.</span><span class="sxs-lookup"><span data-stu-id="307b6-120">The endpoint address and binding used to contact the local security token service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="307b6-121">Eş</span><span class="sxs-lookup"><span data-stu-id="307b6-121">Peer</span></span>  
 <span data-ttu-id="307b6-122">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="307b6-122">Data type: string</span></span>  
  
 <span data-ttu-id="307b6-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="307b6-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="307b6-124">Eşdüzey düğümündeki diğer düğümlere kafes kendi kimliğini doğrulamak için kullandığı kimlik bilgileri.</span><span class="sxs-lookup"><span data-stu-id="307b6-124">The credentials that the peer node uses to authenticate itself to other nodes in the mesh.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="307b6-125">serviceCertificate</span><span class="sxs-lookup"><span data-stu-id="307b6-125">ServiceCertificate</span></span>  
 <span data-ttu-id="307b6-126">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="307b6-126">Data type: string</span></span>  
  
 <span data-ttu-id="307b6-127">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="307b6-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="307b6-128">Hizmetin X.509 sertifikası.</span><span class="sxs-lookup"><span data-stu-id="307b6-128">The service's X.509 certificate.</span></span>  
  
### <a name="supportinteractive"></a><span data-ttu-id="307b6-129">SupportInteractive</span><span class="sxs-lookup"><span data-stu-id="307b6-129">SupportInteractive</span></span>  
 <span data-ttu-id="307b6-130">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="307b6-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="307b6-131">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="307b6-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="307b6-132">Kimlik bilgisi etkileşimli anlaşma destekleyip desteklemediğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="307b6-132">A Boolean value that specifies whether the credential supports interactive negotiation.</span></span>  
  
### <a name="username"></a><span data-ttu-id="307b6-133">UserName</span><span class="sxs-lookup"><span data-stu-id="307b6-133">UserName</span></span>  
 <span data-ttu-id="307b6-134">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="307b6-134">Data type: string</span></span>  
  
 <span data-ttu-id="307b6-135">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="307b6-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="307b6-136">Kullanıcı adı ve parola İstemcinin hizmete kendi kimliğini doğrulamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="307b6-136">The username and password the client uses to authenticate itself to the service.</span></span>  
  
### <a name="windows"></a><span data-ttu-id="307b6-137">Windows</span><span class="sxs-lookup"><span data-stu-id="307b6-137">Windows</span></span>  
 <span data-ttu-id="307b6-138">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="307b6-138">Data type: string</span></span>  
  
 <span data-ttu-id="307b6-139">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="307b6-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="307b6-140">Windows kimlik bilgileri hizmete kendi kimliğini doğrulamak için istemci kullanır.</span><span class="sxs-lookup"><span data-stu-id="307b6-140">The windows credentials the client uses to authenticate itself to the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="307b6-141">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="307b6-141">Requirements</span></span>  
  
|<span data-ttu-id="307b6-142">MOF</span><span class="sxs-lookup"><span data-stu-id="307b6-142">MOF</span></span>|<span data-ttu-id="307b6-143">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="307b6-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="307b6-144">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="307b6-144">Namespace</span></span>|<span data-ttu-id="307b6-145">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="307b6-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="307b6-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="307b6-146">See also</span></span>

- <xref:System.ServiceModel.Description.ClientCredentials>
