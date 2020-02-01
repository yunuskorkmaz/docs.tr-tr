---
title: Azure Işlevleri-sunucusuz uygulamalar
description: Azure işlevleri, olay odaklı anında ölçeklendirme kodu sağlamak içinC#birden çok dilde (, JavaScript, Java) ve platformlarda sunucusuz yetenekler sağlar.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 8764e6a33f3fdd53e60fa767d0fb584a9c07de7e
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920976"
---
# <a name="azure-functions"></a><span data-ttu-id="3571e-103">Azure İşlevleri</span><span class="sxs-lookup"><span data-stu-id="3571e-103">Azure Functions</span></span>

<span data-ttu-id="3571e-104">Azure işlevleri, sunucusuz bir işlem deneyimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="3571e-104">Azure functions provide a serverless compute experience.</span></span> <span data-ttu-id="3571e-105">Bir işlev bir *tetikleyici* tarafından çağrılır (bir HTTP uç noktasına veya bir zamanlayıcıya erişim gibi) ve bir kod bloğu veya iş mantığı yürütür.</span><span class="sxs-lookup"><span data-stu-id="3571e-105">A function is invoked by a *trigger* (such as access to an HTTP endpoint or a timer) and executes a block of code or business logic.</span></span> <span data-ttu-id="3571e-106">İşlevler ayrıca depolama ve kuyruklar gibi kaynaklara bağlanan özelleştirilmiş *bağlamaları* destekler.</span><span class="sxs-lookup"><span data-stu-id="3571e-106">Functions also support specialized *bindings* that connect to resources like storage and queues.</span></span>

![Azure işlevleri logosu](./media/azure-functions-logo.png)

<span data-ttu-id="3571e-108">Azure Işlevleri çerçevesinin iki sürümü vardır.</span><span class="sxs-lookup"><span data-stu-id="3571e-108">There are two versions of the Azure Functions framework.</span></span> <span data-ttu-id="3571e-109">Eski sürüm, tam .NET Framework destekler ve yeni çalışma zamanı platformlar arası .NET Core uygulamalarını destekler.</span><span class="sxs-lookup"><span data-stu-id="3571e-109">The legacy version supports the full .NET Framework and the new runtime supports cross-platform .NET Core applications.</span></span> <span data-ttu-id="3571e-110">JavaScript, F#ve C# Java gibi ek diller de desteklenir.</span><span class="sxs-lookup"><span data-stu-id="3571e-110">Additional languages besides C# such as JavaScript, F#, and Java are supported.</span></span> <span data-ttu-id="3571e-111">Portalda oluşturulan işlevler, zengin bir betik sözdizimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="3571e-111">Functions created in the portal provide a rich scripting syntax.</span></span> <span data-ttu-id="3571e-112">Tek başına projeler olarak oluşturulan işlevler, tam platform desteği ve özellikleri ile dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="3571e-112">Functions created as standalone projects can be deployed with full platform support and capabilities.</span></span>

