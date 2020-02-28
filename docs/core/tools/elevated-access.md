---
title: DotNet komutları için yükseltilmiş erişim
description: Yükseltilmiş erişim gerektiren DotNet komutları için en iyi uygulamaları öğrenin.
author: wli3
ms.date: 06/26/2019
ms.openlocfilehash: 4aff9badfa8ad9b83adc4496d4ebd6df29252e36
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156770"
---
# <a name="elevated-access-for-dotnet-commands"></a><span data-ttu-id="5b5c3-103">DotNet komutları için yükseltilmiş erişim</span><span class="sxs-lookup"><span data-stu-id="5b5c3-103">Elevated access for dotnet commands</span></span>

<span data-ttu-id="5b5c3-104">Yazılım geliştirme en iyi uygulamaları, geliştiricilerin en az ayrıcalık gerektiren yazılımları yazmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="5b5c3-104">Software development best practices guide developers to writing software that requires the least amount of privilege.</span></span> <span data-ttu-id="5b5c3-105">Ancak, performans izleme araçları gibi bazı yazılımlar, işletim sistemi kuralları nedeniyle yönetici izni gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5b5c3-105">However, some software, like performance monitoring tools, requires admin permission because of operating system rules.</span></span> <span data-ttu-id="5b5c3-106">Aşağıdaki kılavuzda .NET Core ile bu tür yazılımları yazmaya yönelik desteklenen senaryolar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5b5c3-106">The following guidance describes supported scenarios for writing such software with .NET Core.</span></span>

<span data-ttu-id="5b5c3-107">Aşağıdaki komutlar yükseltilmiş olarak çalıştırılabilir:</span><span class="sxs-lookup"><span data-stu-id="5b5c3-107">The following commands can be run elevated:</span></span>

- <span data-ttu-id="5b5c3-108">[DotNet aracı yüklemesi](dotnet-tool-install.md)gibi `dotnet tool` komutlar.</span><span class="sxs-lookup"><span data-stu-id="5b5c3-108">`dotnet tool` commands, such as [dotnet tool install](dotnet-tool-install.md).</span></span>
- `dotnet run --no-build`

<span data-ttu-id="5b5c3-109">Diğer komutların yükseltilme çalıştırılmasını önermiyoruz.</span><span class="sxs-lookup"><span data-stu-id="5b5c3-109">We don't recommend running other commands elevated.</span></span> <span data-ttu-id="5b5c3-110">Özellikle, [DotNet restore](dotnet-restore.md), [DotNet Build](dotnet-build.md)ve [DotNet Run](dotnet-run.md)gibi MSBuild kullanan komutlarla yükseltmeyi önermiyoruz.</span><span class="sxs-lookup"><span data-stu-id="5b5c3-110">In particular, we don't recommend elevation with commands that use MSBuild, such as [dotnet restore](dotnet-restore.md), [dotnet build](dotnet-build.md), and [dotnet run](dotnet-run.md).</span></span> <span data-ttu-id="5b5c3-111">Birincil sorun, bir Kullanıcı DotNet komutları verdikten sonra kök ve kısıtlanmış bir hesap arasında geri ve ileri geçiş yaptığında izin yönetimi sorunlardır.</span><span class="sxs-lookup"><span data-stu-id="5b5c3-111">The primary issue is permission management problems when a user transitions back and forth between root and a restricted account after issuing dotnet commands.</span></span> <span data-ttu-id="5b5c3-112">Bir kök kullanıcı tarafından oluşturulan dosyaya erişiminizin olmadığı kısıtlı bir kullanıcı olarak bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="5b5c3-112">You may find as a restricted user that you don't have access to the file built by a root user.</span></span> <span data-ttu-id="5b5c3-113">Bu durumu çözmek için bazı yollar vardır, ancak ilk yerde içine aktarılmaları gereksizdir.</span><span class="sxs-lookup"><span data-stu-id="5b5c3-113">There are ways to resolve this situation, but they're unnecessary to get into in the first place.</span></span>

<span data-ttu-id="5b5c3-114">Kök ve sınırlı hesap arasında geri geçiş yapmıyorsanız ve komutları kök olarak çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b5c3-114">You can run commands as root as long as you don’t transition back and forth between root and a restricted account.</span></span> <span data-ttu-id="5b5c3-115">Örneğin, Docker Kapsayıcıları varsayılan olarak kök olarak çalışır, bu nedenle bu özelliğe sahiptirler.</span><span class="sxs-lookup"><span data-stu-id="5b5c3-115">For example, Docker containers run as root by default, so they have this characteristic.</span></span>

## <a name="global-tool-installation"></a><span data-ttu-id="5b5c3-116">Küresel araç yüklemesi</span><span class="sxs-lookup"><span data-stu-id="5b5c3-116">Global tool installation</span></span>

