---
title: WS-AtomicTransaction Yapılandırma Yardımcı Programı (wsatConfig.exe)
ms.date: 03/30/2017
ms.assetid: 1c56cf98-3963-46d5-a4e1-482deae58c58
ms.openlocfilehash: dbd33869de6b1ecee6406dfeede88afc4eca07f1
ms.sourcegitcommit: fe8877e564deb68d77fa4b79f55584ac8d7e8997
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90720497"
---
# <a name="ws-atomictransaction-configuration-utility-wsatconfigexe"></a>WS-AtomicTransaction Yapılandırma Yardımcı Programı (wsatConfig.exe)

WS-AtomicTransaction Yapılandırma yardımcı programı, temel WS-AtomicTransaction destek ayarlarını yapılandırmak için kullanılır.  
  
## <a name="syntax"></a>Syntax  
  
```console  
wsatConfig [Options]  
```  
  
## <a name="remarks"></a>Açıklamalar

 Bu komut satırı aracı, yalnızca yerel bir makinedeki temel WS-AT ayarlarını yapılandırmak için kullanılabilir. Hem yerel hem de uzak makinelerde ayarları yapılandırmanız gerekiyorsa, [WS Atomik Işlem desteğini yapılandırma](./feature-details/configuring-ws-atomic-transaction-support.md)bölümünde AÇıKLANDıĞı gibi MMC ek bileşenini kullanmanız gerekir.  
  
 Komut satırı aracı Windows SDK yükleme konumunda bulunabilir:
  
 %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Iletişim Foundation\wsatConfig.exe
  
 Aşağıdaki tabloda, WS-AtomicTransaction Yapılandırma yardımcı programı (wsatConfig.exe) ile kullanılabilecek seçenekler gösterilmektedir.  
  
> [!NOTE]
> Seçili bir bağlantı noktası için bir SSL sertifikası ayarladığınızda, varsa, bu bağlantı noktasıyla ilişkili özgün SSL sertifikasının üzerine yazarsınız.  
  
|Seçenekler|Description|  
|-------------|-----------------|  
|hesapları\<account,>|WS-AtomicTransaction öğesine katılabilen hesapların virgülle ayrılmış bir listesini belirtir. Bu hesapların geçerliliği denetlenmez.|  
|-accountsCerts: \<thumb>&#124; "Issuer\SubjectName", >|WS-AtomicTransaction ' ye katılabileceğiniz sertifikaların virgülle ayrılmış listesini belirtir. Sertifikalar parmak izi veya Issuer\SubjectName çifti tarafından belirtilir. Eğer boşsa, konu adı için {EMPTY} kullanın.|  
|-endpointCert: <Machine&#124;\<thumb>&#124; "Issuer\SubjectName" >|Makine sertifikasını veya parmak izi veya Issuer\SubjectName çifti tarafından belirtilen başka bir yerel uç nokta sertifikasını kullanır. Boşsa konu adı için {EMPTY} kullanır.|  
|-maxTimeout:\<sec>|Saniye cinsinden en uzun zaman aşımını belirtir. Geçerli değerler 0 ile 3600 arasında geçerlidir.|  
|Network\<enable&#124;disable>|WS-AtomicTransaction ağ desteğini etkinleştirilir veya devre dışı bırakır.|  
|bağ\<portNum>|WS-AtomicTransaction için HTTPS bağlantı noktasını ayarlar.<br /><br /> Bu aracı çalıştırmadan önce güvenlik duvarını zaten etkinleştirdiyseniz, bağlantı noktası otomatik olarak özel durum listesine kaydedilir. Bu aracı çalıştırmadan önce güvenlik duvarı devre dışıysa, güvenlik duvarıyla ilgili başka hiçbir şey yapılandırılmadı.<br /><br /> WS-AT yapılandırıldıktan sonra güvenlik duvarını etkinleştirirseniz, bu aracı yeniden çalıştırmanız ve bu parametreyi kullanarak bağlantı noktası numarasını sağlamanız gerekir. Yapılandırma sonrasında güvenlik duvarını devre dışı bırakırsanız, WS-AT ek giriş olmadan çalışmaya devam eder.|  
|aş\<sec>|Varsayılan zaman aşımını saniye cinsinden belirtir. Geçerli değerler 1 ile 3600 arasında.|  
|-traceActivity:\<enable&#124;disable>|Etkinlik olaylarının izlenmesini etkinleştirilir veya devre dışı bırakır.|  
|-traceLevel: \<Off&#124;Error&#124;Critical&#124;Warning&#124;Information&#124; Verbose&#124;All> }|İzleme düzeyini belirtir.|  
|tracePII\<enable&#124;disable>|Kişisel bilgilerin izlenmesini etkinleştirilir veya devre dışı bırakır.|  
|-traceProp:\<enable&#124;disable>|Yayma olaylarının izlenmesini etkinleştirilir veya devre dışı bırakır.|  
|-yeniden Başlat|Değişiklikleri hemen etkinleştirmek için MSDTC 'yi yeniden başlatır. Bu belirtilmemişse, değişiklikler MSDTC yeniden başlatıldığında geçerli olur.|  
|-göster|Geçerli WS-AtomicTransaction protokol ayarlarını görüntüler.|  
|-virtualServer:\<virtualServer>|DTC kaynak kümesi adını belirtir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WS-AtomicTransaction Kullanma](./feature-details/using-ws-atomictransaction.md)
- [WS-Atomic İşlem Desteğini Yapılandırma](./feature-details/configuring-ws-atomic-transaction-support.md)
