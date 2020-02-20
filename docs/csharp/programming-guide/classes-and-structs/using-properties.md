---
title: Özellikleri kullanma- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- set accessor [C#]
- get accessor [C#]
- properties [C#], about properties
ms.assetid: f7f67b05-0983-4cdb-96af-1855d24c967c
ms.openlocfilehash: d873f626b660bb6bd94710add4543e21e11823d6
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452025"
---
# <a name="using-properties-c-programming-guide"></a>Özellikleri Kullanma (C# Programlama Kılavuzu)

Özellikler her iki alanın ve yöntemin yönlerini birleştirir. Bir nesnenin kullanıcısına, bir özellik bir alan gibi görünür, özelliğe erişim de aynı sözdizimini gerektirir. Bir sınıfın uygulayıcısı için bir özellik bir veya iki kod blobunun yanı sıra bir [Get](../../language-reference/keywords/get.md) erişimcisini ve/veya [set](../../language-reference/keywords/set.md) erişimcisini temsil eder. `get` erişimcisinin kod bloğu, özellik okuma sırasında yürütülür; `set` erişimcisine yönelik kod bloğu, özelliğe yeni bir değer atandığında yürütülür. `set` erişimcisi olmayan bir özellik salt okunurdur. `get` erişimcisi olmayan bir özellik salt yazılır olarak değerlendirilir. Her iki erişimciyi sahip bir özellik okuma-yazma ' dır.

Alanların aksine, özellikler değişken olarak sınıflandırılmaz. Bu nedenle, bir özelliği [ref](../../language-reference/keywords/ref.md) veya [Out](../../language-reference/keywords/out-parameter-modifier.md) parametresi olarak geçiremezsiniz.

Özelliklerin birçok kullanımı vardır: bir değişikliğe izin vermeden önce verileri doğrulayabilir; verilerin aslında bir veritabanı gibi başka bir kaynaktan alındığı bir sınıf üzerinde saydam bir şekilde veri sunabilir; bir olayı oluşturma veya diğer alanların değerini değiştirme gibi veriler değiştirildiğinde bir eylem gerçekleştirebilir.

Özellikler, alanın erişim düzeyini, sonra özelliğin türünü ve sonra da bir `get`erişimcisi ve/veya `set` erişimcisi bildiren bir kod bloğu belirtilerek, sınıf bloğunda bildirilir. Örneğin:

[!code-csharp[csProgGuideProperties#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#7)]

Bu örnekte, `Month` özellik olarak bildirildiği için `set` erişimcisinin `Month` değerinin 1 ile 12 arasında ayarlanmış olduğundan emin olabilir. `Month` özelliği, gerçek değeri izlemek için özel bir alan kullanır. Özelliğin verilerinin gerçek konumu genellikle özelliğin "yedekleme deposu" olarak adlandırılır. Özelliklerin özel alanları bir yedekleme deposu olarak kullanması yaygındır. Bu alan, yalnızca özelliği çağırarak değiştirilebilmesi için özel olarak işaretlenir. Ortak ve özel erişim kısıtlamaları hakkında daha fazla bilgi için bkz. [erişim değiştiricileri](./access-modifiers.md).

Otomatik uygulanan özellikler basit özellik bildirimleri için Basitleştirilmiş söz dizimi sağlar. Daha fazla bilgi için bkz. [Otomatik uygulanan özellikler](auto-implemented-properties.md).

## <a name="the-get-accessor"></a>Get erişimcisi

`get` erişimcisinin gövdesi bir yönteme benzer. Özellik türünün bir değerini döndürmesi gerekir. `get` erişimcisinin yürütülmesi alanın değerini okumayla eşdeğerdir. Örneğin, `get` erişimcisinden özel değişkeni döndürmekte ve iyileştirmeler etkinleştirildikten sonra, `get` erişimci metoduna yapılan çağrı derleyici tarafından satır içine alınır ve bu nedenle bir yöntem çağrı yükü yoktur. Ancak, derleyici derleme zamanında hangi yöntemin çalışma zamanında çağrıldığı hakkında bilgi sahibi olmadığından, bir sanal `get` erişimci yöntemi satır içine alınamaz. Aşağıda bir özel alan `_name`değerini döndüren bir `get` erişimcisi verilmiştir:

[!code-csharp[csProgGuideProperties#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#8)]

Özelliğe başvurduğunuzda, bir atamanın hedefi dışında, özelliğin değerini okumak için `get` erişimcisi çağrılır. Örneğin:

[!code-csharp[csProgGuideProperties#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#9)]

`get` erişimcisinin [Return](../../language-reference/keywords/return.md) veya [throw](../../language-reference/keywords/throw.md) ifadesinde bitmesi ve denetim erişimci gövdesinin akışını kapatamıyor olması gerekir.

`get` erişimcisini kullanarak nesnenin durumunu değiştirmek için hatalı bir programlama stilidir. Örneğin, aşağıdaki erişimci `_number` alana her erişildiğinde nesnenin durumunu değiştirmenin yan etkisini üretir.

[!code-csharp[csProgGuideProperties#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#10)]

`get` erişimcisi, alan değerini döndürmek veya hesaplamak ve döndürmek için kullanılabilir. Örneğin:

[!code-csharp[csProgGuideProperties#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#11)]

Önceki kod segmentinde, `Name` özelliğine bir değer atamadıysanız, `NA`değeri döndürülür.

## <a name="the-set-accessor"></a>Set erişimcisi

`set` erişimcisi, dönüş türü [void](../../language-reference/builtin-types/void.md)olan bir yönteme benzer. Türü özelliğin türü olan `value`adlı örtük bir parametre kullanır. Aşağıdaki örnekte, `Name` özelliğine bir `set` erişimcisi eklenmiştir:

[!code-csharp[csProgGuideProperties#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#12)]

Özelliğe bir değer atadığınızda, `set` erişimcisi yeni değeri sağlayan bir bağımsız değişken kullanılarak çağrılır. Örneğin:

[!code-csharp[csProgGuideProperties#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#13)]

`set` erişimcisindeki yerel değişken bildirimi için `value`örtük parametre adını kullanmak hatadır.

## <a name="remarks"></a>Açıklamalar

Özellikler `public`, `private`, `protected`, `internal`, `protected internal` veya `private protected`olarak işaretlenebilir. Bu erişim değiştiricileri, sınıfın kullanıcılarının özelliğe nasıl erişekullanabileceğinizi tanımlar. Aynı özelliğin `get` ve `set` erişimcileri farklı erişim değiştiricilerine sahip olabilir. Örneğin `get`, türün dışından salt okuma erişimine izin vermek için `public` olabilir ve `set` `private` veya `protected`olabilir. Daha fazla bilgi için bkz. [erişim değiştiricileri](./access-modifiers.md).

Bir özellik `static` anahtar sözcüğü kullanılarak statik bir özellik olarak bildirilemez. Bu özellik, sınıfın bir örneği mevcut olmasa bile, özelliği herhangi bir zamanda çağıranlar için kullanılabilir hale getirir. Daha fazla bilgi için bkz. [statik sınıflar ve statik sınıf üyeleri](./static-classes-and-static-class-members.md).

Bir özellik [sanal](../../language-reference/keywords/virtual.md) anahtar sözcüğü kullanılarak sanal bir özellik olarak işaretlenebilir. Bu, türetilmiş sınıfların [geçersiz kılma](../../language-reference/keywords/override.md) anahtar sözcüğünü kullanarak özellik davranışını geçersiz kılmasını sağlar. Bu seçenekler hakkında daha fazla bilgi için bkz. [Devralma](inheritance.md).

Sanal bir özelliği geçersiz kılan bir özellik de [mühürlenebilir](../../language-reference/keywords/sealed.md), bu da türetilmiş sınıflar için artık sanal değildir. Son olarak, bir özellik [soyut](../../language-reference/keywords/abstract.md)olarak bildirilemez. Bu, sınıfta bir uygulama olmadığı ve türetilen sınıfların kendi uygulamasını yazması gerektiği anlamına gelir. Bu seçenekler hakkında daha fazla bilgi için bkz. [soyut ve korumalı sınıflar ve sınıf üyeleri](abstract-and-sealed-classes-and-class-members.md).
  
> [!NOTE]
> [Statik](../../language-reference/keywords/static.md) bir özelliğin erişimcisi üzerinde [sanal](../../language-reference/keywords/virtual.md), [Özet](../../language-reference/keywords/abstract.md)veya [geçersiz kılma](../../language-reference/keywords/override.md) değiştiricisi kullanmak hatadır.

## <a name="example"></a>Örnek

Bu örnek örnek, statik ve salt okunurdur özelliklerini gösterir. Klavyeden çalışanın adını kabul eder, 1 ile `NumberOfEmployees` artırır ve çalışan adını ve numarasını görüntüler.

[!code-csharp[csProgGuideProperties#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#2)]

## <a name="example"></a>Örnek

Bu örnekte, türetilmiş bir sınıfta aynı ada sahip başka bir özellik tarafından gizlenen bir temel sınıftaki bir özelliğe nasıl erişebileceğiniz gösterilmektedir:

[!code-csharp[csProgGuideProperties#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#3)]

Aşağıda, önceki örnekteki önemli noktaları verilmiştir:

- Türetilmiş sınıftaki özellik `Name`, temel sınıftaki özelliği `Name` gizler. Böyle bir durumda `new` değiştiricisi türetilmiş sınıftaki özelliğin bildiriminde kullanılır:

     [!code-csharp[csProgGuideProperties#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#4)]  

- Cast `(Employee)`, temel sınıftaki Hidden özelliğine erişmek için kullanılır:

     [!code-csharp[csProgGuideProperties#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#5)]

     Üyeleri gizleme hakkında daha fazla bilgi için bkz. [Yeni değiştirici](../../language-reference/keywords/new-modifier.md).

## <a name="example"></a>Örnek

Bu örnekte, iki sınıf, `Cube` ve `Square`, soyut bir sınıfı uygular `Shape`ve soyut `Area` özelliğini geçersiz kılar. Özelliklerde geçersiz kılma değiştiricisinin kullanımını göz önünde [kılarsınız](../../language-reference/keywords/override.md) . Program, yüzü bir giriş olarak kabul eder ve kare ve küpün alanını hesaplar. Ayrıca, alanı bir girdi olarak kabul eder ve kare ve küp için ilgili tarafı hesaplar.

[!code-csharp[csProgGuideProperties#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#6)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Özellikler](properties.md)
- [Arabirim Özellikleri](interface-properties.md)
- [Otomatik Uygulanan Özellikler](auto-implemented-properties.md)
