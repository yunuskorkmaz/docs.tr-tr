---
title: Öğeleri, öznitelikleri ve bir XML Tree1 düğümler değiştirme
ms.date: 07/20/2015
ms.assetid: 865cf54e-f8ac-4871-863b-a3e6fc61a4b9
ms.openlocfilehash: 91a7cca2e39e5ddc62d6010fbe4efad9bd7ff3c2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33645219"
---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a>Öğeleri, öznitelikleri ve bir XML ağacında düğümlerin değiştirme
Bir öğe, alt öğelerini veya özniteliklerini değiştirmek için kullanabileceğiniz özellikler ve yöntemler aşağıdaki tabloda özetlenmiştir.  
  
 Aşağıdaki yöntemlerden değiştirme bir <xref:System.Xml.Linq.XElement>.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>|Bir öğenin ayrıştırılmış XML ile değiştirir.|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|Bir öğenin tüm içeriğin (alt düğümleri ve öznitelikleri) kaldırır.|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|Bir öğenin öznitelikleri kaldırır.|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=nameWithType>|Bir öğenin tüm içeriğin (alt düğümleri ve öznitelikleri) yerini alır.|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=nameWithType>|Bir öğenin özniteliklerini değiştirir.|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|Özniteliğin değerini ayarlar. Öznitelik yoksa oluşturur. Değer ayarlanmışsa `null`, öznitelik kaldırır.|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|Bir alt öğenin değerini ayarlar. Yoksa öğesi oluşturur. Değer ayarlanmışsa `null`, öğeyi kaldırır.|  
|<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>|Bir öğenin içeriğini (alt düğümler) belirtilen metinle değiştirir.|  
|<xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=nameWithType>|Bir öğenin değerini ayarlar.|  
  
 Aşağıdaki yöntemlerden değiştirme bir <xref:System.Xml.Linq.XAttribute>.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>|Özniteliğin değerini ayarlar.|  
|<xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=nameWithType>|Özniteliğin değerini ayarlar.|  
  
 Aşağıdaki yöntemlerden değiştirme bir <xref:System.Xml.Linq.XNode> (dahil olmak üzere bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument>).  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=nameWithType>|Bir düğüm yeni içerikle değiştirir.|  
  
 Aşağıdaki yöntemlerden değiştirme bir <xref:System.Xml.Linq.XContainer> (bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument>).  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=nameWithType>|Alt düğümler ile yeni içerik değiştirir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML ağaçları (LINQ-XML) değiştirme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
