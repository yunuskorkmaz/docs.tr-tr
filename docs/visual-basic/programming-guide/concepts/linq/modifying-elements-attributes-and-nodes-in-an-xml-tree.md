---
title: XML Tree1 içinde öğeleri, öznitelikleri ve düğümleri değiştirme
ms.date: 07/20/2015
ms.assetid: 865cf54e-f8ac-4871-863b-a3e6fc61a4b9
ms.openlocfilehash: 002e87d58ad1a3730889225bf4b3e50448431f2d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360936"
---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a>XML Ağacındaki Öğe, Öznitelik ve Düğümleri Değiştirme
Aşağıdaki tabloda bir öğe, alt öğeleri veya özniteliklerini değiştirmek için kullanabileceğiniz yöntemler ve Özellikler özetlenmektedir.  
  
 Aşağıdaki yöntemler bir değiştirir <xref:System.Xml.Linq.XElement> .  
  
|Yöntem|Description|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>|Bir öğeyi ayrıştırılmış XML ile değiştirir.|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|Bir öğenin tüm içeriğini (alt düğümleri ve öznitelikleri) kaldırır.|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|Bir öğenin özniteliklerini kaldırır.|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=nameWithType>|Bir öğenin tüm içeriğini (alt düğümleri ve öznitelikleri) değiştirir.|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=nameWithType>|Bir öğenin özniteliklerini değiştirir.|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|Bir özniteliğin değerini ayarlar. Mevcut değilse özniteliği oluşturur. Değer olarak ayarlanırsa `null` , özniteliğini kaldırır.|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|Bir alt öğenin değerini ayarlar. Yoksa, öğesini oluşturur. Değer olarak ayarlanırsa `null` , öğesini kaldırır.|  
|<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>|Bir öğenin içeriğini (alt düğümleri) belirtilen metinle değiştirir.|  
|<xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=nameWithType>|Bir öğenin değerini ayarlar.|  
  
 Aşağıdaki yöntemler bir değiştirir <xref:System.Xml.Linq.XAttribute> .  
  
|Yöntem|Description|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>|Bir özniteliğin değerini ayarlar.|  
|<xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=nameWithType>|Bir özniteliğin değerini ayarlar.|  
  
 Aşağıdaki yöntemler bir ' i <xref:System.Xml.Linq.XNode> (veya dahil <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> ) değiştirir.  
  
|Yöntem|Description|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=nameWithType>|Bir düğümü yeni içerikle değiştirir.|  
  
 Aşağıdaki yöntemler bir <xref:System.Xml.Linq.XContainer> ( <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument> ) değiştirir.  
  
|Yöntem|Description|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=nameWithType>|Alt düğümleri yeni içerikle değiştirir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML ağaçlarını değiştirme (LINQ to XML) (Visual Basic)](modifying-xml-trees-linq-to-xml.md)
