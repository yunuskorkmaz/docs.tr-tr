---
title: 'Nasıl yapılır: Yönetilen Bir Uygulamada Bir WCF Hizmeti Barındırma'
description: Şirket içinde barındırılan bir hizmet oluşturarak ve test ederek, yönetilen bir uygulama içinde bir WCF hizmetini nasıl barındıracağınızı öğrenin.
ms.date: 09/17/2018
dev_langs:
- csharp
- vb
ms.assetid: 5eb29db0-b6dc-4e77-8c68-0a62f79d743b
ms.openlocfilehash: 7d1d61b683f60a6c643d2a2f03d367a6ae6c6c15
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246174"
---
# <a name="how-to-host-a-wcf-service-in-a-managed-app"></a>Nasıl yapılır: yönetilen bir uygulamada bir WCF hizmetini barındırma

Yönetilen bir uygulama içinde bir hizmeti barındırmak için, hizmetin kodunu yönetilen uygulama kodu içine ekleyin, hizmet için bir uç nokta tanımlayın, yapılandırma yoluyla veya varsayılan uç noktaları kullanarak, bir örneği oluşturun <xref:System.ServiceModel.ServiceHost> .

İleti almaya başlamak için üzerinde öğesini <xref:System.ServiceModel.ICommunicationObject.Open%2A> çağırın <xref:System.ServiceModel.ServiceHost> . Bu, hizmet için dinleyiciyi oluşturur ve açar. Bir hizmetin bu şekilde barındırılması, yönetilen uygulama barındırma işinin kendisini yaptığından, genellikle "kendiliğinden barındırma" olarak adlandırılır. Hizmeti kapatmak için üzerinde öğesini çağırın <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> <xref:System.ServiceModel.ServiceHost> .

Bir hizmet Ayrıca, yönetilen bir Windows hizmetinde, Internet Information Services (IIS) veya Windows Işlem etkinleştirme hizmeti 'nde (WAS) barındırılabilir. Bir hizmet için barındırma seçenekleri hakkında daha fazla bilgi için bkz. [barındırma hizmetleri](hosting-services.md).

Dağıtım için en az altyapıyı gerektirdiğinden, yönetilen bir uygulamada bir hizmetin barındırılması en esnek seçenektir. Yönetilen uygulamalarda barındırma hizmetleri hakkında daha fazla bilgi için bkz. [yönetilen bir uygulamada barındırma](./feature-details/hosting-in-a-managed-application.md).

Aşağıdaki yordamda, bir konsol uygulamasında şirket içinde barındırılan bir hizmetin nasıl uygulanacağı gösterilmiştir.

## <a name="create-a-self-hosted-service"></a>Şirket içinde barındırılan hizmet oluşturma

1. Yeni bir konsol uygulaması oluşturun:

   1. Visual Studio 'yu açın ve **New**  >  **Dosya** menüsünden Yeni**Proje** ' yi seçin.

   2. **Yüklü şablonlar** listesinde, **Visual C#** veya **Visual Basic**seçin ve ardından **Windows Masaüstü**' nü seçin.

   3. **Konsol uygulaması** şablonunu seçin. `SelfHost` **Ad** kutusuna yazın ve ardından **Tamam**' ı seçin.

2. **Çözüm Gezgini** ' de **Selfhost** ' a sağ tıklayın ve **Başvuru Ekle**' yi seçin. **.Net** sekmesinden **System. ServiceModel** ' i seçin ve ardından **Tamam**' ı seçin.

    > [!TIP]
    > **Çözüm Gezgini** penceresi görünmüyorsa, **Görünüm** menüsünden **Çözüm Gezgini** ' i seçin.

