---
title: Dotnet komutları için yükseltilmiş erişim
description: Yükseltilmiş erişim gerektiren dotnet komutları için en iyi uygulamaları öğrenin.
author: wli3
ms.date: 06/26/2019
ms.openlocfilehash: 3d874a76eadbf5330c4e5efe4e86bfeca0a9b504
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410646"
---
# <a name="elevated-access-for-dotnet-commands"></a><span data-ttu-id="631ef-103">Dotnet komutları için yükseltilmiş erişim</span><span class="sxs-lookup"><span data-stu-id="631ef-103">Elevated access for dotnet commands</span></span>

<span data-ttu-id="631ef-104">Yazılım geliştirme en iyi uygulamalar, az ayrıcalık gerektiren yazılım yazma için Geliştirici Kılavuzu.</span><span class="sxs-lookup"><span data-stu-id="631ef-104">Software development best practices guide developers to writing software that requires the least amount of privilege.</span></span> <span data-ttu-id="631ef-105">Ancak, performans araçları, izleme gibi bazı yazılım nedeniyle işletim sistemi kuralları yönetici izni gerektirir.</span><span class="sxs-lookup"><span data-stu-id="631ef-105">However, some software, like performance monitoring tools, requires admin permission because of operating system rules.</span></span> <span data-ttu-id="631ef-106">Aşağıdaki yönergeler, yazılımla .NET Core ile yazmak için desteklenen senaryolar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="631ef-106">The following guidance describes supported scenarios for writing such software with .NET Core.</span></span> 

<span data-ttu-id="631ef-107">Aşağıdaki komutları yükseltilmiş çalıştırılabilir:</span><span class="sxs-lookup"><span data-stu-id="631ef-107">The following commands can be run elevated:</span></span>

- <span data-ttu-id="631ef-108">`dotnet tool` gibi komutlar [dotnet aracı yükleme](dotnet-tool-install.md).</span><span class="sxs-lookup"><span data-stu-id="631ef-108">`dotnet tool` commands, such as [dotnet tool install](dotnet-tool-install.md).</span></span>
- `dotnet run --no-build`

<span data-ttu-id="631ef-109">Diğer komutlar yükseltilmiş çalıştıran önerilmemektedir.</span><span class="sxs-lookup"><span data-stu-id="631ef-109">We don't recommend running other commands elevated.</span></span> <span data-ttu-id="631ef-110">Özellikle, yükseltme ile MSBuild gibi kullandığınız komutlar önermemekteyiz [dotnet restore](dotnet-restore.md), [dotnet derleme](dotnet-build.md), ve [çalıştırma dotnet](dotnet-run.md).</span><span class="sxs-lookup"><span data-stu-id="631ef-110">In particular, we don't recommend elevation with commands that use MSBuild, such as [dotnet restore](dotnet-restore.md), [dotnet build](dotnet-build.md), and [dotnet run](dotnet-run.md).</span></span> <span data-ttu-id="631ef-111">Kullanıcı geri ve İleri kök ve sınırlı bir hesap arasında dotnet komutları kestikten sonra geçiş yaptığında birincil izin yönetimi sorunlarını sorunudur.</span><span class="sxs-lookup"><span data-stu-id="631ef-111">The primary issue is permission management problems when a user transitions back and forth between root and a restricted account after issuing dotnet commands.</span></span> <span data-ttu-id="631ef-112">Kök kullanıcı tarafından oluşturulmuş dosyaya erişime sahip olmadığından, sınırlı bir kullanıcı bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="631ef-112">You may find as a restricted user that you don't have access to the file built by a root user.</span></span> <span data-ttu-id="631ef-113">Bu sorunu çözmek için vardır, ancak bunların başlangıçta içine alın gerekmez.</span><span class="sxs-lookup"><span data-stu-id="631ef-113">There are ways to resolve this situation, but they're unnecessary to get into in the first place.</span></span>

<span data-ttu-id="631ef-114">Kök ve sınırlı bir hesap arasında sürekli geçiş yoksa sürece komutları kök olarak çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="631ef-114">You can run commands as root as long as you don’t transition back and forth between root and a restricted account.</span></span> <span data-ttu-id="631ef-115">Örneğin, bu özellik sahip oldukları için Docker kapsayıcılarını varsayılan olarak, kök olarak çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="631ef-115">For example, Docker containers run as root by default, so they have this characteristic.</span></span>

## <a name="global-tool-installation"></a><span data-ttu-id="631ef-116">Genel aracı yükleme</span><span class="sxs-lookup"><span data-stu-id="631ef-116">Global tool installation</span></span>

