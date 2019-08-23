---
title: WS-Atomic İşlem Desteğini Yapılandırma
ms.date: 03/30/2017
helpviewer_keywords:
- WS-AT protocol [WCF], configuring WS-Atomic Transaction
ms.assetid: cb9f1c9c-1439-4172-b9bc-b01c3e09ac48
ms.openlocfilehash: 986481cb2ee52cd1d5737f7422bf2fc4eea70f33
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911234"
---
# <a name="configuring-ws-atomic-transaction-support"></a>WS-Atomic İşlem Desteğini Yapılandırma
Bu konu, WS-AT yapılandırma yardımcı programını kullanarak WS-AtomicTransaction (WS-AT) desteğini nasıl yapılandırabileceğinizi açıklamaktadır.  
  
## <a name="using-the-ws-at-configuration-utility"></a>WS-AT yapılandırma yardımcı programını kullanma  
 Ws-at yapılandırma yardımcı programı (wsatConfig. exe), WS-AT ayarlarını yapılandırmak için kullanılır. WS-AT protokol hizmetini etkinleştirmek için, yapılandırma yardımcı programını kullanarak WS-AT için HTTPS bağlantı noktasını yapılandırın, bir X. 509.440 sertifikasını HTTPS bağlantı noktasına bağlayın ve sertifika konu adlarını belirterek yetkili iş ortağı sertifikalarını yapılandırmanız gerekir. parmak izleri. Yapılandırma yardımcı programı, izleme modunu seçmenize ve varsayılan giden ve en fazla gelen işlem zaman aşımlarını ayarlamanıza olanak tanır.  
  
 Bu aracın işlevselliğine Bileşen Hizmetleri yönetim konsolundaki bir Microsoft Yönetim Konsolu (MMC) özellik sayfası ek bileşenini kullanarak veya bir komut satırı penceresinden erişebilirsiniz. Yerel makinede WS-AT desteğini komut satırı penceresi aracılığıyla yapılandırın; MMC ek bileşenini kullanarak hem yerel hem de uzak makinelerde ayarları yapılandırın.  
  
 Komut satırı penceresine, "%WINDIR%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation" Windows SDK yükleme konumundan erişilebilir.  
  
 Komut satırı aracı hakkında daha fazla bilgi için bkz. [WS-AtomicTransaction Yapılandırma yardımcı programı (wsatConfig. exe)](../../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md).  
  
 [!INCLUDE[wxp](../../../../includes/wxp-md.md)]Veya çalıştırıyorsanız[!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], **Denetim Masası/Yönetim Araçları/Bileşen Hizmetleri**' ne giderek, Bilgisayarım ' a sağ tıklayıp Özellikler ' i seçerek MMC ek bileşenine erişebilirsiniz. Bu, Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) yapılandırabileceğiniz konumdur. Yapılandırma için kullanılabilen seçenekler **ws-at** sekmesi altında gruplandırılır. Windows Vista veya [!INCLUDE[lserver](../../../../includes/lserver-md.md)]çalıştırıyorsanız, MMC ek bileşeni **Başlat** düğmesine tıklayıp `dcomcnfg.exe` **arama** kutusuna girerek bulunabilir. MMC açıldığında, **bilgisayar \ dağıtılmış işlem Koordinatlıklasör** düğümü ' ne gidin, sağ tıklayın ve **Özellikler**' i seçin. Yapılandırma için kullanılabilen seçenekler **ws-at** sekmesi altında gruplandırılır.  
  
 Ek bileşen hakkında daha fazla bilgi için bkz. [WS-AtomicTransaction YAPıLANDıRMASı MMC ek bileşeni](../../../../docs/framework/wcf/ws-atomictransaction-configuration-mmc-snap-in.md).  
  
 Aracın Kullanıcı arabirimini etkinleştirmek için, önce aşağıdaki yolda bulunan WsatUI. dll dosyasını kaydetmeniz gerekir  
  
 %PROGRAMFILES%\Microsoft SDKs\Windows\v6.0\Bin  
  
 Ürünü kaydetmek için bir komut Istemi penceresinden aşağıdaki komutu yürütün:  
  
 `regasm.exe /codebase WsatUI.dll`  
  
## <a name="enabling-ws-at"></a>WS-AT etkinleştiriliyor  
 443 numaralı bağlantı noktasını ve yerel makine deposuna yüklenmiş bir özel anahtara sahip bir X. 509.440 sertifikasını kullanarak MSDTC içindeki WS-AT protokol hizmetini etkinleştirmek için aşağıdaki komutla wsatConfig. exe aracını kullanın.  
  
 `WsatConfig.exe –network:enable –port:8443 –endpointCert:<machine|"Issuer\SubjectName"> -accountsCerts:<thumbprint|"Issuer\SubjectName"> -restart`  
  
 İlgili parametreleri ortamınıza uygun değerlerle değiştirin.  
  
 MSDTC içindeki WS-AT protokol hizmetini devre dışı bırakmak için aşağıdaki komutla wsatConfig. exe aracını kullanın.  
  
 `WsatConfig.exe –network:disable -restart`  
  
