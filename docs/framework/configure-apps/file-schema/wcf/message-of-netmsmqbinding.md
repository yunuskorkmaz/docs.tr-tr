---
title: '&lt;netMsmqBinding&gt; &lt;iletisi&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8a7fdb8c6df84a76450aabaa983275f563d342fa
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="ltmessagegt-of-ltnetmsmqbindinggt"></a><span data-ttu-id="a6597-102">&lt;netMsmqBinding&gt; &lt;iletisi&gt;</span><span class="sxs-lookup"><span data-stu-id="a6597-102">&lt;message&gt; of &lt;netMsmqBinding&gt;</span></span>
<span data-ttu-id="a6597-103">SOAP iletisi güvenlik ayarlarını bu tanımlar `netMsmqBinding` bağlama.</span><span class="sxs-lookup"><span data-stu-id="a6597-103">Defines the SOAP message security settings on this `netMsmqBinding` binding.</span></span>  
  
 <span data-ttu-id="a6597-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a6597-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a6597-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="a6597-105">\<bindings></span></span>  
<span data-ttu-id="a6597-106">\<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="a6597-106">\<netMsmqBinding></span></span>  
<span data-ttu-id="a6597-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="a6597-107">\<binding></span></span>  
<span data-ttu-id="a6597-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="a6597-108">\<security></span></span>  
<span data-ttu-id="a6597-109">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="a6597-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6597-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a6597-110">Syntax</span></span>  
  
