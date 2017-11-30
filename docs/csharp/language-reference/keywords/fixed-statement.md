---
title: "fixed Deyimi (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords: fixed keyword [C#]
ms.assetid: 7ea6db08-ad49-4a7a-b934-d8c4acad1c3a
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 13633e71c863b075eede41c9a18419d65350bdb0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="fixed-statement-c-reference"></a>fixed Deyimi (C# Başvurusu)
`fixed` Deyimi taşınabilir bir değişken yerini değiştirme atık toplayıcı engeller. `fixed` Deyimi izin yalnızca bir [güvensiz](../../../csharp/language-reference/keywords/unsafe.md) bağlamı. `Fixed`oluşturmak için de kullanılabilir [sabit boyutlu arabellekler](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md).  
  
 `fixed` Deyimi ayarlar bir işaretçi bir yönetilen değişken ve "PIN" için değişken deyimin yürütülmesi sırasında. Olmadan `fixed`, atık toplama değişkenleri beklenmedik şekilde taşımanızı beri taşınabilir yönetilen değişkenleri işaretçiler az kullanımını olacaktır. C# Derleyici yalnızca bir işaretçi yönetilen bir değişkene atayın olanak sağlayan bir `fixed` deyimi.  
  
 [!code-csharp[csrefKeywordsFixedLock#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_1.cs)]  
  
 Bir dizi, bir dize, bir sabit boyutlu arabellek veya değişkenin adresini kullanarak bir işaretçi başlatabilirsiniz. Aşağıdaki örnekte değişken adresleri, dizileri ve dizeleri kullanımını göstermektedir. Sabit boyutlu arabellekler hakkında daha fazla bilgi için bkz: [sabit boyutlu arabellekler](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md).  
  
 [!code-csharp[csrefKeywordsFixedLock#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_2.cs)]  
  
 Bunların tümü aynı türde sürece birden çok işaretçileri başlatabilirsiniz.  
  
```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}  
```
  
 Farklı türlerdeki işaretçileri başlatmak için yalnızca içe `fixed` aşağıdaki örnekte gösterildiği gibi deyimleri.  
  
 [!code-csharp[csrefKeywordsFixedLock#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_3.cs)]  
  
 Deyim kodda yürütüldükten sonra tüm sabitlenmiş sabitlenmemiş ve atık toplama değişkenlerdir. Bu nedenle, bu değişkenleri dışında işaret etmiyor `fixed` deyimi.  
  
> [!NOTE]
>  Sabit deyimlerinde başlatılmış işaretçileri değiştirilemez.  
  
 Güvenli modda, burada atık toplama tabi değildir ve bu nedenle sabitlenmelidir gerekmez yığında bellek ayrılabilir. Daha fazla bilgi için bkz: [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csrefKeywordsFixedLock#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_4.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# anahtar sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [güvenli olmayan](../../../csharp/language-reference/keywords/unsafe.md)  
 [Sabit boyutlu arabellekler](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
