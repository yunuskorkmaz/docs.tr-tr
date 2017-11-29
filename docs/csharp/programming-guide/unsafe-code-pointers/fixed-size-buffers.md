---
title: "Sabit Boyutlu Arabellekler (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.assetid: 6220d454-947c-4977-ac9d-9308c6ed5051
caps.latest.revision: "31"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3f99c2c6d477fca988fcca77de5ca5c2f8addd4d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="fixed-size-buffers-c-programming-guide"></a>Sabit Boyutlu Arabellekler (C# Programlama Kılavuzu)
C# ' ta kullanabileceğiniz [sabit](../../../csharp/language-reference/keywords/fixed-statement.md) ifadesi bir veri yapısında bir sabit boyutlu bir diziye sahip bir arabellek oluşturun. Diğer diller önceden varolan DLL'leri veya COM projeleri yazılan kod gibi var olan kodu ile çalışırken kullanışlıdır. Sabit dizi öznitelik ya da normal Yapı üyeleri için izin verilen değiştiricileri alabilir. Yalnızca dizi türü olmalıdır kısıtlamadır `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, veya `double`.  
  
```  
private fixed char name[30];  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Bir dizi içeren bir C# yapı dizi öğeleri içermediğinden erken sürümlerinde C#, C++ stili sabit boyutlu yapısı bildirme zordu. Bunun yerine, yapı öğeleri bir başvuru içeriyor.  
  
 C# 2.0 içinde sabit boyutlu bir dizi ekleme yeteneği eklenen bir [yapısı](../../../csharp/language-reference/keywords/struct.md) içinde kullanıldığında bir [güvensiz](../../../csharp/language-reference/keywords/unsafe.md) kod bloğu.  
  
 Örneğin, C# 2.0, aşağıdaki önce `struct` 8 bayt boyutunda olabilir. `pathName` Dizidir yığında ayrılmış dizi başvurusu:  
  
 [!code-csharp[csProgGuidePointers#19](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/fixed-size-buffers_1.cs)]  
  
 C# 2.0 ile başlayan bir `struct` katıştırılmış bir dizi içerebilir. Aşağıdaki örnekte, `fixedBuffer` dizi sabit bir boyuta sahiptir. Dizideki öğeler erişmek için kullandığınız bir `fixed` deyimi ilk öğe için bir işaretçi oluşturun. `fixed` Deyimi sabitler örneği `fixedBuffer` bellekte belirli bir konuma.  
  
 [!code-csharp[csProgGuidePointers#20](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/fixed-size-buffers_2.cs)]  
  
 128 öğe boyutunu `char` 256 baytı dizisidir. Boyutu sabit [char](../../../csharp/language-reference/keywords/char.md) arabellekleri her zaman karakter kodlama bağımsız olarak, her iki byte uygulamanız. Bu bile zaman char arabellekleri API yöntemlerini veya yapılar ile sıralanmış geçerlidir `CharSet = CharSet.Auto` veya `CharSet = CharSet.Ansi`. Daha fazla bilgi için bkz. <xref:System.Runtime.InteropServices.CharSet>.  
  
 Başka bir ortak sabit boyutlu dizi [bool](../../../csharp/language-reference/keywords/bool.md) dizi. Öğeleri bir `bool` dizi her zaman bir bayt boyutunda. `bool`diziler bit dizileri veya arabelleklerinin oluşturmak için uygun değildir.  
  
> [!NOTE]
>  Kullanılarak oluşturulan bellek dışında [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md), C# Derleyici ve ortak dil çalışma zamanı (CLR) tüm güvenlik arabellek taşması denetimlerini gerçekleştirmeyin. Tüm güvenli olmayan kod ile dikkatli olarak.  
  
 Güvenli olmayan arabellekler normal diziler de aşağıdaki yollarla farklılık gösterir:  
  
-   Bu gibi durumlarda, güvenli olmayan arabellekler yalnızca güvensiz bir bağlamda kullanabilirsiniz.  
  
-   Güvenli olmayan arabellekler her zaman vektörlerinin ya da tek boyutlu diziler olur.  
  
-   Dizi bildirimi gibi bir sayı bulunması `char id[8]`. Kullanamazsınız `char id[]` yerine.  
  
-   Güvenli olmayan arabellekler yalnızca güvenli olmayan bir bağlamda yapılar örneği alanları olabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Güvenli olmayan kod ve işaretçiler](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [fixed deyimi](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [Birlikte çalışabilirlik](../../../csharp/programming-guide/interop/index.md)
