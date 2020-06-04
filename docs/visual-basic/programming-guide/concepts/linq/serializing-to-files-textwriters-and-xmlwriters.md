---
title: Dosyalara serileştirme, TextWriters ve XmlWriters3
ms.date: 07/20/2015
ms.assetid: 7a0c24df-79ef-41a0-87f5-e6cf79382da9
ms.openlocfilehash: d8b929ef02b8fd9c6a9f29ea997a754699a6e1c4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403569"
---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a>Dosya, TextWriters ve XmlWriters Serileştirme

XML ağaçlarını bir, a veya olarak seri hale getirebilirsiniz <xref:System.IO.File> <xref:System.IO.TextWriter> <xref:System.Xml.XmlWriter> .

Yöntemini kullanarak, ve dahil olmak üzere herhangi bir XML bileşenini bir dizeye seri hale getirebilirsiniz <xref:System.Xml.Linq.XDocument> <xref:System.Xml.Linq.XElement> `ToString` .

Bir dizeye serileştirilirken biçimlendirmeyi bastırmak istiyorsanız <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> yöntemini kullanabilirsiniz.

Bir dosyaya serileştirilirken varsayılan davranış, elde edilen XML belgesini biçimlendirmek (Girintile). Girinti yaptığınızda XML ağacındaki önemli boşluk korunmaz. Biçimlendirme ile seri hale getirmek için, aşağıdaki yöntemlerin bağımsız değişken olarak olmayan aşırı yüklemelerinin birini kullanın <xref:System.Xml.Linq.SaveOptions> :

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

Seçeneği girintileme ve XML ağacındaki önemli boşlukları korumak istiyorsanız bağımsız değişken olarak kullanılan aşağıdaki yöntemlerin aşırı yüklemelerinin birini kullanın <xref:System.Xml.Linq.SaveOptions> :

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

Örnekler için, ilgili başvuru konusuna bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [XML ağaçlarını serileştirme (Visual Basic)](serializing-xml-trees.md)
