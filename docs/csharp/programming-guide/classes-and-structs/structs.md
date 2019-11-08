---
title: Yapılar- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
ms.openlocfilehash: 945d4b060dd9d08f6f16013b27980f66e804ad45
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739234"
---
# <a name="structs-c-programming-guide"></a>Yapılar (C# Programlama Kılavuzu)

Yapılar [struct](../../language-reference/keywords/struct.md) anahtar sözcüğü kullanılarak tanımlanır, örneğin:  
  
 [!code-csharp[csProgGuideObjects#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#39)]  
  
Yapılar, aynı sözdiziminin büyük bir kısmını sınıflarla paylaşır. Yapının adı geçerli C# bir [tanımlayıcı adı](../inside-a-program/identifier-names.md)olmalıdır. Yapılar aşağıdaki yollarla sınıflardan daha sınırlıdır:  
  
- Bir struct bildiriminde, alanlar const veya static olarak bildirilmeyen sürece başlatılamaz.  
- Struct parametresiz bir Oluşturucu (parametresiz bir Oluşturucu) veya sonlandırıcısı bildiremez.  
- Yapılar atamaya kopyalanır. Bir yapı yeni bir değişkene atandığında, tüm veriler kopyalanır ve yeni kopyada yapılan değişiklikler özgün kopyanın verilerini değiştirmez. Bu, `Dictionary<string, myStruct>`gibi değer türlerinin koleksiyonlarıyla çalışırken unutmamak önemlidir.  
- Yapılar, başvuru türleri olan sınıfların aksine değer türlerdir.  
- Sınıfların aksine, yapılar `new` işleci kullanılmadan oluşturulabilir.  
- Yapılar, parametreleri olan oluşturucular bildirebilir.
- Yapı, başka bir struct veya sınıftan devralınabilir ve bir sınıfın temeli olamaz. Tüm yapılar, <xref:System.Object>devralan <xref:System.ValueType>doğrudan devralır.  
- Bir struct, arabirimler uygulayabilir.
- Bir struct `null`olamaz ve değişken null değer türü olarak bildirildiği sürece bir struct değişkeni `null` atanamaz.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Yapılar](index.md)
- [Sınıflar](classes.md)
- [Null yapılabilir değer türleri](../../language-reference/builtin-types/nullable-value-types.md)
- [Tanımlayıcı adları](../inside-a-program/identifier-names.md)
- [Yapıları Kullanma](using-structs.md)
- [Nasıl yapılır: Yapı Geçirme ile Yönteme Sınıf Başvurusu Geçirme Arasındaki Farkı Bilme](how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)
