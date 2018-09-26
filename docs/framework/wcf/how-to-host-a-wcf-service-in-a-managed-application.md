---
title: 'Nasıl yapılır: Yönetilen Bir Uygulamada Bir WCF Hizmeti Barındırma'
ms.date: 09/17/2018
dev_langs:
- csharp
- vb
ms.assetid: 5eb29db0-b6dc-4e77-8c68-0a62f79d743b
ms.openlocfilehash: 131d99457427e0818f78076d987f550a99ad7cf0
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47113682"
---
# <a name="how-to-host-a-wcf-service-in-a-managed-app"></a>Nasıl yapılır: yönetilen bir uygulamada bir WCF Hizmeti barındırma

Bir hizmet içinde yönetilen bir uygulamayı barındırmak için hizmet içinde yönetilen bir uygulama kodu için kod ekleme, hizmet için bir uç nokta kesin kodda, yapılandırma veya varsayılan uç nokta kullanarak aracılığıyla bildirimli olarak tanımlamanızı ve oluşturup bir örneğini <xref:System.ServiceModel.ServiceHost>.

İletileri almaya başlaması için çağrı <xref:System.ServiceModel.ICommunicationObject.Open%2A> üzerinde <xref:System.ServiceModel.ServiceHost>. Bu, oluşturur ve hizmet için dinleyici açılır. Bu şekilde bir hizmet barındırma genellikle "yönetilen uygulamayı barındıran iş yapıyor çünkü kendi kendine barındırma olarak" adlandırılır. Hizmeti kapatmak için çağrı <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> üzerinde <xref:System.ServiceModel.ServiceHost>.

Bir hizmet, yönetilen bir Windows hizmetinde, Internet Information Services (IIS) veya Windows İşlem Etkinleştirme Hizmeti (WAS) barındırılabilir. Barındırma seçenekleri bir hizmet için hakkında daha fazla bilgi için bkz. [barındırma hizmetleri](../../../docs/framework/wcf/hosting-services.md).

Dağıtmak için en az bir altyapı gerektiğinden bir hizmeti yönetilen bir uygulamada barındırma en esnek seçenektir. Barındırma hizmetleri, yönetilen uygulamalar hakkında daha fazla bilgi için bkz. [yönetilen bir uygulamada barındırma](../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md).

Aşağıdaki yordam, şirket içinde barındırılan hizmeti bir konsol uygulamasında uygulama gösterilmiştir.

## <a name="create-a-self-hosted-service"></a>Şirket içinde barındırılan bir hizmet oluşturma

1. Yeni bir konsol uygulaması oluşturun:

   1. Visual Studio açıp seçin **yeni** > **proje** gelen **dosya** menüsü.

   2. İçinde **yüklü şablonlar** listesinden **Visual C#** veya **Visual Basic**ve ardından **Windows Masaüstü**.

   3. Seçin **konsol uygulaması** şablonu. Tür `SelfHost` içinde **adı** kutusuna ve ardından **Tamam**.

2. Sağ **SelfHost** içinde **Çözüm Gezgini** seçip **Başvuru Ekle**. Seçin **System.ServiceModel** gelen **.NET** sekmesine ve ardından **Tamam**.

    > [!TIP]
    > Varsa **Çözüm Gezgini** pencere görünür, select değil **Çözüm Gezgini** gelen **görünümü** menüsü.

