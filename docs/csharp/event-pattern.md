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
# <a name="standard-net-event-patterns"></a><span data-ttu-id="26a06-103">Standart .NET olay desenleri</span><span class="sxs-lookup"><span data-stu-id="26a06-103">Standard .NET event patterns</span></span>

[<span data-ttu-id="26a06-104">Önceki</span><span class="sxs-lookup"><span data-stu-id="26a06-104">Previous</span></span>](events-overview.md)

<span data-ttu-id="26a06-105">.NET olayları genellikle bilinen birkaç desen izler.</span><span class="sxs-lookup"><span data-stu-id="26a06-105">.NET events generally follow a few known patterns.</span></span> <span data-ttu-id="26a06-106">Bu desenleri standartlaştırmak, geliştiricilerin herhangi bir .NET etkinlik programına uygulanabilen bu standart desenler hakkındaki bilgilerden yararlanabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="26a06-106">Standardizing on these patterns means that developers can leverage knowledge of those standard patterns, which can be applied to any .NET event program.</span></span>

<span data-ttu-id="26a06-107">Standart etkinlik kaynakları oluşturmak ve kodunuzda standart olaylara abone olmak ve işlemek için ihtiyacınız olan tüm bilgilere sahip olmak için bu standart desenleri gözden geçirelim.</span><span class="sxs-lookup"><span data-stu-id="26a06-107">Let's go through these standard patterns so you will have all the knowledge you need to create standard event sources, and subscribe and process standard events in your code.</span></span>

## <a name="event-delegate-signatures"></a><span data-ttu-id="26a06-108">Olay Temsilci İmzaları</span><span class="sxs-lookup"><span data-stu-id="26a06-108">Event Delegate Signatures</span></span>

<span data-ttu-id="26a06-109">.NET olay temsilcisinin standart imzası:</span><span class="sxs-lookup"><span data-stu-id="26a06-109">The standard signature for a .NET event delegate is:</span></span>

```csharp
void OnEventRaised(object sender, EventArgs args);
```

<span data-ttu-id="26a06-110">İade türü geçersizdir.</span><span class="sxs-lookup"><span data-stu-id="26a06-110">The return type is void.</span></span> <span data-ttu-id="26a06-111">Olaylar delegelere dayanır ve çok noktaya yayın lı temsilcilerdir.</span><span class="sxs-lookup"><span data-stu-id="26a06-111">Events are based on delegates and are multicast delegates.</span></span> <span data-ttu-id="26a06-112">Bu, herhangi bir etkinlik kaynağı için birden çok aboneyi destekler.</span><span class="sxs-lookup"><span data-stu-id="26a06-112">That supports multiple subscribers for any event source.</span></span> <span data-ttu-id="26a06-113">Bir yöntemden gelen tek iade değeri birden çok olay abonesine ölçeklendirilmez.</span><span class="sxs-lookup"><span data-stu-id="26a06-113">The single return value from a method doesn't scale to multiple event subscribers.</span></span> <span data-ttu-id="26a06-114">Olay kaynağı, bir olayı yükselttikten sonra hangi iade değerini görür?</span><span class="sxs-lookup"><span data-stu-id="26a06-114">Which return value does the event source see after raising an event?</span></span> <span data-ttu-id="26a06-115">Bu makalenin ilerleyen saatlerinde, olay kaynağına bilgi rapor eden olay abonelerini destekleyen olay protokollerinin nasıl oluşturulacağını görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="26a06-115">Later in this article you'll see how to create event protocols that support event subscribers that report information to the event source.</span></span>

<span data-ttu-id="26a06-116">Bağımsız değişken listesi iki bağımsız değişken içerir: gönderen ve olay bağımsız değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="26a06-116">The argument list contains two arguments: the sender, and the event arguments.</span></span> <span data-ttu-id="26a06-117">Derleme zaman `sender` `System.Object`türü, büyük olasılıkla her zaman doğru olacağını daha türemiş bir tür biliyorum olsa bile.</span><span class="sxs-lookup"><span data-stu-id="26a06-117">The compile time type of `sender` is `System.Object`, even though you likely know a more derived type that would always be correct.</span></span> <span data-ttu-id="26a06-118">Kurallara göre, kullanın. `object`</span><span class="sxs-lookup"><span data-stu-id="26a06-118">By convention, use `object`.</span></span>

