---
title: WS-AtomicTransaction Yapılandırması MMC Ek Bileşeni
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 23592973-1d51-44cc-b887-bf8b0d801e9e
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2e8b127e0d3c241a1e37ac2161d9fadcea990425
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="ws-atomictransaction-configuration-mmc-snap-in"></a>WS-AtomicTransaction Yapılandırması MMC Ek Bileşeni
WS-AtomicTransaction yapılandırması MMC ek bileşenini hem yerel hem de uzak makinelerde bir kısmı WS-AtomicTransaction ayarlarını yapılandırmak için kullanılır.  
  
## <a name="remarks"></a>Açıklamalar  
 Çalıştırıyorsanız, [!INCLUDE[wxp](../../../includes/wxp-md.md)] veya [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], MMC ek bileşenini e gidilerek bulunabilir **Denetim Masası/Yönetimsel Araçlar/Bileşen Hizmetleri /**, sağ **Bilgisayarım**, ve seçme **özellikleri**. Bu MSDTC yapılandırabileceğiniz konumdur. Yapılandırma için kullanılabilir seçenekleri altında gruplandırılır **WS-AT** sekmesi.  
  
 Windows Vista çalıştırıyorsanız veya [!INCLUDE[lserver](../../../includes/lserver-md.md)], MMC ek bileşeninde bulunabilir tıklayarak **Başlat** düğmesine tıklayın ve yazarak `dcomcnfg.exe` içinde **arama** kutusu. MMC açıldığında gidin **My Computer\Distributed işlem Coordinator\Local DTC** düğümünü sağ tıklatın ve seçin **özellikleri**. Yapılandırma için kullanılabilir seçenekleri altında gruplandırılır **WS-AT** sekmesi.  
  
 Önceki adımlar yerel makine yapılandırma eklentisi başlatmak için kullanılır. Bir uzak makine yapılandırmak istiyorsanız, Uzak makinenin adında bulun **Denetim Masası/Yönetimsel Araçlar/Bileşen Hizmetleri /** ve çalıştırıyorsanız, benzer adımları [!INCLUDE[wxp](../../../includes/wxp-md.md)] veya [!INCLUDE[ws2003](../../../includes/ws2003-md.md)]. Windows Vista çalıştırıyorsanız veya [!INCLUDE[lserver](../../../includes/lserver-md.md)], Vista için önceki adımları izleyin ve [!INCLUDE[lserver](../../../includes/lserver-md.md)], ancak **dağıtılmış işlem Coordinator\Local DTC** düğümü altında uzaktaki bilgisayarın düğümü.  
  
 Aracı tarafından sağlanan kullanıcı arabirimi kullanmak için aşağıdaki yolda bulunur WsatUI.dll dosyasını kaydetmek sahip olduğunuz  
  
 **%PROGRAMFILES%\Microsoft SDKs\Windows\v6.0\Bin\WsatUI.dll**  
  
 Kayıt aşağıdaki komutu tarafından yapılabilir.  
  
```Output  
regasm.exe /codebase WsatUI.dll  
```  
  
 Temel WS-AtomicTransaction ayarlarını değiştirmek için bu aracı kullanabilirsiniz. Örneğin, etkinleştirmek ve WS-AtomicTransaction Protokolü desteğini devre dışı bırakın, WS-AT için HTTP bağlantı noktalarını yapılandırmak, bir SSL sertifikası HTTP bağlantı noktasına bağlayın, sertifikalar sertifika konu adları belirterek yapılandırabilir, izleme modunu seçin ve ayarlayın Varsayılan ve en büyük zaman aşımı.  
  
 WS-AtomicTransaction desteği yalnızca yerel makinede yapılandırmanız gerekir, bu aracı komut satırı sürümünü kullanabilirsiniz. Komut satırı aracı hakkında daha fazla bilgi için bkz: [WS-AtomicTransaction yapılandırma yardımcı programı (wsatConfig.exe)](../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md) konu.  
  
 MMC ek bileşenini hem de komut satırı aracı tüm WS-AT ayarlarını yapılandırmayı desteklemez olduğunu bilmeniz gerekir. Bu ayarlar yalnızca kayıt defterini doğrudan değiştirerek düzenlenebilir. Bu kayıt defteri ayarları hakkında daha fazla bilgi için bkz: [WS-Atomic işlem desteğini yapılandırma](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md).  
  
### <a name="user-interface-description"></a>Kullanıcı arabirimi açıklaması  
 **WS-Atomic işlem ağ desteğini etkinleştirme**:  
  
 Bu onay kutusunu geçiş etkinleştirir veya GUI bileşenlerinin tümünü bu ek bileşen, devre dışı bırakır.  
  
 Bu onay kutusunu önce ağ DTC erişimi gelen veya giden iletişim veya her ikisi ile etkin olduğundan emin olun. İçinde bu değer doğrulanabilir **güvenlik** MSDTC ek bileşenini sekmesinde.  
  
#### <a name="network-group-box"></a>Ağ Grup kutusu  
 SSL şifreleme gibi ek güvenlik ayarları ve HTTPS bağlantı noktası ağ grubunda belirtebilirsiniz. Bu Grup (gri) devre dışı DTC ağ işlemlerini etkin değilse.  
  
 **HTTPS bağlantı noktası**  
  
 WS-AT için kullanılan HTTPS bağlantı noktası değeri budur. Değer (geçerli bir bağlantı noktası temsil etmek için) 1-65535 aralığında bir sayı olmalıdır. HTTP bağlantı noktasını değiştirmek daha önce kullanılan WS-AT Hizmeti adresi serbest bırakılır ve yeni bağlantı noktasına yeni bir WS-AT hizmet adresi tabanlı olarak kaydedilir anlamına gelir HTTP hizmet yapılandırmasını değiştirir. Ayrıca, yeni seçilen bağlantı noktası şu anda seçili sertifikayla SSL şifrelemesi için şifrelenir.  
  
> [!NOTE]
>  Bu aracı çalıştırmadan önce güvenlik duvarını zaten etkinleştirdiyseniz, bağlantı noktası özel durum listesinde otomatik olarak kaydedilir. Bu aracı çalıştırmadan önce güvenlik duvarını devre dışıysa, ek bir şey Güvenlik Duvarı'nı ilgili olarak yapılandırılır.  
  
 WS-AT yapılandırdıktan sonra Güvenlik Duvarı'nı etkinleştirirseniz, bu aracı yeniden çalıştırın ve bu parametresini kullanarak bağlantı noktası numarası girmeniz gerekir. Yapılandırdıktan sonra Güvenlik Duvarı'nı devre dışı bırakırsanız, WS-AT ek girişi olmadan çalışmaya devam eder.  
  
 **Son nokta sertifikası**  
  
 Tıklatarak **seçin** düğmesi yerel makinedeki kullanıcının SSL şifreleme için kullanılan sertifikayı seçmek, şu anda kullanılabilir sertifikalarla bir liste görüntüler. Sertifika bir özel anahtara sahip olmalıdır. Aksi takdirde bir hata iletisi alırsınız.  
  
> [!NOTE]
>  Seçilen bağlantı noktası için bir SSL sertifikası ayarladığınızda, varsa, bu bağlantı noktasıyla ilişkili özgün SSL sertifikası üzerine yazın.  
  
 **Yetkili hesaplar**  
  
 Tıklatarak **seçin** düğmesi çağırır belirtebileceğiniz katılabilir kullanıcı grubunun WS-Atomic işlemleri denetleyerek Windows erişim denetimi listesi düzenleyici **izin** veya **Reddetme** kutusunda **katılabilir** izin grubu.  
  
 **Yetkili sertifikaları**  
  
 Tıklatarak **seçin** düğmesi, LocalMachine üzerinde şu anda kullanılabilir sertifikaların listesini görüntüler. Daha sonra hangi sertifika kimlikleri WS Atomik işlemlere katılmasına izin verilen da seçebilirsiniz.  
  
#### <a name="timeout-group-box"></a>Zaman aşımı grup kutusu  
 **Zaman aşımı** grup kutusu WS-Atomic işlemleri için varsayılan ve en büyük zaman aşımı belirtmenize olanak verir. Giden zaman aşımı için geçerli bir değer 1 ile 3600 arasında ' dir. Gelen zaman aşımı için geçerli bir değer, 0 ile 3600 arasında ' dir.  
  
#### <a name="tracing-and-logging-group-box"></a>İzleme ve grup kutusu günlüğe kaydetme  
 **İzleme ve günlüğe kaydetme** grup kutusu istenen izleme ve günlüğe kaydetme düzeyi yapılandırmanıza olanak sağlar.  
  
 Tıklatarak **seçenekleri** düğmesi ek ayarlar belirtebileceğiniz bir sayfa çağırır.  
  
 **İzleme düzeyi** birleşimi kutusu geçerli her değerini seçmenize olanak verir <xref:System.Diagnostics.TraceLevel> numaralandırması. Etkinlik izleme, Etkinlik yayma gerçekleştirmek veya kişisel olarak tanımlanabilir bilgileri toplamak isteyip istemediğinizi belirtmek için onay kutularını da kullanabilirsiniz.  
  
 Günlüğe kaydetme oturumlarında da belirtebilirsiniz **günlüğü oturum** grup kutusu.  
  
> [!NOTE]
>  Başka bir izleme tüketici WS-AT izleme sağlayıcısı kullanırken, olayları izlemek için yeni bir günlük oturumu oluşturulamıyor. Hata iletisinde "Sağlayıcı etkinleştirme başarısız oldu. Bu süre boyunca günlüğe kaydetmeyi yapılandırmak için her türlü girişim sonuçları Hata kodu: 1".  
  
 İzleme ve kaydetme hakkında daha fazla bilgi için bkz: [yönetim ve tanılama](../../../docs/framework/wcf/diagnostics/index.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WS-Atomic İşlem Desteğini Yapılandırma](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)  
 [WS-AtomicTransaction Yapılandırma Yardımcı Programı (wsatConfig.exe)](../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)  
 [Yönetim ve Tanılama](../../../docs/framework/wcf/diagnostics/index.md)
