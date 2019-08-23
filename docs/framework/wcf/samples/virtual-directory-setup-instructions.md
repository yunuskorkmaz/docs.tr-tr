---
title: Sanal Dizin Ayarlama Yönergeleri
ms.date: 03/30/2017
ms.assetid: 3c62cab5-81a4-48b6-ac8c-9ce33a85a157
ms.openlocfilehash: f755fadf6bef2bdd58fd31f3460a143b8f52eddf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966735"
---
# <a name="virtual-directory-setup-instructions"></a>Sanal Dizin Ayarlama Yönergeleri
Windows Communication Foundation (WCF) örnekleri,%SystemDrive%\inetpub\wwwroot\servicemodelsamples klasörüne eşlenmiş servicemodelsamples adlı ortak bir sanal dizinin paylaşılması için tasarlanmıştır.  
  
> [!NOTE]
> % SystemDrive%, Internet Information Services (IIS) yüklü olduğu sürücü konumuna bağlı olarak genellikle C: veya D: ' dır.  
  
 Sanal dizin oluşturmak için [Windows Communication Foundation Örnekleri Için bir kerelik kurulum yordamından](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) Setupvroot. bat ve Cleanupvroot. bat dosyalarını çalıştırabilirsiniz. Sanal dizini el ile oluşturmayı tercih ediyorsanız, aşağıdaki yordamları kullanın.  
  
## <a name="procedures"></a>Yordamlar  
  
#### <a name="to-create-a-virtual-directory-in-iis-70-or-75"></a>IIS 7,0 veya 7,5 ' de bir sanal dizin oluşturmak için  
  
1. **Başlat** menüsünde **Çalıştır**' a tıklayın ve ardından Internet INFORMATION SERVICES (IIS) MMC ek bileşenini açmak için **inetmgr** yazın.  
  
2. Sol bölmede, bilgisayarın adı ile düğümünü genişletin ve ardından **siteler** düğümünü genişletin.  
  
3. **Varsayılan Web sitesi**' ne sağ tıklayın ve ardından uygulama Ekle ' yi seçerek **Uygulama Ekle penceresini**açın.  
  
4. Penceresinde, oluşturmakta olduğunuz sanal `servicemodelsamples` dizinin diğer adı olarak yazın.  
  
5. Şu dizini oluşturun:%SystemDrive%\inetpub\wwwroot\servicemodelsamples  
  
6. Fiziksel yolu%SystemDrive%\inetpub\wwwroot\servicemodelsamples. olarak ayarla  WCF örneklerinin çoğu yapılandırıldığında bu konuma hizmet yürütülebilir dosyalarını kopyalar.  
  
7. **Tamam**'ı tıklatın. Web uygulaması artık WCF örnekleri için oluşturulmuştur.  
  
    > [!NOTE]
    >  Tüm WCF örnekleri aynı servicemodelsamples Web uygulamasını kullandığından, bu görevin yalnızca bir kez gerçekleştirilmesi gerekir.  
  
    > [!NOTE]
    >  Bu belgenin amacına yönelik terim `virtual directory` , ile `Web application`eşanlamlıdır.  
  
     Sanal dizin oluşturmanın yanı sıra, WCF hizmetlerinin çalışmasını sağlamak için özelliklerini de ayarlamanız gerekir. Ayrıntılar için aşağıya bakın.  
  
#### <a name="to-create-a-virtual-directory-in-iis-51-or-60"></a>IIS 5,1 veya 6,0 ' de bir sanal dizin oluşturmak için  
  
1. Bir komut istemi penceresi açın ve Internet Information Services `start inetmgr` (IIS) MMC ek bileşenini açmak için yazın.  
  
2. Sol bölmede, bilgisayarın adı ile düğümünü genişletin ve ardından **Web siteleri** düğümünü genişletin.  
  
3. **Varsayılan Web sitesi** ' ne sağ tıklayın ve **Yeni, sanal dizin** ' i seçerek sanal dizin oluşturma Sihirbazı 'nı açın.  
  
4. Sihirbazda, oluşturmakta olduğunuz sanal `servicemodelsamples` dizinin diğer adı olarak yazın.  
  
5. Yolu%SystemDrive%\inetpub\wwwroot\servicemodelsamples. olarak ayarlayın WCF örneklerinin çoğu yapılandırıldığında bu konuma hizmet yürütülebilir dosyalarını kopyalar.  
  
