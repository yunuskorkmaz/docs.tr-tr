---
title: "Temsilciler için ortak desenler"
description: "Temsilciler kodunuzda güçlü bileşeniniz arasında Kaçın kullanmayı için ortak desenler hakkında bilgi edinin."
keywords: .NET, .NET core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 0ff8fdfd-6a11-4327-b061-0f2526f35b43
ms.openlocfilehash: 83214800fb997e9274cacfd1bae85ab07c4515a2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="common-patterns-for-delegates"></a><span data-ttu-id="3e939-104">Temsilciler için ortak desenler</span><span class="sxs-lookup"><span data-stu-id="3e939-104">Common Patterns for Delegates</span></span>

[<span data-ttu-id="3e939-105">Önceki</span><span class="sxs-lookup"><span data-stu-id="3e939-105">Previous</span></span>](delegates-strongly-typed.md)

<span data-ttu-id="3e939-106">Temsilciler bileşenler arasındaki en az bağlantı içeren yazılım tasarımları sağlayan bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="3e939-106">Delegates provide a mechanism that enables software designs involving minimal coupling between components.</span></span>

<span data-ttu-id="3e939-107">Bu tür bir tasarım için mükemmel bir örnek LINQ ' dir.</span><span class="sxs-lookup"><span data-stu-id="3e939-107">One excellent example for this kind of design is LINQ.</span></span> <span data-ttu-id="3e939-108">LINQ Sorgu ifade deseni özelliklerinin tümünü temsilcileri kullanır.</span><span class="sxs-lookup"><span data-stu-id="3e939-108">The LINQ Query Expression Pattern relies on delegates for all of its features.</span></span> <span data-ttu-id="3e939-109">Bu basit örnekte göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="3e939-109">Consider this simple example:</span></span>

```csharp
var smallNumbers = numbers.Where(n => n < 10);
```

<span data-ttu-id="3e939-110">Bu, yalnızca değerinden 10 sayılara dizisini filtreler.</span><span class="sxs-lookup"><span data-stu-id="3e939-110">This filters the sequence of numbers to only those less than the value 10.</span></span>
<span data-ttu-id="3e939-111">`Where` Yöntemi kullanan bir dizi hangi öğeleri filtre geçip belirler bir temsilci.</span><span class="sxs-lookup"><span data-stu-id="3e939-111">The `Where` method uses a delegate that determines which elements of a sequence pass the filter.</span></span> <span data-ttu-id="3e939-112">LINQ sorgu oluşturduğunuzda, bu belirli bir amaca yönelik temsilci uyarlamasını sağlayın.</span><span class="sxs-lookup"><span data-stu-id="3e939-112">When you create a LINQ query, you supply the implementation of the delegate for this specific purpose.</span></span>

<span data-ttu-id="3e939-113">Prototip yerdir yöntemi için:</span><span class="sxs-lookup"><span data-stu-id="3e939-113">The prototype for the Where method is:</span></span>

```csharp
public static IEnumerable<TSource> Where<in TSource> (IEnumerable<TSource> source, Func<TSource, bool> predicate);
```

<span data-ttu-id="3e939-114">Bu örnek LINQ parçası olan tüm yöntemleri ile yinelenir.</span><span class="sxs-lookup"><span data-stu-id="3e939-114">This example is repeated with all the methods that are part of LINQ.</span></span> <span data-ttu-id="3e939-115">Tüm temsilcileri belirli sorgu yönetir kodu güvenirler.</span><span class="sxs-lookup"><span data-stu-id="3e939-115">They all rely on delegates for the code that manages the specific query.</span></span> <span data-ttu-id="3e939-116">Bu API tasarım deseni öğrenin ve anlamak için çok güçlü bir adrestir.</span><span class="sxs-lookup"><span data-stu-id="3e939-116">This API design pattern is a very powerful one to learn and understand.</span></span>

<span data-ttu-id="3e939-117">Bu basit örnekte, nasıl temsilciler bileşenleri arasında çok az bağlantı gerektiren gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3e939-117">This simple example illustrates how delegates require very little coupling between components.</span></span> <span data-ttu-id="3e939-118">Belirli bir taban sınıftan türeyen bir sınıf oluşturmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="3e939-118">You don't need to create a class that derives from a particular base class.</span></span> <span data-ttu-id="3e939-119">Belirli bir arabirim uygulamanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="3e939-119">You don't need to implement a specific interface.</span></span>
<span data-ttu-id="3e939-120">Tek gereksinim elinizdeki için temel bir yöntemin kullanımı sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="3e939-120">The only requirement is to provide the implementation of one method that is fundamental to the task at hand.</span></span>

