---
title: Alanlar-C# Programlama Kılavuzu
description: C# ' deki bir alan, doğrudan bir sınıf veya yapı içinde belirtilen her türlü tür değişkenidir. Alanlar, kapsayan türlerinin üyeleridir.
ms.date: 07/20/2015
helpviewer_keywords:
- fields [C#]
ms.assetid: 3cbb2f61-75f8-4cce-b4ef-f5d1b3de0db7
ms.openlocfilehash: 58e60e1dc0b574ae922e6a27a22978b91aca4ec4
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899054"
---
# <a name="fields-c-programming-guide"></a>Alanlar (C# Programlama Kılavuzu)

*Alan* , bir [sınıf](../../language-reference/keywords/class.md) veya [Yapı](../../language-reference/builtin-types/struct.md)içinde doğrudan tanımlanmış herhangi bir türdeki değişkendir. Alanlar, kapsayan türlerinin *üyeleridir* .

Bir sınıf veya yapının örnek alanları, statik alanları veya her ikisi birden olabilir. Örnek alanları, bir türün örneğine özeldir. Örnek alanı F olan bir sınıf T 'si varsa, T türünde iki nesne oluşturabilir ve diğer nesnedeki değeri etkilemeden her bir nesnede F değerini değiştirebilirsiniz. Buna karşılık, statik bir alan sınıfa aittir ve bu sınıfın tüm örnekleri arasında paylaşılır. Statik alana yalnızca sınıf adını kullanarak erişebilirsiniz. Statik alana bir örnek adı ile eriştiğinizde, [CS0176](../../misc/cs0176.md) derleme zamanı hatası alırsınız.

Genellikle, yalnızca özel veya korumalı erişilebilirliği olan değişkenler için alanları kullanmanız gerekir. Sınıfınızın istemci koduna sunduğu veriler [Yöntemler](./methods.md), [Özellikler](./properties.md)ve [Dizin oluşturucular](../indexers/index.md)aracılığıyla sağlanmalıdır. İç alanlara dolaylı erişim için bu yapıları kullanarak, geçersiz giriş değerlerine karşı koruma sağlayabilirsiniz. Ortak bir özellik tarafından açığa çıkarılan verileri depolayan özel bir alan, *yedekleme deposu* veya *yedekleme alanı* olarak adlandırılır.

Alanlar genellikle birden fazla sınıf yöntemine erişilebilir olması gereken verileri depolar ve tek bir yöntemin yaşam süresinden daha uzun bir süre içinde depolanmalıdır. Örneğin, bir takvim tarihini temsil eden bir sınıf üç tamsayı alanına sahip olabilir: biri ayda, biri gün için ve diğeri yıl için. Tek bir yöntemin kapsamı dışında kullanılmayan değişkenler, Yöntem gövdesinin içinde *yerel değişkenler* olarak bildirilmelidir.

Alanlar, alanın erişim düzeyini, ardından alanın türü ve ardından alanın adı tarafından belirtilen sınıf bloğunda belirtilir. Örneğin:

[!code-csharp[fields#1](snippets/fields/Program.cs#1)]

Bir nesne içindeki bir alana erişmek için, nesne adından sonra, ' de olduğu gibi alanın adı ile bir nokta ekleyin `objectname.fieldname` . Örneğin:

[!code-csharp[fields#2](snippets/fields/Program.cs#2)]

Alan bildirildiği zaman atama işleci kullanılarak bir alana ilk değer verilebilir. Alanı için otomatik olarak atamak için `day` `"Monday"` , örneğin, `day` Aşağıdaki örnekte olduğu gibi bildirimini yapmanız gerekir:

[!code-csharp[fields#3](snippets/fields/Program.cs#3)]

Alanlar, nesne örneği Oluşturucusu çağrılmadan hemen önce başlatılır. Oluşturucu bir alanın değerini atadığında, alan bildirimi sırasında verilen değerin üzerine yazar. Daha fazla bilgi için bkz. [oluşturucular kullanma](./using-constructors.md).

> [!NOTE]
> Alan başlatıcısı diğer örnek alanlarına başvuramaz.

Alanlar [ortak](../../language-reference/keywords/public.md), [özel](../../language-reference/keywords/private.md), [korumalı](../../language-reference/keywords/protected.md), [iç](../../language-reference/keywords/internal.md), [korunan iç](../../language-reference/keywords/protected-internal.md)veya [özel korumalı](../../language-reference/keywords/private-protected.md)olarak işaretlenebilir. Bu erişim değiştiricileri, sınıfın kullanıcılarının alanlara nasıl erişebileceğini tanımlar. Daha fazla bilgi için bkz. [erişim değiştiricileri](./access-modifiers.md).

Bir alan, isteğe bağlı olarak [statik](../../language-reference/keywords/static.md)olarak bildirilemez. Bu, sınıfın bir örneği mevcut olmasa bile, alanı her zaman çağıranlar için kullanılabilir hale getirir. Daha fazla bilgi için bkz. [statik sınıflar ve statik sınıf üyeleri](./static-classes-and-static-class-members.md).

Bir alan [ReadOnly](../../language-reference/keywords/readonly.md)olarak bildirilemez. Salt okunurdur bir alana yalnızca başlatma sırasında veya oluşturucuda bir değer atanabilir. Bir `static readonly` alan, C# derleyicisinin derleme zamanında statik bir salt okuma alanının değerine erişiminin olmaması dışında, yalnızca çalışma zamanında bir sabit değere benzer. Daha fazla bilgi için bkz. [sabitler](./constants.md).

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Yapılar](./index.md)
- [Oluşturucular Kullanma](./using-constructors.md)
- [Devralma](./inheritance.md)
- [Erişim Değiştiricileri](./access-modifiers.md)
- [Soyut ve Korumalı Sınıflar ve Sınıf Üyeleri](./abstract-and-sealed-classes-and-class-members.md)
