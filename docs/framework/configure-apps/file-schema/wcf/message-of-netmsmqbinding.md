---
title: <message> / <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
ms.openlocfilehash: b163dcb08e9656e3bde9c7fbb71fa1c92c9957ca
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931510"
---
# <a name="message-of-netmsmqbinding"></a><span data-ttu-id="48cae-102">\<\<NetMsmqBinding > ileti ></span><span class="sxs-lookup"><span data-stu-id="48cae-102">\<message> of \<netMsmqBinding></span></span>

<span data-ttu-id="48cae-103">Bu `netMsmqBinding` bağlamada soap iletisi güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="48cae-103">Defines the SOAP message security settings on this `netMsmqBinding` binding.</span></span>

```xml
<system.ServiceModel>
  <bindings>
    <netMsmqBinding>
      <binding>
        <security>
          <message>
```

## <a name="syntax"></a><span data-ttu-id="48cae-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="48cae-104">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="48cae-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="48cae-105">Attributes and Elements</span></span>

<span data-ttu-id="48cae-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="48cae-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="48cae-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="48cae-107">Attributes</span></span>

|<span data-ttu-id="48cae-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="48cae-108">Attribute</span></span>|<span data-ttu-id="48cae-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="48cae-109">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="48cae-110">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="48cae-110">algorithmSuite</span></span>|<span data-ttu-id="48cae-111">MSMQ aktarımı üzerinden gönderilen iletiler için ileti tabanlı güvenlik elde etmek üzere kullanılan ileti şifrelemesini ve anahtar sarması algoritmalarını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="48cae-111">Sets the message encryption and key-wrap algorithms that are used to achieve message-based security for messages sent over MSMQ transport.</span></span><br /><br /> <span data-ttu-id="48cae-112">Varsayılan değer `Aes256` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="48cae-112">The default value is `Aes256`.</span></span> <span data-ttu-id="48cae-113">Bu öznitelik türü <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="48cae-113">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span>|
|<span data-ttu-id="48cae-114">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="48cae-114">clientCredentialType</span></span>|<span data-ttu-id="48cae-115">MSMQ aktarımı üzerinden gönderilen iletiler için istemci kimlik doğrulaması gerçekleştirirken kullanılacak kimlik bilgisinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="48cae-115">Specifies the type of credential to be used when performing client authentication for messages sent over the MSMQ transport.</span></span> <span data-ttu-id="48cae-116">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="48cae-116">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="48cae-117">Seçim Bu, hizmetin anonim istemcilerle etkileşime geçmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="48cae-117">-   None: This allows the service to interact with anonymous clients.</span></span> <span data-ttu-id="48cae-118">Ne hizmet ne de istemci bir kimlik bilgisi gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="48cae-118">Neither the service nor the client requires a credential.</span></span><br /><span data-ttu-id="48cae-119">Pencerelerin Bu, SOAP değişimlerinin bir Windows kimlik bilgisinin kimliği doğrulanmış bağlamı altında olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="48cae-119">-   Windows: This enables the SOAP exchanges to be under the authenticated context of a Windows credential.</span></span> <span data-ttu-id="48cae-120">Bu, her zaman Kerberos tabanlı kimlik doğrulaması gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="48cae-120">This always performs Kerberos-based authentication.</span></span><br /><span data-ttu-id="48cae-121">Nitelen Bu, hizmetin Kullanıcı adı kimlik bilgisi kullanarak kimlik doğrulaması yapmasını zorunlu kılabilir.</span><span class="sxs-lookup"><span data-stu-id="48cae-121">-   UserName: This enables the service to require that the client be authenticated using a UserName credential.</span></span> <span data-ttu-id="48cae-122">Bu durumda kimlik bilgisinin, `clientCredentials` davranış uyarısı kullanılarak belirtilmesi gerekir **:**  Windows Communication Foundation (WCF) parola özetinin gönderilmesini veya parola kullanarak anahtar türemesini veya ileti güvenliği için bu tuşları kullanmayı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="48cae-122">The credential in this case needs to be specified using the `clientCredentials` behavior **Caution:**  Windows Communication Foundation (WCF) does not support sending a password digest or deriving keys using password and using such keys for message security.</span></span> <span data-ttu-id="48cae-123">Bu nedenle, WCF, Kullanıcı adı kimlik bilgileri kullanılırken Exchange 'in güvenliğinin sağlanmasını zorunlu kılar.</span><span class="sxs-lookup"><span data-stu-id="48cae-123">Therefore, WCF enforces that the exchange is secured when using UserName credentials.</span></span> <span data-ttu-id="48cae-124">Bu mod, hizmet sertifikasının, ve `clientCredential` `serviceCertificate`davranışı kullanılarak istemci tarafında belirtilmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="48cae-124">This mode requires that the service certificate be specified on the client side using `clientCredential` behavior and `serviceCertificate`.</span></span> <br /><br /> <span data-ttu-id="48cae-125">Sertifika Bu, hizmetin bir sertifika kullanarak kimliğinin doğrulanmasını gerektirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="48cae-125">-   Certificate: This enables the service to require that the client be authenticated using a certificate.</span></span> <span data-ttu-id="48cae-126">Bu durumda istemci kimlik bilgisinin `clientCredentials` davranış kullanılarak belirtilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="48cae-126">The client credential in this case needs to be specified using the `clientCredentials` behavior.</span></span> <span data-ttu-id="48cae-127">Bu durumda hizmet kimlik bilgilerinin, `clientCredentials` `serviceCertificate`yöntemi belirtilerek davranışı kullanılarak belirtilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="48cae-127">The service credential in this case needs to be specified using the `clientCredentials` behavior by specifying the `serviceCertificate`.</span></span><br /><span data-ttu-id="48cae-128">Rağmen Bu, hizmetin bir CardSpace kullanarak istemcinin kimliğinin doğrulanmasını gerektirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="48cae-128">-   CardSpace: This allows the service to require that the client be authenticated using a CardSpace.</span></span> <span data-ttu-id="48cae-129">Davranışınınsağlanması`clientCredential` gerekir `serviceCertificate` .</span><span class="sxs-lookup"><span data-stu-id="48cae-129">The `serviceCertificate` must be provisioned in the `clientCredential` behavior.</span></span><br /><br /> <span data-ttu-id="48cae-130">Varsayılan değer `Windows` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="48cae-130">The default value is `Windows`.</span></span> <span data-ttu-id="48cae-131">Bu öznitelik türü <xref:System.ServiceModel.MessageCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="48cae-131">This attribute is of type <xref:System.ServiceModel.MessageCredentialType>.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="48cae-132">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="48cae-132">Child Elements</span></span>

<span data-ttu-id="48cae-133">Yok.</span><span class="sxs-lookup"><span data-stu-id="48cae-133">None</span></span>

### <a name="parent-elements"></a><span data-ttu-id="48cae-134">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="48cae-134">Parent Elements</span></span>

|<span data-ttu-id="48cae-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="48cae-135">Element</span></span>|<span data-ttu-id="48cae-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="48cae-136">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="48cae-137">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="48cae-137">\<security></span></span>](security-of-netmsmqbinding.md)|<span data-ttu-id="48cae-138">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="48cae-138">Defines the security settings for a binding.</span></span>|

## <a name="see-also"></a><span data-ttu-id="48cae-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="48cae-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>
- <xref:System.ServiceModel.MessageSecurityOverMsmq>
- [<span data-ttu-id="48cae-140">WCF'de Kuyruklar</span><span class="sxs-lookup"><span data-stu-id="48cae-140">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="48cae-141">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="48cae-141">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="48cae-142">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="48cae-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="48cae-143">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="48cae-143">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="48cae-144">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="48cae-144">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="48cae-145">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="48cae-145">\<binding></span></span>](../../../misc/binding.md)
