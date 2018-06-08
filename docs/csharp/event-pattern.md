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
# <a name="standard-net-event-patterns"></a><span data-ttu-id="1500e-103">Standart .NET olay desenleri</span><span class="sxs-lookup"><span data-stu-id="1500e-103">Standard .NET event patterns</span></span>

[<span data-ttu-id="1500e-104">Önceki</span><span class="sxs-lookup"><span data-stu-id="1500e-104">Previous</span></span>](events-overview.md)

<span data-ttu-id="1500e-105">.NET olaylar genellikle birkaç bilinen desenlerini izleyin.</span><span class="sxs-lookup"><span data-stu-id="1500e-105">.NET events generally follow a few known patterns.</span></span> <span data-ttu-id="1500e-106">Bu düzenleri üzerinde Standartlaştırma, geliştiricilerin bilgi .NET olay programlarından uygulanabilir bu standart desenlerinin yararlanabilirsiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="1500e-106">Standardizing on these patterns means that developers can leverage knowledge of those standard patterns, which can be applied to any .NET event program.</span></span>

<span data-ttu-id="1500e-107">Bu standart desenleri standart olay kaynakları oluşturmanız ve abone olma ve kodunuzda standart olayları işlemek için gereken tüm bilgisine sahip şekilde edelim.</span><span class="sxs-lookup"><span data-stu-id="1500e-107">Let's go through these standard patterns so you will have all the knowledge you need to create standard event sources, and subscribe and process standard events in your code.</span></span>

## <a name="event-delegate-signatures"></a><span data-ttu-id="1500e-108">Olay temsilci imzaları</span><span class="sxs-lookup"><span data-stu-id="1500e-108">Event Delegate Signatures</span></span>

<span data-ttu-id="1500e-109">Bir .NET olay temsilci için standart imza şöyledir:</span><span class="sxs-lookup"><span data-stu-id="1500e-109">The standard signature for a .NET event delegate is:</span></span>

```csharp
void OnEventRaised(object sender, EventArgs args);
```

<span data-ttu-id="1500e-110">Dönüş türü void ' dir.</span><span class="sxs-lookup"><span data-stu-id="1500e-110">The return type is void.</span></span> <span data-ttu-id="1500e-111">Olaylar temsilciler üzerinde temel alır ve çok noktaya yayın temsilcileri.</span><span class="sxs-lookup"><span data-stu-id="1500e-111">Events are based on delegates and are multicast delegates.</span></span> <span data-ttu-id="1500e-112">Tüm olay kaynağı için birden çok aboneye destekleyen.</span><span class="sxs-lookup"><span data-stu-id="1500e-112">That supports multiple subscribers for any event source.</span></span> <span data-ttu-id="1500e-113">Bir yöntem gelen tek bir dönüş değeri için birden çok olay aboneye ölçeklendirilmediğini.</span><span class="sxs-lookup"><span data-stu-id="1500e-113">The single return value from a method doesn't scale to multiple event subscribers.</span></span> <span data-ttu-id="1500e-114">Hangi dönüş değeri, bir olayı tetiklenmeden sonra olay kaynağı bakın mu?</span><span class="sxs-lookup"><span data-stu-id="1500e-114">Which return value does the event source see after raising an event?</span></span> <span data-ttu-id="1500e-115">Bu makalenin sonraki bölümlerinde, olay kaynağı için bu raporu bilgileri olay aboneleri destek olay protokolleri oluşturma görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="1500e-115">Later in this article you'll see how to create event protocols that support event subscribers that report information to the event source.</span></span>

<span data-ttu-id="1500e-116">İki bağımsız değişken listesi içerir: gönderici ve olay bağımsız değişkenler.</span><span class="sxs-lookup"><span data-stu-id="1500e-116">The argument list contains two arguments: the sender, and the event arguments.</span></span> <span data-ttu-id="1500e-117">Derleme zamanı türünün `sender` olan `System.Object`, büyük olasılıkla her zaman doğru olacak daha fazla türetilmiş bir tür bildiğiniz olsa bile.</span><span class="sxs-lookup"><span data-stu-id="1500e-117">The compile time type of `sender` is `System.Object`, even though you likely know a more derived type that would always be correct.</span></span> <span data-ttu-id="1500e-118">Kurala göre kullanmak `object`.</span><span class="sxs-lookup"><span data-stu-id="1500e-118">By convention, use `object`.</span></span>

