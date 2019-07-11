---
title: Yapılar - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
ms.openlocfilehash: 063d7e3b68fbe6c01ff0df4ae935fec5af6f6891
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743842"
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Yapılar](index.md)
- [Sınıflar](classes.md)
- [Boş Değer Atanabilir Tipler](../nullable-types/index.md)
- [Tanımlayıcı adları](../inside-a-program/identifier-names.md)
- [Yapıları Kullanma](using-structs.md)
- [Nasıl yapılır: Yapı geçirme ile Metoda sınıf başvurusu geçirme arasındaki farkı bilme](how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)