## <a name="building-your-own-components-with-delegates"></a><span data-ttu-id="3e939-121">Temsilcileri kendi bileşenleriyle oluşturma</span><span class="sxs-lookup"><span data-stu-id="3e939-121">Building Your Own Components with Delegates</span></span>

<span data-ttu-id="3e939-122">Şimdi bu örneğinde yetkililer güvenen bir tasarım kullanarak bir bileşeni oluşturarak oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3e939-122">Let's build on that example by creating a component using a design that relies on delegates.</span></span>

<span data-ttu-id="3e939-123">Şimdi, büyük bir sistemde günlüğü iletileri için kullanılabilecek bir bileşen tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="3e939-123">Let's define a component that could be used for log messages in a large system.</span></span> <span data-ttu-id="3e939-124">Kitaplığı bileşenlerini birden çok farklı platformlarda birçok farklı ortamlarda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3e939-124">The library components could be used in many different environments, on multiple different platforms.</span></span> <span data-ttu-id="3e939-125">Birçok ortak özellik günlüklerini yönetir bileşeninde vardır.</span><span class="sxs-lookup"><span data-stu-id="3e939-125">There are a lot of common features in the component that manages the logs.</span></span> <span data-ttu-id="3e939-126">Sistemde herhangi bir bileşenin gelen iletileri kabul etmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="3e939-126">It will need to accept messages from any component in the system.</span></span> <span data-ttu-id="3e939-127">Bu iletiler çekirdek bileşeni yönetebilirsiniz farklı önceliklere sahip olur.</span><span class="sxs-lookup"><span data-stu-id="3e939-127">Those messages will have different priorities, which the core component can manage.</span></span> <span data-ttu-id="3e939-128">İletileri zaman damgaları kendi son arşivlenmiş biçiminde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3e939-128">The messages should have timestamps in their final archived form.</span></span> <span data-ttu-id="3e939-129">Daha Gelişmiş senaryolar için kaynak bileşen tarafından iletileri filtre uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e939-129">For more advanced scenarios, you could filter messages by the source component.</span></span>

<span data-ttu-id="3e939-130">Genellikle değiştirecek özelliği tek bir yönüne yoktur: iletileri yazıldığı.</span><span class="sxs-lookup"><span data-stu-id="3e939-130">There is one aspect of the feature that will change often: where messages are written.</span></span> <span data-ttu-id="3e939-131">Bazı ortamlarda, bunlar hata konsola yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="3e939-131">In some environments, they may be written to the error console.</span></span> <span data-ttu-id="3e939-132">Bazı durumlarda, bir dosya.</span><span class="sxs-lookup"><span data-stu-id="3e939-132">In others, a file.</span></span> <span data-ttu-id="3e939-133">Diğer olasılıklar veritabanı depolama, işletim sistemi olay günlüklerini veya başka bir belge depolama içerir.</span><span class="sxs-lookup"><span data-stu-id="3e939-133">Other possibilities include database storage, OS event logs, or other document storage.</span></span>

<span data-ttu-id="3e939-134">Farklı senaryolarda kullanılabilir çıktı birleşimlerini vardır.</span><span class="sxs-lookup"><span data-stu-id="3e939-134">There are also combinations of output that might be used in different scenarios.</span></span> <span data-ttu-id="3e939-135">İletilerini konsola ve bir dosyaya yazmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e939-135">You may want to write messages to the console and to a file.</span></span>

<span data-ttu-id="3e939-136">Temsilciler üzerinde temel tasarım esneklik büyük bir bölümünü sağlayın ve gelecekte eklenebilir destek depolama mekanizmaları kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="3e939-136">A design based on delegates will provide a great deal of flexibility, and make it easy to support storage mechanisms that may be added in the future.</span></span>

