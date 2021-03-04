---
title: 'Öğretici: .NET yerel araçlarını yükleyip kullanın'
description: .NET aracını yerel bir araç olarak yüklemeyi ve kullanmayı öğrenin.
ms.topic: tutorial
ms.date: 12/11/2020
ms.openlocfilehash: 29c561d27aad99c0383fc8e0bb5a4543ae65705a
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102104134"
---
# <a name="tutorial-install-and-use-a-net-local-tool-using-the-net-cli"></a><span data-ttu-id="5fd58-103">Öğretici: .NET CLı kullanarak .NET yerel aracını yükleyip kullanma</span><span class="sxs-lookup"><span data-stu-id="5fd58-103">Tutorial: Install and use a .NET local tool using the .NET CLI</span></span>

<span data-ttu-id="5fd58-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 3,0 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="5fd58-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

<span data-ttu-id="5fd58-105">Bu öğretici, yerel bir araç yüklemeyi ve kullanmayı öğretir.</span><span class="sxs-lookup"><span data-stu-id="5fd58-105">This tutorial teaches you how to install and use a local tool.</span></span> <span data-ttu-id="5fd58-106">[Bu serinin ilk öğreticisinde](global-tools-how-to-create.md)oluşturduğunuz bir aracı kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="5fd58-106">You use a tool that you create in the [first tutorial of this series](global-tools-how-to-create.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5fd58-107">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="5fd58-107">Prerequisites</span></span>

* <span data-ttu-id="5fd58-108">[Bu serinin ilk öğreticisini](global-tools-how-to-create.md)doldurun.</span><span class="sxs-lookup"><span data-stu-id="5fd58-108">Complete the [first tutorial of this series](global-tools-how-to-create.md).</span></span>
* <span data-ttu-id="5fd58-109">.NET Core 2,1 çalışma zamanını yükler.</span><span class="sxs-lookup"><span data-stu-id="5fd58-109">Install the .NET Core 2.1 runtime.</span></span>

  <span data-ttu-id="5fd58-110">Bu öğreticide, .NET Core 2,1 ' i hedefleyen bir araç yükleyip kullanacaksınız, bu yüzden çalışma zamanının makinenizde yüklü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5fd58-110">For this tutorial you install and use a tool that targets .NET Core 2.1, so you need to have that runtime installed on your machine.</span></span> <span data-ttu-id="5fd58-111">2,1 çalışma zamanını yüklemek için [.NET Core 2,1 indirme sayfasına](https://dotnet.microsoft.com/download/dotnet/2.1) gidin ve **Çalıştır-çalışma zamanı** sütununda çalışma zamanı yükleme bağlantısını bulun.</span><span class="sxs-lookup"><span data-stu-id="5fd58-111">To install the 2.1 runtime, go to the [.NET Core 2.1 download page](https://dotnet.microsoft.com/download/dotnet/2.1) and find the runtime installation link in the **Run apps - Runtime** column.</span></span>

## <a name="create-a-manifest-file"></a><span data-ttu-id="5fd58-112">Bildirim dosyası oluşturma</span><span class="sxs-lookup"><span data-stu-id="5fd58-112">Create a manifest file</span></span>

<span data-ttu-id="5fd58-113">Yalnızca yerel erişim için bir araç yüklemek üzere (geçerli dizin ve alt dizinler için), bir bildirim dosyasına eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="5fd58-113">To install a tool for local access only (for the current directory and subdirectories), it has to be added to a manifest file.</span></span>

<span data-ttu-id="5fd58-114">*Microsoft. botsay* klasöründen, *Depo* klasörü için bir düzey yukarı gidin:</span><span class="sxs-lookup"><span data-stu-id="5fd58-114">From the *microsoft.botsay* folder, navigate up one level to the *repository* folder:</span></span>

```console
cd ..
```

<span data-ttu-id="5fd58-115">[DotNet yeni](dotnet-new.md) komutunu çalıştırarak bir bildirim dosyası oluşturun:</span><span class="sxs-lookup"><span data-stu-id="5fd58-115">Create a manifest file by running the [dotnet new](dotnet-new.md) command:</span></span>

```dotnetcli
dotnet new tool-manifest
```

<span data-ttu-id="5fd58-116">Çıktı, dosyanın başarıyla oluşturulmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5fd58-116">The output indicates successful creation of the file.</span></span>

```console
The template "Dotnet local tool manifest file" was created successfully.
```

<span data-ttu-id="5fd58-117">Dosya *üzerinde. config/dotnet-tools.js* henüz bir araç içermiyor:</span><span class="sxs-lookup"><span data-stu-id="5fd58-117">The *.config/dotnet-tools.json* file has no tools in it yet:</span></span>

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {}
}
```

<span data-ttu-id="5fd58-118">Bir bildirim dosyasında listelenen araçlar geçerli dizin ve alt dizinler için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5fd58-118">The tools listed in a manifest file are available to the current directory and subdirectories.</span></span> <span data-ttu-id="5fd58-119">Geçerli dizin, bildirim dosyası ile *. config* dizinini içeren bir dizindir.</span><span class="sxs-lookup"><span data-stu-id="5fd58-119">The current directory is the one that contains the *.config* directory with the manifest file.</span></span>

<span data-ttu-id="5fd58-120">Yerel bir araca başvuran bir CLı komutu kullandığınızda, SDK geçerli dizin ve üst dizinlerde bir bildirim dosyası arar.</span><span class="sxs-lookup"><span data-stu-id="5fd58-120">When you use a CLI command that refers to a local tool, the SDK searches for a manifest file in the current directory and parent directories.</span></span> <span data-ttu-id="5fd58-121">Bir bildirim dosyası bulursa, ancak dosya başvurulan aracı içermiyorsa, üst dizinlere göre aramaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="5fd58-121">If it finds a manifest file, but the file doesn't include the referenced tool, it continues the search up through parent directories.</span></span> <span data-ttu-id="5fd58-122">Arama, başvurulan aracı bulduğunda sona erer veya olarak ayarlanmış bir bildirim dosyası bulur `isRoot` `true` .</span><span class="sxs-lookup"><span data-stu-id="5fd58-122">The search ends when it finds the referenced tool or it finds a manifest file with `isRoot` set to `true`.</span></span>

## <a name="install-botsay-as-a-local-tool"></a><span data-ttu-id="5fd58-123">Botsay 'ı yerel araç olarak yükler</span><span class="sxs-lookup"><span data-stu-id="5fd58-123">Install botsay as a local tool</span></span>

<span data-ttu-id="5fd58-124">Aracı ilk öğreticide oluşturduğunuz paketten yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5fd58-124">Install the tool from the package that you created in the first tutorial:</span></span>

```dotnetcli
dotnet tool install --add-source ./microsoft.botsay/nupkg microsoft.botsay
```

<span data-ttu-id="5fd58-125">Bu komut, önceki adımda oluşturduğunuz bildirim dosyasına aracı ekler.</span><span class="sxs-lookup"><span data-stu-id="5fd58-125">This command adds the tool to the manifest file that you created in the preceding step.</span></span> <span data-ttu-id="5fd58-126">Komut çıktısı, yeni yüklenen aracın hangi bildirim dosyasında olduğunu gösterir:</span><span class="sxs-lookup"><span data-stu-id="5fd58-126">The command output shows which manifest file the newly installed tool is in:</span></span>

 ```console
 You can invoke the tool from this directory using the following command:
 'dotnet tool run botsay' or 'dotnet botsay'
 Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
 Entry is added to the manifest file /home/name/repository/.config/dotnet-tools.json
 ```

<span data-ttu-id="5fd58-127">Dosyadaki *. config/dotnet-tools.js* artık bir araca sahiptir:</span><span class="sxs-lookup"><span data-stu-id="5fd58-127">The *.config/dotnet-tools.json* file now has one tool:</span></span>

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

## <a name="use-the-tool"></a><span data-ttu-id="5fd58-128">Aracı kullanma</span><span class="sxs-lookup"><span data-stu-id="5fd58-128">Use the tool</span></span>

<span data-ttu-id="5fd58-129">`dotnet tool run`Komutu *Depo* klasöründen çalıştırarak aracı çağırın:</span><span class="sxs-lookup"><span data-stu-id="5fd58-129">Invoke the tool by running the `dotnet tool run` command from the *repository* folder:</span></span>

```dotnetcli
dotnet tool run botsay hello from the bot
```

## <a name="restore-a-local-tool-installed-by-others"></a><span data-ttu-id="5fd58-130">Başkaları tarafından yüklenen bir yerel aracı geri yükleme</span><span class="sxs-lookup"><span data-stu-id="5fd58-130">Restore a local tool installed by others</span></span>

<span data-ttu-id="5fd58-131">Genellikle deponun kök dizinine yerel bir araç yüklersiniz.</span><span class="sxs-lookup"><span data-stu-id="5fd58-131">You typically install a local tool in the root directory of the repository.</span></span> <span data-ttu-id="5fd58-132">Bildirim dosyasını depoya iade ettikten sonra, diğer geliştiriciler en son bildirim dosyasını alabilir.</span><span class="sxs-lookup"><span data-stu-id="5fd58-132">After you check in the manifest file to the repository, other developers can get the latest manifest file.</span></span> <span data-ttu-id="5fd58-133">Bildirim dosyasında listelenen tüm araçları yüklemek için, tek bir `dotnet tool restore` komut çalıştırabilir.</span><span class="sxs-lookup"><span data-stu-id="5fd58-133">To install all of the tools listed in the manifest file, they can run a single `dotnet tool restore` command.</span></span>

1. <span data-ttu-id="5fd58-134">Dosya *üzerinde. config/dotnet-tools.js* açın ve IÇERIĞINI aşağıdaki JSON ile değiştirin:</span><span class="sxs-lookup"><span data-stu-id="5fd58-134">Open the *.config/dotnet-tools.json* file, and replace the contents with the following JSON:</span></span>

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

1. <span data-ttu-id="5fd58-135">`<name>`Projeyi oluşturmak için kullandığınız adla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="5fd58-135">Replace `<name>` with the name you used to create the project.</span></span>

1. <span data-ttu-id="5fd58-136">Yaptığınız değişiklikleri kaydedin.</span><span class="sxs-lookup"><span data-stu-id="5fd58-136">Save your changes.</span></span>

   <span data-ttu-id="5fd58-137">Bu değişikliğin yapılması, proje dizini paketini başka birisi yükledikten sonra depodan en son sürümü alma ile aynıdır `dotnetsay` .</span><span class="sxs-lookup"><span data-stu-id="5fd58-137">Making this change is the same as getting the latest version from the repository after someone else installed the package `dotnetsay` for the project directory.</span></span>

1. <span data-ttu-id="5fd58-138">`dotnet tool restore` komutunu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5fd58-138">Run the `dotnet tool restore` command.</span></span>

   ```dotnetcli
   dotnet tool restore
   ```

   <span data-ttu-id="5fd58-139">Komut aşağıdaki örnekte olduğu gibi bir çıktı üretir:</span><span class="sxs-lookup"><span data-stu-id="5fd58-139">The command produces output like the following example:</span></span>

   ```console
   Tool 'microsoft.botsay' (version '1.0.0') was restored. Available commands: botsay
   Tool 'dotnetsay' (version '2.1.3') was restored. Available commands: dotnetsay
   Restore was successful.
   ```

1. <span data-ttu-id="5fd58-140">Araçların kullanılabilir olduğunu doğrulayın:</span><span class="sxs-lookup"><span data-stu-id="5fd58-140">Verify that the tools are available:</span></span>

   ```dotnetcli
   dotnet tool list
   ```

   <span data-ttu-id="5fd58-141">Çıktı, aşağıdaki örneğe benzer şekilde paketlerin ve komutların listesidir:</span><span class="sxs-lookup"><span data-stu-id="5fd58-141">The output is a list of packages and commands, similar to the following example:</span></span>

   ```console
   Package Id      Version      Commands       Manifest
   --------------------------------------------------------------------------------------------
   microsoft.botsay 1.0.0        botsay         /home/name/repository/.config/dotnet-tools.json
   dotnetsay        2.1.3        dotnetsay      /home/name/repository/.config/dotnet-tools.json
   ```

1. <span data-ttu-id="5fd58-142">Araçları test etme:</span><span class="sxs-lookup"><span data-stu-id="5fd58-142">Test the tools:</span></span>

   ```dotnetcli
   dotnet tool run dotnetsay hello from dotnetsay
   dotnet tool run botsay hello from botsay
   ```

## <a name="update-a-local-tool"></a><span data-ttu-id="5fd58-143">Yerel bir aracı güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="5fd58-143">Update a local tool</span></span>

<span data-ttu-id="5fd58-144">Yerel aracın yüklü sürümü `dotnetsay` 2.1.3.</span><span class="sxs-lookup"><span data-stu-id="5fd58-144">The installed version of local tool `dotnetsay` is 2.1.3.</span></span>  <span data-ttu-id="5fd58-145">Aracı en son sürüme güncelleştirmek için [DotNet araç Güncelleştir](dotnet-tool-update.md) komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="5fd58-145">Use the [dotnet tool update](dotnet-tool-update.md) command to update the tool to the latest version.</span></span>

```dotnetcli
dotnet tool update dotnetsay
```

<span data-ttu-id="5fd58-146">Çıkış, yeni sürüm numarasını gösterir:</span><span class="sxs-lookup"><span data-stu-id="5fd58-146">The output indicates the new version number:</span></span>

```console
Tool 'dotnetsay' was successfully updated from version '2.1.3' to version '2.1.7'
(manifest file /home/name/repository/.config/dotnet-tools.json).
```

<span data-ttu-id="5fd58-147">Update komutu, paket KIMLIĞINI içeren ilk bildirim dosyasını bulur ve güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="5fd58-147">The update command finds the first manifest file that contains the package ID and updates it.</span></span> <span data-ttu-id="5fd58-148">Arama kapsamındaki herhangi bir bildirim dosyasında böyle bir paket KIMLIĞI yoksa, SDK en yakın bildirim dosyasına yeni bir giriş ekler.</span><span class="sxs-lookup"><span data-stu-id="5fd58-148">If there is no such package ID in any manifest file that is in the scope of the search, the SDK adds a new entry to the closest manifest file.</span></span> <span data-ttu-id="5fd58-149">İle bir bildirim dosyası bulunana kadar arama kapsamı üst dizinler üzerinden çalışır `isRoot = true` .</span><span class="sxs-lookup"><span data-stu-id="5fd58-149">The search scope is up through parent directories until a manifest file with `isRoot = true` is found.</span></span>

## <a name="remove-local-tools"></a><span data-ttu-id="5fd58-150">Yerel araçları kaldır</span><span class="sxs-lookup"><span data-stu-id="5fd58-150">Remove local tools</span></span>

<span data-ttu-id="5fd58-151">[DotNet Aracı kaldırma](dotnet-tool-uninstall.md) komutunu çalıştırarak yüklü araçları kaldırın:</span><span class="sxs-lookup"><span data-stu-id="5fd58-151">Remove the installed tools by running the [dotnet tool uninstall](dotnet-tool-uninstall.md) command:</span></span>

```dotnetcli
dotnet tool uninstall microsoft.botsay
```

```dotnetcli
dotnet tool uninstall dotnetsay
```

## <a name="troubleshoot"></a><span data-ttu-id="5fd58-152">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="5fd58-152">Troubleshoot</span></span>

<span data-ttu-id="5fd58-153">Öğreticiyi takip ederken bir hata mesajı alırsanız bkz. [.NET araç kullanım sorunlarını giderme](troubleshoot-usage-issues.md).</span><span class="sxs-lookup"><span data-stu-id="5fd58-153">If you get an error message while following the tutorial, see [Troubleshoot .NET tool usage issues](troubleshoot-usage-issues.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5fd58-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5fd58-154">See also</span></span>

<span data-ttu-id="5fd58-155">Daha fazla bilgi için bkz. [.NET araçları](global-tools.md)</span><span class="sxs-lookup"><span data-stu-id="5fd58-155">For more information, see [.NET tools](global-tools.md)</span></span>
