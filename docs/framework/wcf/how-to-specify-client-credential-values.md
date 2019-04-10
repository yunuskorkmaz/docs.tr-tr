---
title: 'Nasıl yapılır: İstemci Kimlik Bilgileri Değerlerini Belirtme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 82293d7f-471a-4549-8f19-0be890e7b074
ms.openlocfilehash: ecb8f7ef74f1f0625454eb2d6cebf9d282a5ece3
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59327106"
---
# <a name="how-to-specify-client-credential-values"></a><span data-ttu-id="1916f-102">Nasıl yapılır: İstemci Kimlik Bilgileri Değerlerini Belirtme</span><span class="sxs-lookup"><span data-stu-id="1916f-102">How to: Specify Client Credential Values</span></span>
<span data-ttu-id="1916f-103">Windows Communication Foundation (WCF) kullanarak, hizmet, bir istemci için hizmet kimliğinin nasıl doğrulandığını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1916f-103">Using Windows Communication Foundation (WCF), the service can specify how a client is authenticated to the service.</span></span> <span data-ttu-id="1916f-104">Örneğin, bir hizmeti bir sertifikayla istemcinin kimliğinin doğrulanmasını koşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1916f-104">For example, a service can stipulate that the client be authenticated with a certificate.</span></span>  
  
### <a name="to-determine-the-client-credential-type"></a><span data-ttu-id="1916f-105">İstemci kimlik bilgileri türünü belirlemek için</span><span class="sxs-lookup"><span data-stu-id="1916f-105">To determine the client credential type</span></span>  
  
1. <span data-ttu-id="1916f-106">Hizmet meta veri uç noktasından meta verilerini alın.</span><span class="sxs-lookup"><span data-stu-id="1916f-106">Retrieve metadata from the service's metadata endpoint.</span></span> <span data-ttu-id="1916f-107">Meta veriler genellikle iki dosyalardan oluşur: İstemci kodu seçtiğiniz programlama dilinde (varsayılan görsel ise C#) ve bir XML yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="1916f-107">The metadata typically consists of two files: the client code in the programming language of your choice (the default is Visual C#), and an XML configuration file.</span></span> <span data-ttu-id="1916f-108">Meta veri alma yollarından biri İstemci kodu ve istemci yapılandırması döndürmek için Svcutil.exe aracını kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="1916f-108">One way to retrieve metadata is to use the Svcutil.exe tool to return the client code and client configuration.</span></span> <span data-ttu-id="1916f-109">Daha fazla bilgi için [meta verileri alınırken](../../../docs/framework/wcf/feature-details/retrieving-metadata.md) ve [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="1916f-109">For more information, see [Retrieving Metadata](../../../docs/framework/wcf/feature-details/retrieving-metadata.md) and [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
2. <span data-ttu-id="1916f-110">XML yapılandırma dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="1916f-110">Open the XML configuration file.</span></span> <span data-ttu-id="1916f-111">Svcutil.exe aracını kullanırsanız, varsayılan dosya Output.config adıdır.</span><span class="sxs-lookup"><span data-stu-id="1916f-111">If you use the Svcutil.exe tool, the default name of the file is Output.config.</span></span>  
  
