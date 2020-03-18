---
title: Standart .NET olay desenleri
description: .NET olay desenleri ve standart etkinlik kaynaklarının nasıl oluşturulup kodundaki standart olaylara abone olun ve işlenirsiniz hakkında bilgi edinin.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 8a3133d6-4ef2-46f9-9c8d-a8ea8898e4c9
ms.openlocfilehash: dec516767e43a6bf4edfa555e34f3adcc21a46e3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146147"
---
# <a name="standard-net-event-patterns"></a>Standart .NET olay desenleri

[Önceki](events-overview.md)

.NET olayları genellikle bilinen birkaç desen izler. Bu desenleri standartlaştırmak, geliştiricilerin herhangi bir .NET etkinlik programına uygulanabilen bu standart desenler hakkındaki bilgilerden yararlanabileceği anlamına gelir.

Standart etkinlik kaynakları oluşturmak ve kodunuzda standart olaylara abone olmak ve işlemek için ihtiyacınız olan tüm bilgilere sahip olmak için bu standart desenleri gözden geçirelim.

## <a name="event-delegate-signatures"></a>Olay Temsilci İmzaları

.NET olay temsilcisinin standart imzası:

```csharp
void OnEventRaised(object sender, EventArgs args);
```

İade türü geçersizdir. Olaylar delegelere dayanır ve çok noktaya yayın lı temsilcilerdir. Bu, herhangi bir etkinlik kaynağı için birden çok aboneyi destekler. Bir yöntemden gelen tek iade değeri birden çok olay abonesine ölçeklendirilmez. Olay kaynağı, bir olayı yükselttikten sonra hangi iade değerini görür? Bu makalenin ilerleyen saatlerinde, olay kaynağına bilgi rapor eden olay abonelerini destekleyen olay protokollerinin nasıl oluşturulacağını görürsünüz.

Bağımsız değişken listesi iki bağımsız değişken içerir: gönderen ve olay bağımsız değişkenleri. Derleme zaman `sender` `System.Object`türü, büyük olasılıkla her zaman doğru olacağını daha türemiş bir tür biliyorum olsa bile. Kurallara göre, kullanın. `object`

İkinci bağımsız değişken genellikle `System.EventArgs`türetilen bir tür olmuştur. (Bir [sonraki bölümde](modern-events.md) bu kuralın artık uygulanmadığını görürsünüz.) Olay türünün ek bağımsız değişkenleri yoksa, her iki bağımsız değişkeni de sağlamaya devam edesiniz.
Etkinliğinizin herhangi bir `EventArgs.Empty` ek bilgi içermediğini belirtmek için kullanmanız gereken özel bir değer vardır.

Dosyaları bir dizindeki veya bir deseni izleyen alt dizinişlerini listeleyen bir sınıf oluşturalım. Bu bileşen, deseneşleşen bulunan her dosya için bir olay yükseltir.

Olay modeli kullanmak bazı tasarım avantajları sağlar. Aranan bir dosya bulunduğunda farklı eylemler gerçekleştiren birden çok olay dinleyicisi oluşturabilirsiniz. Farklı dinleyicileri birleştirmek daha sağlam algoritmalar oluşturabilir.

Aranan bir dosyayı bulmak için ilk olay bağımsız değişken bildirimi aşağıda veda edilir:

