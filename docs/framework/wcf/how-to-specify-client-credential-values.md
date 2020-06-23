---
title: 'Nasıl yapılır: İstemci Kimlik Bilgileri Değerlerini Belirtme'
description: Bir WCF hizmetinin istemcinin bu hizmette nasıl kimlik doğrulaması yapıldığını nasıl belirtmesini istediğinizi öğrenin. Bu örnek bir X. 509.440 sertifikası ve aktarım modunu belirtir.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 82293d7f-471a-4549-8f19-0be890e7b074
ms.openlocfilehash: 75a21a7dc083282f6b2fe839167ff1b2eddfb373
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244458"
---
# <a name="how-to-specify-client-credential-values"></a><span data-ttu-id="fab16-104">Nasıl yapılır: İstemci Kimlik Bilgileri Değerlerini Belirtme</span><span class="sxs-lookup"><span data-stu-id="fab16-104">How to: Specify Client Credential Values</span></span>

<span data-ttu-id="fab16-105">Hizmet, Windows Communication Foundation (WCF) kullanarak, bir istemcinin hizmette nasıl kimlik doğrulaması yapıldığını belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="fab16-105">Using Windows Communication Foundation (WCF), the service can specify how a client is authenticated to the service.</span></span> <span data-ttu-id="fab16-106">Örneğin, bir hizmet, istemcinin kimliğinin bir sertifikayla doğrulanmasını sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="fab16-106">For example, a service can stipulate that the client be authenticated with a certificate.</span></span>

## <a name="to-determine-the-client-credential-type"></a><span data-ttu-id="fab16-107">İstemci kimlik bilgisi türünü belirleme</span><span class="sxs-lookup"><span data-stu-id="fab16-107">To determine the client credential type</span></span>

1. <span data-ttu-id="fab16-108">Hizmetin meta veri uç noktasından meta verileri alın.</span><span class="sxs-lookup"><span data-stu-id="fab16-108">Retrieve metadata from the service's metadata endpoint.</span></span> <span data-ttu-id="fab16-109">Meta veriler genellikle iki dosyadan oluşur: seçtiğiniz programlama dilinde istemci kodu (varsayılan olarak Visual C#) ve bir XML yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="fab16-109">The metadata typically consists of two files: the client code in the programming language of your choice (the default is Visual C#), and an XML configuration file.</span></span> <span data-ttu-id="fab16-110">Meta verileri almanın bir yolu, istemci kodunu ve istemci yapılandırmasını döndürmek için Svcutil.exe aracını kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="fab16-110">One way to retrieve metadata is to use the Svcutil.exe tool to return the client code and client configuration.</span></span> <span data-ttu-id="fab16-111">Daha fazla bilgi için bkz. [meta verileri](./feature-details/retrieving-metadata.md) ve [ServiceModel meta verilerini alma yardımcı programı Aracı (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="fab16-111">For more information, see [Retrieving Metadata](./feature-details/retrieving-metadata.md) and [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>

2. <span data-ttu-id="fab16-112">XML yapılandırma dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="fab16-112">Open the XML configuration file.</span></span> <span data-ttu-id="fab16-113">Svcutil.exe aracını kullanırsanız, dosyanın varsayılan adı Output.config.</span><span class="sxs-lookup"><span data-stu-id="fab16-113">If you use the Svcutil.exe tool, the default name of the file is Output.config.</span></span>

