---
title: Alanlar- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- fields [C#]
ms.assetid: 3cbb2f61-75f8-4cce-b4ef-f5d1b3de0db7
ms.openlocfilehash: 46d4f77a4a490b2acdb5da20b9a477f27c38d410
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628247"
---
# <a name="fields-c-programming-guide"></a>Alanlar (C# Programlama Kılavuzu)

*Alan* , bir [sınıf](../../language-reference/keywords/class.md) veya [Yapı](../../language-reference/builtin-types/struct.md)içinde doğrudan tanımlanmış herhangi bir türdeki değişkendir. Alanlar, kapsayan türlerinin *üyeleridir* .

Bir sınıf veya yapının örnek alanları, statik alanları veya her ikisi birden olabilir. Örnek alanları, bir türün örneğine özeldir. Örnek alanı F olan bir sınıf T 'si varsa, T türünde iki nesne oluşturabilir ve diğer nesnedeki değeri etkilemeden her bir nesnede F değerini değiştirebilirsiniz. Buna karşılık, statik bir alan sınıfa aittir ve bu sınıfın tüm örnekleri arasında paylaşılır. Statik alana yalnızca sınıf adını kullanarak erişebilirsiniz. Statik alana bir örnek adı ile eriştiğinizde, [CS0176](../../misc/cs0176.md) derleme zamanı hatası alırsınız.

Genellikle, yalnızca özel veya korumalı erişilebilirliği olan değişkenler için alanları kullanmanız gerekir. Sınıfınızın istemci koduna sunduğu veriler [Yöntemler](./methods.md), [Özellikler](./properties.md)ve [Dizin oluşturucular](../indexers/index.md)aracılığıyla sağlanmalıdır. İç alanlara dolaylı erişim için bu yapıları kullanarak, geçersiz giriş değerlerine karşı koruma sağlayabilirsiniz. Ortak bir özellik tarafından açığa çıkarılan verileri depolayan özel bir alan, *yedekleme deposu* veya *yedekleme alanı*olarak adlandırılır.

Alanlar genellikle birden fazla sınıf yöntemine erişilebilir olması gereken verileri depolar ve tek bir yöntemin yaşam süresinden daha uzun bir süre içinde depolanmalıdır. Örneğin, bir takvim tarihini temsil eden bir sınıf üç tamsayı alanına sahip olabilir: biri ayda, biri gün için ve diğeri yıl için. Tek bir yöntemin kapsamı dışında kullanılmayan değişkenler, Yöntem gövdesinin içinde *yerel değişkenler* olarak bildirilmelidir.

Alanlar, alanın erişim düzeyini, ardından alanın türü ve ardından alanın adı tarafından belirtilen sınıf bloğunda belirtilir. Örnek:

[!code-csharp[csProgGuideObjects#61](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#61)]

Bir nesnedeki alana erişmek için, nesne adından sonra, `objectname.fieldname`' de olduğu gibi alanın adı ile bir nokta ekleyin. Örnek:

[!code-csharp[csProgGuideObjects#62](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#62)]

Alan bildirildiği zaman atama işleci kullanılarak bir alana ilk değer verilebilir. `day` alanını `"Monday"`otomatik olarak atamak için, örneğin, aşağıdaki örnekte olduğu gibi `day` bildirimini yapmanız gerekir:

[!code-csharp[csProgGuideObjects#63](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#63)]

Alanlar, nesne örneği Oluşturucusu çağrılmadan hemen önce başlatılır. Oluşturucu bir alanın değerini atadığında, alan bildirimi sırasında verilen değerin üzerine yazar. Daha fazla bilgi için bkz. [oluşturucular kullanma](./using-constructors.md).

> [!NOTE]
> Alan başlatıcısı diğer örnek alanlarına başvuramaz.

Alanlar [ortak](../../language-reference/keywords/public.md), [özel](../../language-reference/keywords/private.md), [korumalı](../../language-reference/keywords/protected.md), [iç](../../language-reference/keywords/internal.md), [korunan iç](../../language-reference/keywords/protected-internal.md)veya [özel korumalı](../../language-reference/keywords/private-protected.md)olarak işaretlenebilir. Bu erişim değiştiricileri, sınıfın kullanıcılarının alanlara nasıl erişebileceğini tanımlar. Daha fazla bilgi için bkz. [erişim değiştiricileri](./access-modifiers.md).

Bir alan, isteğe bağlı olarak [statik](../../language-reference/keywords/static.md)olarak bildirilemez. Bu, sınıfın bir örneği mevcut olmasa bile, alanı her zaman çağıranlar için kullanılabilir hale getirir. Daha fazla bilgi için bkz. [statik sınıflar ve statik sınıf üyeleri](./static-classes-and-static-class-members.md).

Bir alan [ReadOnly](../../language-reference/keywords/readonly.md)olarak bildirilemez. Salt okunurdur bir alana yalnızca başlatma sırasında veya oluşturucuda bir değer atanabilir. Bir `static readonly` alanı, C# derleyicinin derleme zamanında statik bir salt okuma alanının değerine erişimi olmaması dışında, yalnızca çalışma zamanında bir sabit değere benzer. Daha fazla bilgi için bkz. [sabitler](./constants.md).

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Yapılar](./index.md)
- [Oluşturucuları Kullanma](./using-constructors.md)
- [Devralma](./inheritance.md)
- [Erişim Değiştiricileri](./access-modifiers.md)
- [Soyut ve Korumalı Sınıflar ve Sınıf Üyeleri](./abstract-and-sealed-classes-and-class-members.md)
