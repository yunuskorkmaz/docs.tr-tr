---
title: "XML işleme seçenekleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33ced8ee-1745-4e71-8dee-ebe70ec067c7
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2619842bedef2c28e792969dfbd5c724375122bf
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="xml-processing-options"></a>XML işleme seçenekleri
XML verilerini işlemek için kullanabileceğiniz Microsoft teknolojilerin bir listesi için aşağıdaki tablolara bakın.  
  
## <a name="net-framework-options"></a>.NET framework seçenekleri  
  
|**Seçeneği**|**İşleme türü**|**Açıklama**|  
|----------------|-------------------------|---------------------|  
|[LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) <br />(<xref:System.Xml.Linq> ad alanı)|Bellek içi|-.NET Framework Language-Integrated sorgu (LINQ) teknolojisine dayalı.<br />-Nesneleri, ilişkisel veri ve XML verilerini SQL benzer sorgu deneyimi sağlar.<br />-İnituive belge oluşturma ve dönüştürme özellikleri sağlar.<br />-Yeni kod yazıyorsanız, bu seçeneği kullanın.|  
|<xref:System.Xml.XmlReader?displayProperty=nameWithType>|Akış tabanlı|-XML verilerine erişmek için hızlı, önbelleğe alınmamış, yalnızca ileri bir yol sağlar.<br />-Nesneleri kullanarak oluşturabileceğiniz <xref:System.Xml.XmlReader.Create%2A?displayProperty=nameWithType> yöntemini ve bir nesne üzerinde kullanarak etkinleştirmek için özellik kümesi belirtin <xref:System.Xml.XmlReaderSettings> sınıfı.|  
|<xref:System.Xml.XmlWriter?displayProperty=nameWithType>|Akış tabanlı|-XML verileri oluşturmak için hızlı, önbelleğe alınmamış, yalnızca ileri bir yol sağlar.<br />-Nesneleri kullanarak oluşturabileceğiniz <xref:System.Xml.XmlWriter.Create%2A?displayProperty=nameWithType> yöntemini ve bir nesne üzerinde kullanarak etkinleştirmek için özellik kümesi belirtin <xref:System.Xml.XmlWriterSettings> sınıfı.|  
|<xref:System.Xml.XmlDocument?displayProperty=nameWithType>|Bellek içi|-Uygulayan [W3C belge nesne modeli (DOM) Düzey 1 çekirdek](http://www.w3.org/TR/REC-DOM-Level-1/level-one-core.html) ve [DOM Düzey 2 Çekirdek](http://www.w3.org/TR/DOM-Level-2-Core/) öneriler.<br />-Oluşturabilir, Ekle, Kaldır ve düğümler yöntemleri ve tanıdık DOM modelini temel alan özelliklerini kullanarak değiştirebilirsiniz.<br />-Bu seçenek W3C DOM kullanan var olan kodu değiştiriyorsanız kullanın|  
|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|Bellek içi|-Birçok düzenleme seçeneklerini ve bir imleç modeli kullanılarak Gezinti özellikleri sunar.<br />-XML belgelerini içinde barındırılan bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> nesnesi.<br />-XML salt okunur işlenmesi için mükemmel performans sağlar.<br />-XPath sorguları veya XSLT dönüştürmeleri varolan kodla değiştiriyorsanız bu seçeneği kullanın.|  
|<xref:System.Xml.Xsl.XslCompiledTransform>|Bellek içi|-XSL Dönüşümleri kullanarak XML veri dönüştürme için seçenekler sağlar.<br />- [XSLT derleyici (xsltc.exe)](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md) önceden derlenmiş dönüşümleri, uygulamanızda başvuru sağlar.|  
  
## <a name="win32-and-com-based-options"></a>Win32 ve COM tabanlı seçenekler  
  
|**Seçeneği**|**Açıklama**|  
|----------------|---------------------|  
|[XmlLite](http://go.microsoft.com/fwlink/?LinkId=93723)|-a olmayan önbelleğe alma hızlı ve güvenli, yardımcı salt iletme XML Ayrıştırıcı yapı yüksek performanslı XML uygulamalar.<br />-Dinamik bağlantı kitaplıklarını (DLL'ler); kullanabilirsiniz herhangi bir dil ile çalışır C++ kullanmanızı öneririz.|  
|[MSXML](http://go.microsoft.com/fwlink/?LinkId=93722)|-Windows işletim sisteminde bulunan XML işlemek için COM tabanlı teknolojidir.<br />-DOM yerel bir uygulama XPath ve XSLT için destek sağlar.<br />-Olay tabanlı SAX2 ayrıştırıcısını içerir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DOM Modelini Kullanarak XML Verilerini İşleme](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)  
 [XPath Veri Modelini Kullanarak XML Verilerini İşleme](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [XSLT Derleyicisi (xsltc.exe)](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md)
