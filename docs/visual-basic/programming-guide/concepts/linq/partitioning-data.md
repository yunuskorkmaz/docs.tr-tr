---
title: "Bölümleme veri (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 69c59379-b66e-422c-b324-5b5c07760ef7
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0ea305a67765e1b11ceebbf65c48a685024a41f3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="partitioning-data-visual-basic"></a>Bölümleme veri (Visual Basic)
LINQ bölümlendirme öğeleri yeniden düzenleme ve bölümlerden biri döndürme olmadan bir giriş sırası iki bölümlere ayırma işlemi ifade eder.  
  
 Aşağıdaki çizim üç farklı bölümleme işlemlerde bir dizi karakter sonuçlarını gösterir. İlk işlemi ilk üç öğeleri dizisi döndürür. İkinci bir işlem ilk üç öğeleri atlar ve kalan öğeleri döndürür. Üçüncü işlem sırası ilk iki öğeleri atlar ve sonraki üç öğeleri döndürür.  
  
 ![LINQ işlemleri bölümleme](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")  
  
 Dizileri bölüm standart sorgu işleci yöntemler aşağıdaki bölümde listelenmektedir.  
  
## <a name="operators"></a>İşleçler  
  
|İşleç Adı|Açıklama|Visual Basic sorgu ifade sözdizimi|Daha Fazla Bilgi|  
|-------------------|-----------------|------------------------------------------|----------------------|  
|Atla|Öğeleri bir sırada belirtilen konum kadar atlar.|`Skip`|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|SkipWhile|Bir öğe koşulu karşılamadığı kadar bir koşul işlevine bağlı öğeleri atlar.|`Skip While`|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|Take|Öğeleri bir sırada belirtilen konum kadar sürer.|`Take`|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|TakeWhile|Bir öğe koşulu karşılamadığı kadar bir koşul işlevine bağlı öğeleri alır.|`Take While`|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Sorgu ifade sözdizimi örnekleri  
  
### <a name="skip"></a>Atla  
 Aşağıdaki kod örneğinde `Skip` yan tümcesinde [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kalan dizeleri dizideki döndürmeden önce bir dizeler dizisi ilk dört dizelerde üzerinden atlanacak.  
  
 [!code-vb[CsLINQPartitioning#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_1.vb)]  
  
### <a name="skipwhile"></a>SkipWhile  
 Aşağıdaki kod örneğinde `Skip While` yan tümcesinde [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] dizenin ilk harfi sırasında bir dizi dizelerde atlamayı için "a". Dizi kalan dizelerde döndürülür.  
  
 [!code-vb[CsLINQPartitioning#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_2.vb)]  
  
### <a name="take"></a>Take  
 Aşağıdaki kod örneğinde `Take` yan tümcesinde [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] bir dizeler dizisi ilk iki dizeyi dönün.  
  
 [!code-vb[CsLINQPartitioning#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_3.vb)]  
  
### <a name="takewhile"></a>TakeWhile  
 Aşağıdaki kod örneğinde `Take While` yan tümcesinde [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] beş veya daha az dize uzunluğu iken dizeleri dizisinden dönün.  
  
 [!code-vb[CsLINQPartitioning#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_4.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Linq>  
 [Standart sorgu işleçlerine genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Skip tümcesi](../../../../visual-basic/language-reference/queries/skip-clause.md)  
 [Skip While tümcesi](../../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [Take tümcesi](../../../../visual-basic/language-reference/queries/take-clause.md)  
 [Take While tümcesi](../../../../visual-basic/language-reference/queries/take-while-clause.md)
