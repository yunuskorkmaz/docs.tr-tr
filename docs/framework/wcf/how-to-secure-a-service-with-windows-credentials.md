---
title: 'Nasıl yapılır: Windows Kimlik Bilgileri ile Bir Hizmeti Güvenli Hale Getirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
ms.assetid: d171b5ca-96ef-47ff-800c-c138023cf76e
author: BrucePerlerMS
ms.openlocfilehash: bf88073c25351aac0e421d69a947605de3e37759
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47200704"
---
# <a name="how-to-secure-a-service-with-windows-credentials"></a>Nasıl yapılır: Windows Kimlik Bilgileri ile Bir Hizmeti Güvenli Hale Getirme
Bu konuda, bir Windows etki alanında bulunan ve aynı etki alanında istemcileri tarafından çağrılan bir Windows Communication Foundation (WCF) hizmeti aktarım güvenliği etkinleştirme gösterilmektedir. Bu senaryo hakkında daha fazla bilgi için bkz. [Windows kimlik doğrulama ile Aktarım güvenliği](../../../docs/framework/wcf/feature-details/transport-security-with-windows-authentication.md). Örnek bir uygulama için bkz: [WSHttpBinding](../../../docs/framework/wcf/samples/wshttpbinding.md) örnek.  
  
 Bu konu, mevcut bir sözleşme arabirimi varsa ve uygulama zaten tanımlanmış ve açın ekleyen varsayar. Bir mevcut hizmet ve istemci de değiştirebilirsiniz.  
  
 Kod içinde tamamen Windows kimlik bilgileri ile bir hizmeti güvenli hale getirebilirsiniz. Alternatif olarak, bazı kodları bir yapılandırma dosyası kullanarak atlayabilirsiniz. Bu konu, her iki yönde gösterir. Yalnızca şekilde ikisini kullandığınızdan emin olun.  
  
 İlk üç yordamlar kod kullanarak hizmet güvenliğinin nasıl sağlanacağını gösterir. Dördüncü ve beşinci yordamı, bir yapılandırma dosyası ile nasıl yapılacağını gösterir.  
  
## <a name="using-code"></a>Kod kullanarak  
 Tam hizmet ve istemci için bu konunun sonundaki örneği bölümündeki kodudur.  
  
 İlk yordam oluşturma ve yapılandırma aracılığıyla size yol gösterir bir <xref:System.ServiceModel.WSHttpBinding> kod sınıfı. Bağlama HTTP aktarımı kullanır. Aynı bağlama istemci üzerinde kullanılır.  
  
#### <a name="to-create-a-wshttpbinding-that-uses-windows-credentials-and-message-security"></a>İleti güvenliği Windows kimlik bilgilerini kullanan bir WSHttpBinding oluşturmak için  
  
1.  Bu yordamın kod başında eklenen `Run` yöntemi `Test` örnek bölümünde hizmeti kodunda bir sınıfta.  
  
2.  Öğesinin bir örneğini oluşturur <xref:System.ServiceModel.WSHttpBinding> sınıfı.  
  
3.  Ayarlama <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> özelliği <xref:System.ServiceModel.WSHttpSecurity> sınıfının <xref:System.ServiceModel.SecurityMode.Message>.  
  
4.  Ayarlama <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> özelliği <xref:System.ServiceModel.MessageSecurityOverHttp> sınıfının <xref:System.ServiceModel.MessageCredentialType.Windows>.  
  
