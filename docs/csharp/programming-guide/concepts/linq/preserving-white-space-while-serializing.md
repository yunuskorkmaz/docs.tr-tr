---
title: Serileştirme yaparken Beyaz Boşluğu Koruma3
ms.date: 07/20/2015
ms.assetid: 0c4f8b98-483b-4cf8-86be-fa146eef90dc
ms.openlocfilehash: 6d357d40c13a66a152b3c8bb5f61e3a3374c4055
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "66484083"
---
# <a name="preserving-white-space-while-serializing"></a>Serileştirirken Boşlukları Koruma
Bu konu, bir XML ağacını seri hale alırken beyaz alanı nasıl denetleriz açıklanır.  
  
 Ortak bir senaryo girintisi XML okumak, herhangi bir beyaz boşluk metin düğümleri olmadan bir bellek XML ağacı oluşturmak (yani, beyaz boşluk koruyarak değil), XML bazı işlemler gerçekleştirmek ve sonra girintiyle XML kaydedin. XML'yi biçimlendirme yle seri hale aldığınızda, XML ağacında yalnızca önemli beyaz boşluk korunur. Bu, '' [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]için varsayılan davranıştır.  
  
 Başka bir yaygın senaryo okumak ve zaten kasıtlı olarak girintilmiş xml değiştirmektir. Bu girintiyi herhangi bir şekilde değiştirmek istemeyebilirsiniz. Bunu yapmak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]için, XML'i yüklerken veya ayrıştırırken beyaz alanı korur ve XML'i seri hale rirken biçimlendirmeyi devre dışı bırakabilirsiniz.  
  
## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a>XML Ağaçlarını SeriHale Getiren Yöntemlerin Beyaz Alan Davranışı  
 Aşağıdaki yöntemler <xref:System.Xml.Linq.XElement> ve <xref:System.Xml.Linq.XDocument> sınıflar da bir XML ağacı serihale. Bir XML ağacını bir dosyaya, <xref:System.IO.TextReader>bir <xref:System.Xml.XmlReader>dosyaya veya bir ' ye seri leştirebilirsiniz. Yöntem `ToString` seri bir dize içinize.  
  
- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
- [XElement.ToString()](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
  
- [XDocument.ToString()](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
  
 Yöntem bir bağımsız <xref:System.Xml.Linq.SaveOptions> değişken olarak almazsa, yöntem serileştirilmiş XML biçimlendir (girintisi) olur. Bu durumda, XML ağacındaki tüm önemsiz beyaz boşluk atılır.  
  
 Yöntem bir bağımsız <xref:System.Xml.Linq.SaveOptions> değişken olarak alırsa, o zaman yöntem indenist (girintisi) seri xml biçimlendirmek değil belirtebilirsiniz. Bu durumda, XML ağacındaki tüm beyaz boşluk korunur.  