<span data-ttu-id="3e939-137">Bu tasarım altında birincil günlük bileşeni bir sanal olmayan, hatta sınıf korumalı olabilir.</span><span class="sxs-lookup"><span data-stu-id="3e939-137">Under this design, the primary log component can be a non-virtual, even sealed class.</span></span> <span data-ttu-id="3e939-138">Farklı depolama ortamına ileti yazmak için temsilciler kümesinden ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e939-138">You can plug in any set of delegates to write the messages to different storage media.</span></span> <span data-ttu-id="3e939-139">Çok noktaya yayın temsilcileri için yerleşik destek iletileri birden fazla konuma (bir dosya ve bir konsol) burada yazılmalıdır destek senaryoları kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="3e939-139">The built in support for multicast delegates makes it easy to support scenarios where messages must be written to multiple locations (a file, and a console).</span></span>

## <a name="a-first-implementation"></a><span data-ttu-id="3e939-140">İlk uygulama</span><span class="sxs-lookup"><span data-stu-id="3e939-140">A First Implementation</span></span>

<span data-ttu-id="3e939-141">Küçük başlayalım: ilk uygulama yeni iletileri kabul edin ve herhangi bir ekli temsilci kullanarak bunları yazma.</span><span class="sxs-lookup"><span data-stu-id="3e939-141">Let's start small: the initial implementation will accept new messages, and write them using any attached delegate.</span></span> <span data-ttu-id="3e939-142">İletilerini konsola yazar bir temsilci ile başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e939-142">You can start with one delegate that writes messages to the console.</span></span>

```csharp
public static class Logger
{
    public static Action<string> WriteMessage;
    
    public static void LogMessage(string msg)
    {
        WriteMessage(msg);
    }
}
```

<span data-ttu-id="3e939-143">Yukarıdaki statik sınıf çalışabileceği en basit bir şeydir.</span><span class="sxs-lookup"><span data-stu-id="3e939-143">The static class above is the simplest thing that can work.</span></span> <span data-ttu-id="3e939-144">İletilerini konsola yazar yöntemi için tek uygulama yazmak ihtiyacımız var:</span><span class="sxs-lookup"><span data-stu-id="3e939-144">We need to write the single implementation for the method that writes messages to the console:</span></span> 

```csharp
public static void LogToConsole(string message)
{
    Console.Error.WriteLine(message);
}
```

<span data-ttu-id="3e939-145">Son olarak, temsilci Günlükçü bildirilen WriteMessage ekleyerek temsilci bağlama gerekir:</span><span class="sxs-lookup"><span data-stu-id="3e939-145">Finally, you need to hook up the delegate by attaching it to the WriteMessage delegate declared in the logger:</span></span>

```csharp
Logger.WriteMessage += LogToConsole;
```

## <a name="practices"></a><span data-ttu-id="3e939-146">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="3e939-146">Practices</span></span>

<span data-ttu-id="3e939-147">Bizim örnek kadarki de oldukça basittir, ancak bunu hala temsilciler içeren tasarımları için önemli yönergeleri bazılarını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="3e939-147">Our sample so far is fairly simple, but it still demonstrates some of the important guidelines for designs involving delegates.</span></span>

<span data-ttu-id="3e939-148">Çekirdek çerçevesinde tanımlanan temsilci türleri, temsilci ile çalışmak kullanıcıların kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="3e939-148">Using the delegate types defined in the Core Framework makes it easier for users to work with the delegates.</span></span> <span data-ttu-id="3e939-149">Yeni türlerini tanımlamak üzere gerekmez ve yeni, özelleştirilmiş temsilci türleri öğrenmek kitaplığınızın kullanan geliştiriciler gerekmez.</span><span class="sxs-lookup"><span data-stu-id="3e939-149">You don't need to define new types, and developers using your library do not need to learn new, specialized delegate types.</span></span>

<span data-ttu-id="3e939-150">Kullanılan arabirimlere olarak minimal ve kadar esnek: yeni bir çıkış Günlükçü oluşturmak için bir yöntem oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3e939-150">The interfaces used are as minimal and as flexible as possible: To create a new output logger, you must create one method.</span></span> <span data-ttu-id="3e939-151">Bu yöntem, bir statik yöntem veya örnek yöntemi olabilir.</span><span class="sxs-lookup"><span data-stu-id="3e939-151">That method may be a static method, or an instance method.</span></span> <span data-ttu-id="3e939-152">Herhangi bir erişim olabilir.</span><span class="sxs-lookup"><span data-stu-id="3e939-152">It may have any access.</span></span>

## <a name="formatting-output"></a><span data-ttu-id="3e939-153">Çıktı biçimlendirmesi</span><span class="sxs-lookup"><span data-stu-id="3e939-153">Formatting Output</span></span>

