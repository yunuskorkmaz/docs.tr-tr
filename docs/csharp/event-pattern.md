---
title: Standart .NET olay desenleri
description: .NET olay desenleri ve abone standart olay kaynakları oluşturmak ve kodunuzun içinde standart olayları işleme hakkında daha fazla bilgi edinin.
ms.date: 06/20/2016
ms.assetid: 8a3133d6-4ef2-46f9-9c8d-a8ea8898e4c9
ms.openlocfilehash: 16a091dabe34a064ab3ee65a6d9f3e0ab36f1db4
ms.sourcegitcommit: 35316b768394e56087483cde93f854ba607b63bc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52297042"
---
# <a name="standard-net-event-patterns"></a>Standart .NET olay desenleri

[Önceki](events-overview.md)

.NET etkinliklerini genellikle birkaç bilinen desenleri takip edin. Bu eğilimlere Standartlaştırma, geliştiricilerin, .NET olay programıyla uygulanabilir bu standart desenlerinin bilgi yararlanabileceğiniz anlamına gelir.

Bu standart desenleri standart olay kaynakları oluşturmak ve abone olma ve kodunuzda standart olayları işlemek için ihtiyaç duyduğunuz tüm bilgisine sahip şekilde Bahsedelim.

## <a name="event-delegate-signatures"></a>Olay temsilci imzaları

Standart .NET olay temsilci imzası verilmiştir:

```csharp
void OnEventRaised(object sender, EventArgs args);
```

Dönüş türü void. Olaylar, temsilciler üzerinde temel alır ve çok noktaya yayın temsilcileri, bir. Herhangi bir olay kaynağı için birden fazla aboneye destekleyen. Tek bir yöntemin dönüş değeri için birden fazla olay abonesi ölçeklendirilemez. Olay kaynağı bakın, dönüş değeri bir olayı tetiklenmeden sonra mu? Bu makalenin sonraki bölümlerinde etkinlik abonelerinden destekleyen olay protokolleri oluşturma olay kaynağı bu rapor bilgileri görürsünüz.

İki bağımsız değişken bağımsız değişken listesi içeriyor: göndereni ve olay bağımsız değişkenleri. Derleme zamanı türü `sender` olduğu `System.Object`, büyük olasılıkla her zaman doğru olmayacak daha türetilmiş türde bildiğiniz olsa bile. Kural gereği, kullanın `object`.

İkinci bağımsız değişkeni genellikle tan türetilmiş bir tür olan `System.EventArgs`. (Görüşelim [sonraki bölümde](modern-events.md) , bu kural artık zorlanmamaktadır.) Herhangi bir ek bağımsız değişken, olay türü gereksinimi yoksa, yine de her iki değişken sağlar.
Özel bir değer `EventArgs.Empty` etkinliğiniz herhangi ek bir bilgi içermediğini belirtmek için kullanmanız gerekir.

Şimdi bir dizin ya da herhangi bir düzen izleyen dizinlerinden dosyaları listeleyen bir sınıf oluşturun. Bu bileşen, deseni, eşleşen her dosya bulundu için bir olay başlatır.

Bir olay modeli kullanarak bazı tasarım avantajları sağlar. Aranan bir dosya bulunduğunda, farklı eylemler gerçekleştirmesini birden çok olay dinleyicileri oluşturabilirsiniz. Farklı dinleyicileri birleştirerek daha güçlü algoritmalar oluşturabilirsiniz.

Aranan bir dosyayı bulmak için ilk olay bağımsız değişkeni bildirimi şu şekildedir: 