[!code-csharp[EventArgs](../../samples/snippets/csharp/events/Program.cs#EventArgsV1 "Define event arguments")]

Bu tür küçük, yalnızca veri türü gibi görünse de, kuralı izlemeli`class`ve bir başvuru ( ) türü yapmalısınız. Bu, bağımsız değişken nesnesinin başvuru yoluyla geçirileceği ve verilerdeki tüm güncelleştirmelerin tüm aboneler tarafından görüntüleneceği anlamına gelir. İlk sürüm değişmez bir nesnedir. Olay bağımsız değişken türündeki özellikleri değişmez hale getirmeyi tercih edersiniz. Bu şekilde, bir abone, başka bir abone görmeden önce değerleri değiştiremez. (Aşağıda göreceğiniz gibi, bunun istisnaları vardır.)  

Ardından, FileSearcher sınıfında olay bildirimioluşturmamız gerekir. `EventHandler<T>` Türden yararlanmak, başka bir tür tanımı oluşturmanız gerekolmadığı anlamına gelir. Sadece genel bir uzmanlık kullanın.

Bir desenle eşleşen dosyaları aramak için FileSearcher sınıfını dolduralım ve bir eşleşme keşfedildiğinde doğru olayı yükseltelim.

[!code-csharp[FileSearcher](../../samples/snippets/csharp/events/Program.cs#FileSearcherV1 "Create the initial file searcher")]

## <a name="defining-and-raising-field-like-events"></a>Alan Benzeri Etkinliklerin Tanımlanması ve Yükseltilmesi

Bir olayı sınıfınıza eklemenin en basit yolu, önceki örnekte olduğu gibi, bu olayı ortak alan olarak bildirmektir:

[!code-csharp[DeclareEvent](../../samples/snippets/csharp/events/Program.cs#DeclareEvent "Declare the file found event")]

Bu, kötü nesne yönelimli bir uygulama gibi görünen bir kamusal alan ilan ediyor gibi görünüyor. Özellikler veya yöntemler aracılığıyla veri erişimini korumak istiyorsunuz. Bu kötü bir uygulama gibi görünse de, derleyici tarafından oluşturulan kod, olay nesnelerine yalnızca güvenli yollarla erişilebilmek için sarmalayıcılar oluşturur. Alan benzeri bir etkinlikte kullanılabilen tek işlem işleyicisi vardır:

[!code-csharp[DeclareEventHandler](../../samples/snippets/csharp/events/Program.cs#DeclareEventHandler "Declare the file found event handler")]

ve işleyiciyi kaldırın:

[!code-csharp[RemoveEventHandler](../../samples/snippets/csharp/events/Program.cs#RemoveHandler "Remove the event handler")]

İşleyici için yerel bir değişken olduğunu unutmayın. Lambda gövdesi kullanılırsa, kaldırmak doğru çalışmaz. Bu delege farklı bir örnek olacaktır ve sessizce hiçbir şey yok.

Sınıfın dışındaki kod olayı yükseltemez ve başka bir işlem gerçekleştiremez.

## <a name="returning-values-from-event-subscribers"></a>Etkinlik Abonelerinden Dönen Değerler

Basit versiyonun gayet iyi çalışıyor. Başka bir özellik ekleyelim: İptal.

Bulunan olayı yükselttiğinizde, dinleyiciler bu dosya aranan son dosyaysa, daha fazla işleme durdurabilmeli.

Olay işleyicileri bir değer döndürmez, bu nedenle bunu başka bir şekilde iletmeniz gerekir. Standart olay deseni, event abonelerinin iptal iletişimi kurmak için kullanabilecekleri alanları eklemek için EventArgs nesnesini kullanır.

İptal sözleşmesinin anlambilimine göre kullanılabilecek iki farklı desen vardır. Her iki durumda da, bulunan dosya olayı için EventArguments'a bir boolean alanı eklersiniz.

Bir desen, herhangi bir abonenin işlemi iptal etmesine izin verir.
Bu desen için, yeni alan `false`' a' ya başharf. Herhangi bir abone bunu `true`. Tüm aboneler olayın yükseltildiğini gördükten sonra, FileSearcher bileşeni boolean değerini inceler ve harekete geçer.

İkinci desen, yalnızca tüm aboneler işlemin iptalini isterse işlemi iptal eder. Bu desende, işlemin iptal etmesi gerektiğini belirtmek için yeni alan başolarak başolarak başlanır ve herhangi bir abone, işlemin devam etmesi gerektiğini belirtmek için değiştirebilirsiniz.
Tüm aboneler olayın yükseltildiğini gördükten sonra, FileSearcher bileşeni boolean inceler ve harekete geçer. Bu desende fazladan bir adım vardır: bileşenin olayı gören aboneler olup olmadığını bilmesi gerekir. Abone yoksa, alan yanlış iptal olduğunu gösterir.

Bu örnek için ilk sürümü uygulayalım. Türüne adlandırılmış `CancelRequested` bir boolean `FileFoundArgs` alanı eklemeniz gerekir:

[!code-csharp[EventArgs](../../samples/snippets/csharp/events/Program.cs#EventArgs "Update event arguments")]

Bu yeni Alan otomatik olarak `false`bir Boolean alanı için varsayılan değer e-baş harfe ayarlanır, böylece yanlışlıkla iptal etmezsiniz. Bileşendeki diğer tek değişiklik, abonelerden herhangi birinin iptal talebinde bulunıp var olmadığını görmek için olayı yükselttikten sonra bayrağı denetlemektir:

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

Bu modelin bir avantajı, bir kırılma değişiklik değildir.
Abonelerin hiçbiri daha önce iptal talebinde bulunmadı ve hala da iptal edilmedi. Yeni iptal protokolünü desteklemek istemedikleri sürece abone kodunun hiçbirinin güncelleştirilmesi gerekir. Çok gevşek bir şekilde birleştirilmiş.

Aboneyi, ilk çalıştırılabilir ibareyi bulduğunda iptal talebinde bulunsun diye güncelleyelim:

```csharp
EventHandler<FileFoundArgs> onFileFound = (sender, eventArgs) =>
{
    Console.WriteLine(eventArgs.FoundFile);
    eventArgs.CancelRequested = true;
};
```

## <a name="adding-another-event-declaration"></a>Başka bir olay bildirimi ekleme

Bir özellik daha ekleyelim ve etkinlikler için diğer dil deyimlerini gösterelim. Dosya aramasında `Search` tüm alt dizinleri geçen yöntemin aşırı yüklenmesini ekleyelim.

Bu, birçok alt diziniçeren bir dizinde uzun bir işlem olabilir. Her yeni dizin araması başladığında gündeme gelen bir olay ekleyelim. Bu, abonelerin ilerlemeyi izlemesini ve kullanıcıyı ilerleme olarak güncelleştirmesini sağlar. Şimdiye kadar oluşturduğunuz tüm örnekler herkese açıktır. Bunu bir iç olay haline getirelim. Bu, iç bağımsız değişkenler için kullanılan türleri de yapabileceğiniz anlamına gelir.

Yeni dizini ve ilerlemeyi bildirmek için yeni EventArgs türetilmiş sınıfını oluşturarak başlarsınız.

[!code-csharp[DirEventArgs](../../samples/snippets/csharp/events/Program.cs#SearchDirEventArgs "Define search directory event arguments")]

Yine, olay bağımsız değişkenleri için değişmez bir başvuru türü yapmak için önerileri izleyebilirsiniz.

Sonra, olayı tanımlayın. Bu sefer farklı bir sözdizimi kullanacaksın. Alan sözdizimini kullanmanın yanı sıra, özelliği açıkça ekleyip kaldır işleyicileriyle oluşturabilirsiniz. Bu örnekte, bu işleyicilerde fazladan kod gerekmez, ancak bu bunları nasıl oluşturacağınızı gösterir.

[!code-csharp[Declare event with add and remove handlers](../../samples/snippets/csharp/events/Program.cs#DeclareSearchEvent "Declare the event with add and remove handlers")]

Birçok yönden, burada yazdığınız kod, derleyicinin daha önce gördüğünüz alan olay tanımları için oluşturduğu kodu yansıtAbilir. Olayı, [özellikler](properties.md)için kullanılana çok benzer sözdizimini kullanarak oluşturursunuz. İşleyicilerin farklı adları olduğuna `add` dikkat `remove`edin: ve . Bunlar, etkinliğe abone olmak veya etkinlikten aboneliğiiptal etmek için çağrılır. Olay değişkenini depolamak için özel bir destek alanı da bildirmeniz gerektiğine dikkat edin. Null için başharf.

Ardından, alt dizinleri geçen `Search` ve her iki olayı da yükselten yöntemin aşırı yüklenmesini ekleyelim. Bunu gerçekleştirmenin en kolay yolu, tüm dizinlerde arama yapmak istediğinizi belirtmek için varsayılan bir bağımsız değişken kullanmaktır:

[!code-csharp[SearchImplementation](../../samples/snippets/csharp/events/Program.cs#FinalImplementation "Implementation to search directories")]

Bu noktada, tüm alt dizinleri aramak için aşırı yükleme çağıran uygulamayı çalıştırabilirsiniz. Yeni `ChangeDirectory` etkinlikte abone yok, ancak deyimin `?.Invoke()` kullanılması bunun doğru çalışmasını sağlar.

 Konsol penceresinde ilerlemeyi gösteren bir satır yazmak için bir işleyici ekleyelim.

[!code-csharp[Search](../../samples/snippets/csharp/events/Program.cs#Search "Declare event handler")]

.NET ekosistemi boyunca izlenen desenler ilerler siniz.
Bu kalıpları ve kuralları öğrenerek, idiomatic C# ve .NET'i hızla yazacaksınız.

Ardından, .NET'in en son sürümünde bu desenlerde bazı değişiklikler görürsünüz.

[Sonraki](modern-events.md)