<span data-ttu-id="3571e-113">Daha fazla bilgi için bkz. [Azure işlevleri belgeleri](https://docs.microsoft.com/azure/azure-functions).</span><span class="sxs-lookup"><span data-stu-id="3571e-113">For more information, see [Azure Functions documentation](https://docs.microsoft.com/azure/azure-functions).</span></span>

## <a name="functions-v1-vs-v2"></a><span data-ttu-id="3571e-114">İşlevler v1 ve v2</span><span class="sxs-lookup"><span data-stu-id="3571e-114">Functions v1 vs. v2</span></span>

<span data-ttu-id="3571e-115">Azure Işlevleri çalışma zamanının iki sürümü vardır: 1. x ve 2. x.</span><span class="sxs-lookup"><span data-stu-id="3571e-115">There are two versions of the Azure Functions runtime: 1.x and 2.x.</span></span> <span data-ttu-id="3571e-116">Sürüm 1. x genel kullanıma sunuldu (GA).</span><span class="sxs-lookup"><span data-stu-id="3571e-116">Version 1.x is generally available (GA).</span></span> <span data-ttu-id="3571e-117">Portal veya Windows makinelerinden .NET geliştirmesini destekler ve .NET Framework kullanır.</span><span class="sxs-lookup"><span data-stu-id="3571e-117">It supports .NET development from the portal or Windows machines and uses the .NET Framework.</span></span> <span data-ttu-id="3571e-118">1. x, C#Python, php, F#TypeScript, Batch, bash ve PowerShell için deneysel destekle birlikte desteklenir, JavaScript ve.</span><span class="sxs-lookup"><span data-stu-id="3571e-118">1.x supports C#, JavaScript, and F#, with experimental support for Python, PHP, TypeScript, Batch, Bash, and PowerShell.</span></span>

<span data-ttu-id="3571e-119">[Sürüm 2. x artık genel olarak kullanılabilir](https://azure.microsoft.com/blog/introducing-azure-functions-2-0/).</span><span class="sxs-lookup"><span data-stu-id="3571e-119">[Version 2.x is also generally available now](https://azure.microsoft.com/blog/introducing-azure-functions-2-0/).</span></span> <span data-ttu-id="3571e-120">.NET Core 'u kullanır ve Windows, macOS ve Linux makinelerinde platformlar arası geliştirmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="3571e-120">It leverages .NET Core and supports cross-platform development on Windows, macOS, and Linux machines.</span></span> <span data-ttu-id="3571e-121">2. x, Java için birinci sınıf destek ekler ancak deneysel dillerin hiçbirini henüz doğrudan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="3571e-121">2.x adds first-class support for Java but doesn't yet directly support any of the experimental languages.</span></span> <span data-ttu-id="3571e-122">Sürüm 2. x, platforma üçüncü taraf uzantılar, bağlamaların bağımsız sürümü ve daha kolay bir yürütme ortamı sağlayan yeni bir bağlama genişletilebilirlik modeli kullanır.</span><span class="sxs-lookup"><span data-stu-id="3571e-122">Version 2.x uses a new binding extensibility model that enables third-party extensions to the platform, independent versioning of bindings, and a more streamlined execution environment.</span></span>

> <span data-ttu-id="3571e-123">**[Bağlama yeniden yönlendirme desteğiyle](https://github.com/Azure/azure-functions-host/issues/992)1. x içinde bilinen bir sorun var.**</span><span class="sxs-lookup"><span data-stu-id="3571e-123">**There is a known issue in 1.x with [binding redirect support](https://github.com/Azure/azure-functions-host/issues/992).**</span></span> <span data-ttu-id="3571e-124">Bu sorun .NET geliştirmeye özgüdür.</span><span class="sxs-lookup"><span data-stu-id="3571e-124">The issue is specific to .NET development.</span></span> <span data-ttu-id="3571e-125">Çalışma zamanına dahil olan kitaplıkların farklı bir sürümü olan kitaplıklarda bağımlılıklar içeren projeler etkilenir.</span><span class="sxs-lookup"><span data-stu-id="3571e-125">Projects with dependencies on libraries that are a different version from the libraries included in the runtime are impacted.</span></span> <span data-ttu-id="3571e-126">Takım işlevleri, sorun üzerinde somut ilerleme durumu yapmayı taahhüt etti.</span><span class="sxs-lookup"><span data-stu-id="3571e-126">The functions team has committed to making concrete progress on the problem.</span></span> <span data-ttu-id="3571e-127">Takım, genel kullanıma geçmeden önce 2. x içindeki bağlama yeniden yönlendirmelerini ele alacak.</span><span class="sxs-lookup"><span data-stu-id="3571e-127">The team will address binding redirects in 2.x before it goes into general availability.</span></span> <span data-ttu-id="3571e-128">Önerilen düzeltmeler ve geçici çözümler içeren resmi takım bildirimine buradan ulaşabilirsiniz: [Azure işlevleri 'Nde derleme çözümlemesi](https://github.com/Azure/azure-functions-host/wiki/Assembly-Resolution-in-Azure-Functions).</span><span class="sxs-lookup"><span data-stu-id="3571e-128">The official team statement with suggested fixes and workarounds is available here: [Assembly resolution in Azure Functions](https://github.com/Azure/azure-functions-host/wiki/Assembly-Resolution-in-Azure-Functions).</span></span>

<span data-ttu-id="3571e-129">Daha fazla bilgi için bkz. [Compare 1. x ve 2. x](https://docs.microsoft.com/azure/azure-functions/functions-versions).</span><span class="sxs-lookup"><span data-stu-id="3571e-129">For more information, see [Compare 1.x and 2.x](https://docs.microsoft.com/azure/azure-functions/functions-versions).</span></span>

## <a name="programming-language-support"></a><span data-ttu-id="3571e-130">Programlama dili desteği</span><span class="sxs-lookup"><span data-stu-id="3571e-130">Programming language support</span></span>

<span data-ttu-id="3571e-131">Aşağıdaki diller genel kullanılabilirlik (GA), önizleme veya deneysel olarak desteklenir.</span><span class="sxs-lookup"><span data-stu-id="3571e-131">The following languages are supported either in general availability (GA), preview, or experimental.</span></span>

|<span data-ttu-id="3571e-132">Dil</span><span class="sxs-lookup"><span data-stu-id="3571e-132">Language</span></span>      |<span data-ttu-id="3571e-133">'in</span><span class="sxs-lookup"><span data-stu-id="3571e-133">1.x</span></span>         |<span data-ttu-id="3571e-134">2.x</span><span class="sxs-lookup"><span data-stu-id="3571e-134">2.x</span></span>      |
|--------------|------------|---------|
|<span data-ttu-id="3571e-135">**C#**</span><span class="sxs-lookup"><span data-stu-id="3571e-135">**C#**</span></span>        |<span data-ttu-id="3571e-136">GA</span><span class="sxs-lookup"><span data-stu-id="3571e-136">GA</span></span>          |<span data-ttu-id="3571e-137">Önizleme</span><span class="sxs-lookup"><span data-stu-id="3571e-137">Preview</span></span>  |
|<span data-ttu-id="3571e-138">**JavaScript**</span><span class="sxs-lookup"><span data-stu-id="3571e-138">**JavaScript**</span></span>|<span data-ttu-id="3571e-139">GA</span><span class="sxs-lookup"><span data-stu-id="3571e-139">GA</span></span>          |<span data-ttu-id="3571e-140">Önizleme</span><span class="sxs-lookup"><span data-stu-id="3571e-140">Preview</span></span>  |
|<span data-ttu-id="3571e-141">**F#**</span><span class="sxs-lookup"><span data-stu-id="3571e-141">**F#**</span></span>        |<span data-ttu-id="3571e-142">GA</span><span class="sxs-lookup"><span data-stu-id="3571e-142">GA</span></span>          |         |
|<span data-ttu-id="3571e-143">**Java**</span><span class="sxs-lookup"><span data-stu-id="3571e-143">**Java**</span></span>      |            |<span data-ttu-id="3571e-144">Önizleme</span><span class="sxs-lookup"><span data-stu-id="3571e-144">Preview</span></span>  |
|<span data-ttu-id="3571e-145">**Python**</span><span class="sxs-lookup"><span data-stu-id="3571e-145">**Python**</span></span>    |<span data-ttu-id="3571e-146">Deneysel</span><span class="sxs-lookup"><span data-stu-id="3571e-146">Experimental</span></span>|         |
|<span data-ttu-id="3571e-147">**PHP**</span><span class="sxs-lookup"><span data-stu-id="3571e-147">**PHP**</span></span>       |<span data-ttu-id="3571e-148">Deneysel</span><span class="sxs-lookup"><span data-stu-id="3571e-148">Experimental</span></span>|         |
|<span data-ttu-id="3571e-149">**TypeScript**</span><span class="sxs-lookup"><span data-stu-id="3571e-149">**TypeScript**</span></span>|<span data-ttu-id="3571e-150">Deneysel</span><span class="sxs-lookup"><span data-stu-id="3571e-150">Experimental</span></span>|         |
|<span data-ttu-id="3571e-151">**İşlemini**</span><span class="sxs-lookup"><span data-stu-id="3571e-151">**Batch**</span></span>     |<span data-ttu-id="3571e-152">Deneysel</span><span class="sxs-lookup"><span data-stu-id="3571e-152">Experimental</span></span>|         |
|<span data-ttu-id="3571e-153">**Bash**</span><span class="sxs-lookup"><span data-stu-id="3571e-153">**Bash**</span></span>      |<span data-ttu-id="3571e-154">Deneysel</span><span class="sxs-lookup"><span data-stu-id="3571e-154">Experimental</span></span>|         |
|<span data-ttu-id="3571e-155">**PowerShell**</span><span class="sxs-lookup"><span data-stu-id="3571e-155">**PowerShell**</span></span>|<span data-ttu-id="3571e-156">Deneysel</span><span class="sxs-lookup"><span data-stu-id="3571e-156">Experimental</span></span>|         |

<span data-ttu-id="3571e-157">Daha fazla bilgi için bkz. [desteklenen diller](https://docs.microsoft.com/azure/azure-functions/supported-languages).</span><span class="sxs-lookup"><span data-stu-id="3571e-157">For more information, see [Supported languages](https://docs.microsoft.com/azure/azure-functions/supported-languages).</span></span>

## <a name="app-service-plans"></a><span data-ttu-id="3571e-158">App Service planları</span><span class="sxs-lookup"><span data-stu-id="3571e-158">App service plans</span></span>

<span data-ttu-id="3571e-159">İşlevler bir *App Service planı*tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="3571e-159">Functions are backed by an *app service plan*.</span></span> <span data-ttu-id="3571e-160">Plan, işlevler uygulaması tarafından kullanılan kaynakları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3571e-160">The plan defines the resources used by the functions app.</span></span> <span data-ttu-id="3571e-161">Bir bölgeye planlar atayabilir, kullanılacak sanal makinelerin boyutunu ve sayısını belirleyebilir ve bir fiyatlandırma katmanı seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3571e-161">You can assign plans to a region, determine the size and number of virtual machines that will be used, and pick a pricing tier.</span></span> <span data-ttu-id="3571e-162">Doğru sunucusuz bir yaklaşım için işlev uygulamaları **Tüketim** planını kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="3571e-162">For a true serverless approach, function apps may use the **consumption** plan.</span></span> <span data-ttu-id="3571e-163">Tüketim planı, yük temelinde arka ucu otomatik olarak ölçeklendirecektir.</span><span class="sxs-lookup"><span data-stu-id="3571e-163">The consumption plan will scale the back end automatically based on load.</span></span>

<span data-ttu-id="3571e-164">Daha fazla bilgi için bkz. [App Service planları](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).</span><span class="sxs-lookup"><span data-stu-id="3571e-164">For more information, see [App service plans](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).</span></span>

## <a name="create-your-first-function"></a><span data-ttu-id="3571e-165">İlk işlevinizi oluşturma</span><span class="sxs-lookup"><span data-stu-id="3571e-165">Create your first function</span></span>

<span data-ttu-id="3571e-166">İşlev uygulamaları oluşturabileceğiniz üç yaygın yol vardır.</span><span class="sxs-lookup"><span data-stu-id="3571e-166">There are three common ways you can create function apps.</span></span>

- <span data-ttu-id="3571e-167">Portalda betik işlevleri.</span><span class="sxs-lookup"><span data-stu-id="3571e-167">Script functions in the portal.</span></span>
- <span data-ttu-id="3571e-168">Azure CLı kullanarak gereken kaynakları oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3571e-168">Create the necessary resources using the Azure CLI.</span></span>
- <span data-ttu-id="3571e-169">En sevdiğiniz IDE 'yi kullanarak işlevleri yerel olarak derleyin ve Azure 'da yayımlayın.</span><span class="sxs-lookup"><span data-stu-id="3571e-169">Build functions locally using your favorite IDE and publish them to Azure.</span></span>

<span data-ttu-id="3571e-170">Portalda betikleştirilmiş bir işlev oluşturma hakkında daha fazla bilgi için, [Azure Portal ilk işlevinizi oluşturma](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="3571e-170">For more information on creating a scripted function in the portal, see [Create your first function in the Azure portal](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function).</span></span>

<span data-ttu-id="3571e-171">Azure CLı 'dan derlemek için bkz. [Azure CLI kullanarak ilk işlevinizi oluşturma](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli).</span><span class="sxs-lookup"><span data-stu-id="3571e-171">To build from the Azure CLI, see [Create your first function using the Azure CLI](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli).</span></span>

<span data-ttu-id="3571e-172">Visual Studio 'dan bir işlev oluşturmak için bkz. [Visual Studio kullanarak ilk işlevinizi oluşturma](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="3571e-172">To create a function from Visual Studio, see [Create your first function using Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio).</span></span>

## <a name="understand-triggers-and-bindings"></a><span data-ttu-id="3571e-173">Tetikleyicileri ve bağlamaları anlama</span><span class="sxs-lookup"><span data-stu-id="3571e-173">Understand triggers and bindings</span></span>

<span data-ttu-id="3571e-174">İşlevler bir *tetikleyici* tarafından çağrılır ve tam olarak bir tane olabilir.</span><span class="sxs-lookup"><span data-stu-id="3571e-174">Functions are invoked by a *trigger* and can have exactly one.</span></span> <span data-ttu-id="3571e-175">İşlevi çağırmaya ek olarak, bazı Tetikleyiciler de bağlamalar olarak görev yapar.</span><span class="sxs-lookup"><span data-stu-id="3571e-175">In addition to invoking the function, certain triggers also serve as bindings.</span></span> <span data-ttu-id="3571e-176">Ayrıca, tetikleyicisine ek olarak birden çok bağlama de tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3571e-176">You may also define multiple bindings in addition to the trigger.</span></span> <span data-ttu-id="3571e-177">*Bağlamalar* , verileri kodunuza bağlamanın bildirim temelli bir yolunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="3571e-177">*Bindings* provide a declarative way to connect data to your code.</span></span> <span data-ttu-id="3571e-178">Bunlar (giriş) veya veri alabilir (çıktı).</span><span class="sxs-lookup"><span data-stu-id="3571e-178">They can be passed in (input) or receive data (output).</span></span> <span data-ttu-id="3571e-179">Tetikleyiciler ve bağlamalar işlevleri ile çalışmayı kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="3571e-179">Triggers and bindings make functions easy to work with.</span></span> <span data-ttu-id="3571e-180">Bağlamalar, veritabanı veya dosya sistemi bağlantılarını el ile oluşturma ek yükünü ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="3571e-180">Bindings remove the overhead of manually creating database or file system connections.</span></span> <span data-ttu-id="3571e-181">Bağlamalar için gereken tüm bilgiler, betikler için özel bir *Functions. JSON* dosyasında bulunur veya koddaki özniteliklerle birlikte bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3571e-181">All of the information needed for the bindings is contained in a special *functions.json* file for scripts or declared with attributes in code.</span></span>

<span data-ttu-id="3571e-182">Bazı ortak Tetikleyiciler şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="3571e-182">Some common triggers include:</span></span>

- <span data-ttu-id="3571e-183">BLOB depolama: bir dosya veya klasör bir depolama alanında karşıya yüklenirken veya değiştirildiğinde işlevinizi çağırın.</span><span class="sxs-lookup"><span data-stu-id="3571e-183">Blob Storage: invoke your function when a file or folder is uploaded or changed in storage.</span></span>
- <span data-ttu-id="3571e-184">HTTP: işlevinizi REST API gibi çağırın.</span><span class="sxs-lookup"><span data-stu-id="3571e-184">HTTP: invoke your function like a REST API.</span></span>
- <span data-ttu-id="3571e-185">Queue: bir kuyrukta öğeler mevcutsa işlevinizi çağırın.</span><span class="sxs-lookup"><span data-stu-id="3571e-185">Queue: invoke your function when items exist in a queue.</span></span>
- <span data-ttu-id="3571e-186">Süreölçer: işlevinizi düzenli bir temposunda çağırma.</span><span class="sxs-lookup"><span data-stu-id="3571e-186">Timer: invoke your function on a regular cadence.</span></span>

<span data-ttu-id="3571e-187">Bağlama örnekleri şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="3571e-187">Examples of bindings include:</span></span>

- <span data-ttu-id="3571e-188">CosmosDB: dosyaları yüklemek veya kaydetmek için kolayca veritabanına bağlanın.</span><span class="sxs-lookup"><span data-stu-id="3571e-188">CosmosDB: easily connect to the database to load or save files.</span></span>
- <span data-ttu-id="3571e-189">Tablo Depolama: işlev uygulamanızdan anahtar/değer depolama ile çalışma.</span><span class="sxs-lookup"><span data-stu-id="3571e-189">Table Storage: work with key/value storage from your function app.</span></span>
- <span data-ttu-id="3571e-190">Kuyruk depolama: bir kuyruktan kolayca öğe alın veya yeni öğeleri kuyruğa yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="3571e-190">Queue Storage: easily retrieve items from a queue, or place new items on the queue.</span></span>

<span data-ttu-id="3571e-191">Aşağıdaki örnek *Functions. JSON* dosyası bir tetikleyiciyi ve bağlamayı tanımlar:</span><span class="sxs-lookup"><span data-stu-id="3571e-191">The following example *functions.json* file defines a trigger and a binding:</span></span>

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

<span data-ttu-id="3571e-192">Bu örnekte, işlevi `images` kapsayıcısındaki blob depolamada yapılan bir değişiklik tarafından tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="3571e-192">In this example, the function is triggered by a change to blob storage in the `images` container.</span></span> <span data-ttu-id="3571e-193">Dosya ile ilgili bilgiler geçirilir, bu nedenle tetikleyici de bir bağlama işlevi görür.</span><span class="sxs-lookup"><span data-stu-id="3571e-193">The information for the file is passed in, so the trigger also acts as a binding.</span></span> <span data-ttu-id="3571e-194">`images`adlı bir kuyruğa bilgi koymak için başka bir bağlama var.</span><span class="sxs-lookup"><span data-stu-id="3571e-194">Another binding exists to put information onto a queue named `images`.</span></span>

<span data-ttu-id="3571e-195">İşlevin C# betiği şöyledir:</span><span class="sxs-lookup"><span data-stu-id="3571e-195">Here is the C# script for the function:</span></span>

```csharp
public static string Run(Stream myBlob, string name, TraceWriter log)
{
    log.Info($"C# Blob trigger function Processed blob\n Name:{name} \n Size: {myBlob.Length} Bytes");
    return name;
}
```

<span data-ttu-id="3571e-196">Örnek, değiştirilen veya blob depolamaya yüklenen dosyanın adını alan ve daha sonra işlenmek üzere bir kuyruğa yerleştirtiren basit bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="3571e-196">The example is a simple function that takes the name of the file that was modified or uploaded to blob storage, and places it on a queue for later processing.</span></span>

<span data-ttu-id="3571e-197">Tetikleyiciler ve bağlamaların tam listesi için bkz. [Azure işlevleri Tetikleyicileri ve bağlamaları kavramları](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings).</span><span class="sxs-lookup"><span data-stu-id="3571e-197">For a full list of triggers and bindings, see [Azure Functions triggers and bindings concepts](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings).</span></span>

## <a name="proxies"></a><span data-ttu-id="3571e-198">Proxy'ler</span><span class="sxs-lookup"><span data-stu-id="3571e-198">Proxies</span></span>

<span data-ttu-id="3571e-199">Proxy 'ler, uygulamanız için yeniden yönlendirme işlevi sağlar.</span><span class="sxs-lookup"><span data-stu-id="3571e-199">Proxies provide redirect functionality for your application.</span></span> <span data-ttu-id="3571e-200">Proxy 'ler bir uç noktayı kullanıma sunar ve bu uç noktayı başka bir kaynakla eşler.</span><span class="sxs-lookup"><span data-stu-id="3571e-200">Proxies expose an endpoint and map that endpoint to another resource.</span></span> <span data-ttu-id="3571e-201">Proxy 'ler ile şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3571e-201">With proxies, you can:</span></span>

- <span data-ttu-id="3571e-202">Gelen isteği başka bir uç noktaya yeniden yönlendir.</span><span class="sxs-lookup"><span data-stu-id="3571e-202">Reroute an incoming request to another endpoint.</span></span>
- <span data-ttu-id="3571e-203">Gelen isteği geçirilmeden önce değiştirin.</span><span class="sxs-lookup"><span data-stu-id="3571e-203">Modify the incoming request before it's passed along.</span></span>
- <span data-ttu-id="3571e-204">Bir yanıtı değiştirin veya bir yanıt verin.</span><span class="sxs-lookup"><span data-stu-id="3571e-204">Modify or provide a response.</span></span>

<span data-ttu-id="3571e-205">Proxy 'ler gibi senaryolar için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="3571e-205">Proxies are used for scenarios such as:</span></span>

- <span data-ttu-id="3571e-206">URL 'YI basitleştirecek, kısaltaştırın veya değiştirmeyi kolaylaştırın.</span><span class="sxs-lookup"><span data-stu-id="3571e-206">Simplifying, shortening, or changing the URL.</span></span>
- <span data-ttu-id="3571e-207">Birden fazla arka uç hizmetine tutarlı bir API öneki sağlama.</span><span class="sxs-lookup"><span data-stu-id="3571e-207">Providing a consistent API prefix to multiple back-end services.</span></span>
- <span data-ttu-id="3571e-208">Geliştirmekte olan bir uç noktaya yanıt verme.</span><span class="sxs-lookup"><span data-stu-id="3571e-208">Mocking a response to an endpoint being developed.</span></span>
- <span data-ttu-id="3571e-209">İyi bilinen bir uç noktaya statik yanıt sağlama.</span><span class="sxs-lookup"><span data-stu-id="3571e-209">Providing a static response to a well-known endpoint.</span></span>
- <span data-ttu-id="3571e-210">Arka uç taşındığında veya geçirildiğinde bir API uç noktasının tutarlı tutulması.</span><span class="sxs-lookup"><span data-stu-id="3571e-210">Keeping an API endpoint consistent while the back end is moved or migrated.</span></span>

<span data-ttu-id="3571e-211">Proxy 'ler JSON tanımları olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="3571e-211">Proxies are stored as JSON definitions.</span></span> <span data-ttu-id="3571e-212">Aşağıda bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="3571e-212">Here is an example:</span></span>

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

<span data-ttu-id="3571e-213">`Domain Redirect` proxy, kısaltılmış bir yol alır ve daha uzun işlev kaynağıyla eşlenir.</span><span class="sxs-lookup"><span data-stu-id="3571e-213">The `Domain Redirect` proxy takes a shortened route and maps it to the longer function resource.</span></span> <span data-ttu-id="3571e-214">Dönüştürme şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="3571e-214">The transformation looks like:</span></span>

`https://--shorturl--/123` -> `https://--longurl--.azurewebsites.net/api/UrlRedirect/123`

<span data-ttu-id="3571e-215">`Root` proxy, kök URL 'ye gönderilen her şeyi alır (`https://--shorturl--/`) ve belge sitesine yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="3571e-215">The `Root` proxy takes anything sent to the root URL (`https://--shorturl--/`) and redirects it to the documentation site.</span></span>

<span data-ttu-id="3571e-216">Azure 'da ara sunucu kullanımıyla ilgili bir örnek gösterilir [: sunucusuz Azure işlevleri ile Uygulamanızı buluta taşıyın](https://channel9.msdn.com/events/Connect/2017/E102).</span><span class="sxs-lookup"><span data-stu-id="3571e-216">An example of using proxies is shown in the video [Azure: Bring your app to the cloud with serverless Azure Functions](https://channel9.msdn.com/events/Connect/2017/E102).</span></span> <span data-ttu-id="3571e-217">Gerçek zamanlı olarak, yerel SQL Server üzerinde çalışan bir ASP.NET Core uygulaması Azure bulutuna geçirilir.</span><span class="sxs-lookup"><span data-stu-id="3571e-217">In real time, an ASP.NET Core application running on local SQL Server is migrated to the Azure Cloud.</span></span> <span data-ttu-id="3571e-218">Proxy 'ler, işlevleri kullanmak üzere geleneksel bir Web API projesini yeniden düzenleme konusunda yardımcı olmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3571e-218">Proxies are used to help refactor a traditional Web API project to use functions.</span></span>

<span data-ttu-id="3571e-219">Proxy 'Ler hakkında daha fazla bilgi için bkz. [Azure işlev proxy'leri Ile çalışma](https://docs.microsoft.com/azure/azure-functions/functions-proxies).</span><span class="sxs-lookup"><span data-stu-id="3571e-219">For more information about Proxies, see [Work with Azure Functions Proxies](https://docs.microsoft.com/azure/azure-functions/functions-proxies).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="3571e-220">[Önceki](azure-serverless-platform.md)
>[İleri](application-insights.md)</span><span class="sxs-lookup"><span data-stu-id="3571e-220">[Previous](azure-serverless-platform.md)
[Next](application-insights.md)</span></span>
