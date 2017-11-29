---
title: ServiceCredentials
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9c780793-4785-46f7-add9-ac1ebeadb614
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e4cc9d7d7d46157b7df202c6daffb31b90fa98c1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="servicecredentials"></a><span data-ttu-id="5a003-102">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="5a003-102">ServiceCredentials</span></span>
<span data-ttu-id="5a003-103">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="5a003-103">ServiceCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a003-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5a003-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="5a003-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="5a003-105">Methods</span></span>  
 <span data-ttu-id="5a003-106">ServiceCredentials sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="5a003-106">The ServiceCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="5a003-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="5a003-107">Properties</span></span>  
 <span data-ttu-id="5a003-108">ServiceCredentials sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="5a003-108">The ServiceCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="5a003-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="5a003-109">ClientCertificate</span></span>  
 <span data-ttu-id="5a003-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="5a003-110">Data type: string</span></span>  
  
 <span data-ttu-id="5a003-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="5a003-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5a003-112">Sertifika kimlik doğrulaması ve sağlama için istemci ayarlarını bu hizmet.</span><span class="sxs-lookup"><span data-stu-id="5a003-112">The client certificate authentication and provisioning settings for this service.</span></span>  
  
### <a name="issuedtokenauthentication"></a><span data-ttu-id="5a003-113">IssuedTokenAuthentication</span><span class="sxs-lookup"><span data-stu-id="5a003-113">IssuedTokenAuthentication</span></span>  
 <span data-ttu-id="5a003-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="5a003-114">Data type: string</span></span>  
  
 <span data-ttu-id="5a003-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="5a003-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5a003-116">Geçerli belirteç kimlik doğrulama ayarlarını bu hizmet için verilmiş.</span><span class="sxs-lookup"><span data-stu-id="5a003-116">The current issued token authentication settings for this service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="5a003-117">Eş</span><span class="sxs-lookup"><span data-stu-id="5a003-117">Peer</span></span>  
 <span data-ttu-id="5a003-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="5a003-118">Data type: string</span></span>  
  
 <span data-ttu-id="5a003-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="5a003-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5a003-120">Geçerli kimlik doğrulama ve eş aktarım uç noktaları tarafından kullanılacak ayarları sağlama kimlik bilgileri.</span><span class="sxs-lookup"><span data-stu-id="5a003-120">The current credential authentication and provisioning settings to be used by peer transport endpoints.</span></span>  
  
### <a name="secureconversationauthentication"></a><span data-ttu-id="5a003-121">Servicecredential</span><span class="sxs-lookup"><span data-stu-id="5a003-121">SecureConversationAuthentication</span></span>  
 <span data-ttu-id="5a003-122">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="5a003-122">Data type: string</span></span>  
  
 <span data-ttu-id="5a003-123">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="5a003-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5a003-124">Geçerli güvenli konuşma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5a003-124">Specifies the current secure conversation settings.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="5a003-125">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="5a003-125">ServiceCertificate</span></span>  
 <span data-ttu-id="5a003-126">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="5a003-126">Data type: string</span></span>  
  
 <span data-ttu-id="5a003-127">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="5a003-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5a003-128">Bu hizmet ile ilişkili sertifika.</span><span class="sxs-lookup"><span data-stu-id="5a003-128">The certificate associated with this service.</span></span>  
  
### <a name="usernameauthentication"></a><span data-ttu-id="5a003-129">UserNameAuthentication</span><span class="sxs-lookup"><span data-stu-id="5a003-129">UserNameAuthentication</span></span>  
 <span data-ttu-id="5a003-130">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="5a003-130">Data type: string</span></span>  
  
 <span data-ttu-id="5a003-131">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="5a003-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5a003-132">Bu hizmet için kullanıcı adı/parola ayarları.</span><span class="sxs-lookup"><span data-stu-id="5a003-132">The username/password settings for this service.</span></span>  
  
### <a name="windowsauthentication"></a><span data-ttu-id="5a003-133">WindowsAuthentication</span><span class="sxs-lookup"><span data-stu-id="5a003-133">WindowsAuthentication</span></span>  
 <span data-ttu-id="5a003-134">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="5a003-134">Data type: string</span></span>  
  
 <span data-ttu-id="5a003-135">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="5a003-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5a003-136">Bu hizmet Windows kimlik doğrulama ayarları.</span><span class="sxs-lookup"><span data-stu-id="5a003-136">The Windows authentication settings for this service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a003-137">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5a003-137">Requirements</span></span>  
  
|<span data-ttu-id="5a003-138">MOF</span><span class="sxs-lookup"><span data-stu-id="5a003-138">MOF</span></span>|<span data-ttu-id="5a003-139">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="5a003-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="5a003-140">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="5a003-140">Namespace</span></span>|<span data-ttu-id="5a003-141">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="5a003-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5a003-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5a003-142">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceCredentials>
