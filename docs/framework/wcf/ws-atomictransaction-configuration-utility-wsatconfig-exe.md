---
title: WS-AtomicTransaction Yapılandırma Yardımcı Programı (wsatConfig.exe)
ms.date: 03/30/2017
ms.assetid: 1c56cf98-3963-46d5-a4e1-482deae58c58
ms.openlocfilehash: 31b2b3cf16857bf08a4f8d09f47f80d9b34a53b8
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43659966"
---
# <a name="ws-atomictransaction-configuration-utility-wsatconfigexe"></a>WS-AtomicTransaction Yapılandırma Yardımcı Programı (wsatConfig.exe)
WS-AtomicTransaction yapılandırma yardımcı programını temel WS-AtomicTransaction destek ayarları yapılandırmak için kullanılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
wsatConfig [Options]  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Bu komut satırı aracı, yalnızca yerel makine içinde temel WS-AT ayarlarını yapılandırmak için kullanılabilir. Hem yerel hem de uzak makinelerde ayarlarını yapılandırmak varsa, MMC ek bileşeninde açıklandığı gibi kullanmalısınız [WS-Atomic işlem desteğini yapılandırma](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md).  
  
 Komut satırı aracını Windows SDK'sını yükleme konumunda, özellikle bulunabilir,  
  
 %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows iletişimi Foundation\wsatConfig.exe  
  
 Çalıştırıyorsanız [!INCLUDE[wxp](../../../includes/wxp-md.md)] veya [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], WsatConfig.exe çalıştırmadan önce bir güncelleştirme karşıdan yüklemeniz gerekir. Bu güncelleştirme hakkında daha fazla bilgi için bkz. [(KB912817) Commerce Server 2007 için güncelleştirme](https://go.microsoft.com/fwlink/?LinkId=95340) ve [kullanılabilirliği, Windows XP COM + Düzeltme dökümü paket 13](https://go.microsoft.com/fwlink/?LinkId=95341).  
  
 Aşağıdaki tabloda WS-AtomicTransaction yapılandırma yardımcı programı ile (wsatConfig.exe) kullanılabilir seçenekler gösterilmektedir.  
  
> [!NOTE]
>  Seçilen bir bağlantı noktası için SSL sertifikası ayarladığınızda, özgün SSL sertifikası varsa, bu bağlantı noktasıyla ilişkili üzerine yazın.  
  
|Seçenekler|Açıklama|  
|-------------|-----------------|  
|-hesapları:\<hesabı >|WS-AtomicTransaction katılabilir hesapları, virgülle ayrılmış listesini belirtir. Bu hesaplar geçerliliğini denetlenmez.|  
|-accountsCerts:\<thumb >&#124;"Issuer\SubjectName" >|WS-AtomicTransaction katılabilir sertifikaları, virgülle ayrılmış listesini belirtir. Sertifika parmak izi veya Issuer\SubjectName çifti tarafından belirtilir. Boşsa, konu adı için {boş} kullanın.|  
|-endpointCert: < makine&#124;\<thumb >&#124;"Issuer\SubjectName" >|Makine sertifikası veya başka bir yerel uç nokta sertifika parmak izi veya Issuer\SubjectName çifti tarafından belirtilen kullanır. Boş ise konu adı için {boş} kullanır.|  
|-maxTimeout:\<sn >|En uzun zaman aşımı saniye cinsinden belirtir. Geçerli değerler 0 ile 3600 arasındadır.|  
|-Ağ:\<etkinleştirme&#124;devre dışı >|Etkinleştirir veya WS-AtomicTransaction ağ desteği devre dışı bırakır.|  
|-bağlantı noktası:\<portNum >|HTTPS bağlantı noktası WS-AtomicTransaction için ayarlar.<br /><br /> Bu aracı çalıştırmadan önce güvenlik duvarı zaten etkinleştirdiyseniz, bağlantı noktası özel durum listesine otomatik olarak kaydedilir. Bu aracı çalıştırmadan önce güvenlik duvarı devre dışıysa, başka bir şey ile ilgili güvenlik duvarı yapılandırılır.<br /><br /> Güvenlik Duvarı WS-AT yapılandırdıktan sonra etkinleştirirseniz, bu aracı yeniden çalıştırın ve bu parametre kullanarak bağlantı noktası numarası girmeniz gerekir. Yapılandırdıktan sonra güvenlik duvarı devre dışı bırakırsanız WS-AT ek giriş çalışmaya devam eder.|  
|-zaman aşımı:\<sn >|Varsayılan zaman aşımını saniye cinsinden belirtir. Geçerli değerler 1 ile 3600:.|  
|-traceActivity:\<etkinleştirme&#124;devre dışı >|Etkinleştirir veya etkinlik olaylarını izlemeyi devre dışı bırakır.|  
|-traceLevel:\<kapalı&#124;hata&#124;kritik&#124;uyarı&#124;bilgi&#124; ayrıntılı&#124;tüm >}|İzleme düzeyini belirtir.|  
|-TracePII:\<etkinleştirme&#124;devre dışı >|Etkinleştirir veya kişisel olarak tanımlanabilen bilgilerin izlemeyi devre dışı bırakır.|  
|-traceProp:\<etkinleştirme&#124;devre dışı >|Etkinleştirir veya yayma olaylarını izlemeyi devre dışı bırakır.|  
|-Yeniden Başlat|Değişiklikler hemen etkinleştirmeye MSDTC yeniden başlatır. Bu seçenek belirtilmezse MSDTC yeniden başlatıldığında değişiklikler geçerli olacaktır.|  
|-Göster|Geçerli WS-AtomicTransaction protokol ayarlarını görüntüler.|  
|-virtualServer:\<virtualServer >|DTC kaynak kümesi adını belirtir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WS-AtomicTransaction Kullanma](../../../docs/framework/wcf/feature-details/using-ws-atomictransaction.md)  
 [WS-Atomic İşlem Desteğini Yapılandırma](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)