<span data-ttu-id="631ef-117">Aşağıdaki yönergeler, yükleme, çalıştırma ve yürütmek için yükseltilmiş izinler gerektirir ve .NET Core Araçları'nı kaldırmak için önerilen yol gösterir.</span><span class="sxs-lookup"><span data-stu-id="631ef-117">The following instructions demonstrate the recommended way to install, run, and uninstall .NET Core tools that require elevated permissions to execute.</span></span>

# <a name="windowstabwindows"></a>[<span data-ttu-id="631ef-118">Windows</span><span class="sxs-lookup"><span data-stu-id="631ef-118">Windows</span></span>](#tab/windows)

### <a name="install-the-global-tool"></a><span data-ttu-id="631ef-119">Genel aracı yükleme</span><span class="sxs-lookup"><span data-stu-id="631ef-119">Install the global tool</span></span>

<span data-ttu-id="631ef-120">Varsa klasörü `%ProgramFiles%\dotnet-tools` zaten var "Kullanıcılar" grubunu yazın veya bu dizine değiştirmek için izni olup olmadığını denetlemek için aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="631ef-120">If the folder `%ProgramFiles%\dotnet-tools` already exists, do the following to check whether the "Users" group has permission to write or modify that directory:</span></span>

* <span data-ttu-id="631ef-121">Sağ `%ProgramFiles%\dotnet-tools` klasörü ve select **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="631ef-121">Right-click the `%ProgramFiles%\dotnet-tools` folder and select **Properties**.</span></span> <span data-ttu-id="631ef-122">**Ortak özellikler** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="631ef-122">The **Common Properties** dialog box opens.</span></span> 
* <span data-ttu-id="631ef-123">Seçin **güvenlik** sekmesi. Altında **grup veya kullanıcı adları**, "Kullanıcılar" grubunu yazma veya dizin değiştirme iznine sahip olup olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="631ef-123">Select the **Security** tab. Under **Group or user names**, check whether the “Users” group has permission to write or modify the directory.</span></span> 
* <span data-ttu-id="631ef-124">"Kullanıcılar" grubunu yazma veya dizinini değiştirin, Araçlar yüklenirken farklı dizin adı kullanmak yerine *dotnet-tools*.</span><span class="sxs-lookup"><span data-stu-id="631ef-124">If the "Users" group can write or modify the directory, use a different directory name when installing the tools rather than *dotnet-tools*.</span></span>

<span data-ttu-id="631ef-125">Araçları yüklemek için yükseltilmiş isteminde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="631ef-125">To install tools, run the following command in elevated prompt.</span></span> <span data-ttu-id="631ef-126">Oluşturacağı *dotnet-tools* yüklenmesi sırasında klasör.</span><span class="sxs-lookup"><span data-stu-id="631ef-126">It will create the *dotnet-tools* folder during the installation.</span></span>

```cmd
dotnet tool install PACKAGEID --tool-path "%ProgramFiles%\dotnet-tools".
```

### <a name="run-the-global-tool"></a><span data-ttu-id="631ef-127">Genel aracı çalıştırın</span><span class="sxs-lookup"><span data-stu-id="631ef-127">Run the global tool</span></span>

<span data-ttu-id="631ef-128">**1. seçenek** yükseltilmiş istemiyle tam yolu kullanın:</span><span class="sxs-lookup"><span data-stu-id="631ef-128">**Option 1** Use the full path with elevated prompt:</span></span>

```cmd
"%ProgramFiles%\dotnet-tools\TOOLCOMMAND"
```

<span data-ttu-id="631ef-129">**2. seçenek** eklemek için yeni oluşturulan klasör `%Path%`.</span><span class="sxs-lookup"><span data-stu-id="631ef-129">**Option 2** Add the newly created folder to `%Path%`.</span></span> <span data-ttu-id="631ef-130">Yalnızca bir kez bu işlemi yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="631ef-130">You only need to do this operation once.</span></span>

```cmd
setx Path "%Path%;%ProgramFiles%\dotnet-tools\"
```

<span data-ttu-id="631ef-131">Ve çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="631ef-131">And run with:</span></span>

```cmd
TOOLCOMMAND
```

### <a name="uninstall-the-global-tool"></a><span data-ttu-id="631ef-132">Genel Aracı kaldırma</span><span class="sxs-lookup"><span data-stu-id="631ef-132">Uninstall the global tool</span></span>

<span data-ttu-id="631ef-133">Yükseltilmiş isteminde, aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="631ef-133">In an elevated prompt, type the following command:</span></span>

```cmd
dotnet tool uninstall PACKAGEID --tool-path "%ProgramFiles%\dotnet-tools"
```

# <a name="linuxtablinux"></a>[<span data-ttu-id="631ef-134">Linux</span><span class="sxs-lookup"><span data-stu-id="631ef-134">Linux</span></span>](#tab/linux)

