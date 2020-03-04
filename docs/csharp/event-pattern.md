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
# <a name="standard-net-event-patterns"></a><span data-ttu-id="ca3f8-103">Standart .NET olay desenleri</span><span class="sxs-lookup"><span data-stu-id="ca3f8-103">Standard .NET event patterns</span></span>

[<span data-ttu-id="ca3f8-104">Öncekini</span><span class="sxs-lookup"><span data-stu-id="ca3f8-104">Previous</span></span>](events-overview.md)

<span data-ttu-id="ca3f8-105">.NET olayları genellikle bilinen birkaç deseni izler.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-105">.NET events generally follow a few known patterns.</span></span> <span data-ttu-id="ca3f8-106">Bu desenlerin standartlaştırılacağı geliştiriciler, geliştiricilerin herhangi bir .NET olay programına uygulanabilecek standart desenlerle ilgili bilgi sahibi olabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-106">Standardizing on these patterns means that developers can leverage knowledge of those standard patterns, which can be applied to any .NET event program.</span></span>

<span data-ttu-id="ca3f8-107">Standart bir olay kaynağı oluşturmak ve kodunuzda standart olayları abone olmak ve işlemek için ihtiyacınız olan tüm bilgilere sahip olacak şekilde bu standart desenleri ilerlim.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-107">Let's go through these standard patterns so you will have all the knowledge you need to create standard event sources, and subscribe and process standard events in your code.</span></span>

## <a name="event-delegate-signatures"></a><span data-ttu-id="ca3f8-108">Olay temsilcisi Imzaları</span><span class="sxs-lookup"><span data-stu-id="ca3f8-108">Event Delegate Signatures</span></span>

<span data-ttu-id="ca3f8-109">.NET olay temsilcisi için standart imza:</span><span class="sxs-lookup"><span data-stu-id="ca3f8-109">The standard signature for a .NET event delegate is:</span></span>

```csharp
void OnEventRaised(object sender, EventArgs args);
```

<span data-ttu-id="ca3f8-110">Dönüş türü void.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-110">The return type is void.</span></span> <span data-ttu-id="ca3f8-111">Olaylar temsilcilere dayalıdır ve çok noktaya yayın temsilcileriniz.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-111">Events are based on delegates and are multicast delegates.</span></span> <span data-ttu-id="ca3f8-112">Bu, herhangi bir olay kaynağı için birden çok aboneyi destekler.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-112">That supports multiple subscribers for any event source.</span></span> <span data-ttu-id="ca3f8-113">Bir yöntemden tek dönüş değeri, birden çok olay abonelerine ölçeklenmez.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-113">The single return value from a method doesn't scale to multiple event subscribers.</span></span> <span data-ttu-id="ca3f8-114">Olay kaynağı, olay oluşturulduktan sonra hangi dönüş değeri görebilir?</span><span class="sxs-lookup"><span data-stu-id="ca3f8-114">Which return value does the event source see after raising an event?</span></span> <span data-ttu-id="ca3f8-115">Bu makalenin ilerleyen kısımlarında, olay kaynağına rapor veren olay abonelerini destekleyen olay protokollerini nasıl oluşturacağınız hakkında bilgi edineceksiniz.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-115">Later in this article you'll see how to create event protocols that support event subscribers that report information to the event source.</span></span>

<span data-ttu-id="ca3f8-116">Bağımsız değişken listesi iki bağımsız değişken içerir: gönderici ve olay bağımsız değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-116">The argument list contains two arguments: the sender, and the event arguments.</span></span> <span data-ttu-id="ca3f8-117">`sender` derleme zaman türü `System.Object`, ancak her zaman doğru olacak şekilde daha fazla türetilmiş bir tür bildiğiniz halde olabilir.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-117">The compile time type of `sender` is `System.Object`, even though you likely know a more derived type that would always be correct.</span></span> <span data-ttu-id="ca3f8-118">Kurala göre `object`kullanın.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-118">By convention, use `object`.</span></span>

