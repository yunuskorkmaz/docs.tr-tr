---
title: 'Nasıl yapılır: Windows Hizmetleri Yükleme ve kaldırma'
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
ms.openlocfilehash: 0119fee443aafd1d4215260d2cf42cec9f7eba74
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59308477"
---
# <a name="how-to-install-and-uninstall-windows-services"></a>Nasıl yapılır: Windows Hizmetleri Yükleme ve kaldırma
.NET Framework ile Windows hizmet geliştiriyorsanız, hızlı bir şekilde hizmet uygulamanızı kullanarak yükleyebileceğiniz [ *InstallUtil.exe* ](../tools/installutil-exe-installer-tool.md) komut satırı yardımcı programı. Bir Windows hizmeti, kullanıcıların yüklemek ve kaldırmak yayımlamayı isteyen geliştiriciler InstallShield kullanmanız gerekir. Daha fazla bilgi için [bir yükleyici paketi (Windows istemcisi) oluşturma](https://docs.microsoft.com/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-client).
  
> [!WARNING]
>  Bir hizmeti bilgisayarınızdan kaldırmak istiyorsanız, bu makaledeki adımları izlemeyin. Bunun yerine, hangi program veya yazılım paketinin yüklü kullanıma hizmeti bulun ve ardından **uygulamaları** Bu program kaldırma ayarları. Birçok hizmet Windows ayrılmaz olduğunu unutmayın; bunları kaldırırsanız, sistem kararsızlığına neden olabilir.  
  
 Bu makaledeki adımları kullanmak için önce Windows hizmetinize hizmeti yükleyicisi eklemeniz gerekir. Daha fazla bilgi için [izlenecek yol: Bir Windows hizmeti uygulaması oluşturma](../windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).  
  
 Windows service projeleri F5 tuşuna basarak, doğrudan Visual Studio geliştirme ortamından çalıştırılamaz. Proje çalıştırmadan önce hizmet projede yüklemeniz gerekir.  
  
> [!TIP]
>  Kullanabileceğiniz **Sunucu Gezgini** sizin yüklü veya hizmetinizi kaldırılması doğrulamak için. Daha fazla bilgi için [Visual Studio'da Sunucu Gezgini kullanma](https://support.microsoft.com/help/316649/how-to-use-the-server-explorer-in-visual-studio-net-and-visual-studio).
  
### <a name="install-your-service-manually"></a>Hizmetinizi el ile yükleyin  
  
1. Gelen **Başlat** menüsünde **Visual Studio \< *sürüm* >**  dizin ve select **Geliştirici komut istemi VS için \< *sürüm*>**.
  
     Visual Studio için geliştirici komut istemi görünür. 
  
2. Projenizin derlenmiş çalıştırılabilir dosyasının bulunduğu dizine erişin.  
  
3. Çalıştırma *InstallUtil.exe* komutu istemi projenizle parametre olarak çalıştırılabilir:  
  
    ```console
    installutil <yourproject>.exe  
    ```  

     Visual Studio için geliştirici komut istemi kullanıyorsanız *InstallUtil.exe* sistem yolunda olmalıdır. Aksi takdirde, yola ekleyin veya onu çağırmak için tam yolu kullanın. Bu araç, .NET Framework ile yüklenir *% WINDIR%\Microsoft.NET\Framework[64]\\< framework_version >*.
     
     Örneğin:
     - .NET Framework 4 veya 4.5 ve üzeri, eğer 32-bit sürümü için Windows yükleme dizinine olan *C:\Windows*, varsayılan yolu *C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*.
     - .NET Framework 4 veya 4.5 ve sonraki 64-bit sürümü için varsayılan yoldur *C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.
  
### <a name="uninstall-your-service-manually"></a>Hizmetinizi el ile kaldırma  
  
1. Gelen **Başlat** menüsünde **Visual Studio \< *sürüm* >**  dizin ve select **Geliştirici komut istemi VS için \< *sürüm*>**.
  
     Visual Studio için geliştirici komut istemi görünür.  
  
2. Çalıştırma *InstallUtil.exe* bir parametre olarak projenizin çıktısı ile komut isteminden:  
  
    ```console  
    installutil /u <yourproject>.exe  
    ```  
  
3. Yürütülebilir dosya için bir hizmet silindikten sonra hizmet kayıt defterinde mevcut olabilir. Bu durumda, komutu kullanın [sc delete](/windows-server/administration/windows-commands/sc-delete) kayıt defterinden service girişini kaldırmak için.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows hizmeti uygulamalarına giriş](../windows-services/introduction-to-windows-service-applications.md)
- [Nasıl yapılır: Windows Hizmetleri oluşturma](../windows-services/how-to-create-windows-services.md)
- [Nasıl yapılır: Hizmet uygulamasına yükleyiciler ekleme](../windows-services/how-to-add-installers-to-your-service-application.md)
- [InstallUtil.exe (Yükleme aracı)](../tools/installutil-exe-installer-tool.md)
