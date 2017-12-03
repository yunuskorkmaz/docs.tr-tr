---
title: "Internet Information Service Barındırma Yönergeleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 959a21c8-9d9d-4757-b255-4e57793ae9d6
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7dd9d70a3b93faf721b5ac3bbd5f1114bf5c1461
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="internet-information-service-hosting-instructions"></a>Internet Information Service Barındırma Yönergeleri
Internet Information Services (IIS) tarafından barındırılan örnekleri çalıştırmak için IIS düzgün yüklendiğinden ve çalıştığından emin olmanız gerekir.  
  
### <a name="to-install-iis-version-75-on-windows-server-2008-r2"></a>Windows Server 2008 R2'de IIS sürüm 7.5 yüklemek için  
  
1.  Gelen **Sunucu Yöneticisi'ni**seçin **rolleri.** Altında **Rol Özeti**, tıklatın **rolleri Ekle**.  
  
2.  Tıklatın **sonraki** görüntülemek için **Sunucu Rollerini Seç** iletişim.  
  
3.  Seçin **uygulama sunucusu** gelen **rolleri** listeleyin ve ardından **sonraki** iki kez görüntülenecek **rol hizmetlerini Seç** için iletişim kutusu Uygulama sunucusu rolü.  
  
4.  Seçin **Web sunucusu (IIS)** onay kutusu. Ek rol hizmetlerini ve özellikleri yükleme istenirse tıklatın **gereken özellikleri Ekle**. Tıklatın **sonraki** iki kez görüntülenecek **rol hizmetlerini Seç** Web sunucusu (IIS) rolü için iletişim kutusu.  
  
5.  Genişletme **Yönetim Araçları**, genişletin ve ardından **IIS 6 Yönetim uyumluluğu**. Seçin **IIS 6 komut dosyası araçları**. Ek rol hizmetlerini ve özellikleri yükleme istenirse tıklatın **gereken rol hizmetlerini Ekle**. 
              **İleri**'ye tıklayın.  
  
6.  Seçim Özeti doğru ise, tıklatın **yükleme**.  
  
7.  Yükleme tamamlandığında tıklayın **Kapat**.  
  
### <a name="to-install-iis-version-75-on-windows-7"></a>IIS sürüm 7.5 Windows 7 yüklemek için  
  
1.  Tıklatın **Başlat**ve ardından **Denetim Masası**.  
  
2.  Açık **programları** grubu.  
  
3.  Altında **programlar ve Özellikler**, tıklatın **Windows özelliklerini aç veya Kapat**.  
  
4.  **Kullanıcı hesabı denetimi** iletişim kutusu gösterilir. 
              **Devam**'a tıklayın.  
  
5.  **Windows özelliklerini** iletişim kutusu gösterilir. Öğesi etiketli genişletin **Internet Information Services**.  
  
6.  Öğesi etiketli genişletin **World Wide Web Hizmetleri**.  
  
7.  Öğesi etiketli genişletin **uygulama geliştirme özellikleri**.  
  
8.  Aşağıdaki öğeler seçili olduğundan emin olun:  
  
    1.  **.NET genişletilebilirliği**  
  
    2.  **ASP.NET**  
  
    3.  **ISAPI Uzantıları**  
  
    4.  **ISAPI Filtreleri**  
  
9. Öğe altında etiketli **World Wide Web Hizmetleri**, genişletin **ortak Http özellikleri**.  
  
10. Emin olun **statik içerik** seçilir.  
  
11. Öğe altında etiketli **World Wide Web Hizmetleri**, genişletin **güvenlik**.  
  
12. Olduğundan emin olun **Windows kimlik doğrulaması** seçilir.  
  
13. Altında **Internet Information Services** dizin öğesi etiketli genişletin **Web yönetimi araçları**ve ardından **IIS Yönetim Konsolu**.  
  
14. Öğesi etiketli genişletin **IIS 6 Yönetim uyumluluğu**ve ardından **IIS 6 komut dosyası araçları**.  
  
15. Altında **Internet Information Services** dizin öğesi etiketli genişletin **Microsoft .NET Framework 3.5.1**ve ardından **Windows Communication Foundation Http etkinleştirmesi**.  
  
16. **Tamam**'ı tıklatın.  
  
### <a name="to-install-iis-version-70-on-windows-server-2008"></a>Windows Server 2008'de IIS 7.0 sürümünü yüklemek için  
  
1.  Gelen **Sunucu Yöneticisi'ni**seçin **rolleri**. Altında **Rol Özeti**, tıklatın **rolleri Ekle**.  
  
2.  Tıklatın **sonraki** görüntülemek için **Sunucu Rollerini Seç** iletişim.  
  
3.  Seçin **uygulama sunucusu** gelen **rolleri** listeleyin ve ardından **sonraki** iki kez görüntülenecek **rol hizmetlerini Seç** için iletişim kutusu Uygulama sunucusu rolü.  
  
4.  Seçin **Web sunucusu (IIS)** onay kutusu. Ek rol hizmetlerini ve özellikleri yükleme istenirse tıklatın **gereken özellikleri Ekle**. Tıklatın **sonraki** iki kez görüntülenecek **rol hizmetlerini Seç** Web sunucusu (IIS) rolü için iletişim kutusu.  
  
