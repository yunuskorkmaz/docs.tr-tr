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
# <a name="debug-net-apps-on-raspberry-pi"></a>Raspberry PI üzerinde .NET uygulamalarında hata ayıklama

Raspberry PI gibi ARM tabanlı IoT cihazlarında çalışan .NET uygulamalarında hata ayıklama, benzersiz bir zorluk gösterir. ARM cihazlarda .NET uygulamaları geliştirmek mümkündür. Ancak, Visual Studio dışında .NET uygulamalarında hata ayıklamak için gereken OmniSharp ARM cihazlarıyla uyumlu değildir. Sonuç olarak, uygulamaların uyumlu bir platformdan uzaktan ayıklanmalıdır.

::: zone pivot="vscode"

## <a name="debug-from-visual-studio-code-cross-platform"></a>Visual Studio Code hata ayıklama (platformlar arası)

Visual Studio Code Raspberry Pi üzerinde .NET hatası ayıklama, Raspberry Pi üzerinde yapılandırma adımlarını ve projenin *launch.jsdosya üzerinde* olmasını gerektirir.

### <a name="enable-ssh-on-the-raspberry-pi"></a>Raspberry PI üzerinde SSH 'yi etkinleştirme

Uzaktan hata ayıklama için SSH gereklidir. SSH 'yi etkinleştirmek için [Raspberry PI BELGELERINDEKI *SSH 'yi etkinleştirme* bölümüne bakın](https://www.raspberrypi.org/documentation/remote-access/ssh/).

### <a name="install-the-visual-studio-remote-debugger-on-the-raspberry-pi"></a>Visual Studio Uzaktan Hata Ayıklayıcı Raspberry Pi 'ye yükler

Raspberry PI 'deki Bash konsolu içinde (yerel olarak veya SSH aracılığıyla), aşağıdaki adımları izleyin:

1. Raspberry Pi 'ye Visual Studio Uzaktan Hata Ayıklayıcı indirmek ve yüklemek için aşağıdaki komutu yürütün:

    ```bash
    curl -sSL https://aka.ms/getvsdbgsh | /bin/sh /dev/stdin -v latest -l ~/vsdbg
    ```

1. Hata ayıklayıcı farklı şekilde çalışıyor olmalıdır `root` . Varsayılan olarak, `root` Raspberry PI üzerinde parola yoktur. `root`Aşağıdaki komutu yürüterek ve istemleri izleyerek için bir parola ayarlayın.

    ```bash
    sudo passwd root
    ```

1. Visual Studio Code, uzaktan hata ayıklamak için SSH protokolünü kullanır. Güvenlik nedeniyle, `root` Varsayılan olarak SSH aracılığıyla oturum açmasına izin verilmez. `root`SSH aracılığıyla oturum açmaya olanak tanımak için aşağıdaki adımları izleyin:

    1. [Nano](https://www.nano-editor.org/docs.php)'da */etc/ssh/sshd_config* açmak için aşağıdaki komutu yürütün.

        ```bash
        sudo nano /etc/ssh/sshd_config
        ```

    1. <kbd>CTRL + W</kbd> tuşlarına basın ve **Permitrootlogın**'i arayın.
    1. Gerekirse, **Permitrootlogın** 'e sahip satırın açıklamasını kaldırın.
    1. Satırı şu şekilde okunacak şekilde değiştirin:

        ```console
        PermitRootLogin yes
        ```

        > [!NOTE]
        > */Etc/ssh/sshd_config*'de **PermitRootLogin** satırı yoksa yukarıda gösterilen değere sahip yeni bir satır ekleyin.

    1. Çıkmak için <kbd>CTRL + X</kbd> tuşlarına basın ve olasılığınızı kaydedin. **Değiştirilen arabelleği kaydetmek** isteyip istemediğiniz sorulduğunda, onaylamak için <kbd>Y</kbd> tuşuna basın. Özgün dosyanın üzerine yazılmasını onaylamak için <kbd>ENTER</kbd> tuşuna basın.
    1. Aşağıdaki komutu yürüterek Raspberry Pi 'yi yeniden başlatın:

        ```bash
        sudo reboot
        ```

### <a name="setup-launchjson-in-visual-studio-code"></a>Visual Studio Code launch.jskurulum

Projenin *launch.jsüzerinde* bir başlatma yapılandırması ekleyin. Projenin dosya *üzerinde birlaunch.js* yoksa, **Çalıştır** sekmesine geçerek, **dosya üzerinde launch.jsoluştur**' u seçerek ve iletişim kutusunda **.net** veya **.NET Core** ' u seçerek bir tane ekleyin.

*launch.jsüzerindeki* yeni yapılandırma şuna benzer görünmelidir:

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

Aşağıdakilere dikkat edin:

- `program` , PI üzerinde .NET çalışma zamanının yoludur.
- `args` , Pi üzerinde hata ayıklamak için derlemenin yoludur.
- `cwd` , uygulama PI üzerinde başlatıldığında kullanılacak çalışma dizinidir.
- `pipeProgram` , yerel makinedeki bir SSH istemcisinin yoludur.
- `pipeArgs` , SSH istemcisine geçirilecek parametrelerdir. Parola parametresini ve bu biçimdeki kullanıcıyı da belirttiğinizden emin olun `root` `<user>@<hostname>` .

> [!IMPORTANT]
> Yukarıdaki örnek, [Putty](https://www.ssh.com/ssh/putty/) SSH istemcisinin bir bileşeni olan *plınk*'i kullanır <span class="docon docon-navigate-external x-hidden-focus"></span> . [](https://www.openssh.com/) <span class="docon docon-navigate-external x-hidden-focus"></span> Windows ve Linux 'un son sürümlerinde bulunan OpenSSH, bunun yerine kullanılabilir. Ancak, OpenSSH, parolaların komut satırı parametresi olarak gönderilmesini desteklemez. OpenSSH kullanmak için, [Raspberry PI 'nizi passwordless SSH erişimi için yapılandırın](https://www.raspberrypi.org/documentation/remote-access/ssh/passwordless.md).

### <a name="deploy-the-app"></a>Uygulamayı dağıtma

Uygulamayı [.NET uygulamalarını Raspberry PI 'ye dağıtma](deployment.md)bölümünde açıklandığı şekilde dağıtın. Dağıtım yolunun, `cwd` yapılandırmada *launch.js* parametresinde belirtilen yol olduğundan emin olun.

### <a name="launch-the-debugger"></a>Hata ayıklayıcıyı başlatma

**Çalıştır** sekmesinde **.NET Core başlatma (uzak konsol)** yapılandırmasını seçin ve **hata ayıklamayı Başlat**' ı seçin. Uygulama Raspberry PI üzerinde başlatılır. Hata ayıklayıcı, kesme noktaları ayarlamak, yerelleri incelemek ve daha fazlasını yapmak için kullanılabilir.

## <a name="references"></a>Başvurular

[ARM 'de .NET Core kullanarak Windows üzerinde VS Code uzaktan hata ayıklama](https://www.hanselman.com/blog/remote-debugging-with-vs-code-on-windows-to-a-raspberry-pi-using-net-core-on-arm)

::: zone-end

::: zone pivot="visualstudio"

## <a name="debug-from-visual-studio-on-windows"></a>Windows üzerinde Visual Studio 'da hata ayıklama

Visual Studio, uzak cihazlarda .NET uygulamalarında SSH aracılığıyla hata ayıklama yapabilir. Cihazda özelleştirilmiş yapılandırma gerekmez. .NET uzaktan hata ayıklamak için Visual Studio 'Yu kullanma hakkında ayrıntılı bilgi için bkz. [SSH kullanarak Linux üzerinde uzaktan hata ayıklama .net](/visualstudio/debugger/remote-debugging-dotnet-core-linux-with-ssh?view=vs-2019).

::: zone-end