6. **İleri**'ye tıklayın.  
  
7. Varsayılan olarak, aşağıdaki onay kutuları seçilidir:  
  
    - **Read**  
  
    - **Betikleri Çalıştır (ASP gibi)**  
  
8. **İleri**' ye tıklayın ve Sihirbazı tamamladıktan sonra **son** ' a tıklayın.  
  
    > [!NOTE]
    >  Tüm WCF örnekleri aynı servicemodelsamples sanal dizinini kullandığından, bu görevin yalnızca bir kez gerçekleştirilmesi gerekir.  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-70-or-75"></a>IIS 7,0 veya 7,5 ' de ek sanal dizin özellikleri ayarlamak için  
  
1. Servicemodelsamples düğümüne tıklayın. Pencerenin alt kısmında iki görünüm listelenir. Henüz seçili değilse **Özellikler Görünümü** ' nü seçin.  
  
2. **Dizin tarama**girişine çift tıklayın.  
  
3. Eylemler bölmesinde **Etkinleştir** seçeneğini belirleyin. Bu, bir hizmetin Hata ayıklamasında yardımcı olan Internet Explorer 'ı kullanarak dizinin dizinine erişmenizi sağlar.  
  
 Son olarak, servicemodelsamples klasörünün güvenlik özelliklerini diğerlerinin erişmesine izin verecek şekilde ayarlamanız gerekir. Ayrıntılar için aşağıya bakın.  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-51-or-60"></a>IIS 5,1 veya 6,0 ' de ek sanal dizin özellikleri ayarlamak için  
  
1. Servicemodelsamples düğümüne sağ tıklayın ve ardından **Özellikler**' e tıklayın.  
  
2. Varsayılan olarak, aşağıdaki onay kutuları seçilidir:  
  
    - **Read**  
  
    - **Günlüğe ziyaretleri Kaydet**  
  
    - **Bu kaynağı dizine oluştur**  
  
3. **Dizin tarama** onay kutusunu seçin. Bu, bir hizmetin Hata ayıklamasında yardımcı olan Internet Explorer 'ı kullanarak dizinin dizinine erişmenizi sağlar.  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-70-or-75"></a>IIS 7,0 veya 7,5 ' de klasörün güvenlik özelliklerini ayarlamak için  
  
1. %SystemDrive%\inetpub\wwwroot\servicemodelsamples. adresine gidin  
  
2. Servicemodelsamples klasörüne sağ tıklayın ve **paylaşma** ya da **paylaşma**' ya tıklayın.  
  
3. **Ekle** düğmesinin solundaki aşağı oka tıklayın.  
  
4. **Find** girişini seçin. **Kullanıcıları veya grupları seç** penceresi açılır.  
  
5. **Gelişmiş**'e tıklayın.  
  
6. **Konumlar**' a tıklayın. **Konumlar** penceresi artık açıktır.  
  
7. Kullanılan bilgisayar için girişi seçin. Listelenen herhangi bir etki alanı veya ağ için bir giriş değil, yerel bilgisayarı seçmek önemlidir. Bilgisayarı seçtikten sonra **Tamam**' a tıklayın.  
  
8. **Şimdi bul**' a tıklayın. Bu, arama sonuçlarını yerel bilgisayarla ilişkili nesnelerle doldurur.  
  
9. **Ad (göreli ayırt edici ad)** sütununda **IIS_IUSRS** girişini bulun. Bu girişi seçin ve **Tamam** ' a tıklayarak arama sonuçları penceresini kapatın.  
  
10. **Tamam** ' a tıklayarak **kullanıcıları veya grupları seç** penceresini kapatın.  
  
11. Değişiklikleri kalıcı hale getirmek için **paylaşma** ' ya tıklayın.  
  
12. Paylaşımı etkinleştirme değişiklikleri tamamlandıktan sonra, **dosya paylaşımı** penceresini kapatmak için **bitti** ' ye tıklayın.  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-51-or-60"></a>IIS 5,1 veya 6,0 ' de klasörün güvenlik özelliklerini ayarlamak için  
  
1. %SystemDrive%\inetpub\wwwroot\servicemodelsamples. adresine gidin  
  
