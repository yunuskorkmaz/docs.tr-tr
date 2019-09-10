---
title: 'Nasıl yapılır: Windows Kimlik Bilgileri ile Bir Hizmeti Güvenli Hale Getirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
ms.assetid: d171b5ca-96ef-47ff-800c-c138023cf76e
ms.openlocfilehash: 19ac9da94ce6e405632293a7d569698c9d866bef
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70856056"
---
# <a name="how-to-secure-a-service-with-windows-credentials"></a>Nasıl yapılır: Windows Kimlik Bilgileri ile Bir Hizmeti Güvenli Hale Getirme

Bu konu başlığı altında, bir Windows etki alanında bulunan ve aynı etki alanındaki istemciler tarafından çağrılan bir Windows Communication Foundation (WCF) hizmetinde aktarım güvenliğinin nasıl etkinleştirileceği gösterilmektedir. Bu senaryo hakkında daha fazla bilgi için bkz. [Windows kimlik doğrulamasıyla taşıma güvenliği](../../../docs/framework/wcf/feature-details/transport-security-with-windows-authentication.md). Örnek bir uygulama için bkz. [WSHttpBinding](../../../docs/framework/wcf/samples/wshttpbinding.md) örneği.

Bu konu başlığı altında, var olan bir sözleşme arabirimi ve uygulamanızın zaten tanımlanmış olduğu varsayılır ve bu uygulamaya eklenir. Ayrıca var olan bir hizmeti ve istemciyi de değiştirebilirsiniz.

Windows kimlik bilgileriyle bir hizmetin güvenliğini tamamen kodda bulabilirsiniz. Alternatif olarak, bir yapılandırma dosyası kullanarak bazı kodları atlayabilirsiniz. Bu konuda her iki yol da gösterilmektedir. Her ikisini değil yalnızca birini kullandığınızdan emin olun.

İlk üç yordam, kodu kullanarak hizmetin nasıl güvence altına alınacağını gösterir. Dördüncü ve beşinci yordam, bir yapılandırma dosyası ile nasıl yapılacağını gösterir.

## <a name="using-code"></a>Kod kullanma

Hizmetin ve istemcinin tüm kodu, bu konunun sonundaki örnek bölümdür.

İlk yordam kodda bir <xref:System.ServiceModel.WSHttpBinding> sınıf oluşturma ve yapılandırmayı adım adım göstermektedir. Bağlama HTTP aktarımını kullanır. İstemcide aynı bağlama kullanılır.

#### <a name="to-create-a-wshttpbinding-that-uses-windows-credentials-and-message-security"></a>Windows kimlik bilgileri ve ileti güvenliği kullanan bir WSHttpBinding oluşturmak için

1. Bu yordamın kodu, örnek bölümünde hizmet kodundaki `Run` `Test` sınıfının yönteminin başına eklenir.

2. Öğesinin bir örneğini oluşturur <xref:System.ServiceModel.WSHttpBinding> sınıfı.

3. Sınıfının özelliğini olarak<xref:System.ServiceModel.SecurityMode.Message>ayarlayın. <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> <xref:System.ServiceModel.WSHttpSecurity>

4. Sınıfının özelliğini olarak<xref:System.ServiceModel.MessageCredentialType.Windows>ayarlayın. <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> <xref:System.ServiceModel.MessageSecurityOverHttp>

