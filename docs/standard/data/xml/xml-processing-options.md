---
title: XML İşleme Seçenekleri
description: LINQ to XML, XmlReader, XmlWriter, XmlDocument, XPathNavigator, XslCompiledTransform, XmlLite ve MSXML dahil olmak üzere XML işleme seçeneklerini gözden geçirin.
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 33ced8ee-1745-4e71-8dee-ebe70ec067c7
ms.openlocfilehash: c41b3dd99264b9043c5914b84bbb76ac02b317ac
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84767773"
---
# <a name="xml-processing-options"></a>XML İşleme Seçenekleri
XML verilerini işlemek için kullanabileceğiniz Microsoft teknolojilerinin bir listesi için aşağıdaki tablolara bakın.  
  
## <a name="net-framework-options"></a>.NET Framework seçenekleri  
  
|**Seçeneği**|**İşlem türü**|**Açıklama**|  
|----------------|-------------------------|---------------------|  
|[LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) <br/> [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) <br />( <xref:System.Xml.Linq> ad alanı)|Bellek içi|.NET Framework dil ile tümleşik sorgu (LINQ) teknolojisine göre.<br />-Nesneler, ilişkisel veriler ve XML verileri için SQL 'e benzeyen sorgu deneyimi sağlar.<br />-Sezgisel belge oluşturma ve dönüştürme özellikleri sağlar.<br />-Yeni kod yazıyorsanız bu seçeneği kullanın.|  
|<xref:System.Xml.XmlReader?displayProperty=nameWithType>|Akış tabanlı|-XML verilerine erişmenin hızlı, önbelleğe alınmamış ve salt ileri bir yolunu sağlar.<br />-Yöntemini kullanarak nesneler oluşturabilir <xref:System.Xml.XmlReader.Create%2A?displayProperty=nameWithType> ve sınıfını kullanarak nesne üzerinde etkinleştirilecek özellikler kümesini belirtebilirsiniz <xref:System.Xml.XmlReaderSettings> .|  
|<xref:System.Xml.XmlWriter?displayProperty=nameWithType>|Akış tabanlı|-XML verisi oluşturmak için hızlı, önbelleğe alınmamış ve salt ileri bir yol sağlar.<br />-Yöntemini kullanarak nesneler oluşturabilir <xref:System.Xml.XmlWriter.Create%2A?displayProperty=nameWithType> ve sınıfını kullanarak nesne üzerinde etkinleştirilecek özellikler kümesini belirtebilirsiniz <xref:System.Xml.XmlWriterSettings> .|  
|<xref:System.Xml.XmlDocument?displayProperty=nameWithType>|Bellek içi|- [W3C belge nesne modeli (DOM) düzey 1 Core](https://www.w3.org/TR/REC-DOM-Level-1/level-one-core.html) ve [DOM düzey 2 temel](https://www.w3.org/TR/DOM-Level-2-Core/) önerilerini uygular.<br />-Tanıdık DOM modeline göre yöntemleri ve özellikleri kullanarak düğümleri oluşturabilir, ekleyebilir, kaldırabilir ve değiştirebilirsiniz.<br />-W3C DOM kullanan mevcut kodu değiştiriyorsanız bu seçeneği kullanın.|  
|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|Bellek içi|-Bir imleç modeli kullanarak birkaç düzenleyici seçeneği ve gezinme özelliği sunar.<br />-XML belgeleri bir veya nesnesi içinde bulunabilir <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> .<br />-XML 'nin salt okuma işlemesi için mükemmel performans sağlar.<br />-Mevcut kodu XPath sorgularıyla veya XSLT dönüşümlerinde değiştiriyorsanız bu seçeneği kullanın.|  
|<xref:System.Xml.Xsl.XslCompiledTransform>|Bellek içi|-XSL dönüştürmeleri kullanarak XML verilerini dönüştürmek için seçenekler sağlar.<br />- [XSLT derleyicisi (xsltc.exe)](xslt-compiler-xsltc-exe.md) , uygulamanızda önceden derlenmiş dönüşümlere başvurmanıza olanak sağlar.|  
  
## <a name="win32-and-com-based-options"></a>Win32 ve COM tabanlı seçenekler  
  
|**Seçeneği**|**Açıklama**|  
|----------------|---------------------|  
|[Yönelik](https://docs.microsoft.com/previous-versions/windows/desktop/ms752872(v=vs.85))|-Hızlı, güvenli, önbelleğe alınmamış ve yalnızca ileri düzey bir XML Ayrıştırıcısı, yüksek performanslı XML uygulamaları oluşturmanıza yardımcı olur.<br />-Dinamik bağlantı kitaplıklarını (dll 'Ler) kullanan herhangi bir dille birlikte çalışarak. C++ kullanmanızı öneririz.|  
|[MSXML](https://docs.microsoft.com/previous-versions/windows/desktop/ms763742(v=vs.85))|-Windows işletim sisteminde yer alan XML işlemek için COM tabanlı teknoloji.<br />-XPath ve XSLT desteğiyle DOM 'ın yerel bir uygulamasını sağlar.<br />-SAX2 olay tabanlı ayrıştırıcısı içerir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DOM Modelini Kullanarak XML Verilerini İşleme](process-xml-data-using-the-dom-model.md)
- [XPath Veri Modelini Kullanarak XML Verilerini İşleme](process-xml-data-using-the-xpath-data-model.md)
- [XSLT Derleyicisi (xsltc.exe)](xslt-compiler-xsltc-exe.md)
