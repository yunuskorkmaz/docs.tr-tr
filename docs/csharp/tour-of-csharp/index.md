---
title: C#-C# Kılavuzu turu
description: C# ' ta yeni misiniz? Dilin temel bilgilerini öğrenin.
ms.date: 08/06/2020
ms.openlocfilehash: 42c4ff59a520a1b99bbb2fb01d79d8902e16bdd5
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063555"
---
# <a name="a-tour-of-the-c-language"></a>C# dilinin turu

C# ("bkz. diyez") modern, nesne odaklı ve tür açısından güvenli bir programlama dilidir. C#, C ailesinin köklerine sahiptir ve C, C++, Java ve JavaScript programcıları için hemen tanıdık gelecektir. Bu tur, C# 8 ve önceki sürümlerde dilin önemli bileşenlerine genel bakış sunar. Etkileşimli örneklerle dili araştırmak istiyorsanız C# öğreticilerine [giriş](../tutorials/intro-to-csharp/index.md) ' i deneyin.

C#, nesne odaklı, ***bileşen odaklı*** bir programlama dilidir. C#, bu kavramları doğrudan desteklemek için dil yapıları sağlar ve c#, yazılım bileşenlerinin oluşturulması ve kullanılması için doğal bir dil yapar. Başlangıç noktası nedeniyle, C# yeni iş yüklerini destekleyecek ve yazılım tasarımı uygulamalarını gelişren özellikler ekledi.

Birçok C# özelliği sağlam ve dayanıklı uygulamalar oluşturmaya yardımcı olur. [***Çöp toplama***](../../standard/garbage-collection/index.md) , erişilemeyen kullanılmayan nesneler tarafından kullanılan belleği otomatik olarak geri kazanır. [***Özel durum işleme***](../programming-guide/exceptions/index.md) , hata algılama ve kurtarmaya yönelik yapılandırılmış ve genişletilebilir bir yaklaşım sağlar. [***Lambda ifadeleri***](../programming-guide/statements-expressions-operators/lambda-expressions.md) fonksiyonel programlama tekniklerini destekler. [***Sorgu sözdizimi***](../linq/index.md) , herhangi bir kaynaktaki verilerle çalışmak için ortak bir model oluşturur. [***Zaman uyumsuz işlemler***](../programming-guide/concepts/async/index.md) için dil desteği, dağıtılmış sistemler oluşturmak için söz dizimi sağlar. [***Model eşleştirme***](..//pattern-matching.md) , modern dağıtılan sistemlerdeki algoritmalardan kolayca veri ayırmak için söz dizimi sağlar. C# Birleşik bir [***tür sistemine***](../programming-guide/types/index.md)sahiptir. Ve gibi temel türler dahil olmak üzere tüm C# `int` türleri `double` , tek bir kök türünden devralınır `object` . Tüm türler ortak işlemler kümesini paylaşır. Herhangi bir türdeki değerler tutarlı bir şekilde depolanabilir, taşınır ve çalıştırılabilir. Ayrıca, C# hem Kullanıcı tanımlı başvuru türlerini hem de değer türlerini destekler. C#, basit yapıların nesnelerin dinamik ayrılmasına ve satır içi depolamaya olanak tanır.

C#, programları ve kitaplıkları zamanla uyumlu bir şekilde gelişebilmesini sağlamak için ***sürüm oluşturmayı*** vurgular. C# tasarımının sürüm oluşturma konuları tarafından doğrudan etkilenmiş olan yönleri `virtual` , ayrı ve `override` değiştiriciler, yöntem aşırı yükleme çözümlemesi kurallarını ve açık arabirim üyesi bildirimleri için desteği içerir.

## <a name="hello-world"></a>Merhaba dünya

"Hello, World" programı, genellikle bir programlama dilini tanıtmak için kullanılır. Burada C# ' de yer verilmiştir:

:::code language="csharp" interactive="try-dotnet" source="./snippets/shared/HelloWorld.cs":::

