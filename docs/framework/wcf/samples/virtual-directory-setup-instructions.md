---
title: "Sanal Dizin Ayarlama Yönergeleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3c62cab5-81a4-48b6-ac8c-9ce33a85a157
caps.latest.revision: "36"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b727f391abfeb1112de1b6cde3ceb564d3860974
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="virtual-directory-setup-instructions"></a>Sanal Dizin Ayarlama Yönergeleri
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Örnekleri %SystemDrive%\inetpub\wwwroot\servicemodelsamples klasörüne eşlenmiş servicemodelsamples adlı ortak bir sanal dizini paylaşmak için yöneliktir.  
  
> [!NOTE]
>  % SYSTEMDRIVE % genellikle C: veya D:, Internet Information Services (IIS) yüklü olduğu sürücü bağlı olarak konumudur.  
  
 Setupvroot.bat ve Cleanupvroot.bat dosyalarından çalıştırabilirsiniz [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) sanal dizin oluşturulamıyor. Sanal dizin el ile oluşturmayı tercih ederseniz, aşağıdaki yordamları kullanın.  
  
## <a name="procedures"></a>Yordamlar  
  
#### <a name="to-create-a-virtual-directory-in-iis-70-or-75"></a>IIS 7.0 veya 7.5 bir sanal dizin oluşturmak için  
  
1.  Gelen **Başlat** menüsünde tıklatın **çalıştırmak**, yazın **inetmgr** Internet Information Services (IIS) MMC ek bileşenini açmak için.  
  
2.  Sol bölmede, bilgisayarın adıyla düğümünü genişletin ve ardından **siteleri** düğümü.  
  
3.  Sağ **varsayılan Web sitesi**ve ardından **uygulama Ekle** açmak için **uygulama Ekle penceresi**.  
  
4.  Penceresinde yazın `servicemodelsamples` oluşturmakta olduğunuz sanal dizin için diğer ad olarak.  
  
5.  Şu dizin oluşturulamıyor: %SystemDrive%\inetpub\wwwroot\servicemodelsamples  
  
6.  Fiziksel yolu % SystemDrive%\inetpub\wwwroot\servicemodelsamples ayarlayın.  WCF örnekleri çoğu hizmeti yürütülebilir dosyaları yapılandırıldığında bu konuma kopyalayın.  
  
7.  **Tamam**'ı tıklatın. Web uygulaması şimdi WCF örnekleri oluşturulur.  
  
    > [!NOTE]
    >  Bu görevi yalnızca bir kez, çünkü gerçekleştirilmesi gereken tüm [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] örnekleri aynı servicemodelsamples Web uygulaması kullanın.  
  
    > [!NOTE]
    >  Bu belge, amacıyla terimi `virtual directory` ile çalışır `Web application`.  
  
     Sanal dizin oluşturmaya ek olarak, özelliklerini etkinleştirmek için de ayarlamalısınız [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] çalıştırmak için hizmetleri. Ayrıntılar için aşağıya bakın.  
  
#### <a name="to-create-a-virtual-directory-in-iis-51-or-60"></a>IIS 5.1 veya 6.0 bir sanal dizin oluşturmak için  
  
1.  Bir komut istemi penceresi açıp `start inetmgr` Internet Information Services (IIS) MMC ek bileşenini açın.  
  
2.  Sol bölmede, bilgisayarın adıyla düğümünü genişletin ve ardından **Web siteleri** düğümü.  
  
3.  Sağ **varsayılan Web sitesi** seçip **yeni, sanal dizin** sanal dizin oluşturma Sihirbazı'nı açın.  
  
4.  Sihirbazı'nda yazın `servicemodelsamples` oluşturmakta olduğunuz sanal dizin için diğer ad olarak.  
  
5.  Yolun % SystemDrive%\inetpub\wwwroot\servicemodelsamples ayarlayın. Çoğu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] örnekleri hizmeti yürütülebilir dosyaları yapılandırıldığında bu konuma kopyalayın.  
  
6.  
              **İleri**'ye tıklayın.  
  
