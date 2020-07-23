---
title: 'Nasıl yapılır: Windows hizmetlerini yükleme ve kaldırma'
description: Bkz. Windows hizmetlerini yükleme ve kaldırma. .NET ile bir Windows hizmeti geliştirmekte çalışıyorsanız InstallUtil.exe veya PowerShell kullanabilirsiniz.
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
ms.openlocfilehash: 5597043bb1c5af05f5f3633cba6ee6e6de1c52c1
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925611"
---
# <a name="how-to-install-and-uninstall-windows-services"></a>Nasıl yapılır: Windows hizmetlerini yükleme ve kaldırma

.NET Framework ile bir Windows hizmeti geliştiriyorsanız, [*InstallUtil.exe*](../tools/installutil-exe-installer-tool.md) komut satırı yardımcı programını veya [PowerShell](/powershell/scripting/overview)'i kullanarak hizmet uygulamanızı hızlı bir şekilde yükleyebilirsiniz. Kullanıcıların yükleyebileceği ve kaldırabildiği bir Windows hizmetini yayınlamak isteyen geliştiriciler InstallShield kullanmalıdır. Daha fazla bilgi için bkz. [Yükleyici paketi oluşturma (Windows Masaüstü)](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).

> [!WARNING]
> Bilgisayarınızdan bir hizmeti kaldırmak istiyorsanız, bu makaledeki adımları izleyin. Bunun yerine, hizmeti hangi programın veya yazılım paketinin yüklendiğini öğrenin ve ardından bu programı kaldırmak için ayarlar ' da **uygulamalar** ' ı seçin. Birçok hizmetin Windows 'un ayrılmaz parçaları olduğunu unutmayın; Bunları kaldırırsanız, sistem kararsızlığına neden olabilirsiniz.

Bu makaledeki adımları kullanmak için, önce Windows hizmetinize bir hizmet Yükleyicisi eklemeniz gerekir. Daha fazla bilgi için bkz. [Izlenecek yol: Windows hizmet uygulaması oluşturma](walkthrough-creating-a-windows-service-application-in-the-component-designer.md).

F5 'e basarak Windows hizmeti projelerini doğrudan Visual Studio geliştirme ortamından çalıştıramazsınız. Projeyi çalıştırmadan önce, hizmeti projeye yüklemelisiniz.

> [!TIP]
> Hizmetinizi yüklediğinizi veya kaldırdığınızı doğrulamak için **Sunucu Gezgini** kullanabilirsiniz. Daha fazla bilgi için bkz. [Visual Studio 'da Sunucu Gezgini kullanma](https://support.microsoft.com/help/316649/how-to-use-the-server-explorer-in-visual-studio-net-and-visual-studio).

### <a name="install-your-service-manually-using-installutilexe-utility"></a>InstallUtil.exe yardımcı programını kullanarak hizmetinizi el ile yükleyebilirsiniz

1. **Başlat** menüsünde **Visual Studio \<*version*> ** dizinini seçin ve ardından ** \<*version*> vs için geliştirici komut istemi **seçin.

     Visual Studio için Geliştirici Komut İstemi görüntülenir.

2. Projenizin derlenmiş yürütülebilir dosyasının bulunduğu dizine erişin.

3. Komut isteminden proje yürütülebiliri olarak parametre olarak *InstallUtil.exe* çalıştırın:

    ```console
    installutil <yourproject>.exe
    ```

     Visual Studio için Geliştirici Komut İstemi kullanıyorsanız, *InstallUtil.exe* sistem yolunda olmalıdır. Aksi takdirde, yolu yola ekleyebilir veya tam yolu kullanarak çağırabilirsiniz. Bu araç, *%windir%\Microsoft.NET\Framework [64] \\<framework_version \> *.NET Framework ile yüklenir.

     Örneğin:
     - .NET Framework 4 veya 4,5 ' nin 32 bit sürümü ve sonrasında, Windows yükleme dizininiz *C:\Windows*ise, varsayılan yol *C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*.
     - .NET Framework 4 veya 4,5 ve sonraki sürümlerin 64 bit sürümü için varsayılan yol *C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.

### <a name="uninstall-your-service-manually-using-installutilexe-utility"></a>InstallUtil.exe yardımcı programını kullanarak hizmetinizi el ile kaldırın

1. **Başlat** menüsünde **Visual Studio \<*version*> ** dizinini seçin ve ardından ** \<*version*> vs için geliştirici komut istemi **seçin.

     Visual Studio için Geliştirici Komut İstemi görüntülenir.

2. Komut isteminden *InstallUtil.exe* bir parametre olarak projenizin çıkışıyla çalıştırın:

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

- [Windows hizmet uygulamalarına giriş](introduction-to-windows-service-applications.md)
- [Nasıl yapılır: Windows Hizmetleri oluşturma](how-to-create-windows-services.md)
- [Nasıl yapılır: hizmet uygulamanıza yükleyiciler ekleme](how-to-add-installers-to-your-service-application.md)
- [Installutil.exe (Yükleme aracı)](../tools/installutil-exe-installer-tool.md)