"Hello, World" programı, `using` ad alanına başvuran bir yönergeyle başlar `System` . Ad alanları, C# programlarının ve kitaplıklarının düzenlenmesi için hiyerarşik bir yol sağlar. Ad alanları türler ve diğer ad alanlarını içerir — örneğin, `System` ad alanı programda başvurulan sınıf gibi bir dizi tür içerir `Console` ve ve gibi diğer ad alanları vardır `IO` `Collections` . `using`Verilen bir ad alanına başvuruda bulunan bir yönerge, bu ad alanının üyesi olan türlerin nitelenmemiş kullanımını mümkün değildir. `using`Yönergesi nedeniyle program, `Console.WriteLine` için toplu olarak kullanabilir `System.Console.WriteLine` .

`Hello`"Hello, World" programı tarafından belirtilen sınıf tek bir üyeye sahiptir, yöntemi adlı `Main` . `Main`Yöntemi `static` değiştiriciyle birlikte bildirilmiştir. Örnek yöntemleri, anahtar sözcüğünü kullanarak belirli bir kapsayan nesne örneğine başvurabilir `this` , ancak statik yöntemler belirli bir nesneye başvuru olmadan çalışır. Kurala göre, adlı statik bir yöntem `Main` C# programının giriş noktası olarak görev yapar.

Programın çıktısı, `WriteLine` `Console` ad alanındaki sınıfının yöntemi tarafından üretilir `System` . Bu sınıf, varsayılan olarak derleyicinin otomatik olarak başvurduğu standart sınıf kitaplıkları tarafından sağlanır.

## <a name="types-and-variables"></a>Türler ve değişkenler

C# ' de iki tür tür vardır: *değer türleri* ve *başvuru türleri*. Değer türlerinin değişkenleri doğrudan verilerini içerir, ancak başvuru türündeki değişkenler verilerine başvuruları depolar, ikincisi ise nesneler olarak bilinir. Başvuru türleriyle, iki değişkenin aynı nesneye başvurması ve diğer değişken tarafından başvurulan nesneyi etkilemek için bir değişkende işlemler için mümkün olması mümkündür. Değer türleriyle, her birinin kendi verilerinin bir kopyasına sahiptir ve bir üzerindeki işlemler, diğerini etkileme ( `ref` ve `out` parametre değişkenleri hariç) için kullanılamaz.

***Tanımlayıcı*** bir değişken adıdır. Tanımlayıcı, bir boşluk olmadan Unicode karakterlerinden oluşan bir dizidir. Bir tanımlayıcı, öneki olan bir C# ayrılmış sözcüğü olabilir `@` . Diğer dillerle etkileşim kurarken faydalı olabilir.

C# ' nin değer türleri, *basit türlere*, *enum türlerine*, *yapı türlerine*ve *null yapılabilir değer türlerine*daha fazla bölünmüştür. C# ' nin başvuru türleri, *Sınıf türlerine*, *arabirim türlerine*, *dizi türlerine*ve *temsilci türlerine*daha fazla bölünmüştür.

Aşağıdaki ana hat C# tür sistemine genel bir bakış sağlar.

