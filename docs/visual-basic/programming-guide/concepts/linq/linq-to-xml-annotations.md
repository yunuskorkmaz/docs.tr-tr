---
title: LINQ to XML Annotations2
ms.date: 07/20/2015
ms.assetid: c3e8b3ff-fceb-4428-b0ca-1ed6f128aac8
ms.openlocfilehash: 917129a06483ce2001e178d744440504533d28d6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84369017"
---
# <a name="linq-to-xml-annotations"></a>LINQ to XML Ek Açıklamaları
İçindeki ek açıklamalar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] BIR XML ağacındaki herhangi BIR XML bileşeniyle herhangi bir rastgele türdeki herhangi bir rastgele nesneyi ilişkilendirmenizi sağlar.  
  
 Bir XML bileşenine bir veya gibi bir ek açıklama eklemek için <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XAttribute> <xref:System.Xml.Linq.XObject.AddAnnotation%2A> yöntemini çağırın. Ek açıklamaları türe göre alırsınız.  
  
 Ek açıklamaların XML bilgi kümesinin bir parçası olmadığına unutmayın; Bunlar serileştirilmez veya seri durumdan çıkarılmaz.  
  
## <a name="methods"></a>Yöntemler  
 Ek açıklamalarla çalışırken aşağıdaki yöntemleri kullanabilirsiniz:  
  
|Yöntem|Description|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|Ek açıklama listesine bir nesne ekler <xref:System.Xml.Linq.XObject> .|  
|<xref:System.Xml.Linq.XObject.Annotation%2A>|Belirtilen türdeki ilk ek açıklama nesnesini bir kaynağından alır <xref:System.Xml.Linq.XObject> .|  
|<xref:System.Xml.Linq.XObject.Annotations%2A>|İçin belirtilen türde ek açıklamaların bir koleksiyonunu alır <xref:System.Xml.Linq.XObject> .|  
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|Belirtilen türdeki ek açıklamaları bir öğesinden kaldırır <xref:System.Xml.Linq.XObject> .|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Gelişmiş LINQ to XML Programlama (Visual Basic)](advanced-linq-to-xml-programming.md)
