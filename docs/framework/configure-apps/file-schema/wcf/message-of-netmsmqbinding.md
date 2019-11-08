---
title: <message> / <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
ms.openlocfilehash: 5a4a4e8b645ee2c607988ac3031af537c93ca8c0
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736749"
---
# <a name="message-of-netmsmqbinding"></a><span data-ttu-id="dbd7c-102">\<netMsmqBinding > \<ileti ></span><span class="sxs-lookup"><span data-stu-id="dbd7c-102">\<message> of \<netMsmqBinding></span></span>

<span data-ttu-id="dbd7c-103">Bu `netMsmqBinding` bağlamasındaki SOAP iletisi güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="dbd7c-103">Defines the SOAP message security settings on this `netMsmqBinding` binding.</span></span>

<span data-ttu-id="dbd7c-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="dbd7c-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="dbd7c-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="dbd7c-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="dbd7c-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="dbd7c-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="dbd7c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netMsmqBinding >** ](netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="dbd7c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBinding>**](netmsmqbinding.md)</span></span>\
<span data-ttu-id="dbd7c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="dbd7c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="dbd7c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<güvenlik >** ](security-of-netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="dbd7c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netmsmqbinding.md)</span></span>\
<span data-ttu-id="dbd7c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<ileti >**</span><span class="sxs-lookup"><span data-stu-id="dbd7c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="dbd7c-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dbd7c-111">Syntax</span></span>

