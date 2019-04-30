---
title: <message> / <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
ms.openlocfilehash: c623b7daf1e91c9c1800b9653525cd51b1087506
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768959"
---
# <a name="message-of-netmsmqbinding"></a><span data-ttu-id="f898f-102">\<İleti >, \<netMsmqBinding ></span><span class="sxs-lookup"><span data-stu-id="f898f-102">\<message> of \<netMsmqBinding></span></span>

<span data-ttu-id="f898f-103">SOAP ileti güvenlik ayarları bu tanımlar `netMsmqBinding` bağlama.</span><span class="sxs-lookup"><span data-stu-id="f898f-103">Defines the SOAP message security settings on this `netMsmqBinding` binding.</span></span>

```xml
<system.ServiceModel>
  <bindings>
    <netMsmqBinding>
      <binding>
        <security>
          <message>
```

## <a name="syntax"></a><span data-ttu-id="f898f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f898f-104">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="f898f-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f898f-105">Attributes and Elements</span></span>

<span data-ttu-id="f898f-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f898f-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="f898f-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f898f-107">Attributes</span></span>

|<span data-ttu-id="f898f-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f898f-108">Attribute</span></span>|<span data-ttu-id="f898f-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f898f-109">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="f898f-110">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="f898f-110">algorithmSuite</span></span>|<span data-ttu-id="f898f-111">İletinin MSMQ taşıma gönderilen iletiler için ileti tabanlı güvenlik elde etmek için kullanılan şifreleme ve anahtar-wrap algoritmaları ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f898f-111">Sets the message encryption and key-wrap algorithms that are used to achieve message-based security for messages sent over MSMQ transport.</span></span><br /><br /> <span data-ttu-id="f898f-112">Varsayılan değer `Aes256` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="f898f-112">The default value is `Aes256`.</span></span> <span data-ttu-id="f898f-113">Bu öznitelik türünde <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="f898f-113">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span>|
|<span data-ttu-id="f898f-114">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="f898f-114">clientCredentialType</span></span>|<span data-ttu-id="f898f-115">MSMQ taşıma gönderilen iletiler için istemci kimlik doğrulaması yapılırken kullanılacak kimlik bilgisi türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="f898f-115">Specifies the type of credential to be used when performing client authentication for messages sent over the MSMQ transport.</span></span> <span data-ttu-id="f898f-116">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f898f-116">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f898f-117">-Yok: Bu, anonim istemcilerle etkileşime geçmek bir hizmet sağlar.</span><span class="sxs-lookup"><span data-stu-id="f898f-117">-   None: This allows the service to interact with anonymous clients.</span></span> <span data-ttu-id="f898f-118">Hizmet ya da istemci kimlik bilgileri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f898f-118">Neither the service nor the client requires a credential.</span></span><br /><span data-ttu-id="f898f-119">-   Windows: Bu, SOAP değişimleri, Windows kimlik bilgisi kimliği doğrulanmış bağlamı altında olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="f898f-119">-   Windows: This enables the SOAP exchanges to be under the authenticated context of a Windows credential.</span></span> <span data-ttu-id="f898f-120">Bu, her zaman Kerberos tabanlı kimlik doğrulaması gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="f898f-120">This always performs Kerberos-based authentication.</span></span><br /><span data-ttu-id="f898f-121">-UserName: Bu hizmet gerektirecek şekilde sağlar, istemci kimlik doğrulaması kullanarak bir kullanıcı adı kimlik bilgisi.</span><span class="sxs-lookup"><span data-stu-id="f898f-121">-   UserName: This enables the service to require that the client be authenticated using a UserName credential.</span></span> <span data-ttu-id="f898f-122">Kimlik bilgisi bu durumda kullanarak belirtilmesi gerekiyor `clientCredentials` davranışı **dikkatli olun:**  Windows Communication Foundation (WCF), bir parola özeti gönderme veya parola ve ileti güvenliği için bu anahtarları kullanarak anahtarlar türetme desteklemez.</span><span class="sxs-lookup"><span data-stu-id="f898f-122">The credential in this case needs to be specified using the `clientCredentials` behavior **Caution:**  Windows Communication Foundation (WCF) does not support sending a password digest or deriving keys using password and using such keys for message security.</span></span> <span data-ttu-id="f898f-123">Bu nedenle, WCF exchange kullanıcı adı kimlik bilgileri kullanılırken sağlandığını zorlar.</span><span class="sxs-lookup"><span data-stu-id="f898f-123">Therefore, WCF enforces that the exchange is secured when using UserName credentials.</span></span> <span data-ttu-id="f898f-124">Bu mod, hizmet sertifikası kullanarak istemci tarafı belirtilmesini gerektirir `clientCredential` davranışı ve `serviceCertificate`.</span><span class="sxs-lookup"><span data-stu-id="f898f-124">This mode requires that the service certificate be specified on the client side using `clientCredential` behavior and `serviceCertificate`.</span></span> <br /><br /> <span data-ttu-id="f898f-125">-Sertifikası: Bu hizmet gerektirecek şekilde sağlar, istemci kimlik doğrulaması kullanarak bir sertifika.</span><span class="sxs-lookup"><span data-stu-id="f898f-125">-   Certificate: This enables the service to require that the client be authenticated using a certificate.</span></span> <span data-ttu-id="f898f-126">İstemci kimlik bilgisi bu durumda kullanarak belirtilmesi gerekiyor `clientCredentials` davranışı.</span><span class="sxs-lookup"><span data-stu-id="f898f-126">The client credential in this case needs to be specified using the `clientCredentials` behavior.</span></span> <span data-ttu-id="f898f-127">Hizmet kimlik bilgisi bu durumda kullanarak belirtilmesi gerekiyor `clientCredentials` belirterek davranışı `serviceCertificate`.</span><span class="sxs-lookup"><span data-stu-id="f898f-127">The service credential in this case needs to be specified using the `clientCredentials` behavior by specifying the `serviceCertificate`.</span></span><br /><span data-ttu-id="f898f-128">-CardSpace: Bu hizmet gerektirecek şekilde sağlar, istemci kimlik doğrulaması kullanarak bir CardSpace.</span><span class="sxs-lookup"><span data-stu-id="f898f-128">-   CardSpace: This allows the service to require that the client be authenticated using a CardSpace.</span></span> <span data-ttu-id="f898f-129">`serviceCertificate` İçinde sağlanmalıdır `clientCredential` davranışı.</span><span class="sxs-lookup"><span data-stu-id="f898f-129">The `serviceCertificate` must be provisioned in the `clientCredential` behavior.</span></span><br /><br /> <span data-ttu-id="f898f-130">Varsayılan değer `Windows` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="f898f-130">The default value is `Windows`.</span></span> <span data-ttu-id="f898f-131">Bu öznitelik türünde <xref:System.ServiceModel.MessageCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="f898f-131">This attribute is of type <xref:System.ServiceModel.MessageCredentialType>.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="f898f-132">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f898f-132">Child Elements</span></span>

<span data-ttu-id="f898f-133">None</span><span class="sxs-lookup"><span data-stu-id="f898f-133">None</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f898f-134">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f898f-134">Parent Elements</span></span>

|<span data-ttu-id="f898f-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="f898f-135">Element</span></span>|<span data-ttu-id="f898f-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f898f-136">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f898f-137">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="f898f-137">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|<span data-ttu-id="f898f-138">Bir bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f898f-138">Defines the security settings for a binding.</span></span>|

## <a name="see-also"></a><span data-ttu-id="f898f-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f898f-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>
- <xref:System.ServiceModel.MessageSecurityOverMsmq>
- [<span data-ttu-id="f898f-140">WCF'de Kuyruklar</span><span class="sxs-lookup"><span data-stu-id="f898f-140">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="f898f-141">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="f898f-141">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="f898f-142">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="f898f-142">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="f898f-143">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f898f-143">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="f898f-144">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="f898f-144">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="f898f-145">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="f898f-145">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