<span data-ttu-id="26a06-119">İkinci bağımsız değişken genellikle `System.EventArgs`türetilen bir tür olmuştur.</span><span class="sxs-lookup"><span data-stu-id="26a06-119">The second argument has typically been a type that is derived from `System.EventArgs`.</span></span> <span data-ttu-id="26a06-120">(Bir [sonraki bölümde](modern-events.md) bu kuralın artık uygulanmadığını görürsünüz.) Olay türünün ek bağımsız değişkenleri yoksa, her iki bağımsız değişkeni de sağlamaya devam edesiniz.</span><span class="sxs-lookup"><span data-stu-id="26a06-120">(You'll see in the [next section](modern-events.md) that this convention is no longer enforced.) If your event type does not need any additional arguments, you will still provide both arguments.</span></span>
<span data-ttu-id="26a06-121">Etkinliğinizin herhangi bir `EventArgs.Empty` ek bilgi içermediğini belirtmek için kullanmanız gereken özel bir değer vardır.</span><span class="sxs-lookup"><span data-stu-id="26a06-121">There is a special value, `EventArgs.Empty` that you should use to denote that your event does not contain any additional information.</span></span>

<span data-ttu-id="26a06-122">Dosyaları bir dizindeki veya bir deseni izleyen alt dizinişlerini listeleyen bir sınıf oluşturalım.</span><span class="sxs-lookup"><span data-stu-id="26a06-122">Let's build a class that lists files in a directory, or any of its subdirectories that follow a pattern.</span></span> <span data-ttu-id="26a06-123">Bu bileşen, deseneşleşen bulunan her dosya için bir olay yükseltir.</span><span class="sxs-lookup"><span data-stu-id="26a06-123">This component raises an event for each file found that matches the pattern.</span></span>

<span data-ttu-id="26a06-124">Olay modeli kullanmak bazı tasarım avantajları sağlar.</span><span class="sxs-lookup"><span data-stu-id="26a06-124">Using an event model provides some design advantages.</span></span> <span data-ttu-id="26a06-125">Aranan bir dosya bulunduğunda farklı eylemler gerçekleştiren birden çok olay dinleyicisi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="26a06-125">You can create multiple event listeners that perform different actions when a sought file is found.</span></span> <span data-ttu-id="26a06-126">Farklı dinleyicileri birleştirmek daha sağlam algoritmalar oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="26a06-126">Combining the different listeners can create more robust algorithms.</span></span>

<span data-ttu-id="26a06-127">Aranan bir dosyayı bulmak için ilk olay bağımsız değişken bildirimi aşağıda veda edilir:</span><span class="sxs-lookup"><span data-stu-id="26a06-127">Here is the initial event argument declaration for finding a sought file:</span></span>

[!code-csharp[EventArgs](../../samples/snippets/csharp/events/Program.cs#EventArgsV1 "Define event arguments")]

<span data-ttu-id="26a06-128">Bu tür küçük, yalnızca veri türü gibi görünse de, kuralı izlemeli`class`ve bir başvuru ( ) türü yapmalısınız.</span><span class="sxs-lookup"><span data-stu-id="26a06-128">Even though this type looks like a small, data-only type, you should follow the convention and make it a reference (`class`) type.</span></span> <span data-ttu-id="26a06-129">Bu, bağımsız değişken nesnesinin başvuru yoluyla geçirileceği ve verilerdeki tüm güncelleştirmelerin tüm aboneler tarafından görüntüleneceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="26a06-129">That means the argument object will be passed by reference, and any updates to the data will be viewed by all subscribers.</span></span> <span data-ttu-id="26a06-130">İlk sürüm değişmez bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="26a06-130">The first version is an immutable object.</span></span> <span data-ttu-id="26a06-131">Olay bağımsız değişken türündeki özellikleri değişmez hale getirmeyi tercih edersiniz.</span><span class="sxs-lookup"><span data-stu-id="26a06-131">You should prefer to make the properties in your event argument type immutable.</span></span> <span data-ttu-id="26a06-132">Bu şekilde, bir abone, başka bir abone görmeden önce değerleri değiştiremez.</span><span class="sxs-lookup"><span data-stu-id="26a06-132">That way, one subscriber cannot change the values before another subscriber sees them.</span></span> <span data-ttu-id="26a06-133">(Aşağıda göreceğiniz gibi, bunun istisnaları vardır.)</span><span class="sxs-lookup"><span data-stu-id="26a06-133">(There are exceptions to this, as you'll see below.)</span></span>  

<span data-ttu-id="26a06-134">Ardından, FileSearcher sınıfında olay bildirimioluşturmamız gerekir.</span><span class="sxs-lookup"><span data-stu-id="26a06-134">Next, we need to create the event declaration in the FileSearcher class.</span></span> <span data-ttu-id="26a06-135">`EventHandler<T>` Türden yararlanmak, başka bir tür tanımı oluşturmanız gerekolmadığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="26a06-135">Leveraging the `EventHandler<T>` type means that you don't need to create yet another type definition.</span></span> <span data-ttu-id="26a06-136">Sadece genel bir uzmanlık kullanın.</span><span class="sxs-lookup"><span data-stu-id="26a06-136">You simply use a generic specialization.</span></span>

<span data-ttu-id="26a06-137">Bir desenle eşleşen dosyaları aramak için FileSearcher sınıfını dolduralım ve bir eşleşme keşfedildiğinde doğru olayı yükseltelim.</span><span class="sxs-lookup"><span data-stu-id="26a06-137">Let's fill out the FileSearcher class to search for files that match a pattern, and raise the correct event when a match is discovered.</span></span>

[!code-csharp[FileSearcher](../../samples/snippets/csharp/events/Program.cs#FileSearcherV1 "Create the initial file searcher")]

## <a name="defining-and-raising-field-like-events"></a><span data-ttu-id="26a06-138">Alan Benzeri Etkinliklerin Tanımlanması ve Yükseltilmesi</span><span class="sxs-lookup"><span data-stu-id="26a06-138">Defining and Raising Field-Like Events</span></span>

<span data-ttu-id="26a06-139">Bir olayı sınıfınıza eklemenin en basit yolu, önceki örnekte olduğu gibi, bu olayı ortak alan olarak bildirmektir:</span><span class="sxs-lookup"><span data-stu-id="26a06-139">The simplest way to add an event to your class is to declare that event as a public field, as in the preceding example:</span></span>

[!code-csharp[DeclareEvent](../../samples/snippets/csharp/events/Program.cs#DeclareEvent "Declare the file found event")]

<span data-ttu-id="26a06-140">Bu, kötü nesne yönelimli bir uygulama gibi görünen bir kamusal alan ilan ediyor gibi görünüyor.</span><span class="sxs-lookup"><span data-stu-id="26a06-140">This looks like it's declaring a public field, which would appear to be bad object-oriented practice.</span></span> <span data-ttu-id="26a06-141">Özellikler veya yöntemler aracılığıyla veri erişimini korumak istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="26a06-141">You want to protect data access through properties, or methods.</span></span> <span data-ttu-id="26a06-142">Bu kötü bir uygulama gibi görünse de, derleyici tarafından oluşturulan kod, olay nesnelerine yalnızca güvenli yollarla erişilebilmek için sarmalayıcılar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="26a06-142">While this may look like a bad practice, the code generated by the compiler does create wrappers so that the event objects can only be accessed in safe ways.</span></span> <span data-ttu-id="26a06-143">Alan benzeri bir etkinlikte kullanılabilen tek işlem işleyicisi vardır:</span><span class="sxs-lookup"><span data-stu-id="26a06-143">The only operations available on a field-like event are add handler:</span></span>

[!code-csharp[DeclareEventHandler](../../samples/snippets/csharp/events/Program.cs#DeclareEventHandler "Declare the file found event handler")]

<span data-ttu-id="26a06-144">ve işleyiciyi kaldırın:</span><span class="sxs-lookup"><span data-stu-id="26a06-144">and remove handler:</span></span>

[!code-csharp[RemoveEventHandler](../../samples/snippets/csharp/events/Program.cs#RemoveHandler "Remove the event handler")]

<span data-ttu-id="26a06-145">İşleyici için yerel bir değişken olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="26a06-145">Note that there's a local variable for the handler.</span></span> <span data-ttu-id="26a06-146">Lambda gövdesi kullanılırsa, kaldırmak doğru çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="26a06-146">If you used the body of the lambda, the remove would not work correctly.</span></span> <span data-ttu-id="26a06-147">Bu delege farklı bir örnek olacaktır ve sessizce hiçbir şey yok.</span><span class="sxs-lookup"><span data-stu-id="26a06-147">It would be a different instance of the delegate, and silently do nothing.</span></span>

<span data-ttu-id="26a06-148">Sınıfın dışındaki kod olayı yükseltemez ve başka bir işlem gerçekleştiremez.</span><span class="sxs-lookup"><span data-stu-id="26a06-148">Code outside the class cannot raise the event, nor can it perform any other operations.</span></span>

## <a name="returning-values-from-event-subscribers"></a><span data-ttu-id="26a06-149">Etkinlik Abonelerinden Dönen Değerler</span><span class="sxs-lookup"><span data-stu-id="26a06-149">Returning Values from Event Subscribers</span></span>

<span data-ttu-id="26a06-150">Basit versiyonun gayet iyi çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="26a06-150">Your simple version is working fine.</span></span> <span data-ttu-id="26a06-151">Başka bir özellik ekleyelim: İptal.</span><span class="sxs-lookup"><span data-stu-id="26a06-151">Let's add another feature: Cancellation.</span></span>

<span data-ttu-id="26a06-152">Bulunan olayı yükselttiğinizde, dinleyiciler bu dosya aranan son dosyaysa, daha fazla işleme durdurabilmeli.</span><span class="sxs-lookup"><span data-stu-id="26a06-152">When you raise the found event, listeners should be able to stop further processing, if this file is that last one sought.</span></span>

<span data-ttu-id="26a06-153">Olay işleyicileri bir değer döndürmez, bu nedenle bunu başka bir şekilde iletmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="26a06-153">The event handlers do not return a value, so you need to communicate that in another way.</span></span> <span data-ttu-id="26a06-154">Standart olay deseni, event abonelerinin iptal iletişimi kurmak için kullanabilecekleri alanları eklemek için EventArgs nesnesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="26a06-154">The standard event pattern uses the EventArgs object to include fields that event subscribers can use to communicate cancel.</span></span>

<span data-ttu-id="26a06-155">İptal sözleşmesinin anlambilimine göre kullanılabilecek iki farklı desen vardır.</span><span class="sxs-lookup"><span data-stu-id="26a06-155">There are two different patterns that could be used, based on the semantics of the Cancel contract.</span></span> <span data-ttu-id="26a06-156">Her iki durumda da, bulunan dosya olayı için EventArguments'a bir boolean alanı eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="26a06-156">In both cases, you'll add a boolean field to the EventArguments for the found file event.</span></span>

<span data-ttu-id="26a06-157">Bir desen, herhangi bir abonenin işlemi iptal etmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="26a06-157">One pattern would allow any one subscriber to cancel the operation.</span></span>
<span data-ttu-id="26a06-158">Bu desen için, yeni alan `false`' a' ya başharf.</span><span class="sxs-lookup"><span data-stu-id="26a06-158">For this pattern, the new field is initialized to `false`.</span></span> <span data-ttu-id="26a06-159">Herhangi bir abone bunu `true`.</span><span class="sxs-lookup"><span data-stu-id="26a06-159">Any subscriber can change it to `true`.</span></span> <span data-ttu-id="26a06-160">Tüm aboneler olayın yükseltildiğini gördükten sonra, FileSearcher bileşeni boolean değerini inceler ve harekete geçer.</span><span class="sxs-lookup"><span data-stu-id="26a06-160">After all subscribers have seen the event raised, the FileSearcher component examines the boolean value and takes action.</span></span>

<span data-ttu-id="26a06-161">İkinci desen, yalnızca tüm aboneler işlemin iptalini isterse işlemi iptal eder.</span><span class="sxs-lookup"><span data-stu-id="26a06-161">The second pattern would only cancel the operation if all subscribers wanted the operation cancelled.</span></span> <span data-ttu-id="26a06-162">Bu desende, işlemin iptal etmesi gerektiğini belirtmek için yeni alan başolarak başolarak başlanır ve herhangi bir abone, işlemin devam etmesi gerektiğini belirtmek için değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="26a06-162">In this pattern, the new field is initialized to indicate the operation should cancel, and any subscriber could change it to indicate the operation should continue.</span></span>
<span data-ttu-id="26a06-163">Tüm aboneler olayın yükseltildiğini gördükten sonra, FileSearcher bileşeni boolean inceler ve harekete geçer.</span><span class="sxs-lookup"><span data-stu-id="26a06-163">After all subscribers have seen the event raised, the FileSearcher component examines the boolean and takes action.</span></span> <span data-ttu-id="26a06-164">Bu desende fazladan bir adım vardır: bileşenin olayı gören aboneler olup olmadığını bilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="26a06-164">There is one extra step in this pattern: the component needs to know if any subscribers have seen the event.</span></span> <span data-ttu-id="26a06-165">Abone yoksa, alan yanlış iptal olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="26a06-165">If there are no subscribers, the field would indicate a cancel incorrectly.</span></span>

<span data-ttu-id="26a06-166">Bu örnek için ilk sürümü uygulayalım.</span><span class="sxs-lookup"><span data-stu-id="26a06-166">Let's implement the first version for this sample.</span></span> <span data-ttu-id="26a06-167">Türüne adlandırılmış `CancelRequested` bir boolean `FileFoundArgs` alanı eklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="26a06-167">You need to add a boolean field named `CancelRequested` to the `FileFoundArgs` type:</span></span>

[!code-csharp[EventArgs](../../samples/snippets/csharp/events/Program.cs#EventArgs "Update event arguments")]

<span data-ttu-id="26a06-168">Bu yeni Alan otomatik olarak `false`bir Boolean alanı için varsayılan değer e-baş harfe ayarlanır, böylece yanlışlıkla iptal etmezsiniz.</span><span class="sxs-lookup"><span data-stu-id="26a06-168">This new Field is automatically initialized to `false`, the default value for a Boolean field, so you don't cancel accidentally.</span></span> <span data-ttu-id="26a06-169">Bileşendeki diğer tek değişiklik, abonelerden herhangi birinin iptal talebinde bulunıp var olmadığını görmek için olayı yükselttikten sonra bayrağı denetlemektir:</span><span class="sxs-lookup"><span data-stu-id="26a06-169">The only other change to the component is to check the flag after raising the event to see if any of the subscribers have requested a cancellation:</span></span>

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

<span data-ttu-id="26a06-170">Bu modelin bir avantajı, bir kırılma değişiklik değildir.</span><span class="sxs-lookup"><span data-stu-id="26a06-170">One advantage of this pattern is that it isn't a breaking change.</span></span>
<span data-ttu-id="26a06-171">Abonelerin hiçbiri daha önce iptal talebinde bulunmadı ve hala da iptal edilmedi.</span><span class="sxs-lookup"><span data-stu-id="26a06-171">None of the subscribers requested a cancellation before, and they still are not.</span></span> <span data-ttu-id="26a06-172">Yeni iptal protokolünü desteklemek istemedikleri sürece abone kodunun hiçbirinin güncelleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="26a06-172">None of the subscriber code needs updating unless they want to support the new cancel protocol.</span></span> <span data-ttu-id="26a06-173">Çok gevşek bir şekilde birleştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="26a06-173">It's very loosely coupled.</span></span>

<span data-ttu-id="26a06-174">Aboneyi, ilk çalıştırılabilir ibareyi bulduğunda iptal talebinde bulunsun diye güncelleyelim:</span><span class="sxs-lookup"><span data-stu-id="26a06-174">Let's update the subscriber so that it requests a cancellation once it finds the first executable:</span></span>

```csharp
EventHandler<FileFoundArgs> onFileFound = (sender, eventArgs) =>
{
    Console.WriteLine(eventArgs.FoundFile);
    eventArgs.CancelRequested = true;
};
```

## <a name="adding-another-event-declaration"></a><span data-ttu-id="26a06-175">Başka bir olay bildirimi ekleme</span><span class="sxs-lookup"><span data-stu-id="26a06-175">Adding Another Event Declaration</span></span>

<span data-ttu-id="26a06-176">Bir özellik daha ekleyelim ve etkinlikler için diğer dil deyimlerini gösterelim.</span><span class="sxs-lookup"><span data-stu-id="26a06-176">Let's add one more feature, and demonstrate other language idioms for events.</span></span> <span data-ttu-id="26a06-177">Dosya aramasında `Search` tüm alt dizinleri geçen yöntemin aşırı yüklenmesini ekleyelim.</span><span class="sxs-lookup"><span data-stu-id="26a06-177">Let's add an overload of the `Search` method that traverses all subdirectories in search of files.</span></span>

<span data-ttu-id="26a06-178">Bu, birçok alt diziniçeren bir dizinde uzun bir işlem olabilir.</span><span class="sxs-lookup"><span data-stu-id="26a06-178">This could get to be a lengthy operation in a directory with many sub-directories.</span></span> <span data-ttu-id="26a06-179">Her yeni dizin araması başladığında gündeme gelen bir olay ekleyelim.</span><span class="sxs-lookup"><span data-stu-id="26a06-179">Let's add an event that gets raised when each new directory search begins.</span></span> <span data-ttu-id="26a06-180">Bu, abonelerin ilerlemeyi izlemesini ve kullanıcıyı ilerleme olarak güncelleştirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="26a06-180">This enables subscribers to track progress, and update the user as to progress.</span></span> <span data-ttu-id="26a06-181">Şimdiye kadar oluşturduğunuz tüm örnekler herkese açıktır.</span><span class="sxs-lookup"><span data-stu-id="26a06-181">All the samples you've created so far are public.</span></span> <span data-ttu-id="26a06-182">Bunu bir iç olay haline getirelim.</span><span class="sxs-lookup"><span data-stu-id="26a06-182">Let's make this one an internal event.</span></span> <span data-ttu-id="26a06-183">Bu, iç bağımsız değişkenler için kullanılan türleri de yapabileceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="26a06-183">That means you can also make the types used for the arguments internal as well.</span></span>

<span data-ttu-id="26a06-184">Yeni dizini ve ilerlemeyi bildirmek için yeni EventArgs türetilmiş sınıfını oluşturarak başlarsınız.</span><span class="sxs-lookup"><span data-stu-id="26a06-184">You'll start by creating the new EventArgs derived class for reporting the new directory and progress.</span></span>

[!code-csharp[DirEventArgs](../../samples/snippets/csharp/events/Program.cs#SearchDirEventArgs "Define search directory event arguments")]

<span data-ttu-id="26a06-185">Yine, olay bağımsız değişkenleri için değişmez bir başvuru türü yapmak için önerileri izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="26a06-185">Again, you can follow the recommendations to make an immutable reference type for the event arguments.</span></span>

<span data-ttu-id="26a06-186">Sonra, olayı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="26a06-186">Next, define the event.</span></span> <span data-ttu-id="26a06-187">Bu sefer farklı bir sözdizimi kullanacaksın.</span><span class="sxs-lookup"><span data-stu-id="26a06-187">This time, you'll use a different syntax.</span></span> <span data-ttu-id="26a06-188">Alan sözdizimini kullanmanın yanı sıra, özelliği açıkça ekleyip kaldır işleyicileriyle oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="26a06-188">In addition to using the field syntax, you can explicitly create the property, with add and remove handlers.</span></span> <span data-ttu-id="26a06-189">Bu örnekte, bu işleyicilerde fazladan kod gerekmez, ancak bu bunları nasıl oluşturacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="26a06-189">In this sample, you won't need extra code in those handlers, but this shows how you would create them.</span></span>

[!code-csharp[Declare event with add and remove handlers](../../samples/snippets/csharp/events/Program.cs#DeclareSearchEvent "Declare the event with add and remove handlers")]

<span data-ttu-id="26a06-190">Birçok yönden, burada yazdığınız kod, derleyicinin daha önce gördüğünüz alan olay tanımları için oluşturduğu kodu yansıtAbilir.</span><span class="sxs-lookup"><span data-stu-id="26a06-190">In many ways, the code you write here mirrors the code the compiler generates for the field event definitions you've seen earlier.</span></span> <span data-ttu-id="26a06-191">Olayı, [özellikler](properties.md)için kullanılana çok benzer sözdizimini kullanarak oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="26a06-191">You create the event using syntax very similar to that used for [properties](properties.md).</span></span> <span data-ttu-id="26a06-192">İşleyicilerin farklı adları olduğuna `add` dikkat `remove`edin: ve .</span><span class="sxs-lookup"><span data-stu-id="26a06-192">Notice that the handlers have different names: `add` and `remove`.</span></span> <span data-ttu-id="26a06-193">Bunlar, etkinliğe abone olmak veya etkinlikten aboneliğiiptal etmek için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="26a06-193">These are called to subscribe to the event, or unsubscribe from the event.</span></span> <span data-ttu-id="26a06-194">Olay değişkenini depolamak için özel bir destek alanı da bildirmeniz gerektiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="26a06-194">Notice that you also must declare a private backing field to store the event variable.</span></span> <span data-ttu-id="26a06-195">Null için başharf.</span><span class="sxs-lookup"><span data-stu-id="26a06-195">It is initialized to null.</span></span>

<span data-ttu-id="26a06-196">Ardından, alt dizinleri geçen `Search` ve her iki olayı da yükselten yöntemin aşırı yüklenmesini ekleyelim.</span><span class="sxs-lookup"><span data-stu-id="26a06-196">Next, let's add the overload of the `Search` method that traverses subdirectories and raises both events.</span></span> <span data-ttu-id="26a06-197">Bunu gerçekleştirmenin en kolay yolu, tüm dizinlerde arama yapmak istediğinizi belirtmek için varsayılan bir bağımsız değişken kullanmaktır:</span><span class="sxs-lookup"><span data-stu-id="26a06-197">The easiest way to accomplish this is to use a default argument to specify that you want to search all directories:</span></span>

[!code-csharp[SearchImplementation](../../samples/snippets/csharp/events/Program.cs#FinalImplementation "Implementation to search directories")]

<span data-ttu-id="26a06-198">Bu noktada, tüm alt dizinleri aramak için aşırı yükleme çağıran uygulamayı çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="26a06-198">At this point, you can run the application calling the overload for searching all sub-directories.</span></span> <span data-ttu-id="26a06-199">Yeni `ChangeDirectory` etkinlikte abone yok, ancak deyimin `?.Invoke()` kullanılması bunun doğru çalışmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="26a06-199">There are no subscribers on the new `ChangeDirectory` event, but using the `?.Invoke()` idiom ensures that this works correctly.</span></span>

 <span data-ttu-id="26a06-200">Konsol penceresinde ilerlemeyi gösteren bir satır yazmak için bir işleyici ekleyelim.</span><span class="sxs-lookup"><span data-stu-id="26a06-200">Let's add a handler to write a line that shows the progress in the console window.</span></span>

[!code-csharp[Search](../../samples/snippets/csharp/events/Program.cs#Search "Declare event handler")]

<span data-ttu-id="26a06-201">.NET ekosistemi boyunca izlenen desenler ilerler siniz.</span><span class="sxs-lookup"><span data-stu-id="26a06-201">You've seen patterns that are followed throughout the .NET ecosystem.</span></span>
<span data-ttu-id="26a06-202">Bu kalıpları ve kuralları öğrenerek, idiomatic C# ve .NET'i hızla yazacaksınız.</span><span class="sxs-lookup"><span data-stu-id="26a06-202">By learning these patterns and conventions, you'll be writing idiomatic C# and .NET quickly.</span></span>

<span data-ttu-id="26a06-203">Ardından, .NET'in en son sürümünde bu desenlerde bazı değişiklikler görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="26a06-203">Next, you'll see some changes in these patterns in the most recent release of .NET.</span></span>

[<span data-ttu-id="26a06-204">Sonraki</span><span class="sxs-lookup"><span data-stu-id="26a06-204">Next</span></span>](modern-events.md)
