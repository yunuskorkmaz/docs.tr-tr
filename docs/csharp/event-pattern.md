---
title: Standart .NET olay desenleri
description: .NET olay desenleri ve standart olay kaynakları oluşturma ve abone olma ve kodunuzda standart olayları işleme hakkında bilgi edinin.
ms.date: 06/20/2016
ms.assetid: 8a3133d6-4ef2-46f9-9c8d-a8ea8898e4c9
ms.openlocfilehash: 9bd9f71726647966dd1e4426b260484decb048c6
ms.sourcegitcommit: d955cb4c681d68cf301d410925d83f25172ece86
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/07/2018
ms.locfileid: "34827254"
---
# <a name="standard-net-event-patterns"></a>Standart .NET olay desenleri

[Önceki](events-overview.md)

.NET olaylar genellikle birkaç bilinen desenlerini izleyin. Bu düzenleri üzerinde Standartlaştırma, geliştiricilerin bilgi .NET olay programlarından uygulanabilir bu standart desenlerinin yararlanabilirsiniz anlamına gelir.

Bu standart desenleri standart olay kaynakları oluşturmanız ve abone olma ve kodunuzda standart olayları işlemek için gereken tüm bilgisine sahip şekilde edelim.

## <a name="event-delegate-signatures"></a>Olay temsilci imzaları

Bir .NET olay temsilci için standart imza şöyledir:

```csharp
void OnEventRaised(object sender, EventArgs args);
```

Dönüş türü void ' dir. Olaylar temsilciler üzerinde temel alır ve çok noktaya yayın temsilcileri. Tüm olay kaynağı için birden çok aboneye destekleyen. Bir yöntem gelen tek bir dönüş değeri için birden çok olay aboneye ölçeklendirilmediğini. Hangi dönüş değeri, bir olayı tetiklenmeden sonra olay kaynağı bakın mu? Bu makalenin sonraki bölümlerinde, olay kaynağı için bu raporu bilgileri olay aboneleri destek olay protokolleri oluşturma görürsünüz.

İki bağımsız değişken listesi içerir: gönderici ve olay bağımsız değişkenler. Derleme zamanı türünün `sender` olan `System.Object`, büyük olasılıkla her zaman doğru olacak daha fazla türetilmiş bir tür bildiğiniz olsa bile. Kurala göre kullanmak `object`.

İkinci bağımsız değişkeni genellikle türetilmiş bir tür bırakıldı `System.EventArgs`. (İçinde görürsünüz [sonraki bölümde](modern-events.md) , bu kural artık uygulanmaz.) Olay türü herhangi bir ek bağımsız değişkeni gerekli değildir, her iki değişken hala sağlayacaktır.
Özel bir değer `EventArgs.Empty` , olay ek bilgileri içermiyor belirtmek için kullanmanız gerekir.

Şimdi bir dizin ya da herhangi bir yol izler dizinlerinden dosyaları listeleyen bir sınıf oluşturun. Desenle eşleşen her bir dosya bulunduğunda bu bileşen bir olay başlatır.

Bir olay modelini kullanarak bazı tasarım avantajlar sağlar. Aranan dosya bulunduğunda, farklı eylemler gerçekleştiren birden çok olay dinleyicileri oluşturabilirsiniz. Farklı dinleyicileri birleştirerek daha sağlam algoritmaları oluşturabilirsiniz.

İlk olay bağımsız değişken bildirimi'Aranan dosyasını bulmak için aşağıda verilmiştir: 

