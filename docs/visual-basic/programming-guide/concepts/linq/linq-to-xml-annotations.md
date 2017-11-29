---
title: LINQ-XML Annotations2
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c3e8b3ff-fceb-4428-b0ca-1ed6f128aac8
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ca84af7cd750529eadb9d0967f4d5570b7038a07
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="linq-to-xml-annotations"></a>LINQ-XML ek açıklamaları
Ek açıklamalar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] herhangi bir rastgele nesne rasgele herhangi bir türde bir XML ağacındaki herhangi bir XML bileşeni ilişkilendirmek olanak sağlar.  
  
 Ek açıklamanın bir XML bileşene gibi eklemek için bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XAttribute>, çağırmanız <xref:System.Xml.Linq.XObject.AddAnnotation%2A> yöntemi. Türe göre ek açıklamalarını alır.  
  
 Ek Açıklamalar XML bilgi parçası olmadığını unutmayın; Bunlar seri durumdan veya güncelleştirilmez.  
  
## <a name="methods"></a>Yöntemler  
 Ek açıklamalar ile çalışırken aşağıdaki yöntemleri kullanabilirsiniz:  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|Ek açıklama listesine bir nesne ekler bir <xref:System.Xml.Linq.XObject>.|  
|<xref:System.Xml.Linq.XObject.Annotation%2A>|Belirtilen türden ilk ek açıklama nesnesinin alır bir <xref:System.Xml.Linq.XObject>.|  
|<xref:System.Xml.Linq.XObject.Annotations%2A>|Belirtilen tür için ek açıklamalar koleksiyonunu alır bir <xref:System.Xml.Linq.XObject>.|  
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|Belirtilen türden ek açıklamalar kaldırır bir <xref:System.Xml.Linq.XObject>.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Gelişmiş LINQ-XML programlama (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
