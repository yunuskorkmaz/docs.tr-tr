---
title: XML İşleme Seçenekleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 33ced8ee-1745-4e71-8dee-ebe70ec067c7
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 585a6e568bde6e6eca15477eaa10b5c91c91c5a4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61958918"
---
# <a name="xml-processing-options"></a>XML İşleme Seçenekleri
XML verilerini işlemek için kullanabileceğiniz Microsoft teknolojilerinin bir listesi için aşağıdaki tablolara bakın.  
  
## <a name="net-framework-options"></a>.NET framework seçenekleri  
  
|**Seçeneği**|**İşleme türü**|**Açıklama**|  
|----------------|-------------------------|---------------------|  
|[LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) <br/> [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) <br />(<xref:System.Xml.Linq> ad alanı)|Bellek içi|-.NET Framework Language-Integrated sorgu (LINQ) teknolojisini temel alan.<br />-SQL nesneleri, ilişkisel veriler ve XML veri benzer sorgu deneyimi sağlar.<br />-Sezgisel belge oluşturma ve dönüştürme özelliklerini sağlar.<br />-Yeni kod yazıyorsanız, bu seçeneği kullanın.|  
|<xref:System.Xml.XmlReader?displayProperty=nameWithType>|Stream tabanlı|-XML verilerine erişmek için hızlı, önbelleğe alınmamış, yalnızca iletme bir yol sağlar.<br />-Kullanarak nesne oluşturabilirsiniz <xref:System.Xml.XmlReader.Create%2A?displayProperty=nameWithType> yöntemi ve bir nesne üzerinde kullanarak etkinleştirmek için özellik kümesini belirtin <xref:System.Xml.XmlReaderSettings> sınıfı.|  
|<xref:System.Xml.XmlWriter?displayProperty=nameWithType>|Stream tabanlı|-XML verileri oluşturmak için hızlı, önbelleğe alınmamış, yalnızca iletme bir yol sağlar.<br />-Kullanarak nesne oluşturabilirsiniz <xref:System.Xml.XmlWriter.Create%2A?displayProperty=nameWithType> yöntemi ve bir nesne üzerinde kullanarak etkinleştirmek için özellik kümesini belirtin <xref:System.Xml.XmlWriterSettings> sınıfı.|  
|<xref:System.Xml.XmlDocument?displayProperty=nameWithType>|Bellek içi|-Uygulayan [W3C belge nesne modeli (DOM) Düzey 1 çekirdek](https://www.w3.org/TR/REC-DOM-Level-1/level-one-core.html) ve [DOM düzeyi 2 Çekirdek](https://www.w3.org/TR/DOM-Level-2-Core/) öneriler.<br />-, Ekle, Kaldır, oluşturup düzenleyebilir düğümleri yöntemleri ve tanıdık DOM modelini temel alan özelliklerini kullanarak.<br />-W3C yerli kullanan mevcut kodu değiştiriyorsanız bu seçeneği kullanın|  
|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|Bellek içi|-Birçok düzenleme seçeneklerini ve imleç modelini kullanarak gezinti özellikleri sunar.<br />-XML belgeleri yer almalıdır içinde bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> nesne.<br />-XML salt okunur işlenmesi için mükemmel bir performans sağlar.<br />-XPath sorguları veya XSLT dönüşümleri ile mevcut kodu değiştiriliyorsa bu seçeneği kullanın.|  
|<xref:System.Xml.Xsl.XslCompiledTransform>|Bellek içi|-Gt; XSL Dönüşümleri kullanarak XML verilerine dönüştürme için seçenekler sağlar.<br />- [XSLT derleyicisi (xsltc.exe)](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md) önceden derlenmiş uygulamanızı dönüşümlerini başvuru sağlar.|  
  
## <a name="win32-and-com-based-options"></a>Win32 ve COM tabanlı seçenekler  
  
|**Seçeneği**|**Açıklama**|  
|----------------|---------------------|  
|[XmlLite](https://docs.microsoft.com/previous-versions/windows/desktop/ms752872(v=vs.85))|Olmayan önbelleğe alma hızlı, güvenli, yardımcı olan yalnızca iletme XML Ayrıştırıcı yüksek performanslı XML uygulamalar oluşturun.<br />-Dinamik bağlantı kitaplıklarını (DLL'ler); kullanabilirsiniz herhangi bir dil ile çalışır C++ kullanmanızı öneririz.|  
|[MSXML](https://docs.microsoft.com/previous-versions/windows/desktop/ms763742(v=vs.85))|-Windows işletim sisteminde bulunan XML işlemek için COM tabanlı teknoloji.<br />-XPath ve XSLT desteğiyle DOM yerel bir uygulamasını sağlar.<br />-Olay tabanlı SAX2 ayrıştırıcının içerir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DOM Modelini Kullanarak XML Verilerini İşleme](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)
- [XPath Veri Modelini Kullanarak XML Verilerini İşleme](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [XSLT Derleyicisi (xsltc.exe)](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md)
