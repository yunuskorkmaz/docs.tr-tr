---
title: 'Nasıl yapılır: Meta Veri Uç Noktalarını Güvenli Hale Getirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9f71b6ae-737c-4382-8d89-0a7b1c7e182b
ms.openlocfilehash: 2746c608fb47b94446c5d7e10748ba185d555e7f
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202325"
---
# <a name="how-to-secure-metadata-endpoints"></a><span data-ttu-id="89a14-102">Nasıl yapılır: Meta Veri Uç Noktalarını Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="89a14-102">How to: Secure Metadata Endpoints</span></span>

<span data-ttu-id="89a14-103">Bir hizmetin meta verileri, uygulamanız hakkında kötü niyetli bir kullanıcının yararlanabilen gizli bilgiler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="89a14-103">Metadata for a service can contain sensitive information about your application that a malicious user can leverage.</span></span> <span data-ttu-id="89a14-104">Hizmetinizin tüketicileri, hizmetinize ilişkin meta verileri almak için güvenli bir mekanizma da gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="89a14-104">Consumers of your service may also require a secure mechanism for obtaining metadata about your service.</span></span> <span data-ttu-id="89a14-105">Bu nedenle, bazen güvenli bir uç nokta kullanarak meta verilerinizi yayımlamak gerekir.</span><span class="sxs-lookup"><span data-stu-id="89a14-105">Therefore, it is sometimes necessary to publish your metadata using a secure endpoint.</span></span>

<span data-ttu-id="89a14-106">Meta veri uç noktaları, uygulama uç noktalarını güvenli hale getirmek için Windows Communication Foundation (WCF) ' de tanımlanan standart güvenlik mekanizmaları kullanılarak genellikle güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="89a14-106">Metadata endpoints are generally secured using the standard security mechanisms defined in Windows Communication Foundation (WCF) for securing application endpoints.</span></span> <span data-ttu-id="89a14-107">Daha fazla bilgi için bkz. [Güvenliğe genel bakış](security-overview.md).</span><span class="sxs-lookup"><span data-stu-id="89a14-107">For more information, see [Security Overview](security-overview.md).</span></span>

<span data-ttu-id="89a14-108">Bu konu, bir Güvenli Yuva Katmanı (SSL) sertifikasıyla veya diğer bir deyişle, bir HTTPS uç noktası tarafından güvenliği sağlanmış bir uç nokta oluşturma adımlarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="89a14-108">This topic walks through the steps to create an endpoint secured by a Secure Sockets Layer (SSL) certificate or, in other words, an HTTPS endpoint.</span></span>

### <a name="to-create-a-secure-https-get-metadata-endpoint-in-code"></a><span data-ttu-id="89a14-109">Kodda güvenli bir HTTPS GET meta veri uç noktası oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="89a14-109">To create a secure HTTPS GET metadata endpoint in code</span></span>

