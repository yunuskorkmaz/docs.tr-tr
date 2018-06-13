---
title: Beyaz alan yüklenirken veya XML2 Ayrıştırma sırasında koruma
ms.date: 07/20/2015
ms.assetid: ef6518e0-2c8d-462c-8b92-a16e9dc737ad
ms.openlocfilehash: 3341bfae8ff9de5e17ba18273c60b525f77bff16
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33645648"
---
# <a name="preserving-white-space-while-loading-or-parsing-xml"></a>Beyaz alan yüklenirken veya XML Ayrıştırma sırasında koruma
Bu konu, boşluk davranışını denetlemek açıklar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
 Girintili XML okuma, bir bellek içi XML ağacı boşluk metin düğüm (diğer bir deyişle, değil koruma boşluk) olmadan oluşturmak, XML bazı işlemleri ve ardından XML girintileme ile kaydetmek için yaygın bir senaryo değil. Biçimlendirmeye sahip XML serileştirme, yalnızca önemli boşluk XML ağacında korunur. Varsayılan davranışı budur [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
 Okumak ve özellikle girintili zaten XML değiştirmek için başka bir yaygın bir senaryo değil. Bu girinti herhangi bir şekilde değiştirmek istemeyebilirsiniz. Bunu yapmak için [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], yükleme veya XML Ayrıştırma ve XML serileştirme zaman biçimlendirme devre dışı olduğunda boşluk korumak.  
  
 Bu konuda XML ağaçları doldurmak yöntemleri boşluk davranışını açıklanmaktadır. XML ağaçları seri boşluk denetleme hakkında daha fazla bilgi için bkz: [koruma boşluk sırada seri hale getirme](../../../../visual-basic/programming-guide/concepts/linq/preserving-white-space-while-serializing.md).  
  
## <a name="behavior-of-methods-that-populate-xml-trees"></a>XML ağaçları doldurmak yöntemleri davranışı  
 Aşağıdaki yöntemleri <xref:System.Xml.Linq.XElement> ve <xref:System.Xml.Linq.XDocument> sınıfları doldurmak bir XML ağacı. Bir dosyayı bir XML ağacından doldurabilirsiniz bir <xref:System.IO.TextReader>, bir <xref:System.Xml.XmlReader>, veya bir dize:  
  
-   <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>  
  
 Yöntem değil izlerseniz <xref:System.Xml.Linq.LoadOptions> bir bağımsız değişken olarak Önemsiz boşluk yöntemi korumaz.  
  
 Çoğu durumda, yöntem sürerse <xref:System.Xml.Linq.LoadOptions> bir bağımsız değişken olarak, isteğe bağlı olarak Önemsiz boşluk XML ağacında metin düğümleri olarak koruyabilirsiniz. Ancak, XML'den yöntemi yüklenirken, bir <xref:System.Xml.XmlReader>, sonra <xref:System.Xml.XmlReader> boşluk veya korunması olup olmadığını belirler. Ayarı <xref:System.Xml.Linq.LoadOptions.PreserveWhitespace> hiçbir etkisi olmaz.  
  
 Beyaz alan korunuyorsa, bu yöntemlerle anlamsız boşluk XML ağaç olarak eklenir <xref:System.Xml.Linq.XText> düğümleri. Beyaz alan korunmaz, metin düğümleri eklenmez.  
  
 Bir XML ağacı kullanarak oluşturabileceğiniz bir <xref:System.Xml.XmlWriter>. Yazılan düğümleri <xref:System.Xml.XmlWriter> ağacında doldurulur. Bu yöntemi kullanarak bir XML ağacı yapılandırdığınızda, Bununla birlikte, tüm düğümler korunan, düğüm boşluk olup ya da boşluk önemli olup olmamasına bakılmaksızın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ayrıştırma XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