3. Zaten açık değilse, kod penceresinde açmak için **Çözüm Gezgini** içinde **program.cs** veya **Module1. vb** öğesine çift tıklayın. Aşağıdaki deyimlerini dosyanın üst kısmına ekleyin:

     [!code-csharp[CFX_SelfHost4#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#1)]
     [!code-vb[CFX_SelfHost4#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#1)]

4. Hizmet sözleşmesi tanımlama ve uygulama. Bu örnek, `HelloWorldService` hizmete girişe dayalı bir ileti döndüren bir tanımlar.

     [!code-csharp[CFX_SelfHost4#2](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#2)]
     [!code-vb[CFX_SelfHost4#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#2)]

    > [!NOTE]
    > Bir hizmet arabirimini tanımlama ve uygulama hakkında daha fazla bilgi için bkz. [nasıl yapılır: hizmet sözleşmesi tanımlama](how-to-define-a-wcf-service-contract.md) ve [nasıl yapılır: hizmet sözleşmesi uygulama](how-to-implement-a-wcf-contract.md).

5. Yönteminin en üstünde `Main` , <xref:System.Uri> hizmetin temel adresiyle sınıfının bir örneğini oluşturun.

     [!code-csharp[CFX_SelfHost4#3](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#3)]
     [!code-vb[CFX_SelfHost4#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#3)]

6. Sınıfının bir örneğini oluşturun <xref:System.ServiceModel.ServiceHost> <xref:System.Type> ve hizmet türünü ve temel adres Tekdüzen Kaynak tanımlayıcısını (URI) temsil eder <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29> . Meta veri yayımlamayı etkinleştirin ve sonra <xref:System.ServiceModel.ICommunicationObject.Open%2A> <xref:System.ServiceModel.ServiceHost> hizmeti başlatmak ve iletiyi almak üzere hazırlamak için üzerinde yöntemini çağırın.

     [!code-csharp[CFX_SelfHost4#4](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#4)]
     [!code-vb[CFX_SelfHost4#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#4)]

    > [!NOTE]
    > Bu örnek, varsayılan uç noktaları kullanır ve bu hizmet için hiçbir yapılandırma dosyası gerekli değildir. Hiçbir uç nokta yapılandırılmamışsa, çalışma zamanı, hizmet tarafından uygulanan her bir hizmet sözleşmesinin her bir temel adresi için bir uç nokta oluşturur. Varsayılan uç noktalar hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](./samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](simplified-configuration.md) ve Basitleştirilmiş yapılandırma.

7. **Ctrl** + **Shift** + Çözümü derlemek için CTRL SHIFT**B** tuşlarına basın.

## <a name="test-the-service"></a>Hizmeti test etme

1. **Ctrl** + Hizmeti çalıştırmak için CTRL**F5** tuşuna basın.

2. **WCF Test istemcisi**'ni açın.

    > [!TIP]
    > **WCF test istemcisini**açmak Için, Visual Studio için geliştirici komut istemi açın ve **WcfTestClient.exe**yürütün.

3. **Dosya** menüsünden **Hizmet Ekle** ' yi seçin.

4. `http://localhost:8080/hello`Adres kutusuna yazın ve **Tamam**' a tıklayın.

    > [!TIP]
    > Hizmetin çalıştığından emin olun, aksi takdirde bu adım başarısız olur. Koddaki temel adresi değiştirdiyseniz, bu adımda değiştirilen temel adresi kullanın.

5. **Hizmet projeleri** düğümünün altında **SayHello** ' ya çift tıklayın. **İstek** listesindeki **değer** sütununa adınızı yazın ve **çağır**' a tıklayın.

   **Yanıt** listesinde bir yanıt iletisi görüntülenir.

## <a name="example"></a>Örnek

Aşağıdaki örnek <xref:System.ServiceModel.ServiceHost> , türünde bir hizmeti barındırmak için bir nesnesi oluşturur `HelloWorldService` ve sonra <xref:System.ServiceModel.ICommunicationObject.Open%2A> yöntemi ' de çağırır <xref:System.ServiceModel.ServiceHost> . Kodda bir temel adres sağlanır, meta veri yayımlama etkindir ve varsayılan uç noktalar kullanılır.

[!code-csharp[CFX_SelfHost4#5](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#5)]
[!code-vb[CFX_SelfHost4#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#5)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Uri>
- <xref:System.Configuration.ConfigurationManager.AppSettings%2A>
- <xref:System.Configuration.ConfigurationManager>
- [Nasıl yapılır: IIS'de WCF Hizmeti Barındırma](./feature-details/how-to-host-a-wcf-service-in-iis.md)
- [Kendini Barındırma](./samples/self-host.md)
- [Barındırma Hizmetleri](hosting-services.md)
- [Nasıl yapılır: Bir Hizmet Anlaşması Tanımlama](how-to-define-a-wcf-service-contract.md)
- [Nasıl yapılır: Bir Hizmet Anlaşmasını Uygulama](how-to-implement-a-wcf-contract.md)
- [ServiceModel Meta Veri Yardımcı Programracı (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](using-bindings-to-configure-services-and-clients.md)
- [Sistem tarafından sağlanmış bağlamalar](system-provided-bindings.md)
