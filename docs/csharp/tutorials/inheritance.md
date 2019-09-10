---
title: DevralınanlarC#
description: C# Kitaplıklarda ve uygulamalarda devralma kullanmayı öğrenin.
author: rpetrusha
ms.author: ronpet
ms.date: 07/05/2018
ms.assetid: aeb68c74-0ea0-406f-9fbe-2ce02d47ef31
ms.openlocfilehash: 41377cb47836624160a5b402e0a85270b68eba4f
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850993"
---
# <a name="inheritance-in-c-and-net"></a>C# ve .NET içinde devralma

Bu öğretici, ' de C#devralma işlemini tanıtır. Devralma, belirli işlevleri (veri ve davranış) sağlayan bir temel sınıf tanımlamanızı ve bu işlevi devralıp geçersiz kılan türetilmiş sınıfları tanımlamanızı sağlayan nesne odaklı programlama dillerinin bir özelliğidir.

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

## <a name="background-what-is-inheritance"></a>Arka plan Devralma nedir?

*Devralma* , nesne odaklı programlamanın temel özniteliklerinden biridir. Bir üst sınıfın davranışını yeniden kullanan (devralan), genişleten veya değiştiren bir alt sınıf tanımlamanızı sağlar. Üyelerine devralınan sınıfa *temel sınıf*denir. Taban sınıfının üyelerini devralan sınıf *türetilmiş sınıf*olarak adlandırılır.

C#ve .NET yalnızca *tek devralma* desteği. Diğer bir deyişle, bir sınıf yalnızca tek bir sınıftan devralınabilir. Ancak, devralma geçişlidir ve bu, bir tür kümesi için devralma hiyerarşisi tanımlamanızı sağlar. Diğer `D` bir deyişle, türü, temel sınıf türünden `C` `A`devralan türünden devralan türünden devralabilir `B`. Devralma geçişli olduğundan, türü `A` üyeleri türü `D`için kullanılabilir.

Bir taban sınıfın tüm üyeleri türetilmiş sınıflar tarafından devralınmaz. Aşağıdaki Üyeler devralınmaz:

- Statik [oluşturucular](../programming-guide/classes-and-structs/static-constructors.md), bir sınıfın statik verilerini başlatır.

- Sınıfının yeni bir örneğini oluşturmak için çağırdığınız [örnek oluşturucular](../programming-guide/classes-and-structs/constructors.md). Her sınıfın kendi oluşturucuları tanımlanmalıdır.

- Çalışma zamanının atık toplayıcısı tarafından bir sınıfın örneklerini yok etmek için çağrılan [sonlandırıcılar](../programming-guide/classes-and-structs/destructors.md).

Bir temel sınıfın diğer tüm üyeleri türetilmiş sınıflar tarafından devralınırken, görünür olup olmadığı ve erişilebilirliğine bağlı olup olmadığı. Üyenin erişilebilirliği, türetilmiş sınıfların görünürlüğünü aşağıdaki gibi etkiler:

