---
title: <message> / <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
ms.openlocfilehash: 5a4a4e8b645ee2c607988ac3031af537c93ca8c0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736749"
---
# <a name="message-of-netmsmqbinding"></a><span data-ttu-id="c1692-102">\<message> / \<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="c1692-102">\<message> of \<netMsmqBinding></span></span>

<span data-ttu-id="c1692-103">Bu bağlamada SOAP iletisi güvenlik ayarlarını tanımlar `netMsmqBinding` .</span><span class="sxs-lookup"><span data-stu-id="c1692-103">Defines the SOAP message security settings on this `netMsmqBinding` binding.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBinding>**](netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**  

## <a name="syntax"></a><span data-ttu-id="c1692-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c1692-104">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="c1692-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c1692-105">Attributes and Elements</span></span>

<span data-ttu-id="c1692-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c1692-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="c1692-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c1692-107">Attributes</span></span>

|<span data-ttu-id="c1692-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c1692-108">Attribute</span></span>|<span data-ttu-id="c1692-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c1692-109">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="c1692-110">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="c1692-110">algorithmSuite</span></span>|<span data-ttu-id="c1692-111">MSMQ aktarımı üzerinden gönderilen iletiler için ileti tabanlı güvenlik elde etmek üzere kullanılan ileti şifrelemesini ve anahtar sarması algoritmalarını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c1692-111">Sets the message encryption and key-wrap algorithms that are used to achieve message-based security for messages sent over MSMQ transport.</span></span><br /><br /> <span data-ttu-id="c1692-112">Varsayılan değer: `Aes256`.</span><span class="sxs-lookup"><span data-stu-id="c1692-112">The default value is `Aes256`.</span></span> <span data-ttu-id="c1692-113">Bu öznitelik türü <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> .</span><span class="sxs-lookup"><span data-stu-id="c1692-113">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span>|
|<span data-ttu-id="c1692-114">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="c1692-114">clientCredentialType</span></span>|<span data-ttu-id="c1692-115">MSMQ aktarımı üzerinden gönderilen iletiler için istemci kimlik doğrulaması gerçekleştirirken kullanılacak kimlik bilgisinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="c1692-115">Specifies the type of credential to be used when performing client authentication for messages sent over the MSMQ transport.</span></span> <span data-ttu-id="c1692-116">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="c1692-116">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="c1692-117">-None: Bu, hizmetin anonim istemcilerle etkileşime geçmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="c1692-117">-   None: This allows the service to interact with anonymous clients.</span></span> <span data-ttu-id="c1692-118">Ne hizmet ne de istemci bir kimlik bilgisi gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="c1692-118">Neither the service nor the client requires a credential.</span></span><br /><span data-ttu-id="c1692-119">-Windows: Bu, SOAP değişimlerinin bir Windows kimlik bilgisinin kimliği doğrulanmış bağlamı altında olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="c1692-119">-   Windows: This enables the SOAP exchanges to be under the authenticated context of a Windows credential.</span></span> <span data-ttu-id="c1692-120">Bu, her zaman Kerberos tabanlı kimlik doğrulaması gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="c1692-120">This always performs Kerberos-based authentication.</span></span><br /><span data-ttu-id="c1692-121">-UserName: Bu, hizmetin, bir Kullanıcı adı kimlik bilgisi kullanılarak kimliğinin doğrulanmasını gerektirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="c1692-121">-   UserName: This enables the service to require that the client be authenticated using a UserName credential.</span></span> <span data-ttu-id="c1692-122">Bu durumda kimlik bilgisinin davranış biçimi kullanılarak belirtilmesi gerekir `clientCredentials` **:** Windows Communication Foundation (WCF) parola özetinin gönderilmesini veya parolayı kullanarak anahtar türemesini veya ileti güvenliği için bu anahtarları kullanmayı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="c1692-122">The credential in this case needs to be specified using the `clientCredentials` behavior **Caution:**  Windows Communication Foundation (WCF) does not support sending a password digest or deriving keys using password and using such keys for message security.</span></span> <span data-ttu-id="c1692-123">Bu nedenle, WCF, Kullanıcı adı kimlik bilgileri kullanılırken Exchange 'in güvenliğinin sağlanmasını zorunlu kılar.</span><span class="sxs-lookup"><span data-stu-id="c1692-123">Therefore, WCF enforces that the exchange is secured when using UserName credentials.</span></span> <span data-ttu-id="c1692-124">Bu mod, hizmet sertifikasının, ve davranışı kullanılarak istemci tarafında belirtilmesini gerektirir `clientCredential` `serviceCertificate` .</span><span class="sxs-lookup"><span data-stu-id="c1692-124">This mode requires that the service certificate be specified on the client side using `clientCredential` behavior and `serviceCertificate`.</span></span> <br /><br /> <span data-ttu-id="c1692-125">-Certificate: Bu, hizmetin bir sertifika kullanarak kimlik doğrulaması yapmasını zorunlu kılabilir.</span><span class="sxs-lookup"><span data-stu-id="c1692-125">-   Certificate: This enables the service to require that the client be authenticated using a certificate.</span></span> <span data-ttu-id="c1692-126">Bu durumda istemci kimlik bilgisinin davranış kullanılarak belirtilmesi gerekir `clientCredentials` .</span><span class="sxs-lookup"><span data-stu-id="c1692-126">The client credential in this case needs to be specified using the `clientCredentials` behavior.</span></span> <span data-ttu-id="c1692-127">Bu durumda hizmet kimlik bilgilerinin `clientCredentials` , yöntemi belirtilerek davranışı kullanılarak belirtilmesi gerekir `serviceCertificate` .</span><span class="sxs-lookup"><span data-stu-id="c1692-127">The service credential in this case needs to be specified using the `clientCredentials` behavior by specifying the `serviceCertificate`.</span></span><br /><span data-ttu-id="c1692-128">-CardSpace: Bu, hizmetin bir CardSpace kullanarak kimliğinin doğrulanmasını gerektirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="c1692-128">-   CardSpace: This allows the service to require that the client be authenticated using a CardSpace.</span></span> <span data-ttu-id="c1692-129">`serviceCertificate`Davranışının sağlanması gerekir `clientCredential` .</span><span class="sxs-lookup"><span data-stu-id="c1692-129">The `serviceCertificate` must be provisioned in the `clientCredential` behavior.</span></span><br /><br /> <span data-ttu-id="c1692-130">Varsayılan değer: `Windows`.</span><span class="sxs-lookup"><span data-stu-id="c1692-130">The default value is `Windows`.</span></span> <span data-ttu-id="c1692-131">Bu öznitelik türü <xref:System.ServiceModel.MessageCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="c1692-131">This attribute is of type <xref:System.ServiceModel.MessageCredentialType>.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="c1692-132">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c1692-132">Child Elements</span></span>

<span data-ttu-id="c1692-133">Yok</span><span class="sxs-lookup"><span data-stu-id="c1692-133">None</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c1692-134">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c1692-134">Parent Elements</span></span>

|<span data-ttu-id="c1692-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="c1692-135">Element</span></span>|<span data-ttu-id="c1692-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c1692-136">Description</span></span>|
|-------------|-----------------|
|[\<security>](security-of-netmsmqbinding.md)|<span data-ttu-id="c1692-137">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c1692-137">Defines the security settings for a binding.</span></span>|

## <a name="see-also"></a><span data-ttu-id="c1692-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c1692-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>
- <xref:System.ServiceModel.MessageSecurityOverMsmq>
- [<span data-ttu-id="c1692-139">WCF'de Kuyruklar</span><span class="sxs-lookup"><span data-stu-id="c1692-139">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="c1692-140">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="c1692-140">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="c1692-141">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="c1692-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="c1692-142">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c1692-142">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="c1692-143">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="c1692-143">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
