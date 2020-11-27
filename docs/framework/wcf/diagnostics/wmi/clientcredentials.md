---
title: ClientCredentials
ms.date: 03/30/2017
ms.assetid: 41dffd6b-8f14-4fed-aefb-2a1bb168efb3
ms.openlocfilehash: c63e1b3de464b306f46e2f0935b1208d7262925a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96274198"
---
# <a name="clientcredentials"></a><span data-ttu-id="b630a-102">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="b630a-102">ClientCredentials</span></span>

<span data-ttu-id="b630a-103">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="b630a-103">ClientCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b630a-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="b630a-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="b630a-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b630a-105">Methods</span></span>  

 <span data-ttu-id="b630a-106">ClientCredentials sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="b630a-106">The ClientCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b630a-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="b630a-107">Properties</span></span>  

 <span data-ttu-id="b630a-108">ClientCredentials sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="b630a-108">The ClientCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="b630a-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="b630a-109">ClientCertificate</span></span>  

 <span data-ttu-id="b630a-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="b630a-110">Data type: string</span></span>  
  
 <span data-ttu-id="b630a-111">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="b630a-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b630a-112">İstemcinin hizmet kimliğini doğrulamak için kullandığı X. 509.440 sertifikası.</span><span class="sxs-lookup"><span data-stu-id="b630a-112">The X.509 certificate the client uses to authenticate to the service.</span></span>  
  
### <a name="httpdigest"></a><span data-ttu-id="b630a-113">HttpDigest</span><span class="sxs-lookup"><span data-stu-id="b630a-113">HttpDigest</span></span>  

 <span data-ttu-id="b630a-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="b630a-114">Data type: string</span></span>  
  
 <span data-ttu-id="b630a-115">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="b630a-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b630a-116">Geçerli http Digest kimlik bilgileri.</span><span class="sxs-lookup"><span data-stu-id="b630a-116">The current Http Digest credential.</span></span>  
  
### <a name="issuedtoken"></a><span data-ttu-id="b630a-117">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="b630a-117">IssuedToken</span></span>  

 <span data-ttu-id="b630a-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="b630a-118">Data type: string</span></span>  
  
 <span data-ttu-id="b630a-119">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="b630a-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b630a-120">Yerel güvenlik belirteci hizmetiyle iletişim kurmak için kullanılan uç nokta adresi ve bağlama.</span><span class="sxs-lookup"><span data-stu-id="b630a-120">The endpoint address and binding used to contact the local security token service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="b630a-121">Eşdüzey hizmet sağlayıcı</span><span class="sxs-lookup"><span data-stu-id="b630a-121">Peer</span></span>  

 <span data-ttu-id="b630a-122">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="b630a-122">Data type: string</span></span>  
  
 <span data-ttu-id="b630a-123">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="b630a-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b630a-124">Eş düğümün, ağ üzerindeki diğer düğümlere kimliğini doğrulamak için kullandığı kimlik bilgileri.</span><span class="sxs-lookup"><span data-stu-id="b630a-124">The credentials that the peer node uses to authenticate itself to other nodes in the mesh.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="b630a-125">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="b630a-125">ServiceCertificate</span></span>  

 <span data-ttu-id="b630a-126">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="b630a-126">Data type: string</span></span>  
  
 <span data-ttu-id="b630a-127">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="b630a-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b630a-128">Hizmetin X. 509.440 sertifikası.</span><span class="sxs-lookup"><span data-stu-id="b630a-128">The service's X.509 certificate.</span></span>  
  
### <a name="supportinteractive"></a><span data-ttu-id="b630a-129">Supportınteractıve</span><span class="sxs-lookup"><span data-stu-id="b630a-129">SupportInteractive</span></span>  

 <span data-ttu-id="b630a-130">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="b630a-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="b630a-131">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="b630a-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b630a-132">Kimlik bilgisinin etkileşimli anlaşmayı destekleyip desteklemediğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="b630a-132">A Boolean value that specifies whether the credential supports interactive negotiation.</span></span>  
  
### <a name="username"></a><span data-ttu-id="b630a-133">UserName</span><span class="sxs-lookup"><span data-stu-id="b630a-133">UserName</span></span>  

 <span data-ttu-id="b630a-134">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="b630a-134">Data type: string</span></span>  
  
 <span data-ttu-id="b630a-135">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="b630a-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b630a-136">İstemcinin hizmete kendi kimliğini doğrulamak için kullandığı Kullanıcı adı ve parola.</span><span class="sxs-lookup"><span data-stu-id="b630a-136">The username and password the client uses to authenticate itself to the service.</span></span>  
  
### <a name="windows"></a><span data-ttu-id="b630a-137">Windows</span><span class="sxs-lookup"><span data-stu-id="b630a-137">Windows</span></span>  

 <span data-ttu-id="b630a-138">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="b630a-138">Data type: string</span></span>  
  
 <span data-ttu-id="b630a-139">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="b630a-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b630a-140">İstemcinin hizmete kendi kimliğini doğrulamak için kullandığı Windows kimlik bilgileri.</span><span class="sxs-lookup"><span data-stu-id="b630a-140">The windows credentials the client uses to authenticate itself to the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b630a-141">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b630a-141">Requirements</span></span>  
  
|<span data-ttu-id="b630a-142">MOF</span><span class="sxs-lookup"><span data-stu-id="b630a-142">MOF</span></span>|<span data-ttu-id="b630a-143">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b630a-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="b630a-144">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="b630a-144">Namespace</span></span>|<span data-ttu-id="b630a-145">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="b630a-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b630a-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b630a-146">See also</span></span>

- <xref:System.ServiceModel.Description.ClientCredentials>
