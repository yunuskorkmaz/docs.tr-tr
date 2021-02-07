---
description: 'Hakkında daha fazla bilgi <message> edinin: <netMsmqBinding>'
title: <message> / <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
ms.openlocfilehash: 0e8cf641ef8ba5361318f7b658d5d60beef6ce56
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749590"
---
# <a name="message-of-netmsmqbinding"></a><span data-ttu-id="0b5e6-103">\<message> / \<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="0b5e6-103">\<message> of \<netMsmqBinding></span></span>

<span data-ttu-id="0b5e6-104">Bu bağlamada SOAP iletisi güvenlik ayarlarını tanımlar `netMsmqBinding` .</span><span class="sxs-lookup"><span data-stu-id="0b5e6-104">Defines the SOAP message security settings on this `netMsmqBinding` binding.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBinding>**](netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**  

## <a name="syntax"></a><span data-ttu-id="0b5e6-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="0b5e6-105">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="0b5e6-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0b5e6-106">Attributes and Elements</span></span>

<span data-ttu-id="0b5e6-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0b5e6-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="0b5e6-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0b5e6-108">Attributes</span></span>

|<span data-ttu-id="0b5e6-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0b5e6-109">Attribute</span></span>|<span data-ttu-id="0b5e6-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0b5e6-110">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="0b5e6-111">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="0b5e6-111">algorithmSuite</span></span>|<span data-ttu-id="0b5e6-112">MSMQ aktarımı üzerinden gönderilen iletiler için ileti tabanlı güvenlik elde etmek üzere kullanılan ileti şifrelemesini ve anahtar sarması algoritmalarını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0b5e6-112">Sets the message encryption and key-wrap algorithms that are used to achieve message-based security for messages sent over MSMQ transport.</span></span><br /><br /> <span data-ttu-id="0b5e6-113">`Aes256` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="0b5e6-113">The default value is `Aes256`.</span></span> <span data-ttu-id="0b5e6-114">Bu öznitelik türü <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> .</span><span class="sxs-lookup"><span data-stu-id="0b5e6-114">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span>|
|<span data-ttu-id="0b5e6-115">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="0b5e6-115">clientCredentialType</span></span>|<span data-ttu-id="0b5e6-116">MSMQ aktarımı üzerinden gönderilen iletiler için istemci kimlik doğrulaması gerçekleştirirken kullanılacak kimlik bilgisinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="0b5e6-116">Specifies the type of credential to be used when performing client authentication for messages sent over the MSMQ transport.</span></span> <span data-ttu-id="0b5e6-117">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="0b5e6-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="0b5e6-118">-None: Bu, hizmetin anonim istemcilerle etkileşime geçmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="0b5e6-118">-   None: This allows the service to interact with anonymous clients.</span></span> <span data-ttu-id="0b5e6-119">Ne hizmet ne de istemci bir kimlik bilgisi gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="0b5e6-119">Neither the service nor the client requires a credential.</span></span><br /><span data-ttu-id="0b5e6-120">-Windows: Bu, SOAP değişimlerinin bir Windows kimlik bilgisinin kimliği doğrulanmış bağlamı altında olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="0b5e6-120">-   Windows: This enables the SOAP exchanges to be under the authenticated context of a Windows credential.</span></span> <span data-ttu-id="0b5e6-121">Bu, her zaman Kerberos tabanlı kimlik doğrulaması gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="0b5e6-121">This always performs Kerberos-based authentication.</span></span><br /><span data-ttu-id="0b5e6-122">-UserName: Bu, hizmetin, bir Kullanıcı adı kimlik bilgisi kullanılarak kimliğinin doğrulanmasını gerektirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="0b5e6-122">-   UserName: This enables the service to require that the client be authenticated using a UserName credential.</span></span> <span data-ttu-id="0b5e6-123">Bu durumda kimlik bilgisinin davranış biçimi kullanılarak belirtilmesi gerekir `clientCredentials` **:**  Windows Communication Foundation (WCF) parola özetinin gönderilmesini veya parolayı kullanarak anahtar türemesini veya ileti güvenliği için bu anahtarları kullanmayı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="0b5e6-123">The credential in this case needs to be specified using the `clientCredentials` behavior **Caution:**  Windows Communication Foundation (WCF) does not support sending a password digest or deriving keys using password and using such keys for message security.</span></span> <span data-ttu-id="0b5e6-124">Bu nedenle, WCF, Kullanıcı adı kimlik bilgileri kullanılırken Exchange 'in güvenliğinin sağlanmasını zorunlu kılar.</span><span class="sxs-lookup"><span data-stu-id="0b5e6-124">Therefore, WCF enforces that the exchange is secured when using UserName credentials.</span></span> <span data-ttu-id="0b5e6-125">Bu mod, hizmet sertifikasının, ve davranışı kullanılarak istemci tarafında belirtilmesini gerektirir `clientCredential` `serviceCertificate` .</span><span class="sxs-lookup"><span data-stu-id="0b5e6-125">This mode requires that the service certificate be specified on the client side using `clientCredential` behavior and `serviceCertificate`.</span></span> <br /><br /> <span data-ttu-id="0b5e6-126">-Certificate: Bu, hizmetin bir sertifika kullanarak kimlik doğrulaması yapmasını zorunlu kılabilir.</span><span class="sxs-lookup"><span data-stu-id="0b5e6-126">-   Certificate: This enables the service to require that the client be authenticated using a certificate.</span></span> <span data-ttu-id="0b5e6-127">Bu durumda istemci kimlik bilgisinin davranış kullanılarak belirtilmesi gerekir `clientCredentials` .</span><span class="sxs-lookup"><span data-stu-id="0b5e6-127">The client credential in this case needs to be specified using the `clientCredentials` behavior.</span></span> <span data-ttu-id="0b5e6-128">Bu durumda hizmet kimlik bilgilerinin `clientCredentials` , yöntemi belirtilerek davranışı kullanılarak belirtilmesi gerekir `serviceCertificate` .</span><span class="sxs-lookup"><span data-stu-id="0b5e6-128">The service credential in this case needs to be specified using the `clientCredentials` behavior by specifying the `serviceCertificate`.</span></span><br /><span data-ttu-id="0b5e6-129">-CardSpace: Bu, hizmetin bir CardSpace kullanarak kimliğinin doğrulanmasını gerektirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="0b5e6-129">-   CardSpace: This allows the service to require that the client be authenticated using a CardSpace.</span></span> <span data-ttu-id="0b5e6-130">`serviceCertificate`Davranışının sağlanması gerekir `clientCredential` .</span><span class="sxs-lookup"><span data-stu-id="0b5e6-130">The `serviceCertificate` must be provisioned in the `clientCredential` behavior.</span></span><br /><br /> <span data-ttu-id="0b5e6-131">`Windows` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="0b5e6-131">The default value is `Windows`.</span></span> <span data-ttu-id="0b5e6-132">Bu öznitelik türü <xref:System.ServiceModel.MessageCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="0b5e6-132">This attribute is of type <xref:System.ServiceModel.MessageCredentialType>.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="0b5e6-133">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0b5e6-133">Child Elements</span></span>

<span data-ttu-id="0b5e6-134">Yok</span><span class="sxs-lookup"><span data-stu-id="0b5e6-134">None</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0b5e6-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0b5e6-135">Parent Elements</span></span>

|<span data-ttu-id="0b5e6-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="0b5e6-136">Element</span></span>|<span data-ttu-id="0b5e6-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0b5e6-137">Description</span></span>|
|-------------|-----------------|
|[\<security>](security-of-netmsmqbinding.md)|<span data-ttu-id="0b5e6-138">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0b5e6-138">Defines the security settings for a binding.</span></span>|

## <a name="see-also"></a><span data-ttu-id="0b5e6-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b5e6-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>
- <xref:System.ServiceModel.MessageSecurityOverMsmq>
- [<span data-ttu-id="0b5e6-140">WCF'de Kuyruklar</span><span class="sxs-lookup"><span data-stu-id="0b5e6-140">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="0b5e6-141">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="0b5e6-141">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="0b5e6-142">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="0b5e6-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="0b5e6-143">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="0b5e6-143">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="0b5e6-144">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="0b5e6-144">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
