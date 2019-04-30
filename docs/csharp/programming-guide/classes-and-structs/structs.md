---
title: Yapılar - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
ms.openlocfilehash: 0c0faf9fe6d9752cafa03ee054f669334f56090d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61703302"
---
# <a name="structs-c-programming-guide"></a>Yapılar (C# Programlama Kılavuzu)

Yapılar kullanarak tanımlanmış [yapı](../../language-reference/keywords/struct.md) anahtar sözcüğü, örneğin:  
  
 [!code-csharp[csProgGuideObjects#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#39)]  
  
Yapılar sınıflar olarak aynı sözdizimini çoğunu paylaşır. Struct'ın adı geçerli C# olmalıdır [tanımlayıcı adı](../inside-a-program/identifier-names.md). Yapılar aşağıdaki yollarla sınıfları daha büyük/küçük harf sınırlıdır:  
  
- Const veya statik olarak bildirilirler sürece bir yapının bildirimi içinde alanları başlatılamıyor.  
- Bir yapı, parametresiz bir oluşturucu (parametresiz bir oluşturucu) veya bir sonlandırıcı bildiremezsiniz.  
- Yapılar, atamaya bağlı kopyalanır. Bir yapı için yeni bir değişken atandığında, tüm verileri kopyalanır ve yeni bir kopyasını değişiklik özgün kopya verileri değiştirmez. Bu ne zaman değerinin koleksiyonlar ile çalışma gibi türleri unutmamak önemlidir `Dictionary<string, myStruct>`.  
- Başvuru türleri sınıflar, aksine, değer türleri birimleridir.  
- Sınıflardan farklı olarak, yapılar kullanmadan oluşturulabilir bir `new` işleci.  
- Yapılar parametrelerine sahip oluşturucular bildirebilirsiniz. 
- Bir yapı, başka bir yapı veya sınıfından devralamaz ve temel bir sınıfı olamaz. Tüm yapıları doğrudan devralan <xref:System.ValueType>, işlevinden devralan <xref:System.Object>.  
- Bir yapı, arabirim uygulayabilir. 
- Bir yapı olamaz `null`, ve bir yapı değişkene atanamaz `null` boş değer atanabilir bir tür değişkenin bildirildiği sürece.
  
## <a name="related-sections"></a>İlgili bölümler  

Daha fazla bilgi için:  
  
- [Yapıları Kullanma](using-structs.md)
- [Oluşturucular](constructors.md)
- [Boş Değer Atanabilir Tipler](../nullable-types/index.md)
- [Nasıl yapılır: Yapı geçirme ile Metoda sınıf başvurusu geçirme arasındaki farkı bilme](how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)
- [Nasıl yapılır: Yapılar arasında kullanıcı tanımlı Dönüşümler Uygulama](../statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Yapılar](index.md)
- [Sınıflar](classes.md)
- [Tanımlayıcı adları](../inside-a-program/identifier-names.md)