## <a name="configuring-trust-between-two-machines"></a>Iki makine arasında güveni yapılandırma  
 WS-AT protokol hizmeti, yöneticinin dağıtılan işlemlere katılmak için bireysel hesaplara açık olarak yetki vermiş olmasını gerektirir. İki makine için yöneticiyseniz, makineler arasında doğru sertifika kümesini değiş tokuş ederek, bunları uygun sertifika depolarına yükleyerek ve ' yi kullanarak karşılıklı güven ilişkisi kurmak için her iki makineyi de yapılandırabilirsiniz. Her makinenin sertifikasını diğer yetkili katılımcı sertifikaları listesine eklemek için wsatConfig. exe aracı. Bu adım WS-AT kullanan iki makine arasında dağıtılmış işlemler gerçekleştirmek için gereklidir.  
  
 Aşağıdaki örnekte, A ve B olmak üzere iki makine arasında güven oluşturma adımları özetlenmektedir.  
  
### <a name="creating-and-exporting-certificates"></a>Sertifikaları oluşturma ve dışarı aktarma  
 Bu yordam MMC sertifikaları ek bileşenini gerektirir. Ek bileşene, Başlat/Çalıştır menüsü açılarak giriş kutusuna "MMC" yazarak ve Tamam ' a basılarak erişilebilir. Ardından, **Konsol1** penceresinde, **Dosya/Ekle/Kaldır** ek bileşenine gidin, Ekle ' ye tıklayın ve **kullanılabilir tek başına ek bileşen** listesinden **Sertifikalar** ' ı seçin. Son olarak, yönetilecek **bilgisayar hesabı** ' nı seçin ve **Tamam**' a tıklayın. **Sertifikalar** düğümü ek bileşen konsolunda görünür.  
  
 Güven sağlamak için gerekli sertifikalara sahip olmanız gerekir. Aşağıdaki adımlardan önce yeni sertifikalar oluşturma ve yüklemeyi öğrenmek için bkz [. nasıl yapılır: Geliştirme](https://go.microsoft.com/fwlink/?LinkId=158925)sırasında WCF 'de geçici istemci sertifikaları oluşturun ve bunları yükler.  
  
1. A makinesi ' nde, MMC sertifikaları ek bileşenini kullanarak mevcut sertifikayı (certA) Localmachine\(Personal node) ve localmachıneroot deposuna (güvenilen kök sertifika yetkilisi düğümü) içeri aktarın. Belirli bir düğüme bir sertifikayı içeri aktarmak için düğüme sağ tıklayın ve **Tüm görevler/Içeri aktar**' ı seçin.  
  
2. B makinesi 'nde, MMC sertifikaları ek bileşenini kullanarak, özel bir anahtarla bir sertifika sertifikası oluşturun veya alın ve bunu Localmachine\(Personal node) ve localmachıneroot deposuna (güvenilen kök sertifika yetkilisi düğümü) içeri aktarın.  
  
3. Daha önce yapmadıysanız, certA 'ın ortak anahtarını bir dosyaya aktarın.  
  
4. Daha önce yapmadıysanız, certB 'ın ortak anahtarını bir dosyaya aktarın.  
  
### <a name="establishing-mutual-trust-between-machines"></a>Makineler arasında karşılıklı güven oluşturma  
  
1. A makinesinde, certB dosya gösterimini Localmachine\ve Localmachıne\root depolarına aktarın. Bu, makine ile iletişim kurmak için bir güven sertifikası olduğunu bildirir.  
  
2. B makinesinde, certA dosyasını Localmachine\ve Localmachıne\root depolarına aktarın. Bu, B makinesi ile iletişim kurmak için certA güveneceği anlamına gelir.  
  
 Bu adımları tamamladıktan sonra, iki makine arasında güven oluşturulur ve bunlar WS-AT kullanılarak birbirleriyle iletişim kuracak şekilde yapılandırılabilirler.  
  
### <a name="configuring-msdtc-to-use-certificates"></a>MSDTC 'yi sertifikaları kullanacak şekilde yapılandırma  
 WS-AT protokol hizmeti hem istemci hem de sunucu olarak davrandığından, hem gelen bağlantıları dinlemesi hem de giden bağlantıları başlatması gerekir. Bu nedenle, MSDTC 'yi, dış taraflarla iletişim kurarken hangi sertifikanın kullanılacağını ve gelen iletişimi kabul edilirken hangi sertifikaların yetkilendirireceğini bilmesi için yapılandırmanız gerekir.  
  
 Bunu, MMC WS-AT ek bileşenini kullanarak yapılandırabilirsiniz. Bu araç hakkında daha fazla bilgi için [WS-AtomicTransaction YAPıLANDıRMASı MMC ek bileşeni](../../../../docs/framework/wcf/ws-atomictransaction-configuration-mmc-snap-in.md) konusuna bakın. Aşağıdaki adımlarda, MSDTC çalıştıran iki bilgisayar arasında güven oluşturma açıklanır.  
  
1. Makine A 'nın ayarlarını yapılandırın. "Uç nokta sertifikası" için certA öğesini seçin. "Yetkilendirilmiş sertifikalar" için, certB ' yi seçin.  
  
2. Makine B 'nin ayarlarını yapılandırın. "Uç nokta sertifikası" için, certB ' yi seçin. "Yetkilendirilmiş sertifikalar" için, certA ' yı seçin.  
  
> [!NOTE]
> Bir makine başka bir makineye bir ileti gönderdiğinde, gönderici alıcının sertifikasının konu adının ve alıcının makine adının eşleştiğini doğrulamaya çalışır. Bunlar eşleşmiyorsa, sertifika doğrulama başarısız olur ve iki makine iletişim kuramaz.  
>   
>  Bir etki alanına katılmış bir makine için ad, tam etki alanı adıdır. Varsayılan olarak, bir çalışma grubundaki makinenin adı makinenin NetBIOS adıdır. Ancak, iki makine arasında kullanılan bağlantı için varsa, ad bir etki alanı adı sistemi (DNS) soneki de içerebilir.  
>   
>  Makinenin adı değişirse (örneğin, bir çalışma grubu makinesi bir etki alanına katıldığında), sertifikaları yeniden oluşturmanız veya DNS soneklerini el ile yapılandırmanız gerekir.  
  
## <a name="security"></a>Güvenlik  
 MSDTC ve WS ile ilgili ayarlardan bazıları HKLM\Software\Microsoft\MSDTC ve HKLM\Software\Microsoft\WSAT üzerinde kayıt defterine depolandığından, bu kayıt defteri anahtarlarının yalnızca yöneticiler tarafından yazabilmesi için güvenli olduğundan emin olun. Kayıt Defteri Düzenleyicisi aracında, güvenli hale getirmek istediğiniz anahtara sağ tıklayın ve uygun erişim denetimini ayarlamak için **izin** ' ı seçin. Düşük ayrıcalıklı kullanıcılar için önemli anahtarların salt okuma yaptığı sistemin güvenliği ve bütünlüğü açısından önemlidir.  
  
 MSDTC dağıtıldığında, yönetici tüm MSDTC veri değişim güvenliğinin güvende olduğundan emin olmalıdır. Çalışma grubu dağıtımında, işlem altyapısını kötü amaçlı kullanıcılardan yalıtın; küme dağıtımında, küme kayıt defterini güvenli hale getirin.  
  
## <a name="tracing"></a>İzleme  
 WS-AT protokol hizmeti, [WS-AtomicTransaction Yapılandırma MMC ek bileşeni](../../../../docs/framework/wcf/ws-atomictransaction-configuration-mmc-snap-in.md) Aracı kullanılarak etkinleştirilebilecek ve yönetilebilen tümleşik, işleme özgü izlemeyi destekler.  İzlemeler, belirli bir işlem için bir kayıt yapıldığı saati, bir işlemin Terminal durumuna ulaştığı süreyi, her işlem kaydı alındığını belirten verileri içerebilir. Tüm izlemeler, [hizmet Izleme Görüntüleyicisi Aracı (SvcTraceViewer. exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) Aracı kullanılarak görüntülenebilir.  
  
 WS-AT protokol hizmeti Ayrıca ETW izleme oturumu aracılığıyla tümleşik ServiceModel izlemeyi destekler. Bu, mevcut işlem izlemelerinin yanı sıra daha ayrıntılı, iletişime özgü izlemeler sağlar.  Bu ek izlemeleri etkinleştirmek için şu adımları izleyin  
  
1. **Başlat/Çalıştır** menüsünü açın, giriş kutusuna "regedit" yazın ve **Tamam**' ı seçin.  
  
2. **Kayıt defteri Düzenleyicisi**'nde sol bölmedeki şu klasöre gidin, Hkey_Local_Machine\SOFTWARE\Microsoft\WSAT\3.0\  
  
3. Sağ bölmedeki `ServiceModelDiagnosticTracing` değere sağ tıklayın ve **Değiştir**' i seçin.  
  
4. **Değer verisi** girişi kutusuna, etkinleştirmek istediğiniz izleme düzeyini belirtmek için aşağıdaki geçerli değerlerden birini girin.  
  
- 0: kapalı  
  
- 1: kritik  
  
- 3: hata. Bu varsayılan değerdir  
  
- 7: uyarı  
  
- 15: bilgi  
  
- 31: ayrıntılı  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WS-AtomicTransaction Yapılandırma Yardımcı Programı (wsatConfig.exe)](../../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)
- [WS-AtomicTransaction Yapılandırması MMC Ek Bileşeni](../../../../docs/framework/wcf/ws-atomictransaction-configuration-mmc-snap-in.md)