[!INCLUDE [elevated-access-unix](../../../includes/elevated-access-unix.md)]

# <a name="macostabmacos"></a>[<span data-ttu-id="631ef-135">macOS</span><span class="sxs-lookup"><span data-stu-id="631ef-135">macOS</span></span>](#tab/macos)

[!INCLUDE [elevated-access-unix](../../../includes/elevated-access-unix.md)]

---

## <a name="local-tools"></a><span data-ttu-id="631ef-136">Yerel Araçlar</span><span class="sxs-lookup"><span data-stu-id="631ef-136">Local tools</span></span>

<span data-ttu-id="631ef-137">Yerel Araçlar, kullanıcı başına alt ağacı başına belirlenir.</span><span class="sxs-lookup"><span data-stu-id="631ef-137">Local tools are scoped per subdirectory tree, per user.</span></span> <span data-ttu-id="631ef-138">Yükseltilmiş çalıştırdığınızda, yerel Araçlar yükseltilmiş ortamı için kısıtlı kullanıcı ortamını paylaşın.</span><span class="sxs-lookup"><span data-stu-id="631ef-138">When run elevated, local tools share a restricted user environment to the elevated environment.</span></span> <span data-ttu-id="631ef-139">Linux ve macOS, kök yalnızca kullanıcı erişimi ile ayarlanan dosyaları sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="631ef-139">In Linux and macOS, this results in files being set with root user-only access.</span></span> <span data-ttu-id="631ef-140">Kullanıcı, kısıtlı bir hesapta geçerse, kullanıcı artık erişmek veya dosyalara yazmak.</span><span class="sxs-lookup"><span data-stu-id="631ef-140">If the user switches back to a restricted account, the user can no longer access or write to the files.</span></span> <span data-ttu-id="631ef-141">Bu nedenle yerel araçlar olarak yetki yükseltmesi gerektiren araçlarını yükleme önerilmez.</span><span class="sxs-lookup"><span data-stu-id="631ef-141">So installing tools that require elevation as local tools isn't recommended.</span></span> <span data-ttu-id="631ef-142">Bunun yerine, `--tool-path` seçeneği ve genel araçları için önceki yönergeleri.</span><span class="sxs-lookup"><span data-stu-id="631ef-142">Instead, use the `--tool-path` option and the previous guidelines for global tools.</span></span>

## <a name="elevation-during-development"></a><span data-ttu-id="631ef-143">Geliştirme sırasında yükseltme</span><span class="sxs-lookup"><span data-stu-id="631ef-143">Elevation during development</span></span>

<span data-ttu-id="631ef-144">Geliştirme sırasında uygulamanızı test etmek için yükseltilmiş erişim gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="631ef-144">During development, you may need elevated access to test your application.</span></span> <span data-ttu-id="631ef-145">Bu örneğin IOT uygulamaları için yaygın senaryodur.</span><span class="sxs-lookup"><span data-stu-id="631ef-145">This scenario is common for IoT apps, for example.</span></span> <span data-ttu-id="631ef-146">Yükseltme olmadan uygulamayı derleyin ve ardından yükseltme ile çalıştırın öneririz.</span><span class="sxs-lookup"><span data-stu-id="631ef-146">We recommend that you build the application without elevation and then run it with elevation.</span></span> <span data-ttu-id="631ef-147">Aşağıdaki gibi birkaç desen vardır:</span><span class="sxs-lookup"><span data-stu-id="631ef-147">There are a few patterns, as follows:</span></span>

- <span data-ttu-id="631ef-148">Oluşturulan yürütülebilir dosya (en iyi başlangıç performansı sağlar) kullanarak:</span><span class="sxs-lookup"><span data-stu-id="631ef-148">Using generated executable (it provides the best startup performance):</span></span>

   ```bash
   dotnet build
   sudo ./bin/Debug/netcoreapp3.0/APPLICATIONNAME
   ```
    
- <span data-ttu-id="631ef-149">Kullanarak [çalıştırma dotnet](dotnet-run.md) komutunu `—no-build` yeni ikili dosyaları oluşturmamak üzere bayrağı:</span><span class="sxs-lookup"><span data-stu-id="631ef-149">Using the [dotnet run](dotnet-run.md) command with the `—no-build` flag to avoid generating new binaries:</span></span>

   ```bash
   dotnet build
   sudo dotnet run --no-build
   ```

## <a name="see-also"></a><span data-ttu-id="631ef-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="631ef-150">See also</span></span>

* [<span data-ttu-id="631ef-151">.NET core Araçları Genel genel bakış</span><span class="sxs-lookup"><span data-stu-id="631ef-151">.NET Core Global Tools overview</span></span>](global-tools.md)
