---
title: Aracı kaldır
description: .NET Core SDK 'Ları ve çalışma zamanlarını denetimli temizleme işlemini sağlayan kılavuzlu bir araç olan .NET Core kaldırma aracına genel bakış.
author: sfoslund
ms.date: 05/27/2020
ms.openlocfilehash: 4e70fd3438b582bd5a0d6a52d7e58ed5e07f8811
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/05/2020
ms.locfileid: "84446912"
---
# <a name="net-core-uninstall-tool"></a><span data-ttu-id="98eb2-103">.NET Core Kaldırma Aracı</span><span class="sxs-lookup"><span data-stu-id="98eb2-103">.NET Core Uninstall Tool</span></span>

<span data-ttu-id="98eb2-104">[.NET Core kaldırma aracı](https://aka.ms/dotnet-core-uninstall-tool) ( `dotnet-core-uninstall` ), bir sistemden .NET Core SDK 'Larını ve çalışma zamanlarını kaldırmanıza imkan sağlar.</span><span class="sxs-lookup"><span data-stu-id="98eb2-104">The [.NET Core Uninstall Tool](https://aka.ms/dotnet-core-uninstall-tool) (`dotnet-core-uninstall`) lets you remove .NET Core SDKs and Runtimes from a system.</span></span> <span data-ttu-id="98eb2-105">Kaldırmak istediğiniz sürümleri belirlemek için bir seçenek koleksiyonu kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="98eb2-105">A collection of options is available to specify which versions you want to uninstall.</span></span>

<span data-ttu-id="98eb2-106">Araç Windows ve macOS 'yi destekler.</span><span class="sxs-lookup"><span data-stu-id="98eb2-106">The tool supports Windows and macOS.</span></span> <span data-ttu-id="98eb2-107">Linux Şu anda desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="98eb2-107">Linux is currently not supported.</span></span>

<span data-ttu-id="98eb2-108">Bu araç, Windows 'ta yalnızca aşağıdaki yükleyicilerden biri kullanılarak yüklenen SDK 'Ları ve çalışma zamanlarını kaldırabilir:</span><span class="sxs-lookup"><span data-stu-id="98eb2-108">On Windows, the tool can only uninstall SDKs and Runtimes that were installed using one of the following installers:</span></span>

- <span data-ttu-id="98eb2-109">.NET Core SDK ve çalışma zamanı yükleyicisi.</span><span class="sxs-lookup"><span data-stu-id="98eb2-109">The .NET Core SDK and runtime installer.</span></span>
- <span data-ttu-id="98eb2-110">Visual Studio 2019 sürüm 16,3 ' den önceki sürümlerde Visual Studio yükleyicisi.</span><span class="sxs-lookup"><span data-stu-id="98eb2-110">The Visual Studio installer in versions earlier than Visual Studio 2019 version 16.3.</span></span>

<span data-ttu-id="98eb2-111">MacOS 'ta, araç yalnızca */usr/local/share/DotNet* klasöründe bulunan SDK 'ları ve çalışma zamanlarını kaldırabilir.</span><span class="sxs-lookup"><span data-stu-id="98eb2-111">On macOS, the tool can only uninstall SDKs and runtimes located in the */usr/local/share/dotnet* folder.</span></span>

<span data-ttu-id="98eb2-112">Bu sınırlamalar nedeniyle araç, makinenizde tüm .NET Core SDK 'larını ve çalışma zamanlarını kaldıramayabilir.</span><span class="sxs-lookup"><span data-stu-id="98eb2-112">Because of these limitations, the tool may not be able to uninstall all of the .NET Core SDKs and runtimes on your machine.</span></span> <span data-ttu-id="98eb2-113">`dotnet --info`Bu aracın kaldırakaldıramıyorum SDK 'lar ve çalışma zamanları dahil tüm .NET Core SDK 'larını ve çalışma zamanlarını bulmak için komutunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="98eb2-113">You can use the `dotnet --info` command to find all of the .NET Core SDKs and runtimes installed, including those SDKs and runtimes that this tool can't remove.</span></span> <span data-ttu-id="98eb2-114">`dotnet-core-uninstall list`Komut, araçla hangi SDK 'ların kaldırılabileceği görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="98eb2-114">The `dotnet-core-uninstall list` command displays which SDKs can be uninstalled with the tool.</span></span>

## <a name="install-the-tool"></a><span data-ttu-id="98eb2-115">Aracı 'nı yükler</span><span class="sxs-lookup"><span data-stu-id="98eb2-115">Install the tool</span></span>

<span data-ttu-id="98eb2-116">.NET Core kaldırma aracını [buradan](https://aka.ms/dotnet-core-uninstall-tool) indirebilir ve [DotNet/CLI-Lab](https://github.com/dotnet/cli-lab) GitHub deposunda kaynak kodu bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="98eb2-116">You can download the .NET Core Uninstall Tool from [here](https://aka.ms/dotnet-core-uninstall-tool) and find the source code at the [dotnet/cli-lab](https://github.com/dotnet/cli-lab) GitHub repository.</span></span>

> [!NOTE]
> <span data-ttu-id="98eb2-117">Aracın .NET Core SDK 'larını ve çalışma zamanlarını kaldırması için yükseltme gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="98eb2-117">The tool requires elevation to uninstall .NET Core SDKs and runtimes.</span></span> <span data-ttu-id="98eb2-118">Bu nedenle, Windows üzerinde *C:\Program Files* veya MacOS 'ta */usr/local/bin* gibi bir yazma korumalı dizine yüklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="98eb2-118">Therefore, it should be installed in a write-protected directory such as *C:\Program Files* on Windows or */usr/local/bin* on macOS.</span></span> <span data-ttu-id="98eb2-119">Ayrıca bkz. [DotNet komutları Için yükseltilmiş erişim](../tools/elevated-access.md).</span><span class="sxs-lookup"><span data-stu-id="98eb2-119">See also [Elevated access for dotnet commands](../tools/elevated-access.md).</span></span> <span data-ttu-id="98eb2-120">Daha fazla bilgi için bkz. [ayrıntılı yükleme yönergeleri](https://aka.ms/dotnet-core-uninstall-tool).</span><span class="sxs-lookup"><span data-stu-id="98eb2-120">For more information, see the [detailed installation instructions](https://aka.ms/dotnet-core-uninstall-tool).</span></span>

## <a name="run-the-tool"></a><span data-ttu-id="98eb2-121">Aracı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="98eb2-121">Run the tool</span></span>

<span data-ttu-id="98eb2-122">Aşağıdaki adımlarda, kaldırma aracını çalıştırmak için önerilen yaklaşım gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="98eb2-122">The following steps show the recommended approach for running the uninstall tool:</span></span>

- [<span data-ttu-id="98eb2-123">1. adım-yüklü .NET Core SDK 'larını ve çalışma zamanlarını görüntüleme</span><span class="sxs-lookup"><span data-stu-id="98eb2-123">Step 1 - Display installed .NET Core SDKs and runtimes</span></span>](#step-1---display-installed-net-core-sdks-and-runtimes)
- [<span data-ttu-id="98eb2-124">2. adım-bir kuru çalıştırma</span><span class="sxs-lookup"><span data-stu-id="98eb2-124">Step 2 - Do a dry run</span></span>](#step-2---do-a-dry-run)
- [<span data-ttu-id="98eb2-125">3. adım-.NET Core SDK 'larını ve çalışma zamanlarını kaldırma</span><span class="sxs-lookup"><span data-stu-id="98eb2-125">Step 3 - Uninstall .NET Core SDKs and Runtimes</span></span>](#step-3---uninstall-net-core-sdks-and-runtimes)
- [<span data-ttu-id="98eb2-126">4. adım-NuGet geri dönüş klasörünü silme (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="98eb2-126">Step 4 - Delete the NuGet fallback folder (optional)</span></span>](#step-4---delete-the-nuget-fallback-folder-optional)

### <a name="step-1---display-installed-net-core-sdks-and-runtimes"></a><span data-ttu-id="98eb2-127">1. adım-yüklü .NET Core SDK 'larını ve çalışma zamanlarını görüntüleme</span><span class="sxs-lookup"><span data-stu-id="98eb2-127">Step 1 - Display installed .NET Core SDKs and runtimes</span></span>

<span data-ttu-id="98eb2-128">`dotnet-core-uninstall list`Komutu, bu araçla kaldırılamayan yüklü .NET Core SDK 'larını ve çalışma zamanlarını listeler.</span><span class="sxs-lookup"><span data-stu-id="98eb2-128">The `dotnet-core-uninstall list` command lists the installed .NET Core SDKs and runtimes that can be removed with this tool.</span></span> <span data-ttu-id="98eb2-129">Bazı SDK 'lar ve çalışma zamanları Visual Studio için gerekli olabilir ve bunların kaldırılması önerilmez.</span><span class="sxs-lookup"><span data-stu-id="98eb2-129">Some SDKs and runtimes may be required by Visual Studio and they're displayed with a note of why it isn't recommended to uninstall them.</span></span>

> [!NOTE]
> <span data-ttu-id="98eb2-130">Komutun çıktısı, `dotnet-core-uninstall list` çoğu durumda çıkış içindeki yüklü sürümlerin listesiyle eşleşmez `dotnet --info` .</span><span class="sxs-lookup"><span data-stu-id="98eb2-130">The output of the `dotnet-core-uninstall list` command will not match the list of installed versions in the output of `dotnet --info` in most cases.</span></span> <span data-ttu-id="98eb2-131">Özellikle, bu araç ZIP dosyaları tarafından yüklenen veya Visual Studio tarafından yönetilen sürümleri (Visual Studio 2019 16,3 veya üzeri sürümleriyle yüklenmiş herhangi bir sürüm) görüntüleyemez.</span><span class="sxs-lookup"><span data-stu-id="98eb2-131">Specifically, this tool will not display versions installed by zip files or managed by Visual Studio (any version installed with Visual Studio 2019 16.3 or later).</span></span> <span data-ttu-id="98eb2-132">Bir sürümün Visual Studio tarafından yönetilip yönetilmediğini kontrol etmenin bir yolu `Add or Remove Programs` , Visual Studio tarafından yönetilen sürümlerin görüntüleme adlarında gösterildiği gibi işaretlendiğine göz atın.</span><span class="sxs-lookup"><span data-stu-id="98eb2-132">One way to check if a version is managed by Visual Studio is to view it in `Add or Remove Programs`, where Visual Studio managed versions are marked as such in their display names.</span></span>

<span data-ttu-id="98eb2-133">**DotNet-çekirdek-kaldırma listesi**</span><span class="sxs-lookup"><span data-stu-id="98eb2-133">**dotnet-core-uninstall list**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="98eb2-134">Özeti</span><span class="sxs-lookup"><span data-stu-id="98eb2-134">Synopsis</span></span>

```console
dotnet-core-uninstall list [options]
```

#### <a name="options"></a><span data-ttu-id="98eb2-135">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="98eb2-135">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="98eb2-136">Windows</span><span class="sxs-lookup"><span data-stu-id="98eb2-136">Windows</span></span>](#tab/windows)

* **`--aspnet-runtime`**

  <span data-ttu-id="98eb2-137">Bu araçla kaldırılabilecek tüm ASP.NET Core çalışma zamanlarını listeler.</span><span class="sxs-lookup"><span data-stu-id="98eb2-137">Lists all the ASP.NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="98eb2-138">Bu araçla kaldırılabilecek tüm .NET Core barındırma paketlerini listeler.</span><span class="sxs-lookup"><span data-stu-id="98eb2-138">Lists all the .NET Core hosting bundles that can be uninstalled with this tool.</span></span>

* **`--runtime`**

  <span data-ttu-id="98eb2-139">Bu araçla kaldırılabilecek tüm .NET Core çalışma zamanlarını listeler.</span><span class="sxs-lookup"><span data-stu-id="98eb2-139">Lists all .NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="98eb2-140">Bu araçla kaldırılabilecek tüm .NET Core SDK 'larını listeler.</span><span class="sxs-lookup"><span data-stu-id="98eb2-140">Lists all .NET Core SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="98eb2-141">Ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="98eb2-141">Sets the verbosity level.</span></span> <span data-ttu-id="98eb2-142">İzin verilen değerler,,, `q[uiet]` `m[inimal]` `n[ormal]` `d[etailed]` ve `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="98eb2-142">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="98eb2-143">Varsayılan değer: `normal`.</span><span class="sxs-lookup"><span data-stu-id="98eb2-143">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="98eb2-144">Bu araçla kaldırılabilecek tüm x64 .NET Core SDK 'larını ve çalışma zamanlarını listeler.</span><span class="sxs-lookup"><span data-stu-id="98eb2-144">Lists all x64 .NET Core SDKs and runtimes that can be uninstalled with this tool.</span></span>

* **`--x86`**

  <span data-ttu-id="98eb2-145">Bu araçla kaldırılabilecek tüm x86 .NET Core SDK 'larını ve çalışma zamanlarını listeler.</span><span class="sxs-lookup"><span data-stu-id="98eb2-145">Lists all x86 .NET Core SDKs and runtimes that can be uninstalled with this tool.</span></span>

## <a name="macos"></a>[<span data-ttu-id="98eb2-146">macOS</span><span class="sxs-lookup"><span data-stu-id="98eb2-146">macOS</span></span>](#tab/macos)

* **`--runtime`**

  <span data-ttu-id="98eb2-147">Bu araçla kaldırılabilecek tüm .NET Core çalışma zamanlarını listeler.</span><span class="sxs-lookup"><span data-stu-id="98eb2-147">Lists all .NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="98eb2-148">Bu araçla kaldırılabilecek tüm .NET Core SDK 'larını listeler.</span><span class="sxs-lookup"><span data-stu-id="98eb2-148">Lists all .NET Core SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="98eb2-149">Ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="98eb2-149">Sets the verbosity level.</span></span> <span data-ttu-id="98eb2-150">İzin verilen değerler,,, `q[uiet]` `m[inimal]` `n[ormal]` `d[etailed]` ve `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="98eb2-150">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="98eb2-151">Varsayılan değer: `normal`.</span><span class="sxs-lookup"><span data-stu-id="98eb2-151">The default value is `normal`.</span></span>
  
---

#### <a name="examples"></a><span data-ttu-id="98eb2-152">Örnekler</span><span class="sxs-lookup"><span data-stu-id="98eb2-152">Examples</span></span>

* <span data-ttu-id="98eb2-153">Bu araçla kaldırılabileceği tüm .NET Core SDK 'larını ve çalışma zamanlarını listeleyin:</span><span class="sxs-lookup"><span data-stu-id="98eb2-153">List all .NET Core SDKs and runtimes that can be removed with this tool:</span></span>

  ```console
  dotnet-core-uninstall list
  ```

* <span data-ttu-id="98eb2-154">Tüm x64 .NET Core SDK 'larını ve çalışma zamanlarını listeleyin:</span><span class="sxs-lookup"><span data-stu-id="98eb2-154">List all x64 .NET Core SDKs and runtimes:</span></span>

  ```console
  dotnet-core-uninstall list --x64
  ```

* <span data-ttu-id="98eb2-155">Tüm x86 .NET Core SDK 'larını listeleyin:</span><span class="sxs-lookup"><span data-stu-id="98eb2-155">List all x86 .NET Core SDKs:</span></span>

  ```console
  dotnet-core-uninstall list --sdk --x86
  ```

### <a name="step-2---do-a-dry-run"></a><span data-ttu-id="98eb2-156">2. adım-bir kuru çalıştırma</span><span class="sxs-lookup"><span data-stu-id="98eb2-156">Step 2 - Do a dry run</span></span>

<span data-ttu-id="98eb2-157">`dotnet-core-uninstall dry-run`Ve `dotnet-core-uninstall whatif` komutları, kaldırma işlemi yapılmadan belirtilen seçeneklere bağlı olarak kaldırılacak .NET Core SDK 'larını ve çalışma zamanlarını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="98eb2-157">The `dotnet-core-uninstall dry-run` and `dotnet-core-uninstall whatif` commands display the .NET Core SDKs and runtimes that will be removed based on the options provided without performing the uninstall.</span></span> <span data-ttu-id="98eb2-158">Bu komutlar eş anlamlılardır.</span><span class="sxs-lookup"><span data-stu-id="98eb2-158">These commands are synonyms.</span></span>

<span data-ttu-id="98eb2-159">**DotNet-çekirdek-kaldırma kuru çalıştırma ve DotNet-çekirdek-kaldırma whatIf**</span><span class="sxs-lookup"><span data-stu-id="98eb2-159">**dotnet-core-uninstall dry-run and dotnet-core-uninstall whatif**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="98eb2-160">Özeti</span><span class="sxs-lookup"><span data-stu-id="98eb2-160">Synopsis</span></span>

```console
dotnet-core-uninstall dry-run [options] [<VERSION>...]

dotnet-core-uninstall whatif [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="98eb2-161">Arguments</span><span class="sxs-lookup"><span data-stu-id="98eb2-161">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="98eb2-162">Kaldırılacak belirtilen sürüm.</span><span class="sxs-lookup"><span data-stu-id="98eb2-162">The specified version to uninstall.</span></span> <span data-ttu-id="98eb2-163">Birden çok sürümü, boşluklarla ayırarak, birbirinden daha sonra listeleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="98eb2-163">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="98eb2-164">Yanıt dosyaları da desteklenir.</span><span class="sxs-lookup"><span data-stu-id="98eb2-164">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="98eb2-165">Yanıt dosyaları, tüm sürümlerin komut satırına yerleştirilmesi için bir alternatiftir.</span><span class="sxs-lookup"><span data-stu-id="98eb2-165">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="98eb2-166">Bunlar genellikle \* . rsp uzantılı metin dosyalarıdır ve her sürüm ayrı bir satırda listelenir.</span><span class="sxs-lookup"><span data-stu-id="98eb2-166">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="98eb2-167">Bağımsız değişken için bir yanıt dosyası belirtmek için `VERSION` , \@ hemen arkasından yanıt dosyası adı gelen karakteri kullanın.</span><span class="sxs-lookup"><span data-stu-id="98eb2-167">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="98eb2-168">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="98eb2-168">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="98eb2-169">Windows</span><span class="sxs-lookup"><span data-stu-id="98eb2-169">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="98eb2-170">Tüm .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="98eb2-170">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>[ <VERSION>...]`**

  <span data-ttu-id="98eb2-171">Yalnızca .NET Core SDK 'larını ve çalışma zamanlarını belirtilen sürümden daha küçük bir sürüme kaldırır.</span><span class="sxs-lookup"><span data-stu-id="98eb2-171">Removes only the .NET Core SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="98eb2-172">Belirtilen sürüm yüklü durumda kalır.</span><span class="sxs-lookup"><span data-stu-id="98eb2-172">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>[ <VERSION>...]`**

  <span data-ttu-id="98eb2-173">Belirtilen sürümler hariç tüm .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="98eb2-173">Removes all .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="98eb2-174">En yüksek sürüm dışında .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="98eb2-174">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="98eb2-175">Daha yüksek düzeltme eklerinin yerine geçen .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="98eb2-175">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="98eb2-176">Bu seçenek Global. JSON korumasını korur.</span><span class="sxs-lookup"><span data-stu-id="98eb2-176">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="98eb2-177">Önizleme olarak işaretlenen .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="98eb2-177">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="98eb2-178">En yüksek önizleme dışında, önizleme olarak işaretlenen .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="98eb2-178">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="98eb2-179">Yalnızca ASP.NET Core çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="98eb2-179">Removes ASP.NET Core runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="98eb2-180">Yalnızca .NET Core çalışma zamanı ve barındırma paketleri kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="98eb2-180">Removes .NET Core runtime and hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="98eb2-181">Belirtilen sürümle eşleşen .NET Core SDK 'larını ve çalışma zamanlarını kaldırır `major.minor` .</span><span class="sxs-lookup"><span data-stu-id="98eb2-181">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="98eb2-182">Yalnızca .NET Core çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="98eb2-182">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="98eb2-183">Yalnızca .NET Core SDK 'larını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="98eb2-183">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="98eb2-184">Ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="98eb2-184">Sets the verbosity level.</span></span> <span data-ttu-id="98eb2-185">İzin verilen değerler,,, `q[uiet]` `m[inimal]` `n[ormal]` `d[etailed]` ve `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="98eb2-185">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="98eb2-186">Varsayılan değer: `normal`.</span><span class="sxs-lookup"><span data-stu-id="98eb2-186">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="98eb2-187">`--sdk` `--runtime` `--aspnet-runtime` X64 SDK 'larını veya çalışma zamanlarını kaldırmak için, ve ile birlikte kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="98eb2-187">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="98eb2-188">`--sdk` `--runtime` `--aspnet-runtime` X86 SDK 'larını veya çalışma zamanlarını kaldırmak için ve ile birlikte kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="98eb2-188">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="98eb2-189">**`--force`** Visual Studio tarafından kullanılabilecek sürümlerin kaldırılmasını zorlar.</span><span class="sxs-lookup"><span data-stu-id="98eb2-189">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="98eb2-190">Notlar:</span><span class="sxs-lookup"><span data-stu-id="98eb2-190">Notes:</span></span>

1. <span data-ttu-id="98eb2-191">,, Ve yalnızca biri `--sdk` `--runtime` `--aspnet-runtime` `--hosting-bundle` gereklidir.</span><span class="sxs-lookup"><span data-stu-id="98eb2-191">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="98eb2-192">`--all`,,,,, `--all-below` `--all-but` `--all-but-latest` `--all-lower-patches` `--all-previews` , `--all-previews-but-latest` , `--major-minor` ve `[<VERSION>...]` dışlamalı.</span><span class="sxs-lookup"><span data-stu-id="98eb2-192">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="98eb2-193">`--x64`Veya `--x86` belirtilmemişse, hem x64 hem de x86 kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="98eb2-193">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macos"></a>[<span data-ttu-id="98eb2-194">macOS</span><span class="sxs-lookup"><span data-stu-id="98eb2-194">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="98eb2-195">Tüm .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="98eb2-195">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>[ <VERSION>...]`**

  <span data-ttu-id="98eb2-196">Belirtilen sürümün altındaki .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="98eb2-196">Removes .NET Core SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="98eb2-197">Belirtilen sürüm kalacak.</span><span class="sxs-lookup"><span data-stu-id="98eb2-197">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>[ <VERSION>...]`**

  <span data-ttu-id="98eb2-198">Bu sürümler dışında .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="98eb2-198">Removes .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="98eb2-199">En yüksek sürüm dışında .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="98eb2-199">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="98eb2-200">Daha yüksek düzeltme eklerinin yerine geçen .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="98eb2-200">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="98eb2-201">Bu seçenek Global. JSON korumasını korur.</span><span class="sxs-lookup"><span data-stu-id="98eb2-201">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="98eb2-202">Önizleme olarak işaretlenen .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="98eb2-202">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="98eb2-203">En yüksek önizleme dışında, önizleme olarak işaretlenen .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="98eb2-203">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="98eb2-204">Belirtilen sürümle eşleşen .NET Core SDK 'larını ve çalışma zamanlarını kaldırır `major.minor` .</span><span class="sxs-lookup"><span data-stu-id="98eb2-204">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="98eb2-205">Yalnızca .NET Core çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="98eb2-205">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="98eb2-206">Yalnızca .NET Core SDK 'larını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="98eb2-206">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="98eb2-207">Ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="98eb2-207">Sets the verbosity level.</span></span> <span data-ttu-id="98eb2-208">İzin verilen değerler,,, `q[uiet]` `m[inimal]` `n[ormal]` `d[etailed]` ve `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="98eb2-208">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="98eb2-209">Varsayılan değer: `normal`.</span><span class="sxs-lookup"><span data-stu-id="98eb2-209">The default value is `normal`.</span></span>
  
* <span data-ttu-id="98eb2-210">**`--force`** Visual Studio veya SDK 'lar tarafından kullanılan sürümlerin kaldırılmasını zorlar.</span><span class="sxs-lookup"><span data-stu-id="98eb2-210">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="98eb2-211">Notlar:</span><span class="sxs-lookup"><span data-stu-id="98eb2-211">Notes:</span></span>

1. <span data-ttu-id="98eb2-212">Ve bunlardan yalnızca `--sdk` biri `--runtime` gereklidir.</span><span class="sxs-lookup"><span data-stu-id="98eb2-212">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="98eb2-213">`--all`,,,,, `--all-below` `--all-but` `--all-but-latest` `--all-lower-patches` `--all-previews` , `--all-previews-but-latest` , `--major-minor` ve `[<VERSION>...]` dışlamalı.</span><span class="sxs-lookup"><span data-stu-id="98eb2-213">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="98eb2-214">Örnekler</span><span class="sxs-lookup"><span data-stu-id="98eb2-214">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="98eb2-215">Varsayılan olarak, Visual Studio veya diğer SDK 'lar için gerekli olabilecek .NET Core SDK 'Ları ve çalışma zamanları çıkışa dahil edilmez `dotnet-core-uninstall dry-run` .</span><span class="sxs-lookup"><span data-stu-id="98eb2-215">By default, .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs are not included in `dotnet-core-uninstall dry-run` output.</span></span> <span data-ttu-id="98eb2-216">Aşağıdaki örneklerde, makinenin durumuna bağlı olarak belirtilen SDK ve çalışma zamanlarının bazıları çıkışa dahil edilmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="98eb2-216">In the following examples, some of the specified SDKs and runtimes may not be included in the output, depending on the state of the machine.</span></span> <span data-ttu-id="98eb2-217">Tüm SDK 'Ları ve çalışma zamanlarını dahil etmek için bunları açık bağımsız değişken olarak listeleyin veya `--force` seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="98eb2-217">To include all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="98eb2-218">Daha yüksek düzeltme eklerinin yerini aldığı tüm .NET Core çalışma zamanlarını kaldırma kuru:</span><span class="sxs-lookup"><span data-stu-id="98eb2-218">Dry run of removing all .NET Core runtimes that have been superseded by higher patches:</span></span>

  ```console
  dotnet-core-uninstall dry-run --all-lower-patches --runtime
  ```

* <span data-ttu-id="98eb2-219">Sürümün altındaki tüm .NET Core SDK 'larını kaldırma konusunda Kuru çalıştırın `2.2.301` :</span><span class="sxs-lookup"><span data-stu-id="98eb2-219">Dry run of removing all .NET Core SDKs below the version `2.2.301`:</span></span>

  ```console
  dotnet-core-uninstall whatif --all-below 2.2.301 --sdk
  ```

### <a name="step-3---uninstall-net-core-sdks-and-runtimes"></a><span data-ttu-id="98eb2-220">3. adım-.NET Core SDK 'larını ve çalışma zamanlarını kaldırma</span><span class="sxs-lookup"><span data-stu-id="98eb2-220">Step 3 - Uninstall .NET Core SDKs and Runtimes</span></span>

<span data-ttu-id="98eb2-221">`dotnet-core-uninstall remove`bir seçenek koleksiyonuyla belirtilen .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="98eb2-221">`dotnet-core-uninstall remove` uninstalls .NET Core SDKs and Runtimes that are specified by a collection of options.</span></span> <span data-ttu-id="98eb2-222">Araç, sürüm 5,0 veya üzeri olan SDK 'Ları ve çalışma zamanlarını kaldırmak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="98eb2-222">The tool can't be used to uninstall SDKs and Runtimes with version 5.0 or above.</span></span>

<span data-ttu-id="98eb2-223">Bu aracın bozucu bir davranışı olduğundan, Kaldır komutunu çalıştırmadan önce bir kuru çalıştırma yapmanız **önemle** önerilir.</span><span class="sxs-lookup"><span data-stu-id="98eb2-223">Since this tool has a destructive behavior, it's **highly** recommended that you do a dry run before running the remove command.</span></span> <span data-ttu-id="98eb2-224">Kuru çalıştırma, komutu kullandığınızda hangi .NET Core SDK 'larının ve çalışma zamanlarının kaldırılacağını gösterir `remove` .</span><span class="sxs-lookup"><span data-stu-id="98eb2-224">The dry run will show you what .NET Core SDKs and runtimes will be removed when you use the `remove` command.</span></span> <span data-ttu-id="98eb2-225">Hangi SDK 'ların ve çalışma zamanlarının kaldırılacağını öğrenmek için bkz. [bir sürümü kaldırmalıyım?](../install/remove-runtime-sdk-versions.md#should-i-remove-a-version) .</span><span class="sxs-lookup"><span data-stu-id="98eb2-225">Refer to [Should I remove a version?](../install/remove-runtime-sdk-versions.md#should-i-remove-a-version) to learn which SDKs and runtimes are safe to remove.</span></span>

> [!CAUTION]
> <span data-ttu-id="98eb2-226">Aşağıdaki uyarıları aklınızda bulundurun:</span><span class="sxs-lookup"><span data-stu-id="98eb2-226">Keep in mind the following caveats:</span></span>
>
>- <span data-ttu-id="98eb2-227">Bu araç, makinenizde bulunan dosyalar için gereken .NET Core SDK sürümlerini kaldırabilir `global.json` .</span><span class="sxs-lookup"><span data-stu-id="98eb2-227">This tool can uninstall versions of the .NET Core SDK that are required by `global.json` files on your machine.</span></span> <span data-ttu-id="98eb2-228">.NET Core SDK 'larını [indirme .NET Core](https://dotnet.microsoft.com/download/dotnet-core) sayfasından yeniden yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="98eb2-228">You can reinstall .NET Core SDKs from the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>
>- <span data-ttu-id="98eb2-229">Bu araç, makinenizde bağımlı uygulamalar için gerekli olan .NET Core çalışma zamanının sürümlerini kaldırabilir.</span><span class="sxs-lookup"><span data-stu-id="98eb2-229">This tool can uninstall versions of the .NET Core runtime that are required by framework dependent applications on your machine.</span></span> <span data-ttu-id="98eb2-230">.NET Core çalışma zamanları 'nı [indirme .NET Core](https://dotnet.microsoft.com/download/dotnet-core) sayfasından yeniden yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="98eb2-230">You can reinstall .NET Core runtimes from the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>
>- <span data-ttu-id="98eb2-231">Bu araç, Visual Studio 'nun bağımlı olduğu .NET Core SDK ve çalışma zamanının sürümlerini kaldırabilir.</span><span class="sxs-lookup"><span data-stu-id="98eb2-231">This tool can uninstall versions of the .NET Core SDK and runtime that Visual Studio relies on.</span></span> <span data-ttu-id="98eb2-232">Visual Studio yüklemenizi ayırırsanız, çalışma durumuna geri dönmek için Visual Studio yükleyicisindeki "Onar" ı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="98eb2-232">If you break your Visual Studio installation, run "Repair" in the Visual Studio installer to get back to a working state.</span></span>

<span data-ttu-id="98eb2-233">Varsayılan olarak, tüm komutlar, Visual Studio veya diğer SDK 'lar için gerekli olabilecek .NET Core SDK 'larını ve çalışma zamanlarını saklar.</span><span class="sxs-lookup"><span data-stu-id="98eb2-233">By default, all commands keep the .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs.</span></span> <span data-ttu-id="98eb2-234">Bu SDK 'lar ve çalışma zamanları, açıkça bağımsız değişken olarak listelenerek veya seçeneği kullanılarak kaldırılabilir `--force` .</span><span class="sxs-lookup"><span data-stu-id="98eb2-234">These SDKs and runtimes can be uninstalled by listing them explicitly as arguments or by using the `--force` option.</span></span>

<span data-ttu-id="98eb2-235">Aracın .NET Core SDK 'larını ve çalışma zamanlarını kaldırması için yükseltme gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="98eb2-235">The tool requires elevation to uninstall .NET Core SDKs and runtimes.</span></span> <span data-ttu-id="98eb2-236">Aracı, Windows 'da ve macOS 'ta bulunan bir yönetici komut isteminde çalıştırın `sudo` .</span><span class="sxs-lookup"><span data-stu-id="98eb2-236">Run the tool in an Administrator command prompt on Windows and with `sudo` on macOS.</span></span> <span data-ttu-id="98eb2-237">`dry-run`Ve `whatif` komutları yükseltme gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="98eb2-237">The `dry-run` and `whatif` commands don't require elevation.</span></span>

<span data-ttu-id="98eb2-238">**DotNet-çekirdek-kaldırma kaldırma**</span><span class="sxs-lookup"><span data-stu-id="98eb2-238">**dotnet-core-uninstall remove**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="98eb2-239">Özeti</span><span class="sxs-lookup"><span data-stu-id="98eb2-239">Synopsis</span></span>

```console
dotnet-core-uninstall remove [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="98eb2-240">Arguments</span><span class="sxs-lookup"><span data-stu-id="98eb2-240">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="98eb2-241">Kaldırılacak belirtilen sürüm.</span><span class="sxs-lookup"><span data-stu-id="98eb2-241">The specified version to uninstall.</span></span> <span data-ttu-id="98eb2-242">Birden çok sürümü, boşluklarla ayırarak, birbirinden daha sonra listeleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="98eb2-242">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="98eb2-243">Yanıt dosyaları da desteklenir.</span><span class="sxs-lookup"><span data-stu-id="98eb2-243">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="98eb2-244">Yanıt dosyaları, tüm sürümlerin komut satırına yerleştirilmesi için bir alternatiftir.</span><span class="sxs-lookup"><span data-stu-id="98eb2-244">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="98eb2-245">Bunlar genellikle \* . rsp uzantılı metin dosyalarıdır ve her sürüm ayrı bir satırda listelenir.</span><span class="sxs-lookup"><span data-stu-id="98eb2-245">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="98eb2-246">Bağımsız değişken için bir yanıt dosyası belirtmek için `VERSION` , \@ hemen arkasından yanıt dosyası adı gelen karakteri kullanın.</span><span class="sxs-lookup"><span data-stu-id="98eb2-246">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="98eb2-247">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="98eb2-247">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="98eb2-248">Windows</span><span class="sxs-lookup"><span data-stu-id="98eb2-248">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="98eb2-249">Tüm .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="98eb2-249">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>[ <VERSION>...]`**

  <span data-ttu-id="98eb2-250">Yalnızca .NET Core SDK 'larını ve çalışma zamanlarını belirtilen sürümden daha küçük bir sürüme kaldırır.</span><span class="sxs-lookup"><span data-stu-id="98eb2-250">Removes only the .NET Core SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="98eb2-251">Belirtilen sürüm yüklü durumda kalır.</span><span class="sxs-lookup"><span data-stu-id="98eb2-251">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>[ <VERSION>...]`**

  <span data-ttu-id="98eb2-252">Belirtilen sürümler hariç tüm .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="98eb2-252">Removes all .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="98eb2-253">En yüksek sürüm dışında .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="98eb2-253">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="98eb2-254">Daha yüksek düzeltme eklerinin yerine geçen .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="98eb2-254">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="98eb2-255">Bu seçenek Global. JSON korumasını korur.</span><span class="sxs-lookup"><span data-stu-id="98eb2-255">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="98eb2-256">Önizleme olarak işaretlenen .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="98eb2-256">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="98eb2-257">En yüksek önizleme dışında, önizleme olarak işaretlenen .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="98eb2-257">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="98eb2-258">Yalnızca ASP.NET Core çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="98eb2-258">Removes ASP.NET Core runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="98eb2-259">Yalnızca .NET Core barındırma paketlerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="98eb2-259">Removes .NET Core hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="98eb2-260">Belirtilen sürümle eşleşen .NET Core SDK 'larını ve çalışma zamanlarını kaldırır `major.minor` .</span><span class="sxs-lookup"><span data-stu-id="98eb2-260">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="98eb2-261">Yalnızca .NET Core çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="98eb2-261">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="98eb2-262">Yalnızca .NET Core SDK 'larını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="98eb2-262">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="98eb2-263">Ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="98eb2-263">Sets the verbosity level.</span></span> <span data-ttu-id="98eb2-264">İzin verilen değerler,,, `q[uiet]` `m[inimal]` `n[ormal]` `d[etailed]` ve `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="98eb2-264">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="98eb2-265">Varsayılan değer: `normal`.</span><span class="sxs-lookup"><span data-stu-id="98eb2-265">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="98eb2-266">`--sdk` `--runtime` `--aspnet-runtime` X64 SDK 'larını veya çalışma zamanlarını kaldırmak için, ve ile birlikte kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="98eb2-266">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="98eb2-267">`--sdk` `--runtime` `--aspnet-runtime` X86 SDK 'larını veya çalışma zamanlarını kaldırmak için ve ile birlikte kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="98eb2-267">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="98eb2-268">**`-y, --yes`** Komutu Evet veya onay olmadan yürütür.</span><span class="sxs-lookup"><span data-stu-id="98eb2-268">**`-y, --yes`** Executes the command without requiring a yes or no confirmation.</span></span>

* <span data-ttu-id="98eb2-269">**`--force`** Visual Studio tarafından kullanılabilecek sürümlerin kaldırılmasını zorlar.</span><span class="sxs-lookup"><span data-stu-id="98eb2-269">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="98eb2-270">Notlar:</span><span class="sxs-lookup"><span data-stu-id="98eb2-270">Notes:</span></span>

1. <span data-ttu-id="98eb2-271">,, Ve yalnızca biri `--sdk` `--runtime` `--aspnet-runtime` `--hosting-bundle` gereklidir.</span><span class="sxs-lookup"><span data-stu-id="98eb2-271">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="98eb2-272">`--all`,,,,, `--all-below` `--all-but` `--all-but-latest` `--all-lower-patches` `--all-previews` , `--all-previews-but-latest` , `--major-minor` ve `[<VERSION>...]` dışlamalı.</span><span class="sxs-lookup"><span data-stu-id="98eb2-272">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="98eb2-273">`--x64`Veya `--x86` belirtilmemişse, hem x64 hem de x86 kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="98eb2-273">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macos"></a>[<span data-ttu-id="98eb2-274">macOS</span><span class="sxs-lookup"><span data-stu-id="98eb2-274">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="98eb2-275">Tüm .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="98eb2-275">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>[ <VERSION>...]`**

  <span data-ttu-id="98eb2-276">Belirtilen sürümün altındaki .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="98eb2-276">Removes .NET Core SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="98eb2-277">Belirtilen sürüm kalacak.</span><span class="sxs-lookup"><span data-stu-id="98eb2-277">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>[ <VERSION>...]`**

  <span data-ttu-id="98eb2-278">Bu sürümler dışında .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="98eb2-278">Removes .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="98eb2-279">En yüksek sürüm dışında .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="98eb2-279">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="98eb2-280">Daha yüksek düzeltme eklerinin yerine geçen .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="98eb2-280">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="98eb2-281">Bu seçenek Global. JSON korumasını korur.</span><span class="sxs-lookup"><span data-stu-id="98eb2-281">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="98eb2-282">Önizleme olarak işaretlenen .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="98eb2-282">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="98eb2-283">En yüksek önizleme dışında, önizleme olarak işaretlenen .NET Core SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="98eb2-283">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="98eb2-284">Belirtilen sürümle eşleşen .NET Core SDK 'larını ve çalışma zamanlarını kaldırır `major.minor` .</span><span class="sxs-lookup"><span data-stu-id="98eb2-284">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="98eb2-285">Yalnızca .NET Core çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="98eb2-285">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="98eb2-286">Yalnızca .NET Core SDK 'larını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="98eb2-286">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="98eb2-287">Ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="98eb2-287">Sets the verbosity level.</span></span> <span data-ttu-id="98eb2-288">İzin verilen değerler,,, `q[uiet]` `m[inimal]` `n[ormal]` `d[etailed]` ve `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="98eb2-288">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="98eb2-289">Varsayılan değer: `normal`.</span><span class="sxs-lookup"><span data-stu-id="98eb2-289">The default value is `normal`.</span></span>

* <span data-ttu-id="98eb2-290">**`-y, --yes`** Komutu Y/N onayına gerek kalmadan yürütür.</span><span class="sxs-lookup"><span data-stu-id="98eb2-290">**`-y, --yes`** Executes the command without requiring Y/N confirmation.</span></span>
  
* <span data-ttu-id="98eb2-291">**`--force`** Visual Studio veya SDK 'lar tarafından kullanılan sürümlerin kaldırılmasını zorlar.</span><span class="sxs-lookup"><span data-stu-id="98eb2-291">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="98eb2-292">Notlar:</span><span class="sxs-lookup"><span data-stu-id="98eb2-292">Notes:</span></span>

1. <span data-ttu-id="98eb2-293">Ve bunlardan yalnızca `--sdk` biri `--runtime` gereklidir.</span><span class="sxs-lookup"><span data-stu-id="98eb2-293">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="98eb2-294">`--all`,,,,, `--all-below` `--all-but` `--all-but-latest` `--all-lower-patches` `--all-previews` , `--all-previews-but-latest` , `--major-minor` ve `[<VERSION>...]` dışlamalı.</span><span class="sxs-lookup"><span data-stu-id="98eb2-294">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="98eb2-295">Örnekler</span><span class="sxs-lookup"><span data-stu-id="98eb2-295">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="98eb2-296">Varsayılan olarak, Visual Studio veya diğer SDK 'lar için gerekli olabilecek .NET Core SDK 'Ları ve çalışma zamanları tutulur.</span><span class="sxs-lookup"><span data-stu-id="98eb2-296">By default, .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs are kept.</span></span> <span data-ttu-id="98eb2-297">Aşağıdaki örneklerde, belirtilen SDK ve çalışma zamanlarının bazıları makinenin durumuna bağlı olarak kalabilir.</span><span class="sxs-lookup"><span data-stu-id="98eb2-297">In the following examples, some of the specified SDKs and runtimes may remain, depending on the state of the machine.</span></span> <span data-ttu-id="98eb2-298">Tüm SDK 'Ları ve çalışma zamanlarını kaldırmak için bunları açık bağımsız değişken olarak listeleyin veya `--force` seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="98eb2-298">To remove all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="98eb2-299">Y/N onayı gerekmeden sürüm dışındaki tüm .NET Core çalışma zamanlarını kaldırın `3.0.0-preview6-27804-01` :</span><span class="sxs-lookup"><span data-stu-id="98eb2-299">Remove all .NET Core runtimes except the version `3.0.0-preview6-27804-01` without requiring Y/N confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --all-but 3.0.0-preview6-27804-01 --runtime --yes
  ```

* <span data-ttu-id="98eb2-300">Y/n onayı gerekmeden tüm .NET Core 1,1 SDK 'larını kaldırın:</span><span class="sxs-lookup"><span data-stu-id="98eb2-300">Remove all .NET Core 1.1 SDKs without requiring Y/n confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --sdk --major-minor 1.1 -y
  ```

* <span data-ttu-id="98eb2-301">Konsol çıktısı olmadan .NET Core 1.1.11 SDK 'sını kaldırın:</span><span class="sxs-lookup"><span data-stu-id="98eb2-301">Remove the .NET Core 1.1.11 SDK with no console output:</span></span>

  ```console
  dotnet-core-uninstall remove 1.1.11 --sdk --yes --verbosity q
  ```

* <span data-ttu-id="98eb2-302">Bu araç tarafından güvenli bir şekilde kaldırılabileceği tüm .NET Core SDK 'larını kaldırın:</span><span class="sxs-lookup"><span data-stu-id="98eb2-302">Remove all .NET Core SDKs that can safely be removed by this tool:</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk
  ```

* <span data-ttu-id="98eb2-303">Bu araç tarafından kaldırılabileceği tüm .NET Core SDK 'larını, Visual Studio tarafından gerekebilecek SDK 'lar da dahil olmak üzere kaldırın (önerilmez):</span><span class="sxs-lookup"><span data-stu-id="98eb2-303">Remove all .NET Core SDKs that can be removed by this tool, including those SDKs that may be required by Visual Studio (not recommended):</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk --force
  ```

* <span data-ttu-id="98eb2-304">Yanıt dosyasında belirtilen tüm .NET Core SDK 'larını kaldırın`versions.rsp`</span><span class="sxs-lookup"><span data-stu-id="98eb2-304">Remove all .NET Core SDKs that are specified in the response file `versions.rsp`</span></span>

  ```console
  dotnet-core-uninstall remove --sdk @versions.rsp
  ```

  <span data-ttu-id="98eb2-305">*Versions. rsp* içeriği aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="98eb2-305">The content of *versions.rsp* is as follows:</span></span>
  
  ```text
  2.2.300
  2.1.700
  ```

### <a name="step-4---delete-the-nuget-fallback-folder-optional"></a><span data-ttu-id="98eb2-306">4. adım-NuGet geri dönüş klasörünü silme (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="98eb2-306">Step 4 - Delete the NuGet fallback folder (optional)</span></span>

<span data-ttu-id="98eb2-307">Bazı durumlarda, artık gerekli değildir `NuGetFallbackFolder` ve silmek isteyebilir.</span><span class="sxs-lookup"><span data-stu-id="98eb2-307">In some cases, you no longer need the `NuGetFallbackFolder` and may wish to delete it.</span></span> <span data-ttu-id="98eb2-308">Bu klasörü silme hakkında daha fazla bilgi için bkz. [NuGetFallbackFolder 'ı kaldırma](../install/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).</span><span class="sxs-lookup"><span data-stu-id="98eb2-308">For more information about deleting this folder, see [Remove the NuGetFallbackFolder](../install/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).</span></span>

## <a name="uninstall-the-tool"></a><span data-ttu-id="98eb2-309">Aracı kaldır</span><span class="sxs-lookup"><span data-stu-id="98eb2-309">Uninstall the tool</span></span>

## <a name="windows"></a>[<span data-ttu-id="98eb2-310">Windows</span><span class="sxs-lookup"><span data-stu-id="98eb2-310">Windows</span></span>](#tab/windows)

1. <span data-ttu-id="98eb2-311">**Program Ekle veya Kaldır**'ı açın.</span><span class="sxs-lookup"><span data-stu-id="98eb2-311">Open **Add or Remove Programs**.</span></span>
2. <span data-ttu-id="98eb2-312">`Microsoft .NET Core SDK Uninstall Tool` arayın.</span><span class="sxs-lookup"><span data-stu-id="98eb2-312">Search for `Microsoft .NET Core SDK Uninstall Tool`.</span></span>
3. <span data-ttu-id="98eb2-313">**Kaldır**'ı seçin.</span><span class="sxs-lookup"><span data-stu-id="98eb2-313">Select **Uninstall**.</span></span>

## <a name="macos"></a>[<span data-ttu-id="98eb2-314">macOS</span><span class="sxs-lookup"><span data-stu-id="98eb2-314">macOS</span></span>](#tab/macos)

<span data-ttu-id="98eb2-315">İndirilen *DotNet-Core-Uninstall. tar. gz* dosyasını yüklendiği dizinden silin.</span><span class="sxs-lookup"><span data-stu-id="98eb2-315">Delete the downloaded *dotnet-core-uninstall.tar.gz* file from the directory where it was installed.</span></span> <span data-ttu-id="98eb2-316">Bu dosyanın içeriğini başka bir dizine sıkıştırdıysanız, bu içeriği de sildiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="98eb2-316">If you unzipped the contents of this file into another directory, be sure to delete that content as well.</span></span>

---
