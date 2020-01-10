---
title: 'Nasıl yapılır: XslTransform kodunuzu geçirme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 910beb2f-cfb3-4e8e-9936-f7e0c5f4064a
ms.openlocfilehash: 2bc5cbc1b0857a82d3b0a11f05a4eb5756724546
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710849"
---
# <a name="how-to-migrate-your-xsltransform-code"></a>Nasıl yapılır: XslTransform kodunuzu geçirme
Yeni XSLT sınıfları, mevcut sınıflara çok benzer olacak şekilde tasarlanmıştır. <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı <xref:System.Xml.Xsl.XslTransform> sınıfının yerini alır. Stil sayfaları <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> yöntemi kullanılarak derlenir. Dönüşümler <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemi kullanılarak yürütülür. Aşağıdaki yordamlarda ortak XSLT görevleri gösterilmektedir ve <xref:System.Xml.Xsl.XslTransform> sınıfını kullanarak kodu <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı ile karşılaştırın.  
  
### <a name="to-transform-a-file-and-output-to-a-uri"></a>Bir dosyayı ve çıktıyı bir URI 'ye dönüştürmek için  
  
- <xref:System.Xml.Xsl.XslTransform> sınıfını kullanan kod.  
  
     [!code-csharp[XML_Migration#9](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#9)]
     [!code-vb[XML_Migration#9](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#9)]  
  
- <xref:System.Xml.Xsl.XslCompiledTransform> sınıfını kullanan kod.  
  
     [!code-csharp[XML_Migration#10](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#10)]
     [!code-vb[XML_Migration#10](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#10)]  
  
### <a name="to-compile-a-style-sheet-and-use-a-resolver-with-default-credentials"></a>Bir stil sayfası derlemek ve varsayılan kimlik bilgileriyle çözümleyici kullanmak için  
  
- <xref:System.Xml.Xsl.XslTransform> sınıfını kullanan kod.  
  
     [!code-csharp[XML_Migration#11](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#11)]
     [!code-vb[XML_Migration#11](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#11)]  
  
- <xref:System.Xml.Xsl.XslCompiledTransform> sınıfını kullanan kod.  
  
     [!code-csharp[XML_Migration#12](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#12)]
     [!code-vb[XML_Migration#12](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#12)]  
  
### <a name="to-use-an-xslt-parameter"></a>XSLT parametresi kullanmak için  
  
- <xref:System.Xml.Xsl.XslTransform> sınıfını kullanan kod.  
  
     [!code-csharp[XML_Migration#13](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#13)]
     [!code-vb[XML_Migration#13](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#13)]  
  
- <xref:System.Xml.Xsl.XslCompiledTransform> sınıfını kullanan kod.  
  
     [!code-csharp[XML_Migration#14](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#14)]
     [!code-vb[XML_Migration#14](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#14)]  
  
### <a name="to-enable-xslt-scripting"></a>XSLT komut dosyalarını etkinleştirmek için  
  
- <xref:System.Xml.Xsl.XslTransform> sınıfını kullanan kod.  
  
     [!code-csharp[XML_Migration#15](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#15)]
     [!code-vb[XML_Migration#15](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#15)]  
  
- <xref:System.Xml.Xsl.XslCompiledTransform> sınıfını kullanan kod.  
  
     [!code-csharp[XML_Migration#16](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#16)]
     [!code-vb[XML_Migration#16](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#16)]  
  
### <a name="to-load-the-results-into-a-dom-object"></a>Sonuçları DOM nesnesine yüklemek için  
  
- <xref:System.Xml.Xsl.XslTransform> sınıfını kullanan kod.  
  
     [!code-csharp[XML_Migration#19](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#19)]
     [!code-vb[XML_Migration#19](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#19)]  
  
- <xref:System.Xml.Xsl.XslCompiledTransform> sınıfını kullanan kod.  
  
    > [!NOTE]
    > <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı, XSLT dönüştürme sonuçlarını bir <xref:System.Xml.XmlReader> nesnesi olarak döndüren bir yönteme sahip değil. Ancak, bir XML dosyasına çıktı verebilir ve XML dosyasını başka bir nesneye yükleyebilirsiniz.  
  
     [!code-csharp[XML_Migration#20](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#20)]
     [!code-vb[XML_Migration#20](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#20)]  
  
### <a name="to-stream-the-results-into-another-data-store"></a>Sonuçları başka bir veri deposuna akışa almak için  
  
- <xref:System.Xml.Xsl.XslTransform> sınıfını kullanan kod.  
  
     [!code-csharp[XML_Migration#17](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#17)]
     [!code-vb[XML_Migration#17](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#17)]  
  
- <xref:System.Xml.Xsl.XslCompiledTransform> sınıfını kullanan kod.  
  
     [!code-csharp[XML_Migration#18](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#18)]
     [!code-vb[XML_Migration#18](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#18)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XslTransform Sınıfından Geçirme](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)
- [XslCompiledTransform Sınıfını Kullanma](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)
