---
title: "C'de Kalıtım #"
description: C# kitaplıklarında ve uygulamalarında devralma yı kullanmayı öğrenin.
ms.date: 07/05/2018
ms.technology: csharp-fundamentals
ms.assetid: aeb68c74-0ea0-406f-9fbe-2ce02d47ef31
ms.openlocfilehash: b72badb7833e018dfcbf5d2583b17f17c800c382
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156759"
---
# <a name="inheritance-in-c-and-net"></a>C# ve .NET içinde devralma

Bu öğretici c# kalıtım size tanıttı. Devralma, belirli işlevsellik (veri ve davranış) sağlayan bir taban sınıf tanımlamanızı ve bu işlevselliği devralan veya geçersiz kılan türemiş sınıfları tanımlamanızı sağlayan nesne yönelimli programlama dillerinin bir özelliğidir.

## <a name="prerequisites"></a>Önkoşullar

Bu öğretici, .NET Core SDK'yı yüklediğinizi varsayar. İndirmek için [.NET Çekirdek İndirmeler](https://dotnet.microsoft.com/download) sayfasını ziyaret edin. Ayrıca bir kod düzenleyicisi gerekir. Bu öğretici [Visual Studio Code](https://code.visualstudio.com)kullanır, ancak seçtiğiniz herhangi bir kod editörü kullanabilirsiniz.

## <a name="running-the-examples"></a>Örnekleri çalıştırma

Bu öğreticideki örnekleri oluşturmak ve çalıştırmak için komut satırındaki [dotnet](../../core/tools/dotnet.md) yardımcı programını kullanırsınız. Her örnek için aşağıdaki adımları izleyin:

