---
title: 'Nasıl yapılır: Windows Kimlik Bilgileri ile Bir Hizmeti Güvenli Hale Getirme'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
ms.assetid: d171b5ca-96ef-47ff-800c-c138023cf76e
caps.latest.revision: 26
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: c754a4ec57751b2ca5a809c771b2fb5235ec0510
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="how-to-secure-a-service-with-windows-credentials"></a>Nasıl yapılır: Windows Kimlik Bilgileri ile Bir Hizmeti Güvenli Hale Getirme
Bu konu, taşıma güvenliği etkinleştirmek gösterilmiştir bir [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] bir Windows etki alanında bulunan ve aynı etki alanındaki istemciler tarafından çağrılan hizmet. [!INCLUDE[crabout](../../../includes/crabout-md.md)] Bu senaryo, bkz: [Windows kimlik doğrulama ile taşıma güvenliği](../../../docs/framework/wcf/feature-details/transport-security-with-windows-authentication.md). Örnek bir uygulama için bkz: [WSHttpBinding](../../../docs/framework/wcf/samples/wshttpbinding.md) örnek.  
  
 Bu konu, varolan sözleşme arabirimi varsa ve uygulama zaten tanımlanmış ve açın ekleyen varsayar. Varolan hizmet ve istemci de değiştirebilirsiniz.  
  
 Windows kimlik bilgilerini tamamen kod hizmetiyle güvenliğini sağlayabilirsiniz. Alternatif olarak, bazı kodları bir yapılandırma dosyası kullanarak atlayabilirsiniz. Bu konu, her iki yolunu gösterir. Yalnızca bir yolla ikisini kullandığınızdan emin olun.  
  
 İlk üç yordamlar kod kullanarak hizmet güvenliğini sağlamak nasıl gösterir. Dördüncü ve beşinci yordam bir yapılandırma dosyası ile nasıl yapılacağını gösterir.  
  
## <a name="using-code"></a>Kod kullanarak  
 Tam hizmeti ve istemci için örnek bölümünde, bu konunun sonunda kodudur.  
  
 İlk yordam oluşturma ve yapılandırma yoluyla anlatılmaktadır bir <xref:System.ServiceModel.WSHttpBinding> kodda sınıfı. Bağlama HTTP aktarımı kullanır. Aynı bağlama istemcide kullanılır.  
  
#### <a name="to-create-a-wshttpbinding-that-uses-windows-credentials-and-message-security"></a>Windows kimlik bilgileri ve ileti güvenliği kullanan bir WSHttpBinding oluşturmak için  
  
1.  Bu yordamın kodu başında eklenir `Run` yöntemi `Test` örnek bölümüne hizmet kodunda sınıfta.  
  
2.  Öğesinin bir örneğini oluşturur <xref:System.ServiceModel.WSHttpBinding> sınıfı.  
  
3.  Ayarlama <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> özelliği <xref:System.ServiceModel.WSHttpSecurity> sınıfının <xref:System.ServiceModel.SecurityMode.Message>.  
  
4.  Ayarlama <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> özelliği <xref:System.ServiceModel.MessageSecurityOverHttp> sınıfının <xref:System.ServiceModel.MessageCredentialType.Windows>.  
  
