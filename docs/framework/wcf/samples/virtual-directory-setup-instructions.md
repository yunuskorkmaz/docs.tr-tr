---
title: Sanal Dizin Ayarlama Yönergeleri
ms.date: 03/30/2017
ms.assetid: 3c62cab5-81a4-48b6-ac8c-9ce33a85a157
ms.openlocfilehash: fdff88026a49989870ee5c47f9a38a65ecad3c80
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59325351"
---
# <a name="virtual-directory-setup-instructions"></a>Sanal Dizin Ayarlama Yönergeleri
Windows Communication Foundation (WCF) örnekleri %SystemDrive%\inetpub\wwwroot\servicemodelsamples klasörle eşlendi servicemodelsamples adlı ortak bir sanal dizin paylaşmak için tasarlanmıştır.  
  
> [!NOTE]
>  % SYSTEMDRIVE % genellikle C: veya D:, Internet Information Services (IIS) yüklü olduğu sürücü bağlı olarak konumudur.  
  
 Setupvroot.bat ve Cleanupvroot.bat dosyalarından çalıştırabileceğiniz [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) sanal dizin oluşturmak için. Sanal dizin el ile oluşturmak isterseniz, aşağıdaki yordamları kullanın.  
  
## <a name="procedures"></a>Yordamlar  
  
#### <a name="to-create-a-virtual-directory-in-iis-70-or-75"></a>IIS 7.0 veya 7.5 bir sanal dizin oluşturmak için  
  
1. Gelen **Başlat** menüsünde, tıklayın **çalıştırın**, yazın **inetmgr** Internet Information Services (IIS) MMC ek bileşenini açın.  
  
2. Sol bölmede, bilgisayarın adını içeren düğüme genişletin ve ardından **siteleri** düğümü.  
  
3. Sağ **varsayılan Web sitesi**ve ardından **uygulama Ekle** açmak için **uygulama Ekle penceresi**.  
  
4. Penceresinde `servicemodelsamples` oluşturmakta olduğunuz sanal dizin için diğer ad olarak.  
  
5. Şu dizin oluşturma: %SystemDrive%\inetpub\wwwroot\servicemodelsamples  
  
6. % SystemDrive%\inetpub\wwwroot\servicemodelsamples fiziksel yolunu ayarlayın.  WCF örnekleri çoğu hizmet yürütülebilir dosya oluşturulduğunda bu konuma kopyalayın.  
  
7. **Tamam**'ı tıklatın. Web uygulaması WCF örnekleri için oluşturuldu.  
  
    > [!NOTE]
    >  Tüm WCF örnekleri aynı servicemodelsamples Web uygulamasını kullanmak için bu görevi yalnızca bir kez gerçekleştirilmesi gerekir.  
  
    > [!NOTE]
    >  Bu belge, amacıyla terimi `virtual directory` ile eşanlamlıdır `Web application`.  
  
     Sanal dizin oluşturmaya ek olarak, WCF hizmetlerini çalıştırmak için etkinleştirmek için özelliklerini de ayarlamanız gerekir. Ayrıntılar için aşağıya bakın.  
  
#### <a name="to-create-a-virtual-directory-in-iis-51-or-60"></a>IIS 5.1 veya 6.0 sanal bir dizin oluşturmak için  
  
1. Bir komut istemi penceresi açıp `start inetmgr` Internet Information Services (IIS) MMC ek bileşenini açın.  
  
2. Sol bölmede, bilgisayarın adını içeren düğüme genişletin ve ardından **Web siteleri** düğümü.  
  
3. Sağ **varsayılan Web sitesi** seçip **yeni sanal dizin** sanal dizin oluşturma Sihirbazı'nı açın.  
  
4. Sihirbazı'nda yazın `servicemodelsamples` oluşturmakta olduğunuz sanal dizin için diğer ad olarak.  
  
5. % SystemDrive%\inetpub\wwwroot\servicemodelsamples yolunu ayarlayın. WCF örnekleri çoğu hizmet yürütülebilir dosya oluşturulduğunda bu konuma kopyalayın.  
  
