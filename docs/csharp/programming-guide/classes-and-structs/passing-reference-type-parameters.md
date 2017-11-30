---
title: "Başvuru Türü Parametreleri Geçirme (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- method parameters [C#], reference types
- parameters [C#], reference
ms.assetid: 9e6eb65c-942e-48ab-920a-b7ba9df4ea20
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2cd862a9179e027ab82631631784203993d0465a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="passing-reference-type-parameters-c-programming-guide"></a>Başvuru Türü Parametreleri Geçirme (C# Programlama Kılavuzu)
Bir değişken bir [başvuru türüne](../../../csharp/language-reference/keywords/reference-types.md) verileri içermiyor doğrudan; verilerine bir başvuru içeriyor. Bir başvuru türü parametre değerine göre geçirdiğinizde, bir sınıf üyesi değerini gibi başvuru işaret verileri değiştirmek mümkündür. Ancak, başvuru değeri değiştirilemiyor; diğer bir deyişle, aynı başvuru için yeni bir sınıf bellek ayırabilir ve onu dışında blok kalıcı olması için kullanamazsınız. Bunu yapmak için parametresini kullanarak geçirmek [ref](../../../csharp/language-reference/keywords/ref.md) veya [çıkışı](../../../csharp/language-reference/keywords/out.md) anahtar sözcüğü. Kolaylık olması için aşağıdaki örneklerde `ref`.  
  
## <a name="passing-reference-types-by-value"></a>Değere göre geçirme başvuru türleri  
 Aşağıdaki örnek, bir başvuru türü parametre geçirme gösterir `arr`, bir yönteme değeriyle `Change`. Parametresi için bir başvuru olduğundan `arr`, dizi öğelerinin değerlerini değiştirmek mümkündür. Ancak, parametre yalnızca farklı bellek konumuna yeniden denemesi yönteminin içinde çalışır ve özgün değişkeni etkilemez `arr`.  
  
 [!code-csharp[csProgGuideParameters#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-reference-type-parameters_1.cs)]  
  
 Önceki örnekte, dizi `arr`, bir başvuru türü olduğu yöntemine iletilir `ref` parametresi. Böyle bir durumda, başvuru kopyasını işaret ettiği için `arr`, yönteme geçirilen. Yöntemin bir dizi öğesine içeriğini bu durumda değiştirmek mümkündür çıkış gösterir `1` için `888`. Ancak, belleğin yeni bir kısmını kullanarak ayırma [yeni](../../../csharp/language-reference/keywords/new.md) içinde işleci `Change` yöntemi yapar değişkeni `pArray` yeni bir dizi başvuru. Bu nedenle, özgün dizi etkilemez sonra değişiklikleri `arr`, içinde oluşturulan `Main`. Aslında, bu örnekte, biri içinde dizilerinin oluşturulan `Main` ve bir iç `Change` yöntemi.  
  
## <a name="passing-reference-types-by-reference"></a>Başvuruya göre geçirme başvuru türleri  
 Aşağıdaki örnek önceki örnekte, hariç aynıdır `ref` yöntemi üstbilgi ve arama anahtar sözcüğü eklenir. Yönteminde gerçekleşecek herhangi bir değişiklik, çağıran program özgün değişkeninde etkiler.  
  
 [!code-csharp[csProgGuideParameters#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-reference-type-parameters_2.cs)]  
  
 Yöntemi içinde gerçekleşmesi tüm değişiklikleri özgün dizisinde etkileyen `Main`. Özgün dizinin kullanarak aslında, bırakılan `new` işleci. Bu nedenle, çağırdıktan sonra `Change` yöntemi, herhangi bir başvuru için `arr` oluşturulan beş öğesi diziyi işaret `Change` yöntemi.  
  
## <a name="swapping-two-strings"></a>İki dizeyi değiştirme  
 Dizeleri değiştirme başvuruya göre başvuru türü parametreleri geçirme, iyi bir örnek verilmiştir. Örnekte, iki dizeyi `str1` ve `str2`, içinde başlatılan `Main` ve geçirilen `SwapStrings` yöntemi değiştiren parametreleri olarak `ref` anahtar sözcüğü. İki dizeyi yöntemi ve iç içinde değiştirilen `Main` de.  
  
 [!code-csharp[csProgGuideParameters#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-reference-type-parameters_3.cs)]  
  
 Bu örnekte, çağıran program değişkenlerde etkileyen başvuruya geçirilecek parametreleri gerekir. Kaldırırsanız `ref` yöntemi üstbilgi ve yöntem çağrısının anahtar sözcüğü, hiçbir değişiklik çağıran program yerinde götürür.  
  
 Dizeleri hakkında daha fazla bilgi için bkz: [dize](../../../csharp/language-reference/keywords/string.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Parametreleri geçirme](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md)  
 [Dizileri kullanma ref ve out geçirme](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md)  
 [Ref](../../../csharp/language-reference/keywords/ref.md)  
 [Başvuru türleri](../../../csharp/language-reference/keywords/reference-types.md)
