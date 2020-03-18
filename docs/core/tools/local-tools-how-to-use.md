---
title: 'Öğretici: .NET Core yerel araçlarını yükleyin ve kullanın'
description: Yerel bir araç olarak bir .NET aracını nasıl yükleyip kullanacağınızı öğrenin.
ms.date: 02/12/2020
ms.openlocfilehash: a4355886513040e2436bdbd87905e5baee2dd7a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156705"
---
# <a name="tutorial-install-and-use-a-net-core-local-tool-using-the-net-core-cli"></a><span data-ttu-id="9ec87-103">Öğretici: .NET Core CLI'yi kullanarak bir .NET Core yerel aracı nı yükleyin ve kullanın</span><span class="sxs-lookup"><span data-stu-id="9ec87-103">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>

<span data-ttu-id="9ec87-104">**Bu makale şu şekilde dir:** ✔️ .NET Core 3.0 SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="9ec87-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

<span data-ttu-id="9ec87-105">Bu öğretici, yerel bir aracı nasıl yükleyip kullanacağınızı öğretir.</span><span class="sxs-lookup"><span data-stu-id="9ec87-105">This tutorial teaches you how to install and use a local tool.</span></span> <span data-ttu-id="9ec87-106">[Bu serinin ilk öğretici](global-tools-how-to-create.md)oluşturduğunuz bir araç kullanın.</span><span class="sxs-lookup"><span data-stu-id="9ec87-106">You use a tool that you create in the [first tutorial of this series](global-tools-how-to-create.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9ec87-107">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="9ec87-107">Prerequisites</span></span>

* <span data-ttu-id="9ec87-108">Bu [serinin ilk öğretici](global-tools-how-to-create.md)tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="9ec87-108">Complete the [first tutorial of this series](global-tools-how-to-create.md).</span></span>
* <span data-ttu-id="9ec87-109">.NET Core 2.1 çalışma süresini yükleyin.</span><span class="sxs-lookup"><span data-stu-id="9ec87-109">Install the .NET Core 2.1 runtime.</span></span>

  <span data-ttu-id="9ec87-110">Bu öğretici için .NET Core 2.1'i hedefleyen bir araç yükler ve kullanırsınız, bu nedenle makinenizde çalışma zamanının yüklü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9ec87-110">For this tutorial you install and use a tool that targets .NET Core 2.1, so you need to have that runtime installed on your machine.</span></span> <span data-ttu-id="9ec87-111">2.1 çalışma süresini yüklemek için [.NET Core 2.1 indirme sayfasına](https://dotnet.microsoft.com/download/dotnet-core/2.1) gidin ve **Run uygulamaları - Runtime** sütununda çalışma zamanı yükleme bağlantısını bulun.</span><span class="sxs-lookup"><span data-stu-id="9ec87-111">To install the 2.1 runtime, go to the [.NET Core 2.1 download page](https://dotnet.microsoft.com/download/dotnet-core/2.1) and find the runtime installation link in the **Run apps - Runtime** column.</span></span>

## <a name="create-a-manifest-file"></a><span data-ttu-id="9ec87-112">Bir bildirim dosyası oluşturma</span><span class="sxs-lookup"><span data-stu-id="9ec87-112">Create a manifest file</span></span>

<span data-ttu-id="9ec87-113">Yalnızca yerel erişim için bir araç yüklemek için (geçerli dizin ve alt dizinler için), bir bildirim dosyasına eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="9ec87-113">To install a tool for local access only (for the current directory and subdirectories), it has to be added to a manifest file.</span></span>

<span data-ttu-id="9ec87-114">*microsoft.botsay* klasöründen, bir düzeyyukarı depo *klasörüne* gidin:</span><span class="sxs-lookup"><span data-stu-id="9ec87-114">From the *microsoft.botsay* folder, navigate up one level to the *repository* folder:</span></span>

```console
cd ..
```

<span data-ttu-id="9ec87-115">[dotnet yeni](dotnet-new.md) komutunu çalıştırarak bir bildirim dosyası oluşturun:</span><span class="sxs-lookup"><span data-stu-id="9ec87-115">Create a manifest file by running the [dotnet new](dotnet-new.md) command:</span></span>

```dotnetcli
dotnet new tool-manifest
```

<span data-ttu-id="9ec87-116">Çıktı, dosyanın başarılı bir şekilde oluşturuldurunan kısmı gösterir.</span><span class="sxs-lookup"><span data-stu-id="9ec87-116">The output indicates successful creation of the file.</span></span>

```console
The template "Dotnet local tool manifest file" was created successfully.
```

<span data-ttu-id="9ec87-117">*.config/dotnet-tools.json* dosyasında henüz hiçbir araç bulunmamaktadır:</span><span class="sxs-lookup"><span data-stu-id="9ec87-117">The *.config/dotnet-tools.json* file has no tools in it yet:</span></span>

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {}
}
```

<span data-ttu-id="9ec87-118">Bir bildirim dosyasında listelenen araçlar geçerli dizin ve alt dizinler tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9ec87-118">The tools listed in a manifest file are available to the current directory and subdirectories.</span></span> <span data-ttu-id="9ec87-119">Geçerli dizin, *.config* dizinini içeren dizindir.</span><span class="sxs-lookup"><span data-stu-id="9ec87-119">The current directory is the one that contains the *.config* directory with the manifest file.</span></span>

<span data-ttu-id="9ec87-120">Yerel bir araca atıfta bulunan bir CLI komutu kullandığınızda, SDK geçerli dizinde ve üst dizinde bir bildirim dosyası arar.</span><span class="sxs-lookup"><span data-stu-id="9ec87-120">When you use a CLI command that refers to a local tool, the SDK searches for a manifest file in the current directory and parent directories.</span></span> <span data-ttu-id="9ec87-121">Bir bildirim dosyası bulursa, ancak dosya başvurulan aracı içermiyorsa, ana dizinler aracılığıyla aramaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="9ec87-121">If it finds a manifest file, but the file doesn't include the referenced tool, it continues the search up through parent directories.</span></span> <span data-ttu-id="9ec87-122">Başvurulan aracı bulduğunda veya `isRoot` `true`'' için ayarlanmış bir manifesto dosyası bulduğunda arama sona erer.</span><span class="sxs-lookup"><span data-stu-id="9ec87-122">The search ends when it finds the referenced tool or it finds a manifest file with `isRoot` set to `true`.</span></span>

## <a name="install-botsay-as-a-local-tool"></a><span data-ttu-id="9ec87-123">Botsay'ı yerel bir araç olarak yükleyin</span><span class="sxs-lookup"><span data-stu-id="9ec87-123">Install botsay as a local tool</span></span>

<span data-ttu-id="9ec87-124">Aracı ilk öğreticide oluşturduğunuz paketten yükleyin:</span><span class="sxs-lookup"><span data-stu-id="9ec87-124">Install the tool from the package that you created in the first tutorial:</span></span>

```dotnetcli
dotnet tool install --add-source ./microsoft.botsay/nupkg microsoft.botsay
```

<span data-ttu-id="9ec87-125">Bu komut, aracı önceki adımda oluşturduğunuz bildirim dosyasına ekler.</span><span class="sxs-lookup"><span data-stu-id="9ec87-125">This command adds the tool to the manifest file that you created in the preceding step.</span></span> <span data-ttu-id="9ec87-126">Komut çıktısı, yeni yüklenen aracın hangi bildirim dosyasında olduğunu gösterir:</span><span class="sxs-lookup"><span data-stu-id="9ec87-126">The command output shows which manifest file the newly installed tool is in:</span></span>

 ```console
 You can invoke the tool from this directory using the following command:
 'dotnet tool run botsay' or 'dotnet botsay'
 Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
 Entry is added to the manifest file /home/name/repository/.config/dotnet-tools.json
 ```

<span data-ttu-id="9ec87-127">*.config/dotnet-tools.json* dosyasının artık bir aracı vardır:</span><span class="sxs-lookup"><span data-stu-id="9ec87-127">The *.config/dotnet-tools.json* file now has one tool:</span></span>

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {
    "microsoft.botsay": {
      "version": "1.0.0",
      "commands": [
        "botsay"
      ]
    }
  }
}
```

