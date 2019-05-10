---
title: 'Nasıl yapılır: XslTransform Kodunuzu Geçirme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 910beb2f-cfb3-4e8e-9936-f7e0c5f4064a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 67cf4636a8b947bc6ad0ce0475c53bc25cd0f678
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647921"
---
# <a name="how-to-migrate-your-xsltransform-code"></a>Nasıl yapılır: XslTransform Kodunuzu Geçirme
Yeni XSLT sınıfları varolan sınıflara çok benzer şekilde tasarlanmıştır. <xref:System.Xml.Xsl.XslCompiledTransform> Sınıfı değiştirir <xref:System.Xml.Xsl.XslTransform> sınıfı. Stil sayfaları kullanarak derlenen <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> yöntemi. Dönüşümler kullanılarak çalıştırılır <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemi. Aşağıdaki yordamlar, ortak XSLT görevleri göstermek ve kodla karşılaştırın <xref:System.Xml.Xsl.XslTransform> karşı sınıf <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.  
  
### <a name="to-transform-a-file-and-output-to-a-uri"></a>Dosya ve çıkış için bir URI dönüştürmek için  
  
- Kod kullanarak <xref:System.Xml.Xsl.XslTransform> sınıfı.  
  
     [!code-csharp[XML_Migration#9](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#9)]
     [!code-vb[XML_Migration#9](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#9)]  
  
- Kod kullanarak <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.  
  
     [!code-csharp[XML_Migration#10](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#10)]
     [!code-vb[XML_Migration#10](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#10)]  
  
### <a name="to-compile-a-style-sheet-and-use-a-resolver-with-default-credentials"></a>Bir stil sayfası derlemek ve varsayılan kimlik bilgileriyle bir çözümleyici kullanma  
  
- Kod kullanarak <xref:System.Xml.Xsl.XslTransform> sınıfı.  
  
     [!code-csharp[XML_Migration#11](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#11)]
     [!code-vb[XML_Migration#11](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#11)]  
  
- Kod kullanarak <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.  
  
     [!code-csharp[XML_Migration#12](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#12)]
     [!code-vb[XML_Migration#12](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#12)]  
  
### <a name="to-use-an-xslt-parameter"></a>XSLT parametresini kullanma  
  
- Kod kullanarak <xref:System.Xml.Xsl.XslTransform> sınıfı.  
  
     [!code-csharp[XML_Migration#13](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#13)]
     [!code-vb[XML_Migration#13](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#13)]  
  
- Kod kullanarak <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.  
  
     [!code-csharp[XML_Migration#14](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#14)]
     [!code-vb[XML_Migration#14](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#14)]  
  
### <a name="to-enable-xslt-scripting"></a>XSLT betik etkinleştirmek için  
  
- Kod kullanarak <xref:System.Xml.Xsl.XslTransform> sınıfı.  
  
     [!code-csharp[XML_Migration#15](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#15)]
     [!code-vb[XML_Migration#15](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#15)]  
  
- Kod kullanarak <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.  
  
     [!code-csharp[XML_Migration#16](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#16)]
     [!code-vb[XML_Migration#16](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#16)]  
  
### <a name="to-load-the-results-into-a-dom-object"></a>Sonuç bir DOM nesnesine yüklemek için  
  
- Kod kullanarak <xref:System.Xml.Xsl.XslTransform> sınıfı.  
  
     [!code-csharp[XML_Migration#19](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#19)]
     [!code-vb[XML_Migration#19](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#19)]  
  
- Kod kullanarak <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.  
  
    > [!NOTE]
    >  <xref:System.Xml.Xsl.XslCompiledTransform> Sınıfı XSLT dönüşümü sonuçları döndüren bir yöntem yok bir <xref:System.Xml.XmlReader> nesne. Ancak, bir XML dosyasına çıkarmak ve başka bir nesnede XML dosyasını yükleyin.  
  
     [!code-csharp[XML_Migration#20](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#20)]
     [!code-vb[XML_Migration#20](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#20)]  
  
### <a name="to-stream-the-results-into-another-data-store"></a>Sonuçları başka bir veri deposuna veri akışı  
  
- Kod kullanarak <xref:System.Xml.Xsl.XslTransform> sınıfı.  
  
     [!code-csharp[XML_Migration#17](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#17)]
     [!code-vb[XML_Migration#17](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#17)]  
  
- Kod kullanarak <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.  
  
     [!code-csharp[XML_Migration#18](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#18)]
     [!code-vb[XML_Migration#18](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#18)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XslTransform Sınıfından Geçirme](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)
- [XslCompiledTransform Sınıfını Kullanma](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)