<span data-ttu-id="5b5c3-117">Aşağıdaki yönergelerde, yürütme için yükseltilmiş izinler gerektiren .NET Core araçlarını yüklemek, çalıştırmak ve kaldırmak için önerilen yol gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5b5c3-117">The following instructions demonstrate the recommended way to install, run, and uninstall .NET Core tools that require elevated permissions to execute.</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[<span data-ttu-id="5b5c3-118">Windows</span><span class="sxs-lookup"><span data-stu-id="5b5c3-118">Windows</span></span>](#tab/windows)

### <a name="install-the-tool"></a><span data-ttu-id="5b5c3-119">Aracı 'nı yükler</span><span class="sxs-lookup"><span data-stu-id="5b5c3-119">Install the tool</span></span>

<span data-ttu-id="5b5c3-120">`%ProgramFiles%\dotnet-tools` klasör zaten mevcutsa, "kullanıcılar" grubunun bu dizini yazma veya değiştirme izni olup olmadığını denetlemek için aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="5b5c3-120">If the folder `%ProgramFiles%\dotnet-tools` already exists, do the following to check whether the "Users" group has permission to write or modify that directory:</span></span>

- <span data-ttu-id="5b5c3-121">`%ProgramFiles%\dotnet-tools` klasörüne sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="5b5c3-121">Right-click the `%ProgramFiles%\dotnet-tools` folder and select **Properties**.</span></span> <span data-ttu-id="5b5c3-122">**Ortak özellikler** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="5b5c3-122">The **Common Properties** dialog box opens.</span></span>
- <span data-ttu-id="5b5c3-123">**Güvenlik** sekmesini seçin. **Grup veya Kullanıcı adları**altında "kullanıcılar" grubunun dizini yazma veya değiştirme izni olup olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="5b5c3-123">Select the **Security** tab. Under **Group or user names**, check whether the “Users” group has permission to write or modify the directory.</span></span>
- <span data-ttu-id="5b5c3-124">"Kullanıcılar" grubu dizini yazabilir veya değiştirebiliyorsanız, *DotNet araçları*yerine araçları yüklerken farklı bir dizin adı kullanın.</span><span class="sxs-lookup"><span data-stu-id="5b5c3-124">If the "Users" group can write or modify the directory, use a different directory name when installing the tools rather than *dotnet-tools*.</span></span>

<span data-ttu-id="5b5c3-125">Araçları yüklemek için, yükseltilmiş komut isteminde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5b5c3-125">To install tools, run the following command in elevated prompt.</span></span> <span data-ttu-id="5b5c3-126">Yükleme sırasında *DotNet araçları* klasörünü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5b5c3-126">It will create the *dotnet-tools* folder during the installation.</span></span>

```dotnetcli
dotnet tool install PACKAGEID --tool-path "%ProgramFiles%\dotnet-tools".
```

### <a name="run-the-global-tool"></a><span data-ttu-id="5b5c3-127">Genel aracı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="5b5c3-127">Run the global tool</span></span>

<span data-ttu-id="5b5c3-128">**Seçenek 1** Tam yolu yükseltilmiş istemle kullanın:</span><span class="sxs-lookup"><span data-stu-id="5b5c3-128">**Option 1** Use the full path with elevated prompt:</span></span>

```cmd
"%ProgramFiles%\dotnet-tools\TOOLCOMMAND"
```

<span data-ttu-id="5b5c3-129">**Seçenek 2** Yeni oluşturulan klasörü `%Path%`ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5b5c3-129">**Option 2** Add the newly created folder to `%Path%`.</span></span> <span data-ttu-id="5b5c3-130">Bu işlemi yalnızca bir kez yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5b5c3-130">You only need to do this operation once.</span></span>

```cmd
setx Path "%Path%;%ProgramFiles%\dotnet-tools\"
```

<span data-ttu-id="5b5c3-131">Ve şunu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="5b5c3-131">And run with:</span></span>

```cmd
TOOLCOMMAND
```

### <a name="uninstall-the-global-tool"></a><span data-ttu-id="5b5c3-132">Genel aracı kaldır</span><span class="sxs-lookup"><span data-stu-id="5b5c3-132">Uninstall the global tool</span></span>

<span data-ttu-id="5b5c3-133">Yükseltilmiş bir komut isteminde aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="5b5c3-133">In an elevated prompt, type the following command:</span></span>

```dotnetcli
dotnet tool uninstall PACKAGEID --tool-path "%ProgramFiles%\dotnet-tools"
```

# <a name="linux"></a>[<span data-ttu-id="5b5c3-134">Linux</span><span class="sxs-lookup"><span data-stu-id="5b5c3-134">Linux</span></span>](#tab/linux)

[!INCLUDE [elevated-access-unix](../../../includes/elevated-access-unix.md)]

