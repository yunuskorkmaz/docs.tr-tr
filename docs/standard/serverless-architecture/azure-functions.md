---
title: Azure işlevleri - sunucusuz uygulamalar
description: Azure işlevleri, sunucusuz özellikler birden çok dil arasında (C#, JavaScript, Java) sağlar ve olay odaklı anında sağlamak için Platform kodu ölçeklendirin.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 4febcc01eebf3efce3fc1eb42e19c2ec6c0baa52
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64754225"
---
# <a name="azure-functions"></a><span data-ttu-id="fcd26-103">Azure İşlevleri</span><span class="sxs-lookup"><span data-stu-id="fcd26-103">Azure Functions</span></span>

<span data-ttu-id="fcd26-104">Azure işlevleri, sunucusuz işlem deneyimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="fcd26-104">Azure functions provide a serverless compute experience.</span></span> <span data-ttu-id="fcd26-105">Bir işlev tarafından çağrılan bir *tetikleyici* (örneğin, bir HTTP uç noktası veya bir zamanlayıcı erişim) ve kod veya iş mantığı bloğunu yürütür.</span><span class="sxs-lookup"><span data-stu-id="fcd26-105">A function is invoked by a *trigger* (such as access to an HTTP endpoint or a timer) and executes a block of code or business logic.</span></span> <span data-ttu-id="fcd26-106">Ayrıca destek özel işlevler *bağlamaları* depolama ve kuyruk gibi kaynaklara bağlanın.</span><span class="sxs-lookup"><span data-stu-id="fcd26-106">Functions also support specialized *bindings* that connect to resources like storage and queues.</span></span>

![Azure işlevleri logosu](./media/azure-functions-logo.png)

<span data-ttu-id="fcd26-108">Azure işlevleri framework'ün iki sürümü vardır.</span><span class="sxs-lookup"><span data-stu-id="fcd26-108">There are two versions of the Azure Functions framework.</span></span> <span data-ttu-id="fcd26-109">Eski sürüm tam .NET Framework ve .NET Core uygulamaları platformlar arası yeni çalışma zamanı destekler.</span><span class="sxs-lookup"><span data-stu-id="fcd26-109">The legacy version supports the full .NET Framework and the new runtime supports cross-platform .NET Core applications.</span></span> <span data-ttu-id="fcd26-110">İlave diller yanı sıra C# JavaScript gibi F#, ve Java desteklenir.</span><span class="sxs-lookup"><span data-stu-id="fcd26-110">Additional languages besides C# such as JavaScript, F#, and Java are supported.</span></span> <span data-ttu-id="fcd26-111">Portalda oluşturulan işlevleri, zengin bir betik söz dizimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="fcd26-111">Functions created in the portal provide a rich scripting syntax.</span></span> <span data-ttu-id="fcd26-112">Tek başına projeleri oluşturulan işlevleri tam bir platform desteği ve özellikleri ile dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="fcd26-112">Functions created as standalone projects can be deployed with full platform support and capabilities.</span></span>

<span data-ttu-id="fcd26-113">Daha fazla bilgi için [Azure işlevleri belgelerinde](https://docs.microsoft.com/azure/azure-functions).</span><span class="sxs-lookup"><span data-stu-id="fcd26-113">For more information, see [Azure Functions documentation](https://docs.microsoft.com/azure/azure-functions).</span></span>

## <a name="functions-v1-vs-v2"></a><span data-ttu-id="fcd26-114">İşlevler v1 ve v2 karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="fcd26-114">Functions v1 vs. v2</span></span>

<span data-ttu-id="fcd26-115">Azure işlevleri çalışma zamanı iki sürümü vardır: 1.x ve 2.x'i.</span><span class="sxs-lookup"><span data-stu-id="fcd26-115">There are two versions of the Azure Functions runtime: 1.x and 2.x.</span></span> <span data-ttu-id="fcd26-116">Sürüm 1.x olan genel kullanıma (GA).</span><span class="sxs-lookup"><span data-stu-id="fcd26-116">Version 1.x is generally available (GA).</span></span> <span data-ttu-id="fcd26-117">.NET geliştirme portalı veya Windows makineleri destekler ve .NET Framework'ü kullanır.</span><span class="sxs-lookup"><span data-stu-id="fcd26-117">It supports .NET development from the portal or Windows machines and uses the .NET Framework.</span></span> <span data-ttu-id="fcd26-118">1.x destekler C#, JavaScript ve F#, Python, PHP, TypeScript, Batch, Bash ve PowerShell için Deneysel desteği.</span><span class="sxs-lookup"><span data-stu-id="fcd26-118">1.x supports C#, JavaScript, and F#, with experimental support for Python, PHP, TypeScript, Batch, Bash, and PowerShell.</span></span>

<span data-ttu-id="fcd26-119">[Sürüm 2.x de genel kullanıma sunulan artık](https://azure.microsoft.com/blog/introducing-azure-functions-2-0/).</span><span class="sxs-lookup"><span data-stu-id="fcd26-119">[Version 2.x is also generally available now](https://azure.microsoft.com/blog/introducing-azure-functions-2-0/).</span></span> <span data-ttu-id="fcd26-120">.NET Core yararlanır ve Windows, macOS ve Linux makinelerini platformlar arası geliştirmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="fcd26-120">It leverages .NET Core and supports cross-platform development on Windows, macOS, and Linux machines.</span></span> <span data-ttu-id="fcd26-121">2.x Java için birinci sınıf destek ekler, ancak henüz doğrudan Deneysel dillerden herhangi birini desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="fcd26-121">2.x adds first-class support for Java but doesn't yet directly support any of the experimental languages.</span></span> <span data-ttu-id="fcd26-122">Sürüm 2.x üçüncü taraf uzantıları bağımsız sürüm oluşturma işlemlerini bağlamaları platforma sağlayan yeni bir bağlama genişletilebilirlik modeli kullanır ve daha rahat bir yürütme ortamı.</span><span class="sxs-lookup"><span data-stu-id="fcd26-122">Version 2.x uses a new binding extensibility model that enables third-party extensions to the platform, independent versioning of bindings, and a more streamlined execution environment.</span></span>

> <span data-ttu-id="fcd26-123">**1.x ile içinde bilinen bir sorun var. [bağlama yeniden yönlendirme desteği](https://github.com/Azure/azure-functions-host/issues/992).**</span><span class="sxs-lookup"><span data-stu-id="fcd26-123">**There is a known issue in 1.x with [binding redirect support](https://github.com/Azure/azure-functions-host/issues/992).**</span></span> <span data-ttu-id="fcd26-124">Sorun için .NET geliştirme özeldir.</span><span class="sxs-lookup"><span data-stu-id="fcd26-124">The issue is specific to .NET development.</span></span> <span data-ttu-id="fcd26-125">Kitaplıkların çalışma zamanı'nda bulunan farklı bir sürüm kitaplıkları bağımlı olan projeler etkilenir.</span><span class="sxs-lookup"><span data-stu-id="fcd26-125">Projects with dependencies on libraries that are a different version from the libraries included in the runtime are impacted.</span></span> <span data-ttu-id="fcd26-126">İşlevleri ekibi, sorunu somut ilerleme kaydediyor için kaydoldu.</span><span class="sxs-lookup"><span data-stu-id="fcd26-126">The functions team has committed to making concrete progress on the problem.</span></span> <span data-ttu-id="fcd26-127">Genel kullanıma geçmeden önce takım 2.x bağlama yeniden yönlendirmelerini ele alınacaktır.</span><span class="sxs-lookup"><span data-stu-id="fcd26-127">The team will address binding redirects in 2.x before it goes into general availability.</span></span> <span data-ttu-id="fcd26-128">Önerilen düzeltmeler ve geçici çözümler resmi takım deyimiyle buradan kullanılabilir: [Azure işlevleri'nde derleme çözümlemesine](https://github.com/Azure/azure-functions-host/wiki/Assembly-Resolution-in-Azure-Functions).</span><span class="sxs-lookup"><span data-stu-id="fcd26-128">The official team statement with suggested fixes and workarounds is available here: [Assembly resolution in Azure Functions](https://github.com/Azure/azure-functions-host/wiki/Assembly-Resolution-in-Azure-Functions).</span></span>

<span data-ttu-id="fcd26-129">Daha fazla bilgi için [1.x ve 2.x'i karşılaştırma](https://docs.microsoft.com/azure/azure-functions/functions-versions).</span><span class="sxs-lookup"><span data-stu-id="fcd26-129">For more information, see [Compare 1.x and 2.x](https://docs.microsoft.com/azure/azure-functions/functions-versions).</span></span>

## <a name="programming-language-support"></a><span data-ttu-id="fcd26-130">Programlama dili desteği</span><span class="sxs-lookup"><span data-stu-id="fcd26-130">Programming language support</span></span>

<span data-ttu-id="fcd26-131">Aşağıdaki dillerde desteklenmektedir ya da genel kullanıma (GA) Önizleme, veya Deneysel.</span><span class="sxs-lookup"><span data-stu-id="fcd26-131">The following languages are supported either in general availability (GA), preview, or experimental.</span></span>

|<span data-ttu-id="fcd26-132">Dil</span><span class="sxs-lookup"><span data-stu-id="fcd26-132">Language</span></span>      |<span data-ttu-id="fcd26-133">1.x</span><span class="sxs-lookup"><span data-stu-id="fcd26-133">1.x</span></span>         |<span data-ttu-id="fcd26-134">2.x</span><span class="sxs-lookup"><span data-stu-id="fcd26-134">2.x</span></span>      |
|--------------|------------|---------|
|<span data-ttu-id="fcd26-135">**C#**</span><span class="sxs-lookup"><span data-stu-id="fcd26-135">**C#**</span></span>        |<span data-ttu-id="fcd26-136">GA</span><span class="sxs-lookup"><span data-stu-id="fcd26-136">GA</span></span>          |<span data-ttu-id="fcd26-137">Önizleme</span><span class="sxs-lookup"><span data-stu-id="fcd26-137">Preview</span></span>  |
|<span data-ttu-id="fcd26-138">**JavaScript**</span><span class="sxs-lookup"><span data-stu-id="fcd26-138">**JavaScript**</span></span>|<span data-ttu-id="fcd26-139">GA</span><span class="sxs-lookup"><span data-stu-id="fcd26-139">GA</span></span>          |<span data-ttu-id="fcd26-140">Önizleme</span><span class="sxs-lookup"><span data-stu-id="fcd26-140">Preview</span></span>  |
|<span data-ttu-id="fcd26-141">**F#**</span><span class="sxs-lookup"><span data-stu-id="fcd26-141">**F#**</span></span>        |<span data-ttu-id="fcd26-142">GA</span><span class="sxs-lookup"><span data-stu-id="fcd26-142">GA</span></span>          |         |
|<span data-ttu-id="fcd26-143">**Java**</span><span class="sxs-lookup"><span data-stu-id="fcd26-143">**Java**</span></span>      |            |<span data-ttu-id="fcd26-144">Önizleme</span><span class="sxs-lookup"><span data-stu-id="fcd26-144">Preview</span></span>  |
|<span data-ttu-id="fcd26-145">**Python**</span><span class="sxs-lookup"><span data-stu-id="fcd26-145">**Python**</span></span>    |<span data-ttu-id="fcd26-146">Deneysel</span><span class="sxs-lookup"><span data-stu-id="fcd26-146">Experimental</span></span>|         |
|<span data-ttu-id="fcd26-147">**PHP**</span><span class="sxs-lookup"><span data-stu-id="fcd26-147">**PHP**</span></span>       |<span data-ttu-id="fcd26-148">Deneysel</span><span class="sxs-lookup"><span data-stu-id="fcd26-148">Experimental</span></span>|         |
|<span data-ttu-id="fcd26-149">**TypeScript**</span><span class="sxs-lookup"><span data-stu-id="fcd26-149">**TypeScript**</span></span>|<span data-ttu-id="fcd26-150">Deneysel</span><span class="sxs-lookup"><span data-stu-id="fcd26-150">Experimental</span></span>|         |
|<span data-ttu-id="fcd26-151">**Batch**</span><span class="sxs-lookup"><span data-stu-id="fcd26-151">**Batch**</span></span>     |<span data-ttu-id="fcd26-152">Deneysel</span><span class="sxs-lookup"><span data-stu-id="fcd26-152">Experimental</span></span>|         |
|<span data-ttu-id="fcd26-153">**Bash**</span><span class="sxs-lookup"><span data-stu-id="fcd26-153">**Bash**</span></span>      |<span data-ttu-id="fcd26-154">Deneysel</span><span class="sxs-lookup"><span data-stu-id="fcd26-154">Experimental</span></span>|         |
|<span data-ttu-id="fcd26-155">**PowerShell**</span><span class="sxs-lookup"><span data-stu-id="fcd26-155">**PowerShell**</span></span>|<span data-ttu-id="fcd26-156">Deneysel</span><span class="sxs-lookup"><span data-stu-id="fcd26-156">Experimental</span></span>|         |

<span data-ttu-id="fcd26-157">Daha fazla bilgi için [desteklenen diller](https://docs.microsoft.com/azure/azure-functions/supported-languages).</span><span class="sxs-lookup"><span data-stu-id="fcd26-157">For more information, see [Supported languages](https://docs.microsoft.com/azure/azure-functions/supported-languages).</span></span>

## <a name="app-service-plans"></a><span data-ttu-id="fcd26-158">App service planları</span><span class="sxs-lookup"><span data-stu-id="fcd26-158">App service plans</span></span>

<span data-ttu-id="fcd26-159">İşlevleri tarafından desteklenen bir *app service planı*.</span><span class="sxs-lookup"><span data-stu-id="fcd26-159">Functions are backed by an *app service plan*.</span></span> <span data-ttu-id="fcd26-160">Plan, İşlevler uygulama tarafından kullanılan kaynakları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fcd26-160">The plan defines the resources used by the functions app.</span></span> <span data-ttu-id="fcd26-161">Planları bir bölgeye atama, kullanılacak ve fiyatlandırma katmanı seçme sanal makinelerin sayısını ve boyutunu belirler.</span><span class="sxs-lookup"><span data-stu-id="fcd26-161">You can assign plans to a region, determine the size and number of virtual machines that will be used, and pick a pricing tier.</span></span> <span data-ttu-id="fcd26-162">İşlev uygulamaları için doğru bir sunucusuz yaklaşım, kullanabilir **tüketim** planı.</span><span class="sxs-lookup"><span data-stu-id="fcd26-162">For a true serverless approach, function apps may use the **consumption** plan.</span></span> <span data-ttu-id="fcd26-163">Tüketim planı otomatik olarak yüküne göre arka uç ölçeklenir.</span><span class="sxs-lookup"><span data-stu-id="fcd26-163">The consumption plan will scale the back end automatically based on load.</span></span>

<span data-ttu-id="fcd26-164">Daha fazla bilgi için [App service planları](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).</span><span class="sxs-lookup"><span data-stu-id="fcd26-164">For more information, see [App service plans](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).</span></span>

## <a name="create-your-first-function"></a><span data-ttu-id="fcd26-165">İlk işlevinizi oluşturma</span><span class="sxs-lookup"><span data-stu-id="fcd26-165">Create your first function</span></span>

<span data-ttu-id="fcd26-166">İşlev uygulamaları oluşturabileceğiniz üç yaygın yolları vardır.</span><span class="sxs-lookup"><span data-stu-id="fcd26-166">There are three common ways you can create function apps.</span></span>

* <span data-ttu-id="fcd26-167">Portalda betik işlevleri.</span><span class="sxs-lookup"><span data-stu-id="fcd26-167">Script functions in the portal.</span></span>
* <span data-ttu-id="fcd26-168">Azure komut satırı arabirimi (CLI) kullanarak gerekli kaynakları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fcd26-168">Create the necessary resources using the Azure Command Line Interface (CLI).</span></span>
* <span data-ttu-id="fcd26-169">Sık kullandığınız IDE'yi kullanarak yerel olarak işlevler oluşturun ve bunları Azure'a yayımlayın.</span><span class="sxs-lookup"><span data-stu-id="fcd26-169">Build functions locally using your favorite IDE and publish them to Azure.</span></span>

<span data-ttu-id="fcd26-170">Portalda komut dosyalı bir işlev oluşturma hakkında daha fazla bilgi için bkz. [Azure portalında ilk işlevinizi oluşturma](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function).</span><span class="sxs-lookup"><span data-stu-id="fcd26-170">For more information on creating a scripted function in the portal, see [Create your first function in the Azure portal](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function).</span></span>

<span data-ttu-id="fcd26-171">Azure CLI üzerinden oluşturmak için bkz: [Azure CLI kullanarak ilk işlevinizi oluşturma](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli).</span><span class="sxs-lookup"><span data-stu-id="fcd26-171">To build from the Azure CLI, see [Create your first function using the Azure CLI](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli).</span></span>

<span data-ttu-id="fcd26-172">Visual Studio'dan bir işlev oluşturmak için bkz [Visual Studio kullanarak ilk işlevinizi oluşturma](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="fcd26-172">To create a function from Visual Studio, see [Create your first function using Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio).</span></span>

## <a name="understand-triggers-and-bindings"></a><span data-ttu-id="fcd26-173">Tetikleyiciler ve bağlamalar anlama</span><span class="sxs-lookup"><span data-stu-id="fcd26-173">Understand triggers and bindings</span></span>

<span data-ttu-id="fcd26-174">İşlevler tarafından çağrılır bir *tetikleyici* ve tam olarak bir olabilir.</span><span class="sxs-lookup"><span data-stu-id="fcd26-174">Functions are invoked by a *trigger* and can have exactly one.</span></span> <span data-ttu-id="fcd26-175">İşlev çağırma yanı sıra belirli Tetikleyicileri bağlamaları Ayrıca hizmet.</span><span class="sxs-lookup"><span data-stu-id="fcd26-175">In addition to invoking the function, certain triggers also serve as bindings.</span></span> <span data-ttu-id="fcd26-176">Ayrıca, tetikleyici yanı sıra birden çok bağlamaları tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="fcd26-176">You may also define multiple bindings in addition to the trigger.</span></span> <span data-ttu-id="fcd26-177">*Bağlamaları* kodunuza veri bağlanmak için bildirim temelli bir yöntemini sağlar.</span><span class="sxs-lookup"><span data-stu-id="fcd26-177">*Bindings* provide a declarative way to connect data to your code.</span></span> <span data-ttu-id="fcd26-178">Bunlar, (giriş) geçirilebilir veya verileri (çıktı) alırsınız.</span><span class="sxs-lookup"><span data-stu-id="fcd26-178">They can be passed in (input) or receive data (output).</span></span> <span data-ttu-id="fcd26-179">İşlevleri Tetikleyicileri ve bağlamaları ile çalışmak kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="fcd26-179">Triggers and bindings make functions easy to work with.</span></span> <span data-ttu-id="fcd26-180">Veritabanı veya dosya sistemi bağlantıları el ile oluşturma ek yükü bağlamaları kaldırın.</span><span class="sxs-lookup"><span data-stu-id="fcd26-180">Bindings remove the overhead of manually creating database or file system connections.</span></span> <span data-ttu-id="fcd26-181">Özel bir barındırılan tüm bağlamaları için gereken bilgileri *functions.json* için komut dosyası veya kod öznitelikleri ile bildirilen.</span><span class="sxs-lookup"><span data-stu-id="fcd26-181">All of the information needed for the bindings is contained in a special *functions.json* file for scripts or declared with attributes in code.</span></span>

<span data-ttu-id="fcd26-182">Bazı sık kullanılan Tetikleyicileri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="fcd26-182">Some common triggers include:</span></span>

* <span data-ttu-id="fcd26-183">BLOB Depolama: dosya veya klasör karşıya veya depolama alanında değiştirildi, işlevinizi çağırır.</span><span class="sxs-lookup"><span data-stu-id="fcd26-183">Blob Storage: invoke your function when a file or folder is uploaded or changed in storage.</span></span>
* <span data-ttu-id="fcd26-184">HTTP:, işlev bir REST API gibi çağırın.</span><span class="sxs-lookup"><span data-stu-id="fcd26-184">HTTP: invoke your function like a REST API.</span></span>
* <span data-ttu-id="fcd26-185">Kuyruk:, kuyrukta öğeleri mevcut olduğunda, işlev çağırın.</span><span class="sxs-lookup"><span data-stu-id="fcd26-185">Queue: invoke your function when items exist in a queue.</span></span>
* <span data-ttu-id="fcd26-186">Zamanlayıcı: normal temposu üzerinde işlevinizi çağırır.</span><span class="sxs-lookup"><span data-stu-id="fcd26-186">Timer: invoke your function on a regular cadence.</span></span>

<span data-ttu-id="fcd26-187">Bağlamaları örnekleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="fcd26-187">Examples of bindings include:</span></span>

* <span data-ttu-id="fcd26-188">Cosmos DB: kolayca yüklemek veya dosyaları kaydetmek için veritabanına bağlanın.</span><span class="sxs-lookup"><span data-stu-id="fcd26-188">CosmosDB: easily connect to the database to load or save files.</span></span>
* <span data-ttu-id="fcd26-189">Tablo depolaması: işlev uygulamanızı depolamadan anahtar/değer çalışın.</span><span class="sxs-lookup"><span data-stu-id="fcd26-189">Table Storage: work with key/value storage from your function app.</span></span>
* <span data-ttu-id="fcd26-190">Kuyruk Depolama: kolayca öğeleri kuyruktan almak veya yeni öğeleri sıraya koyun.</span><span class="sxs-lookup"><span data-stu-id="fcd26-190">Queue Storage: easily retrieve items from a queue, or place new items on the queue.</span></span>

<span data-ttu-id="fcd26-191">Aşağıdaki örnek *functions.json* dosyası, bir tetikleyici ve bağlama tanımlar:</span><span class="sxs-lookup"><span data-stu-id="fcd26-191">The following example *functions.json* file defines a trigger and a binding:</span></span>

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

<span data-ttu-id="fcd26-192">Bu örnekte, bir blob depolama alanında değişiklik işlevi tetiklenir `images` kapsayıcı.</span><span class="sxs-lookup"><span data-stu-id="fcd26-192">In this example, the function is triggered by a change to blob storage in the `images` container.</span></span> <span data-ttu-id="fcd26-193">Tetikleyici olarak bir bağlama ayrıca çalışır. Bu nedenle, dosya bilgilerini geçirilir.</span><span class="sxs-lookup"><span data-stu-id="fcd26-193">The information for the file is passed in, so the trigger also acts as a binding.</span></span> <span data-ttu-id="fcd26-194">Bilgi adlı bir sıra üstüne koymak için başka bir bağlamanın mevcut `images`.</span><span class="sxs-lookup"><span data-stu-id="fcd26-194">Another binding exists to put information onto a queue named `images`.</span></span>

<span data-ttu-id="fcd26-195">C# betik işlevi için şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="fcd26-195">Here is the C# script for the function:</span></span>

```csharp
public static string Run(Stream myBlob, string name, TraceWriter log)
{
    log.Info($"C# Blob trigger function Processed blob\n Name:{name} \n Size: {myBlob.Length} Bytes");
    return name;
}
```

<span data-ttu-id="fcd26-196">Dosyanın adı almayan basit bir işlevi değiştirildi veya BLOB depolamaya yüklediğiniz ve daha sonra işlemek için bir kuyruk yerleştirir örnektir.</span><span class="sxs-lookup"><span data-stu-id="fcd26-196">The example is a simple function that takes the name of the file that was modified or uploaded to blob storage, and places it on a queue for later processing.</span></span>

<span data-ttu-id="fcd26-197">Tetikleyiciler ve bağlamalar tam listesi için bkz [Azure işlevleri Tetikleyicileri ve bağlamaları kavramları](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings).</span><span class="sxs-lookup"><span data-stu-id="fcd26-197">For a full list of triggers and bindings, see [Azure Functions triggers and bindings concepts](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings).</span></span>

## <a name="proxies"></a><span data-ttu-id="fcd26-198">Proxy'ler</span><span class="sxs-lookup"><span data-stu-id="fcd26-198">Proxies</span></span>

<span data-ttu-id="fcd26-199">Proxy'leri, uygulamanızın yeniden yönlendirme işlevselliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="fcd26-199">Proxies provide redirect functionality for your application.</span></span> <span data-ttu-id="fcd26-200">Proxy'leri, bir uç noktanın kullanıma ve başka bir kaynak için uç noktanın eşleyin.</span><span class="sxs-lookup"><span data-stu-id="fcd26-200">Proxies expose an endpoint and map that endpoint to another resource.</span></span> <span data-ttu-id="fcd26-201">Proxy ile şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="fcd26-201">With proxies, you can:</span></span>

* <span data-ttu-id="fcd26-202">Başka bir uç nokta gelen bir isteği yeniden yönlendirebilir.</span><span class="sxs-lookup"><span data-stu-id="fcd26-202">Reroute an incoming request to another endpoint.</span></span>
* <span data-ttu-id="fcd26-203">Gelen istek boyunca geçirilmeden önce değiştirin.</span><span class="sxs-lookup"><span data-stu-id="fcd26-203">Modify the incoming request before it's passed along.</span></span>
* <span data-ttu-id="fcd26-204">Değiştirmek veya bir yanıt verin.</span><span class="sxs-lookup"><span data-stu-id="fcd26-204">Modify or provide a response.</span></span>

<span data-ttu-id="fcd26-205">Proxy'leri gibi senaryolar için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="fcd26-205">Proxies are used for scenarios such as:</span></span>

* <span data-ttu-id="fcd26-206">Basitleştirme, kısaltmayı veya URL değiştirme.</span><span class="sxs-lookup"><span data-stu-id="fcd26-206">Simplifying, shortening, or changing the URL.</span></span>
* <span data-ttu-id="fcd26-207">Birden fazla arka uç Hizmetleri için tutarlı bir API öneki sağlama.</span><span class="sxs-lookup"><span data-stu-id="fcd26-207">Providing a consistent API prefix to multiple back-end services.</span></span>
* <span data-ttu-id="fcd26-208">Geliştirilmekte olan bir uç nokta için bir yanıt sahte işlem.</span><span class="sxs-lookup"><span data-stu-id="fcd26-208">Mocking a response to an endpoint being developed.</span></span>
* <span data-ttu-id="fcd26-209">İyi bilinen bir uç nokta için statik bir yanıt sağlama.</span><span class="sxs-lookup"><span data-stu-id="fcd26-209">Providing a static response to a well-known endpoint.</span></span>
* <span data-ttu-id="fcd26-210">Arka uç taşınmış veya geçiş yaparken bir API uç noktası tutarlı kalmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="fcd26-210">Keeping an API endpoint consistent while the back end is moved or migrated.</span></span>

<span data-ttu-id="fcd26-211">Proxy'leri JSON tanımları depolanır.</span><span class="sxs-lookup"><span data-stu-id="fcd26-211">Proxies are stored as JSON definitions.</span></span> <span data-ttu-id="fcd26-212">Aşağıda bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="fcd26-212">Here is an example:</span></span>

```json
{
  "$schema": "http://json.schemastore.org/proxies",
  "proxies": {
    "Domain Redirect": {
      "matchCondition": {
        "route": "/{shortUrl}"
      },
      "backendUri": "http://%WEBSITE_HOSTNAME%/api/UrlRedirect/{shortUrl}"
    },
    "Root": {
      "matchCondition": {
        "route": "/"
      },
      "responseOverrides": {
        "response.statusCode": "301",
        "response.statusReason": "Moved Permanently",
        "response.headers.location": "https://docs.microsoft.com/"
      }
    }
  }
}
```

<span data-ttu-id="fcd26-213">`Domain Redirect` Proxy kısaltılmış bir yol alır ve uzun işlevi kaynağa eşler.</span><span class="sxs-lookup"><span data-stu-id="fcd26-213">The `Domain Redirect` proxy takes a shortened route and maps it to the longer function resource.</span></span> <span data-ttu-id="fcd26-214">Dönüştürme şu şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="fcd26-214">The transformation looks like:</span></span>

`https://--shorturl--/123` -> `https://--longurl--.azurewebsites.net/api/UrlRedirect/123`

<span data-ttu-id="fcd26-215">`Root` Proxy kök URL'ye gönderilen her şeyi alır (`https://--shorturl--/`) ve belge sitesine yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="fcd26-215">The `Root` proxy takes anything sent to the root URL (`https://--shorturl--/`) and redirects it to the documentation site.</span></span>

<span data-ttu-id="fcd26-216">Proxy'leri kullanma örneği, videoda gösterilen [Azure: Sunucusuz Azure işlevleri ile bulut uygulamanızı taşıyın](https://channel9.msdn.com/events/Connect/2017/E102).</span><span class="sxs-lookup"><span data-stu-id="fcd26-216">An example of using proxies is shown in the video [Azure: Bring your app to the cloud with serverless Azure Functions](https://channel9.msdn.com/events/Connect/2017/E102).</span></span> <span data-ttu-id="fcd26-217">Gerçek zamanlı olarak yerel SQL Server üzerinde çalışan bir ASP.NET Core uygulaması Azure buluta geçirilir.</span><span class="sxs-lookup"><span data-stu-id="fcd26-217">In real time, an ASP.NET Core application running on local SQL Server is migrated to the Azure Cloud.</span></span> <span data-ttu-id="fcd26-218">Proxy işlevleri kullanmak için geleneksel bir Web API projesi yeniden düzenleme yardımcı olmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fcd26-218">Proxies are used to help refactor a traditional Web API project to use functions.</span></span>

<span data-ttu-id="fcd26-219">Proxy hakkında daha fazla bilgi için bkz: [iş ile Azure işlevleri proxy'leri](https://docs.microsoft.com/azure/azure-functions/functions-proxies).</span><span class="sxs-lookup"><span data-stu-id="fcd26-219">For more information about Proxies, see [Work with Azure Functions Proxies](https://docs.microsoft.com/azure/azure-functions/functions-proxies).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="fcd26-220">[Önceki](azure-serverless-platform.md)
>[İleri](application-insights.md)</span><span class="sxs-lookup"><span data-stu-id="fcd26-220">[Previous](azure-serverless-platform.md)
[Next](application-insights.md)</span></span>
