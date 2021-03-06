---
title: Raspberry PI üzerinde .NET uygulamalarında hata ayıklama
description: Raspberry PI ve benzer cihazlarda .NET uygulamalarında hata ayıklamayı öğrenin.
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: how-to
ms.prod: dotnet
zone_pivot_groups: ide-set-one
ms.openlocfilehash: 58858384c49a296e0b33d663f3ef930caf9cace6
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102258071"
---
# <a name="debug-net-apps-on-raspberry-pi"></a><span data-ttu-id="ee95b-103">Raspberry PI üzerinde .NET uygulamalarında hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="ee95b-103">Debug .NET apps on Raspberry Pi</span></span>

<span data-ttu-id="ee95b-104">Raspberry PI gibi ARM tabanlı IoT cihazlarında çalışan .NET uygulamalarında hata ayıklama, benzersiz bir zorluk gösterir.</span><span class="sxs-lookup"><span data-stu-id="ee95b-104">Debugging .NET apps running on ARM-based IoT devices like Raspberry Pi presents a unique challenge.</span></span> <span data-ttu-id="ee95b-105">ARM cihazlarda .NET uygulamaları geliştirmek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="ee95b-105">It is possible to develop .NET apps on ARM devices.</span></span> <span data-ttu-id="ee95b-106">Ancak, Visual Studio dışında .NET uygulamalarında hata ayıklamak için gereken OmniSharp ARM cihazlarıyla uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="ee95b-106">However, OmniSharp, which is required for debugging .NET apps outside of Visual Studio, is not compatible with ARM devices.</span></span> <span data-ttu-id="ee95b-107">Sonuç olarak, uygulamaların uyumlu bir platformdan uzaktan ayıklanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ee95b-107">As a result, apps must be debugged remotely from a compatible platform.</span></span>

::: zone pivot="vscode"

## <a name="debug-from-visual-studio-code-cross-platform"></a><span data-ttu-id="ee95b-108">Visual Studio Code hata ayıklama (platformlar arası)</span><span class="sxs-lookup"><span data-stu-id="ee95b-108">Debug from Visual Studio Code (cross-platform)</span></span>

<span data-ttu-id="ee95b-109">Visual Studio Code Raspberry Pi üzerinde .NET hatası ayıklama, Raspberry Pi üzerinde yapılandırma adımlarını ve projenin *launch.jsdosya üzerinde* olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ee95b-109">Debugging .NET on Raspberry Pi from Visual Studio Code requires configuration steps on the Raspberry Pi and in the project's *launch.json* file.</span></span>

### <a name="enable-ssh-on-the-raspberry-pi"></a><span data-ttu-id="ee95b-110">Raspberry PI üzerinde SSH 'yi etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="ee95b-110">Enable SSH on the Raspberry Pi</span></span>

<span data-ttu-id="ee95b-111">Uzaktan hata ayıklama için SSH gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ee95b-111">SSH is required for remote debugging.</span></span> <span data-ttu-id="ee95b-112">SSH 'yi etkinleştirmek için [Raspberry PI BELGELERINDEKI *SSH 'yi etkinleştirme* bölümüne bakın](https://www.raspberrypi.org/documentation/remote-access/ssh/).</span><span class="sxs-lookup"><span data-stu-id="ee95b-112">To enable SSH, [refer to *Enable SSH* in the Raspberry Pi documentation](https://www.raspberrypi.org/documentation/remote-access/ssh/).</span></span>

### <a name="install-the-visual-studio-remote-debugger-on-the-raspberry-pi"></a><span data-ttu-id="ee95b-113">Visual Studio Uzaktan Hata Ayıklayıcı Raspberry Pi 'ye yükler</span><span class="sxs-lookup"><span data-stu-id="ee95b-113">Install the Visual Studio Remote Debugger on the Raspberry Pi</span></span>

<span data-ttu-id="ee95b-114">Raspberry PI 'deki Bash konsolu içinde (yerel olarak veya SSH aracılığıyla), aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="ee95b-114">Within a Bash console on the Raspberry Pi (either locally or via SSH), complete the following steps:</span></span>

1. <span data-ttu-id="ee95b-115">Raspberry Pi 'ye Visual Studio Uzaktan Hata Ayıklayıcı indirmek ve yüklemek için aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="ee95b-115">Execute the following command to download and install the Visual Studio Remote Debugger on the Raspberry Pi:</span></span>

    ```bash
    curl -sSL https://aka.ms/getvsdbgsh | /bin/sh /dev/stdin -v latest -l ~/vsdbg
    ```

