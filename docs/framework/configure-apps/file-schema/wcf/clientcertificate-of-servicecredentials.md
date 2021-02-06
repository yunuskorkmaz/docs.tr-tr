---
description: 'Hakkında daha fazla bilgi <clientCertificate> edinin: <serviceCredentials>'
title: <clientCertificate> / <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 90ad03aa-2317-43dd-8a72-6d24cdcad15c
ms.openlocfilehash: c3e6378f9646ec30188e2de3d1c832f363904ad0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638827"
---
# <a name="clientcertificate-of-servicecredentials"></a><span data-ttu-id="6f3e4-103">\<clientCertificate> / \<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="6f3e4-103">\<clientCertificate> of \<serviceCredentials></span></span>

<span data-ttu-id="6f3e4-104">Bir çift yönlü iletişim düzeninde bir hizmet oluşturmak ve bir istemciye iletileri şifrelemek için kullanılan bir X. 509.440 sertifikası tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6f3e4-104">Defines an X.509 certificate used to sign and encrypt messages to a client form a service in a duplex communication pattern.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clientCertificate>**  
  
## <a name="syntax"></a><span data-ttu-id="6f3e4-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="6f3e4-105">Syntax</span></span>  
  
```xml  
<clientCertificate>
  <certificate />
  <authentication />
</clientCertificate>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6f3e4-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6f3e4-106">Attributes and Elements</span></span>  

 <span data-ttu-id="6f3e4-107">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="6f3e4-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6f3e4-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6f3e4-108">Attributes</span></span>  

 <span data-ttu-id="6f3e4-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="6f3e4-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6f3e4-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6f3e4-110">Child Elements</span></span>  
  
|<span data-ttu-id="6f3e4-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="6f3e4-111">Element</span></span>|<span data-ttu-id="6f3e4-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6f3e4-112">Description</span></span>|  
|-------------|-----------------|  
|[\<authentication>](authentication-of-clientcertificate-element.md)|<span data-ttu-id="6f3e4-113">İstemci sertifikası için kimlik doğrulama seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f3e4-113">Specifies authentication options for the client certificate.</span></span>|  
|[\<certificate>](certificate-of-clientcertificate-element.md)|<span data-ttu-id="6f3e4-114">Kullanılacak sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f3e4-114">Specifies the certificate to use.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6f3e4-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6f3e4-115">Parent Elements</span></span>  
  
|<span data-ttu-id="6f3e4-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="6f3e4-116">Element</span></span>|<span data-ttu-id="6f3e4-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6f3e4-117">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="6f3e4-118">Hizmetin kimliğini doğrulamak için kullanılacak kimlik bilgilerini ve istemci kimlik bilgileri doğrulaması ile ilgili ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f3e4-118">Specifies the credentials to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f3e4-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6f3e4-119">Remarks</span></span>  

 <span data-ttu-id="6f3e4-120">Bu öğe, hizmetin istemci sertifikası ile güvenli bir şekilde iletişim kurmak için istemcinin sertifikasının önceden olması gerektiği durumlarda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6f3e4-120">This element is used when the service must have the client's certificate in advance to communicate securely with the client.</span></span> <span data-ttu-id="6f3e4-121">Bu, çift yönlü iletişim deseninin kullanıldığı durumlarda oluşur.</span><span class="sxs-lookup"><span data-stu-id="6f3e4-121">This occurs when using the duplex communication pattern.</span></span> <span data-ttu-id="6f3e4-122">Daha tipik istek/yanıt modelinde istemci, isteğin sertifikasını istemciye geri yanıtını şifrelemek ve imzalamak için kullandığı isteği içerir.</span><span class="sxs-lookup"><span data-stu-id="6f3e4-122">In the more typical request/response pattern, the client includes its certificate in the request, which the service uses to encrypt and sign its response back to the client.</span></span> <span data-ttu-id="6f3e4-123">Çift yönlü iletişim modelinde, hizmette istemciden bir istek yoktur ve bu nedenle iletinin istemciye güvenmesi için istemcinin sertifikasının önceden olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6f3e4-123">In the duplex communication pattern, however, the service does not have a request from the client and therefore it needs the client's certificate in advance to secure the message to the client.</span></span> <span data-ttu-id="6f3e4-124">Bu nedenle, istemcinin sertifikasını bant dışı bir anlaşmede edinmeniz ve bu öğeyi kullanarak sertifikayı belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6f3e4-124">Therefore you must obtain the client's certificate in an out-of-band negotiation, and specify the certificate using this element.</span></span> <span data-ttu-id="6f3e4-125">Çift yönlü hizmetler hakkında daha fazla bilgi için bkz. [nasıl yapılır: çift yönlü sözleşme oluşturma](../../../wcf/feature-details/how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="6f3e4-125">For more information about duplex services, see [How to: Create a Duplex Contract](../../../wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
 <span data-ttu-id="6f3e4-126">Bu öğedeki sertifika kümesi, iletileri yalnızca `MutualCertificateDuplex` ileti güvenliği kimlik doğrulama moduyla yapılandırılan bağlamalar için istemciye şifrelemek üzere kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6f3e4-126">The certificate set in this element is used to encrypt messages to the client only for bindings that are configured with `MutualCertificateDuplex` message security authentication mode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f3e4-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f3e4-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ClientCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>
- [<span data-ttu-id="6f3e4-128">Nasıl yapılır: Çift Yönlü Sözleşme Oluşturma</span><span class="sxs-lookup"><span data-stu-id="6f3e4-128">How to: Create a Duplex Contract</span></span>](../../../wcf/feature-details/how-to-create-a-duplex-contract.md)
- [<span data-ttu-id="6f3e4-129">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="6f3e4-129">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="6f3e4-130">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="6f3e4-130">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