3. <span data-ttu-id="1916f-112">Bulma  **\<Güvenlik >** öğeyle **modu** özniteliği (**< güvenlik modu =** `MessageOrTransport` **>** nerede `MessageOrTransport` güvenlik modlardan birine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1916f-112">Find the **\<security>** element with the **mode** attribute (**<security mode =**`MessageOrTransport`**>** where `MessageOrTransport` is set to one of the security modes.</span></span>  
  
4. <span data-ttu-id="1916f-113">Mod değeri ile eşleşen alt öğe bulun.</span><span class="sxs-lookup"><span data-stu-id="1916f-113">Find the child element that matches the mode value.</span></span> <span data-ttu-id="1916f-114">Örneğin moduna ayarlanır, **ileti**, bulma  **\<ileti >** içerdiği öğesi  **\<Güvenlik >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="1916f-114">For example, if the mode is set to **Message**, find the **\<message>** element contained in the **\<security>** element.</span></span>  
  
5. <span data-ttu-id="1916f-115">Atanan değer Not **clientCredentialType** özniteliği.</span><span class="sxs-lookup"><span data-stu-id="1916f-115">Note the value assigned to the **clientCredentialType** attribute.</span></span> <span data-ttu-id="1916f-116">Hangi modun kullanıldığına, gerçek değer bağlıdır taşıma veya ileti.</span><span class="sxs-lookup"><span data-stu-id="1916f-116">The actual value depends on which mode is used, transport or message.</span></span>  
  
 <span data-ttu-id="1916f-117">Aşağıdaki XML kodunu, istemcinin kimliğini doğrulamak ileti güveliği kullanarak ve sertifika gerektiren bir istemci için yapılandırmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1916f-117">The following XML code shows configuration for a client using message security and requiring a certificate to authenticate the client.</span></span>  
  
```xml  
<security mode="Message">  
    <transport clientCredentialType="Windows" proxyCredentialType="None"  
        realm="" />  
     <message clientCredentialType="Certificate" negotiateServiceCredential="true"  
    algorithmSuite="Default" establishSecurityContext="true" />  
</security>  
```  
  
## <a name="example-tcp-transport-mode-with-certificate-as-client-credential"></a><span data-ttu-id="1916f-118">Örnek: İstemci kimlik bilgileri olarak sertifika ile TCP taşıma modu</span><span class="sxs-lookup"><span data-stu-id="1916f-118">Example: TCP Transport Mode with Certificate as Client Credential</span></span>  
 <span data-ttu-id="1916f-119">Bu örnek, güvenlik modu aktarım modu için ayarlar ve istemci bir X.509 sertifikası için kimlik bilgisi değeri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1916f-119">This example sets the security mode to Transport mode and sets the client credential value to an X.509 certificate.</span></span> <span data-ttu-id="1916f-120">Aşağıdaki yordamlar, istemci kodu ve yapılandırması istemci kimlik bilgisi değeri ayarlamak nasıl ekleyebileceğiniz gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1916f-120">The following procedures demonstrate how to set the client credential value on the client in code and configuration.</span></span> <span data-ttu-id="1916f-121">Bu, kullandığınızı varsayar [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) hizmetinden (kod ve yapılandırma) meta verileri döndürmek için.</span><span class="sxs-lookup"><span data-stu-id="1916f-121">This assumes that you have used the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to return the metadata (code and configuration) from the service.</span></span> <span data-ttu-id="1916f-122">Daha fazla bilgi için [nasıl yapılır: Bir istemci oluşturmanız](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="1916f-122">For more information, see [How to: Create a Client](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span>  
  
#### <a name="to-specify-the-client-credential-value-on-the-client-in-code"></a><span data-ttu-id="1916f-123">Kod içinde bulunan istemciye istemci kimlik bilgisi değeri belirtmek için</span><span class="sxs-lookup"><span data-stu-id="1916f-123">To specify the client credential value on the client in code</span></span>  
  
1. <span data-ttu-id="1916f-124">Kullanım [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) kod ve Yapılandırma hizmeti oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="1916f-124">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate code and configuration from the service.</span></span>  
  
2. <span data-ttu-id="1916f-125">Oluşturulan kod kullanarak WCF istemci örneği oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1916f-125">Create an instance of the WCF client using the generated code.</span></span>  
  
3. <span data-ttu-id="1916f-126">İstemci sınıfına <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> özelliği <xref:System.ServiceModel.ClientBase%601> sınıfı uygun değeri.</span><span class="sxs-lookup"><span data-stu-id="1916f-126">On the client class, set the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the <xref:System.ServiceModel.ClientBase%601> class to an appropriate value.</span></span> <span data-ttu-id="1916f-127">Bu örnek özelliği kullanarak bir X.509 sertifikası ayarlar <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> yöntemi <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1916f-127">This example sets the property to an X.509 certificate using the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> class.</span></span>  
  
     [!code-csharp[c_TcpService#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#4)]
     [!code-vb[c_TcpService#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#4)]  
  
     <span data-ttu-id="1916f-128">Numaralandırmalar dilediğinizi kullanabilirsiniz <xref:System.Security.Cryptography.X509Certificates.X509FindType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1916f-128">You can use any of the enumerations of the <xref:System.Security.Cryptography.X509Certificates.X509FindType> class.</span></span> <span data-ttu-id="1916f-129">Konu adı, sertifika (sona erme tarihi nedeniyle) değişir durumda burada kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1916f-129">The subject name is used here in case the certificate is changed (due to an expiration date).</span></span> <span data-ttu-id="1916f-130">Konu adı'nı kullanarak sertifikayı yeniden bulmak için altyapı sağlar.</span><span class="sxs-lookup"><span data-stu-id="1916f-130">Using the subject name enables the infrastructure to find the certificate again.</span></span>  
  
#### <a name="to-specify-the-client-credential-value-on-the-client-in-configuration"></a><span data-ttu-id="1916f-131">İstemci yapılandırması üzerinde istemci kimlik bilgisi değeri belirtmek için</span><span class="sxs-lookup"><span data-stu-id="1916f-131">To specify the client credential value on the client in configuration</span></span>  
  
1. <span data-ttu-id="1916f-132">Ekleme bir [ \<davranışı >](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) öğesine [ \<davranışları >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="1916f-132">Add a [\<behavior>](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element to the [\<behaviors>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span></span>  
  
2. <span data-ttu-id="1916f-133">Ekleme bir [ \<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) öğesine [ \<davranışları >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="1916f-133">Add a [\<clientCredentials>](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element to the [\<behaviors>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span></span> <span data-ttu-id="1916f-134">Gerekli ayarladığınızdan emin olun `name` özniteliği için uygun bir değer.</span><span class="sxs-lookup"><span data-stu-id="1916f-134">Be sure to set the required `name` attribute to an appropriate value.</span></span>  
  
3. <span data-ttu-id="1916f-135">Ekleme bir [ \<clientCertificate >](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md) öğesine [ \<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="1916f-135">Add a [\<clientCertificate>](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md) element to the [\<clientCredentials>](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element.</span></span>  
  
4. <span data-ttu-id="1916f-136">Aşağıdaki öznitelikler uygun değerlere ayarlayın: `storeLocation`, `storeName`, `x509FindType`, ve `findValue`aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="1916f-136">Set the following attributes to appropriate values: `storeLocation`, `storeName`, `x509FindType`, and `findValue`, as shown in the following code.</span></span> <span data-ttu-id="1916f-137">Sertifikalar hakkında daha fazla bilgi için bkz. [Working with Certificates](../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="1916f-137">For more information about certificates, see [Working with Certificates](../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>  
  
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
  
5. <span data-ttu-id="1916f-138">İstemci yapılandırırken ayarlayarak davranışı belirtin `behaviorConfiguration` özniteliği `<endpoint>` öğesi, aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="1916f-138">When configuring the client, specify the behavior by setting the `behaviorConfiguration` attribute of the `<endpoint>` element, as shown in the following code.</span></span> <span data-ttu-id="1916f-139">Uç nokta öğesi bir alt öğesidir [ \<istemci >](../../../docs/framework/configure-apps/file-schema/wcf/client.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="1916f-139">The endpoint element is a child of the [\<client>](../../../docs/framework/configure-apps/file-schema/wcf/client.md) element.</span></span> <span data-ttu-id="1916f-140">Ayrıca, ayarlayarak bağlama yapılandırmasının adını belirtin. `bindingConfiguration` istemci için bağlama özniteliği.</span><span class="sxs-lookup"><span data-stu-id="1916f-140">Also, specify the name of the binding configuration by setting the `bindingConfiguration` attribute to the binding for the client.</span></span> <span data-ttu-id="1916f-141">Bağlama adı, oluşturulan yapılandırma dosyası kullanıyorsanız, otomatik olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1916f-141">If you are using a generated configuration file, the binding's name is automatically generated.</span></span> <span data-ttu-id="1916f-142">Bu örnekte, addır `"tcpBindingWithCredential"`.</span><span class="sxs-lookup"><span data-stu-id="1916f-142">In this example, the name is `"tcpBindingWithCredential"`.</span></span>  
  
    ```xml  
    <client>  
      <endpoint name =""  
                address="net.tcp://contoso.com:8036/aloha"  
                binding="netTcpBinding"  
                bindingConfiguration="tcpBindingWithCredential"  
                behaviorConfiguration="endpointCredentialBehavior" />  
    </client>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="1916f-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1916f-143">See also</span></span>

- <xref:System.ServiceModel.NetTcpBinding>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>
- <xref:System.ServiceModel.ClientBase%601>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>
- [<span data-ttu-id="1916f-144">WCF Güvenliğini Programlama</span><span class="sxs-lookup"><span data-stu-id="1916f-144">Programming WCF Security</span></span>](../../../docs/framework/wcf/feature-details/programming-wcf-security.md)
- [<span data-ttu-id="1916f-145">Kimlik Bilgisi Türü Seçme</span><span class="sxs-lookup"><span data-stu-id="1916f-145">Selecting a Credential Type</span></span>](../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="1916f-146">ServiceModel Meta Veri Yardımcı Programracı (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="1916f-146">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="1916f-147">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="1916f-147">Working with Certificates</span></span>](../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="1916f-148">Nasıl yapılır: İstemci Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1916f-148">How to: Create a Client</span></span>](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
- [<span data-ttu-id="1916f-149">\<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="1916f-149">\<netTcpBinding></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)
- [<span data-ttu-id="1916f-150">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="1916f-150">\<security></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
- [<span data-ttu-id="1916f-151">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="1916f-151">\<message></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)
- [<span data-ttu-id="1916f-152">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="1916f-152">\<behavior></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)
- [<span data-ttu-id="1916f-153">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="1916f-153">\<behaviors></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)
- [<span data-ttu-id="1916f-154">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="1916f-154">\<clientCertificate></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)
- [<span data-ttu-id="1916f-155">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="1916f-155">\<clientCredentials></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)