5.  Bu yordamı için kod aşağıdaki gibidir:  
  
     [!code-csharp[c_SecureWindowsService#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#1)]
     [!code-vb[c_SecureWindowsService#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#1)]  
  
### <a name="using-the-binding-in-a-service"></a>Bir hizmet olarak bağlama işlemini kullanma  
 Şirket içinde barındırılan hizmetinde bağlama işlemi gösterilmektedir ikinci yordam budur. Barındırma hizmetleri hakkında daha fazla bilgi için bkz. [barındırma hizmetleri](../../../docs/framework/wcf/hosting-services.md).  
  
##### <a name="to-use-a-binding-in-a-service"></a>Hizmet bağlamayı kullanmak için  
  
1.  Bu yordamın kod, önceki yordamdaki koddan sonra ekleyin.  
  
2.  Oluşturma bir <xref:System.Type> adlı değişken `contractType` ve arabirim türü atayın (`ICalculator`). Visual Basic, kullanırken `GetType` işleci; C#, kullanım kullanırken `typeof` anahtar sözcüğü.  
  
3.  Bir saniye oluşturun `Type` adlı değişken `serviceType` ve uygulanan sözleşme türü atayın (`Calculator`).  
  
4.  Bir örneğini oluşturmak <xref:System.Uri> adlı sınıfı `baseAddress` hizmetin taban adresine sahip. Taban adresi taşıma eşleşen bir düzen olmalıdır. Bu durumda, HTTP taşıma şeması olduğunda ve özel adresini içeren "Localhost" Tekdüzen Kaynak Tanımlayıcısı (URI) ve bağlantı noktası numarası (8036) yanı sıra bir taban uç nokta adresi ("serviceModelSamples /): http://localhost:8036/serviceModelSamples/.  
  
5.  Bir örneğini oluşturmak <xref:System.ServiceModel.ServiceHost> sınıfıyla `serviceType` ve `baseAddress` değişkenleri.  
  
6.  Kullanarak hizmet için uç nokta ekleme `contractType`, bağlama ve bir uç nokta adı (secureCalculator). Bir istemci taban adresini ve bitiş noktası adı hizmeti çağrısı başlatırken bağlamak gerekir.  
  
7.  Çağrı <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> hizmeti başlatmak için yöntemi. Bu yordam kodu aşağıda gösterilmiştir:  
  
     [!code-csharp[c_SecureWindowsService#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#2)]
     [!code-vb[c_SecureWindowsService#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#2)]  
  
### <a name="using-the-binding-in-a-client"></a>Bir istemci kullanarak bağlama  
 Bu yordam, hizmet ile iletişim kuran bir proxy oluşturma adımları anlatılmaktadır. Proxy ile oluşturulan [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) proxy oluşturmak için hizmet meta verileri kullanır.  
  
 Bu yordam, ayrıca bir örneğini oluşturur <xref:System.ServiceModel.WSHttpBinding> hizmetiyle iletişim kurmak için sınıf ve ardından hizmeti çağırır.  
  
 Bu örnek yalnızca kod istemcisi oluşturmak için kullanır. Alternatif olarak, bu yordamı aşağıdaki bölümde görüntülenen bir yapılandırma dosyası kullanabilirsiniz.  
  
##### <a name="to-use-a-binding-in-a-client-with-code"></a>Bir istemci koduna sahip bir bağlama kullanmak için  
  
1.  Hizmet meta verilerinden proxy kodunu üretmek için SvcUtil.exe aracını kullanın. Daha fazla bilgi için [nasıl yapılır: istemci oluşturma](../../../docs/framework/wcf/how-to-create-a-wcf-client.md). Oluşturulan proxy kodu devraldığı <xref:System.ServiceModel.ClientBase%601> her istemci gerekli Oluşturucular, yöntemleri ve özellikleri bir WCF Hizmeti ile iletişim kurmak için sahip olmasını sağlar sınıfını. Bu örnekte, oluşturulan kod içeren `CalculatorClient` sınıfını `ICalculator` arabirimi, hizmet kod uyumluluğunu etkinleştirme.  
  
2.  Bu yordamın kod başında eklenen `Main` istemci programı yöntemi.  
  
3.  Bir örneğini oluşturmak <xref:System.ServiceModel.WSHttpBinding> sınıfı ve kendi güvenlik modunu ayarlama `Message` ve kimlik bilgisi türü için istemci `Windows`. Örnekte, değişken adları `clientBinding`.  
  
4.  Bir örneğini oluşturmak <xref:System.ServiceModel.EndpointAddress> adlı sınıfı `serviceAddress`. Uç nokta adı ile birleştirilmiş temel adresine sahip örneği başlatır.  
  
5.  Oluşturulmuş istemci sınıfı örneğini oluşturmak `serviceAddress` ve `clientBinding` değişkenleri.  
  
6.  Çağrı <xref:System.ServiceModel.ClientBase%601.Open%2A> yöntemi, aşağıdaki kodda gösterildiği gibi.  
  
7.  Hizmet çağrısı ve sonuçları görüntüler.  
  
     [!code-csharp[c_secureWindowsClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#1)]
     [!code-vb[c_secureWindowsClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#1)]  
  
## <a name="using-the-configuration-file"></a>Yapılandırma dosyasını kullanma  
 Yordam kodu ile bağlama oluşturmak yerine, yapılandırma dosyasının bağlamalar bölümü için gösterilen aşağıdaki kodu kullanabilirsiniz.  
  
 Tanımlı bir hizmet zaten yoksa bkz [Hizmetleri Tasarlama ve uygulama](../../../docs/framework/wcf/designing-and-implementing-services.md), ve [Hizmetleri'ni Yapılandırma](../../../docs/framework/wcf/configuring-services.md).  
  
 **Not** bu yapılandırma kod hizmet ve istemci yapılandırma dosyalarında kullanılır.  
  
#### <a name="to-enable-transfer-security-on-a-service-in-a-windows-domain-using-configuration"></a>Aktarım Güvenlik Yapılandırması'nı kullanarak bir Windows etki alanında bir hizmet üzerinde etkinleştirmek için  
  
1.  Ekleme bir [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) öğesine [ \<bağlamaları >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) yapılandırma dosyası bölümünü öğesi.  
  
2.  Ekleyin bir <`binding`> öğesi <`WSHttpBinding`> öğesi ve set `configurationName` uygulamanız için uygun bir değer özniteliği.  
  
3.  Ekleme bir <`security`> öğesi ve kümesi `mode` özniteliği ileti.  
  
4.  Ekleme bir <`message`> öğesi ve set `clientCredentialType` Windows için öznitelik.  
  
5.  Hizmet yapılandırma dosyasında değiştirin `<bindings>` bölümü aşağıdaki kod ile. Hizmet yapılandırma dosyasını zaten yoksa bkz [hizmetlerini yapılandırın ve istemciler için bağlamaları kullanma](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).  
  
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
  
### <a name="using-the-binding-in-a-client"></a>Bir istemci kullanarak bağlama  
 Bu yordamda, iki dosya oluşturmak gösterilmiştir: bir proxy hizmeti ve yapılandırma dosyası ile iletişim kurar. Ayrıca, istemcide kullanılan üçüncü dosya istemci programı değişiklikler açıklanmaktadır.  
  
##### <a name="to-use-a-binding-in-a-client-with-configuration"></a>Bir istemci yapılandırma ile bir bağlama kullanmak için  
  
1.  Hizmet meta verilerinden proxy kod ve yapılandırma dosyası üretmek için SvcUtil.exe aracını kullanın. Daha fazla bilgi için [nasıl yapılır: istemci oluşturma](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).  
  
2.  Değiştirin [ \<bağlamaları >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) ise önceki bölümden yapılandırma kod ile oluşturulan yapılandırma dosyasının.  
  
3.  Yordam kodu başında eklenen `Main` istemci programı yöntemi.  
  
4.  Giriş parametresi olarak yapılandırma dosyasında bağlama adını geçirerek oluşturulan istemci sınıfının bir örneğini oluşturun.  
  
5.  Çağrı <xref:System.ServiceModel.ClientBase%601.Open%2A> yöntemi, aşağıdaki kodda gösterildiği gibi.  
  
6.  Hizmet çağrısı ve sonuçları görüntüler.  
  
     [!code-csharp[c_secureWindowsClient#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#2)]  
  
## <a name="example"></a>Örnek  
 [!code-csharp[c_SecureWindowsService#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#0)]  
  
 [!code-csharp[c_SecureWindowsClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#0)] 
 [!code-vb[c_SecureWindowsClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#0)]      
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.WSHttpBinding>  
 [ServiceModel Meta Veri Yardımcı Programı Aracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [Nasıl yapılır: İstemci Oluşturma](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [Hizmetleri Güvenli Hale Getirme](../../../docs/framework/wcf/securing-services.md)  
 [Güvenliğe Genel Bakış](../../../docs/framework/wcf/feature-details/security-overview.md)
