---
title: Dosya, TextWriters ve XmlWriters Serileştirme
ms.date: 07/20/2015
ms.assetid: bd3ea6f7-895b-4ff4-a625-fe2bb55b1886
ms.openlocfilehash: 20cb84a9f79ca8de3e86a996f18c388dc53340ae
ms.sourcegitcommit: 9ee6cd851b6e176a5811ea28ed0d5935c71950f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68868851"
---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a>Dosya, TextWriters ve XmlWriters Serileştirme

XML ağaçlarını bir <xref:System.IO.File>, a <xref:System.IO.TextWriter>veya <xref:System.Xml.XmlWriter>olarak seri hale getirebilirsiniz.

Yöntemini kullanarak, ve <xref:System.Xml.Linq.XDocument> <xref:System.Xml.Linq.XElement>dahil olmak üzere herhangi bir XML bileşenini bir dizeye seri hale getirebilirsiniz. `ToString`

Bir dizeye serileştirilirken biçimlendirmeyi bastırmak istiyorsanız <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> yöntemini kullanabilirsiniz.

Bir dosyaya serileştirilirken varsayılan davranış, elde edilen XML belgesini biçimlendirmek (Girintile). Girinti yaptığınızda XML ağacındaki önemli boşluk korunmaz. Biçimlendirme ile seri hale getirmek için, aşağıdaki yöntemlerin <xref:System.Xml.Linq.SaveOptions> bağımsız değişken olarak olmayan aşırı yüklemelerinin birini kullanın:

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

Seçeneği girintileme ve XML ağacındaki önemli boşlukları korumak istiyorsanız bağımsız değişken <xref:System.Xml.Linq.SaveOptions> olarak kullanılan aşağıdaki yöntemlerin aşırı yüklemelerinin birini kullanın:

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

Örnekler için, ilgili başvuru konusuna bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [XML ağaçlarını serileştirme (C#)](serializing-to-files-textwriters-and-xmlwriters.md)
