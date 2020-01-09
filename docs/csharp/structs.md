---
title: Yapılar- C# kılavuz
description: Yapı türü ve bunları nasıl oluşturacağınız hakkında bilgi edinin
ms.date: 10/12/2016
ms.technology: csharp-fundamentals
ms.assetid: a7094b8c-7229-4b6f-82fc-824d0ea0ec40
ms.openlocfilehash: cdfe2a763058b8f568ede2ff93c918c2dae874f7
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346897"
---
# <a name="structs"></a>Yapılar

*Struct* bir değer türüdür. Bir struct oluşturulduğunda, yapının atandığı değişken yapının gerçek verilerini barındırır. Yapı yeni bir değişkene atandığında, kopyalanır. Bu nedenle, yeni değişken ve özgün değişken aynı verilerin iki ayrı kopyasını içerir. Bir kopyada yapılan değişiklikler diğer kopyayı etkilemez.

Değer türü değişkenleri doğrudan değerlerini içerir, bu da belleğin, değişkenin bildirildiği bağlamda satır içi olarak ayrıldığı anlamına gelir. Değer türü değişkenler için ayrı bir yığın ayırma veya çöp toplama ek yükü yoktur.

Değer türlerinin iki kategorisi vardır: [struct](language-reference/keywords/struct.md) ve [enum](language-reference/builtin-types/enum.md).

Yerleşik sayısal türler yapı birimleridir ve erişebileceğiniz özelliklere ve yöntemlere sahiptirler:

[!code-csharp[Static Method](../../samples/snippets/csharp/concepts/structs/static-method.cs)]

Ancak bunları, basit olmayan türler gibi bu değerlere bildirir ve bunlara atanır:

[!code-csharp[Assign Values](../../samples/snippets/csharp/concepts/structs/assign-value.cs)]

Değer türleri *korumalıdır*, yani örneğin, bir türü <xref:System.Int32>türetemezsiniz ve Kullanıcı tanımlı herhangi bir sınıftan veya yapıdan devralacak bir struct tanımlayamazsınız, çünkü bir struct yalnızca <xref:System.ValueType>devralabilir. Ancak, bir struct bir veya daha fazla arabirim uygulayabilir. Bir yapı türünü arabirim türüne çevirebilirsiniz; Bu, bir *kutulama* işleminin yapıyı yönetilen yığında bir başvuru türü nesnesinin içine sarmasına neden olur. Paketleme işlemleri, bir <xref:System.Object> giriş parametresi olarak alan bir yönteme bir değer türü geçirdiğinizde oluşur. Daha fazla bilgi için bkz. [kutulama ve kutudan](./programming-guide/types/boxing-and-unboxing.md )çıkarma.

Kendi özel değer türlerinizi oluşturmak için [struct](./language-reference/keywords/struct.md) anahtar sözcüğünü kullanırsınız. Genellikle, bir yapı aşağıdaki örnekte gösterildiği gibi küçük bir ilgili değişkenler kümesi için kapsayıcı olarak kullanılır:

[!code-csharp[Struct Keyword](../../samples/snippets/csharp/concepts/structs/struct-keyword.cs)]

.NET Framework değer türleri hakkında daha fazla bilgi için bkz. [ortak tür sistemi](../standard/common-type-system.md).

Yapılar sınıflarla aynı sözdiziminin çoğunu paylaşır, ancak yapılar sınıflardan daha sınırlıdır:

- Bir struct bildiriminde, `const` veya `static`olarak belirtilemediği sürece alanlar başlatılamaz.

- Struct parametresiz bir Oluşturucu (parametresiz bir Oluşturucu) veya sonlandırıcısı bildiremez.

- Yapılar atamaya kopyalanır. Bir yapı yeni bir değişkene atandığında, tüm veriler kopyalanır ve yeni kopyada yapılan değişiklikler özgün kopyanın verilerini değiştirmez. Bu, sözlük < dize, myStruct > gibi değer türlerinin koleksiyonlarıyla çalışırken unutmamak önemlidir.

- Yapılar, değer türlerdir ve sınıflardır başvuru türleridir.

- Sınıfların aksine, yapılar `new` işleci kullanılmadan oluşturulabilir.

   > [!NOTE]
   > .NET Core 2,1 ve üzeri sürümlerde, bir yapı türü [Yeni işleç](language-reference/operators/new-operator.md) veya [varsayılan değişmez değer](language-reference/operators/default.md#default-literal)kullanılarak veya özel alanlarının her biri başlatılarak oluşturulmalıdır. Daha fazla bilgi için [2,0 sürümünden 2,1 ' e geçiş Için Son değişiklikler](../core/compatibility/2.0-2.1.md#corefx)konusuna bakın.

- Yapılar, parametreleri olan oluşturucular bildirebilir.

- Yapı, başka bir struct veya sınıftan devralınabilir ve bir sınıfın temeli olamaz. Tüm yapılar, <xref:System.Object>devralan <xref:System.ValueType>doğrudan devralır.

- Sınıf gibi bir yapı, arabirimler uygulayabilir.

## <a name="nullable-value-types"></a>Boş değer atanabilen değer türleri

Sıradan değer türlerinin değeri [null](language-reference/keywords/null.md)olamaz. Ancak, türden sonra bir `?` ekleyerek null yapılabilir değer türleri oluşturabilirsiniz. Örneğin `int?`, [null](./language-reference/keywords/null.md)değeri de olan bir `int` türüdür. Null yapılabilir değer türleri <xref:System.Nullable%601>genel yapı türü örnekleridir. Null olabilen değer türleri, genellikle sayısal değerlerin null veya tanımsız olabileceği veritabanlarına veri geçirirken faydalıdır. Daha fazla bilgi için bkz. [Nullable değer türleri](language-reference/builtin-types/nullable-value-types.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Sınıflar](programming-guide/classes-and-structs/classes.md)
- [Temel Türler](basic-types.md)
