---
title: 'Nasıl Yapılır: Hizmetleri Yükleme ve Kaldırma'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, deploying
- services, uninstalling
- services, installing
- installing Windows Services
- uninstalling applications, Windows Services
- installation, Windows Services
- uninstalling Windows Services
- installutil.exe tool
ms.assetid: c89c5169-f567-4305-9d62-db31a1de5481
author: ghogen
manager: douge
ms.openlocfilehash: 0d42a37b2e84c310569666771ded38e5feca3608
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-install-and-uninstall-services"></a>Nasıl Yapılır: Hizmetleri Yükleme ve Kaldırma
Bir Windows hizmeti .NET Framework kullanarak geliştiriyorsanız InstallUtil.exe olarak adlandırılan bir komut satırı yardımcı programını kullanarak hizmet uygulamanızı hızlı bir şekilde yükleyebilirsiniz. Geliştiriciyseniz Windows kullanıcıları yüklemek ve kaldırmanız hizmeti yayımlamayı isteyen InstallShield kullanmanız gerekir. Bkz: [Windows Installer dağıtımı](http://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0).  
  
> [!WARNING]
>  Bir hizmeti bilgisayarınızdan kaldırmak istiyorsanız, bu makaledeki adımları izlemeyin. Bunun yerine, hizmet hangi program veya yazılım paketine yüklendiğini çıkışı bulun ve ardından **Program Ekle/Kaldır** bu programı kaldırmak için Denetim Masası'nda. Birçok Hizmetleri Windows ayrılmaz olduğunu unutmayın; bunları kaldırırsanız, sistem kararsızlığına neden olabilir.  
  
 Bu makaledeki adımları kullanabilmek için öncelikle bir hizmet yükleyici Windows hizmetinize eklemeniz gerekir. Bkz: [izlenecek yol: bir Windows oluşturma hizmet uygulaması Bileşen tasarımcısında](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).  
  
 Windows hizmeti projeleri F5 tuşuna basarak doğrudan Visual Studio geliştirme ortamından çalıştırılamaz. Proje çalıştırmadan önce projede hizmet yüklenmelidir olmasıdır.  
  
> [!TIP]
>  Başlatabilirsiniz **Sunucu Gezgini** ve hizmetinizi yüklü veya kaldırılmış olduğunu doğrulayın. Daha fazla bilgi için bkz: nasıl yapılır: erişim ve Sunucu Gezgini veritabanı Gezgini başlatılamıyor.  
  
### <a name="to-install-your-service-manually"></a>Hizmetinizi el ile yüklemek için  
  
1.  Windows **Başlat** menüsü veya **Başlat** ekranında, seçin **Visual Studio** , **Visual Studio Araçları**, **Geliştirici Komut İstemi**.  
  
     Visual Studio komut istemi belirir.  
  
2.  Projenizin derlenmiş yürütülebilir dosyasının bulunduğu dizine erişim.  
  
3.  InstallUtil.exe parametre olarak projenizin yürütülebilir ile komut isteminden çalıştırın:  
  
    ```  
    installutil <yourproject>.exe  
    ```  
  
     Visual Studio komut istemi kullanıyorsanız, InstallUtil.exe sistem yolunda olmalıdır. Değilse, yoluna ekleyin veya tam yolunu da çağırmak için kullanın. Bu aracı ile .NET Framework yüklü olduğundan ve kendi yolu `%WINDIR%\Microsoft.NET\Framework[64]\<framework_version>`. Örneğin, .NET Framework 4 veya 4.5 32-bit sürümünü. *, Windows yükleme dizini C:\Windows yol ise, `C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe`. 64-bit sürüm 4.5 veya .NET Framework 4. \*, varsayılan yol `C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe`.  
  
### <a name="to-uninstall-your-service-manually"></a>Hizmetinizi el ile kaldırmak için  
  
1.  Windows **Başlat** menüsü veya **Başlat** ekranında, seçin **Visual Studio**, **Visual Studio Araçları**, **Geliştirici Komut İstemi**.  
  
     Visual Studio komut istemi belirir.  
  
2.  InstallUtil.exe parametre olarak projenizin çıkış komut isteminden çalıştırın:  
  
    ```  
    installutil /u <yourproject>.exe  
    ```  
  
3.  Bazı durumlarda, hizmet yürütülebilir dosyası için bir hizmet silindikten sonra kayıt defterinde mevcut olabilir. Bu durumda, komutunu [sc delete](http://technet.microsoft.com/library/cc742045.aspx) girişi hizmeti için kayıt defterinden kaldırmak için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Hizmeti Uygulamalarına Giriş](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Nasıl Yapılır: Windows Hizmetleri Oluşturma](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 [Nasıl Yapılır: Hizmet Uygulamasına Yükleyiciler Ekleme](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [Installutil.exe (Yükleme Aracı)](../../../docs/framework/tools/installutil-exe-installer-tool.md)