<span data-ttu-id="3e939-154">Bu ilk sürüm bir bit daha sağlam ve diğer günlük mekanizmaları oluşturma başlatın olalım.</span><span class="sxs-lookup"><span data-stu-id="3e939-154">Let's make this first version a bit more robust, and then start creating other logging mechanisms.</span></span>

<span data-ttu-id="3e939-155">Ardından, birkaç bağımsız değişkenleri ekleyelim `LogMessage()` yöntemi günlük sınıfınıza daha fazla yapılandırılmış ileti oluşturur, böylece:</span><span class="sxs-lookup"><span data-stu-id="3e939-155">Next, let's add a few arguments to the `LogMessage()` method so that your log class creates more structured messages:</span></span>

```csharp
// Logger implementation two
public enum Severity
{
    Verbose,
    Trace,
    Information,
    Warning,
    Error,
    Critical
}

public static class Logger
{
    public static Action<string> WriteMessage;
    
    public static void LogMessage(Severity s, string component, string msg)
    {
        var outputMsg = $"{DateTime.Now}\t{s}\t{component}\t{msg}";
        WriteMessage(outputMsg);
    }
}
```

<span data-ttu-id="3e939-156">Ardından, olalım kullanan `Severity` animasyonun günlüğüne gönderilen iletilere filtre uygulamak için bağımsız değişken çıktı.</span><span class="sxs-lookup"><span data-stu-id="3e939-156">Next, let's make use of that `Severity` argument to filter the messages that are sent to the log's output.</span></span> 

```csharp
public static class Logger
{
    public static Action<string> WriteMessage;
    
    public static Severity LogLevel {get;set;} = Severity.Warning;
    
    public static void LogMessage(Severity s, string component, string msg)
    {
        if (s < LogLevel)
            return;
            
        var outputMsg = $"{DateTime.Now}\t{s}\t{component}\t{msg}";
        WriteMessage(outputMsg);
    }
}
```
## <a name="practices"></a><span data-ttu-id="3e939-157">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="3e939-157">Practices</span></span>

<span data-ttu-id="3e939-158">Günlük altyapısı yeni özellik ekledik.</span><span class="sxs-lookup"><span data-stu-id="3e939-158">You've added new features to the logging infrastructure.</span></span> <span data-ttu-id="3e939-159">Günlükçü bileşeni çok herhangi bir çıktı mekanizma gevşek için herhangi bir Günlükçü temsilci uygulama kodu hiçbir etkisi olmadan bu yeni özellikler eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="3e939-159">Because the logger component is very loosely coupled to any output mechanism, these new features can be added with no impact on any of the code implementing the logger delegate.</span></span>

<span data-ttu-id="3e939-160">Bu derleme tutmak gibi daha fazla örnekleri bu gevşek bağlantı herhangi bir değişiklik yapılmadan sitesinin bölümlerini başka konumlara güncelleştirme esneklik nasıl sağladığını görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="3e939-160">As you keep building this, you'll see more examples of how this loose coupling enables greater flexibility in updating parts of the site without any changes to other locations.</span></span> <span data-ttu-id="3e939-161">Aslında, daha büyük bir uygulamanın Günlükçü çıktı sınıfları farklı bir derlemede olması ve bile yeniden oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3e939-161">In fact, in a larger application, the logger output classes might be in a different assembly, and not even need to be rebuilt.</span></span>

## <a name="building-a-second-output-engine"></a><span data-ttu-id="3e939-162">İkinci bir çıktı altyapısı oluşturma</span><span class="sxs-lookup"><span data-stu-id="3e939-162">Building a Second Output Engine</span></span>

<span data-ttu-id="3e939-163">Günlük bileşeni iyi geliyor.</span><span class="sxs-lookup"><span data-stu-id="3e939-163">The Log component is coming along well.</span></span> <span data-ttu-id="3e939-164">İletiler bir dosyaya kaydeder bir daha fazla çıkış altyapısı ekleyelim.</span><span class="sxs-lookup"><span data-stu-id="3e939-164">Let's add one more output engine that logs messages to a file.</span></span> <span data-ttu-id="3e939-165">Bu biraz daha karmaşık bir çıkış altyapısı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="3e939-165">This will be a slightly more involved output engine.</span></span> <span data-ttu-id="3e939-166">Dosya işlemleri yalıtır ve dosyayı her zaman sonra her bir yazma kapalı sağlar bir sınıf olacaktır.</span><span class="sxs-lookup"><span data-stu-id="3e939-166">It will be a class that encapsulates the file operations, and ensures that the file is always closed after each write.</span></span> <span data-ttu-id="3e939-167">Sağlar, tüm verileri Temizlenen her ileti oluşturulduktan sonra disk.</span><span class="sxs-lookup"><span data-stu-id="3e939-167">That ensures that all the data is flushed to disk after each message is generated.</span></span>

