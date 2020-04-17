---
title: 'Nasıl yapilir: Windows hizmetlerini yükleme ve kaldırma'
ms.date: 02/05/2019
helpviewer_keywords:
- Windows Service applications, deploying
- services, uninstalling
- services, installing
- installing Windows Services
- uninstalling applications, apps, Windows services
- installation, Windows services
- uninstalling Windows services
- installutil.exe tool
ms.assetid: c89c5169-f567-4305-9d62-db31a1de5481
author: ghogen
ms.openlocfilehash: 8937ef8b4007253b06444e59b292395084e4df2f
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607925"
---
# <a name="how-to-install-and-uninstall-windows-services"></a>Nasıl yapilir: Windows hizmetlerini yükleme ve kaldırma

.NET Framework yüklü bir Windows hizmeti geliştiriyorsanız, [*InstallUtil.exe*](../tools/installutil-exe-installer-tool.md) komut satırı yardımcı programını veya [PowerShell'i](/powershell/scripting/overview)kullanarak servis uygulamanızı hızlı bir şekilde yükleyebilirsiniz. Kullanıcıların yükleyip kaldırabileceği bir Windows hizmeti yayımlamak isteyen geliştiriciler InstallShield'i kullanmalıdır. Daha fazla bilgi için [bkz.](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop)

> [!WARNING]
> Bilgisayarınızdan bir hizmeti kaldırmak istiyorsanız, bu makaledeki adımları izlemeyin. Bunun yerine, hizmeti hangi program veya yazılım paketinin yüklediğini öğrenin ve ardından bu programı kaldırmak için Ayarlar'daki **Uygulamaları** seçin. Birçok hizmetin Windows'un ayrılmaz parçaları olduğunu unutmayın; bunları kaldırırsanız, sistem kararsızlığı neden olabilir.

Bu makaledeki adımları kullanmak için öncelikle Windows hizmetinize bir hizmet yükleyici eklemeniz gerekir. Daha fazla bilgi için [Walkthrough: Windows hizmeti uygulaması oluşturma '](../windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)na bakın.

F5 tuşuna basarak Windows hizmet projelerini doğrudan Visual Studio geliştirme ortamından çalıştıramazsınız. Projeyi çalıştıramadan önce hizmeti projeye yüklemeniz gerekir.

> [!TIP]
> Hizmetinizi yüklediğinizi veya kaldırdığınızı doğrulamak için **Server Explorer'ı** kullanabilirsiniz. Daha fazla bilgi için [Visual Studio'da Sunucu Gezgini nasıl kullanılır.](https://support.microsoft.com/help/316649/how-to-use-the-server-explorer-in-visual-studio-net-and-visual-studio)

### <a name="install-your-service-manually-using-installutilexe-utility"></a>InstallUtil.exe yardımcı programını kullanarak hizmetinizi el ile yükleyin

1. **Başlat** menüsünden Visual ** \<Studio *sürüm* > ** dizinini seçin ve ardından **VS \< *sürümü*>için Geliştirici Komut Komut Ustem'i**seçin.

     Visual Studio için Geliştirici Komut Komut Ustem görüntülenir.

2. Projenizin derlenebilir yürütülebilir dosyasının bulunduğu dizine erişin.

3. *InstallUtil.exe* komut isteminden projenizin yürütülebilir bir parametre olarak çalıştırılabilir çalıştırışlarını çalıştırın:

    ```console
    installutil <yourproject>.exe
    ```

     Visual Studio için Geliştirici Komut Komut Komut Ui komut istemikullanıyorsanız, *InstallUtil.exe* sistem yolunda olmalıdır. Aksi takdirde, onu yola ekleyebilir veya çağırmak için tam nitelikli yolu kullanabilirsiniz. Bu araç *%WINDIR%\Microsoft.NET\Framework[64]\\<framework_version\>*.NET Framework ile yüklenir.

     Örneğin:
     - .NET Framework 4 veya 4.5 ve sonraki 32 bit sürümü için, Windows yükleme dizininiz *C:\Windows*ise, varsayılan yol *C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*' dir.
     - .NET Framework 4 veya 4.5 ve sonraki 64 bit sürümü için varsayılan yol *C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe'* dir.

### <a name="uninstall-your-service-manually-using-installutilexe-utility"></a>InstallUtil.exe yardımcı programını kullanarak hizmetinizi el ile kaldırın

1. **Başlat** menüsünden Visual ** \<Studio *sürüm* > ** dizinini seçin ve ardından **VS \< *sürümü*>için Geliştirici Komut Komut Ustem'i**seçin.

     Visual Studio için Geliştirici Komut Komut Ustem görüntülenir.

2. *InstallUtil.exe* komut isteminden projenizin çıktısını parametre olarak çalıştırın:

    ```console
    installutil /u <yourproject>.exe
    ```

3. Bir hizmetin yürütülebilirliği silindikten sonra, hizmet kayıt defterinde hala bulunabilir. Bu durumda, hizmetgirişini kayıt defterinden kaldırmak için [sc delete](/windows-server/administration/windows-commands/sc-delete) komutunu kullanın.

### <a name="install-your-service-manually-using-powershell"></a>PowerShell'i kullanarak hizmetinizi el ile yükleyin

1. **Başlat** menüsünden Windows **PowerShell** dizinini seçin ve ardından **Windows PowerShell'i**seçin.

2. Projenizin derlenebilir yürütülebilir dosyasının bulunduğu dizine erişin.

3. Yeni [**Servis**](/powershell/module/microsoft.powershell.management/new-service) cmdletini projenizin çıktısı ve bir hizmet adı ile parametreler olarak çalıştırın:

    ```powershell
    New-Service -Name "YourServiceName" -BinaryPathName <yourproject>.exe
    ```

### <a name="uninstall-your-service-manually-using-powershell"></a>PowerShell'i kullanarak hizmetinizi el ile kaldırın

1. **Başlat** menüsünden Windows **PowerShell** dizinini seçin ve ardından **Windows PowerShell'i**seçin.

2. [**Hizmetin**](/powershell/module/microsoft.powershell.management/remove-service) adı ile Hizmet Kaldır cmdletini parametre olarak çalıştırın:

    ```powershell
    Remove-Service -Name "YourServiceName"
    ```

3. Bir hizmetin yürütülebilirliği silindikten sonra, hizmet kayıt defterinde hala bulunabilir. Bu durumda, hizmetgirişini kayıt defterinden kaldırmak için [sc delete](/windows-server/administration/windows-commands/sc-delete) komutunu kullanın.

    ```powershell
    sc.exe delete "YourServiceName"
    ```

## <a name="see-also"></a>Ayrıca bkz.

- [Windows hizmet uygulamalarına giriş](../windows-services/introduction-to-windows-service-applications.md)
- [Nasıl yapilir: Windows hizmetleri oluşturma](../windows-services/how-to-create-windows-services.md)
- [Nasıl yapilir: Servis uygulamanıza yükleyici ekleme](../windows-services/how-to-add-installers-to-your-service-application.md)
- [Installutil.exe (Yükleme aracı)](../tools/installutil-exe-installer-tool.md)
