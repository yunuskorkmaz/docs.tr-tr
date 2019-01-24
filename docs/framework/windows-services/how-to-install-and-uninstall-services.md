---
title: 'Nasıl yapılır: Hizmetleri Yükleme ve kaldırma'
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
ms.openlocfilehash: eab291528080b75a07c8f8c3994428eafde94568
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54612823"
---
# <a name="how-to-install-and-uninstall-services"></a>Nasıl yapılır: Hizmetleri Yükleme ve kaldırma
.NET Framework kullanarak bir Windows hizmet geliştiriyorsanız, InstallUtil.exe adlı bir komut satırı yardımcı programını kullanarak hizmet uygulamanızı hızlı bir şekilde yükleyebilirsiniz. Kullanıcılar yükleme ve kaldırma, Windows hizmet yayımlamayı isteyen bir geliştiriciyseniz InstallShield kullanmanız gerekir. Bkz: [Windows Installer dağıtımı](https://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0).  
  
> [!WARNING]
>  Bir hizmeti bilgisayarınızdan kaldırmak istiyorsanız, bu makaledeki adımları izlemeyin. Bunun yerine, hangi program veya yazılım paketinin yüklü kullanıma hizmeti bulun ve ardından **Program Ekle/Kaldır** Denetim Masası'nın bu programı kaldırın. Birçok hizmet Windows ayrılmaz olduğunu unutmayın; bunları kaldırırsanız, sistem kararsızlığına neden olabilir.  
  
 Bu makaledeki adımları kullanabilmek için önce Windows hizmetinizin hizmet yükleyici eklemeniz gerekir. Bkz: [izlenecek yol: Oluşturma bir Windows hizmet uygulaması Bileşen Tasarımcısı'nda](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).  
  
 Windows Service projeleri F5 tuşuna basarak doğrudan Visual Studio geliştirme ortamından çalıştırılamaz. Projenin çalışabilmesi için projedeki hizmetin yüklenmiş olması gerekliliğinden budur.  
  
> [!TIP]
>  Başlatabilirsiniz **Sunucu Gezgini** ve hizmetinizi yüklü veya kaldırılmış olduğunu doğrulayın. Daha fazla bilgi için bkz: nasıl yapılır: Erişim ve Sunucu Gezgini veritabanı Gezgini başlatılamıyor.  
  
### <a name="to-install-your-service-manually"></a>Hizmetinizi el ile yüklemek için  
  
1.  Windows üzerinde **Başlat** menüsü veya **Başlat** ekran öğesini **Visual Studio** , **Visual Studio Araçları**, **Geliştirici Komut İstemi**.  
  
     Visual Studio için geliştirici komut istemi görünür.  
  
2.  Projenizin derlenmiş çalıştırılabilir dosyasının bulunduğu dizine erişin.  
  
3.  InstallUtil.exe parametre olarak projenizin yürütülebilir dosya ile komut isteminden çalıştırın:  
  
    ```  
    installutil <yourproject>.exe  
    ```  
  
     Visual Studio için geliştirici komut istemi kullanıyorsanız, InstallUtil.exe sistem yolunda olmalıdır. Aksi halde yola ekleyin veya onu çağırmak için tam yolu kullanın. Bu araç .NET Framework ile birlikte yüklenir ve kendi yolu `%WINDIR%\Microsoft.NET\Framework[64]\<framework_version>`. Örneğin, .NET Framework 4 veya 4.5 32-bit sürümü için. *, Windows yükleme dizinine C:\Windows yol ise, `C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe`. 64-bit sürümü .NET Framework 4 veya 4.5 için. \*, varsayılan yolu `C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe`.  
  
### <a name="to-uninstall-your-service-manually"></a>Hizmetinizi el ile kaldırmak için  
  
1.  Windows üzerinde **Başlat** menüsü veya **Başlat** ekran öğesini **Visual Studio**, **Visual Studio Araçları**, **Geliştirici Komut İstemi**.  
  
     Visual Studio için geliştirici komut istemi görünür.  
  
2.  InstallUtil.exe parametre olarak projenizin çıktısı ile komut isteminden çalıştırın:  
  
    ```  
    installutil /u <yourproject>.exe  
    ```  
  
3.  Bazı durumlarda, hizmetin yürütülebilir dosya için bir hizmet silindikten sonra kayıt defterinde mevcut olabilir. Bu durumda, komutunu [sc delete](/windows-server/administration/windows-commands/sc-delete) kayıt defterinden service girişini kaldırmak için.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Windows Hizmeti Uygulamalarına Giriş](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [Nasıl yapılır: Windows Hizmetleri oluşturma](../../../docs/framework/windows-services/how-to-create-windows-services.md)
- [Nasıl yapılır: Hizmet uygulamasına yükleyiciler ekleme](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)
- [Installutil.exe (Yükleme Aracı)](../../../docs/framework/tools/installutil-exe-installer-tool.md)
