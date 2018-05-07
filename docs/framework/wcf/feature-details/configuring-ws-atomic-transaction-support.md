---
title: WS-Atomic İşlem Desteğini Yapılandırma
ms.date: 03/30/2017
helpviewer_keywords:
- WS-AT protocol [WCF], configuring WS-Atomic Transaction
ms.assetid: cb9f1c9c-1439-4172-b9bc-b01c3e09ac48
ms.openlocfilehash: a89caad51f098e17bca1a5ba3df600a6dbf1dd9f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="configuring-ws-atomic-transaction-support"></a>WS-Atomic İşlem Desteğini Yapılandırma
Bu konuda, WS-AT yapılandırma yardımcı programını kullanarak WS-AtomicTransaction (WS-AT) desteğini nasıl yapılandırabileceğiniz açıklanmaktadır.  
  
## <a name="using-the-ws-at-configuration-utility"></a>WS-AT yapılandırma yardımcı programını kullanma  
 WS-AT yapılandırma yardımcı programı (wsatConfig.exe) WS-AT ayarlarını yapılandırmak için kullanılır. WS-AT protokolü hizmetini etkinleştirmek için yapılandırma yardımcı programı WS-AT için HTTPS bağlantı noktası yapılandırmak, bir X.509 sertifikası HTTPS bağlantı noktasına bağlayın ve yetkili ortak sertifikalar sertifika konu adları belirterek yapılandırmak için kullanmanız gerekir veya parmak izleri. Yapılandırma yardımcı programı izleme modunu ve varsayılan kümesi giden ve en fazla gelen işlem zaman aşımlarını seçmenizi sağlar.  
  
 Bu aracın işlevselliği, bir Microsoft Yönetim Konsolu (MMC) özellik sayfası ek bileşeni Bileşen Hizmetleri Yönetimi konsolunda veya komut satırı penceresinde kullanarak erişebilirsiniz. Komut satırı penceresinde aracılığıyla yerel makinedeki WS-AT desteği yapılandırın; MMC ek bileşenini kullanarak hem yerel hem de uzak makinelerde ayarlarını yapılandırmak.  
  
 Komut satırı penceresinde Windows SDK yükleme konumunda "%WINDIR%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation" erişilebilir.  
  
 Komut satırı aracı hakkında daha fazla bilgi için bkz: [WS-AtomicTransaction yapılandırma yardımcı programı (wsatConfig.exe)](../../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md).  
  
 Çalıştırıyorsanız, [!INCLUDE[wxp](../../../../includes/wxp-md.md)] veya [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], MMC ek bileşenini giderek erişebilirsiniz **Denetim Masası/Yönetimsel Araçlar/Component Services**, sağ **Bilgisayarım**, ve seçme **özellikleri**. Bu, Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) yapılandırabileceğiniz aynı konumdur. Yapılandırma için kullanılabilir seçenekleri altında gruplandırılır **WS-AT** sekmesi. Windows Vista çalıştırıyorsanız veya [!INCLUDE[lserver](../../../../includes/lserver-md.md)], MMC ek bileşenini tıklayarak bulunabilir **Başlat** düğmesi ve girerek `dcomcnfg.exe` içinde **arama** kutusu. MMC açıldığında gidin **My Computer\Distributed işlem Coordinator\Local DTC** düğümünü sağ tıklatın ve seçin **özellikleri**. Yapılandırma için kullanılabilir seçenekleri altında gruplandırılır **WS-AT** sekmesi.  
  
 Ek bileşeni hakkında daha fazla bilgi için bkz: [WS-AtomicTransaction yapılandırması MMC ek bileşenini](../../../../docs/framework/wcf/ws-atomictransaction-configuration-mmc-snap-in.md).  
  
 Aracın kullanıcı arabirimini etkinleştirmek için önce aşağıdaki yolda bulunan WsatUI.dll dosyasını kaydetmeniz gerekir  
  
 %PROGRAMFILES%\Microsoft SDKs\Windows\v6.0\Bin  
  
 Ürünü kaydetmek için bir komut istemi penceresinden aşağıdaki komutu yürütün:  
  
 `regasm.exe /codebase WsatUI.dll`  
  
## <a name="enabling-ws-at"></a>WS-AT etkinleştirme  
 Yerel makine deposunda yüklü bir özel anahtar bağlantı noktası 443 ve bir X.509 sertifikası kullanarak MSDTC içinde WS-AT protokolü hizmetini etkinleştirmek için aşağıdaki komutla wsatConfig.exe aracını kullanın.  
  
 `WsatConfig.exe –network:enable –port:8443 –endpointCert:<machine|"Issuer\SubjectName"> -accountsCerts:<thumbprint|"Issuer\SubjectName"> -restart`  
  
 İlgili parametrelerini ortamınızla ilgili değerlerle değiştirin.  
  
 MSDTC içinde WS-AT protokolü hizmetini devre dışı bırakmak için aşağıdaki komutla wsatConfig.exe aracını kullanın.  
  
 `WsatConfig.exe –network:disable -restart`  
  
