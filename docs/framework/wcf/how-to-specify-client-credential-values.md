---
title: 'Nasıl yapılır: İstemci Kimlik Bilgileri Değerlerini Belirtme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 82293d7f-471a-4549-8f19-0be890e7b074
ms.openlocfilehash: 2417c2dd16224d6cbf00d3f1f4a8958420830b6c
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319856"
---
# <a name="how-to-specify-client-credential-values"></a><span data-ttu-id="1ea8a-102">Nasıl yapılır: İstemci Kimlik Bilgileri Değerlerini Belirtme</span><span class="sxs-lookup"><span data-stu-id="1ea8a-102">How to: Specify Client Credential Values</span></span>

<span data-ttu-id="1ea8a-103">Hizmet, Windows Communication Foundation (WCF) kullanarak, bir istemcinin hizmette nasıl kimlik doğrulaması yapıldığını belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="1ea8a-103">Using Windows Communication Foundation (WCF), the service can specify how a client is authenticated to the service.</span></span> <span data-ttu-id="1ea8a-104">Örneğin, bir hizmet, istemcinin kimliğinin bir sertifikayla doğrulanmasını sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="1ea8a-104">For example, a service can stipulate that the client be authenticated with a certificate.</span></span>

## <a name="to-determine-the-client-credential-type"></a><span data-ttu-id="1ea8a-105">İstemci kimlik bilgisi türünü belirleme</span><span class="sxs-lookup"><span data-stu-id="1ea8a-105">To determine the client credential type</span></span>

1. <span data-ttu-id="1ea8a-106">Hizmetin meta veri uç noktasından meta verileri alın.</span><span class="sxs-lookup"><span data-stu-id="1ea8a-106">Retrieve metadata from the service's metadata endpoint.</span></span> <span data-ttu-id="1ea8a-107">Meta veriler genellikle iki dosyadan oluşur: seçtiğiniz programlama dilinde istemci kodu (varsayılan olarak görseldir C#) ve bir XML yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="1ea8a-107">The metadata typically consists of two files: the client code in the programming language of your choice (the default is Visual C#), and an XML configuration file.</span></span> <span data-ttu-id="1ea8a-108">Meta verileri almanın bir yolu, istemci kodunu ve istemci yapılandırmasını döndürmek için Svcutil. exe aracını kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="1ea8a-108">One way to retrieve metadata is to use the Svcutil.exe tool to return the client code and client configuration.</span></span> <span data-ttu-id="1ea8a-109">Daha fazla bilgi için bkz. [meta verileri](./feature-details/retrieving-metadata.md) ve [ServiceModel meta verilerini alma yardımcı programı Aracı (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="1ea8a-109">For more information, see [Retrieving Metadata](./feature-details/retrieving-metadata.md) and [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>

2. <span data-ttu-id="1ea8a-110">XML yapılandırma dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="1ea8a-110">Open the XML configuration file.</span></span> <span data-ttu-id="1ea8a-111">Svcutil. exe aracını kullanırsanız, dosyanın varsayılan adı output. config olur.</span><span class="sxs-lookup"><span data-stu-id="1ea8a-111">If you use the Svcutil.exe tool, the default name of the file is Output.config.</span></span>