3. Çift **Program.cs** veya **Module1.vb** içinde **Çözüm Gezgini** zaten açık değilse kod penceresinde açmak için. Dosyasının en üstüne aşağıdaki deyimleri ekleyin:

     [!code-csharp[CFX_SelfHost4#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#1)]
     [!code-vb[CFX_SelfHost4#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#1)]

4. Bir hizmet sözleşmesini uygulama ve tanımlayın. Bu örnekte tanımlayan bir `HelloWorldService` giriş hizmete göre bir ileti döndürür.

     [!code-csharp[CFX_SelfHost4#2](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#2)]
     [!code-vb[CFX_SelfHost4#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#2)]

    > [!NOTE]
    > Tanımlaması ve hizmet arabirimi hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir hizmet sözleşmesini tanımlama](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md) ve [nasıl yapılır: bir hizmet sözleşmesini uygulama](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md).

5. Üst kısmındaki `Main` yöntemi, bir örneğini oluşturmak <xref:System.Uri> sınıfı ile hizmet için temel adres.

     [!code-csharp[CFX_SelfHost4#3](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#3)]
     [!code-vb[CFX_SelfHost4#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#3)]

6. Bir örneğini oluşturmak <xref:System.ServiceModel.ServiceHost> geçirme sınıfı, bir <xref:System.Type> temsil eden Tekdüzen Kaynak Tanımlayıcısı (URI) için hizmet türü ve temel adresi <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29>. Meta veri yayımlamayı etkinleştirme ve ardından arama <xref:System.ServiceModel.ICommunicationObject.Open%2A> metodunda <xref:System.ServiceModel.ServiceHost> hizmeti başlatmak ve iletileri almak için hazırlamak üzere.

     [!code-csharp[CFX_SelfHost4#4](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#4)]
     [!code-vb[CFX_SelfHost4#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#4)]

    > [!NOTE]
    > Bu örnek, varsayılan uç noktaları kullanır ve bu hizmet için herhangi bir yapılandırma dosyası gereklidir. Uç nokta yapılandırıldıysa, çalışma zamanı hizmeti tarafından uygulanan her bir hizmet sözleşmesi için her bir temel adres için bir uç nokta oluşturur. Varsayılan uç noktaları hakkında daha fazla bilgi için bkz. [Basitleştirilmiş yapılandırma](../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).

7. Tuşuna **Ctrl**+**Shift**+**B** çözümü derlemek için.

## <a name="test-the-service"></a>Test hizmeti

1. Tuşuna **Ctrl**+**F5** hizmeti çalıştırmak için.

2. Açık **WCF Test istemcisi**.

    > [!TIP]
    > Açmak için **WCF Test istemcisi**, Visual Studio için geliştirici komut istemi açın ve yürütme **WcfTestClient.exe**.

3. Seçin **Hizmet Ekle** gelen **dosya** menüsü.

4. Tür `http://localhost:8080/hello` içine tıklayın ve adres kutusuna **Tamam**.

    > [!TIP]
    > Hizmet çalışıyor; Aksi takdirde bu adımı başarısız olduğundan emin olun. Temel adres kodundaki değiştirdiyseniz, değiştirilmiş temel adresini bu adımı kullanın.

5. Çift **SayHello** altında **hizmet Projelerim** düğümü. İçine adınızı yazın **değer** sütununda **istek** listesinde ve tıklayın **Invoke**.

   Bir yanıt iletisi görünür **yanıt** listesi.

## <a name="example"></a>Örnek

Aşağıdaki örnek, oluşturur bir <xref:System.ServiceModel.ServiceHost> türünde bir hizmet ana bilgisayar nesnesine `HelloWorldService`ve ardından çağırır <xref:System.ServiceModel.ICommunicationObject.Open%2A> metodunda <xref:System.ServiceModel.ServiceHost>. Temel adres kodunda sağlanır, meta veri yayımlama etkin ve varsayılan uç noktaları kullanılır.

[!code-csharp[CFX_SelfHost4#5](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#5)]
[!code-vb[CFX_SelfHost4#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#5)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Uri>
- <xref:System.Configuration.ConfigurationManager.AppSettings%2A>
- <xref:System.Configuration.ConfigurationManager>
- [Nasıl yapılır: IIS'de WCF Hizmeti Barındırma](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)
- [Kendini Barındırma](../../../docs/framework/wcf/samples/self-host.md)
- [Barındırma Hizmetleri](../../../docs/framework/wcf/hosting-services.md)
- [Nasıl yapılır: Bir Hizmet Anlaşması Tanımlama](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)
- [Nasıl yapılır: Bir Hizmet Anlaşmasını Uygulama](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)
- [ServiceModel Meta Veri Yardımcı Programı Aracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [Sistem Tarafından Sağlanan Bağlamalar](../../../docs/framework/wcf/system-provided-bindings.md)