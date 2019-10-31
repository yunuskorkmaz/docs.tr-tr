---
title: Silverlight'ta Hata Ayıklama
ms.date: 03/30/2017
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 5e903e04-17d0-4014-ac9a-a43330ec8b1c
ms.openlocfilehash: b7af03197a43976c47b7ddc30346d622e6b97207
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139142"
---
# <a name="silverlight-debugging"></a>Silverlight'ta Hata Ayıklama
Bu bölümdeki konularda, ortak dil çalışma zamanının (CLR) Windows işletim sisteminde veya Macintosh platformunda çalışan Silverlight tabanlı uygulamalarda hata ayıklamayı desteklemek için sağladığı ortam ve arabirimler açıklanır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [EnumerateCLRs İşlevi](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)  
 Bir işlemdeki CLRs 'yi listelemek için bir mekanizma sağlar.  
  
 [CloseCLREnumeration İşlevi](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md)  
 [EnumerateCLRs işlevi](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)tarafından döndürülen bir dizi tanıtıcıda bulunan geçerli CLR Continue-Startup olaylarını kapatır ve tanıtıcı ve dize yolu dizileri için belleği serbest bırakır.  
  
 [CreateCoreClrDebugTarget İşlevi](../../../../docs/framework/unmanaged-api/debugging/createcoreclrdebugtarget-function.md)  
 İşlem ve çalışma zamanı numaralandırması için uzak hedefe bir bağlantı oluşturur.  
  
 [CreateCordbObject İşlevi](../../../../docs/framework/unmanaged-api/debugging/createcordbobject-function.md)  
 Uzak bir işlemde yönetilen bir hata ayıklama oturumunun örneğini oluşturma işlevselliği sağlayan bir hata ayıklayıcı arabirimi oluşturur.  
  
 [CreateVersionStringFromModule İşlevi](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)  
 Hedef işlemdeki bir CLR yolundan sürüm dizesi oluşturur.  
  
 [CreateDebuggingInterfaceFromVersion İşlevi](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md)  
 [CreateVersionStringFromModule işlev](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)işlevinden döndürülen bir CLR sürüm dizesini kabul eder ve karşılık gelen bir hata ayıklayıcı arabirimi döndürür.  
  
 [CoreClrDebugProcInfo Yapısı](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md)  
 Uzak makinede çalışan bir işlemi temsil eder.  
  
 [CoreClrDebugRuntimeInfo Yapısı](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md)  
 Uzak makinedeki bir işlemde yüklenen bir CLR örneğini temsil eder.  
  
 [GetStartupNotificationEvent İşlevi](../../../../docs/framework/unmanaged-api/debugging/getstartupnotificationevent-function.md)  
 Belirtilen hedef işlemde yüklenen herhangi bir ortak dil çalışma zamanı (CLR) tarafından işaret edilecek bir olay tanıtıcısı oluşturur veya açar.  
  
 [ICoreClrDebugTarget Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)  
 İşlem ve çalışma zamanı numaralandırması için uzak hedefe bir bağlantı oluşturur.  
  
 [InitDbgTransportManager İşlevi](../../../../docs/framework/unmanaged-api/debugging/initdbgtransportmanager-function.md)  
 İşlem ve çalışma zamanı numaralandırması için uzak hedefe bağlanmak üzere aktarım yöneticisini başlatır.  
  
 [ShutdownDbgTransportManager İşlevi](../../../../docs/framework/unmanaged-api/debugging/shutdowndbgtransportmanager-function.md)  
 Uzak hedef makineye bağlantı için taşıma yöneticisini kapatır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Coclass’ları](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Hata Ayıklama Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
- [Hata Ayıklama Sabit Listeleri](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [Hata Ayıklama Yapıları](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
