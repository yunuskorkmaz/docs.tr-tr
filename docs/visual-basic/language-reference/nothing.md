---
title: Nothing (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Nothing
- vb.Nothing
helpviewer_keywords:
- Nothing keyword [Visual Basic]
- Nothing keyword [Visual Basic], syntax
ms.assetid: 06176e2d-bbf7-4a37-afaa-a86ad21ee99f
ms.openlocfilehash: 97c651dbcc657fbab0706c9a959bd0031c0fe343
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826099"
---
# <a name="nothing-visual-basic"></a>Nothing (Visual Basic)
Herhangi bir veri türünün varsayılan değerini temsil eder. Başvuru türleri için varsayılan değerdir `null` başvuru. Değer türleri için varsayılan değer, değer türü null olmasına göre değişir.  
  
> [!NOTE]
>  NULL olmayan değer türleri için `Nothing` Visual Basic'te farklıdır `null` içinde C#. Visual Basic'te, bir NULL olmayan değer türünde bir değişken ayarlarsanız `Nothing`, bildirilen tür için varsayılan değerine ayarlanır. İçinde C#, bir NULL olmayan değer türünde bir değişkene atarsanız `null`, bir derleme zamanı hatası oluşur.  
  
## <a name="remarks"></a>Açıklamalar  
 `Nothing` bir veri türünün varsayılan değerini temsil eder. Varsayılan değer, değişkeni bir değer türü veya başvuru türü olmasına göre değişir.  
  
 Bir değişken bir *değer türü* doğrudan değeri içeriyor. Değer türleri, tüm sayısal veri türleri dahil `Boolean`, `Char`, `Date`, tüm yapıları ve tüm numaralandırma. Bir değişken bir *başvuru türüne* bir nesnenin örneğine başvuru bellekte depolar. Başvuru türleri sınıflar, diziler, temsilciler ve dizeleri içerir. Daha fazla bilgi için [değer türleri ve başvuru türleri](../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).  
  
 Bir değişken değerini ise türü, davranışını `Nothing` değişken bir boş değer atanabilir bir veri türü olmasına göre değişir. Null bir değer türü temsil etmek için ekleme bir `?` tür adının değiştiricisi. Atama `Nothing` boş değer atanabilir bir değişken için değeri ayarlar `null`. Daha fazla bilgi ve örnekler için bkz. [boş değer atanabilir değer türleri](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md).  
  
 Boş değer atanamayan bir değer türünde bir değişken ise atama `Nothing` için varsayılan değer olarak bildirilen tür için ayarlar. Bu tür değişken bir üye içeriyorsa, bunlar varsayılan değerlerine demektir. Aşağıdaki örnekte, skaler türleri için bunu göstermektedir.  
  
 [!code-vb[VbVbalrKeywords#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class2.vb#7)]  
  
 Bir değişken bir başvuru türü ise, atama `Nothing` değişkene ayarlar bir `null` değişkenin türüne başvuru. Ayarlanmış bir değişken bir `null` başvurusu herhangi bir nesne ile ilişkili değil. Aşağıdaki örnekte bu gösterir.  
  
 [!code-vb[VbVbalrKeywords#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class3.vb#8)]  
  
 Bir başvuru (veya boş değer atanabilen değer türü olup olmadığını) değişken denetlenirken `null`, kullanmayın `= Nothing` veya `<> Nothing`. Her zaman `Is Nothing` veya `IsNot Nothing`.  
  
 Visual Basic'de dizeleri için boş bir dize değerine eşittir `Nothing`. Bu nedenle, `"" = Nothing` geçerlidir.  
  
 Aşağıdaki örnekte kullanan karşılaştırmalar `Is` ve `IsNot` işleçleri.  
  
 [!code-vb[VbVbalrKeywords#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class4.vb#9)]  
  
 Kullanmadan bir değişken bildirirseniz bir `As` yan tümcesi ve `Nothing`, değişkeni bir tür olan `Object`. Bunun bir örneği `Dim something = Nothing`. Bu durumda bir derleme zamanı hatası oluşur, `Option Strict` açıktır ve `Option Infer` kapalıdır.  
  
 Atadığınızda `Nothing` bir nesne değişkenine, artık herhangi bir nesne örneğine başvurur. Değişken, önceden bir örneğine adı, bu ayarın `Nothing` örneği sonlanmamasına. Örneği sonlandırıldı ve yalnızca kalan başvuru active olduğunu atık toplayıcı (GC) algıladıktan sonra ilişkili bellek ve sistem kaynaklarını serbest bırakılır.  
  
 `Nothing` farklıdır <xref:System.DBNull> başlatılmayan bir değişken veya var olmayan bir veritabanı sütunu temsil eden nesne.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dim Deyimi](../../visual-basic/language-reference/statements/dim-statement.md)
- [Nesne ömrü: Nesnelerin nasıl oluşturulduğunu ve yok](../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [Visual Basic'de ömür](../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Is İşleci](../../visual-basic/language-reference/operators/is-operator.md)
- [IsNot İşleci](../../visual-basic/language-reference/operators/isnot-operator.md)
- [Boş Değer Atanabilen Değer Türleri](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
