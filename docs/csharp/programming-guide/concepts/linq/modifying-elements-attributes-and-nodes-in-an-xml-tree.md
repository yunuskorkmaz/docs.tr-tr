---
title: XML Ağacındaki Öğeleri, Öznitelikleri ve Düğümleri Değiştirme3
ms.date: 07/20/2015
ms.assetid: 0ed22e4e-4c6b-4eb1-b0eb-06685efd8c33
ms.openlocfilehash: 93a4d67129e22d0bbeef464c1d4d8758439edb7b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "66484237"
---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a>XML Ağacındaki Öğe, Öznitelik ve Düğümleri Değiştirme
Aşağıdaki tablo, bir öğeyi, alt öğelerini veya özniteliklerini değiştirmek için kullanabileceğiniz yöntemleri ve özellikleri özetler.  
  
 Aşağıdaki yöntemler bir. <xref:System.Xml.Linq.XElement>  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>|Bir öğeyi ayrışmış XML ile değiştirir.|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|Bir öğenin tüm içeriğini (alt düğümleri ve öznitelikleri) kaldırır.|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|Bir öğenin özniteliklerini kaldırır.|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=nameWithType>|Bir öğenin tüm içeriğini (alt düğümleri ve öznitelikleri) değiştirir.|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=nameWithType>|Bir öğenin özniteliklerini değiştirir.|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|Bir özniteliğin değerini ayarlar. Yoksa öznitelik oluşturur. Değer `null`ayarlanmışsa, özniteliği kaldırır.|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|Bir alt öğenin değerini ayarlar. Yoksa öğeyi oluşturur. Değer `null`ayarlanmışsa, öğeyi kaldırır.|  
|<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>|Bir öğenin içeriğini (alt düğümleri) belirtilen metinle değiştirir.|  
|<xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=nameWithType>|Bir öğenin değerini ayarlar.|  
  
 Aşağıdaki yöntemler bir. <xref:System.Xml.Linq.XAttribute>  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>|Bir özniteliğin değerini ayarlar.|  
|<xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=nameWithType>|Bir özniteliğin değerini ayarlar.|  
  
 Aşağıdaki yöntemler bir <xref:System.Xml.Linq.XNode> (bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument>dahil) değiştirmek.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=nameWithType>|Düğümü yeni içerikle değiştirir.|  
  
 Aşağıdaki yöntemler bir <xref:System.Xml.Linq.XContainer> <xref:System.Xml.Linq.XElement> (bir <xref:System.Xml.Linq.XDocument>veya) değiştirmek.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=nameWithType>|Çocuk düğümlerini yeni içerikle değiştirir.|  
