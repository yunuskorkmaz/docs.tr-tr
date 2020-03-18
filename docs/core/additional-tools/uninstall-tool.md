---
title: Aracı Kaldır
description: .NET Core SDK'ların ve çalışma saatlerinin kontrollü olarak temizlenmesini sağlayan kılavuzlu bir araç olan .NET Çekirdek Kaldırma Aracı'na genel bir bakış.
author: sfoslund
ms.date: 01/06/2020
ms.openlocfilehash: bd20cba133cbb754dcca48e48b76a391a9efacba
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847096"
---
# <a name="net-core-uninstall-tool"></a><span data-ttu-id="9027e-103">.NET Core Kaldırma Aracı</span><span class="sxs-lookup"><span data-stu-id="9027e-103">.NET Core Uninstall Tool</span></span>

<span data-ttu-id="9027e-104">[.NET Çekirdek Kaldırma](https://aka.ms/dotnet-core-uninstall-tool) Aracı`dotnet-core-uninstall`( ) bir sistemden .NET Core SDK'ları ve Runtimes'ı kaldırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="9027e-104">The [.NET Core Uninstall Tool](https://aka.ms/dotnet-core-uninstall-tool) (`dotnet-core-uninstall`) lets you remove .NET Core SDKs and Runtimes from a system.</span></span> <span data-ttu-id="9027e-105">Hangi sürümleri kaldırmak istediğinizi belirtmek için seçenekler topluluğu kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9027e-105">A collection of options is available to specify which versions you want to uninstall.</span></span>

<span data-ttu-id="9027e-106">Araç Windows ve macOS'u destekler.</span><span class="sxs-lookup"><span data-stu-id="9027e-106">The tool supports Windows and macOS.</span></span> <span data-ttu-id="9027e-107">Linux şu anda desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="9027e-107">Linux is currently not supported.</span></span>

<span data-ttu-id="9027e-108">Windows'da araç yalnızca aşağıdaki yükleyicilerden birini kullanarak yüklenen SDK'ları ve Çalışma Sürelerini kaldırabilir:</span><span class="sxs-lookup"><span data-stu-id="9027e-108">On Windows, the tool can only uninstall SDKs and Runtimes that were installed using one of the following installers:</span></span>

- <span data-ttu-id="9027e-109">.NET Core SDK ve çalışma zamanı yükleyici.</span><span class="sxs-lookup"><span data-stu-id="9027e-109">The .NET Core SDK and runtime installer.</span></span>
- <span data-ttu-id="9027e-110">Visual Studio 2019 sürüm 16.3 daha önceki sürümlerinde Visual Studio yükleyici.</span><span class="sxs-lookup"><span data-stu-id="9027e-110">The Visual Studio installer in versions earlier than Visual Studio 2019 version 16.3.</span></span>

<span data-ttu-id="9027e-111">macOS'ta araç yalnızca */usr/local/share/dotnet* klasöründe bulunan SDK'ları ve çalışma sürelerini kaldırabilir.</span><span class="sxs-lookup"><span data-stu-id="9027e-111">On macOS, the tool can only uninstall SDKs and runtimes located in the */usr/local/share/dotnet* folder.</span></span>

<span data-ttu-id="9027e-112">Bu sınırlamalar nedeniyle, araç makinenizdeki .NET Core SDK'ların ve çalışma sürelerinin tümünün yüklenmesini kaldıramayabilir.</span><span class="sxs-lookup"><span data-stu-id="9027e-112">Because of these limitations, the tool may not be able to uninstall all of the .NET Core SDKs and runtimes on your machine.</span></span> <span data-ttu-id="9027e-113">Bu sdk'lar ve bu aracın kaldıramayacağı çalışma saatleri de dahil olmak üzere, yüklü tüm .NET Core SDK'ları ve çalışma sürelerini bulmak için `dotnet --info` komutu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9027e-113">You can use the `dotnet --info` command to find all of the .NET Core SDKs and runtimes installed, including those SDKs and runtimes that this tool can't remove.</span></span> <span data-ttu-id="9027e-114">Komut, `dotnet-core-uninstall list` araçla birlikte SDK'ların kaldırAbileceği komutu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="9027e-114">The `dotnet-core-uninstall list` command displays which SDKs can be uninstalled with the tool.</span></span>

## <a name="install-the-tool"></a><span data-ttu-id="9027e-115">Aracı yükleme</span><span class="sxs-lookup"><span data-stu-id="9027e-115">Install the tool</span></span>

<span data-ttu-id="9027e-116">.NET Çekirdek Kaldırma Aracı'nı [buradan](https://aka.ms/dotnet-core-uninstall-tool) indirebilir ve kaynak kodunu [dotnet/cli-lab](https://github.com/dotnet/cli-lab) GitHub deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9027e-116">You can download the .NET Core Uninstall Tool from [here](https://aka.ms/dotnet-core-uninstall-tool) and find the source code at the [dotnet/cli-lab](https://github.com/dotnet/cli-lab) GitHub repository.</span></span>

> [!NOTE]
> <span data-ttu-id="9027e-117">Araç .NET Core SDK'ları ve çalışma sürelerini kaldırmak için yükseklik gerektirir.</span><span class="sxs-lookup"><span data-stu-id="9027e-117">The tool requires elevation to uninstall .NET Core SDKs and runtimes.</span></span> <span data-ttu-id="9027e-118">Bu nedenle, Windows'daki *C:\Program Files* veya macOS'taki */usr/local/bin* gibi yazma korumalı bir dizine yüklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="9027e-118">Therefore, it should be installed in a write-protected directory such as *C:\Program Files* on Windows or */usr/local/bin* on macOS.</span></span> <span data-ttu-id="9027e-119">Ayrıca [bakınız Dotnet komutları için yükseltilmiş erişim.](../tools/elevated-access.md)</span><span class="sxs-lookup"><span data-stu-id="9027e-119">See also [Elevated access for dotnet commands](../tools/elevated-access.md).</span></span> <span data-ttu-id="9027e-120">Daha fazla bilgi için [ayrıntılı yükleme yönergelerine](https://aka.ms/dotnet-core-uninstall-tool)bakın.</span><span class="sxs-lookup"><span data-stu-id="9027e-120">For more information, see the [detailed installation instructions](https://aka.ms/dotnet-core-uninstall-tool).</span></span>

## <a name="run-the-tool"></a><span data-ttu-id="9027e-121">Aracı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="9027e-121">Run the tool</span></span>

<span data-ttu-id="9027e-122">Aşağıdaki adımlar, kaldırma aracını çalıştırmak için önerilen yaklaşımı gösterir:</span><span class="sxs-lookup"><span data-stu-id="9027e-122">The following steps show the recommended approach for running the uninstall tool:</span></span>

- [<span data-ttu-id="9027e-123">Adım 1 - Ekran yüklü .NET Core SDK'lar ve çalışma süreleri</span><span class="sxs-lookup"><span data-stu-id="9027e-123">Step 1 - Display installed .NET Core SDKs and runtimes</span></span>](#step-1---display-installed-net-core-sdks-and-runtimes)
- [<span data-ttu-id="9027e-124">Adım 2 - Kuru bir çalışma yapın</span><span class="sxs-lookup"><span data-stu-id="9027e-124">Step 2 - Do a dry run</span></span>](#step-2---do-a-dry-run)
- [<span data-ttu-id="9027e-125">Adım 3 - .NET Çekirdek SDK'ları ve Çalışma Sürelerini Kaldır</span><span class="sxs-lookup"><span data-stu-id="9027e-125">Step 3 - Uninstall .NET Core SDKs and Runtimes</span></span>](#step-3---uninstall-net-core-sdks-and-runtimes)
- [<span data-ttu-id="9027e-126">Adım 4 - NuGet geri dönüş klasörünü silin (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="9027e-126">Step 4 - Delete the NuGet fallback folder (optional)</span></span>](#step-4---delete-the-nuget-fallback-folder-optional)

### <a name="step-1---display-installed-net-core-sdks-and-runtimes"></a><span data-ttu-id="9027e-127">Adım 1 - Ekran yüklü .NET Core SDK'lar ve çalışma süreleri</span><span class="sxs-lookup"><span data-stu-id="9027e-127">Step 1 - Display installed .NET Core SDKs and runtimes</span></span>

<span data-ttu-id="9027e-128">Komut, `dotnet-core-uninstall list` yüklenen .NET Core SDK'ları ve bu araçla kaldırılabilen çalışma sürelerini listeler.</span><span class="sxs-lookup"><span data-stu-id="9027e-128">The `dotnet-core-uninstall list` command lists the installed .NET Core SDKs and runtimes that can be removed with this tool.</span></span> <span data-ttu-id="9027e-129">Bazı SDK'lar ve çalışma süreleri Visual Studio tarafından gerekli olabilir ve bunları kaldırmak için tavsiye edilmez neden bir not ile görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="9027e-129">Some SDKs and runtimes may be required by Visual Studio and they're displayed with a note of why it isn't recommended to uninstall them.</span></span>

<span data-ttu-id="9027e-130">**dotnet-core-uninstall listesi**</span><span class="sxs-lookup"><span data-stu-id="9027e-130">**dotnet-core-uninstall list**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="9027e-131">Özet</span><span class="sxs-lookup"><span data-stu-id="9027e-131">Synopsis</span></span>

```console
dotnet-core-uninstall list [options]
```

#### <a name="options"></a><span data-ttu-id="9027e-132">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="9027e-132">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="9027e-133">Windows</span><span class="sxs-lookup"><span data-stu-id="9027e-133">Windows</span></span>](#tab/windows)

* **`--aspnet-runtime`**

  <span data-ttu-id="9027e-134">Bu araçla kaldırılabilen tüm ASP.NET Core çalışma sürelerini listeler.</span><span class="sxs-lookup"><span data-stu-id="9027e-134">Lists all the ASP.NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="9027e-135">Bu araçla kaldırılabilen tüm .NET Core çalışma süresini ve barındırma paketlerini listeler.</span><span class="sxs-lookup"><span data-stu-id="9027e-135">Lists all the .NET Core runtime and hosting bundles that can be uninstalled with this tool.</span></span>

* **`--runtime`**

  <span data-ttu-id="9027e-136">Bu araçla kaldırılabilen tüm .NET Core çalışma saatlerini listeler.</span><span class="sxs-lookup"><span data-stu-id="9027e-136">Lists all .NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="9027e-137">Bu araçla kaldırılabilen tüm .NET Core SDK'ları listeler.</span><span class="sxs-lookup"><span data-stu-id="9027e-137">Lists all .NET Core SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="9027e-138">Ayrıntılı lık düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9027e-138">Sets the verbosity level.</span></span> <span data-ttu-id="9027e-139">İzin verilen `q[uiet]` `m[inimal]`değerler `n[ormal]` `d[etailed]`, `diag[nostic]`, , , ve .</span><span class="sxs-lookup"><span data-stu-id="9027e-139">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="9027e-140">Varsayılan değer: `normal`.</span><span class="sxs-lookup"><span data-stu-id="9027e-140">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="9027e-141">Bu araçla kaldırılabilen tüm x64 .NET Core SDK'ları ve çalışma sürelerini listeler.</span><span class="sxs-lookup"><span data-stu-id="9027e-141">Lists all x64 .NET Core SDKs and runtimes that can be uninstalled with this tool.</span></span>

* **`--x86`**

  <span data-ttu-id="9027e-142">Bu araçla kaldırılabilen tüm x86 .NET Core SDK'ları ve çalışma sürelerini listeler.</span><span class="sxs-lookup"><span data-stu-id="9027e-142">Lists all x86 .NET Core SDKs and runtimes that can be uninstalled with this tool.</span></span>

## <a name="macos"></a>[<span data-ttu-id="9027e-143">Macos</span><span class="sxs-lookup"><span data-stu-id="9027e-143">macOS</span></span>](#tab/macos)

* **`--runtime`**

  <span data-ttu-id="9027e-144">Bu araçla kaldırılabilen tüm .NET Core çalışma saatlerini listeler.</span><span class="sxs-lookup"><span data-stu-id="9027e-144">Lists all .NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="9027e-145">Bu araçla kaldırılabilen tüm .NET Core SDK'ları listeler.</span><span class="sxs-lookup"><span data-stu-id="9027e-145">Lists all .NET Core SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="9027e-146">Ayrıntılı lık düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9027e-146">Sets the verbosity level.</span></span> <span data-ttu-id="9027e-147">İzin verilen `q[uiet]` `m[inimal]`değerler `n[ormal]` `d[etailed]`, `diag[nostic]`, , , ve .</span><span class="sxs-lookup"><span data-stu-id="9027e-147">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="9027e-148">Varsayılan değer: `normal`.</span><span class="sxs-lookup"><span data-stu-id="9027e-148">The default value is `normal`.</span></span>
  
---

#### <a name="examples"></a><span data-ttu-id="9027e-149">Örnekler</span><span class="sxs-lookup"><span data-stu-id="9027e-149">Examples</span></span>

* <span data-ttu-id="9027e-150">Bu araçla kaldırılabilen tüm .NET Core SDK'ları ve çalışma sürelerini listele:</span><span class="sxs-lookup"><span data-stu-id="9027e-150">List all .NET Core SDKs and runtimes that can be removed with this tool:</span></span>

  ```console
  dotnet-core-uninstall list
  ```

* <span data-ttu-id="9027e-151">Tüm x64 .NET Core SDK'ları ve çalışma sürelerini listele:</span><span class="sxs-lookup"><span data-stu-id="9027e-151">List all x64 .NET Core SDKs and runtimes:</span></span>

  ```console
  dotnet-core-uninstall list --x64
  ```

* <span data-ttu-id="9027e-152">Tüm x86 .NET Çekirdek SDK'larını listele:</span><span class="sxs-lookup"><span data-stu-id="9027e-152">List all x86 .NET Core SDKs:</span></span>

  ```console
  dotnet-core-uninstall list --sdk --x86
  ```

### <a name="step-2---do-a-dry-run"></a><span data-ttu-id="9027e-153">Adım 2 - Kuru bir çalışma yapın</span><span class="sxs-lookup"><span data-stu-id="9027e-153">Step 2 - Do a dry run</span></span>

<span data-ttu-id="9027e-154">Ve `dotnet-core-uninstall dry-run` `dotnet-core-uninstall whatif` komutları,.NET Core SDK'ları ve kaldırma gerçekleştirmeden sağlanan seçeneklere göre kaldırılacak çalışma sürelerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="9027e-154">The `dotnet-core-uninstall dry-run` and `dotnet-core-uninstall whatif` commands display the .NET Core SDKs and runtimes that will be removed based on the options provided without performing the uninstall.</span></span> <span data-ttu-id="9027e-155">Bu komutlar eş anlamlıdır.</span><span class="sxs-lookup"><span data-stu-id="9027e-155">These commands are synonyms.</span></span>

<span data-ttu-id="9027e-156">**dotnet-core-install kuru çalıştır ve dotnet-core-uninstall whatif**</span><span class="sxs-lookup"><span data-stu-id="9027e-156">**dotnet-core-uninstall dry-run and dotnet-core-uninstall whatif**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="9027e-157">Özet</span><span class="sxs-lookup"><span data-stu-id="9027e-157">Synopsis</span></span>

```console
dotnet-core-uninstall dry-run [options] [<VERSION>...]

dotnet-core-uninstall whatif [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="9027e-158">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="9027e-158">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="9027e-159">Kaldırmak için belirtilen sürüm.</span><span class="sxs-lookup"><span data-stu-id="9027e-159">The specified version to uninstall.</span></span> <span data-ttu-id="9027e-160">Boşluklara göre ayrılmış birkaç sürümü birbiri ardına listeleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9027e-160">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="9027e-161">Yanıt dosyaları da desteklenir.</span><span class="sxs-lookup"><span data-stu-id="9027e-161">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="9027e-162">Yanıt dosyaları, tüm sürümleri komut satırına yerleştirmek için bir alternatiftir.</span><span class="sxs-lookup"><span data-stu-id="9027e-162">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="9027e-163">Bunlar genellikle \*.rsp uzantılı metin dosyalarıdır ve her sürüm ayrı bir satırda listelenir.</span><span class="sxs-lookup"><span data-stu-id="9027e-163">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="9027e-164">`VERSION` Bağımsız değişken için yanıt dosyası belirtmek \@ için, yanıt dosyası adını hemen izleyen karakteri kullanın.</span><span class="sxs-lookup"><span data-stu-id="9027e-164">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="9027e-165">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="9027e-165">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="9027e-166">Windows</span><span class="sxs-lookup"><span data-stu-id="9027e-166">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="9027e-167">Tüm .NET Core SDK'ları ve çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9027e-167">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="9027e-168">Yalnızca .NET Core SDK'ları ve çalışma sürelerini belirtilen sürümden daha küçük bir sürümle kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9027e-168">Removes only the .NET Core SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="9027e-169">Belirtilen sürüm yüklü kalır.</span><span class="sxs-lookup"><span data-stu-id="9027e-169">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="9027e-170">Belirtilen sürümler dışında tüm .NET Core SDK'ları ve çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9027e-170">Removes all .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="9027e-171">.NET Core SDK'ları ve çalışma sürelerini, en yüksek sürüm hariç kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9027e-171">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="9027e-172">.NET Core SDK'ları ve daha yüksek düzeltme eki ile değiştirilen çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9027e-172">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="9027e-173">Bu seçenek global.json'ı korur.</span><span class="sxs-lookup"><span data-stu-id="9027e-173">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="9027e-174">.NET Core SDK'ları ve önizleme olarak işaretlenmiş çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9027e-174">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="9027e-175">.NET Core SDK'ları ve en yüksek önizleme dışında önizleme olarak işaretlenmiş çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9027e-175">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="9027e-176">Yalnızca Core çalışma sürelerini ASP.NET kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9027e-176">Removes ASP.NET Core runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="9027e-177">.NET Core çalışma süresini ve yalnızca barındırma paketlerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9027e-177">Removes .NET Core runtime and hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="9027e-178">.NET Core SDK'ları ve belirtilen `major.minor` sürümle eşleşen çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9027e-178">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="9027e-179">Yalnızca .NET Core çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9027e-179">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="9027e-180">Yalnızca .NET Core SDK'ları kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9027e-180">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="9027e-181">Ayrıntılı lık düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9027e-181">Sets the verbosity level.</span></span> <span data-ttu-id="9027e-182">İzin verilen `q[uiet]` `m[inimal]`değerler `n[ormal]` `d[etailed]`, `diag[nostic]`, , , ve .</span><span class="sxs-lookup"><span data-stu-id="9027e-182">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="9027e-183">Varsayılan değer: `normal`.</span><span class="sxs-lookup"><span data-stu-id="9027e-183">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="9027e-184">`--sdk`X64 `--runtime` `--aspnet-runtime` SDK'lar veya çalışma süreleri ile kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9027e-184">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="9027e-185">`--sdk`X86 SDK'ları veya çalışma sürelerini kaldırmak `--aspnet-runtime` için , ve `--runtime`kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9027e-185">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="9027e-186">**`--force`** Visual Studio tarafından kullanılabilecek sürümlerin kaldırılmasını zorlar.</span><span class="sxs-lookup"><span data-stu-id="9027e-186">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="9027e-187">Notlar:</span><span class="sxs-lookup"><span data-stu-id="9027e-187">Notes:</span></span>

1. <span data-ttu-id="9027e-188">Tam olarak `--sdk` `--runtime`biri `--aspnet-runtime`, `--hosting-bundle` , , ve gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9027e-188">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="9027e-189">`--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , , ve münhasırdır.</span><span class="sxs-lookup"><span data-stu-id="9027e-189">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="9027e-190">Belirtilmemişse `--x64` veya `--x86` belirtilmemişse, hem x64 hem de x86 kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="9027e-190">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macos"></a>[<span data-ttu-id="9027e-191">Macos</span><span class="sxs-lookup"><span data-stu-id="9027e-191">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="9027e-192">Tüm .NET Core SDK'ları ve çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9027e-192">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="9027e-193">.NET Core SDK'ları ve çalışma sürelerini belirtilen sürümün altında kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9027e-193">Removes .NET Core SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="9027e-194">Belirtilen sürüm kalır.</span><span class="sxs-lookup"><span data-stu-id="9027e-194">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="9027e-195">Belirtilen sürümler dışında .NET Core SDK'ları ve çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9027e-195">Removes .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="9027e-196">.NET Core SDK'ları ve çalışma sürelerini, en yüksek sürüm hariç kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9027e-196">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="9027e-197">.NET Core SDK'ları ve daha yüksek düzeltme eki ile değiştirilen çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9027e-197">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="9027e-198">Bu seçenek global.json'ı korur.</span><span class="sxs-lookup"><span data-stu-id="9027e-198">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="9027e-199">.NET Core SDK'ları ve önizleme olarak işaretlenmiş çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9027e-199">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="9027e-200">.NET Core SDK'ları ve en yüksek önizleme dışında önizleme olarak işaretlenmiş çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9027e-200">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="9027e-201">.NET Core SDK'ları ve belirtilen `major.minor` sürümle eşleşen çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9027e-201">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="9027e-202">Yalnızca .NET Core çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9027e-202">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="9027e-203">Yalnızca .NET Core SDK'ları kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9027e-203">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="9027e-204">Ayrıntılı lık düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9027e-204">Sets the verbosity level.</span></span> <span data-ttu-id="9027e-205">İzin verilen `q[uiet]` `m[inimal]`değerler `n[ormal]` `d[etailed]`, `diag[nostic]`, , , ve .</span><span class="sxs-lookup"><span data-stu-id="9027e-205">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="9027e-206">Varsayılan değer: `normal`.</span><span class="sxs-lookup"><span data-stu-id="9027e-206">The default value is `normal`.</span></span>
  
* <span data-ttu-id="9027e-207">**`--force`** Visual Studio veya SDK'lar tarafından kullanılabilecek sürümlerin kaldırılmasını zorlar.</span><span class="sxs-lookup"><span data-stu-id="9027e-207">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="9027e-208">Notlar:</span><span class="sxs-lookup"><span data-stu-id="9027e-208">Notes:</span></span>

1. <span data-ttu-id="9027e-209">Tam olarak `--sdk` `--runtime` biri ve gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9027e-209">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="9027e-210">`--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , , ve münhasırdır.</span><span class="sxs-lookup"><span data-stu-id="9027e-210">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="9027e-211">Örnekler</span><span class="sxs-lookup"><span data-stu-id="9027e-211">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="9027e-212">Varsayılan olarak, .NET Core SDK'lar ve Visual Studio veya diğer SDK'lar tarafından `dotnet-core-uninstall dry-run` gerekli olabilecek çalışma süreleri çıktıya dahil edilmez.</span><span class="sxs-lookup"><span data-stu-id="9027e-212">By default, .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs are not included in `dotnet-core-uninstall dry-run` output.</span></span> <span data-ttu-id="9027e-213">Aşağıdaki örneklerde, makinenin durumuna bağlı olarak, belirtilen SDK'lardan ve çalışma sürelerinden bazıları çıktıya dahil edilemez.</span><span class="sxs-lookup"><span data-stu-id="9027e-213">In the following examples, some of the specified SDKs and runtimes may not be included in the output, depending on the state of the machine.</span></span> <span data-ttu-id="9027e-214">Tüm SDK'ları ve çalışma sürelerini eklemek için bunları `--force` açıkça bağımsız değişken olarak listeleyin veya seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="9027e-214">To include all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="9027e-215">Daha yüksek yamalar tarafından yerini almış tüm .NET Core runtimes kaldırma kuru çalışma:</span><span class="sxs-lookup"><span data-stu-id="9027e-215">Dry run of removing all .NET Core runtimes that have been superseded by higher patches:</span></span>

  ```console
  dotnet-core-uninstall dry-run --all-lower-patches --runtime
  ```

* <span data-ttu-id="9027e-216">Sürüm `2.2.301`altındaki tüm .NET Core SDK'ları kaldırmanın kuru çalıştırılması:</span><span class="sxs-lookup"><span data-stu-id="9027e-216">Dry run of removing all .NET Core SDKs below the version `2.2.301`:</span></span>

  ```console
  dotnet-core-uninstall whatif --all-below 2.2.301 --sdk
  ```

### <a name="step-3---uninstall-net-core-sdks-and-runtimes"></a><span data-ttu-id="9027e-217">Adım 3 - .NET Çekirdek SDK'ları ve Çalışma Sürelerini Kaldır</span><span class="sxs-lookup"><span data-stu-id="9027e-217">Step 3 - Uninstall .NET Core SDKs and Runtimes</span></span>

<span data-ttu-id="9027e-218">`dotnet-core-uninstall remove`bir seçenek koleksiyonu tarafından belirtilen .NET Core SDK'ları ve Runtimes'ı yükler.</span><span class="sxs-lookup"><span data-stu-id="9027e-218">`dotnet-core-uninstall remove` uninstalls .NET Core SDKs and Runtimes that are specified by a collection of options.</span></span> <span data-ttu-id="9027e-219">Araç, Sürüm 5.0 veya üzeri sürümile SDK'ları ve Runtimes'ı kaldırmak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="9027e-219">The tool can't be used to uninstall SDKs and Runtimes with version 5.0 or above.</span></span>

<span data-ttu-id="9027e-220">Bu araç yıkıcı bir davranışa sahip olduğundan, kaldırma komutunu çalıştırmadan önce kuru bir çalışma yapmanız **önerilir.**</span><span class="sxs-lookup"><span data-stu-id="9027e-220">Since this tool has a destructive behavior, it's **highly** recommended that you do a dry run before running the remove command.</span></span> <span data-ttu-id="9027e-221">Kuru çalıştırma, `remove` komutu kullandığınızda .NET Core SDK'ların ve çalışma sürelerinin ne kadar kaldırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9027e-221">The dry run will show you what .NET Core SDKs and runtimes will be removed when you use the `remove` command.</span></span> <span data-ttu-id="9027e-222">Hangi SDK'ların ve çalışma sürelerinin kaldırılmasının güvenli olduğunu öğrenmek için [bir sürümü kaldırmam gerekir mi?](../versions/remove-runtime-sdk-versions.md#should-i-remove-a-version)</span><span class="sxs-lookup"><span data-stu-id="9027e-222">Refer to [Should I remove a version?](../versions/remove-runtime-sdk-versions.md#should-i-remove-a-version) to learn which SDKs and runtimes are safe to remove.</span></span>

> [!CAUTION]
> <span data-ttu-id="9027e-223">Aşağıdaki uyarılara dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="9027e-223">Keep in mind the following caveats:</span></span>
>
>- <span data-ttu-id="9027e-224">Bu araç, makinenizdeki dosyalar tarafından `global.json` gerekli olan .NET Core SDK sürümlerini kaldırabilir.</span><span class="sxs-lookup"><span data-stu-id="9027e-224">This tool can uninstall versions of the .NET Core SDK that are required by `global.json` files on your machine.</span></span> <span data-ttu-id="9027e-225">.NET Core SDK'larını [İndir .NET Core](https://dotnet.microsoft.com/download/dotnet-core) sayfasından yeniden yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9027e-225">You can reinstall .NET Core SDKs from the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>
>- <span data-ttu-id="9027e-226">Bu araç, .NET Core çalışma zamanının, makinenizdeki çerçeveye bağımlı uygulamalar tarafından gerekli olan sürümlerini kaldırabilir.</span><span class="sxs-lookup"><span data-stu-id="9027e-226">This tool can uninstall versions of the .NET Core runtime that are required by framework dependent applications on your machine.</span></span> <span data-ttu-id="9027e-227">.NET Core çalışma saatlerini [İndir .NET Core](https://dotnet.microsoft.com/download/dotnet-core) sayfasından yeniden yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9027e-227">You can reinstall .NET Core runtimes from the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>
>- <span data-ttu-id="9027e-228">Bu araç, .NET Core SDK sürümlerini ve Visual Studio'nun güvendiği çalışma süresini kaldırabilir.</span><span class="sxs-lookup"><span data-stu-id="9027e-228">This tool can uninstall versions of the .NET Core SDK and runtime that Visual Studio relies on.</span></span> <span data-ttu-id="9027e-229">Visual Studio yüklemenizi bozarsanız, çalışma durumuna geri dönmek için Visual Studio yükleyicisinde "Onarım"ı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9027e-229">If you break your Visual Studio installation, run "Repair" in the Visual Studio installer to get back to a working state.</span></span>

<span data-ttu-id="9027e-230">Varsayılan olarak, tüm komutlar .NET Core SDK'larını ve Visual Studio veya diğer SDK'lar tarafından gerekli olabilecek çalışma sürelerini tutar.</span><span class="sxs-lookup"><span data-stu-id="9027e-230">By default, all commands keep the .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs.</span></span> <span data-ttu-id="9027e-231">Bu SDK'lar ve çalışma süreleri, bunları açıkça bağımsız değişken olarak `--force` listeleyerek veya seçeneği kullanarak kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="9027e-231">These SDKs and runtimes can be uninstalled by listing them explicitly as arguments or by using the `--force` option.</span></span>

<span data-ttu-id="9027e-232">Araç .NET Core SDK'ları ve çalışma sürelerini kaldırmak için yükseklik gerektirir.</span><span class="sxs-lookup"><span data-stu-id="9027e-232">The tool requires elevation to uninstall .NET Core SDKs and runtimes.</span></span> <span data-ttu-id="9027e-233">Aracı Windows'da ve `sudo` macOS'ta bir Yönetici komut isteminde çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9027e-233">Run the tool in an Administrator command prompt on Windows and with `sudo` on macOS.</span></span> <span data-ttu-id="9027e-234">Ve `dry-run` `whatif` komutları yükseklik gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="9027e-234">The `dry-run` and `whatif` commands don't require elevation.</span></span>

<span data-ttu-id="9027e-235">**dotnet-core-uninstall kaldırma**</span><span class="sxs-lookup"><span data-stu-id="9027e-235">**dotnet-core-uninstall remove**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="9027e-236">Özet</span><span class="sxs-lookup"><span data-stu-id="9027e-236">Synopsis</span></span>

```console
dotnet-core-uninstall remove [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="9027e-237">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="9027e-237">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="9027e-238">Kaldırmak için belirtilen sürüm.</span><span class="sxs-lookup"><span data-stu-id="9027e-238">The specified version to uninstall.</span></span> <span data-ttu-id="9027e-239">Boşluklara göre ayrılmış birkaç sürümü birbiri ardına listeleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9027e-239">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="9027e-240">Yanıt dosyaları da desteklenir.</span><span class="sxs-lookup"><span data-stu-id="9027e-240">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="9027e-241">Yanıt dosyaları, tüm sürümleri komut satırına yerleştirmek için bir alternatiftir.</span><span class="sxs-lookup"><span data-stu-id="9027e-241">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="9027e-242">Bunlar genellikle \*.rsp uzantılı metin dosyalarıdır ve her sürüm ayrı bir satırda listelenir.</span><span class="sxs-lookup"><span data-stu-id="9027e-242">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="9027e-243">`VERSION` Bağımsız değişken için yanıt dosyası belirtmek \@ için, yanıt dosyası adını hemen izleyen karakteri kullanın.</span><span class="sxs-lookup"><span data-stu-id="9027e-243">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="9027e-244">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="9027e-244">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="9027e-245">Windows</span><span class="sxs-lookup"><span data-stu-id="9027e-245">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="9027e-246">Tüm .NET Core SDK'ları ve çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9027e-246">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="9027e-247">Yalnızca .NET Core SDK'ları ve çalışma sürelerini belirtilen sürümden daha küçük bir sürümle kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9027e-247">Removes only the .NET Core SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="9027e-248">Belirtilen sürüm yüklü kalır.</span><span class="sxs-lookup"><span data-stu-id="9027e-248">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="9027e-249">Belirtilen sürümler dışında tüm .NET Core SDK'ları ve çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9027e-249">Removes all .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="9027e-250">.NET Core SDK'ları ve çalışma sürelerini, en yüksek sürüm hariç kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9027e-250">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="9027e-251">.NET Core SDK'ları ve daha yüksek düzeltme eki ile değiştirilen çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9027e-251">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="9027e-252">Bu seçenek global.json'ı korur.</span><span class="sxs-lookup"><span data-stu-id="9027e-252">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="9027e-253">.NET Core SDK'ları ve önizleme olarak işaretlenmiş çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9027e-253">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="9027e-254">.NET Core SDK'ları ve en yüksek önizleme dışında önizleme olarak işaretlenmiş çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9027e-254">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="9027e-255">Yalnızca Core çalışma sürelerini ASP.NET kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9027e-255">Removes ASP.NET Core runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="9027e-256">.NET Core çalışma süresini ve yalnızca barındırma paketlerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9027e-256">Removes .NET Core runtime and hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="9027e-257">.NET Core SDK'ları ve belirtilen `major.minor` sürümle eşleşen çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9027e-257">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="9027e-258">Yalnızca .NET Core çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9027e-258">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="9027e-259">Yalnızca .NET Core SDK'ları kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9027e-259">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="9027e-260">Ayrıntılı lık düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9027e-260">Sets the verbosity level.</span></span> <span data-ttu-id="9027e-261">İzin verilen `q[uiet]` `m[inimal]`değerler `n[ormal]` `d[etailed]`, `diag[nostic]`, , , ve .</span><span class="sxs-lookup"><span data-stu-id="9027e-261">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="9027e-262">Varsayılan değer: `normal`.</span><span class="sxs-lookup"><span data-stu-id="9027e-262">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="9027e-263">`--sdk`X64 `--runtime` `--aspnet-runtime` SDK'lar veya çalışma süreleri ile kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9027e-263">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="9027e-264">`--sdk`X86 SDK'ları veya çalışma sürelerini kaldırmak `--aspnet-runtime` için , ve `--runtime`kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9027e-264">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="9027e-265">**`-y, --yes`** Evet veya hayır onayı gerektirmeden komutu yürütür.</span><span class="sxs-lookup"><span data-stu-id="9027e-265">**`-y, --yes`** Executes the command without requiring a yes or no confirmation.</span></span>

* <span data-ttu-id="9027e-266">**`--force`** Visual Studio tarafından kullanılabilecek sürümlerin kaldırılmasını zorlar.</span><span class="sxs-lookup"><span data-stu-id="9027e-266">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="9027e-267">Notlar:</span><span class="sxs-lookup"><span data-stu-id="9027e-267">Notes:</span></span>

1. <span data-ttu-id="9027e-268">Tam olarak `--sdk` `--runtime`biri `--aspnet-runtime`, `--hosting-bundle` , , ve gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9027e-268">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="9027e-269">`--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , , ve münhasırdır.</span><span class="sxs-lookup"><span data-stu-id="9027e-269">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="9027e-270">Belirtilmemişse `--x64` veya `--x86` belirtilmemişse, hem x64 hem de x86 kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="9027e-270">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macos"></a>[<span data-ttu-id="9027e-271">Macos</span><span class="sxs-lookup"><span data-stu-id="9027e-271">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="9027e-272">Tüm .NET Core SDK'ları ve çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9027e-272">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="9027e-273">.NET Core SDK'ları ve çalışma sürelerini belirtilen sürümün altında kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9027e-273">Removes .NET Core SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="9027e-274">Belirtilen sürüm kalır.</span><span class="sxs-lookup"><span data-stu-id="9027e-274">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="9027e-275">Belirtilen sürümler dışında .NET Core SDK'ları ve çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9027e-275">Removes .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="9027e-276">.NET Core SDK'ları ve çalışma sürelerini, en yüksek sürüm hariç kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9027e-276">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="9027e-277">.NET Core SDK'ları ve daha yüksek düzeltme eki ile değiştirilen çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9027e-277">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="9027e-278">Bu seçenek global.json'ı korur.</span><span class="sxs-lookup"><span data-stu-id="9027e-278">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="9027e-279">.NET Core SDK'ları ve önizleme olarak işaretlenmiş çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9027e-279">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="9027e-280">.NET Core SDK'ları ve en yüksek önizleme dışında önizleme olarak işaretlenmiş çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9027e-280">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="9027e-281">.NET Core SDK'ları ve belirtilen `major.minor` sürümle eşleşen çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9027e-281">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="9027e-282">Yalnızca .NET Core çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9027e-282">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="9027e-283">Yalnızca .NET Core SDK'ları kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9027e-283">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="9027e-284">Ayrıntılı lık düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9027e-284">Sets the verbosity level.</span></span> <span data-ttu-id="9027e-285">İzin verilen `q[uiet]` `m[inimal]`değerler `n[ormal]` `d[etailed]`, `diag[nostic]`, , , ve .</span><span class="sxs-lookup"><span data-stu-id="9027e-285">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="9027e-286">Varsayılan değer: `normal`.</span><span class="sxs-lookup"><span data-stu-id="9027e-286">The default value is `normal`.</span></span>

* <span data-ttu-id="9027e-287">**`-y, --yes`** Y/N onayı gerektirmeden komutu yürütür.</span><span class="sxs-lookup"><span data-stu-id="9027e-287">**`-y, --yes`** Executes the command without requiring Y/N confirmation.</span></span>
  
* <span data-ttu-id="9027e-288">**`--force`** Visual Studio veya SDK'lar tarafından kullanılabilecek sürümlerin kaldırılmasını zorlar.</span><span class="sxs-lookup"><span data-stu-id="9027e-288">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="9027e-289">Notlar:</span><span class="sxs-lookup"><span data-stu-id="9027e-289">Notes:</span></span>

1. <span data-ttu-id="9027e-290">Tam olarak `--sdk` `--runtime` biri ve gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9027e-290">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="9027e-291">`--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , , ve münhasırdır.</span><span class="sxs-lookup"><span data-stu-id="9027e-291">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="9027e-292">Örnekler</span><span class="sxs-lookup"><span data-stu-id="9027e-292">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="9027e-293">Varsayılan olarak, .NET Core SDK'lar ve Visual Studio veya diğer SDK'lar tarafından gerekli olabilecek çalışma süreleri tutulur.</span><span class="sxs-lookup"><span data-stu-id="9027e-293">By default, .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs are kept.</span></span> <span data-ttu-id="9027e-294">Aşağıdaki örneklerde, makinenin durumuna bağlı olarak belirtilen SDK'lardan ve çalışma sürelerinden bazıları kalabilir.</span><span class="sxs-lookup"><span data-stu-id="9027e-294">In the following examples, some of the specified SDKs and runtimes may remain, depending on the state of the machine.</span></span> <span data-ttu-id="9027e-295">Tüm SDK'ları ve çalışma sürelerini kaldırmak için bunları `--force` açıkça bağımsız değişken olarak listeleyin veya seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="9027e-295">To remove all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="9027e-296">Y/N onayı gerektirmeden sürüm `3.0.0-preview6-27804-01` dışındaki tüm .NET Core çalışma sürelerini kaldırın:</span><span class="sxs-lookup"><span data-stu-id="9027e-296">Remove all .NET Core runtimes except the version `3.0.0-preview6-27804-01` without requiring Y/N confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --all-but 3.0.0-preview6-27804-01 --runtime --yes
  ```

* <span data-ttu-id="9027e-297">Y/n onayı gerektirmeden tüm .NET Core 1.1 SDK'larını kaldırın:</span><span class="sxs-lookup"><span data-stu-id="9027e-297">Remove all .NET Core 1.1 SDKs without requiring Y/n confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --sdk --major-minor 1.1 -y
  ```

* <span data-ttu-id="9027e-298">.NET Core 1.1.11 SDK konsol çıkışı olmadan kaldırın:</span><span class="sxs-lookup"><span data-stu-id="9027e-298">Remove the .NET Core 1.1.11 SDK with no console output:</span></span>

  ```console
  dotnet-core-uninstall remove 1.1.11 --sdk --yes --verbosity q
  ```

* <span data-ttu-id="9027e-299">Bu araç tarafından güvenli bir şekilde çıkarılabilen tüm .NET Core SDK'larını kaldırın:</span><span class="sxs-lookup"><span data-stu-id="9027e-299">Remove all .NET Core SDKs that can safely be removed by this tool:</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk
  ```

* <span data-ttu-id="9027e-300">Visual Studio tarafından gerekli olabilecek SDK'lar da dahil olmak üzere bu araç tarafından kaldırılabilecek tüm .NET Core SDK'larını kaldırın (önerilmez):</span><span class="sxs-lookup"><span data-stu-id="9027e-300">Remove all .NET Core SDKs that can be removed by this tool, including those SDKs that may be required by Visual Studio (not recommended):</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk --force
  ```

* <span data-ttu-id="9027e-301">Yanıt dosyasında belirtilen tüm .NET Core SDK'ları kaldırma`versions.rsp`</span><span class="sxs-lookup"><span data-stu-id="9027e-301">Remove all .NET Core SDKs that are specified in the response file `versions.rsp`</span></span>

  ```console
  dotnet-core-uninstall remove --sdk @versions.rsp
  ```

  <span data-ttu-id="9027e-302">*versions.rsp* içeriği aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="9027e-302">The content of *versions.rsp* is as follows:</span></span>
  
  ```text
  2.2.300
  2.1.700
  ```

### <a name="step-4---delete-the-nuget-fallback-folder-optional"></a><span data-ttu-id="9027e-303">Adım 4 - NuGet geri dönüş klasörünü silin (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="9027e-303">Step 4 - Delete the NuGet fallback folder (optional)</span></span>

<span data-ttu-id="9027e-304">Bazı durumlarda, artık ihtiyacınız `NuGetFallbackFolder` yok ve silmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9027e-304">In some cases, you no longer need the `NuGetFallbackFolder` and may wish to delete it.</span></span> <span data-ttu-id="9027e-305">Bu klasörü silme hakkında daha fazla bilgi için [NuGetFallbackFolder'ı Kaldır'a](../versions/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder)bakın.</span><span class="sxs-lookup"><span data-stu-id="9027e-305">For more information about deleting this folder, see [Remove the NuGetFallbackFolder](../versions/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).</span></span>

## <a name="uninstall-the-tool"></a><span data-ttu-id="9027e-306">Aracı kaldırma</span><span class="sxs-lookup"><span data-stu-id="9027e-306">Uninstall the tool</span></span>

## <a name="windows"></a>[<span data-ttu-id="9027e-307">Windows</span><span class="sxs-lookup"><span data-stu-id="9027e-307">Windows</span></span>](#tab/windows)

1. <span data-ttu-id="9027e-308">**Program Ekle veya Kaldır'ı**aç.</span><span class="sxs-lookup"><span data-stu-id="9027e-308">Open **Add or Remove Programs**.</span></span>
2. <span data-ttu-id="9027e-309">`Microsoft .NET Core SDK Uninstall Tool` arayın.</span><span class="sxs-lookup"><span data-stu-id="9027e-309">Search for `Microsoft .NET Core SDK Uninstall Tool`.</span></span>
3. <span data-ttu-id="9027e-310">**Kaldır**'ı seçin.</span><span class="sxs-lookup"><span data-stu-id="9027e-310">Select **Uninstall**.</span></span>

## <a name="macos"></a>[<span data-ttu-id="9027e-311">Macos</span><span class="sxs-lookup"><span data-stu-id="9027e-311">macOS</span></span>](#tab/macos)

<span data-ttu-id="9027e-312">İndirilen *dotnet-core-uninstall.tar.gz* dosyasını yüklendiği dizinden silin.</span><span class="sxs-lookup"><span data-stu-id="9027e-312">Delete the downloaded *dotnet-core-uninstall.tar.gz* file from the directory where it was installed.</span></span> <span data-ttu-id="9027e-313">Bu dosyanın içeriğini başka bir dizine açtıysanız, bu içeriği de sildiğimden emin olun.</span><span class="sxs-lookup"><span data-stu-id="9027e-313">If you unzipped the contents of this file into another directory, be sure to delete that content as well.</span></span>

---
