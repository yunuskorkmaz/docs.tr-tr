---
title: .NET Framework 4 ve 4.5'e Eklenen CLR Barındırma Arabirimleri
ms.date: 03/30/2017
helpviewer_keywords:
- hosting interfaces [.NET Framework], version 4
- .NET Framework 4, hosting interfaces
- interfaces [.NET Framework hosting], version 4
ms.assetid: f6af6116-f5b0-4bda-a276-fffdba70893d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ea95789ea1623985a6a53fcf923b70d7df2ad460
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/18/2019
ms.locfileid: "67170432"
---
# <a name="clr-hosting-interfaces-added-in-the-net-framework-4-and-45"></a>.NET Framework 4 ve 4.5'e Eklenen CLR Barındırma Arabirimleri
Bu bölümde, yönetilmeyen arabirimler açıklanmaktadır. konakları ortak dil çalışma zamanı (CLR) tümleştirme için kullanabileceğiniz bir .NET Framework 4, .NET Framework 4.5 ve sonraki sürümlerinde uygulamalarına. Bu arabirimler, yapılandırmak ve çalışma zamanını bir işleme yüklemek bir konak için yöntemler sağlar.  
  
 Tüm barındırma arabirimleri, .NET Framework 4 ile başlayarak, aşağıdaki özelliklere sahiptir:  
  
- Ömür Yönetimi kullandıkları (`AddRef` ve `Release`), kapsülleme (örtük context) ve `QueryInterface` com gelen  
  
- Aşağıdakiler gibi COM türlerini kullanmazlar `BSTR`, `SAFEARRAY`, veya `VARIANT`.  
  
- Apartman modeli, toplama, veya kayıt defteri etkinleştirme kullanan [CoCreateInstance işlevi](https://go.microsoft.com/fwlink/?LinkId=142894).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [ICLRAppDomainResourceMonitor Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 Bir uygulama etki alanının bellek ve CPU kullanımını denetlemek için yöntemler sağlar.  
  
 [ICLRDomainManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)  
 Varsayılan uygulama etki alanı başlatmak ve başlatma özelliklerini belirtmek için kullanılan uygulama etki alanı yöneticisi belirtmek konak sağlar.  
  
 [ICLRGCManager2 Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)  
 Sağlar [SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) çöp toplama kesim boyutunu ve en büyük boyutu çöp toplama sistemin nesil 0 değerine büyük ayarlamak bir konak sağlayan yöntemi `DWORD`.  
  
 [ICLRMetaHost Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 CLR'nin belirli bir sürümünü döndürmek, tüm yüklü CLRs listesinde, tüm işlem çalışma zamanları listesinde, etkinleştirme arabirimini döndürür ve bir derlemeyi derlemek için kullanılan CLR sürümü bulmak için yöntemler sağlar.  
  
 [ICLRMetaHostPolicy Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)  
 Sağlar [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) CLR arabirimi sağlayan yöntemi temel İlkesi ölçütlerini, yönetilen bir derleme, sürüm ve yapılandırma dosyası.  
  
 [ICLRRuntimeInfo Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 Sürüm, dizin ve yükleme durumu gibi belirli bir çalışma zamanı hakkında bilgi almak için yöntemler sağlar.  
  
 [ICLRStrongName Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)  
 Derlemeleri tanımlayıcı adlarla imzalamak için temel genel statik işlevleri sağlar. Tüm [Iclrstrongname](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) yöntemleri standart COM HRESULTs döndürür.  
  
 [ICLRStrongName2 Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname2-interface.md)  
 SHA-2 karma algoritma (SHA-256, SHA-384 ve SHA-512) güvenli kullanarak güçlü adlar oluşturma olanağı sağlar.  
  
 [ICLRTask2 Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)  
 Tüm işlevlerini sağlar [Iclrtask arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md); Ayrıca, iş parçacığı iptalleri geçerli iş parçacığında geciktirileceği izin vermek için yöntemler sağlar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Kullanım Dışı CLR Barındırma Arabirimleri ve Coclass’ları](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 .NET Framework sürümleri 1.0 ve 1.1 ile sağlanan barındırma arabirimleri açıklar.  
  
 [CLR Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 .NET Framework sürüm 2.0, 3.0 ve 3.5 ile sağlanan barındırma arabirimleri açıklar.  
  
 [Barındırma](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 .NET Framework barındırma tanıtır.