[!code-csharp[EventArgs](../../samples/csharp/events/Program.cs#EventArgsV1 "Define event arguments")]

Bu tür bir küçük, yalnızca veri türü gibi görünse kuralını izler ve bir başvuru yapmak gerekir (`class`) yazın. Başvuruya göre bağımsız değişken nesne geçirilir ve verileri herhangi bir güncelleştirme tüm aboneler tarafından görüntülenecek anlamına gelir. İlk sürümü değişmez bir nesnedir. Özellikler, olay bağımsız değişken türü değişmez yapmak tercih etmelisiniz. Bu şekilde, başka bir abonelik bunları görmeden bir abonesi değerleri değiştiremezsiniz. (Bu, özel durumlar aşağıda göreceğiniz gibi vardır.)  

Ardından, biz olay bildirimi FileSearcher sınıfında oluşturmanız gerekir. Yararlanarak `EventHandler<T>` türü anlamına gelir henüz başka bir tür tanımı oluşturmanız gerekmez. Yalnızca genel uzmanlık kullanın.

Şimdi bir desenle eşleşen dosyaları aramak için FileSearcher sınıfı doldurun ve bir eşleşme bulunduğunda doğru olayı oluşturun.

[!code-csharp[FileSearxcher](../../samples/csharp/events/Program.cs#FileSearcherV1 "Create the initial file searcher")]

## <a name="definining-and-raising-field-like-events"></a>Definining ve alan benzeri olayları

En basit yolu, sınıf için bir olay eklemek için önceki örnekte olduğu gibi ortak bir alan olarak olay bildirmektir:

[!code-csharp[DeclareEvent](../../samples/csharp/events/Program.cs#DeclareEvent "Declare the file found event")]

Bu durum, hatalı nesne yönelimli uygulama olarak görüneceği bir ortak alan bildirme görülüyor. Veri erişimi özelliklerinin veya yöntemlerin aracılığıyla korumak istiyorsunuz. Bunu yaparken böylece olay nesneleri yalnızca güvenli şekilde erişilebilir hatalı bir uygulama, derleyici tarafından oluşturulan kodu sarmalayıcıları oluşturma gibi arayın. Yalnızca kullanılabilir işlemleri alan benzeri olay işleyicisi ekleyin:

[!code-csharp[DeclareEventHandler](../../samples/csharp/events/Program.cs#DeclareEventHandler "Declare the file found event handler")]

ve işleyici kaldırın:

[!code-csharp[RemoveEventHandler](../../samples/csharp/events/Program.cs#RemoveHandler "Remove the event handler")]

İşleyici için bir yerel değişken olduğuna dikkat edin. Lambda gövdesi kullandıysanız, Kaldır düzgün çalışır değil. Temsilci farklı bir örneğine olması ve sessiz bir şekilde hiçbir şey yapma.

Sınıf dışındaki kodu olay oluşturamaz veya diğer işlemler gerçekleştirebilirsiniz.

## <a name="returning-values-from-event-subscribers"></a>Olay aboneleri dönüş değerleri

Basit sürümünüzü düzgün çalışıyor. Başka bir özellik ekleyelim: iptali.

Bulunan olay yükselttiğinizde, bu dosyayı son Aranan ise dinleyicileri başka bir işleme, durdurmak mümkün olması gerekir.

Olay işleyicileri, başka bir şekilde iletişim kurması gereken şekilde bir değer döndürmeyen. Standart olay deseni EventArgs nesne olay aboneleri iptal iletişim kurmak için kullanabileceği alan eklemek için kullanır.

İptal sözleşme semantiği dayalı kullanılabilecek iki farklı modeli vardır. Her iki durumda da EventArguments bulunan dosya olayı için bir Boole alanı eklenecektir. 

Bir desen işlemi iptal etmek herhangi bir abonesi olanak tanır.
Bu model için yeni alan için başlatılmış `false`. Her abonesi değiştirebilirsiniz `true`. Tüm aboneleri olay gerçekleşti gördünüz sonra FileSearcher bileşen boolean değeri inceler ve eylem gerçekleştirir.

Tüm aboneleri işlem iptal edildi istediyseniz ikinci deseni yalnızca işlemi iptal etmek. Bu modelinde işlemi iptal ve her abonesi işlemi devam etmesi gerektiğini belirtmek için değiştirebilir göstermek için yeni alan başlatılır.
Tüm aboneleri olay gerçekleşti gördünüz sonra FileSearcher bileşen boolean inceler ve eylem gerçekleştirir. Bu desen bir ek adım vardır: bileşen, tüm aboneler bir olay gördünüz bilmek ister. Abone yoksa, alanın bir iptal yanlış gösterir.

Şimdi bu örnek için ilk sürüm uygulayın. Adlı bir boolean alanı eklemeniz `CancelRequested` için `FileFoundArgs` türü:

[!code-csharp[EventArgs](../../samples/csharp/events/Program.cs#EventArgs "Update event arguments")]

Bu yeni alan için otomatik olarak başlatılır `false`, yanlışlıkla iptal etme için bir Boole alanı için varsayılan değer. Yalnızca diğer bileşenine aboneleri hiçbirini iptal istenen görmek için olay yükseltme sonrasında bayrağı denetlemek için değişikliktir:

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

Bu desen bir avantajı, önemli bir değişiklik değil ' dir.
Aboneleri hiçbiri önce iptal istenir ve bunlar hala değildir. Abone kod hiçbiri yeni iptal protokolünü destekleyen istemedikçe güncelleştirilmesi gerekiyor. Çok birbirine sıkı şekilde bağlı.

Şimdi ilk yürütülebilir bulduğunda iptal isteklerini şekilde abone güncelleştirin:

```csharp
EventHandler<FileFoundArgs> onFileFound = (sender, eventArgs) =>
{
    Console.WriteLine(eventArgs.FoundFile);
    eventArgs.CancelRequested = true;
};
```

## <a name="adding-another-event-declaration"></a>Başka bir olay bildirimi ekleme

Şimdi bir daha fazla özellik eklemek ve diğer dili deyimleri olayları gösterin. Bir aşırı yüklemesini ekleyelim `Search()` dosyaları aramak üzere tüm alt dizinler geçeceğini yöntemi.

Bu, birden çok alt dizini ile bir dizinde uzun bir işlem olarak alabilir. Her yeni bir dizin arama başladığında bir olayı ekleyelim. Bu, ilerlemeyi izlemek ve ilerleme konusunda kullanıcıyı güncelleştirmek aboneleri sağlar. Şu ana kadar oluşturmuş olduğunuz tüm örnekleri ortak. Bu bir iç olay olalım. Bağımsız değişkenler için dahili olarak da kullanılan türleri de yapabilirsiniz anlamına gelir.

Yeni bir dizin ve ilerleme durumu raporlama için yeni EventArgs türetilmiş sınıf oluşturarak başlayacağız. 

[!code-csharp[DirEventArgs](../../samples/csharp/events/Program.cs#SearchDirEventArgs "Define search directory event arguments")]

Yeniden olay bağımsız değişken için bir sabit başvuru türü sağlayacak öneriler izleyebilirsiniz.

Ardından, olay tanımlayın. Bu süre, farklı bir sözdizimi kullanacaksınız. Alan sözdizimini kullanarak ek olarak, açıkça ile ekleme özelliği oluşturabilir ve işleyicileri kaldırın. Bu örnekte bu işleyiciler ek kod gerekmez, ancak bu nasıl oluşturmak gösterir.

[!code-csharp[Declare event with add and remove handlers](../../samples/csharp/events/Program.cs#DeclareSearchEvent "Declare the event with add and remove handlers")]

Birçok yolla burada yansıtmalar alan olay tanımlarında derleyici kod oluşturur yazdığınız kodları, daha önce gördünüz. İçin kullanılan çok benzer sözdizimi kullanılarak olay oluşturma [özellikleri](properties.md). İşleyicileri farklı adlara sahip dikkat edin: `add` ve `remove`. Bu olaya abone veya olayından aboneliği adı verilir. Olay değişkeni depolamak için bir özel yedekleme alanını da bildirmelidir dikkat edin. Null olarak başlatılır.

Ardından, alt dizinleri erişir ve her iki olayları başlatır Search() yönteminin ekleyelim. Bunu yapmanın en kolay yolu, tüm dizinler arama yapmak istediğinizi belirtmek için bir varsayılan bağımsız değişkeni kullanmaktır:

[!code-csharp[SearchImplementation](../../samples/csharp/events/Program.cs#FinalImplementation "Implementation to search directories")]

Bu noktada, tüm alt dizinler arama için aşırı çağırma uygulamayı çalıştırabilirsiniz. Yeni abone vardır `ChangeDirectory` olay ancak kullanarak `?.Invoke()` deyim bu düzgün çalıştığını sağlar.

 Konsol penceresinde ilerleme durumunu gösteren bir satır yazmak için bir işleyici ekleyelim. 

[!code-csharp[Search](../../samples/csharp/events/Program.cs#Search "Declare event handler")]

.NET ekosistemi izlenen desenleri gördünüz.
Bu desenleri ve kuralları öğrenerek, kullanılan deyimsel C# ve .NET hızla yazacaksınız.

Ardından, bu desenleri .NET en son sürümündeki bazı değişiklikler görürsünüz.

[Next](modern-events.md)
