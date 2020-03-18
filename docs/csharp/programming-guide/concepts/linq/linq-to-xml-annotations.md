---
title: LinQ - XML Ek Açıklamaları3
ms.date: 07/20/2015
ms.assetid: 54e7b9d0-07f5-488f-9065-b6e6b870f810
ms.openlocfilehash: 5f1940be2fc126ff9e9c7a4cb37e5cc7fc95d3c3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "66689949"
---
# <a name="linq-to-xml-annotations"></a>LINQ to XML Ek Açıklamaları

Herhangi [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] bir rasgele türdeki herhangi bir rasgele nesneyi XML ağacındaki herhangi bir XML bileşeniyle ilişkilendirmenize olanak tanıyan ek açıklamalar.

XML bileşenine bir <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XAttribute>ek açıklama eklemek için , <xref:System.Xml.Linq.XObject.AddAnnotation%2A> yöntemi çağırırsınız. Ek açıklamaları türüne göre alırsınız.

Ek açıklamaların XML bilgi kümesinin bir parçası olmadığını unutmayın; serileştirilmeyecek veya serileştirilmeyecektir.

## <a name="methods"></a>Yöntemler

Ek açıklamalarla çalışırken aşağıdaki yöntemleri kullanabilirsiniz:

|Yöntem|Açıklama|
|------------|-----------------|
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|Bir <xref:System.Xml.Linq.XObject>' in ek açıklama listesine bir nesne ekler|
|<xref:System.Xml.Linq.XObject.Annotation%2A>|Belirtilen türün ilk ek açıklama nesnesini <xref:System.Xml.Linq.XObject>bir .'den alır|
|<xref:System.Xml.Linq.XObject.Annotations%2A>|Bir <xref:System.Xml.Linq.XObject>. için belirtilen türdeki ek açıklamalar koleksiyonunu alır.|
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|Belirtilen türdeki ek açıklamaları bir <xref:System.Xml.Linq.XObject>'den kaldırır.|
