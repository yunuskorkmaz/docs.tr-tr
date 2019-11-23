---
title: 'Nasıl yapılır: Windows hizmetlerini yükleme ve kaldırma'
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
ms.openlocfilehash: 38fc0172b5f97561d69fe495237e95597d7b9727
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003127"
---
# <a name="how-to-install-and-uninstall-windows-services"></a>Nasıl yapılır: Windows hizmetlerini yükleme ve kaldırma

.NET Framework ile bir Windows hizmeti geliştiriyorsanız, [*InstallUtil. exe*](../tools/installutil-exe-installer-tool.md) komut satırı yardımcı programını veya [PowerShell](/powershell/scripting/overview)'i kullanarak hizmet uygulamanızı hızlı bir şekilde yükleyebilirsiniz. Kullanıcıların yükleyebileceği ve kaldırabildiği bir Windows hizmetini yayınlamak isteyen geliştiriciler InstallShield kullanmalıdır. Daha fazla bilgi için bkz. [Yükleyici paketi oluşturma (Windows istemcisi)](https://docs.microsoft.com/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-client).

> [!WARNING]
> Bilgisayarınızdan bir hizmeti kaldırmak istiyorsanız, bu makaledeki adımları izleyin. Bunun yerine, hizmeti hangi programın veya yazılım paketinin yüklendiğini öğrenin ve ardından bu programı kaldırmak için ayarlar ' da **uygulamalar** ' ı seçin. Birçok hizmetin Windows 'un ayrılmaz parçaları olduğunu unutmayın; Bunları kaldırırsanız, sistem kararsızlığına neden olabilirsiniz.

Bu makaledeki adımları kullanmak için, önce Windows hizmetinize bir hizmet Yükleyicisi eklemeniz gerekir. Daha fazla bilgi için bkz. [Izlenecek yol: Windows hizmet uygulaması oluşturma](../windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).

F5 'e basarak Windows hizmeti projelerini doğrudan Visual Studio geliştirme ortamından çalıştıramazsınız. Projeyi çalıştırmadan önce, hizmeti projeye yüklemelisiniz.

> [!TIP]
> Hizmetinizi yüklediğinizi veya kaldırdığınızı doğrulamak için **Sunucu Gezgini** kullanabilirsiniz. Daha fazla bilgi için bkz. [Visual Studio 'da Sunucu Gezgini kullanma](https://support.microsoft.com/help/316649/how-to-use-the-server-explorer-in-visual-studio-net-and-visual-studio).

### <a name="install-your-service-manually-using-installutilexe-utility"></a>InstallUtil. exe yardımcı programını kullanarak hizmetinizi el ile yükleme

1. **Başlat** menüsünde, **Visual Studio \<*Sürüm*>** dizinini seçin ve sonra **vs \<*Sürüm*>için geliştirici komut istemi** ' yı seçin.

     Visual Studio için Geliştirici Komut İstemi görüntülenir.

2. Projenizin derlenmiş yürütülebilir dosyasının bulunduğu dizine erişin.

3. Komut isteminden *InstallUtil. exe* ' yi bir parametre olarak projenizin yürütülebilir dosyası ile çalıştırın:

    ```console
    installutil <yourproject>.exe
    ```

     Visual Studio için Geliştirici Komut İstemi kullanıyorsanız, *InstallUtil. exe* dosyası sistem yolunda olmalıdır. Aksi takdirde, yolu yola ekleyebilir veya tam yolu kullanarak çağırabilirsiniz. Bu araç, *%windir%\Microsoft.NET\Framework [64]\\< framework_version\>* .NET Framework ile yüklenir.

     Örneğin:
     - .NET Framework 4 veya 4,5 ' nin 32 bit sürümü ve sonrasında, Windows yükleme dizininiz *C:\Windows*ise, varsayılan yol *C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*' dir.
     - .NET Framework 4 veya 4,5 ve sonraki sürümlerin 64 bit sürümü için varsayılan yol *C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*' dir.

### <a name="uninstall-your-service-manually-using-installutilexe-utility"></a>InstallUtil. exe yardımcı programını kullanarak hizmetinizi el ile kaldırın

1. **Başlat** menüsünde, **Visual Studio \<*Sürüm*>** dizinini seçin ve sonra **vs \<*Sürüm*>için geliştirici komut istemi** ' yı seçin.

     Visual Studio için Geliştirici Komut İstemi görüntülenir.

2. Komut isteminden *InstallUtil. exe* ' yi bir parametre olarak projenizin çıkışıyla çalıştırın:

    ```console
    installutil /u <yourproject>.exe
    ```

3. Bir hizmetin yürütülebilir dosyası silindikten sonra, hizmet kayıt defterinde hala mevcut olabilir. Bu durumda, hizmet girdisini kayıt defterinden kaldırmak için [sc delete](/windows-server/administration/windows-commands/sc-delete) komutunu kullanın.

### <a name="install-your-service-manually-using-powershell"></a>PowerShell kullanarak hizmetinizi el ile yükleyebilirsiniz

1. **Başlat** menüsünde **Windows PowerShell** dizini ' ni seçin ve ardından **Windows PowerShell**' i seçin.

2. Projenizin derlenmiş yürütülebilir dosyasının bulunduğu dizine erişin.

3. [**Yeni-Service**](/powershell/module/microsoft.powershell.management/new-service) cmdlet 'ini, projenizin çıkışıyla ve bir hizmet adıyla birlikte parametre olarak çalıştırın:

    ```powershell
    New-Service -Name "YourServiceName" -BinaryPathName <yourproject>.exe
    ```

### <a name="uninstall-your-service-manually-using-powershell"></a>PowerShell kullanarak hizmetinizi el ile kaldırma

1. **Başlat** menüsünde **Windows PowerShell** dizini ' ni seçin ve ardından **Windows PowerShell**' i seçin.

2. [**Remove-Service**](/powershell/module/microsoft.powershell.management/remove-service) cmdlet 'ini, hizmetinizin adı parametresiyle çalıştırın:

    ```powershell
    Remove-Service -Name "YourServiceName"
    ```

3. Bir hizmetin yürütülebilir dosyası silindikten sonra, hizmet kayıt defterinde hala mevcut olabilir. Bu durumda, hizmet girdisini kayıt defterinden kaldırmak için [sc delete](/windows-server/administration/windows-commands/sc-delete) komutunu kullanın.

    ```powershell
    sc.exe delete "YourServiceName"
    ```

## <a name="see-also"></a>Ayrıca bkz.

- [Windows hizmet uygulamalarına giriş](../windows-services/introduction-to-windows-service-applications.md)
- [Nasıl yapılır: Windows Hizmetleri oluşturma](../windows-services/how-to-create-windows-services.md)
- [Nasıl yapılır: hizmet uygulamanıza yükleyiciler ekleme](../windows-services/how-to-add-installers-to-your-service-application.md)
- [InstallUtil. exe (yükleyici aracı)](../tools/installutil-exe-installer-tool.md)
