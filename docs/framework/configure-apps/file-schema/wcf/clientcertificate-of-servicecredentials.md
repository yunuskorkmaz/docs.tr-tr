---
title: <clientCertificate> / <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 90ad03aa-2317-43dd-8a72-6d24cdcad15c
ms.openlocfilehash: a8a78bbfcd9dfbf6975503a845d5bb4e2d24b13d
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398133"
---
# <a name="clientcertificate-of-servicecredentials"></a><span data-ttu-id="20ee7-102">\<\<ServiceCredentials > ClientCertificate ></span><span class="sxs-lookup"><span data-stu-id="20ee7-102">\<clientCertificate> of \<serviceCredentials></span></span>
<span data-ttu-id="20ee7-103">Bir çift yönlü iletişim düzeninde bir hizmet oluşturmak ve bir istemciye iletileri şifrelemek için kullanılan bir X. 509.440 sertifikası tanımlar.</span><span class="sxs-lookup"><span data-stu-id="20ee7-103">Defines an X.509 certificate used to sign and encrypt messages to a client form a service in a duplex communication pattern.</span></span>  
  
<span data-ttu-id="20ee7-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="20ee7-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="20ee7-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="20ee7-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="20ee7-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="20ee7-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="20ee7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Servicedavranışlar >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="20ee7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="20ee7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="20ee7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="20ee7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCredentials >** ](servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="20ee7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)</span></span>\
<span data-ttu-id="20ee7-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<clientCertificate >**</span><span class="sxs-lookup"><span data-stu-id="20ee7-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clientCertificate>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20ee7-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="20ee7-111">Syntax</span></span>  
  
```xml  
<clientCertificate>
  <certificate />
  <authentication />
</clientCertificate>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="20ee7-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="20ee7-112">Attributes and Elements</span></span>  
 <span data-ttu-id="20ee7-113">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="20ee7-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="20ee7-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="20ee7-114">Attributes</span></span>  
 <span data-ttu-id="20ee7-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="20ee7-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="20ee7-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="20ee7-116">Child Elements</span></span>  
  
|<span data-ttu-id="20ee7-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="20ee7-117">Element</span></span>|<span data-ttu-id="20ee7-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="20ee7-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="20ee7-119">\<kimlik doğrulama ></span><span class="sxs-lookup"><span data-stu-id="20ee7-119">\<authentication></span></span>](authentication-of-clientcertificate-element.md)|<span data-ttu-id="20ee7-120">İstemci sertifikası için kimlik doğrulama seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="20ee7-120">Specifies authentication options for the client certificate.</span></span>|  
|[<span data-ttu-id="20ee7-121">\<Sertifika ></span><span class="sxs-lookup"><span data-stu-id="20ee7-121">\<certificate></span></span>](certificate-of-clientcertificate-element.md)|<span data-ttu-id="20ee7-122">Kullanılacak sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="20ee7-122">Specifies the certificate to use.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="20ee7-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="20ee7-123">Parent Elements</span></span>  
  
|<span data-ttu-id="20ee7-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="20ee7-124">Element</span></span>|<span data-ttu-id="20ee7-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="20ee7-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="20ee7-126">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="20ee7-126">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="20ee7-127">Hizmetin kimliğini doğrulamak için kullanılacak kimlik bilgilerini ve istemci kimlik bilgileri doğrulaması ile ilgili ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="20ee7-127">Specifies the credentials to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20ee7-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="20ee7-128">Remarks</span></span>  
 <span data-ttu-id="20ee7-129">Bu öğe, hizmetin istemci sertifikası ile güvenli bir şekilde iletişim kurmak için istemcinin sertifikasının önceden olması gerektiği durumlarda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="20ee7-129">This element is used when the service must have the client's certificate in advance to communicate securely with the client.</span></span> <span data-ttu-id="20ee7-130">Bu, çift yönlü iletişim deseninin kullanıldığı durumlarda oluşur.</span><span class="sxs-lookup"><span data-stu-id="20ee7-130">This occurs when using the duplex communication pattern.</span></span> <span data-ttu-id="20ee7-131">Daha tipik istek/yanıt modelinde istemci, isteğin sertifikasını istemciye geri yanıtını şifrelemek ve imzalamak için kullandığı isteği içerir.</span><span class="sxs-lookup"><span data-stu-id="20ee7-131">In the more typical request/response pattern, the client includes its certificate in the request, which the service uses to encrypt and sign its response back to the client.</span></span> <span data-ttu-id="20ee7-132">Çift yönlü iletişim modelinde, hizmette istemciden bir istek yoktur ve bu nedenle iletinin istemciye güvenmesi için istemcinin sertifikasının önceden olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="20ee7-132">In the duplex communication pattern, however, the service does not have a request from the client and therefore it needs the client's certificate in advance to secure the message to the client.</span></span> <span data-ttu-id="20ee7-133">Bu nedenle, istemcinin sertifikasını bant dışı bir anlaşmede edinmeniz ve bu öğeyi kullanarak sertifikayı belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="20ee7-133">Therefore you must obtain the client's certificate in an out-of-band negotiation, and specify the certificate using this element.</span></span> <span data-ttu-id="20ee7-134">Çift yönlü hizmetler hakkında daha fazla bilgi için [bkz. nasıl yapılır: Çift yönlü sözleşme](../../../wcf/feature-details/how-to-create-a-duplex-contract.md)oluşturun.</span><span class="sxs-lookup"><span data-stu-id="20ee7-134">For more information about duplex services, see [How to: Create a Duplex Contract](../../../wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
 <span data-ttu-id="20ee7-135">Bu öğedeki sertifika kümesi, iletileri yalnızca `MutualCertificateDuplex` ileti güvenliği kimlik doğrulama moduyla yapılandırılan bağlamalar için istemciye şifrelemek üzere kullanılır.</span><span class="sxs-lookup"><span data-stu-id="20ee7-135">The certificate set in this element is used to encrypt messages to the client only for bindings that are configured with `MutualCertificateDuplex` message security authentication mode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20ee7-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="20ee7-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ClientCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>
- [<span data-ttu-id="20ee7-137">Nasıl yapılır: Çift yönlü sözleşme oluşturma</span><span class="sxs-lookup"><span data-stu-id="20ee7-137">How to: Create a Duplex Contract</span></span>](../../../wcf/feature-details/how-to-create-a-duplex-contract.md)
- [<span data-ttu-id="20ee7-138">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="20ee7-138">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="20ee7-139">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="20ee7-139">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