## <a name="use-the-tool"></a><span data-ttu-id="9ec87-128">Aracı kullanma</span><span class="sxs-lookup"><span data-stu-id="9ec87-128">Use the tool</span></span>

<span data-ttu-id="9ec87-129">`dotnet tool run` *Depo* klasöründen komutu çalıştırarak aracı çağırın:</span><span class="sxs-lookup"><span data-stu-id="9ec87-129">Invoke the tool by running the `dotnet tool run` command from the *repository* folder:</span></span>

```dotnetcli
dotnet tool run botsay hello from the bot
```

## <a name="restore-a-local-tool-installed-by-others"></a><span data-ttu-id="9ec87-130">Başkaları tarafından yüklenen yerel bir aracı geri yükleme</span><span class="sxs-lookup"><span data-stu-id="9ec87-130">Restore a local tool installed by others</span></span>

<span data-ttu-id="9ec87-131">Genellikle deponun kök dizinine yerel bir araç yüklersiniz.</span><span class="sxs-lookup"><span data-stu-id="9ec87-131">You typically install a local tool in the root directory of the repository.</span></span> <span data-ttu-id="9ec87-132">Manifesto dosyasını depoya iade ettikten sonra, diğer geliştiriciler en son bildirim dosyasını alabilir.</span><span class="sxs-lookup"><span data-stu-id="9ec87-132">After you check in the manifest file to the repository, other developers can get the latest manifest file.</span></span> <span data-ttu-id="9ec87-133">Bildirim dosyasında listelenen tüm araçları yüklemek için tek `dotnet tool restore` bir komut çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9ec87-133">To install all of the tools listed in the manifest file, they can run a single `dotnet tool restore` command.</span></span>

