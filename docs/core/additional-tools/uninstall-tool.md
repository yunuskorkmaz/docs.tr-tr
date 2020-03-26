---
title: Aracı Kaldır
description: .NET Core SDK'ların ve çalışma saatlerinin kontrollü olarak temizlenmesini sağlayan kılavuzlu bir araç olan .NET Çekirdek Kaldırma Aracı'na genel bir bakış.
author: sfoslund
ms.date: 01/06/2020
ms.openlocfilehash: 816aef6ab8bc0e51bb8befb14fde60513d4fadfc
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507327"
---
# <a name="net-core-uninstall-tool"></a><span data-ttu-id="ec967-103">.NET Core Kaldırma Aracı</span><span class="sxs-lookup"><span data-stu-id="ec967-103">.NET Core Uninstall Tool</span></span>

<span data-ttu-id="ec967-104">[.NET Çekirdek Kaldırma](https://aka.ms/dotnet-core-uninstall-tool) Aracı`dotnet-core-uninstall`( ) bir sistemden .NET Core SDK'ları ve Runtimes'ı kaldırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="ec967-104">The [.NET Core Uninstall Tool](https://aka.ms/dotnet-core-uninstall-tool) (`dotnet-core-uninstall`) lets you remove .NET Core SDKs and Runtimes from a system.</span></span> <span data-ttu-id="ec967-105">Hangi sürümleri kaldırmak istediğinizi belirtmek için seçenekler topluluğu kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ec967-105">A collection of options is available to specify which versions you want to uninstall.</span></span>

<span data-ttu-id="ec967-106">Araç Windows ve macOS'u destekler.</span><span class="sxs-lookup"><span data-stu-id="ec967-106">The tool supports Windows and macOS.</span></span> <span data-ttu-id="ec967-107">Linux şu anda desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="ec967-107">Linux is currently not supported.</span></span>

<span data-ttu-id="ec967-108">Windows'da araç yalnızca aşağıdaki yükleyicilerden birini kullanarak yüklenen SDK'ları ve Çalışma Sürelerini kaldırabilir:</span><span class="sxs-lookup"><span data-stu-id="ec967-108">On Windows, the tool can only uninstall SDKs and Runtimes that were installed using one of the following installers:</span></span>

- <span data-ttu-id="ec967-109">.NET Core SDK ve çalışma zamanı yükleyici.</span><span class="sxs-lookup"><span data-stu-id="ec967-109">The .NET Core SDK and runtime installer.</span></span>
- <span data-ttu-id="ec967-110">Visual Studio 2019 sürüm 16.3 daha önceki sürümlerinde Visual Studio yükleyici.</span><span class="sxs-lookup"><span data-stu-id="ec967-110">The Visual Studio installer in versions earlier than Visual Studio 2019 version 16.3.</span></span>

<span data-ttu-id="ec967-111">macOS'ta araç yalnızca */usr/local/share/dotnet* klasöründe bulunan SDK'ları ve çalışma sürelerini kaldırabilir.</span><span class="sxs-lookup"><span data-stu-id="ec967-111">On macOS, the tool can only uninstall SDKs and runtimes located in the */usr/local/share/dotnet* folder.</span></span>

<span data-ttu-id="ec967-112">Bu sınırlamalar nedeniyle, araç makinenizdeki .NET Core SDK'ların ve çalışma sürelerinin tümünün yüklenmesini kaldıramayabilir.</span><span class="sxs-lookup"><span data-stu-id="ec967-112">Because of these limitations, the tool may not be able to uninstall all of the .NET Core SDKs and runtimes on your machine.</span></span> <span data-ttu-id="ec967-113">Bu sdk'lar ve bu aracın kaldıramayacağı çalışma saatleri de dahil olmak üzere, yüklü tüm .NET Core SDK'ları ve çalışma sürelerini bulmak için `dotnet --info` komutu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec967-113">You can use the `dotnet --info` command to find all of the .NET Core SDKs and runtimes installed, including those SDKs and runtimes that this tool can't remove.</span></span> <span data-ttu-id="ec967-114">Komut, `dotnet-core-uninstall list` araçla birlikte SDK'ların kaldırAbileceği komutu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ec967-114">The `dotnet-core-uninstall list` command displays which SDKs can be uninstalled with the tool.</span></span>

## <a name="install-the-tool"></a><span data-ttu-id="ec967-115">Aracı yükleme</span><span class="sxs-lookup"><span data-stu-id="ec967-115">Install the tool</span></span>

<span data-ttu-id="ec967-116">.NET Çekirdek Kaldırma Aracı'nı [buradan](https://aka.ms/dotnet-core-uninstall-tool) indirebilir ve kaynak kodunu [dotnet/cli-lab](https://github.com/dotnet/cli-lab) GitHub deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec967-116">You can download the .NET Core Uninstall Tool from [here](https://aka.ms/dotnet-core-uninstall-tool) and find the source code at the [dotnet/cli-lab](https://github.com/dotnet/cli-lab) GitHub repository.</span></span>

> [!NOTE]
> <span data-ttu-id="ec967-117">Araç .NET Core SDK'ları ve çalışma sürelerini kaldırmak için yükseklik gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ec967-117">The tool requires elevation to uninstall .NET Core SDKs and runtimes.</span></span> <span data-ttu-id="ec967-118">Bu nedenle, Windows'daki *C:\Program Files* veya macOS'taki */usr/local/bin* gibi yazma korumalı bir dizine yüklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="ec967-118">Therefore, it should be installed in a write-protected directory such as *C:\Program Files* on Windows or */usr/local/bin* on macOS.</span></span> <span data-ttu-id="ec967-119">Ayrıca [bakınız Dotnet komutları için yükseltilmiş erişim.](../tools/elevated-access.md)</span><span class="sxs-lookup"><span data-stu-id="ec967-119">See also [Elevated access for dotnet commands](../tools/elevated-access.md).</span></span> <span data-ttu-id="ec967-120">Daha fazla bilgi için [ayrıntılı yükleme yönergelerine](https://aka.ms/dotnet-core-uninstall-tool)bakın.</span><span class="sxs-lookup"><span data-stu-id="ec967-120">For more information, see the [detailed installation instructions](https://aka.ms/dotnet-core-uninstall-tool).</span></span>

## <a name="run-the-tool"></a><span data-ttu-id="ec967-121">Aracı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="ec967-121">Run the tool</span></span>

<span data-ttu-id="ec967-122">Aşağıdaki adımlar, kaldırma aracını çalıştırmak için önerilen yaklaşımı gösterir:</span><span class="sxs-lookup"><span data-stu-id="ec967-122">The following steps show the recommended approach for running the uninstall tool:</span></span>

- [<span data-ttu-id="ec967-123">Adım 1 - Ekran yüklü .NET Core SDK'lar ve çalışma süreleri</span><span class="sxs-lookup"><span data-stu-id="ec967-123">Step 1 - Display installed .NET Core SDKs and runtimes</span></span>](#step-1---display-installed-net-core-sdks-and-runtimes)
- [<span data-ttu-id="ec967-124">Adım 2 - Kuru bir çalışma yapın</span><span class="sxs-lookup"><span data-stu-id="ec967-124">Step 2 - Do a dry run</span></span>](#step-2---do-a-dry-run)
- [<span data-ttu-id="ec967-125">Adım 3 - .NET Çekirdek SDK'ları ve Çalışma Sürelerini Kaldır</span><span class="sxs-lookup"><span data-stu-id="ec967-125">Step 3 - Uninstall .NET Core SDKs and Runtimes</span></span>](#step-3---uninstall-net-core-sdks-and-runtimes)
- [<span data-ttu-id="ec967-126">Adım 4 - NuGet geri dönüş klasörünü silin (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="ec967-126">Step 4 - Delete the NuGet fallback folder (optional)</span></span>](#step-4---delete-the-nuget-fallback-folder-optional)

### <a name="step-1---display-installed-net-core-sdks-and-runtimes"></a><span data-ttu-id="ec967-127">Adım 1 - Ekran yüklü .NET Core SDK'lar ve çalışma süreleri</span><span class="sxs-lookup"><span data-stu-id="ec967-127">Step 1 - Display installed .NET Core SDKs and runtimes</span></span>

<span data-ttu-id="ec967-128">Komut, `dotnet-core-uninstall list` yüklenen .NET Core SDK'ları ve bu araçla kaldırılabilen çalışma sürelerini listeler.</span><span class="sxs-lookup"><span data-stu-id="ec967-128">The `dotnet-core-uninstall list` command lists the installed .NET Core SDKs and runtimes that can be removed with this tool.</span></span> <span data-ttu-id="ec967-129">Bazı SDK'lar ve çalışma süreleri Visual Studio tarafından gerekli olabilir ve bunları kaldırmak için tavsiye edilmez neden bir not ile görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="ec967-129">Some SDKs and runtimes may be required by Visual Studio and they're displayed with a note of why it isn't recommended to uninstall them.</span></span>

> [!NOTE]
> <span data-ttu-id="ec967-130">`dotnet-core-uninstall list` Komutun çıktısı, çoğu durumda çıktıdaki yüklü sürümlerin `dotnet --info` listesiyle eşleşmez.</span><span class="sxs-lookup"><span data-stu-id="ec967-130">The output of the `dotnet-core-uninstall list` command will not match the list of installed versions in the output of `dotnet --info` in most cases.</span></span> <span data-ttu-id="ec967-131">Özellikle, bu araç zip dosyaları tarafından yüklenen veya Visual Studio tarafından yönetilen sürümleri görüntülemez (Visual Studio 2019 16.3 veya sonraki sürümler).</span><span class="sxs-lookup"><span data-stu-id="ec967-131">Specifically, this tool will not display versions installed by zip files or managed by Visual Studio (any version installed with Visual Studio 2019 16.3 or later).</span></span> <span data-ttu-id="ec967-132">Bir sürümün Visual Studio tarafından yönetilip yönetilmeyişini denetlemenin bir `Add or Remove Programs`yolu, görsel stüdyo yönetilen sürümlerinin görüntü adlarında bu şekilde işaretlendiği, bu sürümü görüntülemektir.</span><span class="sxs-lookup"><span data-stu-id="ec967-132">One way to check if a version is managed by Visual Studio is to view it in `Add or Remove Programs`, where Visual Studio managed versions are marked as such in their display names.</span></span>

<span data-ttu-id="ec967-133">**dotnet-core-uninstall listesi**</span><span class="sxs-lookup"><span data-stu-id="ec967-133">**dotnet-core-uninstall list**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="ec967-134">Özet</span><span class="sxs-lookup"><span data-stu-id="ec967-134">Synopsis</span></span>

```console
dotnet-core-uninstall list [options]
```

#### <a name="options"></a><span data-ttu-id="ec967-135">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="ec967-135">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="ec967-136">Windows</span><span class="sxs-lookup"><span data-stu-id="ec967-136">Windows</span></span>](#tab/windows)

* **`--aspnet-runtime`**

  <span data-ttu-id="ec967-137">Bu araçla kaldırılabilen tüm ASP.NET Core çalışma sürelerini listeler.</span><span class="sxs-lookup"><span data-stu-id="ec967-137">Lists all the ASP.NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="ec967-138">Bu araçla kaldırılabilen tüm .NET Core çalışma süresini ve barındırma paketlerini listeler.</span><span class="sxs-lookup"><span data-stu-id="ec967-138">Lists all the .NET Core runtime and hosting bundles that can be uninstalled with this tool.</span></span>

* **`--runtime`**

  <span data-ttu-id="ec967-139">Bu araçla kaldırılabilen tüm .NET Core çalışma saatlerini listeler.</span><span class="sxs-lookup"><span data-stu-id="ec967-139">Lists all .NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="ec967-140">Bu araçla kaldırılabilen tüm .NET Core SDK'ları listeler.</span><span class="sxs-lookup"><span data-stu-id="ec967-140">Lists all .NET Core SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="ec967-141">Ayrıntılı lık düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ec967-141">Sets the verbosity level.</span></span> <span data-ttu-id="ec967-142">İzin verilen `q[uiet]` `m[inimal]`değerler `n[ormal]` `d[etailed]`, `diag[nostic]`, , , ve .</span><span class="sxs-lookup"><span data-stu-id="ec967-142">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="ec967-143">Varsayılan değer: `normal`.</span><span class="sxs-lookup"><span data-stu-id="ec967-143">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="ec967-144">Bu araçla kaldırılabilen tüm x64 .NET Core SDK'ları ve çalışma sürelerini listeler.</span><span class="sxs-lookup"><span data-stu-id="ec967-144">Lists all x64 .NET Core SDKs and runtimes that can be uninstalled with this tool.</span></span>

* **`--x86`**

  <span data-ttu-id="ec967-145">Bu araçla kaldırılabilen tüm x86 .NET Core SDK'ları ve çalışma sürelerini listeler.</span><span class="sxs-lookup"><span data-stu-id="ec967-145">Lists all x86 .NET Core SDKs and runtimes that can be uninstalled with this tool.</span></span>

## <a name="macos"></a>[<span data-ttu-id="ec967-146">Macos</span><span class="sxs-lookup"><span data-stu-id="ec967-146">macOS</span></span>](#tab/macos)

* **`--runtime`**

  <span data-ttu-id="ec967-147">Bu araçla kaldırılabilen tüm .NET Core çalışma saatlerini listeler.</span><span class="sxs-lookup"><span data-stu-id="ec967-147">Lists all .NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="ec967-148">Bu araçla kaldırılabilen tüm .NET Core SDK'ları listeler.</span><span class="sxs-lookup"><span data-stu-id="ec967-148">Lists all .NET Core SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="ec967-149">Ayrıntılı lık düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ec967-149">Sets the verbosity level.</span></span> <span data-ttu-id="ec967-150">İzin verilen `q[uiet]` `m[inimal]`değerler `n[ormal]` `d[etailed]`, `diag[nostic]`, , , ve .</span><span class="sxs-lookup"><span data-stu-id="ec967-150">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="ec967-151">Varsayılan değer: `normal`.</span><span class="sxs-lookup"><span data-stu-id="ec967-151">The default value is `normal`.</span></span>
  
---

#### <a name="examples"></a><span data-ttu-id="ec967-152">Örnekler</span><span class="sxs-lookup"><span data-stu-id="ec967-152">Examples</span></span>

* <span data-ttu-id="ec967-153">Bu araçla kaldırılabilen tüm .NET Core SDK'ları ve çalışma sürelerini listele:</span><span class="sxs-lookup"><span data-stu-id="ec967-153">List all .NET Core SDKs and runtimes that can be removed with this tool:</span></span>

  ```console
  dotnet-core-uninstall list
  ```

* <span data-ttu-id="ec967-154">Tüm x64 .NET Core SDK'ları ve çalışma sürelerini listele:</span><span class="sxs-lookup"><span data-stu-id="ec967-154">List all x64 .NET Core SDKs and runtimes:</span></span>

  ```console
  dotnet-core-uninstall list --x64
  ```

* <span data-ttu-id="ec967-155">Tüm x86 .NET Çekirdek SDK'larını listele:</span><span class="sxs-lookup"><span data-stu-id="ec967-155">List all x86 .NET Core SDKs:</span></span>

  ```console
  dotnet-core-uninstall list --sdk --x86
  ```

### <a name="step-2---do-a-dry-run"></a><span data-ttu-id="ec967-156">Adım 2 - Kuru bir çalışma yapın</span><span class="sxs-lookup"><span data-stu-id="ec967-156">Step 2 - Do a dry run</span></span>

<span data-ttu-id="ec967-157">Ve `dotnet-core-uninstall dry-run` `dotnet-core-uninstall whatif` komutları,.NET Core SDK'ları ve kaldırma gerçekleştirmeden sağlanan seçeneklere göre kaldırılacak çalışma sürelerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ec967-157">The `dotnet-core-uninstall dry-run` and `dotnet-core-uninstall whatif` commands display the .NET Core SDKs and runtimes that will be removed based on the options provided without performing the uninstall.</span></span> <span data-ttu-id="ec967-158">Bu komutlar eş anlamlıdır.</span><span class="sxs-lookup"><span data-stu-id="ec967-158">These commands are synonyms.</span></span>

<span data-ttu-id="ec967-159">**dotnet-core-install kuru çalıştır ve dotnet-core-uninstall whatif**</span><span class="sxs-lookup"><span data-stu-id="ec967-159">**dotnet-core-uninstall dry-run and dotnet-core-uninstall whatif**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="ec967-160">Özet</span><span class="sxs-lookup"><span data-stu-id="ec967-160">Synopsis</span></span>

```console
dotnet-core-uninstall dry-run [options] [<VERSION>...]

dotnet-core-uninstall whatif [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="ec967-161">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="ec967-161">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="ec967-162">Kaldırmak için belirtilen sürüm.</span><span class="sxs-lookup"><span data-stu-id="ec967-162">The specified version to uninstall.</span></span> <span data-ttu-id="ec967-163">Boşluklara göre ayrılmış birkaç sürümü birbiri ardına listeleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec967-163">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="ec967-164">Yanıt dosyaları da desteklenir.</span><span class="sxs-lookup"><span data-stu-id="ec967-164">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="ec967-165">Yanıt dosyaları, tüm sürümleri komut satırına yerleştirmek için bir alternatiftir.</span><span class="sxs-lookup"><span data-stu-id="ec967-165">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="ec967-166">Bunlar genellikle \*.rsp uzantılı metin dosyalarıdır ve her sürüm ayrı bir satırda listelenir.</span><span class="sxs-lookup"><span data-stu-id="ec967-166">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="ec967-167">`VERSION` Bağımsız değişken için yanıt dosyası belirtmek \@ için, yanıt dosyası adını hemen izleyen karakteri kullanın.</span><span class="sxs-lookup"><span data-stu-id="ec967-167">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="ec967-168">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="ec967-168">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="ec967-169">Windows</span><span class="sxs-lookup"><span data-stu-id="ec967-169">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="ec967-170">Tüm .NET Core SDK'ları ve çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ec967-170">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="ec967-171">Yalnızca .NET Core SDK'ları ve çalışma sürelerini belirtilen sürümden daha küçük bir sürümle kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ec967-171">Removes only the .NET Core SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="ec967-172">Belirtilen sürüm yüklü kalır.</span><span class="sxs-lookup"><span data-stu-id="ec967-172">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="ec967-173">Belirtilen sürümler dışında tüm .NET Core SDK'ları ve çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ec967-173">Removes all .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="ec967-174">.NET Core SDK'ları ve çalışma sürelerini, en yüksek sürüm hariç kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ec967-174">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="ec967-175">.NET Core SDK'ları ve daha yüksek düzeltme eki ile değiştirilen çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ec967-175">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="ec967-176">Bu seçenek global.json'ı korur.</span><span class="sxs-lookup"><span data-stu-id="ec967-176">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="ec967-177">.NET Core SDK'ları ve önizleme olarak işaretlenmiş çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ec967-177">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="ec967-178">.NET Core SDK'ları ve en yüksek önizleme dışında önizleme olarak işaretlenmiş çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ec967-178">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="ec967-179">Yalnızca Core çalışma sürelerini ASP.NET kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ec967-179">Removes ASP.NET Core runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="ec967-180">.NET Core çalışma süresini ve yalnızca barındırma paketlerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ec967-180">Removes .NET Core runtime and hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="ec967-181">.NET Core SDK'ları ve belirtilen `major.minor` sürümle eşleşen çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ec967-181">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="ec967-182">Yalnızca .NET Core çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ec967-182">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="ec967-183">Yalnızca .NET Core SDK'ları kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ec967-183">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="ec967-184">Ayrıntılı lık düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ec967-184">Sets the verbosity level.</span></span> <span data-ttu-id="ec967-185">İzin verilen `q[uiet]` `m[inimal]`değerler `n[ormal]` `d[etailed]`, `diag[nostic]`, , , ve .</span><span class="sxs-lookup"><span data-stu-id="ec967-185">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="ec967-186">Varsayılan değer: `normal`.</span><span class="sxs-lookup"><span data-stu-id="ec967-186">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="ec967-187">`--sdk`X64 `--runtime` `--aspnet-runtime` SDK'lar veya çalışma süreleri ile kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ec967-187">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="ec967-188">`--sdk`X86 SDK'ları veya çalışma sürelerini kaldırmak `--aspnet-runtime` için , ve `--runtime`kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ec967-188">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="ec967-189">**`--force`** Visual Studio tarafından kullanılabilecek sürümlerin kaldırılmasını zorlar.</span><span class="sxs-lookup"><span data-stu-id="ec967-189">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="ec967-190">Notlar:</span><span class="sxs-lookup"><span data-stu-id="ec967-190">Notes:</span></span>

1. <span data-ttu-id="ec967-191">Tam olarak `--sdk` `--runtime`biri `--aspnet-runtime`, `--hosting-bundle` , , ve gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ec967-191">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="ec967-192">`--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , , ve münhasırdır.</span><span class="sxs-lookup"><span data-stu-id="ec967-192">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="ec967-193">Belirtilmemişse `--x64` veya `--x86` belirtilmemişse, hem x64 hem de x86 kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="ec967-193">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macos"></a>[<span data-ttu-id="ec967-194">Macos</span><span class="sxs-lookup"><span data-stu-id="ec967-194">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="ec967-195">Tüm .NET Core SDK'ları ve çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ec967-195">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="ec967-196">.NET Core SDK'ları ve çalışma sürelerini belirtilen sürümün altında kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ec967-196">Removes .NET Core SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="ec967-197">Belirtilen sürüm kalır.</span><span class="sxs-lookup"><span data-stu-id="ec967-197">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="ec967-198">Belirtilen sürümler dışında .NET Core SDK'ları ve çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ec967-198">Removes .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="ec967-199">.NET Core SDK'ları ve çalışma sürelerini, en yüksek sürüm hariç kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ec967-199">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="ec967-200">.NET Core SDK'ları ve daha yüksek düzeltme eki ile değiştirilen çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ec967-200">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="ec967-201">Bu seçenek global.json'ı korur.</span><span class="sxs-lookup"><span data-stu-id="ec967-201">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="ec967-202">.NET Core SDK'ları ve önizleme olarak işaretlenmiş çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ec967-202">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="ec967-203">.NET Core SDK'ları ve en yüksek önizleme dışında önizleme olarak işaretlenmiş çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ec967-203">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="ec967-204">.NET Core SDK'ları ve belirtilen `major.minor` sürümle eşleşen çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ec967-204">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="ec967-205">Yalnızca .NET Core çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ec967-205">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="ec967-206">Yalnızca .NET Core SDK'ları kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ec967-206">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="ec967-207">Ayrıntılı lık düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ec967-207">Sets the verbosity level.</span></span> <span data-ttu-id="ec967-208">İzin verilen `q[uiet]` `m[inimal]`değerler `n[ormal]` `d[etailed]`, `diag[nostic]`, , , ve .</span><span class="sxs-lookup"><span data-stu-id="ec967-208">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="ec967-209">Varsayılan değer: `normal`.</span><span class="sxs-lookup"><span data-stu-id="ec967-209">The default value is `normal`.</span></span>
  
* <span data-ttu-id="ec967-210">**`--force`** Visual Studio veya SDK'lar tarafından kullanılabilecek sürümlerin kaldırılmasını zorlar.</span><span class="sxs-lookup"><span data-stu-id="ec967-210">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="ec967-211">Notlar:</span><span class="sxs-lookup"><span data-stu-id="ec967-211">Notes:</span></span>

1. <span data-ttu-id="ec967-212">Tam olarak `--sdk` `--runtime` biri ve gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ec967-212">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="ec967-213">`--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , , ve münhasırdır.</span><span class="sxs-lookup"><span data-stu-id="ec967-213">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="ec967-214">Örnekler</span><span class="sxs-lookup"><span data-stu-id="ec967-214">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="ec967-215">Varsayılan olarak, .NET Core SDK'lar ve Visual Studio veya diğer SDK'lar tarafından `dotnet-core-uninstall dry-run` gerekli olabilecek çalışma süreleri çıktıya dahil edilmez.</span><span class="sxs-lookup"><span data-stu-id="ec967-215">By default, .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs are not included in `dotnet-core-uninstall dry-run` output.</span></span> <span data-ttu-id="ec967-216">Aşağıdaki örneklerde, makinenin durumuna bağlı olarak, belirtilen SDK'lardan ve çalışma sürelerinden bazıları çıktıya dahil edilemez.</span><span class="sxs-lookup"><span data-stu-id="ec967-216">In the following examples, some of the specified SDKs and runtimes may not be included in the output, depending on the state of the machine.</span></span> <span data-ttu-id="ec967-217">Tüm SDK'ları ve çalışma sürelerini eklemek için bunları `--force` açıkça bağımsız değişken olarak listeleyin veya seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="ec967-217">To include all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="ec967-218">Daha yüksek yamalar tarafından yerini almış tüm .NET Core runtimes kaldırma kuru çalışma:</span><span class="sxs-lookup"><span data-stu-id="ec967-218">Dry run of removing all .NET Core runtimes that have been superseded by higher patches:</span></span>

  ```console
  dotnet-core-uninstall dry-run --all-lower-patches --runtime
  ```

* <span data-ttu-id="ec967-219">Sürüm `2.2.301`altındaki tüm .NET Core SDK'ları kaldırmanın kuru çalıştırılması:</span><span class="sxs-lookup"><span data-stu-id="ec967-219">Dry run of removing all .NET Core SDKs below the version `2.2.301`:</span></span>

  ```console
  dotnet-core-uninstall whatif --all-below 2.2.301 --sdk
  ```

### <a name="step-3---uninstall-net-core-sdks-and-runtimes"></a><span data-ttu-id="ec967-220">Adım 3 - .NET Çekirdek SDK'ları ve Çalışma Sürelerini Kaldır</span><span class="sxs-lookup"><span data-stu-id="ec967-220">Step 3 - Uninstall .NET Core SDKs and Runtimes</span></span>

<span data-ttu-id="ec967-221">`dotnet-core-uninstall remove`bir seçenek koleksiyonu tarafından belirtilen .NET Core SDK'ları ve Runtimes'ı yükler.</span><span class="sxs-lookup"><span data-stu-id="ec967-221">`dotnet-core-uninstall remove` uninstalls .NET Core SDKs and Runtimes that are specified by a collection of options.</span></span> <span data-ttu-id="ec967-222">Araç, Sürüm 5.0 veya üzeri sürümile SDK'ları ve Runtimes'ı kaldırmak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="ec967-222">The tool can't be used to uninstall SDKs and Runtimes with version 5.0 or above.</span></span>

<span data-ttu-id="ec967-223">Bu araç yıkıcı bir davranışa sahip olduğundan, kaldırma komutunu çalıştırmadan önce kuru bir çalışma yapmanız **önerilir.**</span><span class="sxs-lookup"><span data-stu-id="ec967-223">Since this tool has a destructive behavior, it's **highly** recommended that you do a dry run before running the remove command.</span></span> <span data-ttu-id="ec967-224">Kuru çalıştırma, `remove` komutu kullandığınızda .NET Core SDK'ların ve çalışma sürelerinin ne kadar kaldırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ec967-224">The dry run will show you what .NET Core SDKs and runtimes will be removed when you use the `remove` command.</span></span> <span data-ttu-id="ec967-225">Hangi SDK'ların ve çalışma sürelerinin kaldırılmasının güvenli olduğunu öğrenmek için [bir sürümü kaldırmam gerekir mi?](../versions/remove-runtime-sdk-versions.md#should-i-remove-a-version)</span><span class="sxs-lookup"><span data-stu-id="ec967-225">Refer to [Should I remove a version?](../versions/remove-runtime-sdk-versions.md#should-i-remove-a-version) to learn which SDKs and runtimes are safe to remove.</span></span>

> [!CAUTION]
> <span data-ttu-id="ec967-226">Aşağıdaki uyarılara dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="ec967-226">Keep in mind the following caveats:</span></span>
>
>- <span data-ttu-id="ec967-227">Bu araç, makinenizdeki dosyalar tarafından `global.json` gerekli olan .NET Core SDK sürümlerini kaldırabilir.</span><span class="sxs-lookup"><span data-stu-id="ec967-227">This tool can uninstall versions of the .NET Core SDK that are required by `global.json` files on your machine.</span></span> <span data-ttu-id="ec967-228">.NET Core SDK'larını [İndir .NET Core](https://dotnet.microsoft.com/download/dotnet-core) sayfasından yeniden yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec967-228">You can reinstall .NET Core SDKs from the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>
>- <span data-ttu-id="ec967-229">Bu araç, .NET Core çalışma zamanının, makinenizdeki çerçeveye bağımlı uygulamalar tarafından gerekli olan sürümlerini kaldırabilir.</span><span class="sxs-lookup"><span data-stu-id="ec967-229">This tool can uninstall versions of the .NET Core runtime that are required by framework dependent applications on your machine.</span></span> <span data-ttu-id="ec967-230">.NET Core çalışma saatlerini [İndir .NET Core](https://dotnet.microsoft.com/download/dotnet-core) sayfasından yeniden yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec967-230">You can reinstall .NET Core runtimes from the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>
>- <span data-ttu-id="ec967-231">Bu araç, .NET Core SDK sürümlerini ve Visual Studio'nun güvendiği çalışma süresini kaldırabilir.</span><span class="sxs-lookup"><span data-stu-id="ec967-231">This tool can uninstall versions of the .NET Core SDK and runtime that Visual Studio relies on.</span></span> <span data-ttu-id="ec967-232">Visual Studio yüklemenizi bozarsanız, çalışma durumuna geri dönmek için Visual Studio yükleyicisinde "Onarım"ı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ec967-232">If you break your Visual Studio installation, run "Repair" in the Visual Studio installer to get back to a working state.</span></span>

<span data-ttu-id="ec967-233">Varsayılan olarak, tüm komutlar .NET Core SDK'larını ve Visual Studio veya diğer SDK'lar tarafından gerekli olabilecek çalışma sürelerini tutar.</span><span class="sxs-lookup"><span data-stu-id="ec967-233">By default, all commands keep the .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs.</span></span> <span data-ttu-id="ec967-234">Bu SDK'lar ve çalışma süreleri, bunları açıkça bağımsız değişken olarak `--force` listeleyerek veya seçeneği kullanarak kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="ec967-234">These SDKs and runtimes can be uninstalled by listing them explicitly as arguments or by using the `--force` option.</span></span>

<span data-ttu-id="ec967-235">Araç .NET Core SDK'ları ve çalışma sürelerini kaldırmak için yükseklik gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ec967-235">The tool requires elevation to uninstall .NET Core SDKs and runtimes.</span></span> <span data-ttu-id="ec967-236">Aracı Windows'da ve `sudo` macOS'ta bir Yönetici komut isteminde çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ec967-236">Run the tool in an Administrator command prompt on Windows and with `sudo` on macOS.</span></span> <span data-ttu-id="ec967-237">Ve `dry-run` `whatif` komutları yükseklik gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="ec967-237">The `dry-run` and `whatif` commands don't require elevation.</span></span>

<span data-ttu-id="ec967-238">**dotnet-core-uninstall kaldırma**</span><span class="sxs-lookup"><span data-stu-id="ec967-238">**dotnet-core-uninstall remove**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="ec967-239">Özet</span><span class="sxs-lookup"><span data-stu-id="ec967-239">Synopsis</span></span>

```console
dotnet-core-uninstall remove [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="ec967-240">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="ec967-240">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="ec967-241">Kaldırmak için belirtilen sürüm.</span><span class="sxs-lookup"><span data-stu-id="ec967-241">The specified version to uninstall.</span></span> <span data-ttu-id="ec967-242">Boşluklara göre ayrılmış birkaç sürümü birbiri ardına listeleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec967-242">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="ec967-243">Yanıt dosyaları da desteklenir.</span><span class="sxs-lookup"><span data-stu-id="ec967-243">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="ec967-244">Yanıt dosyaları, tüm sürümleri komut satırına yerleştirmek için bir alternatiftir.</span><span class="sxs-lookup"><span data-stu-id="ec967-244">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="ec967-245">Bunlar genellikle \*.rsp uzantılı metin dosyalarıdır ve her sürüm ayrı bir satırda listelenir.</span><span class="sxs-lookup"><span data-stu-id="ec967-245">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="ec967-246">`VERSION` Bağımsız değişken için yanıt dosyası belirtmek \@ için, yanıt dosyası adını hemen izleyen karakteri kullanın.</span><span class="sxs-lookup"><span data-stu-id="ec967-246">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="ec967-247">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="ec967-247">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="ec967-248">Windows</span><span class="sxs-lookup"><span data-stu-id="ec967-248">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="ec967-249">Tüm .NET Core SDK'ları ve çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ec967-249">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="ec967-250">Yalnızca .NET Core SDK'ları ve çalışma sürelerini belirtilen sürümden daha küçük bir sürümle kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ec967-250">Removes only the .NET Core SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="ec967-251">Belirtilen sürüm yüklü kalır.</span><span class="sxs-lookup"><span data-stu-id="ec967-251">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="ec967-252">Belirtilen sürümler dışında tüm .NET Core SDK'ları ve çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ec967-252">Removes all .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="ec967-253">.NET Core SDK'ları ve çalışma sürelerini, en yüksek sürüm hariç kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ec967-253">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="ec967-254">.NET Core SDK'ları ve daha yüksek düzeltme eki ile değiştirilen çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ec967-254">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="ec967-255">Bu seçenek global.json'ı korur.</span><span class="sxs-lookup"><span data-stu-id="ec967-255">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="ec967-256">.NET Core SDK'ları ve önizleme olarak işaretlenmiş çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ec967-256">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="ec967-257">.NET Core SDK'ları ve en yüksek önizleme dışında önizleme olarak işaretlenmiş çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ec967-257">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="ec967-258">Yalnızca Core çalışma sürelerini ASP.NET kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ec967-258">Removes ASP.NET Core runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="ec967-259">.NET Core çalışma süresini ve yalnızca barındırma paketlerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ec967-259">Removes .NET Core runtime and hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="ec967-260">.NET Core SDK'ları ve belirtilen `major.minor` sürümle eşleşen çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ec967-260">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="ec967-261">Yalnızca .NET Core çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ec967-261">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="ec967-262">Yalnızca .NET Core SDK'ları kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ec967-262">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="ec967-263">Ayrıntılı lık düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ec967-263">Sets the verbosity level.</span></span> <span data-ttu-id="ec967-264">İzin verilen `q[uiet]` `m[inimal]`değerler `n[ormal]` `d[etailed]`, `diag[nostic]`, , , ve .</span><span class="sxs-lookup"><span data-stu-id="ec967-264">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="ec967-265">Varsayılan değer: `normal`.</span><span class="sxs-lookup"><span data-stu-id="ec967-265">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="ec967-266">`--sdk`X64 `--runtime` `--aspnet-runtime` SDK'lar veya çalışma süreleri ile kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ec967-266">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="ec967-267">`--sdk`X86 SDK'ları veya çalışma sürelerini kaldırmak `--aspnet-runtime` için , ve `--runtime`kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ec967-267">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="ec967-268">**`-y, --yes`** Evet veya hayır onayı gerektirmeden komutu yürütür.</span><span class="sxs-lookup"><span data-stu-id="ec967-268">**`-y, --yes`** Executes the command without requiring a yes or no confirmation.</span></span>

* <span data-ttu-id="ec967-269">**`--force`** Visual Studio tarafından kullanılabilecek sürümlerin kaldırılmasını zorlar.</span><span class="sxs-lookup"><span data-stu-id="ec967-269">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="ec967-270">Notlar:</span><span class="sxs-lookup"><span data-stu-id="ec967-270">Notes:</span></span>

1. <span data-ttu-id="ec967-271">Tam olarak `--sdk` `--runtime`biri `--aspnet-runtime`, `--hosting-bundle` , , ve gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ec967-271">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="ec967-272">`--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , , ve münhasırdır.</span><span class="sxs-lookup"><span data-stu-id="ec967-272">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="ec967-273">Belirtilmemişse `--x64` veya `--x86` belirtilmemişse, hem x64 hem de x86 kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="ec967-273">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macos"></a>[<span data-ttu-id="ec967-274">Macos</span><span class="sxs-lookup"><span data-stu-id="ec967-274">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="ec967-275">Tüm .NET Core SDK'ları ve çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ec967-275">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="ec967-276">.NET Core SDK'ları ve çalışma sürelerini belirtilen sürümün altında kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ec967-276">Removes .NET Core SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="ec967-277">Belirtilen sürüm kalır.</span><span class="sxs-lookup"><span data-stu-id="ec967-277">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="ec967-278">Belirtilen sürümler dışında .NET Core SDK'ları ve çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ec967-278">Removes .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="ec967-279">.NET Core SDK'ları ve çalışma sürelerini, en yüksek sürüm hariç kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ec967-279">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="ec967-280">.NET Core SDK'ları ve daha yüksek düzeltme eki ile değiştirilen çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ec967-280">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="ec967-281">Bu seçenek global.json'ı korur.</span><span class="sxs-lookup"><span data-stu-id="ec967-281">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="ec967-282">.NET Core SDK'ları ve önizleme olarak işaretlenmiş çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ec967-282">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="ec967-283">.NET Core SDK'ları ve en yüksek önizleme dışında önizleme olarak işaretlenmiş çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ec967-283">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="ec967-284">.NET Core SDK'ları ve belirtilen `major.minor` sürümle eşleşen çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ec967-284">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="ec967-285">Yalnızca .NET Core çalışma sürelerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ec967-285">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="ec967-286">Yalnızca .NET Core SDK'ları kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ec967-286">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="ec967-287">Ayrıntılı lık düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ec967-287">Sets the verbosity level.</span></span> <span data-ttu-id="ec967-288">İzin verilen `q[uiet]` `m[inimal]`değerler `n[ormal]` `d[etailed]`, `diag[nostic]`, , , ve .</span><span class="sxs-lookup"><span data-stu-id="ec967-288">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="ec967-289">Varsayılan değer: `normal`.</span><span class="sxs-lookup"><span data-stu-id="ec967-289">The default value is `normal`.</span></span>

* <span data-ttu-id="ec967-290">**`-y, --yes`** Y/N onayı gerektirmeden komutu yürütür.</span><span class="sxs-lookup"><span data-stu-id="ec967-290">**`-y, --yes`** Executes the command without requiring Y/N confirmation.</span></span>
  
* <span data-ttu-id="ec967-291">**`--force`** Visual Studio veya SDK'lar tarafından kullanılabilecek sürümlerin kaldırılmasını zorlar.</span><span class="sxs-lookup"><span data-stu-id="ec967-291">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="ec967-292">Notlar:</span><span class="sxs-lookup"><span data-stu-id="ec967-292">Notes:</span></span>

1. <span data-ttu-id="ec967-293">Tam olarak `--sdk` `--runtime` biri ve gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ec967-293">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="ec967-294">`--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , , ve münhasırdır.</span><span class="sxs-lookup"><span data-stu-id="ec967-294">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="ec967-295">Örnekler</span><span class="sxs-lookup"><span data-stu-id="ec967-295">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="ec967-296">Varsayılan olarak, .NET Core SDK'lar ve Visual Studio veya diğer SDK'lar tarafından gerekli olabilecek çalışma süreleri tutulur.</span><span class="sxs-lookup"><span data-stu-id="ec967-296">By default, .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs are kept.</span></span> <span data-ttu-id="ec967-297">Aşağıdaki örneklerde, makinenin durumuna bağlı olarak belirtilen SDK'lardan ve çalışma sürelerinden bazıları kalabilir.</span><span class="sxs-lookup"><span data-stu-id="ec967-297">In the following examples, some of the specified SDKs and runtimes may remain, depending on the state of the machine.</span></span> <span data-ttu-id="ec967-298">Tüm SDK'ları ve çalışma sürelerini kaldırmak için bunları `--force` açıkça bağımsız değişken olarak listeleyin veya seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="ec967-298">To remove all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="ec967-299">Y/N onayı gerektirmeden sürüm `3.0.0-preview6-27804-01` dışındaki tüm .NET Core çalışma sürelerini kaldırın:</span><span class="sxs-lookup"><span data-stu-id="ec967-299">Remove all .NET Core runtimes except the version `3.0.0-preview6-27804-01` without requiring Y/N confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --all-but 3.0.0-preview6-27804-01 --runtime --yes
  ```

* <span data-ttu-id="ec967-300">Y/n onayı gerektirmeden tüm .NET Core 1.1 SDK'larını kaldırın:</span><span class="sxs-lookup"><span data-stu-id="ec967-300">Remove all .NET Core 1.1 SDKs without requiring Y/n confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --sdk --major-minor 1.1 -y
  ```

* <span data-ttu-id="ec967-301">.NET Core 1.1.11 SDK konsol çıkışı olmadan kaldırın:</span><span class="sxs-lookup"><span data-stu-id="ec967-301">Remove the .NET Core 1.1.11 SDK with no console output:</span></span>

  ```console
  dotnet-core-uninstall remove 1.1.11 --sdk --yes --verbosity q
  ```

* <span data-ttu-id="ec967-302">Bu araç tarafından güvenli bir şekilde çıkarılabilen tüm .NET Core SDK'larını kaldırın:</span><span class="sxs-lookup"><span data-stu-id="ec967-302">Remove all .NET Core SDKs that can safely be removed by this tool:</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk
  ```

* <span data-ttu-id="ec967-303">Visual Studio tarafından gerekli olabilecek SDK'lar da dahil olmak üzere bu araç tarafından kaldırılabilecek tüm .NET Core SDK'larını kaldırın (önerilmez):</span><span class="sxs-lookup"><span data-stu-id="ec967-303">Remove all .NET Core SDKs that can be removed by this tool, including those SDKs that may be required by Visual Studio (not recommended):</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk --force
  ```

* <span data-ttu-id="ec967-304">Yanıt dosyasında belirtilen tüm .NET Core SDK'ları kaldırma`versions.rsp`</span><span class="sxs-lookup"><span data-stu-id="ec967-304">Remove all .NET Core SDKs that are specified in the response file `versions.rsp`</span></span>

  ```console
  dotnet-core-uninstall remove --sdk @versions.rsp
  ```

  <span data-ttu-id="ec967-305">*versions.rsp* içeriği aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="ec967-305">The content of *versions.rsp* is as follows:</span></span>
  
  ```text
  2.2.300
  2.1.700
  ```

### <a name="step-4---delete-the-nuget-fallback-folder-optional"></a><span data-ttu-id="ec967-306">Adım 4 - NuGet geri dönüş klasörünü silin (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="ec967-306">Step 4 - Delete the NuGet fallback folder (optional)</span></span>

<span data-ttu-id="ec967-307">Bazı durumlarda, artık ihtiyacınız `NuGetFallbackFolder` yok ve silmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec967-307">In some cases, you no longer need the `NuGetFallbackFolder` and may wish to delete it.</span></span> <span data-ttu-id="ec967-308">Bu klasörü silme hakkında daha fazla bilgi için [NuGetFallbackFolder'ı Kaldır'a](../versions/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder)bakın.</span><span class="sxs-lookup"><span data-stu-id="ec967-308">For more information about deleting this folder, see [Remove the NuGetFallbackFolder](../versions/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).</span></span>

## <a name="uninstall-the-tool"></a><span data-ttu-id="ec967-309">Aracı kaldırma</span><span class="sxs-lookup"><span data-stu-id="ec967-309">Uninstall the tool</span></span>

## <a name="windows"></a>[<span data-ttu-id="ec967-310">Windows</span><span class="sxs-lookup"><span data-stu-id="ec967-310">Windows</span></span>](#tab/windows)

1. <span data-ttu-id="ec967-311">**Program Ekle veya Kaldır'ı**aç.</span><span class="sxs-lookup"><span data-stu-id="ec967-311">Open **Add or Remove Programs**.</span></span>
2. <span data-ttu-id="ec967-312">`Microsoft .NET Core SDK Uninstall Tool` arayın.</span><span class="sxs-lookup"><span data-stu-id="ec967-312">Search for `Microsoft .NET Core SDK Uninstall Tool`.</span></span>
3. <span data-ttu-id="ec967-313">**Kaldır**'ı seçin.</span><span class="sxs-lookup"><span data-stu-id="ec967-313">Select **Uninstall**.</span></span>

## <a name="macos"></a>[<span data-ttu-id="ec967-314">Macos</span><span class="sxs-lookup"><span data-stu-id="ec967-314">macOS</span></span>](#tab/macos)

<span data-ttu-id="ec967-315">İndirilen *dotnet-core-uninstall.tar.gz* dosyasını yüklendiği dizinden silin.</span><span class="sxs-lookup"><span data-stu-id="ec967-315">Delete the downloaded *dotnet-core-uninstall.tar.gz* file from the directory where it was installed.</span></span> <span data-ttu-id="ec967-316">Bu dosyanın içeriğini başka bir dizine açtıysanız, bu içeriği de sildiğimden emin olun.</span><span class="sxs-lookup"><span data-stu-id="ec967-316">If you unzipped the contents of this file into another directory, be sure to delete that content as well.</span></span>

---
