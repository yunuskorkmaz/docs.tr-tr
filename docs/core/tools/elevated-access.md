---
title: dotnet komutları için yüksek erişim
description: Yüksek erişim gerektiren dotnet komutları için en iyi uygulamaları öğrenin.
author: wli3
ms.date: 06/26/2019
ms.openlocfilehash: f99e0b257772e0a73d4945f1129997d1d3308ed2
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805796"
---
# <a name="elevated-access-for-dotnet-commands"></a><span data-ttu-id="67218-103">dotnet komutları için yüksek erişim</span><span class="sxs-lookup"><span data-stu-id="67218-103">Elevated access for dotnet commands</span></span>

<span data-ttu-id="67218-104">Yazılım geliştirme en iyi uygulamaları ayrıcalık en az miktarda gerektiren yazılım yazma geliştiricileri rehberlik eder.</span><span class="sxs-lookup"><span data-stu-id="67218-104">Software development best practices guide developers to writing software that requires the least amount of privilege.</span></span> <span data-ttu-id="67218-105">Ancak, performans izleme araçları gibi bazı yazılımlar, işletim sistemi kuralları nedeniyle yönetici izni gerektirir.</span><span class="sxs-lookup"><span data-stu-id="67218-105">However, some software, like performance monitoring tools, requires admin permission because of operating system rules.</span></span> <span data-ttu-id="67218-106">Aşağıdaki kılavuzda, bu tür yazılımları .NET Core ile yazmak için desteklenen senaryolar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="67218-106">The following guidance describes supported scenarios for writing such software with .NET Core.</span></span>

<span data-ttu-id="67218-107">Aşağıdaki komutlar yükseltilebilir:</span><span class="sxs-lookup"><span data-stu-id="67218-107">The following commands can be run elevated:</span></span>

- <span data-ttu-id="67218-108">`dotnet tool`[komutları, dotnet aracı yükleme](dotnet-tool-install.md)gibi .</span><span class="sxs-lookup"><span data-stu-id="67218-108">`dotnet tool` commands, such as [dotnet tool install](dotnet-tool-install.md).</span></span>
- `dotnet run --no-build`
- `dotnet-core-uninstall`

<span data-ttu-id="67218-109">Diğer komutları yükseltmenizi önermiyoruz.</span><span class="sxs-lookup"><span data-stu-id="67218-109">We don't recommend running other commands elevated.</span></span> <span data-ttu-id="67218-110">Özellikle, [biz dotnet geri yükleme, dotnet](dotnet-restore.md) [yapı](dotnet-build.md)ve [dotnet çalıştırmak](dotnet-run.md)gibi MSBuild kullanan komutları ile yükseklik önermiyoruz.</span><span class="sxs-lookup"><span data-stu-id="67218-110">In particular, we don't recommend elevation with commands that use MSBuild, such as [dotnet restore](dotnet-restore.md), [dotnet build](dotnet-build.md), and [dotnet run](dotnet-run.md).</span></span> <span data-ttu-id="67218-111">Birincil sorun, bir kullanıcı dotnet komutları verdikten sonra kök ve kısıtlı bir hesap arasında ileri ve geri geçiş yaptığında izin yönetimi sorunlarıdır.</span><span class="sxs-lookup"><span data-stu-id="67218-111">The primary issue is permission management problems when a user transitions back and forth between root and a restricted account after issuing dotnet commands.</span></span> <span data-ttu-id="67218-112">Kısıtlanmış bir kullanıcı olarak, bir kök kullanıcı tarafından oluşturulmuş dosyaya erişiminiz olmadığını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="67218-112">You may find as a restricted user that you don't have access to the file built by a root user.</span></span> <span data-ttu-id="67218-113">Bu durumu çözmenin yolları var, ama en başta içine girmek için gereksiz.</span><span class="sxs-lookup"><span data-stu-id="67218-113">There are ways to resolve this situation, but they're unnecessary to get into in the first place.</span></span>

<span data-ttu-id="67218-114">Kök ve kısıtlı bir hesap arasında geçiş yapmadığınız sürece komutları kök olarak çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="67218-114">You can run commands as root as long as you don’t transition back and forth between root and a restricted account.</span></span> <span data-ttu-id="67218-115">Örneğin, Docker kapsayıcıları varsayılan olarak kök olarak çalıştırın, bu nedenle bu özelliğe sahiptirler.</span><span class="sxs-lookup"><span data-stu-id="67218-115">For example, Docker containers run as root by default, so they have this characteristic.</span></span>

