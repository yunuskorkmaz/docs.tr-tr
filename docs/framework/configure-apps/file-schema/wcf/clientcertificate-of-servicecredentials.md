---
title: <clientCertificate> / <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 90ad03aa-2317-43dd-8a72-6d24cdcad15c
ms.openlocfilehash: 26ebac6439a90959e3a926e6a36c9044251a4aae
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59107997"
---
# <a name="clientcertificate-of-servicecredentials"></a><span data-ttu-id="1e767-102">\<clientCertificate >, \<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="1e767-102">\<clientCertificate> of \<serviceCredentials></span></span>
<span data-ttu-id="1e767-103">Bir istemci forma bir çift yönlü iletişim deseni hizmetinde, iletileri imzalamak ve şifrelemek için kullanılan bir X.509 sertifikası tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1e767-103">Defines an X.509 certificate used to sign and encrypt messages to a client form a service in a duplex communication pattern.</span></span>  
  
 <span data-ttu-id="1e767-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1e767-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1e767-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="1e767-105">\<behaviors></span></span>  
<span data-ttu-id="1e767-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="1e767-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="1e767-107">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="1e767-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="1e767-108">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="1e767-108">\<behavior></span></span>  
<span data-ttu-id="1e767-109">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="1e767-109">\<serviceCredentials></span></span>  
<span data-ttu-id="1e767-110">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="1e767-110">\<clientCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e767-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1e767-111">Syntax</span></span>  
  
```xml  
<clientCertificate>
  <certificate />
  <authentication />
</clientCertificate>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1e767-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1e767-112">Attributes and Elements</span></span>  
 <span data-ttu-id="1e767-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1e767-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1e767-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1e767-114">Attributes</span></span>  
 <span data-ttu-id="1e767-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="1e767-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1e767-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1e767-116">Child Elements</span></span>  
  
|<span data-ttu-id="1e767-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="1e767-117">Element</span></span>|<span data-ttu-id="1e767-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1e767-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1e767-119">\<kimlik doğrulama ></span><span class="sxs-lookup"><span data-stu-id="1e767-119">\<authentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)|<span data-ttu-id="1e767-120">İstemci sertifikası kimlik doğrulaması seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1e767-120">Specifies authentication options for the client certificate.</span></span>|  
|[<span data-ttu-id="1e767-121">\<Sertifika ></span><span class="sxs-lookup"><span data-stu-id="1e767-121">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-clientcertificate-element.md)|<span data-ttu-id="1e767-122">Kullanılacak sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="1e767-122">Specifies the certificate to use.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1e767-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1e767-123">Parent Elements</span></span>  
  
|<span data-ttu-id="1e767-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="1e767-124">Element</span></span>|<span data-ttu-id="1e767-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1e767-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1e767-126">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="1e767-126">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="1e767-127">Hizmet kimlik doğrulaması olarak kullanılacak kimlik bilgilerini belirtir ve istemci kimlik bilgileri doğrulaması ilgili ayarları.</span><span class="sxs-lookup"><span data-stu-id="1e767-127">Specifies the credentials to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e767-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1e767-128">Remarks</span></span>  
 <span data-ttu-id="1e767-129">Hizmet istemcisi ile önceden güvenli şekilde iletişim kurması için istemci sertifikasını olmalıdır, bu öğe kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1e767-129">This element is used when the service must have the client's certificate in advance to communicate securely with the client.</span></span> <span data-ttu-id="1e767-130">Bu, çift yönlü iletişim deseni kullanırken gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="1e767-130">This occurs when using the duplex communication pattern.</span></span> <span data-ttu-id="1e767-131">Daha genel istek/yanıt modelinde istemci sertifikasını hizmetin istemciye yanıtına imzalamak ve şifrelemek için kullandığı isteğinde içerir.</span><span class="sxs-lookup"><span data-stu-id="1e767-131">In the more typical request/response pattern, the client includes its certificate in the request, which the service uses to encrypt and sign its response back to the client.</span></span> <span data-ttu-id="1e767-132">Çift yönlü iletişim deseni, ancak hizmetin istemciden gelen istekte yok ve bu nedenle önceden istemciye ileti güvenliğini sağlamak için istemci sertifikasını gerekir.</span><span class="sxs-lookup"><span data-stu-id="1e767-132">In the duplex communication pattern, however, the service does not have a request from the client and therefore it needs the client's certificate in advance to secure the message to the client.</span></span> <span data-ttu-id="1e767-133">Bu nedenle istemci sertifikasının, bir bant dışı anlaşma edinmek ve bu öğenin kullanarak sertifikayı belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1e767-133">Therefore you must obtain the client's certificate in an out-of-band negotiation, and specify the certificate using this element.</span></span> <span data-ttu-id="1e767-134">Çift yönlü hizmetler hakkında daha fazla bilgi için bkz: [nasıl yapılır: Çift yönlü sözleşme oluşturma](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="1e767-134">For more information about duplex services, see [How to: Create a Duplex Contract](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
 <span data-ttu-id="1e767-135">Bu öğe kümesindeki sertifika ile yapılandırılmış bağlamalar istemciye iletileri şifrelemek için kullanılan `MutualCertificateDuplex` ileti güvenlik kimlik doğrulama modu.</span><span class="sxs-lookup"><span data-stu-id="1e767-135">The certificate set in this element is used to encrypt messages to the client only for bindings that are configured with `MutualCertificateDuplex` message security authentication mode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e767-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1e767-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ClientCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>
- [<span data-ttu-id="1e767-137">Nasıl yapılır: Çift yönlü sözleşme oluşturma</span><span class="sxs-lookup"><span data-stu-id="1e767-137">How to: Create a Duplex Contract</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
- [<span data-ttu-id="1e767-138">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="1e767-138">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="1e767-139">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="1e767-139">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
