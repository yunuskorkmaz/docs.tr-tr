---
title: Davpr ile çalışmaya başlama
description: Yerel geliştirme ortamınızı hazırlamaya ve ilk .NET uygulamalarınızı Davpr ile oluşturmaya yönelik bir kılavuz.
author: amolenk
ms.date: 02/07/2021
ms.openlocfilehash: 4d984f5f31f00e776fb9d521592ad9dbb4a79339
ms.sourcegitcommit: b924ade6426cf61a4604c4e2ee54cb3592c29317
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/18/2021
ms.locfileid: "101096746"
---
# <a name="get-started-with-dapr"></a><span data-ttu-id="62038-103">Davpr ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="62038-103">Get started with Dapr</span></span>

<span data-ttu-id="62038-104">İlk iki bölümde, Davpr hakkında temel kavramları öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="62038-104">In the first two chapters, you learned basic concepts about Dapr.</span></span> <span data-ttu-id="62038-105">Bunu bir *sınama sürücüsü* için alma zamanı.</span><span class="sxs-lookup"><span data-stu-id="62038-105">It's time to take it for a *test drive*.</span></span> <span data-ttu-id="62038-106">Bu bölüm, yerel geliştirme ortamınızı hazırlama ve iki Davpr .NET uygulaması oluşturma konusunda size kılavuzluk eder.</span><span class="sxs-lookup"><span data-stu-id="62038-106">This chapter will guide you through preparing your local development environment and building two Dapr .NET applications.</span></span>

## <a name="install-dapr-into-your-local-environment"></a><span data-ttu-id="62038-107">Yerel ortamınıza Davpr 'yi yükler</span><span class="sxs-lookup"><span data-stu-id="62038-107">Install Dapr into your local environment</span></span>

