---
title: Yapılar- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
ms.openlocfilehash: df2a235651a2242ffe18df377dce9995af31e99f
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71392457"
---
# <a name="structs-c-programming-guide"></a>Yapılar (C# Programlama Kılavuzu)

Yapılar [struct](../../language-reference/keywords/struct.md) anahtar sözcüğü kullanılarak tanımlanır, örneğin:  
  
 [!code-csharp[csProgGuideObjects#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#39)]  
  
Yapılar, aynı sözdiziminin büyük bir kısmını sınıflarla paylaşır. Yapının adı geçerli C# bir [tanımlayıcı adı](../inside-a-program/identifier-names.md)olmalıdır. Yapılar aşağıdaki yollarla sınıflardan daha sınırlıdır:  
  
- Bir struct bildiriminde, alanlar const veya static olarak bildirilmeyen sürece başlatılamaz.  
- Struct parametresiz bir Oluşturucu (parametresiz bir Oluşturucu) veya sonlandırıcısı bildiremez.  
- Yapılar atamaya kopyalanır. Bir yapı yeni bir değişkene atandığında, tüm veriler kopyalanır ve yeni kopyada yapılan değişiklikler özgün kopyanın verilerini değiştirmez. Bu, `Dictionary<string, myStruct>` gibi değer türlerinin koleksiyonlarıyla çalışırken unutmamak önemlidir.  
- Yapılar, başvuru türleri olan sınıfların aksine değer türlerdir.  
- Sınıfların aksine, yapılar `new` işleci kullanılmadan örneklenebilir.  
- Yapılar, parametreleri olan oluşturucular bildirebilir.
- Yapı, başka bir struct veya sınıftan devralınabilir ve bir sınıfın temeli olamaz. Tüm yapılar, <xref:System.Object> ' den devralan <xref:System.ValueType> ' dan devralır.  
- Bir struct, arabirimler uygulayabilir.
- Bir struct `null` olamaz ve değişken Nullable bir değer türü olarak bildirilemediği sürece bir struct değişkeni `null` atanamaz.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Yapılar](index.md)
- [Sınıflar](classes.md)
- [Null yapılabilir değer türleri](../nullable-types/index.md)
- [Tanımlayıcı adları](../inside-a-program/identifier-names.md)
- [Yapıları Kullanma](using-structs.md)
- [Nasıl yapılır: Yapı geçirme ve bir sınıf başvurusunu bir yönteme geçirme arasındaki farkı öğrenin @ no__t-0
