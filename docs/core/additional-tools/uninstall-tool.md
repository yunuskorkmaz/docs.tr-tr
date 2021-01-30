---
title: Aracı kaldır
description: .NET SDK 'larının ve çalışma zamanlarının kontrollü temizlenmesini sağlayan kılavuzlu bir araç olan .NET kaldırma aracına genel bakış.
author: sfoslund
ms.date: 01/28/2021
ms.openlocfilehash: a3819b11af94d4fec3ecb072ec3d5ddf6de706c9
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2021
ms.locfileid: "99216323"
---
# <a name="net-uninstall-tool"></a><span data-ttu-id="55acc-103">.NET kaldırma aracı</span><span class="sxs-lookup"><span data-stu-id="55acc-103">.NET Uninstall Tool</span></span>

<span data-ttu-id="55acc-104">[.Net kaldırma aracı](https://aka.ms/dotnet-core-uninstall-tool) ( `dotnet-core-uninstall` ), bir sistemden .NET SDK 'Ları ve çalışma zamanlarını kaldırmanıza imkan sağlar.</span><span class="sxs-lookup"><span data-stu-id="55acc-104">The [.NET Uninstall Tool](https://aka.ms/dotnet-core-uninstall-tool) (`dotnet-core-uninstall`) lets you remove .NET SDKs and Runtimes from a system.</span></span> <span data-ttu-id="55acc-105">Kaldırmak istediğiniz sürümleri belirlemek için bir seçenek koleksiyonu kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="55acc-105">A collection of options is available to specify which versions you want to uninstall.</span></span>

<span data-ttu-id="55acc-106">Araç Windows ve macOS 'yi destekler.</span><span class="sxs-lookup"><span data-stu-id="55acc-106">The tool supports Windows and macOS.</span></span> <span data-ttu-id="55acc-107">Linux Şu anda desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="55acc-107">Linux is currently not supported.</span></span>

<span data-ttu-id="55acc-108">Bu araç, Windows 'ta yalnızca aşağıdaki yükleyicilerden biri kullanılarak yüklenen SDK 'Ları ve çalışma zamanlarını kaldırabilir:</span><span class="sxs-lookup"><span data-stu-id="55acc-108">On Windows, the tool can only uninstall SDKs and Runtimes that were installed using one of the following installers:</span></span>

- <span data-ttu-id="55acc-109">.NET SDK ve çalışma zamanı yükleyicisi.</span><span class="sxs-lookup"><span data-stu-id="55acc-109">The .NET SDK and runtime installer.</span></span>
- <span data-ttu-id="55acc-110">Visual Studio 2019 sürüm 16,3 ' den önceki sürümlerde Visual Studio yükleyicisi.</span><span class="sxs-lookup"><span data-stu-id="55acc-110">The Visual Studio installer in versions earlier than Visual Studio 2019 version 16.3.</span></span>

<span data-ttu-id="55acc-111">MacOS 'ta, araç yalnızca */usr/local/share/DotNet* klasöründe bulunan SDK 'ları ve çalışma zamanlarını kaldırabilir.</span><span class="sxs-lookup"><span data-stu-id="55acc-111">On macOS, the tool can only uninstall SDKs and runtimes located in the */usr/local/share/dotnet* folder.</span></span>

<span data-ttu-id="55acc-112">Bu sınırlamalar nedeniyle araç, makinenizde tüm .NET SDK 'Ları ve çalışma zamanlarını kaldıramayabilir.</span><span class="sxs-lookup"><span data-stu-id="55acc-112">Because of these limitations, the tool may not be able to uninstall all of the .NET SDKs and runtimes on your machine.</span></span> <span data-ttu-id="55acc-113">`dotnet --info`Bu aracın kaldırakaldıramıyorum SDK 'lar ve çalışma zamanları dahil tüm .NET SDK 'ları ve çalışma zamanlarını bulmak için komutunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55acc-113">You can use the `dotnet --info` command to find all of the .NET SDKs and runtimes installed, including those SDKs and runtimes that this tool can't remove.</span></span> <span data-ttu-id="55acc-114">`dotnet-core-uninstall list`Komut, araçla hangi SDK 'ların kaldırılabileceği görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="55acc-114">The `dotnet-core-uninstall list` command displays which SDKs can be uninstalled with the tool.</span></span> <span data-ttu-id="55acc-115">1,2 ve üzeri sürümleri, SDK ve çalışma zamanlarını sürüm 5,0 veya daha önceki bir sürümü ile kaldırabilir ve aracın önceki sürümleri 3,1 ve önceki sürümlerini kaldırabilir.</span><span class="sxs-lookup"><span data-stu-id="55acc-115">Versions 1.2 and later can uninstall SDKs and runtimes with version 5.0 or earlier, and previous versions of the tool can uninstall 3.1 and earlier.</span></span>

## <a name="install-the-tool"></a><span data-ttu-id="55acc-116">Aracı 'nı yükler</span><span class="sxs-lookup"><span data-stu-id="55acc-116">Install the tool</span></span>

<span data-ttu-id="55acc-117">.NET kaldırma aracı 'nı [aracın yayınlar sayfasından](https://aka.ms/dotnet-core-uninstall-tool) indirebilir ve [DotNet/CLI-Lab](https://github.com/dotnet/cli-lab) GitHub deposunda kaynak kodu bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55acc-117">You can download the .NET Uninstall Tool from [the tool's releases page](https://aka.ms/dotnet-core-uninstall-tool) and find the source code at the [dotnet/cli-lab](https://github.com/dotnet/cli-lab) GitHub repository.</span></span>

> [!NOTE]
> <span data-ttu-id="55acc-118">Aracın .NET SDK 'larını ve çalışma zamanlarını kaldırması için yükseltme gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="55acc-118">The tool requires elevation to uninstall .NET SDKs and runtimes.</span></span> <span data-ttu-id="55acc-119">Bu nedenle, Windows üzerinde *C:\Program Files* veya MacOS 'ta */usr/local/bin* gibi bir yazma korumalı dizine yüklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="55acc-119">Therefore, it should be installed in a write-protected directory such as *C:\Program Files* on Windows or */usr/local/bin* on macOS.</span></span> <span data-ttu-id="55acc-120">Ayrıca bkz. [DotNet komutları Için yükseltilmiş erişim](../tools/elevated-access.md).</span><span class="sxs-lookup"><span data-stu-id="55acc-120">See also [Elevated access for dotnet commands](../tools/elevated-access.md).</span></span> <span data-ttu-id="55acc-121">Daha fazla bilgi için bkz. [ayrıntılı yükleme yönergeleri](https://aka.ms/dotnet-core-uninstall-tool).</span><span class="sxs-lookup"><span data-stu-id="55acc-121">For more information, see the [detailed installation instructions](https://aka.ms/dotnet-core-uninstall-tool).</span></span>

## <a name="run-the-tool"></a><span data-ttu-id="55acc-122">Aracı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="55acc-122">Run the tool</span></span>

<span data-ttu-id="55acc-123">Aşağıdaki adımlarda, kaldırma aracını çalıştırmak için önerilen yaklaşım gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="55acc-123">The following steps show the recommended approach for running the uninstall tool:</span></span>

- [<span data-ttu-id="55acc-124">1. adım-yüklü .NET SDK 'larını ve çalışma zamanlarını görüntüleme</span><span class="sxs-lookup"><span data-stu-id="55acc-124">Step 1 - Display installed .NET SDKs and runtimes</span></span>](#step-1---display-installed-net-sdks-and-runtimes)
- [<span data-ttu-id="55acc-125">2. adım-bir kuru çalıştırma</span><span class="sxs-lookup"><span data-stu-id="55acc-125">Step 2 - Do a dry run</span></span>](#step-2---do-a-dry-run)
- [<span data-ttu-id="55acc-126">3. adım-.NET SDK 'larını ve çalışma zamanlarını kaldırma</span><span class="sxs-lookup"><span data-stu-id="55acc-126">Step 3 - Uninstall .NET SDKs and Runtimes</span></span>](#step-3---uninstall-net-sdks-and-runtimes)
- [<span data-ttu-id="55acc-127">4. adım-NuGet geri dönüş klasörünü silme (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="55acc-127">Step 4 - Delete the NuGet fallback folder (optional)</span></span>](#step-4---delete-the-nuget-fallback-folder-optional)

### <a name="step-1---display-installed-net-sdks-and-runtimes"></a><span data-ttu-id="55acc-128">1. adım-yüklü .NET SDK 'larını ve çalışma zamanlarını görüntüleme</span><span class="sxs-lookup"><span data-stu-id="55acc-128">Step 1 - Display installed .NET SDKs and runtimes</span></span>

<span data-ttu-id="55acc-129">`dotnet-core-uninstall list`Komutu, bu araçla kaldırılamayan yüklü .NET SDK 'larını ve çalışma zamanlarını listeler.</span><span class="sxs-lookup"><span data-stu-id="55acc-129">The `dotnet-core-uninstall list` command lists the installed .NET SDKs and runtimes that can be removed with this tool.</span></span> <span data-ttu-id="55acc-130">Bazı SDK 'lar ve çalışma zamanları Visual Studio için gerekli olabilir ve bunların kaldırılması önerilmez.</span><span class="sxs-lookup"><span data-stu-id="55acc-130">Some SDKs and runtimes may be required by Visual Studio and they're displayed with a note of why it isn't recommended to uninstall them.</span></span>

> [!NOTE]
> <span data-ttu-id="55acc-131">Komutun çıktısı, `dotnet-core-uninstall list` çoğu durumda çıkış içindeki yüklü sürümlerin listesiyle eşleşmez `dotnet --info` .</span><span class="sxs-lookup"><span data-stu-id="55acc-131">The output of the `dotnet-core-uninstall list` command will not match the list of installed versions in the output of `dotnet --info` in most cases.</span></span> <span data-ttu-id="55acc-132">Özellikle, bu araç ZIP dosyaları tarafından yüklenen veya Visual Studio tarafından yönetilen sürümleri (Visual Studio 2019 16,3 veya üzeri sürümleriyle yüklenmiş herhangi bir sürüm) görüntüleyemez.</span><span class="sxs-lookup"><span data-stu-id="55acc-132">Specifically, this tool will not display versions installed by zip files or managed by Visual Studio (any version installed with Visual Studio 2019 16.3 or later).</span></span> <span data-ttu-id="55acc-133">Bir sürümün Visual Studio tarafından yönetilip yönetilmediğini kontrol etmenin bir yolu `Add or Remove Programs` , Visual Studio tarafından yönetilen sürümlerin görüntüleme adlarında gösterildiği gibi işaretlendiğine göz atın.</span><span class="sxs-lookup"><span data-stu-id="55acc-133">One way to check if a version is managed by Visual Studio is to view it in `Add or Remove Programs`, where Visual Studio managed versions are marked as such in their display names.</span></span>

<span data-ttu-id="55acc-134">**DotNet-çekirdek-kaldırma listesi**</span><span class="sxs-lookup"><span data-stu-id="55acc-134">**dotnet-core-uninstall list**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="55acc-135">Özeti</span><span class="sxs-lookup"><span data-stu-id="55acc-135">Synopsis</span></span>

```console
dotnet-core-uninstall list [options]
```

#### <a name="options"></a><span data-ttu-id="55acc-136">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="55acc-136">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="55acc-137">Windows</span><span class="sxs-lookup"><span data-stu-id="55acc-137">Windows</span></span>](#tab/windows)

* **`--aspnet-runtime`**

  <span data-ttu-id="55acc-138">Bu araçla kaldırılabilecek tüm ASP.NET çalışma zamanlarını listeler.</span><span class="sxs-lookup"><span data-stu-id="55acc-138">Lists all the ASP.NET Runtimes that can be uninstalled with this tool.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="55acc-139">Bu araçla kaldırılabilecek tüm .NET barındırma paketlerini listeler.</span><span class="sxs-lookup"><span data-stu-id="55acc-139">Lists all the .NET hosting bundles that can be uninstalled with this tool.</span></span>

* **`--runtime`**

  <span data-ttu-id="55acc-140">Bu araçla kaldırılabilecek tüm .NET çalışma zamanları listeler.</span><span class="sxs-lookup"><span data-stu-id="55acc-140">Lists all .NET Runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="55acc-141">Bu araçla kaldırılabilecek tüm .NET SDK 'larını listeler.</span><span class="sxs-lookup"><span data-stu-id="55acc-141">Lists all .NET SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="55acc-142">Ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="55acc-142">Sets the verbosity level.</span></span> <span data-ttu-id="55acc-143">İzin verilen değerler,,, `q[uiet]` `m[inimal]` `n[ormal]` `d[etailed]` ve `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="55acc-143">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="55acc-144">`normal` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="55acc-144">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="55acc-145">Bu araçla kaldırılabilecek tüm x64 .NET SDK ve çalışma zamanlarını listeler.</span><span class="sxs-lookup"><span data-stu-id="55acc-145">Lists all x64 .NET SDKs and runtimes that can be uninstalled with this tool.</span></span>

* **`--x86`**

  <span data-ttu-id="55acc-146">Bu araçla kaldırılabilecek tüm x86 .NET SDK 'larını ve çalışma zamanlarını listeler.</span><span class="sxs-lookup"><span data-stu-id="55acc-146">Lists all x86 .NET SDKs and runtimes that can be uninstalled with this tool.</span></span>

## <a name="macos"></a>[<span data-ttu-id="55acc-147">macOS</span><span class="sxs-lookup"><span data-stu-id="55acc-147">macOS</span></span>](#tab/macos)

* **`--runtime`**

  <span data-ttu-id="55acc-148">Bu araçla kaldırılabilecek tüm .NET çalışma zamanları listeler.</span><span class="sxs-lookup"><span data-stu-id="55acc-148">Lists all .NET Runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="55acc-149">Bu araçla kaldırılabilecek tüm .NET SDK 'larını listeler.</span><span class="sxs-lookup"><span data-stu-id="55acc-149">Lists all .NET SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="55acc-150">Ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="55acc-150">Sets the verbosity level.</span></span> <span data-ttu-id="55acc-151">İzin verilen değerler,,, `q[uiet]` `m[inimal]` `n[ormal]` `d[etailed]` ve `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="55acc-151">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="55acc-152">`normal` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="55acc-152">The default value is `normal`.</span></span>
  
---

#### <a name="examples"></a><span data-ttu-id="55acc-153">Örnekler</span><span class="sxs-lookup"><span data-stu-id="55acc-153">Examples</span></span>

* <span data-ttu-id="55acc-154">Bu araçla kaldırılabileceği tüm .NET SDK 'Ları ve çalışma zamanlarını listeleyin:</span><span class="sxs-lookup"><span data-stu-id="55acc-154">List all .NET SDKs and runtimes that can be removed with this tool:</span></span>

  ```console
  dotnet-core-uninstall list
  ```

* <span data-ttu-id="55acc-155">Tüm x64 .NET SDK 'larını ve çalışma zamanlarını listeleyin:</span><span class="sxs-lookup"><span data-stu-id="55acc-155">List all x64 .NET SDKs and runtimes:</span></span>

  ```console
  dotnet-core-uninstall list --x64
  ```

* <span data-ttu-id="55acc-156">Tüm x86 .NET SDK 'larını listeleyin:</span><span class="sxs-lookup"><span data-stu-id="55acc-156">List all x86 .NET SDKs:</span></span>

  ```console
  dotnet-core-uninstall list --sdk --x86
  ```

### <a name="step-2---do-a-dry-run"></a><span data-ttu-id="55acc-157">2. adım-bir kuru çalıştırma</span><span class="sxs-lookup"><span data-stu-id="55acc-157">Step 2 - Do a dry run</span></span>

<span data-ttu-id="55acc-158">`dotnet-core-uninstall dry-run`Ve `dotnet-core-uninstall whatif` komutları, kaldırma işlemi yapılmadan belirtilen seçeneklere göre kaldırılacak .NET SDK 'larını ve çalışma zamanlarını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="55acc-158">The `dotnet-core-uninstall dry-run` and `dotnet-core-uninstall whatif` commands display the .NET SDKs and runtimes that will be removed based on the options provided without performing the uninstall.</span></span> <span data-ttu-id="55acc-159">Bu komutlar eş anlamlılardır.</span><span class="sxs-lookup"><span data-stu-id="55acc-159">These commands are synonyms.</span></span>

<span data-ttu-id="55acc-160">**DotNet-çekirdek-kaldırma kuru çalıştırma ve DotNet-çekirdek-kaldırma whatIf**</span><span class="sxs-lookup"><span data-stu-id="55acc-160">**dotnet-core-uninstall dry-run and dotnet-core-uninstall whatif**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="55acc-161">Özeti</span><span class="sxs-lookup"><span data-stu-id="55acc-161">Synopsis</span></span>

```console
dotnet-core-uninstall dry-run [options] [<VERSION>...]

dotnet-core-uninstall whatif [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="55acc-162">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="55acc-162">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="55acc-163">Kaldırılacak belirtilen sürüm.</span><span class="sxs-lookup"><span data-stu-id="55acc-163">The specified version to uninstall.</span></span> <span data-ttu-id="55acc-164">Birden çok sürümü, boşluklarla ayırarak, birbirinden daha sonra listeleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55acc-164">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="55acc-165">Yanıt dosyaları da desteklenir.</span><span class="sxs-lookup"><span data-stu-id="55acc-165">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="55acc-166">Yanıt dosyaları, tüm sürümlerin komut satırına yerleştirilmesi için bir alternatiftir.</span><span class="sxs-lookup"><span data-stu-id="55acc-166">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="55acc-167">Bunlar genellikle \* . rsp uzantılı metin dosyalarıdır ve her sürüm ayrı bir satırda listelenir.</span><span class="sxs-lookup"><span data-stu-id="55acc-167">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="55acc-168">Bağımsız değişken için bir yanıt dosyası belirtmek için `VERSION` , \@ hemen arkasından yanıt dosyası adı gelen karakteri kullanın.</span><span class="sxs-lookup"><span data-stu-id="55acc-168">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="55acc-169">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="55acc-169">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="55acc-170">Windows</span><span class="sxs-lookup"><span data-stu-id="55acc-170">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="55acc-171">Tüm .NET SDK 'Ları ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="55acc-171">Removes all .NET SDKs and runtimes.</span></span>

* **`--all-below <VERSION>[ <VERSION>...]`**

  <span data-ttu-id="55acc-172">Belirtilen sürümden daha küçük bir sürüme sahip yalnızca .NET SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="55acc-172">Removes only the .NET SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="55acc-173">Belirtilen sürüm yüklü durumda kalır.</span><span class="sxs-lookup"><span data-stu-id="55acc-173">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>[ <VERSION>...]`**

  <span data-ttu-id="55acc-174">Belirtilen sürümler hariç tüm .NET SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="55acc-174">Removes all .NET SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="55acc-175">En yüksek sürüm dışında .NET SDK 'Ları ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="55acc-175">Removes .NET SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="55acc-176">Daha yüksek düzeltme eklerinin yerine geçen .NET SDK 'Ları ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="55acc-176">Removes .NET SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="55acc-177">Bu seçenek global.jskorur.</span><span class="sxs-lookup"><span data-stu-id="55acc-177">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="55acc-178">Önizleme olarak işaretlenen .NET SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="55acc-178">Removes .NET SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="55acc-179">En yüksek önizleme dışında, önizleme olarak işaretlenen .NET SDK 'Ları ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="55acc-179">Removes .NET SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="55acc-180">Yalnızca ASP.NET çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="55acc-180">Removes ASP.NET Runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="55acc-181">Yalnızca .NET çalışma zamanı ve barındırma paketleri kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="55acc-181">Removes .NET Runtime and hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="55acc-182">Belirtilen sürümle eşleşen .NET SDK 'larını ve çalışma zamanlarını kaldırır `major.minor` .</span><span class="sxs-lookup"><span data-stu-id="55acc-182">Removes .NET SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="55acc-183">Yalnızca .NET çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="55acc-183">Removes .NET Runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="55acc-184">Yalnızca .NET SDK 'larını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="55acc-184">Removes .NET SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="55acc-185">Ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="55acc-185">Sets the verbosity level.</span></span> <span data-ttu-id="55acc-186">İzin verilen değerler,,, `q[uiet]` `m[inimal]` `n[ormal]` `d[etailed]` ve `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="55acc-186">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="55acc-187">`normal` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="55acc-187">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="55acc-188">`--sdk` `--runtime` `--aspnet-runtime` X64 SDK 'larını veya çalışma zamanlarını kaldırmak için, ve ile birlikte kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="55acc-188">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="55acc-189">`--sdk` `--runtime` `--aspnet-runtime` X86 SDK 'larını veya çalışma zamanlarını kaldırmak için ve ile birlikte kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="55acc-189">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="55acc-190">**`--force`** Visual Studio tarafından kullanılabilecek sürümlerin kaldırılmasını zorlar.</span><span class="sxs-lookup"><span data-stu-id="55acc-190">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="55acc-191">Notlar:</span><span class="sxs-lookup"><span data-stu-id="55acc-191">Notes:</span></span>

1. <span data-ttu-id="55acc-192">,, Ve yalnızca biri `--sdk` `--runtime` `--aspnet-runtime` `--hosting-bundle` gereklidir.</span><span class="sxs-lookup"><span data-stu-id="55acc-192">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="55acc-193">`--all`,,,,, `--all-below` `--all-but` `--all-but-latest` `--all-lower-patches` `--all-previews` , `--all-previews-but-latest` , `--major-minor` ve `[<VERSION>...]` dışlamalı.</span><span class="sxs-lookup"><span data-stu-id="55acc-193">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="55acc-194">`--x64`Veya `--x86` belirtilmemişse, hem x64 hem de x86 kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="55acc-194">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macos"></a>[<span data-ttu-id="55acc-195">macOS</span><span class="sxs-lookup"><span data-stu-id="55acc-195">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="55acc-196">Tüm .NET SDK 'Ları ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="55acc-196">Removes all .NET SDKs and runtimes.</span></span>

* **`--all-below <VERSION>[ <VERSION>...]`**

  <span data-ttu-id="55acc-197">Belirtilen sürümün altındaki .NET SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="55acc-197">Removes .NET SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="55acc-198">Belirtilen sürüm kalacak.</span><span class="sxs-lookup"><span data-stu-id="55acc-198">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>[ <VERSION>...]`**

  <span data-ttu-id="55acc-199">Bu sürümler dışında .NET SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="55acc-199">Removes .NET SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="55acc-200">En yüksek sürüm dışında .NET SDK 'Ları ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="55acc-200">Removes .NET SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="55acc-201">Daha yüksek düzeltme eklerinin yerine geçen .NET SDK 'Ları ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="55acc-201">Removes .NET SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="55acc-202">Bu seçenek global.jskorur.</span><span class="sxs-lookup"><span data-stu-id="55acc-202">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="55acc-203">Önizleme olarak işaretlenen .NET SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="55acc-203">Removes .NET SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="55acc-204">En yüksek önizleme dışında, önizleme olarak işaretlenen .NET SDK 'Ları ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="55acc-204">Removes .NET SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="55acc-205">Belirtilen sürümle eşleşen .NET SDK 'larını ve çalışma zamanlarını kaldırır `major.minor` .</span><span class="sxs-lookup"><span data-stu-id="55acc-205">Removes .NET SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="55acc-206">Yalnızca .NET çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="55acc-206">Removes .NET Runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="55acc-207">Yalnızca .NET SDK 'larını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="55acc-207">Removes .NET SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="55acc-208">Ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="55acc-208">Sets the verbosity level.</span></span> <span data-ttu-id="55acc-209">İzin verilen değerler,,, `q[uiet]` `m[inimal]` `n[ormal]` `d[etailed]` ve `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="55acc-209">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="55acc-210">`normal` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="55acc-210">The default value is `normal`.</span></span>
  
* <span data-ttu-id="55acc-211">**`--force`** Visual Studio veya SDK 'lar tarafından kullanılan sürümlerin kaldırılmasını zorlar.</span><span class="sxs-lookup"><span data-stu-id="55acc-211">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="55acc-212">Notlar:</span><span class="sxs-lookup"><span data-stu-id="55acc-212">Notes:</span></span>

1. <span data-ttu-id="55acc-213">Ve bunlardan yalnızca `--sdk` biri `--runtime` gereklidir.</span><span class="sxs-lookup"><span data-stu-id="55acc-213">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="55acc-214">`--all`,,,,, `--all-below` `--all-but` `--all-but-latest` `--all-lower-patches` `--all-previews` , `--all-previews-but-latest` , `--major-minor` ve `[<VERSION>...]` dışlamalı.</span><span class="sxs-lookup"><span data-stu-id="55acc-214">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="55acc-215">Örnekler</span><span class="sxs-lookup"><span data-stu-id="55acc-215">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="55acc-216">Varsayılan olarak, Visual Studio veya diğer SDK 'lar için gerekli olabilecek .NET SDK 'Ları ve çalışma zamanları çıkışa dahil edilmez `dotnet-core-uninstall dry-run` .</span><span class="sxs-lookup"><span data-stu-id="55acc-216">By default, .NET SDKs and runtimes that may be required by Visual Studio or other SDKs are not included in `dotnet-core-uninstall dry-run` output.</span></span> <span data-ttu-id="55acc-217">Aşağıdaki örneklerde, makinenin durumuna bağlı olarak belirtilen SDK ve çalışma zamanlarının bazıları çıkışa dahil edilmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="55acc-217">In the following examples, some of the specified SDKs and runtimes may not be included in the output, depending on the state of the machine.</span></span> <span data-ttu-id="55acc-218">Tüm SDK 'Ları ve çalışma zamanlarını dahil etmek için bunları açık bağımsız değişken olarak listeleyin veya `--force` seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="55acc-218">To include all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="55acc-219">Daha yüksek düzeltme eklerinin yerini aldığı tüm .NET çalışma zamanlarını kaldırma konusunda Kuru çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="55acc-219">Dry run of removing all .NET Runtimes that have been superseded by higher patches:</span></span>

  ```console
  dotnet-core-uninstall dry-run --all-lower-patches --runtime
  ```

* <span data-ttu-id="55acc-220">Sürümün altındaki tüm .NET SDK 'larını kaldırma konusunda Kuru çalıştırın `2.2.301` :</span><span class="sxs-lookup"><span data-stu-id="55acc-220">Dry run of removing all .NET SDKs below the version `2.2.301`:</span></span>

  ```console
  dotnet-core-uninstall whatif --all-below 2.2.301 --sdk
  ```

### <a name="step-3---uninstall-net-sdks-and-runtimes"></a><span data-ttu-id="55acc-221">3. adım-.NET SDK 'larını ve çalışma zamanlarını kaldırma</span><span class="sxs-lookup"><span data-stu-id="55acc-221">Step 3 - Uninstall .NET SDKs and Runtimes</span></span>

<span data-ttu-id="55acc-222">`dotnet-core-uninstall remove` bir seçenek koleksiyonuyla belirtilen .NET SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="55acc-222">`dotnet-core-uninstall remove` uninstalls .NET SDKs and Runtimes that are specified by a collection of options.</span></span> <span data-ttu-id="55acc-223">1,2 ve üzeri sürümleri, SDK ve çalışma zamanlarını sürüm 5,0 veya daha önceki bir sürümü ile kaldırabilir ve aracın önceki sürümleri 3,1 ve önceki sürümlerini kaldırabilir.</span><span class="sxs-lookup"><span data-stu-id="55acc-223">Versions 1.2 and later can uninstall SDKs and runtimes with version 5.0 or earlier, and previous versions of the tool can uninstall 3.1 and earlier.</span></span>

<span data-ttu-id="55acc-224">Bu aracın bozucu bir davranışı olduğundan, Kaldır komutunu çalıştırmadan önce bir kuru çalıştırma yapmanız **önemle** önerilir.</span><span class="sxs-lookup"><span data-stu-id="55acc-224">Since this tool has a destructive behavior, it's **highly** recommended that you do a dry run before running the remove command.</span></span> <span data-ttu-id="55acc-225">Kuru çalıştırma, komutu kullandığınızda hangi .NET SDK 'sının ve çalışma zamanlarının kaldırılacağını gösterir `remove` .</span><span class="sxs-lookup"><span data-stu-id="55acc-225">The dry run will show you what .NET SDKs and runtimes will be removed when you use the `remove` command.</span></span> <span data-ttu-id="55acc-226">Hangi SDK 'ların ve çalışma zamanlarının kaldırılacağını öğrenmek için bkz. [bir sürümü kaldırmalıyım?](../install/remove-runtime-sdk-versions.md#should-i-remove-a-version) .</span><span class="sxs-lookup"><span data-stu-id="55acc-226">Refer to [Should I remove a version?](../install/remove-runtime-sdk-versions.md#should-i-remove-a-version) to learn which SDKs and runtimes are safe to remove.</span></span>

> [!CAUTION]
> <span data-ttu-id="55acc-227">Aşağıdaki uyarıları aklınızda bulundurun:</span><span class="sxs-lookup"><span data-stu-id="55acc-227">Keep in mind the following caveats:</span></span>
>
>- <span data-ttu-id="55acc-228">Bu araç, makinenizde bulunan dosyalar için gerekli olan .NET SDK sürümlerini kaldırabilir `global.json` .</span><span class="sxs-lookup"><span data-stu-id="55acc-228">This tool can uninstall versions of the .NET SDK that are required by `global.json` files on your machine.</span></span> <span data-ttu-id="55acc-229">.NET SDK 'larını [indirme .net](https://dotnet.microsoft.com/download/dotnet-core) sayfasından yeniden yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55acc-229">You can reinstall .NET SDKs from the [Download .NET](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>
>- <span data-ttu-id="55acc-230">Bu araç, makinenizde bağımlı uygulamalar için gerekli olan .NET çalışma zamanının sürümlerini kaldırabilir.</span><span class="sxs-lookup"><span data-stu-id="55acc-230">This tool can uninstall versions of the .NET Runtime that are required by framework dependent applications on your machine.</span></span> <span data-ttu-id="55acc-231">.NET çalışma zamanlarını [.net yükleme](https://dotnet.microsoft.com/download/dotnet-core) sayfasından yeniden yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55acc-231">You can reinstall .NET Runtimes from the [Download .NET](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>
>- <span data-ttu-id="55acc-232">Bu araç, Visual Studio 'nun temel aldığı .NET SDK ve çalışma zamanının sürümlerini kaldırabilir.</span><span class="sxs-lookup"><span data-stu-id="55acc-232">This tool can uninstall versions of the .NET SDK and runtime that Visual Studio relies on.</span></span> <span data-ttu-id="55acc-233">Visual Studio yüklemenizi ayırırsanız, çalışma durumuna geri dönmek için Visual Studio yükleyicisindeki "Onar" ı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="55acc-233">If you break your Visual Studio installation, run "Repair" in the Visual Studio installer to get back to a working state.</span></span>

<span data-ttu-id="55acc-234">Varsayılan olarak, tüm komutlar, Visual Studio veya diğer SDK 'lar için gerekli olabilecek .NET SDK 'larını ve çalışma zamanlarını saklar.</span><span class="sxs-lookup"><span data-stu-id="55acc-234">By default, all commands keep the .NET SDKs and runtimes that may be required by Visual Studio or other SDKs.</span></span> <span data-ttu-id="55acc-235">Bu SDK 'lar ve çalışma zamanları, açıkça bağımsız değişken olarak listelenerek veya seçeneği kullanılarak kaldırılabilir `--force` .</span><span class="sxs-lookup"><span data-stu-id="55acc-235">These SDKs and runtimes can be uninstalled by listing them explicitly as arguments or by using the `--force` option.</span></span>

<span data-ttu-id="55acc-236">Aracın .NET SDK 'larını ve çalışma zamanlarını kaldırması için yükseltme gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="55acc-236">The tool requires elevation to uninstall .NET SDKs and runtimes.</span></span> <span data-ttu-id="55acc-237">Aracı, Windows 'da ve macOS 'ta bulunan bir yönetici komut isteminde çalıştırın `sudo` .</span><span class="sxs-lookup"><span data-stu-id="55acc-237">Run the tool in an Administrator command prompt on Windows and with `sudo` on macOS.</span></span> <span data-ttu-id="55acc-238">`dry-run`Ve `whatif` komutları yükseltme gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="55acc-238">The `dry-run` and `whatif` commands don't require elevation.</span></span>

<span data-ttu-id="55acc-239">**DotNet-çekirdek-kaldırma kaldırma**</span><span class="sxs-lookup"><span data-stu-id="55acc-239">**dotnet-core-uninstall remove**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="55acc-240">Özeti</span><span class="sxs-lookup"><span data-stu-id="55acc-240">Synopsis</span></span>

```console
dotnet-core-uninstall remove [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="55acc-241">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="55acc-241">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="55acc-242">Kaldırılacak belirtilen sürüm.</span><span class="sxs-lookup"><span data-stu-id="55acc-242">The specified version to uninstall.</span></span> <span data-ttu-id="55acc-243">Birden çok sürümü, boşluklarla ayırarak, birbirinden daha sonra listeleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55acc-243">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="55acc-244">Yanıt dosyaları da desteklenir.</span><span class="sxs-lookup"><span data-stu-id="55acc-244">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="55acc-245">Yanıt dosyaları, tüm sürümlerin komut satırına yerleştirilmesi için bir alternatiftir.</span><span class="sxs-lookup"><span data-stu-id="55acc-245">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="55acc-246">Bunlar genellikle \* . rsp uzantılı metin dosyalarıdır ve her sürüm ayrı bir satırda listelenir.</span><span class="sxs-lookup"><span data-stu-id="55acc-246">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="55acc-247">Bağımsız değişken için bir yanıt dosyası belirtmek için `VERSION` , \@ hemen arkasından yanıt dosyası adı gelen karakteri kullanın.</span><span class="sxs-lookup"><span data-stu-id="55acc-247">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="55acc-248">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="55acc-248">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="55acc-249">Windows</span><span class="sxs-lookup"><span data-stu-id="55acc-249">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="55acc-250">Tüm .NET SDK 'Ları ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="55acc-250">Removes all .NET SDKs and runtimes.</span></span>

* **`--all-below <VERSION>[ <VERSION>...]`**

  <span data-ttu-id="55acc-251">Belirtilen sürümden daha küçük bir sürüme sahip yalnızca .NET SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="55acc-251">Removes only the .NET SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="55acc-252">Belirtilen sürüm yüklü durumda kalır.</span><span class="sxs-lookup"><span data-stu-id="55acc-252">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>[ <VERSION>...]`**

  <span data-ttu-id="55acc-253">Belirtilen sürümler hariç tüm .NET SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="55acc-253">Removes all .NET SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="55acc-254">En yüksek sürüm dışında .NET SDK 'Ları ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="55acc-254">Removes .NET SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="55acc-255">Daha yüksek düzeltme eklerinin yerine geçen .NET SDK 'Ları ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="55acc-255">Removes .NET SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="55acc-256">Bu seçenek global.jskorur.</span><span class="sxs-lookup"><span data-stu-id="55acc-256">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="55acc-257">Önizleme olarak işaretlenen .NET SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="55acc-257">Removes .NET SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="55acc-258">En yüksek önizleme dışında, önizleme olarak işaretlenen .NET SDK 'Ları ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="55acc-258">Removes .NET SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="55acc-259">Yalnızca ASP.NET çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="55acc-259">Removes ASP.NET Runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="55acc-260">Yalnızca .NET barındırma paketleri 'ni kaldırır.</span><span class="sxs-lookup"><span data-stu-id="55acc-260">Removes .NET hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="55acc-261">Belirtilen sürümle eşleşen .NET SDK 'larını ve çalışma zamanlarını kaldırır `major.minor` .</span><span class="sxs-lookup"><span data-stu-id="55acc-261">Removes .NET SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="55acc-262">Yalnızca .NET çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="55acc-262">Removes .NET Runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="55acc-263">Yalnızca .NET SDK 'larını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="55acc-263">Removes .NET SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="55acc-264">Ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="55acc-264">Sets the verbosity level.</span></span> <span data-ttu-id="55acc-265">İzin verilen değerler,,, `q[uiet]` `m[inimal]` `n[ormal]` `d[etailed]` ve `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="55acc-265">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="55acc-266">`normal` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="55acc-266">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="55acc-267">`--sdk` `--runtime` `--aspnet-runtime` X64 SDK 'larını veya çalışma zamanlarını kaldırmak için, ve ile birlikte kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="55acc-267">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="55acc-268">`--sdk` `--runtime` `--aspnet-runtime` X86 SDK 'larını veya çalışma zamanlarını kaldırmak için ve ile birlikte kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="55acc-268">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="55acc-269">**`-y, --yes`** Komutu Evet veya onay olmadan yürütür.</span><span class="sxs-lookup"><span data-stu-id="55acc-269">**`-y, --yes`** Executes the command without requiring a yes or no confirmation.</span></span>

* <span data-ttu-id="55acc-270">**`--force`** Visual Studio tarafından kullanılabilecek sürümlerin kaldırılmasını zorlar.</span><span class="sxs-lookup"><span data-stu-id="55acc-270">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="55acc-271">Notlar:</span><span class="sxs-lookup"><span data-stu-id="55acc-271">Notes:</span></span>

1. <span data-ttu-id="55acc-272">,, Ve yalnızca biri `--sdk` `--runtime` `--aspnet-runtime` `--hosting-bundle` gereklidir.</span><span class="sxs-lookup"><span data-stu-id="55acc-272">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="55acc-273">`--all`,,,,, `--all-below` `--all-but` `--all-but-latest` `--all-lower-patches` `--all-previews` , `--all-previews-but-latest` , `--major-minor` ve `[<VERSION>...]` dışlamalı.</span><span class="sxs-lookup"><span data-stu-id="55acc-273">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="55acc-274">`--x64`Veya `--x86` belirtilmemişse, hem x64 hem de x86 kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="55acc-274">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macos"></a>[<span data-ttu-id="55acc-275">macOS</span><span class="sxs-lookup"><span data-stu-id="55acc-275">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="55acc-276">Tüm .NET SDK 'Ları ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="55acc-276">Removes all .NET SDKs and runtimes.</span></span>

* **`--all-below <VERSION>[ <VERSION>...]`**

  <span data-ttu-id="55acc-277">Belirtilen sürümün altındaki .NET SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="55acc-277">Removes .NET SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="55acc-278">Belirtilen sürüm kalacak.</span><span class="sxs-lookup"><span data-stu-id="55acc-278">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>[ <VERSION>...]`**

  <span data-ttu-id="55acc-279">Bu sürümler dışında .NET SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="55acc-279">Removes .NET SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="55acc-280">En yüksek sürüm dışında .NET SDK 'Ları ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="55acc-280">Removes .NET SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="55acc-281">Daha yüksek düzeltme eklerinin yerine geçen .NET SDK 'Ları ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="55acc-281">Removes .NET SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="55acc-282">Bu seçenek global.jskorur.</span><span class="sxs-lookup"><span data-stu-id="55acc-282">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="55acc-283">Önizleme olarak işaretlenen .NET SDK 'larını ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="55acc-283">Removes .NET SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="55acc-284">En yüksek önizleme dışında, önizleme olarak işaretlenen .NET SDK 'Ları ve çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="55acc-284">Removes .NET SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="55acc-285">Belirtilen sürümle eşleşen .NET SDK 'larını ve çalışma zamanlarını kaldırır `major.minor` .</span><span class="sxs-lookup"><span data-stu-id="55acc-285">Removes .NET SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="55acc-286">Yalnızca .NET çalışma zamanlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="55acc-286">Removes .NET Runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="55acc-287">Yalnızca .NET SDK 'larını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="55acc-287">Removes .NET SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="55acc-288">Ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="55acc-288">Sets the verbosity level.</span></span> <span data-ttu-id="55acc-289">İzin verilen değerler,,, `q[uiet]` `m[inimal]` `n[ormal]` `d[etailed]` ve `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="55acc-289">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="55acc-290">`normal` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="55acc-290">The default value is `normal`.</span></span>

* <span data-ttu-id="55acc-291">**`-y, --yes`** Komutu Y/N onayına gerek kalmadan yürütür.</span><span class="sxs-lookup"><span data-stu-id="55acc-291">**`-y, --yes`** Executes the command without requiring Y/N confirmation.</span></span>
  
* <span data-ttu-id="55acc-292">**`--force`** Visual Studio veya SDK 'lar tarafından kullanılan sürümlerin kaldırılmasını zorlar.</span><span class="sxs-lookup"><span data-stu-id="55acc-292">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="55acc-293">Notlar:</span><span class="sxs-lookup"><span data-stu-id="55acc-293">Notes:</span></span>

1. <span data-ttu-id="55acc-294">Ve bunlardan yalnızca `--sdk` biri `--runtime` gereklidir.</span><span class="sxs-lookup"><span data-stu-id="55acc-294">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="55acc-295">`--all`,,,,, `--all-below` `--all-but` `--all-but-latest` `--all-lower-patches` `--all-previews` , `--all-previews-but-latest` , `--major-minor` ve `[<VERSION>...]` dışlamalı.</span><span class="sxs-lookup"><span data-stu-id="55acc-295">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="55acc-296">Örnekler</span><span class="sxs-lookup"><span data-stu-id="55acc-296">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="55acc-297">Varsayılan olarak, Visual Studio veya diğer SDK 'lar için gerekli olabilecek .NET SDK 'Ları ve çalışma zamanları tutulur.</span><span class="sxs-lookup"><span data-stu-id="55acc-297">By default, .NET SDKs and runtimes that may be required by Visual Studio or other SDKs are kept.</span></span> <span data-ttu-id="55acc-298">Aşağıdaki örneklerde, belirtilen SDK ve çalışma zamanlarının bazıları makinenin durumuna bağlı olarak kalabilir.</span><span class="sxs-lookup"><span data-stu-id="55acc-298">In the following examples, some of the specified SDKs and runtimes may remain, depending on the state of the machine.</span></span> <span data-ttu-id="55acc-299">Tüm SDK 'Ları ve çalışma zamanlarını kaldırmak için bunları açık bağımsız değişken olarak listeleyin veya `--force` seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="55acc-299">To remove all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="55acc-300">`3.0.0-preview6-27804-01`Y/N onayına gerek kalmadan sürüm dışındaki tüm .NET çalışma zamanlarını kaldırın:</span><span class="sxs-lookup"><span data-stu-id="55acc-300">Remove all .NET Runtimes except the version `3.0.0-preview6-27804-01` without requiring Y/N confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --all-but 3.0.0-preview6-27804-01 --runtime --yes
  ```

* <span data-ttu-id="55acc-301">Y/n onayı gerekmeden tüm .NET Core 1,1 SDK 'larını kaldırın:</span><span class="sxs-lookup"><span data-stu-id="55acc-301">Remove all .NET Core 1.1 SDKs without requiring Y/n confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --sdk --major-minor 1.1 -y
  ```

* <span data-ttu-id="55acc-302">Konsol çıktısı olmadan .NET Core 1.1.11 SDK 'sını kaldırın:</span><span class="sxs-lookup"><span data-stu-id="55acc-302">Remove the .NET Core 1.1.11 SDK with no console output:</span></span>

  ```console
  dotnet-core-uninstall remove 1.1.11 --sdk --yes --verbosity q
  ```

* <span data-ttu-id="55acc-303">Bu araç tarafından güvenli bir şekilde kaldırılabileceği tüm .NET SDK 'larını kaldırın:</span><span class="sxs-lookup"><span data-stu-id="55acc-303">Remove all .NET SDKs that can safely be removed by this tool:</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk
  ```

* <span data-ttu-id="55acc-304">Visual Studio tarafından gerekebilecek SDK 'lar dahil olmak üzere, bu araç tarafından kaldırılabileceği tüm .NET SDK 'larını kaldırın (önerilmez):</span><span class="sxs-lookup"><span data-stu-id="55acc-304">Remove all .NET SDKs that can be removed by this tool, including those SDKs that may be required by Visual Studio (not recommended):</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk --force
  ```

* <span data-ttu-id="55acc-305">Yanıt dosyasında belirtilen tüm .NET SDK 'larını kaldırın `versions.rsp`</span><span class="sxs-lookup"><span data-stu-id="55acc-305">Remove all .NET SDKs that are specified in the response file `versions.rsp`</span></span>

  ```console
  dotnet-core-uninstall remove --sdk @versions.rsp
  ```

  <span data-ttu-id="55acc-306">*Versions. rsp* içeriği aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="55acc-306">The content of *versions.rsp* is as follows:</span></span>
  
  ```text
  2.2.300
  2.1.700
  ```

### <a name="step-4---delete-the-nuget-fallback-folder-optional"></a><span data-ttu-id="55acc-307">4. adım-NuGet geri dönüş klasörünü silme (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="55acc-307">Step 4 - Delete the NuGet fallback folder (optional)</span></span>

<span data-ttu-id="55acc-308">Bazı durumlarda, artık gerekli değildir `NuGetFallbackFolder` ve silmek isteyebilir.</span><span class="sxs-lookup"><span data-stu-id="55acc-308">In some cases, you no longer need the `NuGetFallbackFolder` and may wish to delete it.</span></span> <span data-ttu-id="55acc-309">Bu klasörü silme hakkında daha fazla bilgi için bkz. [NuGetFallbackFolder 'ı kaldırma](../install/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).</span><span class="sxs-lookup"><span data-stu-id="55acc-309">For more information about deleting this folder, see [Remove the NuGetFallbackFolder](../install/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).</span></span>

## <a name="uninstall-the-tool"></a><span data-ttu-id="55acc-310">Aracı kaldır</span><span class="sxs-lookup"><span data-stu-id="55acc-310">Uninstall the tool</span></span>

## <a name="windows"></a>[<span data-ttu-id="55acc-311">Windows</span><span class="sxs-lookup"><span data-stu-id="55acc-311">Windows</span></span>](#tab/windows)

1. <span data-ttu-id="55acc-312">**Program Ekle veya Kaldır**'ı açın.</span><span class="sxs-lookup"><span data-stu-id="55acc-312">Open **Add or Remove Programs**.</span></span>
2. <span data-ttu-id="55acc-313">`Microsoft .NET SDK Uninstall Tool` arayın.</span><span class="sxs-lookup"><span data-stu-id="55acc-313">Search for `Microsoft .NET SDK Uninstall Tool`.</span></span>
3. <span data-ttu-id="55acc-314">**Kaldır**'ı seçin.</span><span class="sxs-lookup"><span data-stu-id="55acc-314">Select **Uninstall**.</span></span>

## <a name="macos"></a>[<span data-ttu-id="55acc-315">macOS</span><span class="sxs-lookup"><span data-stu-id="55acc-315">macOS</span></span>](#tab/macos)

<span data-ttu-id="55acc-316">İndirilen *DotNet-Core-Uninstall. tar. gz* dosyasını yüklendiği dizinden silin.</span><span class="sxs-lookup"><span data-stu-id="55acc-316">Delete the downloaded *dotnet-core-uninstall.tar.gz* file from the directory where it was installed.</span></span> <span data-ttu-id="55acc-317">Bu dosyanın içeriğini başka bir dizine sıkıştırdıysanız, bu içeriği de sildiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="55acc-317">If you unzipped the contents of this file into another directory, be sure to delete that content as well.</span></span>

---