7.  Varsayılan olarak, aşağıdaki onay kutularını seçilir:  
  
    -   **Okuma**  
  
    -   **(Örneğin, ASP) komut dosyalarını çalıştır**  
  
8.  Tıklatın **sonraki**ve ardından **son** Sihirbazı tamamlayın.  
  
    > [!NOTE]
    >  Bu görevi yalnızca bir kez çünkü gerçekleştirilmesi gereken tüm [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] örnekleri aynı servicemodelsamples sanal dizini kullanır.  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-70-or-75"></a>Ek sanal dizin özellikleri IIS 7.0 veya 7.5 ayarlamak için  
  
1.  Servicemodelsamples düğümünü tıklatın. Pencerenin altındaki iki görünüm listelenir. Seçin **özellikler görünümü** zaten seçili değilse.  
  
2.  İçin girişi çift **Dizin tarama**.  
  
3.  Eylemler bölmesinde seçin **etkinleştirmek** seçeneği. Bu, bir hizmet hata ayıklama sırasında yardımcı olan Internet Explorer kullanarak dizininin dizin erişmenize olanak tanır.  
  
 Son olarak, başkaları tarafından erişilebilmesi izin vermek için servicemodelsamples klasörün güvenlik özelliklerini ayarlamanız gerekir. Ayrıntılar için aşağıya bakın.  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-51-or-60"></a>IIS 5.1 ek sanal dizin özelliklerinde veya 6.0 ayarlamak için  
  
1.  Servicemodelsamples düğümünü sağ tıklatın ve ardından **özellikleri**.  
  
2.  Varsayılan olarak, aşağıdaki onay kutularını seçilir:  
  
    -   **Okuma**  
  
    -   **Ziyaretleri günlüğe yaz**  
  
    -   **Bu kaynak dizini**  
  
3.  Seçin **Dizin tarama** onay kutusu. Bu, bir hizmet hata ayıklama sırasında yardımcı olan Internet Explorer kullanarak dizininin dizin erişmenize olanak tanır.  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-70-or-75"></a>IIS 7.0 veya 7.5 klasörü güvenlik özelliklerini ayarlamak için  
  
1.  % SystemDrive%\inetpub\wwwroot\servicemodelsamples gidin.  
  
2.  Servicemodelsamples klasörü sağ tıklatın ve **paylaşımı** veya **paylaşımı ile**.  
  
3.  Sol tarafındaki aşağı oka tıklayın **Ekle** düğmesi.  
  
4.  Seçin **Bul** girişi. **Kullanıcıları veya Grupları Seç** penceresi açılır.  
  
5.  **Gelişmiş**'e tıklayın.  
  
6.  Tıklatın **konumları**. **Konumları** penceredir artık açık.  
  
7.  Kullanılan bilgisayar girişini seçin. Yerel bilgisayar ve bir giriş değil tüm etki alanları veya listelenen ağları seçmek önemlidir. Bilgisayar seçildikten sonra tıklayın **Tamam**.  
  
8.  Tıklatın **Şimdi Bul**. Bu, arama sonuçlarını yerel bilgisayarla ilişkili nesneleri ile doldurur.  
  
9. Bul **IIS_IUSRS** girişi **adı (göreli ayırt edici adı)** sütun. Bu girişi seçin ve tıklatın **Tamam** sonuçlarını pencere arama'yı kapatmak için.  
  
10. Tıklatın **Tamam** kapatmak için **kullanıcıları veya Grupları Seç** penceresi.  
  
11. Tıklatın **paylaşımı** değişiklikleri kalıcı hale getirmek için.  
  
12. Paylaşıma değişiklik tamamlandıktan sonra tıklatın **Bitti** kapatmak için **dosya paylaşımı** penceresi.  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-51-or-60"></a>IIS 5.1 veya 6.0 klasörü güvenlik özelliklerini ayarlamak için  
  
1.  % SystemDrive%\inetpub\wwwroot\servicemodelsamples gidin.  
  
2.  Sağ **servicemodelsamples** klasörünü ve ardından **paylaşım ve güvenlik.**  
  
