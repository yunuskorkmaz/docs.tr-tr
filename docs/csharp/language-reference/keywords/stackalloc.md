---
title: "stackalloc (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- stackalloc_CSharpKeyword
- stackalloc
helpviewer_keywords: stackalloc keyword [C#]
ms.assetid: adc04c28-3ed2-4326-807a-7545df92b852
caps.latest.revision: "27"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ad4453f889a344fcd44dfad44a30fef07380b6a3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="stackalloc-c-reference"></a>stackalloc (C# Başvurusu)
`stackalloc` Anahtar sözcüğü bir güvenli olmayan kod bağlamında kullanılan yığında bir bellek bloğu ayrılamadı.  
  
```  
int* block = stackalloc int[100];  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Anahtar sözcüğü yalnızca yerel değişken başlatıcıları içinde geçerli değil. Aşağıdaki kod derleyici hataları neden olur.  
  
```  
int* block;  
// The following assignment statement causes compiler errors. You  
// can use stackalloc only when declaring and initializing a local   
// variable.  
block = stackalloc int[100];  
```  
  
 İşaretçi türleri dahil olduğundan `stackalloc` gerektirir [güvensiz](../../../csharp/language-reference/keywords/unsafe.md) bağlamı. Daha fazla bilgi için bkz: [güvenli olmayan kod ve işaretçiler](../../../csharp/programming-guide/unsafe-code-pointers/index.md).  
  
 `stackalloc`benzer [_alloca](/cpp/c-runtime-library/reference/alloca) C Çalışma Zamanı Kitaplığı'nda.  
  
 Aşağıdaki örnek, hesaplar ve ilk 20 sayıları Fibonacci sırada görüntüler. Her numarası önceki sayılarının toplamıdır. Kodda, türündeki 20 öğeler içerecek şekilde yeterli boyutunda bellek bloğu `int` yığın yığında ayrılmış. Blok adresini işaretçinin depolanan `fib`. Bu bellek çöp toplama tabi değildir ve bu nedenle sabitlenmiş olmak zorunda değildir (kullanarak [sabit](../../../csharp/language-reference/keywords/fixed-statement.md)). Bellek bloğu ömrü tanımladığı yöntemi için kullanım ömrü sınırlıdır. Yöntem döndürmeden önce bellek bırakılamıyor.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csrefKeywordsOperator#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/stackalloc_1.cs)]  
  
## <a name="security"></a>Güvenlik  
 Güvenli olmayan kod güvenli alternatifler daha az güvenlidir. Ancak, kullanımını `stackalloc` ortak dil çalışma zamanı (CLR) arabellek taşması algılama özellikleri otomatik olarak etkinleştirir. İşlem, bir arabellek taşması algılanırsa, kötü amaçlı kod yürütülür olasılığını en aza indirmek için mümkün olan en kısa sürede sonlandırılır.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# anahtar sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [İşleç anahtar sözcükleri](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [Güvenli olmayan kod ve işaretçiler](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
