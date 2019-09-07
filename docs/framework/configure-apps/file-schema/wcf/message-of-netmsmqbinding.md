---
title: <message> / <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
ms.openlocfilehash: 09d9d4a5d1967afaf9a6ed5756c309e78fee0923
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400252"
---
# <a name="message-of-netmsmqbinding"></a><span data-ttu-id="fe1b1-102">\<\<NetMsmqBinding > ileti ></span><span class="sxs-lookup"><span data-stu-id="fe1b1-102">\<message> of \<netMsmqBinding></span></span>

<span data-ttu-id="fe1b1-103">Bu `netMsmqBinding` bağlamada soap iletisi güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fe1b1-103">Defines the SOAP message security settings on this `netMsmqBinding` binding.</span></span>

<span data-ttu-id="fe1b1-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="fe1b1-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="fe1b1-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="fe1b1-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="fe1b1-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlama >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="fe1b1-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="fe1b1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netMsmqBinding >** ](netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="fe1b1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBinding>**](netmsmqbinding.md)</span></span>\
<span data-ttu-id="fe1b1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="fe1b1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="fe1b1-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Güvenlik >** ](security-of-netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="fe1b1-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netmsmqbinding.md)</span></span>\
<span data-ttu-id="fe1b1-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<ileti >**</span><span class="sxs-lookup"><span data-stu-id="fe1b1-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="fe1b1-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fe1b1-111">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="fe1b1-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fe1b1-112">Attributes and Elements</span></span>

<span data-ttu-id="fe1b1-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fe1b1-113">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="fe1b1-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fe1b1-114">Attributes</span></span>

