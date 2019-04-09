---
title: 'Nasıl yapılır: Kod Kullanarak Bir Hizmet için Meta Verileri Yayımlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 51407e6d-4d87-42d5-be7c-9887b8652006
ms.openlocfilehash: 5c17f5c399335a2c7cbcc6f4474982de591dd453
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59098009"
---
# <a name="how-to-publish-metadata-for-a-service-using-code"></a>Nasıl yapılır: Kod Kullanarak Bir Hizmet için Meta Verileri Yayımlama
Bu, bir Windows Communication Foundation (WCF) hizmet için meta verileri yayımlama tartışmak iki nasıl yapılır konuları biridir. Hizmet yapılandırma dosyasını ve kod kullanarak meta verileri nasıl yayımlamalısınız belirtmenin iki yolu vardır. Bu konuda, bir kod kullanarak bir hizmet için meta verileri yayımlama gösterilmektedir.  
  
> [!CAUTION]
>  Bu konu, güvenli bir şekilde meta verileri yayımlama gösterilmektedir. Herhangi bir istemci hizmet meta verileri alabilir. Meta verileri güvenli bir şekilde yayımlamak için hizmetinize gerekiyorsa. bkz: [özel güvenli meta veri uç noktası](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).  
  
 Bir yapılandırma dosyasında meta verileri yayımlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: Bir yapılandırma dosyası kullanarak bir hizmet için meta verileri yayımlama](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md). Meta veri yayımlama sağlayan bir WS aktarım GET isteği ya da bir HTTP/GET isteği kullanılarak kullanarak meta verileri almak istemcileri `?wsdl` sorgu dizesi. Kod, çalıştığından emin olmak için temel bir WCF Hizmeti oluşturmanız gerekir. Temel bir şirket içinde barındırılan hizmeti, aşağıdaki kodda sağlanır.  
  
 [!code-csharp[htPublishMetadataCode#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#0)]
 [!code-vb[htPublishMetadataCode#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#0)]  
  
### <a name="to-publish-metadata-in-code"></a>Kodda meta verileri yayımlama  
  
1.  Konsol uygulamasının ana yöntemi içinde örneği bir <xref:System.ServiceModel.ServiceHost> nesnesini geçirerek hizmet türü ve temel adres.  
  
     [!code-csharp[htPublishMetadataCode#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#1)]
     [!code-vb[htPublishMetadataCode#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#1)]  
  
2.  1. adım için kodun hemen altına bir try bloğu oluşturur, bu hizmet çalışırken oluşan herhangi bir özel durumu yakalar.  
  
     [!code-csharp[htPublishMetadataCode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#2)]
     [!code-vb[htPublishMetadataCode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#2)]  
  
     [!code-csharp[htPublishMetadataCode#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#3)]
     [!code-vb[htPublishMetadataCode#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#3)]  
  
3.  Hizmet ana bilgisayarı zaten içerip içermediğini görmek için onay bir <xref:System.ServiceModel.Description.ServiceMetadataBehavior>, aksi takdirde, yeni bir <xref:System.ServiceModel.Description.ServiceMetadataBehavior> örneği.  
  
     [!code-csharp[htPublishMetadataCode#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#4)]
     [!code-vb[htPublishMetadataCode#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#4)]  
  
4.  Ayarlama <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> özelliği `true.`  
  
     [!code-csharp[htPublishMetadataCode#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#5)]
     [!code-vb[htPublishMetadataCode#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#5)]  
  
5.  <xref:System.ServiceModel.Description.ServiceMetadataBehavior> İçeren bir <xref:System.ServiceModel.Description.MetadataExporter> özelliği. <xref:System.ServiceModel.Description.MetadataExporter> İçeren bir <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> özelliği. Değerini <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> özelliğini <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A>. <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> Özelliği de ayarlanabilir <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A>. Ayarlandığında <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> meta verileri dışarı Aktarıcı meta verilerle ilke bilgilerini oluşturur, "için WS-Policy 1.5 uyar. Ayarlandığında <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A> meta verileri dışarı Aktarıcı WS-Policy 1.2 uyan ilke bilgilerini oluşturur.  
  
     [!code-csharp[htPublishMetadataCode#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#6)]
     [!code-vb[htPublishMetadataCode#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#6)]  
  
6.  Ekleme <xref:System.ServiceModel.Description.ServiceMetadataBehavior> örneğine hizmet ana bilgisayarın davranışları koleksiyonu.  
  
     [!code-csharp[htPublishMetadataCode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#7)]
     [!code-vb[htPublishMetadataCode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#7)]  
  
7.  Meta veri değişimi uç noktası için hizmet ana bilgisayarı ekleyin.  
  
     [!code-csharp[htPublishMetadataCode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#8)]
     [!code-vb[htPublishMetadataCode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#8)]  
  
8.  Bir uygulama uç noktası için hizmet ana bilgisayarı ekleyin.  
  
     [!code-csharp[htPublishMetadataCode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#9)]
     [!code-vb[htPublishMetadataCode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#9)]  
  
    > [!NOTE]
    >  Hizmet için uç nokta eklemezseniz, çalışma zamanı varsayılan uç noktalar ekler. Bu örnekte, hizmetin sahip olduğu bir <xref:System.ServiceModel.Description.ServiceMetadataBehavior> kümesine `true`, hizmetin etkin meta veri yayımlama vardır. Varsayılan uç noktaları hakkında daha fazla bilgi için bkz. [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
9. Hizmet ana bilgisayarı'nı açın ve gelen çağrılar için bekleyin. Kullanıcı ENTER tuşuna bastığında hizmet ana bilgisayarını kapatın.  
  
     [!code-csharp[htPublishMetadataCode#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#10)]
     [!code-vb[htPublishMetadataCode#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#10)]  
  
10. Konsol uygulamasını derleyin ve çalıştırın.  
  
11. Hizmetin taban adresine göz atmak için Internet Explorer'ı kullanın (http://localhost:8001/MetadataSample Bu örnekte) ve meta veri yayımlama açık olduğunu doğrulayın. Üst ve hemen "Bir hizmet oluşturdunuz." altında "Basit hizmeti" ifadesini içeren Web görüntülenen sayfası görmeniz gerekir Aksi durumda, sonuçta elde edilen sayfanın üst kısmındaki bir ileti görüntüler: "Bu hizmet için meta veri yayımlama şu anda devre dışı bırakıldı."  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, kod içinde hizmet meta verilerini yayımlayan temel bir WCF Hizmeti uygulamasını gösterir.  
  
 [!code-csharp[htPublishMetadataCode#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#11)]
 [!code-vb[htPublishMetadataCode#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#11)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Yönetilen Bir Uygulamada Bir WCF Hizmeti Barındırma](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)
- [Kendini Barındırma](../../../../docs/framework/wcf/samples/self-host.md)
- [Meta Veri Mimarisi Genel Bakış](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)
- [Meta Verileri Kullanma](../../../../docs/framework/wcf/feature-details/using-metadata.md)
- [Nasıl yapılır: Yapılandırma Dosyası Kullanarak Bir Hizmet için Meta Verileri Yayımlama](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
