---
title: Dosya, TextWriters ve XmlWriters Serileştirme
ms.date: 07/20/2015
ms.assetid: bd3ea6f7-895b-4ff4-a625-fe2bb55b1886
ms.openlocfilehash: 20cb84a9f79ca8de3e86a996f18c388dc53340ae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "68868851"
---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a>Dosya, TextWriters ve XmlWriters Serileştirme

XML ağaçlarını bir <xref:System.IO.File>, a <xref:System.IO.TextWriter>veya <xref:System.Xml.XmlWriter>bir .

Yöntemi kullanarak <xref:System.Xml.Linq.XDocument> <xref:System.Xml.Linq.XElement> `ToString` herhangi bir XML bileşenini bir dize dahil ve seri hale getirebilirsiniz.

Bir dize serihale zaman biçimlendirmebastırmak istiyorsanız, <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> yöntemi kullanabilirsiniz.

Bir dosyaya serileştirme yaparken varsayılan davranış, ortaya çıkan XML belgesini biçimlendirmek (girinti) yapmaktır. Girintisi yaptığınızda, XML ağacındaki önemsiz beyaz boşluk korunmaz. Biçimlendirme ile serihale getirmek için, bağımsız değişken olarak kabul <xref:System.Xml.Linq.SaveOptions> etmeyen aşağıdaki yöntemlerin aşırı yüklerinden birini kullanın:

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

XML ağacındaki önemsiz beyaz alanı girinti yapmama ve koruma seçeneğini zedelemiyorsanız, aşağıdaki yöntemlerin <xref:System.Xml.Linq.SaveOptions> aşırı yüklerinden birini kullanarak bağımsız değişken olarak alır:

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

Örnekler için, uygun başvuru konusuna bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [XML Ağaçlarını Serihale Getirme (C#)](serializing-to-files-textwriters-and-xmlwriters.md)