1. Örneği depolamak için bir dizin oluşturun.
1. Yeni bir .NET Core projesi oluşturmak için komut isteminde [dotnet yeni konsol](../../core/tools/dotnet-new.md) komutunu girin.
1. Örnekteki kodu kopyalayıp kod düzenleyicinize yapıştırın.
1. Projenin bağımlılıklarını yüklemek veya geri yüklemek için komut satırından [dotnet geri yükleme](../../core/tools/dotnet-restore.md) komutunu girin.

  [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

1. Örneği derlemek ve yürütmek için [dotnet çalıştır](../../core/tools/dotnet-run.md) komutunu girin.

## <a name="background-what-is-inheritance"></a>Arka Plan: Kalıtım nedir?

*Kalıtım* nesne yönelimli programlamanın temel özelliklerinden biridir. Bir üst sınıfın davranışını yeniden kullanan (devralan), genişleten veya değiştiren bir alt sınıf tanımlamanıza olanak tanır. Üyeleri devralınan *sınıfa taban sınıf*denir. Taban sınıfın üyelerini devralan *sınıfa türemiş sınıf*denir.

C# ve .NET yalnızca *tek kalıtım desteği.* Diğer bir diğer taraftan, bir sınıf yalnızca tek bir sınıftan devralınabilir. Ancak, devralma geçişli, hangi türleri kümesi için bir devralma hiyerarşisi tanımlamak için izin verir. Başka bir deyişle, `D` tür, `C`taban sınıf türünden `B` `A`devralan türden , türden devralabilir. Kalıtım geçişli olduğundan, tür `A` üyeleri türüne kullanılabilir. `D`

Bir taban sınıfın tüm üyeleri türetilmiş sınıflar tarafından devralınır. Aşağıdaki üyeler ekideğildir:

- Bir sınıfın statik verilerini ilk olarak alan [statik yapıcılar.](../programming-guide/classes-and-structs/static-constructors.md)

- Sınıfın yeni bir örneğini oluşturmak için çağırdığınız [örnek oluşturucular.](../programming-guide/classes-and-structs/constructors.md) Her sınıf kendi oluşturucularını tanımlamalıdır.

- [Finalizers](../programming-guide/classes-and-structs/destructors.md), bir sınıfın örneklerini yok etmek için runtime çöp toplayıcı tarafından denir.

Bir taban sınıfın diğer tüm üyeleri türemiş sınıflar tarafından devralınırken, görünür olup olmadıkları erişilebilirliklerine bağlıdır. Bir üyenin erişilebilirliği, türetilmiş sınıflar için görünürlüğünü aşağıdaki gibi etkiler:

- [Özel](../language-reference/keywords/private.md) üyeler yalnızca taban sınıflarında iç içe olan türemiş sınıflarda görünür. Aksi takdirde, türemiş sınıflarda görünmezler. Aşağıdaki örnekte, `A.B` 'den türeyen ve `A` `C` .'den `A`türeyen iç içe bir sınıftır. Özel `A.value` alan A.B.'de görülebilir. Ancak, yorumları `C.GetValue` yöntemden kaldırır ve örneği derlemeye çalışırsanız, cs0122 derleyici hatası üretir: "'A.value' koruma düzeyi nedeniyle erişilemez."

  [!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/private.cs#1)]

- [Korumalı](../language-reference/keywords/protected.md) üyeler yalnızca türemiş sınıflarda görülebilir.

- [İç](../language-reference/keywords/internal.md) üyeler yalnızca taban sınıfla aynı derlemede bulunan türemiş sınıflarda görülebilir. Taban sınıftan farklı bir derlemede bulunan türemiş sınıflarda görünmezler.

- [Türemiş](../language-reference/keywords/public.md) sınıflarda genel üyeler görünür ve türetilmiş sınıfın ortak arabiriminin bir parçasıdır. Genel olarak devralınan üyeler, türemiş sınıfta tanımlanmış gibi çağrılabilir. Aşağıdaki örnekte, `A` sınıf adlı `Method1`bir yöntem `B` tanımlar ve `A`sınıf sınıftan devralır. Örnek daha `Method1` sonra bir örnek yöntemi `B`sanki çağırır.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/basics.cs#1)]

Türetilen sınıflar, alternatif bir uygulama sağlayarak devralınan üyeleri de *geçersiz kılabilir.* Bir üyeyi geçersiz kılabilmesi için, taban sınıftaki üyenin [sanal](../language-reference/keywords/virtual.md) anahtar kelimeyle işaretlemesi gerekir. Varsayılan olarak, taban sınıf üyeleri `virtual` olarak işaretlenmemiştir ve geçersiz kılınmaz. Aşağıdaki örnekte olduğu gibi sanal olmayan bir üyeyi geçersiz kılmaya çalışmak, cs0506 derleyici hatası oluşturur: "\<üye>, sanal, soyut veya geçersiz kılınma olarak işaretlenmediği için devralınan üye \<> geçersiz kılamaz.

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

Bazı durumlarda, türetilmiş bir sınıfın taban sınıf uygulamasını geçersiz kılması *gerekir.* [Soyut](../language-reference/keywords/abstract.md) anahtar sözcüğüyle işaretlenmiş taban sınıf üyeleri, türemiş sınıfların bunları geçersiz kılmasını gerektirir. Aşağıdaki örneği derlemeye çalışırken derleyici hatası CS0534&lt;oluşturur, " sınıf&gt; kalıtsal &lt;&gt;soyut üye `B` üye "uygulamaz, çünkü sınıf için `A.Method1`hiçbir uygulama sağlar .

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

Kalıtım yalnızca sınıflar ve arabirimler için geçerlidir. Diğer tür kategorileri (structs, delegates ve enums) devralma desteklemez. Bu kurallar nedeniyle, aşağıdaki örnek gibi kod derlemek için çalışırken derleyici hatası CS0527 üretir: "Tür 'ValueType' arayüz listesinde bir arayüz değildir." Hata iletisi, bir yapının uyguladığı arabirimleri tanımlayabildiğiniz halde kalıtımın desteklenmediğini gösterir.

```csharp
using System;

public struct ValueStructure : ValueType // Generates CS0527.
{
}
```

## <a name="implicit-inheritance"></a>Örtülü miras

Tek bir devralma yoluyla devralabilecekleri tüm türlerin yanı sıra, .NET <xref:System.Object> türü sistemindeki tüm türler örtülü olarak devralır veya ondan türetilen bir tür. Ortak işlevselliği <xref:System.Object> herhangi bir tür için kullanılabilir.

Örtük devralmanın ne anlama geldiğini görmek için, `SimpleClass`sadece boş bir sınıf tanımı olan yeni bir sınıf tanımlayalım:

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass.cs#1)]

Daha sonra, `SimpleClass` türe ait üyelerin listesini almak için yansımayı (bu tür hakkında bilgi almak için bir türün meta verilerini incelemenize olanak tanır) kullanabilirsiniz. Sınıfınızda herhangi bir üye tanımlamamış olsanız `SimpleClass` da, örnekten elde edilen çıktı, aslında dokuz üyesi olduğunu gösterir. Bu üyelerden biri, C# derleyicisi tarafından `SimpleClass` tür için otomatik olarak sağlanan parametresiz (veya varsayılan) bir oluşturucudur. Geri kalan sekiz <xref:System.Object>üye, .NET türü sistemindeki tüm sınıfların ve arabirimlerin sonuçta dolaylı olarak devraldığı türdedir.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass.cs#2)]

Sınıftan <xref:System.Object> örtülü devralma bu yöntemleri `SimpleClass` sınıf için kullanılabilir hale getirir:

- Bir `ToString` `SimpleClass` nesneyi dize gösterimine dönüştüren ortak yöntem, tam nitelikli tür adını döndürür. Bu durumda, `ToString` yöntem "SimpleClass" dizesini döndürür.

- İki nesnenin eşitliğini sınayan üç yöntem: genel `Equals(Object)` örnek `Equals(Object, Object)` yöntemi, genel `ReferenceEquals(Object, Object)` statik yöntem ve ortak statik yöntem. Varsayılan olarak, bu yöntemler başvuru eşitliği için test; diğer bir şey, eşit olmak için iki nesne değişkeninin aynı nesneye başvurması gerekir.

- Türdeki `GetHashCode` bir örneğinin hashed koleksiyonlarında kullanılmasına izin veren bir değeri hesaplayan ortak yöntem.

- Türü `GetType` temsil eden bir <xref:System.Type> nesneyi döndüren ortak yöntem. `SimpleClass`

- Bir <xref:System.Object.Finalize%2A> nesnenin belleği çöp toplayıcı tarafından geri önce yönetilmeyen kaynakları serbest bırakmak için tasarlanmış korumalı yöntem.

- Geçerli <xref:System.Object.MemberwiseClone%2A> nesnenin sığ bir klon oluşturur korumalı yöntem.

Örtük devralma nedeniyle, bir nesneden devralınan herhangi bir `SimpleClass` üyeyi, sanki `SimpleClass` sınıfta tanımlanmış bir üyeymiş gibi arayabilirsiniz. Örneğin, aşağıdaki örnekten `SimpleClass.ToString` `SimpleClass` devralınan yöntemi <xref:System.Object>çağırır.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass2.cs#1)]

Aşağıdaki tabloda C#'da oluşturabileceğiniz türler ve bunların örtülü olarak devraldıkları türler listelenerilmiştir. Her taban türü, örtülü olarak türetilmiş türlere devralma yoluyla farklı bir üye kümesi sağlar.

| Tür kategorisi | Dolaylı olarak devralır                                                      |
| ------------- | ----------------------------------------------------------------------------- |
| sınıf         | <xref:System.Object>                                                          |
| struct         | <xref:System.ValueType>, <xref:System.Object>                                 |
| enum          | <xref:System.Enum>, <xref:System.ValueType>, <xref:System.Object>             |
| temsilci      | <xref:System.MulticastDelegate>, <xref:System.Delegate>, <xref:System.Object> |

## <a name="inheritance-and-an-is-a-relationship"></a>Miras ve "bir" ilişkisi

Normalde, devralma, türemiş sınıfların taban sınıfın özel sürümleri olduğu bir taban sınıf ile bir veya daha fazla türetilmiş sınıf arasındaki "bir" ilişkiyi ifade etmek için kullanılır; türemiş sınıf taban sınıfın bir türüdür. Örneğin, `Publication` sınıf her türlü yayını temsil eder `Book` `Magazine` ve sınıflar belirli yayın türlerini temsil eder.

> [!NOTE]
> Bir sınıf veya yapı bir veya daha fazla arabirim uygulayabilir. Arabirim uygulaması genellikle tek bir devralma için bir geçici çözüm olarak veya structs ile kalıtım kullanmanın bir yolu olarak sunulsa da, bir arayüz ve uygulama türü arasında farklı bir ilişki ("yapabilirim" ilişkisi) ifade etmek için tasarlanmıştır Devralma. Arabirim, arabirimin uygulama türlerine sunacağı bir işlev alt kümesini (eşitlik için sınama, nesneleri karşılaştırma veya sıralama veya kültüre duyarlı ayrıştırma ve biçimlendirmeyi destekleme gibi) tanımlar.

"A" da bir tür ve bu tür belirli bir anlık arasındaki ilişkiyi ifade ettiğini unutmayın. Aşağıdaki örnekte, `Automobile` üç benzersiz salt okunur özelliği olan `Make`bir sınıftır: , otomobil üreticisi; `Model`, otomobil türü; ve `Year`, üretim yılı. Sınıfınızın `Automobile` ayrıca, bağımsız değişkenleri özellik değerlerine atanmış bir oluşturucusu vardır ve <xref:System.Object.ToString%2A?displayProperty=nameWithType> `Automobile` `Automobile` sınıf yerine örneği benzersiz olarak tanımlayan bir dize oluşturmak için yöntemi geçersiz kılar.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/is-a.cs#1)]

Bu durumda, belirli araba yapar ve modelleri temsil etmek için miras güvenmemelidir. Örneğin, Packard Motor Car Company `Packard` tarafından üretilen otomobilleri temsil edecek bir tür tanımlamanız gerekmez. Bunun yerine, aşağıdaki örnekte `Automobile` olduğu gibi, sınıf oluşturucusuna geçirilen uygun değerlere sahip bir nesne oluşturarak onları temsil edebilirsiniz.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/is-a.cs#2)]

Devralmaya dayalı bir ilişki, taban sınıfa ve taban sınıfa ek üye ekleyen veya taban sınıfta bulunmayan ek işlevsellik gerektiren türemiş sınıflara en iyi şekilde uygulanır.

## <a name="designing-the-base-class-and-derived-classes"></a>Taban sınıf ve türemiş sınıfların tasarımı

Bir taban sınıf ve türetilmiş sınıflar tasarlama sürecine bakalım. Bu bölümde, kitap, dergi, gazete, dergi, `Publication`makale vb. gibi her türlü yayını temsil eden bir taban sınıf tanımlarsınız. Ayrıca, `Publication`'den `Book` türeyen bir sınıf tanımlarsınız. Örneği `Magazine`kolayca, " , `Journal`, `Newspaper`ve `Article`.

### <a name="the-base-publication-class"></a>Taban Yayın sınıfı

Sınıfınızı `Publication` tasarlarken, birkaç tasarım kararı almanız gerekir:

- Taban `Publication` sınıfınıza hangi üyelerin dahil edilip edilmeyeceği ve üyelerin yöntem uygulamaları sağlayıp sağlamadığı `Publication` veya türetilmiş sınıfları için şablon görevi sunan soyut bir taban sınıf olup olmadığı. `Publication`

  Bu durumda, `Publication` sınıf yöntem uygulamaları sağlayacaktır. [Soyut taban sınıfları ve bunların türemiş sınıfları](#abstract) tasarlama bölümü, türeyen sınıfların geçersiz kılmaları gereken yöntemleri tanımlamak için soyut bir taban sınıfı kullanan bir örnek içerir. Türemiş sınıflar, türetilmiş türe uygun herhangi bir uygulama sağlamakta serbesttir.

  Kodu yeniden kullanabilme (diğer bir şekilde, birden çok türetilmiş sınıf, taban sınıf yöntemlerinin bildirimini ve uygulanmasını paylaşır ve bunları geçersiz kılmaya gerek yoktur) soyut olmayan temel sınıfların bir avantajıdır. Bu nedenle, kodlarının `Publication` bazı veya en özel türler tarafından paylaşılmak olası olup olmadığını üyeler eklemeniz `Publication` gerekir. Taban sınıf uygulamalarını verimli bir şekilde sağlayamazsanız, taban sınıfta tek bir uygulama yerine türemiş sınıflarda büyük ölçüde aynı üye uygulamaları sağlamak zorunda kalırsınız. Yinelenen kodu birden çok konumda tutma gereksinimi, olası bir hata kaynağıdır.

  Hem kod yeniden en üst düzeye çıkarmak hem de mantıksal ve sezgisel bir `Publication` devralma hiyerarşisi oluşturmak için, sınıfa yalnızca tüm veya çoğu yayında ortak olan verileri ve işlevselliği eklediğinizden emin olmak istersiniz. Türemiş sınıflar daha sonra temsil ettikleri belirli yayın türlerine özgü üyeleri uygular.

- Sınıf hiyerarşinizi ne kadar genişletir. Basit bir taban sınıf ve bir veya daha fazla türemiş sınıf yerine üç veya daha fazla sınıftan oluşan bir hiyerarşi geliştirmek istiyor musunuz? `Publication` Örneğin, sırayla bir taban `Periodical`sınıf olan `Magazine`bir taban sınıf `Journal` `Newspaper`olabilir , ve .

  Örneğin, bir `Publication` sınıfın küçük hiyerarşisini ve tek bir türetilmiş `Book`sınıfın. Örneğin, örneğinden `Publication` `Magazine` türeyen bir dizi ek sınıf oluşturmak için `Article`örneği kolayca genişletebilirsiniz.

- Taban sınıfanlık mantıklı olup olmadığını. Yoksa, [özet](../language-reference/keywords/abstract.md) anahtar sözcüğü sınıfa uygulamalısınız. Aksi takdirde, sınıfınız `Publication` sınıf oluşturucusu çağırarak anında kullanılabilir. `abstract` Anahtar kelimeyle işaretlenmiş bir sınıfı sınıf oluşturucuya doğrudan çağrı yaparak anında bir araya getirmeye çalışırsa, C# derleyicisi CS0144 hatası oluşturur: "Soyut sınıfın veya arabirimin bir örneğini oluşturamaz." Yansıma kullanılarak sınıfı anında bir hale getirmeye çalışırsa, yansıma yöntemi bir <xref:System.MemberAccessException>.

  Varsayılan olarak, bir taban sınıf, sınıf oluşturucusu çağırArak anında kullanılabilir. Bir sınıf oluşturucusu açıkça tanımlamanız gerekmez. Temel sınıfın kaynak kodunda bir tane yoksa, C# derleyicisi otomatik olarak varsayılan (parametresiz) bir oluşturucu sağlar.

  Örneğin, `Publication` sınıfı anlık olarak işaretlenememesi için [soyut](../language-reference/keywords/abstract.md) olarak işaretlersiniz.  Herhangi `abstract` `abstract` bir yöntem olmayan bir sınıf, bu sınıfın birkaç somut sınıf `Book`arasında `Journal`paylaşılan soyut bir kavramı temsil ettiğini gösterir (bir, gibi).

- Türemiş sınıfların belirli üyelerin taban sınıf uygulamasını devralması gerekip gerekmediği, taban sınıf uygulamasını geçersiz kılma seçeneğiolup olmadığı veya bir uygulama sağlamaları gerekip gerekmediği. Bir uygulama sağlamak için türetilen sınıfları zorlamak için [soyut](../language-reference/keywords/abstract.md) anahtar sözcük kullanırsınız. Türemiş sınıfların taban sınıf yöntemini geçersiz kılmasına izin vermek için [sanal](../language-reference/keywords/virtual.md) anahtar sözcüğü kullanırsınız. Varsayılan olarak, taban sınıfta tanımlanan yöntemler geçersiz *kılınmaz.*

 Sınıfın `Publication` herhangi bir `abstract` yöntemi yoktur, ancak `abstract`sınıfın kendisi.

- Türetilen bir sınıfın devralma hiyerarşisinde son sınıfı temsil edip etmediği ve kendisi ek türemiş sınıflar için taban sınıf olarak kullanılamayacak. Varsayılan olarak, herhangi bir sınıf bir taban sınıf olarak hizmet verebilir. [Mühürlü](../language-reference/keywords/sealed.md) anahtar sözcüğü, bir sınıfın herhangi bir ek sınıf için taban sınıf olarak hizmet veremeyeceğini belirtmek için uygulayabilirsiniz. CS0509 tarafından oluşturulan mühürlü bir sınıftan türemeye çalışan "mühürlü \<tür Adı>" elde edilemez.

  Örneğin, türemiş sınıfınızı `sealed`.

Aşağıdaki örnek, `Publication` sınıfın kaynak kodunun yanı sıra `PublicationType` özellik tarafından döndürülen bir `Publication.PublicationType` numaralandırmayı da gösterir. <xref:System.Object>Sınıf, devraldığı üyelere ek olarak aşağıdaki benzersiz üyeleri tanımlar ve üye geçersiz `Publication` kılar:

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/base-and-derived.cs#1)]

- Bir yapıcı

  Sınıf `Publication` olduğu `abstract`için, aşağıdaki örnekgibi doğrudan koddan anında alınamaz:

  ```csharp
  var publication = new Publication("Tiddlywinks for Experts", "Fun and Games",
                                    PublicationType.Book);
  ```

  Ancak, `Book` örnek oluşturucu, sınıfın kaynak kodunun gösterdiği gibi, doğrudan türemiş sınıf oluşturucularından çağrılabilir.

- Yayınla ilgili iki özellik

  `Title`değeri yapıcıyı <xref:System.String> arayarak sağlanan salt okunur `Publication` bir özelliktir.

  `Pages`yayının toplam <xref:System.Int32> kaç sayfaya sahip olduğunu gösteren bir okuma-yazma özelliğidir. Değer, ". `totalPages` Pozitif bir sayı olmalı <xref:System.ArgumentOutOfRangeException> veya bir atılmalıdır.

- Yayıncıyla ilgili üyeler

  Salt okunur iki `Publisher` özellik `Type`ve . Değerler özgün olarak `Publication` sınıf oluşturucuya çağrı tarafından sağlanır.

- Yayımlama ile ilgili üyeler

  Ve `GetPublicationDate`, `Publish` ayarve yayın tarihini döndürün. Yöntem, `Publish` `published` `true` çağrıldığı zamana özel bir bayrak ayarlar ve özel `datePublished` alana bağımsız değişken olarak geçen tarihi atar. `GetPublicationDate` Yöntem, `published` bayrak `false`ise "NYP" dizesini ve varsa `datePublished` alanın değerini `true`döndürür.

- Telif hakkı yla ilgili üyeler

  Yöntem, `Copyright` telif hakkı sahibinin adını ve telif hakkının yılını bağımsız `CopyrightName` değişken `CopyrightDate` olarak alır ve bunları bağımsız değişkenlere ve mülklere atar.

- `ToString` Yöntemin geçersiz kılındırı

  Bir tür <xref:System.Object.ToString%2A?displayProperty=nameWithType> yöntemi geçersiz kılmazsa, bir örneği diğerinden ayırt etmede çok az kullanılan türün tam nitelikli adını döndürür. Sınıf `Publication` özelliğin <xref:System.Object.ToString%2A?displayProperty=nameWithType> değerini `Title` döndürmek için geçersiz kılar.

Aşağıdaki şekil, taban `Publication` sınıfınızla örtülü olarak devralınan <xref:System.Object> sınıfı arasındaki ilişkiyi göstermektedir.

![Nesne ve Yayın sınıfları](media/publication-class.jpg)

### <a name="the-book-class"></a>Sınıf `Book`

Sınıf, `Book` bir kitabı özel bir yayın türü olarak temsil eder. Aşağıdaki örnek, `Book` sınıfın kaynak kodunu gösterir.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/base-and-derived.cs#2)]

`Publication`Sınıf, devraldığı üyelere ek olarak aşağıdaki benzersiz üyeleri tanımlar ve üye geçersiz `Book` kılar:

- İki yapıcı

  İki `Book` oluşturucu üç ortak parametreyi paylaşır. İki, *başlık* ve *yayıncı,* `Publication` yapıcı parametrelerine karşılık gelir. Üçüncü *yazar,* bir kamu değişmez `Author` özelliği saklanır. Bir `ISBN` oluşturucu, otomatik özellikte depolanan bir *isbn* parametresi içerir.

  İlk oluşturucu, [diğer](../language-reference/keywords/this.md) oluşturucuyu aramak için bu anahtar sözcüğü kullanır. Yapıcı zincirleme, yapıcıları tanımlamada yaygın bir desendir. Daha az parametreye sahip yapıcılar, en fazla sayıda parametreyle yapıcıyı ararken varsayılan değerler sağlar.

  İkinci oluşturucu, başlığı ve yayımcı adını taban sınıf oluşturucuya geçirmek için [temel](../language-reference/keywords/base.md) anahtar sözcüğü kullanır. Kaynak kodunuzdaki bir taban sınıf oluşturucuya açık bir çağrı yapmazsanız, C# derleyicisi temel sınıfın varsayılan veya parametresiz oluşturucusuna otomatik olarak çağrı sağlar.

- Nesnenin `Book` Uluslararası `ISBN` Standart Kitap Numarasını, benzersiz 10 veya 13 basamaklı bir sayıyı döndüren salt okunur özellik. `Book` ISBN, oluşturuculardan birine bağımsız değişken olarak verilir. ISBN, derleyici tarafından otomatik olarak oluşturulan özel bir destek alanında depolanır.

- Salt `Author` okunur bir özellik. Yazar adı, her iki oluşturucuya da `Book` bağımsız değişken olarak verilir ve özellikte depolanır.

- Salt okunur fiyatla ilgili `Price` iki `Currency`özellik ve . Onların değerleri bir `SetPrice` yöntem çağrısında bağımsız değişken olarak sağlanır. Özellik `Currency` üç haneli ISO para birimi sembolüdür (örneğin, ABD doları için USD). ISO para birimi sembolleri <xref:System.Globalization.RegionInfo.ISOCurrencySymbol%2A> tesisten alınabilir. Bu özelliklerin her ikisi de dışarıdan salt okunur, ancak `Book` her ikisi de sınıfta kod tarafından ayarlanabilir.

- Özelliklerin `SetPrice` `Price` ve `Currency` değerlerin değerlerini belirleyen bir yöntem. Bu değerler aynı özellikler tarafından döndürülür.

- `ToString` Yönteme geçersiz kılar `Publication`(kalıtsal) ve <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> <xref:System.Object.GetHashCode%2A> yöntemleri <xref:System.Object>(devralınan).

  Geçersiz kılınmadığı sürece, <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> yöntem başvuru eşitliği için test edilir. Diğer bir arada, aynı nesneye başvururlarsa, iki nesne değişkeni eşit olarak kabul edilir. `Book` Sınıfta, diğer taraftan, iki `Book` nesne aynı ISBN varsa eşit olmalıdır.

  <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> Yöntemi geçersiz kaldığınızda, çalışma zamanının <xref:System.Object.GetHashCode%2A> maddeleri verimli alma için hashed koleksiyonlarında depolamak için kullandığı bir değeri döndüren yöntemi de geçersiz kılmanız gerekir. Karma kod, eşitlik testiyle tutarlı bir değer döndürmelidir. <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> `true` İki `Book` nesnenin ISBN özellikleri eşitse, <xref:System.String.GetHashCode%2A> `ISBN` özellik tarafından döndürülen dize yöntemini arayarak hesaplanan karma kodu döndürür.

Aşağıdaki şekil `Book` sınıf ve `Publication`, taban sınıf arasındaki ilişkiyi göstermektedir.

![Yayın ve Kitap dersleri](media/book-class.jpg)

Artık bir `Book` nesneyi anında anlayabilir, hem benzersiz hem de devralınan üyelerini çağırabilir ve aşağıdaki örnekte `Publication` görüldüğü `Book`gibi, bir tür veya tür parametresi bekleyen bir yönteme bağımsız değişken olarak geçirebilirsiniz.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/use-publication.cs#1)]

## <a name="designing-abstract-base-classes-and-their-derived-classes"></a>Soyut taban sınıfları ve bunların türemiş sınıflarını tasarlama
<a name="abstract"></a>

Önceki örnekte, türemiş sınıfların kodu paylaşmasına izin vermek için bir dizi yöntem için uygulama sağlayan bir taban sınıf tanımladınız. Ancak çoğu durumda, taban sınıfın bir uygulama sağlaması beklenmez. Bunun yerine, taban sınıf *soyut yöntemleri*bildiren soyut bir *sınıftır;* her türetilmiş sınıfın uygulaması gereken üyeleri tanımlayan bir şablon olarak hizmet vermektedir. Genellikle soyut bir taban sınıfında, türetilen her türün uygulanması bu türe özgüdür. Sınıf yayınlarda ortak işlevsellik uygulamaları sağlasa da, bir `Publication` nesneyi anında anımsamanın hiçbir anlamı olmadığından sınıfı soyut anahtar sözcükle işaretlediniz.

Örneğin, her kapalı iki boyutlu geometrik şekil iki özellik içerir: alan, şeklin iç kapsamı; ve çevre, ya da şeklin kenarları boyunca mesafe. Ancak, bu özelliklerin hesaplanma şekli tamamen belirli şekle bağlıdır. Örneğin, bir dairenin çevresini (veya çevresini) hesaplama formülü, bir üçgeninkinden farklıdır. Sınıf `Shape` yöntemleri `abstract` olan `abstract` bir sınıftır. Bu, türetilmiş sınıfların aynı işlevselliği paylaştığını, ancak bu türemiş sınıfların bu işlevselliği farklı şekilde uyguladığını gösterir.

Aşağıdaki örnek, iki özelliği tanımlayan `Shape` soyut bir taban `Area` `Perimeter`sınıf tanımlar: ve . Sınıfı [soyut](../language-reference/keywords/abstract.md) anahtar kelimeyle işaretlemenin yanı sıra, her örnek üye [soyut](../language-reference/keywords/abstract.md) anahtar kelimeyle de işaretlenir. Bu durumda, `Shape` aynı zamanda <xref:System.Object.ToString%2A?displayProperty=nameWithType> tam nitelikli adı yerine türün adını döndürmek için yöntemi geçersiz kılar. Ve iki statik üye `GetArea` tanımlar `GetPerimeter`ve arayanların türemiş bir sınıfın bir örneğinin alanını ve çevresini kolayca almasına olanak sağlar. Türetilmiş bir sınıfın bir örneğini bu yöntemlerden herhangi biri için geçtiğinde, çalışma zamanı türemiş sınıfın yöntem geçersiz kılınmasını çağırır.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#1)]

Daha sonra belirli şekilleri `Shape` temsil eden bazı sınıflar elde edebilirsiniz. Aşağıdaki örnekte üç sınıf `Triangle` `Rectangle`tanımlanır, `Circle`, , ve . Her alan ve çevre hesaplamak için belirli bir şekil için benzersiz bir formül kullanır. Türetilen sınıflardan bazıları, temsil `Rectangle.Diagonal` ettikleri `Circle.Diameter`şekle özgü olan ve bu özellikleri de tanımlar.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#2)]

Aşağıdaki örnekte `Shape`türetilen nesneler kullanır. Türetilen bir dizi nesneyi anında `Shape` alır ve geri dönüş `Shape` `Shape` özelliği değerlerini saran sınıfın statik yöntemlerini çağırır. Çalışma zamanı, türemiş türlerin geçersiz kılınan özelliklerinden değerleri alır. Örnek ayrıca dizideki `Shape` her nesneyi türetilmiş türüne atar ve döküm başarılı olursa, `Shape`o belirli alt sınıfın özelliklerini alır.

[!code-csharp[Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#3)]

## <a name="see-also"></a>Ayrıca bkz.

- [Sınıflar ve nesneler](../tour-of-csharp/classes-and-objects.md)
- [Devralma (C# Programlama Kılavuzu)](../programming-guide/classes-and-structs/inheritance.md)
