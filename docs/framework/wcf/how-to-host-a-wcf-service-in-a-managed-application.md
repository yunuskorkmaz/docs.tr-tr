---
title: "Nasıl yapılır: Yönetilen Bir Uygulamada Bir WCF Hizmeti Barındırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 5eb29db0-b6dc-4e77-8c68-0a62f79d743b
caps.latest.revision: "42"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ddbf0df6e4fbf62ab0e7ec8c741a0f3be01c35ef
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-host-a-wcf-service-in-a-managed-application"></a>Nasıl yapılır: Yönetilen Bir Uygulamada Bir WCF Hizmeti Barındırma
Yönetilen bir uygulama içinde bir hizmet barındırmak için hizmet içinde yönetilen uygulama kodu için kod ekleme, hizmet için bir uç nokta imperatively kodda, yapılandırma veya varsayılan uç noktalarını kullanarak aracılığıyla bildirimli olarak tanımlamanızı ve ardından oluşturmak bir örneği <xref:System.ServiceModel.ServiceHost>.  
  
 İleti alma başlatmak için arama <xref:System.ServiceModel.ICommunicationObject.Open%2A> üzerinde <xref:System.ServiceModel.ServiceHost>. Bu oluşturur ve hizmet için dinleyici açar. Bu şekilde bir hizmet barındırma genellikle "yönetilen uygulamayı barındıran iş yaptığını çünkü kendi kendine barındırma olarak" adlandırılır. Hizmeti kapatmak için çağrı <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> üzerinde <xref:System.ServiceModel.ServiceHost>.  
  
 Bir hizmet, yönetilen bir Windows hizmetinde, Internet Information Services (IIS) veya Windows İşlem Etkinleştirme Hizmeti (WAS) barındırılabilir. [!INCLUDE[crabout](../../../includes/crabout-md.md)]bir hizmetin seçeneklerini barındırma, bkz: [barındırma hizmetleri](../../../docs/framework/wcf/hosting-services.md).  
  
 Yönetilen bir uygulamada bir hizmet barındırma en esnek bir seçenektir; çünkü dağıtmak için en az altyapısı gerektirir. [!INCLUDE[crabout](../../../includes/crabout-md.md)]barındırma hizmetleri yönetilen uygulamalarda, bkz: [yönetilen bir uygulamada barındırma](../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md).  
  
 Aşağıdaki yordam, bir konsol uygulamasında kendini barındıran hizmet uygulamak gösterilmiştir.  
  
### <a name="to-create-a-self-hosted-service"></a>Kendini barındıran bir hizmet oluşturmak için  
  
1.  Açık [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] seçip **yeni**, **proje...**  gelen **dosya** menüsü.  
  
2.  İçinde **yüklü şablonlar** listesinde **Visual C#**, **Windows** veya **Visual Basic**, **Windows**. Bağlı olarak, [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] ayarları, birini veya bunların her ikisi de altında olabilir **diğer diller** düğümünde **yüklü şablonlar** listesi.  
  
3.  Seçin **konsol uygulaması** gelen **Windows** listesi. Tür `SelfHost` içinde **adı** kutusuna ve tıklatın **Tamam**.  
  
4.  Sağ **SelfHost** içinde **Çözüm Gezgini** seçip **Başvuru Ekle...** . Seçin **System.ServiceModel** gelen **.NET** sekmesinde **Tamam**.  
  
    > [!TIP]
    >  Varsa **Çözüm Gezgini** pencere görünür, select değil **Çözüm Gezgini** gelen **Görünüm** menüsü.  
  
