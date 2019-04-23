---
title: WS-Atomic İşlem Desteğini Yapılandırma
ms.date: 03/30/2017
helpviewer_keywords:
- WS-AT protocol [WCF], configuring WS-Atomic Transaction
ms.assetid: cb9f1c9c-1439-4172-b9bc-b01c3e09ac48
ms.openlocfilehash: 987d6c12262fd6530c6ef6f14cedeec269d3f2f8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59315185"
---
# <a name="configuring-ws-atomic-transaction-support"></a>WS-Atomic İşlem Desteğini Yapılandırma
Bu konuda, WS-AT yapılandırma yardımcı programını kullanarak WS-AtomicTransaction (WS-AT) desteği nasıl yapılandıracağınız açıklanır.  
  
## <a name="using-the-ws-at-configuration-utility"></a>WS-AT yapılandırma yardımcı programını kullanma  
 WS-AT yapılandırma yardımcı programı (wsatConfig.exe) WS-AT ayarlarını yapılandırmak için kullanılır. WS-AT protokolü hizmetini etkinleştirmek için yapılandırma yardımcı programı WS-AT için HTTPS bağlantı noktası yapılandırın, bir X.509 sertifikası HTTPS bağlantı noktasına bağlayın ve sertifikası konu adları belirterek yetkili iş ortağı sertifikaları yapılandırmak için kullanmanız gerekir veya parmak izleri. Yapılandırma yardımcı programı izleme modunu ve varsayılan kümesi giden ve gelen işlem zaman aşımı en fazla seçmenizi sağlar.  
  
 Bir Microsoft Yönetim Konsolu (MMC) özellik sayfası ek bileşenini Bileşen Hizmetleri Yönetimi konsolunda veya komut satırı penceresini kullanarak bu aracın işlevselliği erişebilirsiniz. Komut satırı penceresini aracılığıyla yerel makinede WS-AT desteğini yapılandırmak; ayarları, hem yerel hem de uzak makinelerde MMC ek bileşenini kullanarak yapılandırın.  
  
 Windows SDK yükleme konumu "%WINDIR%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation" komut satırı penceresini erişilebilir.  
  
 Komut satırı aracı hakkında daha fazla bilgi için bkz: [WS-AtomicTransaction yapılandırma yardımcı programı (wsatConfig.exe)](../../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md).  
  
 Çalıştırıyorsanız [!INCLUDE[wxp](../../../../includes/wxp-md.md)] veya [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], MMC ek bileşeninde giderek erişebileceğiniz **Denetim Masası/Yönetim Araçları/Component Services**, sağ **Bilgisayarım**, ve seçme **özellikleri**. Bu, Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) yapılandırabileceğiniz aynı konumdur. İçin yapılandırma seçenekleri altında gruplanır **WS-AT** sekmesi. Windows Vista çalıştırıyorsanız veya [!INCLUDE[lserver](../../../../includes/lserver-md.md)], MMC ek bileşeninde tıklayarak bulunabilir **Başlat** düğmesi ve girerek `dcomcnfg.exe` içinde **arama** kutusu. MMC açıldığında gidin **My Computer\Distributed işlem Coordinator\Local DTC** düğümünü sağ tıklatın ve seçin **özellikleri**. İçin yapılandırma seçenekleri altında gruplanır **WS-AT** sekmesi.  
  
 Eklenti hakkında daha fazla bilgi için bkz. [WS-AtomicTransaction yapılandırması MMC ek bileşenini](../../../../docs/framework/wcf/ws-atomictransaction-configuration-mmc-snap-in.md).  
  
 Aracı'nın kullanıcı arabirimini etkinleştirmek için önce şu yolda bulunan WsatUI.dll dosyasına kaydetmeniz gerekir  
  
 %PROGRAMFILES%\Microsoft SDKs\Windows\v6.0\Bin  
  
 Ürün kaydetmek için bir komut istemi penceresinden aşağıdaki komutu yürütün:  
  
 `regasm.exe /codebase WsatUI.dll`  
  
## <a name="enabling-ws-at"></a>WS-AT etkinleştirme  
 Yerel makine deposuna yüklenmiş olan özel bir anahtar bağlantı noktası 443 ve bir X.509 sertifikası kullanarak MSDTC içinde WS-AT protokolü hizmetini etkinleştirmek için aşağıdaki komutla wsatConfig.exe Aracı'nı kullanın.  
  
 `WsatConfig.exe –network:enable –port:8443 –endpointCert:<machine|"Issuer\SubjectName"> -accountsCerts:<thumbprint|"Issuer\SubjectName"> -restart`  
  
 İlgili parametreleri ortamınızla ilgili değerlerle değiştirin.  
  
 MSDTC içinde WS-AT protokolü hizmetini devre dışı bırakmak için aşağıdaki komutla wsatConfig.exe Aracı'nı kullanın.  
  
 `WsatConfig.exe –network:disable -restart`  
  
