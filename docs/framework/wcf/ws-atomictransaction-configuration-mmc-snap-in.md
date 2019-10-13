---
title: WS-AtomicTransaction Yapılandırması MMC ek bileşeni
ms.date: 03/30/2017
ms.assetid: 23592973-1d51-44cc-b887-bf8b0d801e9e
ms.openlocfilehash: 926332ac1873db89ce9332075380effdfdc1fc37
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291499"
---
# <a name="ws-atomictransaction-configuration-mmc-snap-in"></a>WS-AtomicTransaction Yapılandırması MMC ek bileşeni
WS-AtomicTransaction Yapılandırması MMC ek bileşeni, hem yerel hem de uzak makinelerde WS-AtomicTransaction ayarlarının bir bölümünü yapılandırmak için kullanılır.  
  
## <a name="remarks"></a>Açıklamalar  
 @No__t-0 veya [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] çalıştırıyorsanız, MMC ek bileşeni **Denetim Masası/Yönetim Araçları/Bileşen Hizmetleri/** **, Bilgisayarım ' a sağ tıklayıp** **Özellikler**' i seçerek bulunabilir. Bu, MSDTC 'yi yapılandırabileceğiniz konumdur. Yapılandırma için kullanılabilen seçenekler **ws-at** sekmesi altında gruplandırılır.  
  
 Windows Vista veya [!INCLUDE[lserver](../../../includes/lserver-md.md)] çalıştırıyorsanız, MMC ek bileşeni **Başlat** düğmesine tıklayıp **arama** kutusuna `dcomcnfg.exe` yazarak bulunabilir. MMC açıldığında, **bilgisayar \ dağıtılmış işlem Koordinatlıklasör** düğümü ' ne gidin, sağ tıklayın ve **Özellikler**' i seçin. Yapılandırma için kullanılabilen seçenekler **ws-at** sekmesi altında gruplandırılır.  
  
 Önceki adımlar, yerel bir makineyi yapılandırmak için ek bileşeni başlatmak üzere kullanılır. Uzak bir makineyi yapılandırmak istiyorsanız, uzak makinenin adını **Denetim Masası/Yönetim Araçları/Bileşen Hizmetleri/** olarak bulmanız ve [!INCLUDE[wxp](../../../includes/wxp-md.md)] veya [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] ' yi çalıştırıyorsanız benzer adımları gerçekleştirmeniz gerekir. Windows Vista veya [!INCLUDE[lserver](../../../includes/lserver-md.md)] çalıştırıyorsanız, Vista ve [!INCLUDE[lserver](../../../includes/lserver-md.md)] için önceki adımları izleyin, ancak uzak bilgisayarın düğümü altındaki **Dağıtılmış işlem Koordinatı\local DTC** düğümünü kullanın.  
  
 Araç tarafından sunulan kullanıcı arabirimini kullanmak için, aşağıdaki yolda bulunan WsatUI. dll dosyasını kaydetmeniz gerekir.  
  
 **%PROGRAMFILES%\Microsoft SDKs\Windows\v6.0\Bin\WsatUI.dll**  
  
 Kayıt aşağıdaki komutla yapılabilir.  
  
```console
regasm.exe /codebase WsatUI.dll  
```  
  
 Temel WS-AtomicTransaction ayarlarını değiştirmek için bu aracı kullanabilirsiniz. Örneğin, WS-AtomicTransaction protokol desteğini etkinleştirebilir ve devre dışı bırakabilir, WS-AT için HTTP bağlantı noktalarını yapılandırabilir, HTTP bağlantı noktasına bir SSL sertifikası bağlayabilir, sertifika konu adlarını belirterek sertifikaları yapılandırabilir, Izleme modunu seçebilir ve ayarlayabilirsiniz Varsayılan ve en fazla zaman aşımları.  
  
 Yalnızca yerel makinede WS-AtomicTransaction desteğini yapılandırmanız gerekiyorsa, bu aracın komut satırı sürümünü kullanabilirsiniz. Komut satırı aracı hakkında daha fazla bilgi için, bkz. [WS-AtomicTransaction Yapılandırma yardımcı programı (wsatConfig. exe)](../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md) konusu.  
  
 Hem MMC ek bileşeni hem de komut satırı aracının tüm WS-AT ayarlarını yapılandırmayı desteklemediğini bilmelisiniz. Bu ayarlar yalnızca kayıt defteri doğrudan değiştirilerek düzenlenebilir. Bu kayıt defteri ayarları hakkında daha fazla bilgi için bkz. [WS Atomik Işlem desteğini yapılandırma](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md).  
  
### <a name="user-interface-description"></a>Kullanıcı arabirimi açıklaması  
 **WS Atomik Işlem ağı desteğini etkinleştir**:  
  
 Bu onay kutusunun işaretlenmesi, bu ek bileşenin tüm GUI bileşenlerini sunar veya devre dışı bırakır.  
  
 Bu kutuyu seçmeden önce, Ağ DTC erişiminin gelen veya giden iletişimle veya her ikisiyle de etkinleştirildiğinden emin olun. Bu değer, MSDTC ek bileşeninin **güvenlik** sekmesinde doğrulanabilir.  
  
#### <a name="network-group-box"></a>Ağ grubu kutusu  
 HTTPS bağlantı noktasını ve ağ grubunda SSL şifrelemesi gibi ek güvenlik ayarlarını belirtebilirsiniz. DTC ağ Işlemleri etkinleştirilmemişse bu grup devre dışıdır (gri renkte).  
  
 **HTTPS bağlantı noktası**  
  
 Bu, WS-AT için kullanılan HTTPS bağlantı noktasının değeridir. Değer, 1-65535 aralığında bir sayı olmalıdır (geçerli bir bağlantı noktasını göstermek için olduğu gibi). HTTP bağlantı noktasını değiştirmek, HTTP hizmet yapılandırmasını değiştirir, bu da önceden kullanılan WS-AT hizmet adresinin yayımlandığı ve yeni bir WS-AT hizmet adresinin yeni bağlantı noktasına göre kaydedildiği anlamına gelir. Ayrıca, yeni seçilen bağlantı noktası SSL şifrelemesi için seçili olan sertifikayla şifrelenir.  
  
> [!NOTE]
> Bu aracı çalıştırmadan önce güvenlik duvarını zaten etkinleştirdiyseniz, bağlantı noktası otomatik olarak özel durum listesine kaydedilir. Bu aracı çalıştırmadan önce güvenlik duvarı devre dışıysa, güvenlik duvarıyla ilgili başka hiçbir şey yapılandırılmadı.  
  
 WS-AT yapılandırıldıktan sonra güvenlik duvarını etkinleştirirseniz, bu aracı yeniden çalıştırmanız ve bu parametreyi kullanarak bağlantı noktası numarasını sağlamanız gerekir. Yapılandırma sonrasında güvenlik duvarını devre dışı bırakırsanız, WS-AT ek giriş olmadan çalışmaya devam eder.  
  
 **Uç nokta sertifikası**  
  
 **Seç** düğmesine tıkladığınızda, yerel makinede mevcut olan sertifikaların bulunduğu bir liste görüntülenir ve bu durumda kullanıcının, SSL şifrelemesi için kullanılabilecek sertifikayı seçmesini sağlayabilirsiniz. Sertifikalar bir özel anahtara sahip olmalıdır. Aksi takdirde, bir hata iletisi alırsınız.  
  
> [!NOTE]
> Seçili bir bağlantı noktası için bir SSL sertifikası ayarladığınızda, varsa, bu bağlantı noktasıyla ilişkili özgün SSL sertifikasının üzerine yazarsınız.  
  
 **Yetkili hesaplar**  
  
 **Seç** düğmesine tıkladığınızda, **katıldaki** **izin verme** veya **reddetme** kutusunu işaretleyerek WS Atomik işlemlere katılabilen kullanıcı veya grubu belirtebileceğiniz Windows Access Control liste Düzenleyicisi çağrılır. izin grubu.  
  
 **Yetkili sertifikalar**  
  
 **Seç** düğmesine tıkladığınızda, LocalMachine 'de Şu anda kullanılabilir olan sertifikaların bir listesi görüntülenir. Daha sonra, hangi sertifika kimliklerinin WS Atomik işlemlere katılmasına izin verileceğini seçebilirsiniz.  
  
#### <a name="timeout-group-box"></a>Zaman aşımı grup kutusu  
 **Zaman aşımı** Grup kutusu, WS Atomik bir işlem için varsayılan ve en büyük zaman aşımını belirtmenize olanak tanır. Giden zaman aşımı için geçerli bir değer 1 ile 3600 arasındadır. Gelen zaman aşımı için geçerli bir değer 0 ile 3600 arasındadır.  
  
#### <a name="tracing-and-logging-group-box"></a>İzleme ve günlüğe kaydetme Grup kutusu  
 **İzleme ve günlüğe kaydetme** Grup kutusu, istenen izleme ve günlüğe kaydetme düzeyini yapılandırmanıza olanak tanır.  
  
 **Seçenekler** düğmesine tıkladığınızda, ek ayarları belirtebileceğiniz bir sayfa çağırılır.  
  
 **Izleme düzeyi** birleşimi kutusu, <xref:System.Diagnostics.TraceLevel> Numaralandırmadaki geçerli bir değer arasından seçim yapmanıza olanak tanır. Ayrıca, Etkinlik izlemeyi, etkinlik yaymayı gerçekleştirmek veya kişisel olarak tanımlanabilir bilgileri toplamak istediğinizi belirtmek için onay kutularını da kullanabilirsiniz.  
  
 Günlüğe kaydetme **oturum** grubu kutusunda günlük oturumlarını da belirtebilirsiniz.  
  
> [!NOTE]
> Başka bir izleme tüketicisi WS-AT İzleme sağlayıcısını kullanırken, izleme olayları için yeni bir günlüğe kaydetme oturumu oluşturamazsınız. Bu süre boyunca günlüğe kaydetmeyi yapılandırma girişimleri, "sağlayıcı etkinleştirilemedi. Hata kodu: 1 ".  
  
 İzleme ve günlüğe kaydetme hakkında daha fazla bilgi için bkz. [Yönetim ve tanılama](../../../docs/framework/wcf/diagnostics/index.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WS Atomik Işlem desteğini yapılandırma](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)
- [WS-AtomicTransaction Yapılandırma yardımcı programı (wsatConfig. exe)](../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)
- [Yönetim ve tanılama](../../../docs/framework/wcf/diagnostics/index.md)
