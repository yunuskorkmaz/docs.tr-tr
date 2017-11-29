---
title: "Silverlight'ta Hata Ayıklama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 5e903e04-17d0-4014-ac9a-a43330ec8b1c
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bf39d2dd12207d594c7bf5bd5b249d82c3f15d3c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="silverlight-debugging"></a>Silverlight'ta Hata Ayıklama
Bu bölümdeki konular, ortam ve ortak dil çalışma zamanı (CLR) Windows işletim sisteminde veya Macintosh platformunda çalışan Silverlight tabanlı uygulamalarında hata ayıklama desteği sağlayan arabirimler açıklanmaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [EnumerateCLRs işlevi](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)  
 Bir işlemde CLRs numaralandırma için bir mekanizma sağlar.  
  
 [CloseCLREnumeration işlevi](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md)  
 İşleyici tarafından döndürülen bir dizi bulunan herhangi bir geçerli CLR devam başlangıç olayı kapatır [EnumerateCLRs işlevi](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)ve tanıtıcısı ve dize yolu diziler için bellek boşaltır.  
  
 [CreateCoreClrDebugTarget işlevi](../../../../docs/framework/unmanaged-api/debugging/createcoreclrdebugtarget-function.md)  
 İşlem ve çalışma zamanı numaralandırması için uzaktan bir hedef için bir bağlantı oluşturur.  
  
 [CreateCordbObject işlevi](../../../../docs/framework/unmanaged-api/debugging/createcordbobject-function.md)  
 Yönetilen hata ayıklama oturumu uzak bir işlem üzerinde başlatmasını için işlevsellik sağlayan bir hata ayıklayıcı arabirimi oluşturur.  
  
 [CreateVersionStringFromModule işlevi](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)  
 Bir hedef işlemde CLR yolundan bir sürüm dizesi oluşturur.  
  
 [Createdebuggingınterfacefromversion işlevi](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md)  
 Bir CLR sürüm dizesi döndürdü kabul [CreateVersionStringFromModule işlevi](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)işlev ve karşılık gelen bir hata ayıklayıcı arabirimini döndürür.  
  
 [Coreclrdebugprocınfo yapısı](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md)  
 Uzak makinede çalışan bir işlemin temsil eder.  
  
 [Coreclrdebugruntimeınfo yapısı](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md)  
 Bir işlemde bir uzak makinede yüklü bir CLR örneğini temsil eder.  
  
 [GetStartupNotificationEvent işlevi](../../../../docs/framework/unmanaged-api/debugging/getstartupnotificationevent-function.md)  
 Sonra belirtilen hedef işleminde yüklenen tüm ortak dil çalışma zamanı (CLR) tarafından bildirim yapılan bir olay tanıtıcısı açar veya oluşturur.  
  
 [Icoreclrdebugtarget arabirimi](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)  
 İşlem ve çalışma zamanı numaralandırması için uzaktan bir hedef için bir bağlantı oluşturur.  
  
 [Initdbgtransportmanager işlevi](../../../../docs/framework/unmanaged-api/debugging/initdbgtransportmanager-function.md)  
 İşlem ve çalışma zamanı numaralandırması için uzaktan bir hedef bağlanmak için Aktarım Yöneticisi'ni başlatır.  
  
 [ShutdownDbgTransportManager işlevi](../../../../docs/framework/unmanaged-api/debugging/shutdowndbgtransportmanager-function.md)  
 Bağlantı uzak hedef makine için Aktarım Yöneticisi'ni kapatır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklama coclass'ları](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
 [Hata ayıklama arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Hata ayıklama genel statik işlevleri](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
 [Hata ayıklama numaralandırmaları](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [Hata ayıklama yapıları](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