<span data-ttu-id="3e939-168">Bu dosya tabanlı Günlükçü şöyledir:</span><span class="sxs-lookup"><span data-stu-id="3e939-168">Here is that file based logger:</span></span>

```csharp
public class FileLogger
{
    private readonly string logPath;
    public FileLogger(string path)
    {
        logPath = path;
        Logger.WriteMessage += LogMessage;
    }
    
    public void DetachLog() => Logger.WriteMessage -= LogMessage;

    // make sure this can't throw.
    private void LogMessage(string msg)
    {
        try {
            using (var log = File.AppendText(logPath))
            {
                log.WriteLine(msg);
                log.Flush();
            }
        } catch (Exception e)
        {
            // Hmm. Not sure what to do.
            // Logging is failing...
        }
    }
}
```

<span data-ttu-id="3e939-169">Bu sınıf oluşturduktan sonra örneğini oluşturabilir ve kendi LogMessage yöntemi Günlükçü bileşenine ekler:</span><span class="sxs-lookup"><span data-stu-id="3e939-169">Once you've created this class, you can instantiate it and it attaches its LogMessage method to the Logger component:</span></span>

```csharp
var file = new FileLogger("log.txt");
```

<span data-ttu-id="3e939-170">Bu iki birbirini dışlamaz.</span><span class="sxs-lookup"><span data-stu-id="3e939-170">These two are not mutually exclusive.</span></span> <span data-ttu-id="3e939-171">Her iki günlük yöntemleri ekleyin ve iletileri konsolu ve bir dosya oluşturmak:</span><span class="sxs-lookup"><span data-stu-id="3e939-171">You could attach both log methods and generate messages to the console and a file:</span></span>

```csharp
var fileOutput = new FileLogger("log.txt");
Logger.WriteMessage += LogToConsole;
```

<span data-ttu-id="3e939-172">Daha sonra bile aynı uygulamada sisteme herhangi bir sorun olmadan temsilcileri birini kaldırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3e939-172">Later, even in the same application, you can remove one of the delegates without any other issues to the system:</span></span>

```csharp
Logger.WriteMessage -= LogToConsole;
```

## <a name="practices"></a><span data-ttu-id="3e939-173">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="3e939-173">Practices</span></span>

<span data-ttu-id="3e939-174">Şimdi, günlük alt sistemi için ikinci bir çıktı işleyici ekledik.</span><span class="sxs-lookup"><span data-stu-id="3e939-174">Now, you've added a second output handler for the logging sub-system.</span></span>
<span data-ttu-id="3e939-175">Bunun doğru dosya sistemi desteklemek için biraz daha fazla altyapı gerekir.</span><span class="sxs-lookup"><span data-stu-id="3e939-175">This one needs a bit more infrastructure to correctly support the file system.</span></span> <span data-ttu-id="3e939-176">Temsilci bir örnek yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="3e939-176">The delegate is an instance method.</span></span> <span data-ttu-id="3e939-177">Bu da özel bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="3e939-177">It's also a private method.</span></span>
<span data-ttu-id="3e939-178">Temsilci altyapısını temsilcileri bağlanabildiğinden büyük erişilebilirlik gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="3e939-178">There's no need for greater accessibility because the delegate infrastructure can connect the delegates.</span></span>

<span data-ttu-id="3e939-179">İkinci olarak, temsilci tabanlı tasarım herhangi bir ek kod olmadan birden çok çıktı yöntemlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="3e939-179">Second, the delegate-based design enables multiple output methods without any extra code.</span></span> <span data-ttu-id="3e939-180">Birden çok çıktı yöntemlerini desteklemek için herhangi bir ek altyapı yapılandırmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="3e939-180">You don't need to build any additional infrastructure to support multiple output methods.</span></span> <span data-ttu-id="3e939-181">Bunlar yalnızca başka bir yöntem çağırma listesinde haline gelir.</span><span class="sxs-lookup"><span data-stu-id="3e939-181">They simply become another method on the invocation list.</span></span>

