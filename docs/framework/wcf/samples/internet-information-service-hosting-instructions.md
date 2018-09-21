---
title: Internet Information Service Barındırma Yönergeleri
ms.date: 03/30/2017
ms.assetid: 959a21c8-9d9d-4757-b255-4e57793ae9d6
ms.openlocfilehash: 303fe47df987901b09cee8cc4292f12bcda2b74d
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46480701"
---
# <a name="internet-information-service-hosting-instructions"></a>Internet Information Service Barındırma Yönergeleri
Internet Information Services (IIS) tarafından barındırılan örnekleri çalıştırmak için IIS doğru bir şekilde yüklendiğinden ve çalıştığından emin olmanız gerekir.  
  
### <a name="to-install-iis-version-75-on-windows-server-2008-r2"></a>Windows Server 2008 R2'de IIS sürüm 7.5 yüklemek için  
  
1.  Gelen **Sunucu Yöneticisi'ni**seçin **rolleri.** Altında **rollerin özeti**, tıklayın **rolleri Ekle**.  
  
2.  Tıklayın **sonraki** görüntülenecek **Sunucu Rollerini Seç** iletişim.  
  
3.  Seçin **uygulama sunucusu** gelen **rolleri** listeleyin ve ardından **sonraki** iki kez görüntülenecek **rol hizmetlerini Seç** için iletişim kutusu Uygulama sunucusu rolü.  
  
4.  Seçin **Web sunucusu (IIS)** onay kutusu. Ek rol hizmetlerini ve özellikleri yükleme istenirse tıklayın **gereken özellikleri Ekle**. Tıklayın **sonraki** iki kez görüntülenecek **rol hizmetlerini Seç** Web sunucusu (IIS) rolü için iletişim.  
  
5.  Genişletin **Yönetim Araçları**ve ardından **IIS 6 Yönetim uyumluluğu**. Seçin **IIS 6 komut dosyası araçları**. Ek rol hizmetlerini ve özellikleri yükleme istenirse tıklayın **gerekli rol hizmetleri Ekle**. **İleri**'ye tıklayın.  
  
6.  Seçim Özeti doğruysa **yükleme**.  
  
7.  Yükleme tamamlandığında, tıklayın **Kapat**.  
  
### <a name="to-install-iis-version-75-on-windows-7"></a>Windows 7'de IIS sürüm 7.5 yüklemek için  
  
1.  Tıklayın **Başlat**ve ardından **Denetim Masası**.  
  
2.  Açık **programlar** grubu.  
  
3.  Altında **programlar ve Özellikler**, tıklayın **Windows özelliklerini aç veya Kapat**.  
  
4.  **Kullanıcı hesabı denetimi** iletişim kutusu görüntülenir. 
              **Devam**'a tıklayın.  
  
5.  **Windows özellikleri** iletişim kutusu görüntülenir. Öğeyi etiketli genişletin **Internet Information Services**.  
  
6.  Öğeyi etiketli genişletin **World Wide Web Hizmetleri**.  
  
7.  Öğeyi etiketli genişletin **uygulama geliştirme özellikleri**.  
  
8.  Aşağıdaki öğeler seçili olduğundan emin olun:  
  
    1.  **.NET genişletilebilirliği**  
  
    2.  **ASP.NET**  
  
    3.  **ISAPI Uzantıları**  
  
    4.  **ISAPI Filtreleri**  
  
9. Öğe altında etiketli **World Wide Web Hizmetleri**, genişletme **genel Http özellikleri**.  
  
10. Emin **statik içerik** seçilir.  
  
11. Öğe altında etiketli **World Wide Web Hizmetleri**, genişletme **güvenlik**.  
  
12. Emin olun **Windows kimlik doğrulaması** seçilir.  
  
13. Altında **Internet Information Services** dizine öğeyi etiketli genişletin **Web yönetimi araçları**ve ardından **IIS Yönetim Konsolu**.  
  
14. Öğeyi etiketli genişletin **IIS 6 Yönetim uyumluluğu**ve ardından **IIS 6 komut dosyası araçları**.  
  
15. Altında **Internet Information Services** dizine öğeyi etiketli genişletin **Microsoft .NET Framework 3.5.1**ve ardından **Windows Communication Foundation Http etkinleştirme**.  
  
16. **Tamam**'ı tıklatın.  
  
### <a name="to-install-iis-version-70-on-windows-server-2008"></a>Windows Server 2008'de IIS'in 7.0 sürümünü yüklemek için  
  
1.  Gelen **Sunucu Yöneticisi'ni**seçin **rolleri**. Altında **rollerin özeti**, tıklayın **rolleri Ekle**.  
  
2.  Tıklayın **sonraki** görüntülenecek **Sunucu Rollerini Seç** iletişim.  
  
3.  Seçin **uygulama sunucusu** gelen **rolleri** listeleyin ve ardından **sonraki** iki kez görüntülenecek **rol hizmetlerini Seç** için iletişim kutusu Uygulama sunucusu rolü.  
  
4.  Seçin **Web sunucusu (IIS)** onay kutusu. Ek rol hizmetlerini ve özellikleri yükleme istenirse tıklayın **gereken özellikleri Ekle**. Tıklayın **sonraki** iki kez görüntülenecek **rol hizmetlerini Seç** Web sunucusu (IIS) rolü için iletişim.  
  
