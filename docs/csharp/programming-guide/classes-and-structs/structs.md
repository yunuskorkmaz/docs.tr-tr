---
title: Yapılar (C# Programlama Kılavuzu)
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
ms.openlocfilehash: 27d4b0d7edf1b5e89e84ac1df5783d68ebb4efe0
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44259503"
---
# <a name="structs-c-programming-guide"></a>Yapılar (C# Programlama Kılavuzu)

Yapılar kullanarak tanımlanmış [yapı](../../language-reference/keywords/struct.md) anahtar sözcüğü, örneğin:  
  
[!code-csharp[csProgGuideObjects#39](./codesnippet/CSharp/structs_1.cs)]  
  
Yapılar sınıflar olarak aynı sözdizimini çoğunu paylaşır. Struct'ın adı geçerli C# olmalıdır [tanımlayıcı adı](../inside-a-program/identifier-names.md). Yapılar aşağıdaki yollarla sınıfları daha büyük/küçük harf sınırlıdır:  
  
- Const veya statik olarak bildirilirler sürece bir yapının bildirimi içinde alanları başlatılamıyor.  
- Bir yapı varsayılan (parametresiz bir oluşturucu) bir oluşturucu ya da bir sonlandırıcı bildiremezsiniz.  
- Yapılar, atamaya bağlı kopyalanır. Bir yapı için yeni bir değişken atandığında, tüm verileri kopyalanır ve yeni bir kopyasını değişiklik özgün kopya verileri değiştirmez. Bu ne zaman değerinin koleksiyonlar ile çalışma gibi türleri unutmamak önemlidir `Dictionary<string, myStruct>`.  
- Başvuru türleri sınıflar, aksine, değer türleri birimleridir.  
- Sınıflardan farklı olarak, yapılar kullanmadan oluşturulabilir bir `new` işleci.  
- Yapılar parametrelerine sahip oluşturucular bildirebilirsiniz. 
- Bir yapı, başka bir yapı veya sınıfından devralamaz ve temel bir sınıfı olamaz. Tüm yapıları doğrudan devralan <xref:System.ValueType>, işlevinden devralan <xref:System.Object>.  
- Bir yapı, arabirim uygulayabilir.  
- Bir yapı boş değer atanabilir bir tür kullanılan ve boş değer atanabilir.  
  
## <a name="related-sections"></a>İlgili bölümler  

Daha fazla bilgi için:  
  
- [Yapıları Kullanma](using-structs.md)
- [Oluşturucular](constructors.md)
- [Boş Değer Atanabilir Tipler](../nullable-types/index.md)
- [Nasıl yapılır: Yapı Geçirme ile Yönteme Sınıf Başvurusu Geçirme Arasındaki Farkı Bilme](how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)
- [Nasıl yapılır: Yapılar Arasında Kullanıcı Tanımlı Dönüştürmeler Uygulama](../statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Yapılar](index.md)
- [Sınıflar](classes.md)
- [Tanımlayıcı adları](../inside-a-program/identifier-names.md)
