---
title: Standart .NET olay desenleri
description: .NET olay desenleri ve abone standart olay kaynakları oluşturmak ve kodunuzun içinde standart olayları işleme hakkında daha fazla bilgi edinin.
ms.date: 06/20/2016
ms.assetid: 8a3133d6-4ef2-46f9-9c8d-a8ea8898e4c9
ms.openlocfilehash: cd1ead318529d1afc5b27ff8710cebcaae9b7bc3
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65062960"
---
# <a name="standard-net-event-patterns"></a><span data-ttu-id="f2939-103">Standart .NET olay desenleri</span><span class="sxs-lookup"><span data-stu-id="f2939-103">Standard .NET event patterns</span></span>

[<span data-ttu-id="f2939-104">Önceki</span><span class="sxs-lookup"><span data-stu-id="f2939-104">Previous</span></span>](events-overview.md)

<span data-ttu-id="f2939-105">.NET etkinliklerini genellikle birkaç bilinen desenleri takip edin.</span><span class="sxs-lookup"><span data-stu-id="f2939-105">.NET events generally follow a few known patterns.</span></span> <span data-ttu-id="f2939-106">Bu eğilimlere Standartlaştırma, geliştiricilerin, .NET olay programıyla uygulanabilir bu standart desenlerinin bilgi yararlanabileceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f2939-106">Standardizing on these patterns means that developers can leverage knowledge of those standard patterns, which can be applied to any .NET event program.</span></span>

<span data-ttu-id="f2939-107">Bu standart desenleri standart olay kaynakları oluşturmak ve abone olma ve kodunuzda standart olayları işlemek için ihtiyaç duyduğunuz tüm bilgisine sahip şekilde Bahsedelim.</span><span class="sxs-lookup"><span data-stu-id="f2939-107">Let's go through these standard patterns so you will have all the knowledge you need to create standard event sources, and subscribe and process standard events in your code.</span></span>

## <a name="event-delegate-signatures"></a><span data-ttu-id="f2939-108">Olay temsilci imzaları</span><span class="sxs-lookup"><span data-stu-id="f2939-108">Event Delegate Signatures</span></span>

<span data-ttu-id="f2939-109">Standart .NET olay temsilci imzası verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="f2939-109">The standard signature for a .NET event delegate is:</span></span>

```csharp
void OnEventRaised(object sender, EventArgs args);
```

<span data-ttu-id="f2939-110">Dönüş türü void.</span><span class="sxs-lookup"><span data-stu-id="f2939-110">The return type is void.</span></span> <span data-ttu-id="f2939-111">Olaylar, temsilciler üzerinde temel alır ve çok noktaya yayın temsilcileri, bir.</span><span class="sxs-lookup"><span data-stu-id="f2939-111">Events are based on delegates and are multicast delegates.</span></span> <span data-ttu-id="f2939-112">Herhangi bir olay kaynağı için birden fazla aboneye destekleyen.</span><span class="sxs-lookup"><span data-stu-id="f2939-112">That supports multiple subscribers for any event source.</span></span> <span data-ttu-id="f2939-113">Tek bir yöntemin dönüş değeri için birden fazla olay abonesi ölçeklendirilemez.</span><span class="sxs-lookup"><span data-stu-id="f2939-113">The single return value from a method doesn't scale to multiple event subscribers.</span></span> <span data-ttu-id="f2939-114">Olay kaynağı bakın, dönüş değeri bir olayı tetiklenmeden sonra mu?</span><span class="sxs-lookup"><span data-stu-id="f2939-114">Which return value does the event source see after raising an event?</span></span> <span data-ttu-id="f2939-115">Bu makalenin sonraki bölümlerinde etkinlik abonelerinden destekleyen olay protokolleri oluşturma olay kaynağı bu rapor bilgileri görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="f2939-115">Later in this article you'll see how to create event protocols that support event subscribers that report information to the event source.</span></span>