## <a name="global-tool-installation"></a><span data-ttu-id="67218-116">Genel takım kurulumu</span><span class="sxs-lookup"><span data-stu-id="67218-116">Global tool installation</span></span>

<span data-ttu-id="67218-117">Aşağıdaki yönergeler, yürütmek için yüksek izinler gerektiren .NET Core araçlarını yükleme, çalıştırma ve kaldırmanın önerilen yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="67218-117">The following instructions demonstrate the recommended way to install, run, and uninstall .NET Core tools that require elevated permissions to execute.</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[<span data-ttu-id="67218-118">Windows</span><span class="sxs-lookup"><span data-stu-id="67218-118">Windows</span></span>](#tab/windows)

### <a name="install-the-tool"></a><span data-ttu-id="67218-119">Aracı yükleme</span><span class="sxs-lookup"><span data-stu-id="67218-119">Install the tool</span></span>

<span data-ttu-id="67218-120">Klasör `%ProgramFiles%\dotnet-tools` zaten varsa, "Kullanıcılar" grubunun bu dizini yazma veya değiştirme izni olup olmadığını denetlemek için aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="67218-120">If the folder `%ProgramFiles%\dotnet-tools` already exists, do the following to check whether the "Users" group has permission to write or modify that directory:</span></span>

- <span data-ttu-id="67218-121">Klasöre `%ProgramFiles%\dotnet-tools` sağ tıklayın ve **Özellikler'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="67218-121">Right-click the `%ProgramFiles%\dotnet-tools` folder and select **Properties**.</span></span> <span data-ttu-id="67218-122">**Ortak Özellikler** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="67218-122">The **Common Properties** dialog box opens.</span></span>
- <span data-ttu-id="67218-123">**Güvenlik** sekmesini seçin. **Grup veya kullanıcı adları**altında, "Kullanıcılar" grubunun dizini yazma veya değiştirme izni olup olmadığını kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="67218-123">Select the **Security** tab. Under **Group or user names**, check whether the “Users” group has permission to write or modify the directory.</span></span>
- <span data-ttu-id="67218-124">"Kullanıcılar" grubu dizini yazabilir veya değiştirebiliyorsa, *araçları dotnet araçları*yerine yüklerken farklı bir dizin adı kullanın.</span><span class="sxs-lookup"><span data-stu-id="67218-124">If the "Users" group can write or modify the directory, use a different directory name when installing the tools rather than *dotnet-tools*.</span></span>

<span data-ttu-id="67218-125">Araçları yüklemek için aşağıdaki komutu yükseltilmiş komut isteminde çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="67218-125">To install tools, run the following command in elevated prompt.</span></span> <span data-ttu-id="67218-126">Yükleme sırasında *dotnet-tools* klasörünü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="67218-126">It will create the *dotnet-tools* folder during the installation.</span></span>

```dotnetcli
dotnet tool install PACKAGEID --tool-path "%ProgramFiles%\dotnet-tools".
```

### <a name="run-the-global-tool"></a><span data-ttu-id="67218-127">Genel aracı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="67218-127">Run the global tool</span></span>

<span data-ttu-id="67218-128">**Seçenek 1** Yükseltilmiş komut istemi ile tam yolu kullanın:</span><span class="sxs-lookup"><span data-stu-id="67218-128">**Option 1** Use the full path with elevated prompt:</span></span>

```cmd
"%ProgramFiles%\dotnet-tools\TOOLCOMMAND"
```

<span data-ttu-id="67218-129">**Seçenek 2** Yeni oluşturulan klasörü `%Path%`.</span><span class="sxs-lookup"><span data-stu-id="67218-129">**Option 2** Add the newly created folder to `%Path%`.</span></span> <span data-ttu-id="67218-130">Bu işlemi sadece bir kez yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="67218-130">You only need to do this operation once.</span></span>

```cmd
setx Path "%Path%;%ProgramFiles%\dotnet-tools\"
```

<span data-ttu-id="67218-131">Ve ile çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="67218-131">And run with:</span></span>

```cmd
TOOLCOMMAND
```

### <a name="uninstall-the-global-tool"></a><span data-ttu-id="67218-132">Genel aracı kaldırma</span><span class="sxs-lookup"><span data-stu-id="67218-132">Uninstall the global tool</span></span>

<span data-ttu-id="67218-133">Yükseltilmiş bir istemi olarak, aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="67218-133">In an elevated prompt, type the following command:</span></span>

```dotnetcli
dotnet tool uninstall PACKAGEID --tool-path "%ProgramFiles%\dotnet-tools"
```

# <a name="linux"></a>[<span data-ttu-id="67218-134">Linux</span><span class="sxs-lookup"><span data-stu-id="67218-134">Linux</span></span>](#tab/linux)

[!INCLUDE [elevated-access-unix](../../../includes/elevated-access-unix.md)]

# <a name="macos"></a>[<span data-ttu-id="67218-135">macOS</span><span class="sxs-lookup"><span data-stu-id="67218-135">macOS</span></span>](#tab/macos)

[!INCLUDE [elevated-access-unix](../../../includes/elevated-access-unix.md)]

---

## <a name="local-tools"></a><span data-ttu-id="67218-136">Yerel araçlar</span><span class="sxs-lookup"><span data-stu-id="67218-136">Local tools</span></span>

<span data-ttu-id="67218-137">Yerel araçlar, kullanıcı başına alt dizin ağacı başına kapsamlıdır.</span><span class="sxs-lookup"><span data-stu-id="67218-137">Local tools are scoped per subdirectory tree, per user.</span></span> <span data-ttu-id="67218-138">Yüksek çalıştırıldığında, yerel araçlar kısıtlı bir kullanıcı ortamını yükseltilmiş ortamla paylaşır.</span><span class="sxs-lookup"><span data-stu-id="67218-138">When run elevated, local tools share a restricted user environment to the elevated environment.</span></span> <span data-ttu-id="67218-139">Linux ve macOS'ta bu, yalnızca root kullanıcı erişimine sahip dosyaların ayarlandığına neden olur.</span><span class="sxs-lookup"><span data-stu-id="67218-139">In Linux and macOS, this results in files being set with root user-only access.</span></span> <span data-ttu-id="67218-140">Kullanıcı kısıtlı bir hesaba geri dönerse, kullanıcı artık dosyalara erişemez veya dosyalara yazamaz.</span><span class="sxs-lookup"><span data-stu-id="67218-140">If the user switches back to a restricted account, the user can no longer access or write to the files.</span></span> <span data-ttu-id="67218-141">Bu nedenle, yerel araçlar olarak yükseklik gerektiren araçların yüklenmesi önerilmez.</span><span class="sxs-lookup"><span data-stu-id="67218-141">So installing tools that require elevation as local tools isn't recommended.</span></span> <span data-ttu-id="67218-142">Bunun yerine, `--tool-path` genel araçlar için seçeneği ve önceki yönergeleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="67218-142">Instead, use the `--tool-path` option and the previous guidelines for global tools.</span></span>

## <a name="elevation-during-development"></a><span data-ttu-id="67218-143">Geliştirme sırasında yükseklik</span><span class="sxs-lookup"><span data-stu-id="67218-143">Elevation during development</span></span>

<span data-ttu-id="67218-144">Geliştirme sırasında, uygulamanızı test etmek için yüksek erişim gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="67218-144">During development, you may need elevated access to test your application.</span></span> <span data-ttu-id="67218-145">Bu senaryo, örneğin IoT uygulamaları için yaygındır.</span><span class="sxs-lookup"><span data-stu-id="67218-145">This scenario is common for IoT apps, for example.</span></span> <span data-ttu-id="67218-146">Uygulamayı yükseklik olmadan oluşturmanızı ve yükseklik ile çalıştırmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="67218-146">We recommend that you build the application without elevation and then run it with elevation.</span></span> <span data-ttu-id="67218-147">Aşağıdaki gibi birkaç desen vardır:</span><span class="sxs-lookup"><span data-stu-id="67218-147">There are a few patterns, as follows:</span></span>

- <span data-ttu-id="67218-148">Oluşturulan çalıştırılabilir (en iyi başlangıç performansını sağlar) kullanarak:</span><span class="sxs-lookup"><span data-stu-id="67218-148">Using generated executable (it provides the best startup performance):</span></span>

   ```dotnetcli
   dotnet build
   sudo ./bin/Debug/netcoreapp3.0/APPLICATIONNAME
   ```

- <span data-ttu-id="67218-149">Yeni ikililer oluşturmamak için `—no-build` [bayrakla dotnet çalıştırma](dotnet-run.md) komutunu kullanma:</span><span class="sxs-lookup"><span data-stu-id="67218-149">Using the [dotnet run](dotnet-run.md) command with the `—no-build` flag to avoid generating new binaries:</span></span>

   ```dotnetcli
   dotnet build
   sudo dotnet run --no-build
   ```

## <a name="see-also"></a><span data-ttu-id="67218-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="67218-150">See also</span></span>

- [<span data-ttu-id="67218-151">.NET Core Global Tools genel bakış</span><span class="sxs-lookup"><span data-stu-id="67218-151">.NET Core Global Tools overview</span></span>](global-tools.md)
