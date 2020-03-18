---
title: dotnet yayımlama komutu
description: Dotnet yayımlama komutu bir .NET Core projesi veya çözüm bir dizine yayımlar.
ms.date: 02/24/2020
ms.openlocfilehash: c34618409c9a539043c84c7e03daa8aa249d64f6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146561"
---
# <a name="dotnet-publish"></a><span data-ttu-id="cd4d2-103">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="cd4d2-103">dotnet publish</span></span>

<span data-ttu-id="cd4d2-104">**Bu makale şu şekilde dir:** ✔️ .NET Core 2.1 SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="cd4d2-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="cd4d2-105">Adı</span><span class="sxs-lookup"><span data-stu-id="cd4d2-105">Name</span></span>

<span data-ttu-id="cd4d2-106">`dotnet publish`- Uygulama ve bağımlılıklarını barındırma sistemine dağıtım için bir klasöre yayımlar.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-106">`dotnet publish` - Publishes the application and its dependencies to a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="cd4d2-107">Özet</span><span class="sxs-lookup"><span data-stu-id="cd4d2-107">Synopsis</span></span>

```dotnetcli
dotnet publish [<PROJECT>|<SOLUTION>] [-c|--configuration]
    [-f|--framework] [--force] [--interactive] [--manifest]
    [--no-build] [--no-dependencies] [--no-restore] [--nologo]
    [-o|--output] [-r|--runtime] [--self-contained]
    [--no-self-contained] [-v|--verbosity] [--version-suffix]

dotnet publish [-h|--help]
```

## <a name="description"></a><span data-ttu-id="cd4d2-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cd4d2-108">Description</span></span>

<span data-ttu-id="cd4d2-109">`dotnet publish`uygulamayı derler, proje dosyasında belirtilen bağımlılıkları okur ve ortaya çıkan dosya kümesini bir dizine yayınlar.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-109">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="cd4d2-110">Çıktı aşağıdaki varlıkları içerir:</span><span class="sxs-lookup"><span data-stu-id="cd4d2-110">The output includes the following assets:</span></span>

- <span data-ttu-id="cd4d2-111">*Dll* uzantılı bir derlemede Ara Dil (IL) kodu.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-111">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
- <span data-ttu-id="cd4d2-112">Projenin tüm bağımlılıklarını içeren bir *.deps.json* dosyası.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-112">A *.deps.json* file that includes all of the dependencies of the project.</span></span>
- <span data-ttu-id="cd4d2-113">Uygulamanın beklediği paylaşılan çalışma süresini ve çalışma zamanı için diğer yapılandırma seçeneklerini (örneğin, çöp toplama türü) belirten bir *.runtimeconfig.json* dosyası.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-113">A *.runtimeconfig.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
- <span data-ttu-id="cd4d2-114">NuGet önbelleğinden çıktı klasörüne kopyalanan uygulamabağımlılıkları.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-114">The application's dependencies, which are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="cd4d2-115">Komutun `dotnet publish` çıktısı yürütme için bir barındırma sistemine (örneğin, bir sunucu, PC, Mac, dizüstü bilgisayar) dağıtım için hazırdır.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-115">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution.</span></span> <span data-ttu-id="cd4d2-116">Uygulamayı dağıtıma hazırlamak için resmi olarak desteklenen tek yol bu.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-116">It's the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="cd4d2-117">Projenin belirttiği dağıtım türüne bağlı olarak, barındırma sistemi .NET Core paylaşılan çalışma zamanı yüklü olabilir veya olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-117">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span>

## <a name="arguments"></a><span data-ttu-id="cd4d2-118">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="cd4d2-118">Arguments</span></span>

