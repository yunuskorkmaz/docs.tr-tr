---
title: Silverlight'ta Hata Ayıklama
ms.date: 03/30/2017
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 5e903e04-17d0-4014-ac9a-a43330ec8b1c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d20bc002e52c3c6a42b45c0d1c5d559e65dc52c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59113704"
---
# <a name="silverlight-debugging"></a>Silverlight'ta Hata Ayıklama
Bu bölümdeki konularda, ortam ve ortak dil çalışma zamanı (CLR), Windows işletim sisteminde veya Macintosh platformunda çalışan Silverlight tabanlı uygulamaların hata ayıklama desteği sağlayan arabirimler açıklanmaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [EnumerateCLRs İşlevi](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)  
 Bir işlemde CLRs numaralandırmak için bir mekanizma sağlar.  
  
 [CloseCLREnumeration İşlevi](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md)  
 Bir dizi tarafından döndürülen tanıtıcı bulunan herhangi bir geçerli CLR devam başlangıç olayları kapatır [EnumerateCLRs işlevi](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)ve tanıtıcı ve dize yolu diziler için belleği serbest bırakır.  
  
 [CreateCoreClrDebugTarget İşlevi](../../../../docs/framework/unmanaged-api/debugging/createcoreclrdebugtarget-function.md)  
 Bir uzak hedef işlemi ve çalışma zamanı numaralandırması için bir bağlantı oluşturur.  
  
 [CreateCordbObject İşlevi](../../../../docs/framework/unmanaged-api/debugging/createcordbobject-function.md)  
 Uzak işlem üzerinde yönetilen hata ayıklama oturumu oluşturmak için işlevsellik sağlar. bir hata ayıklayıcı arabirim oluşturur.  
  
 [CreateVersionStringFromModule İşlevi](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)  
 Hedef işlemdeki CLR yoldan bir sürüm dizesi oluşturur.  
  
 [CreateDebuggingInterfaceFromVersion İşlevi](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md)  
 Sağlayıcıdan döndürülen bir CLR sürüm dizesi kabul eden [CreateVersionStringFromModule işlevi](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)işlev ve karşılık gelen bir hata ayıklayıcı arabirimini döndürür.  
  
 [CoreClrDebugProcInfo Yapısı](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md)  
 Uzak bir makinede çalışan bir işlemi temsil eder.  
  
 [CoreClrDebugRuntimeInfo Yapısı](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md)  
 Bir işlem uzak bir makinede yüklü olduğu bir CLR örneğini temsil eder.  
  
 [GetStartupNotificationEvent İşlevi](../../../../docs/framework/unmanaged-api/debugging/getstartupnotificationevent-function.md)  
 Oluşturur veya üzerine belirtilen hedef işlemde yüklenmekte olan tüm ortak dil çalışma zamanı (CLR) tarafından sinyal bir olay işleyici açılır.  
  
 [ICoreClrDebugTarget Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)  
 Bir uzak hedef işlemi ve çalışma zamanı numaralandırması için bir bağlantı oluşturur.  
  
 [InitDbgTransportManager İşlevi](../../../../docs/framework/unmanaged-api/debugging/initdbgtransportmanager-function.md)  
 İşlem ve çalışma zamanı numaralandırması için bir uzak hedef bağlanmak için Aktarım Yöneticisi'ni başlatır.  
  
 [ShutdownDbgTransportManager İşlevi](../../../../docs/framework/unmanaged-api/debugging/shutdowndbgtransportmanager-function.md)  
 Bağlantı için bir uzak hedef makine aktarım Yöneticisi'ni kapatır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Yardımcı Sınıfları](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Hata Ayıklama Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
- [Hata Ayıklama Numaralandırmaları](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [Hata Ayıklama Yapıları](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
