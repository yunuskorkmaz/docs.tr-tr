---
title: LINQ to XML Annotations3
ms.date: 07/20/2015
ms.assetid: 54e7b9d0-07f5-488f-9065-b6e6b870f810
ms.openlocfilehash: 19661f303ccea411ff6088005cb0198b50781d37
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66487396"
---
# <a name="linq-to-xml-annotations"></a>LINQ to XML Ek Açıklamaları
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
  
