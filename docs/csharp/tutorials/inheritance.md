---
title: DevralınanlarC#
description: C# Kitaplıklarda ve uygulamalarda devralma kullanmayı öğrenin.
author: rpetrusha
ms.date: 07/05/2018
ms.technology: csharp-fundamentals
ms.assetid: aeb68c74-0ea0-406f-9fbe-2ce02d47ef31
ms.openlocfilehash: f09eaaf397d148955a151d178566f2b5a0d935fd
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039233"
---
# <a name="inheritance-in-c-and-net"></a>C# ve .NET içinde devralma

Bu öğretici, ' de C#devralma işlemini tanıtır. Devralma, belirli işlevleri (veri ve davranış) sağlayan bir temel sınıf tanımlamanızı ve bu işlevi devralıp geçersiz kılan türetilmiş sınıfları tanımlamanızı sağlayan nesne odaklı programlama dillerinin bir özelliğidir.

## <a name="prerequisites"></a>Prerequisites

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

C#ve .NET yalnızca *tek devralma* desteği. Diğer bir deyişle, bir sınıf yalnızca tek bir sınıftan devralınabilir. Ancak, devralma geçişlidir ve bu, bir tür kümesi için devralma hiyerarşisi tanımlamanızı sağlar. Diğer bir deyişle `D`, temel sınıf türü `A`devralan `B`türünden devralan tür `C`devralabilir. Devralma geçişli olduğundan, `A` türündeki Üyeler `D`türü için kullanılabilir.

Bir taban sınıfın tüm üyeleri türetilmiş sınıflar tarafından devralınmaz. Aşağıdaki Üyeler devralınmaz:

- Statik [oluşturucular](../programming-guide/classes-and-structs/static-constructors.md), bir sınıfın statik verilerini başlatır.

- Sınıfının yeni bir örneğini oluşturmak için çağırdığınız [örnek oluşturucular](../programming-guide/classes-and-structs/constructors.md). Her sınıfın kendi oluşturucuları tanımlanmalıdır.

- Çalışma zamanının atık toplayıcısı tarafından bir sınıfın örneklerini yok etmek için çağrılan [sonlandırıcılar](../programming-guide/classes-and-structs/destructors.md).

Bir temel sınıfın diğer tüm üyeleri türetilmiş sınıflar tarafından devralınırken, görünür olup olmadığı ve erişilebilirliğine bağlı olup olmadığı. Üyenin erişilebilirliği, türetilmiş sınıfların görünürlüğünü aşağıdaki gibi etkiler:

