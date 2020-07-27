---
title: LINQ to XML Ek Açıklamaları
description: Bir XML ağacındaki herhangi bir XML bileşeniyle herhangi bir rastgele türdeki herhangi bir rastgele nesneyi ilişkilendirmek için LINQ to XML ek açıklamaları nasıl kullanacağınızı öğrenin.
ms.date: 07/20/2015
ms.assetid: 54e7b9d0-07f5-488f-9065-b6e6b870f810
ms.openlocfilehash: e7da666139c10b26de37816693202d96498f52d8
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165571"
---
# <a name="linq-to-xml-annotations"></a>LINQ to XML Ek Açıklamaları

İçindeki ek açıklamalar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] BIR XML ağacındaki herhangi BIR XML bileşeniyle herhangi bir rastgele türdeki herhangi bir rastgele nesneyi ilişkilendirmenizi sağlar.

Bir XML bileşenine bir veya gibi bir ek açıklama eklemek için <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XAttribute> <xref:System.Xml.Linq.XObject.AddAnnotation%2A> yöntemini çağırın. Ek açıklamaları türe göre alırsınız.

Ek açıklamaların XML bilgi kümesinin bir parçası olmadığına unutmayın; Bunlar serileştirilmez veya seri durumdan çıkarılmaz.

## <a name="methods"></a>Yöntemler

Ek açıklamalarla çalışırken aşağıdaki yöntemleri kullanabilirsiniz:

|Yöntem|Açıklama|
|------------|-----------------|
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|Ek açıklama listesine bir nesne ekler <xref:System.Xml.Linq.XObject> .|
|<xref:System.Xml.Linq.XObject.Annotation%2A>|Belirtilen türdeki ilk ek açıklama nesnesini bir kaynağından alır <xref:System.Xml.Linq.XObject> .|
|<xref:System.Xml.Linq.XObject.Annotations%2A>|İçin belirtilen türde ek açıklamaların bir koleksiyonunu alır <xref:System.Xml.Linq.XObject> .|
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|Belirtilen türdeki ek açıklamaları bir öğesinden kaldırır <xref:System.Xml.Linq.XObject> .|