6. **İleri**'ye tıklayın.  
  
7. Varsayılan olarak, aşağıdaki onay kutularını seçilir:  
  
    -   **Read**  
  
    -   **Komut dosyalarını (örn. ASP) Çalıştır**  
  
8. Tıklayın **sonraki**ve ardından **son** Sihirbazı tamamlayın.  
  
    > [!NOTE]
    >  Tüm WCF örnekleri aynı servicemodelsamples sanal dizinin kullandığı için bu görevi yalnızca bir kez gerçekleştirilmesi gerekir.  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-70-or-75"></a>Ek sanal dizin özelliklerini IIS 7.0 veya 7.5 ayarlamak için  
  
1. Servicemodelsamples düğümünü tıklatın. Pencerenin altındaki iki görünüm listelenir. Seçin **özellikler görünümü** zaten seçili değilse.  
  
2. Girişini çift **Dizin tarama**.  
  
3. Eylemler bölmesinde seçin **etkinleştirme** seçeneği. Bu, dizini dizinin bir hizmetinde hata ayıklarken yardımcı olan Internet Explorer'ı kullanarak erişmenize olanak sağlar.  
  
 Son olarak, güvenlik özellikleri servicemodelsamples klasörün başkaları tarafından erişilmesine izin verecek şekilde ayarlamanız gerekir. Ayrıntılar için aşağıya bakın.  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-51-or-60"></a>Ek sanal dizini IIS 5.1 özelliklerinde veya 6. 0'ı ayarlamak için  
  
1. Servicemodelsamples düğümüne sağ tıklayın ve ardından **özellikleri**.  
  
2. Varsayılan olarak, aşağıdaki onay kutularını seçilir:  
  
    -   **Read**  
  
    -   **Günlük ziyaret eder.**  
  
    -   **Bu kaynağı dizine Ekle**  
  
3. Seçin **Dizin tarama** onay kutusu. Bu, dizini dizinin bir hizmetinde hata ayıklarken yardımcı olan Internet Explorer'ı kullanarak erişmenize olanak sağlar.  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-70-or-75"></a>IIS 7.0 veya 7.5 klasör güvenlik özelliklerini ayarlamak için  
  
1. % SystemDrive%\inetpub\wwwroot\servicemodelsamples için gidin.  
  
2. Servicemodelsamples klasörü sağ tıklatıp **paylaşımı** veya **paylaşımı ile**.  
  
3. Solundaki aşağı oka tıklayın **Ekle** düğmesi.  
  
4. Seçin **Bul** girişi. **Kullanıcıları veya Grupları Seç** penceresi açılır.  
  
5. **Gelişmiş**'e tıklayın.  
  
6. Tıklayın **konumları**. **Konumları** penceresi açıksa artık.  
  
7. Kullanılan bilgisayar girişini seçin. Yerel bilgisayar ve bir giriş değil herhangi bir etki alanı veya listelenen ağları seçmek önemlidir. Bilgisayar seçildikten sonra tıklayın **Tamam**.  
  
8. Tıklayın **Şimdi Bul**. Bu, arama sonuçlarını yerel bilgisayarla ilişkili nesneleri ile doldurur.  
  
9. Bulma **IIS_IUSRS** girişi **adı (göreli ayırt edici adı)** sütun. Bu girdiyi seçin ve tıklayın **Tamam** sonuçları penceresini aramayı kapatın.  
  
10. Tıklayın **Tamam** kapatmak için **kullanıcıları veya Grupları Seç** penceresi.  
  
11. Tıklayın **paylaşımı** değişiklikleri kalıcı hale getirmek için.  
  
12. Paylaşmayı etkinleştirmek için değişiklik tamamlandıktan sonra tıklayın **Bitti** kapatmak için **dosya paylaşımı** penceresi.  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-51-or-60"></a>IIS 5.1 veya 6.0 klasör güvenlik özelliklerini ayarlamak için  
  
1. % SystemDrive%\inetpub\wwwroot\servicemodelsamples için gidin.  
  
2. Sağ **servicemodelsamples** klasörünü ve ardından **paylaşım ve güvenlik.**  
  
