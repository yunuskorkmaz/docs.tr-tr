---
description: 'Daha fazla bilgi edinin: ClientCredentials'
title: ClientCredentials
ms.date: 03/30/2017
ms.assetid: 41dffd6b-8f14-4fed-aefb-2a1bb168efb3
ms.openlocfilehash: 7b0b5a05e5b61de717567de664079f2ed1e20f6b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757676"
---
# <a name="clientcredentials"></a><span data-ttu-id="440d4-103">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="440d4-103">ClientCredentials</span></span>

<span data-ttu-id="440d4-104">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="440d4-104">ClientCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="440d4-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="440d4-105">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="440d4-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="440d4-106">Methods</span></span>  

 <span data-ttu-id="440d4-107">ClientCredentials sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="440d4-107">The ClientCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="440d4-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="440d4-108">Properties</span></span>  

 <span data-ttu-id="440d4-109">ClientCredentials sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="440d4-109">The ClientCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="440d4-110">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="440d4-110">ClientCertificate</span></span>  

 <span data-ttu-id="440d4-111">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="440d4-111">Data type: string</span></span>  
  
 <span data-ttu-id="440d4-112">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="440d4-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="440d4-113">İstemcinin hizmet kimliğini doğrulamak için kullandığı X. 509.440 sertifikası.</span><span class="sxs-lookup"><span data-stu-id="440d4-113">The X.509 certificate the client uses to authenticate to the service.</span></span>  
  
### <a name="httpdigest"></a><span data-ttu-id="440d4-114">HttpDigest</span><span class="sxs-lookup"><span data-stu-id="440d4-114">HttpDigest</span></span>  

 <span data-ttu-id="440d4-115">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="440d4-115">Data type: string</span></span>  
  
 <span data-ttu-id="440d4-116">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="440d4-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="440d4-117">Geçerli http Digest kimlik bilgileri.</span><span class="sxs-lookup"><span data-stu-id="440d4-117">The current Http Digest credential.</span></span>  
  
### <a name="issuedtoken"></a><span data-ttu-id="440d4-118">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="440d4-118">IssuedToken</span></span>  

 <span data-ttu-id="440d4-119">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="440d4-119">Data type: string</span></span>  
  
 <span data-ttu-id="440d4-120">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="440d4-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="440d4-121">Yerel güvenlik belirteci hizmetiyle iletişim kurmak için kullanılan uç nokta adresi ve bağlama.</span><span class="sxs-lookup"><span data-stu-id="440d4-121">The endpoint address and binding used to contact the local security token service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="440d4-122">Eşdüzey hizmet sağlayıcı</span><span class="sxs-lookup"><span data-stu-id="440d4-122">Peer</span></span>  

 <span data-ttu-id="440d4-123">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="440d4-123">Data type: string</span></span>  
  
 <span data-ttu-id="440d4-124">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="440d4-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="440d4-125">Eş düğümün, ağ üzerindeki diğer düğümlere kimliğini doğrulamak için kullandığı kimlik bilgileri.</span><span class="sxs-lookup"><span data-stu-id="440d4-125">The credentials that the peer node uses to authenticate itself to other nodes in the mesh.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="440d4-126">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="440d4-126">ServiceCertificate</span></span>  

 <span data-ttu-id="440d4-127">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="440d4-127">Data type: string</span></span>  
  
 <span data-ttu-id="440d4-128">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="440d4-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="440d4-129">Hizmetin X. 509.440 sertifikası.</span><span class="sxs-lookup"><span data-stu-id="440d4-129">The service's X.509 certificate.</span></span>  
  
### <a name="supportinteractive"></a><span data-ttu-id="440d4-130">Supportınteractıve</span><span class="sxs-lookup"><span data-stu-id="440d4-130">SupportInteractive</span></span>  

 <span data-ttu-id="440d4-131">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="440d4-131">Data type: boolean</span></span>  
  
 <span data-ttu-id="440d4-132">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="440d4-132">Access type: Read-only</span></span>  
  
 <span data-ttu-id="440d4-133">Kimlik bilgisinin etkileşimli anlaşmayı destekleyip desteklemediğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="440d4-133">A Boolean value that specifies whether the credential supports interactive negotiation.</span></span>  
  
### <a name="username"></a><span data-ttu-id="440d4-134">UserName</span><span class="sxs-lookup"><span data-stu-id="440d4-134">UserName</span></span>  

 <span data-ttu-id="440d4-135">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="440d4-135">Data type: string</span></span>  
  
 <span data-ttu-id="440d4-136">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="440d4-136">Access type: Read-only</span></span>  
  
 <span data-ttu-id="440d4-137">İstemcinin hizmete kendi kimliğini doğrulamak için kullandığı Kullanıcı adı ve parola.</span><span class="sxs-lookup"><span data-stu-id="440d4-137">The username and password the client uses to authenticate itself to the service.</span></span>  
  
### <a name="windows"></a><span data-ttu-id="440d4-138">Windows</span><span class="sxs-lookup"><span data-stu-id="440d4-138">Windows</span></span>  

 <span data-ttu-id="440d4-139">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="440d4-139">Data type: string</span></span>  
  
 <span data-ttu-id="440d4-140">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="440d4-140">Access type: Read-only</span></span>  
  
 <span data-ttu-id="440d4-141">İstemcinin hizmete kendi kimliğini doğrulamak için kullandığı Windows kimlik bilgileri.</span><span class="sxs-lookup"><span data-stu-id="440d4-141">The windows credentials the client uses to authenticate itself to the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="440d4-142">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="440d4-142">Requirements</span></span>  
  
|<span data-ttu-id="440d4-143">MOF</span><span class="sxs-lookup"><span data-stu-id="440d4-143">MOF</span></span>|<span data-ttu-id="440d4-144">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="440d4-144">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="440d4-145">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="440d4-145">Namespace</span></span>|<span data-ttu-id="440d4-146">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="440d4-146">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="440d4-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="440d4-147">See also</span></span>

- <xref:System.ServiceModel.Description.ClientCredentials>
