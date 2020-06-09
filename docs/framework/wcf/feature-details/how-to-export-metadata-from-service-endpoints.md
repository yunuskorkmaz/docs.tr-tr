---
title: 'Nasıl yapılır: Hizmet Uç Noktalarından Meta Verileri Dışa Aktarma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b6c4dfd0-f270-43ec-961a-e16eb6af2f2c
ms.openlocfilehash: 58e86e5566775048e081bfb4ac217a7747b98a35
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579416"
---
# <a name="how-to-export-metadata-from-service-endpoints"></a>Nasıl yapılır: Hizmet Uç Noktalarından Meta Verileri Dışa Aktarma
Bu konuda, hizmet uç noktalarından meta verilerin nasıl dışarı aktarılacağı açıklanmaktadır.  
  
### <a name="to-export-metadata-from-service-endpoints"></a>Meta verileri hizmet uç noktalarından dışarı aktarmak için  
  
1. Yeni bir Visual Studio konsol uygulaması projesi oluşturun. Main () yönteminde oluşturulan Program.cs dosyasına aşağıdaki adımlarda gösterilen kodu ekleyin.  
  
2. Oluşturun <xref:System.ServiceModel.Description.WsdlExporter> .  
  
     [!code-csharp[S_UEWsdlExporter#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#1)]
     [!code-vb[S_UEWsdlExporter#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#1)]  
  
3. <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A>Özelliğini Numaralandırmadaki değerlerden birine ayarlayın <xref:System.ServiceModel.Description.PolicyVersion> . Bu örnek, <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> WS-Policy 1,5 öğesine karşılık gelen değeri ayarlar.  
  
     [!code-csharp[S_UEWsdlExporter#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#2)]
     [!code-vb[S_UEWsdlExporter#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#2)]  
  
4. Nesne dizisi oluşturun <xref:System.ServiceModel.Description.ServiceEndpoint> .  
  
     [!code-csharp[S_UEWsdlExporter#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#3)]
     [!code-vb[S_UEWsdlExporter#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#3)]  
  
5. Her hizmet uç noktası için meta verileri dışarı aktarın.  
  
     [!code-csharp[S_UEWsdlExporter#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#4)]
     [!code-vb[S_UEWsdlExporter#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#4)]  
  
6. Dışarı aktarma işlemi sırasında bir hata olmadığından emin olun ve meta verileri alın.  
  
     [!code-csharp[S_UEWsdlExporter#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#5)]
     [!code-vb[S_UEWsdlExporter#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#5)]  
  
7. Artık, yöntemini çağırarak bir dosyaya yazmak gibi meta verileri kullanabilirsiniz <xref:System.ServiceModel.Description.MetadataSet.WriteTo%28System.Xml.XmlWriter%29> .  
  
## <a name="example"></a>Örnek  
 Bu örnek için tam kod listesi aşağıda verilmiştir.  
  
 [!code-csharp[S_UEWsdlExporter#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#0)]
 [!code-vb[S_UEWsdlExporter#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#0)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Program.cs Reference System. ServiceModel. dll derlenirken.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Mimarisi Genel Bakış](metadata-architecture-overview.md)
- [Meta Verileri Kullanma](using-metadata.md)
- [Uç Noktalar: Adresler, Bağlamalar ve Anlaşmalar](endpoints-addresses-bindings-and-contracts.md)
