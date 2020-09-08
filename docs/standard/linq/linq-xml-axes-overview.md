---
title: LINQ to XML eksenleri genel bakış-LINQ to XML
description: XML ağacındaki öğeleri bulmak ve değerlerini almak için XElement, XDocument ve IEnumerable sınıflarından eksen yöntemleri kullanın.
ms.date: 07/20/2015
ms.assetid: 516792fb-461d-40a8-8a50-9993a51258fc
ms.openlocfilehash: dd4018bbce52000bece4f737368b3807d229714a
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553349"
---
# <a name="linq-to-xml-axes-overview"></a>LINQ to XML eksenlerine genel bakış

Bir xml ağacını oluşturduktan veya bir XML ağacına bir XML belgesi yükledikten sonra, öğeleri ve öznitelikleri bulmak ve değerlerini almak için onu sorgulayabilirsiniz. Koleksiyonları, eksen olarak *da adlandırılan* *eksen yöntemleri*aracılığıyla alırsınız. Eksenlerden bazıları, <xref:System.Xml.Linq.XElement> ve <xref:System.Xml.Linq.XDocument> koleksiyonları döndüren sınıflarda yer alan yöntemlerdir <xref:System.Collections.Generic.IEnumerable%601> . Eksenlerden bazıları, sınıfındaki genişletme yöntemleridir <xref:System.Xml.Linq.Extensions> . Uzantı yöntemleri olarak uygulanan eksenler koleksiyonlar ve dönüş koleksiyonları üzerinde çalışır.

[XElement sınıfına genel bakış](xelement-class-overview.md)bölümünde açıklandığı gibi, bir <xref:System.Xml.Linq.XElement> nesne tek bir öğe düğümünü temsil eder. Bir öğenin içeriği karmaşık olabilir (bazen yapılandırılmış içerik olarak adlandırılır) veya basit bir öğe olabilir. Basit bir öğe boş olabilir veya bir değer içerebilir. Düğüm yapısal içerik içeriyorsa, alt öğelerin numaralandırmalar almak için çeşitli eksen yöntemlerini kullanabilirsiniz. En yaygın kullanılan eksen yöntemleri <xref:System.Xml.Linq.XContainer.Elements%2A> ve ' dir <xref:System.Xml.Linq.XContainer.Descendants%2A> .

Koleksiyonları döndüren eksen yöntemlerine ek olarak, LINQ to XML sorgularda yaygın olarak kullanabileceğiniz iki yöntem vardır. <xref:System.Xml.Linq.XContainer.Element%2A>Yöntemi tek bir döndürür <xref:System.Xml.Linq.XElement> . <xref:System.Xml.Linq.XElement.Attribute%2A>Yöntemi tek bir döndürür <xref:System.Xml.Linq.XAttribute> .

LINQ sorguları birçok amaçla bir ağacı incelemek, verileri dosyadan ayıklamak ve dönüştürmek için en güçlü yolu sağlar. LINQ sorguları, uygulayan nesneler ve koleksiyonlar <xref:System.Collections.Generic.IEnumerable%601> ve koleksiyonlar için LINQ to XML eksenleri üzerinde <xref:System.Collections.Generic.IEnumerable%601> çalışır <xref:System.Xml.Linq.XElement> <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XAttribute> . Sorgularınızı yapmak için bu koleksiyonlara ihtiyacınız vardır.

Öğe ve özniteliklerin koleksiyonlarını alan eksen yöntemlerine ek olarak, ağaç üzerinde harika ayrıntılarla yineleme yapmanızı sağlayan eksen yöntemleri vardır. Örneğin, öğeleri ve öznitelikleri kullanmak yerine, ağacın düğümleri ile çalışabilirsiniz. Düğümler, öğe ve özniteliklerin daha ayrıntılı bir düzeyde ayrıntı düzeyidir. Düğümlerle çalışırken, XML açıklamalarını, metin düğümlerini, işleme talimatlarını ve daha fazlasını inceleyebilirsiniz. Bu işlevsellik, örneğin, bir sözcük işlemcisi yazan ve belgeleri XML olarak kaydetmek isteyen bir kişiye önemlidir. Ancak, XML programcılarının çoğunluğu öncelikle öğeler, öznitelikler ve değerleri ile ilgilidir.

## <a name="methods-for-retrieving-a-collection-of-elements"></a>Öğe koleksiyonunu alma yöntemleri

Aşağıda bir <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XElement> öğe koleksiyonu döndürmek için üzerinde çağırdığınız sınıfının (veya temel sınıflarının) yöntemlerinin bir özeti verilmiştir.

|Yöntem|Açıklama|
|------------|-----------------|
|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|<xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> Bu öğenin üst öğelerinden birini döndürür. Aşırı yükleme <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> , belirtilen üst öğelerinden birini döndürür <xref:System.Xml.Linq.XName> .|
|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>|<xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> Bu öğenin alt öğelerinin birini döndürür. Aşırı yükleme <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> , belirtilen alt öğelerin birini döndürür <xref:System.Xml.Linq.XName> .|
|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|<xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> Bu öğenin alt öğelerinden birini döndürür. Aşırı yükleme <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> , belirtilen alt öğelerinden birini döndürür <xref:System.Xml.Linq.XName> .|
|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType>|<xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> Bu öğeden sonra gelen öğelerin birini döndürür. Aşırı yükleme <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> , belirtilen bu öğeden sonraki öğelerinden birini döndürür <xref:System.Xml.Linq.XName> .|
|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType>|<xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> Bu öğeden önce gelen öğelerin birini döndürür. Aşırı yükleme <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> , belirtilen bu öğeden önceki öğelerinden birini döndürür <xref:System.Xml.Linq.XName> .|
|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|<xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> Bu öğenin ve onun üst öğelerinden birini döndürür. Aşırı yükleme <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> , belirtilen öğelerinden birini döndürür <xref:System.Xml.Linq.XName> .|
|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType>|<xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> Bu öğenin ve alt öğelerinin birini döndürür. Aşırı yükleme <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> , belirtilen öğelerinden birini döndürür <xref:System.Xml.Linq.XName> .|

## <a name="method-for-retrieving-a-single-element"></a>Tek bir öğe alma yöntemi

Aşağıdaki yöntem bir nesneden tek bir alt öğe alır <xref:System.Xml.Linq.XElement> .

|Yöntem|Açıklama|
|------------|-----------------|
|<xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=nameWithType>|Belirtilen ilk alt <xref:System.Xml.Linq.XElement> nesneyi döndürür <xref:System.Xml.Linq.XName> .|

## <a name="method-for-retrieving-a-collection-of-attributes"></a>Özniteliklerin koleksiyonunu alma yöntemi

Aşağıdaki yöntem bir nesnesinden öznitelikleri alır <xref:System.Xml.Linq.XElement> .

|Yöntem|Açıklama|
|------------|-----------------|
|<xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|<xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XAttribute> Tüm özniteliklerin birini döndürür.|

## <a name="method-for-retrieving-a-single-attribute"></a>Tek bir özniteliği alma yöntemi

Aşağıdaki yöntem bir nesnesinden tek bir özniteliği alır <xref:System.Xml.Linq.XElement> .

|Yöntem|Açıklama|
|------------|-----------------|
|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType>|Belirtilen ' i döndürür <xref:System.Xml.Linq.XAttribute> <xref:System.Xml.Linq.XName> .|