```xml  
<netMsmqBinding>  
    <binding>  
      <security>  
         <message   
                      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />  
    </security>  
</netMsmqBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a6597-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a6597-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a6597-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a6597-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a6597-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a6597-113">Attributes</span></span>  
  
|<span data-ttu-id="a6597-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a6597-114">Attribute</span></span>|<span data-ttu-id="a6597-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a6597-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a6597-116">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="a6597-116">algorithmSuite</span></span>|<span data-ttu-id="a6597-117">İletinin MSMQ aktarımı üzerinden gönderilen iletiler için ileti tabanlı güvenlik elde etmek için kullanılan şifreleme ve anahtar-wrap algoritmaları ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a6597-117">Sets the message encryption and key-wrap algorithms that are used to achieve message-based security for messages sent over MSMQ transport.</span></span><br /><br /> <span data-ttu-id="a6597-118">Varsayılan değer `Aes256` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="a6597-118">The default value is `Aes256`.</span></span> <span data-ttu-id="a6597-119">Bu öznitelik türünde <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="a6597-119">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span>|  
|<span data-ttu-id="a6597-120">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="a6597-120">clientCredentialType</span></span>|<span data-ttu-id="a6597-121">MSMQ taşıma gönderilen iletiler için istemci kimlik doğrulaması yapılırken kullanılacak kimlik bilgileri türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="a6597-121">Specifies the type of credential to be used when performing client authentication for messages sent over the MSMQ transport.</span></span> <span data-ttu-id="a6597-122">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="a6597-122">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="a6597-123">-Hiçbiri: Bu, hizmetin anonim istemcilerle etkileşime girmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="a6597-123">-   None: This allows the service to interact with anonymous clients.</span></span> <span data-ttu-id="a6597-124">Hizmetin ne istemci bir kimlik bilgisi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a6597-124">Neither the service nor the client requires a credential.</span></span><br /><span data-ttu-id="a6597-125">-Windows: Bu SOAP alışverişleri Windows kimlik bilgisi kimliği doğrulanmış bağlamı altında olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="a6597-125">-   Windows: This enables the SOAP exchanges to be under the authenticated context of a Windows credential.</span></span> <span data-ttu-id="a6597-126">Bu her zaman Kerberos tabanlı kimlik doğrulaması gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="a6597-126">This always performs Kerberos-based authentication.</span></span><br /><span data-ttu-id="a6597-127">-UserName: Bu gerektirecek şekilde hizmetini etkinleştirir, istemci kimlik doğrulaması kullanıcı adı kimlik bilgilerini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="a6597-127">-   UserName: This enables the service to require that the client be authenticated using a UserName credential.</span></span> <span data-ttu-id="a6597-128">Kimlik bilgisi bu durumda kullanarak belirtilmesi gerekiyor `clientCredentials` davranışı **dikkat:** [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] parola kullanarak ve böyle anahtarların ileti güvenliği için kullanarak Özet veya türetme anahtarları bir parola gönderme desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="a6597-128">The credential in this case needs to be specified using the `clientCredentials` behavior **Caution:**  [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] does not support sending a password digest or deriving keys using password and using such keys for message security.</span></span> <span data-ttu-id="a6597-129">Bu nedenle, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] exchange kullanıcı adı kimlik bilgileri kullanılırken güvenli zorlar.</span><span class="sxs-lookup"><span data-stu-id="a6597-129">Therefore, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] enforces that the exchange is secured when using UserName credentials.</span></span> <span data-ttu-id="a6597-130">Bu mod hizmet sertifikası kullanarak istemci tarafı belirtilmesini gerektirir `clientCredential` davranışı ve `serviceCertificate`.</span><span class="sxs-lookup"><span data-stu-id="a6597-130">This mode requires that the service certificate be specified on the client side using `clientCredential` behavior and `serviceCertificate`.</span></span> <br /><br /> <span data-ttu-id="a6597-131">-Sertifika: Bu gerektirecek şekilde hizmetini etkinleştirir, istemci kimlik doğrulaması kullanarak bir sertifika.</span><span class="sxs-lookup"><span data-stu-id="a6597-131">-   Certificate: This enables the service to require that the client be authenticated using a certificate.</span></span> <span data-ttu-id="a6597-132">İstemci kimlik bilgileri bu durumda kullanarak belirtilmesi gerekiyor `clientCredentials` davranışı.</span><span class="sxs-lookup"><span data-stu-id="a6597-132">The client credential in this case needs to be specified using the `clientCredentials` behavior.</span></span> <span data-ttu-id="a6597-133">Hizmet kimlik bilgilerini bu durumda kullanarak belirtilmesi gerekiyor `clientCredentials` belirterek davranış `serviceCertificate`.</span><span class="sxs-lookup"><span data-stu-id="a6597-133">The service credential in this case needs to be specified using the `clientCredentials` behavior by specifying the `serviceCertificate`.</span></span><br /><span data-ttu-id="a6597-134">-CardSpace: Bu hizmet gerektirecek şekilde sağlar, istemci kimlik doğrulaması bir CardSpace kullanma.</span><span class="sxs-lookup"><span data-stu-id="a6597-134">-   CardSpace: This allows the service to require that the client be authenticated using a CardSpace.</span></span> <span data-ttu-id="a6597-135">`serviceCertiifcate` İçinde sağlanmalıdır `clientCredential` davranışı.</span><span class="sxs-lookup"><span data-stu-id="a6597-135">The `serviceCertiifcate` must be provisioned in the `clientCredential` behavior.</span></span><br /><br /> <span data-ttu-id="a6597-136">Varsayılan değer `Windows` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="a6597-136">The default value is `Windows`.</span></span> <span data-ttu-id="a6597-137">Bu öznitelik türünde <xref:System.ServiceModel.MessageCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="a6597-137">This attribute is of type <xref:System.ServiceModel.MessageCredentialType>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a6597-138">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a6597-138">Child Elements</span></span>  
 <span data-ttu-id="a6597-139">Yok.</span><span class="sxs-lookup"><span data-stu-id="a6597-139">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a6597-140">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a6597-140">Parent Elements</span></span>  
  
|<span data-ttu-id="a6597-141">Öğe</span><span class="sxs-lookup"><span data-stu-id="a6597-141">Element</span></span>|<span data-ttu-id="a6597-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a6597-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a6597-143">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="a6597-143">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|<span data-ttu-id="a6597-144">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a6597-144">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a6597-145">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a6597-145">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>  
 <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>  
 <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>  
 <xref:System.ServiceModel.MessageSecurityOverMsmq>  
 [<span data-ttu-id="a6597-146">WCF'de Kuyruklar</span><span class="sxs-lookup"><span data-stu-id="a6597-146">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [<span data-ttu-id="a6597-147">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="a6597-147">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="a6597-148">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="a6597-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="a6597-149">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a6597-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="a6597-150">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="a6597-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="a6597-151">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="a6597-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
