---
title: "stackalloc (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- stackalloc_CSharpKeyword
- stackalloc
helpviewer_keywords:
- stackalloc keyword [C#]
ms.assetid: adc04c28-3ed2-4326-807a-7545df92b852
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4b9c5328bfa1b0fc9a7751763c7d728096886905
ms.sourcegitcommit: 15316053918995cc1380163a7d7e7edd5c44e6d7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2018
---
# <a name="stackalloc-c-reference"></a>stackalloc (C# Başvurusu)
`stackalloc` Anahtar sözcüğü bir güvenli olmayan kod bağlamında kullanılan yığında bir bellek bloğu ayrılamadı.  
  
```csharp  
int* block = stackalloc int[100];  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Anahtar sözcüğü yalnızca yerel değişken başlatıcıları içinde geçerli değil. Aşağıdaki kod derleyici hataları neden olur.  
  
```csharp  
int* block;  
// The following assignment statement causes compiler errors. You  
// can use stackalloc only when declaring and initializing a local   
// variable.  
block = stackalloc int[100];  
```  
  
 İşaretçi türleri dahil olduğundan `stackalloc` gerektirir [güvensiz](../../../csharp/language-reference/keywords/unsafe.md) bağlamı. Daha fazla bilgi için bkz: [güvenli olmayan kod ve işaretçiler](../../../csharp/programming-guide/unsafe-code-pointers/index.md).  
  
 `stackalloc` benzer [_alloca](/cpp/c-runtime-library/reference/alloca) C Çalışma Zamanı Kitaplığı'nda.  
  
 Aşağıdaki örnek, hesaplar ve ilk 20 sayıları Fibonacci sırada görüntüler. Her numarası önceki sayılarının toplamıdır. Kodda, türündeki 20 öğeler içerecek şekilde yeterli boyutunda bellek bloğu `int` yığın yığında ayrılmış. Blok adresini işaretçinin depolanan `fib`. Bu bellek çöp toplama tabi değildir ve bu nedenle sabitlenmiş olmak zorunda değildir (kullanarak [sabit](../../../csharp/language-reference/keywords/fixed-statement.md)). Bellek bloğu ömrü tanımladığı yöntemi için kullanım ömrü sınırlıdır. Yöntem döndürmeden önce bellek bırakılamıyor.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csrefKeywordsOperator#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/stackalloc_1.cs)]  
  
## <a name="security"></a>Güvenlik  
 Güvenli olmayan kod güvenli alternatifler daha az güvenlidir. Ancak, kullanımını `stackalloc` ortak dil çalışma zamanı (CLR) arabellek taşması algılama özellikleri otomatik olarak etkinleştirir. İşlem, bir arabellek taşması algılanırsa, kötü amaçlı kod yürütülür olasılığını en aza indirmek için mümkün olan en kısa sürede sonlandırılır.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [İşleç Anahtar Sözcükleri](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [Güvenli Olmayan Kod ve İşaretçiler](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