3. <span data-ttu-id="1ea8a-112">**Mode** özniteliği ( **\<güvenlik modu =** `MessageOrTransport` **>** ) olan **\<security >** öğesini bulur (`MessageOrTransport` ' in güvenlik modlarından birine ayarlandığı).</span><span class="sxs-lookup"><span data-stu-id="1ea8a-112">Find the **\<security>** element with the **mode** attribute (**\<security mode =**`MessageOrTransport`**>** where `MessageOrTransport` is set to one of the security modes.</span></span>

4. <span data-ttu-id="1ea8a-113">Mode değeriyle eşleşen alt öğe bulun.</span><span class="sxs-lookup"><span data-stu-id="1ea8a-113">Find the child element that matches the mode value.</span></span> <span data-ttu-id="1ea8a-114">Örneğin, mod **ileti**olarak ayarlandıysa, **\<güvenlik >** öğesinde içerilen **\<message >** öğesini bulun.</span><span class="sxs-lookup"><span data-stu-id="1ea8a-114">For example, if the mode is set to **Message**, find the **\<message>** element contained in the **\<security>** element.</span></span>

5. <span data-ttu-id="1ea8a-115">**ClientCredentialType** özniteliğine atanan değere göz atar.</span><span class="sxs-lookup"><span data-stu-id="1ea8a-115">Note the value assigned to the **clientCredentialType** attribute.</span></span> <span data-ttu-id="1ea8a-116">Gerçek değer, hangi modun kullanıldığı, taşımanın veya iletinin kullanıldığına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="1ea8a-116">The actual value depends on which mode is used, transport or message.</span></span>

<span data-ttu-id="1ea8a-117">Aşağıdaki XML kodu, ileti güvenliği kullanan bir istemcinin yapılandırmasını gösterir ve istemcinin kimliğini doğrulamak için bir sertifika gerektirir.</span><span class="sxs-lookup"><span data-stu-id="1ea8a-117">The following XML code shows configuration for a client using message security and requiring a certificate to authenticate the client.</span></span>

```xml
<security mode="Message">
    <transport clientCredentialType="Windows" proxyCredentialType="None"
        realm="" />
     <message clientCredentialType="Certificate" negotiateServiceCredential="true"
    algorithmSuite="Default" establishSecurityContext="true" />
</security>
```

## <a name="example-tcp-transport-mode-with-certificate-as-client-credential"></a><span data-ttu-id="1ea8a-118">Örnek: Istemci kimlik bilgileri olarak sertifika ile TCP aktarım modu</span><span class="sxs-lookup"><span data-stu-id="1ea8a-118">Example: TCP Transport Mode with Certificate as Client Credential</span></span>

<span data-ttu-id="1ea8a-119">Bu örnek, güvenlik modunu taşıma moduna ayarlar ve istemci kimlik bilgisi değerini bir X. 509.952 sertifikası olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1ea8a-119">This example sets the security mode to Transport mode and sets the client credential value to an X.509 certificate.</span></span> <span data-ttu-id="1ea8a-120">Aşağıdaki yordamlarda, istemcide istemci kimlik bilgileri değerinin kod ve yapılandırmada nasıl ayarlanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1ea8a-120">The following procedures demonstrate how to set the client credential value on the client in code and configuration.</span></span> <span data-ttu-id="1ea8a-121">Bu, hizmetten meta verileri (kod ve yapılandırma) döndürmek için [ServiceModel meta veri yardımcı programı aracını (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) kullandığınızı varsayar.</span><span class="sxs-lookup"><span data-stu-id="1ea8a-121">This assumes that you have used the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to return the metadata (code and configuration) from the service.</span></span> <span data-ttu-id="1ea8a-122">Daha fazla bilgi için bkz. [nasıl yapılır: Istemci oluşturma](how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="1ea8a-122">For more information, see [How to: Create a Client](how-to-create-a-wcf-client.md).</span></span>

### <a name="to-specify-the-client-credential-value-on-the-client-in-code"></a><span data-ttu-id="1ea8a-123">İstemcide istemci kimlik bilgileri değerini belirtmek için</span><span class="sxs-lookup"><span data-stu-id="1ea8a-123">To specify the client credential value on the client in code</span></span>

1. <span data-ttu-id="1ea8a-124">Hizmetten kod ve yapılandırma oluşturmak için [ServiceModel meta veri yardımcı programı aracını (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="1ea8a-124">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to generate code and configuration from the service.</span></span>

2. <span data-ttu-id="1ea8a-125">Oluşturulan kodu kullanarak WCF istemcisinin bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1ea8a-125">Create an instance of the WCF client using the generated code.</span></span>

3. <span data-ttu-id="1ea8a-126">İstemci sınıfında, <xref:System.ServiceModel.ClientBase%601> sınıfının <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> özelliğini uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1ea8a-126">On the client class, set the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the <xref:System.ServiceModel.ClientBase%601> class to an appropriate value.</span></span> <span data-ttu-id="1ea8a-127">Bu örnek, <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> sınıfının <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> yöntemini kullanarak özelliği bir X. 509.440 sertifikası olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1ea8a-127">This example sets the property to an X.509 certificate using the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> class.</span></span>

     [!code-csharp[c_TcpService#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#4)]
     [!code-vb[c_TcpService#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#4)]

     <span data-ttu-id="1ea8a-128">@No__t-0 sınıfının Numaralandırmalardan herhangi birini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1ea8a-128">You can use any of the enumerations of the <xref:System.Security.Cryptography.X509Certificates.X509FindType> class.</span></span> <span data-ttu-id="1ea8a-129">Konu adı, sertifikanın değişmesi durumunda (bir sona erme tarihi nedeniyle) burada kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1ea8a-129">The subject name is used here in case the certificate is changed (due to an expiration date).</span></span> <span data-ttu-id="1ea8a-130">Konu adının kullanılması, altyapının sertifikayı tekrar bulmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="1ea8a-130">Using the subject name enables the infrastructure to find the certificate again.</span></span>

### <a name="to-specify-the-client-credential-value-on-the-client-in-configuration"></a><span data-ttu-id="1ea8a-131">Yapılandırmada istemci kimlik bilgileri değerini belirtmek için</span><span class="sxs-lookup"><span data-stu-id="1ea8a-131">To specify the client credential value on the client in configuration</span></span>

1. <span data-ttu-id="1ea8a-132">[@No__t-3behavior >](../configure-apps/file-schema/wcf/behaviors.md) öğesine [\<behavior >](../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1ea8a-132">Add a [\<behavior>](../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element to the [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md) element.</span></span>

2. <span data-ttu-id="1ea8a-133">[@No__t-3davranışlarına >](../configure-apps/file-schema/wcf/behaviors.md) öğesine [\<clientcredentials >](../configure-apps/file-schema/wcf/clientcredentials.md) öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1ea8a-133">Add a [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) element to the [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md) element.</span></span> <span data-ttu-id="1ea8a-134">Gerekli `name` özniteliğini uygun bir değere ayarladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="1ea8a-134">Be sure to set the required `name` attribute to an appropriate value.</span></span>

3. <span data-ttu-id="1ea8a-135">[@No__t-3clientCredentials >](../configure-apps/file-schema/wcf/clientcredentials.md) öğesine [\<clientcertificate >](../configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md) öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1ea8a-135">Add a [\<clientCertificate>](../configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md) element to the [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) element.</span></span>

4. <span data-ttu-id="1ea8a-136">Aşağıdaki öznitelikleri uygun değerlere ayarlayın: `storeLocation`, `storeName`, `x509FindType` ve `findValue`, aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="1ea8a-136">Set the following attributes to appropriate values: `storeLocation`, `storeName`, `x509FindType`, and `findValue`, as shown in the following code.</span></span> <span data-ttu-id="1ea8a-137">Sertifikalar hakkında daha fazla bilgi için bkz. [sertifikalarla çalışma](./feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="1ea8a-137">For more information about certificates, see [Working with Certificates](./feature-details/working-with-certificates.md).</span></span>

    ```xml
    <behaviors>
       <endpointBehaviors>
          <behavior name="endpointCredentialBehavior">
            <clientCredentials>
              <clientCertificate findValue="Contoso.com"
                                 storeLocation="LocalMachine"
                                 storeName="TrustedPeople"
                                 x509FindType="FindBySubjectName" />
            </clientCredentials>
          </behavior>
       </endpointBehaviors>
    </behaviors>
    ```

5. <span data-ttu-id="1ea8a-138">İstemcisini yapılandırırken, aşağıdaki kodda gösterildiği gibi `<endpoint>` öğesinin `behaviorConfiguration` özniteliğini ayarlayarak davranışı belirtin.</span><span class="sxs-lookup"><span data-stu-id="1ea8a-138">When configuring the client, specify the behavior by setting the `behaviorConfiguration` attribute of the `<endpoint>` element, as shown in the following code.</span></span> <span data-ttu-id="1ea8a-139">Endpoint öğesi [\<client >](../configure-apps/file-schema/wcf/client.md) öğesinin bir alt öğesidir.</span><span class="sxs-lookup"><span data-stu-id="1ea8a-139">The endpoint element is a child of the [\<client>](../configure-apps/file-schema/wcf/client.md) element.</span></span> <span data-ttu-id="1ea8a-140">Ayrıca, `bindingConfiguration` özniteliğini istemci için bağlamaya ayarlayarak bağlama yapılandırmasının adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="1ea8a-140">Also, specify the name of the binding configuration by setting the `bindingConfiguration` attribute to the binding for the client.</span></span> <span data-ttu-id="1ea8a-141">Oluşturulmuş bir yapılandırma dosyası kullanıyorsanız, bağlamanın adı otomatik olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1ea8a-141">If you are using a generated configuration file, the binding's name is automatically generated.</span></span> <span data-ttu-id="1ea8a-142">Bu örnekte ad `"tcpBindingWithCredential"` ' dır.</span><span class="sxs-lookup"><span data-stu-id="1ea8a-142">In this example, the name is `"tcpBindingWithCredential"`.</span></span>

    ```xml
    <client>
      <endpoint name =""
                address="net.tcp://contoso.com:8036/aloha"
                binding="netTcpBinding"
                bindingConfiguration="tcpBindingWithCredential"
                behaviorConfiguration="endpointCredentialBehavior" />
    </client>
    ```

## <a name="see-also"></a><span data-ttu-id="1ea8a-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ea8a-143">See also</span></span>

- <xref:System.ServiceModel.NetTcpBinding>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>
- <xref:System.ServiceModel.ClientBase%601>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>
- [<span data-ttu-id="1ea8a-144">WCF Güvenliğini Programlama</span><span class="sxs-lookup"><span data-stu-id="1ea8a-144">Programming WCF Security</span></span>](./feature-details/programming-wcf-security.md)
- [<span data-ttu-id="1ea8a-145">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="1ea8a-145">Selecting a Credential Type</span></span>](./feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="1ea8a-146">ServiceModel Meta Veri Yardımcı Programı Aracı (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="1ea8a-146">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="1ea8a-147">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="1ea8a-147">Working with Certificates</span></span>](./feature-details/working-with-certificates.md)
- [<span data-ttu-id="1ea8a-148">Nasıl yapılır: İstemci Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1ea8a-148">How to: Create a Client</span></span>](how-to-create-a-wcf-client.md)
- [<span data-ttu-id="1ea8a-149">\<netTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="1ea8a-149">\<netTcpBinding></span></span>](../configure-apps/file-schema/wcf/nettcpbinding.md)
- [<span data-ttu-id="1ea8a-150">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="1ea8a-150">\<security></span></span>](../configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
- [<span data-ttu-id="1ea8a-151">\<ileti ></span><span class="sxs-lookup"><span data-stu-id="1ea8a-151">\<message></span></span>](../configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)
- [<span data-ttu-id="1ea8a-152">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="1ea8a-152">\<behavior></span></span>](../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)
- [<span data-ttu-id="1ea8a-153">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="1ea8a-153">\<behaviors></span></span>](../configure-apps/file-schema/wcf/behaviors.md)
- [<span data-ttu-id="1ea8a-154">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="1ea8a-154">\<clientCertificate></span></span>](../configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)
- [<span data-ttu-id="1ea8a-155">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="1ea8a-155">\<clientCredentials></span></span>](../configure-apps/file-schema/wcf/clientcredentials.md)