3. Tıklayın **güvenlik** sekmesi.  
  
4. IIS 6. 0'da, içinde kullanıyorsanız **grup veya kullanıcı adları** onay kutusuna olup olmadığını **Internet Konuk hesabı** listelenir.  
  
     Bu listede yoksa:  
  
    1.  Tıklayın **Başlat** ve ardından **Denetim Masası**.  
  
    2.  Görmüyorsanız, **kullanıcı hesaplarını** simgesini tıklayın **kategori görünümüne geçiş**.  
  
    3.  Tıklayın **kullanıcı hesaplarını** simgesi.  
  
    4.  Altında "veya bir Denetim Masası simgesi seçin" tıklayın **kullanıcı hesaplarını**.  
  
    5.  İçinde **kullanıcı hesaplarını** iletişim kutusu, tıklayın **Gelişmiş** sekmesi.  
  
    6.  **Gelişmiş**'e tıklayın.  
  
    7.  İçinde **yerel kullanıcılar ve gruplar** iletişim kutusu, genişletmek için tıklatın **kullanıcılar** klasör.  
  
    8.  Sağ bölmede **Internet Konuk hesabı**.  
  
    9. İçinde **özellikleri** iletişim kutusu, kopyalama Internet Konuk hesabı olarak kullanılan adı. Varsayılan olarak, adı "USR_ bilgisayar adından" ile başlar.  
  
    10. **Özellikler** iletişim kutusunu kapatın.  
  
    11. Kapat **yerel kullanıcılar ve gruplar** iletişim kutusu.  
  
    12. Kapat **kullanıcı hesaplarını** iletişim kutusu.  
  
    13. Diğer kapatmak **kullanıcı hesaplarını** iletişim kutusu.  
  
    14. İçinde **servicemodelsamples özellikleri** iletişim kutusundaki **güvenlik** sekmesinde **Ekle**.  
  
    15. Ardından bir eğik bilgisayarın adını yazın ve ardından Internet kullanıcı hesabı, örneğin, myMachineName adını yapıştırın\\InternetGuestAccountName %  
  
    16. Tıklayın **Adları Denetle** eklemeyi doğrulamak için. Geçerliyse, adı tamamı büyük harf olduğundan çizilir.  
  
5. IIS 6.0 için Ayrıca ağ hizmeti listelendiğini kontrol **grup veya kullanıcı adları** kutusu.  
  
     Ağ hizmeti listede yoksa:  
  
    1.  **Ekle**'yi tıklatın.  
  
    2.  İçinde **kullanıcıları veya Grupları Seç** iletişim kutusuna bir ters eğik çizgi ardından bilgisayar adı.  
  
    3.  Tür **hizmet** sonra ters eğik çizgi (boşluksuz).  
  
    4.  Tıklayın **Adları Denetle**.  
  
    5.  Birden fazla adı bulunursa seçip **ağ hizmeti** tıklatıp **Tamam**.  
  
    6.  Tıklayın **Tamam** kapatmak için **kullanıcıları veya Grupları Seç** iletişim kutusu.  
  
6. IIS 5.1 ile Windows XP SP2 kullanıyorsanız, hem Internet Konuk hesabı hem de ASP.NET listelendiğini kontrol **grup veya kullanıcı adları** kutusu.  
  
     ASP.NET kullanıcı yerleşik üyesi olabileceğini unutmayın **kullanıcılar** güvenlik grubu. Bu durumda, sonra eğer **kullanıcılar** Grup iletişim kutusunda listelenen, izin verilen kullanıcıların listesi için ayrı bir öğe olarak eklemeniz gerekmez.  
  
     ASP.NET parçası olup olmadığını denetlemek için **kullanıcılar** güvenlik grubu:  
  
    1.  Üzerinde **Başlat** menüsünde tıklatın **Denetim Masası**.  
  
    2.  Tıklayın **kullanıcı hesaplarını** simgesi.  
  
    3.  İçinde **grubu** sütun kontrol değeri **ASPNET** "kullanıcıları."  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Internet Information Service Barındırma Yönergeleri](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)
