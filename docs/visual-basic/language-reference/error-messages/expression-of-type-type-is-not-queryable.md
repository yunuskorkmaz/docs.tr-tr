---
title: "İfade türü &lt;türü&gt; sorgulanabilir değil"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36593
- vbc36593
helpviewer_keywords: BC36593
ms.assetid: 6f1f5860-bf97-4885-9ebb-bc87d028095c
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3f2b98bf48f0b3965929f9211c2944ff97754f23
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="expression-of-type-lttypegt-is-not-queryable"></a>İfade türü &lt;türü&gt; sorgulanabilir değil
İfade türü \<türü > sorgulanabilir değil. Size bir derleme başvurusu ve/veya ad alanı içe aktarma için LINQ sağlayıcısı eksik değil emin olun.  
  
 Sorgulanabilir türleri tanımlanmış <xref:System.Linq>, <xref:System.Data.Linq>, ve <xref:System.Xml.Linq> ad alanları. Bir veya daha fazla LINQ sorgularını gerçekleştirmek için bu ad alanları içeri aktarmanız gerekir.  
  
 <xref:System.Linq> Ad alanı sağlar, koleksiyonlar ve dizi gibi sorgu nesnelere LINQ kullanarak.  
  
 <xref:System.Data.Linq> Ad alanı LINQ kullanarak sorgu ADO.NET veri kümeleri ve SQL Server veritabanlarını olanak sağlar.  
  
 <xref:System.Xml.Linq> Ad alanı sağlar, sorgu XML'i LINQ kullanarak ve Visual Basic'te XML özellikleri kullanmak için.  
  
 **Hata Kimliği:** BC36593  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Ekleme bir `Import` bildirimi <xref:System.Linq>, <xref:System.Data.Linq>, veya <xref:System.Xml.Linq> kodu dosyanıza ad alanı. Kullanarak projeniz için ad alanları aktarabilirsiniz **başvuruları** sayfası Proje Tasarımcısı'nın (**My proje**).  
  
2.  Sorgunuzun kaynak sorgulanabilir bir türü olarak tanımlanmış türü emin olun. Diğer bir deyişle, uygulayan bir tür <xref:System.Collections.Generic.IEnumerable%601> veya <xref:System.Linq.IQueryable%601>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Linq>  
 <xref:System.Data.Linq>  
 <xref:System.Xml.Linq>  
 [Visual Basic'de LINQ'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [LINQ](../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [References ve Imports deyimi](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 [Imports deyimi (.NET Namespace ve türü)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [Başvurular sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)
