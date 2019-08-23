---
title: 'Nasıl yapılır: Kod Kullanarak Bir Hizmet için Meta Verileri Yayımlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 51407e6d-4d87-42d5-be7c-9887b8652006
ms.openlocfilehash: 5f60bcdb02f61d39711115b07ba989229e39c28c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929138"
---
# <a name="how-to-publish-metadata-for-a-service-using-code"></a>Nasıl yapılır: Kod Kullanarak Bir Hizmet için Meta Verileri Yayımlama
Bu, bir Windows Communication Foundation (WCF) hizmeti için yayımlama meta verilerini tartışan iki nasıl yapılır konuktan biridir. Bir hizmetin bir yapılandırma dosyası kullanarak ve kod kullanarak meta verileri nasıl yayımlayacağınızı belirten iki yol vardır. Bu konu, kod kullanarak bir hizmet için meta verilerin nasıl yayımlanacağını göstermektedir.  
  
> [!CAUTION]
>  Bu konuda, meta verilerin güvensiz bir şekilde nasıl yayımlanacağı gösterilmektedir. Tüm istemciler, hizmetten meta verileri alabilir. Hizmetinizin meta verileri güvenli bir şekilde yayımlamasını istiyorsanız. bkz. [özel güvenli meta veri uç noktası](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).  
  
 Bir yapılandırma dosyasında meta verileri yayımlama hakkında daha fazla bilgi için bkz [. nasıl yapılır: Yapılandırma dosyası](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)kullanarak bir hizmet için meta verileri yayımlayın. Meta veri yayımlama, `?wsdl` istemcilerin bir ws-Transfer get isteği veya sorgu dizesini kullanarak bir http/get isteği kullanarak meta verileri almasına izin verir. Kodun çalıştığından emin olmak için temel bir WCF hizmeti oluşturmanız gerekir. Aşağıdaki kodda temel bir kendini barındıran hizmet sağlanır.  
  
 [!code-csharp[htPublishMetadataCode#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#0)]
 [!code-vb[htPublishMetadataCode#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#0)]  
  
### <a name="to-publish-metadata-in-code"></a>Meta verileri kodda yayınlamak için  
  
1. Konsol uygulamasının Main yönteminde, hizmet türünü ve temel adresi geçirerek <xref:System.ServiceModel.ServiceHost> bir nesnesi örneği oluşturun.  
  
     [!code-csharp[htPublishMetadataCode#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#1)]
     [!code-vb[htPublishMetadataCode#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#1)]  
  
2. 1\. adım için kodun hemen altında bir try bloğu oluşturun, bu, hizmet çalışırken oluşturulan tüm özel durumları yakalar.  
  
     [!code-csharp[htPublishMetadataCode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#2)]
     [!code-vb[htPublishMetadataCode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#2)]  
  
     [!code-csharp[htPublishMetadataCode#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#3)]
     [!code-vb[htPublishMetadataCode#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#3)]  
  
3. Hizmet ana bilgisayarının zaten bir <xref:System.ServiceModel.Description.ServiceMetadataBehavior>içerip içermediğini denetleyin, yoksa yeni <xref:System.ServiceModel.Description.ServiceMetadataBehavior> bir örnek oluşturun.  
  
     [!code-csharp[htPublishMetadataCode#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#4)]
     [!code-vb[htPublishMetadataCode#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#4)]  
  
4. <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> Özelliğini olarak ayarlayın`true.`  
  
     [!code-csharp[htPublishMetadataCode#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#5)]
     [!code-vb[htPublishMetadataCode#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#5)]  
  
5. , <xref:System.ServiceModel.Description.ServiceMetadataBehavior> Bir<xref:System.ServiceModel.Description.MetadataExporter> özelliği içerir. , <xref:System.ServiceModel.Description.MetadataExporter> Bir<xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> özelliği içerir. <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> Özelliğinin değerini olarak <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A>ayarlayın. Özelliği de olarak <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A>ayarlanabilir. <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> Meta veri aktarıcı <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> olarak ayarlandığında, "ws-Policy 1,5 ' a uyan meta verilerle ilke bilgilerini oluşturur. Meta veri aktarıcı <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A> olarak ayarlandığında, WS-Policy 1,2 'e uyan ilke bilgilerini oluşturur.  
  
     [!code-csharp[htPublishMetadataCode#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#6)]
     [!code-vb[htPublishMetadataCode#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#6)]  
  
6. <xref:System.ServiceModel.Description.ServiceMetadataBehavior> Örneği hizmet ana bilgisayarının davranış koleksiyonuna ekleyin.  
  
     [!code-csharp[htPublishMetadataCode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#7)]
     [!code-vb[htPublishMetadataCode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#7)]  
  
7. Meta veri değişimi uç noktasını hizmet ana bilgisayarına ekleyin.  
  
     [!code-csharp[htPublishMetadataCode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#8)]
     [!code-vb[htPublishMetadataCode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#8)]  
  
8. Hizmet ana bilgisayarına bir uygulama uç noktası ekleyin.  
  
     [!code-csharp[htPublishMetadataCode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#9)]
     [!code-vb[htPublishMetadataCode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#9)]  
  
    > [!NOTE]
    > Hizmete herhangi bir uç nokta eklemediğiniz takdirde, çalışma zamanı sizin için varsayılan uç noktaları ekler. Bu örnekte, hizmetin <xref:System.ServiceModel.Description.ServiceMetadataBehavior> olarak `true`ayarlanmış olması nedeniyle, hizmette yayımlama meta verileri etkindir. Varsayılan uç noktalar hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.  
  
9. Hizmet konağını açın ve gelen çağrıları bekleyin. Kullanıcı ENTER tuşuna bastığında hizmet konağını kapatın.  
  
     [!code-csharp[htPublishMetadataCode#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#10)]
     [!code-vb[htPublishMetadataCode#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#10)]  
  
10. Konsol uygulamasını derleyin ve çalıştırın.  
  
11. Internet Explorer 'ı kullanarak hizmetin temel adresine gidin (http://localhost:8001/MetadataSample Bu örnekte) ve meta veri yayımlamanın açık olduğunu doğrulayın. En üstte "basit hizmet" ve hemen aşağıda "bir hizmet oluşturdunuz" ifadesinin görüntülendiğini belirten bir Web sayfası görmeniz gerekir. Aksi takdirde, ortaya çıkan sayfanın en üstündeki bir ileti şunu görüntüler: "Bu hizmet için meta veri yayımlama Şu anda devre dışı."  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, kodda hizmet için meta veriler yayımlayan temel bir WCF hizmeti uygulamasını gösterir.  
  
 [!code-csharp[htPublishMetadataCode#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#11)]
 [!code-vb[htPublishMetadataCode#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#11)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Yönetilen bir uygulamada bir WCF hizmeti barındırma](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)
- [Kendini Barındırma](../../../../docs/framework/wcf/samples/self-host.md)
- [Meta Veri Mimarisine Genel Bakış](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)
- [Meta Verileri Kullanma](../../../../docs/framework/wcf/feature-details/using-metadata.md)
- [Nasıl yapılır: Yapılandırma dosyası kullanarak bir hizmet için meta verileri yayımlama](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
