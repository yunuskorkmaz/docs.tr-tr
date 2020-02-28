---
title: dotnet publish komutu
description: Dotnet publish komutu bir dizine .NET Core projesi veya çözümü yayımlar.
ms.date: 02/24/2020
ms.openlocfilehash: cf41ee09244faad03feb8ccda19135b8c7780106
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157006"
---
# <a name="dotnet-publish"></a><span data-ttu-id="b68a2-103">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="b68a2-103">dotnet publish</span></span>

<span data-ttu-id="b68a2-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="b68a2-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="b68a2-105">Adı</span><span class="sxs-lookup"><span data-stu-id="b68a2-105">Name</span></span>

<span data-ttu-id="b68a2-106">`dotnet publish`-uygulamayı ve bağımlılıklarını barındırma sistemine dağıtım için bir klasöre yayımlar.</span><span class="sxs-lookup"><span data-stu-id="b68a2-106">`dotnet publish` - Publishes the application and its dependencies to a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="b68a2-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="b68a2-107">Synopsis</span></span>

```dotnetcli
dotnet publish [<PROJECT>|<SOLUTION>] [-c|--configuration] 
    [-f|--framework] [--force] [--interactive] [--manifest]
    [--no-build] [--no-dependencies] [--no-restore] [--nologo]
    [-o|--output] [-r|--runtime] [--self-contained]
    [--no-self-contained] [-v|--verbosity] [--version-suffix]

dotnet publish [-h|--help]
```

## <a name="description"></a><span data-ttu-id="b68a2-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b68a2-108">Description</span></span>

<span data-ttu-id="b68a2-109">`dotnet publish` uygulamayı derler, proje dosyasında belirtilen bağımlılıklarını okur ve elde edilen dosya kümesini bir dizine yayınlar.</span><span class="sxs-lookup"><span data-stu-id="b68a2-109">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="b68a2-110">Çıktı aşağıdaki varlıkları içerir:</span><span class="sxs-lookup"><span data-stu-id="b68a2-110">The output includes the following assets:</span></span>

- <span data-ttu-id="b68a2-111">*DLL* uzantılı bir derlemede ara DIL (IL) kodu.</span><span class="sxs-lookup"><span data-stu-id="b68a2-111">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
- <span data-ttu-id="b68a2-112">Projenin tüm bağımlılıklarını içeren bir *. Deps. JSON* dosyası.</span><span class="sxs-lookup"><span data-stu-id="b68a2-112">A *.deps.json* file that includes all of the dependencies of the project.</span></span>
- <span data-ttu-id="b68a2-113">Uygulamanın beklediği paylaşılan çalışma zamanını belirten *. runtimeconfig. JSON* dosyası ve çalışma zamanına yönelik diğer yapılandırma seçenekleri (örneğin, çöp toplama türü).</span><span class="sxs-lookup"><span data-stu-id="b68a2-113">A *.runtimeconfig.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
- <span data-ttu-id="b68a2-114">NuGet önbelleğinden çıkış klasörüne kopyalanmış olan uygulamanın bağımlılıkları.</span><span class="sxs-lookup"><span data-stu-id="b68a2-114">The application's dependencies, which are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="b68a2-115">`dotnet publish` komutun çıktısı, yürütme için bir barındırma sistemine (örneğin, bir sunucu, PC, Mac, dizüstü bilgisayar) dağıtıma yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="b68a2-115">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution.</span></span> <span data-ttu-id="b68a2-116">Uygulamayı dağıtıma hazırlamak için tek resmi olarak desteklenen bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="b68a2-116">It's the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="b68a2-117">Projenin belirttiği dağıtımın türüne bağlı olarak, barındırma sisteminde .NET Core paylaşılan çalışma zamanı yüklü olabilir veya olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="b68a2-117">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span>

## <a name="arguments"></a><span data-ttu-id="b68a2-118">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="b68a2-118">Arguments</span></span>

