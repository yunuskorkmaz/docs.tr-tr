---
title: LINQ to XML Annotations2
ms.date: 07/20/2015
ms.assetid: c3e8b3ff-fceb-4428-b0ca-1ed6f128aac8
ms.openlocfilehash: 891c451bc573e41e26833878187224cf54510435
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566859"
---
# <a name="linq-to-xml-annotations"></a>LINQ to XML ek açıklamaları
Ek açıklamalarda [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] rasgele türden herhangi bir rastgele nesne XML ağacındaki herhangi bir XML bileşeni ile ilişkilendirilecek olanak sağlar.  
  
 Ek açıklamanın gibi bir XML bileşenine eklemek için bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XAttribute>, çağırmanızı <xref:System.Xml.Linq.XObject.AddAnnotation%2A> yöntemi. Türe göre ek açıklamaları aldığınız.  
  
 Ek açıklamaları XML bilgi kümesi parçası olmadığını unutmayın; Kullanıcılar seri durumdan veya.  
  
## <a name="methods"></a>Yöntemler  
 Ek açıklamalar ile çalışırken aşağıdaki yöntemleri kullanabilirsiniz:  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|Bir nesne ekler, ek açıklama listesine bir <xref:System.Xml.Linq.XObject>.|  
|<xref:System.Xml.Linq.XObject.Annotation%2A>|Belirtilen türden ilk ek açıklama nesnesinin alır bir <xref:System.Xml.Linq.XObject>.|  
|<xref:System.Xml.Linq.XObject.Annotations%2A>|Ek açıklamalar için belirtilen türün bir koleksiyonunu alır bir <xref:System.Xml.Linq.XObject>.|  
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|Ek açıklamalar, belirtilen türden kaldırır bir <xref:System.Xml.Linq.XObject>.|  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Gelişmiş LINQ to XML programlama (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