- [Özel](../language-reference/keywords/private.md) Üyeler yalnızca kendi temel sınıfında iç içe yerleştirilmiş türetilmiş sınıflarda görünür. Aksi takdirde, bunlar türetilmiş sınıflarda görünür değildir. Aşağıdaki örnekte, `A.B` `A`türetilen iç içe bir sınıftır ve `C` `A`türetilir. Özel `A.value` alanı A.B. içinde görülebilir Ancak, `C.GetValue` yönteminden açıklamaları kaldırır ve örneği derlemeye çalışırsanız, CS0122 derleyici hatası üretir: "' A. Value ', koruma düzeyi nedeniyle erişilemez."

  [!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/private.cs#1)]

- [Korunan](../language-reference/keywords/protected.md) Üyeler yalnızca türetilmiş sınıflarda görülebilir.

- [İç](../language-reference/keywords/internal.md) Üyeler yalnızca temel sınıfla aynı derlemede bulunan türetilmiş sınıflarda görülebilir. Bunlar, temel sınıftan farklı bir derlemede bulunan türetilmiş sınıflarda görünür değildir.

- [Ortak](../language-reference/keywords/public.md) Üyeler türetilmiş sınıflarda görünür ve türetilmiş sınıf ' genel arabiriminin bir parçasıdır. Ortak devralınmış Üyeler, türetilmiş sınıfta tanımlandıklarında olduğu gibi çağrılabilir. Aşağıdaki örnekte, sınıf `A` `Method1`adlı bir yöntemi tanımlar ve sınıf `B` sınıf `A`devralır. Örnek daha sonra `Method1` `B`bir örnek yöntemi gibi çağırır.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/basics.cs#1)]

Türetilmiş sınıflar, alternatif bir uygulama sağlayarak devralınan üyeleri de *geçersiz kılabilir* . Bir üyeyi geçersiz kılabilmek için, temel sınıftaki üyenin [sanal](../language-reference/keywords/virtual.md) anahtar sözcüğüyle işaretlenmesi gerekir. Varsayılan olarak, temel sınıf üyeleri `virtual` olarak işaretlenmez ve geçersiz kılınamaz. Şu örnekte olduğu gibi sanal olmayan bir üyeyi geçersiz kılma girişimi, CS0506: "\<member >, devralınan üye \<üye > geçersiz kılamaz çünkü sanal, Özet veya geçersiz kılma olarak işaretlenmemiş.

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

Bazı durumlarda, türetilmiş bir sınıf temel sınıf uygulamasını geçersiz *kılmalıdır* . [Soyut](../language-reference/keywords/abstract.md) anahtar sözcükle işaretlenmiş temel sınıf üyeleri, türetilmiş sınıfların bunları geçersiz kılmasını gerektirir. Aşağıdaki örnek derlenmeye çalışıldığında, "&lt;Class&gt; devralınan soyut üye &lt;üye&gt;" uygulamıyor, çünkü sınıf `B` `A.Method1`için uygulama sağlamaz.

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

Tek devralmayla devraldıkları türlerin yanı sıra, .NET tür sistemindeki tüm türler <xref:System.Object> veya ondan türetilmiş bir türden örtülü olarak devralınır. <xref:System.Object> ortak işlevselliği her türlü tür için kullanılabilir.

Örtük devralmanın ne anlama geldiğini görmek için yalnızca boş bir sınıf tanımı olan `SimpleClass`yeni bir sınıf tanımlayalim:

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass.cs#1)]

Daha sonra, `SimpleClass` türüne ait üyelerin bir listesini almak için yansıma (Bu tür hakkında bilgi almak üzere bir türün meta verilerini incelemenizi sağlar) kullanabilirsiniz. `SimpleClass` sınıfınızda herhangi bir üye tanımlamasanız da, örnekteki çıkış aslında dokuz üyeye sahip olduğunu gösterir. Bu üyelerden biri, C# derleyici tarafından `SimpleClass` türü için otomatik olarak sağlanan parametresiz (veya varsayılan) bir oluşturucudur. Kalan sekiz, .NET tür sistemindeki tüm sınıfların ve arabirimlerin sonunda örtük olarak devraldığı <xref:System.Object>üyeleridir.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass.cs#2)]

<xref:System.Object> sınıfından örtük devralma, bu yöntemleri `SimpleClass` sınıfı için kullanılabilir hale getirir:

- Bir `SimpleClass` nesnesini dize gösterimine dönüştüren public `ToString` yöntemi, tam nitelikli tür adını döndürür. Bu durumda `ToString` yöntemi "SimpleClass" dizesini döndürür.

- İki nesnenin eşitlik için test eden üç yöntem: ortak örnek `Equals(Object)` yöntemi, genel statik `Equals(Object, Object)` yöntemi ve genel statik `ReferenceEquals(Object, Object)` yöntemi. Varsayılan olarak, bu yöntemler başvuru eşitliği için test; diğer bir deyişle, eşit olması için iki nesne değişkeninin aynı nesneye başvurması gerekir.

- Karma koleksiyonlarda kullanılacak tür örneğine izin veren bir değeri hesaplayan ortak `GetHashCode` yöntemi.

- `SimpleClass` türünü temsil eden bir <xref:System.Type> nesnesi döndüren public `GetType` yöntemi.

- Bir nesnenin belleğinden önce yönetilmeyen kaynakları serbest bırakmak için tasarlanan korumalı <xref:System.Object.Finalize%2A> yöntemi çöp toplayıcı tarafından geri kazanılır.

- Geçerli nesnesinin basit bir kopyasını oluşturan Protected <xref:System.Object.MemberwiseClone%2A> yöntemi.

Örtük devralma nedeniyle, bir `SimpleClass` nesnesinden devralınan herhangi bir üyeyi, aslında `SimpleClass` sınıfında tanımlanmış bir üye gibi çağırabilirsiniz. Örneğin, aşağıdaki örnek <xref:System.Object>devralan `SimpleClass` `SimpleClass.ToString` yöntemini çağırır.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass2.cs#1)]

Aşağıdaki tabloda, içinde C# oluşturabileceğiniz türlerin kategorileri ve örtülü olarak devraldığı türler listelenmektedir. Her temel tür, devralma yoluyla örtülü olarak türetilmiş türlere farklı bir üye kümesi sağlar.

| Tür kategorisi | Örtülü olarak devralır                                                      |
| ------------- | ----------------------------------------------------------------------------- |
| sınıf         | <xref:System.Object>                                                          |
| struct        | <xref:System.ValueType>, <xref:System.Object>                                 |
| enum          | <xref:System.Enum>, <xref:System.ValueType>, <xref:System.Object>             |
| temsilci      | <xref:System.MulticastDelegate>, <xref:System.Delegate>, <xref:System.Object> |

## <a name="inheritance-and-an-is-a-relationship"></a>Devralma ve "bir" ilişkidir

Genellikle devralma, bir temel sınıf ve bir veya daha fazla türetilmiş sınıf arasındaki "bir", türetilmiş sınıfların temel sınıfın özelleşmiş sürümü olduğu bir veya daha fazla türetilmiş sınıf arasındaki ilişkiyi ifade etmek için kullanılır; türetilmiş sınıf, temel sınıfın bir türüdür. Örneğin, `Publication` sınıfı her türlü yayını temsil eder ve `Book` ve `Magazine` sınıfları belirli yayın türlerini temsil eder.

> [!NOTE]
> Bir sınıf veya yapı, bir veya daha fazla arabirim uygulayabilir. Arabirim uygulaması genellikle tek devralma için geçici bir çözüm olarak veya yapılar ile devralma kullanmanın bir yolu olarak sunulurken, farklı bir ilişki ("bir" ilişki yapabilir) bir arabirim ile uygulama türü devralmayı. Bir arabirim, bir işlev alt kümesini tanımlar (örneğin, eşitlik için test etme, nesneleri karşılaştırma veya sıralama veya kültüre duyarlı ayrıştırma ve biçimlendirmeyi destekleme), arabirimin uygulama türleri için kullanılabilir hale getiren özellik.

"Bunun bir" olduğuna ve bu türün belirli bir örneğini oluşturma arasındaki ilişkiyi ifade eder. Aşağıdaki örnekte `Automobile`, üç benzersiz salt okuma özelliği olan bir sınıftır: `Make`, otomobil üreticisi. `Model`, otomobil türü; `Year`, üretim yılından oluşan yıl. `Automobile` sınıfınız, bağımsız değişkenleri özellik değerlerine atanan bir oluşturucuya sahiptir ve `Automobile` sınıfı yerine `Automobile` örneğini benzersiz bir şekilde tanımlayan bir dize oluşturmak için <xref:System.Object.ToString%2A?displayProperty=nameWithType> yöntemini geçersiz kılar.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/is-a.cs#1)]

Bu durumda, belirli otomobil yaptığı ve modellerinin temsil edilebilmesi için devralmadan güvenmemelisiniz. Örneğin, Packard motor otomobil şirketi tarafından üretilen otomobil 'leri temsil etmek için bir `Packard` türü tanımlamanız gerekmez. Bunun yerine, aşağıdaki örnekte olduğu gibi, sınıf oluşturucusuna geçirilmiş uygun değerlerle bir `Automobile` nesnesi oluşturarak bunları temsil edebilirsiniz.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/is-a.cs#2)]

Bir iş-devralma temelli bir ilişki taban sınıfına ve temel sınıfa ek Üyeler ekleyen ya da temel sınıfta ek işlevsellik gerektiren türetilmiş sınıflara en iyi şekilde uygulanır.

## <a name="designing-the-base-class-and-derived-classes"></a>Temel sınıf ve türetilmiş sınıfları tasarlama

Bir temel sınıf ve türetilmiş sınıfları tasarlama sürecine bakalım. Bu bölümde, kitap, dergi, gazete, günlük, makale vb. gibi her türlü yayını temsil eden `Publication`bir temel sınıf tanımlayacaksınız. Ayrıca, `Publication`türeten bir `Book` sınıfını da tanımlayacaksınız. `Magazine`, `Journal`, `Newspaper`ve `Article`gibi diğer türetilmiş sınıfları tanımlamak için örneği kolayca genişletebilirsiniz.

### <a name="the-base-publication-class"></a>Temel yayın sınıfı

`Publication` sınıfınızı tasarlarken birkaç tasarım kararı vermeniz gerekir:

- Temel `Publication` sınıfınıza dahil edilecek Üyeler ve `Publication` üyelerin Yöntem uygulamaları sağlayıp sağlamadığını veya `Publication` türetilmiş sınıfları için şablon görevi gören bir soyut temel sınıf olup olmadığını belirtir.

  Bu durumda, `Publication` sınıfı Yöntem uygulamaları sağlar. [Soyut temel sınıfları ve bunların türetilmiş sınıflarını tasarlama](#abstract) bölümü, türetilen sınıfların geçersiz kılınması gereken yöntemleri tanımlamak için soyut bir temel sınıf kullanan bir örnek içerir. Türetilmiş sınıflar, türetilmiş tür için uygun olan herhangi bir uygulamayı sağlamak için ücretsizdir.

  Kodu yeniden kullanma özelliği (yani, birden çok türetilmiş sınıflar temel sınıf yöntemlerinin bildirimini ve uygulamasını paylaşır ve bunları geçersiz kılmaları gerekmez) soyut olmayan taban sınıfların avantajlarından yararlanır. Bu nedenle, kodun bazı veya en özelleştirilmiş `Publication` türleri tarafından paylaşılması olasılığı varsa `Publication` üyeleri eklemeniz gerekir. Temel sınıf uygulamalarını verimli bir şekilde sağlayamadıysanız, temel sınıfta tek bir uygulama yerine türetilmiş sınıflarda büyük ölçüde özdeş üye uygulamaları sağlamak zorunda olacaksınız. Yinelenen kodu birden çok konumda sürdürme gereksinimi, olası hataların kaynağıdır.

  Her ikisi de kod yeniden kullanımını en üst düzeye çıkarmak ve mantıksal ve sezgisel bir devralma hiyerarşisi oluşturmak için `Publication` sınıfına yalnızca tüm veya en çok yayınlar için ortak olan verileri ve işlevleri eklediğinizden emin olmak istersiniz. Türetilmiş sınıflar daha sonra temsil ettikleri belirli yayın türlerine özgü olan üyeleri uygular.

- Sınıf hiyerarşinizin ne kadar uzaleceği. Yalnızca bir temel sınıf ve bir ya da daha fazla türetilmiş sınıf yerine üç veya daha fazla sınıf hiyerarşisi geliştirmek istiyor musunuz? Örneğin, `Publication` temel bir `Periodical`sınıfı olabilir. Bu, sırasıyla `Magazine`, `Journal` ve `Newspaper`temel sınıfıdır.

  Örneğinizde, bir `Publication` sınıfının küçük hiyerarşisini ve tek bir türetilmiş sınıf olan `Book`kullanacaksınız. `Magazine` ve `Article`gibi `Publication`türeten bir dizi ek sınıf oluşturmak için bu örneği kolayca genişletebilirsiniz.

- Temel sınıfın örneğini oluşturma konusunda anlamlı olup olmadığı. Değilse, sınıfa [soyut](../language-reference/keywords/abstract.md) anahtar sözcüğünü uygulamanız gerekir. Aksi takdirde, `Publication` sınıfınız sınıf oluşturucusu çağırarak örneklenebilir. Sınıf oluşturucusuna doğrudan çağrı tarafından `abstract` anahtar sözcüğüyle işaretlenmiş bir sınıf örneği oluşturmak için bir girişim yapılırsa, C# DERLEYICI hata CS0144 oluşturuyor, "soyut sınıfın veya arabirimin bir örneği oluşturulamaz." Yansıma kullanarak sınıfın örneğini oluşturmaya yönelik bir girişim yapılırsa, yansıma yöntemi bir <xref:System.MemberAccessException>oluşturur.

  Varsayılan olarak, bir temel sınıf, sınıf oluşturucusu çağırarak örneklenebilir. Açıkça bir sınıf oluşturucusu tanımlamanız gerekmez. Temel sınıfın kaynak kodunda bir tane yoksa, C# derleyici otomatik olarak varsayılan (parametresiz) bir oluşturucu sağlar.

  Örnek olarak, `Publication` sınıfını [Özet](../language-reference/keywords/abstract.md) olarak işaretleyecek ve bu şekilde örneklendirilirsiniz.  Herhangi bir `abstract` yöntemi olmayan bir `abstract` sınıfı, bu sınıfın birkaç somut sınıf (`Book`, `Journal`gibi) arasında paylaşılan bir soyut kavramı temsil ettiğini belirtir.

- Türetilmiş sınıfların belirli üyelerin temel sınıf uygulamasını devralması gerekip gerekmediğini, temel sınıf uygulamasını geçersiz kılma seçeneğine sahip olup olmadığı veya bir uygulama sağlayıp sağlamamaları gerekir. Türetilmiş sınıfların bir uygulama sağlamasına zorlamak için [soyut](../language-reference/keywords/abstract.md) anahtar sözcüğünü kullanırsınız. Türetilmiş sınıfların bir temel sınıf yöntemini geçersiz kılmasına izin vermek için [sanal](../language-reference/keywords/virtual.md) anahtar sözcüğünü kullanırsınız. Varsayılan olarak, temel sınıfta tanımlanan Yöntemler geçersiz kılınabilir *değildir* .

 `Publication` sınıfı hiçbir `abstract` yöntemine sahip değil, ancak sınıfın kendisi `abstract`.

- Türetilmiş bir sınıfın devralma hiyerarşisinde son sınıfı temsil edip etmediği ve kendisi ek türetilmiş sınıflar için temel sınıf olarak kullanılamaz. Varsayılan olarak, herhangi bir sınıf temel sınıf olarak görev yapabilir. Bir sınıfın herhangi bir ek sınıf için temel sınıf olarak işlev veremeyeceğini belirtmek için [Sealed](../language-reference/keywords/sealed.md) anahtar sözcüğünü uygulayabilirsiniz. Sealed sınıf tarafından oluşturulan bir derleyici hatası CS0509, "Sealed Type \<typeName >" öğesinden türetilmeye çalışılıyor.

  Örneğinizdeki türetilmiş sınıfınızı `sealed`olarak işaretlersiniz.

Aşağıdaki örnek, `Publication` sınıfı için kaynak kodu ve `Publication.PublicationType` özelliği tarafından döndürülen `PublicationType` numaralandırması gösterir. <xref:System.Object>devraldığı üyelere ek olarak, `Publication` sınıfı aşağıdaki benzersiz üyeleri ve üye geçersiz kılmalarını tanımlar:

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/base-and-derived.cs#1)]

- Bir Oluşturucu

  `Publication` sınıfı `abstract`olduğundan, doğrudan aşağıdaki örnek gibi koddan başlatılamaz:

  ```csharp
  var publication = new Publication("Tiddlywinks for Experts", "Fun and Games",
                                    PublicationType.Book);
  ```

  Ancak, `Book` sınıfının kaynak kodu gösterdiği gibi, örnek Oluşturucusu doğrudan türetilmiş sınıf oluşturucularından çağrılabilir.

- İki yayınla ilgili özellikler

  `Title`, değeri `Publication` Oluşturucusu çağırarak sağlanan salt okunurdur <xref:System.String> bir özelliktir.

  `Pages`, yayının kaç tane sayfa olduğunu gösteren bir okuma-yazma <xref:System.Int32> özelliğidir. Değer, `totalPages`adlı bir özel alanda depolanır. Pozitif bir sayı olmalıdır veya <xref:System.ArgumentOutOfRangeException> atılır.

- Yayımcının ilgili üyeleri

  İki salt okuma özelliği, `Publisher` ve `Type`. Değerler, başlangıçta `Publication` sınıf oluşturucusuna yapılan çağrı tarafından sağlanır.

- Yayınlamayla ilgili Üyeler

  İki yöntem, `Publish` ve `GetPublicationDate`, yayınlama tarihini ayarlayıp döndürür. `Publish` yöntemi, çağrıldığında `true` için özel bir `published` bayrağını ayarlar ve kendisine geçirilen tarihi özel `datePublished` alanına bağımsız değişken olarak atar. `GetPublicationDate` yöntemi, `published` bayrağı `false`ve `true`ise `datePublished` alanının değeri olan "NYP" dizesini döndürür.

- Telif hakkı ile ilgili Üyeler

  `Copyright` yöntemi, telif hakkı sahibinin adını ve telif hakkı yılını bağımsız değişken olarak alır ve bunları `CopyrightName` ve `CopyrightDate` özelliklerine atar.

- `ToString` yöntemi geçersiz kılma

  Bir tür <xref:System.Object.ToString%2A?displayProperty=nameWithType> yöntemini geçersiz kılamadıysa, bir örneği diğerinden Farklılaştırmada kullanılan, türün tam nitelikli adını döndürür. `Publication` sınıfı `Title` özelliğin değerini döndürmek için <xref:System.Object.ToString%2A?displayProperty=nameWithType> geçersiz kılar.

Aşağıdaki şekilde, temel `Publication` sınıfınız ile örtülü olarak devralınan <xref:System.Object> sınıfı arasındaki ilişki gösterilmektedir.

![Nesne ve yayın sınıfları](media/publication-class.jpg)

### <a name="the-book-class"></a>`Book` sınıfı

`Book` sınıfı, bir kitabı özelleşmiş bir yayın türü olarak temsil eder. Aşağıdaki örnek `Book` sınıfının kaynak kodunu gösterir.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/base-and-derived.cs#2)]

`Publication`devraldığı üyelere ek olarak, `Book` sınıfı aşağıdaki benzersiz üyeleri ve üye geçersiz kılmalarını tanımlar:

- İki Oluşturucu

  İki `Book` Oluşturucusu üç ortak parametreyi paylaşır. İki, *başlık* ve *Yayımcı*, `Publication` oluşturucusunun parametrelerine karşılık gelir. Üçüncü, bir genel sabit `Author` özelliğine depolanan *Yazar*. Bir Oluşturucu, `ISBN` Auto-özelliğinde depolanan bir *ISBN* parametresi içerir.

  İlk Oluşturucu, diğer oluşturucuyu çağırmak için [this](../language-reference/keywords/this.md) anahtar sözcüğünü kullanır. Oluşturucu zincirleme, Oluşturucu tanımlamalarında ortak bir modeldir. Daha az parametreye sahip oluşturucular, oluşturucuyu en fazla parametre sayısıyla çağırırken varsayılan değerleri sağlar.

  İkinci Oluşturucu, başlığı ve yayımcı adını temel sınıf oluşturucusuna geçirmek için [temel](../language-reference/keywords/base.md) anahtar sözcüğünü kullanır. Kaynak kodunuzda bir taban sınıf oluşturucusuna açık bir çağrı yapmazsanız, C# derleyici otomatik olarak taban sınıfının varsayılan veya parametresiz oluşturucusuna bir çağrı sağlar.

- `Book` nesnesinin uluslararası standart kitap numarasını, benzersiz bir 10 veya 13 basamaklı bir sayı döndüren salt okunurdur `ISBN` özelliği. ISBN, `Book` oluşturucularından birine bir bağımsız değişken olarak sağlanır. ISBN, derleyici tarafından otomatik olarak oluşturulan özel bir yedekleme alanında depolanır.

- Salt okunurdur `Author` özelliği. Yazar adı, `Book` oluşturucularının her ikisine de bir bağımsız değişken olarak sağlanır ve özelliğinde depolanır.

- İki salt okuma fiyatına ilişkin özellikler, `Price` ve `Currency`. Değerleri `SetPrice` Yöntem çağrısında bağımsız değişken olarak sağlanır. `Currency` özelliği üç basamaklı ISO para birimi simgedir (örneğin, ABD Doları için USD). ISO para birimi sembolleri <xref:System.Globalization.RegionInfo.ISOCurrencySymbol%2A> özelliğinden alınabilir. Bu özelliklerin her ikisi de dışarıdan salt okunurdur, ancak her ikisi de `Book` sınıfındaki kodla ayarlanabilir.

- `Price` ve `Currency` özelliklerinin değerlerini ayarlayan `SetPrice` yöntemi. Bu değerler, aynı özelliklerle döndürülür.

- `ToString` yöntemine (`Publication`devralınmış) ve <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> ve <xref:System.Object.GetHashCode%2A> yöntemlerine (<xref:System.Object>devralınmış) geçersiz kılar.

  Geçersiz kılınmadıkça <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> yöntemi başvuru eşitliği sınar. Diğer bir deyişle, aynı nesneye başvurduklarında iki nesne değişkeninin eşit olduğu kabul edilir. `Book` sınıfında, diğer taraftan, aynı ıSBN 'e sahip olmaları durumunda iki `Book` nesnesi eşit olmalıdır.

  <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> yöntemi geçersiz kıldığınızda, verimli alma için çalışma zamanının öğeleri karma koleksiyonlara depolamak üzere kullandığı bir değer döndüren <xref:System.Object.GetHashCode%2A> yöntemini de geçersiz kılmanız gerekir. Karma kodu, eşitlik için testle tutarlı bir değer döndürmelidir. İki `Book` nesnesinin ıSBN özellikleri eşitse `true` döndürmek için <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> geçersiz kıldığından, `ISBN` özelliği tarafından döndürülen dizenin <xref:System.String.GetHashCode%2A> yöntemini çağırarak hesaplanan karma kodu döndürürsünüz.

Aşağıdaki şekilde, `Book` sınıfı ve `Publication`temel sınıfı arasındaki ilişki gösterilmektedir.

![Yayın ve kitap sınıfları](media/book-class.jpg)

Artık bir `Book` nesnesi oluşturabilir, hem benzersiz hem de devralınan üyelerini çağırabilir ve aşağıdaki örnekte gösterildiği gibi, `Publication` veya `Book`türünde bir parametre bekleyen bir yönteme bağımsız değişken olarak geçirebilirsiniz.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/use-publication.cs#1)]

## <a name="designing-abstract-base-classes-and-their-derived-classes"></a>Soyut temel sınıfları ve bunların türetilmiş sınıflarını tasarlama
<a name="abstract"></a>

Önceki örnekte, türetilmiş sınıfların kod paylaşmasına izin veren bir dizi yöntem için uygulama sağlayan bir temel sınıf tanımladınız. Ancak çoğu durumda, temel sınıfın bir uygulama sağlaması beklenmez. Bunun yerine, temel sınıf *soyut yöntemleri*bildiren *soyut bir sınıftır* ; Her türetilmiş sınıfın uygulaması gereken üyeleri tanımlayan bir şablon görevi görür. Genellikle soyut bir temel sınıfta, her türetilmiş türün uygulanması o tür için benzersizdir. Sınıf, yayınlar için ortak işlevsellik uygulamaları sağladığından, bir `Publication` nesnesinin örneğini oluşturma konusunda hiçbir fikir olmadığından, bu sınıfı soyut anahtar sözcükle işaretlenir.

Örneğin, her kapatılan iki boyutlu geometrik şekil iki özellik içerir: alan, şeklin iç kapsamı; ve çevre ya da şeklin kenarları arasındaki uzaklık. Ancak, bu özelliklerin hesaplanma şekli, ancak tamamen belirli bir şekle bağlıdır. Örneğin, bir dairenin çevre (veya çevresi) hesaplama formülü, bir üçgenden farklıdır. `Shape` sınıfı, `abstract` Yöntemler içeren bir `abstract` sınıfıdır. Bu, türetilmiş sınıfların aynı işlevselliği paylaştığından, ancak bu türetilmiş sınıfların bu işlevselliği farklı şekilde uyguladığını gösterir.

Aşağıdaki örnek, iki özelliği tanımlayan `Shape` adlı soyut temel sınıfı tanımlar: `Area` ve `Perimeter`. Sınıfı [soyut](../language-reference/keywords/abstract.md) anahtar sözcükle işaretlemeye ek olarak, her örnek üyesi de [soyut](../language-reference/keywords/abstract.md) anahtar sözcüğüyle işaretlenir. Bu durumda `Shape` Ayrıca, tam adı yerine türün adını döndürmek için <xref:System.Object.ToString%2A?displayProperty=nameWithType> yöntemini geçersiz kılar. Ayrıca, arayanlara türetilmiş bir sınıfın bir örneğinin alanını ve çevresini kolayca almasına izin veren `GetArea` ve `GetPerimeter`iki statik üye tanımlar. Türetilmiş bir sınıfın bir örneğini bu yöntemlerin herhangi birine geçirdiğinizde, çalışma zamanı türetilmiş sınıfın yöntem geçersiz kılmasını çağırır.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#1)]

Ardından, belirli şekilleri temsil eden `Shape` bazı sınıfları türetebilirsiniz. Aşağıdaki örnek, `Triangle`, `Rectangle`ve `Circle`üç sınıfı tanımlar. Her biri, alanı ve çevresi hesaplamak için bu belirli bir şekil için benzersiz bir formül kullanır. Türetilmiş sınıflardan bazıları Ayrıca, temsil ettikleri şekle benzersiz olan `Rectangle.Diagonal` ve `Circle.Diameter`gibi özellikleri de tanımlar.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#2)]

Aşağıdaki örnek `Shape`türetilen nesneleri kullanır. `Shape` türetilen nesnelerden oluşan bir dizi oluşturur ve `Shape` sınıfının statik yöntemlerini çağırarak, return `Shape` özellik değerlerini sarmalayan şekilde çağırır. Çalışma zamanı türetilmiş türlerin geçersiz kılınan özelliklerinden değerleri alır. Örnek ayrıca dizideki her bir `Shape` nesnesini türetilmiş türüne yayınlar ve atama başarılı olursa `Shape`söz konusu alt sınıfının özelliklerini alır. 

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#3)]

## <a name="see-also"></a>Ayrıca bkz.

- [Sınıflar ve nesneler](../tour-of-csharp/classes-and-objects.md)
- [Devralma (C# Programlama Kılavuzu)](../programming-guide/classes-and-structs/inheritance.md)