[!code-csharp[EventArgs](../../samples/csharp/events/Program.cs#EventArgsV1 "Define event arguments")]

Bu tür bir küçük, yalnızca veri türü gibi görünse de, kuralını izler ve bir başvuru yapmak gerekir (`class`) türü. Bu başvuruya göre bağımsız değişken nesnesi geçirilir ve verilere herhangi bir güncelleştirme tüm aboneler tarafından görüntülenecek anlamına gelir. İlk sürüm değişmez bir nesnedir. Olay bağımsız değişkeni türünüz özellikleri değişmez yapmak tercih etmelisiniz. Bu şekilde, başka bir aboneyi bunları görmeden bir abone değerlerini değiştiremezsiniz. (İstisnaları vardır, aşağıda anlatıldığı gibi.)  

Ardından, biz FileSearcher sınıfında olay bildirimi oluşturmanız gerekir. Yararlanarak `EventHandler<T>` türü gösterir bir başka tür tanımı oluşturmanız gerekmez. Sadece genel özelleştirmesi kullanın.

Şimdi bir desenle eşleşen dosyaları aramak için FileSearcher sınıfı doldurun ve bir eşleşme bulunduğunda doğru olayı oluşturun.

[!code-csharp[FileSearxcher](../../samples/csharp/events/Program.cs#FileSearcherV1 "Create the initial file searcher")]

## <a name="defining-and-raising-field-like-events"></a>Tanımlama ve alan benzeri olaylara oluşturma

En basit yolu, sınıfa olaya eklemek için önceki örnekte olduğu gibi genel bir alan olarak olay bildirmek için verilmiştir:

[!code-csharp[DeclareEvent](../../samples/csharp/events/Program.cs#DeclareEvent "Declare the file found event")]

Hatalı nesne yönelimli bir uygulama olarak görünebilir bir ortak alan bildirme görülüyor. Özellikleri veya yöntemleri aracılığıyla veri erişimi korumak istiyorsunuz. Bunu yaparken, böylece olay nesneleri yalnızca güvenli şekilde erişilebilir hatalı bir uygulama, derleyici tarafından oluşturulan kodu sarmalayıcıları oluşturma gibi arayın. Yalnızca kullanılabilir işlemleri bir alan benzeri olayı işleyicisi ekleyin:

[!code-csharp[DeclareEventHandler](../../samples/csharp/events/Program.cs#DeclareEventHandler "Declare the file found event handler")]

ve işleyiciyi kaldırın:

[!code-csharp[RemoveEventHandler](../../samples/csharp/events/Program.cs#RemoveHandler "Remove the event handler")]

İşleyici için bir yerel değişken olduğuna dikkat edin. Lambda gövdesi kullandıysanız Kaldır düzgün çalışmaz. Metot temsilcisinin farklı bir örneği olması ve sessizce hiçbir şey yapma.

Sınıf dışındaki kod olay oluşturamaz veya diğer tüm işlemleri gerçekleştirebilir.

## <a name="returning-values-from-event-subscribers"></a>Etkinlik Abonelerinden değerler döndüren

Basit sürümünüzü düzgün çalışıyor. Başka bir özellik ekleyelim: iptal.

Bulunan olay yükselttiğinizde, bu dosya, sonuncu Aranan ise dinleyicileri daha fazla işleme, durdurmak için olmalıdır.

Bu nedenle, başka bir biçimde iletişim kurmasına olanak gerekir olay işleyicileri bir değer döndürmeyen. Standart olay deseni EventArgs etkinlik abonelerinden iptal iletişim kurmak için kullanabileceğiniz alanlar dahil etmek için kullanır.

İptal sözleşmenin semantiği göre kullanılabilecek iki farklı deseni vardır. Her iki durumda da EventArguments bulunan dosyayı olayı için bir Boole alanı ekleyeceksiniz. 

Bir desen işlemi iptal etmek herhangi bir abone çalıştırmasına olanak tanır.
Bu düzeni için yeni alan değerine ayarlanır `false`. Her abone için değiştirebilirsiniz `true`. Tüm aboneler tetiklenen olayı gördünüz sonra FileSearcher bileşen Boole değeri inceler ve eylemi gerçekleştirir.

Tüm aboneler İptal işlemi isterseniz ikinci desen yalnızca işlem iptal. Bu düzende, yeni alan işlemi iptal etmesi gerekir ve işlem devam belirtmek için herhangi bir abone değiştirebilir belirtmek için başlatılır.
Tüm aboneler tetiklenen olayı gördünüz sonra FileSearcher bileşen boolean inceler ve eylemi alır. Bu modelde ek bir adım yoktur: bileşen olayın tüm abonelerine gördünüz mü bilmesi gerekir. Abone varsa, alan iptal yanlış gösterir.

Bu örnek için ilk sürümü şimdi uygulayın. Adlı bir Boole alanı eklemeniz `CancelRequested` için `FileFoundArgs` türü:

[!code-csharp[EventArgs](../../samples/csharp/events/Program.cs#EventArgs "Update event arguments")]

Bu yeni alan için otomatik olarak başlatılır `false`, yanlışlıkla iptal etme için mantıksal bir alan için varsayılan değer. Diğer değişiklik bileşenine abonelerin herhangi bir iptal isteğinde olmadığını görmek için olayın yükseltme sonrasında bayrağı denetlemektir.

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

Bu düzenin bir avantajı, bir değişiklik olmadığından emin olmanızdır.
Abonelerin hiçbiri önce bir iptal isteğinde ve bunlar değil. Abone kod hiçbiri yeni iptal protokolünü destekleyen istemiyorsanız güncelleştirilmesi gerekir. Bu çok birbirine sıkı şekilde bağlı.

Şimdi ilk yürütülebilir bulduğunda iptal ister. böylece abone güncelleştirin:

```csharp
EventHandler<FileFoundArgs> onFileFound = (sender, eventArgs) =>
{
    Console.WriteLine(eventArgs.FoundFile);
    eventArgs.CancelRequested = true;
};
```

## <a name="adding-another-event-declaration"></a>Başka bir olay bildirimi ekleme

Şimdi bir daha fazla özellik eklemek ve diğer dil deyimleri olayları gösterir. Bir aşırı yüklemesini ekleyelim `Search` tüm alt dizinlerde dosyaları saldırılar trafiğiyle yöntemi.

Bu, bir dizinde birden çok alt dizini ile uzun bir işlem olarak alabilir. Her yeni dizin araması başladığında bir olayı ekleyelim. Bu, ilerlemeyi izlemek ve ilerleme için kullanıcıyı güncelleştirmek aboneleri sağlar. Şu ana kadar oluşturulmuş tüm örnekleri ortak. Bu, bir olay olalım. İç bağımsız değişkenleri de kullanılan türleri de yapabileceğiniz anlamına gelir.

Yeni dizine ve ilerlemeyi raporlama için yeni bir EventArgs türetilmiş sınıf oluşturarak başlayacağız. 

[!code-csharp[DirEventArgs](../../samples/csharp/events/Program.cs#SearchDirEventArgs "Define search directory event arguments")]

Tekrar bir değişmez başvuru türü için olay bağımsız değişkenleri olmak için önerileri takip edebilirsiniz.

Ardından, olay tanımlayın. Bu kez, farklı bir sözdizimi kullanırsınız. Alan söz dizimini kullanarak ek olarak, açıkça Özellik Ekle ile oluşturma ve işleyicileri kaldırın. Bu örnekte bu işleyicileri ek bir kod gerekmez, ancak bunları nasıl oluşturacak bu gösterir.

[!code-csharp[Declare event with add and remove handlers](../../samples/csharp/events/Program.cs#DeclareSearchEvent "Declare the event with add and remove handlers")]

Birçok yolla kod burada alan olay tanımları için derleyici kodu oluşturur yansıtmalar Yaz, daha önce gördünüz. İçin kullanılan çok benzer bir sözdizimi kullanarak olay oluşturma [özellikleri](properties.md). İşleyiciler, farklı adlar olduğunu fark edeceksiniz: `add` ve `remove`. Bu olaya abone veya olayın aboneliğini kaldırmak için çağrılır. Ayrıca olay değişkeni depolamak için özel destek alanı bildirmeniz gerekir dikkat edin. Null olarak başlatılır.

Ardından, aşırı yüklemesini ekleyelim `Search` alt dizinleri erişir ve her iki olayı harekete yöntemi. Bunu yapmanın en kolay yolu, tüm dizinlerde arama istediğinizi belirtmek için varsayılan bağımsız değişken kullanmaktır:

[!code-csharp[SearchImplementation](../../samples/csharp/events/Program.cs#FinalImplementation "Implementation to search directories")]

Bu noktada, tüm alt dizinlerinde arama için aşırı yüklemesini çağırmayı uygulamayı çalıştırabilirsiniz. Yeni abone vardır `ChangeDirectory` olay ancak kullanarak `?.Invoke()` deyim, bu düzgün çalıştığını sağlar.

 Konsol penceresinde ilerleme durumunu gösteren bir çizgi yazmak için bir işleyici ekleyelim. 

[!code-csharp[Search](../../samples/csharp/events/Program.cs#Search "Declare event handler")]

.NET ekosisteminin izlendiğini desenleri gördünüz.
Bu desenleri ve kuralları öğrenerek deyimsel C# ve .NET hızla yazdığınız.

Ardından, bu desenleri .NET en son sürümünde bazı değişiklikler görürsünüz.

[Next](modern-events.md)
