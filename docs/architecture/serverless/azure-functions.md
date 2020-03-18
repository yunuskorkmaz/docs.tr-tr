---
title: Azure Fonksiyonları - Sunucusuz uygulamalar
description: Azure işlevleri, olay odaklı anlık ölçek kodu sağlamak için birden çok dilde (C#, JavaScript, Java) ve platformlarda sunucusuz özellikler sağlar.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 8764e6a33f3fdd53e60fa767d0fb584a9c07de7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401615"
---
# <a name="azure-functions"></a><span data-ttu-id="e7e5a-103">Azure İşlevleri</span><span class="sxs-lookup"><span data-stu-id="e7e5a-103">Azure Functions</span></span>

<span data-ttu-id="e7e5a-104">Azure işlevleri sunucusuz bir bilgi işlem deneyimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-104">Azure functions provide a serverless compute experience.</span></span> <span data-ttu-id="e7e5a-105">Bir işlev bir *tetikleyici* tarafından çağrılır (örneğin, bir HTTP bitiş noktası veya zamanlayıcıya erişim) ve bir kod bloğu veya iş mantığı yürütür.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-105">A function is invoked by a *trigger* (such as access to an HTTP endpoint or a timer) and executes a block of code or business logic.</span></span> <span data-ttu-id="e7e5a-106">İşlevler, depolama ve kuyruklar gibi kaynaklara bağlanan özel *bağlamaları* da destekler.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-106">Functions also support specialized *bindings* that connect to resources like storage and queues.</span></span>

![Azure işlevleri logosu](./media/azure-functions-logo.png)

<span data-ttu-id="e7e5a-108">Azure İşlevler çerçevesinin iki sürümü vardır.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-108">There are two versions of the Azure Functions framework.</span></span> <span data-ttu-id="e7e5a-109">Eski sürüm tam .NET Framework'u destekler ve yeni çalışma süresi çapraz platform .NET Core uygulamalarını destekler.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-109">The legacy version supports the full .NET Framework and the new runtime supports cross-platform .NET Core applications.</span></span> <span data-ttu-id="e7e5a-110">JavaScript, F#ve Java gibi C# ek dilleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-110">Additional languages besides C# such as JavaScript, F#, and Java are supported.</span></span> <span data-ttu-id="e7e5a-111">Portalda oluşturulan işlevler zengin bir komut dosyası sözdizimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-111">Functions created in the portal provide a rich scripting syntax.</span></span> <span data-ttu-id="e7e5a-112">Bağımsız projeler olarak oluşturulan işlevler tam platform desteği ve yetenekleri ile dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-112">Functions created as standalone projects can be deployed with full platform support and capabilities.</span></span>

<span data-ttu-id="e7e5a-113">Daha fazla bilgi için Azure [İşlevleri belgelerine](https://docs.microsoft.com/azure/azure-functions)bakın.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-113">For more information, see [Azure Functions documentation](https://docs.microsoft.com/azure/azure-functions).</span></span>

## <a name="functions-v1-vs-v2"></a><span data-ttu-id="e7e5a-114">Fonksiyonlar v1 vs. v2</span><span class="sxs-lookup"><span data-stu-id="e7e5a-114">Functions v1 vs. v2</span></span>

<span data-ttu-id="e7e5a-115">Azure İşlevleri çalışma zamanının iki sürümü vardır: 1.x ve 2.x.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-115">There are two versions of the Azure Functions runtime: 1.x and 2.x.</span></span> <span data-ttu-id="e7e5a-116">Sürüm 1.x genellikle kullanılabilir (GA).</span><span class="sxs-lookup"><span data-stu-id="e7e5a-116">Version 1.x is generally available (GA).</span></span> <span data-ttu-id="e7e5a-117">Portal veya Windows makinelerinden .NET geliştirmeyi destekler ve .NET Framework'i kullanır.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-117">It supports .NET development from the portal or Windows machines and uses the .NET Framework.</span></span> <span data-ttu-id="e7e5a-118">1.x, Python, PHP, TypeScript, Batch, Bash ve PowerShell için deneysel destekle C#, JavaScript ve F#'ı destekler.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-118">1.x supports C#, JavaScript, and F#, with experimental support for Python, PHP, TypeScript, Batch, Bash, and PowerShell.</span></span>

<span data-ttu-id="e7e5a-119">[Sürüm 2.x de genel olarak şimdi kullanılabilir](https://azure.microsoft.com/blog/introducing-azure-functions-2-0/).</span><span class="sxs-lookup"><span data-stu-id="e7e5a-119">[Version 2.x is also generally available now](https://azure.microsoft.com/blog/introducing-azure-functions-2-0/).</span></span> <span data-ttu-id="e7e5a-120">.NET Core'dan yararlanır ve Windows, macOS ve Linux makinelerinde platformlar arası geliştirmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-120">It leverages .NET Core and supports cross-platform development on Windows, macOS, and Linux machines.</span></span> <span data-ttu-id="e7e5a-121">2.x Java için birinci sınıf destek ekler, ancak henüz deneysel dillerin hiçbirini doğrudan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-121">2.x adds first-class support for Java but doesn't yet directly support any of the experimental languages.</span></span> <span data-ttu-id="e7e5a-122">Sürüm 2.x, platforma üçüncü taraf uzantıları, bağlamaların bağımsız sürümü ve daha kolay bir yürütme ortamı sağlayan yeni bir bağlayıcı genişletilebilirlik modeli kullanır.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-122">Version 2.x uses a new binding extensibility model that enables third-party extensions to the platform, independent versioning of bindings, and a more streamlined execution environment.</span></span>

> <span data-ttu-id="e7e5a-123">**[Bağlayıcı yönlendirme desteği](https://github.com/Azure/azure-functions-host/issues/992)ile 1.x bilinen bir sorun vardır.**</span><span class="sxs-lookup"><span data-stu-id="e7e5a-123">**There is a known issue in 1.x with [binding redirect support](https://github.com/Azure/azure-functions-host/issues/992).**</span></span> <span data-ttu-id="e7e5a-124">Sorun .NET geliştirmeye özgüdür.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-124">The issue is specific to .NET development.</span></span> <span data-ttu-id="e7e5a-125">Çalışma zamanında dahil edilen kitaplıklardan farklı bir sürüme sahip kitaplıklara bağımlılık ları olan projeler etkilenir.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-125">Projects with dependencies on libraries that are a different version from the libraries included in the runtime are impacted.</span></span> <span data-ttu-id="e7e5a-126">Fonksiyonlar ekibi, sorun üzerinde somut ilerleme kaydetmeyi taahhüt etmiştir.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-126">The functions team has committed to making concrete progress on the problem.</span></span> <span data-ttu-id="e7e5a-127">Takım, genel kullanılabilirliğe geçmeden önce 2.x'te bağlama yönlendirmelerini ele alacaktır.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-127">The team will address binding redirects in 2.x before it goes into general availability.</span></span> <span data-ttu-id="e7e5a-128">Önerilen düzeltmeler ve geçici çözümleriçeren resmi ekip bildirimine buradan ulaşabilirsiniz: [Azure İşyerlerinde Derleme çözümü.](https://github.com/Azure/azure-functions-host/wiki/Assembly-Resolution-in-Azure-Functions)</span><span class="sxs-lookup"><span data-stu-id="e7e5a-128">The official team statement with suggested fixes and workarounds is available here: [Assembly resolution in Azure Functions](https://github.com/Azure/azure-functions-host/wiki/Assembly-Resolution-in-Azure-Functions).</span></span>

<span data-ttu-id="e7e5a-129">Daha fazla bilgi için bkz: [1.x ve 2.x karşılaştırın.](https://docs.microsoft.com/azure/azure-functions/functions-versions)</span><span class="sxs-lookup"><span data-stu-id="e7e5a-129">For more information, see [Compare 1.x and 2.x](https://docs.microsoft.com/azure/azure-functions/functions-versions).</span></span>

## <a name="programming-language-support"></a><span data-ttu-id="e7e5a-130">Programlama dili desteği</span><span class="sxs-lookup"><span data-stu-id="e7e5a-130">Programming language support</span></span>

<span data-ttu-id="e7e5a-131">Aşağıdaki diller genel kullanılabilirlik (GA), önizleme veya deneysel olarak desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-131">The following languages are supported either in general availability (GA), preview, or experimental.</span></span>

|<span data-ttu-id="e7e5a-132">Dil</span><span class="sxs-lookup"><span data-stu-id="e7e5a-132">Language</span></span>      |<span data-ttu-id="e7e5a-133">1.x</span><span class="sxs-lookup"><span data-stu-id="e7e5a-133">1.x</span></span>         |<span data-ttu-id="e7e5a-134">2.x</span><span class="sxs-lookup"><span data-stu-id="e7e5a-134">2.x</span></span>      |
|--------------|------------|---------|
|<span data-ttu-id="e7e5a-135">**C #**</span><span class="sxs-lookup"><span data-stu-id="e7e5a-135">**C#**</span></span>        |<span data-ttu-id="e7e5a-136">GA</span><span class="sxs-lookup"><span data-stu-id="e7e5a-136">GA</span></span>          |<span data-ttu-id="e7e5a-137">Önizleme</span><span class="sxs-lookup"><span data-stu-id="e7e5a-137">Preview</span></span>  |
|<span data-ttu-id="e7e5a-138">**Javascript**</span><span class="sxs-lookup"><span data-stu-id="e7e5a-138">**JavaScript**</span></span>|<span data-ttu-id="e7e5a-139">GA</span><span class="sxs-lookup"><span data-stu-id="e7e5a-139">GA</span></span>          |<span data-ttu-id="e7e5a-140">Önizleme</span><span class="sxs-lookup"><span data-stu-id="e7e5a-140">Preview</span></span>  |
|<span data-ttu-id="e7e5a-141">**F#**</span><span class="sxs-lookup"><span data-stu-id="e7e5a-141">**F#**</span></span>        |<span data-ttu-id="e7e5a-142">GA</span><span class="sxs-lookup"><span data-stu-id="e7e5a-142">GA</span></span>          |         |
|<span data-ttu-id="e7e5a-143">**Java**</span><span class="sxs-lookup"><span data-stu-id="e7e5a-143">**Java**</span></span>      |            |<span data-ttu-id="e7e5a-144">Önizleme</span><span class="sxs-lookup"><span data-stu-id="e7e5a-144">Preview</span></span>  |
|<span data-ttu-id="e7e5a-145">**Python**</span><span class="sxs-lookup"><span data-stu-id="e7e5a-145">**Python**</span></span>    |<span data-ttu-id="e7e5a-146">Deneysel</span><span class="sxs-lookup"><span data-stu-id="e7e5a-146">Experimental</span></span>|         |
|<span data-ttu-id="e7e5a-147">**PHP**</span><span class="sxs-lookup"><span data-stu-id="e7e5a-147">**PHP**</span></span>       |<span data-ttu-id="e7e5a-148">Deneysel</span><span class="sxs-lookup"><span data-stu-id="e7e5a-148">Experimental</span></span>|         |
|<span data-ttu-id="e7e5a-149">**TypeScript**</span><span class="sxs-lookup"><span data-stu-id="e7e5a-149">**TypeScript**</span></span>|<span data-ttu-id="e7e5a-150">Deneysel</span><span class="sxs-lookup"><span data-stu-id="e7e5a-150">Experimental</span></span>|         |
|<span data-ttu-id="e7e5a-151">**Toplu iş**</span><span class="sxs-lookup"><span data-stu-id="e7e5a-151">**Batch**</span></span>     |<span data-ttu-id="e7e5a-152">Deneysel</span><span class="sxs-lookup"><span data-stu-id="e7e5a-152">Experimental</span></span>|         |
|<span data-ttu-id="e7e5a-153">**Bash**</span><span class="sxs-lookup"><span data-stu-id="e7e5a-153">**Bash**</span></span>      |<span data-ttu-id="e7e5a-154">Deneysel</span><span class="sxs-lookup"><span data-stu-id="e7e5a-154">Experimental</span></span>|         |
|<span data-ttu-id="e7e5a-155">**Powershell**</span><span class="sxs-lookup"><span data-stu-id="e7e5a-155">**PowerShell**</span></span>|<span data-ttu-id="e7e5a-156">Deneysel</span><span class="sxs-lookup"><span data-stu-id="e7e5a-156">Experimental</span></span>|         |

<span data-ttu-id="e7e5a-157">Daha fazla bilgi için bkz. [Desteklenen diller](https://docs.microsoft.com/azure/azure-functions/supported-languages).</span><span class="sxs-lookup"><span data-stu-id="e7e5a-157">For more information, see [Supported languages](https://docs.microsoft.com/azure/azure-functions/supported-languages).</span></span>

## <a name="app-service-plans"></a><span data-ttu-id="e7e5a-158">Uygulama hizmeti planları</span><span class="sxs-lookup"><span data-stu-id="e7e5a-158">App service plans</span></span>

<span data-ttu-id="e7e5a-159">İşlevler bir *uygulama hizmet planı*tarafından yedeklenir.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-159">Functions are backed by an *app service plan*.</span></span> <span data-ttu-id="e7e5a-160">Plan, işlevler uygulaması tarafından kullanılan kaynakları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-160">The plan defines the resources used by the functions app.</span></span> <span data-ttu-id="e7e5a-161">Bir bölgeye planlar atayabilir, kullanılacak sanal makinelerin boyutunu ve sayısını belirleyebilir ve bir fiyatlandırma katmanı seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-161">You can assign plans to a region, determine the size and number of virtual machines that will be used, and pick a pricing tier.</span></span> <span data-ttu-id="e7e5a-162">Gerçek bir sunucusuz yaklaşım için işlev uygulamaları **tüketim** planını kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-162">For a true serverless approach, function apps may use the **consumption** plan.</span></span> <span data-ttu-id="e7e5a-163">Tüketim planı, arka ucunu yüke göre otomatik olarak ölçeklendirecektir.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-163">The consumption plan will scale the back end automatically based on load.</span></span>

<span data-ttu-id="e7e5a-164">Daha fazla bilgi için [Uygulama hizmet planlarına](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview)bakın.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-164">For more information, see [App service plans](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).</span></span>

## <a name="create-your-first-function"></a><span data-ttu-id="e7e5a-165">İlk uygulamanızı oluşturma</span><span class="sxs-lookup"><span data-stu-id="e7e5a-165">Create your first function</span></span>

<span data-ttu-id="e7e5a-166">İşlev uygulamaları oluşturmanın üç yaygın yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-166">There are three common ways you can create function apps.</span></span>

- <span data-ttu-id="e7e5a-167">Portaldaki komut dosyası işlevleri.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-167">Script functions in the portal.</span></span>
- <span data-ttu-id="e7e5a-168">Azure CLI'yi kullanarak gerekli kaynakları oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-168">Create the necessary resources using the Azure CLI.</span></span>
- <span data-ttu-id="e7e5a-169">En sevdiğiniz IDE'yi kullanarak işlevleri yerel olarak oluşturun ve Bunları Azure'da yayınlayın.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-169">Build functions locally using your favorite IDE and publish them to Azure.</span></span>

<span data-ttu-id="e7e5a-170">Portalda komut dosyası işlevi oluşturma hakkında daha fazla bilgi için azure [portalında ilk işlevinizi oluştur'a](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function)bakın.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-170">For more information on creating a scripted function in the portal, see [Create your first function in the Azure portal](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function).</span></span>

<span data-ttu-id="e7e5a-171">Azure CLI'den oluşturmak için [bkz.](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli)</span><span class="sxs-lookup"><span data-stu-id="e7e5a-171">To build from the Azure CLI, see [Create your first function using the Azure CLI](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli).</span></span>

<span data-ttu-id="e7e5a-172">Visual Studio'dan bir işlev oluşturmak için visual [studio'u kullanarak ilk işlevinizi oluşturun'e](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio)bakın.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-172">To create a function from Visual Studio, see [Create your first function using Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio).</span></span>

## <a name="understand-triggers-and-bindings"></a><span data-ttu-id="e7e5a-173">Tetikleyicileri ve bağlamaları anlama</span><span class="sxs-lookup"><span data-stu-id="e7e5a-173">Understand triggers and bindings</span></span>

<span data-ttu-id="e7e5a-174">Fonksiyonlar bir *tetikleyici* tarafından çağrılır ve tam olarak bir tane olabilir.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-174">Functions are invoked by a *trigger* and can have exactly one.</span></span> <span data-ttu-id="e7e5a-175">İşlev çağırmak için ek olarak, bazı tetikleyiciler de bağlama olarak hizmet vermektedir.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-175">In addition to invoking the function, certain triggers also serve as bindings.</span></span> <span data-ttu-id="e7e5a-176">Tetikleyiciye ek olarak birden çok bağlama da tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-176">You may also define multiple bindings in addition to the trigger.</span></span> <span data-ttu-id="e7e5a-177">*Bağlamalar,* verileri kodunuza bağlamak için bildirimsel bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-177">*Bindings* provide a declarative way to connect data to your code.</span></span> <span data-ttu-id="e7e5a-178">Bunlar (giriş) geçirilebilir veya veri (çıktı) alabilir.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-178">They can be passed in (input) or receive data (output).</span></span> <span data-ttu-id="e7e5a-179">Tetikleyiciler ve bağlamalar işlevlerin çalışmasını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-179">Triggers and bindings make functions easy to work with.</span></span> <span data-ttu-id="e7e5a-180">Bağlamalar, veritabanı veya dosya sistemi bağlantılarının el ile oluşturma ek yükü kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-180">Bindings remove the overhead of manually creating database or file system connections.</span></span> <span data-ttu-id="e7e5a-181">Bağlamalar için gereken tüm bilgiler, komut dosyaları için özel bir *functions.json* dosyasında bulunur veya koddaki özniteliklerle birlikte bildirilir.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-181">All of the information needed for the bindings is contained in a special *functions.json* file for scripts or declared with attributes in code.</span></span>

<span data-ttu-id="e7e5a-182">Bazı yaygın tetikleyiciler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e7e5a-182">Some common triggers include:</span></span>

- <span data-ttu-id="e7e5a-183">Blob Depolama: Bir dosya veya klasör depolama alanına yüklendiğinde veya değiştirildiğinde işlevinizi çağırın.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-183">Blob Storage: invoke your function when a file or folder is uploaded or changed in storage.</span></span>
- <span data-ttu-id="e7e5a-184">HTTP: REST API gibi işlevinizi çağırın.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-184">HTTP: invoke your function like a REST API.</span></span>
- <span data-ttu-id="e7e5a-185">Sıra: Öğeler kuyrukta olduğunda işlevinizi çağırın.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-185">Queue: invoke your function when items exist in a queue.</span></span>
- <span data-ttu-id="e7e5a-186">Zamanlayıcı: düzenli bir cadence üzerinde işlevinizi çağırmak.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-186">Timer: invoke your function on a regular cadence.</span></span>

<span data-ttu-id="e7e5a-187">Bağlamalara örnek olarak şunlar verilebilir:</span><span class="sxs-lookup"><span data-stu-id="e7e5a-187">Examples of bindings include:</span></span>

- <span data-ttu-id="e7e5a-188">CosmosDB: dosyaları yüklemek veya kaydetmek için veritabanına kolayca bağlanın.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-188">CosmosDB: easily connect to the database to load or save files.</span></span>
- <span data-ttu-id="e7e5a-189">Tablo Depolama: fonksiyon uygulamanızdan anahtar/değer depolama ile çalışın.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-189">Table Storage: work with key/value storage from your function app.</span></span>
- <span data-ttu-id="e7e5a-190">Sıra Depolama: öğeleri kuyruktan kolayca alın veya kuyruğa yeni öğeler yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-190">Queue Storage: easily retrieve items from a queue, or place new items on the queue.</span></span>

<span data-ttu-id="e7e5a-191">Aşağıdaki örnek *functions.json* dosyası bir tetikleyici ve bağlama tanımlar:</span><span class="sxs-lookup"><span data-stu-id="e7e5a-191">The following example *functions.json* file defines a trigger and a binding:</span></span>

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

<span data-ttu-id="e7e5a-192">Bu örnekte, işlev `images` kapsayıcıda blob depolama bir değişiklik tarafından tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-192">In this example, the function is triggered by a change to blob storage in the `images` container.</span></span> <span data-ttu-id="e7e5a-193">Dosyaiçin bilgiler geçirilir, bu nedenle tetikleyici de bağlayıcı olarak hareket eder.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-193">The information for the file is passed in, so the trigger also acts as a binding.</span></span> <span data-ttu-id="e7e5a-194">Başka bir bağlama adlı `images`bir kuyruğa bilgi koymak için var.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-194">Another binding exists to put information onto a queue named `images`.</span></span>

<span data-ttu-id="e7e5a-195">Burada işlev için C# komut dosyası:</span><span class="sxs-lookup"><span data-stu-id="e7e5a-195">Here is the C# script for the function:</span></span>

```csharp
public static string Run(Stream myBlob, string name, TraceWriter log)
{
    log.Info($"C# Blob trigger function Processed blob\n Name:{name} \n Size: {myBlob.Length} Bytes");
    return name;
}
```

<span data-ttu-id="e7e5a-196">Örnek, değiştirilen veya blob depolamasına yüklenen dosyanın adını alan ve daha sonra işleme için sıraya koyan basit bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-196">The example is a simple function that takes the name of the file that was modified or uploaded to blob storage, and places it on a queue for later processing.</span></span>

<span data-ttu-id="e7e5a-197">Tetikleyicilerin ve bağlamaların tam listesi için Azure [İşlevleri tetikleyicileri ve bağlama kavramlarını](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings)görün.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-197">For a full list of triggers and bindings, see [Azure Functions triggers and bindings concepts](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings).</span></span>

## <a name="proxies"></a><span data-ttu-id="e7e5a-198">Proxy 'leri</span><span class="sxs-lookup"><span data-stu-id="e7e5a-198">Proxies</span></span>

<span data-ttu-id="e7e5a-199">Ek severler, uygulamanız için yeniden yönlendirme işlevselliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-199">Proxies provide redirect functionality for your application.</span></span> <span data-ttu-id="e7e5a-200">Ekseksiler, bitiş noktasını başka bir kaynağa gösterir ve haritayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-200">Proxies expose an endpoint and map that endpoint to another resource.</span></span> <span data-ttu-id="e7e5a-201">Vekillerile şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e7e5a-201">With proxies, you can:</span></span>

- <span data-ttu-id="e7e5a-202">Gelen isteği başka bir bitiş noktasına yeniden yönlendirin.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-202">Reroute an incoming request to another endpoint.</span></span>
- <span data-ttu-id="e7e5a-203">Gelen isteği geçirilmeden önce değiştirin.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-203">Modify the incoming request before it's passed along.</span></span>
- <span data-ttu-id="e7e5a-204">Değiştirin veya yanıt sağlayın.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-204">Modify or provide a response.</span></span>

<span data-ttu-id="e7e5a-205">Ekseksitler gibi senaryolar için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="e7e5a-205">Proxies are used for scenarios such as:</span></span>

- <span data-ttu-id="e7e5a-206">URL'yi basitleştirme, kısaltma veya değiştirme.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-206">Simplifying, shortening, or changing the URL.</span></span>
- <span data-ttu-id="e7e5a-207">Birden çok arka uç hizmetine tutarlı bir API öneki sağlar.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-207">Providing a consistent API prefix to multiple back-end services.</span></span>
- <span data-ttu-id="e7e5a-208">Geliştirilen bir uç noktaya verilen yanıtla alay etmek.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-208">Mocking a response to an endpoint being developed.</span></span>
- <span data-ttu-id="e7e5a-209">Bilinen bir bitiş noktasına statik yanıt sağlar.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-209">Providing a static response to a well-known endpoint.</span></span>
- <span data-ttu-id="e7e5a-210">Arka uç taşınırken veya geçirilirken API bitiş noktasını tutarlı tutmak.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-210">Keeping an API endpoint consistent while the back end is moved or migrated.</span></span>

<span data-ttu-id="e7e5a-211">Yakınlıklar JSON tanımları olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-211">Proxies are stored as JSON definitions.</span></span> <span data-ttu-id="e7e5a-212">Örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="e7e5a-212">Here is an example:</span></span>

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

<span data-ttu-id="e7e5a-213">Proxy `Domain Redirect` kısaltılmış bir rota alır ve daha uzun işlev kaynağıyla eşler.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-213">The `Domain Redirect` proxy takes a shortened route and maps it to the longer function resource.</span></span> <span data-ttu-id="e7e5a-214">Dönüşüm gibi görünüyor:</span><span class="sxs-lookup"><span data-stu-id="e7e5a-214">The transformation looks like:</span></span>

`https://--shorturl--/123` -> `https://--longurl--.azurewebsites.net/api/UrlRedirect/123`

<span data-ttu-id="e7e5a-215">Proxy, kök URL'ye `Root` gönderilen`https://--shorturl--/`bir şeyi alır ( ) ve belgeleme sitesine yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-215">The `Root` proxy takes anything sent to the root URL (`https://--shorturl--/`) and redirects it to the documentation site.</span></span>

<span data-ttu-id="e7e5a-216">Ekseksi kullanmanın bir örneği Azure videosunda [gösterilir: Sunucusuz Azure İşlevleri ile uygulamanızı buluta getirin.](https://channel9.msdn.com/events/Connect/2017/E102)</span><span class="sxs-lookup"><span data-stu-id="e7e5a-216">An example of using proxies is shown in the video [Azure: Bring your app to the cloud with serverless Azure Functions](https://channel9.msdn.com/events/Connect/2017/E102).</span></span> <span data-ttu-id="e7e5a-217">Gerçek zamanlı olarak, yerel SQL Server'da çalışan bir ASP.NET Core uygulaması Azure Bulutu'na geçirilir.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-217">In real time, an ASP.NET Core application running on local SQL Server is migrated to the Azure Cloud.</span></span> <span data-ttu-id="e7e5a-218">Ekseksiler, işlevleri kullanmak için geleneksel bir Web API projesini yeniden düzenlemeye yardımcı olmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-218">Proxies are used to help refactor a traditional Web API project to use functions.</span></span>

<span data-ttu-id="e7e5a-219">Proxies hakkında daha fazla bilgi için Azure [İşleriyle Çalışma'ya](https://docs.microsoft.com/azure/azure-functions/functions-proxies)bakın.</span><span class="sxs-lookup"><span data-stu-id="e7e5a-219">For more information about Proxies, see [Work with Azure Functions Proxies](https://docs.microsoft.com/azure/azure-functions/functions-proxies).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="e7e5a-220">[Önceki](azure-serverless-platform.md)
>[Sonraki](application-insights.md)</span><span class="sxs-lookup"><span data-stu-id="e7e5a-220">[Previous](azure-serverless-platform.md)
[Next](application-insights.md)</span></span>
