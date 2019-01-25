---
title: WS-AtomicTransaction Yapılandırması MMC Ek Bileşeni
ms.date: 03/30/2017
ms.assetid: 23592973-1d51-44cc-b887-bf8b0d801e9e
ms.openlocfilehash: 8dfb9c9a9f6a007e65dbf819d347f335a93d1749
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54573078"
---
# <a name="ws-atomictransaction-configuration-mmc-snap-in"></a>WS-AtomicTransaction Yapılandırması MMC Ek Bileşeni
WS-AtomicTransaction yapılandırması MMC ek bileşeninde hem yerel hem de uzak makinelerde bir kısmını WS-AtomicTransaction ayarlarını yapılandırmak için kullanılır.  
  
## <a name="remarks"></a>Açıklamalar  
 Çalıştırıyorsanız [!INCLUDE[wxp](../../../includes/wxp-md.md)] veya [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], MMC ek bileşeninde giderek bulunabilir **Denetim Masası/Yönetim Araçları/Component Services /**, sağ **Bilgisayarım**, ve seçme **özellikleri**. Bu MSDTC yapılandırabileceğiniz aynı konumdur. İçin yapılandırma seçenekleri altında gruplanır **WS-AT** sekmesi.  
  
 Windows Vista çalıştırıyorsanız veya [!INCLUDE[lserver](../../../includes/lserver-md.md)], MMC ek bileşeninde bulunabilir tıklayarak **Başlat** düğmesini ve yazarak `dcomcnfg.exe` içinde **arama** kutusu. MMC açıldığında gidin **My Computer\Distributed işlem Coordinator\Local DTC** düğümünü sağ tıklatın ve seçin **özellikleri**. İçin yapılandırma seçenekleri altında gruplanır **WS-AT** sekmesi.  
  
 Önceki adımları eklentisini yerel makine yapılandırma başlatmak için kullanılır. Uzak bir makineyi yapılandırmak istiyorsanız, Uzak makinenin adını bulun **Denetim Masası/Yönetim Araçları/Component Services /** ve çalıştırıyorsanız benzer adımları [!INCLUDE[wxp](../../../includes/wxp-md.md)] veya [!INCLUDE[ws2003](../../../includes/ws2003-md.md)]. Windows Vista çalıştırıyorsanız veya [!INCLUDE[lserver](../../../includes/lserver-md.md)], Vista için önceki adımları izleyin ve [!INCLUDE[lserver](../../../includes/lserver-md.md)], ancak **dağıtılmış işlem Coordinator\Local DTC** uzak bilgisayarın düğümü altında düğüm.  
  
 Araç tarafından sağlanan kullanıcı arabirimi kullanmak için şu yolda bulunur WsatUI.dll dosyayı kaydetmek zorunda,  
  
 **%PROGRAMFILES%\Microsoft SDKs\Windows\v6.0\Bin\WsatUI.dll**  
  
 Kayıt, aşağıdaki komutla yapılabilir.  
  
```Output  
regasm.exe /codebase WsatUI.dll  
```  
  
 Temel WS-AtomicTransaction ayarlarını değiştirmek için bu aracı kullanabilirsiniz. Örneğin, etkinleştirmek ve WS-AtomicTransaction Protokolü desteğini devre dışı, HTTP bağlantı noktalarını WS-AT yapılandırabilir, HTTP bağlantı noktasına bir SSL sertifikası bağlama, sertifikaları, sertifika konu adları belirterek yapılandırma, izleme modunu seçin ve ayarlayın Varsayılan ve en büyük zaman aşımı.  
  
 Yalnızca yerel makine üzerinde WS-AtomicTransaction destek yapılandırmanız gerekir, bu aracı komut satırı sürümünü kullanabilirsiniz. Komut satırı aracı hakkında daha fazla bilgi için bkz. [WS-AtomicTransaction yapılandırma yardımcı programı (wsatConfig.exe)](../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md) konu.  
  
 MMC ek bileşenini hem de komut satırı aracı tüm WS-AT ayarlarını yapılandırma desteklemediğini bilmeniz gerekir. Bu ayarlar, yalnızca kayıt defterini doğrudan değiştirme tarafından düzenlenebilir. Bu kayıt defteri ayarları hakkında daha fazla bilgi için bkz. [WS-Atomic işlem desteğini yapılandırma](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md).  
  
### <a name="user-interface-description"></a>Kullanıcı arabirimi açıklaması  
 **WS-Atomic işlem ağ desteğini etkinleştir**:  
  
 Bu onay kutusunu geçiş etkinleştirir veya GUI bileşenlerinin tümünü bu eklenti devre dışı bırakır.  
  
 Bu onay kutusunu önce ağ DTC erişimi, gelen veya giden iletişimi veya her ikisi ile etkin olduğundan emin olun. İçinde bu değer doğrulanabilir **güvenlik** MSDTC ek bileşenini sekmesi.  
  
#### <a name="network-group-box"></a>Ağ Grup kutusu  
 Ağ grubuna HTTPS bağlantı noktası ve SSL şifrelemesi gibi ek güvenlik ayarlarını belirtebilirsiniz. Bu Grup (gri) devre dışı bırakıldı ağ işlemlerini DTC etkin değilse.  
  
 **HTTPS bağlantı noktası**  
  
 Bu değer WS-AT için kullanılan HTTPS bağlantı noktası oluşturulur. Değer (geçerli bir bağlantı noktası temsil etmek için) 1-65535 aralığında bir sayı olmalıdır. HTTP bağlantı noktasını değiştirmek, önceden kullanılmış WS-AT Hizmeti adresi serbest bırakılır ve yeni bağlantı noktasına yeni bir WS-AT hizmet adresi tabanlı olarak kaydedilir anlamına gelir HTTP hizmet yapılandırması değiştirir. Ayrıca, yeni seçilen bağlantı noktası şu anda seçili sertifikayla SSL şifrelemesi için şifrelenir.  
  
> [!NOTE]
>  Bu aracı çalıştırmadan önce güvenlik duvarını zaten etkinleştirdiyseniz, bağlantı noktası özel durum listesine otomatik olarak kaydedilir. Bu aracı çalıştırmadan önce güvenlik duvarını devre dışıysa, başka bir şey ile ilgili güvenlik duvarı yapılandırılır.  
  
 WS-AT yapılandırdıktan sonra Güvenlik Duvarı'nı etkinleştirirseniz, bu aracı yeniden çalıştırın ve bu parametre kullanarak bağlantı noktası numarası girmeniz gerekir. Yapılandırdıktan sonra Güvenlik Duvarı'nı devre dışı bırakırsanız WS-AT ek giriş çalışmaya devam eder.  
  
 **Uç noktası sertifika**  
  
 Tıklayarak **seçin** düğmesi, yerel makinede SSL şifrelemesi için kullanılacak sertifikayı seçmek kullanıcının, şu anda kullanılabilir sertifikaların listesini görüntüler. Sertifika bir özel anahtara sahip olmalıdır. Aksi takdirde bir hata iletisi alırsınız.  
  
> [!NOTE]
>  Seçilen bir bağlantı noktası için SSL sertifikası ayarladığınızda, özgün SSL sertifikası varsa, bu bağlantı noktasıyla ilişkili üzerine yazın.  
  
 **Yetkili hesaplar**  
  
 Tıklayarak **seçin** düğmesi çağırır belirtebileceğiniz katılabilir kullanıcı grubunun WS-Atomic işlemleri kontrol ederek Windows erişim denetimi listesi düzenleyici **izin** veya **Reddet** kutusunda **katılabilir** izin grubu.  
  
 **Yetkili sertifikaları**  
  
 Tıklayarak **seçin** düğmesi LocalMachine üzerinde şu anda kullanılabilir sertifikaların listesini görüntüler. Ardından, hangi sertifika kimlikleri WS-Atomic işlemlere katılmasına izin verilen seçebilirsiniz.  
  
#### <a name="timeout-group-box"></a>Zaman aşımı grup kutusu  
 **Zaman aşımı** grup kutusu WS-Atomic işlem için varsayılan ve en büyük zaman aşımı belirtmenizi sağlar. Giden zaman aşımı için geçerli bir değer 1 ile 3600 arasında ' dir. Gelen zaman aşımı için geçerli bir değer, 0 ila 3600 arasında ' dir.  
  
#### <a name="tracing-and-logging-group-box"></a>İzleme ve günlüğe kaydetme grup kutusu  
 **İzleme ve günlüğe kaydetme** grup kutusu istenen izleme ve günlüğe kaydetme düzeyi yapılandırmanıza olanak tanır.  
  
 Tıklayarak **seçenekleri** düğmesi ek ayarlar belirleyebileceğiniz bir sayfa çağırır.  
  
 **İzleme düzeyini** birleşimi kutusu geçerli bir değerden seçmenize olanak sağlar <xref:System.Diagnostics.TraceLevel> sabit listesi. Onay kutularını, etkinlik izleme, Etkinlik yayma gerçekleştirmek veya kişisel olarak tanımlanabilir bilgileri toplamak isteyip istemediğinizi belirtmek için de kullanabilirsiniz.  
  
 Günlüğe kaydetme oturumlarda belirtebilirsiniz **günlüğe kaydetme oturumu** grup kutusu.  
  
> [!NOTE]
>  Başka bir izleme tüketici WS-AT izleme sağlayıcısı kullanılırken olayları izlemek için yeni bir günlüğe kaydetme oturumu oluşturulamıyor. Bu süre boyunca günlüğe kaydetmeyi yapılandırmak için her türlü girişim "Sağlayıcı etkinleştirilemedi. hata iletisi sonuçlanır. Hata kodu: 1".  
  
 İzleme ve günlüğe kaydetme hakkında daha fazla bilgi için bkz: [yönetim ve tanılama](../../../docs/framework/wcf/diagnostics/index.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [WS-Atomic İşlem Desteğini Yapılandırma](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)
- [WS-AtomicTransaction Yapılandırma Yardımcı Programı (wsatConfig.exe)](../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)
- [Yönetim ve Tanılama](../../../docs/framework/wcf/diagnostics/index.md)
