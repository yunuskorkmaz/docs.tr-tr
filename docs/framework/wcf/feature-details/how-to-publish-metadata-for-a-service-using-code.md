---
title: 'Nasıl yapılır: Kod Kullanarak Bir Hizmet için Meta Verileri Yayımlama'
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
ms.assetid: 51407e6d-4d87-42d5-be7c-9887b8652006
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c3d2fd1222539ec8017846069e7eda9a2c503f22
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-publish-metadata-for-a-service-using-code"></a>Nasıl yapılır: Kod Kullanarak Bir Hizmet için Meta Verileri Yayımlama
Bu meta veri yayımlama için ele iki nasıl yapılır konuları biridir bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hizmet. Bir hizmeti bir yapılandırma dosyası kullanarak ve kod kullanarak meta verileri, nasıl yayınlamalıdır belirtmek için iki yolu vardır. Bu konuda, bir kod kullanarak bir hizmet için meta verileri yayımlama gösterilmektedir.  
  
> [!CAUTION]
>  Bu konu, güvenli olmayan bir şekilde meta verileri yayımlama gösterilmektedir. Herhangi bir istemci hizmetinden meta verileri alabilir. Meta veriler güvenli bir şekilde yayımlamak için hizmetinizin gerekiyorsa. bkz: [özel güvenli meta veri uç noktasının](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).  
  
 Yapılandırma dosyasındaki meta veri yayımlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir yapılandırma dosyası kullanarak bir hizmet için meta veri yayımlama](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md). Meta veri yayımlama sağlayan bir WS-aktarımı GET isteği ya da bir HTTP/GET isteği kullanarak kullanarak meta verileri almak istemcileri `?wsdl` sorgu dizesi. Kod, çalıştığından emin olmak için temel bir WCF Hizmeti oluşturmanız gerekir. Temel bir kendi kendini barındıran hizmet aşağıdaki kodu sağlanır.  
  
 [!code-csharp[htPublishMetadataCode#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#0)]
 [!code-vb[htPublishMetadataCode#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#0)]  
  
### <a name="to-publish-metadata-in-code"></a>Kodda metadata yayımlamak için  
  
1.  Bir konsol uygulaması ana yöntem içinde örneği bir <xref:System.ServiceModel.ServiceHost> hizmet türü ve taban adresi geçirerek nesnesi.  
  
     [!code-csharp[htPublishMetadataCode#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#1)]
     [!code-vb[htPublishMetadataCode#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#1)]  
  
2.  Try bloğunun hemen altındaki 1. adım için kod oluşturur, bu hizmet çalışırken oluşan tüm özel durumları yakalar.  
  
     [!code-csharp[htPublishMetadataCode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#2)]
     [!code-vb[htPublishMetadataCode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#2)]  
  
     [!code-csharp[htPublishMetadataCode#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#3)]
     [!code-vb[htPublishMetadataCode#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#3)]  
  
3.  Hizmet ana bilgisayarı zaten bulunup bulunmadığını denetleyin bir <xref:System.ServiceModel.Description.ServiceMetadataBehavior>, aksi takdirde, yeni bir <xref:System.ServiceModel.Description.ServiceMetadataBehavior> örneği.  
  
     [!code-csharp[htPublishMetadataCode#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#4)]
     [!code-vb[htPublishMetadataCode#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#4)]  
  
4.  Ayarlama <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> özelliği `true.`  
  
     [!code-csharp[htPublishMetadataCode#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#5)]
     [!code-vb[htPublishMetadataCode#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#5)]  
  
5.  <xref:System.ServiceModel.Description.ServiceMetadataBehavior> İçeren bir <xref:System.ServiceModel.Description.MetadataExporter> özelliği. <xref:System.ServiceModel.Description.MetadataExporter> İçeren bir <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> özelliği. Değerini <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> özelliğine <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A>. <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> Özelliği de ayarlanabilir <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A>. Ayarlandığında <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> meta verileri dışarı aktarma ilkesi bilgileri meta verileri ile oluşturur, "WS-Policy 1.5 uyumlu. Ayarlandığında <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A> meta verileri dışarı aktarma WS-Policy 1.2 uyumlu ilke bilgilerini oluşturur.  
  
     [!code-csharp[htPublishMetadataCode#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#6)]
     [!code-vb[htPublishMetadataCode#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#6)]  
  
6.  Ekleme <xref:System.ServiceModel.Description.ServiceMetadataBehavior> hizmet ana bilgisayarın davranışları koleksiyonuna örneği.  
  
     [!code-csharp[htPublishMetadataCode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#7)]
     [!code-vb[htPublishMetadataCode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#7)]  
  
7.  Meta veri exchange uç noktası hizmeti konak ekleyin.  
  
     [!code-csharp[htPublishMetadataCode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#8)]
     [!code-vb[htPublishMetadataCode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#8)]  
  
8.  Uygulama uç hizmeti konak ekleyin.  
  
     [!code-csharp[htPublishMetadataCode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#9)]
     [!code-vb[htPublishMetadataCode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#9)]  
  
    > [!NOTE]
    >  Hizmeti için uç nokta eklemezseniz çalışma zamanı varsayılan uç noktaları ekler. Bu örnekte, hizmetin sahip olduğu bir <xref:System.ServiceModel.Description.ServiceMetadataBehavior> kümesine `true`, hizmetin etkin meta veri yayımlama vardır. Varsayılan uç noktalar hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
9. Hizmet ana bilgisayarı'nı açın ve gelen çağrıları için bekleyin. Kullanıcı ENTER tuşuna bastığında hizmet ana bilgisayarını kapatın.  
  
     [!code-csharp[htPublishMetadataCode#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#10)]
     [!code-vb[htPublishMetadataCode#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#10)]  
  
10. Derleme ve konsol uygulamasını çalıştırın.  
  
11. Hizmetin taban adresine göz atmak için Internet Explorer kullanın (http://localhost:8001/MetadataSample Bu örnekte) ve meta veri yayımlama açık olduğunu doğrulayın. En üstte ve hemen altında "Bir hizmet oluşturdunuz." bir Web görüntülenen "Basit hizmeti" diyen sayfasını görmeniz gerekir Değilse, sayfanın üst kısmındaki ortaya çıkan bir ileti görüntüler: "Bu hizmet için meta veri yayımlama şu anda devre dışı."  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği temel bir gösterir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kod içinde hizmet için meta veriler yayımlar hizmet.  
  
 [!code-csharp[htPublishMetadataCode#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#11)]
 [!code-vb[htPublishMetadataCode#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#11)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Yönetilen Bir Uygulamada Bir WCF Hizmeti Barındırma](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)  
 [Kendini Barındırma](../../../../docs/framework/wcf/samples/self-host.md)  
 [Meta Veri Mimarisine Genel Bakış](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)  
 [Meta Verileri Kullanma](../../../../docs/framework/wcf/feature-details/using-metadata.md)  
 [Nasıl yapılır: Yapılandırma Dosyası Kullanarak Bir Hizmet için Meta Verileri Yayımlama](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