<span data-ttu-id="3e939-182">Özel çıkış yöntemi günlük dosyasındaki kodu dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="3e939-182">Pay special attention to the code in the file logging output method.</span></span> <span data-ttu-id="3e939-183">Özel durumlar oluşturmadığını emin olmak için kodlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="3e939-183">It is coded to ensure that it does not throw any exceptions.</span></span> <span data-ttu-id="3e939-184">Bu her zaman kesinlikle gerekli olmasa da, genellikle iyi bir uygulama olur.</span><span class="sxs-lookup"><span data-stu-id="3e939-184">While this isn't always strictly necessary, it's often a good practice.</span></span> <span data-ttu-id="3e939-185">Temsilci yöntemlerinden birini bir özel durum oluşturursa, çağrısının olan kalan temsilcileri çağrılan olmaz.</span><span class="sxs-lookup"><span data-stu-id="3e939-185">If either of the delegate methods throws an exception, the remaining delegates that are on the invocation won't be invoked.</span></span>

<span data-ttu-id="3e939-186">Son Not Dosya Günlükçü, açma ve kapama dosyanın her günlüğü iletisine göre kaynaklarını yönetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3e939-186">As a last note, the file logger must manage its resources by opening and closing the file on each log message.</span></span> <span data-ttu-id="3e939-187">Dosya açık tutmak ve size tamamlandığında dosyasını kapatmaya IDisposable uygulayan tercih edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e939-187">You could choose to keep the file open and implement IDisposable to close the file when you are completed.</span></span>
<span data-ttu-id="3e939-188">Her iki yöntem, avantajları ve dezavantajları vardır.</span><span class="sxs-lookup"><span data-stu-id="3e939-188">Either method has its advantages and disadvantages.</span></span> <span data-ttu-id="3e939-189">Her ikisi de sınıflar arasında biraz daha fazla bağlantı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3e939-189">Both do create a bit more coupling between the classes.</span></span>

<span data-ttu-id="3e939-190">Günlükçü sınıfı kodda hiçbiri, her iki senaryoyu desteklemek için güncelleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="3e939-190">None of the code in the Logger class would need to be updated in order to support either scenario.</span></span>

## <a name="handling-null-delegates"></a><span data-ttu-id="3e939-191">İşleme Null temsilciler</span><span class="sxs-lookup"><span data-stu-id="3e939-191">Handling Null Delegates</span></span>

<span data-ttu-id="3e939-192">Son olarak, böylece hiçbir çıktı mekanizması seçildiğinde bu gibi durumlarda sağlam şimdi LogMessage yöntemi güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="3e939-192">Finally, let's update the LogMessage method so that it is robust for those cases when no output mechanism is selected.</span></span> <span data-ttu-id="3e939-193">Geçerli uygulama özel durum oluşturacak bir `NullReferenceException` zaman `WriteMessage` temsilci bağlı bir çağrı listesi yok.</span><span class="sxs-lookup"><span data-stu-id="3e939-193">The current implementation will throw a `NullReferenceException` when the `WriteMessage` delegate does not have an invocation list attached.</span></span>
<span data-ttu-id="3e939-194">Hiçbir yöntemi eklendiğinde sessizce devam bir tasarım tercih edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e939-194">You may prefer a design that silently continues when no methods have been attached.</span></span> <span data-ttu-id="3e939-195">Bu birlikte null koşullu işlecini kullanarak kolaydır `Delegate.Invoke()` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="3e939-195">This is easy using the null conditional operator, combined with the `Delegate.Invoke()` method:</span></span>

```csharp
public static void LogMessage(string msg)
{
    WriteMessage?.Invoke(msg);
}
```

<span data-ttu-id="3e939-196">Null koşullu işleç (`?.`) ne zaman short-circuits sol işleneni (`WriteMessage` bu durumda) herhangi bir deneme yapılır bir ileti günlüğe anlamına gelir null.</span><span class="sxs-lookup"><span data-stu-id="3e939-196">The null conditional operator (`?.`) short-circuits when the left operand (`WriteMessage` in this case) is null, which means no attempt is made to log a message.</span></span>

