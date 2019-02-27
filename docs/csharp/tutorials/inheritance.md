---
title: C# içinde devralma
description: C# kitaplıkları ve uygulamaları içinde devralma kullanmayı öğrenin.
author: rpetrusha
ms.author: ronpet
ms.date: 07/05/2018
ms.assetid: aeb68c74-0ea0-406f-9fbe-2ce02d47ef31
ms.openlocfilehash: 942950570253b73cfb9896117bd22189e56389ea
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2019
ms.locfileid: "56836649"
---
# <a name="inheritance-in-c-and-net"></a>C# ve .NET içinde devralma

Bu öğretici, C# içinde devralma tanıtır. Devralma (verilerini ve davranışlarını) belirli işlevleri sağlayan bir temel sınıf tanımlamak için ve devralınan veya bu işlevi geçersiz kılma türetilmiş sınıflar tanımlamanızı sağlayan bir nesne yönelimli programlama dillerinin özelliğidir.

## <a name="prerequisites"></a>Önkoşullar

Bu öğretici, .NET Core yüklediğinizi varsayar. Yükleme yönergeleri için bkz. [.NET Core Yükleme Kılavuzu](https://www.microsoft.com/net/core). Bir kod düzenleyicisi de gerekecektir. Bu öğreticide [Visual Studio Code](https://code.visualstudio.com), tercih ettiğiniz herhangi bir kod düzenleyicisi kullanabilirsiniz, ancak.

## <a name="running-the-examples"></a>Örnekleri çalıştırma

Oluşturmak ve Bu öğreticide örnekleri çalıştırmak için kullandığınız [dotnet](../../core/tools/dotnet.md) komut satırı yardımcı programı. Her örnek için aşağıdaki adımları izleyin:

1. Örnek depolamak için bir dizin oluşturun.
1. Girin [dotnet yeni konsol](../../core/tools/dotnet-new.md) yeni bir .NET Core projesi oluşturmak için bir komut isteminde komutu.
1. Kopyalamak ve örnek kod, kod düzenleyicisine yapıştırın.
1. Girin [dotnet restore](../../core/tools/dotnet-restore.md) yükleyin veya proje bağımlılıklarınızı geri yüklemek için komut satırından komutu.

  [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

1. Girin [çalıştırma dotnet](../../core/tools/dotnet-run.md) derlemek ve örnek çalıştırmak için komutu.

## <a name="background-what-is-inheritance"></a>Arka planı: Devralma nedir?

*Devralma* temel nesne yönelimli programlama özniteliklerini biridir. Yeniden kullanan bir alt sınıfını tanımlamak olanak tanır (devralınan) genişletir ya da bir üst sınıf davranışını değiştirir. Üyeleri devralınan sınıf *temel sınıfı*. Taban sınıfı üyeleri devralan sınıf *türetilmiş sınıf*.

C# ve .NET desteği *tek devralma* yalnızca. Diğer bir deyişle, bir sınıfın yalnızca tek bir sınıftan devralınabilir. Ancak, devralma, bir dizi türleri için devralma hiyerarşisi tanımlamanızı sağlayan geçişli değildir. Diğer bir deyişle, yazın `D` türden devralabilir `C`, türünden devralan `B`, taban sınıf türünden devralan `A`. Devralma geçişli olduğundan türün üyeleri `A` yazmak kullanılabilen `D`.

Bir taban sınıfın tüm üyeleri, türetilmiş sınıflar tarafından devralınır. Aşağıdaki üyeleri devralınmaz:

- [Statik oluşturucular](../programming-guide/classes-and-structs/static-constructors.md), bir sınıfın statik verileri başlatılamıyor.

- [Örnek oluşturucuları](../programming-guide/classes-and-structs/constructors.md), hangi sınıfının yeni bir örneğini oluşturmak için çağırın. Her sınıf kendi oluşturucular tanımlamanız gerekir.

- [Sonlandırıcılar](../programming-guide/classes-and-structs/destructors.md), bir sınıfın örneklerini yok etmek için çalışma zamanının atık toplayıcısı tarafından denir.

Tüm temel sınıf üyelerinin türetilmiş sınıflar tarafından devralınır ancak veya görünür olup olmadıklarından kendi erişilebilirliği bağlıdır. Bir üyenin erişilebilirlik görünürlüğü türetilmiş sınıflar için şu şekilde etkiler:

- [Özel](../language-reference/keywords/private.md) üyeleri yalnızca kendi taban sınıf içinde iç içe geçmiş türetilmiş sınıflarda görünür. Aksi takdirde, bunlar türetilmiş sınıflarda görünür değildir. Aşağıdaki örnekte, `A.B` türetildiği bir iç içe yerleştirilmiş sınıf `A`, ve `C` türetildiği `A`. Özel `A.value` alandır A.B. içinde görünür Ancak, açıklamalardan kaldırırsanız `C.GetValue` yöntemi ve örnek derleme girişimi derleyici hatası CS0122 üretir: "'A.value' koruma düzeyi nedeniyle erişilemez."

  [!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/private.cs#1)]

- [Korumalı](../language-reference/keywords/protected.md) üyeler türetilmiş sınıflarda da görünür.

- [İç](../language-reference/keywords/internal.md) üyeleridir temel sınıf olarak aynı derlemede bulunan türetilmiş sınıflarda görünür. Bunlar, türetilmiş sınıflarda temel sınıfından farklı bir derlemede bulunan görünür değildir.

- [Genel](../language-reference/keywords/public.md) üyeler türetilmiş sınıflarda görünür olduğundan ve türetilen sınıfın ortak arabiriminin bir parçasıdır. Genel devralınan üyeler türetilen sınıfta yalnızca tanımlandıkları alacağı çağrılabilir. Aşağıdaki örnekte, sınıf `A` adlı bir yöntem tanımlar `Method1`ve sınıfı `B` sınıfından devralan `A`. Örnek daha sonra çağırır `Method1` hakkında bir örnek yöntemi gibi `B`.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/basics.cs#1)]

Türetilen sınıfların aynı zamanda *geçersiz kılma* alternatif bir uygulama sağlayarak devralınan üyeleri. Üyesi geçersiz kılmak aktarabilmek için temel sınıf üye ile işaretlenmelidir [sanal](../language-reference/keywords/virtual.md) anahtar sözcüğü. Varsayılan olarak, temel sınıf üyeleri olarak işaretlenmemiş `virtual` ve geçersiz kılınamaz. Aşağıdaki örnekte olduğu gibi sanal olmayan bir üye geçersiz kılma girişiminde CS0506 derleyici hatası oluşturur: "<member> devralınmış üyesi geçersiz kılınamaz <member> sanal işaretlenmemiş çünkü, Özet veya geçersiz.

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

Bazı durumlarda, türetilmiş bir sınıf *gerekir* taban sınıf uygulamasını geçersiz kılın. Temel sınıf üyeleri ile işaretlenen [soyut](../language-reference/keywords/abstract.md) anahtar sözcüğü türetilmiş sınıfların bunları geçersiz kılma gerektirir. Derleyici Hatası CS0534, aşağıdaki örnek derleme çalışırken oluşturur "&lt;sınıfı&gt; devralınan soyut üyesini uygulamıyor &lt;üye&gt;", çünkü sınıfı `B` Hayır sağlar uygulama için `A.Method1`.

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

Devralma, yalnızca sınıflar ve arabirimler için geçerlidir. Diğer tür kategorileri (yapılar, temsilciler ve numaralandırmaları) devralımı desteklemez. Aşağıdaki örnek, derleyici hatası CS0527 üretir gibi Kodu derlemek bu kural nedeniyle çalışılıyor: "Arabirim listesindeki 'ValueType' türü bir arabirim değil." Bir yapının uyguladığı arabirimlerin tanımlayabilirsiniz, devralma desteklenmiyor, hata iletisi gösterir.

```csharp
using System;

public struct ValueStructure : ValueType // Generates CS0527.
{
}
```

## <a name="implicit-inheritance"></a>Örtük devralma

Tek devralma yoluyla devralındığı herhangi bir türü yanı sıra, devralınacak örtük olarak .NET tür sistemi tüm türlerin <xref:System.Object> veya ondan türetilmiş bir tür. Ortak işlevselliğini <xref:System.Object> herhangi bir türü için kullanılabilir.

Yeni bir sınıf tanımlayalım hangi örtük devralma anlamına görmek için `SimpleClass`, yalnızca boş sınıf tanımı olan:

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass.cs#1)]

(Bu, bu tür hakkında bilgi almak için bir türün meta verileri incelemenize olanak tanır) yansıma sonra kullanabileceğiniz ait üyelerinin bir listesini almak için `SimpleClass` türü. Tüm üyeleri tanımladıysanız olsa da, `SimpleClass` sınıfı örnekten çıkış, bu gerçekte dokuz üyeleri bulunduğunu belirtir. Bu üyeleri biri için otomatik olarak sağlanan parametresiz (veya varsayılan) bir oluşturucu `SimpleClass` C# derleyicisi tarafından türü. Sekiz kalan üyeleri <xref:System.Object>, kendisinden tüm sınıfları ve arabirimleri .NET içinde tür sistemi sonuçta örtük tür devralır.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass.cs#2)]

Örtük devralmadan <xref:System.Object> sınıfı kullanılabilir hale getirir bu yöntemler için `SimpleClass` sınıfı:

- Genel `ToString` dönüştüren yöntemi bir `SimpleClass` nesneyi dize gösterimine tam olarak nitelenmiş tür adını döndürür. Bu durumda, `ToString` yöntemi "SimpleClass" dize döndürür.

- İki nesne eşitliği test üç yöntem: ortak örnek `Equals(Object)` yöntemi, bir genel statik `Equals(Object, Object)` yöntemi ve bir genel statik `ReferenceEquals(Object, Object)` yöntemi. Varsayılan olarak, bu yöntemler için başvuru eşitliği testi; diğer bir deyişle, eşit olacak şekilde iki nesne değişkenini aynı nesneye başvurması gerekir.

- Genel `GetHashCode` karma koleksiyonları'nda kullanılmak üzere türün bir örneğini izin veren bir değeri hesaplar yöntemi.

- Genel `GetType` döndüren yöntemi bir <xref:System.Type> temsil eden nesne `SimpleClass` türü.

- Korumalı <xref:System.Object.Finalize%2A> yöntemi nesnenin bellek çöp toplayıcısı tarafından alınmadan önce yönetilmeyen kaynakları serbest bırakmak için tasarlanmıştır.

- Korumalı <xref:System.Object.MemberwiseClone%2A> yöntemi geçerli nesne basit bir kopyasını oluşturur.

Örtük devralma nedeniyle tüm devralınan üye çağırabilirsiniz bir `SimpleClass` nesne aslında bir üyesi ise gibi yalnızca tanımlanmış `SimpleClass` sınıfı. Örneğin, aşağıdaki örnekte çağırır `SimpleClass.ToString` yöntemi, hangi `SimpleClass` devraldığı <xref:System.Object>.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass2.cs#1)]

Aşağıdaki tablo, C# ' de oluşturabileceğiniz türleri ve bunların örtük olarak devraldığı türleri kategorilerini listeler. Her bir temel tür üyelerinin farklı bir dizi örtük olarak türetilmiş türlere de devralma kullanılabilir hale getirir.

| Türü kategorisi | Örtük olarak devraldığı                                                      |
| ------------- | ----------------------------------------------------------------------------- |
| sınıf         | <xref:System.Object>                                                          |
| struct         | <xref:System.ValueType>, <xref:System.Object>                                 |
| enum          | <xref:System.Enum>, <xref:System.ValueType>, <xref:System.Object>             |
| temsilci      | <xref:System.MulticastDelegate>, <xref:System.Delegate>, <xref:System.Object> |

## <a name="inheritance-and-an-is-a-relationship"></a>Devralma ve bir "olan bir" ilişkisi

Normalde, devralma ifade etmek için kullanılan bir "olan bir" türetilmiş sınıflar temel sınıf; özelleşmiş sürümleri olduğu bir veya daha fazla türetilmiş sınıflar temel sınıf arasındaki ilişki türetilen sınıfın temel sınıf türüdür. Örneğin, `Publication` sınıfı temsil eder, herhangi bir türdeki bir yayın ve `Book` ve `Magazine` sınıfları temsil eden belirli tür yayınlar.

> [!NOTE]
> Bir sınıfın veya yapının bir veya daha fazla arabirim uygulayabilir. Arabirim uygulaması genellikle geçici bir çözüm tek devralma için veya yapılar ile devralma kullanmanın bir yolu olarak sunulur, ancak express arasında bir arabirim ve uygulama türünden farklı bir ilişki ("yapılabilir" ilişkisi) için tasarlanmıştır Devralma. Arabirim uygulama türlerinden arabirimi kullanıma sunduğu (örneğin, karşılaştırma ya da sıralama nesnelere, eşitlik için sınama veya kültüre duyarlı ayrıştırma ve biçimlendirme desteği özelliği) işlevlerinin bir alt kümesini tanımlar.

Dikkat "olan bir" da bir tür ve belirli bir örneğini türü arasındaki ilişkiyi ifade eder. Aşağıdaki örnekte, `Automobile` üç benzersiz salt okunur özelliklere sahip bir sınıfı: `Make`, otomobil; üreticisi `Model`, otomobil; türünü ve `Year`, üretim, yıl. `Automobile` Sınıfı ayrıca bir oluşturucu bağımsız değişkenleri için özellik değerlerini atanan sahiptir ve onu geçersiz kılar <xref:System.Object.ToString%2A?displayProperty=nameWithType> benzersiz olarak tanımlayan bir dize oluşturmak için yöntemi `Automobile` örneği yerine `Automobile` sınıfı.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/is-a.cs#1)]

Bu durumda, belirli bir otomobil marka ve model temsil etmek için devralma güvenmemelisiniz. Örneğin, tanımlamanız gerekmez bir `Packard` Packard Motor Çinli araç şirketi tarafından üretilen otomobiller temsil eden tür. Bunun yerine, bunları oluşturarak temsil edebilen bir `Automobile` uygun değerlerle aşağıdaki örnekte olduğu gibi sınıf oluşturucusuna geçirilen nesne.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/is-a.cs#2)]

Devralma tabanlı bir olduğu bir ilişki en iyi bir temel sınıf ve türetilmiş sınıflar temel sınıf için ek üyeler eklemek veya ek işlevsellik mevcut değil temel sınıfta gerektiren uygulanır.

## <a name="designing-the-base-class-and-derived-classes"></a>Temel sınıf tasarlama ve türetilmiş sınıfları

Bir temel sınıf ve türetilmiş sınıflarının tasarlama işlemi göz atalım. Bu bölümde, bir temel sınıf tanımlarsınız `Publication`, bir kitap, vb. bir magazine, bir gazete, günlük, bir makalenin herhangi bir türde bir yayın temsil eder. Ayrıca tanımlarsınız bir `Book` türetilen sınıf `Publication`. Örnek, türetilen diğer sınıflar gibi tanımlamak için kolayca genişletebilirsiniz `Magazine`, `Journal`, `Newspaper`, ve `Article`.

### <a name="the-base-publication-class"></a>Temel yayım sınıfı

İçinde tasarlama, `Publication` sınıfı, gereken birkaç tasarım kararlarını alın:

- Hangi üyelerin tabanınızı içerecek şekilde `Publication` sınıfı ve `Publication` üyeler yöntem uygulamaları sağlamak veya `Publication` türetilmiş sınıfları için şablon görevi gören soyut bir temel sınıf.

  Bu durumda, `Publication` sınıf, yöntem uygulamaları sağlayacaktır. [Soyut temel sınıflar ve kendi türetilmiş sınıfları tasarlama](#abstract) bölümü içeren bir Özet kullanan bir örnek türetilmiş sınıfların yöntemleri tanımlamak için temel sınıf geçersiz kılması gerekir. Türetilen sınıflar türetilen tür için uygun olan herhangi bir uygulama sağlamak ücretsizdir.

  Kod (bildirimini ve uygulamasını tabanın sınıfı yöntemleri ve bunları geçersiz kılmak ihtiyaç duymayan diğer bir deyişle, birden çok türetilmiş sınıflar paylaşım) yeniden kullanabilme soyut olmayan temel sınıfların avantajlıdır. Bu nedenle, üye eklemek `Publication` kodlarını bazı tarafından paylaşılan veya özelleştirilmiş en olasılığı varsa `Publication` türleri. Temel sınıf uygulamalarını verimli bir şekilde sağlamak başarısız olursa, büyük ölçüde aynı üye uygulamalarının türetilmiş sınıflarda temel sınıf yerine tek bir uygulama sağlamak zorunda elde edersiniz. Birden fazla konumda yinelenen kod ortadan, hataların olası bir kaynaktır.

  En üst düzeye çıkarmak için hem de yeniden kod ve mantıksal ve sezgisel devralma hiyerarşisi oluşturmak için de eklediğinizden emin olmasını istediğiniz `Publication` sınıf yalnızca veri ve tüm veya çoğu yayınlar için ortak işlevselliği. Türetilen sınıflar, ardından belirli türlerini temsil ettikleri yayın için benzersiz olan üyeleri uygulayın.

- Şu ana kadar sınıf hiyerarşisi genişletmek nasıl. Üç veya daha fazla sınıf yerine yalnızca bir temel sınıf ve bir veya daha fazla türetilmiş sınıflar hiyerarşisi geliştirmek istiyor musunuz? Örneğin, `Publication` temel bir sınıfı olabilir `Periodical`, sırayla olduğu temel bir sınıfı `Magazine`, `Journal` ve `Newspaper`.

  Küçük hiyerarşisini kullanın, örneğin, bir `Publication` sınıf ve tek bir türetilen sınıf `Book`. Bir dizi öğesinden türetilen ek sınıfları oluşturmak için örnek kolayca genişletebilirsiniz `Publication`, gibi `Magazine` ve `Article`.

- Olup temel sınıfı örneğini oluşturmak için mantıklıdır. Kullanmıyorsa, uygulamalıdır [soyut](../language-reference/keywords/abstract.md) sınıfı anahtar sözcüğü. Aksi takdirde, `Publication` sınıf, sınıf oluşturucusu çağrılarak oluşturulabilir. Denemesi ile işaretlenmiş bir sınıf örneği oluşturmak için yapılması durumunda `abstract` anahtar sözcüğü C# derleyicisi kendi sınıf oluşturucusunda doğrudan çağrı tarafından hata CS0144, "soyut sınıfı veya arabiriminin örneği oluşturulamıyor." oluşturur Yansıma, yansıma yöntemi oluşturur kullanarak sınıf örneği denemesi yapılırsa bir <xref:System.MemberAccessException>.

  Varsayılan olarak, kendi sınıf oluşturucusunu çağırarak bir temel sınıf oluşturulabilir. Bir sınıf oluşturucu açıkça tanımlamak zorunda değildir. Bir temel sınıf kaynak kodunda mevcut değilse, C# derleyici varsayılan (parametresiz) Oluşturucu otomatik olarak sağlar.

  İşaretleme, örneğin `Publication` olarak sınıf [soyut](../language-reference/keywords/abstract.md) böylece örneği oluşturulamıyor.  Bir `abstract` sınıf olmayan `abstract` metodu bu sınıfın birkaç somut sınıflar arasında paylaşılan bir soyut kavramını temsil ettiğini belirtir (gibi bir `Book`, `Journal`).

- Türetilmiş sınıflar temel sınıf uygulamasına belirli üyeleri olup devralmalıdır, temel sınıf uygulamasına geçersiz kılma seçeneği olup olmamasına veya bunlar uygulaması sağlamanız gerekir. Kullandığınız [soyut](../language-reference/keywords/abstract.md) türetilen sınıflar, bir uygulama sunmak amacıyla zorlamak için anahtar sözcüğü. Kullandığınız [sanal](../language-reference/keywords/virtual.md) anahtar sözcüğü türetilmiş sınıflar temel sınıf yöntemini geçersiz kılmak izin vermek için. Varsayılan olarak, temel sınıfta tanımlanan yöntemlerdir *değil* geçersiz kılınabilir.

 `Publication` Sınıfı herhangi yok `abstract` yöntemleri ama sınıfın kendisi `abstract`.

- Bir türetilmiş sınıf devralma hiyerarşisinde son sınıfı temsil eder ve kendisi için ek türetilmiş sınıflar temel sınıf olarak kullanılamaz. Varsayılan olarak, herhangi bir sınıfın temel sınıf olarak hizmet verebilir. Uygulayabileceğiniz [korumalı](../language-reference/keywords/sealed.md) anahtar sözcüğü bir sınıf ek sınıfları için temel sınıf olarak hizmet veremez belirtmek için. Bir korumalı sınıf oluşturulan derleyici hatası CS0509, türetilen çalışılırken "sealed türünden türetilemez <typeName>".

  Türetilmiş sınıfınızın olarak işaretlemek, örneğin `sealed`.

Aşağıdaki örnek, kaynak kodunu gösterir `Publication` sınıfı, hem de bir `PublicationType` tarafından döndürülen sabit listesi `Publication.PublicationType` özelliği. Öğesinden devralınan üyeleri yanı sıra <xref:System.Object>, `Publication` sınıfı aşağıdaki benzersiz üyeleri tanımlar ve üyeyi geçersiz kılar:

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/base-and-derived.cs#1)]

- Bir Oluşturucu

  Çünkü `Publication` sınıfı `abstract`, aşağıdaki örnekte olduğu gibi doğrudan koddan başlatılamaz:

  ```csharp
  var publication = new Publication("Tiddlywinks for Experts", "Fun and Games",
                                    PublicationType.Book);
  ```

  Ancak, kendi örnek oluşturucusu doğrudan türetilmiş sınıf Oluşturucular, için kaynak kodu olarak çağrılabilir `Book` sınıfı gösterir.

- İki yayın ilgili Özellikler

  `Title` salt okunur <xref:System.String> özellik değeri, çağırarak sağlanmaktadır `Publication` Oluşturucusu.

  `Pages` bir okuma-yazma <xref:System.Int32> yayının kaç toplam sayfa gösteren bir özelliğe sahiptir. Değer adlı özel bir alanda depolandığını `totalPages`. Pozitif bir sayı olmalıdır veya bir <xref:System.ArgumentOutOfRangeException> oluşturulur.

- Yayımcı ilgili üyeleri

  İki salt okunur özellikler `Publisher` ve `Type`. Değerlerin ilk çağrı tarafından sağlanan `Publication` sınıf oluşturucusu.

- Yayımlama ile ilgili üyeleri

  İki yöntem `Publish` ve `GetPublicationDate`ayarlayabilir ve yayın tarihi döndürür. `Publish` Yöntemi bir özel ayarlar `published` bayrak `true` ne zaman çağrılır ve tarih atar geçirilen kendisine özel bir bağımsız değişken olarak `datePublished` alan. `GetPublicationDate` Yöntemi döndürür "NYP" dizesi, `published` bayrağı `false`, değeri `datePublished` ise alan `true`.

- Telif Hakkı ilgili üyeleri

  `Copyright` Yöntemi telif hakkı sahibinin adını ve telif hakkı yılın bağımsız değişkenleri olarak alır ve bunlara atar `CopyrightName` ve `CopyrightDate` özellikleri.

- Geçersiz kılma `ToString` yöntemi

  Bir tür değil kılarsanız <xref:System.Object.ToString%2A?displayProperty=nameWithType> yöntemi, başka bir örneği farklılaştırılması az kullanımda olan türü, tam olarak nitelenmiş adını döndürür. `Publication` Sınıf geçersiz kılmalarını <xref:System.Object.ToString%2A?displayProperty=nameWithType> değerini döndürmek için `Title` özelliği.

Aşağıdaki şekilde tabanınızı arasındaki ilişki gösterilmektedir `Publication` sınıf ve onun örtük olarak devralınan <xref:System.Object> sınıfı.

![Nesne ve yayın sınıfları](media/publication-class.jpg)

### <a name="the-book-class"></a>`Book` Sınıfı

`Book` Sınıfı bir kitap Yayını uzmanlaşmış bir türü temsil eder. Aşağıdaki örnek, kaynak kodunu gösterir `Book` sınıfı.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/base-and-derived.cs#2)]

Öğesinden devralınan üyeleri yanı sıra `Publication`, `Book` sınıfı aşağıdaki benzersiz üyeleri tanımlar ve üyeyi geçersiz kılar:

- İki Oluşturucu

  İki `Book` oluşturucular üç ortak parametreleri paylaşın. İki *başlık* ve *yayımcı*, parametreleri için karşılık gelen `Publication` Oluşturucusu. Üçüncü olan *Yazar*, değişmez bir genel depolanan `Author` özelliği. Bir oluşturucu içeren bir *ISBN* depolanan parametre `ISBN` otomatik-özellik.

  İlk Oluşturucu kullanan [bu](../language-reference/keywords/this.md) diğer oluşturucuyu çağırmak için anahtar sözcüğü. Oluşturucu zincirleme oluşturucuları tanımlama ortak bir desendir. En fazla sayıda parametre ile Oluşturucusu çağrılırken, daha az parametre oluşturucularla varsayılan değerleri sağlar.

  İkinci oluşturucu kullanan [temel](../language-reference/keywords/base.md) başlık ve yayımcı adı temel sınıf oluşturucusuna geçirilecek anahtar sözcüğü. Kaynak kodunuzda bir temel sınıf oluşturucusu için açık çağrı yapmazsanız, C# Derleyici taban sınıf varsayılan veya parametresiz oluşturucu çağrısı otomatik olarak sağlar.

- Salt okunur `ISBN` döndüren özellik `Book` nesnenin uluslararası standart kitap numarası, benzersiz 10 veya 13 basamaklı bir sayı. ISBN birine bağımsız değişken olarak sağlanan `Book` oluşturucular. Derleyici tarafından otomatik olarak oluşturulan bir özel yedekleme alanını ISBN depolanır.

- Salt okunur `Author` özelliği. Yazar adı her iki bağımsız değişken olarak sağlanan `Book` oluşturucular ve özelliğinde depolanır.

- İki salt okunur fiyat güvenlikle ilgili Özellikler `Price` ve `Currency`. Değerleri, bağımsız değişken olarak sağlanan bir `SetPrice` yöntem çağrısı. `Currency` Üç basamaklı ISO para birimi simgesi (örneğin, try ABD Doları) bir özelliktir. ISO para birimi simgeleri alınabileceği <xref:System.Globalization.RegionInfo.ISOCurrencySymbol%2A> özelliği. Bu özelliklerin her ikisi de dışarıdan salt okunurdur, ancak her ikisi de, kod tarafından ayarlanabilir `Book` sınıfı.

- A `SetPrice` değerlerini ayarlar yönteminin `Price` ve `Currency` özellikleri. Bu değerler aynı özelliklere göre döndürülür.

- Geçersiz kılmaları `ToString` yöntemi (devralınan `Publication`) ve <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> ve <xref:System.Object.GetHashCode%2A> yöntemleri (devralınan <xref:System.Object>).

  Geçersiz kılınmadığı sürece <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> yöntemi başvuru eşitliği sınar. Diğer bir deyişle, iki nesne değişkenleri, aynı nesneye başvuruyorsa eşit olarak değerlendirilir. İçinde `Book` sınıfının, diğer taraftan, iki `Book` nesneleri aynı ISBN oluşturulduysa eşit olmalıdır.

  Ne zaman geçersiz kılmanız <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> yöntemi de kılmanız gerekir <xref:System.Object.GetHashCode%2A> yöntemi, çalışma öğeleri verimli alma için karma koleksiyonları depolamak için kullandığı bir değer döndürür. Karma kod eşitliği testi ile tutarlı olan bir değer döndürmesi gerekir. Geçersiz olduğundan <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> döndürülecek `true` varsa iki ISBN özelliklerini `Book` nesneler, çağırarak hesaplanan karma kodu döndürmesi <xref:System.String.GetHashCode%2A> yöntemi tarafından döndürülen dizenin `ISBN` özelliği.

Aşağıdaki şekilde arasındaki ilişki gösterilmektedir `Book` sınıfı ve `Publication`, kendi temel sınıfı.

![Yayın ve kitap sınıfları](media/book-class.jpg)

Artık oluşturabileceğiniz bir `Book` nesnesi, her iki benzersiz ve devralınan üyeleri çağırmak ve türünde bir parametre bekliyor. bir yönteme bağımsız değişken olarak geçirmek `Publication` veya türü `Book`aşağıdaki örnekte gösterildiği gibi.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/use-publication.cs#1)]

## <a name="designing-abstract-base-classes-and-their-derived-classes"></a>Soyut temel sınıflar ve kendi türetilmiş sınıfları tasarlama
<a name="abstract"></a>

Önceki örnekte, bir uygulama bir dizi kodu paylaşmak türetilmiş sınıfları izin vermek için yöntem için sağlanan bir temel sınıf tanımlı. Çoğu durumda, ancak temel sınıfta bir uygulama sunmak amacıyla beklenmiyor. Bunun yerine, temel sınıfı olan bir *soyut sınıf* bildiren *soyut yöntemler*; her türetilmiş sınıf üyeleri tanımlayan bir şablon uygulamalıdır olarak görev yapar. Genellikle bir soyut temel sınıf, türetilen her tür bu türe benzersiz uygulamasıdır. Bu örneği oluşturmak için hiçbir mantıklı bir seçimdi çünkü sınıfı soyut anahtar sözcüğü ile işaretlenmiş bir `Publication` sınıfı yayınlar için ortak işlevselliği uygulamaları sağlamadı olsa da, nesne.

Örneğin, kapatılan her iki boyutlu geometrik şekil iki özellik içerir: alan, Şekil; iç kapsamı ve çevre veya şekil kenarlarında uzaklık. Şekilde, bu özellikleri hesaplanır, ancak tamamen belirli şekline bağlıdır. Örneğin, bir daire çevre (veya çevresini) hesaplama formülü bu üçgen farklılık gösterir. `Shape` Sınıfı bir `abstract` sınıfıyla `abstract` yöntemleri. Türetilen sınıfların aynı işlevselliği paylaşır, ancak bu türetilen sınıfların bu işlevselliği desteklememesinden gösterir.

Aşağıdaki örnek adlı bir soyut temel sınıf tanımlar `Shape` iki özellikleri tanımlayan: `Area` ve `Perimeter`. Sınıf ile işaretlemeyi yanı sıra [soyut](../language-reference/keywords/abstract.md) anahtar sözcüğü, her örnek üyesi de ile işaretlenmiş [soyut](../language-reference/keywords/abstract.md) anahtar sözcüğü. Bu durumda, `Shape` de geçersiz kılmalar <xref:System.Object.ToString%2A?displayProperty=nameWithType> türünün adı yerine tam olarak nitelenmiş adını döndürmek için yöntemi. İki statik üyeleri tanımlar `GetArea` ve `GetPerimeter`, alan ve türetilmiş bir sınıf örneği çevre kolayca almak çağıranlar izin. Çalışma zamanı, bu yöntemlerden birini türetilmiş bir sınıf örneğini geçirdiğinizde, türetilmiş sınıf yöntemini geçersiz kılma çağırır.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#1)]

Bazı sınıflardan sonra türetebilirsiniz `Shape` belirli şekiller temsil eder. Aşağıdaki örnek, üç sınıfları tanımlar `Triangle`, `Rectangle`, ve `Circle`. Her alan ve çevre hesaplamak için belirli bir şekil için benzersiz bir formül kullanır. Türetilen sınıfların bazıları da özellikleri gibi tanımlamanız `Rectangle.Diagonal` ve `Circle.Diameter`, bunlar temsil eden şekle benzersiz olan.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#2)]

Aşağıdaki örnek, türetilen nesneler kullanır `Shape`. Bir dizi öğesinden türetilen nesnelerin örneğini oluşturduğunda `Shape` ve statik yöntemlerini çağırır `Shape` dönüş sarmalar sınıfı `Shape` özellik değerleri. Çalışma zamanı, türetilen türlerin geçersiz kılınan özelliklerinden değerlerini alır. Örnekte ayrıca her bıraktığı `Shape` kendi türetilmiş bir tür için bir dizi nesnesinde ve atama işlemi başarılı olursa, o belirli öğesinin özelliklerini alır `Shape`. 

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#3)]

## <a name="see-also"></a>Ayrıca bkz.

- [Sınıflar ve nesneler](../tour-of-csharp/classes-and-objects.md)
- [Devralma (C# programlama Kılavuzu)](../programming-guide/classes-and-structs/inheritance.md)