5.  Bu yordam için kod aşağıdaki gibidir:  
  
     [!code-csharp[c_SecureWindowsService#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#1)]
     [!code-vb[c_SecureWindowsService#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#1)]  
  
### <a name="using-the-binding-in-a-service"></a>Bir hizmet olarak bağlama işlemini kullanma  
 Bir kendi kendini barındıran hizmet bağlama kullanmayı gösterir ikinci yordam budur. [!INCLUDE[crabout](../../../includes/crabout-md.md)] barındırma Hizmetleri Bkz: [barındırma hizmetleri](../../../docs/framework/wcf/hosting-services.md).  
  
##### <a name="to-use-a-binding-in-a-service"></a>Bir hizmet olarak bir bağlama kullanmak için  
  
1.  Yukarıdaki yordamı koddan sonra bu yordamın kodu ekleyin.  
  
2.  Oluşturma bir <xref:System.Type> adlı değişken `contractType` ve arabirim atamak (`ICalculator`). Visual Basic, kullanırken `GetType` C#, kullanım kullanırken işleci; `typeof` anahtar sözcüğü.  
  
3.  İkinci bir oluşturma `Type` adlı değişken `serviceType` ve uygulanan sözleşme atamak (`Calculator`).  
  
4.  Bir örneğini oluşturmak <xref:System.Uri> adlı sınıf `baseAddress` hizmetin taban adresine sahip. Temel adres taşıma eşleşen bir düzeni olması gerekir. Bu durumda, aktarma düzeni HTTP ve özel adres içerir Tekdüzen Kaynak Tanımlayıcısı (URI) "localhost" ve bir bağlantı noktası numarası (8036) yanı sıra temel uç noktası adresi ("serviceModelSamples /): http://localhost:8036/serviceModelSamples/.  
  
5.  Bir örneğini oluşturmak <xref:System.ServiceModel.ServiceHost> ile sınıf `serviceType` ve `baseAddress` değişkenleri.  
  
6.  Hizmeti kullanmaya bir uç nokta ekleyin `contractType`, bağlama ve bir uç nokta adı (secureCalculator). Bir istemci taban adresini ve uç nokta adı hizmetine yapılan bir çağrı başlatırken birleştirme gerekir.  
  
7.  Çağrı <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> hizmetini başlatmak için yöntem. Bu yordam için kod aşağıda gösterilmiştir:  
  
     [!code-csharp[c_SecureWindowsService#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#2)]
     [!code-vb[c_SecureWindowsService#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#2)]  
  
### <a name="using-the-binding-in-a-client"></a>Bir istemcinin, bağlama kullanma  
 Bu yordam hizmeti ile iletişim kuran bir proxy oluşturmak nasıl gösterir. Proxy ile oluşturulan [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) proxy oluşturmak için hizmet meta verilerini kullanır.  
  
 Bu yordam, ayrıca bir örneğini oluşturur <xref:System.ServiceModel.WSHttpBinding> hizmetiyle iletişim kurmak için sınıf ve hizmetini çağırır.  
  
 Bu örnek yalnızca kod istemci oluşturmak için kullanır. Alternatif olarak, aşağıdaki yordamı bölümünde gösterilen bir yapılandırma dosyası kullanabilirsiniz.  
  
##### <a name="to-use-a-binding-in-a-client-with-code"></a>Kod ile bir istemci bir bağlama kullanmak için  
  
1.  Hizmet meta verilerinden proxy kodu oluşturmak için SvcUtil.exe aracını kullanın. Daha fazla bilgi için bkz: [nasıl yapılır: bir istemci oluşturmak](../../../docs/framework/wcf/how-to-create-a-wcf-client.md). Oluşturulan proxy kodu devraldığı <xref:System.ServiceModel.ClientBase%601> her istemci gerekli Oluşturucular, yöntemleri ve özellikleri ile iletişim kurmak için sahip olmasını sağlar sınıfı bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet. Bu örnekte, oluşturulan kod içeren `CalculatorClient` sınıfı, hangi uygular `ICalculator` servis kodunu uyumluluğunu etkinleştirme arabirimi.  
  
2.  Bu yordamın kodu başında eklenir `Main` istemci programı yöntemi.  
  
3.  Bir örneğini oluşturmak <xref:System.ServiceModel.WSHttpBinding> sınıfı ve kendi güvenlik modunu ayarlama `Message` ve türü için kimlik bilgisi kendi istemci `Windows`. Örnek değişken adları `clientBinding`.  
  
4.  Bir örneğini oluşturmak <xref:System.ServiceModel.EndpointAddress> adlı sınıf `serviceAddress`. Uç nokta adı ile birleştirilmiş taban adresi ile örneği başlatır.  
  
5.  İle oluşturulan istemci sınıfının bir örneği oluşturma `serviceAddress` ve `clientBinding` değişkenleri.  
  
6.  Çağrı <xref:System.ServiceModel.ClientBase%601.Open%2A> aşağıdaki kodda gösterildiği gibi yöntemi.  
  
7.  Hizmetini çağırmak ve sonuçları görüntüleyin.  
  
     [!code-csharp[c_secureWindowsClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#1)]
     [!code-vb[c_secureWindowsClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#1)]  
  
## <a name="using-the-configuration-file"></a>Yapılandırma dosyasını kullanma  
 Yordam kodu ile bağlama oluşturmak yerine, yapılandırma dosyasının bağlamaları bölümü için gösterilen aşağıdaki kodu kullanabilirsiniz.  
  
 Tanımlı bir hizmet zaten yoksa bkz [Hizmetleri Tasarlama ve uygulama](../../../docs/framework/wcf/designing-and-implementing-services.md), ve [Hizmetleri'ni Yapılandırma](../../../docs/framework/wcf/configuring-services.md).  
  
 **Not** bu yapılandırma kodunu hem hizmet hem de istemci yapılandırma dosyalarında kullanılır.  
  
#### <a name="to-enable-transfer-security-on-a-service-in-a-windows-domain-using-configuration"></a>Bir hizmet yapılandırması'nı kullanarak bir Windows etki alanındaki aktarımı güvenliği etkinleştirmek için  
  
1.  Ekleme bir [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) öğesine [ \<bağlamaları >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) yapılandırma dosyası öğesi bölümü.  
  
2.  Ekleme bir <`binding`> öğesi <`WSHttpBinding`> öğesi ve kümesi `configurationName` özniteliği uygulamanız için uygun bir değere.  
  
3.  Ekleme bir <`security`> öğesi ve kümesi `mode` özniteliği ileti.  
  
4.  Ekleme bir <`message`> öğesi ve kümesi `clientCredentialType` özniteliği Windows.  
  
5.  Hizmet yapılandırma dosyasında değiştirin `<bindings>` bölümü aşağıdaki kod ile. Hizmet yapılandırma dosyası zaten yoksa bkz [kullanarak bağlamaları yapılandırma hizmetler ve istemcileri için](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).  
  
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
  
### <a name="using-the-binding-in-a-client"></a>Bir istemcinin, bağlama kullanma  
 Bu yordamda, iki dosyaları oluşturmak gösterilmiştir: hizmet ve bir yapılandırma dosyası ile iletişim kuran bir proxy. Ayrıca, istemcide kullanılan üçüncü dosyası istemci programı değişiklikleri açıklar.  
  
##### <a name="to-use-a-binding-in-a-client-with-configuration"></a>Bir istemci yapılandırmasına sahip bir bağlama kullanmak için  
  
1.  Hizmet meta verilerinden proxy kod ve yapılandırma dosyası oluşturmak için SvcUtil.exe aracını kullanın. Daha fazla bilgi için bkz: [nasıl yapılır: bir istemci oluşturmak](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).  
  
2.  Değiştir [ \<bağlamaları >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) önceki bölümdeki yapılandırma koduyla üretilen yapılandırma dosyasının bölümü.  
  
3.  Yordam kodu başında eklenen `Main` istemci programı yöntemi.  
  
4.  Giriş parametresi olarak yapılandırma dosyasında bağlama adını geçirerek oluşturulan istemci sınıfının bir örneğini oluşturun.  
  
5.  Çağrı <xref:System.ServiceModel.ClientBase%601.Open%2A> aşağıdaki kodda gösterildiği gibi yöntemi.  
  
6.  Hizmetini çağırmak ve sonuçları görüntüleyin.  
  
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