1. <span data-ttu-id="89a14-110">Uygun bir X. 509.440 sertifikası ile bir bağlantı noktası yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="89a14-110">Configure a port with an appropriate X.509 certificate.</span></span> <span data-ttu-id="89a14-111">Sertifika, güvenilir bir yetkilinizden gelmiş olmalı ve "hizmet yetkilendirmesi" kullanımı amaçlanan bir şekilde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="89a14-111">The certificate must come from a trusted authority, and it must have an intended use of "Service Authorization."</span></span> <span data-ttu-id="89a14-112">Sertifikayı bağlantı noktasına iliştirmek için HttpCfg. exe aracını kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="89a14-112">You must use the HttpCfg.exe tool to attach the certificate to the port.</span></span> <span data-ttu-id="89a14-113">Bkz. [nasıl yapılır: SSL sertifikası Ile bağlantı noktası yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="89a14-113">See [How to: Configure a Port with an SSL Certificate](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="89a14-114">Sertifikanın konusu veya etki alanı adı sistemi (DNS) bilgisayarın adıyla eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="89a14-114">The subject of the certificate or its Domain Name System (DNS) must match the name of the computer.</span></span> <span data-ttu-id="89a14-115">Bu, HTTPS mekanizmanın gerçekleştirdiği ilk adımlardan biri, sertifikanın çağrıldığı adresle aynı Tekdüzen Kaynak tanımlayıcısına (URI) verildiğine emin olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="89a14-115">This is essential because one of the first steps the HTTPS mechanism performs is to check that the certificate is issued to the same Uniform Resource Identifier (URI) as the address upon which it is invoked.</span></span>

2. <span data-ttu-id="89a14-116">Sınıfının yeni bir örneğini oluşturun <xref:System.ServiceModel.Description.ServiceMetadataBehavior> .</span><span class="sxs-lookup"><span data-stu-id="89a14-116">Create a new instance of the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class.</span></span>

3. <span data-ttu-id="89a14-117"><xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> <xref:System.ServiceModel.Description.ServiceMetadataBehavior> Sınıfının özelliğini olarak ayarlayın `true` .</span><span class="sxs-lookup"><span data-stu-id="89a14-117">Set the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> property of the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class to `true`.</span></span>

4. <span data-ttu-id="89a14-118"><xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>Özelliği uygun BIR URL olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="89a14-118">Set the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> property to an appropriate URL.</span></span> <span data-ttu-id="89a14-119">Mutlak bir adres belirtirseniz URL 'nin şemayla başlaması gerektiğini unutmayın `https://` .</span><span class="sxs-lookup"><span data-stu-id="89a14-119">Note that if you specify an absolute address, the URL must begin with the scheme `https://`.</span></span> <span data-ttu-id="89a14-120">Göreli bir adres belirtirseniz, hizmet ana bilgisayarınız için bir HTTPS temel adresi sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="89a14-120">If you specify a relative address, you must supply an HTTPS base address for your service host.</span></span> <span data-ttu-id="89a14-121">Bu özellik ayarlanmamışsa, varsayılan adres "" veya doğrudan hizmetin HTTPS taban adresidir.</span><span class="sxs-lookup"><span data-stu-id="89a14-121">If this property is not set, the default address is "", or directly at the HTTPS base address for the service.</span></span>

5. <span data-ttu-id="89a14-122"><xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A>Aşağıdaki kodda gösterildiği gibi, örneği, sınıfının özelliğinin döndürdüğü davranışlar koleksiyonuna ekleyin <xref:System.ServiceModel.Description.ServiceDescription> .</span><span class="sxs-lookup"><span data-stu-id="89a14-122">Add the instance to the behaviors collection that the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> property of the <xref:System.ServiceModel.Description.ServiceDescription> class returns, as shown in the following code.</span></span>

    [!code-csharp[c_HowToSecureEndpoint#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#1)]
    [!code-vb[c_HowToSecureEndpoint#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#1)]

### <a name="to-create-a-secure-https-get-metadata-endpoint-in-configuration"></a><span data-ttu-id="89a14-123">Yapılandırmada güvenli bir HTTPS Al meta veri uç noktası oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="89a14-123">To create a secure HTTPS GET metadata endpoint in configuration</span></span>

1. <span data-ttu-id="89a14-124">[\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) Hizmetiniz için yapılandırma dosyasının öğesine bir öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="89a14-124">Add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element to the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element of the configuration file for your service.</span></span>

2. <span data-ttu-id="89a14-125">Öğeye bir [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) öğe ekleyin [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) .</span><span class="sxs-lookup"><span data-stu-id="89a14-125">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) element to the [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span></span>

3. <span data-ttu-id="89a14-126">Öğeye bir [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) öğe ekleyin `<serviceBehaviors>` .</span><span class="sxs-lookup"><span data-stu-id="89a14-126">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element to the `<serviceBehaviors>` element.</span></span>

4. <span data-ttu-id="89a14-127">`name` `<behavior>` Öğesinin özniteliğini uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="89a14-127">Set the `name` attribute of the `<behavior>` element to an appropriate value.</span></span> <span data-ttu-id="89a14-128">`name`Özniteliği gereklidir.</span><span class="sxs-lookup"><span data-stu-id="89a14-128">The `name` attribute is required.</span></span> <span data-ttu-id="89a14-129">Aşağıdaki örnek, değerini kullanır `mySvcBehavior` .</span><span class="sxs-lookup"><span data-stu-id="89a14-129">The example below uses the value `mySvcBehavior`.</span></span>

5. <span data-ttu-id="89a14-130">Öğesi öğesine ekleyin [\<serviceMetadata>](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) `<behavior>` .</span><span class="sxs-lookup"><span data-stu-id="89a14-130">Add a [\<serviceMetadata>](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) to the `<behavior>` element.</span></span>

6. <span data-ttu-id="89a14-131">`httpsGetEnabled` `<serviceMetadata>` Öğesinin özniteliğini olarak ayarlayın `true` .</span><span class="sxs-lookup"><span data-stu-id="89a14-131">Set the `httpsGetEnabled` attribute of the `<serviceMetadata>` element to `true`.</span></span>

7. <span data-ttu-id="89a14-132">`httpsGetUrl` `<serviceMetadata>` Öğesinin özniteliğini uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="89a14-132">Set the `httpsGetUrl` attribute of the `<serviceMetadata>` element to an appropriate value.</span></span> <span data-ttu-id="89a14-133">Mutlak bir adres belirtirseniz URL 'nin şemayla başlaması gerektiğini unutmayın `https://` .</span><span class="sxs-lookup"><span data-stu-id="89a14-133">Note that if you specify an absolute address, the URL must begin with the scheme `https://`.</span></span> <span data-ttu-id="89a14-134">Göreli bir adres belirtirseniz, hizmet ana bilgisayarınız için bir HTTPS temel adresi sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="89a14-134">If you specify a relative address, you must supply an HTTPS base address for your service host.</span></span> <span data-ttu-id="89a14-135">Bu özellik ayarlanmamışsa, varsayılan adres "" veya doğrudan hizmetin HTTPS taban adresidir.</span><span class="sxs-lookup"><span data-stu-id="89a14-135">If this property is not set, the default address is "", or directly at the HTTPS base address for the service.</span></span>

8. <span data-ttu-id="89a14-136">Davranışını bir hizmetle birlikte kullanmak için, `behaviorConfiguration` [\<service>](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) öğesinin özniteliğini Behavior öğesinin Name özniteliğinin değeri olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="89a14-136">To use the behavior with a service, set the `behaviorConfiguration` attribute of the [\<service>](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) element to the value of the name attribute of the behavior element.</span></span> <span data-ttu-id="89a14-137">Aşağıdaki yapılandırma kodu, bir örnek gösterir.</span><span class="sxs-lookup"><span data-stu-id="89a14-137">The following configuration code shows a complete example.</span></span>

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
     <system.serviceModel>
      <behaviors>
       <serviceBehaviors>
        <behavior name="mySvcBehavior">
         <serviceMetadata httpsGetEnabled="true"
              httpsGetUrl="https://localhost:8036/calcMetadata" />
        </behavior>
       </serviceBehaviors>
      </behaviors>
     <services>
      <service behaviorConfiguration="mySvcBehavior"
            name="Microsoft.Security.Samples.Calculator">
       <endpoint address="http://localhost:8037/ServiceModelSamples/calculator"
       binding="wsHttpBinding" bindingConfiguration=""
       contract="Microsoft.Security.Samples.ICalculator" />
      </service>
     </services>
    </system.serviceModel>
    </configuration>
    ```

## <a name="example"></a><span data-ttu-id="89a14-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="89a14-138">Example</span></span>

<span data-ttu-id="89a14-139">Aşağıdaki örnek bir sınıfın örneğini oluşturur <xref:System.ServiceModel.ServiceHost> ve bir uç nokta ekler.</span><span class="sxs-lookup"><span data-stu-id="89a14-139">The following example creates an instance of a <xref:System.ServiceModel.ServiceHost> class and adds an endpoint.</span></span> <span data-ttu-id="89a14-140">Daha sonra kod, sınıfının bir örneğini oluşturur <xref:System.ServiceModel.Description.ServiceMetadataBehavior> ve güvenli bir meta veri değişim noktası oluşturmak için özellikleri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="89a14-140">The code then creates an instance of the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class and sets the properties to create a secure metadata exchange point.</span></span>

[!code-csharp[c_HowToSecureEndpoint#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#0)]
[!code-vb[c_HowToSecureEndpoint#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#0)]

## <a name="compiling-the-code"></a><span data-ttu-id="89a14-141">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="89a14-141">Compiling the Code</span></span>

<span data-ttu-id="89a14-142">Kod örneği aşağıdaki ad alanlarını kullanır:</span><span class="sxs-lookup"><span data-stu-id="89a14-142">The code example uses the following namespaces:</span></span>

- <xref:System.ServiceModel?displayProperty=nameWithType>

- <xref:System.ServiceModel.Description?displayProperty=nameWithType>

## <a name="see-also"></a><span data-ttu-id="89a14-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="89a14-143">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>
- [<span data-ttu-id="89a14-144">Nasıl Yapılır: SSL Sertifikası ile Bir Bağlantı Noktasını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="89a14-144">How to: Configure a Port with an SSL Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
- [<span data-ttu-id="89a14-145">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="89a14-145">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="89a14-146">Meta Veriler Hakkında Güvenlik Konuları</span><span class="sxs-lookup"><span data-stu-id="89a14-146">Security Considerations with Metadata</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)
- [<span data-ttu-id="89a14-147">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="89a14-147">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
