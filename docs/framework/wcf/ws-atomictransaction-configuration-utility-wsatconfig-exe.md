---
title: WS-AtomicTransaction Yapılandırma Yardımcı Programı (wsatConfig.exe)
ms.date: 03/30/2017
ms.assetid: 1c56cf98-3963-46d5-a4e1-482deae58c58
ms.openlocfilehash: 224777fe5bf8e8d832ede582f460a8fa6ae6181d
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802338"
---
# <a name="ws-atomictransaction-configuration-utility-wsatconfigexe"></a>WS-AtomicTransaction Yapılandırma Yardımcı Programı (wsatConfig.exe)
WS-AtomicTransaction Yapılandırma yardımcı programı, temel WS-AtomicTransaction destek ayarlarını yapılandırmak için kullanılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
wsatConfig [Options]  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Bu komut satırı aracı, yalnızca yerel bir makinedeki temel WS-AT ayarlarını yapılandırmak için kullanılabilir. Hem yerel hem de uzak makinelerde ayarları yapılandırmanız gerekiyorsa, [WS Atomik Işlem desteğini yapılandırma](./feature-details/configuring-ws-atomic-transaction-support.md)bölümünde AÇıKLANDıĞı gibi MMC ek bileşenini kullanmanız gerekir.  
  
 Komut satırı aracı, Windows SDK yükleme konumunda bulunabilir, özellikle,  
  
 %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\wsatConfig.exe  
  
 [!INCLUDE[wxp](../../../includes/wxp-md.md)] veya [!INCLUDE[ws2003](../../../includes/ws2003-md.md)]çalıştırıyorsanız, WsatConfig. exe ' yi çalıştırmadan önce bir güncelleştirmeyi indirmeniz gerekir. Bu güncelleştirme hakkında daha fazla bilgi için bkz. [Windows Communication Foundation Güncelleştirmesi (KB912817)](https://www.microsoft.com/en-us/download/details.aspx?id=21520).  
  
 Aşağıdaki tabloda, WS-AtomicTransaction Yapılandırma yardımcı programı (wsatConfig. exe) ile kullanılabilecek seçenekler gösterilmektedir.  
  
> [!NOTE]
> Seçili bir bağlantı noktası için bir SSL sertifikası ayarladığınızda, varsa, bu bağlantı noktasıyla ilişkili özgün SSL sertifikasının üzerine yazarsınız.  
  
|Seçenekler|Açıklama|  
|-------------|-----------------|  
|-hesaplar:\<hesap, >|WS-AtomicTransaction öğesine katılabilen hesapların virgülle ayrılmış bir listesini belirtir. Bu hesapların geçerliliği denetlenmez.|  
|-accountsCerts:\<Thumb >&#124;"Issuer\SubjectName", >|WS-AtomicTransaction ' ye katılabileceğiniz sertifikaların virgülle ayrılmış listesini belirtir. Sertifikalar parmak izi veya Issuer\SubjectName çifti tarafından belirtilir. Eğer boşsa, konu adı için {EMPTY} kullanın.|  
|-endpointCert: < makine&#124;\<Thumb >&#124;"Issuer\SubjectName" >|Makine sertifikasını veya parmak izi veya Issuer\SubjectName çifti tarafından belirtilen başka bir yerel uç nokta sertifikasını kullanır. Boşsa konu adı için {EMPTY} kullanır.|  
|-maxTimeout:\<sn >|Saniye cinsinden en uzun zaman aşımını belirtir. Geçerli değerler 0 ile 3600 arasında geçerlidir.|  
|-Ağ:\<devre&#124;dışı bırak > Etkinleştir|WS-AtomicTransaction ağ desteğini etkinleştirilir veya devre dışı bırakır.|  
|-bağlantı noktası:\<portNum >|WS-AtomicTransaction için HTTPS bağlantı noktasını ayarlar.<br /><br /> Bu aracı çalıştırmadan önce güvenlik duvarını zaten etkinleştirdiyseniz, bağlantı noktası otomatik olarak özel durum listesine kaydedilir. Bu aracı çalıştırmadan önce güvenlik duvarı devre dışıysa, güvenlik duvarıyla ilgili başka hiçbir şey yapılandırılmadı.<br /><br /> WS-AT yapılandırıldıktan sonra güvenlik duvarını etkinleştirirseniz, bu aracı yeniden çalıştırmanız ve bu parametreyi kullanarak bağlantı noktası numarasını sağlamanız gerekir. Yapılandırma sonrasında güvenlik duvarını devre dışı bırakırsanız, WS-AT ek giriş olmadan çalışmaya devam eder.|  
|-zaman aşımı:\<sn >|Varsayılan zaman aşımını saniye cinsinden belirtir. Geçerli değerler 1 ile 3600 arasında.|  
|-traceActivity:\<devre&#124;dışı bırak > Etkinleştir|Etkinlik olaylarının izlenmesini etkinleştirilir veya devre dışı bırakır.|  
|-traceLevel:\<kapalı&#124;hata&#124;kritik&#124;Uyarı&#124;bilgileri&#124; &#124;tüm >}|İzleme düzeyini belirtir.|  
|-tracePII:\<devre&#124;dışı bırak > Etkinleştir|Kişisel bilgilerin izlenmesini etkinleştirilir veya devre dışı bırakır.|  
|-traceProp:\<enable&#124;devre dışı >|Yayma olaylarının izlenmesini etkinleştirilir veya devre dışı bırakır.|  
|-yeniden Başlat|Değişiklikleri hemen etkinleştirmek için MSDTC 'yi yeniden başlatır. Bu belirtilmemişse, değişiklikler MSDTC yeniden başlatıldığında geçerli olur.|  
|-göster|Geçerli WS-AtomicTransaction protokol ayarlarını görüntüler.|  
|-virtualServer: virtualServer\<|DTC kaynak kümesi adını belirtir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WS-AtomicTransaction Kullanma](./feature-details/using-ws-atomictransaction.md)
- [WS-Atomic İşlem Desteğini Yapılandırma](./feature-details/configuring-ws-atomic-transaction-support.md)
