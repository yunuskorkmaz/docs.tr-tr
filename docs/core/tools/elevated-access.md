---
title: DotNet komutları için yükseltilmiş erişim
description: Yükseltilmiş erişim gerektiren DotNet komutları için en iyi uygulamaları öğrenin.
author: wli3
ms.date: 06/26/2019
ms.openlocfilehash: b6de87f375a584da25e160d79f51f1bc48f3c302
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70969858"
---
# <a name="elevated-access-for-dotnet-commands"></a><span data-ttu-id="538d5-103">DotNet komutları için yükseltilmiş erişim</span><span class="sxs-lookup"><span data-stu-id="538d5-103">Elevated access for dotnet commands</span></span>

<span data-ttu-id="538d5-104">Yazılım geliştirme en iyi uygulamaları, geliştiricilerin en az ayrıcalık gerektiren yazılımları yazmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="538d5-104">Software development best practices guide developers to writing software that requires the least amount of privilege.</span></span> <span data-ttu-id="538d5-105">Ancak, performans izleme araçları gibi bazı yazılımlar, işletim sistemi kuralları nedeniyle yönetici izni gerektirir.</span><span class="sxs-lookup"><span data-stu-id="538d5-105">However, some software, like performance monitoring tools, requires admin permission because of operating system rules.</span></span> <span data-ttu-id="538d5-106">Aşağıdaki kılavuzda .NET Core ile bu tür yazılımları yazmaya yönelik desteklenen senaryolar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="538d5-106">The following guidance describes supported scenarios for writing such software with .NET Core.</span></span> 

<span data-ttu-id="538d5-107">Aşağıdaki komutlar yükseltilmiş olarak çalıştırılabilir:</span><span class="sxs-lookup"><span data-stu-id="538d5-107">The following commands can be run elevated:</span></span>

- <span data-ttu-id="538d5-108">`dotnet tool`[DotNet aracı yüklemesi](dotnet-tool-install.md)gibi komutlar.</span><span class="sxs-lookup"><span data-stu-id="538d5-108">`dotnet tool` commands, such as [dotnet tool install](dotnet-tool-install.md).</span></span>
- `dotnet run --no-build`

<span data-ttu-id="538d5-109">Diğer komutların yükseltilme çalıştırılmasını önermiyoruz.</span><span class="sxs-lookup"><span data-stu-id="538d5-109">We don't recommend running other commands elevated.</span></span> <span data-ttu-id="538d5-110">Özellikle, [DotNet restore](dotnet-restore.md), [DotNet Build](dotnet-build.md)ve [DotNet Run](dotnet-run.md)gibi MSBuild kullanan komutlarla yükseltmeyi önermiyoruz.</span><span class="sxs-lookup"><span data-stu-id="538d5-110">In particular, we don't recommend elevation with commands that use MSBuild, such as [dotnet restore](dotnet-restore.md), [dotnet build](dotnet-build.md), and [dotnet run](dotnet-run.md).</span></span> <span data-ttu-id="538d5-111">Birincil sorun, bir Kullanıcı DotNet komutları verdikten sonra kök ve kısıtlanmış bir hesap arasında geri ve ileri geçiş yaptığında izin yönetimi sorunlardır.</span><span class="sxs-lookup"><span data-stu-id="538d5-111">The primary issue is permission management problems when a user transitions back and forth between root and a restricted account after issuing dotnet commands.</span></span> <span data-ttu-id="538d5-112">Bir kök kullanıcı tarafından oluşturulan dosyaya erişiminizin olmadığı kısıtlı bir kullanıcı olarak bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="538d5-112">You may find as a restricted user that you don't have access to the file built by a root user.</span></span> <span data-ttu-id="538d5-113">Bu durumu çözmek için bazı yollar vardır, ancak ilk yerde içine aktarılmaları gereksizdir.</span><span class="sxs-lookup"><span data-stu-id="538d5-113">There are ways to resolve this situation, but they're unnecessary to get into in the first place.</span></span>

<span data-ttu-id="538d5-114">Kök ve sınırlı hesap arasında geri geçiş yapmıyorsanız ve komutları kök olarak çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="538d5-114">You can run commands as root as long as you don’t transition back and forth between root and a restricted account.</span></span> <span data-ttu-id="538d5-115">Örneğin, Docker Kapsayıcıları varsayılan olarak kök olarak çalışır, bu nedenle bu özelliğe sahiptirler.</span><span class="sxs-lookup"><span data-stu-id="538d5-115">For example, Docker containers run as root by default, so they have this characteristic.</span></span>

## <a name="global-tool-installation"></a><span data-ttu-id="538d5-116">Küresel araç yüklemesi</span><span class="sxs-lookup"><span data-stu-id="538d5-116">Global tool installation</span></span>

