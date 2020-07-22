---
title: Özellikleri kullanma-C# Programlama Kılavuzu
description: Bu örnekler C# içindeki özellikleri kullanmayı gösterir. Get ve set erişimcilerinin okuma ve yazma erişimini nasıl uygulayacağınızı görün ve özellikler için kullanımları öğrenin.
ms.date: 07/20/2015
helpviewer_keywords:
- set accessor [C#]
- get accessor [C#]
- properties [C#], about properties
ms.assetid: f7f67b05-0983-4cdb-96af-1855d24c967c
ms.openlocfilehash: 51ca0a37022c99bfbd9d61f2cc47f529d535e72a
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864663"
---
# <a name="using-properties-c-programming-guide"></a>Özellikleri Kullanma (C# Programlama Kılavuzu)

Özellikler her iki alanın ve yöntemin yönlerini birleştirir. Bir nesnenin kullanıcısına, bir özellik bir alan gibi görünür, özelliğe erişim de aynı sözdizimini gerektirir. Bir sınıfın uygulayıcısı için bir özellik bir veya iki kod blobunun yanı sıra bir [Get](../../language-reference/keywords/get.md) erişimcisini ve/veya [set](../../language-reference/keywords/set.md) erişimcisini temsil eder. Erişimci için kod bloğu, `get` Özellik okuma sırasında yürütülür. erişimci için kod bloğu, `set` özelliğe yeni bir değer atandığında yürütülür. Erişimcisi olmayan bir özellik `set` salt okunurdur. Erişimcisi olmayan bir özellik `get` salt yazılır olarak değerlendirilir. Her iki erişimciyi sahip bir özellik okuma-yazma ' dır.

Alanların aksine, özellikler değişken olarak sınıflandırılmaz. Bu nedenle, bir özelliği [ref](../../language-reference/keywords/ref.md) veya [Out](../../language-reference/keywords/out-parameter-modifier.md) parametresi olarak geçiremezsiniz.

Özelliklerin birçok kullanımı vardır: bir değişikliğe izin vermeden önce verileri doğrulayabilir; verilerin aslında bir veritabanı gibi başka bir kaynaktan alındığı bir sınıf üzerinde saydam bir şekilde veri sunabilir; bir olayı oluşturma veya diğer alanların değerini değiştirme gibi veriler değiştirildiğinde bir eylem gerçekleştirebilir.

Özellikler, alanın erişim düzeyini, sonra özelliğin türünü ve sonra özelliğin adını ve ardından bir `get` -erişimci ve/veya erişimci bildiren bir kod bloğunu belirterek sınıf bloğunda bildirilir `set` . Örnek:

[!code-csharp[csProgGuideProperties#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#7)]

Bu örnekte, `Month` `set` erişimcinin `Month` değerin 1 ile 12 arasında ayarlandığından emin olması için bir özellik olarak bildirilmiştir. `Month`Özelliği, gerçek değeri izlemek için bir özel alan kullanır. Özelliğin verilerinin gerçek konumu genellikle özelliğin "yedekleme deposu" olarak adlandırılır. Özelliklerin özel alanları bir yedekleme deposu olarak kullanması yaygındır. Bu alan, yalnızca özelliği çağırarak değiştirilebilmesi için özel olarak işaretlenir. Ortak ve özel erişim kısıtlamaları hakkında daha fazla bilgi için bkz. [erişim değiştiricileri](./access-modifiers.md).

Otomatik uygulanan özellikler basit özellik bildirimleri için Basitleştirilmiş söz dizimi sağlar. Daha fazla bilgi için bkz. [Otomatik uygulanan özellikler](auto-implemented-properties.md).

## <a name="the-get-accessor"></a>Get erişimcisi

`get`Erişimcinin gövdesi bir yönteme benzer. Özellik türünün bir değerini döndürmesi gerekir. `get`Erişimcinin yürütülmesi alanın değerini okumayla eşdeğerdir. Örneğin, erişimcisinden özel değişkeni döndürmekte `get` ve iyileştirmeler etkinleştirildiğinde, `get` erişimci metoduna yapılan çağrı derleyici tarafından satır içine alınır ve bu nedenle Yöntem çağrısı yoktur. Ancak, `get` derleyici derleme zamanında hangi yöntemin çalışma zamanında çağrıldığı hakkında bilgi içermediği için bir sanal erişimci yöntemi satır içine alınamaz. Aşağıda `get` özel bir alanın değerini döndüren bir erişimci verilmiştir `_name` :

[!code-csharp[csProgGuideProperties#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#8)]

Özelliğe başvurduğunuzda, bir atamanın hedefi dışında, `get` özelliğin değerini okumak için erişimci çağrılır. Örnek:

[!code-csharp[csProgGuideProperties#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#9)]

`get`Erişimci bir [Return](../../language-reference/keywords/return.md) veya [throw](../../language-reference/keywords/throw.md) ifadesinde bitmelidir ve denetim erişimci gövdesini kapatamıyor olmalıdır.

Erişimciyi kullanarak nesnenin durumunu değiştirmek için hatalı bir programlama stilidir `get` . Örneğin, aşağıdaki erişimci alana her erişildiğinde nesnenin durumunu değiştirmenin yan etkisini üretir `_number` .

[!code-csharp[csProgGuideProperties#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#10)]

`get`Erişimci, alan değerini döndürmek veya hesaplamak ve döndürmek için kullanılabilir. Örnek:

[!code-csharp[csProgGuideProperties#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#11)]

Önceki kod segmentinde, özelliğe bir değer atamadıysanız, `Name` değer döndürür `NA` .

## <a name="the-set-accessor"></a>Set erişimcisi

`set`Erişimci, dönüş türü [void](../../language-reference/builtin-types/void.md)olan bir yönteme benzer. Türü özelliğin türü olan adlı örtük bir parametre kullanır `value` . Aşağıdaki örnekte, `set` özelliğine bir erişimci eklenmiştir `Name` :

[!code-csharp[csProgGuideProperties#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#12)]

Özelliğe bir değer atadığınızda, `set` erişimci yeni değer sağlayan bir bağımsız değişken kullanılarak çağrılır. Örnek:

[!code-csharp[csProgGuideProperties#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#13)]

`value`Bir erişimcinin yerel değişken bildirimi için örtük parametre adını kullanmak hatadır `set` .

## <a name="remarks"></a>Açıklamalar

Özellikler,,, `public` veya olarak `private` işaretlenebilir `protected` `internal` `protected internal` `private protected` . Bu erişim değiştiricileri, sınıfın kullanıcılarının özelliğe nasıl erişekullanabileceğinizi tanımlar. `get` `set` Aynı özelliğe yönelik ve erişimcileri farklı erişim değiştiricilerine sahip olabilir. Örneğin, `get` `public` türü dışından salt okuma erişimine izin vermek olabilir ve ya da olabilir `set` `private` `protected` . Daha fazla bilgi için bkz. [erişim değiştiricileri](./access-modifiers.md).

Özelliği anahtar sözcüğü kullanılarak statik bir özellik olarak bildirilemez `static` . Bu özellik, sınıfın bir örneği mevcut olmasa bile, özelliği herhangi bir zamanda çağıranlar için kullanılabilir hale getirir. Daha fazla bilgi için bkz. [statik sınıflar ve statik sınıf üyeleri](./static-classes-and-static-class-members.md).

Bir özellik [sanal](../../language-reference/keywords/virtual.md) anahtar sözcüğü kullanılarak sanal bir özellik olarak işaretlenebilir. Bu, türetilmiş sınıfların [geçersiz kılma](../../language-reference/keywords/override.md) anahtar sözcüğünü kullanarak özellik davranışını geçersiz kılmasını sağlar. Bu seçenekler hakkında daha fazla bilgi için bkz. [Devralma](inheritance.md).

Sanal bir özelliği geçersiz kılan bir özellik de [mühürlenebilir](../../language-reference/keywords/sealed.md), bu da türetilmiş sınıflar için artık sanal değildir. Son olarak, bir özellik [soyut](../../language-reference/keywords/abstract.md)olarak bildirilemez. Bu, sınıfta bir uygulama olmadığı ve türetilen sınıfların kendi uygulamasını yazması gerektiği anlamına gelir. Bu seçenekler hakkında daha fazla bilgi için bkz. [soyut ve korumalı sınıflar ve sınıf üyeleri](abstract-and-sealed-classes-and-class-members.md).
  
> [!NOTE]
> [Statik](../../language-reference/keywords/static.md) bir özelliğin erişimcisi üzerinde [sanal](../../language-reference/keywords/virtual.md), [Özet](../../language-reference/keywords/abstract.md)veya [geçersiz kılma](../../language-reference/keywords/override.md) değiştiricisi kullanmak hatadır.

## <a name="example"></a>Örnek

Bu örnek örnek, statik ve salt okunurdur özelliklerini gösterir. Klavye üzerinden çalışanın adını kabul eder, `NumberOfEmployees` 1 artırır ve çalışan adını ve numarasını görüntüler.

[!code-csharp[csProgGuideProperties#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#2)]

## <a name="example"></a>Örnek

Bu örnekte, türetilmiş bir sınıfta aynı ada sahip başka bir özellik tarafından gizlenen bir temel sınıftaki bir özelliğe nasıl erişebileceğiniz gösterilmektedir:

[!code-csharp[csProgGuideProperties#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#3)]

Aşağıda, önceki örnekteki önemli noktaları verilmiştir:

- `Name`Türetilmiş sınıftaki özelliği, `Name` temel sınıftaki özelliği gizler. Böyle bir durumda, `new` değiştirici türetilmiş sınıftaki özelliğin bildiriminde kullanılır:

     [!code-csharp[csProgGuideProperties#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#4)]  

- Atama, `(Employee)` temel sınıftaki gizli özelliğe erişmek için kullanılır:

     [!code-csharp[csProgGuideProperties#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#5)]

     Üyeleri gizleme hakkında daha fazla bilgi için bkz. [Yeni değiştirici](../../language-reference/keywords/new-modifier.md).

## <a name="example"></a>Örnek

Bu örnekte, iki sınıf, `Cube` ve `Square` soyut bir sınıfı uygular `Shape` ve soyut özelliğini geçersiz kılar `Area` . Özelliklerde geçersiz kılma değiştiricisinin kullanımını göz önünde [kılarsınız](../../language-reference/keywords/override.md) . Program, yüzü bir giriş olarak kabul eder ve kare ve küpün alanını hesaplar. Ayrıca, alanı bir girdi olarak kabul eder ve kare ve küp için ilgili tarafı hesaplar.

[!code-csharp[csProgGuideProperties#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#6)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Özellikler](properties.md)
- [Arabirim Özellikleri](interface-properties.md)
- [Otomatik Uygulanan Özellikler](auto-implemented-properties.md)
