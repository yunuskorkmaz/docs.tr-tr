---
title: Erişim değiştiricileri- C# Programlama Kılavuzu
ms.date: 03/08/2020
helpviewer_keywords:
- C# Language, access modifiers
- access modifiers [C#], about
ms.assetid: 6e81ee82-224f-4a12-9baf-a0dca2656c5b
ms.openlocfilehash: 749d53344a2518966cfa5d937069ba73dfd6be8f
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628234"
---
# <a name="access-modifiers-c-programming-guide"></a>Erişim Değiştiricileri (C# Programlama Kılavuzu)

Tüm türler ve tür üyelerinin erişilebilirlik düzeyi vardır. Erişilebilirlik düzeyi, derlemenizin veya diğer derlemelerinizdeki diğer koddan kullanılıp kullanılamayacağını denetler. Bir tür veya üyenin, bunu bildirdiğinizde erişilebilirliği belirtmek için aşağıdaki erişim değiştiricilerini kullanın:

- [ortak](../../language-reference/keywords/public.md): türe veya üyeye aynı derlemedeki veya buna başvuran başka bir derlemede herhangi bir kod tarafından erişilebilir.
- [özel](../../language-reference/keywords/private.md): tür veya üyeye yalnızca aynı `class` veya `struct`kodla erişilebilir.
- [korumalı](../../language-reference/keywords/protected.md): türe veya üyeye yalnızca aynı `class`veya bu `class`türetilmiş bir `class` ait kodla erişilebilir.
- [iç](../../language-reference/keywords/internal.md): tür veya üyeye aynı derlemedeki herhangi bir kod tarafından erişilebilir, ancak başka bir derlemeden erişilebilir.
- [korumalı iç](../../language-reference/keywords/protected-internal.md): türe veya üyeye, bildirildiği derlemede ya da başka bir derlemedeki türetilmiş bir `class` erişilebilir.
- [özel korumalı](../../language-reference/keywords/private-protected.md): tür veya üyeye yalnızca bildirim derlemesi içinde, aynı `class` veya bu `class`türetilmiş bir türde kod ile erişilebilir.

Aşağıdaki örneklerde, bir tür ve üye üzerinde erişim değiştiricilerin nasıl belirtildiğini gösterilmektedir:

[!code-csharp[PublicAccess](~/samples/snippets/csharp/objectoriented/accessmodifiers.cs#PublicAccess)]

Tüm erişim değiştiricileri tüm bağlamlardaki tüm türler veya Üyeler için geçerli değildir. Bazı durumlarda, bir tür üyesinin erişilebilirliği, kapsayan türünün erişilebilirliği tarafından kısıtlanıyor.

## <a name="class-and-struct-accessibility"></a>Sınıf ve yapı erişilebilirliği  

Bir ad alanı içinde doğrudan tanımlanmış sınıflar ve yapılar (diğer bir deyişle, diğer sınıfların veya yapıların içinde olmayan) `public` ya da `internal`olabilir. `Internal`, hiçbir erişim değiştiricisi belirtilmemişse varsayılandır.  

İç içe sınıflar ve yapılar da dahil olmak üzere yapı üyeleri, `public`, `internal`veya `private`olarak bildirilebilecek. İç içe sınıflar ve yapılar dahil olmak üzere sınıf üyeleri `public`, `protected internal`, `protected`, `internal`, `private protected`veya `private`olabilir. İç içe sınıflar ve yapılar dahil olmak üzere sınıf ve yapı üyelerinin varsayılan olarak `private` erişimi vardır. Özel iç içe türler, kapsayan tür dışından erişilebilir değildir.

Türetilmiş sınıfların temel türlerinden daha fazla erişilebilirliği olamaz. Bir iç sınıftan `A`türetilmiş `B` ortak sınıf bildiremezsiniz. İzin veriliyorsa, `A` tüm `protected` veya `internal` üyeleri türetilmiş sınıftan erişilebilir olduğundan `A` genel hale getirme etkisi vardır.

`InternalsVisibleToAttribute`kullanarak, belirli diğer derlemelerin iç türlerinizi erişmesini sağlayabilirsiniz. Daha fazla bilgi için bkz. [arkadaş derlemeler](../../../standard/assembly/friend.md).

## <a name="class-and-struct-member-accessibility"></a>Sınıf ve yapı üye erişilebilirliği  

Sınıf üyeleri (iç içe geçmiş sınıflar ve yapılar dahil) altı erişim türlerinden herhangi biriyle bildirilebilecek. Yapılar devralmayı desteklemediğinden, yapı üyeleri `protected`, `protected internal`veya `private protected` olarak bildirilemez.

Normalde, bir üyenin erişilebilirliği onu içeren tür erişilebilirliğiyle daha büyük değildir. Ancak, bir iç sınıfın `public` üyesine, üye arabirim yöntemleri uygularsa veya ortak bir temel sınıfta tanımlanan sanal yöntemleri geçersiz kıldığında derleme dışından erişilebilir.

Herhangi bir üye alanının, özelliğin veya olayın türü en azından üyenin kendisi olarak erişilebilir olmalıdır. Benzer şekilde, her yöntemin, dizin oluşturucunun veya temsilcinin dönüş türü ve parametre türleri en azından üyenin kendisi olarak erişilebilir olmalıdır. Örneğin, `C` da `public`olmadığı takdirde bir sınıf `C` döndüren bir `public` yöntemi `M` olamaz. Benzer şekilde, `A` `private`olarak bildirilirse, `A` türünde bir `protected` özelliğine sahip olamaz.

Kullanıcı tanımlı işleçler her zaman `public` ve `static`olarak bildirilmelidir. Daha fazla bilgi için bkz. [operatör aşırı yüklemesi](../../language-reference/operators/operator-overloading.md).

Sonlandırıcılar erişilebilirlik değiştiricilerine sahip olamaz.

Bir `class` veya `struct` üyesinin erişim düzeyini ayarlamak için, aşağıdaki örnekte gösterildiği gibi, üye bildirimine uygun anahtar sözcüğü ekleyin.

[!code-csharp[MethodAccess](~/samples/snippets/csharp/objectoriented/accessmodifiers.cs#MethodAccess)]

## <a name="other-types"></a>Diğer türler

Bir ad alanı içinde doğrudan tanımlanmış arabirimler `public` veya `internal` olabilir ve tıpkı sınıflar ve yapılar gibi, arabirimler `internal` erişim için varsayılan değer olarak kullanılır. Arabirim üyeleri varsayılan olarak `public`, çünkü bir arabirimin amacı diğer türlerin bir sınıfa veya yapıya erişmesini sağlamaktır. Arabirim üyesi bildirimleri herhangi bir erişim değiştiricisi içerebilir. Bu, bir sınıfın tüm uygulayıcılar için gereken ortak uygulamaları sağlamak üzere statik yöntemler için kullanışlıdır.

Numaralandırma üyeleri her zaman `public`, hiçbir erişim değiştiricisi uygulanmaz.

Temsilciler sınıflar ve yapılar gibi davranır. Varsayılan olarak, bir ad alanı içinde doğrudan bildirildiği zaman erişim `internal` ve iç içe zaman erişim `private`.

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Yapılar](./index.md)
- [Arabirimler](../interfaces/index.md)
- [private](../../language-reference/keywords/private.md)
- [public](../../language-reference/keywords/public.md)
- [internal](../../language-reference/keywords/internal.md)
- [protected](../../language-reference/keywords/protected.md)
- [protected internal](../../language-reference/keywords/protected-internal.md)
- [private protected](../../language-reference/keywords/private-protected.md)
- [class](../../language-reference/keywords/class.md)
- [struct](../../language-reference/builtin-types/struct.md)
- [interface](../../language-reference/keywords/interface.md)