<span data-ttu-id="538d5-117">Aşağıdaki yönergelerde, yürütme için yükseltilmiş izinler gerektiren .NET Core araçlarını yüklemek, çalıştırmak ve kaldırmak için önerilen yol gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="538d5-117">The following instructions demonstrate the recommended way to install, run, and uninstall .NET Core tools that require elevated permissions to execute.</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windowstabwindows"></a>[<span data-ttu-id="538d5-118">Windows</span><span class="sxs-lookup"><span data-stu-id="538d5-118">Windows</span></span>](#tab/windows)

### <a name="install-the-global-tool"></a><span data-ttu-id="538d5-119">Genel aracı 'nı yükler</span><span class="sxs-lookup"><span data-stu-id="538d5-119">Install the global tool</span></span>

<span data-ttu-id="538d5-120">Klasör `%ProgramFiles%\dotnet-tools` zaten mevcutsa, "kullanıcılar" grubunun bu dizini yazma veya değiştirme izni olup olmadığını denetlemek için aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="538d5-120">If the folder `%ProgramFiles%\dotnet-tools` already exists, do the following to check whether the "Users" group has permission to write or modify that directory:</span></span>

- <span data-ttu-id="538d5-121">`%ProgramFiles%\dotnet-tools` Klasöre sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="538d5-121">Right-click the `%ProgramFiles%\dotnet-tools` folder and select **Properties**.</span></span> <span data-ttu-id="538d5-122">**Ortak özellikler** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="538d5-122">The **Common Properties** dialog box opens.</span></span> 
- <span data-ttu-id="538d5-123">**Güvenlik** sekmesini seçin. **Grup veya Kullanıcı adları**altında "kullanıcılar" grubunun dizini yazma veya değiştirme izni olup olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="538d5-123">Select the **Security** tab. Under **Group or user names**, check whether the “Users” group has permission to write or modify the directory.</span></span> 
- <span data-ttu-id="538d5-124">"Kullanıcılar" grubu dizini yazabilir veya değiştirebiliyorsanız, *DotNet araçları*yerine araçları yüklerken farklı bir dizin adı kullanın.</span><span class="sxs-lookup"><span data-stu-id="538d5-124">If the "Users" group can write or modify the directory, use a different directory name when installing the tools rather than *dotnet-tools*.</span></span>

<span data-ttu-id="538d5-125">Araçları yüklemek için, yükseltilmiş komut isteminde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="538d5-125">To install tools, run the following command in elevated prompt.</span></span> <span data-ttu-id="538d5-126">Yükleme sırasında *DotNet araçları* klasörünü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="538d5-126">It will create the *dotnet-tools* folder during the installation.</span></span>

```cmd
dotnet tool install PACKAGEID --tool-path "%ProgramFiles%\dotnet-tools".
```

### <a name="run-the-global-tool"></a><span data-ttu-id="538d5-127">Genel aracı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="538d5-127">Run the global tool</span></span>

<span data-ttu-id="538d5-128">**Seçenek 1** Tam yolu yükseltilmiş istemle kullanın:</span><span class="sxs-lookup"><span data-stu-id="538d5-128">**Option 1** Use the full path with elevated prompt:</span></span>

```cmd
"%ProgramFiles%\dotnet-tools\TOOLCOMMAND"
```

<span data-ttu-id="538d5-129">**Seçenek 2** Yeni oluşturulan klasörü öğesine `%Path%`ekleyin.</span><span class="sxs-lookup"><span data-stu-id="538d5-129">**Option 2** Add the newly created folder to `%Path%`.</span></span> <span data-ttu-id="538d5-130">Bu işlemi yalnızca bir kez yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="538d5-130">You only need to do this operation once.</span></span>

```cmd
setx Path "%Path%;%ProgramFiles%\dotnet-tools\"
```

<span data-ttu-id="538d5-131">Ve şunu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="538d5-131">And run with:</span></span>

```cmd
TOOLCOMMAND
```

### <a name="uninstall-the-global-tool"></a><span data-ttu-id="538d5-132">Genel aracı kaldır</span><span class="sxs-lookup"><span data-stu-id="538d5-132">Uninstall the global tool</span></span>

<span data-ttu-id="538d5-133">Yükseltilmiş bir komut isteminde aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="538d5-133">In an elevated prompt, type the following command:</span></span>

```cmd
dotnet tool uninstall PACKAGEID --tool-path "%ProgramFiles%\dotnet-tools"
```

# <a name="linuxtablinux"></a>[<span data-ttu-id="538d5-134">Linux</span><span class="sxs-lookup"><span data-stu-id="538d5-134">Linux</span></span>](#tab/linux)

