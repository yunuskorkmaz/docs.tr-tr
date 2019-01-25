---
title: 'Nasıl yapılır: Hizmet uç noktalarından meta verileri dışarı aktarma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b6c4dfd0-f270-43ec-961a-e16eb6af2f2c
ms.openlocfilehash: 86ad062f7b7ee3dd2927f8b5b103adfd719a963d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54530003"
---
# <a name="how-to-export-metadata-from-service-endpoints"></a>Nasıl yapılır: Hizmet uç noktalarından meta verileri dışarı aktarma
Bu konu, hizmet uç noktalarından meta verileri dışarı aktarma açıklar.  
  
### <a name="to-export-metadata-from-service-endpoints"></a>Hizmet uç noktalarından meta verileri dışarı aktarmak için  
  
1.  Yeni Visual Studio konsol uygulama projesi oluşturun. Aşağıdaki adımlarda oluşturulan Program.cs dosyasındaki ana() yöntemi içinde gösterilen kodu ekleyin.  
  
2.  Oluşturma bir <xref:System.ServiceModel.Description.WsdlExporter>.  
  
     [!code-csharp[S_UEWsdlExporter#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#1)]
     [!code-vb[S_UEWsdlExporter#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#1)]  
  
3.  Ayarlama <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> özellik değerlerinden birine <xref:System.ServiceModel.Description.PolicyVersion> sabit listesi. Bu örnek değeri ayarlar <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> WS-Policy 1.5 sürümüne karşılık gelir.  
  
     [!code-csharp[S_UEWsdlExporter#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#2)]
     [!code-vb[S_UEWsdlExporter#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#2)]  
  
4.  Bir dizi oluşturma <xref:System.ServiceModel.Description.ServiceEndpoint> nesneleri.  
  
     [!code-csharp[S_UEWsdlExporter#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#3)]
     [!code-vb[S_UEWsdlExporter#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#3)]  
  
5.  Her hizmet uç noktası için meta verileri dışarı aktarın.  
  
     [!code-csharp[S_UEWsdlExporter#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#4)]
     [!code-vb[S_UEWsdlExporter#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#4)]  
  
6.  Dışarı aktarma işlemi sırasında bir hata oluşmamıştır emin olun ve meta verilerini almak için bu seçeneği işaretleyin.  
  
     [!code-csharp[S_UEWsdlExporter#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#5)]
     [!code-vb[S_UEWsdlExporter#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#5)]  
  
7.  Artık meta çağırarak bir dosyaya yazmak gibi kullanabileceğiniz <xref:System.ServiceModel.Description.MetadataSet.WriteTo%28System.Xml.XmlWriter%29> yöntemi.  
  
## <a name="example"></a>Örnek  
 Bu örnek için listeleme tam kod aşağıda verilmiştir.  
  
 [!code-csharp[S_UEWsdlExporter#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#0)]
 [!code-vb[S_UEWsdlExporter#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#0)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Program.cs başvuru System.ServiceModel.dll derlenirken.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Meta Veri Mimarisine Genel Bakış](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)
- [Meta Verileri Kullanma](../../../../docs/framework/wcf/feature-details/using-metadata.md)
- [Uç noktalar: Adresleri, bağlamalar ve sözleşmeler](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