1. <span data-ttu-id="9ec87-134">*.config/dotnet-tools.json* dosyasını açın ve içindekileri aşağıdaki JSON ile değiştirin:</span><span class="sxs-lookup"><span data-stu-id="9ec87-134">Open the *.config/dotnet-tools.json* file, and replace the contents with the following JSON:</span></span>

   ```json
   {
     "version": 1,
     "isRoot": true,
     "tools": {
       "microsoft.botsay": {
         "version": "1.0.0",
         "commands": [
           "botsay"
         ]
       },
       "dotnetsay": {
         "version": "2.1.3",
         "commands": [
           "dotnetsay"
         ]
       }
     }
   }
   ```

1. <span data-ttu-id="9ec87-135">Projeyi oluşturmak için kullandığınız adla değiştirin. `<name>`</span><span class="sxs-lookup"><span data-stu-id="9ec87-135">Replace `<name>` with the name you used to create the project.</span></span>

1. <span data-ttu-id="9ec87-136">Yaptığınız değişiklikleri kaydedin.</span><span class="sxs-lookup"><span data-stu-id="9ec87-136">Save your changes.</span></span>

   <span data-ttu-id="9ec87-137">Bu değişikliği yapmak, başka biri proje dizininin paketini `dotnetsay` yükledikten sonra depodan en son sürümü almakla aynıdır.</span><span class="sxs-lookup"><span data-stu-id="9ec87-137">Making this change is the same as getting the latest version from the repository after someone else installed the package `dotnetsay` for the project directory.</span></span>

1. <span data-ttu-id="9ec87-138">`dotnet tool restore` komutunu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9ec87-138">Run the `dotnet tool restore` command.</span></span>

   ```dotnetcli
   dotnet tool restore
   ```

   <span data-ttu-id="9ec87-139">Komut aşağıdaki örnek gibi çıktı üretir:</span><span class="sxs-lookup"><span data-stu-id="9ec87-139">The command produces output like the following example:</span></span>

   ```console
   Tool 'microsoft.botsay' (version '1.0.0') was restored. Available commands: botsay
   Tool 'dotnetsay' (version '2.1.3') was restored. Available commands: dotnetsay
   Restore was successful.
   ```

1. <span data-ttu-id="9ec87-140">Araçların kullanılabilir olduğundan doğrulayın:</span><span class="sxs-lookup"><span data-stu-id="9ec87-140">Verify that the tools are available:</span></span>

   ```dotnetcli
   dotnet tool list
   ```

   <span data-ttu-id="9ec87-141">Çıktı, aşağıdaki örneğe benzer şekilde paketlerin ve komutların bir listesidir:</span><span class="sxs-lookup"><span data-stu-id="9ec87-141">The output is a list of packages and commands, similar to the following example:</span></span>

   ```console
   Package Id      Version      Commands       Manifest
   --------------------------------------------------------------------------------------------
   microsoft.botsay 1.0.0        botsay         /home/name/repository/.config/dotnet-tools.json
   dotnetsay        2.1.3        dotnetsay      /home/name/repository/.config/dotnet-tools.json
   ```