5.  Genişletin **Yönetim Araçları**ve ardından **IIS 6 Yönetim uyumluluğu**. Seçin **IIS 6 komut dosyası araçları**. Ek rol hizmetlerini ve özellikleri yükleme istenirse tıklayın **gerekli rol hizmetleri Ekle**. **İleri**'ye tıklayın.  
  
6.  Seçim Özeti doğruysa **yükleme**.  
  
7.  Yükleme tamamlandığında, tıklayın **Kapat**.  
  
### <a name="to-install-iis-version-70-on-windows-vista"></a>Windows Vista'da IIS'in 7.0 sürümünü yüklemek için  
  
1.  Başlat'a tıklayın ve ardından Denetim Masası'nı tıklatın.  
  
2.  Seçin **programlar** grubu.  
  
3.  Altında **programlar ve Özellikler**, tıklayın **Windows özelliklerini aç veya Kapat**.  
  
4.  **Kullanıcı hesabı denetimi** iletişim kutusu görüntülenir. 
              **Devam**'a tıklayın.  
  
5.  **Windows özellikleri** iletişim kutusu görüntülenir. Öğeyi etiketli genişletin **Internet Information Services**.  
  
6.  Öğeyi etiketli genişletin **World Wide Web Hizmetleri**.  
  
7.  Öğeyi etiketli genişletin **uygulama geliştirme özellikleri**.  
  
8.  Aşağıdaki öğeler seçili olduğundan emin olun:  
  
    1.  **.NET genişletilebilirliği**  
  
    2.  **ASP.NET**  
  
    3.  **ISAPI Uzantıları**  
  
    4.  **ISAPI Filtreleri**  
  
9. Öğeyi etiketli genişletin **Web yönetimi araçları**ve ardından **IIS Yönetim Konsolu**.  
  
10. Öğe altında etiketli **World Wide Web Hizmetleri**, genişletme **genel Http özellikleri**.  
  
11. Emin **statik içerik** seçilir.  
  
12. Öğe altında etiketli **World Wide Web Hizmetleri**, genişletme **güvenlik**.  
  
13. Emin **Windows kimlik doğrulaması** seçilir.  
  
14. Öğeyi etiketli genişletin **IIS 6 Yönetim uyumluluğu**ve ardından **IIS 6 komut dosyası araçları**.  
  
15. Öğeyi etiketli genişletin **Microsoft .NET Framework 3.0**ve ardından **Windows Communication Foundation Http etkinleştirme**.  
  
16. **Tamam**'ı tıklatın.  
  
### <a name="to-install-iis-version-60-on-windows-server-2003"></a>Windows Server 2003'te IIS 6.0 sürümü yüklemek için  
  
1.  Gelen **sunucunuzu yönetin**, tıklayın **ekleme veya bir rolü kaldırma**ve ardından **sonraki**.  
  
2.  Seçin **uygulama sunucusu (IIS, ASP.NET)** gelen **sunucu rolü** listeleyin ve ardından **sonraki**.  
  
3.  Seçin **ASP** onay kutusunu işaretleyin ve ardından **sonraki**.  
  
4.  Seçim Özeti doğru ise, İleri'ye tıklayın.  
  
### <a name="to-install-iis-version-51-on-windows-xp-with-service-pack-2-and-service-pack-3-installed"></a>IIS 5.1 sürüm, Windows XP Service Pack 2 ve Service Pack 3'ü yüklemek için  
  
1.  Denetim Masası'nda tıklatın **Program Ekle veya Kaldır**.  
  
2.  İçinde **Program Ekle veya Kaldır** iletişim kutusu, tıklayın **Windows Bileşenlerini Ekle/Kaldır**.  
  
3.  İçinde **Windows Bileşenleri Sihirbazı'nı**seçin **Internet Information Services (IIS)** onay kutusunu işaretleyin ve ardından **sonraki**.  
  
4.  Varsa **gerekli dosyaları** iletişim kutusu görüntülenir, işletim sistemi yükleme diski takın, i386 klasöre göz atın ve ardından **Tamam**.  
  
5.  Yükleme tamamlandığında, tıklayın **son**.  
  
6.  Kapatma **Program Ekle veya Kaldır** iletişim kutusunu ve sonra close **Denetim Masası**.  
  
### <a name="to-verify-the-installation-of-iis-and-aspnet"></a>IIS ve ASP.NET yüklemesini doğrulamak için  
  
1.  HTML dosyasını Kaydet kök \InetPub\wwwroot dizininde bu konunun sonunda bulunan ve Default.aspx olarak adlandırın.  
  
2.  Bir tarayıcı penceresi açın.  
  
3.  Tür `http://localhost/Default.aspx` adres kutusuna ve ardından ENTER tuşuna basın.  
  
4.  "Hello World" metni ile bir Web sayfasında görünmesi gerekir.  
  
> [!NOTE]
>  Her seferinde yeni bir sürümünü yüklemek [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], aspnet_isapi bir Web hizmeti uzantısı IIS yeniden kaydetmeniz gerekir. Bunu yapmak için sorunu `aspnet_regiis –I –enable` komutu.  
  
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
