---
title: Dosyalar, TextWriters ve Xmlyazıcılarında serileştirme-LINQ to XML
description: XML ağaçlarını bir dosya, bir TextWriter veya XmlWriter 'a seri hale getirebilirsiniz ve XDocument ve XElement dahil XML bileşenlerini ToString yöntemini kullanarak bir dizeye seri hale getirebilirsiniz.
ms.date: 07/20/2015
ms.assetid: bd3ea6f7-895b-4ff4-a625-fe2bb55b1886
ms.openlocfilehash: 20651c06a759d83934c4b035a42eac7c2700eb9f
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553929"
---
# <a name="serialize-to-files-textwriters-and-xmlwriters-linq-to-xml"></a>Dosyalar, TextWriters ve Xmlyazıcılarında serileştirme (LINQ to XML)

XML ağaçlarını bir, a veya olarak seri hale getirebilirsiniz <xref:System.IO.File> <xref:System.IO.TextWriter> <xref:System.Xml.XmlWriter> .

Yöntemini kullanarak, ve dahil olmak üzere herhangi bir XML bileşenini bir dizeye seri hale getirebilirsiniz <xref:System.Xml.Linq.XDocument> <xref:System.Xml.Linq.XElement> `ToString` .

Bir dizeye serileştirilirken biçimlendirmeyi bastırmak istiyorsanız <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> yöntemini kullanabilirsiniz.

Bir dosyaya serileştirilirken varsayılan davranış, elde edilen XML belgesini biçimlendirmek (Girintile). Girinti yaptığınızda XML ağacındaki önemli boşluk korunmaz. Biçimlendirme ile seri hale getirmek için, aşağıdaki yöntemlerin bağımsız değişken olarak olmayan aşırı yüklemelerinin birini kullanın <xref:System.Xml.Linq.SaveOptions> :

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

Seçeneği girintileme ve XML ağacındaki önemli boşlukları korumak istiyorsanız bağımsız değişken olarak kullanılan aşağıdaki yöntemlerin aşırı yüklemelerinin birini kullanın <xref:System.Xml.Linq.SaveOptions> :

- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>

Örnekler için ilgili başvuru makalesine bakın.
