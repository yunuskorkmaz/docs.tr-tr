---
title: XML Ağacındaki Öğe, Öznitelik ve Düğümleri Değiştirme
description: Bir öğeyi, alt düğümlerini veya özniteliklerini değiştirmek için kullanabileceğiniz yöntemler ve özellikler hakkında bilgi edinin.
ms.date: 07/20/2015
ms.assetid: 0ed22e4e-4c6b-4eb1-b0eb-06685efd8c33
ms.openlocfilehash: 671ba38350e443d95c92a9bd790eac3d2deb5cdd
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553907"
---
# <a name="modify-elements-attributes-and-nodes-in-an-xml-tree-linq-to-xml"></a>XML ağacındaki öğeleri, öznitelikleri ve düğümleri değiştirme (LINQ to XML)

Aşağıdaki tabloda bir öğe, alt öğeleri veya özniteliklerini değiştirmek için kullanabileceğiniz yöntemler ve Özellikler özetlenmektedir.

Aşağıdaki yöntemler bir değiştirme <xref:System.Xml.Linq.XElement> :

|Yöntem|Açıklama|
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

Aşağıdaki yöntemler bir değiştirme <xref:System.Xml.Linq.XAttribute> :

|Yöntem|Açıklama|
|------------|-----------------|
|<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>|Bir özniteliğin değerini ayarlar.|
|<xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=nameWithType>|Bir özniteliğin değerini ayarlar.|

 Aşağıdaki yöntemler <xref:System.Xml.Linq.XNode> (veya dahil) öğesini değiştirir <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> :

|Yöntem|Açıklama|
|------------|-----------------|
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=nameWithType>|Bir düğümü yeni içerikle değiştirir.|

 Aşağıdaki yöntemler bir <xref:System.Xml.Linq.XContainer> ( <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument> ) değiştirir:

|Yöntem|Açıklama|
|------------|-----------------|
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=nameWithType>|Alt düğümleri yeni içerikle değiştirir:|