<span data-ttu-id="ca3f8-119">İkinci bağımsız değişken genellikle `System.EventArgs`türetilmiş bir türdür.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-119">The second argument has typically been a type that is derived from `System.EventArgs`.</span></span> <span data-ttu-id="ca3f8-120">(Bir [sonraki bölümde](modern-events.md) bu kural artık zorlanmadığını göreceksiniz.) Olay türü herhangi bir ek bağımsız değişken gerekmiyorsa, her iki bağımsız değişkeni de sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-120">(You'll see in the [next section](modern-events.md) that this convention is no longer enforced.) If your event type does not need any additional arguments, you will still provide both arguments.</span></span>
<span data-ttu-id="ca3f8-121">Olaylarınızın ek bilgi içermediğini belirtmek için kullanmanız gereken `EventArgs.Empty` özel bir değer vardır.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-121">There is a special value, `EventArgs.Empty` that you should use to denote that your event does not contain any additional information.</span></span>

<span data-ttu-id="ca3f8-122">Bir dizinde veya bir kalıbı izleyen alt dizinlerindeki dosyaları listeleyen bir sınıf oluşturalım.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-122">Let's build a class that lists files in a directory, or any of its subdirectories that follow a pattern.</span></span> <span data-ttu-id="ca3f8-123">Bu bileşen, bulunan her dosya için, düzeniyle eşleşen bir olay oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-123">This component raises an event for each file found that matches the pattern.</span></span>

<span data-ttu-id="ca3f8-124">Bir olay modelinin kullanılması bazı tasarım avantajları sağlar.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-124">Using an event model provides some design advantages.</span></span> <span data-ttu-id="ca3f8-125">Aranan bir dosya bulunduğunda farklı eylemler gerçekleştiren birden çok olay dinleyicisi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-125">You can create multiple event listeners that perform different actions when a sought file is found.</span></span> <span data-ttu-id="ca3f8-126">Farklı dinleyicileri birleştirmek daha sağlam algoritmalar oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-126">Combining the different listeners can create more robust algorithms.</span></span>

<span data-ttu-id="ca3f8-127">Aranan bir dosyayı bulmak için ilk olay bağımsız değişkeni bildirimi aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="ca3f8-127">Here is the initial event argument declaration for finding a sought file:</span></span> 

[!code-csharp[EventArgs](../../samples/snippets/csharp/events/Program.cs#EventArgsV1 "Define event arguments")]

<span data-ttu-id="ca3f8-128">Bu tür küçük, salt veri türü gibi görünse de, kuralı izlemeniz ve bir başvuru (`class`) türü yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-128">Even though this type looks like a small, data-only type, you should follow the convention and make it a reference (`class`) type.</span></span> <span data-ttu-id="ca3f8-129">Diğer bir deyişle, bağımsız değişken nesnesi başvuruya göre geçirilir ve verilerin tüm güncelleştirmeleri tüm aboneler tarafından görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-129">That means the argument object will be passed by reference, and any updates to the data will be viewed by all subscribers.</span></span> <span data-ttu-id="ca3f8-130">İlk sürüm, sabit bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-130">The first version is an immutable object.</span></span> <span data-ttu-id="ca3f8-131">Olay bağımsız değişkeni türünde özellikleri sabit hale getirmek için tercih etmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-131">You should prefer to make the properties in your event argument type immutable.</span></span> <span data-ttu-id="ca3f8-132">Bu şekilde, bir abone, başka bir abonenin onları görebilmesi için değerleri değiştiremez.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-132">That way, one subscriber cannot change the values before another subscriber sees them.</span></span> <span data-ttu-id="ca3f8-133">(Aşağıda göreceğiniz şekilde bunun için özel durumlar vardır.)</span><span class="sxs-lookup"><span data-stu-id="ca3f8-133">(There are exceptions to this, as you'll see below.)</span></span>  

<span data-ttu-id="ca3f8-134">Sonra, FileSearcher sınıfında olay bildirimini oluşturuyoruz.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-134">Next, we need to create the event declaration in the FileSearcher class.</span></span> <span data-ttu-id="ca3f8-135">`EventHandler<T>` türünden yararlanmak, başka bir tür tanımı oluşturmanız gerekmediği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-135">Leveraging the `EventHandler<T>` type means that you don't need to create yet another type definition.</span></span> <span data-ttu-id="ca3f8-136">Yalnızca genel bir özelleştirme kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-136">You simply use a generic specialization.</span></span>

<span data-ttu-id="ca3f8-137">Bir düzeniyle eşleşen dosyaları aramak ve bir eşleşme bulunduğunda doğru olayı yükseltmek için FileSearcher sınıfını dolduralım.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-137">Let's fill out the FileSearcher class to search for files that match a pattern, and raise the correct event when a match is discovered.</span></span>

[!code-csharp[FileSearcher](../../samples/snippets/csharp/events/Program.cs#FileSearcherV1 "Create the initial file searcher")]

## <a name="defining-and-raising-field-like-events"></a><span data-ttu-id="ca3f8-138">Alan benzeri olayları tanımlama ve oluşturma</span><span class="sxs-lookup"><span data-stu-id="ca3f8-138">Defining and Raising Field-Like Events</span></span>

<span data-ttu-id="ca3f8-139">Sınıfınıza bir olay eklemenin en kolay yolu, önceki örnekte olduğu gibi bu olayı ortak bir alan olarak bildirkullanmaktır:</span><span class="sxs-lookup"><span data-stu-id="ca3f8-139">The simplest way to add an event to your class is to declare that event as a public field, as in the preceding example:</span></span>

[!code-csharp[DeclareEvent](../../samples/snippets/csharp/events/Program.cs#DeclareEvent "Declare the file found event")]

<span data-ttu-id="ca3f8-140">Bu, nesne odaklı kötü bir uygulama gibi görünen bir ortak alan bildirmek gibi görünüyor.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-140">This looks like it's declaring a public field, which would appear to be bad object-oriented practice.</span></span> <span data-ttu-id="ca3f8-141">Özellikler veya yöntemler aracılığıyla veri erişimini korumak istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-141">You want to protect data access through properties, or methods.</span></span> <span data-ttu-id="ca3f8-142">Kötü bir uygulama gibi görünebilir ancak derleyici tarafından oluşturulan kod, olay nesnelerine yalnızca güvenli yollarla erişilebilmesi için sarmalayıcılar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-142">While this may look like a bad practice, the code generated by the compiler does create wrappers so that the event objects can only be accessed in safe ways.</span></span> <span data-ttu-id="ca3f8-143">Alan benzeri bir olayda kullanılabilen tek işlemler ekleme işleyicisidir:</span><span class="sxs-lookup"><span data-stu-id="ca3f8-143">The only operations available on a field-like event are add handler:</span></span>

[!code-csharp[DeclareEventHandler](../../samples/snippets/csharp/events/Program.cs#DeclareEventHandler "Declare the file found event handler")]

<span data-ttu-id="ca3f8-144">ve işleyiciyi kaldır:</span><span class="sxs-lookup"><span data-stu-id="ca3f8-144">and remove handler:</span></span>

[!code-csharp[RemoveEventHandler](../../samples/snippets/csharp/events/Program.cs#RemoveHandler "Remove the event handler")]

<span data-ttu-id="ca3f8-145">İşleyici için yerel bir değişken olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-145">Note that there's a local variable for the handler.</span></span> <span data-ttu-id="ca3f8-146">Lambda gövdesini kullandıysanız, kaldırma doğru çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-146">If you used the body of the lambda, the remove would not work correctly.</span></span> <span data-ttu-id="ca3f8-147">Bu, temsilcinin farklı bir örneği olur ve sessizce hiçbir şey yapmaz.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-147">It would be a different instance of the delegate, and silently do nothing.</span></span>

<span data-ttu-id="ca3f8-148">Sınıf dışındaki kod, olayı yükseltemez, diğer işlemleri de gerçekleştiremez.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-148">Code outside the class cannot raise the event, nor can it perform any other operations.</span></span>

## <a name="returning-values-from-event-subscribers"></a><span data-ttu-id="ca3f8-149">Olay abonelerinden değer döndürme</span><span class="sxs-lookup"><span data-stu-id="ca3f8-149">Returning Values from Event Subscribers</span></span>

<span data-ttu-id="ca3f8-150">Basit sürümünüz sorunsuz çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-150">Your simple version is working fine.</span></span> <span data-ttu-id="ca3f8-151">Başka bir özellik ekleyelim: Iptal.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-151">Let's add another feature: Cancellation.</span></span>

<span data-ttu-id="ca3f8-152">Bulunan olayı yükselttiğinizde, bu dosya son bir aranan ise, dinleyiciler daha fazla işlemeyi durdurabilir.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-152">When you raise the found event, listeners should be able to stop further processing, if this file is that last one sought.</span></span>

<span data-ttu-id="ca3f8-153">Olay işleyicileri bir değer döndürmüyor, bu nedenle başka bir şekilde iletişim kurması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-153">The event handlers do not return a value, so you need to communicate that in another way.</span></span> <span data-ttu-id="ca3f8-154">Standart olay deseninin, olay abonelerinin iptali iletişim kurmak için kullanabileceği alanları dahil etmek için EventArgs nesnesi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-154">The standard event pattern uses the EventArgs object to include fields that event subscribers can use to communicate cancel.</span></span>

<span data-ttu-id="ca3f8-155">Iptal sözleşmesinin semantiğine bağlı olarak kullanılabilecek iki farklı desen vardır.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-155">There are two different patterns that could be used, based on the semantics of the Cancel contract.</span></span> <span data-ttu-id="ca3f8-156">Her iki durumda da, bulunan dosya olayı için EventArguments öğesine bir Boole alanı ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-156">In both cases, you'll add a boolean field to the EventArguments for the found file event.</span></span> 

<span data-ttu-id="ca3f8-157">Bir model, bir abonenin işlemi iptal edebilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-157">One pattern would allow any one subscriber to cancel the operation.</span></span>
<span data-ttu-id="ca3f8-158">Bu model için yeni alan `false`olarak başlatılır.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-158">For this pattern, the new field is initialized to `false`.</span></span> <span data-ttu-id="ca3f8-159">Herhangi bir abone, `true`olarak değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-159">Any subscriber can change it to `true`.</span></span> <span data-ttu-id="ca3f8-160">Tüm aboneler oluşturulan olayı gördüğünde, FileSearcher bileşeni Boole değerini inceler ve işlem gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-160">After all subscribers have seen the event raised, the FileSearcher component examines the boolean value and takes action.</span></span>

<span data-ttu-id="ca3f8-161">İkinci model yalnızca tüm aboneler işlemi iptal etmek istiyorlarsa işlemi iptal eder.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-161">The second pattern would only cancel the operation if all subscribers wanted the operation cancelled.</span></span> <span data-ttu-id="ca3f8-162">Bu düzende, yeni alan işlemin iptal olması gerektiğini belirtecek şekilde başlatılır ve herhangi bir abone işlemin devam etmesi gerektiğini belirtecek şekilde değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-162">In this pattern, the new field is initialized to indicate the operation should cancel, and any subscriber could change it to indicate the operation should continue.</span></span>
<span data-ttu-id="ca3f8-163">Tüm aboneler oluşturulan olayı gördüğünde, FileSearcher bileşeni Boole değerini inceler ve işlem gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-163">After all subscribers have seen the event raised, the FileSearcher component examines the boolean and takes action.</span></span> <span data-ttu-id="ca3f8-164">Bu düzende bir ek adım vardır: bileşeni, olayı gördük bir abone olup olmadığını bilmelidir.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-164">There is one extra step in this pattern: the component needs to know if any subscribers have seen the event.</span></span> <span data-ttu-id="ca3f8-165">Abone yoksa, alan yanlışlıkla iptal olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-165">If there are no subscribers, the field would indicate a cancel incorrectly.</span></span>

<span data-ttu-id="ca3f8-166">Bu örnek için ilk sürümü uygulayalim.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-166">Let's implement the first version for this sample.</span></span> <span data-ttu-id="ca3f8-167">`FileFoundArgs` türüne `CancelRequested` adlı bir Boole alanı eklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="ca3f8-167">You need to add a boolean field named `CancelRequested` to the `FileFoundArgs` type:</span></span>

[!code-csharp[EventArgs](../../samples/snippets/csharp/events/Program.cs#EventArgs "Update event arguments")]

<span data-ttu-id="ca3f8-168">Bu yeni alan, bir Boole alanı için varsayılan değer olan `false`için otomatik olarak başlatılır, böylece yanlışlıkla iptal edemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-168">This new Field is automatically initialized to `false`, the default value for a Boolean field, so you don't cancel accidentally.</span></span> <span data-ttu-id="ca3f8-169">Bileşendeki tek bir değişiklik, abonelerden birinin iptal isteğinde bulunup bulunmadığını görmek için olayı oluşturduktan sonra bayrağı denetmektir:</span><span class="sxs-lookup"><span data-stu-id="ca3f8-169">The only other change to the component is to check the flag after raising the event to see if any of the subscribers have requested a cancellation:</span></span>

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

<span data-ttu-id="ca3f8-170">Bu düzenin bir avantajı, önemli olmayan bir değişiklik değildir.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-170">One advantage of this pattern is that it isn't a breaking change.</span></span>
<span data-ttu-id="ca3f8-171">Abonelerden hiçbiri daha önce bir iptal isteğinde bulunmadı ve yine de yok.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-171">None of the subscribers requested a cancellation before, and they still are not.</span></span> <span data-ttu-id="ca3f8-172">Yeni iptal protokolünü desteklemek istemmedikleri takdirde abone kodunun hiçbirinin güncelleştirilmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-172">None of the subscriber code needs updating unless they want to support the new cancel protocol.</span></span> <span data-ttu-id="ca3f8-173">Çok esnek bir şekilde bağlanmış.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-173">It's very loosely coupled.</span></span>

<span data-ttu-id="ca3f8-174">İlk yürütülebilir dosyayı bulduktan sonra bir iptali istemesi için aboneyi güncelleştirelim:</span><span class="sxs-lookup"><span data-stu-id="ca3f8-174">Let's update the subscriber so that it requests a cancellation once it finds the first executable:</span></span>

```csharp
EventHandler<FileFoundArgs> onFileFound = (sender, eventArgs) =>
{
    Console.WriteLine(eventArgs.FoundFile);
    eventArgs.CancelRequested = true;
};
```

## <a name="adding-another-event-declaration"></a><span data-ttu-id="ca3f8-175">Başka bir olay bildirimi ekleme</span><span class="sxs-lookup"><span data-stu-id="ca3f8-175">Adding Another Event Declaration</span></span>

<span data-ttu-id="ca3f8-176">Daha fazla özellik ekleyelim ve olaylar için diğer dil deyimler gösterimi.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-176">Let's add one more feature, and demonstrate other language idioms for events.</span></span> <span data-ttu-id="ca3f8-177">Dosya aramasında tüm alt dizinlere geçiş yapan `Search` yönteminin bir aşırı yüklemesini ekleyelim.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-177">Let's add an overload of the `Search` method that traverses all subdirectories in search of files.</span></span>

<span data-ttu-id="ca3f8-178">Bu, çok sayıda alt dizine sahip bir dizinde uzun bir işlem olabilir.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-178">This could get to be a lengthy operation in a directory with many sub-directories.</span></span> <span data-ttu-id="ca3f8-179">Her yeni dizin araması başladığında ortaya çıkan bir olay ekleyelim.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-179">Let's add an event that gets raised when each new directory search begins.</span></span> <span data-ttu-id="ca3f8-180">Bu sayede aboneler ilerlemeyi izleyebilir ve kullanıcıyı ilerleme durumuna göre güncelleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-180">This enables subscribers to track progress, and update the user as to progress.</span></span> <span data-ttu-id="ca3f8-181">Şimdiye kadar oluşturduğunuz tüm örnekler geneldir.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-181">All the samples you've created so far are public.</span></span> <span data-ttu-id="ca3f8-182">Bunu bir iç olay haline olalım.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-182">Let's make this one an internal event.</span></span> <span data-ttu-id="ca3f8-183">Diğer bir deyişle, iç değişkenler için de kullanılan türleri de yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-183">That means you can also make the types used for the arguments internal as well.</span></span>

<span data-ttu-id="ca3f8-184">Yeni dizin ve ilerlemeyi raporlamak için yeni EventArgs türetilmiş sınıfını oluşturarak başlayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-184">You'll start by creating the new EventArgs derived class for reporting the new directory and progress.</span></span> 

[!code-csharp[DirEventArgs](../../samples/snippets/csharp/events/Program.cs#SearchDirEventArgs "Define search directory event arguments")]

<span data-ttu-id="ca3f8-185">Yine, olay bağımsız değişkenleri için sabit bir başvuru türü oluşturmak üzere önerileri izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-185">Again, you can follow the recommendations to make an immutable reference type for the event arguments.</span></span>

<span data-ttu-id="ca3f8-186">Sonra, olayı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-186">Next, define the event.</span></span> <span data-ttu-id="ca3f8-187">Bu kez, farklı bir sözdizimi kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-187">This time, you'll use a different syntax.</span></span> <span data-ttu-id="ca3f8-188">Alan söz dizimini kullanmanın yanı sıra, özelliği ekleme ve kaldırma işleyicileri ile açık bir şekilde oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-188">In addition to using the field syntax, you can explicitly create the property, with add and remove handlers.</span></span> <span data-ttu-id="ca3f8-189">Bu örnekte, bu işleyicilerde ek kod gerekmez, ancak bunları nasıl oluşturacağınız gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-189">In this sample, you won't need extra code in those handlers, but this shows how you would create them.</span></span>

[!code-csharp[Declare event with add and remove handlers](../../samples/snippets/csharp/events/Program.cs#DeclareSearchEvent "Declare the event with add and remove handlers")]

<span data-ttu-id="ca3f8-190">Birçok şekilde, yazdığınız kod, daha önce gördüğünüz alan olay tanımları için derleyicinin oluşturduğu kodu yansıtır.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-190">In many ways, the code you write here mirrors the code the compiler generates for the field event definitions you've seen earlier.</span></span> <span data-ttu-id="ca3f8-191">[Özellikler](properties.md)için kullanılan için çok benzer sözdizimini kullanarak olayı oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-191">You create the event using syntax very similar to that used for [properties](properties.md).</span></span> <span data-ttu-id="ca3f8-192">İşleyicilerin farklı adlara sahip olduğuna dikkat edin: `add` ve `remove`.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-192">Notice that the handlers have different names: `add` and `remove`.</span></span> <span data-ttu-id="ca3f8-193">Bunlar olaya abone olmak ya da olaydan abonelik kaldırmak için çağırılır.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-193">These are called to subscribe to the event, or unsubscribe from the event.</span></span> <span data-ttu-id="ca3f8-194">Ayrıca, olay değişkenini depolamak için özel bir destek alanı bildirmeniz gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-194">Notice that you also must declare a private backing field to store the event variable.</span></span> <span data-ttu-id="ca3f8-195">Null olarak başlatılır.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-195">It is initialized to null.</span></span>

<span data-ttu-id="ca3f8-196">Sonra, alt dizinlere geçiş yapan `Search` yönteminin aşırı yüklemesini ekleyelim ve her iki olayı da oluşturuyor.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-196">Next, let's add the overload of the `Search` method that traverses subdirectories and raises both events.</span></span> <span data-ttu-id="ca3f8-197">Bunu yapmanın en kolay yolu, tüm dizinlerde arama yapmak istediğinizi belirtmek için varsayılan bir bağımsız değişken kullanmaktır:</span><span class="sxs-lookup"><span data-stu-id="ca3f8-197">The easiest way to accomplish this is to use a default argument to specify that you want to search all directories:</span></span>

[!code-csharp[SearchImplementation](../../samples/snippets/csharp/events/Program.cs#FinalImplementation "Implementation to search directories")]

<span data-ttu-id="ca3f8-198">Bu noktada, tüm alt dizinleri aramak için aşırı yüklemeyi çağıran uygulamayı çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-198">At this point, you can run the application calling the overload for searching all sub-directories.</span></span> <span data-ttu-id="ca3f8-199">Yeni `ChangeDirectory` olayında abone yoktur, ancak `?.Invoke()` deyim kullanmak bunun doğru şekilde çalıştığından emin olmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-199">There are no subscribers on the new `ChangeDirectory` event, but using the `?.Invoke()` idiom ensures that this works correctly.</span></span>

 <span data-ttu-id="ca3f8-200">Konsol penceresinde ilerleme durumunu gösteren bir çizgi yazmak için bir işleyici ekleyelim.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-200">Let's add a handler to write a line that shows the progress in the console window.</span></span> 

[!code-csharp[Search](../../samples/snippets/csharp/events/Program.cs#Search "Declare event handler")]

<span data-ttu-id="ca3f8-201">.NET ekosisteminin tamamında izlenen desenleri gördünüz.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-201">You've seen patterns that are followed throughout the .NET ecosystem.</span></span>
<span data-ttu-id="ca3f8-202">Bu desenleri ve kuralları öğrenerek, hızlı bir şekilde C# ve .net ' i hızla yazabileceksiniz.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-202">By learning these patterns and conventions, you'll be writing idiomatic C# and .NET quickly.</span></span>

<span data-ttu-id="ca3f8-203">Daha sonra, en son .NET sürümünde bu desenlerde bazı değişiklikler görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="ca3f8-203">Next, you'll see some changes in these patterns in the most recent release of .NET.</span></span>

[<span data-ttu-id="ca3f8-204">Next</span><span class="sxs-lookup"><span data-stu-id="ca3f8-204">Next</span></span>](modern-events.md)