2. **Servicemodelsamples** klasörüne sağ tıklayın ve ardından **Paylaşım ve güvenlik** ' e tıklayın.  
  
3. **Güvenlik** sekmesine tıklayın.  
  
4. IIS 6,0 kullanıyorsanız, **Grup veya Kullanıcı adları** kutusunda **Internet Konuk hesabının** listelenip listelenmediğini denetleyin.  
  
     Listede yoksa:  
  
    1. **Başlat** ' a ve ardından **Denetim Masası**' na tıklayın.  
  
    2. **Kullanıcı hesapları** simgesini görmüyorsanız **Kategori görünümüne geç ' e**tıklayın.  
  
    3. **Kullanıcı hesapları** simgesine tıklayın.  
  
    4. "Veya bir Denetim Masası simgesi seçin" altında **Kullanıcı hesapları**' na tıklayın.  
  
    5. **Kullanıcı hesapları** Iletişim kutusunda **Gelişmiş** sekmesine tıklayın.  
  
    6. **Gelişmiş**'e tıklayın.  
  
    7. **Yerel kullanıcılar ve gruplar** Iletişim kutusunda **Kullanıcılar** klasörünü genişletmek için tıklayın.  
  
    8. Sağ bölmede **Internet Konuk hesabı**' na çift tıklayın.  
  
    9. **Özellikler** iletişim kutusunda, Internet Konuk hesabı olarak kullanılan adı kopyalayın. Varsayılan olarak, ad "USR_" ile başlar ve ardından bilgisayarın adı gelir.  
  
    10. **Özellikler** iletişim kutusunu kapatın.  
  
    11. **Yerel kullanıcılar ve gruplar** iletişim kutusunu kapatın.  
  
    12. **Kullanıcı hesapları** iletişim kutusunu kapatın.  
  
    13. Diğer **Kullanıcı hesapları** iletişim kutusunu kapatın.  
  
    14. **Servicemodelsamples özellikleri** iletişim kutusunda, **güvenlik** sekmesinde, **Ekle**' ye tıklayın.  
  
    15. Bilgisayarın adını ve ters eğik çizgiyi yazın, ardından Internet Kullanıcı hesabının adını yapıştırın, örneğin, mymachinename\\% InternetGuestAccountName%  
  
    16. Eklemeyi doğrulamak için **adları denetle** ' ye tıklayın. Geçerliyse, ad tüm büyük harflerle ve altı çizilir.  
  
5. IIS 6,0 için, ağ HIZMETI 'nin **Grup veya Kullanıcı adları** kutusunda listelendiğini de denetleyin.  
  
     Ağ HIZMETI listelenmiyorsa:  
  
    1. **Ekle**'yi tıklatın.  
  
    2. **Kullanıcı veya Grup Seç** iletişim kutusunda, bilgisayarın adını ve ardından bir ters eğik çizgi yazın.  
  
    3. Ters eğik çizgiden sonra **hizmet** yazın (boşluk olmadan).  
  
    4. **Adları denetle**' ye tıklayın.  
  
    5. Birden çok ad bulunursa **ağ hizmeti** ' ni seçin ve **Tamam**' ı tıklatın.  
  
    6. **Tamam** ' a tıklayarak **kullanıcıları veya grupları seç** iletişim kutusunu kapatın.  
  
6. IIS 5,1 ile Windows XP SP2 kullanıyorsanız, hem Internet Konuk hesabı hem de ASPNET 'in **Grup veya Kullanıcı adları** kutusunda listelendiğinden emin olun.  
  
     ASPNET kullanıcısının yerleşik **Kullanıcılar** güvenlik grubunun bir üyesi olabileceğini unutmayın. Bu durumda, **Kullanıcılar** grubu iletişim kutusunda listeleniyorsa, izin verilen kullanıcılar listesine ayrı bir öğe olarak eklemeniz gerekmez.  
  
     ASPNET 'in **Kullanıcılar** güvenlik grubunun bir parçası olup olmadığını denetlemek için:  
  
    1. **Başlat** menüsünde, **Denetim Masası**' na tıklayın.  
  
    2. **Kullanıcı hesapları** simgesine tıklayın.  
  
    3. **Grup** sütununda, **ASPNET** değerinin "kullanıcılar" olup olmadığını kontrol edin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Internet Information Service Barındırma Yönergeleri](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)