5.  Genişletme **Yönetim Araçları**, genişletin ve ardından **IIS 6 Yönetim uyumluluğu**. Seçin **IIS 6 komut dosyası araçları**. Ek rol hizmetlerini ve özellikleri yükleme istenirse tıklatın **gereken rol hizmetlerini Ekle**. 
              **İleri**'ye tıklayın.  
  
6.  Seçim Özeti doğru ise, tıklatın **yükleme**.  
  
7.  Yükleme tamamlandığında tıklayın **Kapat**.  
  
### <a name="to-install-iis-version-70-on-windows-vista"></a>Windows Vista'da IIS'in 7.0 sürümünü yüklemek için  
  
1.  Başlat'ı tıklatın ve ardından Denetim Masası'nı tıklatın.  
  
2.  Seçin **programları** grubu.  
  
3.  Altında **programlar ve Özellikler**, tıklatın **Windows özelliklerini aç veya Kapat**.  
  
4.  **Kullanıcı hesabı denetimi** iletişim kutusu gösterilir. 
              **Devam**'a tıklayın.  
  
5.  **Windows özelliklerini** iletişim kutusu gösterilir. Öğesi etiketli genişletin **Internet Information Services**.  
  
6.  Öğesi etiketli genişletin **World Wide Web Hizmetleri**.  
  
7.  Öğesi etiketli genişletin **uygulama geliştirme özellikleri**.  
  
8.  Aşağıdaki öğeler seçili olduğundan emin olun:  
  
    1.  **.NET genişletilebilirliği**  
  
    2.  **ASP.NET**  
  
    3.  **ISAPI Uzantıları**  
  
    4.  **ISAPI Filtreleri**  
  
9. Öğesi etiketli genişletin **Web yönetimi araçları**ve ardından **IIS Yönetim Konsolu**.  
  
10. Öğe altında etiketli **World Wide Web Hizmetleri**, genişletin **ortak Http özellikleri**.  
  
11. Emin olun **statik içerik** seçilir.  
  
12. Öğe altında etiketli **World Wide Web Hizmetleri**, genişletin **güvenlik**.  
  
13. Emin olun **Windows kimlik doğrulaması** seçilir.  
  
14. Öğesi etiketli genişletin **IIS 6 Yönetim uyumluluğu**ve ardından **IIS 6 komut dosyası araçları**.  
  
15. Öğesi etiketli genişletin **Microsoft .NET Framework 3.0**ve ardından **Windows Communication Foundation Http etkinleştirmesi**.  
  
16. Tıklatın**Tamam**.  
  
### <a name="to-install-iis-version-60-on-windows-server-2003"></a>IIS sürüm 6.0 Windows Server 2003'te yüklemek için  
  
1.  Gelen **sunucunuzu yönetin**, tıklatın **ekleme veya kaldırma rol**ve ardından **sonraki**.  
  
2.  Seçin **uygulama sunucusu (IIS, ASP.NET)** gelen **sunucu rolü** listeleyin ve ardından **sonraki**.  
  
3.  Seçin **ASP** onay kutusunu işaretleyin ve ardından **sonraki**.  
  
4.  Seçim Özeti doğru ise, İleri'yi tıklatın.  
  
### <a name="to-install-iis-version-51-on-windows-xp-with-service-pack-2-and-service-pack-3-installed"></a>IIS sürüm 5.1, Windows XP Service Pack 2 ve Service Pack 3'ü yüklemek için  
  
1.  Denetim Masası'nda tıklatın **Program Ekle veya Kaldır**.  
  
2.  İçinde **Program Ekle veya Kaldır** iletişim kutusu, tıklatın **Windows Bileşenlerini Ekle/Kaldır**.  
  
3.  İçinde **Windows Bileşenleri Sihirbazı'nı**seçin **Internet Information Services (IIS)** onay kutusunu işaretleyin ve ardından **sonraki**.  
  
4.  Varsa **gerekli dosyaları** iletişim kutusu görüntülenir, işletim sistemi yükleme diski takın, i386 klasörüne göz atın ve ardından **Tamam**.  
  
5.  Yükleme tamamlandığında tıklayın **son**.  
  
6.  Kapat **Program Ekle veya Kaldır** iletişim kutusunu ve ardından Kapat **Denetim Masası**.  
  
### <a name="to-verify-the-installation-of-iis-and-aspnet"></a>IIS ve ASP.NET yüklemesini doğrulamak için  
  
1.  HTML dosyasını Kaydet kök \InetPub\wwwroot dizinini bu konudaki sonunda bulunan ve Default.aspx adlandırın.  
  
2.  Bir tarayıcı penceresi açın.  
  
3.  Tür `http://localhost/Default.aspx` adresi kutusunda ve ENTER tuşuna BASIN.  
  
4.  "Hello World" metni ile bir Web sayfasında görünmesi gerekir.  
  
> [!NOTE]
>  Her zaman yeni bir sürümünü yüklemek [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], aspnet_isapi bir Web hizmeti uzantısı olarak IIS için yeniden kaydetmeniz gerekir. Bunu yapmak için sorunu `aspnet_regiis –I –enable` komutu.  
  
## <a name="sample-code"></a>Örnek kod  
  
```xml  
<html>  
   <body>  
       <form >  
           <h3> Hello World  
           </h3>  
       </form>  
   </body>  
</html>  
```
