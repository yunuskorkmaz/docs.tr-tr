---
title: Yükleme veya XML1 Ayrıştırma sırasında boşluk koruma
ms.date: 07/20/2015
ms.assetid: f3ff58c4-55aa-4fcd-b933-e3a2ee6e706c
ms.openlocfilehash: 3dbbbc8412cdef6ea62197171bb950d6c5344350
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61682150"
---
# <a name="preserving-white-space-while-loading-or-parsing-xml"></a>XML Yükleme veya Ayrıştırma Sırasında Boşluk Koruma
Bu konuda boşluk davranışını denetlemek nasıl açıklar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
 Sık karşılaşılan bir senaryodur girintili XML oku, herhangi bir boşluk metin düğümleri (diğer bir deyişle, beyaz boşluk olmayan koruma) olmadan bir bellek içi XML ağacı oluşturmak, bazı XML işlemleri ve XML girintilemeli kaydedin sağlamaktır. Biçimlendirme ile XML serileştirme, yalnızca önemli boşluk XML ağacındaki korunur. Varsayılan davranışı budur [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
 Başka bir yaygın bir senaryo, okuma ve değiştirme kasıtlı olarak girintili zaten XML sağlamaktır. Bu girinti herhangi bir şekilde değiştirmek istemeyebilirsiniz. Bunu yapmak için [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], yükleme veya XML Ayrıştırma ve XML serileştirme seçildiğinde biçimlendirmeyi devre dışı olduğunda bölünemez boşluğu koruyacak.  
  
 Bu konu, XML ağacı doldurma yöntemleri boşluk davranışını açıklar. XML ağaçlarını serileştirme boşluk denetleme hakkında daha fazla bilgi için bkz. [koruma boşluk sırada serileştirmek](../../../../csharp/programming-guide/concepts/linq/preserving-white-space-while-serializing.md).  
  
## <a name="behavior-of-methods-that-populate-xml-trees"></a>XML ağaçlarını doldurmak yöntemleri davranışı  
 Aşağıdaki yöntemleri <xref:System.Xml.Linq.XElement> ve <xref:System.Xml.Linq.XDocument> sınıfları bir XML ağacı doldurma. Bir dosyadan XML ağacı doldurabilirsiniz bir <xref:System.IO.TextReader>e <xref:System.Xml.XmlReader>, veya bir dize:  
  
- <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>  
  
 Yöntem değil izlerseniz <xref:System.Xml.Linq.LoadOptions> anlamsız boşluk yöntemi bir bağımsız değişken olarak korumaz.  
  
 Çoğu durumda, yöntem sürerse <xref:System.Xml.Linq.LoadOptions> bir bağımsız değişken olarak, isteğe bağlı olarak anlamsız boşluk XML ağacı metin düğümleri olarak koruyabilirsiniz. Ancak, yöntem bir XML dosyası şuradan yükleniyor, bir <xref:System.Xml.XmlReader>, ardından <xref:System.Xml.XmlReader> veya boşluk korunur olup olmadığını belirler. Ayar <xref:System.Xml.Linq.LoadOptions.PreserveWhitespace> hiçbir etkisi olmaz.  
  
 Boşluk korunur, bu yöntemlerle Önemsiz boşluk XML ağacı eklenir <xref:System.Xml.Linq.XText> düğümleri. Metin düğümleri boşluk korunur değil, eklenmiyor.  
  
 Bir XML ağacı kullanarak oluşturabileceğiniz bir <xref:System.Xml.XmlWriter>. Yazılan düğümleri <xref:System.Xml.XmlWriter> ağacında doldurulur. Bu yöntemi kullanarak bir XML ağacı oluşturma sırasında ancak tüm düğümleri korunan, düğüm boşluk olup veya boşluk önemli olup olmamasına bakılmaksızın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Ayrıştırma (C#)](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)
