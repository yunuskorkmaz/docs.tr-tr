---
title: Standart .NET olay desenleri
description: .NET olay desenleri ve standart olay kaynakları oluşturma ve kodunuzda standart olayları abonelik ve işleme hakkında bilgi edinin.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 8a3133d6-4ef2-46f9-9c8d-a8ea8898e4c9
ms.openlocfilehash: 517e46ffec163a9bd49baa58fc0b37b54b2b2809
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239865"
---
# <a name="standard-net-event-patterns"></a>Standart .NET olay desenleri

[Öncekini](events-overview.md)

.NET olayları genellikle bilinen birkaç deseni izler. Bu desenlerin standartlaştırılacağı geliştiriciler, geliştiricilerin herhangi bir .NET olay programına uygulanabilecek standart desenlerle ilgili bilgi sahibi olabileceği anlamına gelir.

Standart bir olay kaynağı oluşturmak ve kodunuzda standart olayları abone olmak ve işlemek için ihtiyacınız olan tüm bilgilere sahip olacak şekilde bu standart desenleri ilerlim.

## <a name="event-delegate-signatures"></a>Olay temsilcisi Imzaları

.NET olay temsilcisi için standart imza:

```csharp
void OnEventRaised(object sender, EventArgs args);
```

Dönüş türü void. Olaylar temsilcilere dayalıdır ve çok noktaya yayın temsilcileriniz. Bu, herhangi bir olay kaynağı için birden çok aboneyi destekler. Bir yöntemden tek dönüş değeri, birden çok olay abonelerine ölçeklenmez. Olay kaynağı, olay oluşturulduktan sonra hangi dönüş değeri görebilir? Bu makalenin ilerleyen kısımlarında, olay kaynağına rapor veren olay abonelerini destekleyen olay protokollerini nasıl oluşturacağınız hakkında bilgi edineceksiniz.

Bağımsız değişken listesi iki bağımsız değişken içerir: gönderici ve olay bağımsız değişkenleri. `sender` derleme zaman türü `System.Object`, ancak her zaman doğru olacak şekilde daha fazla türetilmiş bir tür bildiğiniz halde olabilir. Kurala göre `object`kullanın.

İkinci bağımsız değişken genellikle `System.EventArgs`türetilmiş bir türdür. (Bir [sonraki bölümde](modern-events.md) bu kural artık zorlanmadığını göreceksiniz.) Olay türü herhangi bir ek bağımsız değişken gerekmiyorsa, her iki bağımsız değişkeni de sağlamanız gerekir.
Olaylarınızın ek bilgi içermediğini belirtmek için kullanmanız gereken `EventArgs.Empty` özel bir değer vardır.

Bir dizinde veya bir kalıbı izleyen alt dizinlerindeki dosyaları listeleyen bir sınıf oluşturalım. Bu bileşen, bulunan her dosya için, düzeniyle eşleşen bir olay oluşturur.

Bir olay modelinin kullanılması bazı tasarım avantajları sağlar. Aranan bir dosya bulunduğunda farklı eylemler gerçekleştiren birden çok olay dinleyicisi oluşturabilirsiniz. Farklı dinleyicileri birleştirmek daha sağlam algoritmalar oluşturabilir.

Aranan bir dosyayı bulmak için ilk olay bağımsız değişkeni bildirimi aşağıda verilmiştir: 

