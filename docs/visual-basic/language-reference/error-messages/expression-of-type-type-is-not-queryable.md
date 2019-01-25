---
title: Türündeki ifade &lt;türü&gt; sorgulanabilir değil
ms.date: 07/20/2015
f1_keywords:
- bc36593
- vbc36593
helpviewer_keywords:
- BC36593
ms.assetid: 6f1f5860-bf97-4885-9ebb-bc87d028095c
ms.openlocfilehash: ce0831e0770e5733759c072b8d7c6f20b56f771b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521497"
---
# <a name="expression-of-type-lttypegt-is-not-queryable"></a>Türündeki ifade &lt;türü&gt; sorgulanabilir değil
Türündeki ifade \<türü > sorgulanabilir değil. Bir derleme başvurusunun ve/veya ad alanı alma LINQ sağlayıcısı için eksik olmadığından emin olun.  
  
 Sorgulanabilir türleri <xref:System.Linq>, <xref:System.Data.Linq>, ve <xref:System.Xml.Linq> ad alanları. Bir veya daha fazla LINQ sorguları gerçekleştirmek için bu ad alanları içeri aktarmanız gerekir.  
  
 <xref:System.Linq> Ad alanı sağlar, koleksiyonlar ve diziler gibi sorgu nesnelere LINQ kullanarak.  
  
 <xref:System.Data.Linq> Ad alanı, ADO.NET veri kümeleri ve SQL Server veritabanlarını LINQ kullanarak sorgulama olanak tanır.  
  
 <xref:System.Xml.Linq> Ad alanı sayesinde sorgu XML'i LINQ kullanarak ve Visual Basic'te XML özellikleri kullanmak için.  
  
 **Hata Kimliği:** BC36593  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Ekleme bir `Import` bildirimi <xref:System.Linq>, <xref:System.Data.Linq>, veya <xref:System.Xml.Linq> kod dosyanıza ad alanı. Kullanarak projeniz için ad alanları aktarabilirsiniz **başvuruları** sayfası Proje Tasarımcısı (**Projem**).  
  
2.  Sorgulanabilir tür kaynak sorgunuzun olduğu gibi belirlediğiniz türü emin olun. Diğer bir deyişle, uygulayan bir tür <xref:System.Collections.Generic.IEnumerable%601> veya <xref:System.Linq.IQueryable%601>.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Linq>
- <xref:System.Data.Linq>
- <xref:System.Xml.Linq>
- [Visual Basic'de LINQ'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [LINQ](../../../visual-basic/programming-guide/language-features/linq/index.md)
- [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)
- [References ve Imports Deyimi](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)
- [Imports Deyimi (.NET Ad Alanı ve Türü)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Başvurular Sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)
