---
title: Azure Işlevleri-sunucusuz uygulamalar
description: Azure işlevleri, olay odaklı anında ölçeklendirme kodu sağlamak için birden çok dilde (C#, JavaScript, Java) ve platformlarda sunucusuz yetenekler sağlar.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 04/06/2020
ms.openlocfilehash: 2dee60e3635be94a55ee26a7f04942bc59cb8dec
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135730"
---
# <a name="azure-functions"></a><span data-ttu-id="10bac-103">Azure İşlevleri</span><span class="sxs-lookup"><span data-stu-id="10bac-103">Azure Functions</span></span>

<span data-ttu-id="10bac-104">Azure işlevleri, sunucusuz bir işlem deneyimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="10bac-104">Azure functions provide a serverless compute experience.</span></span> <span data-ttu-id="10bac-105">Bir işlev bir *tetikleyici* tarafından çağrılır (bir HTTP uç noktasına veya bir zamanlayıcıya erişim gibi) ve bir kod bloğu veya iş mantığı yürütür.</span><span class="sxs-lookup"><span data-stu-id="10bac-105">A function is invoked by a *trigger* (such as access to an HTTP endpoint or a timer) and executes a block of code or business logic.</span></span> <span data-ttu-id="10bac-106">İşlevler ayrıca depolama ve kuyruklar gibi kaynaklara bağlanan özelleştirilmiş *bağlamaları* destekler.</span><span class="sxs-lookup"><span data-stu-id="10bac-106">Functions also support specialized *bindings* that connect to resources like storage and queues.</span></span>

![Azure işlevleri logosu](./media/azure-functions-logo.png)

<span data-ttu-id="10bac-108">Geçerli çalışma zamanı sürüm 3,0, platformlar arası .NET Core 3,1 uygulamalarını destekler.</span><span class="sxs-lookup"><span data-stu-id="10bac-108">The current runtime version 3.0 supports cross-platform .NET Core 3.1 applications.</span></span> <span data-ttu-id="10bac-109">JavaScript, F # ve Java gibi ek diller de desteklenir.</span><span class="sxs-lookup"><span data-stu-id="10bac-109">Additional languages besides C# such as JavaScript, F#, and Java are supported.</span></span> <span data-ttu-id="10bac-110">Portalda oluşturulan işlevler, zengin bir betik sözdizimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="10bac-110">Functions created in the portal provide a rich scripting syntax.</span></span> <span data-ttu-id="10bac-111">Tek başına projeler olarak oluşturulan işlevler, tam platform desteği ve özellikleri ile dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="10bac-111">Functions created as standalone projects can be deployed with full platform support and capabilities.</span></span>

<span data-ttu-id="10bac-112">Daha fazla bilgi için bkz. [Azure işlevleri belgeleri](https://docs.microsoft.com/azure/azure-functions).</span><span class="sxs-lookup"><span data-stu-id="10bac-112">For more information, see [Azure Functions documentation](https://docs.microsoft.com/azure/azure-functions).</span></span>

## <a name="programming-language-support"></a><span data-ttu-id="10bac-113">Programlama dili desteği</span><span class="sxs-lookup"><span data-stu-id="10bac-113">Programming language support</span></span>

<span data-ttu-id="10bac-114">Aşağıdaki dillerin tümü genel kullanılabilirlik (GA) içinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="10bac-114">The following languages are all supported in general availability (GA).</span></span>

|<span data-ttu-id="10bac-115">Dil</span><span class="sxs-lookup"><span data-stu-id="10bac-115">Language</span></span>      |<span data-ttu-id="10bac-116">Desteklenen çalışma zamanları</span><span class="sxs-lookup"><span data-stu-id="10bac-116">Supported runtimes</span></span>|
|--------------|------------------|
|<span data-ttu-id="10bac-117">**C#**</span><span class="sxs-lookup"><span data-stu-id="10bac-117">**C#**</span></span>        |<span data-ttu-id="10bac-118">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="10bac-118">.NET Core 3.1</span></span>     |
|<span data-ttu-id="10bac-119">**JavaScript**</span><span class="sxs-lookup"><span data-stu-id="10bac-119">**JavaScript**</span></span>|<span data-ttu-id="10bac-120">Düğüm 10 & 12</span><span class="sxs-lookup"><span data-stu-id="10bac-120">Node 10 & 12</span></span>      |
|<span data-ttu-id="10bac-121">**F#**</span><span class="sxs-lookup"><span data-stu-id="10bac-121">**F#**</span></span>        |<span data-ttu-id="10bac-122">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="10bac-122">.NET Core 3.1</span></span>     |
|<span data-ttu-id="10bac-123">**Java**</span><span class="sxs-lookup"><span data-stu-id="10bac-123">**Java**</span></span>      |<span data-ttu-id="10bac-124">Java 8</span><span class="sxs-lookup"><span data-stu-id="10bac-124">Java 8</span></span>            |
|<span data-ttu-id="10bac-125">**Python**</span><span class="sxs-lookup"><span data-stu-id="10bac-125">**Python**</span></span>    |<span data-ttu-id="10bac-126">Python 3,6, 3,7, & 3,8</span><span class="sxs-lookup"><span data-stu-id="10bac-126">Python 3.6, 3.7, & 3.8</span></span>|
|<span data-ttu-id="10bac-127">**TypeScript**</span><span class="sxs-lookup"><span data-stu-id="10bac-127">**TypeScript**</span></span>|<span data-ttu-id="10bac-128">Düğüm 10 & 12 (JavaScript aracılığıyla)</span><span class="sxs-lookup"><span data-stu-id="10bac-128">Node 10 & 12 (via JavaScript)</span></span>|
|<span data-ttu-id="10bac-129">**PowerShell**</span><span class="sxs-lookup"><span data-stu-id="10bac-129">**PowerShell**</span></span>|<span data-ttu-id="10bac-130">PowerShell Core 6</span><span class="sxs-lookup"><span data-stu-id="10bac-130">PowerShell Core 6</span></span>|

<span data-ttu-id="10bac-131">Daha fazla bilgi için bkz. [Desteklenen diller](https://docs.microsoft.com/azure/azure-functions/supported-languages).</span><span class="sxs-lookup"><span data-stu-id="10bac-131">For more information, see [Supported languages](https://docs.microsoft.com/azure/azure-functions/supported-languages).</span></span>

## <a name="app-service-plans"></a><span data-ttu-id="10bac-132">App Service planları</span><span class="sxs-lookup"><span data-stu-id="10bac-132">App service plans</span></span>

<span data-ttu-id="10bac-133">İşlevler bir *App Service planı*tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="10bac-133">Functions are backed by an *app service plan*.</span></span> <span data-ttu-id="10bac-134">Plan, işlevler uygulaması tarafından kullanılan kaynakları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="10bac-134">The plan defines the resources used by the functions app.</span></span> <span data-ttu-id="10bac-135">Bir bölgeye planlar atayabilir, kullanılacak sanal makinelerin boyutunu ve sayısını belirleyebilir ve bir fiyatlandırma katmanı seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="10bac-135">You can assign plans to a region, determine the size and number of virtual machines that will be used, and pick a pricing tier.</span></span> <span data-ttu-id="10bac-136">Doğru sunucusuz bir yaklaşım için işlev uygulamaları **Tüketim** planını kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="10bac-136">For a true serverless approach, function apps may use the **consumption** plan.</span></span> <span data-ttu-id="10bac-137">Tüketim planı, yük temelinde arka ucu otomatik olarak ölçeklendirecektir.</span><span class="sxs-lookup"><span data-stu-id="10bac-137">The consumption plan will scale the back end automatically based on load.</span></span>

<span data-ttu-id="10bac-138">İşlev uygulamaları için başka bir barındırma seçeneği de [Premium plandır](https://docs.microsoft.com/azure/azure-functions/functions-premium-plan).</span><span class="sxs-lookup"><span data-stu-id="10bac-138">Another hosting option for function apps is the [Premium plan](https://docs.microsoft.com/azure/azure-functions/functions-premium-plan).</span></span> <span data-ttu-id="10bac-139">Bu plan, soğuk başlangıçtan kaçınmak için "Always On" örneği sağlar, VNet bağlantısı gibi gelişmiş özellikleri destekler ve Premium donanımda çalışır.</span><span class="sxs-lookup"><span data-stu-id="10bac-139">This plan provides an "always on" instance to avoid cold start, supports advanced features like VNet connectivity, and runs on premium hardware.</span></span>

<span data-ttu-id="10bac-140">Daha fazla bilgi için bkz. [App Service planları](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).</span><span class="sxs-lookup"><span data-stu-id="10bac-140">For more information, see [App service plans](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).</span></span>

## <a name="create-your-first-function"></a><span data-ttu-id="10bac-141">İlk uygulamanızı oluşturma</span><span class="sxs-lookup"><span data-stu-id="10bac-141">Create your first function</span></span>

<span data-ttu-id="10bac-142">İşlev uygulamaları oluşturabileceğiniz üç yaygın yol vardır.</span><span class="sxs-lookup"><span data-stu-id="10bac-142">There are three common ways you can create function apps.</span></span>

- <span data-ttu-id="10bac-143">Portalda betik işlevleri.</span><span class="sxs-lookup"><span data-stu-id="10bac-143">Script functions in the portal.</span></span>
- <span data-ttu-id="10bac-144">Azure CLı kullanarak gereken kaynakları oluşturun.</span><span class="sxs-lookup"><span data-stu-id="10bac-144">Create the necessary resources using the Azure CLI.</span></span>
- <span data-ttu-id="10bac-145">En sevdiğiniz IDE 'yi kullanarak işlevleri yerel olarak derleyin ve Azure 'da yayımlayın.</span><span class="sxs-lookup"><span data-stu-id="10bac-145">Build functions locally using your favorite IDE and publish them to Azure.</span></span>

<span data-ttu-id="10bac-146">Portalda betikleştirilmiş bir işlev oluşturma hakkında daha fazla bilgi için, [Azure Portal ilk işlevinizi oluşturma](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="10bac-146">For more information on creating a scripted function in the portal, see [Create your first function in the Azure portal](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function).</span></span>

<span data-ttu-id="10bac-147">Azure CLı 'dan derlemek için bkz. [Azure CLI kullanarak ilk işlevinizi oluşturma](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli).</span><span class="sxs-lookup"><span data-stu-id="10bac-147">To build from the Azure CLI, see [Create your first function using the Azure CLI](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli).</span></span>

<span data-ttu-id="10bac-148">Visual Studio 'dan bir işlev oluşturmak için bkz. [Visual Studio kullanarak ilk işlevinizi oluşturma](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="10bac-148">To create a function from Visual Studio, see [Create your first function using Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio).</span></span>

## <a name="understand-triggers-and-bindings"></a><span data-ttu-id="10bac-149">Tetikleyicileri ve bağlamaları anlama</span><span class="sxs-lookup"><span data-stu-id="10bac-149">Understand triggers and bindings</span></span>

<span data-ttu-id="10bac-150">İşlevler bir *tetikleyici* tarafından çağrılır ve tam olarak bir tane olabilir.</span><span class="sxs-lookup"><span data-stu-id="10bac-150">Functions are invoked by a *trigger* and can have exactly one.</span></span> <span data-ttu-id="10bac-151">İşlevi çağırmaya ek olarak, bazı Tetikleyiciler de bağlamalar olarak görev yapar.</span><span class="sxs-lookup"><span data-stu-id="10bac-151">In addition to invoking the function, certain triggers also serve as bindings.</span></span> <span data-ttu-id="10bac-152">Ayrıca, tetikleyicisine ek olarak birden çok bağlama de tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="10bac-152">You may also define multiple bindings in addition to the trigger.</span></span> <span data-ttu-id="10bac-153">*Bağlamalar* , verileri kodunuza bağlamanın bildirim temelli bir yolunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="10bac-153">*Bindings* provide a declarative way to connect data to your code.</span></span> <span data-ttu-id="10bac-154">Bunlar (giriş) veya veri alabilir (çıktı).</span><span class="sxs-lookup"><span data-stu-id="10bac-154">They can be passed in (input) or receive data (output).</span></span> <span data-ttu-id="10bac-155">Tetikleyiciler ve bağlamalar işlevleri ile çalışmayı kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="10bac-155">Triggers and bindings make functions easy to work with.</span></span> <span data-ttu-id="10bac-156">Bağlamalar, veritabanı veya dosya sistemi bağlantılarını el ile oluşturma ek yükünü ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="10bac-156">Bindings remove the overhead of manually creating database or file system connections.</span></span> <span data-ttu-id="10bac-157">Bağlamalar için gereken tüm bilgiler, betikler için özel bir *Functions. JSON* dosyasında bulunur veya koddaki özniteliklerle birlikte bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="10bac-157">All of the information needed for the bindings is contained in a special *functions.json* file for scripts or declared with attributes in code.</span></span>

<span data-ttu-id="10bac-158">Bazı ortak Tetikleyiciler şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="10bac-158">Some common triggers include:</span></span>

- <span data-ttu-id="10bac-159">BLOB depolama: bir dosya veya klasör bir depolama alanında karşıya yüklenirken veya değiştirildiğinde işlevinizi çağırın.</span><span class="sxs-lookup"><span data-stu-id="10bac-159">Blob Storage: invoke your function when a file or folder is uploaded or changed in storage.</span></span>
- <span data-ttu-id="10bac-160">HTTP: işlevinizi REST API gibi çağırın.</span><span class="sxs-lookup"><span data-stu-id="10bac-160">HTTP: invoke your function like a REST API.</span></span>
- <span data-ttu-id="10bac-161">Queue: bir kuyrukta öğeler mevcutsa işlevinizi çağırın.</span><span class="sxs-lookup"><span data-stu-id="10bac-161">Queue: invoke your function when items exist in a queue.</span></span>
- <span data-ttu-id="10bac-162">Süreölçer: işlevinizi düzenli bir temposunda çağırma.</span><span class="sxs-lookup"><span data-stu-id="10bac-162">Timer: invoke your function on a regular cadence.</span></span>

<span data-ttu-id="10bac-163">Bağlama örnekleri şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="10bac-163">Examples of bindings include:</span></span>

- <span data-ttu-id="10bac-164">CosmosDB: dosyaları yüklemek veya kaydetmek için kolayca veritabanına bağlanın.</span><span class="sxs-lookup"><span data-stu-id="10bac-164">CosmosDB: easily connect to the database to load or save files.</span></span>
- <span data-ttu-id="10bac-165">Tablo Depolama: işlev uygulamanızdan anahtar/değer depolama ile çalışma.</span><span class="sxs-lookup"><span data-stu-id="10bac-165">Table Storage: work with key/value storage from your function app.</span></span>
- <span data-ttu-id="10bac-166">Kuyruk depolama: bir kuyruktan kolayca öğe alın veya yeni öğeleri kuyruğa yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="10bac-166">Queue Storage: easily retrieve items from a queue, or place new items on the queue.</span></span>

<span data-ttu-id="10bac-167">Aşağıdaki örnek *Functions. JSON* dosyası bir tetikleyiciyi ve bağlamayı tanımlar:</span><span class="sxs-lookup"><span data-stu-id="10bac-167">The following example *functions.json* file defines a trigger and a binding:</span></span>

```json
{
  "bindings": [
    {
      "name": "myBlob",
      "type": "blobTrigger",
      "direction": "in",
      "path": "images/{name}",
      "connection": "AzureWebJobsStorage"
    },
    {
      "name": "$return",
      "type": "queue",
      "direction": "out",
      "queueName": "images",
      "connection": "AzureWebJobsStorage"
    }
  ],
  "disabled": false
}
```

<span data-ttu-id="10bac-168">Bu örnekte, işlev, `images` kapsayıcıda blob depolamaya yapılan bir değişiklik tarafından tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="10bac-168">In this example, the function is triggered by a change to blob storage in the `images` container.</span></span> <span data-ttu-id="10bac-169">Dosya ile ilgili bilgiler geçirilir, bu nedenle tetikleyici de bir bağlama işlevi görür.</span><span class="sxs-lookup"><span data-stu-id="10bac-169">The information for the file is passed in, so the trigger also acts as a binding.</span></span> <span data-ttu-id="10bac-170">Adlı `images`bir kuyruğa bilgi koymak için başka bir bağlama var.</span><span class="sxs-lookup"><span data-stu-id="10bac-170">Another binding exists to put information onto a queue named `images`.</span></span>

<span data-ttu-id="10bac-171">İşlevin C# betiği aşağıdadır:</span><span class="sxs-lookup"><span data-stu-id="10bac-171">Here is the C# script for the function:</span></span>

```csharp
public static string Run(Stream myBlob, string name, TraceWriter log)
{
    log.Info($"C# Blob trigger function Processed blob\n Name:{name} \n Size: {myBlob.Length} Bytes");
    return name;
}
```

<span data-ttu-id="10bac-172">Örnek, değiştirilen veya blob depolamaya yüklenen dosyanın adını alan ve daha sonra işlenmek üzere bir kuyruğa yerleştirtiren basit bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="10bac-172">The example is a simple function that takes the name of the file that was modified or uploaded to blob storage, and places it on a queue for later processing.</span></span>

<span data-ttu-id="10bac-173">Tetikleyiciler ve bağlamaların tam listesi için bkz. [Azure işlevleri Tetikleyicileri ve bağlamaları kavramları](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings).</span><span class="sxs-lookup"><span data-stu-id="10bac-173">For a full list of triggers and bindings, see [Azure Functions triggers and bindings concepts](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="10bac-174">[Önceki](azure-serverless-platform.md)
>[İleri](application-insights.md)</span><span class="sxs-lookup"><span data-stu-id="10bac-174">[Previous](azure-serverless-platform.md)
[Next](application-insights.md)</span></span>