- **`PROJECT|SOLUTION`**

  <span data-ttu-id="cd4d2-119">Yayımlanmak için proje veya çözüm.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-119">The project or solution to publish.</span></span>
  
  * <span data-ttu-id="cd4d2-120">`PROJECT`[C#](csproj.md), F#veya Visual Basic proje dosyasının yolu ve dosya adı veya C#, F#veya Visual Basic proje dosyası içeren bir dizine giden yoldur.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-120">`PROJECT` is the path and filename of a [C#](csproj.md), F#, or Visual Basic project file, or the path to a directory that contains a C#, F#, or Visual Basic project file.</span></span> <span data-ttu-id="cd4d2-121">Dizin belirtilmemişse, geçerli dizine varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-121">If the directory is not specified, it defaults to the current directory.</span></span>

  * <span data-ttu-id="cd4d2-122">`SOLUTION`çözüm dosyasının *(.sln* uzantısı) veya çözüm dosyası içeren bir dizine giden yol ve dosya adıdır.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-122">`SOLUTION` is the path and filename of a solution file (*.sln* extension), or the path to a directory that contains a solution file.</span></span> <span data-ttu-id="cd4d2-123">Dizin belirtilmemişse, geçerli dizine varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-123">If the directory is not specified, it defaults to the current directory.</span></span> <span data-ttu-id="cd4d2-124">.NET Core 3.0 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-124">Available since .NET Core 3.0 SDK.</span></span>

## <a name="options"></a><span data-ttu-id="cd4d2-125">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="cd4d2-125">Options</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="cd4d2-126">Yapı yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-126">Defines the build configuration.</span></span> <span data-ttu-id="cd4d2-127">Çoğu proje için `Debug`varsayılan değer, ancak projenizdeki yapı yapılandırma ayarlarını geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-127">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="cd4d2-128">Belirtilen [hedef çerçeve](../../standard/frameworks.md)için uygulama yayımlar.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-128">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="cd4d2-129">Proje dosyasındaki hedef çerçeveyi belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-129">You must specify the target framework in the project file.</span></span>

- **`--force`**

  <span data-ttu-id="cd4d2-130">Son geri yükleme başarılı olsa bile tüm bağımlılıkları çözüme kavuşturmaya zorlar.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-130">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="cd4d2-131">Bu bayrağı *belirtmek, project.assets.json* dosyasını silmekle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-131">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="cd4d2-132">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-132">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="cd4d2-133">Komutun durmasını ve kullanıcı girişi veya eylemini beklemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-133">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="cd4d2-134">Örneğin, kimlik doğrulamasını tamamlamak için.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-134">For example, to complete authentication.</span></span> <span data-ttu-id="cd4d2-135">.NET Core 3.0 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-135">Available since .NET Core 3.0 SDK.</span></span>

- **`--manifest <PATH_TO_MANIFEST_FILE>`**

  <span data-ttu-id="cd4d2-136">Uygulamayla birlikte yayınlanan paket kümesini kırpmak için kullanılacak bir veya birkaç [hedef bildirimi](../deploying/runtime-store.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-136">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="cd4d2-137">Bildirim dosyası [ `dotnet store` komutun](dotnet-store.md)çıktısının bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-137">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="cd4d2-138">Birden çok bildirim belirtmek `--manifest` için, her bildirim için bir seçenek ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-138">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span>

- **`--no-build`**

  <span data-ttu-id="cd4d2-139">Yayımlamadan önce projeyi oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-139">Doesn't build the project before publishing.</span></span> <span data-ttu-id="cd4d2-140">Ayrıca bayrağı da `--no-restore` örtülü olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-140">It also implicitly sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="cd4d2-141">Projeden projeye başvuruları yoksa ve yalnızca kök projeyi geri yükler.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-141">Ignores project-to-project references and only restores the root project.</span></span>

- **`--nologo`**

  <span data-ttu-id="cd4d2-142">Başlangıç bayrağını veya telif hakkı iletisini görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-142">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="cd4d2-143">.NET Core 3.0 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-143">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="cd4d2-144">Komutu çalıştırırken örtük bir geri yükleme yürütmez.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-144">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="cd4d2-145">Çıktı dizininin yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-145">Specifies the path for the output directory.</span></span> <span data-ttu-id="cd4d2-146">Belirtilmemişse, çalışma süresine bağlı yürütülebilir ve çapraz platform ikilileri için *./bin/[configuration]/[framework]/publish/* varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-146">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a runtime-dependent executable and cross-platform binaries.</span></span> <span data-ttu-id="cd4d2-147">Kendi kendine yeten bir yürütülebilir için *./bin/[configuration]/[framework]/[runtime]/[runtime]/publish/* olarak varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-147">It defaults to *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained executable.</span></span>

  <span data-ttu-id="cd4d2-148">Yol göreceliyse, oluşturulan çıktı dizini geçerli çalışma dizinine değil, proje dosyası konumuna göredir.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-148">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

- **`--self-contained [true|false]`**

  <span data-ttu-id="cd4d2-149">.NET Core çalışma zamanını uygulamanızla birlikte yayınlar, böylece çalışma süresinin hedef makineye yüklenmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-149">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="cd4d2-150">Varsayılan, `true` çalışma zamanı tanımlayıcısı belirtilmişse.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-150">Default is `true` if a runtime identifier is specified.</span></span> <span data-ttu-id="cd4d2-151">Daha fazla bilgi için [.NET Core uygulama yayımlama](../deploying/index.md) ve [.NET Core CLI ile .NET Core uygulamaları yayımlama](../deploying/deploy-with-cli.md)'ya bakın.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-151">For more information, see [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

- **`--no-self-contained`**

  <span data-ttu-id="cd4d2-152">`--self-contained false`Eşdeğeri .</span><span class="sxs-lookup"><span data-stu-id="cd4d2-152">Equivalent to `--self-contained false`.</span></span> <span data-ttu-id="cd4d2-153">.NET Core 3.0 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-153">Available since .NET Core 3.0 SDK.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="cd4d2-154">Belirli bir çalışma zamanı için uygulamayı yayımlar.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-154">Publishes the application for a given runtime.</span></span> <span data-ttu-id="cd4d2-155">Runtime Tanımlayıcıları (RID'ler) listesi için RID [kataloğuna](../rid-catalog.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-155">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="cd4d2-156">Daha fazla bilgi için [.NET Core uygulama yayımlama](../deploying/index.md) ve [.NET Core CLI ile .NET Core uygulamaları yayımlama](../deploying/deploy-with-cli.md)'ya bakın.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-156">For more information, see [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="cd4d2-157">Komutun ayrıntılı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-157">Sets the verbosity level of the command.</span></span> <span data-ttu-id="cd4d2-158">İzin verilen `q[uiet]` `m[inimal]`değerler `n[ormal]` `d[etailed]`, `diag[nostic]`, , , ve .</span><span class="sxs-lookup"><span data-stu-id="cd4d2-158">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="cd4d2-159">Varsayılan değer. `minimal`</span><span class="sxs-lookup"><span data-stu-id="cd4d2-159">Default value is `minimal`.</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="cd4d2-160">Proje dosyasının sürüm alanında yıldız işaretini`*`( ) değiştirmek için sürüm soneki tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-160">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

## <a name="examples"></a><span data-ttu-id="cd4d2-161">Örnekler</span><span class="sxs-lookup"><span data-stu-id="cd4d2-161">Examples</span></span>

- <span data-ttu-id="cd4d2-162">Geçerli dizinde proje için [çalışma süresine bağımlı çapraz platform ikilisi](../deploying/index.md#produce-a-cross-platform-binary) oluşturun:</span><span class="sxs-lookup"><span data-stu-id="cd4d2-162">Create a [runtime-dependent cross-platform binary](../deploying/index.md#produce-a-cross-platform-binary) for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet publish
  ```

  <span data-ttu-id="cd4d2-163">.NET Core 3.0 SDK ile başlayarak, bu örnek aynı zamanda geçerli platform için [çalıştırılabilir bir çalışma zamanı bağımlı](../deploying/index.md#publish-runtime-dependent) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-163">Starting with .NET Core 3.0 SDK, this example also creates a [runtime-dependent executable](../deploying/index.md#publish-runtime-dependent) for the current platform.</span></span>

- <span data-ttu-id="cd4d2-164">Belirli bir çalışma süresi için geçerli dizindeki proje için bağımsız bir [yürütülebilir](../deploying/index.md#publish-self-contained) oluşturun:</span><span class="sxs-lookup"><span data-stu-id="cd4d2-164">Create a [self-contained executable](../deploying/index.md#publish-self-contained) for the project in the current directory, for a specific runtime:</span></span>

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64
  ```

  <span data-ttu-id="cd4d2-165">RID proje dosyasında olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-165">The RID must be in the project file.</span></span>

- <span data-ttu-id="cd4d2-166">Belirli bir platform için geçerli dizindeki proje için [çalışma süresine bağlı yürütülebilir bir çalıştırılmaz](../deploying/index.md#publish-runtime-dependent) oluşturun:</span><span class="sxs-lookup"><span data-stu-id="cd4d2-166">Create a [runtime-dependent executable](../deploying/index.md#publish-runtime-dependent) for the project in the current directory, for a specific platform:</span></span>

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64 --self-contained false
  ```

  <span data-ttu-id="cd4d2-167">RID proje dosyasında olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-167">The RID must be in the project file.</span></span> <span data-ttu-id="cd4d2-168">Bu örnek .NET Core 3.0 SDK ve sonraki sürümler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-168">This example applies to .NET Core 3.0 SDK and later versions.</span></span>

- <span data-ttu-id="cd4d2-169">Belirli bir çalışma zamanı ve hedef çerçeve için projeyi geçerli dizinde yayımlayın:</span><span class="sxs-lookup"><span data-stu-id="cd4d2-169">Publish the project in the current directory, for a specific runtime and target framework:</span></span>

  ```dotnetcli
  dotnet publish --framework netcoreapp3.1 --runtime osx.10.11-x64
  ```

- <span data-ttu-id="cd4d2-170">Belirtilen proje dosyasını yayımlayın:</span><span class="sxs-lookup"><span data-stu-id="cd4d2-170">Publish the specified project file:</span></span>

  ```dotnetcli
  dotnet publish ~/projects/app1/app1.csproj
  ```

- <span data-ttu-id="cd4d2-171">Geçerli uygulamayı yayımlayın, ancak projeden projeye (P2P) başvurularını, yalnızca geri yükleme işlemi sırasındaki kök projeyi geri yüklemeyin:</span><span class="sxs-lookup"><span data-stu-id="cd4d2-171">Publish the current application but don't restore project-to-project (P2P) references, just the root project during the restore operation:</span></span>

  ```dotnetcli
  dotnet publish --no-dependencies
  ```

## <a name="see-also"></a><span data-ttu-id="cd4d2-172">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cd4d2-172">See also</span></span>

- [<span data-ttu-id="cd4d2-173">.NET Core uygulama yayıncılığı genel bakış</span><span class="sxs-lookup"><span data-stu-id="cd4d2-173">.NET Core application publishing overview</span></span>](../deploying/index.md)
- [<span data-ttu-id="cd4d2-174">.NET Core CLI ile .NET Core uygulamalarını yayımla</span><span class="sxs-lookup"><span data-stu-id="cd4d2-174">Publish .NET Core apps with the .NET Core CLI</span></span>](../deploying/deploy-with-cli.md)
- [<span data-ttu-id="cd4d2-175">Hedef çerçeveler</span><span class="sxs-lookup"><span data-stu-id="cd4d2-175">Target frameworks</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="cd4d2-176">Çalışma Zamanı Tanımlayıcı (RID) kataloğu</span><span class="sxs-lookup"><span data-stu-id="cd4d2-176">Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
- <span data-ttu-id="cd4d2-177">[macOS Catalina Noterizasyonu ile çalışma](../install/macos-notarization-issues.md) Daha fazla bilgi için aşağıdaki kaynaklara bakın:</span><span class="sxs-lookup"><span data-stu-id="cd4d2-177">[Working with macOS Catalina Notarization](../install/macos-notarization-issues.md) For more information, see he following resources:</span></span>
- [<span data-ttu-id="cd4d2-178">Yayınlanan bir uygulamanın dizin yapısı</span><span class="sxs-lookup"><span data-stu-id="cd4d2-178">Directory structure of a published application</span></span>](/aspnet/core/hosting/directory-structure)