## <a name="configuring-trust-between-two-machines"></a>İki makine arasında güven yapılandırma  
 WS-AT protokolü hizmetini açıkça dağıtılmış işlemlere katılmasına bireysel hesaplar yetkilendirmek yöneticiye gerekir. İki makine için bir yöneticiyseniz doğru ortaklık kümesi makineler arasında sertifika alışverişi, uygun sertifika depolarına yüklemeden ve kullanarak bir karşılıklı güven ilişkisi oluşturmak için her iki makine yapılandırabilirsiniz. her makinenin sertifika diğer tarafın yetkili katılımcı sertifikası listesine eklemek için wsatConfig.exe Aracı'nı tıklatın. WS-AT kullanan iki makine arasında dağıtılmış işlemler gerçekleştirmek Bu adım gereklidir.  
  
 Aşağıdaki örnekte A ve b olmak üzere iki makine arasında güven oluşturma adımları açıklanmaktadır  
  
### <a name="creating-and-exporting-certificates"></a>Oluşturma ve sertifika dışarı aktarma  
 Bu yordam sertifikalar MMC ek bileşenini gerektirir. Ek bileşenini başlangıç/çalıştırma menüsünü açarak, "mmc" giriş kutusuna ve Tamam'tuşuna basarak erişilebilir. Ardından **Konsol1** penceresinde gidin **Dosya/Ekle / Kaldır** ek bileşenini Ekle ve seçin **sertifikaları** gelen **kullanılabilir tek başına Ek bileşen** listesi. Son olarak, seçin **bilgisayar hesabı** yönetip tıklayın **Tamam**. **Sertifikaları** düğümü ek bileşenini konsolda görüntülenir.  
  
 Güven oluşturmak için gerekli sertifikaları zaten sahip olması gerekir. Oluşturun ve aşağıdaki adımları önce yeni sertifika yükleme konusunda bilgi almak için bkz: [nasıl yapılır: Oluşturma ve yükleme geçici istemci sertifikaları WCF'de geliştirme sırasında](https://go.microsoft.com/fwlink/?LinkId=158925).  
  
1. Makine A'da sertifikalar MMC ek bileşenini alma LocalMachine\MY (Kişisel düğümü) ve LocalMachine\ROOT deposu (güvenilen kök sertifika yetkilisi düğümü) mevcut sertifikayı (certA) kullanarak. Belirli bir düğüme sertifikayı içeri aktarmak için düğümünü sağ tıklatın ve seçin **tüm görevler/içeri aktarma**.  
  
2. B sertifikalar MMC ek bileşenini kullanarak, makinede oluşturun veya bir özel anahtara sahip bir sertifika certB edinmek ve LocalMachine\MY (Kişisel düğümü) ve LocalMachine\ROOT deposu (güvenilen kök sertifika yetkilisi düğümü) içe aktarın.  
  
3. Bu zaten yapılmadıysa, certA'ın ortak anahtarını bir dosyaya dışarı aktarın.  
  
4. Bu zaten yapılmadıysa, certB'ın ortak anahtarını bir dosyaya dışarı aktarın.  
  
### <a name="establishing-mutual-trust-between-machines"></a>Makineler arasındaki karşılıklı güven oluşturma  
  
1. Makine A'da certB dosya gösterimini LocalMachine\MY ve LocalMachine\ROOT depolarına aktarın. Bu, makine ile iletişim kurmak için güvenleri certB bildirir.  
  
2. B makinede LocalMachine\MY ve LocalMachine\ROOT depolara certA'ın dosyasını içeri aktarın. Bu, makine ile iletişim kurmak için B güvenleri certA anlamına gelir.  
  
 Bu adımları tamamladıktan sonra iki makine arasında güven ve WS-AT aracılığıyla birbirleriyle iletişim kurmak için yapılandırılabilir.  
  
### <a name="configuring-msdtc-to-use-certificates"></a>MSDTC sertifikalarını kullanacak şekilde yapılandırma  
 WS-AT protokolü hizmetini hem istemci hem de bir sunucu görev yapar. bu yana, hem gelen bağlantıları için dinlemek ve gerekir giden bağlantılar başlatabilirsiniz. Bu nedenle, hangi sertifikanın harici taraflarla iletişim kurarken kullanması ve gelen iletişimi kabul ederken yetkilendirmek için hangi sertifikaların bilir MSDTC yapılandırmanız gerekir.  
  
 Bu, WS-AT MMC ek bileşenini kullanarak yapılandırabilirsiniz. Bu araç hakkında daha fazla bilgi için bkz. [WS-AtomicTransaction yapılandırması MMC ek bileşenini](../../../../docs/framework/wcf/ws-atomictransaction-configuration-mmc-snap-in.md) konu. Aşağıdaki adımlar, MSDTC çalıştıran iki bilgisayar arasında güven oluşturma açıklanmaktadır.  
  
1. Makine A'ın ayarlarını yapılandırın. "Son nokta sertifikası" için certA seçin. "Yetkili sertifikaları için" certB seçin.  
  
2. Makine B'nin ayarlarını yapılandırın. "Son nokta sertifikası" için certB seçin. "Yetkili sertifikaları için" certA seçin.  
  
> [!NOTE]
>  Bir makineyi başka bir makine için bir ileti gönderdiğinde, gönderenin alıcının sertifikanın konu adı ve alıcının makinenin adını eşleştiğini doğrulayın dener. Bunlar eşleşmiyorsa, sertifika doğrulama başarısız olur ve iki makine iletişim kuramıyor.  
>   
>  Bir etki alanına katılmış bir makine için adı tam etki alanı adıdır. Varsayılan olarak, makine NetBIOS adını bir çalışma grubu makinesinde adıdır. Ancak, iki makine arasında kullanılan bağlantı varsa, ad etki alanı adı sistemi (DNS) soneki de içerebilir.  
>   
>  Bir çalışma grubu makinesine bir etki alanına katıldığında makinenin adını, örneğin, değişirse sertifikaları yeniden gönderin veya DNS son eklerini el ile yapılandırmanız gerekir.  
  
## <a name="security"></a>Güvenlik  
 Bazı MSDTC ve WS-AT ilgili ayarlar kayıt defterinde HKLM\Software\Microsoft\MSDTC ve HKLM\Software\Microsoft\WSAT, sırasıyla depolandığından, yalnızca Yöneticiler, kendilerine yazabilmesi amacıyla bu kayıt defteri anahtarlarını güvenli olduğundan emin olun. Güvenli ve seçmek için istediğiniz anahtarı kayıt defteri Düzenleyicisi'ni aracında, sağ **izni** uygun erişim denetimini ayarlama. Düşük ayrıcalıklı kullanıcı için salt okunur anahtarlar, önemli sistem bütünlüğü ve güvenlik için önemlidir.  
  
 MSDTC dağıtırken yönetici herhangi MSDTC veri değişimi güvenli olduğundan emin olmanız gerekir. Bir çalışma grubu dağıtımında, işlem altyapısı kötü niyetli kullanıcıların yalıtmak; bir küme dağıtımında, küme kayıt defteri güvenliğini sağlayın.  
  
## <a name="tracing"></a>İzleme  
 Tümleşik WS-AT protokolü destekler, belirli izleme etkinleştirilebilir ve kullanımının yönetilen işlem [WS-AtomicTransaction yapılandırması MMC ek bileşenini](../../../../docs/framework/wcf/ws-atomictransaction-configuration-mmc-snap-in.md) aracı.  İzlemeleri, belirli bir işlem, bir işlem terminal durumuna, sonucu her işlem kaydı ulaştığında zaman bir kaydı yapıldığında aldı gösteren veriler içerebilir. Tüm izlemeleri kullanılarak görüntülenebilir [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) aracı.  
  
 WS-AT protokolü hizmet ayrıca tümleşik ServiceModel izlemeye ETW izleme oturumunu destekler. Bu, var olan işlem izlemeleri yanı sıra ayrıntılı ve iletişim özgü izlemeler sağlar.  Bu ek izlemeleri etkinleştirmek için şu adımları izleyin.  
  
1. Açık **başlangıç/çalıştırma** menüsünden "regedit" giriş kutusuna girin ve seçin **Tamam**.  
  
2. İçinde **Kayıt Defteri Düzenleyicisi'ni**, sol bölmede, Hkey_Local_Machine\SOFTWARE\Microsoft\WSAT\3.0\ aşağıdaki klasöre gidin  
  
3. Sağ tıklayın `ServiceModelDiagnosticTracing` seçin ve sağ bölmede değer **Değiştir**.  
  
4. İçinde **değer verisi** giriş kutusunda, aşağıdakilerden birini etkinleştirmek istediğiniz izleme düzeyini belirtmek için aşağıdaki geçerli değerleri girin.  
  
-   0: kapalı  
  
-   1: kritik  
  
-   3: hata. Varsayılan değer budur.  
  
-   7: uyarı  
  
-   15: bilgi  
  
-   31: ayrıntılı  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WS-AtomicTransaction Yapılandırma Yardımcı Programı (wsatConfig.exe)](../../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)
- [WS-AtomicTransaction Yapılandırması MMC Ek Bileşeni](../../../../docs/framework/wcf/ws-atomictransaction-configuration-mmc-snap-in.md)