<span data-ttu-id="f2939-116">İki bağımsız değişken bağımsız değişken listesi içeriyor: göndereni ve olay bağımsız değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="f2939-116">The argument list contains two arguments: the sender, and the event arguments.</span></span> <span data-ttu-id="f2939-117">Derleme zamanı türü `sender` olduğu `System.Object`, büyük olasılıkla her zaman doğru olmayacak daha türetilmiş türde bildiğiniz olsa bile.</span><span class="sxs-lookup"><span data-stu-id="f2939-117">The compile time type of `sender` is `System.Object`, even though you likely know a more derived type that would always be correct.</span></span> <span data-ttu-id="f2939-118">Kural gereği, kullanın `object`.</span><span class="sxs-lookup"><span data-stu-id="f2939-118">By convention, use `object`.</span></span>

<span data-ttu-id="f2939-119">İkinci bağımsız değişkeni genellikle tan türetilmiş bir tür olan `System.EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="f2939-119">The second argument has typically been a type that is derived from `System.EventArgs`.</span></span> <span data-ttu-id="f2939-120">(Görüşelim [sonraki bölümde](modern-events.md) , bu kural artık zorlanmamaktadır.) Herhangi bir ek bağımsız değişken, olay türü gereksinimi yoksa, yine de her iki değişken sağlar.</span><span class="sxs-lookup"><span data-stu-id="f2939-120">(You'll see in the [next section](modern-events.md) that this convention is no longer enforced.) If your event type does not need any additional arguments, you will still provide both arguments.</span></span>
<span data-ttu-id="f2939-121">Özel bir değer `EventArgs.Empty` etkinliğiniz herhangi ek bir bilgi içermediğini belirtmek için kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f2939-121">There is a special value, `EventArgs.Empty` that you should use to denote that your event does not contain any additional information.</span></span>

<span data-ttu-id="f2939-122">Şimdi bir dizin ya da herhangi bir düzen izleyen dizinlerinden dosyaları listeleyen bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f2939-122">Let's build a class that lists files in a directory, or any of its subdirectories that follow a pattern.</span></span> <span data-ttu-id="f2939-123">Bu bileşen, deseni, eşleşen her dosya bulundu için bir olay başlatır.</span><span class="sxs-lookup"><span data-stu-id="f2939-123">This component raises an event for each file found that matches the pattern.</span></span>

<span data-ttu-id="f2939-124">Bir olay modeli kullanarak bazı tasarım avantajları sağlar.</span><span class="sxs-lookup"><span data-stu-id="f2939-124">Using an event model provides some design advantages.</span></span> <span data-ttu-id="f2939-125">Aranan bir dosya bulunduğunda, farklı eylemler gerçekleştirmesini birden çok olay dinleyicileri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2939-125">You can create multiple event listeners that perform different actions when a sought file is found.</span></span> <span data-ttu-id="f2939-126">Farklı dinleyicileri birleştirerek daha güçlü algoritmalar oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2939-126">Combining the different listeners can create more robust algorithms.</span></span>

<span data-ttu-id="f2939-127">Aranan bir dosyayı bulmak için ilk olay bağımsız değişkeni bildirimi şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="f2939-127">Here is the initial event argument declaration for finding a sought file:</span></span> 

[!code-csharp[EventArgs](../../samples/csharp/events/Program.cs#EventArgsV1 "Define event arguments")]

<span data-ttu-id="f2939-128">Bu tür bir küçük, yalnızca veri türü gibi görünse de, kuralını izler ve bir başvuru yapmak gerekir (`class`) türü.</span><span class="sxs-lookup"><span data-stu-id="f2939-128">Even though this type looks like a small, data-only type, you should follow the convention and make it a reference (`class`) type.</span></span> <span data-ttu-id="f2939-129">Bu başvuruya göre bağımsız değişken nesnesi geçirilir ve verilere herhangi bir güncelleştirme tüm aboneler tarafından görüntülenecek anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f2939-129">That means the argument object will be passed by reference, and any updates to the data will be viewed by all subscribers.</span></span> <span data-ttu-id="f2939-130">İlk sürüm değişmez bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="f2939-130">The first version is an immutable object.</span></span> <span data-ttu-id="f2939-131">Olay bağımsız değişkeni türünüz özellikleri değişmez yapmak tercih etmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="f2939-131">You should prefer to make the properties in your event argument type immutable.</span></span> <span data-ttu-id="f2939-132">Bu şekilde, başka bir aboneyi bunları görmeden bir abone değerlerini değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2939-132">That way, one subscriber cannot change the values before another subscriber sees them.</span></span> <span data-ttu-id="f2939-133">(İstisnaları vardır, aşağıda anlatıldığı gibi.)</span><span class="sxs-lookup"><span data-stu-id="f2939-133">(There are exceptions to this, as you'll see below.)</span></span>  

<span data-ttu-id="f2939-134">Ardından, biz FileSearcher sınıfında olay bildirimi oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f2939-134">Next, we need to create the event declaration in the FileSearcher class.</span></span> <span data-ttu-id="f2939-135">Yararlanarak `EventHandler<T>` türü gösterir bir başka tür tanımı oluşturmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="f2939-135">Leveraging the `EventHandler<T>` type means that you don't need to create yet another type definition.</span></span> <span data-ttu-id="f2939-136">Sadece genel özelleştirmesi kullanın.</span><span class="sxs-lookup"><span data-stu-id="f2939-136">You simply use a generic specialization.</span></span>

<span data-ttu-id="f2939-137">Şimdi bir desenle eşleşen dosyaları aramak için FileSearcher sınıfı doldurun ve bir eşleşme bulunduğunda doğru olayı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f2939-137">Let's fill out the FileSearcher class to search for files that match a pattern, and raise the correct event when a match is discovered.</span></span>

[!code-csharp[FileSearcher](../../samples/csharp/events/Program.cs#FileSearcherV1 "Create the initial file searcher")]

## <a name="defining-and-raising-field-like-events"></a><span data-ttu-id="f2939-138">Tanımlama ve alan benzeri olaylara oluşturma</span><span class="sxs-lookup"><span data-stu-id="f2939-138">Defining and Raising Field-Like Events</span></span>

<span data-ttu-id="f2939-139">En basit yolu, sınıfa olaya eklemek için önceki örnekte olduğu gibi genel bir alan olarak olay bildirmek için verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="f2939-139">The simplest way to add an event to your class is to declare that event as a public field, as in the preceding example:</span></span>

[!code-csharp[DeclareEvent](../../samples/csharp/events/Program.cs#DeclareEvent "Declare the file found event")]

<span data-ttu-id="f2939-140">Hatalı nesne yönelimli bir uygulama olarak görünebilir bir ortak alan bildirme görülüyor.</span><span class="sxs-lookup"><span data-stu-id="f2939-140">This looks like it's declaring a public field, which would appear to be bad object-oriented practice.</span></span> <span data-ttu-id="f2939-141">Özellikleri veya yöntemleri aracılığıyla veri erişimi korumak istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="f2939-141">You want to protect data access through properties, or methods.</span></span> <span data-ttu-id="f2939-142">Bu, hatalı bir uygulama gibi görünebilir, ancak derleyici tarafından oluşturulan kodu olay nesneleri yalnızca güvenli şekilde erişilebilir olacak şekilde sarmalayıcıları oluşturma.</span><span class="sxs-lookup"><span data-stu-id="f2939-142">While this may look like a bad practice, the code generated by the compiler does create wrappers so that the event objects can only be accessed in safe ways.</span></span> <span data-ttu-id="f2939-143">Yalnızca kullanılabilir işlemleri bir alan benzeri olayı işleyicisi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f2939-143">The only operations available on a field-like event are add handler:</span></span>

[!code-csharp[DeclareEventHandler](../../samples/csharp/events/Program.cs#DeclareEventHandler "Declare the file found event handler")]

<span data-ttu-id="f2939-144">ve işleyiciyi kaldırın:</span><span class="sxs-lookup"><span data-stu-id="f2939-144">and remove handler:</span></span>

[!code-csharp[RemoveEventHandler](../../samples/csharp/events/Program.cs#RemoveHandler "Remove the event handler")]

<span data-ttu-id="f2939-145">İşleyici için bir yerel değişken olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="f2939-145">Note that there's a local variable for the handler.</span></span> <span data-ttu-id="f2939-146">Lambda gövdesi kullandıysanız Kaldır düzgün çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="f2939-146">If you used the body of the lambda, the remove would not work correctly.</span></span> <span data-ttu-id="f2939-147">Metot temsilcisinin farklı bir örneği olması ve sessizce hiçbir şey yapma.</span><span class="sxs-lookup"><span data-stu-id="f2939-147">It would be a different instance of the delegate, and silently do nothing.</span></span>

<span data-ttu-id="f2939-148">Sınıf dışındaki kod olay oluşturamaz veya diğer tüm işlemleri gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="f2939-148">Code outside the class cannot raise the event, nor can it perform any other operations.</span></span>

## <a name="returning-values-from-event-subscribers"></a><span data-ttu-id="f2939-149">Etkinlik Abonelerinden değerler döndüren</span><span class="sxs-lookup"><span data-stu-id="f2939-149">Returning Values from Event Subscribers</span></span>

<span data-ttu-id="f2939-150">Basit sürümünüzü düzgün çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="f2939-150">Your simple version is working fine.</span></span> <span data-ttu-id="f2939-151">Başka bir özellik ekleyelim: İptali.</span><span class="sxs-lookup"><span data-stu-id="f2939-151">Let's add another feature: Cancellation.</span></span>

<span data-ttu-id="f2939-152">Bulunan olay yükselttiğinizde, bu dosya, sonuncu Aranan ise dinleyicileri daha fazla işleme, durdurmak için olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f2939-152">When you raise the found event, listeners should be able to stop further processing, if this file is that last one sought.</span></span>

<span data-ttu-id="f2939-153">Bu nedenle, başka bir biçimde iletişim kurmasına olanak gerekir olay işleyicileri bir değer döndürmeyen.</span><span class="sxs-lookup"><span data-stu-id="f2939-153">The event handlers do not return a value, so you need to communicate that in another way.</span></span> <span data-ttu-id="f2939-154">Standart olay deseni EventArgs etkinlik abonelerinden iptal iletişim kurmak için kullanabileceğiniz alanlar dahil etmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="f2939-154">The standard event pattern uses the EventArgs object to include fields that event subscribers can use to communicate cancel.</span></span>

<span data-ttu-id="f2939-155">İptal sözleşmenin semantiği göre kullanılabilecek iki farklı deseni vardır.</span><span class="sxs-lookup"><span data-stu-id="f2939-155">There are two different patterns that could be used, based on the semantics of the Cancel contract.</span></span> <span data-ttu-id="f2939-156">Her iki durumda da EventArguments bulunan dosyayı olayı için bir Boole alanı ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="f2939-156">In both cases, you'll add a boolean field to the EventArguments for the found file event.</span></span> 

<span data-ttu-id="f2939-157">Bir desen işlemi iptal etmek herhangi bir abone çalıştırmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="f2939-157">One pattern would allow any one subscriber to cancel the operation.</span></span>
<span data-ttu-id="f2939-158">Bu düzeni için yeni alan değerine ayarlanır `false`.</span><span class="sxs-lookup"><span data-stu-id="f2939-158">For this pattern, the new field is initialized to `false`.</span></span> <span data-ttu-id="f2939-159">Her abone için değiştirebilirsiniz `true`.</span><span class="sxs-lookup"><span data-stu-id="f2939-159">Any subscriber can change it to `true`.</span></span> <span data-ttu-id="f2939-160">Tüm aboneler tetiklenen olayı gördünüz sonra FileSearcher bileşen Boole değeri inceler ve eylemi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="f2939-160">After all subscribers have seen the event raised, the FileSearcher component examines the boolean value and takes action.</span></span>

<span data-ttu-id="f2939-161">Tüm aboneler İptal işlemi isterseniz ikinci desen yalnızca işlem iptal.</span><span class="sxs-lookup"><span data-stu-id="f2939-161">The second pattern would only cancel the operation if all subscribers wanted the operation cancelled.</span></span> <span data-ttu-id="f2939-162">Bu düzende, yeni alan işlemi iptal etmesi gerekir ve işlem devam belirtmek için herhangi bir abone değiştirebilir belirtmek için başlatılır.</span><span class="sxs-lookup"><span data-stu-id="f2939-162">In this pattern, the new field is initialized to indicate the operation should cancel, and any subscriber could change it to indicate the operation should continue.</span></span>
<span data-ttu-id="f2939-163">Tüm aboneler tetiklenen olayı gördünüz sonra FileSearcher bileşen boolean inceler ve eylemi alır.</span><span class="sxs-lookup"><span data-stu-id="f2939-163">After all subscribers have seen the event raised, the FileSearcher component examines the boolean and takes action.</span></span> <span data-ttu-id="f2939-164">Bu modelde ek bir adım yoktur: bileşen olayın tüm abonelerine gördünüz mü bilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="f2939-164">There is one extra step in this pattern: the component needs to know if any subscribers have seen the event.</span></span> <span data-ttu-id="f2939-165">Abone varsa, alan iptal yanlış gösterir.</span><span class="sxs-lookup"><span data-stu-id="f2939-165">If there are no subscribers, the field would indicate a cancel incorrectly.</span></span>

<span data-ttu-id="f2939-166">Bu örnek için ilk sürümü şimdi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="f2939-166">Let's implement the first version for this sample.</span></span> <span data-ttu-id="f2939-167">Adlı bir Boole alanı eklemeniz `CancelRequested` için `FileFoundArgs` türü:</span><span class="sxs-lookup"><span data-stu-id="f2939-167">You need to add a boolean field named `CancelRequested` to the `FileFoundArgs` type:</span></span>

[!code-csharp[EventArgs](../../samples/csharp/events/Program.cs#EventArgs "Update event arguments")]

<span data-ttu-id="f2939-168">Bu yeni alan için otomatik olarak başlatılır `false`, yanlışlıkla iptal etme için mantıksal bir alan için varsayılan değer.</span><span class="sxs-lookup"><span data-stu-id="f2939-168">This new Field is automatically initialized to `false`, the default value for a Boolean field, so you don't cancel accidentally.</span></span> <span data-ttu-id="f2939-169">Diğer değişiklik bileşenine abonelerin herhangi bir iptal isteğinde olmadığını görmek için olayın yükseltme sonrasında bayrağı denetlemektir.</span><span class="sxs-lookup"><span data-stu-id="f2939-169">The only other change to the component is to check the flag after raising the event to see if any of the subscribers have requested a cancellation:</span></span>

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

<span data-ttu-id="f2939-170">Bu düzenin bir avantajı, bir değişiklik olmadığından emin olmanızdır.</span><span class="sxs-lookup"><span data-stu-id="f2939-170">One advantage of this pattern is that it isn't a breaking change.</span></span>
<span data-ttu-id="f2939-171">Abonelerin hiçbiri önce bir iptal isteğinde ve bunlar değil.</span><span class="sxs-lookup"><span data-stu-id="f2939-171">None of the subscribers requested a cancellation before, and they still are not.</span></span> <span data-ttu-id="f2939-172">Abone kod hiçbiri yeni iptal protokolünü destekleyen istemiyorsanız güncelleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="f2939-172">None of the subscriber code needs updating unless they want to support the new cancel protocol.</span></span> <span data-ttu-id="f2939-173">Bu çok birbirine sıkı şekilde bağlı.</span><span class="sxs-lookup"><span data-stu-id="f2939-173">It's very loosely coupled.</span></span>

<span data-ttu-id="f2939-174">Şimdi ilk yürütülebilir bulduğunda iptal ister. böylece abone güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="f2939-174">Let's update the subscriber so that it requests a cancellation once it finds the first executable:</span></span>

```csharp
EventHandler<FileFoundArgs> onFileFound = (sender, eventArgs) =>
{
    Console.WriteLine(eventArgs.FoundFile);
    eventArgs.CancelRequested = true;
};
```

## <a name="adding-another-event-declaration"></a><span data-ttu-id="f2939-175">Başka bir olay bildirimi ekleme</span><span class="sxs-lookup"><span data-stu-id="f2939-175">Adding Another Event Declaration</span></span>

<span data-ttu-id="f2939-176">Şimdi bir daha fazla özellik eklemek ve diğer dil deyimleri olayları gösterir.</span><span class="sxs-lookup"><span data-stu-id="f2939-176">Let's add one more feature, and demonstrate other language idioms for events.</span></span> <span data-ttu-id="f2939-177">Bir aşırı yüklemesini ekleyelim `Search` tüm alt dizinlerde dosyaları saldırılar trafiğiyle yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f2939-177">Let's add an overload of the `Search` method that traverses all subdirectories in search of files.</span></span>

<span data-ttu-id="f2939-178">Bu, bir dizinde birden çok alt dizini ile uzun bir işlem olarak alabilir.</span><span class="sxs-lookup"><span data-stu-id="f2939-178">This could get to be a lengthy operation in a directory with many sub-directories.</span></span> <span data-ttu-id="f2939-179">Her yeni dizin araması başladığında bir olayı ekleyelim.</span><span class="sxs-lookup"><span data-stu-id="f2939-179">Let's add an event that gets raised when each new directory search begins.</span></span> <span data-ttu-id="f2939-180">Bu, ilerlemeyi izlemek ve ilerleme için kullanıcıyı güncelleştirmek aboneleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="f2939-180">This enables subscribers to track progress, and update the user as to progress.</span></span> <span data-ttu-id="f2939-181">Şu ana kadar oluşturulmuş tüm örnekleri ortak.</span><span class="sxs-lookup"><span data-stu-id="f2939-181">All the samples you've created so far are public.</span></span> <span data-ttu-id="f2939-182">Bu, bir olay olalım.</span><span class="sxs-lookup"><span data-stu-id="f2939-182">Let's make this one an internal event.</span></span> <span data-ttu-id="f2939-183">İç bağımsız değişkenleri de kullanılan türleri de yapabileceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f2939-183">That means you can also make the types used for the arguments internal as well.</span></span>

<span data-ttu-id="f2939-184">Yeni dizine ve ilerlemeyi raporlama için yeni bir EventArgs türetilmiş sınıf oluşturarak başlayacağız.</span><span class="sxs-lookup"><span data-stu-id="f2939-184">You'll start by creating the new EventArgs derived class for reporting the new directory and progress.</span></span> 

[!code-csharp[DirEventArgs](../../samples/csharp/events/Program.cs#SearchDirEventArgs "Define search directory event arguments")]

<span data-ttu-id="f2939-185">Tekrar bir değişmez başvuru türü için olay bağımsız değişkenleri olmak için önerileri takip edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2939-185">Again, you can follow the recommendations to make an immutable reference type for the event arguments.</span></span>

<span data-ttu-id="f2939-186">Ardından, olay tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="f2939-186">Next, define the event.</span></span> <span data-ttu-id="f2939-187">Bu kez, farklı bir sözdizimi kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="f2939-187">This time, you'll use a different syntax.</span></span> <span data-ttu-id="f2939-188">Alan söz dizimini kullanarak ek olarak, açıkça Özellik Ekle ile oluşturma ve işleyicileri kaldırın.</span><span class="sxs-lookup"><span data-stu-id="f2939-188">In addition to using the field syntax, you can explicitly create the property, with add and remove handlers.</span></span> <span data-ttu-id="f2939-189">Bu örnekte bu işleyicileri ek bir kod gerekmez, ancak bunları nasıl oluşturacak bu gösterir.</span><span class="sxs-lookup"><span data-stu-id="f2939-189">In this sample, you won't need extra code in those handlers, but this shows how you would create them.</span></span>

[!code-csharp[Declare event with add and remove handlers](../../samples/csharp/events/Program.cs#DeclareSearchEvent "Declare the event with add and remove handlers")]

<span data-ttu-id="f2939-190">Birçok yolla kod burada alan olay tanımları için derleyici kodu oluşturur yansıtmalar Yaz, daha önce gördünüz.</span><span class="sxs-lookup"><span data-stu-id="f2939-190">In many ways, the code you write here mirrors the code the compiler generates for the field event definitions you've seen earlier.</span></span> <span data-ttu-id="f2939-191">İçin kullanılan çok benzer bir sözdizimi kullanarak olay oluşturma [özellikleri](properties.md).</span><span class="sxs-lookup"><span data-stu-id="f2939-191">You create the event using syntax very similar to that used for [properties](properties.md).</span></span> <span data-ttu-id="f2939-192">İşleyiciler, farklı adlar olduğunu fark edeceksiniz: `add` ve `remove`.</span><span class="sxs-lookup"><span data-stu-id="f2939-192">Notice that the handlers have different names: `add` and `remove`.</span></span> <span data-ttu-id="f2939-193">Bu olaya abone veya olayın aboneliğini kaldırmak için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="f2939-193">These are called to subscribe to the event, or unsubscribe from the event.</span></span> <span data-ttu-id="f2939-194">Ayrıca olay değişkeni depolamak için özel destek alanı bildirmeniz gerekir dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="f2939-194">Notice that you also must declare a private backing field to store the event variable.</span></span> <span data-ttu-id="f2939-195">Null olarak başlatılır.</span><span class="sxs-lookup"><span data-stu-id="f2939-195">It is initialized to null.</span></span>

<span data-ttu-id="f2939-196">Ardından, aşırı yüklemesini ekleyelim `Search` alt dizinleri erişir ve her iki olayı harekete yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f2939-196">Next, let's add the overload of the `Search` method that traverses subdirectories and raises both events.</span></span> <span data-ttu-id="f2939-197">Bunu yapmanın en kolay yolu, tüm dizinlerde arama istediğinizi belirtmek için varsayılan bağımsız değişken kullanmaktır:</span><span class="sxs-lookup"><span data-stu-id="f2939-197">The easiest way to accomplish this is to use a default argument to specify that you want to search all directories:</span></span>

[!code-csharp[SearchImplementation](../../samples/csharp/events/Program.cs#FinalImplementation "Implementation to search directories")]

<span data-ttu-id="f2939-198">Bu noktada, tüm alt dizinlerinde arama için aşırı yüklemesini çağırmayı uygulamayı çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2939-198">At this point, you can run the application calling the overload for searching all sub-directories.</span></span> <span data-ttu-id="f2939-199">Yeni abone vardır `ChangeDirectory` olay ancak kullanarak `?.Invoke()` deyim, bu düzgün çalıştığını sağlar.</span><span class="sxs-lookup"><span data-stu-id="f2939-199">There are no subscribers on the new `ChangeDirectory` event, but using the `?.Invoke()` idiom ensures that this works correctly.</span></span>

 <span data-ttu-id="f2939-200">Konsol penceresinde ilerleme durumunu gösteren bir çizgi yazmak için bir işleyici ekleyelim.</span><span class="sxs-lookup"><span data-stu-id="f2939-200">Let's add a handler to write a line that shows the progress in the console window.</span></span> 

[!code-csharp[Search](../../samples/csharp/events/Program.cs#Search "Declare event handler")]

<span data-ttu-id="f2939-201">.NET ekosisteminin izlendiğini desenleri gördünüz.</span><span class="sxs-lookup"><span data-stu-id="f2939-201">You've seen patterns that are followed throughout the .NET ecosystem.</span></span>
<span data-ttu-id="f2939-202">Bu desenleri ve kuralları öğrenerek deyimsel C# ve .NET hızla yazdığınız.</span><span class="sxs-lookup"><span data-stu-id="f2939-202">By learning these patterns and conventions, you'll be writing idiomatic C# and .NET quickly.</span></span>

<span data-ttu-id="f2939-203">Ardından, bu desenleri .NET en son sürümünde bazı değişiklikler görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="f2939-203">Next, you'll see some changes in these patterns in the most recent release of .NET.</span></span>

[<span data-ttu-id="f2939-204">Next</span><span class="sxs-lookup"><span data-stu-id="f2939-204">Next</span></span>](modern-events.md)
