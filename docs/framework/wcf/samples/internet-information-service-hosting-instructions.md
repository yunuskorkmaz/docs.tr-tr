---
title: Internet Information Service Barındırma Yönergeleri
ms.date: 03/30/2017
ms.assetid: 959a21c8-9d9d-4757-b255-4e57793ae9d6
ms.openlocfilehash: 226b47bfd90dc4cffb0a364a804016043cc25d02
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929107"
---
# <a name="internet-information-service-hosting-instructions"></a>Internet Information Service Barındırma Yönergeleri
Internet Information Services (IIS) tarafından barındırılan örnekleri çalıştırmak için, IIS 'nin düzgün bir şekilde yüklendiğinden ve çalıştığından emin olmanız gerekir.  
  
### <a name="to-install-iis-version-75-on-windows-server-2008-r2"></a>Windows Server 2008 R2 'de IIS sürüm 7,5 ' ü yüklemek için  
  
1. **Sunucu Yöneticisi**, roller ' i seçin **.** **Roller Özeti**altında **Rol Ekle**' ye tıklayın.  
  
2. **İleri** ' ye tıklayarak **sunucu rollerini Seç** iletişim kutusunu görüntüleyin.  
  
3. **Roller** listesinden **uygulama sunucusu** ' nu seçin ve ardından iki kez **Ileri** ' ye tıklayarak uygulama sunucusu rolü için **rol hizmetlerini Seç** iletişim kutusunu görüntüleyin.  
  
4. **Web sunucusu (IIS)** onay kutusunu seçin. Ek rol hizmetleri ve özellikler yüklemek isteyip istemediğiniz sorulursa **gerekli özellikleri ekle**' ye tıklayın. Web sunucusu (IIS) rolü için **rol hizmetlerini Seç** iletişim kutusunu göstermek için Iki kez **İleri** ' ye tıklayın.  
  
5. **Yönetim Araçları**' nı genişletin ve ardından **IIS 6 Yönetim uyumluluğu**' nı genişletin. **IIS 6 komut dosyası araçları**' nı seçin. Ek rol hizmetleri ve özellikler yüklemek isteyip istemediğiniz sorulursa **gerekli rol hizmetleri Ekle**' ye tıklayın. **İleri**'ye tıklayın.  
  
6. Seçimlerin Özeti doğru ise, **yükler**' e tıklayın.  
  
7. Yükleme tamamlandığında **Kapat**' a tıklayın.  
  
### <a name="to-install-iis-version-75-on-windows-7"></a>Windows 7 ' ye IIS sürüm 7,5 yüklemek için  
  
1. **Başlat**' a ve ardından **Denetim Masası**' na tıklayın.  
  
2. **Programlar** grubunu açın.  
  
3. **Programlar ve Özellikler**altında, **Windows özelliklerini aç veya kapat**' a tıklayın.  
  
4. **Kullanıcı hesabı denetimi** iletişim kutusu görüntülenir. **Devam**'a tıklayın.  
  
5. **Windows özellikleri** iletişim kutusu görüntülenir. **Internet Information Services**etiketli öğeyi genişletin.  
  
6. **World Wide Web Services**etiketli öğeyi genişletin.  
  
7. **Uygulama geliştirme özellikleri**etiketli öğeyi genişletin.  
  
8. Aşağıdaki öğelerin seçildiğinden emin olun:  
  
    1. **.NET Genişletilebilirliği**  
  
    2. **ASP.NET**  
  
    3. **ISAPI Uzantıları**  
  
    4. **ISAPI Filtreleri**  
  
9. **World Wide Web Services**etiketli öğe altında **ortak http özellikleri**' ni genişletin.  
  
10. **Statik içeriğin** seçildiğinden emin olun.  
  
11. **World Wide Web Services**etiketli öğe altında **güvenlik**' i genişletin.  
  
12. **Windows kimlik doğrulamasının** seçili olduğundan emin olun.  
  
13. **Internet Information Services** dizininde, **Web yönetim araçları**etiketli öğeyi genişletin ve ardından **IIS Yönetim Konsolu**' nu seçin.  
  
14. **IIS 6 Yönetim uyumluluğu**etiketli öğeyi genişletin ve ardından **IIS 6 komut dosyası araçları**' nı seçin.  
  
15. **Internet Information Services** dizininde, **Microsoft .NET Framework 3.5.1**etiketli öğeyi genişletin ve ardından **http etkinleştirme Windows Communication Foundation**' yı seçin.  
  
16. **Tamam**'ı tıklatın.  
  
### <a name="to-install-iis-version-70-on-windows-server-2008"></a>Windows Server 2008 ' ye IIS 7,0 sürümünü yüklemek için  
  
1. **Sunucu Yöneticisi**, **Roller**' i seçin. **Roller Özeti**altında **Rol Ekle**' ye tıklayın.  
  
2. **İleri** ' ye tıklayarak **sunucu rollerini Seç** iletişim kutusunu görüntüleyin.  
  
3. **Roller** listesinden **uygulama sunucusu** ' nu seçin ve ardından iki kez **Ileri** ' ye tıklayarak uygulama sunucusu rolü için **rol hizmetlerini Seç** iletişim kutusunu görüntüleyin.  
  
4. **Web sunucusu (IIS)** onay kutusunu seçin. Ek rol hizmetleri ve özellikler yüklemek isteyip istemediğiniz sorulursa **gerekli özellikleri ekle**' ye tıklayın. Web sunucusu (IIS) rolü için **rol hizmetlerini Seç** iletişim kutusunu göstermek için Iki kez **İleri** ' ye tıklayın.  
  
