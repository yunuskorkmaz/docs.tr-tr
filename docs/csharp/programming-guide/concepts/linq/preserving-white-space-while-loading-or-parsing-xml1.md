---
title: XML Yükleme veya Ayrıştırma Sırasında Boşluk Koruma
ms.date: 07/20/2015
ms.assetid: f3ff58c4-55aa-4fcd-b933-e3a2ee6e706c
ms.openlocfilehash: d015c21813df2224356bb49212fe282fa5372d03
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69591547"
---
# <a name="preserving-white-space-while-loading-or-parsing-xml"></a>XML Yükleme veya Ayrıştırma Sırasında Boşluk Koruma
Bu konu, beyaz alan davranışını [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]nasıl denetleriz açıklar.  
  
 Ortak bir senaryo girintisi XML okumak, herhangi bir beyaz boşluk metin düğümleri olmadan bir bellek XML ağacı oluşturmak (yani, beyaz boşluk koruyarak değil), XML bazı işlemler gerçekleştirmek ve sonra girintiyle XML kaydetmek. XML'yi biçimlendirme yle seri hale aldığınızda, XML ağacında yalnızca önemli beyaz boşluk korunur. Bu, '' [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]için varsayılan davranıştır.  
  
 Başka bir yaygın senaryo okumak ve zaten kasıtlı olarak girintilmiş xml değiştirmektir. Bu girintiyi herhangi bir şekilde değiştirmek istemeyebilirsiniz. Bunu yapmak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]için, XML'i yüklerken veya ayrıştırırken beyaz alanı korur ve XML'i seri hale rirken biçimlendirmeyi devre dışı bırakabilirsiniz.  
  
 Bu konu, XML ağaçlarını dolduran yöntemlerin beyaz alan davranışını açıklar. XML ağaçlarını seri hale getirmede beyaz alanı denetleme hakkında bilgi için seri [hale alırken Beyaz Alanı Koruma'ya](./preserving-white-space-while-serializing.md)bakın.  
  
## <a name="behavior-of-methods-that-populate-xml-trees"></a>XML Ağaçlarını Dolduran Yöntemlerin Davranışı  
 Aşağıdaki yöntemler <xref:System.Xml.Linq.XElement> ve <xref:System.Xml.Linq.XDocument> sınıflarda bir XML ağacı doldurmak. Bir XML ağacını bir dosyadan, <xref:System.IO.TextReader>bir, bir, bir <xref:System.Xml.XmlReader>veya dizeden doldurabilirsiniz:  
  
- <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>  
  
 Yöntem bir bağımsız <xref:System.Xml.Linq.LoadOptions> değişken olarak almazsa, yöntem önemsiz beyaz alanı korumaz.  
  
 Çoğu durumda, yöntem bir <xref:System.Xml.Linq.LoadOptions> bağımsız değişken olarak alırsa, isteğe bağlı olarak XML ağacında metin düğümleri olarak önemsiz beyaz alanı koruyabilirsiniz. Ancak, yöntem XML'yi bir <xref:System.Xml.XmlReader>'den <xref:System.Xml.XmlReader> yüklüyorsa, beyaz boşluğun korunup korunmayacağını belirler. Ayar <xref:System.Xml.Linq.LoadOptions.PreserveWhitespace> hiçbir etkisi olmayacaktır.  
  
 Bu yöntemlerle, beyaz boşluk korunursa, xml ağacına düğüm olarak <xref:System.Xml.Linq.XText> önemsiz beyaz boşluk eklenir. Beyaz boşluk korunmuyorsa, metin düğümleri eklenmez.  
  
 Bir XML ağacı kullanarak bir <xref:System.Xml.XmlWriter>XML ağacı oluşturabilirsiniz. Ağaçlara yazılan <xref:System.Xml.XmlWriter> düğümler ağaçta doldurulur. Ancak, bu yöntemi kullanarak bir XML ağacı oluşturduğunuzda, düğüm beyaz boşluk olup olmadığına veya beyaz alanın önemli olup olmadığına bakılmaksızın tüm düğümler korunur.  
  