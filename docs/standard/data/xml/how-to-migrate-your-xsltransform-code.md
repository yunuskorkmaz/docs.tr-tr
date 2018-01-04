---
title: "Nasıl yapılır: çok kodunuzu geçirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 910beb2f-cfb3-4e8e-9936-f7e0c5f4064a
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 9bfef535ecfae48ce09ef0eaca3f11de0a8d6667
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-migrate-your-xsltransform-code"></a>Nasıl yapılır: çok kodunuzu geçirme
Yeni XSLT sınıfları varolan sınıfları çok benzer şekilde tasarlanmıştır. <xref:System.Xml.Xsl.XslCompiledTransform> Sınıf değiştirir <xref:System.Xml.Xsl.XslTransform> sınıfı. Stil sayfaları, kullanarak derlenen <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> yöntemi. Dönüşümler kullanarak yürütülme <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemi. Aşağıdaki yordamlar ortak XSLT görevleri göster ve kod kullanarak karşılaştırın <xref:System.Xml.Xsl.XslTransform> karşı sınıfı <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.  
  
### <a name="to-transform-a-file-and-output-to-a-uri"></a>Dosya ve bir URI çıktısına dönüştürmek için  
  
-   Kullanarak kod <xref:System.Xml.Xsl.XslTransform> sınıfı.  
  
     [!code-csharp[XML_Migration#9](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#9)]
     [!code-vb[XML_Migration#9](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#9)]  
  
-   Kullanarak kod <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.  
  
     [!code-csharp[XML_Migration#10](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#10)]
     [!code-vb[XML_Migration#10](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#10)]  
  
### <a name="to-compile-a-style-sheet-and-use-a-resolver-with-default-credentials"></a>Stil sayfası derlemek ve çözümleyici varsayılan kimlik bilgileri ile kullanmak için  
  
-   Kullanarak kod <xref:System.Xml.Xsl.XslTransform> sınıfı.  
  
     [!code-csharp[XML_Migration#11](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#11)]
     [!code-vb[XML_Migration#11](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#11)]  
  
-   Kullanarak kod <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.  
  
     [!code-csharp[XML_Migration#12](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#12)]
     [!code-vb[XML_Migration#12](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#12)]  
  
### <a name="to-use-an-xslt-parameter"></a>XSLT parametresini kullanma  
  
-   Kullanarak kod <xref:System.Xml.Xsl.XslTransform> sınıfı.  
  
     [!code-csharp[XML_Migration#13](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#13)]
     [!code-vb[XML_Migration#13](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#13)]  
  
-   Kullanarak kod <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.  
  
     [!code-csharp[XML_Migration#14](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#14)]
     [!code-vb[XML_Migration#14](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#14)]  
  
### <a name="to-enable-xslt-scripting"></a>XSLT betik kullanımını etkinleştirmek için  
  
-   Kullanarak kod <xref:System.Xml.Xsl.XslTransform> sınıfı.  
  
     [!code-csharp[XML_Migration#15](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#15)]
     [!code-vb[XML_Migration#15](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#15)]  
  
-   Kullanarak kod <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.  
  
     [!code-csharp[XML_Migration#16](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#16)]
     [!code-vb[XML_Migration#16](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#16)]  
  
### <a name="to-load-the-results-into-a-dom-object"></a>Sonuçları bir DOM nesnesine yüklemek için  
  
-   Kullanarak kod <xref:System.Xml.Xsl.XslTransform> sınıfı.  
  
     [!code-csharp[XML_Migration#19](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#19)]
     [!code-vb[XML_Migration#19](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#19)]  
  
-   Kullanarak kod <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.  
  
    > [!NOTE]
    >  <xref:System.Xml.Xsl.XslCompiledTransform> Sınıfı olarak XSLT dönüşümü sonuçları döndüren bir yöntem yok bir <xref:System.Xml.XmlReader> nesnesi. Ancak, bir XML dosyasına çıkarmak ve başka bir nesnede XML dosyasını yükle.  
  
     [!code-csharp[XML_Migration#20](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#20)]
     [!code-vb[XML_Migration#20](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#20)]  
  
### <a name="to-stream-the-results-into-another-data-store"></a>Başka bir veri deposuna sonuçları akışı  
  
-   Kullanarak kod <xref:System.Xml.Xsl.XslTransform> sınıfı.  
  
     [!code-csharp[XML_Migration#17](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#17)]
     [!code-vb[XML_Migration#17](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#17)]  
  
-   Kullanarak kod <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.  
  
     [!code-csharp[XML_Migration#18](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#18)]
     [!code-vb[XML_Migration#18](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#18)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XslTransform Sınıfından Geçirme](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)  
 [XslCompiledTransform Sınıfını Kullanma](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)