- [Değer türleri](../language-reference/builtin-types/value-types.md)
  - [Basit türler](../language-reference/builtin-types/value-types.md#built-in-value-types)
    - [İmzalanan integral](../language-reference/builtin-types/integral-numeric-types.md): `sbyte` , `short` , `int` ,`long`
    - [İşaretsiz integral](../language-reference/builtin-types/integral-numeric-types.md): `byte` , `ushort` , `uint` ,`ulong`
    - [Unicode karakterler](/dotnet/standard/base-types/character-encoding-introduction): `char` bir UTF-16 kod birimini temsil eden
    - [IEEE ikili kayan nokta](../language-reference/builtin-types/floating-point-numeric-types.md): `float` ,`double`
    - [Yüksek duyarlıklı ondalık kayan nokta](../language-reference/builtin-types/floating-point-numeric-types.md):`decimal`
    - Boolean `bool` değerleri temsil eden Boole değeri — ya da olan değerler `true``false`
  - [Sabit listesi türleri](../language-reference/builtin-types/enum.md)
    - Formun Kullanıcı tanımlı türleri `enum E {...}` . Bir `enum` tür, adlandırılmış sabitleri olan ayrı bir türdür. Her `enum` türün, sekiz integral türünden biri olması gereken temel bir türü vardır. Bir türün değer kümesi, `enum` temel alınan türün değerleri kümesiyle aynıdır.
  - [Yapı türleri](../language-reference/builtin-types/struct.md)
    - Formun Kullanıcı tanımlı türleri`struct S {...}`
  - [Boş değer atanabilen değer türleri](../language-reference/builtin-types/nullable-value-types.md)
    - Bir değere sahip diğer tüm değer türlerinin uzantıları `null`
  - [Demet değer türleri](../tuples.md)
    - Formun Kullanıcı tanımlı türleri`(T1, T2, ...)`
- [Başvuru türleri](../language-reference/keywords/reference-types.md)
  - [Sınıf türleri](../language-reference/keywords/class.md)
    - Diğer tüm türlerin Ultimate temel sınıfı:`object`
    - [Unicode dizeleri](/dotnet/standard/base-types/character-encoding-introduction): `string` bir UTF-16 kod birimi dizisini temsil eden
    - Formun Kullanıcı tanımlı türleri`class C {...}`
  - [Arabirim türleri](../language-reference/keywords/interface.md)
    - Formun Kullanıcı tanımlı türleri`interface I {...}`
  - [Dizi türleri](../programming-guide/arrays/index.md)
    - Tek ve çok boyutlu ve pürüzlü, örneğin,, `int[]` `int[,]` ve`int[][]`
  - [Temsilci türleri](../language-reference/keywords/delegate.md)
    - Formun Kullanıcı tanımlı türleri`delegate int D(...)`

C# programları yeni türler oluşturmak için *tür bildirimleri* kullanır. Tür bildiriminde yeni türün adı ve üyeleri belirtilir. C# tür kategorilerinin sayısı Kullanıcı tarafından tanımlanabilir: sınıf türleri, yapı türleri, arabirim türleri, sabit listesi türleri ve temsilci türleri.

- Bir `class` tür, veri üyeleri (alanlar) ve işlev üyeleri (Yöntemler, Özellikler ve diğerleri) içeren bir veri yapısını tanımlar. Sınıf türleri, tek devralma ve çok biçimlilik destekler, türetilmiş sınıfların temel sınıfları genişletebileceği ve özelleştireceği mekanizmalar.
- Bir `struct` tür, veri üyeleri ve işlev üyeleri olan bir yapıyı temsil eden bir sınıf türüne benzerdir. Ancak, sınıfların aksine yapılar değer türlerdir ve genellikle yığın ayırmayı gerektirmez. Yapı türleri Kullanıcı tarafından belirtilen devralmayı desteklemez ve tüm yapı türleri örtülü olarak türünden devralınır `object` .
- Bir `interface` tür, bir sözleşmeyi adlandırılmış bir ortak üye kümesi olarak tanımlar. `class`Uygulayan bir veya `struct` `interface` , arabirimin üyelerinin uygulamalarını sağlamalıdır. `interface`, Birden fazla taban arabiriminden devralınabilir ve bir `class` veya `struct` birden çok arabirim uygulayabilir.
- Bir `delegate` tür, belirli bir parametre listesi ve dönüş türü olan yöntemlere yapılan başvuruları temsil eder. Temsilciler, yöntemleri değişkenlere atanabilecek ve parametre olarak geçirilen varlıklar olarak işleme olanağı tanır. Temsilciler, işlevsel diller tarafından sunulan işlev türlerine benzerdir. Ayrıca, diğer bazı dillerde bulunan işlev işaretçileri kavramına de benzer. İşlev işaretçilerinden farklı olarak, temsilciler nesne odaklı ve tür açısından güvenlidir.

`class`,, `struct` `interface` Ve `delegate` türleri tüm genel türleri destekler, diğer türlerle parametrelenebilir.

C#, herhangi bir türdeki tek ve çok boyutlu dizileri destekler. Yukarıda listelenen türlerin aksine, kullanılmadan önce dizi türlerinin bildirilmesini gerekmez. Bunun yerine, dizi türleri Köşeli parantezlerle bir tür adı izleyerek oluşturulur. Örneğin, `int[]` tek boyutlu bir diziyse `int` , iki boyutlu bir dizidir ve tek boyutlu `int[,]` `int` `int[][]` dizi ya da "pürüzlü" dizisinin tek boyutlu bir dizisidir `int` .

Null yapılabilir türler ayrı bir tanım gerektirmez. Null yapılamayan her tür için, `T` ek bir değer içerebilen, buna karşılık gelen null yapılabilir bir tür vardır `T?` `null` . Örneğin, `int?` herhangi bir 32 bit tamsayı veya değeri tutabilecek bir türdür `null` ve `string?` herhangi birini veya değeri tutabilecek bir türüdür `string` `null` .

C# tür sistemi, herhangi bir türde bir değer olarak işlenemeyeceği şekilde birleştirilmiştir `object` . C# içindeki her tür doğrudan veya dolaylı olarak `object` sınıf türünden türetilir ve `object` tüm türlerin en son temel sınıfıdır. Başvuru türlerinin değerleri, yalnızca değerleri tür olarak görüntüleyerek nesne olarak değerlendirilir `object` . Değer türlerinin değerleri, *kutulama* ve *kutudan çıkarma işlemleri*gerçekleştirerek nesneler olarak değerlendirilir. Aşağıdaki örnekte, bir değeri öğesine `int` dönüştürülüp `object` öğesine yeniden döndürülür `int` .

:::code language="csharp" source="./snippets/shared/Program.cs" ID="boxing" :::

Bir başvuru için bir değer türü değeri atandığında `object` , değeri tutmak için bir "Box" tahsis edilir. Bu kutu bir başvuru türünün örneğidir ve değer bu kutuya kopyalanır. Buna karşılık, bir `object` Başvuru bir değer türüne yayınlandığınızda, başvurulan `object` öğesinin doğru değer türünün bir kutusu olduğunu belirten bir denetim yapılır. Denetim başarılı olursa, kutudaki değer değer türüne kopyalanır.

C# ' nin Birleşik tür sistemi etkin bir şekilde değer türlerinin `object` "istek üzerine" başvuru olarak işleneceği anlamına gelir. Birleşme nedeniyle, türü kullanılan genel amaçlı kitaplıklar, `object` `object` başvuru türleri ve değer türleri dahil, öğesinden türetilen tüm türlerle birlikte kullanılabilir.

C# ' de alanlar, dizi öğeleri, yerel değişkenler ve parametreler gibi çeşitli türlerde *değişkenler* vardır. Değişkenler, depolama konumlarını temsil eder. Her değişken, aşağıda gösterildiği gibi, değişkende hangi değerlerin depolanabileceğini belirleyen bir tür içerir.

- Null yapılamayan değer türü
  - Bu tam türden bir değer
- Null yapılabilir değer türü
  - `null`Bu tam türün değeri veya değeri
- object
  - `null`Başvuru, herhangi bir başvuru türünün nesnesine başvuru veya herhangi bir değer türünün paketlenmiş değerine başvuru
- Sınıf türü
  - `null`Başvuru, bu sınıf türünün bir örneğine başvuru veya bu sınıf türünden türetilmiş bir sınıfın örneğine başvuru
- Arabirim türü
  - `null`Başvuru, bu arabirim türünü uygulayan bir sınıf türü örneğine başvuru veya bu arabirim türünü uygulayan bir değer türünün paketlenmiş değerine başvuru
- Dizi türü
  - `null`Başvuru, bu dizi türü örneğine başvuru veya uyumlu bir dizi türü örneğine başvuru
- Temsilci türü
  - `null`Uyumlu bir temsilci türü örneğine başvuru veya başvuru

## <a name="program-structure"></a>Program yapısı

C# ' deki temel kurumsal kavramlar [***Programlar***](../programming-guide/inside-a-program/index.md), [***ad alanları***](../programming-guide/namespaces/index.md), [***türler***](../programming-guide/types/index.md), [***Üyeler***](../programming-guide/classes-and-structs/members.md)ve [***derlemelerdir***](../../standard/assembly/index.md). Programlar, üyeleri içeren ve ad alanları halinde düzenlenebilen türleri bildirir. Sınıflar, yapılar ve arabirimler tür örnekleridir. Alanlar, Yöntemler, Özellikler ve olaylar üye örnekleridir. C# programları derlendiğinde, fiziksel olarak derlemeler halinde paketlenir. Derlemeler, `.exe` `.dll` sırasıyla ***uygulama*** veya ***kitaplık***uygulanıp uygulamadığına bağlı olarak, genellikle dosya uzantısına sahiptir.

Küçük bir örnek olarak, aşağıdaki kodu içeren bir derlemeyi göz önünde bulundurun:

:::code language="csharp" source="./snippets/shared/AcmeStack.cs":::

Bu sınıfın tam adı `Acme.Collections.Stack` . Sınıf birçok üye içerir: adlı bir alan `top` , ve adlı iki yöntem `Push` `Pop` ve adlı bir iç içe sınıf `Entry` . `Entry`Sınıf daha fazla üç üye içerir: adlı alan `next` , adlı alan `data` ve Oluşturucu. , `Stack` *Genel* bir sınıftır. Bir tür parametresi vardır, `T` Bu, kullanıldığında somut bir türle değiştirilmiştir.

> [!NOTE]
> *Yığın* , "ilk son çıkar" (filo) koleksiyonudur. Yeni öğeler yığının üst kısmına eklenir. Bir öğe kaldırıldığında, yığının en üstünden kaldırılır.

Derlemeler, ara dil (IL) yönergeleri biçiminde çalıştırılabilir kodu ve meta veri biçimindeki sembolik bilgileri içerir. Yürütülmeden önce, .NET ortak dil çalışma zamanının tam zamanında (JıT) derleyicisi, bir derlemedeki Il kodunu işlemciye özel koda dönüştürür.

Bir derleme, hem kodu hem de meta verileri içeren işlevsellikten oluşan bir birim olduğundan, `#include` C# dilinde yönergeler ve başlık dosyaları gerekmez. Belirli bir derlemede yer alan ortak türler ve Üyeler, yalnızca program derlenirken bu derlemeye başvurarak bir C# programında kullanılabilir hale getirilir. Örneğin, bu program `Acme.Collections.Stack` derlemeden sınıfını kullanır `acme.dll` :

:::code language="csharp" source="./snippets/shared/StackUsage.cs":::

Bu programı derlemek için, önceki örnekte tanımlanan yığın sınıfını içeren derlemeye *başvurmanız* gerekir.

C# programları, çeşitli kaynak dosyalarında depolanabilir. Bir C# programı derlendiğinde, tüm kaynak dosyaları birlikte işlenir ve kaynak dosyalar birbirini serbestçe başvurabilir. Kavramsal olarak, tüm kaynak dosyaları işlenmeden önce bir büyük dosyada birleştirilmiş olur. Birkaç özel durum dışında, bildirim sırası çok önemli olduğundan, C# ' ta ileri bildirimlere hiçbir şekilde gerek yoktur. C#, kaynak dosyayı yalnızca bir ortak tür bildirmek üzere sınırlamaz veya kaynak dosyanın adının kaynak dosyada belirtilen bir türle eşleşmesi için gerekli değildir.

Bu turdaki diğer makalelere bu kuruluş blokları açıklanacaktır.

>[!div class="step-by-step"]
>[Sonraki](types.md)
