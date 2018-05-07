---
title: C# devralma
description: C# kitaplıkları ve uygulamalarda devralma kullanmayı öğrenin.
author: rpetrusha
ms.author: ronpet
ms.date: 08/16/2017
ms.assetid: aeb68c74-0ea0-406f-9fbe-2ce02d47ef31
ms.openlocfilehash: 1476425594e55531fdb56de531ee61808dccd7db
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="inheritance-in-c-and-net"></a>C# ve .NET devralma

Bu öğretici, C# ' nde Devralmanın tanıtır. Devralma (verileri ve davranış) belirli işlevleri sağlayan bir temel sınıf tanımlar ve devralmalı ya da bu işlevleri geçersiz kılma türetilmiş sınıfları tanımlamak için sağlayan bir nesne odaklı programlama dilleri özelliğidir.

## <a name="prerequisites"></a>Önkoşullar

Bu öğreticide, .NET Core yüklediğiniz varsayılır. Yükleme yönergeleri için bkz: [.NET Core Yükleme Kılavuzu'na](https://www.microsoft.com/net/core). Kod Düzenleyicisi de gerekir. Bu öğretici kullanır [Visual Studio Code](https://code.visualstudio.com), herhangi bir kod düzenleyiciyi kullanabilirsiniz ancak.

## <a name="running-the-examples"></a>Örnekleri çalıştırma

Oluşturmak ve Bu öğreticide örnekleri çalıştırmak için kullandığınız [dotnet](../../core/tools/dotnet.md) komut satırından yardımcı programı. Her örneği için şu adımları izleyin:

1. Örnek depolamak için bir dizin oluşturun.
1. Girin [dotnet yeni konsol](../../core/tools/dotnet-new.md) yeni bir .NET Core projesi oluşturmak için bir komut isteminde komutu.
1. Kopyalama ve örnek kod, kod düzenleyicisine yapıştırın.
1. Girin [dotnet geri yükleme](../../core/tools/dotnet-restore.md) yüklemek veya proje bağımlılıkları geri yüklemek için komut satırından komutu.

  [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

1. Girin [çalıştırmak dotnet](../../core/tools/dotnet-run.md) derlemek ve örnek çalıştırmak için komutu.


## <a name="background-what-is-inheritance"></a>Arka plan: Devralma nedir?

*Devralma* nesne odaklı programlama temel özniteliklerini biridir. Yeniden kullanır bir alt sınıfı tanımlamanıza olanak verir (devralır) genişletir ya da bir üst sınıf davranışını değiştirir. Üyeleri devralındığı sınıfı adlı *temel sınıfı*. Taban sınıfı üyeleri devralınan sınıflarda adlı *türetilmiş sınıf*.

C# ve .NET Destek *tek devralma* yalnızca. Diğer bir deyişle, bir sınıfın yalnızca tek bir sınıfı devralabilirsiniz. Ancak, devralma türleri kümesi için bir devralma hiyerarşisi tanımlamanıza olanak sağlayan geçişli olur. Diğer bir deyişle, yazın `D` türünden devralabilirsiniz `C`, türünden devralan `B`, taban sınıf türünden devralan `A`. Devralma geçişli olduğundan türün üyeleri `A` yazmak kullanılabilen `D`.

Bir taban sınıfın tüm üyeleri türetilmiş sınıflar tarafından devralınır. Aşağıdaki üyeleri devralınmaz:

- [Statik oluşturucular](../programming-guide/classes-and-structs/static-constructors.md), bir sınıfın statik verileri başlatılamıyor.

- [Örnek oluşturucuları](../programming-guide/classes-and-structs/constructors.md), hangi sınıfının yeni bir örneğini oluşturmak için çağırın. Her sınıf kendi oluşturucular tanımlamanız gerekir.

- [Sonlandırıcılar](../programming-guide/classes-and-structs/destructors.md), bir sınıfın örneklerini yok etmek için çalışma zamanındaki atık toplayıcısı tarafından çağrılır.

Tüm bir taban sınıfı üyeleri türetilmiş sınıflar tarafından devralınır olsa da, veya görünür olup olmadıklarına kendi erişilebilirliği bağlıdır. Bir üyenin erişilebilirlik görünürlüğü türetilen sınıflar için şu şekilde etkiler:

- [Özel](../language-reference/keywords/private.md) üyeleri yalnızca kendi taban sınıf içinde iç içe geçmiş türetilmiş sınıfları görünür. Aksi takdirde, bunlar türetilmiş sınıflarda görünür değildir. Aşağıdaki örnekte, `A.B` türetilen iç içe bir sınıf `A`, ve `C` türetilen `A`. Özel `A.value` alandır A.B. içinde görünür Ancak, açıklamalardan kaldırırsanız `C.GetValue` yöntemi ve örnek derleme girişimi derleyici hatası CS0122 oluşturur: "'A.value' kendi koruma düzeyi nedeniyle erişilemiyor."

  [!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/private.cs#1)]

- [Korumalı](../language-reference/keywords/protected.md) üyeleri yalnızca türetilmiş sınıflarda görünür.

- [İç](../language-reference/keywords/internal.md) üyeleridir temel sınıf olarak aynı bütünleştirilmiş kodda yer alan yalnızca türetilmiş sınıflarda görünür. Bunlar türetilmiş sınıflarda temel sınıfından farklı bir derlemede bulunan görünür değildir.

- [Ortak](../language-reference/keywords/public.md) üyeleri türetilmiş sınıflarda görünür ve türetilmiş sınıf ortak arabirimi bir parçasıdır. Yalnızca türetilmiş sınıfta tanımlanmadı sanki genel devralınan üyeler çağrılabilir. Aşağıdaki örnekte, sınıf `A` adlı bir yöntem tanımlar `Method1`ve sınıf `B` sınıfından devralan `A`. Bu örnek daha sonra çağırır `Method1` üzerinde örnek yöntemi gibi `B`.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/basics.cs#1)]

Türetilen sınıflar için de *geçersiz kılma* alternatif uygulaması sağlayarak devralınan üyeleri. Üye geçersiz kılma oluşturabilmek, temel sınıf üye ile işaretlenmelidir [sanal](../language-reference/keywords/virtual.md) anahtar sözcüğü. Varsayılan olarak, taban sınıfı üyeleri olarak işaretlenmemiş `virtual` ve değiştirilemiyor. Aşağıdaki örnekte olduğu gibi sanal olmayan üyesi geçersiz kılma girişiminde derleyici hatası CS0506 oluşturur: "<member> devralınan üye geçersiz kılamaz <member> sanal işaretlenmemiş çünkü soyut veya geçersiz kılamazsınız.

```csharp
public class A
{
    public void Method1()
    {
        // Do something.
    }
}

public class B : A
{
    public override void Method1() // Generates CS0506.
    {
        // Do something else.
    }
}
```

Bazı durumlarda, türetilmiş bir sınıf *gerekir* taban sınıfı uygulama geçersiz kılar. Taban sınıfı üyeleri ile işaretli [soyut](../language-reference/keywords/abstract.md) anahtar sözcüğü gerektiren türetilen sınıflar onları geçersiz kılar. Aşağıdaki örnek derleme çalışılıyor oluşturur derleyici hatası CS0534, "<class> devralınan özet üyesini uygulamıyor <member>', çünkü sınıfı `B` hiçbir uygulamasını sağlar `A.Method1`.

```csharp
public abstract class A
{
    public abstract void Method1();
}

public class B : A // Generates CS0534.
{
    public void Method3()
    {
        // Do something.
    }
}
```

Devralma yalnızca sınıfları ve arabirimleri için geçerlidir. Diğer tür kategorileri (yapılar, temsilciler ve numaralandırmaları) devralma desteklemez. Bu nedenle, aşağıdaki gibi kod derleme çalışılıyor derleyici hatası CS0527 oluşturur: "Arabirim listesindeki ' ValueType' türünde değil bir arabirim." Yapı uygulayan arabirimler tanımlayabilirsiniz rağmen devralma desteklenmiyor, hata iletisi gösterir.

```csharp
using System;

public struct ValueStructure : ValueType // Generates CS0527.
{
}
```

## <a name="implicit-inheritance"></a>Örtük devralma

Bunlar tek devralma yoluyla devralınmalıdır herhangi bir türünün yanı sıra, devralınmalıdır örtük olarak .NET tür sistemi içindeki tüm türler <xref:System.Object> veya ondan türetilmiş bir tür. Bu ortak işlevsellik için herhangi bir türü kullanılabilir olmasını sağlar.

Şimdi yeni bir sınıf tanımlama hangi örtük devralma gelir görmek için `SimpleClass`, yalnızca boş sınıf tanımı değil:

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass.cs#1)]

Biz sonra (sağlayan bize türü hakkında bilgi almak için bir tür meta verileri incelemek) yansıma kullanabilirsiniz ait üyelerin listesini almak için `SimpleClass` türü. Herhangi bir üye tanımlanan henüz rağmen bizim `SimpleClass` örnekten çıktı sınıfı gösterir gerçekte dokuz üye olduğunu. Bunlardan biridir için otomatik olarak sağlanan bir parametresiz (veya varsayılan) Oluşturucu `SimpleClass` C# Derleyici tarafından türü. Sekiz kalan üyeleri olan <xref:System.Object>, kendisinden tüm sınıflar ve arabirimler .NET içinde sistem sonuçta örtük olarak yazın devralır.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass.cs#2)]

Örtük devralmadan <xref:System.Object> sınıfı bu yöntemleri kullanılabilir kılar `SimpleClass` sınıfı:

- Ortak `ToString` dönüştürür yöntemi bir `SimpleClass` nesnesi tam olarak nitelenmiş tür adını kendi dize gösterimini döndürür. Bu durumda, `ToString` yöntemi "SimpleClass" dizesini döndürür.

- İki nesnenin eşitlik için test üç yöntem: ortak örnek `Equals(Object)` yöntemi, bir genel statik `Equals(Object, Object)` yöntemi ve ortak statik `ReferenceEquals(Object, Object)` yöntemi. Varsayılan olarak, bu yöntemleri referans eşitlik için test; diğer bir deyişle, eşit olacak şekilde iki nesne değişkenleri de aynı nesneye başvurması gerekir.

- Ortak `GetHashCode` karma koleksiyonlarda kullanılacak türünün bir örneği sağlayan bir değeri hesaplar yöntemi.

- Ortak `GetType` döndürür yöntemi bir <xref:System.Type> temsil eden nesnesi `SimpleClass` türü.

- Korumalı <xref:System.Object.Finalize%2A> nesnenin bellek çöp toplayıcı tarafından alınmadan önce yönetilmeyen kaynakları serbest bırakmak için tasarlanmış yöntemi.

- Korumalı <xref:System.Object.MemberwiseClone%2A> yöntemi geçerli nesne basit bir kopyasını oluşturur.

Örtük devralma nedeniyle biz devralınan bir üyeden çağırabilirsiniz bir `SimpleClass` gerçekten üyesi boşmuş gibi yalnızca nesne tanımlanan `SimpleClass` sınıfı. Örneğin, aşağıdaki örnek çağırır `SimpleClass.ToString` yöntemi, hangi `SimpleClass` devraldığı <xref:System.Object>.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass2.cs#1)]

Aşağıdaki tabloda, C# ' ta oluşturabilirsiniz türleri ve kendisinden bunlar örtük olarak devral türleri kategorilerini listeler. Her temel türü farklı bir üye kümesi için örtük olarak türetilmiş türler devralma yoluyla kullanılabilir hale getirir.

| Türü kategori | Örtük olarak devralır                                                      |
| ------------- | ----------------------------------------------------------------------------- |
| sınıf         | <xref:System.Object>                                                          |
| struct         | <xref:System.ValueType>, <xref:System.Object>                                 |
| enum          | <xref:System.Enum>, <xref:System.ValueType>, <xref:System.Object>             |
| temsilci      | <xref:System.MulticastDelegate>, <xref:System.Delegate>, <xref:System.Object> |

## <a name="inheritance-and-an-is-a-relationship"></a>Devralma ve bir "olan bir" ilişki

Normalde, devralma ifade etmek için kullanılan bir "olan bir" temel sınıf ve türetilen sınıflar temel sınıfın özel sürümleri olduğu bir veya daha fazla türetilmiş sınıflar arasındaki ilişki türetilen sınıfın temel sınıf türüdür. Örneğin, `Publication` sınıfı, herhangi bir türde bir yayın'ı temsil eder ve `Book` ve `Magazine` sınıfları belirli tür yayınlar temsil eder.

> [!NOTE]
> Sınıfta veya yapı bir daha fazla arabirim uygulayabilirsiniz. Arabirim uygulaması genellikle geçici bir çözüm için tek devralma veya devralma ile yapılar kullanmanın bir yolu olarak sunulan olsa da, bir arabirim ve uygulama türü daha arasında farklı bir ilişkiye ("yapabilirsiniz" ilişki) express için tasarlanmıştır Devralma. Bir arabirim arabirimi uygulayan türlerinden kullanılabilmesini (örneğin, özelliği nesnelere karşılaştırma veya sıralama eşitlik için test etmek için ya da kültüre duyarlı ayrıştırma ve biçimlendirme desteklemek için) işlevlerinin bir alt kümesini tanımlar.

Unutmayın "olan bir" de türünü ve belirli bir örnek oluşturma türü arasındaki ilişkiyi ifade eder. Aşağıdaki örnekte, `Automobile` üç benzersiz salt okunur özelliklere sahip bir sınıftır: `Make`, otomobil; üreticisi `Model`, otomobil; tür ve `Year`, kendi yılın üretim. Bizim `Automobile` sınıfı ayrıca olan bağımsız değişkenler için özellik değerlerine atanmış bir oluşturucuya sahip ve onu geçersiz kılmaları <xref:System.Object.ToString%2A?displayProperty=nameWithType> benzersiz olarak tanımlayan bir dize üretmek için yöntemi `Automobile` örneği yerine `Automobile` sınıfı.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/is-a.cs#1)]

Bu durumda, biz belirli araba marka ve model temsil devralma güvenmemelisiniz. Örneğin, tanımlamak ihtiyacımız olmayan bir `Packard` Packard Motor Car şirket tarafından üretilen otomobiller temsil eden tür. Bunun yerine, biz bunları oluşturarak temsil edebilen bir `Automobile` aşağıdaki örnekte olduğu gibi sınıfı oluşturucuya geçirilen uygun değerleri içeren nesne.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/is-a.cs#2)]

Devralmayı tabanlı bir olan bir ilişki en iyi bir taban sınıf ve türetilen için temel sınıf ek üye eklemek veya ek işlevsellik taban sınıf içinde mevcut değil gerektiren sınıfları uygulanır.

## <a name="designing-the-base-class-and-derived-classes"></a>Taban sınıf tasarlama ve türetilmiş sınıflar

Bir taban sınıf ve türetilmiş sınıflarının tasarlama işlemi bakalım. Bu bölümde, bir taban sınıf tanımlarız `Publication`, kitap, vb. bir dergi, bir gazete, bir günlük, bir makale herhangi bir türde bir yayın temsil eder. Biz de tanımlarsınız bir `Book` öğesinden türetilen sınıf `Publication`. Biz kolayca diğer türetilen sınıflar gibi tanımlamak için örnek genişletebilirsiniz `Magazine`, `Journal`, `Newspaper`, ve `Article`.

### <a name="the-base-publication-class"></a>Temel yayım sınıfı

Tasarlama, bizim `Publication` sınıfı, ihtiyacımız birkaç tasarım kararları almak:

- Bizim Bankası'ndaki eklenecek üyeleri `Publication` sınıfı olup `Publication` üyeleri yöntem uygulamalarını sağlayın veya `Publication` türetilmiş sınıflarının için bir şablon olarak hizmet veren bir Özet temel sınıf.

  Bu durumda, `Publication` sınıfı, yöntem uygulamalarını sağlayacaktır. [Soyut taban sınıfları ve bunların türetilmiş sınıfları tasarlama](#abstract) bölüm içeren bir Özet kullanan bir örnek türetilmiş sınıfları yöntemlerini tanımlamak için temel sınıf geçersiz kılması gerekir. Türetilen sınıflar türetilen tür uygun herhangi bir uygulama sağlamak boş.

  Kodunu (bildirim ve uygulamasını taban yöntemleri sınıfı ve bunları geçersiz kılma gerekmez diğer bir deyişle, birden çok türetilen sınıflar paylaşım) yeniden Özet olmayan taban sınıflar avantajı yeteneğidir. Bu nedenle, biz üyelerine eklemelisiniz `Publication` kendi kodu bazı tarafından paylaşılabilir veya özelleştirilmiş en büyük olasılıkla ise `Publication` türleri. Biz bunu verimli bir şekilde yapmak başarısız olursa, biz büyük ölçüde aynı üye türetilmiş sınıflarda temel sınıf yerine tek bir uygulama uygulamalarını gerek kalmadan elde edersiniz. Birden fazla konumda yinelenen kodunu korumak için gereken, hataların olası bir kaynaktır.

  En üst düzeye çıkarmak için her ikisini de yeniden kod ve mantıksal ve sezgisel devralma hiyerarşisi oluşturmak için eklediğimiz emin olmak istiyoruz `Publication` sınıf yalnızca veri ve tüm veya çoğu yayınlar için ortak işlevselliği. Türetilen sınıflar, ardından belirli temsil ettikleri yayın türleri için benzersiz üyelerini uygulayın.

- Şu ana kadar bizim sınıf hiyerarşisi genişletmek nasıl. Üç veya daha fazla sınıf yerine yalnızca bir temel sınıf ve bir veya daha fazla türetilmiş sınıflar hiyerarşisi geliştirmek istiyor musunuz? Örneğin, `Publication` temel bir sınıfında olabilir `Periodical`, sırayla olduğu temel bir sınıfında `Magazine`, `Journal` ve `Newspaper`.

  Bizim örneğimizde, basit hiyerarşisini kullanacağız bir `Publication` sınıfı ve tek bir türetilen sınıflar `Book`. Biz kolayca birkaç öğesinden türetilen ek sınıfları oluşturmak için örnek genişletebilirsiniz `Publication`, gibi `Magazine` ve `Article`.

- Olup temel sınıf örneği oluşturmak için mantıklıdır. Yoksa, biz uygulamalıdır [soyut](../language-reference/keywords/abstract.md) anahtar sözcüğü ile sınıfı. Girişiminde ile işaretli bir sınıf örneği oluşturmak için yapılması durumunda `abstract` anahtar sözcüğü sınıf oluşturucusu, C# Derleyici doğrudan çağrısıyla hatasına neden CS0144, "soyut sınıf veya arabirim bir örneğini oluşturamıyor." Yansıma, yansıma yöntemi atar kullanarak sınıfının örneği için bir girişimde varsa bir <xref:System.MemberAccessException>. Aksi takdirde, bizim `Publication` sınıfı, kendi sınıf oluşturucu çağırarak oluşturulabilir.

  Varsayılan olarak, bir taban sınıf, sınıf oluşturucu çağırarak oluşturulabilir. Biz açıkça bir sınıf oluşturucu tanımlamak sahip olmadığını unutmayın. Bir temel sınıf kaynak kodunda mevcut değilse, C# Derleyici (parametresiz) bir varsayılan oluşturucusu otomatik olarak sağlar.

  Bizim örneğimizde, biz işaretlemek `Publication` olarak sınıf [soyut](../language-reference/keywords/abstract.md) böylece örneği oluşturulamıyor.

- Türetilmiş sınıflar temel sınıf uygulamasını belirli üyeleri olup devralmalıdır veya temel sınıf uygulamasını geçersiz kılma seçeneği olup olmadığını. Biz kullanmak zorunda [sanal](../language-reference/keywords/virtual.md) anahtar sözcüğü bir temel sınıf yöntemi geçersiz kılmak türetilen sınıflar izin vermek için. Varsayılan olarak, taban sınıf içinde tanımlanan yöntemlerdir *değil* geçersiz kılınabilir.

- Türetilmiş sınıf devralma hiyerarşisinde son sınıfı temsil eder ve kendisi için ek türetilmiş sınıflar temel sınıf olarak kullanılamaz. Varsayılan olarak, herhangi bir sınıfın temel sınıf olarak hizmet verebilir. Biz uygulayabilirsiniz [korumalı](../language-reference/keywords/sealed.md) bir sınıf ek sınıfları için temel sınıf olarak sunulamıyor göstermek için anahtar sözcüğü. Bir korumalı sınıf oluşturulan derleyici hatası CS0509, çıkarmaya çalışırken "korumalı türünden türetilemez <typeName>".

  Bizim örneğimizde, biz bizim türetilmiş sınıf olarak işaretlemek `sealed`.

Aşağıdaki örnek için kaynak kodunu gösterir `Publication` sınıfı, yanı sıra bir `PublicationType` tarafından döndürülen numaralandırma `Publication.PublicationType` özelliği. Öğesinden devralınan üyeler yanı sıra <xref:System.Object>, `Publication` sınıfı aşağıdaki benzersiz üyeleri tanımlar ve üye geçersiz kılar:

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/base-and-derived.cs#1)]

- Bir Oluşturucu

  Çünkü `Publication` sınıf `abstract`, doğrudan aşağıdaki gibi kodundan örneği oluşturulamıyor:

  ```csharp
  var publication = new Publication("Tiddlywinks for Experts", "Fun and Games",
                                    PublicationType.Book);
  ```

  Ancak, örnek kurucusu türetilmiş sınıf oluşturucu doğrudan için kaynak kodunu olarak çağrılabilir `Book` sınıfı gösterir.

- İki yayın ilgili Özellikler

  `Title` salt okunur <xref:System.String> özelliği değeri, çağıran sağlanmaktadır `Publication` Oluşturucusu.

  `Pages` bir okuma-yazma <xref:System.Int32> kaç toplam yayın sayfaları gösterir özelliğine sahiptir. Değer adlı özel bir alanda depolanan `totalPages`. Pozitif bir sayı olmalıdır veya bir <xref:System.ArgumentOutOfRangeException> oluşturulur.

- Yayımcı ilgili üyeleri

  İki salt okunur özellikler `Publisher` ve `Type`. Değerlerin ilk olarak çağrısıyla sağlanan `Publication` sınıfı oluşturucusu.

- Yayımlama ile ilgili üyeleri

  İki yöntem `Publish` ve `GetPublicationDate`, ayarlayın ve yayın tarihi döndürür. `Publish` Yöntemi bir özel ayarlar `published` bayrağını `true` zaman olarak adlandırılır ve tarihi atadığında geçirilen kendisine özel bir bağımsız değişken olarak `datePublished` alan. `GetPublicationDate` Yöntemi durumunda "NYP" dizesini döndürür `published` bayrağı `false`, değerini `datePublished` , alan `true`.

- Telif Hakkı ilgili üyeleri

  `Copyright` Yöntemi telif hakkı sahibinin adını ve telif hakkı yılın bağımsız değişkenleri olarak alır ve bunlara atar `CopyrightName` ve `CopyrightDate` özellikleri.

- Geçersiz kılma `ToString` yöntemi

  Bir tür değil geçersiz kılarsanız <xref:System.Object.ToString%2A?displayProperty=nameWithType> yöntemi türü olan bir örneği başka bir ayrım içinde çok az kullanım tam adını döndürür. `Publication` Geçersiz kılmaları sınıf <xref:System.Object.ToString%2A?displayProperty=nameWithType> değerini döndürmek için `Title` özelliği.

Aşağıdaki şekilde bizim temel arasındaki ilişki gösterilmektedir `Publication` sınıfı ve onun örtük olarak devralınan <xref:System.Object> sınıfı.

![Nesne ve yayın sınıfları](media/publication-class.jpg)

### <a name="the-book-class"></a>`Book` Sınıfı

`Book` Sınıfı kitap yayın özel bir tür olarak temsil eder. Aşağıdaki örnek için kaynak kodunu gösterir `Book` sınıfı.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/base-and-derived.cs#2)]

Öğesinden devralınan üyeler yanı sıra `Publication`, `Book` sınıfı aşağıdaki benzersiz üyeleri tanımlar ve üye geçersiz kılar:

- İki Oluşturucusu

  İki `Book` oluşturucular üç ortak parametreler paylaşın. İki *başlık* ve *yayımcı*, parametreleri için karşılık gelen `Publication` Oluşturucusu. Üçüncü olan *Yazar*, özel depolanmış `authorName` alan. Bir oluşturucu içeren bir *ISBN* depolanan parametresi `ISBN` otomatik özelliği.

  İlk Oluşturucusu kullanan [bu](../language-reference/keywords/this.md) diğer oluşturucuyu çağırmak için anahtar sözcüğü. Oluşturucular tanımlamakta genel bir desen budur. Daha az parametreli oluşturucular en fazla sayıda parametre ile oluşturucu çağrılırken, varsayılan değerleri sağlayın.

  İkinci oluşturucu kullanan [temel](../language-reference/keywords/base.md) temel sınıf oluşturucu başlık ve yayımcı adını geçirmek için anahtar sözcüğü. Kaynak kodunuz bir temel sınıf oluşturucu için açık bir çağrı yapmazsanız, C# derleyici temel sınıf varsayılan veya parametresiz oluşturucu için bir çağrı otomatik olarak sağlar.

- Salt okunur `ISBN` döndürür özelliği `Book` nesnenin uluslararası standart kitap numarası, benzersiz 10 veya 13 basamaklı bir sayı. ISBN birine bağımsız değişken olarak sağlanan `Book` oluşturucular. ISBN derleyici tarafından otomatik olarak oluşturulan bir özel yedekleme alanını depolanır.

- Salt okunur `Author` özelliği. Yazar adı hem de bağımsız değişken olarak sağlanan `Book` oluşturucular ve özel depolanan `authorName` alan.

- İki salt okunur fiyat ile ilgili özellikler, `Price` ve `Currency`. Bağımsız değişken olarak değerlerine sağlanan bir `SetPrice` yöntem çağrısı. Fiyat özel bir alanda depolanan `bookPrice`. `Currency` Özelliği üç basamaklı ISO para birimi simgesini (örneğin, ABD Doları ABD Doları) ve özel depolanan `ISOCurrencySymbol` alan. ISO para birimi simgeleri alınabileceği <xref:System.Globalization.RegionInfo.ISOCurrencySymbol%2A> özelliği.

- A `SetPrice` değerlerini ayarlar yöntemi `bookPrice` ve `ISOCurrencySymbol` alanları. Bunlar tarafından döndürülen değerlerdir `Price` ve `Currency` özellikleri.

- Geçersiz kılmaları `ToString` yöntemi (devralınan `Publication`) ve <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> ve <xref:System.Object.GetHashCode%2A> yöntemleri (devralınan <xref:System.Object>).

  Bu geçersiz kılınmadığı sürece <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> yöntemi testleri başvuru eşitliği. Diğer bir deyişle, iki nesne değişkenlerini de aynı nesneye başvurduğundan eşit olduğu kabul edilir. Durumunda `Book` sınıfı, diğer yandan, iki `Book` nesneleri aynı ISBN varsa eşit olmalıdır.

  Kıldığınızda <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> yöntemi, ayrıca kılmanız gerekir <xref:System.Object.GetHashCode%2A> çalışma zamanı verimli alma için karma koleksiyonlarda öğeleri depolamak için kullandığı bir değer döndürür yöntemi. Karma kod eşitlik için test ile tutarlı olan bir değer döndürmelidir. Biz geçersiz olduğundan <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> döndürülecek `true` , iki ISBN özelliklerini `Book` nesneleri eşit olan, biz çağırarak hesaplanan karma kodu döndürür <xref:System.String.GetHashCode%2A> yöntemi tarafından döndürülen dize `ISBN` özelliği.

Aşağıdaki şekilde arasındaki ilişki gösterilmektedir `Book` sınıfı ve `Publication`, kendi temel sınıfı.

![Yayın ve kitap sınıfları](media/book-class.jpg)

Biz şimdi örneği bir `Book` nesnesi, her iki benzersiz ve devralınan üyeleri çağırma ve bağımsız değişken olarak türünde bir parametre bekler bir yönteme geçirin `Publication` veya türünde `Book`, aşağıdaki örnekte gösterildiği gibi.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/use-publication.cs#1)]

## <a name="designing-abstract-base-classes-and-their-derived-classes"></a>Soyut taban sınıfları ve bunların türetilmiş sınıfları tasarlama
<a name="abstract"></a>

Önceki örnekte, bir uygulama çeşitli yöntemler kod paylaşmak türetilen sınıflar izin vermek için sağlanan bir taban sınıf tanımlı. Çoğu durumda, ancak temel sınıfı bir uygulama sunmak amacıyla beklenmiyor. Bunun yerine, temel sınıfı olan bir *soyut sınıf*; her türetilmiş sınıf üyeleri tanımlayan bir şablon uygulamalıdır olarak görev yapar. Genellikle Özet temel sınıf söz konusu olduğunda, her türetilmiş bir tür için bu türü benzersiz uygulamasıdır.

Örneğin, her kapalı iki boyutlu geometrik şekil iki özellikleri içerir: alanı, iç ölçüde şeklin; ve çevre veya şekli kenarlarında uzaklığı. Bu özellikler, hesaplanan, yolu tamamen ancak, belirli şekline bağlıdır. Bir daire çevre (veya çevresini) hesaplama formülü Örneğin, çok, bir üçgen farklıdır.

Aşağıdaki örnek adlı Özet temel sınıf tanımlar `Shape` iki özelliklerini tanımlar: `Area` ve `Perimeter`. Sınıfı işaretlemeyi yanı sıra unutmayın [soyut](../language-reference/keywords/abstract.md) anahtar sözcüğü, her örnek üyesinin ayrıca ile işaretlenir [soyut](../language-reference/keywords/abstract.md) anahtar sözcüğü. Bu durumda, `Shape` ayrıca geçersiz kılar <xref:System.Object.ToString%2A?displayProperty=nameWithType> türünün adı yerine tam olarak nitelenmiş adını döndürmek için yöntem. Ve iki statik üyeleri tanımlayan `GetArea` ve `GetPerimeter`, alan ve çevre türetilmiş bir sınıf örneği kolayca almak arayanlara izin verin. Biz türetilmiş bir sınıf örneği bu yöntemlerden birini geçirdiğinizde, çalışma zamanı türetilmiş sınıf yöntemi geçersiz kılma çağırır.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#1)]

Biz sonra bazı sınıflardan türetilemeyeceğini `Shape` belirli şekiller temsil eder. Aşağıdaki örnek, üç sınıf tanımlar `Triangle`, `Rectangle`, ve `Circle`. Her alan ve çevre hesaplamak için bu belirli şekil için benzersiz bir formül kullanır. Türetilen sınıfların bazıları da özelliklerini gibi tanımlamak `Rectangle.Diagonal` ve `Circle.Diameter`, bunlar temsil eden şekli benzersiz olan.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#2)]

Aşağıdaki örnek, türetilen nesneler kullanır `Shape`. Türetilen nesnelerinin bir dizisi başlatır `Shape` ve statik yöntemlerini çağırır `Shape` return sarmalar sınıfı `Shape` özellik değerleri. Çalışma zamanı türetilmiş türlerde geçersiz kılınan özelliklerinden değerleri alan unutmayın. Bu örnek ayrıca her bıraktığı `Shape` dizi, türetilmiş bir tür olarak nesnesinde ve Dönüştürme başarılı olursa, o belirli bir alt sınıfı özelliklerini alır `Shape`. 

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#3)]

## <a name="see-also"></a>Ayrıca bkz.

[Sınıflar ve nesneler](../tour-of-csharp/classes-and-objects.md)   
[Devralma (C# programlama Kılavuzu)](../programming-guide/classes-and-structs/inheritance.md)
