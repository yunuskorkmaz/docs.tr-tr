---
title: Nothing (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- Nothing
- vb.Nothing
helpviewer_keywords:
- Nothing keyword [Visual Basic]
- Nothing keyword [Visual Basic], syntax
ms.assetid: 06176e2d-bbf7-4a37-afaa-a86ad21ee99f
caps.latest.revision: "31"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6932fee01ec6f39f67fb1a26a9a5b5cbd47d9767
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="nothing-visual-basic"></a>Nothing (Visual Basic)
Herhangi bir veri türünün varsayılan değerini temsil eder. Referans türleri için varsayılan değerdir `null` başvuru. Değer türleri için varsayılan değer, değer türü boş değer atanabilir olmasına bağlıdır.  
  
> [!NOTE]
>  Null değer türleri için `Nothing` Visual Basic'te farklı `null` C#. Visual Basic'te bir null değer türü bir değişkeni ayarlandıysa, `Nothing`, değişken bildirilen türü için varsayılan değere ayarlanır. C# ' de bir null değer türü için bir değişken atarsanız, `null`, derleme zamanı hata oluşur.  
  
## <a name="remarks"></a>Açıklamalar  
 `Nothing`bir veri türü varsayılan değerini temsil eder. Varsayılan değer, değişken değer türü veya başvuru türünde olduğuna bağlıdır.  
  
 Bir değişken bir *değer türü* doğrudan değerini içerir. Değer türleri dahil tüm sayısal veri türleri, `Boolean`, `Char`, `Date`, tüm yapılar ve tüm numaralandırma. Bir değişken bir *başvuru türüne* nesnesinin örneği başvuru bellekte depolar. Başvuru türleri sınıfları, dizileri, temsilciler ve dizeleri içerir. Daha fazla bilgi için bkz: [değer türleri ve başvuru türleri](../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).  
  
 Bir değişken değerini ise yazın, davranışını `Nothing` değişkeni boş değer atanabilir veri türü olmasına bağlıdır. Bir boş değer atanabilen değer türü göstermek için ekleme bir `?` değiştiricisi türü adı. Atama `Nothing` değeri için boş değer atanabilir bir değişken ayarlar `null`. Daha fazla bilgi ve örnekler için bkz: [boş değer atanabilir değer türlerinin](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md).  
  
 Bir değişken NULL olmayan bir değer türü ise atama `Nothing` için onu varsayılan değer olarak bildirilen türü için ayarlar. Bu tür değişken üyeleri içeriyorsa, bunlar tüm varsayılan değerlerine kümesidir. Aşağıdaki örnekte bu skaler türleri için gösterilmektedir.  
  
 [!code-vb[VbVbalrKeywords#7](../../visual-basic/language-reference/codesnippet/VisualBasic/nothing_1.vb)]  
  
 Bir değişkeni bir başvuru türü ise atama `Nothing` değişkenine ayarlar bir `null` başvuru değişkenin türü. Ayarlanmış bir değişken bir `null` başvurusu herhangi bir nesne ile ilişkili değil. Aşağıdaki örnekte bu gösterir.  
  
 [!code-vb[VbVbalrKeywords#8](../../visual-basic/language-reference/codesnippet/VisualBasic/nothing_2.vb)]  
  
 Bir başvuru (veya boş değer atanabilen değer türü olup olmadığını) değişken denetlerken `null`, kullanmayın `= Nothing` veya `<> Nothing`. Her zaman kullanmak `Is Nothing` veya `IsNot Nothing`.  
  
 Visual Basic'de dizeleri için boş dize eşittir `Nothing`. Bu nedenle, `"" = Nothing` doğrudur.  
  
 Aşağıdaki örnek, kullanma karşılaştırmaları gösterir `Is` ve `IsNot` işleçler.  
  
 [!code-vb[VbVbalrKeywords#9](../../visual-basic/language-reference/codesnippet/VisualBasic/nothing_3.vb)]  
  
 Kullanmadan bir değişken bildirirseniz bir `As` yan tümcesi ve ayarlamak `Nothing`, bir değişken türü `Object`. Bunun bir örneği `Dim something = Nothing`. Bu durumda bir derleme zamanı hatası meydana zaman `Option Strict` açıktır ve `Option Infer` kapalıdır.  
  
 Atadığınızda `Nothing` bir nesne değişkeni için artık herhangi bir nesnenin örneğine başvuruyor. Değişkeni daha önce bir örneğine başvurulan değilse, bunu ayarını `Nothing` örneği sonlandırılacak değil. Örnek sonlandırılır ve yalnızca kalan etkin başvuru olduğunu (GC) atık toplayıcı algılandıktan sonra ilişkili bellek ve sistem kaynaklarını serbest bırakılır.  
  
 `Nothing`farklı <xref:System.DBNull> başlatılmamış bir değişken veya var olmayan veritabanı sütunu temsil eden nesne.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Dim deyimi](../../visual-basic/language-reference/statements/dim-statement.md)  
 [Nesne ömrü: Nesneleri oluşturma ve yok etme](../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)  
 [Visual Basic'de ömür](../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [Is işleci](../../visual-basic/language-reference/operators/is-operator.md)  
 [IsNot işleci](../../visual-basic/language-reference/operators/isnot-operator.md)  
 [Boş değer atanabilen değer türleri](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