- [Özel](../language-reference/keywords/private.md) Üyeler yalnızca kendi temel sınıfında iç içe yerleştirilmiş türetilmiş sınıflarda görünür. Aksi takdirde, bunlar türetilmiş sınıflarda görünür değildir. Aşağıdaki örnekte, `A.B` öğesinden `A`türetilen ve `C` türeten `A`türetilmiş bir iç içe sınıftır. Özel `A.value` alan A.B. içinde görünür Ancak, `C.GetValue` yöntemden açıklamaları kaldırır ve örneği derlemeye çalışırsanız, CS0122 derleyici hatası üretir: "' A. Value ', koruma düzeyi nedeniyle erişilemez."

  [!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/private.cs#1)]

- [Korunan](../language-reference/keywords/protected.md) Üyeler yalnızca türetilmiş sınıflarda görülebilir.

- [İç](../language-reference/keywords/internal.md) Üyeler yalnızca temel sınıfla aynı derlemede bulunan türetilmiş sınıflarda görülebilir. Bunlar, temel sınıftan farklı bir derlemede bulunan türetilmiş sınıflarda görünür değildir.

- [Ortak](../language-reference/keywords/public.md) Üyeler türetilmiş sınıflarda görünür ve türetilmiş sınıf ' genel arabiriminin bir parçasıdır. Ortak devralınmış Üyeler, türetilmiş sınıfta tanımlandıklarında olduğu gibi çağrılabilir. Aşağıdaki örnekte, `A` sınıfı adlı `Method1`bir yöntemi tanımlar `A`ve `B` sınıf sınıfından devralır. Örnek daha sonra ' `Method1` `B`de bir örnek yöntemi gibi çağırır.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/basics.cs#1)]

Türetilmiş sınıflar, alternatif bir uygulama sağlayarak devralınan üyeleri de *geçersiz kılabilir* . Bir üyeyi geçersiz kılabilmek için, temel sınıftaki üyenin [sanal](../language-reference/keywords/virtual.md) anahtar sözcüğüyle işaretlenmesi gerekir. Varsayılan olarak, temel sınıf üyeleri olarak `virtual` işaretlenir ve geçersiz kılınamaz. Aşağıdaki örnek yaptığı için sanal olmayan bir üyeyi geçersiz kılma girişimi, CS0506: "\<üye > devralınan üye \<> üyesini geçersiz kılamaz; çünkü sanal, Özet veya geçersiz kılma olarak işaretlenmemiş.

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

Bazı durumlarda, türetilmiş bir sınıf temel sınıf uygulamasını geçersiz *kılmalıdır* . [Soyut](../language-reference/keywords/abstract.md) anahtar sözcükle işaretlenmiş temel sınıf üyeleri, türetilmiş sınıfların bunları geçersiz kılmasını gerektirir. Aşağıdaki örnek&lt;derlenmeye çalışıldığında derleyici hatası CS0534, "sınıf&gt; devralınmış soyut üye &lt;üyesini&gt;uygulamıyor", çünkü sınıf `B` şunu sağlamıyor için `A.Method1`uygulama.

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

Devralma yalnızca sınıflar ve arabirimler için geçerlidir. Diğer tür kategorileri (yapılar, temsilciler ve numaralandırmalar) devralmayı desteklemez. Bu kurallar nedeniyle, aşağıdaki örnekte olduğu gibi kodu derlemeye çalışmak derleyici hatası CS0527 üretir: Arabirim listesindeki "tür ' ValueType ' bir arabirim değil." Hata iletisi, bir yapının uyguladığı arabirimleri tanımlayabilseniz de devralmanın desteklenmediğini belirtir.

```csharp
using System;

public struct ValueStructure : ValueType // Generates CS0527.
{
}
```

## <a name="implicit-inheritance"></a>Örtük devralma

Tek devralmayla devraldıkları türlerin yanı sıra, .net tür sistemi 'ndeki tüm türler örtülü olarak devralınır <xref:System.Object> veya ondan türetilmiş bir tür. Ortak işlevselliği <xref:System.Object> her türlü tür için kullanılabilir.

Örtük devralmanın ne anlama geldiğini görmek için, yalnızca boş bir sınıf tanımı `SimpleClass`olan yeni bir sınıf tanımlayalim:

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass.cs#1)]

Daha sonra, `SimpleClass` türe ait üyelerin bir listesini almak için yansıma (Bu tür hakkında bilgi almak üzere bir türün meta verilerini incelemenizi sağlar) kullanabilirsiniz. Sınıfınızda `SimpleClass` herhangi bir üye tanımlamadıysanız, örnekteki çıkış gerçekten dokuz üyeye sahip olduğunu gösterir. Bu üyelerden biri, `SimpleClass` C# derleyici tarafından tür için otomatik olarak sağlanan parametresiz (veya varsayılan) bir oluşturucudur. Kalan sekiz, .net tür sistemindeki <xref:System.Object>tüm sınıfların ve arabirimlerin sonunda dolaylı olarak devraldığı tür üyesidir.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass.cs#2)]

<xref:System.Object> Sınıfından örtük devralma, bu yöntemleri `SimpleClass` sınıfı için kullanılabilir hale getirir:

- `ToString` Bir`SimpleClass` nesneyi dize gösterimine dönüştüren public yöntemi, tam nitelikli tür adını döndürür. Bu durumda, `ToString` yöntemi "simpleclass" dizesini döndürür.

- İki nesnenin eşitlik için test eden üç yöntem: ortak örnek `Equals(Object)` yöntemi, ortak statik `Equals(Object, Object)` Yöntem ve genel statik `ReferenceEquals(Object, Object)` yöntem. Varsayılan olarak, bu yöntemler başvuru eşitliği için test; diğer bir deyişle, eşit olması için iki nesne değişkeninin aynı nesneye başvurması gerekir.

- Karma koleksiyonlarda kullanılacak tür örneğine izin veren bir değeri hesaplayan ortak `GetHashCode` yöntemi.

- Türü temsil <xref:System.Type> `GetType` edenbirnesnedöndürenpublicyöntemi`SimpleClass` .

- Bir nesnenin <xref:System.Object.Finalize%2A> belleğinden önce yönetilmeyen kaynakları serbest bırakmak için tasarlanan Protected yöntemi çöp toplayıcı tarafından geri kazanılır.

- Geçerli nesnesinin <xref:System.Object.MemberwiseClone%2A> basit bir kopyasını oluşturan Protected yöntemi.

Örtük devralma nedeniyle, bir `SimpleClass` nesneden devralınan herhangi bir üyeyi, aslında yalnızca `SimpleClass` sınıfında tanımlanmış bir üye gibi çağırabilirsiniz. Örneğin, aşağıdaki örnek öğesinden `SimpleClass.ToString` `SimpleClass` <xref:System.Object>devralan yöntemini çağırır.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass2.cs#1)]

Aşağıdaki tabloda, içinde C# oluşturabileceğiniz türlerin kategorileri ve örtülü olarak devraldığı türler listelenmektedir. Her temel tür, devralma yoluyla örtülü olarak türetilmiş türlere farklı bir üye kümesi sağlar.

| Tür kategorisi | Örtülü olarak devralır                                                      |
| ------------- | ----------------------------------------------------------------------------- |
| sınıf         | <xref:System.Object>                                                          |
| struct        | <xref:System.ValueType>, <xref:System.Object>                                 |
| enum          | <xref:System.Enum>, <xref:System.ValueType>, <xref:System.Object>             |
| temsilci      | <xref:System.MulticastDelegate>, <xref:System.Delegate>, <xref:System.Object> |

## <a name="inheritance-and-an-is-a-relationship"></a>Devralma ve "bir" ilişkidir

Genellikle devralma, bir temel sınıf ve bir veya daha fazla türetilmiş sınıf arasındaki "bir", türetilmiş sınıfların temel sınıfın özelleşmiş sürümü olduğu bir veya daha fazla türetilmiş sınıf arasındaki ilişkiyi ifade etmek için kullanılır; türetilmiş sınıf, temel sınıfın bir türüdür. Örneğin, `Publication` sınıf herhangi bir türdeki yayını temsil eder `Book` ve ve `Magazine` sınıfları belirli yayın türlerini temsil eder.

> [!NOTE]
> Bir sınıf veya yapı, bir veya daha fazla arabirim uygulayabilir. Arabirim uygulaması genellikle tek devralma için geçici bir çözüm olarak veya yapılar ile devralma kullanmanın bir yolu olarak sunulurken, farklı bir ilişki ("bir" ilişki yapabilir) bir arabirim ile uygulama türü devralmayı. Bir arabirim, bir işlev alt kümesini tanımlar (örneğin, eşitlik için test etme, nesneleri karşılaştırma veya sıralama veya kültüre duyarlı ayrıştırma ve biçimlendirmeyi destekleme), arabirimin uygulama türleri için kullanılabilir hale getiren özellik.

"Bunun bir" olduğuna ve bu türün belirli bir örneğini oluşturma arasındaki ilişkiyi ifade eder. Aşağıdaki örnekte, `Automobile` üç benzersiz salt okuma özelliği olan bir sınıftır: `Make`, otomobil üreticisi , otomobil türü ve `Year`üretim yılı. `Model` Sınıfınız Ayrıca, bağımsız değişkenleri özellik değerlerine atanan bir oluşturucuya sahiptir ve `Automobile` sınıfı yerine `Automobile` örneği benzersiz bir şekilde tanımlayan <xref:System.Object.ToString%2A?displayProperty=nameWithType> bir dize oluşturmak için yöntemini geçersiz kılar. `Automobile`

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/is-a.cs#1)]

Bu durumda, belirli otomobil yaptığı ve modellerinin temsil edilebilmesi için devralmadan güvenmemelisiniz. Örneğin, Packard motor otomobil şirketi tarafından üretilen otomobil `Packard` 'leri temsil eden bir tür tanımlamanız gerekmez. Bunun yerine, aşağıdaki örnekte olduğu gibi, sınıf `Automobile` oluşturucusuna geçirilmiş uygun değerlerle bir nesne oluşturarak bunları temsil edebilirsiniz.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/is-a.cs#2)]

Bir iş-devralma temelli bir ilişki taban sınıfına ve temel sınıfa ek Üyeler ekleyen ya da temel sınıfta ek işlevsellik gerektiren türetilmiş sınıflara en iyi şekilde uygulanır.

## <a name="designing-the-base-class-and-derived-classes"></a>Temel sınıf ve türetilmiş sınıfları tasarlama

Bir temel sınıf ve türetilmiş sınıfları tasarlama sürecine bakalım. Bu bölümde, bir kitap, dergi, gazete, bir `Publication`günlük, makale vb. gibi her türlü yayını temsil eden bir temel sınıf tanımlayacaksınız. Ayrıca, öğesinden `Publication`türetilen bir `Book` sınıf tanımlayacaksınız. Örneğin, `Magazine`, ve `Newspaper` `Journal` gibi`Article`diğer türetilmiş sınıfları tanımlamak için örneği kolayca genişletebilirsiniz.

### <a name="the-base-publication-class"></a>Temel yayın sınıfı

`Publication` Sınıfınızı tasarlarken birkaç tasarım kararı vermeniz gerekir:

- Temel `Publication` sınıfınıza hangi Üyeler dahil edileceğini ve `Publication` üyelerin Yöntem uygulamaları sağlayıp sağlamadığını ya da türetilmiş sınıfları `Publication` için şablon görevi gören bir soyut temel sınıf olup olmadığını belirtir.

  Bu durumda, `Publication` sınıfı Yöntem uygulamaları sağlar. [Soyut temel sınıfları ve bunların türetilmiş sınıflarını tasarlama](#abstract) bölümü, türetilen sınıfların geçersiz kılınması gereken yöntemleri tanımlamak için soyut bir temel sınıf kullanan bir örnek içerir. Türetilmiş sınıflar, türetilmiş tür için uygun olan herhangi bir uygulamayı sağlamak için ücretsizdir.

  Kodu yeniden kullanma özelliği (yani, birden çok türetilmiş sınıflar temel sınıf yöntemlerinin bildirimini ve uygulamasını paylaşır ve bunları geçersiz kılmaları gerekmez) soyut olmayan taban sınıfların avantajlarından yararlanır. Bu nedenle, kendi kodunun bazı veya `Publication` en özel `Publication` türler tarafından paylaşılması olasılıklı Üyeler eklemeniz gerekir. Temel sınıf uygulamalarını verimli bir şekilde sağlayamadıysanız, temel sınıfta tek bir uygulama yerine türetilmiş sınıflarda büyük ölçüde özdeş üye uygulamaları sağlamak zorunda olacaksınız. Yinelenen kodu birden çok konumda sürdürme gereksinimi, olası hataların kaynağıdır.

  Her ikisi de kod yeniden kullanımını en üst düzeye çıkarmak ve mantıksal ve sezgisel bir devralma hiyerarşisi oluşturmak için, yalnızca tüm veya en çok `Publication` yayımlarda ortak olan verileri ve işlevleri sınıfa dahil ettiğinizden emin olmak istersiniz. Türetilmiş sınıflar daha sonra temsil ettikleri belirli yayın türlerine özgü olan üyeleri uygular.

- Sınıf hiyerarşinizin ne kadar uzaleceği. Yalnızca bir temel sınıf ve bir ya da daha fazla türetilmiş sınıf yerine üç veya daha fazla sınıf hiyerarşisi geliştirmek istiyor musunuz? Örneğin `Publication` , bir taban `Magazine` `Periodical`sınıfı olabilir, bu, ' ın temel sınıfı ve `Newspaper`' `Journal` dir.

  Örneğinizde, bir `Publication` sınıfın küçük hiyerarşisini ve tek bir türetilmiş sınıf olan ' i `Book`kullanacaksınız. Bu örneği, `Publication` `Magazine` ve `Article`gibi öğesinden türeten bir dizi ek sınıf oluşturmak için kolayca genişletebilirsiniz.

- Temel sınıfın örneğini oluşturma konusunda anlamlı olup olmadığı. Değilse, sınıfa [soyut](../language-reference/keywords/abstract.md) anahtar sözcüğünü uygulamanız gerekir. Aksi halde, `Publication` sınıfınızın sınıf oluşturucusu çağırarak örneklenebilir. Sınıf oluşturucusuna doğrudan çağrı tarafından `abstract` anahtar sözcükle işaretlenmiş bir sınıf örneği oluşturmak için bir girişimde bulunuldu, C# derleyici hata CS0144 oluşturuyor, "soyut sınıfın veya arabirimin bir örneği oluşturulamaz." Yansıma kullanarak sınıfın örneğini oluşturmaya yönelik bir girişim yapılırsa, yansıma yöntemi bir <xref:System.MemberAccessException>oluşturur.

  Varsayılan olarak, bir temel sınıf, sınıf oluşturucusu çağırarak örneklenebilir. Açıkça bir sınıf oluşturucusu tanımlamanız gerekmez. Temel sınıfın kaynak kodunda bir tane yoksa, C# derleyici otomatik olarak varsayılan (parametresiz) bir oluşturucu sağlar.

  Örneğinizdeki `Publication` sınıfı, örneklenemez hale gelecek şekilde bir [Özet](../language-reference/keywords/abstract.md) olarak işaretlersiniz.  Herhangi `abstract` `Book` `Journal`bir yöntemi olmayan bir sınıf, bu sınıfın birkaç somut sınıf (örneğin,) arasında paylaşılan bir soyut kavramı temsil ettiğini belirtir. `abstract`

- Türetilmiş sınıfların belirli üyelerin temel sınıf uygulamasını devralması gerekip gerekmediğini, temel sınıf uygulamasını geçersiz kılma seçeneğine sahip olup olmadığı veya bir uygulama sağlayıp sağlamamaları gerekir. Türetilmiş sınıfların bir uygulama sağlamasına zorlamak için [soyut](../language-reference/keywords/abstract.md) anahtar sözcüğünü kullanırsınız. Türetilmiş sınıfların bir temel sınıf yöntemini geçersiz kılmasına izin vermek için [sanal](../language-reference/keywords/virtual.md) anahtar sözcüğünü kullanırsınız. Varsayılan olarak, temel sınıfta tanımlanan Yöntemler geçersiz kılınabilir *değildir* .

 Sınıfın herhangi bir `abstract` yöntemi yoktur, ancak sınıfın kendisi olur `abstract`. `Publication`

- Türetilmiş bir sınıfın devralma hiyerarşisinde son sınıfı temsil edip etmediği ve kendisi ek türetilmiş sınıflar için temel sınıf olarak kullanılamaz. Varsayılan olarak, herhangi bir sınıf temel sınıf olarak görev yapabilir. Bir sınıfın herhangi bir ek sınıf için temel sınıf olarak işlev veremeyeceğini belirtmek için [Sealed](../language-reference/keywords/sealed.md) anahtar sözcüğünü uygulayabilirsiniz. "Sealed Type \<TypeName öğesinden türetilemez >", "korumalı bir sınıftan türetmeye çalışılıyor.

  Örneğinizdeki türetilmiş sınıfınızı olarak `sealed`işaretlersiniz.

Aşağıdaki örnek, `Publication` sınıfının kaynak kodunu ve `Publication.PublicationType` özelliği tarafından döndürülen bir `PublicationType` numaralandırmayı gösterir. Öğesinden <xref:System.Object>devraldığı üyelere ek olarak `Publication` , sınıfı aşağıdaki benzersiz üyeleri ve üye geçersiz kılmalarını tanımlar:

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/base-and-derived.cs#1)]

- Bir Oluşturucu

  `Publication` Sınıfıolduğundan,doğrudanaşağıdaki`abstract`örnek gibi koddan başlatılamaz:

  ```csharp
  var publication = new Publication("Tiddlywinks for Experts", "Fun and Games",
                                    PublicationType.Book);
  ```

  Ancak, `Book` sınıfının kaynak kodu gösterdiği gibi, örnek Oluşturucusu doğrudan türetilmiş sınıf oluşturucularından çağrılabilir.

- İki yayınla ilgili özellikler

  `Title`, <xref:System.String> oluşturucuyu`Publication` çağırarak değeri sağlanan salt okunurdur.

  `Pages`, yayının kaç tane sayfa <xref:System.Int32> olduğunu gösteren bir okuma-yazma özelliğidir. Değer adlı `totalPages`bir özel alanda depolanır. Pozitif bir sayı olmalı veya bir <xref:System.ArgumentOutOfRangeException> değer oluşturulmalıdır.

- Yayımcının ilgili üyeleri

  İki salt okuma özelliği `Publisher` ve. `Type` Değerler, başlangıçta `Publication` sınıf oluşturucusuna yapılan çağrı tarafından sağlanır.

- Yayınlamayla ilgili Üyeler

  İki yöntem `Publish` ve `GetPublicationDate`, yayınlama tarihini ayarlayın ve döndürür. Yöntemi, çağrıldığında `datePublished` için `true` bir `published` özel bayrak ayarlar ve kendisine geçirilen tarihi özel alana bağımsız değişken olarak atar. `Publish` `published` `datePublished` Yöntemi, `true`bayrak ise"NYP"dizesinivevarsaalanındeğerinidöndürür.`false` `GetPublicationDate`

- Telif hakkı ile ilgili Üyeler

  Yöntemi, telif hakkı sahibinin adını ve telif hakkı yılını bağımsız değişken olarak alır ve bunları `CopyrightName` ve `CopyrightDate` özelliklerine atar. `Copyright`

- `ToString` Yöntemi geçersiz kılma

  Bir tür <xref:System.Object.ToString%2A?displayProperty=nameWithType> yöntemi geçersiz kılmadığından, bir örneği diğerinden Farklılaştırmada çok az kullanılan, türün tam nitelikli adını döndürür. Sınıfı, özelliğinin`Title` değerini döndürecek şekilde geçersiz kılar <xref:System.Object.ToString%2A?displayProperty=nameWithType>. `Publication`

Aşağıdaki şekilde, taban `Publication` sınıfınız ve örtülü olarak devralınan <xref:System.Object> sınıfı arasındaki ilişki gösterilmektedir.

![Nesne ve yayın sınıfları](media/publication-class.jpg)

### <a name="the-book-class"></a>`Book` Sınıfı

Sınıfı `Book` , bir kitabı özelleşmiş bir yayın türü olarak temsil eder. Aşağıdaki örnek, `Book` sınıfının kaynak kodunu gösterir.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/base-and-derived.cs#2)]

Öğesinden `Publication`devraldığı üyelere ek olarak `Book` , sınıfı aşağıdaki benzersiz üyeleri ve üye geçersiz kılmalarını tanımlar:

- İki Oluşturucu

  İki `Book` Oluşturucu üç ortak parametreyi paylaşır. İki, *başlık* ve *Yayımcı*, `Publication` oluşturucunun parametrelerine karşılık gelir. Üçüncü, genelbir sabit `Author` özelliğe depolanan yazar. Bir Oluşturucu, `ISBN` Auto-Property içinde depolanan bir *ISBN* parametresi içerir.

  İlk Oluşturucu, diğer oluşturucuyu çağırmak için [this](../language-reference/keywords/this.md) anahtar sözcüğünü kullanır. Oluşturucu zincirleme, Oluşturucu tanımlamalarında ortak bir modeldir. Daha az parametreye sahip oluşturucular, oluşturucuyu en fazla parametre sayısıyla çağırırken varsayılan değerleri sağlar.

  İkinci Oluşturucu, başlığı ve yayımcı adını temel sınıf oluşturucusuna geçirmek için [temel](../language-reference/keywords/base.md) anahtar sözcüğünü kullanır. Kaynak kodunuzda bir taban sınıf oluşturucusuna açık bir çağrı yapmazsanız, C# derleyici otomatik olarak taban sınıfının varsayılan veya parametresiz oluşturucusuna bir çağrı sağlar.

- Nesnenin uluslararası standart defter `ISBN` numarasını, 10 veya 13 basamaklı bir sayıyı döndüren salt okunurdur bir özellik. `Book` ISBN `Book` oluşturuculardan birine bir bağımsız değişken olarak sağlanır. ISBN, derleyici tarafından otomatik olarak oluşturulan özel bir yedekleme alanında depolanır.

- Salt okunurdur `Author` özelliği. Yazar adı her iki `Book` Oluşturucu için bir bağımsız değişken olarak sağlanır ve özellikte depolanır.

- İki salt okuma fiyatına ilişkin özellikler `Price` ve. `Currency` Değerleri bir `SetPrice` Yöntem çağrısında bağımsız değişken olarak sağlanır. `Currency` Özelliği üç basamaklı ISO para birimi simgedir (örneğin, ABD Doları için USD). ISO para birimi sembolleri <xref:System.Globalization.RegionInfo.ISOCurrencySymbol%2A> özelliğinden alınabilir. Bu özelliklerin her ikisi de dışarıdan salt okunurdur, ancak her ikisi de `Book` sınıftaki kodla ayarlanabilir.

- `Price` `SetPrice` Ve`Currency` özelliklerinin değerlerini ayarlayan bir yöntemi. Bu değerler, aynı özelliklerle döndürülür.

- <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> <xref:System.Object.GetHashCode%2A> <xref:System.Object>Yöntemi (Devralındığı yer `Publication`) ve ve yöntemlerini (öğesinden devralınan) geçersiz kılar. `ToString`

  Geçersiz kılınmadıkça, <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> yöntemi başvuru eşitliği için test eder. Diğer bir deyişle, aynı nesneye başvurduklarında iki nesne değişkeninin eşit olduğu kabul edilir. Sınıfında, diğer yandan, aynı ISBN 'e sahip olmaları `Book` durumunda iki nesne eşit olmalıdır. `Book`

  <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> Yöntemi geçersiz kıldığınızda, verimli alma için, çalışma zamanının <xref:System.Object.GetHashCode%2A> öğeleri karma koleksiyonlara depolamak üzere kullandığı bir değer döndüren yöntemini de geçersiz kılmanız gerekir. Karma kodu, eşitlik için testle tutarlı bir değer döndürmelidir. İki <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> `ISBN` <xref:System.String.GetHashCode%2A> nesnenin ISBN özellikleri eşitse döndürülecek `true` şekilde geçersiz kılındığından, özelliği tarafından döndürülen dize yöntemini çağırarak hesaplanan karma kodu döndürün. `Book`

Aşağıdaki şekilde, `Book` sınıfı ve `Publication`temel sınıfı arasındaki ilişki gösterilmektedir.

![Yayın ve kitap sınıfları](media/book-class.jpg)

Artık bir `Book` nesnesi örneği oluşturabilir, hem benzersiz hem de devralınan üyelerini çağırabilir ve aşağıdaki örnekte gösterildiği gibi, türü `Publication` veya türü `Book`bir parametreyi bekleyen bir yönteme bağımsız değişken olarak geçirebilirsiniz.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/use-publication.cs#1)]

## <a name="designing-abstract-base-classes-and-their-derived-classes"></a>Soyut temel sınıfları ve bunların türetilmiş sınıflarını tasarlama
<a name="abstract"></a>

Önceki örnekte, türetilmiş sınıfların kod paylaşmasına izin veren bir dizi yöntem için uygulama sağlayan bir temel sınıf tanımladınız. Ancak çoğu durumda, temel sınıfın bir uygulama sağlaması beklenmez. Bunun yerine, temel sınıf *soyut yöntemleri*bildiren *soyut bir sınıftır* ; Her türetilmiş sınıfın uygulaması gereken üyeleri tanımlayan bir şablon görevi görür. Genellikle soyut bir temel sınıfta, her türetilmiş türün uygulanması o tür için benzersizdir. Sınıf, yayınlar için ortak işlevsellik uygulamaları sağlasa da, bir `Publication` nesnenin örneğini oluşturma konusunda hiçbir fikir olmadığından, bu sınıfı soyut anahtar sözcükle işaretlenir.

Örneğin, her kapatılan iki boyutlu geometrik şekil iki özellik içerir: alan, şeklin iç kapsamı; ve çevre ya da şeklin kenarları arasındaki uzaklık. Ancak, bu özelliklerin hesaplanma şekli, ancak tamamen belirli bir şekle bağlıdır. Örneğin, bir dairenin çevre (veya çevresi) hesaplama formülü, bir üçgenden farklıdır. Sınıfı yöntemler `abstract` içeren`abstract`birsınıftır. `Shape` Bu, türetilmiş sınıfların aynı işlevselliği paylaştığından, ancak bu türetilmiş sınıfların bu işlevselliği farklı şekilde uyguladığını gösterir.

Aşağıdaki örnek, adlı `Shape` bir soyut temel sınıfı tanımlar ve iki özelliği tanımlar: `Area` ve. `Perimeter` Sınıfı [soyut](../language-reference/keywords/abstract.md) anahtar sözcükle işaretlemeye ek olarak, her örnek üyesi de [soyut](../language-reference/keywords/abstract.md) anahtar sözcüğüyle işaretlenir. Bu durumda, `Shape` tam adı yerine türün <xref:System.Object.ToString%2A?displayProperty=nameWithType> adını döndürmek için yöntemini de geçersiz kılar. Ve bu, iki statik üye `GetArea` tanımlar ve `GetPerimeter`bu, çağıranların, türetilmiş bir sınıfın bir örneğinin alanını ve çevresini kolayca almasına imkan tanır. Türetilmiş bir sınıfın bir örneğini bu yöntemlerin herhangi birine geçirdiğinizde, çalışma zamanı türetilmiş sınıfın yöntem geçersiz kılmasını çağırır.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#1)]

Daha sonra belirli şekilleri temsil `Shape` eden bazı sınıfları türetebilirsiniz. Aşağıdaki örnek üç sınıfı `Triangle` `Rectangle`tanımlar,, ve `Circle`. Her biri, alanı ve çevresi hesaplamak için bu belirli bir şekil için benzersiz bir formül kullanır. Türetilmiş sınıflardan bazıları Ayrıca, `Rectangle.Diagonal` ve gibi özellikleri tanımlar ve `Circle.Diameter`temsil ettikleri şekle özeldir.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#2)]

Aşağıdaki örnek, öğesinden `Shape`türetilmiş nesneleri kullanır. Sınıfından türetilmiş `Shape` bir nesne dizisi oluşturur ve döndürülen `Shape` özellik değerlerini sarmalayan `Shape` sınıfın statik yöntemlerini çağırır. Çalışma zamanı türetilmiş türlerin geçersiz kılınan özelliklerinden değerleri alır. Örnek ayrıca dizideki her `Shape` bir nesneyi türetilmiş türüne yayınlar ve atama başarılı olursa, belirli bir `Shape`alt sınıfının özelliklerini alır. 

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#3)]

## <a name="see-also"></a>Ayrıca bkz.

- [Sınıflar ve nesneler](../tour-of-csharp/classes-and-objects.md)
- [Devralma (C# Programlama Kılavuzu)](../programming-guide/classes-and-structs/inheritance.md)
