---
title: "WS-AtomicTransaction Yapılandırma Yardımcı Programı (wsatConfig.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c56cf98-3963-46d5-a4e1-482deae58c58
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 59b56b542a1624f1bae332ab91e1ac835aa47c8b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ws-atomictransaction-configuration-utility-wsatconfigexe"></a>WS-AtomicTransaction Yapılandırma Yardımcı Programı (wsatConfig.exe)
WS-AtomicTransaction yapılandırma yardımcı programı'nı temel WS-AtomicTransaction destek ayarlarını yapılandırmak için kullanılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
wsatConfig [Options]  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Bu komut satırı aracı, bir yerel makinede yalnızca temel WS-AT ayarlarını yapılandırmak için kullanılabilir. Hem yerel hem de uzak makinelerde ayarlarını yapılandırmak varsa, MMC ek bileşenini açıklandığı gibi kullanmalısınız [WS-Atomic işlem desteğini yapılandırma](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md).  
  
 Komut satırı aracı Windows SDK yükleme konumunda, özellikle bulunabilir,  
  
 %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows iletişim Foundation\wsatConfig.exe  
  
 Çalıştırıyorsanız, [!INCLUDE[wxp](../../../includes/wxp-md.md)] veya [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], WsatConfig.exe çalıştırmadan önce bir güncelleştirmeyi yüklemelidir. Bu güncelleştirme hakkında daha fazla bilgi için bkz: [güncelleştirme Commerce Server 2007 (KB912817)](http://go.microsoft.com/fwlink/?LinkId=95340) ve [kullanılabilirlik, Windows XP COM + Düzeltme Toplaması Paketi 13](http://go.microsoft.com/fwlink/?LinkId=95341).  
  
 Aşağıdaki tabloda, WS-AtomicTransaction yapılandırma yardımcı programı ile (wsatConfig.exe) kullanılabilir seçenekler gösterilmektedir.  
  
> [!NOTE]
>  Seçilen bağlantı noktası için bir SSL sertifikası ayarladığınızda, varsa, bu bağlantı noktasıyla ilişkili özgün SSL sertifikası üzerine yazın.  
  
|Seçenekler|Açıklama|  
|-------------|-----------------|  
|-hesapları:\<hesabı >|WS-AtomicTransaction katılabilir hesapları virgülle ayrılmış listesini belirtir. Bu hesapları geçerliliğini işaretlenmemiştir.|  
|-accountsCerts:\<Flash > &#124; " Issuer\SubjectName">|WS-AtomicTransaction katılabilir sertifikaları virgülle ayrılmış bir listesini belirtir. Sertifika parmak izi veya Issuer\SubjectName çifti tarafından belirtilir. Boş ise, konu adı için {EMPTY} kullanın.|  
|-endpointCert: < makine &#124; \<Flash > &#124; " Issuer\SubjectName">|Makine sertifikası veya başka bir yerel uç nokta sertifika parmak izi ya da Issuer\SubjectName çifti tarafından belirtilen kullanır. Boşsa konu adı için {EMPTY} kullanır.|  
|-maxTimeout:\<sn >|En uzun zaman aşımı saniye cinsinden belirtir. Geçerli değerler 0 ile 3600 arasındadır.|  
|-Ağ:\<etkinleştir &#124; devre dışı bırakma >|Etkinleştirir veya WS-AtomicTransaction ağ desteğini devre dışı bırakır.|  
|-bağlantı noktası:\<portNum >|WS-AtomicTransaction için HTTPS bağlantı noktasını ayarlar.<br /><br /> Bu aracı çalıştırmadan önce güvenlik duvarı zaten etkinleştirdiyseniz, bağlantı noktası özel durum listesinde otomatik olarak kaydedilir. Bu aracı çalıştırmadan önce güvenlik duvarı devre dışıysa, ek bir şey Güvenlik Duvarı'nı ilgili olarak yapılandırılır.<br /><br /> WS-AT yapılandırdıktan sonra Güvenlik Duvarı'nı etkinleştirirseniz, bu aracı yeniden çalıştırın ve bu parametresini kullanarak bağlantı noktası numarası girmeniz gerekir. Yapılandırdıktan sonra Güvenlik Duvarı'nı devre dışı bırakırsanız, WS-AT ek girişi olmadan çalışmaya devam eder.|  
|-zaman aşımı:\<sn >|Varsayılan zaman aşımı saniye cinsinden belirtir. Geçerli değerler 1 ile 3600 ' dir.|  
|-traceActivity:\<etkinleştir &#124; devre dışı bırakma >|Etkinleştirir veya etkinlik olaylarını izlemeyi devre dışı bırakır.|  
|-traceLevel:\<devre dışı &#124; Hata &#124; Kritik &#124; Uyarı &#124; bilgileri &#124; Ayrıntılı &#124; Tüm >}|İzleme düzeyini belirtir.|  
|-TracePII:\<etkinleştir &#124; devre dışı bırakma >|Etkinleştirir veya kişisel olarak tanımlanabilen bilgilere izlemeyi devre dışı bırakır.|  
|-traceProp:\<etkinleştir &#124; devre dışı bırakma >|Etkinleştirir veya yayma olaylarını izlemeyi devre dışı bırakır.|  
|-Yeniden Başlat|Değişiklikler hemen etkinleştirmeye MSDTC yeniden başlatır. Bu belirtilmezse MSDTC yeniden başlatıldığında değişiklikleri etkili olur.|  
|-Göster|Geçerli WS-AtomicTransaction Protokolü ayarlarını görüntüler.|  
|-virtualServer:\<virtualServer >|DTC kaynak küme adını belirtir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WS-AtomicTransaction kullanma](../../../docs/framework/wcf/feature-details/using-ws-atomictransaction.md)  
 [WS-Atomic işlem desteğini yapılandırma](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)