- **`PROJECT|SOLUTION`**

  <span data-ttu-id="b68a2-119">Yayımlanacak proje veya çözüm.</span><span class="sxs-lookup"><span data-stu-id="b68a2-119">The project or solution to publish.</span></span>
  
  * <span data-ttu-id="b68a2-120">`PROJECT`, veya Visual Basic proje dosyasının yolu ve [C#](csproj.md)dosya F#adıdır ya da C#, F#veya Visual Basic proje dosyası içeren bir dizinin yoludur.</span><span class="sxs-lookup"><span data-stu-id="b68a2-120">`PROJECT` is the path and filename of a [C#](csproj.md), F#, or Visual Basic project file, or the path to a directory that contains a C#, F#, or Visual Basic project file.</span></span> <span data-ttu-id="b68a2-121">Dizin belirtilmemişse, varsayılan olarak geçerli dizine ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="b68a2-121">If the directory is not specified, it defaults to the current directory.</span></span>

  * <span data-ttu-id="b68a2-122">`SOLUTION`, bir çözüm dosyasının ( *. sln* uzantısının) yolu ve dosya adıdır veya çözüm dosyası içeren bir dizinin yoludur.</span><span class="sxs-lookup"><span data-stu-id="b68a2-122">`SOLUTION` is the path and filename of a solution file (*.sln* extension), or the path to a directory that contains a solution file.</span></span> <span data-ttu-id="b68a2-123">Dizin belirtilmemişse, varsayılan olarak geçerli dizine ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="b68a2-123">If the directory is not specified, it defaults to the current directory.</span></span> <span data-ttu-id="b68a2-124">**.NET Core 3,0 SDK ile başlayarak kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="b68a2-124">**Available starting with .NET Core 3.0 SDK.**</span></span> 

## <a name="options"></a><span data-ttu-id="b68a2-125">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="b68a2-125">Options</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="b68a2-126">Yapı yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b68a2-126">Defines the build configuration.</span></span> <span data-ttu-id="b68a2-127">Çoğu proje için varsayılan değer `Debug`, ancak projenizde derleme yapılandırma ayarlarını geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b68a2-127">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="b68a2-128">Belirtilen [hedef çerçeve](../../standard/frameworks.md)için uygulamayı yayımlar.</span><span class="sxs-lookup"><span data-stu-id="b68a2-128">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="b68a2-129">Hedef çerçeveyi proje dosyasında belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b68a2-129">You must specify the target framework in the project file.</span></span>

- **`--force`**

  <span data-ttu-id="b68a2-130">Son geri yükleme başarılı olsa bile tüm bağımlılıkların çözülmesini zorlar.</span><span class="sxs-lookup"><span data-stu-id="b68a2-130">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="b68a2-131">Bu bayrağın belirtilmesi, *Project. varlıklar. JSON* dosyasını silme ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="b68a2-131">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="b68a2-132">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="b68a2-132">Prints out a short help for the command.</span></span>

- <span data-ttu-id="b68a2-133">**`--interactive`** **.NET Core 3,0 SDK ile başlayarak kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="b68a2-133">**`--interactive`** **Available starting with .NET Core 3.0 SDK.**</span></span>

  <span data-ttu-id="b68a2-134">Komutun Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="b68a2-134">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="b68a2-135">Örneğin, kimlik doğrulamasını tamamlamaya yönelik.</span><span class="sxs-lookup"><span data-stu-id="b68a2-135">For example, to complete authentication.</span></span> 

- **`--manifest <PATH_TO_MANIFEST_FILE>`**

  <span data-ttu-id="b68a2-136">Uygulamayla yayımlanmış paket kümesini kırpmak için kullanılacak bir veya birkaç [hedef bildirimi](../deploying/runtime-store.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="b68a2-136">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="b68a2-137">Bildirim dosyası [`dotnet store` komutunun](dotnet-store.md)çıktısının bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="b68a2-137">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="b68a2-138">Birden çok bildirim belirtmek için her bildirim için bir `--manifest` seçeneği ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b68a2-138">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span>

- **`--no-build`**

  <span data-ttu-id="b68a2-139">Yayımlamadan önce projeyi oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="b68a2-139">Doesn't build the project before publishing.</span></span> <span data-ttu-id="b68a2-140">Ayrıca `--no-restore` bayrağını örtülü olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b68a2-140">It also implicitly sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="b68a2-141">Projeden projeye başvuruları yoksayar ve yalnızca kök projeyi geri yükler.</span><span class="sxs-lookup"><span data-stu-id="b68a2-141">Ignores project-to-project references and only restores the root project.</span></span>

- <span data-ttu-id="b68a2-142">**`--nologo`** **.NET Core 3,0 SDK ile başlayarak kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="b68a2-142">**`--nologo`** **Available starting with .NET Core 3.0 SDK.**</span></span>

  <span data-ttu-id="b68a2-143">Başlangıç başlığını veya telif hakkı iletisini görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="b68a2-143">Doesn't display the startup banner or the copyright message.</span></span> 

- **`--no-restore`**

  <span data-ttu-id="b68a2-144">Komutu çalıştırılırken örtük geri yükleme yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="b68a2-144">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="b68a2-145">Çıkış dizini için yolu belirtir.</span><span class="sxs-lookup"><span data-stu-id="b68a2-145">Specifies the path for the output directory.</span></span> <span data-ttu-id="b68a2-146">Belirtilmemişse, çalışma zamanına bağlı bir yürütülebilir dosya ve platformlar arası ikili dosyalar için *./bin/[Configuration]/[Framework]/Publish/* varsayılan değeri.</span><span class="sxs-lookup"><span data-stu-id="b68a2-146">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a runtime-dependent executable and cross-platform binaries.</span></span> <span data-ttu-id="b68a2-147">Otomatik olarak içerilen bir yürütülebilir dosya için *./bin/[Configuration]/[Framework]/[Runtime]/Publish/* varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="b68a2-147">It defaults to *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained executable.</span></span>

  <span data-ttu-id="b68a2-148">Yol göreli ise, oluşturulan çıkış dizini geçerli çalışma dizinine değil, proje dosyası konumuna göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="b68a2-148">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

- **`--self-contained [true|false]`**

  <span data-ttu-id="b68a2-149">.NET Core çalışma zamanını uygulamanızla yayımlar, böylece çalışma zamanının hedef makinede yüklü olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="b68a2-149">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="b68a2-150">Bir çalışma zamanı tanımlayıcısı belirtilmişse varsayılan `true`.</span><span class="sxs-lookup"><span data-stu-id="b68a2-150">Default is `true` if a runtime identifier is specified.</span></span> <span data-ttu-id="b68a2-151">Daha fazla bilgi için bkz. [.NET Core uygulaması yayımlama](../deploying/index.md) ve [.NET Core CLI .NET Core uygulamaları](../deploying/deploy-with-cli.md)yayımlama.</span><span class="sxs-lookup"><span data-stu-id="b68a2-151">For more information, see [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

- <span data-ttu-id="b68a2-152">**`--no-self-contained`** **.NET Core 3,0 SDK ile başlayarak kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="b68a2-152">**`--no-self-contained`**  **Available starting with .NET Core 3.0 SDK.**</span></span>

  <span data-ttu-id="b68a2-153">`--self-contained false`eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="b68a2-153">Equivalent to `--self-contained false`.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="b68a2-154">Uygulamayı belirli bir çalışma zamanı için yayımlar.</span><span class="sxs-lookup"><span data-stu-id="b68a2-154">Publishes the application for a given runtime.</span></span> <span data-ttu-id="b68a2-155">Çalışma zamanı tanımlayıcıları (RID 'Ler) listesi için bkz. [RID kataloğu](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="b68a2-155">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="b68a2-156">Daha fazla bilgi için bkz. [.NET Core uygulaması yayımlama](../deploying/index.md) ve [.NET Core CLI .NET Core uygulamaları](../deploying/deploy-with-cli.md)yayımlama.</span><span class="sxs-lookup"><span data-stu-id="b68a2-156">For more information, see [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="b68a2-157">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b68a2-157">Sets the verbosity level of the command.</span></span> <span data-ttu-id="b68a2-158">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="b68a2-158">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="b68a2-159">Proje dosyasının sürüm alanındaki yıldız işaretini (`*`) değiştirecek sürüm sonekini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b68a2-159">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

## <a name="examples"></a><span data-ttu-id="b68a2-160">Örnekler</span><span class="sxs-lookup"><span data-stu-id="b68a2-160">Examples</span></span>

- <span data-ttu-id="b68a2-161">Geçerli dizindeki proje için [çalışma zamanına bağımlı platformlar arası ikili](../deploying/index.md#produce-a-cross-platform-binary) oluşturun:</span><span class="sxs-lookup"><span data-stu-id="b68a2-161">Create a [runtime-dependent cross-platform binary](../deploying/index.md#produce-a-cross-platform-binary) for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet publish
  ```

  <span data-ttu-id="b68a2-162">.NET Core 3,0 SDK ile başlayarak bu örnek ayrıca geçerli platform için [çalışma zamanına bağlı bir yürütülebilir dosya](../deploying/index.md#publish-runtime-dependent) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b68a2-162">Starting with .NET Core 3.0 SDK, this example also creates a [runtime-dependent executable](../deploying/index.md#publish-runtime-dependent) for the current platform.</span></span>

- <span data-ttu-id="b68a2-163">Belirli bir çalışma zamanı için geçerli dizindeki proje için [kendi kendine içerilen bir yürütülebilir dosya](../deploying/index.md#publish-self-contained) oluşturun:</span><span class="sxs-lookup"><span data-stu-id="b68a2-163">Create a [self-contained executable](../deploying/index.md#publish-self-contained) for the project in the current directory, for a specific runtime:</span></span>

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64
  ```

  <span data-ttu-id="b68a2-164">RID proje dosyasında olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b68a2-164">The RID must be in the project file.</span></span>

- <span data-ttu-id="b68a2-165">Belirli bir platform için geçerli dizindeki proje için [çalışma zamanına bağımlı bir yürütülebilir dosya](../deploying/index.md#publish-runtime-dependent) oluşturun:</span><span class="sxs-lookup"><span data-stu-id="b68a2-165">Create a [runtime-dependent executable](../deploying/index.md#publish-runtime-dependent) for the project in the current directory, for a specific platform:</span></span>

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64 --self-contained false
  ```

  <span data-ttu-id="b68a2-166">RID proje dosyasında olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b68a2-166">The RID must be in the project file.</span></span> <span data-ttu-id="b68a2-167">Bu örnek .NET Core 3,0 SDK ve sonraki sürümleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b68a2-167">This example applies to .NET Core 3.0 SDK and later versions.</span></span>

- <span data-ttu-id="b68a2-168">Projeyi, belirli bir çalışma zamanı ve hedef çerçeve için geçerli dizinde yayımlayın:</span><span class="sxs-lookup"><span data-stu-id="b68a2-168">Publish the project in the current directory, for a specific runtime and target framework:</span></span>

  ```dotnetcli
  dotnet publish --framework netcoreapp3.1 --runtime osx.10.11-x64
  ```

- <span data-ttu-id="b68a2-169">Belirtilen proje dosyasını Yayımla:</span><span class="sxs-lookup"><span data-stu-id="b68a2-169">Publish the specified project file:</span></span>

  ```dotnetcli
  dotnet publish ~/projects/app1/app1.csproj
  ```

- <span data-ttu-id="b68a2-170">Geçerli uygulamayı yayımlayın ancak projeden projeye (P2P) başvurularını geri yüklemeyin, ancak geri yükleme işlemi sırasında yalnızca kök proje:</span><span class="sxs-lookup"><span data-stu-id="b68a2-170">Publish the current application but don't restore project-to-project (P2P) references, just the root project during the restore operation:</span></span>

  ```dotnetcli
  dotnet publish --no-dependencies
  ```

## <a name="see-also"></a><span data-ttu-id="b68a2-171">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b68a2-171">See also</span></span>

- [<span data-ttu-id="b68a2-172">.NET Core uygulama yayımlamaya genel bakış</span><span class="sxs-lookup"><span data-stu-id="b68a2-172">.NET Core application publishing overview</span></span>](../deploying/index.md)
- [<span data-ttu-id="b68a2-173">.NET Core CLI .NET Core uygulamaları yayımlayın</span><span class="sxs-lookup"><span data-stu-id="b68a2-173">Publish .NET Core apps with the .NET Core CLI</span></span>](../deploying/deploy-with-cli.md)
- [<span data-ttu-id="b68a2-174">Hedef çerçeveler</span><span class="sxs-lookup"><span data-stu-id="b68a2-174">Target frameworks</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="b68a2-175">Çalışma zamanı tanımlayıcı (RID) kataloğu</span><span class="sxs-lookup"><span data-stu-id="b68a2-175">Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
- <span data-ttu-id="b68a2-176">[MacOS Catalina notarle çalışma](../install/macos-notarization-issues.md) Daha fazla bilgi için aşağıdaki kaynaklara bakın:</span><span class="sxs-lookup"><span data-stu-id="b68a2-176">[Working with macOS Catalina Notarization](../install/macos-notarization-issues.md) For more information, see he following resources:</span></span>
- [<span data-ttu-id="b68a2-177">Yayımlanan bir uygulamanın dizin yapısı</span><span class="sxs-lookup"><span data-stu-id="b68a2-177">Directory structure of a published application</span></span>](/aspnet/core/hosting/directory-structure)