<span data-ttu-id="62038-108">Geliştirme bilgisayarınıza Dadpr 'yi yükleyerek başlayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="62038-108">You'll start by installing Dapr on your development computer.</span></span> <span data-ttu-id="62038-109">Tamamlandıktan sonra, [kendi kendine barındırılan modda](https://docs.dapr.io/operations/hosting/self-hosted/self-hosted-overview/)dadpr uygulamaları oluşturup çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62038-109">Once complete, you can build and run Dapr applications in [self-hosted mode](https://docs.dapr.io/operations/hosting/self-hosted/self-hosted-overview/).</span></span>

1. <span data-ttu-id="62038-110">[Davpr CLI 'Yı yükler](https://docs.dapr.io/getting-started/install-dapr-cli/).</span><span class="sxs-lookup"><span data-stu-id="62038-110">[Install the Dapr CLI](https://docs.dapr.io/getting-started/install-dapr-cli/).</span></span> <span data-ttu-id="62038-111">Bu, Davpr örneklerini başlatmanıza, çalıştırmanıza ve yönetmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="62038-111">It enables you to launch, run, and manage Dapr instances.</span></span> <span data-ttu-id="62038-112">Hata ayıklama desteği de sağlar.</span><span class="sxs-lookup"><span data-stu-id="62038-112">It also provides debugging support.</span></span>

1. <span data-ttu-id="62038-113">[Docker Desktop](https://docs.docker.com/get-docker/)'ı yükler.</span><span class="sxs-lookup"><span data-stu-id="62038-113">Install [Docker Desktop](https://docs.docker.com/get-docker/).</span></span> <span data-ttu-id="62038-114">Windows üzerinde çalıştırıyorsanız, **Windows Için Docker Desktop** ' ın Linux kapsayıcıları kullanacak şekilde yapılandırıldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="62038-114">If you're running on Windows, make sure that **Docker Desktop for Windows** is configured to use Linux containers.</span></span>

  > [!NOTE]
  > <span data-ttu-id="62038-115">Varsayılan olarak, Davpr size en iyi kullanıma hazır deneyim sağlamak için Docker Kapsayıcıları kullanır.</span><span class="sxs-lookup"><span data-stu-id="62038-115">By default, Dapr uses Docker containers to provide you the best out-of-the-box experience.</span></span> <span data-ttu-id="62038-116">PAPR 'yi Docker dışında çalıştırmak için, bu adımı atlayabilir ve [ *ince* bir başlatma yürütebilirsiniz](https://docs.dapr.io/operations/hosting/self-hosted/self-hosted-no-docker/).</span><span class="sxs-lookup"><span data-stu-id="62038-116">To run Dapr outside of Docker, you can skip this step and [execute a *slim* initialization](https://docs.dapr.io/operations/hosting/self-hosted/self-hosted-no-docker/).</span></span> <span data-ttu-id="62038-117">Bu bölümdeki örneklerde Docker Kapsayıcıları kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="62038-117">The examples in this chapter require you use Docker containers.</span></span>

1. <span data-ttu-id="62038-118">[Davpr 'Yi başlatın](https://docs.dapr.io/getting-started/install-dapr/).</span><span class="sxs-lookup"><span data-stu-id="62038-118">[Initialize Dapr](https://docs.dapr.io/getting-started/install-dapr/).</span></span> <span data-ttu-id="62038-119">Bu adım, en son Davpr ikililerini ve kapsayıcı görüntülerini yükleyerek geliştirme ortamınızı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="62038-119">This step sets up your development environment by installing the latest Dapr binaries and container images.</span></span>

1. <span data-ttu-id="62038-120">.NET Core 3,1 için [.NET Core 3 geliştirme araçları](https://dotnet.microsoft.com/download/dotnet-core/3.1) 'nı yükler.</span><span class="sxs-lookup"><span data-stu-id="62038-120">Install the [.NET Core 3 Development Tools](https://dotnet.microsoft.com/download/dotnet-core/3.1) for .NET Core 3.1.</span></span>

<span data-ttu-id="62038-121">Artık, bu, ilk bir Davpr uygulamanızı oluşturmak için gereklidir!</span><span class="sxs-lookup"><span data-stu-id="62038-121">Now that Dapr is installed, it's time to build your first Dapr application!</span></span>

## <a name="build-your-first-dapr-application"></a><span data-ttu-id="62038-122">İlk Davpr uygulamanızı oluşturma</span><span class="sxs-lookup"><span data-stu-id="62038-122">Build your first Dapr application</span></span>

<span data-ttu-id="62038-123">Bu, [Davpr durum yönetimi](state-management.md) yapı taşını tüketen basit bir .NET konsol uygulaması oluşturarak başlar.</span><span class="sxs-lookup"><span data-stu-id="62038-123">You'll start by building a simple .NET Console application that consumes the [Dapr state management](state-management.md) building block.</span></span>

### <a name="create-the-application"></a><span data-ttu-id="62038-124">Uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="62038-124">Create the application</span></span>

1. <span data-ttu-id="62038-125">Seçtiğiniz komut kabuğunu veya terminali açın.</span><span class="sxs-lookup"><span data-stu-id="62038-125">Open up the command shell or terminal of your choice.</span></span> <span data-ttu-id="62038-126">[Visual Studio Code](https://code.visualstudio.com/)içindeki Terminal özelliklerini göz önünde bulundurmayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62038-126">You might consider the terminal capabilities in [Visual Studio Code](https://code.visualstudio.com/).</span></span> <span data-ttu-id="62038-127">Uygulamanızı derlemek istediğiniz kök klasöre gidin.</span><span class="sxs-lookup"><span data-stu-id="62038-127">Navigate to the root folder in which you want to build your application.</span></span> <span data-ttu-id="62038-128">Bu kez, yeni bir .NET konsol uygulaması oluşturmak için aşağıdaki komutu girin:</span><span class="sxs-lookup"><span data-stu-id="62038-128">Once there, enter the following command to create a new .NET Console application:</span></span>

   ```dotnetcli
   dotnet new console -o DaprCounter
   ```

   <span data-ttu-id="62038-129">Komut, basit bir "Merhaba Dünya" .NET Core uygulamasını yasaklıyor.</span><span class="sxs-lookup"><span data-stu-id="62038-129">The command scaffolds a simple "Hello World" .NET Core application.</span></span>

1. <span data-ttu-id="62038-130">Ardından, önceki komutla oluşturulan yeni dizine gidin:</span><span class="sxs-lookup"><span data-stu-id="62038-130">Then, navigate into the new directory created by the previous command:</span></span>

   ```console
   cd DaprCounter
   ```

1. <span data-ttu-id="62038-131">Komutunu kullanarak yeni oluşturulan uygulamayı çalıştırın `dotnet run` .</span><span class="sxs-lookup"><span data-stu-id="62038-131">Run the newly created application using the `dotnet run` command.</span></span> <span data-ttu-id="62038-132">"Merhaba Dünya!" yazıyorsa</span><span class="sxs-lookup"><span data-stu-id="62038-132">Doing so writes "Hello World!"</span></span> <span data-ttu-id="62038-133">konsol ekranına:</span><span class="sxs-lookup"><span data-stu-id="62038-133">to the console screen:</span></span>

   ```dotnetcli
   dotnet run
   ```

### <a name="add-dapr-state-management"></a><span data-ttu-id="62038-134">Davpr durum yönetimi ekleme</span><span class="sxs-lookup"><span data-stu-id="62038-134">Add Dapr State Management</span></span>

<span data-ttu-id="62038-135">Daha sonra, programda durum bilgisi olan bir sayaç uygulamak için, Davpr [durum yönetimi yapı taşını](https://docs.dapr.io/developing-applications/building-blocks/state-management/state-management-overview/) kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="62038-135">Next, you'll use the Dapr [state management building block](https://docs.dapr.io/developing-applications/building-blocks/state-management/state-management-overview/) to implement a stateful counter in the program.</span></span>

<span data-ttu-id="62038-136">HTTP ve gRPC için, Davpr 'nin yerel desteğini kullanarak herhangi bir geliştirme platformunda, Davpr API 'Leri çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62038-136">You can invoke Dapr APIs across any development platform using Dapr's native support for HTTP and gRPC.</span></span> <span data-ttu-id="62038-137">Ancak, .NET geliştiricileri, Davpr .NET SDK 'sını daha doğal ve sezgisel olarak bulacaktır.</span><span class="sxs-lookup"><span data-stu-id="62038-137">However, .NET Developers will find the Dapr .NET SDK more natural and intuitive.</span></span> <span data-ttu-id="62038-138">Bu, Davpr API 'Lerini çağırmak için kesin türü belirtilmiş bir .NET istemcisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="62038-138">It provides a strongly-typed .NET client to call the Dapr APIs.</span></span> <span data-ttu-id="62038-139">.NET SDK Ayrıca ASP.NET Core sıkı bir şekilde tümleşir.</span><span class="sxs-lookup"><span data-stu-id="62038-139">The .NET SDK also tightly integrates with ASP.NET Core.</span></span>

1. <span data-ttu-id="62038-140">Terminal penceresinde, `Dapr.Client` NuGet paketini uygulamanıza ekleyin:</span><span class="sxs-lookup"><span data-stu-id="62038-140">From the terminal window, add the `Dapr.Client` NuGet package to your application:</span></span>

   ```dotnetcli
   dotnet add package Dapr.Client
   ```

   > [!NOTE]
   > <span data-ttu-id="62038-141">Bir Davpr 'nin yayın öncesi sürümüyle çalışıyorsanız, bayrağını komuta eklediğinizden emin olun `--prerelease` .</span><span class="sxs-lookup"><span data-stu-id="62038-141">If you're working with a pre-release version of Dapr, be sure to add the `--prerelease` flag to the command.</span></span>

1. <span data-ttu-id="62038-142">Dosyayı en `Program.cs` sevdiğiniz düzenleyicide açın ve içeriğini aşağıdaki kodla güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="62038-142">Open the `Program.cs` file in your favorite editor and update its contents to the following code:</span></span>

   ```csharp
   using System;
   using System.Threading.Tasks;
   using Dapr;
   using Dapr.Client;
   
   namespace DaprCounter
   {
       class Program
       {
           static async Task Main(string[] args)
           {
               var daprClient = new DaprClientBuilder().Build();
   
               var counter = await daprClient.GetStateAsync<int>("statestore", "counter");
   
               while (true)
               {
                   Console.WriteLine($"Counter = {counter++}");
   
                   await daprClient.SaveStateAsync("statestore", "counter", counter);
   
                   await Task.Delay(1000);
               }
           }
       }
   }
   ```

   <span data-ttu-id="62038-143">Güncelleştirilmiş kod aşağıdaki adımları uygular:</span><span class="sxs-lookup"><span data-stu-id="62038-143">The updated code implements the following steps:</span></span>

   - <span data-ttu-id="62038-144">İlk olarak yeni bir `DaprClient` örnek örneği oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="62038-144">First a new `DaprClient` instance is instantiated.</span></span> <span data-ttu-id="62038-145">Bu sınıf, Davpr sidecar ile etkileşim kurmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="62038-145">This class enables you to interact with the Dapr sidecar.</span></span>
   - <span data-ttu-id="62038-146">Durum deposundan, `DaprClient.GetStateAsync` anahtarın değerini getirir `counter` .</span><span class="sxs-lookup"><span data-stu-id="62038-146">From the state store, `DaprClient.GetStateAsync` fetches the value for the `counter` key.</span></span> <span data-ttu-id="62038-147">Anahtar yoksa, varsayılan `int` değer (yani `0` ) döndürülür.</span><span class="sxs-lookup"><span data-stu-id="62038-147">If the key doesn't exist, the default `int` value (which is `0`) is returned.</span></span>
   - <span data-ttu-id="62038-148">Daha sonra kod, `counter` değeri konsola yazarak ve artan bir değeri durum deposuna kaydederek yinelenir.</span><span class="sxs-lookup"><span data-stu-id="62038-148">The code then iterates, writing the `counter` value to the console and saving an incremented value to the state store.</span></span>

1. <span data-ttu-id="62038-149">Davpr CLı `run` komutu uygulamayı başlatır.</span><span class="sxs-lookup"><span data-stu-id="62038-149">The Dapr CLI `run` command starts the application.</span></span> <span data-ttu-id="62038-150">Temel alınan Davpr çalışma zamanını çağırır ve hem uygulama hem de Davpr sepet birlikte çalışmasını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="62038-150">It invokes the underlying Dapr runtime and enables both the application and Dapr sidecar to run together.</span></span> <span data-ttu-id="62038-151">' I atlarsanız, `app-id` davpr uygulama için benzersiz bir ad oluşturacaktır.</span><span class="sxs-lookup"><span data-stu-id="62038-151">If you omit the `app-id`, Dapr will generate a unique name for the application.</span></span> <span data-ttu-id="62038-152">Komutun son segmenti, `dotnet run` Davpr çalışma zamanına .NET Core uygulamasını çalıştırmasını söyler.</span><span class="sxs-lookup"><span data-stu-id="62038-152">The final segment of the command, `dotnet run`, instructs the Dapr runtime to run the .NET core application.</span></span>

   > [!IMPORTANT]
   > <span data-ttu-id="62038-153">Durum yönetimi yapı taşı kullanılırken her zaman açık bir parametre iletilmesi için dikkatli olunmalıdır `app-id` .</span><span class="sxs-lookup"><span data-stu-id="62038-153">Care must be taken to always pass an explicit `app-id` parameter when consuming the state management building block.</span></span> <span data-ttu-id="62038-154">Blok, uygulama kimliği değerini her anahtar/değer çiftinin durum anahtarı için bir *ön ek* olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="62038-154">The block uses the application id value as a *prefix* for its state key for each key/value pair.</span></span> <span data-ttu-id="62038-155">Uygulama kimliği değişirse, önceki depolanmış duruma artık erişemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="62038-155">If the application id changes, you can no longer access the previous stored state.</span></span>

   <span data-ttu-id="62038-156">Şimdi aşağıdaki komutla uygulamayı çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="62038-156">Now run the application with the following command:</span></span>

   ```console
   dapr run --app-id DaprCounter dotnet run
   ```

   <span data-ttu-id="62038-157">Uygulamayı durdurmayı ve yeniden başlatmayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="62038-157">Try stopping and restarting the application.</span></span> <span data-ttu-id="62038-158">Sayacın sıfırlandığını görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="62038-158">You'll see that the counter doesn't reset.</span></span> <span data-ttu-id="62038-159">Bunun yerine, daha önce kaydedilen durumdan devam eder.</span><span class="sxs-lookup"><span data-stu-id="62038-159">Instead it continues from the previously saved state.</span></span> <span data-ttu-id="62038-160">Davpr yapı taşı, uygulamanın durum bilgisi olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="62038-160">The Dapr building block makes the application stateful.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="62038-161">Örnek uygulamanızın önceden yapılandırılmış bir durum bileşeniyle iletişim kuracağını anlamak önemlidir, ancak buna doğrudan bağımlılığı yoktur.</span><span class="sxs-lookup"><span data-stu-id="62038-161">It's important to understand your sample application communicates with a pre-configured state component, but has no direct dependency on it.</span></span> <span data-ttu-id="62038-162">Davpr, bağımlılığı dışarıda bir şekilde soyutlar.</span><span class="sxs-lookup"><span data-stu-id="62038-162">Dapr abstracts away the dependency.</span></span> <span data-ttu-id="62038-163">Kısa bir süre sonra, temel alınan durum deposu bileşeni bir basit yapılandırma güncelleştirmesiyle değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="62038-163">As you'll shortly see, the underlying state store component can be changed with a simple configuration update.</span></span>

<span data-ttu-id="62038-164">Durum tam olarak nerede depolanabileceğini merak ediyor olabilirsiniz mi?</span><span class="sxs-lookup"><span data-stu-id="62038-164">You might be wondering, where exactly is the state stored?</span></span>

## <a name="component-configuration-files"></a><span data-ttu-id="62038-165">Bileşen yapılandırma dosyaları</span><span class="sxs-lookup"><span data-stu-id="62038-165">Component configuration files</span></span>

<span data-ttu-id="62038-166">Yerel ortamınız için ilk olarak Davpr 'yi başlattığınızda, otomatik olarak Redsıs kapsayıcısı temin edilir.</span><span class="sxs-lookup"><span data-stu-id="62038-166">When you first initialized Dapr for your local environment, it automatically provisioned a Redis container.</span></span> <span data-ttu-id="62038-167">Daha sonra, bir bileşen yapılandırma dosyası olan, Redsıs kapsayıcısını varsayılan durum deposu bileşeni olarak Yapılandır `statestore.yaml`</span><span class="sxs-lookup"><span data-stu-id="62038-167">Dapr then configured the Redis container as the default state store component with a component configuration file, entitled `statestore.yaml`.</span></span> <span data-ttu-id="62038-168">İçeriğine göz atın:</span><span class="sxs-lookup"><span data-stu-id="62038-168">Here's a look at its contents:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: statestore
spec:
  type: state.redis
  version: v1
  metadata:
  - name: redisHost
    value: localhost:6379
  - name: redisPassword
    value: ""
  - name: actorStateStore
    value: "true"
```

> [!NOTE]
> <span data-ttu-id="62038-169">Varsayılan bileşen yapılandırma dosyaları `$HOME/.dapr/components` , Linux/macOS klasöründe ve `%USERPROFILE%\.dapr\components` Windows üzerindeki klasörde depolanır.</span><span class="sxs-lookup"><span data-stu-id="62038-169">Default component configuration files are stored in the `$HOME/.dapr/components` folder on Linux/macOS, and in the `%USERPROFILE%\.dapr\components` folder on Windows.</span></span>

<span data-ttu-id="62038-170">Önceki bileşen yapılandırma dosyasının biçimini aklınızda yazın:</span><span class="sxs-lookup"><span data-stu-id="62038-170">Note the format of the previous component configuration file:</span></span>

- <span data-ttu-id="62038-171">Her bileşenin bir adı vardır.</span><span class="sxs-lookup"><span data-stu-id="62038-171">Each component has a name.</span></span> <span data-ttu-id="62038-172">Yukarıdaki örnekte, bileşen adlandırılır `statestore` .</span><span class="sxs-lookup"><span data-stu-id="62038-172">In the sample above, the component is named `statestore`.</span></span> <span data-ttu-id="62038-173">Bu adı, ilk kod örneğimizde bu adı kullandık ve hangi bileşenin kullanılacağını gösteren bir vapr dışarıdan çekme.</span><span class="sxs-lookup"><span data-stu-id="62038-173">We used that name in our first code example to tell the Dapr sidecar which component to use.</span></span>
- <span data-ttu-id="62038-174">Her bileşen yapılandırma dosyasının bir `spec` bölümü vardır.</span><span class="sxs-lookup"><span data-stu-id="62038-174">Each component configuration file has a `spec` section.</span></span> <span data-ttu-id="62038-175">`type`Bileşen türünü belirten bir alan içerir.</span><span class="sxs-lookup"><span data-stu-id="62038-175">It contains a `type` field that specifies the component type.</span></span> <span data-ttu-id="62038-176">`version`Alan, bileşen sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="62038-176">The `version` field specifies the component version.</span></span> <span data-ttu-id="62038-177">`metadata`Alan, bileşenin gerektirdiği, bağlantı ayrıntıları ve diğer ayarlar gibi bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="62038-177">The `metadata` field contains information that the component requires, such as connection details and other settings.</span></span> <span data-ttu-id="62038-178">Meta veri değerleri farklı bileşen türleri için farklılık gösterecektir.</span><span class="sxs-lookup"><span data-stu-id="62038-178">The metadata values will vary for the different types of components.</span></span>

<span data-ttu-id="62038-179">Bir davpr sepet, uygulamanızda yapılandırılmış herhangi bir davpr bileşenini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="62038-179">A Dapr sidecar can consume any Dapr component configured in your application.</span></span> <span data-ttu-id="62038-180">Ancak, bir bileşenin erişilebilirliğini sınırlamak için mimari gerekçe varsa ne olacak?</span><span class="sxs-lookup"><span data-stu-id="62038-180">But, what if you had an architectural justification to limit the accessibility of a component?</span></span> <span data-ttu-id="62038-181">Redin bileşenini yalnızca bir üretim ortamında çalışan Davpr sıfları ile kısıtlayabiliyor musunuz?</span><span class="sxs-lookup"><span data-stu-id="62038-181">How could you restrict the Redis component to Dapr sidecars running only in a production environment?</span></span>

<span data-ttu-id="62038-182">Bunu yapmak için, `namespace` üretim ortamı için bir tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62038-182">To do so, you could define a `namespace` for the production environment.</span></span> <span data-ttu-id="62038-183">Bu adı yazabilirsiniz `production` .</span><span class="sxs-lookup"><span data-stu-id="62038-183">You might name it `production`.</span></span> <span data-ttu-id="62038-184">Şirket içinde barındırılan modda, ortam değişkenini ayarlayarak bir davpr sepet ad alanını belirtirsiniz `NAMESPACE` .</span><span class="sxs-lookup"><span data-stu-id="62038-184">In self-hosted mode, you specify the namespace of a Dapr sidecar by setting the `NAMESPACE` environment variable.</span></span> <span data-ttu-id="62038-185">Yapılandırıldığında, davpr sepet yalnızca ad alanıyla eşleşen bileşenleri yükler.</span><span class="sxs-lookup"><span data-stu-id="62038-185">When configured, the Dapr sidecar will only load the components that match the namespace.</span></span> <span data-ttu-id="62038-186">Kubernetes dağıtımları için Kubernetes ad alanı yüklenen bileşenleri belirler.</span><span class="sxs-lookup"><span data-stu-id="62038-186">For Kubernetes deployments, the Kubernetes namespace determines the components that are loaded.</span></span> <span data-ttu-id="62038-187">Aşağıdaki örnek, bir ad alanına yerleştirilmiş olan redo bileşenini gösterir `production` .</span><span class="sxs-lookup"><span data-stu-id="62038-187">The following sample shows the Redis component placed in a `production` namespace.</span></span> <span data-ttu-id="62038-188">`namespace`Öğesindeki bildirime göz önünde edin `metadata` :</span><span class="sxs-lookup"><span data-stu-id="62038-188">Note the `namespace` declaration in the `metadata` element:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: statestore
  namespace: production
spec:
  type: state.redis
  version: v1
  metadata:
  - name: redisHost
    value: localhost:6379
  - name: redisPassword
    value: ""
  - name: actorStateStore
    value: "true"
```

> [!IMPORTANT]
> <span data-ttu-id="62038-189">Bir gösterilemez bileşeni yalnızca aynı ad alanında çalışan uygulamalar için erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="62038-189">A namespaced component is only accessible to applications running in the same namespace.</span></span> <span data-ttu-id="62038-190">Eğer Davpr uygulamanız bir bileşeni yükleyemediğinde, uygulama ad alanının bileşen ad alanıyla eşleştiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="62038-190">If your Dapr application fails to load a component, make sure that the application namespace matches the component namespace.</span></span> <span data-ttu-id="62038-191">Bu, uygulama ad alanının bir ortam değişkeninde depolandığı, kendi kendine barındırılan modda özellikle karmaşık olabilir `NAMESPACE` .</span><span class="sxs-lookup"><span data-stu-id="62038-191">This can be especially tricky in self-hosted mode where the application namespace is stored in a `NAMESPACE` environment variable.</span></span>

<span data-ttu-id="62038-192">Gerekirse, bir bileşeni belirli bir uygulamayla daha fazla kısıtlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62038-192">If needed, you could further restrict a component to a particular application.</span></span> <span data-ttu-id="62038-193">`production`Ad alanı içinde, Redo önbelleğinin erişimini yalnızca uygulamayla sınırlamak isteyebilirsiniz `DaprCounter` .</span><span class="sxs-lookup"><span data-stu-id="62038-193">Within the `production` namespace, you may want to limit access of the Redis cache to only the `DaprCounter` application.</span></span> <span data-ttu-id="62038-194">Bunu, `scopes` bileşen yapılandırmasında belirterek yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62038-194">You do so by specifying `scopes` in the component configuration.</span></span> <span data-ttu-id="62038-195">Aşağıdaki örnek, `statestore` ad alanındaki uygulamaya redsıs bileşenine erişimin nasıl kısıtlanacağını göstermektedir `DaprCounter` `production` :</span><span class="sxs-lookup"><span data-stu-id="62038-195">The following example shows how to restrict access to the Redis `statestore` component to the application `DaprCounter` in the `production` namespace:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: statestore
  namespace: production
spec:
  type: state.redis
  version: v1
  metadata:
  - name: redisHost
    value: localhost:6379
  - name: redisPassword
    value: ""
  - name: actorStateStore
    value: "true"
  scopes:
  - DaprCounter
```

## <a name="build-a-multi-container-dapr-application"></a><span data-ttu-id="62038-196">Çok kapsayıcılı bir Davpr uygulaması oluşturun</span><span class="sxs-lookup"><span data-stu-id="62038-196">Build a multi-container Dapr application</span></span>

<span data-ttu-id="62038-197">İlk örnekte, bir Davpr sidecar ile yan yana çalıştırılan bir basit .NET konsol uygulaması oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="62038-197">In the first example, you created a simple .NET console application that ran side-by-side with a Dapr sidecar.</span></span> <span data-ttu-id="62038-198">Ancak modern dağıtılmış uygulamalar genellikle birçok hareketli parçadan oluşur.</span><span class="sxs-lookup"><span data-stu-id="62038-198">Modern distributed applications, however, often consist of many moving parts.</span></span> <span data-ttu-id="62038-199">Bağımsız mikro hizmetleri eşzamanlı olarak çalıştırabilirler.</span><span class="sxs-lookup"><span data-stu-id="62038-199">They can simultaneously run independent microservices.</span></span> <span data-ttu-id="62038-200">Bu modern uygulamalar genellikle Kapsayıcılı hale getirilir ve Docker Compose veya Kubernetes gibi kapsayıcı düzenleme araçları gerektirir.</span><span class="sxs-lookup"><span data-stu-id="62038-200">These modern applications are typically containerized and require container orchestration tools such as Docker Compose or Kubernetes.</span></span>

<span data-ttu-id="62038-201">Sonraki örnekte, çok kapsayıcılı bir uygulama oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="62038-201">In the next example, you'll create a multi-container application.</span></span> <span data-ttu-id="62038-202">Ayrıca, hizmetler arasında iletişim kurmak için de [Davpr hizmet çağırma](service-invocation.md) yapı taşını kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="62038-202">You'll also use the [Dapr service invocation](service-invocation.md) building block to communicate between services.</span></span> <span data-ttu-id="62038-203">Çözüm, Web API 'sinden Hava durumu tahminlerini alan bir Web uygulamasından oluşur.</span><span class="sxs-lookup"><span data-stu-id="62038-203">The solution will consist of a web application that retrieves weather forecasts from a web API.</span></span> <span data-ttu-id="62038-204">Her biri bir Docker kapsayıcısında çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="62038-204">They will each run in a Docker container.</span></span> <span data-ttu-id="62038-205">Kapsayıcıyı yerel olarak çalıştırmak ve hata ayıklama yeteneklerini etkinleştirmek için Docker Compose kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="62038-205">You'll use Docker Compose to run the container locally and enable debugging capabilities.</span></span>

<span data-ttu-id="62038-206">Inpr için yerel ortamınızı yapılandırdığınızdan ve [.NET Core 3 geliştirme araçlarının](https://dotnet.microsoft.com/download/dotnet-core/3.1) yüklü olduğundan emin olun (Bu bölümün başında yönergeler mevcuttur).</span><span class="sxs-lookup"><span data-stu-id="62038-206">Make sure you've configured your local environment for Dapr and installed the [.NET Core 3 Development Tools](https://dotnet.microsoft.com/download/dotnet-core/3.1) (instructions are available at the beginning of this chapter).</span></span>

<span data-ttu-id="62038-207">Ayrıca, **.NET Core platformlar arası geliştirme** iş yükü yüklü olan [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) kullanarak bu örneği doldurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="62038-207">Additionally, you'll need complete this sample using [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) with the **.NET Core cross-platform development** workload installed.</span></span>

### <a name="create-the-application"></a><span data-ttu-id="62038-208">Uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="62038-208">Create the application</span></span>

1. <span data-ttu-id="62038-209">Visual Studio 2019 ' de bir **ASP.NET Core Web uygulaması** projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="62038-209">In Visual Studio 2019, create an **ASP.NET Core Web Application** project:</span></span>

   ![Yeni proje oluşturma ekran görüntüsü](./media/getting-started/multicontainer-createproject.png)

1. <span data-ttu-id="62038-211">Projenizi `DaprFrontEnd` ve çözümünüzü adlandırın `DaprMultiContainer` :</span><span class="sxs-lookup"><span data-stu-id="62038-211">Name your project `DaprFrontEnd` and your solution `DaprMultiContainer`:</span></span>

   ![Yeni projenizi yapılandırma ekran görüntüsü](./media/getting-started/multicontainer-configureproject.png)

1. <span data-ttu-id="62038-213">Razor sayfaları olan bir Web uygulaması oluşturmak için **Web uygulaması** ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="62038-213">Select **Web Application** to create a web application with Razor pages.</span></span> <span data-ttu-id="62038-214">**Docker desteğini etkinleştir**' i seçmeyin.</span><span class="sxs-lookup"><span data-stu-id="62038-214">Don't select **Enable Docker Support**.</span></span> <span data-ttu-id="62038-215">Docker desteğini daha sonra ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="62038-215">You'll add Docker support later.</span></span>

   ![Yeni bir ASP.NET Core Web uygulaması oluşturma ekran görüntüsü](./media/getting-started/multicontainer-createwebapp.png)

1. <span data-ttu-id="62038-217">İkinci bir ASP.NET Core Web uygulaması projesini aynı çözüme ekleyin ve bu uygulamayı, *Baprarka uca* çağırın.</span><span class="sxs-lookup"><span data-stu-id="62038-217">Add a second ASP.NET Core Web Application project to the same solution and call it *DaprBackEnd*.</span></span> <span data-ttu-id="62038-218">Proje türü olarak **API 'yi** seçin.</span><span class="sxs-lookup"><span data-stu-id="62038-218">Select **API** as the project type.</span></span> <span data-ttu-id="62038-219">Varsayılan olarak, bir davpr sepet, genel API 'sine erişimi sınırlandırmak için ağ sınırını kullanır.</span><span class="sxs-lookup"><span data-stu-id="62038-219">By default, a Dapr sidecar relies on the network boundary to limit access to its public API.</span></span> <span data-ttu-id="62038-220">Bu nedenle, **https Için yapılandırma** onay kutusunu temizleyin.</span><span class="sxs-lookup"><span data-stu-id="62038-220">Therefore, clear the checkbox for **Configure for HTTPS**.</span></span>

   ![Web API 'sini oluşturma ekran görüntüsü](./media/getting-started/multicontainer-createwebapi.png)

### <a name="add-dapr-service-invocation"></a><span data-ttu-id="62038-222">Davpr hizmeti çağrısı Ekle</span><span class="sxs-lookup"><span data-stu-id="62038-222">Add Dapr service invocation</span></span>

<span data-ttu-id="62038-223">Şimdi, Davpr [hizmet çağırma yapı](https://docs.dapr.io/developing-applications/building-blocks/service-invocation/service-invocation-overview/)taşı kullanan hizmetler arasındaki iletişimi yapılandıracaksınız.</span><span class="sxs-lookup"><span data-stu-id="62038-223">Now, you'll configure communication between the services using Dapr [service invocation building block](https://docs.dapr.io/developing-applications/building-blocks/service-invocation/service-invocation-overview/).</span></span> <span data-ttu-id="62038-224">Web API 'sinden Hava durumu tahminlerini almak için Web uygulamasını etkinleştireceksiniz.</span><span class="sxs-lookup"><span data-stu-id="62038-224">You'll enable the  web app to retrieve weather forecasts from the  web API.</span></span> <span data-ttu-id="62038-225">Hizmet çağırma oluşturma bloğu birçok avantaj sunar.</span><span class="sxs-lookup"><span data-stu-id="62038-225">The service invocation building block features many benefits.</span></span> <span data-ttu-id="62038-226">Hizmet bulma, otomatik yeniden denemeler, ileti şifreleme (mTLS kullanarak) ve geliştirilmiş Observability içerir.</span><span class="sxs-lookup"><span data-stu-id="62038-226">It includes service discovery, automatic retries, message encryption (using mTLS), and improved observability.</span></span> <span data-ttu-id="62038-227">Davpr sidecar üzerinde hizmet çağırma API 'sini çağırmak için, Davpr .NET SDK 'sını kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="62038-227">You'll use the Dapr .NET SDK to invoke the service invocation API on the Dapr sidecar.</span></span>

1. <span data-ttu-id="62038-228">Visual Studio 'da Paket Yöneticisi konsolunu (**araçlar > NuGet paket yöneticisi > Paket Yöneticisi konsolu**) açın ve bunun varsayılan proje olduğundan emin olun `DaprFrontEnd` .</span><span class="sxs-lookup"><span data-stu-id="62038-228">In Visual Studio, open the Package Manager Console (**Tools > NuGet Package Manager > Package Manager Console**) and make sure that `DaprFrontEnd` is the default project.</span></span> <span data-ttu-id="62038-229">Konsolundan `Dapr.AspNetCore` NuGet paketini projeye ekleyin:</span><span class="sxs-lookup"><span data-stu-id="62038-229">From the console, add the `Dapr.AspNetCore` NuGet package to the project:</span></span>

   ```powershell
   Install-Package Dapr.AspNetCore
   ```

   > [!NOTE]
   > <span data-ttu-id="62038-230">Uygulamasının ön sürümde olan bir sürümünü hedefliyorsanız `Dapr.AspNetCore` , bayrağını belirtmeniz gerekir `-Prerelease` .</span><span class="sxs-lookup"><span data-stu-id="62038-230">If you're targeting a version of `Dapr.AspNetCore` that is in prerelease, you need to specify the `-Prerelease` flag.</span></span>

1. <span data-ttu-id="62038-231">Projesinde, `DaprFrontEnd` *Startup.cs* dosyasını açın ve `ConfigureServices` yöntemi aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="62038-231">In the `DaprFrontEnd` project, open the *Startup.cs* file, and replace the `ConfigureServices` method with the following code:</span></span>

   ```csharp
   // This method gets called by the runtime. Use this method to add services to the container.
   public void ConfigureServices(IServiceCollection services)
   {
       services.AddControllers().AddDapr();
       services.AddRazorPages();
   }
   ```

   <span data-ttu-id="62038-232">' A çağrı, `AddDapr` `DaprClient` ASP.NET Core bağımlılık ekleme sistemiyle birlikte kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="62038-232">The call to `AddDapr` registers the `DaprClient` class with the ASP.NET Core dependency injection system.</span></span> <span data-ttu-id="62038-233">Bu `DaprClient` sınıfı daha sonra, Davpr sidecar ile iletişim kurmak için kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="62038-233">You'll use the `DaprClient` class later on to communicate with the Dapr sidecar.</span></span>

1. <span data-ttu-id="62038-234">Projeye *dalgalı tahmin tahmini* adlı yeni bir C# sınıf dosyası ekleyin `DaprFrontEnd` :</span><span class="sxs-lookup"><span data-stu-id="62038-234">Add a new C# class file named *WeatherForecast* to the `DaprFrontEnd` project:</span></span>

   ```csharp
   using System;
      
   namespace DaprFrontEnd
   {
       public class WeatherForecast
       {
           public DateTime Date { get; set; }
      
           public int TemperatureC { get; set; }
      
           public int TemperatureF { get; set; }
      
           public string Summary { get; set; }
       }
   }
   ```

1. <span data-ttu-id="62038-235">*Sayfalar* klasöründe *Index.cshtml.cs* dosyasını açın ve içeriğini şu kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="62038-235">Open the *Index.cshtml.cs* file in the *Pages* folder, and replace its contents with the following code:</span></span>

   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Net.Http;
   using System.Threading.Tasks;
   using Dapr.Client;
   using Microsoft.AspNetCore.Mvc.RazorPages;

   namespace DaprFrontEnd.Pages
   {
       public class IndexModel : PageModel
       {
           private readonly DaprClient _daprClient;

           public IndexModel(DaprClient daprClient)
           {
               _daprClient = daprClient ?? throw new ArgumentNullException(nameof(daprClient));
           }

           public async Task OnGet()
           {
               var forecasts = await _daprClient.InvokeMethodAsync<IEnumerable<WeatherForecast>>(
                   HttpMethod.Get,
                   "daprbackend",
                   "weatherforecast");

               ViewData["WeatherForecastData"] = forecasts;
           }
       }
   }
   ```

   <span data-ttu-id="62038-236">Ekleme sınıfını oluşturucuya ekleyerek, Web uygulamasına Davpr özellikleri ekleyin `DaprClient` `IndexModel` .</span><span class="sxs-lookup"><span data-stu-id="62038-236">You add Dapr capabilities into the  web app by injecting the `DaprClient` class into `IndexModel` constructor.</span></span> <span data-ttu-id="62038-237">`OnGet`Yönteminde, API hizmetini Davpr hizmet çağırma yapı taşı ile çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62038-237">In the `OnGet` method, you call the  API service with the Dapr service invocation building block.</span></span> <span data-ttu-id="62038-238">`OnGet`Yöntemi, bir kullanıcı giriş sayfasını ziyaret ettiğinde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="62038-238">The `OnGet` method is invoked whenever a user visits the home page.</span></span> <span data-ttu-id="62038-239">`DaprClient.InvokeMethodAsync`Yöntemi, hizmetin yöntemini çağırmak için kullanılır `weatherforecast` `daprbackend` .</span><span class="sxs-lookup"><span data-stu-id="62038-239">You use the `DaprClient.InvokeMethodAsync` method to invoke the `weatherforecast` method of the `daprbackend` service.</span></span> <span data-ttu-id="62038-240">Web API 'sini, `daprbackend` uygulama kimliği olarak kullanmak üzere bir daha sonra, bu uygulamayı, Davpr ile çalışacak şekilde yapılandırırken yapılandıracaksınız.</span><span class="sxs-lookup"><span data-stu-id="62038-240">You'll configure the  web API to use `daprbackend` as its application id later on when configuring it to run with Dapr.</span></span> <span data-ttu-id="62038-241">Son olarak, hizmet yanıtı Görünüm verilerini içine kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="62038-241">Finally, the service response is saved in view data.</span></span>

1. <span data-ttu-id="62038-242">*Sayfalar* klasöründeki *Index. cshtml* dosyasının içeriğini aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="62038-242">Replace the contents of the *Index.cshtml* file in the *Pages* folder, with the following code.</span></span> <span data-ttu-id="62038-243">Görüntüleme verilerinde depolanan Hava durumu tahminlerini kullanıcıya görüntüler:</span><span class="sxs-lookup"><span data-stu-id="62038-243">It displays the weather forecasts stored in the view data to the user:</span></span>

   ```html
   @page
   @model IndexModel
   @{
       ViewData["Title"] = "Home page";
   }
   
   <div class="text-center">
       <h1 class="display-4">Welcome</h1>
       <p>Learn about <a href="https://docs.microsoft.com/aspnet/core">building Web apps with ASP.NET Core</a>.</p>
       @foreach (var forecast in (IEnumerable<WeatherForecast>)ViewData["WeatherForecastData"])
       {
           <p>The forecast for @forecast.Date is @forecast.Summary!</p>
       }
   </div>
   ```

### <a name="add-container-support"></a><span data-ttu-id="62038-244">Kapsayıcı desteği ekle</span><span class="sxs-lookup"><span data-stu-id="62038-244">Add container support</span></span>

<span data-ttu-id="62038-245">Bu örneğin son bölümünde kapsayıcı desteği ekleyecek ve Docker Compose kullanarak çözümü çalıştıracaksınız.</span><span class="sxs-lookup"><span data-stu-id="62038-245">In the final part of this example, you'll add container support and run the solution using Docker Compose.</span></span>

1. <span data-ttu-id="62038-246">Projeye sağ tıklayın `DaprFrontEnd` ve **> kapsayıcı Orchestrator desteği ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="62038-246">Right-click the `DaprFrontEnd` project, and choose **Add > Container Orchestrator Support**.</span></span> <span data-ttu-id="62038-247">**Kapsayıcı Orchestrator desteği ekle** iletişim kutusu görünür:</span><span class="sxs-lookup"><span data-stu-id="62038-247">The **Add Container Orchestrator Support** dialog appears:</span></span>

   ![Kapsayıcı Orchestrator desteği ekleme ekran görüntüsü](./media/getting-started/multicontainer-addorchestrator.png)

   <span data-ttu-id="62038-249">**Docker Compose** seçin.</span><span class="sxs-lookup"><span data-stu-id="62038-249">Choose **Docker Compose**.</span></span>

1. <span data-ttu-id="62038-250">Sonraki iletişim kutusunda, hedef işletim sistemi olarak **Linux** ' u seçin:</span><span class="sxs-lookup"><span data-stu-id="62038-250">In the next dialog, select **Linux** as the Target OS:</span></span>

   ![Docker hedef işletim sistemini seçme ekran görüntüsü](./media/getting-started/multicontainer-targetos.png)

   <span data-ttu-id="62038-252">Visual Studio, çözümdeki **Docker-Compose** klasöründe bir *Docker-Compose. yml* dosyası ve bir *. dockerıgnore* dosyası oluşturur:</span><span class="sxs-lookup"><span data-stu-id="62038-252">Visual Studio creates a *docker-compose.yml* file and a *.dockerignore* file in the **docker-compose** folder in the solution:</span></span>

   ![Docker-Compose projesinin ekran görüntüsü](./media/getting-started/multicontainer-dockersolution.png)

   <span data-ttu-id="62038-254">*Docker-Compose. yml* dosyası aşağıdaki içeriğe sahiptir:</span><span class="sxs-lookup"><span data-stu-id="62038-254">The *docker-compose.yml* file has the following content:</span></span>

   ```yaml
   version: '3.4'
   
   services:
     daprfrontend:
       image: ${DOCKER_REGISTRY-}daprfrontend
       build:
         context: .
         dockerfile: DaprFrontEnd/Dockerfile
   
   ```

   <span data-ttu-id="62038-255">*. Dockerıgnore* dosyası, Docker 'ın kapsayıcıya dahil etmesini istemediğiniz dosya türlerini ve uzantılarını içerir.</span><span class="sxs-lookup"><span data-stu-id="62038-255">The *.dockerignore* file contains file types and extensions that you don't want Docker to include in the container.</span></span> <span data-ttu-id="62038-256">Bu dosyalar geliştirme ortamı ve kaynak denetimiyle ilişkilendirilir ve dağıttığınız uygulama veya hizmetten değildir.</span><span class="sxs-lookup"><span data-stu-id="62038-256">These files are associated with the development environment and source control and not the app or service you're deploying.</span></span>

1. <span data-ttu-id="62038-257">`DaprBackEnd`Web API projesinde, proje düğümüne sağ tıklayın ve   >  **kapsayıcı Orchestrator desteği** Ekle ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="62038-257">In the `DaprBackEnd` web API project, right-click on the project node, and choose **Add** > **Container Orchestrator Support**.</span></span> <span data-ttu-id="62038-258">**Docker Compose** öğesini seçin ve ardından hedef işletim sistemi olarak **Linux** ' u yeniden seçin.</span><span class="sxs-lookup"><span data-stu-id="62038-258">Choose **Docker Compose**, and then select **Linux** again as the target OS.</span></span>

   <span data-ttu-id="62038-259">*Docker-Compose. yıml* dosyasını yeniden açın ve içeriğini inceleyin.</span><span class="sxs-lookup"><span data-stu-id="62038-259">Open the *docker-compose.yml* file again and examine its contents.</span></span> <span data-ttu-id="62038-260">Visual Studio Docker Compose dosyasını günceletti.</span><span class="sxs-lookup"><span data-stu-id="62038-260">Visual Studio has update the Docker Compose file.</span></span> <span data-ttu-id="62038-261">Artık her iki hizmet de dahil edilmiştir:</span><span class="sxs-lookup"><span data-stu-id="62038-261">Now both services are included:</span></span>

   ```yaml
   version: '3.4'
   
   services:
     daprfrontend:
       image: ${DOCKER_REGISTRY-}daprfrontend
       build:
         context: .
         dockerfile: DaprFrontEnd/Dockerfile
   
     daprbackend:
       image: ${DOCKER_REGISTRY-}daprbackend
       build:
         context: .
         dockerfile: DaprBackEnd/Dockerfile
   ```

1. <span data-ttu-id="62038-262">Kapsayıcılı bir uygulamanın içinden Davpr yapı taşlarını kullanmak için, oluşturma dosyanıza Davpr sıdecars kapsayıcıları eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="62038-262">To use Dapr building blocks from inside a containerized application, you'll need to add the Dapr sidecars containers to your Compose file.</span></span> <span data-ttu-id="62038-263">*Docker-Compose. yıml* dosyasının içeriğini aşağıdaki örnekle eşleşecek şekilde dikkatle güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="62038-263">Carefully update the content of the *docker-compose.yml* file to match the following example.</span></span> <span data-ttu-id="62038-264">Biçimlendirme ve aralığa yakın bir ilgi ödeyin ve sekmeleri kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="62038-264">Pay close attention to the formatting and spacing and don't use tabs.</span></span>

   ```yaml
   version: '3.4'
   
   services:
     daprfrontend:
       image: ${DOCKER_REGISTRY-}daprfrontend
       build:
         context: .
         dockerfile: DaprFrontEnd/Dockerfile
       ports:
         - "51000:50001" 
   
     daprfrontend-dapr:
       image: "daprio/daprd:latest"
       command: [ "./daprd", "-app-id", "daprfrontend", "-app-port", "80" ]
       depends_on:
         - daprfrontend
       network_mode: "service:daprfrontend"
   
     daprbackend:
       image: ${DOCKER_REGISTRY-}daprbackend
       build:
         context: .
         dockerfile: DaprBackEnd/Dockerfile
       ports:
         - "52000:50001"
   
     daprbackend-dapr:
       image: "daprio/daprd:latest"
       command: [ "./daprd", "-app-id", "daprbackend", "-app-port", "80" ]
       depends_on:
         - daprfrontend
       network_mode: "service:daprbackend" 
   ```

   <span data-ttu-id="62038-265">Güncelleştirilmiş dosyada, `daprfrontend-dapr` `daprbackend-dapr` `daprfrontend` ve `daprbackend` hizmetlerini sırasıyla ve hizmetleri için ekledik.</span><span class="sxs-lookup"><span data-stu-id="62038-265">In the updated file, we've added `daprfrontend-dapr` and `daprbackend-dapr` sidecars for the `daprfrontend` and `daprbackend` services respectively.</span></span> <span data-ttu-id="62038-266">Güncelleştirilmiş dosyada, aşağıdaki değişikliklere dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="62038-266">In the updated file, pay close attention to the following changes:</span></span>

   - <span data-ttu-id="62038-267">Sıfları `daprio/daprd:latest` kapsayıcı görüntüsünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="62038-267">The sidecars use the `daprio/daprd:latest` container image.</span></span> <span data-ttu-id="62038-268">Etiket kullanımı, `latest` Üretim senaryolarında önerilmez.</span><span class="sxs-lookup"><span data-stu-id="62038-268">The use of the `latest` tag isn't recommended for production scenarios.</span></span> <span data-ttu-id="62038-269">Üretim için belirli bir sürüm numarası kullanmak daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="62038-269">For production, it's better to use a specific version number.</span></span>
   - <span data-ttu-id="62038-270">Oluşturma dosyasında tanımlanan her bir hizmetin ağ yalıtımı amacıyla kendi ağ ad alanı vardır.</span><span class="sxs-lookup"><span data-stu-id="62038-270">Each service defined in the Compose file has its own network namespace for network isolation purposes.</span></span> <span data-ttu-id="62038-271">Bu kişilerin `network_mode: "service:..."` uygulamayla aynı ağ ad alanında çalıştırıldıklarından emin olmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="62038-271">The sidecars use `network_mode: "service:..."` to ensure they run in the same network namespace as the application.</span></span> <span data-ttu-id="62038-272">Bunun yapılması, dışarıdan ve uygulamanın kullanarak iletişim kurmasına izin verir `localhost` .</span><span class="sxs-lookup"><span data-stu-id="62038-272">Doing so allows the sidecar and the application to communicate using `localhost`.</span></span>
   - <span data-ttu-id="62038-273">Bapr kapsayıcınızı 'ın GRPC iletişimini dinlediği bağlantı noktaları (varsayılan olarak 50001), aynı kişilerin birbirleriyle iletişim kurmasına izin vermek için gösterilmelidir.</span><span class="sxs-lookup"><span data-stu-id="62038-273">The ports on which the Dapr sidecars are listening for gRPC communication (by default 50001) must be exposed to allow the sidecars to communicate with each other.</span></span>

1. <span data-ttu-id="62038-274">Çözümü, beklendiği gibi çalıştığını doğrulamak için çalıştırın (**F5** veya **CTRL + F5**).</span><span class="sxs-lookup"><span data-stu-id="62038-274">Run the solution (**F5** or **Ctrl+F5**) to verify that it works as expected.</span></span> <span data-ttu-id="62038-275">Her şey doğru yapılandırılmışsa, hava durumu tahmin verilerini görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="62038-275">If everything is configured correctly, you should see the weather forecast data:</span></span>

   ![Hava durumu tahmin verilerinin gösterildiği son çözümün ekran görüntüsü](./media/getting-started/multicontainer-result.png)

   <span data-ttu-id="62038-277">Docker Compose ve Visual Studio 2019 ile yerel olarak çalışırken, kesme noktaları ve hata ayıklama işlemlerini uygulamaya ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62038-277">Running locally with Docker Compose and Visual Studio 2019, you can set breakpoints and debug into the application.</span></span> <span data-ttu-id="62038-278">Üretim senaryolarında, uygulamanızın Kubernetes 'te barındırmasının yapılması önerilir.</span><span class="sxs-lookup"><span data-stu-id="62038-278">For production scenarios, it's recommended to host your application in Kubernetes.</span></span> <span data-ttu-id="62038-279">Bu kitap, Kubernetes 'e dağıtılacak betikleri içeren [Eshopondadpr](https://github.com/dotnet-architecture/eShopOnDapr)öğesine eşlik eden bir başvuru uygulaması içerir.</span><span class="sxs-lookup"><span data-stu-id="62038-279">This book includes an accompanying reference application, [eShopOnDapr](https://github.com/dotnet-architecture/eShopOnDapr), that contains scripts to deploy to Kubernetes.</span></span>

   <span data-ttu-id="62038-280">Bu kılavuzda kullanılan Davpr hizmet çağrısı yapı taşı hakkında daha fazla bilgi edinmek için [Bölüm 6](service-invocation.md)' ya başvurun.</span><span class="sxs-lookup"><span data-stu-id="62038-280">To learn more about the Dapr service invocation building block used in this walkthrough, refer to [chapter 6](service-invocation.md).</span></span>

## <a name="summary"></a><span data-ttu-id="62038-281">Özet</span><span class="sxs-lookup"><span data-stu-id="62038-281">Summary</span></span>

<span data-ttu-id="62038-282">Bu bölümde, dadpr *sürücüsünü test* etme fırsatınız vardı.</span><span class="sxs-lookup"><span data-stu-id="62038-282">In this chapter, you had an opportunity to *test drive* Dapr.</span></span> <span data-ttu-id="62038-283">Davpr .NET SDK 'yı kullanarak, Davpr 'nin .NET uygulama platformu ile nasıl tümleştiğini gördünüz.</span><span class="sxs-lookup"><span data-stu-id="62038-283">Using the Dapr .NET SDK, you saw how Dapr integrates with the .NET application platform.</span></span>

<span data-ttu-id="62038-284">İlk örnek, Davpr durum yönetimi oluşturma bloğunu kullanan basit ve durum bilgisi olan bir .NET konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="62038-284">The first example was a simple, stateful, .NET Console application that used the Dapr state management building block.</span></span>

<span data-ttu-id="62038-285">İkinci örnek, Docker 'da çalışan çok kapsayıcılı bir uygulama ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="62038-285">The second example involved a multi-container application running in Docker.</span></span> <span data-ttu-id="62038-286">Visual Studio 'Yu Docker Compose kullanarak tüm .NET uygulamalarında sunulan tanıdık *F5 hata ayıklama deneyimiyle* karşılaşmış olursunuz.</span><span class="sxs-lookup"><span data-stu-id="62038-286">By using Visual Studio with Docker Compose, you experienced the familiar *F5 debugging experience* available across all .NET apps.</span></span>

<span data-ttu-id="62038-287">Ayrıca, Bapr bileşen yapılandırma dosyalarına daha yakından bakalım.</span><span class="sxs-lookup"><span data-stu-id="62038-287">You also got a closer look at Dapr component configuration files.</span></span> <span data-ttu-id="62038-288">Bunlar, Davpr yapı taşları tarafından kullanılan gerçek altyapı uygulamasını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="62038-288">They configure the actual infrastructure implementation used by the Dapr building blocks.</span></span> <span data-ttu-id="62038-289">Belirli ortamlara ve uygulamalara bileşen erişimini kısıtlamak için ad alanlarını ve kapsamları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62038-289">You can use namespaces and scopes to restrict component access to particular environments and applications.</span></span>

<span data-ttu-id="62038-290">Yaklaşan bölümlerde, Davpr tarafından sunulan yapı taşları hakkında ayrıntılı bilgi edineceksiniz.</span><span class="sxs-lookup"><span data-stu-id="62038-290">In the upcoming chapters, you'll dive deep into the building blocks offered by Dapr.</span></span>

### <a name="references"></a><span data-ttu-id="62038-291">Başvurular</span><span class="sxs-lookup"><span data-stu-id="62038-291">References</span></span>

- [<span data-ttu-id="62038-292">Davpr belgeleri-Başlarken</span><span class="sxs-lookup"><span data-stu-id="62038-292">Dapr documentation - Getting started</span></span>](https://docs.dapr.io/getting-started/)

- [<span data-ttu-id="62038-293">Eshopondadpr</span><span class="sxs-lookup"><span data-stu-id="62038-293">eShopOnDapr</span></span>](https://github.com/dotnet-architecture/eShopOnDapr)

> [!div class="step-by-step"]
> <span data-ttu-id="62038-294">[Önceki](dapr-at-20000-feet.md) 
>  [Sonraki](reference-application.md)</span><span class="sxs-lookup"><span data-stu-id="62038-294">[Previous](dapr-at-20000-feet.md)
[Next](reference-application.md)</span></span>
