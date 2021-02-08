---
description: 'Hakkında daha fazla bilgi edinin: Silverlight hata ayıklaması'
title: Silverlight'ta Hata Ayıklama
ms.date: 03/30/2017
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 5e903e04-17d0-4014-ac9a-a43330ec8b1c
ms.openlocfilehash: 54a3f7f4b2de867509ff94dafa25c067a78b3ee6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800545"
---
# <a name="silverlight-debugging"></a>Silverlight'ta Hata Ayıklama

Bu bölümdeki konularda, ortak dil çalışma zamanının (CLR) Windows işletim sisteminde veya Macintosh platformunda çalışan Silverlight tabanlı uygulamalarda hata ayıklamayı desteklemek için sağladığı ortam ve arabirimler açıklanır.  
  
## <a name="in-this-section"></a>Bu Bölümde  

 [EnumerateCLRs İşlevi](enumerateclrs-function.md)  
 Bir işlemdeki CLRs 'yi listelemek için bir mekanizma sağlar.  
  
 [CloseCLREnumeration İşlevi](closeclrenumeration-function.md)  
 [EnumerateCLRs işlevi](enumerateclrs-function.md)tarafından döndürülen bir dizi tanıtıcıda bulunan geçerli CLR Continue-Startup olaylarını kapatır ve tanıtıcı ve dize yolu dizileri için belleği serbest bırakır.  
  
 [CreateCoreClrDebugTarget İşlevi](createcoreclrdebugtarget-function.md)  
 İşlem ve çalışma zamanı numaralandırması için uzak hedefe bir bağlantı oluşturur.  
  
 [CreateCordbObject İşlevi](createcordbobject-function.md)  
 Uzak bir işlemde yönetilen bir hata ayıklama oturumunun örneğini oluşturma işlevselliği sağlayan bir hata ayıklayıcı arabirimi oluşturur.  
  
 [CreateVersionStringFromModule İşlevi](createversionstringfrommodule-function.md)  
 Hedef işlemdeki bir CLR yolundan sürüm dizesi oluşturur.  
  
 [CreateDebuggingInterfaceFromVersion İşlevi](createdebugginginterfacefromversion-function-for-silverlight.md)  
 [CreateVersionStringFromModule işlev](createversionstringfrommodule-function.md)işlevinden döndürülen bir CLR sürüm dizesini kabul eder ve karşılık gelen bir hata ayıklayıcı arabirimi döndürür.  
  
 [CoreClrDebugProcInfo Yapısı](coreclrdebugprocinfo-structure.md)  
 Uzak makinede çalışan bir işlemi temsil eder.  
  
 [CoreClrDebugRuntimeInfo Yapısı](coreclrdebugruntimeinfo-structure.md)  
 Uzak makinedeki bir işlemde yüklenen bir CLR örneğini temsil eder.  
  
 [GetStartupNotificationEvent İşlevi](getstartupnotificationevent-function.md)  
 Belirtilen hedef işlemde yüklenen herhangi bir ortak dil çalışma zamanı (CLR) tarafından işaret edilecek bir olay tanıtıcısı oluşturur veya açar.  
  
 [ICoreClrDebugTarget Arabirimi](icoreclrdebugtarget-interface.md)  
 İşlem ve çalışma zamanı numaralandırması için uzak hedefe bir bağlantı oluşturur.  
  
 [InitDbgTransportManager İşlevi](initdbgtransportmanager-function.md)  
 İşlem ve çalışma zamanı numaralandırması için uzak hedefe bağlanmak üzere aktarım yöneticisini başlatır.  
  
 [ShutdownDbgTransportManager İşlevi](shutdowndbgtransportmanager-function.md)  
 Uzak hedef makineye bağlantı için taşıma yöneticisini kapatır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Yardımcı Sınıfları](debugging-coclasses.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama Genel Statik İşlevleri](debugging-global-static-functions.md)
- [Hata Ayıklama Numaralandırmaları](debugging-enumerations.md)
- [Hata Ayıklama Yapıları](debugging-structures.md)
