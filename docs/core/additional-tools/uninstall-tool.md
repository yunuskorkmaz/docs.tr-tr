---
title: Aracı kaldır
description: .NET Core SDK 'Ları ve çalışma zamanlarını denetimli temizleme işlemini sağlayan kılavuzlu bir araç olan .NET Core kaldırma aracına genel bakış.
author: sfoslund
ms.date: 01/06/2020
ms.openlocfilehash: 4944c983cbd02b456c3a09a1b03bc28ba6e458cc
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714547"
---
# <a name="net-core-uninstall-tool"></a><span data-ttu-id="dfadf-103">.NET Core Kaldırma Aracı</span><span class="sxs-lookup"><span data-stu-id="dfadf-103">.NET Core Uninstall Tool</span></span>

<span data-ttu-id="dfadf-104">[.NET Core kaldırma aracı](https://github.com/dotnet/cli-lab/releases) (`dotnet-core-uninstall`), bir sistemden .NET Core SDK 'larını ve çalışma zamanlarını kaldırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="dfadf-104">The [.NET Core Uninstall Tool](https://github.com/dotnet/cli-lab/releases) (`dotnet-core-uninstall`) lets you remove .NET Core SDKs and Runtimes from a system.</span></span> <span data-ttu-id="dfadf-105">Kaldırmak istediğiniz sürümleri belirlemek için bir seçenek koleksiyonu kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dfadf-105">A collection of options is available to specify which versions you want to uninstall.</span></span>

<span data-ttu-id="dfadf-106">Araç Windows ve macOS 'yi destekler.</span><span class="sxs-lookup"><span data-stu-id="dfadf-106">The tool supports Windows and macOS.</span></span> <span data-ttu-id="dfadf-107">Linux Şu anda desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="dfadf-107">Linux is currently not supported.</span></span>

<span data-ttu-id="dfadf-108">Bu araç, Windows 'ta yalnızca aşağıdaki yükleyicilerden biri kullanılarak yüklenen SDK 'Ları ve çalışma zamanlarını kaldırabilir:</span><span class="sxs-lookup"><span data-stu-id="dfadf-108">On Windows, the tool can only uninstall SDKs and Runtimes that were installed using one of the following installers:</span></span>

- <span data-ttu-id="dfadf-109">.NET Core SDK ve çalışma zamanı yükleyicisi.</span><span class="sxs-lookup"><span data-stu-id="dfadf-109">The .NET Core SDK and runtime installer.</span></span>
- <span data-ttu-id="dfadf-110">Visual Studio 2019 sürüm 16,3 ' den önceki sürümlerde Visual Studio yükleyicisi.</span><span class="sxs-lookup"><span data-stu-id="dfadf-110">The Visual Studio installer in versions earlier than Visual Studio 2019 version 16.3.</span></span>

<span data-ttu-id="dfadf-111">MacOS 'ta, araç yalnızca */usr/local/share/DotNet* klasöründe bulunan SDK 'ları ve çalışma zamanlarını kaldırabilir.</span><span class="sxs-lookup"><span data-stu-id="dfadf-111">On macOS, the tool can only uninstall SDKs and runtimes located in the */usr/local/share/dotnet* folder.</span></span>

<span data-ttu-id="dfadf-112">Bu sınırlamalar nedeniyle araç, makinenizde tüm .NET Core SDK 'larını ve çalışma zamanlarını kaldıramayabilir.</span><span class="sxs-lookup"><span data-stu-id="dfadf-112">Because of these limitations, the tool may not be able to uninstall all of the .NET Core SDKs and runtimes on your machine.</span></span> <span data-ttu-id="dfadf-113">Bu aracın kaldırakaldıramıyorum Bu SDK 'lar ve çalışma zamanları dahil tüm .NET Core SDK 'larını ve çalışma zamanlarını bulmak için `dotnet --info` komutunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dfadf-113">You can use the `dotnet --info` command to find all of the .NET Core SDKs and runtimes installed, including those SDKs and runtimes that this tool can't remove.</span></span> <span data-ttu-id="dfadf-114">`dotnet-core-uninstall list` komutu, araçla hangi SDK 'ların kaldırılabileceği görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="dfadf-114">The `dotnet-core-uninstall list` command displays which SDKs can be uninstalled with the tool.</span></span>

## <a name="install-the-tool"></a><span data-ttu-id="dfadf-115">Aracı 'nı yükler</span><span class="sxs-lookup"><span data-stu-id="dfadf-115">Install the tool</span></span>

<span data-ttu-id="dfadf-116">.NET Core kaldırma aracını [DotNet/CLI-Lab](https://github.com/dotnet/cli-lab/releases) GitHub deposundan indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dfadf-116">You can download the .NET Core Uninstall Tool from the [dotnet/cli-lab](https://github.com/dotnet/cli-lab/releases) GitHub repository.</span></span>

> [!NOTE]
> <span data-ttu-id="dfadf-117">Aracın .NET Core SDK 'larını ve çalışma zamanlarını kaldırması için yükseltme gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="dfadf-117">The tool requires elevation to uninstall .NET Core SDKs and runtimes.</span></span> <span data-ttu-id="dfadf-118">Bu nedenle, Windows üzerinde *C:\Program Files* veya MacOS 'ta */usr/local/bin* gibi bir yazma korumalı dizine yüklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="dfadf-118">Therefore, it should be installed in a write-protected directory such as *C:\Program Files* on Windows or */usr/local/bin* on macOS.</span></span> <span data-ttu-id="dfadf-119">Ayrıca bkz. [DotNet komutları Için yükseltilmiş erişim](../tools/elevated-access.md).</span><span class="sxs-lookup"><span data-stu-id="dfadf-119">See also [Elevated access for dotnet commands](../tools/elevated-access.md).</span></span> <span data-ttu-id="dfadf-120">Ayrıntılı yükleme yönergeleri [GitHub yayınları sayfasında](https://github.com/dotnet/cli-lab/releases)bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="dfadf-120">Detailed installation instructions are available on the [GitHub Releases page](https://github.com/dotnet/cli-lab/releases).</span></span>

## <a name="run-the-tool"></a><span data-ttu-id="dfadf-121">Aracı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="dfadf-121">Run the tool</span></span>

<span data-ttu-id="dfadf-122">Aşağıdaki adımlarda, kaldırma aracını çalıştırmak için önerilen yaklaşım gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="dfadf-122">The following steps show the recommended approach for running the uninstall tool:</span></span>

- [<span data-ttu-id="dfadf-123">1. adım-yüklü .NET Core SDK 'larını ve çalışma zamanlarını görüntüleme</span><span class="sxs-lookup"><span data-stu-id="dfadf-123">Step 1 - Display installed .NET Core SDKs and runtimes</span></span>](#step-1---display-installed-net-core-sdks-and-runtimes)
- [<span data-ttu-id="dfadf-124">2. adım-bir kuru çalıştırma</span><span class="sxs-lookup"><span data-stu-id="dfadf-124">Step 2 - Do a dry run</span></span>](#step-2---do-a-dry-run)
- [<span data-ttu-id="dfadf-125">3. adım-.NET Core SDK 'larını ve çalışma zamanlarını kaldırma</span><span class="sxs-lookup"><span data-stu-id="dfadf-125">Step 3 - Uninstall .NET Core SDKs and Runtimes</span></span>](#step-3---uninstall-net-core-sdks-and-runtimes)
- [<span data-ttu-id="dfadf-126">4. adım-NuGet geri dönüş klasörünü silme (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="dfadf-126">Step 4 - Delete the NuGet fallback folder (optional)</span></span>](#step-4---delete-the-nuget-fallback-folder-optional)

### <a name="step-1---display-installed-net-core-sdks-and-runtimes"></a><span data-ttu-id="dfadf-127">1\. adım-yüklü .NET Core SDK 'larını ve çalışma zamanlarını görüntüleme</span><span class="sxs-lookup"><span data-stu-id="dfadf-127">Step 1 - Display installed .NET Core SDKs and runtimes</span></span>

<span data-ttu-id="dfadf-128">`dotnet-core-uninstall list` komutu, bu araçla kaldırılabileceği yüklü .NET Core SDK 'larını ve çalışma zamanlarını listeler.</span><span class="sxs-lookup"><span data-stu-id="dfadf-128">The `dotnet-core-uninstall list` command lists the installed .NET Core SDKs and runtimes that can be removed with this tool.</span></span> <span data-ttu-id="dfadf-129">Bazı SDK 'lar ve çalışma zamanları Visual Studio için gerekli olabilir ve bunların kaldırılması önerilmez.</span><span class="sxs-lookup"><span data-stu-id="dfadf-129">Some SDKs and runtimes may be required by Visual Studio and they're displayed with a note of why it isn't recommended to uninstall them.</span></span>

<span data-ttu-id="dfadf-130">**DotNet-çekirdek-kaldırma listesi**</span><span class="sxs-lookup"><span data-stu-id="dfadf-130">**dotnet-core-uninstall list**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="dfadf-131">Özeti</span><span class="sxs-lookup"><span data-stu-id="dfadf-131">Synopsis</span></span>

```console
dotnet-core-uninstall list [options]
```

#### <a name="options"></a><span data-ttu-id="dfadf-132">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="dfadf-132">Options</span></span>

## <a name="windowstabwindows"></a>[<span data-ttu-id="dfadf-133">Windows</span><span class="sxs-lookup"><span data-stu-id="dfadf-133">Windows</span></span>](#tab/windows)

* **`--aspnet-runtime`**

  <span data-ttu-id="dfadf-134">Bu araçla kaldırılabilecek tüm ASP.NET Core çalışma zamanlarını listeler.</span><span class="sxs-lookup"><span data-stu-id="dfadf-134">Lists all the ASP.NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="dfadf-135">Bu araçla kaldırılabilecek tüm .NET Core çalışma zamanını ve barındırma paketlerini listeler.</span><span class="sxs-lookup"><span data-stu-id="dfadf-135">Lists all the .NET Core runtime and hosting bundles that can be uninstalled with this tool.</span></span>

* **`--runtime`**

  <span data-ttu-id="dfadf-136">Bu araçla kaldırılabilecek tüm .NET Core çalışma zamanlarını listeler.</span><span class="sxs-lookup"><span data-stu-id="dfadf-136">Lists all .NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="dfadf-137">Bu araçla kaldırılabilecek tüm .NET Core SDK 'larını listeler.</span><span class="sxs-lookup"><span data-stu-id="dfadf-137">Lists all .NET Core SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="dfadf-138">Ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="dfadf-138">Sets the verbosity level.</span></span> <span data-ttu-id="dfadf-139">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="dfadf-139">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="dfadf-140">Varsayılan değer `normal` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="dfadf-140">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="dfadf-141">Bu araçla kaldırılabilecek tüm x64 .NET Core SDK 'larını ve çalışma zamanlarını listeler.</span><span class="sxs-lookup"><span data-stu-id="dfadf-141">Lists all x64 .NET Core SDKs and runtimes that can be uninstalled with this tool.</span></span>

* **`--x86`**

  <span data-ttu-id="dfadf-142">Bu araçla kaldırılabilecek tüm x86 .NET Core SDK 'larını ve çalışma zamanlarını listeler.</span><span class="sxs-lookup"><span data-stu-id="dfadf-142">Lists all x86 .NET Core SDKs and runtimes that can be uninstalled with this tool.</span></span>

## <a name="macostabmacos"></a>[<span data-ttu-id="dfadf-143">macOS</span><span class="sxs-lookup"><span data-stu-id="dfadf-143">macOS</span></span>](#tab/macos)

* **`--runtime`**

  <span data-ttu-id="dfadf-144">Bu araçla kaldırılabilecek tüm .NET Core çalışma zamanlarını listeler.</span><span class="sxs-lookup"><span data-stu-id="dfadf-144">Lists all .NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="dfadf-145">Bu araçla kaldırılabilecek tüm .NET Core SDK 'larını listeler.</span><span class="sxs-lookup"><span data-stu-id="dfadf-145">Lists all .NET Core SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="dfadf-146">Ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="dfadf-146">Sets the verbosity level.</span></span> <span data-ttu-id="dfadf-147">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="dfadf-147">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="dfadf-148">Varsayılan değer `normal` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="dfadf-148">The default value is `normal`.</span></span>
  
---

#### <a name="examples"></a><span data-ttu-id="dfadf-149">Örnekler</span><span class="sxs-lookup"><span data-stu-id="dfadf-149">Examples</span></span>

* <span data-ttu-id="dfadf-150">Bu araçla kaldırılabileceği tüm .NET Core SDK 'larını ve çalışma zamanlarını listeleyin:</span><span class="sxs-lookup"><span data-stu-id="dfadf-150">List all .NET Core SDKs and runtimes that can be removed with this tool:</span></span>

  ```console
  dotnet-core-uninstall list
  ```

* <span data-ttu-id="dfadf-151">Tüm x64 .NET Core SDK 'larını ve çalışma zamanlarını listeleyin:</span><span class="sxs-lookup"><span data-stu-id="dfadf-151">List all x64 .NET Core SDKs and runtimes:</span></span>

  ```console
  dotnet-core-uninstall list --x64
  ```

* <span data-ttu-id="dfadf-152">Tüm x86 .NET Core SDK 'larını listeleyin:</span><span class="sxs-lookup"><span data-stu-id="dfadf-152">List all x86 .NET Core SDKs:</span></span>

  ```console
  dotnet-core-uninstall list --sdk --x86
  ```

### <a name="step-2---do-a-dry-run"></a><span data-ttu-id="dfadf-153">2\. adım-bir kuru çalıştırma</span><span class="sxs-lookup"><span data-stu-id="dfadf-153">Step 2 - Do a dry run</span></span>

<span data-ttu-id="dfadf-154">`dotnet-core-uninstall dry-run` ve `dotnet-core-uninstall whatif` komutları, kaldırma işlemi yapılmadan belirtilen seçeneklere göre kaldırılacak .NET Core SDK 'larını ve çalışma zamanlarını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="dfadf-154">The `dotnet-core-uninstall dry-run` and `dotnet-core-uninstall whatif` commands display the .NET Core SDKs and runtimes that will be removed based on the options provided without performing the uninstall.</span></span> <span data-ttu-id="dfadf-155">Bu komutlar eş anlamlılardır.</span><span class="sxs-lookup"><span data-stu-id="dfadf-155">These commands are synonyms.</span></span>

<span data-ttu-id="dfadf-156">**DotNet-çekirdek-kaldırma kuru çalıştırma ve DotNet-çekirdek-kaldırma whatIf**</span><span class="sxs-lookup"><span data-stu-id="dfadf-156">**dotnet-core-uninstall dry-run and dotnet-core-uninstall whatif**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="dfadf-157">Özeti</span><span class="sxs-lookup"><span data-stu-id="dfadf-157">Synopsis</span></span>

```console
dotnet-core-uninstall dry-run [options] [<VERSION>...]

dotnet-core-uninstall whatif [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="dfadf-158">Arguments</span><span class="sxs-lookup"><span data-stu-id="dfadf-158">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="dfadf-159">Kaldırılacak belirtilen sürüm.</span><span class="sxs-lookup"><span data-stu-id="dfadf-159">The specified version to uninstall.</span></span> <span data-ttu-id="dfadf-160">Birden çok sürümü, boşluklarla ayırarak, birbirinden daha sonra listeleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dfadf-160">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="dfadf-161">Yanıt dosyaları da desteklenir.</span><span class="sxs-lookup"><span data-stu-id="dfadf-161">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="dfadf-162">Yanıt dosyaları, tüm sürümlerin komut satırına yerleştirilmesi için bir alternatiftir.</span><span class="sxs-lookup"><span data-stu-id="dfadf-162">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="dfadf-163">Genellikle \*. rsp uzantılı metin dosyalarıdır ve her sürüm ayrı bir satırda listelenir.</span><span class="sxs-lookup"><span data-stu-id="dfadf-163">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="dfadf-164">`VERSION` bağımsız değişkenine bir yanıt dosyası belirtmek için, yanıt dosyası adının hemen ardından \@ karakterini kullanın.</span><span class="sxs-lookup"><span data-stu-id="dfadf-164">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="dfadf-165">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="dfadf-165">Options</span></span>

## <a name="windowstabwindows"></a>[<span data-ttu-id="dfadf-166">Windows</span><span class="sxs-lookup"><span data-stu-id="dfadf-166">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="dfadf-167">Tüm .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="dfadf-167">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="dfadf-168">Yalnızca .NET Core SDK 'larını ve çalışma zamanlarını belirtilen sürümden daha küçük bir sürüme kaldırır.</span><span class="sxs-lookup"><span data-stu-id="dfadf-168">Removes only the .NET Core SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="dfadf-169">Belirtilen sürüm yüklü durumda kalır.</span><span class="sxs-lookup"><span data-stu-id="dfadf-169">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="dfadf-170">Belirtilen sürümler hariç tüm .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="dfadf-170">Removes all .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="dfadf-171">En yüksek sürüm dışında .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="dfadf-171">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="dfadf-172">Daha yüksek düzeltme eklerinin yerine geçen .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="dfadf-172">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="dfadf-173">Bu seçenek Global. JSON korumasını korur.</span><span class="sxs-lookup"><span data-stu-id="dfadf-173">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="dfadf-174">Önizleme olarak işaretlenen .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="dfadf-174">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="dfadf-175">En yüksek önizleme dışında, önizleme olarak işaretlenen .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="dfadf-175">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="dfadf-176">Yalnızca ASP.NET Core çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="dfadf-176">Removes ASP.NET Core runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="dfadf-177">Yalnızca .NET Core çalışma zamanı ve barındırma paketleri kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="dfadf-177">Removes .NET Core runtime and hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="dfadf-178">Belirtilen `major.minor` sürümüyle eşleşen .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="dfadf-178">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="dfadf-179">Yalnızca .NET Core çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="dfadf-179">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="dfadf-180">Yalnızca .NET Core SDK 'larını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="dfadf-180">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="dfadf-181">Ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="dfadf-181">Sets the verbosity level.</span></span> <span data-ttu-id="dfadf-182">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="dfadf-182">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="dfadf-183">Varsayılan değer `normal` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="dfadf-183">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="dfadf-184">X64 SDK 'larını veya çalışma zamanlarını kaldırmak için `--sdk`, `--runtime`ve `--aspnet-runtime` birlikte kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dfadf-184">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="dfadf-185">X86 SDK 'larını veya çalışma zamanlarını kaldırmak için `--sdk`, `--runtime`ve `--aspnet-runtime` birlikte kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dfadf-185">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="dfadf-186">**`--force`** Visual Studio tarafından kullanılabilecek sürümlerin kaldırılmasını zorlar.</span><span class="sxs-lookup"><span data-stu-id="dfadf-186">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="dfadf-187">Notlar:</span><span class="sxs-lookup"><span data-stu-id="dfadf-187">Notes:</span></span>

1. <span data-ttu-id="dfadf-188">`--sdk`, `--runtime`, `--aspnet-runtime`ve `--hosting-bundle` tam olarak biri gereklidir.</span><span class="sxs-lookup"><span data-stu-id="dfadf-188">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="dfadf-189">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`ve `[<VERSION>...]` dışlamalı.</span><span class="sxs-lookup"><span data-stu-id="dfadf-189">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="dfadf-190">`--x64` veya `--x86` belirtilmemişse, hem x64 hem de x86 kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="dfadf-190">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macostabmacos"></a>[<span data-ttu-id="dfadf-191">macOS</span><span class="sxs-lookup"><span data-stu-id="dfadf-191">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="dfadf-192">Tüm .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="dfadf-192">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="dfadf-193">Belirtilen sürümün altındaki .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="dfadf-193">Removes .NET Core SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="dfadf-194">Belirtilen sürüm kalacak.</span><span class="sxs-lookup"><span data-stu-id="dfadf-194">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="dfadf-195">Bu sürümler dışında .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="dfadf-195">Removes .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="dfadf-196">En yüksek sürüm dışında .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="dfadf-196">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="dfadf-197">Daha yüksek düzeltme eklerinin yerine geçen .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="dfadf-197">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="dfadf-198">Bu seçenek Global. JSON korumasını korur.</span><span class="sxs-lookup"><span data-stu-id="dfadf-198">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="dfadf-199">Önizleme olarak işaretlenen .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="dfadf-199">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="dfadf-200">En yüksek önizleme dışında, önizleme olarak işaretlenen .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="dfadf-200">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="dfadf-201">Belirtilen `major.minor` sürümüyle eşleşen .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="dfadf-201">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="dfadf-202">Yalnızca .NET Core çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="dfadf-202">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="dfadf-203">Yalnızca .NET Core SDK 'larını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="dfadf-203">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="dfadf-204">Ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="dfadf-204">Sets the verbosity level.</span></span> <span data-ttu-id="dfadf-205">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="dfadf-205">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="dfadf-206">Varsayılan değer `normal` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="dfadf-206">The default value is `normal`.</span></span>
  
* <span data-ttu-id="dfadf-207">**`--force`** Visual Studio veya SDK 'lar tarafından kullanılan sürümlerin kaldırılmasını zorlar.</span><span class="sxs-lookup"><span data-stu-id="dfadf-207">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="dfadf-208">Notlar:</span><span class="sxs-lookup"><span data-stu-id="dfadf-208">Notes:</span></span>

1. <span data-ttu-id="dfadf-209">`--sdk` ve `--runtime` tam olarak biri gereklidir.</span><span class="sxs-lookup"><span data-stu-id="dfadf-209">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="dfadf-210">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`ve `[<VERSION>...]` dışlamalı.</span><span class="sxs-lookup"><span data-stu-id="dfadf-210">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="dfadf-211">Örnekler</span><span class="sxs-lookup"><span data-stu-id="dfadf-211">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="dfadf-212">Varsayılan olarak, Visual Studio veya diğer SDK 'lar tarafından gerekebilecek .NET Core SDK 'Ları ve çalışma zamanları `dotnet-core-uninstall dry-run` çıkışına dahil edilmez.</span><span class="sxs-lookup"><span data-stu-id="dfadf-212">By default, .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs are not included in `dotnet-core-uninstall dry-run` output.</span></span> <span data-ttu-id="dfadf-213">Aşağıdaki örneklerde, makinenin durumuna bağlı olarak belirtilen SDK ve çalışma zamanlarının bazıları çıkışa dahil edilmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="dfadf-213">In the following examples, some of the specified SDKs and runtimes may not be included in the output, depending on the state of the machine.</span></span> <span data-ttu-id="dfadf-214">Tüm SDK 'Ları ve çalışma zamanlarını dahil etmek için bunları açık bağımsız değişken olarak listeleyin veya `--force` seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="dfadf-214">To include all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="dfadf-215">Daha yüksek düzeltme eklerinin yerini aldığı tüm .NET Core çalışma zamanlarını kaldırma kuru:</span><span class="sxs-lookup"><span data-stu-id="dfadf-215">Dry run of removing all .NET Core runtimes that have been superseded by higher patches:</span></span>

  ```console
  dotnet-core-uninstall dry-run --all-lower-patches --runtime
  ```

* <span data-ttu-id="dfadf-216">`2.2.301`sürümünün altındaki tüm .NET Core SDK 'larını kaldırma konusunda Kuru çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="dfadf-216">Dry run of removing all .NET Core SDKs below the version `2.2.301`:</span></span>

  ```console
  dotnet-core-uninstall whatif --all-below 2.2.301 --sdk
  ```

### <a name="step-3---uninstall-net-core-sdks-and-runtimes"></a><span data-ttu-id="dfadf-217">3\. adım-.NET Core SDK 'larını ve çalışma zamanlarını kaldırma</span><span class="sxs-lookup"><span data-stu-id="dfadf-217">Step 3 - Uninstall .NET Core SDKs and Runtimes</span></span>

<span data-ttu-id="dfadf-218">`dotnet-core-uninstall remove`, .NET Core SDK 'larını ve bir seçenek koleksiyonuyla belirtilen çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="dfadf-218">`dotnet-core-uninstall remove` uninstalls .NET Core SDKs and Runtimes that are specified by a collection of options.</span></span> <span data-ttu-id="dfadf-219">Araç, sürüm 5,0 veya üzeri olan SDK 'Ları ve çalışma zamanlarını kaldırmak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="dfadf-219">The tool can't be used to uninstall SDKs and Runtimes with version 5.0 or above.</span></span>

<span data-ttu-id="dfadf-220">Bu aracın bozucu bir davranışı olduğundan, Kaldır komutunu çalıştırmadan önce bir kuru çalıştırma yapmanız **önemle** önerilir.</span><span class="sxs-lookup"><span data-stu-id="dfadf-220">Since this tool has a destructive behavior, it's **highly** recommended that you do a dry run before running the remove command.</span></span> <span data-ttu-id="dfadf-221">Kuru çalıştırma, `remove` komutunu kullandığınızda hangi .NET Core SDK 'larının ve çalışma zamanlarının kaldırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="dfadf-221">The dry run will show you what .NET Core SDKs and runtimes will be removed when you use the `remove` command.</span></span> <span data-ttu-id="dfadf-222">Hangi SDK 'ların ve çalışma zamanlarının kaldırılacağını öğrenmek için bkz. [bir sürümü kaldırmalıyım?](../versions/remove-runtime-sdk-versions.md#should-i-remove-a-version) .</span><span class="sxs-lookup"><span data-stu-id="dfadf-222">Refer to [Should I remove a version?](../versions/remove-runtime-sdk-versions.md#should-i-remove-a-version) to learn which SDKs and runtimes are safe to remove.</span></span>

> [!CAUTION]
> <span data-ttu-id="dfadf-223">Aşağıdaki uyarıları aklınızda bulundurun:</span><span class="sxs-lookup"><span data-stu-id="dfadf-223">Keep in mind the following caveats:</span></span>
>
>- <span data-ttu-id="dfadf-224">Bu araç, makinenizde `global.json` dosyaları için gereken .NET Core SDK sürümlerini kaldırabilir.</span><span class="sxs-lookup"><span data-stu-id="dfadf-224">This tool can uninstall versions of the .NET Core SDK that are required by `global.json` files on your machine.</span></span> <span data-ttu-id="dfadf-225">.NET Core SDK 'larını [indirme .NET Core](https://dotnet.microsoft.com/download/dotnet-core) sayfasından yeniden yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dfadf-225">You can reinstall .NET Core SDKs from the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>
>- <span data-ttu-id="dfadf-226">Bu araç, makinenizde bağımlı uygulamalar için gerekli olan .NET Core çalışma zamanının sürümlerini kaldırabilir.</span><span class="sxs-lookup"><span data-stu-id="dfadf-226">This tool can uninstall versions of the .NET Core runtime that are required by framework dependent applications on your machine.</span></span> <span data-ttu-id="dfadf-227">.NET Core çalışma zamanları 'nı [indirme .NET Core](https://dotnet.microsoft.com/download/dotnet-core) sayfasından yeniden yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dfadf-227">You can reinstall .NET Core runtimes from the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>
>- <span data-ttu-id="dfadf-228">Bu araç, Visual Studio 'nun bağımlı olduğu .NET Core SDK ve çalışma zamanının sürümlerini kaldırabilir.</span><span class="sxs-lookup"><span data-stu-id="dfadf-228">This tool can uninstall versions of the .NET Core SDK and runtime that Visual Studio relies on.</span></span> <span data-ttu-id="dfadf-229">Visual Studio yüklemenizi ayırırsanız, çalışma durumuna geri dönmek için Visual Studio yükleyicisindeki "Onar" ı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="dfadf-229">If you break your Visual Studio installation, run "Repair" in the Visual Studio installer to get back to a working state.</span></span>

<span data-ttu-id="dfadf-230">Varsayılan olarak, tüm komutlar, Visual Studio veya diğer SDK 'lar için gerekli olabilecek .NET Core SDK 'larını ve çalışma zamanlarını saklar.</span><span class="sxs-lookup"><span data-stu-id="dfadf-230">By default, all commands keep the .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs.</span></span> <span data-ttu-id="dfadf-231">Bu SDK 'lar ve çalışma zamanları, açıkça bağımsız değişken olarak listelenerek veya `--force` seçeneği kullanılarak kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="dfadf-231">These SDKs and runtimes can be uninstalled by listing them explicitly as arguments or by using the `--force` option.</span></span>

<span data-ttu-id="dfadf-232">Aracın .NET Core SDK 'larını ve çalışma zamanlarını kaldırması için yükseltme gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="dfadf-232">The tool requires elevation to uninstall .NET Core SDKs and runtimes.</span></span> <span data-ttu-id="dfadf-233">Aracı, Windows 'da ve macOS 'ta `sudo` bir yönetici komut isteminde çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="dfadf-233">Run the tool in an Administrator command prompt on Windows and with `sudo` on macOS.</span></span> <span data-ttu-id="dfadf-234">`dry-run` ve `whatif` komutlarının yükseltilmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="dfadf-234">The `dry-run` and `whatif` commands don't require elevation.</span></span>

<span data-ttu-id="dfadf-235">**DotNet-çekirdek-kaldırma kaldırma**</span><span class="sxs-lookup"><span data-stu-id="dfadf-235">**dotnet-core-uninstall remove**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="dfadf-236">Özeti</span><span class="sxs-lookup"><span data-stu-id="dfadf-236">Synopsis</span></span>

```console
dotnet-core-uninstall remove [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="dfadf-237">Arguments</span><span class="sxs-lookup"><span data-stu-id="dfadf-237">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="dfadf-238">Kaldırılacak belirtilen sürüm.</span><span class="sxs-lookup"><span data-stu-id="dfadf-238">The specified version to uninstall.</span></span> <span data-ttu-id="dfadf-239">Birden çok sürümü, boşluklarla ayırarak, birbirinden daha sonra listeleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dfadf-239">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="dfadf-240">Yanıt dosyaları da desteklenir.</span><span class="sxs-lookup"><span data-stu-id="dfadf-240">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="dfadf-241">Yanıt dosyaları, tüm sürümlerin komut satırına yerleştirilmesi için bir alternatiftir.</span><span class="sxs-lookup"><span data-stu-id="dfadf-241">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="dfadf-242">Genellikle \*. rsp uzantılı metin dosyalarıdır ve her sürüm ayrı bir satırda listelenir.</span><span class="sxs-lookup"><span data-stu-id="dfadf-242">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="dfadf-243">`VERSION` bağımsız değişkenine bir yanıt dosyası belirtmek için, yanıt dosyası adının hemen ardından \@ karakterini kullanın.</span><span class="sxs-lookup"><span data-stu-id="dfadf-243">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="dfadf-244">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="dfadf-244">Options</span></span>

## <a name="windowstabwindows"></a>[<span data-ttu-id="dfadf-245">Windows</span><span class="sxs-lookup"><span data-stu-id="dfadf-245">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="dfadf-246">Tüm .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="dfadf-246">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="dfadf-247">Yalnızca .NET Core SDK 'larını ve çalışma zamanlarını belirtilen sürümden daha küçük bir sürüme kaldırır.</span><span class="sxs-lookup"><span data-stu-id="dfadf-247">Removes only the .NET Core SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="dfadf-248">Belirtilen sürüm yüklü durumda kalır.</span><span class="sxs-lookup"><span data-stu-id="dfadf-248">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="dfadf-249">Belirtilen sürümler hariç tüm .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="dfadf-249">Removes all .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="dfadf-250">En yüksek sürüm dışında .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="dfadf-250">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="dfadf-251">Daha yüksek düzeltme eklerinin yerine geçen .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="dfadf-251">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="dfadf-252">Bu seçenek Global. JSON korumasını korur.</span><span class="sxs-lookup"><span data-stu-id="dfadf-252">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="dfadf-253">Önizleme olarak işaretlenen .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="dfadf-253">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="dfadf-254">En yüksek önizleme dışında, önizleme olarak işaretlenen .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="dfadf-254">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="dfadf-255">Yalnızca ASP.NET Core çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="dfadf-255">Removes ASP.NET Core runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="dfadf-256">Yalnızca .NET Core çalışma zamanı ve barındırma paketleri kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="dfadf-256">Removes .NET Core runtime and hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="dfadf-257">Belirtilen `major.minor` sürümüyle eşleşen .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="dfadf-257">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="dfadf-258">Yalnızca .NET Core çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="dfadf-258">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="dfadf-259">Yalnızca .NET Core SDK 'larını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="dfadf-259">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="dfadf-260">Ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="dfadf-260">Sets the verbosity level.</span></span> <span data-ttu-id="dfadf-261">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="dfadf-261">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="dfadf-262">Varsayılan değer `normal` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="dfadf-262">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="dfadf-263">X64 SDK 'larını veya çalışma zamanlarını kaldırmak için `--sdk`, `--runtime`ve `--aspnet-runtime` birlikte kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dfadf-263">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="dfadf-264">X86 SDK 'larını veya çalışma zamanlarını kaldırmak için `--sdk`, `--runtime`ve `--aspnet-runtime` birlikte kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dfadf-264">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="dfadf-265">**`-y, --yes`** Komutu Evet veya onay olmadan yürütür.</span><span class="sxs-lookup"><span data-stu-id="dfadf-265">**`-y, --yes`** Executes the command without requiring a yes or no confirmation.</span></span>

* <span data-ttu-id="dfadf-266">**`--force`** Visual Studio tarafından kullanılabilecek sürümlerin kaldırılmasını zorlar.</span><span class="sxs-lookup"><span data-stu-id="dfadf-266">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="dfadf-267">Notlar:</span><span class="sxs-lookup"><span data-stu-id="dfadf-267">Notes:</span></span>

1. <span data-ttu-id="dfadf-268">`--sdk`, `--runtime`, `--aspnet-runtime`ve `--hosting-bundle` tam olarak biri gereklidir.</span><span class="sxs-lookup"><span data-stu-id="dfadf-268">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="dfadf-269">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`ve `[<VERSION>...]` dışlamalı.</span><span class="sxs-lookup"><span data-stu-id="dfadf-269">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="dfadf-270">`--x64` veya `--x86` belirtilmemişse, hem x64 hem de x86 kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="dfadf-270">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macostabmacos"></a>[<span data-ttu-id="dfadf-271">macOS</span><span class="sxs-lookup"><span data-stu-id="dfadf-271">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="dfadf-272">Tüm .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="dfadf-272">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="dfadf-273">Belirtilen sürümün altındaki .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="dfadf-273">Removes .NET Core SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="dfadf-274">Belirtilen sürüm kalacak.</span><span class="sxs-lookup"><span data-stu-id="dfadf-274">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="dfadf-275">Bu sürümler dışında .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="dfadf-275">Removes .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="dfadf-276">En yüksek sürüm dışında .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="dfadf-276">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="dfadf-277">Daha yüksek düzeltme eklerinin yerine geçen .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="dfadf-277">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="dfadf-278">Bu seçenek Global. JSON korumasını korur.</span><span class="sxs-lookup"><span data-stu-id="dfadf-278">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="dfadf-279">Önizleme olarak işaretlenen .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="dfadf-279">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="dfadf-280">En yüksek önizleme dışında, önizleme olarak işaretlenen .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="dfadf-280">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="dfadf-281">Belirtilen `major.minor` sürümüyle eşleşen .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="dfadf-281">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="dfadf-282">Yalnızca .NET Core çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="dfadf-282">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="dfadf-283">Yalnızca .NET Core SDK 'larını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="dfadf-283">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="dfadf-284">Ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="dfadf-284">Sets the verbosity level.</span></span> <span data-ttu-id="dfadf-285">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="dfadf-285">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="dfadf-286">Varsayılan değer `normal` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="dfadf-286">The default value is `normal`.</span></span>

* <span data-ttu-id="dfadf-287">**`-y, --yes`** Komutu Y/N onayına gerek kalmadan yürütür.</span><span class="sxs-lookup"><span data-stu-id="dfadf-287">**`-y, --yes`** Executes the command without requiring Y/N confirmation.</span></span>
  
* <span data-ttu-id="dfadf-288">**`--force`** Visual Studio veya SDK 'lar tarafından kullanılan sürümlerin kaldırılmasını zorlar.</span><span class="sxs-lookup"><span data-stu-id="dfadf-288">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="dfadf-289">Notlar:</span><span class="sxs-lookup"><span data-stu-id="dfadf-289">Notes:</span></span>

1. <span data-ttu-id="dfadf-290">`--sdk` ve `--runtime` tam olarak biri gereklidir.</span><span class="sxs-lookup"><span data-stu-id="dfadf-290">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="dfadf-291">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`ve `[<VERSION>...]` dışlamalı.</span><span class="sxs-lookup"><span data-stu-id="dfadf-291">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="dfadf-292">Örnekler</span><span class="sxs-lookup"><span data-stu-id="dfadf-292">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="dfadf-293">Varsayılan olarak, Visual Studio veya diğer SDK 'lar için gerekli olabilecek .NET Core SDK 'Ları ve çalışma zamanları tutulur.</span><span class="sxs-lookup"><span data-stu-id="dfadf-293">By default, .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs are kept.</span></span> <span data-ttu-id="dfadf-294">Aşağıdaki örneklerde, belirtilen SDK ve çalışma zamanlarının bazıları makinenin durumuna bağlı olarak kalabilir.</span><span class="sxs-lookup"><span data-stu-id="dfadf-294">In the following examples, some of the specified SDKs and runtimes may remain, depending on the state of the machine.</span></span> <span data-ttu-id="dfadf-295">Tüm SDK 'Ları ve çalışma zamanlarını kaldırmak için bunları açık bağımsız değişken olarak listeleyin veya `--force` seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="dfadf-295">To remove all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="dfadf-296">Y/N onayı gerekmeden sürüm `3.0.0-preview6-27804-01` dışındaki tüm .NET Core çalışma zamanlarını kaldırın:</span><span class="sxs-lookup"><span data-stu-id="dfadf-296">Remove all .NET Core runtimes except the version `3.0.0-preview6-27804-01` without requiring Y/N confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --all-but 3.0.0-preview6-27804-01 --runtime --yes
  ```

* <span data-ttu-id="dfadf-297">Y/n onayı gerekmeden tüm .NET Core 1,1 SDK 'larını kaldırın:</span><span class="sxs-lookup"><span data-stu-id="dfadf-297">Remove all .NET Core 1.1 SDKs without requiring Y/n confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --sdk --major-minor 1.1 -y
  ```

* <span data-ttu-id="dfadf-298">Konsol çıktısı olmadan .NET Core 1.1.11 SDK 'sını kaldırın:</span><span class="sxs-lookup"><span data-stu-id="dfadf-298">Remove the .NET Core 1.1.11 SDK with no console output:</span></span>

  ```console
  dotnet-core-uninstall remove 1.1.11 --sdk --yes --verbosity q
  ```

* <span data-ttu-id="dfadf-299">Bu araç tarafından güvenli bir şekilde kaldırılabileceği tüm .NET Core SDK 'larını kaldırın:</span><span class="sxs-lookup"><span data-stu-id="dfadf-299">Remove all .NET Core SDKs that can safely be removed by this tool:</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk
  ```

* <span data-ttu-id="dfadf-300">Bu araç tarafından kaldırılabileceği tüm .NET Core SDK 'larını, Visual Studio tarafından gerekebilecek SDK 'lar da dahil olmak üzere kaldırın (önerilmez):</span><span class="sxs-lookup"><span data-stu-id="dfadf-300">Remove all .NET Core SDKs that can be removed by this tool, including those SDKs that may be required by Visual Studio (not recommended):</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk --force
  ```

* <span data-ttu-id="dfadf-301">Yanıt dosyasında belirtilen tüm .NET Core SDK 'larını kaldırın `versions.rsp`</span><span class="sxs-lookup"><span data-stu-id="dfadf-301">Remove all .NET Core SDKs that are specified in the response file `versions.rsp`</span></span>

  ```console
  dotnet-core-uninstall remove --sdk @versions.rsp
  ```

  <span data-ttu-id="dfadf-302">*Versions. rsp* içeriği aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="dfadf-302">The content of *versions.rsp* is as follows:</span></span>
  
  ```text
  2.2.300
  2.1.700
  ```

### <a name="step-4---delete-the-nuget-fallback-folder-optional"></a><span data-ttu-id="dfadf-303">4\. adım-NuGet geri dönüş klasörünü silme (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="dfadf-303">Step 4 - Delete the NuGet fallback folder (optional)</span></span>

<span data-ttu-id="dfadf-304">Bazı durumlarda `NuGetFallbackFolder` artık gerekmez ve silmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dfadf-304">In some cases, you no longer need the `NuGetFallbackFolder` and may wish to delete it.</span></span> <span data-ttu-id="dfadf-305">Bu klasörü silme hakkında daha fazla bilgi için bkz. [NuGetFallbackFolder 'ı kaldırma](../versions/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).</span><span class="sxs-lookup"><span data-stu-id="dfadf-305">For more information about deleting this folder, see [Remove the NuGetFallbackFolder](../versions/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).</span></span>

## <a name="uninstall-the-tool"></a><span data-ttu-id="dfadf-306">Aracı kaldır</span><span class="sxs-lookup"><span data-stu-id="dfadf-306">Uninstall the tool</span></span>

## <a name="windowstabwindows"></a>[<span data-ttu-id="dfadf-307">Windows</span><span class="sxs-lookup"><span data-stu-id="dfadf-307">Windows</span></span>](#tab/windows)

1. <span data-ttu-id="dfadf-308">**Program Ekle veya Kaldır**'ı açın.</span><span class="sxs-lookup"><span data-stu-id="dfadf-308">Open **Add or Remove Programs**.</span></span>
2. <span data-ttu-id="dfadf-309">`Microsoft .NET Core SDK Uninstall Tool` arayın.</span><span class="sxs-lookup"><span data-stu-id="dfadf-309">Search for `Microsoft .NET Core SDK Uninstall Tool`.</span></span>
3. <span data-ttu-id="dfadf-310">**Kaldır**'ı seçin.</span><span class="sxs-lookup"><span data-stu-id="dfadf-310">Select **Uninstall**.</span></span>

## <a name="macostabmacos"></a>[<span data-ttu-id="dfadf-311">macOS</span><span class="sxs-lookup"><span data-stu-id="dfadf-311">macOS</span></span>](#tab/macos)

<span data-ttu-id="dfadf-312">İndirilen *DotNet-Core-Uninstall. tar. gz* dosyasını yüklendiği dizinden silin.</span><span class="sxs-lookup"><span data-stu-id="dfadf-312">Delete the downloaded *dotnet-core-uninstall.tar.gz* file from the directory where it was installed.</span></span> <span data-ttu-id="dfadf-313">Bu dosyanın içeriğini başka bir dizine sıkıştırdıysanız, bu içeriği de sildiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="dfadf-313">If you unzipped the contents of this file into another directory, be sure to delete that content as well.</span></span>

---
