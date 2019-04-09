---
title: <clientCertificate> , <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 90ad03aa-2317-43dd-8a72-6d24cdcad15c
ms.openlocfilehash: 26ebac6439a90959e3a926e6a36c9044251a4aae
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107997"
---
# <a name="clientcertificate-of-servicecredentials"></a><span data-ttu-id="fa146-102">\<clientCertificate >, \<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="fa146-102">\<clientCertificate> of \<serviceCredentials></span></span>
<span data-ttu-id="fa146-103">Bir istemci forma bir çift yönlü iletişim deseni hizmetinde, iletileri imzalamak ve şifrelemek için kullanılan bir X.509 sertifikası tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fa146-103">Defines an X.509 certificate used to sign and encrypt messages to a client form a service in a duplex communication pattern.</span></span>  
  
 <span data-ttu-id="fa146-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="fa146-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="fa146-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="fa146-105">\<behaviors></span></span>  
<span data-ttu-id="fa146-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="fa146-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="fa146-107">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="fa146-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="fa146-108">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="fa146-108">\<behavior></span></span>  
<span data-ttu-id="fa146-109">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="fa146-109">\<serviceCredentials></span></span>  
<span data-ttu-id="fa146-110">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="fa146-110">\<clientCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa146-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fa146-111">Syntax</span></span>  
  
```xml  
<clientCertificate>
  <certificate />
  <authentication />
</clientCertificate>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fa146-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fa146-112">Attributes and Elements</span></span>  
 <span data-ttu-id="fa146-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fa146-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fa146-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fa146-114">Attributes</span></span>  
 <span data-ttu-id="fa146-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="fa146-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fa146-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fa146-116">Child Elements</span></span>  
  
|<span data-ttu-id="fa146-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="fa146-117">Element</span></span>|<span data-ttu-id="fa146-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fa146-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fa146-119">\<kimlik doğrulama ></span><span class="sxs-lookup"><span data-stu-id="fa146-119">\<authentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)|<span data-ttu-id="fa146-120">İstemci sertifikası kimlik doğrulaması seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="fa146-120">Specifies authentication options for the client certificate.</span></span>|  
|[<span data-ttu-id="fa146-121">\<Sertifika ></span><span class="sxs-lookup"><span data-stu-id="fa146-121">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-clientcertificate-element.md)|<span data-ttu-id="fa146-122">Kullanılacak sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="fa146-122">Specifies the certificate to use.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fa146-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fa146-123">Parent Elements</span></span>  
  
|<span data-ttu-id="fa146-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="fa146-124">Element</span></span>|<span data-ttu-id="fa146-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fa146-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fa146-126">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="fa146-126">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="fa146-127">Hizmet kimlik doğrulaması olarak kullanılacak kimlik bilgilerini belirtir ve istemci kimlik bilgileri doğrulaması ilgili ayarları.</span><span class="sxs-lookup"><span data-stu-id="fa146-127">Specifies the credentials to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa146-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fa146-128">Remarks</span></span>  
 <span data-ttu-id="fa146-129">Hizmet istemcisi ile önceden güvenli şekilde iletişim kurması için istemci sertifikasını olmalıdır, bu öğe kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fa146-129">This element is used when the service must have the client's certificate in advance to communicate securely with the client.</span></span> <span data-ttu-id="fa146-130">Bu, çift yönlü iletişim deseni kullanırken gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="fa146-130">This occurs when using the duplex communication pattern.</span></span> <span data-ttu-id="fa146-131">Daha genel istek/yanıt modelinde istemci sertifikasını hizmetin istemciye yanıtına imzalamak ve şifrelemek için kullandığı isteğinde içerir.</span><span class="sxs-lookup"><span data-stu-id="fa146-131">In the more typical request/response pattern, the client includes its certificate in the request, which the service uses to encrypt and sign its response back to the client.</span></span> <span data-ttu-id="fa146-132">Çift yönlü iletişim deseni, ancak hizmetin istemciden gelen istekte yok ve bu nedenle önceden istemciye ileti güvenliğini sağlamak için istemci sertifikasını gerekir.</span><span class="sxs-lookup"><span data-stu-id="fa146-132">In the duplex communication pattern, however, the service does not have a request from the client and therefore it needs the client's certificate in advance to secure the message to the client.</span></span> <span data-ttu-id="fa146-133">Bu nedenle istemci sertifikasının, bir bant dışı anlaşma edinmek ve bu öğenin kullanarak sertifikayı belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fa146-133">Therefore you must obtain the client's certificate in an out-of-band negotiation, and specify the certificate using this element.</span></span> <span data-ttu-id="fa146-134">Çift yönlü hizmetler hakkında daha fazla bilgi için bkz: [nasıl yapılır: Çift yönlü sözleşme oluşturma](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="fa146-134">For more information about duplex services, see [How to: Create a Duplex Contract](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
 <span data-ttu-id="fa146-135">Bu öğe kümesindeki sertifika ile yapılandırılmış bağlamalar istemciye iletileri şifrelemek için kullanılan `MutualCertificateDuplex` ileti güvenlik kimlik doğrulama modu.</span><span class="sxs-lookup"><span data-stu-id="fa146-135">The certificate set in this element is used to encrypt messages to the client only for bindings that are configured with `MutualCertificateDuplex` message security authentication mode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa146-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fa146-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ClientCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>
- [<span data-ttu-id="fa146-137">Nasıl yapılır: Çift Yönlü Sözleşme Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fa146-137">How to: Create a Duplex Contract</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
- [<span data-ttu-id="fa146-138">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="fa146-138">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="fa146-139">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="fa146-139">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