3.  Tıklatın **güvenlik** sekmesi.  
  
4.  IIS 6. 0'da, içinde kullanıyorsanız **grup veya kullanıcı adları** onay kutusuna olup olmadığını **Internet Konuk hesabı** listelenir.  
  
     Listelenmemişse:  
  
    1.  Tıklatın **Başlat** ve ardından **Denetim Masası**.  
  
    2.  Görmüyorsanız, **kullanıcı hesapları** simgesini tıklatın **kategori görünümüne geçiş**.  
  
    3.  Tıklatın **kullanıcı hesapları** simgesi.  
  
    4.  Altında "veya Denetim Masası simgesi seçin" tıklatın **kullanıcı hesaplarını**.  
  
    5.  İçinde **kullanıcı hesapları** iletişim kutusu, tıklatın **Gelişmiş** sekmesi.  
  
    6.  **Gelişmiş**'e tıklayın.  
  
    7.  İçinde **yerel kullanıcılar ve gruplar** iletişim kutusu, genişletmek için tıklatın **kullanıcılar** klasör.  
  
    8.  Sağ bölmede, çift **Internet Konuk hesabı**.  
  
    9. İçinde **özellikleri** iletişim kutusu, kopyalama Internet Konuk hesabı olarak kullanılan adı. Varsayılan olarak, adı "bilgisayar adından USR_" ile başlar.  
  
    10. **Özellikler** iletişim kutusunu kapatın.  
  
    11. Kapat **yerel kullanıcılar ve gruplar** iletişim kutusu.  
  
    12. Kapat **kullanıcı hesapları** iletişim kutusu.  
  
    13. Diğer kapatmak **kullanıcı hesapları** iletişim kutusu.  
  
    14. İçinde **servicemodelsamples özellikleri** iletişim kutusundaki **güvenlik** sekmesini tıklatın, **Ekle**.  
  
    15. Ardından bir eğik bilgisayarın adını yazın, sonra Internet kullanıcı hesabının, örneğin, myMachineName adını yapıştırın\\InternetGuestAccountName %  
  
    16. Tıklatın **Adları Denetle** eklenmesini doğrulamak için. Geçerli ise, ad büyük harflerle olduğu ve altı çizilir.  
  
5.  Ağ hizmeti listelenen IIS 6.0 için ayrıca kontrol **grup veya kullanıcı adları** kutusu.  
  
     Ağ hizmeti listelenmemişse:  
  
    1.  **Ekle**'yi tıklatın.  
  
    2.  İçinde **kullanıcıları veya Grupları Seç** iletişim kutusuna bilgisayarın adını ve ardından bir eğik.  
  
    3.  Tür **hizmet** ters eğik çizgi (boşluksuz) sonra.  
  
    4.  Tıklatın **Adları Denetle**.  
  
    5.  Birden çok ad bulunursa seçip **ağ hizmeti** tıklatıp **Tamam**.  
  
    6.  Tıklatın **Tamam** kapatmak için **kullanıcıları veya Grupları Seç** iletişim kutusu.  
  
6.  IIS 5.1 ile Windows XP SP2 kullanıyorsanız, Internet Konuk hesabı ve ASPNET listelendiğini kontrol **grup veya kullanıcı adları** kutusu.  
  
     ASPNET kullanıcı yerleşik üyesi olabileceğine dikkat edin **kullanıcılar** güvenlik grubu. Bu durumda, ardından IF **kullanıcılar** Grup iletişim kutusunda listelenen, ayrı bir öğe olarak izin verilen kullanıcıları listesine eklemek gerekmez.  
  
     ASPNET parçası olup olmadığını denetlemek için **kullanıcılar** güvenlik grubu:  
  
    1.  Üzerinde **Başlat** menüsünde tıklatın **Denetim Masası**.  
  
    2.  Tıklatın **kullanıcı hesapları** simgesi.  
  
    3.  İçinde **grup** sütun denetleyin değeri **ASPNET** "kullanıcıları."  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Internet Information Service barındırma yönergeleri](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)
