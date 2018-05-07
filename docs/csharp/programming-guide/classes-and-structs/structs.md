---
title: Yapılar (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
ms.openlocfilehash: ffb5b8da6c72056620cf890f38af4e7a8116ab3e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
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
  
-   [Yapıları Kullanma](../../../csharp/programming-guide/classes-and-structs/using-structs.md)  
  
-   [Oluşturucular](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [Boş Değer Atanabilir Tipler](../../../csharp/programming-guide/nullable-types/index.md)  
  
-   [Nasıl yapılır: Yapı Geçirme ile Yönteme Sınıf Başvurusu Geçirme Arasındaki Farkı Bilme](../../../csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)  
  
-   [Nasıl yapılır: Yapılar Arasında Kullanıcı Tanımlı Dönüştürmeler Uygulama](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Sınıflar ve Yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Sınıflar](../../../csharp/programming-guide/classes-and-structs/classes.md)
