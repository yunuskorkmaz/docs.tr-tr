---
title: Alanlar - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- fields [C#]
ms.assetid: 3cbb2f61-75f8-4cce-b4ef-f5d1b3de0db7
ms.openlocfilehash: 46d4f77a4a490b2acdb5da20b9a477f27c38d410
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77628247"
---
# <a name="fields-c-programming-guide"></a>Alanlar (C# Programlama Kılavuzu)

*Alan,* doğrudan bir [sınıf](../../language-reference/keywords/class.md) veya [yapı](../../language-reference/builtin-types/struct.md)içinde bildirilen herhangi bir türdeki değişkendir. Alanlar, içerme türüne *üyedir.*

Bir sınıf veya yapı örnek alanları, statik alanlar veya her ikisi olabilir. Örnek alanlar bir tür örneğine özgüdir. T sınıfı nız varsa, F örnek alanı ile, T türünden iki nesne oluşturabilir ve diğer nesnedeki değeri etkilemeden her nesnedeki F değerini değiştirebilirsiniz. Bunun aksine, statik bir alan sınıfın kendisine aittir ve bu sınıfın tüm örnekleri arasında paylaşılır. Statik alana yalnızca sınıf adını kullanarak erişebilirsiniz. Statik alana bir örnek adıyla erişerseniz, [CS0176](../../misc/cs0176.md) derleme zamanı hatası alırsınız.

Genel olarak, alanları yalnızca özel veya korumalı erişilebilirliği olan değişkenler için kullanmalısınız. Sınıfınızın istemci koduna maruz kaktEttiği veriler [yöntemler,](./methods.md) [özellikler](./properties.md)ve [dizinleyiciler](../indexers/index.md)aracılığıyla sağlanmalıdır. Bu yapıları iç alanlara dolaylı erişim için kullanarak, geçersiz giriş değerlerine karşı koruyabilirsiniz. Kamu malı tarafından açığa çıkarılan verileri depolayan özel alana *destek deposu* veya *destek alanı*denir.

Alanlar genellikle birden fazla sınıf yöntemi için erişilebilir olması gereken verileri depolar ve tek bir yöntemin kullanım ömründen daha uzun süre depolanmalıdır. Örneğin, takvim tarihini temsil eden bir sınıfın üç tamsayı alanı olabilir: biri ay için, biri gün için ve diğeri yıl için. Tek bir yöntemin kapsamı dışında kullanılmayan *değişkenler,* yöntem gövdesi içinde yerel değişkenler olarak bildirilmelidir.

Alanlar sınıf bloğunda alanın erişim düzeyi belirtilerek, alan türü ve ardından alanın adı belirtilerek bildirilir. Örnek:

[!code-csharp[csProgGuideObjects#61](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#61)]

Bir nesnedeki bir alana erişmek için, nesne adından sonra bir nokta ekleyin `objectname.fieldname`ve ardından alanın adını, 'deki gibi. Örnek:

[!code-csharp[csProgGuideObjects#62](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#62)]

Alan beyan edildiğinde atama işleci kullanılarak bir alana bir başlangıç değeri verilebilir. `day` Alanı otomatik olarak atamak `"Monday"`için , örneğin, `day` aşağıdaki örnekte olduğu gibi beyan eylesiniz:

[!code-csharp[csProgGuideObjects#63](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#63)]

Alanlar, nesne örneğinin oluşturucusu çağrılmadan hemen önce başharflere alınır. Oluşturucu bir alanın değerini atatırsa, alan bildirimi sırasında verilen herhangi bir değerin üzerine yazar. Daha fazla bilgi için Yapı [Oluşturucuları Kullanma'ya](./using-constructors.md)bakın.

> [!NOTE]
> Alan baş harflerini diğer örnek alanlara atıfta bulunamaz.

Alanlar [genel,](../../language-reference/keywords/public.md) [özel,](../../language-reference/keywords/private.md) [korumalı,](../../language-reference/keywords/protected.md) [dahili,](../../language-reference/keywords/internal.md) [korumalı iç](../../language-reference/keywords/protected-internal.md)veya [özel korumalı](../../language-reference/keywords/private-protected.md)olarak işaretlenebilir. Bu erişim değiştiriciler, sınıfın kullanıcılarının alanlara nasıl erişebileceğini tanımlar. Daha fazla bilgi için [Erişim Değiştiriciler'e](./access-modifiers.md)bakın.

Bir alan isteğe bağlı olarak [statik](../../language-reference/keywords/static.md)olarak bildirilebilir. Bu, sınıfın hiçbir örneği olmasa bile alanı her zaman arayanlariçin kullanılabilir hale getirir. Daha fazla bilgi için Statik [Sınıflar ve Statik Sınıf Üyeleri'ne](./static-classes-and-static-class-members.md)bakın.

Bir alan [yalnızca okunur](../../language-reference/keywords/readonly.md)ilan edilebilir. Salt okunur alan yalnızca başlatma sırasında veya bir oluşturucuya bir değer atanabilir. C# derleyicisinin derleme zamanında, yalnızca çalışma zamanında statik bir salt okunur alanın değerine erişememesi dışında, bir `static readonly` alan sabite çok benzer. Daha fazla bilgi için [Sabitler'e](./constants.md)bakın.

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Structs](./index.md)
- [Oluşturucuları Kullanma](./using-constructors.md)
- [Devralma](./inheritance.md)
- [Erişim Değiştiricileri](./access-modifiers.md)
- [Soyut ve Korumalı Sınıflar ve Sınıf Üyeleri](./abstract-and-sealed-classes-and-class-members.md)
