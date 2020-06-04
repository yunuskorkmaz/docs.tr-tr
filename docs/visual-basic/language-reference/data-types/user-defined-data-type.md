---
title: Kullanıcı Tanımlı Veri Türü
ms.date: 07/20/2015
f1_keywords:
- UserDefined
- UDT
- vb.UDT
- User-Defined
- vb.UserDefined
- vb.User-Defined
helpviewer_keywords:
- user-defined data types [Visual Basic], Visual Basic
- user-defined types
- structures [Visual Basic], as user-defined data types
- user-defined types [Visual Basic], Visual Basic
- user-defined types [Visual Basic], structure declaration
- user-defined types [Visual Basic], structures in Visual Basic
- user-defined data types [Visual Basic], structure declaration
- data types [Visual Basic], assigning
- Structure statement [Visual Basic]
- data types [Visual Basic], user-defined
- user-defined data types [Visual Basic], structures in Visual Basic
- user-defined data types
- types [Visual Basic], user-defined
ms.assetid: be913dca-a364-4a51-96a1-549a1b390b0a
ms.openlocfilehash: fbd9536a54d7fb471d6cb2e130b14a84e40a4940
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415498"
---
# <a name="user-defined-data-type"></a>Kullanıcı Tanımlı Veri Türü

Verileri tanımladığınız biçimde tutar. `Structure`İfade biçimi tanımlar.

Önceki Visual Basic sürümleri Kullanıcı tanımlı türü (UDT) destekler. Geçerli sürüm, UDT 'yi bir *yapıya*genişletir. Yapı, çeşitli veri türlerindeki bir veya daha fazla *üyenin* bitiştirilmesi olur. Visual Basic, üyelerine tek bir birim olarak davranır, ancak üyelerine ayrı ayrı de erişebilirsiniz.

## <a name="remarks"></a>Açıklamalar

Çeşitli veri türlerini tek bir birimde birleştirmeniz gerektiğinde veya temel veri türlerinden hiçbiri ihtiyaçlarınıza uygun olmadığında bir yapı veri türü tanımlayın ve kullanın.

Bir yapı veri türünün varsayılan değeri, üyelerinden her birinin varsayılan değerlerinin birleşiminden oluşur.

## <a name="declaration-format"></a>Bildirim biçimi

Yapı bildirimi, [Yapı ifadesiyle](../statements/structure-statement.md) başlar ve `End Structure` ifadesiyle biter. `Structure`Bu ifade yapının adını sağlar, bu da yapının tanımlayan veri türünün tanımlayıcısıdır. Kodun diğer kısımları, bu yapının veri türünde olması için değişkenleri, parametreleri ve işlev dönüş değerlerini bildirmek üzere bu tanımlayıcıyı kullanabilir.

Ve deyimleri arasındaki bildirimler `Structure` `End Structure` yapının üyelerini tanımlar.

## <a name="member-access-levels"></a>Üye erişim düzeyleri

Her üyeyi, bir [Dim ifadesini](../statements/dim-statement.md) veya [Public](../modifiers/public.md), [Friend](../modifiers/friend.md)veya [Private](../modifiers/private.md)gibi erişim düzeyini belirten bir bildirimi kullanarak bildirmeniz gerekir. Bir `Dim` ifade kullanırsanız, erişim düzeyi varsayılan olarak ortak olur.

## <a name="programming-tips"></a>Programlama İpuçları

- **Bellek tüketimi.** Tüm bileşik veri türlerinde olduğu gibi, üyelerinin nominal depolama ayırmalarını birlikte ekleyerek bir yapının toplam bellek tüketimini güvenle hesaplayabilirsiniz. Ayrıca, bellekteki depolama sırasının bildirimin sıralamayla aynı olduğunu güvenli bir şekilde varsayamaz. Bir yapının depolama yerleşimini denetetmeniz gerekirse, <xref:System.Runtime.InteropServices.StructLayoutAttribute> özniteliğini `Structure` ifadeye uygulayabilirsiniz.

- **Birlikte çalışma konuları.** Otomasyon veya COM nesneleri gibi .NET Framework için yazılmayan bileşenlerle ilgili bir arabirimleriniz varsa, diğer ortamlardaki Kullanıcı tanımlı türlerin Visual Basic yapısı türleriyle uyumlu olmadığını aklınızda bulundurun.

- **Kan.** Herhangi bir yapı veri türünden veya bundan otomatik dönüşüm yoktur. [Işleç ifadesini](../statements/operator-statement.md)kullanarak yapınıza dönüştürme işleçleri tanımlayabilir ve her bir dönüştürme işlecini veya olarak bildirebilirsiniz `Widening` `Narrowing` .

- **Tür karakterleri.** Yapı veri türlerinde değişmez değer türü karakteri veya tanımlayıcı türü karakteri yok.

- **Çerçeve türü.** .NET Framework ilgili hiçbir tür yoktur. Tüm yapılar .NET Framework sınıfından devralınır <xref:System.ValueType?displayProperty=nameWithType> , ancak tek bir yapı öğesine karşılık gelir <xref:System.ValueType?displayProperty=nameWithType> .

## <a name="example"></a>Örnek

Aşağıdaki paradigma, bir yapının bildiriminin ana hattını gösterir.

```vb
[Public | Protected | Friend | Protected Friend | Private] Structure structname
    {Dim | Public | Friend | Private} member1 As datatype1
    ' ...
    {Dim | Public | Friend | Private} memberN As datatypeN
End Structure
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ValueType>
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- [Veri türleri](index.md)
- [Tür Dönüştürme İşlevleri](../functions/type-conversion-functions.md)
- [Dönüştürme Özeti](../keywords/conversion-summary.md)
- [Structure Yapısı](../statements/structure-statement.md)
- [Genişletme](../modifiers/widening.md)
- [Narrowing](../modifiers/narrowing.md)
- [Yapılar](../../programming-guide/language-features/data-types/structures.md)
- [Veri Türlerinin Etkili Kullanımı](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
