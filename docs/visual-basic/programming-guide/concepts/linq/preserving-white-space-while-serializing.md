---
title: Serializing2 sırasında boşluk koruma
ms.date: 07/20/2015
ms.assetid: 2d7abbd4-37f4-422b-89dd-0a694b5edc17
ms.openlocfilehash: e9b73089830bf7e6cb0ea9e469bf667f12c571d8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396408"
---
# <a name="preserving-white-space-while-serializing"></a>Serileştirirken Boşlukları Koruma
Bu konu, bir XML ağacı serileştirilirken boşluk denetimini nasıl denetleyebileceğinizi açıklamaktadır.  
  
 Yaygın bir senaryo, girintili XML 'yi okumak, boşluk metin düğümleri olmadan bir bellek içi XML ağacı oluşturmaktır (diğer bir deyişle, beyaz alanı korumadan), XML üzerinde bazı işlemleri gerçekleştirir ve ardından XML 'i girintilemeli olarak kaydeder. XML 'yi biçimlendirme ile serileştirçalıştığınızda, XML ağacında yalnızca önemli boşluk korunur. Bu varsayılan davranıştır [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .  
  
 Diğer bir yaygın senaryo, daha önce kasıtlı olarak girintili olan XML 'i okuyup değiştirmektir. Bu Girintiyi istediğiniz şekilde değiştirmek istemeyebilirsiniz. Bunu yapmak için [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , XML 'i yüklediğinizde veya ayrıştırdığınızda veya XML 'yi seri hale alırken biçimlendirmeyi devre dışı bıraktığınızda boşluğu koruyabilirsiniz.  
  
## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a>XML ağaçlarını seri hale getirme yöntemlerinin boşluk davranışı  
 <xref:System.Xml.Linq.XElement>Ve sınıflarında aşağıdaki yöntemler <xref:System.Xml.Linq.XDocument> bir xml ağacını serileştirin. Bir XML ağacını bir dosyaya, a 'ya veya bir dosyasına seri hale getirebilirsiniz <xref:System.IO.TextReader> <xref:System.Xml.XmlReader> . `ToString`Yöntemi bir dizeye seri hale getirir.  
  
- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
- [XElement. ToString ()](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
  
- [XDocument. ToString ()](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
  
 Yöntem <xref:System.Xml.Linq.SaveOptions> bir bağımsız değişken olarak kullanmıyorsa, yöntemi SERILEŞTIRILMIŞ XML 'i biçimlendirir (girintili). Bu durumda, XML ağacındaki tüm önemli boşluklar atılır.  
  
 Yöntemi <xref:System.Xml.Linq.SaveOptions> bir bağımsız değişken olarak ele alıyorsa, yöntemin SERILEŞTIRILMIŞ XML 'yi biçimlendirme (girintileme) seçeneğini belirtebilirsiniz. Bu durumda, XML ağacındaki tüm boşluklar korunur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML ağaçlarını serileştirme (Visual Basic)](serializing-xml-trees.md)
