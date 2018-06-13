---
title: Boş Değer Atanabilir Türler (C# Programlama Kılavuzu)
ms.date: 05/15/2017
helpviewer_keywords:
- nullable types [C#]
- C# language, nullable types
- types [C#], nullable
ms.assetid: e473cb01-28ca-42be-9cea-f717055d72c6
ms.openlocfilehash: fcff492f420a60a41b373bf9042ed0c2d66d0446
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/23/2018
ms.locfileid: "34456594"
---
# <a name="nullable-types-c-programming-guide"></a>Boş Değer Atanabilir Türler (C# Programlama Kılavuzu)
Boş değer atanabilir türler örnekleridir <xref:System.Nullable%601?displayProperty=nameWithType> yapısı. Boş değer atanabilir bir tür değerleri temel alınan değer türü artı ek için doğru aralığı gösterebilir `null` değeri. Örneğin, bir `Nullable<Int32>`, okunur "Boş değer atanabilir, Int32," atanabilir herhangi bir değer -2147483648 2147483647 için ya da bu atanabilir `null` değeri. A `Nullable<bool>` değerler atanabilir [true](../../../csharp/language-reference/keywords/true.md), [false](../../../csharp/language-reference/keywords/false.md), veya [null](../../../csharp/language-reference/keywords/null.md). Atama olanağı `null` veritabanları ve bir değer atanamaz öğeleri içeren diğer veri türleri ile ilgilenirken sayısal ve Boole türleri için özellikle yararlıdır. Örneğin, bir veritabanında bir Boole alanı değerleri depolayabilir `true` veya `false`, veya tanımsız olabilir. 
  
[!code-csharp[nullable-types](../../../../samples/snippets/csharp/programming-guide/nullable-types/nullable-ex1.cs)]  
  
Daha fazla örnek için bkz: [boş değer atanabilir türleri kullanma](../../../csharp/programming-guide/nullable-types/using-nullable-types.md)  
  
## <a name="nullable-types-overview"></a>Boş değer atanabilir türler genel bakış  
 Boş değer atanabilir türler aşağıdaki özelliklere sahiptir:  
  
-   Boş değer atanabilir türleri temsil eden değeri atanabilir değer türü değişkenleri `null`. Bir başvuru türüne göre boş değer atanabilir bir tür oluşturulamıyor. (Başvuru türleri zaten Destek `null` değeri.)  
  
-   Sözdizimi `T?` için toplu özelliktir <xref:System.Nullable%601>, burada `T` değer türü değil. İki tür birbirinin yerine kullanılabilir.  
  
-   Sıradan değer türü için örneğin gibi bir değer null olabilir bir tür atama `int? x = 10;` veya `double? d = 4.108`. Boş değer atanabilir bir tür, değer atanabilir `null`: `int? x = null.`  
  
-   Kullanım <xref:System.Nullable%601.GetValueOrDefault%2A?displayProperty=nameWithType> değer ise atanan değer veya temel alınan türü için varsayılan değer döndürmek için yöntemini `null`, örneğin `int j = x.GetValueOrDefault();`  
  
-   Kullanım <xref:System.Nullable%601.HasValue%2A> ve <xref:System.Nullable%601.Value%2A> salt okunur özellikler için null sınamak ve aşağıdaki örnekte gösterildiği gibi değeri almak için: `if(x.HasValue) j = x.Value;`  
  
    -   `HasValue` Özelliği döndürür `true` değişkeni bir değer içeriyorsa veya `false` , `null`.  
  
    -   `Value` Özelliği bir atanmışsa değeri döndürür. Aksi halde, bir <xref:System.InvalidOperationException?displayProperty=nameWithType> oluşturulur.  
  
    -   İçin varsayılan değer `HasValue` olan `false`. `Value` Özelliğine sahip bir varsayılan değeri yok.  
  
    -   Aynı zamanda `==` ve `!=` aşağıdaki örnekte gösterildiği gibi null olabilir bir tür işleçlerle: `if (x != null) y = x;`  
  
-   Kullanım `??` geçerli değeri null olabilir bir tür olduğunda uygulanan varsayılan bir değer atamak için işleci `null` alamayan bir tür için örneğin atanır `int? x = null; int y = x ?? -1;`  
  
-   İç içe geçmiş boş değer atanabilir türler izin verilmiyor. Aşağıdaki satırı derlenmez: `Nullable<Nullable<int>> n;`  
  
## <a name="related-sections"></a>İlgili Bölümler  
 Daha fazla bilgi için:  
  
-   [Boş Değer Atanabilir Tipleri Kullanma](../../../csharp/programming-guide/nullable-types/using-nullable-types.md)  
  
-   [Boş Değer Atanabilir Tipleri Kutulama](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)  
  
-   [?? İşleç](../../../csharp/language-reference/operators/null-coalescing-operator.md)  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Nullable>  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C#](../../../csharp/index.md)  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [Tam olarak 'kaldırılmış' anlamı nedir?](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)
