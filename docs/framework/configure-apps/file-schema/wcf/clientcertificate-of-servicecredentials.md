---
title: <clientCertificate> / <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 90ad03aa-2317-43dd-8a72-6d24cdcad15c
ms.openlocfilehash: 277e5e33bcc7f9d417da7ce24caa4c6200c23e23
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919545"
---
# <a name="clientcertificate-of-servicecredentials"></a><span data-ttu-id="be30a-102">\<\<ServiceCredentials > ClientCertificate ></span><span class="sxs-lookup"><span data-stu-id="be30a-102">\<clientCertificate> of \<serviceCredentials></span></span>
<span data-ttu-id="be30a-103">Bir çift yönlü iletişim düzeninde bir hizmet oluşturmak ve bir istemciye iletileri şifrelemek için kullanılan bir X. 509.440 sertifikası tanımlar.</span><span class="sxs-lookup"><span data-stu-id="be30a-103">Defines an X.509 certificate used to sign and encrypt messages to a client form a service in a duplex communication pattern.</span></span>  
  
 <span data-ttu-id="be30a-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="be30a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="be30a-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="be30a-105">\<behaviors></span></span>  
<span data-ttu-id="be30a-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="be30a-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="be30a-107">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="be30a-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="be30a-108">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="be30a-108">\<behavior></span></span>  
<span data-ttu-id="be30a-109">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="be30a-109">\<serviceCredentials></span></span>  
<span data-ttu-id="be30a-110">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="be30a-110">\<clientCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be30a-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="be30a-111">Syntax</span></span>  
  
```xml  
<clientCertificate>
  <certificate />
  <authentication />
</clientCertificate>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="be30a-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="be30a-112">Attributes and Elements</span></span>  
 <span data-ttu-id="be30a-113">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="be30a-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="be30a-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="be30a-114">Attributes</span></span>  
 <span data-ttu-id="be30a-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="be30a-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="be30a-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="be30a-116">Child Elements</span></span>  
  
|<span data-ttu-id="be30a-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="be30a-117">Element</span></span>|<span data-ttu-id="be30a-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="be30a-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="be30a-119">\<kimlik doğrulama ></span><span class="sxs-lookup"><span data-stu-id="be30a-119">\<authentication></span></span>](authentication-of-clientcertificate-element.md)|<span data-ttu-id="be30a-120">İstemci sertifikası için kimlik doğrulama seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="be30a-120">Specifies authentication options for the client certificate.</span></span>|  
|[<span data-ttu-id="be30a-121">\<Sertifika ></span><span class="sxs-lookup"><span data-stu-id="be30a-121">\<certificate></span></span>](certificate-of-clientcertificate-element.md)|<span data-ttu-id="be30a-122">Kullanılacak sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="be30a-122">Specifies the certificate to use.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="be30a-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="be30a-123">Parent Elements</span></span>  
  
|<span data-ttu-id="be30a-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="be30a-124">Element</span></span>|<span data-ttu-id="be30a-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="be30a-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="be30a-126">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="be30a-126">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="be30a-127">Hizmetin kimliğini doğrulamak için kullanılacak kimlik bilgilerini ve istemci kimlik bilgileri doğrulaması ile ilgili ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="be30a-127">Specifies the credentials to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="be30a-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="be30a-128">Remarks</span></span>  
 <span data-ttu-id="be30a-129">Bu öğe, hizmetin istemci sertifikası ile güvenli bir şekilde iletişim kurmak için istemcinin sertifikasının önceden olması gerektiği durumlarda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="be30a-129">This element is used when the service must have the client's certificate in advance to communicate securely with the client.</span></span> <span data-ttu-id="be30a-130">Bu, çift yönlü iletişim deseninin kullanıldığı durumlarda oluşur.</span><span class="sxs-lookup"><span data-stu-id="be30a-130">This occurs when using the duplex communication pattern.</span></span> <span data-ttu-id="be30a-131">Daha tipik istek/yanıt modelinde istemci, isteğin sertifikasını istemciye geri yanıtını şifrelemek ve imzalamak için kullandığı isteği içerir.</span><span class="sxs-lookup"><span data-stu-id="be30a-131">In the more typical request/response pattern, the client includes its certificate in the request, which the service uses to encrypt and sign its response back to the client.</span></span> <span data-ttu-id="be30a-132">Çift yönlü iletişim modelinde, hizmette istemciden bir istek yoktur ve bu nedenle iletinin istemciye güvenmesi için istemcinin sertifikasının önceden olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="be30a-132">In the duplex communication pattern, however, the service does not have a request from the client and therefore it needs the client's certificate in advance to secure the message to the client.</span></span> <span data-ttu-id="be30a-133">Bu nedenle, istemcinin sertifikasını bant dışı bir anlaşmede edinmeniz ve bu öğeyi kullanarak sertifikayı belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="be30a-133">Therefore you must obtain the client's certificate in an out-of-band negotiation, and specify the certificate using this element.</span></span> <span data-ttu-id="be30a-134">Çift yönlü hizmetler hakkında daha fazla bilgi için [bkz. nasıl yapılır: Çift yönlü sözleşme](../../../wcf/feature-details/how-to-create-a-duplex-contract.md)oluşturun.</span><span class="sxs-lookup"><span data-stu-id="be30a-134">For more information about duplex services, see [How to: Create a Duplex Contract](../../../wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
 <span data-ttu-id="be30a-135">Bu öğedeki sertifika kümesi, iletileri yalnızca `MutualCertificateDuplex` ileti güvenliği kimlik doğrulama moduyla yapılandırılan bağlamalar için istemciye şifrelemek üzere kullanılır.</span><span class="sxs-lookup"><span data-stu-id="be30a-135">The certificate set in this element is used to encrypt messages to the client only for bindings that are configured with `MutualCertificateDuplex` message security authentication mode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be30a-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="be30a-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ClientCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>
- [<span data-ttu-id="be30a-137">Nasıl yapılır: Çift yönlü sözleşme oluşturma</span><span class="sxs-lookup"><span data-stu-id="be30a-137">How to: Create a Duplex Contract</span></span>](../../../wcf/feature-details/how-to-create-a-duplex-contract.md)
- [<span data-ttu-id="be30a-138">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="be30a-138">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="be30a-139">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="be30a-139">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