5.  Çift **Program.cs** veya **Module1.vb** içinde **Çözüm Gezgini** zaten açık değilse kod penceresinde açın. Dosyanın üst kısmında aşağıdaki deyimleri ekleyin.  
  
     [!code-csharp[CFX_SelfHost4#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#1)]
     [!code-vb[CFX_SelfHost4#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#1)]  
  
6.  Bir hizmet sözleşmesini uygulama ve tanımlayın. Bu örnek tanımlayan bir `HelloWorldService` hizmetine giriş dayalı bir ileti döndürür.  
  
     [!code-csharp[CFX_SelfHost4#2](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#2)]
     [!code-vb[CFX_SelfHost4#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#2)]  
  
    > [!NOTE]
    >  [!INCLUDE[crabout](../../../includes/crabout-md.md)]tanımlamak ve bir hizmet arabirimini uygulayan bkz [nasıl yapılır: bir hizmet sözleşmesini tanımlama](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md) ve [nasıl yapılır: bir hizmet sözleşmesini uygulama](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md).  
  
7.  Üstündeki `Main` yöntemi, bir örneğini oluşturmak <xref:System.Uri> hizmeti temel adresi ile sınıfı.  
  
     [!code-csharp[CFX_SelfHost4#3](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#3)]
     [!code-vb[CFX_SelfHost4#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#3)]  
  
8.  Bir örneğini oluşturmak <xref:System.ServiceModel.ServiceHost> geçirme sınıfı, bir <xref:System.Type> bu temsil Tekdüzen Kaynak Tanımlayıcısı (URI) için hizmet türü ve taban adresi <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29>. Meta veri yayımlama etkinleştirin ve ardından arama <xref:System.ServiceModel.ICommunicationObject.Open%2A> yöntemi <xref:System.ServiceModel.ServiceHost> hizmeti başlatmak ve iletileri almak için hazırlayın.  
  
     [!code-csharp[CFX_SelfHost4#4](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#4)]
     [!code-vb[CFX_SelfHost4#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#4)]       
  
    > [!NOTE]
    >  Bu örnek varsayılan uç noktaları kullanır ve bu hizmet için herhangi bir yapılandırma dosyası gereklidir. Uç nokta yok yapılandırdıysanız, çalışma zamanı hizmeti tarafından uygulanan her hizmet sözleşmesi için her bir taban adresi için bir uç noktası oluşturur. [!INCLUDE[crabout](../../../includes/crabout-md.md)]Varsayılan uç noktaları için bkz: [Basitleştirilmiş yapılandırma](../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
9. Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
### <a name="to-test-the-service"></a>Hizmeti sınamak için  
  
1.  Hizmetini çalıştırmak için Ctrl + F5 tuşuna basın.  
  
2.  Açık **WCF Test istemcisi**.  
  
    > [!TIP]
    >  Açmak için **WCF Test istemcisi**, açık bir [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] komut istemi ve yürütme **WcfTestClient.exe**.  
  
3.  Seçin **hizmeti Ekle...**  gelen **dosya** menüsü.  
  
4.  Tür `http://localhost:8080/hello` tıklatın ve adres kutusuna içine **Tamam**.  
  
    > [!TIP]
    >  Bu adım başarısız yoksa hizmetinin çalıştığından emin olun. Kodda taban adresi değiştiyse, değiştirilmiş taban adresi bu adımı kullanın.  
  
5.  Çift **SayHello** altında **My hizmeti projeleri** düğümü. Adınızı içine yazın **değeri** sütununda **isteği** liste öğesini tıklatıp **Invoke**. Bir yanıt iletisi görünür **yanıt** listesi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir <xref:System.ServiceModel.ServiceHost> türünde bir hizmet barındırmak için nesne `HelloWorldService`ve ardından çağırır <xref:System.ServiceModel.ICommunicationObject.Open%2A> yöntemi <xref:System.ServiceModel.ServiceHost>. Temel adres kodunda sağlanır, meta veri yayımlama etkindir ve varsayılan uç noktaları kullanılır.  
  
 [!code-csharp[CFX_SelfHost4#5](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#5)]
 [!code-vb[CFX_SelfHost4#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#5)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Uri>  
 <xref:System.Configuration.ConfigurationManager.AppSettings%2A>  
 <xref:System.Configuration.ConfigurationManager>  
 [Nasıl yapılır: IIS'de WCF Hizmeti barındırma](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)  
 [Kendini barındırma](../../../docs/framework/wcf/samples/self-host.md)  
 [Barındırma hizmetleri](../../../docs/framework/wcf/hosting-services.md)  
 [Nasıl yapılır: bir hizmet sözleşmesini tanımlama](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)  
 [Nasıl yapılır: bir hizmet sözleşmesini uygulama](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)  
 [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [Hizmetler ve istemcileri yapılandırmak için bağlamaları kullanma](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [Sistem tarafından sağlanan bağlamalar](../../../docs/framework/wcf/system-provided-bindings.md)
