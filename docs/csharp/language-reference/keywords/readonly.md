---
title: readonly (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: c6071e7a3c3bfcc96c57ecb34632a911835685fd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="readonly-c-reference"></a>readonly (C# Başvurusu)
`readonly` Alanları kullanabileceğiniz Değiştirici bir anahtar sözcüktür. Ne zaman alan bildirimini içeren bir `readonly` değiştiricisi, bildirimi tarafından sunulan alanlar atamalar yalnızca oluşabilir parçası olarak bildirimiyle veya oluşturucusu aynı sınıfta.  
  
## <a name="readonly-field-example"></a>Salt okunur alanı örneği  
 Bu örnekte, alanın değerini `year` yönteminde değiştirilemez `ChangeYear`rağmen sınıfı oluşturucusu değerinde atanır:  
  
 [!code-csharp[csrefKeywordsModifiers#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/readonly_1.cs)]  
  
 Bir değere atayabileceğiniz bir `readonly` yalnızca aşağıdaki bağlamlarda alan:  
  
-   Ne zaman değişkeni bildiriminde örneğin başlatılır:  
  
    ```  
    public readonly int y = 5;  
    ```  
  
-   Bir örnek alanındaki için sınıfın örnek oluşturucuları alan bildirimini içeren veya statik bir alan için alan bildirimini içeren sınıfın statik Oluşturucusu. Ayrıca olduğu geçirmek için geçerli tek bağlamları bunlar bir `readonly` olarak alan bir [çıkışı](../../../csharp/language-reference/keywords/out-parameter-modifier.md) veya [ref](../../../csharp/language-reference/keywords/ref.md) parametresi.  
  
> [!NOTE]
>  `readonly` Sözcüktür farklı [const](../../../csharp/language-reference/keywords/const.md) anahtar sözcüğü. A `const` alan alan bildirimi sırasında yalnızca başlatılabilir. A `readonly` bildirimi sırasında veya bir oluşturucuya alan başlatılabilir. Bu nedenle, `readonly` alanları kullanılan Oluşturucusu bağlı olarak farklı değerlere sahip olabilir. Ayrıca, ancak bir `const` alandır derleme zamanı sabiti `readonly` alan, aşağıdaki örnekte olduğu gibi çalışma zamanı sabitleri için kullanılabilir:  
  
```  
public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;  
```  
  
## <a name="comparing-readonly-and-non-readonly-instance-fields"></a>Salt okunur ve salt okunur olmayan örneği alanları karşılaştırma  
 [!code-csharp[csrefKeywordsModifiers#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/readonly_2.cs)]  
  
 Önceki örnekte, bu gibi bir ifade kullanıyorsanız:  
  
 `p2.y = 66;        // Error`  
  
 derleyici hatası iletisi alırsınız:  
  
 `The left-hand side of an assignment must be an l-value`  
  
 bir sabit bir değer atamaya çalış edilirken aynı hata olduğu.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Değiştiriciler](../../../csharp/language-reference/keywords/modifiers.md)  
 [const](../../../csharp/language-reference/keywords/const.md)  
 [Alanlar](../../../csharp/programming-guide/classes-and-structs/fields.md)
