---
title: .NET Framework 4 ve 4.5'e Eklenen CLR Barındırma Arabirimleri
ms.date: 03/30/2017
helpviewer_keywords:
- hosting interfaces [.NET Framework], version 4
- .NET Framework 4, hosting interfaces
- interfaces [.NET Framework hosting], version 4
ms.assetid: f6af6116-f5b0-4bda-a276-fffdba70893d
ms.openlocfilehash: aea88430d8f83234a1568bcaf433c2a75492e23a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73195921"
---
# <a name="clr-hosting-interfaces-added-in-the-net-framework-4-and-45"></a>.NET Framework 4 ve 4.5'e Eklenen CLR Barındırma Arabirimleri
Bu bölümde, yönetilmeyen ana bilgisayarların .NET Framework 4, .NET Framework 4,5 ve sonraki sürümlerindeki ortak dil çalışma zamanını (CLR) bütünleştirmek için kullanabileceği arabirimler açıklanmaktadır. Bu arabirimler, bir ana bilgisayarın çalışma zamanını yapılandırmak ve bir işleme yüklemek için yöntemler sağlar.  
  
 .NET Framework 4 ' te başlayarak, tüm barındırma arabirimleri aşağıdaki özelliklere sahiptir:  
  
- Yaşam süresi yönetimi (`AddRef` ve `Release`), kapsülleme (örtük bağlam) ve COM 'dan `QueryInterface` kullanırlar.  
  
- `BSTR`, `SAFEARRAY`veya `VARIANT`gibi COM türlerini kullanmaz.  
  
- [Cocreateınstance işlevini](https://go.microsoft.com/fwlink/?LinkId=142894)kullanan hiçbir Grup modeli, toplama veya kayıt defteri etkinleştirmesi yoktur.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [ICLRAppDomainResourceMonitor Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 Bir uygulama etki alanının belleğini ve CPU kullanımını denetleyen yöntemler sağlar.  
  
 [ICLRDomainManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)  
 Ana bilgisayarın varsayılan uygulama etki alanını başlatmak için kullanılacak uygulama etki alanı yöneticisini belirtmesini ve başlatma özelliklerini belirtmesini sağlar.  
  
 [ICLRGCManager2 Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)  
 , Bir konağın çöp toplama kesiminin boyutunu ve çöp toplama sisteminin 1. kuşak en büyük boyutunu `DWORD`daha büyük değerlere ayarlayabilmesine olanak tanıyan [SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) yöntemini sağlar.  
  
 [ICLRMetaHost Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 CLR 'nin belirli bir sürümünü döndüren, tüm yüklü CLRs 'leri listeleme, tüm işlem içi çalışma zamanlarını listeleme, etkinleştirme arabirimini geri döndürme ve bir derlemeyi derlemek için kullanılan CLR sürümünü bulma yöntemlerini sağlar.  
  
 [ICLRMetaHostPolicy Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)  
 İlke ölçütlerini, yönetilen derlemeyi, sürümü ve yapılandırma dosyasını temel alan bir CLR arabirimi sağlayan [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) metodunu sağlar.  
  
 [ICLRRuntimeInfo Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 Sürüm, dizin ve yükleme durumu dahil olmak üzere belirli bir çalışma zamanı hakkında bilgi döndüren yöntemler sağlar.  
  
 [ICLRStrongName Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)  
 Derlemeleri tanımlayıcı adlarla imzalamak için temel genel statik işlevler sağlar. Tüm [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) YÖNTEMLERI standart com HResults döndürür.  
  
 [ICLRStrongName2 Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname2-interface.md)  
 , SHA-2 güvenli karma algoritmaları grubunu (SHA-256, SHA-384 ve SHA-512) kullanarak tanımlayıcı adlar oluşturma olanağı sağlar.  
  
 [ICLRTask2 Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)  
 [ICLRTask arabiriminin](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)tüm işlevlerini sağlar; Ayrıca, geçerli iş parçacığında iş parçacığı iptal vermesinin ertelenmesini sağlayan yöntemler sağlar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Kullanım Dışı CLR Barındırma Arabirimleri ve Coclass’ları](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 1,0 ve 1,1 .NET Framework sürümleriyle birlikte sunulan barındırma arabirimlerini açıklar.  
  
 [CLR Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 2,0, 3,0 ve 3,5 .NET Framework sürümleriyle birlikte sunulan barındırma arabirimlerini açıklar.  
  
 [Barındırma](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 .NET Framework barındırılmasını tanıtır.