# <a name="macos"></a>[<span data-ttu-id="5b5c3-135">macOS</span><span class="sxs-lookup"><span data-stu-id="5b5c3-135">macOS</span></span>](#tab/macos)

[!INCLUDE [elevated-access-unix](../../../includes/elevated-access-unix.md)]

---

## <a name="local-tools"></a><span data-ttu-id="5b5c3-136">Yerel Araçlar</span><span class="sxs-lookup"><span data-stu-id="5b5c3-136">Local tools</span></span>

<span data-ttu-id="5b5c3-137">Yerel araçlar, Kullanıcı başına alt dizin ağacı başına kapsamlandırılır.</span><span class="sxs-lookup"><span data-stu-id="5b5c3-137">Local tools are scoped per subdirectory tree, per user.</span></span> <span data-ttu-id="5b5c3-138">Yükseltilmiş olarak çalıştırıldığında yerel araçlar, kısıtlı bir Kullanıcı ortamını yükseltilmiş ortamda paylaşır.</span><span class="sxs-lookup"><span data-stu-id="5b5c3-138">When run elevated, local tools share a restricted user environment to the elevated environment.</span></span> <span data-ttu-id="5b5c3-139">Linux ve macOS 'ta bu, dosyaların yalnızca kök kullanıcı erişimiyle ayarlanmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="5b5c3-139">In Linux and macOS, this results in files being set with root user-only access.</span></span> <span data-ttu-id="5b5c3-140">Kullanıcı kısıtlı bir hesaba geri geçtiğinde, Kullanıcı artık dosyalara erişemez veya dosyalara yazamaz.</span><span class="sxs-lookup"><span data-stu-id="5b5c3-140">If the user switches back to a restricted account, the user can no longer access or write to the files.</span></span> <span data-ttu-id="5b5c3-141">Bu nedenle, yerel araçlar olarak yükseltme gerektiren araçların yüklenmesi önerilmez.</span><span class="sxs-lookup"><span data-stu-id="5b5c3-141">So installing tools that require elevation as local tools isn't recommended.</span></span> <span data-ttu-id="5b5c3-142">Bunun yerine, genel araçlar için `--tool-path` seçeneğini ve önceki yönergeleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="5b5c3-142">Instead, use the `--tool-path` option and the previous guidelines for global tools.</span></span>

## <a name="elevation-during-development"></a><span data-ttu-id="5b5c3-143">Geliştirme sırasında yükseltme</span><span class="sxs-lookup"><span data-stu-id="5b5c3-143">Elevation during development</span></span>

<span data-ttu-id="5b5c3-144">Geliştirme sırasında uygulamanızı test etmek için yükseltilmiş erişime sahip olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b5c3-144">During development, you may need elevated access to test your application.</span></span> <span data-ttu-id="5b5c3-145">Bu senaryo, IoT uygulamaları için yaygın olarak kullanılan bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="5b5c3-145">This scenario is common for IoT apps, for example.</span></span> <span data-ttu-id="5b5c3-146">Uygulamayı yükseltme olmadan oluşturmanızı ve ardından yükseltme ile çalıştırmayı öneririz.</span><span class="sxs-lookup"><span data-stu-id="5b5c3-146">We recommend that you build the application without elevation and then run it with elevation.</span></span> <span data-ttu-id="5b5c3-147">Aşağıda gösterildiği gibi birkaç desen vardır:</span><span class="sxs-lookup"><span data-stu-id="5b5c3-147">There are a few patterns, as follows:</span></span>

- <span data-ttu-id="5b5c3-148">Oluşturulan yürütülebiliri kullanma (en iyi başlangıç performansını sağlar):</span><span class="sxs-lookup"><span data-stu-id="5b5c3-148">Using generated executable (it provides the best startup performance):</span></span>

   ```dotnetcli
   dotnet build
   sudo ./bin/Debug/netcoreapp3.0/APPLICATIONNAME
   ```

- <span data-ttu-id="5b5c3-149">Yeni ikili dosyaları üretmemek için `—no-build` bayrağıyla [DotNet Run](dotnet-run.md) komutunu kullanma:</span><span class="sxs-lookup"><span data-stu-id="5b5c3-149">Using the [dotnet run](dotnet-run.md) command with the `—no-build` flag to avoid generating new binaries:</span></span>

   ```dotnetcli
   dotnet build
   sudo dotnet run --no-build
   ```

## <a name="see-also"></a><span data-ttu-id="5b5c3-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5b5c3-150">See also</span></span>

- [<span data-ttu-id="5b5c3-151">.NET Core genel araçlarına genel bakış</span><span class="sxs-lookup"><span data-stu-id="5b5c3-151">.NET Core Global Tools overview</span></span>](global-tools.md)
