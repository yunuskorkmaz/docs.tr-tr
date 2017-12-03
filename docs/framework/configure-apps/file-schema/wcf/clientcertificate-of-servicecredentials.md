---
title: "&lt;serviceCredentials&gt; için &lt;clientCertificate&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 90ad03aa-2317-43dd-8a72-6d24cdcad15c
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fc2dfd94ffbf8ce08dee9c14421f389861e99e77
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltclientcertificategt-of-ltservicecredentialsgt"></a><span data-ttu-id="70e3e-102">&lt;serviceCredentials&gt; için &lt;clientCertificate&gt;</span><span class="sxs-lookup"><span data-stu-id="70e3e-102">&lt;clientCertificate&gt; of &lt;serviceCredentials&gt;</span></span>
<span data-ttu-id="70e3e-103">Oturum açın ve bir istemci forma çift yönlü iletişim düzeni hizmetinde iletileri şifrelemek için kullanılan bir X.509 sertifikası tanımlar.</span><span class="sxs-lookup"><span data-stu-id="70e3e-103">Defines an X.509 certificate used to sign and encrypt messages to a client form a service in a duplex communication pattern.</span></span>  
  
 <span data-ttu-id="70e3e-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="70e3e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="70e3e-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="70e3e-105">\<behaviors></span></span>  
<span data-ttu-id="70e3e-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="70e3e-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="70e3e-107">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="70e3e-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="70e3e-108">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="70e3e-108">\<behavior></span></span>  
<span data-ttu-id="70e3e-109">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="70e3e-109">\<serviceCredentials></span></span>  
<span data-ttu-id="70e3e-110">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="70e3e-110">\<clientCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70e3e-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="70e3e-111">Syntax</span></span>  
  
```xml  
<clientCertificate>  
 <certificate/>  
 <authentication/>  
</clientCertificate>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="70e3e-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="70e3e-112">Attributes and Elements</span></span>  
 <span data-ttu-id="70e3e-113">Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır</span><span class="sxs-lookup"><span data-stu-id="70e3e-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="70e3e-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="70e3e-114">Attributes</span></span>  
 <span data-ttu-id="70e3e-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="70e3e-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="70e3e-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="70e3e-116">Child Elements</span></span>  
  
|<span data-ttu-id="70e3e-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="70e3e-117">Element</span></span>|<span data-ttu-id="70e3e-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="70e3e-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="70e3e-119">\<kimlik doğrulama ></span><span class="sxs-lookup"><span data-stu-id="70e3e-119">\<authentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)|<span data-ttu-id="70e3e-120">İstemci sertifikası kimlik doğrulama seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="70e3e-120">Specifies authentication options for the client certificate.</span></span>|  
|[<span data-ttu-id="70e3e-121">\<Sertifika ></span><span class="sxs-lookup"><span data-stu-id="70e3e-121">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-clientcertificate-element.md)|<span data-ttu-id="70e3e-122">Kullanılacak sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="70e3e-122">Specifies the certificate to use.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="70e3e-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="70e3e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="70e3e-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="70e3e-124">Element</span></span>|<span data-ttu-id="70e3e-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="70e3e-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="70e3e-126">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="70e3e-126">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="70e3e-127">Hizmet kimlik doğrulaması kullanmak için kimlik bilgilerini belirtir ve istemci kimlik doğrulaması ilgili ayarları.</span><span class="sxs-lookup"><span data-stu-id="70e3e-127">Specifies the credentials to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70e3e-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="70e3e-128">Remarks</span></span>  
 <span data-ttu-id="70e3e-129">Bu öğe, hizmeti istemcisi ile önceden güvenli bir şekilde iletişim kurmak için istemci sertifikasını olmalıdır kullanılır.</span><span class="sxs-lookup"><span data-stu-id="70e3e-129">This element is used when the service must have the client's certificate in advance to communicate securely with the client.</span></span> <span data-ttu-id="70e3e-130">Bu, çift yönlü iletişim düzeni kullanırken oluşur.</span><span class="sxs-lookup"><span data-stu-id="70e3e-130">This occurs when using the duplex communication pattern.</span></span> <span data-ttu-id="70e3e-131">Daha tipik istek/yanıt desende istemci sertifikasını istemciye yanıt imzalamak ve şifrelemek için hizmet kullanır istekte içerir.</span><span class="sxs-lookup"><span data-stu-id="70e3e-131">In the more typical request/response pattern, the client includes its certificate in the request, which the service uses to encrypt and sign its response back to the client.</span></span> <span data-ttu-id="70e3e-132">Çift yönlü iletişimi düzeninde ancak, hizmeti istemciden gelen istekte yok ve bu nedenle önceden istemciye ileti güvenliğini sağlamak için istemci sertifikasını gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="70e3e-132">In the duplex communication pattern, however, the service does not have a request from the client and therefore it needs the client's certificate in advance to secure the message to the client.</span></span> <span data-ttu-id="70e3e-133">Bu nedenle bir bant dışı anlaşma istemci sertifikasını elde etmek ve bu öğe kullanarak sertifikayı belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="70e3e-133">Therefore you must obtain the client's certificate in an out-of-band negotiation, and specify the certificate using this element.</span></span> <span data-ttu-id="70e3e-134">Çift yönlü hizmetler hakkında daha fazla bilgi için bkz: [nasıl yapılır: çift yönlü sözleşme oluşturma](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="70e3e-134">For more information about duplex services, see [How to: Create a Duplex Contract](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
 <span data-ttu-id="70e3e-135">Bu öğe kümesindeki sertifika ile yapılandırılmış bağlamaları için istemciye iletileri şifrelemek için kullanılan `MutualCertificateDuplex` ileti güvenlik kimlik doğrulama modu.</span><span class="sxs-lookup"><span data-stu-id="70e3e-135">The certificate set in this element is used to encrypt messages to the client only for bindings that are configured with `MutualCertificateDuplex` message security authentication mode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70e3e-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="70e3e-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ClientCertificate%2A>  
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>  
 <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>  
 [<span data-ttu-id="70e3e-137">Nasıl yapılır: çift yönlü sözleşme oluşturma</span><span class="sxs-lookup"><span data-stu-id="70e3e-137">How to: Create a Duplex Contract</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)  
 [<span data-ttu-id="70e3e-138">Güvenlik davranışları</span><span class="sxs-lookup"><span data-stu-id="70e3e-138">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="70e3e-139">Sertifikalar ile çalışma</span><span class="sxs-lookup"><span data-stu-id="70e3e-139">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
