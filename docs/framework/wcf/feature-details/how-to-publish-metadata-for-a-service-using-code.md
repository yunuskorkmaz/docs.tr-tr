---
title: 'Nasıl yapılır: Kod Kullanarak Bir Hizmet için Meta Verileri Yayımlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 51407e6d-4d87-42d5-be7c-9887b8652006
ms.openlocfilehash: 9239e8bd9b85986d41006c4b2a21b6f2304e8275
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601237"
---
# <a name="how-to-publish-metadata-for-a-service-using-code"></a>Nasıl yapılır: Kod Kullanarak Bir Hizmet için Meta Verileri Yayımlama
Bu, bir Windows Communication Foundation (WCF) hizmeti için yayımlama meta verilerini tartışan iki nasıl yapılır konuktan biridir. Bir hizmetin bir yapılandırma dosyası kullanarak ve kod kullanarak meta verileri nasıl yayımlayacağınızı belirten iki yol vardır. Bu konu, kod kullanarak bir hizmet için meta verilerin nasıl yayımlanacağını göstermektedir.  
  
> [!CAUTION]
> Bu konuda, meta verilerin güvensiz bir şekilde nasıl yayımlanacağı gösterilmektedir. Tüm istemciler, hizmetten meta verileri alabilir. Hizmetinizin meta verileri güvenli bir şekilde yayımlamasını istiyorsanız. bkz. [özel güvenli meta veri uç noktası](../samples/custom-secure-metadata-endpoint.md).  
  
 Bir yapılandırma dosyasında meta verileri yayımlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: yapılandırma dosyası kullanarak bir hizmet Için meta verileri yayımlama](how-to-publish-metadata-for-a-service-using-a-configuration-file.md). Meta veri yayımlama, istemcilerin bir WS-transfer GET isteği veya sorgu dizesini kullanarak bir HTTP/GET isteği kullanarak meta verileri almasına izin verir `?wsdl` . Kodun çalıştığından emin olmak için temel bir WCF hizmeti oluşturmanız gerekir. Aşağıdaki kodda temel bir kendini barındıran hizmet sağlanır.  
  
 [!code-csharp[htPublishMetadataCode#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#0)]
 [!code-vb[htPublishMetadataCode#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#0)]  
  
### <a name="to-publish-metadata-in-code"></a>Meta verileri kodda yayınlamak için  
  
1. Konsol uygulamasının Main yönteminde, <xref:System.ServiceModel.ServiceHost> hizmet türünü ve temel adresi geçirerek bir nesnesi örneği oluşturun.  
  
     [!code-csharp[htPublishMetadataCode#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#1)]
     [!code-vb[htPublishMetadataCode#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#1)]  
  
2. 1. adım için kodun hemen altında bir try bloğu oluşturun, bu, hizmet çalışırken oluşturulan tüm özel durumları yakalar.  
  
     [!code-csharp[htPublishMetadataCode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#2)]
     [!code-vb[htPublishMetadataCode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#2)]  
  
     [!code-csharp[htPublishMetadataCode#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#3)]
     [!code-vb[htPublishMetadataCode#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#3)]  
  
3. Hizmet ana bilgisayarının zaten bir içerip içermediğini denetleyin, yoksa <xref:System.ServiceModel.Description.ServiceMetadataBehavior> Yeni bir <xref:System.ServiceModel.Description.ServiceMetadataBehavior> örnek oluşturun.  
  
     [!code-csharp[htPublishMetadataCode#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#4)]
     [!code-vb[htPublishMetadataCode#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#4)]  
  
4. <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A>Özelliğini olarak ayarlayın`true.`  
  
     [!code-csharp[htPublishMetadataCode#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#5)]
     [!code-vb[htPublishMetadataCode#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#5)]  
  
5. , <xref:System.ServiceModel.Description.ServiceMetadataBehavior> Bir <xref:System.ServiceModel.Description.MetadataExporter> özelliği içerir. , <xref:System.ServiceModel.Description.MetadataExporter> Bir <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> özelliği içerir. <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A>Özelliğinin değerini olarak ayarlayın <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> . <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A>Özelliği de olarak ayarlanabilir <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A> . <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A>Meta veri aktarıcı olarak ayarlandığında, "ws-policy 1,5 ' a uyan meta verilerle ilke bilgilerini oluşturur. <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A>Meta veri aktarıcı olarak ayarlandığında, WS-policy 1,2 'e uyan ilke bilgilerini oluşturur.  
  
     [!code-csharp[htPublishMetadataCode#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#6)]
     [!code-vb[htPublishMetadataCode#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#6)]  
  
6. <xref:System.ServiceModel.Description.ServiceMetadataBehavior>Örneği hizmet ana bilgisayarının davranış koleksiyonuna ekleyin.  
  
     [!code-csharp[htPublishMetadataCode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#7)]
     [!code-vb[htPublishMetadataCode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#7)]  
  
7. Meta veri değişimi uç noktasını hizmet ana bilgisayarına ekleyin.  
  
     [!code-csharp[htPublishMetadataCode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#8)]
     [!code-vb[htPublishMetadataCode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#8)]  
  
8. Hizmet ana bilgisayarına bir uygulama uç noktası ekleyin.  
  
     [!code-csharp[htPublishMetadataCode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#9)]
     [!code-vb[htPublishMetadataCode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#9)]  
  
    > [!NOTE]
    > Hizmete herhangi bir uç nokta eklemediğiniz takdirde, çalışma zamanı sizin için varsayılan uç noktaları ekler. Bu örnekte, hizmetin <xref:System.ServiceModel.Description.ServiceMetadataBehavior> olarak ayarlanmış olması nedeniyle `true` , hizmette yayımlama meta verileri etkindir. Varsayılan uç noktalar hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../simplified-configuration.md) ve Basitleştirilmiş yapılandırma.  
  
9. Hizmet konağını açın ve gelen çağrıları bekleyin. Kullanıcı ENTER tuşuna bastığında hizmet konağını kapatın.  
  
     [!code-csharp[htPublishMetadataCode#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#10)]
     [!code-vb[htPublishMetadataCode#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#10)]  
  
10. Konsol uygulamasını derleyin ve çalıştırın.  
  
11. Internet Explorer 'ı kullanarak hizmetin temel adresine gidin ( `http://localhost:8001/MetadataSample` Bu örnekte) ve meta veri yayımlamanın açık olduğunu doğrulayın. En üstte "basit hizmet" ve hemen aşağıda "bir hizmet oluşturdunuz" ifadesinin görüntülendiğini belirten bir Web sayfası görmeniz gerekir. Aksi takdirde, sonuçta ortaya çıkan sayfanın en üstündeki bir ileti şunu görüntüler: "Bu hizmet için meta veri yayımlama Şu anda devre dışı."  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, kodda hizmet için meta veriler yayımlayan temel bir WCF hizmeti uygulamasını gösterir.  
  
 [!code-csharp[htPublishMetadataCode#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#11)]
 [!code-vb[htPublishMetadataCode#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#11)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Yönetilen Bir Uygulamada Bir WCF Hizmeti Barındırma](../how-to-host-a-wcf-service-in-a-managed-application.md)
- [Kendini Barındırma](../samples/self-host.md)
- [Meta Veri Mimarisi Genel Bakış](metadata-architecture-overview.md)
- [Meta Verileri Kullanma](using-metadata.md)
- [Nasıl yapılır: Yapılandırma Dosyası Kullanarak Bir Hizmet için Meta Verileri Yayımlama](how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
