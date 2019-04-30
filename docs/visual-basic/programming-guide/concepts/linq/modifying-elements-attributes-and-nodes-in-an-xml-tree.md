---
title: Öğe, öznitelik ve düğümleri bir XML Tree1 değiştirme
ms.date: 07/20/2015
ms.assetid: 865cf54e-f8ac-4871-863b-a3e6fc61a4b9
ms.openlocfilehash: d548e6f5912437e5c5df27f55fcdb28990e92c8d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61666150"
---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a>XML Ağacındaki Öğe, Öznitelik ve Düğümleri Değiştirme
Bir öğe, alt öğelerini ve özniteliklerini değiştirmek için kullanabileceğiniz özellikler ve yöntemler aşağıdaki tabloda özetlenmiştir.  
  
 Aşağıdaki yöntemlerden değiştirme bir <xref:System.Xml.Linq.XElement>.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>|Bir öğe ayrıştırılmış XML ile değiştirir.|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|Bir öğenin tüm içeriğin (alt düğümleri ve öznitelikleri) kaldırır.|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|Bir öğenin öznitelikleri kaldırır.|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=nameWithType>|Bir öğenin tüm içeriğin (alt düğümleri ve öznitelikleri) değiştirir.|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=nameWithType>|Bir öğenin öznitelikleri değiştirir.|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|Bir özniteliğin değerini ayarlar. Öznitelik yoksa oluşturur. Değer ayarlanmışsa `null`, öznitelik kaldırır.|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|Bir alt öğenin değerini ayarlar. Öğe yoksa oluşturur. Değer ayarlanmışsa `null`, öğeyi kaldırır.|  
|<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>|Bir öğenin içeriğini (alt düğümleri) belirtilen metinle değiştirir.|  
|<xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=nameWithType>|Bir öğenin değerini ayarlar.|  
  
 Aşağıdaki yöntemlerden değiştirme bir <xref:System.Xml.Linq.XAttribute>.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>|Bir özniteliğin değerini ayarlar.|  
|<xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=nameWithType>|Bir özniteliğin değerini ayarlar.|  
  
 Aşağıdaki yöntemlerden değiştirme bir <xref:System.Xml.Linq.XNode> (dahil olmak üzere bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument>).  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=nameWithType>|Bir düğüm, yeni içerikle değiştirir.|  
  
 Aşağıdaki yöntemlerden değiştirme bir <xref:System.Xml.Linq.XContainer> (bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument>).  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=nameWithType>|Alt düğüm, yeni içerikle değiştirir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [(LINQ to XML) XML ağaçlarını değiştirme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
