---
title: where tümcesi (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- whereclause_CSharpKeyword
helpviewer_keywords:
- where keyword [C#]
- where clause [C#]
ms.assetid: 7f9bf952-7744-4f91-b676-cddb55d107c3
ms.openlocfilehash: bc040e17f5c612b9fc43a9ef24fb6f15f0942b8e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33284309"
---
# <a name="where-clause-c-reference"></a>where tümcesi (C# Başvurusu)
`where` Yan tümcesi, veri kaynağından hangi öğelerin sorgu ifadesinde döndürülecek belirtmek için bir sorgu ifadesinde kullanılır. Bir Boole koşulu geçerlidir (*koşulu*) (aralık değişkeni tarafından başvurulan) her kaynak öğesine ve bunlar belirtilen koşulu olduğu true döndürür. Tek bir sorgu ifade birden çok içerebilir `where` yan tümceleri ve tek bir yan tümce birden çok koşul alt ifadelerin içerebilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, `where` en az beş olanlar dışındaki tüm sayılar filtreleyen yan tümcesi. Kaldırırsanız `where` yan tümcesi, veri kaynağından gelen tüm sayıları döndürülen. İfade `num < 5` her öğeye uygulanan koşul.  
  
 [!code-csharp[cscsrefQueryKeywords#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_1.cs)]  
  
## <a name="example"></a>Örnek  
 Tek bir `where` yan tümcesi sayıda koşulları gerektiği gibi kullanarak belirleyebileceğiniz [ && ](../../../csharp/language-reference/operators/conditional-and-operator.md) ve [ &#124; &#124; ](../../../csharp/language-reference/operators/conditional-or-operator.md) işleçler. Aşağıdaki örnekte, sorgunun yalnızca en az beş olan çift sayı seçmek için iki koşulları belirtir.  
  
 [!code-csharp[cscsrefQueryKeywords#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_2.cs)]  
  
## <a name="example"></a>Örnek  
 A `where` yan tümcesi, Boole değerleri döndüren bir veya daha fazla yöntemleri içerebilir. Aşağıdaki örnekte, `where` yan tümcesinin aralık değişkeni geçerli değeri çift veya tek olup olmadığını belirlemek için bir yöntem kullanır.  
  
 [!code-csharp[cscsrefQueryKeywords#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_3.cs)]  
  
## <a name="remarks"></a>Açıklamalar  
 `where` Yan tümcesi olan bir filtreleme mekanizması. İlk veya son yan tümcesi olamaz dışında neredeyse her yerden sorgu ifadesinde yerleştirilebilir. A `where` yan tümcesi önce veya sonra görünebilir bir [grup](../../../csharp/language-reference/keywords/group-clause.md) önce veya sonra bunlar gruplandırılır kaynağı öğeleri filtrelemek sahip bağlı olarak yan tümcesi.  
  
 Belirtilen önerme veri kaynağındaki öğeler için geçerli değilse, derleme zamanı hata neden olur. Tanımlayıcı türü tarafından sağlanan denetimi bir yararı budur [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].  
  
 Derleme zamanında `where` anahtar sözcüğü bir çağrı biçimine dönüştürülür <xref:System.Linq.Enumerable.Where%2A> standart sorgu işleci yöntemi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sorgu anahtar sözcükleri (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md)  
 [from yan tümcesi](../../../csharp/language-reference/keywords/from-clause.md)  
 [select yan tümcesi](../../../csharp/language-reference/keywords/select-clause.md)  
 [Verileri Filtreleme](../../programming-guide/concepts/linq/filtering-data.md)  
 [LINQ Sorgu ifadeleri](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [C#'de LINQ Kullanmaya Başlama](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