```xml
<netMsmqBinding>
  <binding>
    <security>
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
    </security>
  </binding>
</netMsmqBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="dbd7c-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="dbd7c-112">Attributes and Elements</span></span>

<span data-ttu-id="dbd7c-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dbd7c-113">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="dbd7c-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="dbd7c-114">Attributes</span></span>

|<span data-ttu-id="dbd7c-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="dbd7c-115">Attribute</span></span>|<span data-ttu-id="dbd7c-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dbd7c-116">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="dbd7c-117">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="dbd7c-117">algorithmSuite</span></span>|<span data-ttu-id="dbd7c-118">MSMQ aktarımı üzerinden gönderilen iletiler için ileti tabanlı güvenlik elde etmek üzere kullanılan ileti şifrelemesini ve anahtar sarması algoritmalarını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="dbd7c-118">Sets the message encryption and key-wrap algorithms that are used to achieve message-based security for messages sent over MSMQ transport.</span></span><br /><br /> <span data-ttu-id="dbd7c-119">Varsayılan değer `Aes256` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="dbd7c-119">The default value is `Aes256`.</span></span> <span data-ttu-id="dbd7c-120">Bu öznitelik <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>türündedir.</span><span class="sxs-lookup"><span data-stu-id="dbd7c-120">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span>|
|<span data-ttu-id="dbd7c-121">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="dbd7c-121">clientCredentialType</span></span>|<span data-ttu-id="dbd7c-122">MSMQ aktarımı üzerinden gönderilen iletiler için istemci kimlik doğrulaması gerçekleştirirken kullanılacak kimlik bilgisinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="dbd7c-122">Specifies the type of credential to be used when performing client authentication for messages sent over the MSMQ transport.</span></span> <span data-ttu-id="dbd7c-123">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="dbd7c-123">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="dbd7c-124">-None: Bu, hizmetin anonim istemcilerle etkileşime geçmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="dbd7c-124">-   None: This allows the service to interact with anonymous clients.</span></span> <span data-ttu-id="dbd7c-125">Ne hizmet ne de istemci bir kimlik bilgisi gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="dbd7c-125">Neither the service nor the client requires a credential.</span></span><br /><span data-ttu-id="dbd7c-126">-Windows: Bu, SOAP değişimlerinin bir Windows kimlik bilgisinin kimliği doğrulanmış bağlamı altında olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="dbd7c-126">-   Windows: This enables the SOAP exchanges to be under the authenticated context of a Windows credential.</span></span> <span data-ttu-id="dbd7c-127">Bu, her zaman Kerberos tabanlı kimlik doğrulaması gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="dbd7c-127">This always performs Kerberos-based authentication.</span></span><br /><span data-ttu-id="dbd7c-128">-UserName: Bu, hizmetin, bir Kullanıcı adı kimlik bilgisi kullanılarak kimliğinin doğrulanmasını gerektirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="dbd7c-128">-   UserName: This enables the service to require that the client be authenticated using a UserName credential.</span></span> <span data-ttu-id="dbd7c-129">Bu durumda kimlik bilgisinin **`clientCredentials` davranışı kullanılarak belirtilmesi gerekir. Windows Communication Foundation** (WCF) parola özetinin gönderilmesini veya parolayı kullanarak anahtar türemesini veya ileti güvenliği için bu anahtarları kullanmayı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="dbd7c-129">The credential in this case needs to be specified using the `clientCredentials` behavior **Caution:**  Windows Communication Foundation (WCF) does not support sending a password digest or deriving keys using password and using such keys for message security.</span></span> <span data-ttu-id="dbd7c-130">Bu nedenle, WCF, Kullanıcı adı kimlik bilgileri kullanılırken Exchange 'in güvenliğinin sağlanmasını zorunlu kılar.</span><span class="sxs-lookup"><span data-stu-id="dbd7c-130">Therefore, WCF enforces that the exchange is secured when using UserName credentials.</span></span> <span data-ttu-id="dbd7c-131">Bu mod, hizmet sertifikasının istemci tarafında `clientCredential` davranış ve `serviceCertificate`kullanılarak belirtilmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="dbd7c-131">This mode requires that the service certificate be specified on the client side using `clientCredential` behavior and `serviceCertificate`.</span></span> <br /><br /> <span data-ttu-id="dbd7c-132">-Certificate: Bu, hizmetin bir sertifika kullanarak kimlik doğrulaması yapmasını zorunlu kılabilir.</span><span class="sxs-lookup"><span data-stu-id="dbd7c-132">-   Certificate: This enables the service to require that the client be authenticated using a certificate.</span></span> <span data-ttu-id="dbd7c-133">Bu durumda istemci kimlik bilgisinin `clientCredentials` davranışı kullanılarak belirtilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="dbd7c-133">The client credential in this case needs to be specified using the `clientCredentials` behavior.</span></span> <span data-ttu-id="dbd7c-134">Bu durumda hizmet kimlik bilgisinin, `serviceCertificate`belirtilerek `clientCredentials` davranışı kullanılarak belirtilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="dbd7c-134">The service credential in this case needs to be specified using the `clientCredentials` behavior by specifying the `serviceCertificate`.</span></span><br /><span data-ttu-id="dbd7c-135">-CardSpace: Bu, hizmetin bir CardSpace kullanarak kimliğinin doğrulanmasını gerektirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="dbd7c-135">-   CardSpace: This allows the service to require that the client be authenticated using a CardSpace.</span></span> <span data-ttu-id="dbd7c-136">`serviceCertificate` `clientCredential` davranışının sağlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="dbd7c-136">The `serviceCertificate` must be provisioned in the `clientCredential` behavior.</span></span><br /><br /> <span data-ttu-id="dbd7c-137">Varsayılan değer `Windows` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="dbd7c-137">The default value is `Windows`.</span></span> <span data-ttu-id="dbd7c-138">Bu öznitelik <xref:System.ServiceModel.MessageCredentialType>türündedir.</span><span class="sxs-lookup"><span data-stu-id="dbd7c-138">This attribute is of type <xref:System.ServiceModel.MessageCredentialType>.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="dbd7c-139">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="dbd7c-139">Child Elements</span></span>

<span data-ttu-id="dbd7c-140">Yok.</span><span class="sxs-lookup"><span data-stu-id="dbd7c-140">None</span></span>

### <a name="parent-elements"></a><span data-ttu-id="dbd7c-141">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="dbd7c-141">Parent Elements</span></span>

|<span data-ttu-id="dbd7c-142">Öğe</span><span class="sxs-lookup"><span data-stu-id="dbd7c-142">Element</span></span>|<span data-ttu-id="dbd7c-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dbd7c-143">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dbd7c-144">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="dbd7c-144">\<security></span></span>](security-of-netmsmqbinding.md)|<span data-ttu-id="dbd7c-145">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="dbd7c-145">Defines the security settings for a binding.</span></span>|

## <a name="see-also"></a><span data-ttu-id="dbd7c-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dbd7c-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>
- <xref:System.ServiceModel.MessageSecurityOverMsmq>
- [<span data-ttu-id="dbd7c-147">WCF'de Kuyruklar</span><span class="sxs-lookup"><span data-stu-id="dbd7c-147">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="dbd7c-148">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="dbd7c-148">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="dbd7c-149">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="dbd7c-149">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="dbd7c-150">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="dbd7c-150">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="dbd7c-151">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="dbd7c-151">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="dbd7c-152">\< bağlama ></span><span class="sxs-lookup"><span data-stu-id="dbd7c-152">\<binding></span></span>](bindings.md)
