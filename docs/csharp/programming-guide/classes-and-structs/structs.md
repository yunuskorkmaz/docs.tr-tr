---
title: "Yapılar (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
caps.latest.revision: "31"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 475d9b96e078270faf6c841a62e6031556e8e539
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="structs-c-programming-guide"></a>Yapılar (C# Programlama Kılavuzu)
Yapılar kullanılarak tanımlanmış [yapısı](../../../csharp/language-reference/keywords/struct.md) anahtar sözcüğü, örneğin:  
  
 [!code-csharp[csProgGuideObjects#39](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/structs_1.cs)]  
  
 Yapılar sınıfları'den daha kısıtlı olsa yapılar sınıfları, aynı söz dizimini çoğunu paylaşır:  
  
-   Const veya statik olarak bildirilir sürece yapısı bildirimi içinde alanları başlatılamaz.  
  
-   Yapı, varsayılan bir oluşturucu (parametresiz bir oluşturucu) veya bir sonlandırıcı bildiremezsiniz.  
  
-   Yapılar atamada kopyalanır. Yapı için yeni bir değişken atandığında, tüm verileri kopyalanır ve yeni bir kopyasını kendilerine herhangi bir değişiklik özgün kopya verileri değiştirmez. Bu değer türleri sözlük gibi koleksiyonları ile çalışırken unutulmaması önemlidir;\<dize, myStruct >.  
  
-   Yapılar değer türleri ve sınıfları başvuru türleri.  
  
-   Sınıfları kullanmadan yapılar oluşturulabilir bir `new` işleci.  
  
-   Yapılar parametrelere sahip oluşturucular bildirebilirsiniz.  
  
-   Yapı başka bir yapı veya sınıfından devralan ve bir sınıfın temel olamaz. Tüm yapıları doğrudan devralınmalıdır `System.ValueType`, devralan `System.Object`.  
  
-   Yapı arabirimleri uygulayabilir.  
  
-   Yapı boş değer atanabilir bir tür olarak kullanılan ve boş değer atanabilir.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 Daha fazla bilgi için:  
  
-   [Yapıları kullanma](../../../csharp/programming-guide/classes-and-structs/using-structs.md)  
  
-   [Oluşturucular](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [Boş değer atanabilir türler](../../../csharp/programming-guide/nullable-types/index.md)  
  
-   [Nasıl yapılır: Yapı geçirme ile yönteme sınıf başvurusu geçirme arasındaki farkı bilme](../../../csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)  
  
-   [Nasıl yapılır: yapılar arasında kullanıcı tanımlı dönüşümler](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Sınıflar ve yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Sınıfları](../../../csharp/programming-guide/classes-and-structs/classes.md)