<span data-ttu-id="3e939-197">Bulamaz `Invoke()` yöntemi listelenen belgelerindeki `System.Delegate` veya `System.MulticastDelegate`.</span><span class="sxs-lookup"><span data-stu-id="3e939-197">You won't find the `Invoke()` method listed in the documentation for `System.Delegate` or `System.MulticastDelegate`.</span></span> <span data-ttu-id="3e939-198">Tür uyumlu derleyici oluşturur `Invoke` yöntemi herhangi temsilci bildirilen türü.</span><span class="sxs-lookup"><span data-stu-id="3e939-198">The compiler generates a type safe `Invoke` method for any delegate type declared.</span></span> <span data-ttu-id="3e939-199">Bu örnekte, yani `Invoke` tek bir alan `string` bağımsız değişkeni, ve geçersiz bir dönüş türüne sahip.</span><span class="sxs-lookup"><span data-stu-id="3e939-199">In this example, that means `Invoke` takes a single `string` argument, and has a void return type.</span></span>

## <a name="summary-of-practices"></a><span data-ttu-id="3e939-200">Yöntemler özeti</span><span class="sxs-lookup"><span data-stu-id="3e939-200">Summary of Practices</span></span>

<span data-ttu-id="3e939-201">Genişletilemiyor günlük bileşeni beginnings diğer yazarlar ve diğer özellikleri ile gördünüz.</span><span class="sxs-lookup"><span data-stu-id="3e939-201">You've seen the beginnings of a log component that could be expanded with other writers, and other features.</span></span> <span data-ttu-id="3e939-202">Tasarımda temsilciler kullanarak farklı bu bileşenlerin çok gevşek.</span><span class="sxs-lookup"><span data-stu-id="3e939-202">By using delegates in the design these different components are very loosely coupled.</span></span> <span data-ttu-id="3e939-203">Bu, birkaç avantaj sağlar.</span><span class="sxs-lookup"><span data-stu-id="3e939-203">This provides several advantages.</span></span> <span data-ttu-id="3e939-204">Yeni çıkış mekanizmaları oluşturmak ve bunları sisteme eklemek çok kolaydır.</span><span class="sxs-lookup"><span data-stu-id="3e939-204">It's very easy to create new output mechanisms and attach them to the system.</span></span> <span data-ttu-id="3e939-205">Bu diğer mekanizmalar yalnızca bir yöntem gerekir: günlük iletisi Yazar yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3e939-205">These other mechanisms only need one method: the method that writes the log message.</span></span> <span data-ttu-id="3e939-206">Bu yeni özellikler eklendiğinde çok esnek bir tasarımdır.</span><span class="sxs-lookup"><span data-stu-id="3e939-206">It's a design that is very resilient when new features are added.</span></span> <span data-ttu-id="3e939-207">Tüm yazan bir yöntem uygulamak için gereken sözleşme.</span><span class="sxs-lookup"><span data-stu-id="3e939-207">The contract required for any writer is to implement one method.</span></span> <span data-ttu-id="3e939-208">Bu yöntem, bir statik olarak veya yöntemi örneği.</span><span class="sxs-lookup"><span data-stu-id="3e939-208">That method could be a static or instance method.</span></span> <span data-ttu-id="3e939-209">Genel, özel veya herhangi bir yasal erişim olabilir.</span><span class="sxs-lookup"><span data-stu-id="3e939-209">It could be public, private, or any other legal access.</span></span>

<span data-ttu-id="3e939-210">Günlükçü sınıfı, önemli değişiklikler oluşturmaksızın herhangi bir sayıda yenilikleri veya değişiklikleri yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e939-210">The Logger class can make any number of enhancements or changes without introducing breaking changes.</span></span> <span data-ttu-id="3e939-211">Herhangi bir sınıf gibi önemli değişiklikler riski olmadan ortak API değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e939-211">Like any class, you cannot modify the public API without the risk of breaking changes.</span></span> <span data-ttu-id="3e939-212">Ancak, Günlükçü ve herhangi bir çıktı motorları arasında bağ yalnızca temsilci olduğundan (arabirimleri veya temel sınıflar gibi) diğer türü yok ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="3e939-212">But, because the coupling between the logger and any output engines is only through the delegate, no other types (like interfaces or base classes) are involved.</span></span> <span data-ttu-id="3e939-213">Bağ olabildiğince küçük.</span><span class="sxs-lookup"><span data-stu-id="3e939-213">The coupling is as small as possible.</span></span>

[<span data-ttu-id="3e939-214">Sonraki</span><span class="sxs-lookup"><span data-stu-id="3e939-214">Next</span></span>](events-overview.md)
