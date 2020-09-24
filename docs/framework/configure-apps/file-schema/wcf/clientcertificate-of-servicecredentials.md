---
title: <clientCertificate> / <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 90ad03aa-2317-43dd-8a72-6d24cdcad15c
ms.openlocfilehash: 9df49777efc80f425cad3b353f95db523a027214
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148923"
---
# <a name="clientcertificate-of-servicecredentials"></a><span data-ttu-id="afca7-102">\<clientCertificate> / \<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="afca7-102">\<clientCertificate> of \<serviceCredentials></span></span>

<span data-ttu-id="afca7-103">Bir çift yönlü iletişim düzeninde bir hizmet oluşturmak ve bir istemciye iletileri şifrelemek için kullanılan bir X. 509.440 sertifikası tanımlar.</span><span class="sxs-lookup"><span data-stu-id="afca7-103">Defines an X.509 certificate used to sign and encrypt messages to a client form a service in a duplex communication pattern.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clientCertificate>**  
  
## <a name="syntax"></a><span data-ttu-id="afca7-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="afca7-104">Syntax</span></span>  
  
```xml  
<clientCertificate>
  <certificate />
  <authentication />
</clientCertificate>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="afca7-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="afca7-105">Attributes and Elements</span></span>  

 <span data-ttu-id="afca7-106">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="afca7-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="afca7-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="afca7-107">Attributes</span></span>  

 <span data-ttu-id="afca7-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="afca7-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="afca7-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="afca7-109">Child Elements</span></span>  
  
|<span data-ttu-id="afca7-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="afca7-110">Element</span></span>|<span data-ttu-id="afca7-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="afca7-111">Description</span></span>|  
|-------------|-----------------|  
|[\<authentication>](authentication-of-clientcertificate-element.md)|<span data-ttu-id="afca7-112">İstemci sertifikası için kimlik doğrulama seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="afca7-112">Specifies authentication options for the client certificate.</span></span>|  
|[\<certificate>](certificate-of-clientcertificate-element.md)|<span data-ttu-id="afca7-113">Kullanılacak sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="afca7-113">Specifies the certificate to use.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="afca7-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="afca7-114">Parent Elements</span></span>  
  
|<span data-ttu-id="afca7-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="afca7-115">Element</span></span>|<span data-ttu-id="afca7-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="afca7-116">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="afca7-117">Hizmetin kimliğini doğrulamak için kullanılacak kimlik bilgilerini ve istemci kimlik bilgileri doğrulaması ile ilgili ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="afca7-117">Specifies the credentials to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="afca7-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="afca7-118">Remarks</span></span>  

 <span data-ttu-id="afca7-119">Bu öğe, hizmetin istemci sertifikası ile güvenli bir şekilde iletişim kurmak için istemcinin sertifikasının önceden olması gerektiği durumlarda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="afca7-119">This element is used when the service must have the client's certificate in advance to communicate securely with the client.</span></span> <span data-ttu-id="afca7-120">Bu, çift yönlü iletişim deseninin kullanıldığı durumlarda oluşur.</span><span class="sxs-lookup"><span data-stu-id="afca7-120">This occurs when using the duplex communication pattern.</span></span> <span data-ttu-id="afca7-121">Daha tipik istek/yanıt modelinde istemci, isteğin sertifikasını istemciye geri yanıtını şifrelemek ve imzalamak için kullandığı isteği içerir.</span><span class="sxs-lookup"><span data-stu-id="afca7-121">In the more typical request/response pattern, the client includes its certificate in the request, which the service uses to encrypt and sign its response back to the client.</span></span> <span data-ttu-id="afca7-122">Çift yönlü iletişim modelinde, hizmette istemciden bir istek yoktur ve bu nedenle iletinin istemciye güvenmesi için istemcinin sertifikasının önceden olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="afca7-122">In the duplex communication pattern, however, the service does not have a request from the client and therefore it needs the client's certificate in advance to secure the message to the client.</span></span> <span data-ttu-id="afca7-123">Bu nedenle, istemcinin sertifikasını bant dışı bir anlaşmede edinmeniz ve bu öğeyi kullanarak sertifikayı belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="afca7-123">Therefore you must obtain the client's certificate in an out-of-band negotiation, and specify the certificate using this element.</span></span> <span data-ttu-id="afca7-124">Çift yönlü hizmetler hakkında daha fazla bilgi için bkz. [nasıl yapılır: çift yönlü sözleşme oluşturma](../../../wcf/feature-details/how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="afca7-124">For more information about duplex services, see [How to: Create a Duplex Contract](../../../wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
 <span data-ttu-id="afca7-125">Bu öğedeki sertifika kümesi, iletileri yalnızca `MutualCertificateDuplex` ileti güvenliği kimlik doğrulama moduyla yapılandırılan bağlamalar için istemciye şifrelemek üzere kullanılır.</span><span class="sxs-lookup"><span data-stu-id="afca7-125">The certificate set in this element is used to encrypt messages to the client only for bindings that are configured with `MutualCertificateDuplex` message security authentication mode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afca7-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="afca7-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ClientCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>
- [<span data-ttu-id="afca7-127">Nasıl yapılır: Çift Yönlü Sözleşme Oluşturma</span><span class="sxs-lookup"><span data-stu-id="afca7-127">How to: Create a Duplex Contract</span></span>](../../../wcf/feature-details/how-to-create-a-duplex-contract.md)
- [<span data-ttu-id="afca7-128">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="afca7-128">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="afca7-129">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="afca7-129">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