5. Bu yordamın kodu aşağıdaki gibidir:

    [!code-csharp[c_SecureWindowsService#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#1)]
    [!code-vb[c_SecureWindowsService#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#1)]

### <a name="using-the-binding-in-a-service"></a>Bir hizmette bağlamayı kullanma

Bu, bağlamanın şirket içinde barındırılan bir hizmette nasıl kullanılacağını gösteren ikinci yordamdır. Barındırma hizmetleri hakkında daha fazla bilgi için bkz. [barındırma hizmetleri](../../../docs/framework/wcf/hosting-services.md).

##### <a name="to-use-a-binding-in-a-service"></a>Bir hizmette bağlama kullanmak için

1. Önceki yordamdan koddan sonra bu yordamın kodunu ekleyin.

2. `ICalculator`Adlı <xref:System.Type> birdeğişkenoluşturunvearabirimintürünü`contractType` () atayın. Visual Basic kullanırken `GetType` işlecini kullanın; kullanırken C#, `typeof` anahtar sözcüğünü kullanın.

3. `Calculator`Adlı <xref:System.Type> ikincibirdeğişkenoluşturunveuygulanansözleşmenintürünü`serviceType` () atayın.

4. Hizmetin temel adresiyle adlı <xref:System.Uri> `baseAddress` sınıfının bir örneğini oluşturun. Temel adres, aktarımdan eşleşen bir şemaya sahip olmalıdır. Bu durumda, aktarım düzeni HTTP olur ve adres, özel Tekdüzen Kaynak tanımlayıcısı (URI) "localhost" ve bir bağlantı noktası numarası (8036) ve bir taban bitiş noktası adresi ("serviceModelSamples/): `http://localhost:8036/serviceModelSamples/`ile birlikte yer alır.

5. Ve`serviceType` <xref:System.ServiceModel.ServiceHost> değişkenleriilesınıfının`baseAddress` bir örneğini oluşturun.

6. `contractType`, Bağlamayı ve bir uç nokta adını (secureCalculator) kullanarak hizmete bir uç nokta ekleyin. Bir istemcinin, hizmete bir çağrı başlatırken temel adresi ve uç nokta adını birleştirme gerekir.

7. Hizmeti başlatmak için yöntemini çağırın. <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> Bu yordamın kodu burada gösterilmektedir:

    [!code-csharp[c_SecureWindowsService#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#2)]
    [!code-vb[c_SecureWindowsService#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#2)]

### <a name="using-the-binding-in-a-client"></a>Bir Istemcide bağlamayı kullanma

Bu yordamda hizmeti ile iletişim kuran bir proxy oluşturma işlemi gösterilmektedir. Proxy, proxy 'yi oluşturmak için hizmet meta verilerini kullanan [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ile oluşturulur.

Bu yordam Ayrıca, hizmet ile iletişim kurmak <xref:System.ServiceModel.WSHttpBinding> için sınıfının bir örneğini oluşturur ve ardından hizmeti çağırır.

Bu örnek, yalnızca istemciyi oluşturmak için kod kullanır. Alternatif olarak, bu yordamı izleyen bölümünde gösterilen bir yapılandırma dosyası kullanabilirsiniz.

##### <a name="to-use-a-binding-in-a-client-with-code"></a>Bir istemcide kodla bir bağlama kullanmak için

1. Hizmetin meta verilerinden proxy kodunu oluşturmak için SvcUtil. exe aracını kullanın. Daha fazla bilgi için [nasıl yapılır: Istemci](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)oluşturun. Oluşturulan proxy kodu <xref:System.ServiceModel.ClientBase%601> sınıfından devralır, bu, her istemcinin bir WCF hizmetiyle iletişim kurmak için gerekli oluşturucular, Yöntemler ve özelliklere sahip olmasını sağlar. Bu örnekte, oluşturulan kod, `CalculatorClient` `ICalculator` arabirimi uygulayan sınıfı içerir ve hizmet koduyla uyumluluğu etkinleştirir.

2. Bu yordamın kodu, istemci programı `Main` yönteminin başına eklenir.

3. <xref:System.ServiceModel.WSHttpBinding> Sınıfının bir örneğini oluşturun ve güvenlik `Message` modunu ve onun istemci kimlik bilgisi türünü olarak `Windows`ayarlayın. Örnek, değişkenini `clientBinding`adlandırır.

4. <xref:System.ServiceModel.EndpointAddress> Adlı`serviceAddress`sınıfının bir örneğini oluşturun. Uç nokta adıyla birleştirilmiş temel adresi olan örneği başlatın.

5. Oluşturulan istemci sınıfının `serviceAddress` `clientBinding` ve değişkenlerini içeren bir örneğini oluşturun.

6. Aşağıdaki kodda gösterildiği gibi yönteminiçağırın.<xref:System.ServiceModel.ClientBase%601.Open%2A>

7. Hizmeti çağırın ve sonuçları görüntüleyin.

    [!code-csharp[c_secureWindowsClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#1)]
    [!code-vb[c_secureWindowsClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#1)]

## <a name="using-the-configuration-file"></a>Yapılandırma dosyasını kullanma

Yordam kodu ile bağlama oluşturmak yerine, yapılandırma dosyasının bağlamalar bölümü için gösterilen aşağıdaki kodu kullanabilirsiniz.

Önceden tanımlanmış bir hizmetiniz yoksa, bkz. [Hizmetleri tasarlama ve uygulama](../../../docs/framework/wcf/designing-and-implementing-services.md)ve [Hizmetleri yapılandırma](../../../docs/framework/wcf/configuring-services.md).

> [!NOTE]
> Bu yapılandırma kodu hem hizmet hem de istemci yapılandırma dosyalarında kullanılır.

#### <a name="to-enable-transfer-security-on-a-service-in-a-windows-domain-using-configuration"></a>Yapılandırma kullanarak Windows etki alanındaki bir hizmette aktarım güvenliğini sağlamak için

1. Yapılandırma [dosyasının \<bağlamalar >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) öğesi bölümüne bir [ \<WSHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) öğesi ekleyin.

2. <`binding``WSHttpBinding` >Öğesinebir<>öğesiekleyinveözniteliğiuygulamanızauygun`configurationName` bir değere ayarlayın.

3. Bir <`security`> öğesi ekleyin ve `mode` özniteliği ileti olarak ayarlayın.

4. <`message`Bir > öğesi ekleyin ve `clientCredentialType` özniteliği Windows 'a ayarlayın.

5. Hizmetin yapılandırma dosyasında `<bindings>` bölümünü aşağıdaki kodla değiştirin. Zaten bir hizmet yapılandırma dosyanız yoksa, bkz. [Hizmetleri ve Istemcileri yapılandırmak Için bağlamaları kullanma](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).

    ```xml
    <bindings>
      <wsHttpBinding>
       <binding name = "wsHttpBinding_Calculator">
         <security mode="Message">
           <message clientCredentialType="Windows"/>
         </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    ```

### <a name="using-the-binding-in-a-client"></a>Bir Istemcide bağlamayı kullanma

Bu yordamda iki dosyanın nasıl oluşturulacağı gösterilmektedir: hizmetle iletişim kuran bir ara sunucu ve bir yapılandırma dosyası. Ayrıca, istemci programında, istemcide kullanılan üçüncü dosya olan değişiklikleri açıklar.

##### <a name="to-use-a-binding-in-a-client-with-configuration"></a>Yapılandırmaya sahip bir istemcide bağlama kullanmak için

1. Proxy kodunu ve yapılandırma dosyasını hizmetin meta verilerinden oluşturmak için SvcUtil. exe aracını kullanın. Daha fazla bilgi için [nasıl yapılır: Istemci](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)oluşturun.

2. Oluşturulan yapılandırma dosyasının [ bağlama>bölümünü,öncekibölümdekiyapılandırmakoduiledeğiştirin.\<](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)

3. Yordam kodu, istemci programı `Main` yönteminin başına eklenir.

4. Yapılandırma dosyasındaki bağlamanın adını giriş parametresi olarak geçirerek oluşturulan istemci sınıfının bir örneğini oluşturun.

5. Aşağıdaki kodda gösterildiği gibi yönteminiçağırın.<xref:System.ServiceModel.ClientBase%601.Open%2A>

6. Hizmeti çağırın ve sonuçları görüntüleyin.

    [!code-csharp[c_secureWindowsClient#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#2)]

## <a name="example"></a>Örnek

[!code-csharp[c_SecureWindowsService#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#0)]

[!code-csharp[c_SecureWindowsClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#0)]
[!code-vb[c_SecureWindowsClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#0)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.WSHttpBinding>
- [ServiceModel Meta Veri Yardımcı Programı Aracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Nasıl yapılır: Istemci oluşturma](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
- [Hizmetleri Güvenli Hale Getirme](../../../docs/framework/wcf/securing-services.md)
- [Güvenliğe Genel Bakış](../../../docs/framework/wcf/feature-details/security-overview.md)
