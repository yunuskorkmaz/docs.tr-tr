---
title: <type> türündeki ifade sorgulanabilir değil
ms.date: 07/20/2015
f1_keywords:
- bc36593
- vbc36593
helpviewer_keywords:
- BC36593
ms.assetid: 6f1f5860-bf97-4885-9ebb-bc87d028095c
ms.openlocfilehash: e61b4dac109f714b5cf25226d1029237ca77032d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409484"
---
# <a name="expression-of-type-type-is-not-queryable"></a>\<type> türündeki ifade sorgulanabilir değil
Türündeki ifade \<type> sorgulanabilir değil. LINQ sağlayıcısı için bir derleme başvurusu ve/veya ad alanı içeri aktarma olmadığından emin olun.  
  
 Sorgulanabilir türler <xref:System.Linq> ,, <xref:System.Data.Linq> ve <xref:System.Xml.Linq> ad alanlarında tanımlanmıştır. LINQ sorguları gerçekleştirmek için bu ad alanlarından bir veya daha fazlasını içeri aktarmanız gerekir.  
  
 <xref:System.Linq>Ad alanı, LINQ kullanarak koleksiyonlar ve diziler gibi nesneleri sorgulamanızı sağlar.  
  
 <xref:System.Data.Linq>Ad alanı, LINQ kullanarak ADO.NET veri kümelerini ve SQL Server veritabanlarını sorgulamanızı sağlar.  
  
 <xref:System.Xml.Linq>Ad alanı, LINQ kullanarak XML sorgusu yapmanızı ve VISUAL BASIC xml özelliklerini kullanmayı sağlar.  
  
 **Hata kimliği:** BC36593  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. `Import` <xref:System.Linq> <xref:System.Data.Linq> Kod dosyanıza, veya ad alanı için bir ifade ekleyin <xref:System.Xml.Linq> . Ayrıca, proje Tasarımcısı 'nın (**projem**) **Başvurular** sayfasını kullanarak projenizin ad alanlarını içeri aktarabilirsiniz.  
  
2. Sorgunuzun kaynağı olarak tanımladığınız türün sorgulanabilir bir tür olduğundan emin olun. Diğer bir deyişle, veya uygulayan bir <xref:System.Collections.Generic.IEnumerable%601> tür <xref:System.Linq.IQueryable%601> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq>
- <xref:System.Data.Linq>
- <xref:System.Xml.Linq>
- [Visual Basic'de LINQ'e Giriş](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [LINQ](../../programming-guide/language-features/linq/index.md)
- [XML](../../programming-guide/language-features/xml/index.md)
- [References ve Imports Deyimi](../../programming-guide/program-structure/references-and-the-imports-statement.md)
- [Imports Deyimi (.NET Ad Alanı ve Türü)](../statements/imports-statement-net-namespace-and-type.md)
- [Başvurular Sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)
