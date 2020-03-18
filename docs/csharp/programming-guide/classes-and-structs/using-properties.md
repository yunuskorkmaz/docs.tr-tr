---
title: Özellikleri Kullanma - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- set accessor [C#]
- get accessor [C#]
- properties [C#], about properties
ms.assetid: f7f67b05-0983-4cdb-96af-1855d24c967c
ms.openlocfilehash: d873f626b660bb6bd94710add4543e21e11823d6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77452025"
---
# <a name="using-properties-c-programming-guide"></a>Özellikleri Kullanma (C# Programlama Kılavuzu)

Özellikler hem alanların hem de yöntemlerin yönlerini birleştirir. Bir nesnenin kullanıcısı için, bir özellik bir alan gibi görünür, özelliği niçin erişmek aynı sözdizimini gerektirir. Bir sınıfın uygulayıcısı için özellik, [get](../../language-reference/keywords/get.md) accessor'u ve/veya [ayarlanmış](../../language-reference/keywords/set.md) bir erişime sahibini temsil eden bir veya iki kod bloğudur. Özellik okunduğunda `get` erişime erişimiçin kod bloğu yürütülür; özellik yeni bir `set` değer atandığında, erişimcinin kod bloğu yürütülür. Erişimi olmayan `set` bir özellik salt okunur olarak kabul edilir. Erişimi olmayan `get` bir özellik yalnızca yazma olarak kabul edilir. Her iki erişime de sahip olan bir özellik okuma yazmadır.

Alanların aksine, özellikler değişken olarak sınıflandırılmaz. Bu nedenle, bir özelliği [ref](../../language-reference/keywords/ref.md) veya [çıkış](../../language-reference/keywords/out-parameter-modifier.md) parametresi olarak geçiremezsiniz.

Özelliklerin birçok kullanımı vardır: bir değişikliğe izin vermeden önce verileri doğrulayabilirler; bu verilerin veritabanı gibi başka bir kaynaktan alındığı bir sınıftaki verileri saydam bir şekilde ortaya çıkarabilirler; bir olayı yükseltmek veya diğer alanların değerini değiştirmek gibi veriler değiştirildiğinde bir eylemde bulunabilirler.

Özellikler, alanın erişim düzeyi belirtilerek sınıf bloğunda, ardından özelliğin türünü, ardından özelliğin adını ve ardından -erişimci ve/veya `get` `set` erişimci bildiren bir kod bloğu belirtilerek bildirilir. Örnek:

[!code-csharp[csProgGuideProperties#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#7)]

Bu örnekte, `Month` erişime girenin `set` `Month` değerin 1 ile 12 arasında ayarlandıkdan emin olabilmesi için bir özellik olarak bildirilir. Özellik, `Month` gerçek değeri izlemek için özel bir alan kullanır. Bir mülkün verilerinin gerçek konumu genellikle mülkün "destek deposu" olarak adlandırılır. Özelliklerin özel alanları destek deposu olarak kullanması yaygındır. Alan, yalnızca özelliği arayarak değiştirilebilmesini sağlamak için özel olarak işaretlenir. Genel ve özel erişim kısıtlamaları hakkında daha fazla bilgi için [Erişim Değiştiriciler'e](./access-modifiers.md)bakın.

Otomatik olarak uygulanan özellikler, basit özellik bildirimleri için basitleştirilmiş sözdizimi sağlar. Daha fazla bilgi için otomatik [olarak uygulanan özellikler'e](auto-implemented-properties.md)bakın.

## <a name="the-get-accessor"></a>Erişime Erişim

`get` Erişimcinin gövdesi bir yöntemin kine benzer. Özellik türünün bir değerini döndürmesi gerekir. `get` Erişimcinin yürütülmesi alanın değerini okumaya eşdeğerdir. Örneğin, özel değişkeni `get` erişimciden döndürdüyseniz ve optimizasyonlar etkinleştirildiğinde, `get` erişimci yöntemine çağrı derleyici tarafından sıralanır, böylece yöntem arama yükü yoktur. Ancak, derleyici derleme zamanında hangi yöntemin çalışma zamanında çağrılabileceğini bilmediği için sanal `get` bir erişimci yöntemi eklenemez. Aşağıda, özel `get` bir alanın `_name`değerini döndüren bir erişimci ve

[!code-csharp[csProgGuideProperties#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#8)]

Bir atamanın hedefi dışında, özellik başvururken, `get` erişimci özelliğin değerini okumak için çağrılır. Örnek:

[!code-csharp[csProgGuideProperties#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#9)]

Erişime `get` erişimeden bir [iade](../../language-reference/keywords/return.md) veya [atma](../../language-reference/keywords/throw.md) deyimiyle sona ermelidir ve denetim erişimci gövdeden akamaz.

Bu `get` erişimci kullanarak nesnenin durumunu değiştirmek için kötü bir programlama stilidir. Örneğin, aşağıdaki `_number` erişimci, alana her erişigeldiğinde nesnenin durumunu değiştirmenin yan etkisini üretir.

[!code-csharp[csProgGuideProperties#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#10)]

Erişime `get` giren alan değerini döndürmek veya hesaplamak ve döndürmek için kullanılabilir. Örnek:

[!code-csharp[csProgGuideProperties#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#11)]

Önceki kod segmentinde, `Name` bir değer özelliği atamazsanız, değeri `NA`döndürecek.

## <a name="the-set-accessor"></a>Ayarlı Erişimci

Erişimci, `set` dönüş türü [geçersiz](../../language-reference/builtin-types/void.md)olan bir yönteme benzer. Bu özelliğin türü `value`olan , adlı örtük bir parametre kullanır. Aşağıdaki örnekte, `set` `Name` bir erişimci özelliği eklenir:

[!code-csharp[csProgGuideProperties#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#12)]

Bir değer özelliğiatadığınızda, `set` yeni değer sağlayan bir bağımsız değişken kullanılarak erişimci çağrılır. Örnek:

[!code-csharp[csProgGuideProperties#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#13)]

Bir `set` erişimcideki yerel değişken bildirimi `value`için örtük parametre adını kullanmak bir hatadır.

## <a name="remarks"></a>Açıklamalar

Özellikler , , `public` `private` `protected`, `internal`, `protected internal` `private protected`veya . olarak işaretlenebilir. Bu erişim değiştiriciler, sınıfın kullanıcılarının özelliğe nasıl erişebileceğini tanımlar. Aynı `get` `set` özelliğin ve erişimcilerin farklı erişim değiştiricileri olabilir. `get` Örneğin, tür dışından `public` salt okunur erişime izin verilebilir ve `set` olabilir `private` `protected`veya . Daha fazla bilgi için [Erişim Değiştiriciler'e](./access-modifiers.md)bakın.

Bir `static` özellik, anahtar kelime kullanılarak statik özellik olarak beyan edilebilir. Bu, sınıfın hiçbir örneği olmasa bile özelliği her zaman arayanların kullanımına açık hale getirir. Daha fazla bilgi için Statik [Sınıflar ve Statik Sınıf Üyeleri'ne](./static-classes-and-static-class-members.md)bakın.

Bir [özellik, sanal](../../language-reference/keywords/virtual.md) anahtar sözcük kullanılarak sanal özellik olarak işaretlenebilir. Bu, türetilmiş sınıfların [geçersiz kılma](../../language-reference/keywords/override.md) anahtar sözcük kullanarak özellik davranışını geçersiz kılmasına olanak tanır. Bu seçenekler hakkında daha fazla bilgi için [Kalıtım'a](inheritance.md)bakın.

Sanal bir özelliği geçersiz kılan bir özellik de [mühürlenebilir](../../language-reference/keywords/sealed.md)ve türetilmiş sınıflar için artık sanal olmadığını belirtir. Son olarak, bir özellik [soyut](../../language-reference/keywords/abstract.md)ilan edilebilir. Bu, sınıfta uygulama olmadığı ve türemiş sınıfların kendi uygulamalarını yazmaları gerektiği anlamına gelir. Bu seçenekler hakkında daha fazla bilgi için [Özet ve Mühürlü Sınıflar ve Sınıf Üyeleri'ne](abstract-and-sealed-classes-and-class-members.md)bakın.
  
> [!NOTE]
> Sanal, [soyut](../../language-reference/keywords/abstract.md)bir [virtual](../../language-reference/keywords/virtual.md)özellik kullanmak veya [statik](../../language-reference/keywords/static.md) bir özelliğin bir erişimcisi üzerinde değiştirici [geçersiz kılmak](../../language-reference/keywords/override.md) bir hatadır.

## <a name="example"></a>Örnek

Bu örnek, statik ve salt okunur özellikleri gösterir. Klavyeden çalışanın adını kabul eder, 1'e `NumberOfEmployees` göre artışlar ve Çalışan adını ve numarasını görüntüler.

[!code-csharp[csProgGuideProperties#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#2)]

## <a name="example"></a>Örnek

Bu örnek, türemiş bir sınıfta aynı ada sahip başka bir özellik tarafından gizli bir taban sınıfta bir özellik erişmek için nasıl gösterir:

[!code-csharp[csProgGuideProperties#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#3)]

Önceki örnekte önemli noktalar şunlardır:

- Türemiş sınıftaki özellik, `Name` `Name` özelliği taban sınıfta gizler. Böyle bir durumda, `new` değiştirici türemiş sınıfta özelliğin bildiriminde kullanılır:

     [!code-csharp[csProgGuideProperties#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#4)]  

- Döküm `(Employee)` taban sınıftaki gizli özelliğe erişmek için kullanılır:

     [!code-csharp[csProgGuideProperties#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#5)]

     Üyeleri gizleme hakkında daha fazla bilgi için [yeni Değiştirici'ye](../../language-reference/keywords/new-modifier.md)bakın.

## <a name="example"></a>Örnek

Bu örnekte, iki `Cube` `Square`sınıf ve , `Shape`soyut bir sınıf `Area` uygulamak ve soyut özelliğigeçersiz. Özelliklerüzerinde geçersiz [kılma değiştiricinin](../../language-reference/keywords/override.md) kullanımına dikkat edin. Program bir giriş olarak yan kabul eder ve kare ve küp için alanları hesaplar. Ayrıca bir giriş olarak alanı kabul eder ve kare ve küp için ilgili tarafı hesaplar.

[!code-csharp[csProgGuideProperties#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#6)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Özellikler](properties.md)
- [Arayüz Özellikleri](interface-properties.md)
- [Otomatik Uygulanan Özellikler](auto-implemented-properties.md)