5. **Yönetim Araçları**' nı genişletin ve ardından **IIS 6 Yönetim uyumluluğu**' nı genişletin. **IIS 6 komut dosyası araçları**' nı seçin. Ek rol hizmetleri ve özellikler yüklemek isteyip istemediğiniz sorulursa **gerekli rol hizmetleri Ekle**' ye tıklayın. **İleri**'ye tıklayın.  
  
6. Seçimlerin Özeti doğru ise, **yükler**' e tıklayın.  
  
7. Yükleme tamamlandığında **Kapat**' a tıklayın.  
  
### <a name="to-install-iis-version-70-on-windows-vista"></a>Windows Vista 'da IIS sürüm 7,0 ' ü yüklemek için  
  
1. Başlat ' a ve ardından Denetim Masası ' na tıklayın.  
  
2. **Programlar** grubunu seçin.  
  
3. **Programlar ve Özellikler**altında, **Windows özelliklerini aç veya kapat**' a tıklayın.  
  
4. **Kullanıcı hesabı denetimi** iletişim kutusu görüntülenir. **Devam**'a tıklayın.  
  
5. **Windows özellikleri** iletişim kutusu görüntülenir. **Internet Information Services**etiketli öğeyi genişletin.  
  
6. **World Wide Web Services**etiketli öğeyi genişletin.  
  
7. **Uygulama geliştirme özellikleri**etiketli öğeyi genişletin.  
  
8. Aşağıdaki öğelerin seçildiğinden emin olun:  
  
    1. **.NET Genişletilebilirliği**  
  
    2. **ASP.NET**  
  
    3. **ISAPI Uzantıları**  
  
    4. **ISAPI Filtreleri**  
  
9. **Web yönetimi araçları**etiketli öğeyi genişletin ve ardından **IIS Yönetim Konsolu**' nu seçin.  
  
10. **World Wide Web Services**etiketli öğe altında **ortak http özellikleri**' ni genişletin.  
  
11. **Statik içeriğin** seçildiğinden emin olun.  
  
12. **World Wide Web Services**etiketli öğe altında **güvenlik**' i genişletin.  
  
13. **Windows kimlik doğrulamasının** seçili olduğundan emin olun.  
  
14. **IIS 6 Yönetim uyumluluğu**etiketli öğeyi genişletin ve ardından **IIS 6 komut dosyası araçları**' nı seçin.  
  
15. **Microsoft .NET Framework 3,0**etiketli öğeyi genişletin ve sonra **Windows Communication Foundation HTTP etkinleştirmesi**' ni seçin.  
  
16. **Tamam**'ı tıklatın.  
  
### <a name="to-install-iis-version-60-on-windows-server-2003"></a>Windows Server 2003 ' ye IIS 6,0 sürümünü yüklemek için  
  
1. **Sunucunuzu Yönetin**' ten **bir rol Ekle veya Kaldır ' a**tıklayın ve ardından **İleri**' ye tıklayın.  
  
2. **Sunucu rolü** listesinden **uygulama sunucusu (IIS, ASP.net)** öğesini seçin ve ardından **İleri**' ye tıklayın.  
  
3. **ASP.net etkinleştir** onay kutusunu seçin ve ardından **İleri**' ye tıklayın.  
  
4. Seçimlerin Özeti doğru ise Ileri ' ye tıklayın.  
  
### <a name="to-install-iis-version-51-on-windows-xp-with-service-pack-2-and-service-pack-3-installed"></a>Service Pack 2 ve Service Pack 3 yüklü Windows XP 'de IIS sürüm 5,1 ' ü yüklemek için  
  
1. Denetim Masası 'nda **Program Ekle veya Kaldır**' a tıklayın.  
  
2. **Program Ekle veya Kaldır** Iletişim kutusunda **Windows Bileşenlerini Ekle/Kaldır**' a tıklayın.  
  
3. **Windows bileşenleri sihirbazında** **Internet Information Services (IIS)** onay kutusunu seçin ve ardından **İleri**' ye tıklayın.  
  
4. **Gerekli dosyalar** iletişim kutusu görüntülenirse, işletim sistemi yükleme diskinizi takın, i386 klasörüne gidin ve ardından **Tamam**' a tıklayın.  
  
5. Yükleme tamamlandığında **son**' a tıklayın.  
  
6. **Program Ekle veya Kaldır** iletişim kutusunu kapatın ve ardından **Denetim Masası**' nı kapatın.  
  
### <a name="to-verify-the-installation-of-iis-and-aspnet"></a>IIS ve ASP.NET 'in yüklenmesini doğrulamak için  
  
1. Bu konunun sonunda bulunan HTML dosyasını kök \Inetpub\Wwwroot dizinine kaydedin ve default. aspx olarak adlandırın.  
  
2. Bir tarayıcı penceresi açın.  
  
3. Adres `http://localhost/Default.aspx` kutusuna yazın ve ENTER tuşuna basın.  
  
4. "Merhaba Dünya" metnine sahip bir Web sayfası görünmelidir.  
  
> [!NOTE]
> .NET Framework yeni bir sürümünü her yüklediğinizde, aspnet_isapi IIS için bir Web hizmeti uzantısı olarak yeniden kaydolmanız gerekir. Bunu yapmak için `aspnet_regiis –I –enable` komutunu verin.  
  
## <a name="sample-code"></a>Örnek Kod  
  
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