## <a name="configuring-trust-between-two-machines"></a>İki makine arasında güven yapılandırma  
 WS-AT protokolü hizmeti açıkça bireysel hesaplar dağıtılmış işlemlere katılmasına yetkilendirmek yönetici gerektirir. İki makine için bir yöneticiyseniz, sertifikalar makine arasında doğru kümesini değişimi bunları uygun sertifika depolarını yükleme ve kullanma karşılıklı güven ilişkisi oluşturmak için her iki makine yapılandırabilirsiniz her makinenin sertifika diğerinin yetkili katılımcı sertifikalar listesine eklemek için wsatConfig.exe Aracı'nı tıklatın. WS-AT kullanarak iki makine arasında dağıtılmış işlemler gerçekleştirmek Bu adım gereklidir.  
  
 Aşağıdaki örnekte A ve b iki makine arasında güven oluşturmak için gereken adımları özetler  
  
### <a name="creating-and-exporting-certificates"></a>Oluşturma ve sertifika verme  
 Bu yordam, sertifikalar MMC ek bileşenini gerektirir. Ek bileşenini başlangıç/Çalıştır menüsünü açma, "mmc" giriş kutusuna yazıp Tamam tuşuna basarak erişilebilir. Ardından **Konsol1** penceresinde gidin **Dosya/Ekle / Kaldır** ek bileşenini Ekle'yi tıklatın ve seçin **sertifikaları** gelen **kullanılabilir tek başına Ek bileşen** listesi. Son olarak, seçin **bilgisayar hesabı** yönetmek tıklatıp **Tamam**. **Sertifikaları** düğümü ek bileşenini konsolunda görüntülenir.  
  
 Güven sağlamak için gerekli sertifikaları zaten sahip olması gerekir. Oluşturmak ve yeni sertifikalar için aşağıdaki adımları önce yüklemek öğrenmek için bkz: [nasıl yapılır: geliştirme sırasında WCF geçici istemci sertifikalarını yükleyip oluşturma](http://go.microsoft.com/fwlink/?LinkId=158925).  
  
1.  Makine A'da MMC Sertifikalar ek bileşenini varolan bir sertifikayı (certA) LocalMachine\MY (Kişisel düğümü) ve LocalMachine\ROOT deposu (güvenilen kök sertifika yetkilisi düğüm) kullanarak alma. Belirli bir düğüme bir sertifikayı almak için düğümünü sağ tıklatın ve seçin **tüm görevler/içe aktarma**.  
  
2.  Sertifikalar MMC ek bileşenini kullanarak B, makinedeki oluşturun veya özel anahtara sahip bir sertifika certB elde ve LocalMachine\MY (Kişisel düğümü) ve LocalMachine\ROOT deposu (güvenilen kök sertifika yetkilisi düğüm) alın.  
  
3.  Bu zaten yapılmadıysa varsa certA'ın ortak anahtarı bir dosyaya aktarın.  
  
4.  Bu zaten yapılmadıysa varsa certB'ın ortak anahtarı bir dosyaya aktarın.  
  
### <a name="establishing-mutual-trust-between-machines"></a>Makineler arasında karşılıklı güven oluşturma  
  
1.  Makine A'da certB dosya gösterimini LocalMachine\MY ve LocalMachine\ROOT depolarını alın. Bu, bu makine ile iletişim kurmak için güvenleri certB bildirir.  
  
2.  B makinede LocalMachine\MY ve LocalMachine\ROOT depolarını certA'ın dosyasını içeri aktarın. Bu, bu makine ile iletişim kurmak için B güvenleri certA anlamına gelir.  
  
 Bu adımları tamamladıktan sonra iki makine arasında güven ve birbirleri ile WS-AT kullanarak iletişim kurmak üzere yapılandırılabilir.  
  
### <a name="configuring-msdtc-to-use-certificates"></a>Sertifikaları kullanmasını MSDTC yapılandırma  
 WS-AT protokolü hizmetini hem istemci hem de bir sunucu olarak görev olduğundan, hem gelen bağlantılar için dinleme ve gerekir giden bağlantılar başlatamaz. Bu nedenle, böylece dış taraflarla iletişim kurarken kullanması için hangi sertifikanın ve gelen iletişimi kabul ederken yetkilendirmek için hangi sertifikaların bilir MSDTC yapılandırmanız gerekir.  
  
 Bu WS-AT MMC ek bileşenini kullanarak yapılandırabilirsiniz. Bu araç hakkında daha fazla bilgi için bkz: [WS-AtomicTransaction yapılandırması MMC ek bileşenini](../../../../docs/framework/wcf/ws-atomictransaction-configuration-mmc-snap-in.md) konu. Aşağıdaki adımlar MSDTC çalıştıran iki bilgisayar arasında güven oluşturmak nasıl açıklamaktadır.  
  
1.  Makine A'ın ayarlarını yapılandırın. "İçin sertifika uç noktası," certA seçin. "Yetkili sertifikaları için" certB seçin.  
  
2.  Makine B'nin ayarlarını yapılandırın. "İçin sertifika uç noktası," certB seçin. "Yetkili sertifikaları için" certA seçin.  
  
> [!NOTE]
>  Bir makine diğer makineye bir ileti gönderdiğinde, gönderenin alıcı sertifikasının konu adını ve alıcının makinenin adını eşleştiğini doğrulayın dener. Bunlar eşleşmiyorsa sertifika doğrulaması başarısız olur ve iki makine iletişim kuramıyor.  
>   
>  Bir etki alanına katılmış bir makine için adı tam etki alanı adıdır. Varsayılan olarak, bir çalışma grubunda bir makine makine NetBIOS adı adıdır. Ancak, iki makine arasında kullanılan bağlantı için var olan ad de bir etki alanı adı sistemi (DNS) soneki içerir.  
>   
>  Bir çalışma grubu makinesi bir etki alanına katıldığında makinenin adını, örneğin, bir değişiklik olursa sertifikaları yeniden veya DNS sonekleri el ile yapılandırmanız gerekir.  
  
## <a name="security"></a>Güvenlik  
 MSDTC ve WS-AT ilgili ayarlardan bazıları HKLM\Software\Microsoft\MSDTC ve HKLM\Software\Microsoft\WSAT, kayıt defterinde sırasıyla depolandığından, yalnızca Yöneticiler bunları yazabilirler böylece bu kayıt defteri anahtarlarını güvenli olduğundan emin olun. Güvenli ve seçmek için istediğiniz anahtarı kayıt defteri Düzenleyicisi'ni aracında sağ **izin** uygun erişim denetimini ayarlama. Düşük ayrıcalıklı kullanıcılar için salt okunur anahtarları diğer önemli sistem bütünlüğü ve güvenlik için önemlidir.  
  
 MSDTC dağıtırken, yöneticinin tüm MSDTC veri değişim güvenli olduğundan emin olmanız gerekir. Bir çalışma grubu dağıtımında, kötü niyetli kullanıcılar işlem altyapısından yalıtmak; bir küme dağıtımında, küme kayıt defteri güvenliğini sağlayın.  
  
## <a name="tracing"></a>İzleme  
 WS-AT protokolü hizmetini destekler tümleşik, belirli izleme etkinleştirilebilir ve kullanım yoluyla yönetilen işlem [WS-AtomicTransaction yapılandırması MMC ek bileşenini](../../../../docs/framework/wcf/ws-atomictransaction-configuration-mmc-snap-in.md) aracı.  İzlemeler, bir işlem terminal durumuna, sonucu her işlem kaydı ulaştığında saat gibi belirli bir işlem için bir kaydı yapıldığında aldı gösteren verileri içerebilir. Tüm izlemeleri kullanılarak görüntülenebilir [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) aracı.  
  
 WS-AT protokolü hizmet ayrıca tümleşik ServiceModel izleme ETW İzleme oturumu aracılığıyla destekler. Bu, var olan işlem izlemeleri yanı sıra daha ayrıntılı ve iletişim özgü izlemeleri sağlar.  Bu ek izleri etkinleştirmek için şu adımları izleyin.  
  
1.  Açık **Başlat/Çalıştır** menüsünde giriş kutusuna "regedit" yazın ve seçin **Tamam**.  
  
2.  İçinde **Kayıt Defteri Düzenleyicisi'ni**, sol bölmede, Hkey_Local_Machine\SOFTWARE\Microsoft\WSAT\3.0\ aşağıdaki klasöre gidin  
  
3.  Sağ tıklayın `ServiceModelDiagnosticTracing` seçin ve değeri sağ bölmede **Değiştir**.  
  
4.  İçinde **değer verisi** giriş kutusu, etkinleştirmek istediğiniz izleme düzeyini belirtmek için aşağıdaki geçerli değerlerden birini girin.  
  
-   0: kapalı  
  
-   1: kritik  
  
-   3: hata. Bu varsayılan değerdir  
  
-   7: uyarı  
  
-   15: bilgi  
  
-   31: ayrıntılı  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WS-AtomicTransaction Yapılandırma Yardımcı Programı (wsatConfig.exe)](../../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)  
 [WS-AtomicTransaction Yapılandırması MMC Ek Bileşeni](../../../../docs/framework/wcf/ws-atomictransaction-configuration-mmc-snap-in.md)