3. <span data-ttu-id="fab16-114">**\<security>** **Mode** özniteliğine sahip öğeyi bulun ( **\<security mode =**`MessageOrTransport`**>** burada `MessageOrTransport` güvenlik modlarından birine ayarlanır).</span><span class="sxs-lookup"><span data-stu-id="fab16-114">Find the **\<security>** element with the **mode** attribute (**\<security mode =**`MessageOrTransport`**>** where `MessageOrTransport` is set to one of the security modes.</span></span>

4. <span data-ttu-id="fab16-115">Mode değeriyle eşleşen alt öğe bulun.</span><span class="sxs-lookup"><span data-stu-id="fab16-115">Find the child element that matches the mode value.</span></span> <span data-ttu-id="fab16-116">Örneğin, mod **ileti**olarak ayarlandıysa, **\<message>** öğesinde içerilen öğeyi bulun **\<security>** .</span><span class="sxs-lookup"><span data-stu-id="fab16-116">For example, if the mode is set to **Message**, find the **\<message>** element contained in the **\<security>** element.</span></span>

5. <span data-ttu-id="fab16-117">**ClientCredentialType** özniteliğine atanan değere göz atar.</span><span class="sxs-lookup"><span data-stu-id="fab16-117">Note the value assigned to the **clientCredentialType** attribute.</span></span> <span data-ttu-id="fab16-118">Gerçek değer, hangi modun kullanıldığı, taşımanın veya iletinin kullanıldığına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="fab16-118">The actual value depends on which mode is used, transport or message.</span></span>

<span data-ttu-id="fab16-119">Aşağıdaki XML kodu, ileti güvenliği kullanan bir istemcinin yapılandırmasını gösterir ve istemcinin kimliğini doğrulamak için bir sertifika gerektirir.</span><span class="sxs-lookup"><span data-stu-id="fab16-119">The following XML code shows configuration for a client using message security and requiring a certificate to authenticate the client.</span></span>

```xml
<security mode="Message">
    <transport clientCredentialType="Windows" proxyCredentialType="None"
        realm="" />
     <message clientCredentialType="Certificate" negotiateServiceCredential="true"
    algorithmSuite="Default" establishSecurityContext="true" />
</security>
```

## <a name="example-tcp-transport-mode-with-certificate-as-client-credential"></a><span data-ttu-id="fab16-120">Örnek: Istemci kimlik bilgileri olarak sertifika ile TCP aktarım modu</span><span class="sxs-lookup"><span data-stu-id="fab16-120">Example: TCP Transport Mode with Certificate as Client Credential</span></span>

<span data-ttu-id="fab16-121">Bu örnek, güvenlik modunu taşıma moduna ayarlar ve istemci kimlik bilgisi değerini bir X. 509.952 sertifikası olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="fab16-121">This example sets the security mode to Transport mode and sets the client credential value to an X.509 certificate.</span></span> <span data-ttu-id="fab16-122">Aşağıdaki yordamlarda, istemcide istemci kimlik bilgileri değerinin kod ve yapılandırmada nasıl ayarlanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fab16-122">The following procedures demonstrate how to set the client credential value on the client in code and configuration.</span></span> <span data-ttu-id="fab16-123">Bu, hizmetten meta verileri (kod ve yapılandırma) döndürmek için [ServiceModel meta veri yardımcı programı aracını (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) kullandığınızı varsayar.</span><span class="sxs-lookup"><span data-stu-id="fab16-123">This assumes that you have used the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to return the metadata (code and configuration) from the service.</span></span> <span data-ttu-id="fab16-124">Daha fazla bilgi için bkz. [nasıl yapılır: Istemci oluşturma](how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="fab16-124">For more information, see [How to: Create a Client](how-to-create-a-wcf-client.md).</span></span>

### <a name="to-specify-the-client-credential-value-on-the-client-in-code"></a><span data-ttu-id="fab16-125">İstemcide istemci kimlik bilgileri değerini belirtmek için</span><span class="sxs-lookup"><span data-stu-id="fab16-125">To specify the client credential value on the client in code</span></span>

1. <span data-ttu-id="fab16-126">Hizmetten kod ve yapılandırma oluşturmak için [ServiceModel meta veri yardımcı programı aracını (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="fab16-126">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to generate code and configuration from the service.</span></span>

2. <span data-ttu-id="fab16-127">Oluşturulan kodu kullanarak WCF istemcisinin bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fab16-127">Create an instance of the WCF client using the generated code.</span></span>

3. <span data-ttu-id="fab16-128">İstemci sınıfında, <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> <xref:System.ServiceModel.ClientBase%601> sınıfının özelliğini uygun bir değer olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="fab16-128">On the client class, set the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the <xref:System.ServiceModel.ClientBase%601> class to an appropriate value.</span></span> <span data-ttu-id="fab16-129">Bu örnek, sınıfının yöntemini kullanarak özelliği bir X. 509.440 sertifikası olarak ayarlar <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> .</span><span class="sxs-lookup"><span data-stu-id="fab16-129">This example sets the property to an X.509 certificate using the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> class.</span></span>

     [!code-csharp[c_TcpService#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#4)]
     [!code-vb[c_TcpService#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#4)]

     <span data-ttu-id="fab16-130">Sınıfın Numaralandırmalardan herhangi birini kullanabilirsiniz <xref:System.Security.Cryptography.X509Certificates.X509FindType> .</span><span class="sxs-lookup"><span data-stu-id="fab16-130">You can use any of the enumerations of the <xref:System.Security.Cryptography.X509Certificates.X509FindType> class.</span></span> <span data-ttu-id="fab16-131">Konu adı, sertifikanın değişmesi durumunda (bir sona erme tarihi nedeniyle) burada kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fab16-131">The subject name is used here in case the certificate is changed (due to an expiration date).</span></span> <span data-ttu-id="fab16-132">Konu adının kullanılması, altyapının sertifikayı tekrar bulmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="fab16-132">Using the subject name enables the infrastructure to find the certificate again.</span></span>

### <a name="to-specify-the-client-credential-value-on-the-client-in-configuration"></a><span data-ttu-id="fab16-133">Yapılandırmada istemci kimlik bilgileri değerini belirtmek için</span><span class="sxs-lookup"><span data-stu-id="fab16-133">To specify the client credential value on the client in configuration</span></span>

1. <span data-ttu-id="fab16-134">Öğeye bir [\<behavior>](../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) öğe ekleyin [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md) .</span><span class="sxs-lookup"><span data-stu-id="fab16-134">Add a [\<behavior>](../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element to the [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md) element.</span></span>

2. <span data-ttu-id="fab16-135">Öğeye bir [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) öğe ekleyin [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md) .</span><span class="sxs-lookup"><span data-stu-id="fab16-135">Add a [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) element to the [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md) element.</span></span> <span data-ttu-id="fab16-136">Gerekli `name` özniteliği uygun bir değere ayarladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="fab16-136">Be sure to set the required `name` attribute to an appropriate value.</span></span>

3. <span data-ttu-id="fab16-137">Öğeye bir [\<clientCertificate>](../configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md) öğe ekleyin [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) .</span><span class="sxs-lookup"><span data-stu-id="fab16-137">Add a [\<clientCertificate>](../configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md) element to the [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) element.</span></span>

4. <span data-ttu-id="fab16-138">Aşağıdaki öznitelikleri uygun değerlere ayarlayın:,, `storeLocation` `storeName` `x509FindType` , ve `findValue` , aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="fab16-138">Set the following attributes to appropriate values: `storeLocation`, `storeName`, `x509FindType`, and `findValue`, as shown in the following code.</span></span> <span data-ttu-id="fab16-139">Sertifikalar hakkında daha fazla bilgi için bkz. [sertifikalarla çalışma](./feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="fab16-139">For more information about certificates, see [Working with Certificates](./feature-details/working-with-certificates.md).</span></span>

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

5. <span data-ttu-id="fab16-140">İstemcisini yapılandırırken, `behaviorConfiguration` `<endpoint>` aşağıdaki kodda gösterildiği gibi, öğesinin özniteliğini ayarlayarak davranışı belirtin.</span><span class="sxs-lookup"><span data-stu-id="fab16-140">When configuring the client, specify the behavior by setting the `behaviorConfiguration` attribute of the `<endpoint>` element, as shown in the following code.</span></span> <span data-ttu-id="fab16-141">Endpoint öğesi öğesinin bir alt öğesidir [\<client>](../configure-apps/file-schema/wcf/client.md) .</span><span class="sxs-lookup"><span data-stu-id="fab16-141">The endpoint element is a child of the [\<client>](../configure-apps/file-schema/wcf/client.md) element.</span></span> <span data-ttu-id="fab16-142">Ayrıca, `bindingConfiguration` özniteliğini istemci için bağlamaya ayarlayarak bağlama yapılandırmasının adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="fab16-142">Also, specify the name of the binding configuration by setting the `bindingConfiguration` attribute to the binding for the client.</span></span> <span data-ttu-id="fab16-143">Oluşturulmuş bir yapılandırma dosyası kullanıyorsanız, bağlamanın adı otomatik olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="fab16-143">If you are using a generated configuration file, the binding's name is automatically generated.</span></span> <span data-ttu-id="fab16-144">Bu örnekte, adı ' dir `"tcpBindingWithCredential"` .</span><span class="sxs-lookup"><span data-stu-id="fab16-144">In this example, the name is `"tcpBindingWithCredential"`.</span></span>

    ```xml
    <client>
      <endpoint name =""
                address="net.tcp://contoso.com:8036/aloha"
                binding="netTcpBinding"
                bindingConfiguration="tcpBindingWithCredential"
                behaviorConfiguration="endpointCredentialBehavior" />
    </client>
    ```

## <a name="see-also"></a><span data-ttu-id="fab16-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fab16-145">See also</span></span>

- <xref:System.ServiceModel.NetTcpBinding>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>
- <xref:System.ServiceModel.ClientBase%601>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>
- [<span data-ttu-id="fab16-146">WCF Güvenliğini Programlama</span><span class="sxs-lookup"><span data-stu-id="fab16-146">Programming WCF Security</span></span>](./feature-details/programming-wcf-security.md)
- [<span data-ttu-id="fab16-147">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="fab16-147">Selecting a Credential Type</span></span>](./feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="fab16-148">ServiceModel Meta Veri Yardımcı Programracı (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="fab16-148">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="fab16-149">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="fab16-149">Working with Certificates</span></span>](./feature-details/working-with-certificates.md)
- [<span data-ttu-id="fab16-150">Nasıl yapılır: İstemci Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fab16-150">How to: Create a Client</span></span>](how-to-create-a-wcf-client.md)
- [\<netTcpBinding>](../configure-apps/file-schema/wcf/nettcpbinding.md)
- [\<security>](../configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
- [\<message>](../configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)
- [\<behavior>](../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)
- [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md)
- [\<clientCertificate>](../configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)
- [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md)
