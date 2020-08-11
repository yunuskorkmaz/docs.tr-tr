---
title: "C 'de devralma #"
description: C# kitaplıkları ve uygulamalarında devralmayı kullanmayı öğrenin.
ms.date: 07/05/2018
ms.technology: csharp-fundamentals
ms.assetid: aeb68c74-0ea0-406f-9fbe-2ce02d47ef31
ms.openlocfilehash: 70db8716bea84984ad56d79fa9e26aab3a8182fa
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063516"
---
# <a name="inheritance-in-c-and-net"></a>C# ve .NET içinde devralma

Bu öğretici, C# dilinde devralma işlemini tanıtır. Devralma, belirli işlevleri (veri ve davranış) sağlayan bir temel sınıf tanımlamanızı ve bu işlevi devralıp geçersiz kılan türetilmiş sınıfları tanımlamanızı sağlayan nesne odaklı programlama dillerinin bir özelliğidir.

## <a name="prerequisites"></a>Önkoşullar

Bu öğreticide .NET Core SDK yüklediğinizi varsayılmaktadır. [.NET Core İndirmeleri](https://dotnet.microsoft.com/download) sayfasını ziyaret ederek indirin. Ayrıca bir kod düzenleyicisine ihtiyacınız vardır. Bu öğretici [Visual Studio Code](https://code.visualstudio.com)kullanır, ancak istediğiniz herhangi bir kod düzenleyicisini kullanabilirsiniz.

## <a name="running-the-examples"></a>Örnekleri çalıştırma

Bu öğreticide örnekleri oluşturmak ve çalıştırmak için, komut satırından [DotNet](../../core/tools/dotnet.md) yardımcı programını kullanın. Her örnek için aşağıdaki adımları izleyin:

1. Örneği depolamak için bir dizin oluşturun.
1. Yeni bir .NET Core projesi oluşturmak için bir komut isteminde [DotNet yeni konsol](../../core/tools/dotnet-new.md) komutunu girin.
1. Kod düzenleyicinize örnekteki kodu kopyalayın ve yapıştırın.
1. Projenin bağımlılıklarını yüklemek veya geri yüklemek için komut satırından [DotNet restore](../../core/tools/dotnet-restore.md) komutunu girin.

   [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

1. Örneği derlemek ve yürütmek için [DotNet Run](../../core/tools/dotnet-run.md) komutunu girin.

## <a name="background-what-is-inheritance"></a>Arka plan: devralma nedir?

*Devralma* , nesne odaklı programlamanın temel özniteliklerinden biridir. Bir üst sınıfın davranışını yeniden kullanan (devralan), genişleten veya değiştiren bir alt sınıf tanımlamanızı sağlar. Üyelerine devralınan sınıfa *temel sınıf*denir. Taban sınıfının üyelerini devralan sınıf *türetilmiş sınıf*olarak adlandırılır.

C# ve .NET yalnızca *tek devralmayı* destekler. Diğer bir deyişle, bir sınıf yalnızca tek bir sınıftan devralınabilir. Ancak, devralma geçişlidir ve bu, bir tür kümesi için devralma hiyerarşisi tanımlamanızı sağlar. Diğer bir deyişle, türü, `D` `C` `B` temel sınıf türünden devralan türünden devralan türünden devralabilir `A` . Devralma geçişli olduğundan, türü üyeleri `A` türü için kullanılabilir `D` .

Bir taban sınıfın tüm üyeleri türetilmiş sınıflar tarafından devralınmaz. Aşağıdaki Üyeler devralınmaz:

- Statik [oluşturucular](../programming-guide/classes-and-structs/static-constructors.md), bir sınıfın statik verilerini başlatır.

- Sınıfının yeni bir örneğini oluşturmak için çağırdığınız [örnek oluşturucular](../programming-guide/classes-and-structs/constructors.md). Her sınıfın kendi oluşturucuları tanımlanmalıdır.

- Çalışma zamanının atık toplayıcısı tarafından bir sınıfın örneklerini yok etmek için çağrılan [sonlandırıcılar](../programming-guide/classes-and-structs/destructors.md).

Bir temel sınıfın diğer tüm üyeleri türetilmiş sınıflar tarafından devralınırken, görünür olup olmadığı ve erişilebilirliğine bağlı olup olmadığı. Üyenin erişilebilirliği, türetilmiş sınıfların görünürlüğünü aşağıdaki gibi etkiler:

- [Özel](../language-reference/keywords/private.md) Üyeler yalnızca kendi temel sınıfında iç içe yerleştirilmiş türetilmiş sınıflarda görünür. Aksi takdirde, bunlar türetilmiş sınıflarda görünür değildir. Aşağıdaki örnekte, `A.B` öğesinden türetilen `A` ve türeten türetilmiş bir iç içe sınıftır `C` `A` . Özel `A.value` alan A.B. içinde görünür Ancak, yöntemden açıklamaları kaldırır `C.GetValue` ve örneği derlemeye çalışırsanız, CS0122 derleyici hatası üretir: "' A. Value ', koruma düzeyi nedeniyle erişilemez."

  [!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/private.cs#1)]

- [Korunan](../language-reference/keywords/protected.md) Üyeler yalnızca türetilmiş sınıflarda görülebilir.

- [İç](../language-reference/keywords/internal.md) Üyeler yalnızca temel sınıfla aynı derlemede bulunan türetilmiş sınıflarda görülebilir. Bunlar, temel sınıftan farklı bir derlemede bulunan türetilmiş sınıflarda görünür değildir.

- [Ortak](../language-reference/keywords/public.md) Üyeler türetilmiş sınıflarda görünür ve türetilmiş sınıf ' genel arabiriminin bir parçasıdır. Ortak devralınmış Üyeler, türetilmiş sınıfta tanımlandıklarında olduğu gibi çağrılabilir. Aşağıdaki örnekte, sınıfı `A` adlı bir yöntemi tanımlar ve sınıf sınıfından `Method1` `B` devralır `A` . Örnek daha sonra `Method1` ' de bir örnek yöntemi gibi çağırır `B` .

  [!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/basics.cs#1)]

Türetilmiş sınıflar, alternatif bir uygulama sağlayarak devralınan üyeleri de *geçersiz kılabilir* . Bir üyeyi geçersiz kılabilmek için, temel sınıftaki üyenin [sanal](../language-reference/keywords/virtual.md) anahtar sözcüğüyle işaretlenmesi gerekir. Varsayılan olarak, temel sınıf üyeleri olarak işaretlenir `virtual` ve geçersiz kılınamaz. Aşağıdaki örnekte olduğu gibi sanal olmayan bir üyeyi geçersiz kılma girişimi, CS0506: " \<member> \<member> sanal, Özet veya geçersiz kılma olarak işaretlenmediğinden devralınan üye geçersiz kılınamaz.

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

Bazı durumlarda, türetilmiş bir sınıf temel sınıf uygulamasını geçersiz *kılmalıdır* . [Soyut](../language-reference/keywords/abstract.md) anahtar sözcükle işaretlenmiş temel sınıf üyeleri, türetilmiş sınıfların bunları geçersiz kılmasını gerektirir. Aşağıdaki örnek derlenmeye çalışıldığında derleyici hatası CS0534, " &lt; sınıf &gt; devralınmış soyut üye &lt; üyesini uygulamıyor", &gt; çünkü sınıf `B` için uygulama sağlamaz `A.Method1` .

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

Devralma yalnızca sınıflar ve arabirimler için geçerlidir. Diğer tür kategorileri (yapılar, temsilciler ve numaralandırmalar) devralmayı desteklemez. Bu kurallar nedeniyle, aşağıdaki örnek gibi kodu derlemeye çalışmak derleyici hatası oluşturur CS0527: "tür ' ValueType ', arabirim listesinde bir arabirim değil." Hata iletisi, bir yapının uyguladığı arabirimleri tanımlayabilseniz de devralmanın desteklenmediğini belirtir.

```csharp
using System;

public struct ValueStructure : ValueType // Generates CS0527.
{
}
```

## <a name="implicit-inheritance"></a>Örtük devralma

Tek devralmayla devraldıkları türlerin yanı sıra, .NET tür sistemi 'ndeki tüm türler örtülü olarak <xref:System.Object> devralınır veya ondan türetilmiş bir tür. Ortak işlevselliği <xref:System.Object> her türlü tür için kullanılabilir.

Örtük devralmanın ne anlama geldiğini görmek için, `SimpleClass` yalnızca boş bir sınıf tanımı olan yeni bir sınıf tanımlayalim:

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass.cs#1)]

Daha sonra, türe ait üyelerin bir listesini almak için yansıma (Bu tür hakkında bilgi almak üzere bir türün meta verilerini incelemenizi sağlar) kullanabilirsiniz `SimpleClass` . Sınıfınızda herhangi bir üye tanımlamadıysanız `SimpleClass` , örnekteki çıkış gerçekten dokuz üyeye sahip olduğunu gösterir. Bu üyelerden biri, `SimpleClass` C# derleyicisi tarafından tür için otomatik olarak sağlanan parametresiz (veya varsayılan) bir oluşturucudur. Kalan sekiz, <xref:System.Object> .net tür sistemindeki tüm sınıfların ve arabirimlerin sonunda dolaylı olarak devraldığı tür üyesidir.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass.cs#2)]

Sınıfından örtük devralma, <xref:System.Object> Bu yöntemleri sınıfı için kullanılabilir hale getirir `SimpleClass` :

- `ToString`Bir nesneyi dize gösterimine dönüştüren public yöntemi `SimpleClass` , tam nitelikli tür adını döndürür. Bu durumda, `ToString` yöntemi "SimpleClass" dizesini döndürür.

- İki nesnenin eşitlik için test eden üç yöntem: ortak örnek `Equals(Object)` yöntemi, ortak statik `Equals(Object, Object)` Yöntem ve genel statik `ReferenceEquals(Object, Object)` Yöntem. Varsayılan olarak, bu yöntemler başvuru eşitliği için test; diğer bir deyişle, eşit olması için iki nesne değişkeninin aynı nesneye başvurması gerekir.

- `GetHashCode`Karma koleksiyonlarda kullanılacak tür örneğine izin veren bir değeri hesaplayan ortak yöntemi.

- `GetType` <xref:System.Type> Türü temsil eden bir nesne döndüren public yöntemi `SimpleClass` .

- <xref:System.Object.Finalize%2A>Bir nesnenin belleğinden önce yönetilmeyen kaynakları serbest bırakmak için tasarlanan Protected yöntemi çöp toplayıcı tarafından geri kazanılır.

- <xref:System.Object.MemberwiseClone%2A>Geçerli nesnesinin basit bir kopyasını oluşturan Protected yöntemi.

Örtük devralma nedeniyle, bir nesneden devralınan herhangi bir üyeyi, `SimpleClass` aslında yalnızca sınıfında tanımlanmış bir üye gibi çağırabilirsiniz `SimpleClass` . Örneğin, aşağıdaki örnek `SimpleClass.ToString` `SimpleClass` öğesinden devralan yöntemini çağırır <xref:System.Object> .

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass2.cs#1)]

Aşağıdaki tabloda, C# ' de oluşturabileceğiniz türlerin ve örtülü olarak devraldığı türlerin kategorileri listelenmektedir. Her temel tür, devralma yoluyla örtülü olarak türetilmiş türlere farklı bir üye kümesi sağlar.

| Tür kategorisi | Örtülü olarak devralır                                                      |
| ------------- | ----------------------------------------------------------------------------- |
| sınıf         | <xref:System.Object>                                                          |
| struct        | <xref:System.ValueType>, <xref:System.Object>                                 |
| enum          | <xref:System.Enum>, <xref:System.ValueType>, <xref:System.Object>             |
| temsilci      | <xref:System.MulticastDelegate>, <xref:System.Delegate>, <xref:System.Object> |

## <a name="inheritance-and-an-is-a-relationship"></a>Devralma ve "bir" ilişkidir

Genellikle devralma, bir temel sınıf ve bir veya daha fazla türetilmiş sınıf arasındaki "bir", türetilmiş sınıfların temel sınıfın özelleşmiş sürümü olduğu bir veya daha fazla türetilmiş sınıf arasındaki ilişkiyi ifade etmek için kullanılır; türetilmiş sınıf, temel sınıfın bir türüdür. Örneğin, `Publication` sınıf herhangi bir türdeki yayını temsil eder ve `Book` ve `Magazine` sınıfları belirli yayın türlerini temsil eder.

> [!NOTE]
> Bir sınıf veya yapı, bir veya daha fazla arabirim uygulayabilir. Arabirim uygulaması, tek devralma için bir geçici çözüm olarak veya yapı ile devralma kullanmanın bir yolu olarak sunulurken, bir arabirim ile devralma türü arasında farklı bir ilişki ("yapabilir" ilişki) ifade etmek için tasarlanmıştır. Bir arabirim, bir işlev alt kümesini tanımlar (örneğin, eşitlik için test etme, nesneleri karşılaştırma veya sıralama veya kültüre duyarlı ayrıştırma ve biçimlendirmeyi destekleme), arabirimin uygulama türleri için kullanılabilir hale getiren özellik.

"Bunun bir" olduğuna ve bu türün belirli bir örneğini oluşturma arasındaki ilişkiyi ifade eder. Aşağıdaki örnekte, `Automobile` üç benzersiz salt okuma özelliği olan bir sınıftır: `Make` , otomobil üreticisi;, `Model` otomobil türü; ve `Year` , üretim yılı. `Automobile`Sınıfınız Ayrıca, bağımsız değişkenleri özellik değerlerine atanan bir oluşturucuya sahiptir ve <xref:System.Object.ToString%2A?displayProperty=nameWithType> `Automobile` sınıfı yerine örneği benzersiz bir şekilde tanımlayan bir dize oluşturmak için yöntemini geçersiz kılar `Automobile` .

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/is-a.cs#1)]

Bu durumda, belirli otomobil yaptığı ve modellerinin temsil edilebilmesi için devralmadan güvenmemelisiniz. Örneğin, `Packard` Packard motor otomobil şirketi tarafından üretilen otomobil 'leri temsil eden bir tür tanımlamanız gerekmez. Bunun yerine, `Automobile` Aşağıdaki örnekte olduğu gibi, sınıf oluşturucusuna geçirilmiş uygun değerlerle bir nesne oluşturarak bunları temsil edebilirsiniz.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/is-a.cs#2)]

Bir iş-devralma temelli bir ilişki taban sınıfına ve temel sınıfa ek Üyeler ekleyen ya da temel sınıfta ek işlevsellik gerektiren türetilmiş sınıflara en iyi şekilde uygulanır.

## <a name="designing-the-base-class-and-derived-classes"></a>Temel sınıf ve türetilmiş sınıfları tasarlama

Bir temel sınıf ve türetilmiş sınıfları tasarlama sürecine bakalım. Bu bölümde, `Publication` bir kitap, dergi, gazete, bir günlük, makale vb. gibi her türlü yayını temsil eden bir temel sınıf tanımlayacaksınız. Ayrıca, `Book` öğesinden türetilen bir sınıf tanımlayacaksınız `Publication` . Örneğin,, ve gibi diğer türetilmiş sınıfları tanımlamak için örneği kolayca genişletebilirsiniz `Magazine` `Journal` `Newspaper` `Article` .

### <a name="the-base-publication-class"></a>Temel yayın sınıfı

`Publication`Sınıfınızı tasarlarken birkaç tasarım kararı vermeniz gerekir:

- Temel sınıfınıza hangi Üyeler dahil edileceğini `Publication` ve `Publication` üyelerin Yöntem uygulamaları sağlayıp sağlamadığını ya da `Publication` türetilmiş sınıfları için şablon görevi gören bir soyut temel sınıf olup olmadığını belirtir.

  Bu durumda, `Publication` sınıfı Yöntem uygulamaları sağlar. [Soyut temel sınıfları ve bunların türetilmiş sınıflarını tasarlama](#abstract) bölümü, türetilen sınıfların geçersiz kılınması gereken yöntemleri tanımlamak için soyut bir temel sınıf kullanan bir örnek içerir. Türetilmiş sınıflar, türetilmiş tür için uygun olan herhangi bir uygulamayı sağlamak için ücretsizdir.

  Kodu yeniden kullanma özelliği (yani, birden çok türetilmiş sınıflar temel sınıf yöntemlerinin bildirimini ve uygulamasını paylaşır ve bunları geçersiz kılmaları gerekmez) soyut olmayan taban sınıfların avantajlarından yararlanır. Bu nedenle, `Publication` kendi kodunun bazı veya en özel türler tarafından paylaşılması olasılıklı Üyeler eklemeniz gerekir `Publication` . Temel sınıf uygulamalarını verimli bir şekilde sağlayamadıysanız, temel sınıfta tek bir uygulama yerine türetilmiş sınıflarda büyük ölçüde özdeş üye uygulamaları sağlamak zorunda olacaksınız. Yinelenen kodu birden çok konumda sürdürme gereksinimi, olası hataların kaynağıdır.

  Her ikisi de kod yeniden kullanımını en üst düzeye çıkarmak ve mantıksal ve sezgisel bir devralma hiyerarşisi oluşturmak için, `Publication` yalnızca tüm veya en çok yayımlarda ortak olan verileri ve işlevleri sınıfa dahil ettiğinizden emin olmak istersiniz. Türetilmiş sınıflar daha sonra temsil ettikleri belirli yayın türlerine özgü olan üyeleri uygular.

- Sınıf hiyerarşinizin ne kadar uzaleceği. Yalnızca bir temel sınıf ve bir ya da daha fazla türetilmiş sınıf yerine üç veya daha fazla sınıf hiyerarşisi geliştirmek istiyor musunuz? Örneğin, bir `Publication` taban sınıfı olabilir `Periodical` , bu, ' ın temel sınıfı `Magazine` ve ' dir `Journal` `Newspaper` .

  Örneğinizde, bir sınıfın küçük hiyerarşisini `Publication` ve tek bir türetilmiş sınıf olan ' i kullanacaksınız `Book` . Bu örneği, ve gibi öğesinden türeten bir dizi ek sınıf oluşturmak için kolayca genişletebilirsiniz `Publication` `Magazine` `Article` .

- Temel sınıfın örneğini oluşturma konusunda anlamlı olup olmadığı. Değilse, sınıfa [soyut](../language-reference/keywords/abstract.md) anahtar sözcüğünü uygulamanız gerekir. Aksi halde, sınıfınızın `Publication` sınıf oluşturucusu çağırarak örneklenebilir. Sınıf oluşturucusuna doğrudan çağrı tarafından anahtar sözcükle işaretlenmiş bir sınıf örneği oluşturmak için bir girişimde bulunuldu, `abstract` C# derleyicisi hata CS0144 oluşturuyor, "soyut sınıfın veya arabirimin bir örneği oluşturulamaz." Yansıma kullanarak sınıfın örneğini oluşturmaya yönelik bir girişim yapılırsa, yansıma yöntemi bir oluşturur <xref:System.MemberAccessException> .

  Varsayılan olarak, bir temel sınıf, sınıf oluşturucusu çağırarak örneklenebilir. Açıkça bir sınıf oluşturucusu tanımlamanız gerekmez. Temel sınıfın kaynak kodunda bir tane yoksa, C# derleyicisi otomatik olarak varsayılan (parametresiz) bir oluşturucu sağlar.

  Örneğinizdeki `Publication` sınıfı, örneklenemez hale gelecek şekilde bir [Özet](../language-reference/keywords/abstract.md) olarak işaretlersiniz.  `abstract`Herhangi bir yöntemi olmayan bir sınıf `abstract` , bu sınıfın birkaç somut sınıf (örneğin,) arasında paylaşılan bir soyut kavramı temsil ettiğini `Book` belirtir `Journal` .

- Türetilmiş sınıfların belirli üyelerin temel sınıf uygulamasını devralması gerekip gerekmediğini, temel sınıf uygulamasını geçersiz kılma seçeneğine sahip olup olmadığı veya bir uygulama sağlayıp sağlamamaları gerekir. Türetilmiş sınıfların bir uygulama sağlamasına zorlamak için [soyut](../language-reference/keywords/abstract.md) anahtar sözcüğünü kullanırsınız. Türetilmiş sınıfların bir temel sınıf yöntemini geçersiz kılmasına izin vermek için [sanal](../language-reference/keywords/virtual.md) anahtar sözcüğünü kullanırsınız. Varsayılan olarak, temel sınıfta tanımlanan Yöntemler geçersiz kılınabilir *değildir* .

  `Publication`Sınıfın herhangi bir `abstract` yöntemi yoktur, ancak sınıfın kendisi olur `abstract` .

- Türetilmiş bir sınıfın devralma hiyerarşisinde son sınıfı temsil edip etmediği ve kendisi ek türetilmiş sınıflar için temel sınıf olarak kullanılamaz. Varsayılan olarak, herhangi bir sınıf temel sınıf olarak görev yapabilir. Bir sınıfın herhangi bir ek sınıf için temel sınıf olarak işlev veremeyeceğini belirtmek için [Sealed](../language-reference/keywords/sealed.md) anahtar sözcüğünü uygulayabilirsiniz. Sealed sınıfından türetmeye çalışılıyor CS0509, "mühürlü türden türetilemez \<typeName> ".

  Örneğinizdeki türetilmiş sınıfınızı olarak işaretlersiniz `sealed` .

Aşağıdaki örnek, sınıfının kaynak kodunu ve `Publication` `PublicationType` özelliği tarafından döndürülen bir numaralandırmayı gösterir `Publication.PublicationType` . Öğesinden devraldığı üyelere ek olarak <xref:System.Object> , `Publication` sınıfı aşağıdaki benzersiz üyeleri ve üye geçersiz kılmalarını tanımlar:

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/base-and-derived.cs#1)]

- Bir Oluşturucu

  Sınıfı olduğundan `Publication` `abstract` , doğrudan aşağıdaki örnek gibi koddan başlatılamaz:

  ```csharp
  var publication = new Publication("Tiddlywinks for Experts", "Fun and Games",
                                    PublicationType.Book);
  ```

  Ancak, sınıfının kaynak kodu gösterdiği gibi, örnek Oluşturucusu doğrudan türetilmiş sınıf oluşturucularından çağrılabilir `Book` .

- İki yayınla ilgili özellikler

  `Title`, <xref:System.String> oluşturucuyu çağırarak değeri sağlanan salt okunurdur `Publication` .

  `Pages`, <xref:System.Int32> yayının kaç tane sayfa olduğunu gösteren bir okuma-yazma özelliğidir. Değer adlı bir özel alanda depolanır `totalPages` . Pozitif bir sayı olmalı veya bir değer oluşturulmalıdır <xref:System.ArgumentOutOfRangeException> .

- Yayımcının ilgili üyeleri

  İki salt okuma özelliği `Publisher` ve `Type` . Değerler, başlangıçta sınıf oluşturucusuna yapılan çağrı tarafından sağlanır `Publication` .

- Yayınlamayla ilgili Üyeler

  İki yöntem `Publish` ve `GetPublicationDate` , yayınlama tarihini ayarlayın ve döndürür. `Publish`Yöntemi, `published` çağrıldığında için bir özel bayrak ayarlar `true` ve kendisine geçirilen tarihi özel alana bağımsız değişken olarak atar `datePublished` . `GetPublicationDate`Yöntemi, bayrak ise "NYP" dizesini `published` `false` ve `datePublished` varsa alanın değerini döndürür `true` .

- Telif hakkı ile ilgili Üyeler

  `Copyright`Yöntemi, telif hakkı sahibinin adını ve telif hakkı yılını bağımsız değişken olarak alır ve bunları `CopyrightName` ve özelliklerine atar `CopyrightDate` .

- Yöntemi geçersiz kılma `ToString`

  Bir tür yöntemi geçersiz kılmadığından, bir <xref:System.Object.ToString%2A?displayProperty=nameWithType> örneği diğerinden Farklılaştırmada çok az kullanılan, türün tam nitelikli adını döndürür. `Publication`Sınıfı, <xref:System.Object.ToString%2A?displayProperty=nameWithType> özelliğinin değerini döndürecek şekilde geçersiz kılar `Title` .

Aşağıdaki şekilde, taban `Publication` sınıfınız ve örtülü olarak devralınan sınıfı arasındaki ilişki gösterilmektedir <xref:System.Object> .

![Nesne ve yayın sınıfları](media/publication-class.jpg)

### <a name="the-book-class"></a>`Book`Sınıfı

`Book`Sınıfı, bir kitabı özelleşmiş bir yayın türü olarak temsil eder. Aşağıdaki örnek, sınıfının kaynak kodunu gösterir `Book` .

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/base-and-derived.cs#2)]

Öğesinden devraldığı üyelere ek olarak `Publication` , `Book` sınıfı aşağıdaki benzersiz üyeleri ve üye geçersiz kılmalarını tanımlar:

- İki Oluşturucu

  İki `Book` Oluşturucu üç ortak parametreyi paylaşır. İki, *başlık* ve *Yayımcı*, oluşturucunun parametrelerine karşılık gelir `Publication` . Üçüncü, genel bir sabit özelliğe depolanan *Yazar* `Author` . Bir Oluşturucu, Auto-Property içinde depolanan bir *ISBN* parametresi içerir `ISBN` .

  İlk Oluşturucu, diğer oluşturucuyu çağırmak için [this](../language-reference/keywords/this.md) anahtar sözcüğünü kullanır. Oluşturucu zincirleme, Oluşturucu tanımlamalarında ortak bir modeldir. Daha az parametreye sahip oluşturucular, oluşturucuyu en fazla parametre sayısıyla çağırırken varsayılan değerleri sağlar.

  İkinci Oluşturucu, başlığı ve yayımcı adını temel sınıf oluşturucusuna geçirmek için [temel](../language-reference/keywords/base.md) anahtar sözcüğünü kullanır. Kaynak kodunuzda bir taban sınıf oluşturucusuna açık bir çağrı yapmazsanız, C# derleyicisi otomatik olarak taban sınıfının varsayılan veya parametresiz oluşturucusuna bir çağrı sağlar.

- `ISBN` `Book` Nesnenin uluslararası standart defter numarasını, 10 veya 13 basamaklı bir sayıyı döndüren salt okunurdur bir özellik. ISBN oluşturuculardan birine bir bağımsız değişken olarak sağlanır `Book` . ISBN, derleyici tarafından otomatik olarak oluşturulan özel bir yedekleme alanında depolanır.

- Salt okunurdur `Author` özelliği. Yazar adı her iki Oluşturucu için bir bağımsız değişken olarak sağlanır `Book` ve özellikte depolanır.

- İki salt okuma fiyatına ilişkin özellikler `Price` ve `Currency` . Değerleri bir yöntem çağrısında bağımsız değişken olarak sağlanır `SetPrice` . `Currency`Özelliği üç BASAMAKLı ISO para birimi simgedir (örneğin, ABD Doları IÇIN USD). ISO para birimi sembolleri <xref:System.Globalization.RegionInfo.ISOCurrencySymbol%2A> özelliğinden alınabilir. Bu özelliklerin her ikisi de dışarıdan salt okunurdur, ancak her ikisi de sınıftaki kodla ayarlanabilir `Book` .

- `SetPrice`Ve özelliklerinin değerlerini ayarlayan bir yöntemi `Price` `Currency` . Bu değerler, aynı özelliklerle döndürülür.

- `ToString`Yöntemi (Devralındığı yer `Publication` ) ve <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> ve <xref:System.Object.GetHashCode%2A> yöntemlerini (öğesinden devralınan <xref:System.Object> ) geçersiz kılar.

  Geçersiz kılınmadıkça, <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> yöntemi başvuru eşitliği için test eder. Diğer bir deyişle, aynı nesneye başvurduklarında iki nesne değişkeninin eşit olduğu kabul edilir. `Book`Sınıfında, diğer yandan, `Book` aynı ISBN 'e sahip olmaları durumunda iki nesne eşit olmalıdır.

  Yöntemi geçersiz kıldığınızda, <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> <xref:System.Object.GetHashCode%2A> verimli alma için, çalışma zamanının öğeleri karma koleksiyonlara depolamak üzere kullandığı bir değer döndüren yöntemini de geçersiz kılmanız gerekir. Karma kodu, eşitlik için testle tutarlı bir değer döndürmelidir. <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> `true` Ikı nesnenin ISBN özellikleri eşitse döndürülecek şekilde geçersiz kılındığından `Book` , <xref:System.String.GetHashCode%2A> özelliği tarafından döndürülen dize yöntemini çağırarak hesaplanan karma kodu döndürün `ISBN` .

Aşağıdaki şekilde, `Book` sınıfı ve temel sınıfı arasındaki ilişki gösterilmektedir `Publication` .

![Yayın ve kitap sınıfları](media/book-class.jpg)

Artık bir nesnesi örneği oluşturabilir `Book` , hem benzersiz hem de devralınan üyelerini çağırabilir ve `Publication` `Book` Aşağıdaki örnekte gösterildiği gibi, türü veya türü bir parametreyi bekleyen bir yönteme bağımsız değişken olarak geçirebilirsiniz.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/use-publication.cs#1)]

## <a name="designing-abstract-base-classes-and-their-derived-classes"></a>Soyut temel sınıfları ve bunların türetilmiş sınıflarını tasarlama
<a name="abstract"></a>

Önceki örnekte, türetilmiş sınıfların kod paylaşmasına izin veren bir dizi yöntem için uygulama sağlayan bir temel sınıf tanımladınız. Ancak çoğu durumda, temel sınıfın bir uygulama sağlaması beklenmez. Bunun yerine, temel sınıf *soyut yöntemleri*bildiren *soyut bir sınıftır* ; Her türetilmiş sınıfın uygulaması gereken üyeleri tanımlayan bir şablon görevi görür. Genellikle soyut bir temel sınıfta, her türetilmiş türün uygulanması o tür için benzersizdir. Sınıf, `Publication` yayınlar için ortak işlevsellik uygulamaları sağlasa da, bir nesnenin örneğini oluşturma konusunda hiçbir fikir olmadığından, bu sınıfı soyut anahtar sözcükle işaretlenir.

Örneğin, her kapatılan iki boyutlu geometrik şekil iki özellik içerir: alan, şeklin iç kapsamı; ve çevre ya da şeklin kenarları arasındaki uzaklık. Ancak, bu özelliklerin hesaplanma şekli, ancak tamamen belirli bir şekle bağlıdır. Örneğin, bir dairenin çevre (veya çevresi) hesaplama formülü, bir üçgenden farklıdır. `Shape`Sınıfı `abstract` Yöntemler içeren bir sınıftır `abstract` . Bu, türetilmiş sınıfların aynı işlevselliği paylaştığından, ancak bu türetilmiş sınıfların bu işlevselliği farklı şekilde uyguladığını gösterir.

Aşağıdaki örnek, adlı bir soyut temel sınıfı tanımlar `Shape` ve iki özelliği tanımlar: `Area` ve `Perimeter` . Sınıfı [soyut](../language-reference/keywords/abstract.md) anahtar sözcükle işaretlemeye ek olarak, her örnek üyesi de [soyut](../language-reference/keywords/abstract.md) anahtar sözcüğüyle işaretlenir. Bu durumda, `Shape` <xref:System.Object.ToString%2A?displayProperty=nameWithType> tam adı yerine türün adını döndürmek için yöntemini de geçersiz kılar. Ve bu, iki statik üye tanımlar `GetArea` ve `GetPerimeter` Bu, çağıranların, türetilmiş bir sınıfın bir örneğinin alanını ve çevresini kolayca almasına imkan tanır. Türetilmiş bir sınıfın bir örneğini bu yöntemlerin herhangi birine geçirdiğinizde, çalışma zamanı türetilmiş sınıfın yöntem geçersiz kılmasını çağırır.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#1)]

Daha sonra `Shape` belirli şekilleri temsil eden bazı sınıfları türetebilirsiniz. Aşağıdaki örnek üç sınıfı tanımlar,, `Triangle` `Rectangle` ve `Circle` . Her biri, alanı ve çevresi hesaplamak için bu belirli bir şekil için benzersiz bir formül kullanır. Türetilmiş sınıflardan bazıları Ayrıca, ve gibi özellikleri tanımlar `Rectangle.Diagonal` ve `Circle.Diameter` temsil ettikleri şekle özeldir.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#2)]

Aşağıdaki örnek, öğesinden türetilmiş nesneleri kullanır `Shape` . Sınıfından türetilmiş bir nesne dizisi oluşturur `Shape` ve `Shape` döndürülen özellik değerlerini sarmalayan sınıfın statik yöntemlerini çağırır `Shape` . Çalışma zamanı türetilmiş türlerin geçersiz kılınan özelliklerinden değerleri alır. Örnek ayrıca dizideki her bir `Shape` nesneyi türetilmiş türüne yayınlar ve atama başarılı olursa, belirli bir alt sınıfının özelliklerini alır `Shape` .

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#3)]

## <a name="see-also"></a>Ayrıca bkz.

- [Devralma (C# Programlama Kılavuzu)](../programming-guide/classes-and-structs/inheritance.md)
