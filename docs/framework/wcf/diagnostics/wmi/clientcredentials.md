---
title: ClientCredentials
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 41dffd6b-8f14-4fed-aefb-2a1bb168efb3
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 68a2fa36c8a4fa1fde3ca8d8aaf1898060ea972f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="clientcredentials"></a><span data-ttu-id="e9b34-102">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="e9b34-102">ClientCredentials</span></span>
<span data-ttu-id="e9b34-103">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="e9b34-103">ClientCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9b34-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e9b34-104">Syntax</span></span>  
  
```  
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
  
## <a name="methods"></a><span data-ttu-id="e9b34-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e9b34-105">Methods</span></span>  
 <span data-ttu-id="e9b34-106">ClientCredentials sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="e9b34-106">The ClientCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e9b34-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e9b34-107">Properties</span></span>  
 <span data-ttu-id="e9b34-108">ClientCredentials sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="e9b34-108">The ClientCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="e9b34-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="e9b34-109">ClientCertificate</span></span>  
 <span data-ttu-id="e9b34-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="e9b34-110">Data type: string</span></span>  
  
 <span data-ttu-id="e9b34-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e9b34-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e9b34-112">X.509 sertifikası istemci, bir hizmetin kimliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="e9b34-112">The X.509 certificate the client uses to authenticate to the service.</span></span>  
  
### <a name="httpdigest"></a><span data-ttu-id="e9b34-113">HttpDigest</span><span class="sxs-lookup"><span data-stu-id="e9b34-113">HttpDigest</span></span>  
 <span data-ttu-id="e9b34-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="e9b34-114">Data type: string</span></span>  
  
 <span data-ttu-id="e9b34-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e9b34-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e9b34-116">Geçerli Http Digest kimlik bilgileri.</span><span class="sxs-lookup"><span data-stu-id="e9b34-116">The current Http Digest credential.</span></span>  
  
### <a name="issuedtoken"></a><span data-ttu-id="e9b34-117">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="e9b34-117">IssuedToken</span></span>  
 <span data-ttu-id="e9b34-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="e9b34-118">Data type: string</span></span>  
  
 <span data-ttu-id="e9b34-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e9b34-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e9b34-120">Uç noktası adresi ve yerel güvenlik belirteci hizmeti ile iletişim kurmada kullanılan bağlama.</span><span class="sxs-lookup"><span data-stu-id="e9b34-120">The endpoint address and binding used to contact the local security token service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="e9b34-121">Eş</span><span class="sxs-lookup"><span data-stu-id="e9b34-121">Peer</span></span>  
 <span data-ttu-id="e9b34-122">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="e9b34-122">Data type: string</span></span>  
  
 <span data-ttu-id="e9b34-123">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e9b34-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e9b34-124">Eş düğüm kafes içindeki diğer düğümlere kendi kimliğini doğrulamak için kullandığı kimlik bilgileri.</span><span class="sxs-lookup"><span data-stu-id="e9b34-124">The credentials that the peer node uses to authenticate itself to other nodes in the mesh.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="e9b34-125">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="e9b34-125">ServiceCertificate</span></span>  
 <span data-ttu-id="e9b34-126">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="e9b34-126">Data type: string</span></span>  
  
 <span data-ttu-id="e9b34-127">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e9b34-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e9b34-128">Hizmetin X.509 sertifikası.</span><span class="sxs-lookup"><span data-stu-id="e9b34-128">The service's X.509 certificate.</span></span>  
  
### <a name="supportinteractive"></a><span data-ttu-id="e9b34-129">SupportInteractive</span><span class="sxs-lookup"><span data-stu-id="e9b34-129">SupportInteractive</span></span>  
 <span data-ttu-id="e9b34-130">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="e9b34-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="e9b34-131">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e9b34-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e9b34-132">Kimlik bilgisi etkileşimli anlaşmayı destekleyip desteklemediğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="e9b34-132">A Boolean value that specifies whether the credential supports interactive negotiation.</span></span>  
  
### <a name="username"></a><span data-ttu-id="e9b34-133">UserName</span><span class="sxs-lookup"><span data-stu-id="e9b34-133">UserName</span></span>  
 <span data-ttu-id="e9b34-134">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="e9b34-134">Data type: string</span></span>  
  
 <span data-ttu-id="e9b34-135">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e9b34-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e9b34-136">Kullanıcı adı ve parola istemci hizmete kendi kimliğini doğrulamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="e9b34-136">The username and password the client uses to authenticate itself to the service.</span></span>  
  
### <a name="windows"></a><span data-ttu-id="e9b34-137">Windows</span><span class="sxs-lookup"><span data-stu-id="e9b34-137">Windows</span></span>  
 <span data-ttu-id="e9b34-138">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="e9b34-138">Data type: string</span></span>  
  
 <span data-ttu-id="e9b34-139">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e9b34-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e9b34-140">Windows kimlik bilgileri hizmete kendi kimliğini doğrulamak için istemci kullanır.</span><span class="sxs-lookup"><span data-stu-id="e9b34-140">The windows credentials the client uses to authenticate itself to the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9b34-141">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e9b34-141">Requirements</span></span>  
  
|<span data-ttu-id="e9b34-142">MOF</span><span class="sxs-lookup"><span data-stu-id="e9b34-142">MOF</span></span>|<span data-ttu-id="e9b34-143">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="e9b34-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e9b34-144">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="e9b34-144">Namespace</span></span>|<span data-ttu-id="e9b34-145">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e9b34-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e9b34-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e9b34-146">See Also</span></span>  
 <xref:System.ServiceModel.Description.ClientCredentials>