<span data-ttu-id="1500e-119">İkinci bağımsız değişkeni genellikle türetilmiş bir tür bırakıldı `System.EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="1500e-119">The second argument has typically been a type that is derived from `System.EventArgs`.</span></span> <span data-ttu-id="1500e-120">(İçinde görürsünüz [sonraki bölümde](modern-events.md) , bu kural artık uygulanmaz.) Olay türü herhangi bir ek bağımsız değişkeni gerekli değildir, her iki değişken hala sağlayacaktır.</span><span class="sxs-lookup"><span data-stu-id="1500e-120">(You'll see in the [next section](modern-events.md) that this convention is no longer enforced.) If your event type does not need any additional arguments, you will still provide both arguments.</span></span>
<span data-ttu-id="1500e-121">Özel bir değer `EventArgs.Empty` , olay ek bilgileri içermiyor belirtmek için kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1500e-121">There is a special value, `EventArgs.Empty` that you should use to denote that your event does not contain any additional information.</span></span>

<span data-ttu-id="1500e-122">Şimdi bir dizin ya da herhangi bir yol izler dizinlerinden dosyaları listeleyen bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1500e-122">Let's build a class that lists files in a directory, or any of its subdirectories that follow a pattern.</span></span> <span data-ttu-id="1500e-123">Desenle eşleşen her bir dosya bulunduğunda bu bileşen bir olay başlatır.</span><span class="sxs-lookup"><span data-stu-id="1500e-123">This component raises an event for each file found that matches the pattern.</span></span>

<span data-ttu-id="1500e-124">Bir olay modelini kullanarak bazı tasarım avantajlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="1500e-124">Using an event model provides some design advantages.</span></span> <span data-ttu-id="1500e-125">Aranan dosya bulunduğunda, farklı eylemler gerçekleştiren birden çok olay dinleyicileri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1500e-125">You can create multiple event listeners that perform different actions when a sought file is found.</span></span> <span data-ttu-id="1500e-126">Farklı dinleyicileri birleştirerek daha sağlam algoritmaları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1500e-126">Combining the different listeners can create more robust algorithms.</span></span>

<span data-ttu-id="1500e-127">İlk olay bağımsız değişken bildirimi'Aranan dosyasını bulmak için aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="1500e-127">Here is the initial event argument declaration for finding a sought file:</span></span> 

[!code-csharp[EventArgs](../../samples/csharp/events/Program.cs#EventArgsV1 "Define event arguments")]

<span data-ttu-id="1500e-128">Bu tür bir küçük, yalnızca veri türü gibi görünse kuralını izler ve bir başvuru yapmak gerekir (`class`) yazın.</span><span class="sxs-lookup"><span data-stu-id="1500e-128">Even though this type looks like a small, data-only type, you should follow the convention and make it a reference (`class`) type.</span></span> <span data-ttu-id="1500e-129">Başvuruya göre bağımsız değişken nesne geçirilir ve verileri herhangi bir güncelleştirme tüm aboneler tarafından görüntülenecek anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="1500e-129">That means the argument object will be passed by reference, and any updates to the data will be viewed by all subscribers.</span></span> <span data-ttu-id="1500e-130">İlk sürümü değişmez bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="1500e-130">The first version is an immutable object.</span></span> <span data-ttu-id="1500e-131">Özellikler, olay bağımsız değişken türü değişmez yapmak tercih etmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="1500e-131">You should prefer to make the properties in your event argument type immutable.</span></span> <span data-ttu-id="1500e-132">Bu şekilde, başka bir abonelik bunları görmeden bir abonesi değerleri değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="1500e-132">That way, one subscriber cannot change the values before another subscriber sees them.</span></span> <span data-ttu-id="1500e-133">(Bu, özel durumlar aşağıda göreceğiniz gibi vardır.)</span><span class="sxs-lookup"><span data-stu-id="1500e-133">(There are exceptions to this, as you'll see below.)</span></span>  

<span data-ttu-id="1500e-134">Ardından, biz olay bildirimi FileSearcher sınıfında oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1500e-134">Next, we need to create the event declaration in the FileSearcher class.</span></span> <span data-ttu-id="1500e-135">Yararlanarak `EventHandler<T>` türü anlamına gelir henüz başka bir tür tanımı oluşturmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="1500e-135">Leveraging the `EventHandler<T>` type means that you don't need to create yet another type definition.</span></span> <span data-ttu-id="1500e-136">Yalnızca genel uzmanlık kullanın.</span><span class="sxs-lookup"><span data-stu-id="1500e-136">You simply use a generic specialization.</span></span>

<span data-ttu-id="1500e-137">Şimdi bir desenle eşleşen dosyaları aramak için FileSearcher sınıfı doldurun ve bir eşleşme bulunduğunda doğru olayı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1500e-137">Let's fill out the FileSearcher class to search for files that match a pattern, and raise the correct event when a match is discovered.</span></span>

[!code-csharp[FileSearxcher](../../samples/csharp/events/Program.cs#FileSearcherV1 "Create the initial file searcher")]

## <a name="definining-and-raising-field-like-events"></a><span data-ttu-id="1500e-138">Definining ve alan benzeri olayları</span><span class="sxs-lookup"><span data-stu-id="1500e-138">Definining and Raising Field-Like Events</span></span>

<span data-ttu-id="1500e-139">En basit yolu, sınıf için bir olay eklemek için önceki örnekte olduğu gibi ortak bir alan olarak olay bildirmektir:</span><span class="sxs-lookup"><span data-stu-id="1500e-139">The simplest way to add an event to your class is to declare that event as a public field, as in the preceding example:</span></span>

[!code-csharp[DeclareEvent](../../samples/csharp/events/Program.cs#DeclareEvent "Declare the file found event")]

<span data-ttu-id="1500e-140">Bu durum, hatalı nesne yönelimli uygulama olarak görüneceği bir ortak alan bildirme görülüyor.</span><span class="sxs-lookup"><span data-stu-id="1500e-140">This looks like it's declaring a public field, which would appear to be bad object-oriented practice.</span></span> <span data-ttu-id="1500e-141">Veri erişimi özelliklerinin veya yöntemlerin aracılığıyla korumak istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="1500e-141">You want to protect data access through properties, or methods.</span></span> <span data-ttu-id="1500e-142">Bunu yaparken böylece olay nesneleri yalnızca güvenli şekilde erişilebilir hatalı bir uygulama, derleyici tarafından oluşturulan kodu sarmalayıcıları oluşturma gibi arayın.</span><span class="sxs-lookup"><span data-stu-id="1500e-142">While this make look like a bad practice, the code generated by the compiler does create wrappers so that the event objects can only be accessed in safe ways.</span></span> <span data-ttu-id="1500e-143">Yalnızca kullanılabilir işlemleri alan benzeri olay işleyicisi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1500e-143">The only operations available on a field-like event are add handler:</span></span>

[!code-csharp[DeclareEventHandler](../../samples/csharp/events/Program.cs#DeclareEventHandler "Declare the file found event handler")]

<span data-ttu-id="1500e-144">ve işleyici kaldırın:</span><span class="sxs-lookup"><span data-stu-id="1500e-144">and remove handler:</span></span>

[!code-csharp[RemoveEventHandler](../../samples/csharp/events/Program.cs#RemoveHandler "Remove the event handler")]

<span data-ttu-id="1500e-145">İşleyici için bir yerel değişken olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="1500e-145">Note that there's a local variable for the handler.</span></span> <span data-ttu-id="1500e-146">Lambda gövdesi kullandıysanız, Kaldır düzgün çalışır değil.</span><span class="sxs-lookup"><span data-stu-id="1500e-146">If you used the body of the lambda, the remove would not work correctly.</span></span> <span data-ttu-id="1500e-147">Temsilci farklı bir örneğine olması ve sessiz bir şekilde hiçbir şey yapma.</span><span class="sxs-lookup"><span data-stu-id="1500e-147">It would be a different instance of the delegate, and silently do nothing.</span></span>

<span data-ttu-id="1500e-148">Sınıf dışındaki kodu olay oluşturamaz veya diğer işlemler gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1500e-148">Code outside the class cannot raise the event, nor can it perform any other operations.</span></span>

## <a name="returning-values-from-event-subscribers"></a><span data-ttu-id="1500e-149">Olay aboneleri dönüş değerleri</span><span class="sxs-lookup"><span data-stu-id="1500e-149">Returning Values from Event Subscribers</span></span>

<span data-ttu-id="1500e-150">Basit sürümünüzü düzgün çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="1500e-150">Your simple version is working fine.</span></span> <span data-ttu-id="1500e-151">Başka bir özellik ekleyelim: iptali.</span><span class="sxs-lookup"><span data-stu-id="1500e-151">Let's add another feature: Cancellation.</span></span>

<span data-ttu-id="1500e-152">Bulunan olay yükselttiğinizde, bu dosyayı son Aranan ise dinleyicileri başka bir işleme, durdurmak mümkün olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1500e-152">When you raise the found event, listeners should be able to stop further processing, if this file is that last one sought.</span></span>

<span data-ttu-id="1500e-153">Olay işleyicileri, başka bir şekilde iletişim kurması gereken şekilde bir değer döndürmeyen.</span><span class="sxs-lookup"><span data-stu-id="1500e-153">The event handlers do not return a value, so you need to communicate that in another way.</span></span> <span data-ttu-id="1500e-154">Standart olay deseni EventArgs nesne olay aboneleri iptal iletişim kurmak için kullanabileceği alan eklemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="1500e-154">The standard event pattern uses the EventArgs object to include fields that event subscribers can use to communicate cancel.</span></span>

<span data-ttu-id="1500e-155">İptal sözleşme semantiği dayalı kullanılabilecek iki farklı modeli vardır.</span><span class="sxs-lookup"><span data-stu-id="1500e-155">There are two different patterns that could be used, based on the semantics of the Cancel contract.</span></span> <span data-ttu-id="1500e-156">Her iki durumda da EventArguments bulunan dosya olayı için bir Boole alanı eklenecektir.</span><span class="sxs-lookup"><span data-stu-id="1500e-156">In both cases, you'll add a boolean field to the EventArguments for the found file event.</span></span> 

<span data-ttu-id="1500e-157">Bir desen işlemi iptal etmek herhangi bir abonesi olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="1500e-157">One pattern would allow any one subscriber to cancel the operation.</span></span>
<span data-ttu-id="1500e-158">Bu model için yeni alan için başlatılmış `false`.</span><span class="sxs-lookup"><span data-stu-id="1500e-158">For this pattern, the new field is initialized to `false`.</span></span> <span data-ttu-id="1500e-159">Her abonesi değiştirebilirsiniz `true`.</span><span class="sxs-lookup"><span data-stu-id="1500e-159">Any subscriber can change it to `true`.</span></span> <span data-ttu-id="1500e-160">Tüm aboneleri olay gerçekleşti gördünüz sonra FileSearcher bileşen boolean değeri inceler ve eylem gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="1500e-160">After all subscribers have seen the event raised, the FileSearcher component examines the boolean value and takes action.</span></span>

<span data-ttu-id="1500e-161">Tüm aboneleri işlem iptal edildi istediyseniz ikinci deseni yalnızca işlemi iptal etmek.</span><span class="sxs-lookup"><span data-stu-id="1500e-161">The second pattern would only cancel the operation if all subscribers wanted the operation cancelled.</span></span> <span data-ttu-id="1500e-162">Bu modelinde işlemi iptal ve her abonesi işlemi devam etmesi gerektiğini belirtmek için değiştirebilir göstermek için yeni alan başlatılır.</span><span class="sxs-lookup"><span data-stu-id="1500e-162">In this pattern, the new field is initialized to indicate the operation should cancel, and any subscriber could change it to indicate the operation should continue.</span></span>
<span data-ttu-id="1500e-163">Tüm aboneleri olay gerçekleşti gördünüz sonra FileSearcher bileşen boolean inceler ve eylem gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="1500e-163">After all subscribers have seen the event raised, the FileSearcher component examines the boolean and takes action.</span></span> <span data-ttu-id="1500e-164">Bu desen bir ek adım vardır: bileşen, tüm aboneler bir olay gördünüz bilmek ister.</span><span class="sxs-lookup"><span data-stu-id="1500e-164">There is one extra step in this pattern: the component needs to know if any subscribers have seen the event.</span></span> <span data-ttu-id="1500e-165">Abone yoksa, alanın bir iptal yanlış gösterir.</span><span class="sxs-lookup"><span data-stu-id="1500e-165">If there are no subscribers, the field would indicate a cancel incorrectly.</span></span>

<span data-ttu-id="1500e-166">Şimdi bu örnek için ilk sürüm uygulayın.</span><span class="sxs-lookup"><span data-stu-id="1500e-166">Let's implement the first version for this sample.</span></span> <span data-ttu-id="1500e-167">Adlı bir boolean alanı eklemeniz `CancelRequested` için `FileFoundArgs` türü:</span><span class="sxs-lookup"><span data-stu-id="1500e-167">You need to add a boolean field named `CancelRequested` to the `FileFoundArgs` type:</span></span>

[!code-csharp[EventArgs](../../samples/csharp/events/Program.cs#EventArgs "Update event arguments")]

<span data-ttu-id="1500e-168">Bu yeni alan için otomatik olarak başlatılır `false`, yanlışlıkla iptal etme için bir Boole alanı için varsayılan değer.</span><span class="sxs-lookup"><span data-stu-id="1500e-168">This new Field is automatically initialized to `false`, the default value for a Boolean field, so you don't cancel accidentally.</span></span> <span data-ttu-id="1500e-169">Yalnızca diğer bileşenine aboneleri hiçbirini iptal istenen görmek için olay yükseltme sonrasında bayrağı denetlemek için değişikliktir:</span><span class="sxs-lookup"><span data-stu-id="1500e-169">The only other change to the component is to check the flag after raising the event to see if any of the subscribers have requested a cancellation:</span></span>

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

<span data-ttu-id="1500e-170">Bu desen bir avantajı, önemli bir değişiklik değil ' dir.</span><span class="sxs-lookup"><span data-stu-id="1500e-170">One advantage of this pattern is that it isn't a breaking change.</span></span>
<span data-ttu-id="1500e-171">Aboneleri hiçbiri önce iptal istenir ve bunlar hala değildir.</span><span class="sxs-lookup"><span data-stu-id="1500e-171">None of the subscribers requested a cancellation before, and they still are not.</span></span> <span data-ttu-id="1500e-172">Abone kod hiçbiri yeni iptal protokolünü destekleyen istemedikçe güncelleştirilmesi gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="1500e-172">None of the subscriber code needs updating unless they want to support the new cancel protocol.</span></span> <span data-ttu-id="1500e-173">Çok birbirine sıkı şekilde bağlı.</span><span class="sxs-lookup"><span data-stu-id="1500e-173">It's very loosely coupled.</span></span>

<span data-ttu-id="1500e-174">Şimdi ilk yürütülebilir bulduğunda iptal isteklerini şekilde abone güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="1500e-174">Let's update the subscriber so that it requests a cancellation once it finds the first executable:</span></span>

```csharp
EventHandler<FileFoundArgs> onFileFound = (sender, eventArgs) =>
{
    Console.WriteLine(eventArgs.FoundFile);
    eventArgs.CancelRequested = true;
};
```

## <a name="adding-another-event-declaration"></a><span data-ttu-id="1500e-175">Başka bir olay bildirimi ekleme</span><span class="sxs-lookup"><span data-stu-id="1500e-175">Adding Another Event Declaration</span></span>

<span data-ttu-id="1500e-176">Şimdi bir daha fazla özellik eklemek ve diğer dili deyimleri olayları gösterin.</span><span class="sxs-lookup"><span data-stu-id="1500e-176">Let's add one more feature, and demonstrate other language idioms for events.</span></span> <span data-ttu-id="1500e-177">Bir aşırı yüklemesini ekleyelim `Search()` dosyaları aramak üzere tüm alt dizinler geçeceğini yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1500e-177">Let's add an overload of the `Search()` method that traverses all subdirectories in search of files.</span></span>

<span data-ttu-id="1500e-178">Bu, birden çok alt dizini ile bir dizinde uzun bir işlem olarak alabilir.</span><span class="sxs-lookup"><span data-stu-id="1500e-178">This could get to be a lengthy operation in a directory with many sub-directories.</span></span> <span data-ttu-id="1500e-179">Her yeni bir dizin arama başladığında bir olayı ekleyelim.</span><span class="sxs-lookup"><span data-stu-id="1500e-179">Let's add an event that gets raised when each new directory search begins.</span></span> <span data-ttu-id="1500e-180">Bu, ilerlemeyi izlemek ve ilerleme konusunda kullanıcıyı güncelleştirmek aboneleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="1500e-180">This enables subscribers to track progress, and update the user as to progress.</span></span> <span data-ttu-id="1500e-181">Şu ana kadar oluşturmuş olduğunuz tüm örnekleri ortak.</span><span class="sxs-lookup"><span data-stu-id="1500e-181">All the samples you've created so far are public.</span></span> <span data-ttu-id="1500e-182">Bu bir iç olay olalım.</span><span class="sxs-lookup"><span data-stu-id="1500e-182">Let's make this one an internal event.</span></span> <span data-ttu-id="1500e-183">Bağımsız değişkenler için dahili olarak da kullanılan türleri de yapabilirsiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="1500e-183">That means you can also make the types used for the arguments internal as well.</span></span>

<span data-ttu-id="1500e-184">Yeni bir dizin ve ilerleme durumu raporlama için yeni EventArgs türetilmiş sınıf oluşturarak başlayacağız.</span><span class="sxs-lookup"><span data-stu-id="1500e-184">You'll start by creating the new EventArgs derived class for reporting the new directory and progress.</span></span> 

[!code-csharp[DirEventArgs](../../samples/csharp/events/Program.cs#SearchDirEventArgs "Define search directory event arguments")]

<span data-ttu-id="1500e-185">Yeniden olay bağımsız değişken için bir sabit başvuru türü sağlayacak öneriler izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1500e-185">Again, you can follow the recommendations to make an immutable reference type for the event arguments.</span></span>

<span data-ttu-id="1500e-186">Ardından, olay tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="1500e-186">Next, define the event.</span></span> <span data-ttu-id="1500e-187">Bu süre, farklı bir sözdizimi kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="1500e-187">This time, you'll use a different syntax.</span></span> <span data-ttu-id="1500e-188">Alan sözdizimini kullanarak ek olarak, açıkça ile ekleme özelliği oluşturabilir ve işleyicileri kaldırın.</span><span class="sxs-lookup"><span data-stu-id="1500e-188">In addition to using the field syntax, you can explicitly create the property, with add and remove handlers.</span></span> <span data-ttu-id="1500e-189">Bu örnekte bu işleyiciler ek kod gerekmez, ancak bu nasıl oluşturmak gösterir.</span><span class="sxs-lookup"><span data-stu-id="1500e-189">In this sample, you won't need extra code in those handlers, but this shows how you would create them.</span></span>

[!code-csharp[Declare event with add and remove handlers](../../samples/csharp/events/Program.cs#DeclareSearchEvent "Declare the event with add and remove handlers")]

<span data-ttu-id="1500e-190">Birçok yolla burada yansıtmalar alan olay tanımlarında derleyici kod oluşturur yazdığınız kodları, daha önce gördünüz.</span><span class="sxs-lookup"><span data-stu-id="1500e-190">In many ways, the code you write here mirrors the code the compiler generates for the field event definitions you've seen earlier.</span></span> <span data-ttu-id="1500e-191">İçin kullanılan çok benzer sözdizimi kullanılarak olay oluşturma [özellikleri](properties.md).</span><span class="sxs-lookup"><span data-stu-id="1500e-191">You create the event using syntax very similar to that used for [properties](properties.md).</span></span> <span data-ttu-id="1500e-192">İşleyicileri farklı adlara sahip dikkat edin: `add` ve `remove`.</span><span class="sxs-lookup"><span data-stu-id="1500e-192">Notice that the handlers have different names: `add` and `remove`.</span></span> <span data-ttu-id="1500e-193">Bu olaya abone veya olayından aboneliği adı verilir.</span><span class="sxs-lookup"><span data-stu-id="1500e-193">These are called to subscribe to the event, or unsubscribe from the event.</span></span> <span data-ttu-id="1500e-194">Olay değişkeni depolamak için bir özel yedekleme alanını da bildirmelidir dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="1500e-194">Notice that you also must declare a private backing field to store the event variable.</span></span> <span data-ttu-id="1500e-195">Null olarak başlatılır.</span><span class="sxs-lookup"><span data-stu-id="1500e-195">It is initialized to null.</span></span>

<span data-ttu-id="1500e-196">Ardından, alt dizinleri erişir ve her iki olayları başlatır Search() yönteminin ekleyelim.</span><span class="sxs-lookup"><span data-stu-id="1500e-196">Next, let's add the overload of the Search() method that traverses subdirectories and raises both events.</span></span> <span data-ttu-id="1500e-197">Bunu yapmanın en kolay yolu, tüm dizinler arama yapmak istediğinizi belirtmek için bir varsayılan bağımsız değişkeni kullanmaktır:</span><span class="sxs-lookup"><span data-stu-id="1500e-197">The easiest way to accomplish this is to use a default argument to specify that you want to search all directories:</span></span>

[!code-csharp[SearchImplementation](../../samples/csharp/events/Program.cs#FinalImplementation "Implementation to search directories")]

<span data-ttu-id="1500e-198">Bu noktada, tüm alt dizinler arama için aşırı çağırma uygulamayı çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1500e-198">At this point, you can run the application calling the overload for searching all sub-directories.</span></span> <span data-ttu-id="1500e-199">Yeni abone vardır `ChangeDirectory` olay ancak kullanarak `?.Invoke()` deyim bu düzgün çalıştığını sağlar.</span><span class="sxs-lookup"><span data-stu-id="1500e-199">There are no subscribers on the new `ChangeDirectory` event, but using the `?.Invoke()` idiom ensures that this works correctly.</span></span>

 <span data-ttu-id="1500e-200">Konsol penceresinde ilerleme durumunu gösteren bir satır yazmak için bir işleyici ekleyelim.</span><span class="sxs-lookup"><span data-stu-id="1500e-200">Let's add a handler to write a line that shows the progress in the console window.</span></span> 

[!code-csharp[Search](../../samples/csharp/events/Program.cs#Search "Declare event handler")]

<span data-ttu-id="1500e-201">.NET ekosistemi izlenen desenleri gördünüz.</span><span class="sxs-lookup"><span data-stu-id="1500e-201">You've seen patterns that are followed throughout the .NET ecosystem.</span></span>
<span data-ttu-id="1500e-202">Bu desenleri ve kuralları öğrenerek, kullanılan deyimsel C# ve .NET hızla yazacaksınız.</span><span class="sxs-lookup"><span data-stu-id="1500e-202">By learning these patterns and conventions, you'll be writing idiomatic C# and .NET quickly.</span></span>

<span data-ttu-id="1500e-203">Ardından, bu desenleri .NET en son sürümündeki bazı değişiklikler görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="1500e-203">Next, you'll see some changes in these patterns in the most recent release of .NET.</span></span>

[<span data-ttu-id="1500e-204">Next</span><span class="sxs-lookup"><span data-stu-id="1500e-204">Next</span></span>](modern-events.md)