[!code-csharp[EventArgs](../../samples/snippets/csharp/events/Program.cs#EventArgsV1 "Define event arguments")]

Bu tür küçük, salt veri türü gibi görünse de, kuralı izlemeniz ve bir başvuru (`class`) türü yapmanız gerekir. Diğer bir deyişle, bağımsız değişken nesnesi başvuruya göre geçirilir ve verilerin tüm güncelleştirmeleri tüm aboneler tarafından görüntülenir. İlk sürüm, sabit bir nesnedir. Olay bağımsız değişkeni türünde özellikleri sabit hale getirmek için tercih etmelisiniz. Bu şekilde, bir abone, başka bir abonenin onları görebilmesi için değerleri değiştiremez. (Aşağıda göreceğiniz şekilde bunun için özel durumlar vardır.)  

Sonra, FileSearcher sınıfında olay bildirimini oluşturuyoruz. `EventHandler<T>` türünden yararlanmak, başka bir tür tanımı oluşturmanız gerekmediği anlamına gelir. Yalnızca genel bir özelleştirme kullanırsınız.

Bir düzeniyle eşleşen dosyaları aramak ve bir eşleşme bulunduğunda doğru olayı yükseltmek için FileSearcher sınıfını dolduralım.

[!code-csharp[FileSearcher](../../samples/snippets/csharp/events/Program.cs#FileSearcherV1 "Create the initial file searcher")]

## <a name="defining-and-raising-field-like-events"></a>Alan benzeri olayları tanımlama ve oluşturma

Sınıfınıza bir olay eklemenin en kolay yolu, önceki örnekte olduğu gibi bu olayı ortak bir alan olarak bildirkullanmaktır:

[!code-csharp[DeclareEvent](../../samples/snippets/csharp/events/Program.cs#DeclareEvent "Declare the file found event")]

Bu, nesne odaklı kötü bir uygulama gibi görünen bir ortak alan bildirmek gibi görünüyor. Özellikler veya yöntemler aracılığıyla veri erişimini korumak istiyorsunuz. Kötü bir uygulama gibi görünebilir ancak derleyici tarafından oluşturulan kod, olay nesnelerine yalnızca güvenli yollarla erişilebilmesi için sarmalayıcılar oluşturur. Alan benzeri bir olayda kullanılabilen tek işlemler ekleme işleyicisidir:

[!code-csharp[DeclareEventHandler](../../samples/snippets/csharp/events/Program.cs#DeclareEventHandler "Declare the file found event handler")]

ve işleyiciyi kaldır:

[!code-csharp[RemoveEventHandler](../../samples/snippets/csharp/events/Program.cs#RemoveHandler "Remove the event handler")]

İşleyici için yerel bir değişken olduğunu unutmayın. Lambda gövdesini kullandıysanız, kaldırma doğru çalışmaz. Bu, temsilcinin farklı bir örneği olur ve sessizce hiçbir şey yapmaz.

Sınıf dışındaki kod, olayı yükseltemez, diğer işlemleri de gerçekleştiremez.

## <a name="returning-values-from-event-subscribers"></a>Olay abonelerinden değer döndürme

Basit sürümünüz sorunsuz çalışıyor. Başka bir özellik ekleyelim: Iptal.

Bulunan olayı yükselttiğinizde, bu dosya son bir aranan ise, dinleyiciler daha fazla işlemeyi durdurabilir.

Olay işleyicileri bir değer döndürmüyor, bu nedenle başka bir şekilde iletişim kurması gerekir. Standart olay deseninin, olay abonelerinin iptali iletişim kurmak için kullanabileceği alanları dahil etmek için EventArgs nesnesi kullanılır.

Iptal sözleşmesinin semantiğine bağlı olarak kullanılabilecek iki farklı desen vardır. Her iki durumda da, bulunan dosya olayı için EventArguments öğesine bir Boole alanı ekleyeceksiniz. 

Bir model, bir abonenin işlemi iptal edebilmesini sağlar.
Bu model için yeni alan `false`olarak başlatılır. Herhangi bir abone, `true`olarak değiştirebilir. Tüm aboneler oluşturulan olayı gördüğünde, FileSearcher bileşeni Boole değerini inceler ve işlem gerçekleştirir.

İkinci model yalnızca tüm aboneler işlemi iptal etmek istiyorlarsa işlemi iptal eder. Bu düzende, yeni alan işlemin iptal olması gerektiğini belirtecek şekilde başlatılır ve herhangi bir abone işlemin devam etmesi gerektiğini belirtecek şekilde değiştirebilir.
Tüm aboneler oluşturulan olayı gördüğünde, FileSearcher bileşeni Boole değerini inceler ve işlem gerçekleştirir. Bu düzende bir ek adım vardır: bileşeni, olayı gördük bir abone olup olmadığını bilmelidir. Abone yoksa, alan yanlışlıkla iptal olduğunu gösterir.

Bu örnek için ilk sürümü uygulayalim. `FileFoundArgs` türüne `CancelRequested` adlı bir Boole alanı eklemeniz gerekir:

[!code-csharp[EventArgs](../../samples/snippets/csharp/events/Program.cs#EventArgs "Update event arguments")]

Bu yeni alan, bir Boole alanı için varsayılan değer olan `false`için otomatik olarak başlatılır, böylece yanlışlıkla iptal edemezsiniz. Bileşendeki tek bir değişiklik, abonelerden birinin iptal isteğinde bulunup bulunmadığını görmek için olayı oluşturduktan sonra bayrağı denetmektir:

```csharp
public void List(string directory, string searchPattern)
{
    foreach (var file in Directory.EnumerateFiles(directory, searchPattern))
    {
        var args = new FileFoundArgs(file);
        FileFound?.Invoke(this, args);
        if (args.CancelRequested)
            break;
    }
}
```

Bu düzenin bir avantajı, önemli olmayan bir değişiklik değildir.
Abonelerden hiçbiri daha önce bir iptal isteğinde bulunmadı ve yine de yok. Yeni iptal protokolünü desteklemek istemmedikleri takdirde abone kodunun hiçbirinin güncelleştirilmesi gerekmez. Çok esnek bir şekilde bağlanmış.

İlk yürütülebilir dosyayı bulduktan sonra bir iptali istemesi için aboneyi güncelleştirelim:

```csharp
EventHandler<FileFoundArgs> onFileFound = (sender, eventArgs) =>
{
    Console.WriteLine(eventArgs.FoundFile);
    eventArgs.CancelRequested = true;
};
```

## <a name="adding-another-event-declaration"></a>Başka bir olay bildirimi ekleme

Daha fazla özellik ekleyelim ve olaylar için diğer dil deyimler gösterimi. Dosya aramasında tüm alt dizinlere geçiş yapan `Search` yönteminin bir aşırı yüklemesini ekleyelim.

Bu, çok sayıda alt dizine sahip bir dizinde uzun bir işlem olabilir. Her yeni dizin araması başladığında ortaya çıkan bir olay ekleyelim. Bu sayede aboneler ilerlemeyi izleyebilir ve kullanıcıyı ilerleme durumuna göre güncelleştirebilir. Şimdiye kadar oluşturduğunuz tüm örnekler geneldir. Bunu bir iç olay haline olalım. Diğer bir deyişle, iç değişkenler için de kullanılan türleri de yapabilirsiniz.

Yeni dizin ve ilerlemeyi raporlamak için yeni EventArgs türetilmiş sınıfını oluşturarak başlayacaksınız. 

[!code-csharp[DirEventArgs](../../samples/snippets/csharp/events/Program.cs#SearchDirEventArgs "Define search directory event arguments")]

Yine, olay bağımsız değişkenleri için sabit bir başvuru türü oluşturmak üzere önerileri izleyebilirsiniz.

Sonra, olayı tanımlayın. Bu kez, farklı bir sözdizimi kullanacaksınız. Alan söz dizimini kullanmanın yanı sıra, özelliği ekleme ve kaldırma işleyicileri ile açık bir şekilde oluşturabilirsiniz. Bu örnekte, bu işleyicilerde ek kod gerekmez, ancak bunları nasıl oluşturacağınız gösterilmektedir.

[!code-csharp[Declare event with add and remove handlers](../../samples/snippets/csharp/events/Program.cs#DeclareSearchEvent "Declare the event with add and remove handlers")]

Birçok şekilde, yazdığınız kod, daha önce gördüğünüz alan olay tanımları için derleyicinin oluşturduğu kodu yansıtır. [Özellikler](properties.md)için kullanılan için çok benzer sözdizimini kullanarak olayı oluşturursunuz. İşleyicilerin farklı adlara sahip olduğuna dikkat edin: `add` ve `remove`. Bunlar olaya abone olmak ya da olaydan abonelik kaldırmak için çağırılır. Ayrıca, olay değişkenini depolamak için özel bir destek alanı bildirmeniz gerektiğini unutmayın. Null olarak başlatılır.

Sonra, alt dizinlere geçiş yapan `Search` yönteminin aşırı yüklemesini ekleyelim ve her iki olayı da oluşturuyor. Bunu yapmanın en kolay yolu, tüm dizinlerde arama yapmak istediğinizi belirtmek için varsayılan bir bağımsız değişken kullanmaktır:

[!code-csharp[SearchImplementation](../../samples/snippets/csharp/events/Program.cs#FinalImplementation "Implementation to search directories")]

Bu noktada, tüm alt dizinleri aramak için aşırı yüklemeyi çağıran uygulamayı çalıştırabilirsiniz. Yeni `ChangeDirectory` olayında abone yoktur, ancak `?.Invoke()` deyim kullanmak bunun doğru şekilde çalıştığından emin olmanızı sağlar.

 Konsol penceresinde ilerleme durumunu gösteren bir çizgi yazmak için bir işleyici ekleyelim. 

[!code-csharp[Search](../../samples/snippets/csharp/events/Program.cs#Search "Declare event handler")]

.NET ekosisteminin tamamında izlenen desenleri gördünüz.
Bu desenleri ve kuralları öğrenerek, hızlı bir şekilde C# ve .net ' i hızla yazabileceksiniz.

Daha sonra, en son .NET sürümünde bu desenlerde bazı değişiklikler görürsünüz.

[Next](modern-events.md)
