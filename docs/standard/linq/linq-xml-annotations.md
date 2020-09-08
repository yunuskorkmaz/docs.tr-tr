---
title: Ek açıklamalar-LINQ to XML
description: Bir XML ağacındaki herhangi bir XML bileşeniyle herhangi bir rastgele türdeki herhangi bir rastgele nesneyi ilişkilendirmek için LINQ to XML ek açıklamaları nasıl kullanacağınızı öğrenin.
ms.date: 07/20/2015
ms.assetid: 54e7b9d0-07f5-488f-9065-b6e6b870f810
ms.openlocfilehash: 80710b3596fc37ed76f23e31d1d781c64d0bc909
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553366"
---
# <a name="linq-to-xml-annotations-linq-to-xml"></a>LINQ to XML ek açıklamaları (LINQ to XML)

LINQ to XML ek açıklamaları bir XML ağacındaki herhangi bir XML bileşeniyle herhangi bir rastgele türdeki herhangi bir rastgele nesneyi ilişkilendirmenizi sağlar.

Bir XML bileşenine bir veya gibi bir ek açıklama eklemek için <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XAttribute> <xref:System.Xml.Linq.XObject.AddAnnotation%2A> yöntemini çağırın. Ek açıklamaları türe göre alırsınız.

Ek açıklamaların XML bilgi kümesinin bir parçası olmadığı unutulmamalıdır; Bunlar serileştirilmez veya seri durumdan çıkarılmaz.

## <a name="methods"></a>Yöntemler

Ek açıklamalarla çalışırken aşağıdaki yöntemleri kullanabilirsiniz:

|Yöntem|Açıklama|
|------------|-----------------|
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|Ek açıklama listesine bir nesne ekler <xref:System.Xml.Linq.XObject> .|
|<xref:System.Xml.Linq.XObject.Annotation%2A>|Belirtilen türdeki ilk ek açıklama nesnesini bir kaynağından alır <xref:System.Xml.Linq.XObject> .|
|<xref:System.Xml.Linq.XObject.Annotations%2A>|İçin belirtilen türde ek açıklamaların bir koleksiyonunu alır <xref:System.Xml.Linq.XObject> .|
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|Belirtilen türdeki ek açıklamaları bir öğesinden kaldırır <xref:System.Xml.Linq.XObject> .|