1. <span data-ttu-id="ee95b-116">Hata ayıklayıcı farklı şekilde çalışıyor olmalıdır `root` .</span><span class="sxs-lookup"><span data-stu-id="ee95b-116">The debugger requires running as `root`.</span></span> <span data-ttu-id="ee95b-117">Varsayılan olarak, `root` Raspberry PI üzerinde parola yoktur.</span><span class="sxs-lookup"><span data-stu-id="ee95b-117">By default, `root` has no password on Raspberry Pi.</span></span> <span data-ttu-id="ee95b-118">`root`Aşağıdaki komutu yürüterek ve istemleri izleyerek için bir parola ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ee95b-118">Set a password for `root` by executing the following command and following the prompts.</span></span>

    ```bash
    sudo passwd root
    ```

1. <span data-ttu-id="ee95b-119">Visual Studio Code, uzaktan hata ayıklamak için SSH protokolünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="ee95b-119">Visual Studio Code uses the SSH protocol to debug remotely.</span></span> <span data-ttu-id="ee95b-120">Güvenlik nedeniyle, `root` Varsayılan olarak SSH aracılığıyla oturum açmasına izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="ee95b-120">For security purposes, `root` is not permitted to log on via SSH by default.</span></span> <span data-ttu-id="ee95b-121">`root`SSH aracılığıyla oturum açmaya olanak tanımak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="ee95b-121">To enable `root` to log on via SSH, complete the following steps:</span></span>

    1. <span data-ttu-id="ee95b-122">[Nano](https://www.nano-editor.org/docs.php)'da */etc/ssh/sshd_config* açmak için aşağıdaki komutu yürütün.</span><span class="sxs-lookup"><span data-stu-id="ee95b-122">Execute the following command to open */etc/ssh/sshd_config* in [nano](https://www.nano-editor.org/docs.php).</span></span>

        ```bash
        sudo nano /etc/ssh/sshd_config
        ```

    1. <span data-ttu-id="ee95b-123"><kbd>CTRL + W</kbd> tuşlarına basın ve **Permitrootlogın**'i arayın.</span><span class="sxs-lookup"><span data-stu-id="ee95b-123">Press <kbd>Ctrl+W</kbd> and search for **PermitRootLogin**.</span></span>
    1. <span data-ttu-id="ee95b-124">Gerekirse, **Permitrootlogın** 'e sahip satırın açıklamasını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="ee95b-124">Uncomment the line with **PermitRootLogin** if needed.</span></span>
    1. <span data-ttu-id="ee95b-125">Satırı şu şekilde okunacak şekilde değiştirin:</span><span class="sxs-lookup"><span data-stu-id="ee95b-125">Change the line to read as follows:</span></span>

        ```console
        PermitRootLogin yes
        ```

        > [!NOTE]
        > <span data-ttu-id="ee95b-126">*/Etc/ssh/sshd_config*'de **PermitRootLogin** satırı yoksa yukarıda gösterilen değere sahip yeni bir satır ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ee95b-126">If there is no **PermitRootLogin** line in */etc/ssh/sshd_config*, add a new line with the value shown above.</span></span>

    1. <span data-ttu-id="ee95b-127">Çıkmak için <kbd>CTRL + X</kbd> tuşlarına basın ve olasılığınızı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="ee95b-127">Press <kbd>Ctrl+X</kbd> to exit and save your chances.</span></span> <span data-ttu-id="ee95b-128">**Değiştirilen arabelleği kaydetmek** isteyip istemediğiniz sorulduğunda, onaylamak için <kbd>Y</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="ee95b-128">When prompted **Save modified buffer?**, press <kbd>Y</kbd> to confirm.</span></span> <span data-ttu-id="ee95b-129">Özgün dosyanın üzerine yazılmasını onaylamak için <kbd>ENTER</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="ee95b-129">Press <kbd>Enter</kbd> to confirm overwriting the original file.</span></span>
    1. <span data-ttu-id="ee95b-130">Aşağıdaki komutu yürüterek Raspberry Pi 'yi yeniden başlatın:</span><span class="sxs-lookup"><span data-stu-id="ee95b-130">Reboot the Raspberry Pi by executing the following command:</span></span>

        ```bash
        sudo reboot
        ```

### <a name="setup-launchjson-in-visual-studio-code"></a><span data-ttu-id="ee95b-131">Visual Studio Code launch.jskurulum</span><span class="sxs-lookup"><span data-stu-id="ee95b-131">Setup launch.json in Visual Studio Code</span></span>

<span data-ttu-id="ee95b-132">Projenin *launch.jsüzerinde* bir başlatma yapılandırması ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ee95b-132">Add a launch configuration to the project's *launch.json*.</span></span> <span data-ttu-id="ee95b-133">Projenin dosya *üzerinde birlaunch.js* yoksa, **Çalıştır** sekmesine geçerek, **dosya üzerinde launch.jsoluştur**' u seçerek ve iletişim kutusunda **.net** veya **.NET Core** ' u seçerek bir tane ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ee95b-133">If the project doesn't have a *launch.json* file, add one by switching to the **Run** tab, selecting **create a launch.json file**, and selecting **.NET** or **.NET Core** in the dialog.</span></span>

<span data-ttu-id="ee95b-134">*launch.jsüzerindeki* yeni yapılandırma şuna benzer görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="ee95b-134">The new configuration in *launch.json* should look similar to this:</span></span>

```json
"configurations": [
    {
        "name": ".NET Core Launch (remote console)",
        "type": "coreclr",
        "request": "launch",
        "preLaunchTask": "build",
        "program": "/home/pi/.dotnet/dotnet",
        "args": ["/home/pi/sample/Sample.dll"],
        "cwd": "/home/pi/sample",
        "stopAtEntry": false,
        "console": "internalConsole",
        "pipeTransport": {
            "pipeCwd": "${workspaceFolder}",
            "pipeProgram": "C:\\Program Files\\PuTTY\\PLINK.EXE",
            "pipeArgs": [
                "-pw",
                "P@ssw0rd",
                "root@raspberrypi"
            ],
            "debuggerPath": "/home/pi/vsdbg/vsdbg"
        }
    },
```

<span data-ttu-id="ee95b-135">Aşağıdakilere dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="ee95b-135">Notice the following:</span></span>

- <span data-ttu-id="ee95b-136">`program` , PI üzerinde .NET çalışma zamanının yoludur.</span><span class="sxs-lookup"><span data-stu-id="ee95b-136">`program` is the path to the .NET runtime on the Pi.</span></span>
- <span data-ttu-id="ee95b-137">`args` , Pi üzerinde hata ayıklamak için derlemenin yoludur.</span><span class="sxs-lookup"><span data-stu-id="ee95b-137">`args` is the path to the assembly to debug on the Pi.</span></span>
- <span data-ttu-id="ee95b-138">`cwd` , uygulama PI üzerinde başlatıldığında kullanılacak çalışma dizinidir.</span><span class="sxs-lookup"><span data-stu-id="ee95b-138">`cwd` is the working directory to use when launching the app on the Pi.</span></span>
- <span data-ttu-id="ee95b-139">`pipeProgram` , yerel makinedeki bir SSH istemcisinin yoludur.</span><span class="sxs-lookup"><span data-stu-id="ee95b-139">`pipeProgram` is the path to an SSH client on the local machine.</span></span>
- <span data-ttu-id="ee95b-140">`pipeArgs` , SSH istemcisine geçirilecek parametrelerdir.</span><span class="sxs-lookup"><span data-stu-id="ee95b-140">`pipeArgs` are the parameters to be passed to the SSH client.</span></span> <span data-ttu-id="ee95b-141">Parola parametresini ve bu biçimdeki kullanıcıyı da belirttiğinizden emin olun `root` `<user>@<hostname>` .</span><span class="sxs-lookup"><span data-stu-id="ee95b-141">Be sure to specify the password parameter, as well as the `root` user in the format `<user>@<hostname>`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ee95b-142">Yukarıdaki örnek, [Putty](https://www.ssh.com/ssh/putty/) SSH istemcisinin bir bileşeni olan *plınk*'i kullanır <span class="docon docon-navigate-external x-hidden-focus"></span> .</span><span class="sxs-lookup"><span data-stu-id="ee95b-142">The above example uses *plink*, a component of the [PuTTY](https://www.ssh.com/ssh/putty/)<span class="docon docon-navigate-external x-hidden-focus"></span> SSH client.</span></span> <span data-ttu-id="ee95b-143">[](https://www.openssh.com/) <span class="docon docon-navigate-external x-hidden-focus"></span> Windows ve Linux 'un son sürümlerinde bulunan OpenSSH, bunun yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ee95b-143">[OpenSSH](https://www.openssh.com/)<span class="docon docon-navigate-external x-hidden-focus"></span>, which is included in recent versions of Windows and Linux, may be used instead.</span></span> <span data-ttu-id="ee95b-144">Ancak, OpenSSH, parolaların komut satırı parametresi olarak gönderilmesini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="ee95b-144">However, OpenSSH doesn't support sending passwords as a command-line parameter.</span></span> <span data-ttu-id="ee95b-145">OpenSSH kullanmak için, [Raspberry PI 'nizi passwordless SSH erişimi için yapılandırın](https://www.raspberrypi.org/documentation/remote-access/ssh/passwordless.md).</span><span class="sxs-lookup"><span data-stu-id="ee95b-145">To use OpenSSH, [configure your Raspberry Pi for passwordless SSH access](https://www.raspberrypi.org/documentation/remote-access/ssh/passwordless.md).</span></span>

### <a name="deploy-the-app"></a><span data-ttu-id="ee95b-146">Uygulamayı dağıtma</span><span class="sxs-lookup"><span data-stu-id="ee95b-146">Deploy the app</span></span>

<span data-ttu-id="ee95b-147">Uygulamayı [.NET uygulamalarını Raspberry PI 'ye dağıtma](deployment.md)bölümünde açıklandığı şekilde dağıtın.</span><span class="sxs-lookup"><span data-stu-id="ee95b-147">Deploy the app as described in [Deploy .NET apps to Raspberry Pi](deployment.md).</span></span> <span data-ttu-id="ee95b-148">Dağıtım yolunun, `cwd` yapılandırmada *launch.js* parametresinde belirtilen yol olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="ee95b-148">Ensure the deployment path is the same path specified in the `cwd` parameter in the *launch.json* configuration.</span></span>

### <a name="launch-the-debugger"></a><span data-ttu-id="ee95b-149">Hata ayıklayıcıyı başlatma</span><span class="sxs-lookup"><span data-stu-id="ee95b-149">Launch the debugger</span></span>

<span data-ttu-id="ee95b-150">**Çalıştır** sekmesinde **.NET Core başlatma (uzak konsol)** yapılandırmasını seçin ve **hata ayıklamayı Başlat**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="ee95b-150">On the **Run** tab, select the **.NET Core Launch (remote console)** configuration and select **Start Debugging**.</span></span> <span data-ttu-id="ee95b-151">Uygulama Raspberry PI üzerinde başlatılır.</span><span class="sxs-lookup"><span data-stu-id="ee95b-151">The app launches on the Raspberry Pi.</span></span> <span data-ttu-id="ee95b-152">Hata ayıklayıcı, kesme noktaları ayarlamak, yerelleri incelemek ve daha fazlasını yapmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ee95b-152">The debugger may be used to set breakpoints, inspect locals, and more.</span></span>

## <a name="references"></a><span data-ttu-id="ee95b-153">Başvurular</span><span class="sxs-lookup"><span data-stu-id="ee95b-153">References</span></span>

[<span data-ttu-id="ee95b-154">ARM 'de .NET Core kullanarak Windows üzerinde VS Code uzaktan hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="ee95b-154">Remote debugging with VS Code on Windows to a Raspberry Pi using .NET Core on ARM</span></span>](https://www.hanselman.com/blog/remote-debugging-with-vs-code-on-windows-to-a-raspberry-pi-using-net-core-on-arm)

::: zone-end

::: zone pivot="visualstudio"

## <a name="debug-from-visual-studio-on-windows"></a><span data-ttu-id="ee95b-155">Windows üzerinde Visual Studio 'da hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="ee95b-155">Debug from Visual Studio on Windows</span></span>

<span data-ttu-id="ee95b-156">Visual Studio, uzak cihazlarda .NET uygulamalarında SSH aracılığıyla hata ayıklama yapabilir.</span><span class="sxs-lookup"><span data-stu-id="ee95b-156">Visual Studio can debug .NET apps on remote devices via SSH.</span></span> <span data-ttu-id="ee95b-157">Cihazda özelleştirilmiş yapılandırma gerekmez.</span><span class="sxs-lookup"><span data-stu-id="ee95b-157">No specialized configuration is required on the device.</span></span> <span data-ttu-id="ee95b-158">.NET uzaktan hata ayıklamak için Visual Studio 'Yu kullanma hakkında ayrıntılı bilgi için bkz. [SSH kullanarak Linux üzerinde uzaktan hata ayıklama .net](/visualstudio/debugger/remote-debugging-dotnet-core-linux-with-ssh?view=vs-2019).</span><span class="sxs-lookup"><span data-stu-id="ee95b-158">For details on using Visual Studio to debug .NET remotely, see [Remote debug .NET on Linux using SSH](/visualstudio/debugger/remote-debugging-dotnet-core-linux-with-ssh?view=vs-2019).</span></span>

::: zone-end