1. <span data-ttu-id="9ec87-142">Araçları test edin:</span><span class="sxs-lookup"><span data-stu-id="9ec87-142">Test the tools:</span></span>

   ```dotnetcli
   dotnet tool run dotnetsay hello from dotnetsay
   dotnet tool run botsay hello from botsay
   ```

## <a name="update-a-local-tool"></a><span data-ttu-id="9ec87-143">Yerel bir aracı güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="9ec87-143">Update a local tool</span></span>

<span data-ttu-id="9ec87-144">Yerel aracın `dotnetsay` yüklü sürümü 2.1.3'tür.</span><span class="sxs-lookup"><span data-stu-id="9ec87-144">The installed version of local tool `dotnetsay` is 2.1.3.</span></span>  <span data-ttu-id="9ec87-145">En son sürümü 2.1.4 olduğunu.</span><span class="sxs-lookup"><span data-stu-id="9ec87-145">The latest version is 2.1.4.</span></span> <span data-ttu-id="9ec87-146">Aracı en son sürüme güncellemek için [dotnet araç güncelleştirme](dotnet-tool-update.md) komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="9ec87-146">Use the [dotnet tool update](dotnet-tool-update.md) command to update the tool to the latest version.</span></span>

```dotnetcli
dotnet tool update dotnetsay
```

<span data-ttu-id="9ec87-147">Çıktı yeni sürüm numarasını gösterir:</span><span class="sxs-lookup"><span data-stu-id="9ec87-147">The output indicates the new version number:</span></span>

```console
Tool 'dotnetsay' was successfully updated from version '2.1.3' to version '2.1.4'
(manifest file /home/name/repository/.config/dotnet-tools.json).
```

<span data-ttu-id="9ec87-148">Güncelleştirme komutu, paket kimliğini içeren ilk bildirim dosyasını bulur ve güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="9ec87-148">The update command finds the first manifest file that contains the package ID and updates it.</span></span> <span data-ttu-id="9ec87-149">Arama kapsamında ki herhangi bir bildirim dosyasında böyle bir paket kimliği yoksa, SDK en yakın bildirim dosyasına yeni bir giriş ekler.</span><span class="sxs-lookup"><span data-stu-id="9ec87-149">If there is no such package ID in any manifest file that is in the scope of the search, the SDK adds a new entry to the closest manifest file.</span></span> <span data-ttu-id="9ec87-150">Arama kapsamı, bir `isRoot = true` bildirim dosyası bulunana kadar üst dizinler aracılığıyla tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="9ec87-150">The search scope is up through parent directories until a manifest file with `isRoot = true` is found.</span></span>

## <a name="remove-local-tools"></a><span data-ttu-id="9ec87-151">Yerel araçları kaldırma</span><span class="sxs-lookup"><span data-stu-id="9ec87-151">Remove local tools</span></span>

<span data-ttu-id="9ec87-152">Yüklü araçları [dotnet aracını kaldır](dotnet-tool-uninstall.md) komutunu çalıştırarak kaldırın:</span><span class="sxs-lookup"><span data-stu-id="9ec87-152">Remove the installed tools by running the [dotnet tool uninstall](dotnet-tool-uninstall.md) command:</span></span>

```dotnetcli
dotnet tool uninstall microsoft.botsay
```

```dotnetcli
dotnet tool uninstall dotnetsay
```

## <a name="troubleshoot"></a><span data-ttu-id="9ec87-153">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="9ec87-153">Troubleshoot</span></span>

<span data-ttu-id="9ec87-154">Öğreticiyi izlerken bir hata iletisi alırsanız, [Sorun Giderme .NET Core araç kullanım sorunlarına](troubleshoot-usage-issues.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="9ec87-154">If you get an error message while following the tutorial, see [Troubleshoot .NET Core tool usage issues](troubleshoot-usage-issues.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9ec87-155">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9ec87-155">See also</span></span>

<span data-ttu-id="9ec87-156">Daha fazla bilgi için [bkz.](global-tools.md)</span><span class="sxs-lookup"><span data-stu-id="9ec87-156">For more information, see [.NET Core tools](global-tools.md)</span></span>
