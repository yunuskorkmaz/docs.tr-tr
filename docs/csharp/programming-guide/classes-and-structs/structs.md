---
title: Yapılar (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
ms.openlocfilehash: abe39b336aa8e9aa7a8a8ee96ed6848804644ddd
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43518709"
---
# <a name="structs-c-programming-guide"></a>Yapılar (C# Programlama Kılavuzu)
Yapılar kullanarak tanımlanmış [yapı](../../../csharp/language-reference/keywords/struct.md) anahtar sözcüğü, örneğin:  
  
 [!code-csharp[csProgGuideObjects#39](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/structs_1.cs)]  
  
 Yapılar sınıfları daha sınırlı olmasına karşın yapılar sınıfları, aynı söz dizimini çoğunu paylaşır:  
  
-   Const veya statik olarak bildirilirler sürece bir yapının bildirimi içinde alanları başlatılamıyor.  
  
-   Bir yapı varsayılan (parametresiz bir oluşturucu) bir oluşturucu ya da bir sonlandırıcı bildiremezsiniz.  
  
-   Yapılar, atamaya bağlı kopyalanır. Bir yapı için yeni bir değişken atandığında, tüm verileri kopyalanır ve yeni bir kopyasını değişiklik özgün kopya verileri değiştirmez. Bu sözlük gibi değer türlerinin koleksiyonları ile çalışırken unutmamak önemlidir\<string, myStruct >.  
  
-   Yapılar değer türüdür ve sınıflar, başvuru türleridir.  
  
-   Sınıflardan farklı olarak, yapılar kullanmadan oluşturulabilir bir `new` işleci.  
  
-   Yapılar parametrelerine sahip oluşturucular bildirebilirsiniz.  
  
-   Bir yapı, başka bir yapı veya sınıfından devralamaz ve temel bir sınıfı olamaz. Tüm yapıları doğrudan devralan `System.ValueType`, işlevinden devralan `System.Object`.  
  
-   Bir yapı, arabirim uygulayabilir.  
  
-   Bir yapı boş değer atanabilir bir tür kullanılan ve boş değer atanabilir.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 Daha fazla bilgi için:  
  
-   [Yapıları Kullanma](../../../csharp/programming-guide/classes-and-structs/using-structs.md)  
  
-   [Oluşturucular](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [Boş Değer Atanabilir Tipler](../../../csharp/programming-guide/nullable-types/index.md)  
  
-   [Nasıl yapılır: Yapı Geçirme ile Yönteme Sınıf Başvurusu Geçirme Arasındaki Farkı Bilme](../../../csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)  
  
-   [Nasıl yapılır: Yapılar Arasında Kullanıcı Tanımlı Dönüştürmeler Uygulama](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Sınıflar ve Yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [Sınıflar](../../../csharp/programming-guide/classes-and-structs/classes.md)