|<span data-ttu-id="fe1b1-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fe1b1-115">Attribute</span></span>|<span data-ttu-id="fe1b1-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fe1b1-116">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="fe1b1-117">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="fe1b1-117">algorithmSuite</span></span>|<span data-ttu-id="fe1b1-118">MSMQ aktarımı üzerinden gönderilen iletiler için ileti tabanlı güvenlik elde etmek üzere kullanılan ileti şifrelemesini ve anahtar sarması algoritmalarını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="fe1b1-118">Sets the message encryption and key-wrap algorithms that are used to achieve message-based security for messages sent over MSMQ transport.</span></span><br /><br /> <span data-ttu-id="fe1b1-119">Varsayılan değer `Aes256` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="fe1b1-119">The default value is `Aes256`.</span></span> <span data-ttu-id="fe1b1-120">Bu öznitelik türü <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="fe1b1-120">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span>|
|<span data-ttu-id="fe1b1-121">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="fe1b1-121">clientCredentialType</span></span>|<span data-ttu-id="fe1b1-122">MSMQ aktarımı üzerinden gönderilen iletiler için istemci kimlik doğrulaması gerçekleştirirken kullanılacak kimlik bilgisinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="fe1b1-122">Specifies the type of credential to be used when performing client authentication for messages sent over the MSMQ transport.</span></span> <span data-ttu-id="fe1b1-123">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="fe1b1-123">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="fe1b1-124">Seçim Bu, hizmetin anonim istemcilerle etkileşime geçmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe1b1-124">-   None: This allows the service to interact with anonymous clients.</span></span> <span data-ttu-id="fe1b1-125">Ne hizmet ne de istemci bir kimlik bilgisi gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="fe1b1-125">Neither the service nor the client requires a credential.</span></span><br /><span data-ttu-id="fe1b1-126">Pencerelerin Bu, SOAP değişimlerinin bir Windows kimlik bilgisinin kimliği doğrulanmış bağlamı altında olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe1b1-126">-   Windows: This enables the SOAP exchanges to be under the authenticated context of a Windows credential.</span></span> <span data-ttu-id="fe1b1-127">Bu, her zaman Kerberos tabanlı kimlik doğrulaması gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="fe1b1-127">This always performs Kerberos-based authentication.</span></span><br /><span data-ttu-id="fe1b1-128">Nitelen Bu, hizmetin Kullanıcı adı kimlik bilgisi kullanarak kimlik doğrulaması yapmasını zorunlu kılabilir.</span><span class="sxs-lookup"><span data-stu-id="fe1b1-128">-   UserName: This enables the service to require that the client be authenticated using a UserName credential.</span></span> <span data-ttu-id="fe1b1-129">Bu durumda kimlik bilgisinin, `clientCredentials` davranış uyarısı kullanılarak belirtilmesi gerekir **:**  Windows Communication Foundation (WCF) parola özetinin gönderilmesini veya parola kullanarak anahtar türemesini veya ileti güvenliği için bu tuşları kullanmayı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="fe1b1-129">The credential in this case needs to be specified using the `clientCredentials` behavior **Caution:**  Windows Communication Foundation (WCF) does not support sending a password digest or deriving keys using password and using such keys for message security.</span></span> <span data-ttu-id="fe1b1-130">Bu nedenle, WCF, Kullanıcı adı kimlik bilgileri kullanılırken Exchange 'in güvenliğinin sağlanmasını zorunlu kılar.</span><span class="sxs-lookup"><span data-stu-id="fe1b1-130">Therefore, WCF enforces that the exchange is secured when using UserName credentials.</span></span> <span data-ttu-id="fe1b1-131">Bu mod, hizmet sertifikasının, ve `clientCredential` `serviceCertificate`davranışı kullanılarak istemci tarafında belirtilmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="fe1b1-131">This mode requires that the service certificate be specified on the client side using `clientCredential` behavior and `serviceCertificate`.</span></span> <br /><br /> <span data-ttu-id="fe1b1-132">Sertifika Bu, hizmetin bir sertifika kullanarak kimliğinin doğrulanmasını gerektirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe1b1-132">-   Certificate: This enables the service to require that the client be authenticated using a certificate.</span></span> <span data-ttu-id="fe1b1-133">Bu durumda istemci kimlik bilgisinin `clientCredentials` davranış kullanılarak belirtilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="fe1b1-133">The client credential in this case needs to be specified using the `clientCredentials` behavior.</span></span> <span data-ttu-id="fe1b1-134">Bu durumda hizmet kimlik bilgilerinin, `clientCredentials` `serviceCertificate`yöntemi belirtilerek davranışı kullanılarak belirtilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="fe1b1-134">The service credential in this case needs to be specified using the `clientCredentials` behavior by specifying the `serviceCertificate`.</span></span><br /><span data-ttu-id="fe1b1-135">Rağmen Bu, hizmetin bir CardSpace kullanarak istemcinin kimliğinin doğrulanmasını gerektirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe1b1-135">-   CardSpace: This allows the service to require that the client be authenticated using a CardSpace.</span></span> <span data-ttu-id="fe1b1-136">Davranışınınsağlanması`clientCredential` gerekir `serviceCertificate` .</span><span class="sxs-lookup"><span data-stu-id="fe1b1-136">The `serviceCertificate` must be provisioned in the `clientCredential` behavior.</span></span><br /><br /> <span data-ttu-id="fe1b1-137">Varsayılan değer `Windows` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="fe1b1-137">The default value is `Windows`.</span></span> <span data-ttu-id="fe1b1-138">Bu öznitelik türü <xref:System.ServiceModel.MessageCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="fe1b1-138">This attribute is of type <xref:System.ServiceModel.MessageCredentialType>.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="fe1b1-139">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fe1b1-139">Child Elements</span></span>

<span data-ttu-id="fe1b1-140">Yok.</span><span class="sxs-lookup"><span data-stu-id="fe1b1-140">None</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fe1b1-141">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fe1b1-141">Parent Elements</span></span>

|<span data-ttu-id="fe1b1-142">Öğe</span><span class="sxs-lookup"><span data-stu-id="fe1b1-142">Element</span></span>|<span data-ttu-id="fe1b1-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fe1b1-143">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fe1b1-144">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="fe1b1-144">\<security></span></span>](security-of-netmsmqbinding.md)|<span data-ttu-id="fe1b1-145">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fe1b1-145">Defines the security settings for a binding.</span></span>|

## <a name="see-also"></a><span data-ttu-id="fe1b1-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe1b1-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>
- <xref:System.ServiceModel.MessageSecurityOverMsmq>
- [<span data-ttu-id="fe1b1-147">WCF'de Kuyruklar</span><span class="sxs-lookup"><span data-stu-id="fe1b1-147">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="fe1b1-148">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="fe1b1-148">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="fe1b1-149">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="fe1b1-149">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="fe1b1-150">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="fe1b1-150">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="fe1b1-151">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="fe1b1-151">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="fe1b1-152">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="fe1b1-152">\<binding></span></span>](../../../misc/binding.md)
