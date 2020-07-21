---
title: Erişim değiştiricileri-C# Programlama Kılavuzu
description: C# ' deki tüm türler ve tür üyeleri, diğer koddan kullanılıp kullanılamayacağını denetleyen bir erişilebilirlik düzeyine sahiptir. Bu erişim değiştiricileri listesini gözden geçirin.
ms.date: 03/08/2020
helpviewer_keywords:
- C# Language, access modifiers
- access modifiers [C#], about
ms.assetid: 6e81ee82-224f-4a12-9baf-a0dca2656c5b
ms.openlocfilehash: 557f5d9f302b08d32896b462e86ce1d96710ff36
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474533"
---
# <a name="access-modifiers-c-programming-guide"></a>Erişim Değiştiricileri (C# Programlama Kılavuzu)

Tüm türler ve tür üyelerinin erişilebilirlik düzeyi vardır. Erişilebilirlik düzeyi, derlemenizin veya diğer derlemelerinizdeki diğer koddan kullanılıp kullanılamayacağını denetler. Bir tür veya üyenin, bunu bildirdiğinizde erişilebilirliği belirtmek için aşağıdaki erişim değiştiricilerini kullanın:

- [ortak](../../language-reference/keywords/public.md): türe veya üyeye aynı derlemedeki veya buna başvuran başka bir derlemede herhangi bir kod tarafından erişilebilir.
- [özel](../../language-reference/keywords/private.md): tür veya üyeye yalnızca aynı veya içindeki kodla erişilebilir `class` `struct` .
- [korumalı](../../language-reference/keywords/protected.md): tür veya üyeye yalnızca aynı veya aynı koda `class` sahip olan ya da ondan türetilmiş bir kod tarafından erişilebilir `class` `class` .
- [iç](../../language-reference/keywords/internal.md): tür veya üyeye aynı derlemedeki herhangi bir kod tarafından erişilebilir, ancak başka bir derlemeden erişilebilir.
- [korumalı iç](../../language-reference/keywords/protected-internal.md): türe veya üyeye, bildirildiği derlemede ya da başka bir derlemedeki türetilmiş bir kodla erişilebilir `class` .
- [özel korumalı](../../language-reference/keywords/private-protected.md): tür veya üyeye yalnızca bildirim derlemesi içinde, aynı `class` veya ondan türetilmiş bir türde kodla erişilebilir `class` .

Aşağıdaki örneklerde, bir tür ve üye üzerinde erişim değiştiricilerin nasıl belirtildiğini gösterilmektedir:

[!code-csharp[PublicAccess](~/samples/snippets/csharp/objectoriented/accessmodifiers.cs#PublicAccess)]

Tüm erişim değiştiricileri tüm bağlamlardaki tüm türler veya Üyeler için geçerli değildir. Bazı durumlarda, bir tür üyesinin erişilebilirliği, kapsayan türünün erişilebilirliği tarafından kısıtlanıyor.

## <a name="class-and-struct-accessibility"></a>Sınıf ve yapı erişilebilirliği  

Bir ad alanı içinde doğrudan tanımlanmış sınıflar ve yapılar (diğer bir deyişle, diğer sınıfların veya yapıların içinde iç içe olmayan diğer bir deyişle) ya da olabilir `public` `internal` . `Internal`, hiçbir erişim değiştiricisi belirtilmemişse varsayılandır.  

İç içe sınıflar ve yapılar dahil yapı üyeleri, veya olarak bildirilemez `public` `internal` `private` . İç içe sınıflar ve yapılar dahil olmak üzere sınıf üyeleri,,,, `public` `protected internal` veya olabilir `protected` `internal` `private protected` `private` . İç içe sınıflar ve yapılar dahil olmak üzere sınıf ve yapı üyelerinin `private` Varsayılan olarak erişimi vardır. Özel iç içe türler, kapsayan tür dışından erişilebilir değildir.

Türetilmiş sınıfların temel türlerinden daha fazla erişilebilirliği olamaz. Bir iç sınıftan türeyen ortak bir sınıf bildiremezsiniz `B` `A` . İzin veriliyorsa, `A` tüm `protected` veya `internal` üyeleri `A` türetilmiş sınıftan erişilebilir olduğundan ortak hale getirme etkisi olur.

Kullanarak iç Türlerinize erişmek için belirli diğer derlemelerin de etkinleştirebilirsiniz `InternalsVisibleToAttribute` . Daha fazla bilgi için bkz. [arkadaş derlemeler](../../../standard/assembly/friend.md).

## <a name="class-and-struct-member-accessibility"></a>Sınıf ve yapı üye erişilebilirliği  

Sınıf üyeleri (iç içe geçmiş sınıflar ve yapılar dahil) altı erişim türlerinden herhangi biriyle bildirilebilecek. `protected` `protected internal` Yapılar devralma desteklemediğinden, yapı üyeleri, veya olarak bildirilemez `private protected` .

Normalde, bir üyenin erişilebilirliği onu içeren tür erişilebilirliğiyle daha büyük değildir. Ancak, `public` üye arabirim yöntemleri uygularsa veya ortak bir temel sınıfta tanımlanan sanal yöntemleri geçersiz kıldığında, iç sınıfın bir üyesine derleme dışından erişilebilir.

Herhangi bir üye alanının, özelliğin veya olayın türü en azından üyenin kendisi olarak erişilebilir olmalıdır. Benzer şekilde, her yöntemin, dizin oluşturucunun veya temsilcinin dönüş türü ve parametre türleri en azından üyenin kendisi olarak erişilebilir olmalıdır. Örneğin, `public` `M` aynı zamanda bir sınıfı döndüren bir metoda sahip olabilirsiniz `C` `C` `public` . Benzer şekilde, `protected` olarak bildirilirse türünde bir özelliğine sahip `A` olamaz `A` `private` .

Kullanıcı tanımlı işleçler her zaman ve olarak bildirilmelidir `public` `static` . Daha fazla bilgi için bkz. [operatör aşırı yüklemesi](../../language-reference/operators/operator-overloading.md).

Sonlandırıcılar erişilebilirlik değiştiricilerine sahip olamaz.

Bir veya üyesi için erişim düzeyini ayarlamak `class` için `struct` , aşağıdaki örnekte gösterildiği gibi, üye bildirimine uygun anahtar sözcüğü ekleyin.

[!code-csharp[MethodAccess](~/samples/snippets/csharp/objectoriented/accessmodifiers.cs#MethodAccess)]

## <a name="other-types"></a>Diğer türler

Bir ad alanı içinde doğrudan tanımlanmış arabirimler, `public` `internal` sınıflar ve yapılar gibi, varsayılan olarak erişim için arabirimler olabilir `internal` . Arabirim üyeleri `public` Varsayılan olarak, bir arabirimin amacı diğer türlerin bir sınıfa veya yapıya erişmesine olanak sağlamaktır. Arabirim üyesi bildirimleri herhangi bir erişim değiştiricisi içerebilir. Bu, bir sınıfın tüm uygulayıcılar için gereken ortak uygulamaları sağlamak üzere statik yöntemler için kullanışlıdır.

Numaralandırma üyeleri her zaman `public` ve erişim değiştiricileri uygulanmaz.

Temsilciler sınıflar ve yapılar gibi davranır. Varsayılan olarak, `internal` bir ad alanı içinde bildirildiği zaman erişime sahiptirler ve `private` iç içe olduğunda erişim vardır.

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve yapılar](./index.md)
- [Arabirimler](../interfaces/index.md)
- [private](../../language-reference/keywords/private.md)
- [genel](../../language-reference/keywords/public.md)
- [internal](../../language-reference/keywords/internal.md)
- [protected](../../language-reference/keywords/protected.md)
- [protected internal](../../language-reference/keywords/protected-internal.md)
- [private protected](../../language-reference/keywords/private-protected.md)
- [sınıfı](../../language-reference/keywords/class.md)
- [sýný](../../language-reference/builtin-types/struct.md)
- [arayüz](../../language-reference/keywords/interface.md)
