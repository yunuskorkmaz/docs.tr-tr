---
title: Erişim Değiştiriciler - C# Programlama Kılavuzu
ms.date: 03/08/2020
helpviewer_keywords:
- C# Language, access modifiers
- access modifiers [C#], about
ms.assetid: 6e81ee82-224f-4a12-9baf-a0dca2656c5b
ms.openlocfilehash: 749d53344a2518966cfa5d937069ba73dfd6be8f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77628234"
---
# <a name="access-modifiers-c-programming-guide"></a>Erişim Değiştiricileri (C# Programlama Kılavuzu)

Tüm tür ve tür üyeleri erişilebilirlik düzeyine sahiptir. Erişilebilirlik düzeyi, bunların derlemenizdeki diğer kodlardan mı yoksa diğer derlemelerinizden mi kullanılabileceğini denetler. Bir türün veya üyenin erişilebilirliğini bildirmek için aşağıdaki erişim değiştiricilerini kullanın:

- [public](../../language-reference/keywords/public.md): Tür veya üyeye, aynı derlemede veya ona atıfta bulunan başka bir derlemedeki başka bir kodla erişilebilir.
- [private](../../language-reference/keywords/private.md): Tür veya üye aynı `class` veya `struct`sadece kod ile erişilebilir .
- [korumalı](../../language-reference/keywords/protected.md): Tür etek veya üye ye `class`yalnızca aynı `class` kodla veya `class`ondan türetilen bir kodla erişilebilir.
- [dahili](../../language-reference/keywords/internal.md): Tür veya üye ye aynı derlemedeki herhangi bir kodtarafından erişilebilir, ancak başka bir derlemeden erişilemez.
- [korumalı iç](../../language-reference/keywords/protected-internal.md): Tür veya üye, beyan edildiği derlemedeki herhangi bir kodtarafından veya `class` başka bir derlemede türetilen bir koddan erişilebilir.
- [private protected](../../language-reference/keywords/private-protected.md): Tür veya üye, yalnızca beyan eden assemblyi içinde, aynı `class` kodla veya `class`ondan türetilen bir türde erişilebilir.

Aşağıdaki örnekler, bir tür ve üye üzerinde erişim değiştiriciler nasıl belirtin gösterilmektedir:

[!code-csharp[PublicAccess](~/samples/snippets/csharp/objectoriented/accessmodifiers.cs#PublicAccess)]

Tüm erişim değiştiriciler tüm bağlamlarda tüm türleri veya üyeleri için geçerli değildir. Bazı durumlarda, bir tür üyesinin erişilebilirliği, içerdiği türün erişilebilirliğiyle sınırlandırılır.

## <a name="class-and-struct-accessibility"></a>Sınıf ve yapı erişilebilirliği  

Doğrudan bir ad alanı içinde bildirilen sınıflar ve structs (diğer sınıflar veya structs içinde `public` iç `internal`içe değildir) ya da olabilir. `Internal`erişim değiştiricisi belirtilmemişse varsayılandır.  

İç içe sınıflar ve structs dahil olmak üzere `public` `internal`Struct üyeleri, , , veya `private`. İç içe sınıflar ve yapılar da dahil `public`olmak `protected internal` `protected`üzere `internal` `private protected`sınıf `private`üyeleri , , , , , veya . İç içe sınıflar ve structs dahil olmak üzere `private` sınıf ve yapı üyeleri varsayılan olarak erişilebilmiştir. Özel iç içe çeşitli türlere içerme türü dışından erişilemez.

Türetilen sınıflar, taban türlerinden daha fazla erişilebilirlik sahibi olamaz. Bir iç sınıftan `B` `A`türeyen bir genel sınıf ilan edemez. İzin verilirse, türemiş `A` sınıftan `protected` tümveya `internal` üyeler `A` erişilebildiğinden, herkese açık hale getirme etkisi ne olur?

Belirli diğer derlemelerin dahili türlerinize erişmesini `InternalsVisibleToAttribute`etkinleştirebilirsiniz. Daha fazla bilgi için [Arkadaş Derlemeleri'ne](../../../standard/assembly/friend.md)bakın.

## <a name="class-and-struct-member-accessibility"></a>Sınıf ve yapı üyesi erişilebilirliği  

Sınıf üyeleri (iç içe sınıflar ve structs dahil) erişim altı tür herhangi biri ile ilan edilebilir. Yapı üyeleri , "veya `protected` `protected internal` `private protected` yapılaşmalar kalıtımı desteklemediği için" olarak beyan edilemez.

Normalde, bir üyenin erişilebilirliği, onu içeren türün erişilebilirliğinden büyük değildir. Ancak, `public` üye arabirim yöntemlerini uygularsa veya ortak taban sınıfında tanımlanan sanal yöntemleri geçersiz kılarsa, dahili bir sınıfın üyesine derleme dışından erişilebilir olabilir.

Herhangi bir üye alanının, özelliğinin veya etkinliğinin türü en az üyenin kendisi kadar erişilebilir olmalıdır. Benzer şekilde, herhangi bir yöntemin, dizinleyicinin veya temsilcinin dönüş türü ve parametre türleri en az üyenin kendisi kadar erişilebilir olmalıdır. Örneğin, aynı `public` zamanda `M` `C` `C` `public`olmadığı sürece bir sınıfı döndüren bir yöntem olamaz. Aynı şekilde, '' olarak `protected` `private`beyan `A` `A` edilirse, türünde bir özelliği olamaz.

Kullanıcı tanımlı işleçler `public` her `static`zaman ve . Daha fazla bilgi için operatör [aşırı yüklemesi'ne](../../language-reference/operators/operator-overloading.md)bakın.

Finalize edenlerin erişilebilirlik değiştiricileri olamaz.

Bir `class` veya `struct` üyenin erişim düzeyini ayarlamak için, aşağıdaki örnekte gösterildiği gibi üye bildirimine uygun anahtar kelimeyi ekleyin.

[!code-csharp[MethodAccess](~/samples/snippets/csharp/objectoriented/accessmodifiers.cs#MethodAccess)]

## <a name="other-types"></a>Diğer türleri

Doğrudan bir ad alanı içinde `public` bildirilen `internal` arabirimler veya olabilir ve, sınıflar ve `internal` structs gibi, arabirimler erişim varsayılan. Arabirimin `public` amacı diğer türlerin bir sınıfa veya yapıya erişmesini etkinleştirmek olduğundan, arabirim üyeleri varsayılan olarak vardır. Arabirim üye bildirimleri herhangi bir erişim değiştirici içerebilir. Bu, bir sınıfın tüm uygulayıcıları tarafından gereken ortak uygulamaları sağlamak için statik yöntemler için en yararlıdır.

Numaralandırma üyeleri her `public`zaman vardır ve erişim değiştiriciler uygulanamaz.

Delegeler sınıflar ve yapı lar gibi olur. Varsayılan olarak, `internal` doğrudan bir ad alanı içinde `private` beyan edildiğinde erişebilirler ve iç içe geçtiklerinde erişebiliyorlar.

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Structs](./index.md)
- [Arabirimler](../interfaces/index.md)
- [Özel](../../language-reference/keywords/private.md)
- [Kamu](../../language-reference/keywords/public.md)
- [Iç](../../language-reference/keywords/internal.md)
- [protected](../../language-reference/keywords/protected.md)
- [protected internal](../../language-reference/keywords/protected-internal.md)
- [özel korumalı](../../language-reference/keywords/private-protected.md)
- [Sınıfı](../../language-reference/keywords/class.md)
- [Yapı](../../language-reference/builtin-types/struct.md)
- [Arabirim](../../language-reference/keywords/interface.md)