[!INCLUDE [elevated-access-unix](../../../includes/elevated-access-unix.md)]

# <a name="macostabmacos"></a>[<span data-ttu-id="538d5-135">macOS</span><span class="sxs-lookup"><span data-stu-id="538d5-135">macOS</span></span>](#tab/macos)

[!INCLUDE [elevated-access-unix](../../../includes/elevated-access-unix.md)]

---

## <a name="local-tools"></a><span data-ttu-id="538d5-136">Yerel Araçlar</span><span class="sxs-lookup"><span data-stu-id="538d5-136">Local tools</span></span>

<span data-ttu-id="538d5-137">Yerel araçlar, Kullanıcı başına alt dizin ağacı başına kapsamlandırılır.</span><span class="sxs-lookup"><span data-stu-id="538d5-137">Local tools are scoped per subdirectory tree, per user.</span></span> <span data-ttu-id="538d5-138">Yükseltilmiş olarak çalıştırıldığında yerel araçlar, kısıtlı bir Kullanıcı ortamını yükseltilmiş ortamda paylaşır.</span><span class="sxs-lookup"><span data-stu-id="538d5-138">When run elevated, local tools share a restricted user environment to the elevated environment.</span></span> <span data-ttu-id="538d5-139">Linux ve macOS 'ta bu, dosyaların yalnızca kök kullanıcı erişimiyle ayarlanmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="538d5-139">In Linux and macOS, this results in files being set with root user-only access.</span></span> <span data-ttu-id="538d5-140">Kullanıcı kısıtlı bir hesaba geri geçtiğinde, Kullanıcı artık dosyalara erişemez veya dosyalara yazamaz.</span><span class="sxs-lookup"><span data-stu-id="538d5-140">If the user switches back to a restricted account, the user can no longer access or write to the files.</span></span> <span data-ttu-id="538d5-141">Bu nedenle, yerel araçlar olarak yükseltme gerektiren araçların yüklenmesi önerilmez.</span><span class="sxs-lookup"><span data-stu-id="538d5-141">So installing tools that require elevation as local tools isn't recommended.</span></span> <span data-ttu-id="538d5-142">Bunun yerine, genel `--tool-path` araçlar için seçeneğini ve önceki yönergeleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="538d5-142">Instead, use the `--tool-path` option and the previous guidelines for global tools.</span></span>

## <a name="elevation-during-development"></a><span data-ttu-id="538d5-143">Geliştirme sırasında yükseltme</span><span class="sxs-lookup"><span data-stu-id="538d5-143">Elevation during development</span></span>

<span data-ttu-id="538d5-144">Geliştirme sırasında uygulamanızı test etmek için yükseltilmiş erişime sahip olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="538d5-144">During development, you may need elevated access to test your application.</span></span> <span data-ttu-id="538d5-145">Bu senaryo, IoT uygulamaları için yaygın olarak kullanılan bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="538d5-145">This scenario is common for IoT apps, for example.</span></span> <span data-ttu-id="538d5-146">Uygulamayı yükseltme olmadan oluşturmanızı ve ardından yükseltme ile çalıştırmayı öneririz.</span><span class="sxs-lookup"><span data-stu-id="538d5-146">We recommend that you build the application without elevation and then run it with elevation.</span></span> <span data-ttu-id="538d5-147">Aşağıda gösterildiği gibi birkaç desen vardır:</span><span class="sxs-lookup"><span data-stu-id="538d5-147">There are a few patterns, as follows:</span></span>

- <span data-ttu-id="538d5-148">Oluşturulan yürütülebiliri kullanma (en iyi başlangıç performansını sağlar):</span><span class="sxs-lookup"><span data-stu-id="538d5-148">Using generated executable (it provides the best startup performance):</span></span>

   ```bash
   dotnet build
   sudo ./bin/Debug/netcoreapp3.0/APPLICATIONNAME
   ```
    
- <span data-ttu-id="538d5-149">Yeni ikililer oluşturmaktan kaçınmak için, `—no-build` [DotNet Run](dotnet-run.md) komutunu bayrağıyla birlikte kullanma:</span><span class="sxs-lookup"><span data-stu-id="538d5-149">Using the [dotnet run](dotnet-run.md) command with the `—no-build` flag to avoid generating new binaries:</span></span>

   ```bash
   dotnet build
   sudo dotnet run --no-build
   ```

## <a name="see-also"></a><span data-ttu-id="538d5-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="538d5-150">See also</span></span>

- [<span data-ttu-id="538d5-151">.NET Core genel araçlarına genel bakış</span><span class="sxs-lookup"><span data-stu-id="538d5-151">.NET Core Global Tools overview</span></span>](global-tools.md)
