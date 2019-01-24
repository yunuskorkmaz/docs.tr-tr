---
title: '&lt;serviceCredentials&gt; için &lt;clientCertificate&gt;'
ms.date: 03/30/2017
ms.assetid: 90ad03aa-2317-43dd-8a72-6d24cdcad15c
ms.openlocfilehash: e1334e42149de29c4fc7534863f02ede93c638ad
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54536834"
---
# <a name="ltclientcertificategt-of-ltservicecredentialsgt"></a><span data-ttu-id="36184-102">&lt;serviceCredentials&gt; için &lt;clientCertificate&gt;</span><span class="sxs-lookup"><span data-stu-id="36184-102">&lt;clientCertificate&gt; of &lt;serviceCredentials&gt;</span></span>
<span data-ttu-id="36184-103">Bir istemci forma bir çift yönlü iletişim deseni hizmetinde, iletileri imzalamak ve şifrelemek için kullanılan bir X.509 sertifikası tanımlar.</span><span class="sxs-lookup"><span data-stu-id="36184-103">Defines an X.509 certificate used to sign and encrypt messages to a client form a service in a duplex communication pattern.</span></span>  
  
 <span data-ttu-id="36184-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="36184-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="36184-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="36184-105">\<behaviors></span></span>  
<span data-ttu-id="36184-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="36184-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="36184-107">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="36184-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="36184-108">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="36184-108">\<behavior></span></span>  
<span data-ttu-id="36184-109">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="36184-109">\<serviceCredentials></span></span>  
<span data-ttu-id="36184-110">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="36184-110">\<clientCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36184-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="36184-111">Syntax</span></span>  
  
```xml  
<clientCertificate>
  <certificate />
  <authentication />
</clientCertificate>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="36184-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="36184-112">Attributes and Elements</span></span>  
 <span data-ttu-id="36184-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="36184-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="36184-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="36184-114">Attributes</span></span>  
 <span data-ttu-id="36184-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="36184-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="36184-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="36184-116">Child Elements</span></span>  
  
|<span data-ttu-id="36184-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="36184-117">Element</span></span>|<span data-ttu-id="36184-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="36184-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="36184-119">\<kimlik doğrulama ></span><span class="sxs-lookup"><span data-stu-id="36184-119">\<authentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)|<span data-ttu-id="36184-120">İstemci sertifikası kimlik doğrulaması seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="36184-120">Specifies authentication options for the client certificate.</span></span>|  
|[<span data-ttu-id="36184-121">\<Sertifika ></span><span class="sxs-lookup"><span data-stu-id="36184-121">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-clientcertificate-element.md)|<span data-ttu-id="36184-122">Kullanılacak sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="36184-122">Specifies the certificate to use.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="36184-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="36184-123">Parent Elements</span></span>  
  
|<span data-ttu-id="36184-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="36184-124">Element</span></span>|<span data-ttu-id="36184-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="36184-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="36184-126">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="36184-126">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="36184-127">Hizmet kimlik doğrulaması olarak kullanılacak kimlik bilgilerini belirtir ve istemci kimlik bilgileri doğrulaması ilgili ayarları.</span><span class="sxs-lookup"><span data-stu-id="36184-127">Specifies the credentials to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36184-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="36184-128">Remarks</span></span>  
 <span data-ttu-id="36184-129">Hizmet istemcisi ile önceden güvenli şekilde iletişim kurması için istemci sertifikasını olmalıdır, bu öğe kullanılır.</span><span class="sxs-lookup"><span data-stu-id="36184-129">This element is used when the service must have the client's certificate in advance to communicate securely with the client.</span></span> <span data-ttu-id="36184-130">Bu, çift yönlü iletişim deseni kullanırken gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="36184-130">This occurs when using the duplex communication pattern.</span></span> <span data-ttu-id="36184-131">Daha genel istek/yanıt modelinde istemci sertifikasını hizmetin istemciye yanıtına imzalamak ve şifrelemek için kullandığı isteğinde içerir.</span><span class="sxs-lookup"><span data-stu-id="36184-131">In the more typical request/response pattern, the client includes its certificate in the request, which the service uses to encrypt and sign its response back to the client.</span></span> <span data-ttu-id="36184-132">Çift yönlü iletişim deseni, ancak hizmetin istemciden gelen istekte yok ve bu nedenle önceden istemciye ileti güvenliğini sağlamak için istemci sertifikasını gerekir.</span><span class="sxs-lookup"><span data-stu-id="36184-132">In the duplex communication pattern, however, the service does not have a request from the client and therefore it needs the client's certificate in advance to secure the message to the client.</span></span> <span data-ttu-id="36184-133">Bu nedenle istemci sertifikasının, bir bant dışı anlaşma edinmek ve bu öğenin kullanarak sertifikayı belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="36184-133">Therefore you must obtain the client's certificate in an out-of-band negotiation, and specify the certificate using this element.</span></span> <span data-ttu-id="36184-134">Çift yönlü hizmetler hakkında daha fazla bilgi için bkz: [nasıl yapılır: Çift yönlü sözleşme oluşturma](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="36184-134">For more information about duplex services, see [How to: Create a Duplex Contract](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
 <span data-ttu-id="36184-135">Bu öğe kümesindeki sertifika ile yapılandırılmış bağlamalar istemciye iletileri şifrelemek için kullanılan `MutualCertificateDuplex` ileti güvenlik kimlik doğrulama modu.</span><span class="sxs-lookup"><span data-stu-id="36184-135">The certificate set in this element is used to encrypt messages to the client only for bindings that are configured with `MutualCertificateDuplex` message security authentication mode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36184-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36184-136">See also</span></span>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ClientCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>
- [<span data-ttu-id="36184-137">Nasıl yapılır: Çift yönlü sözleşme oluşturma</span><span class="sxs-lookup"><span data-stu-id="36184-137">How to: Create a Duplex Contract</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
- [<span data-ttu-id="36184-138">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="36184-138">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="36184-139">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="36184-139">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
