---
title: .NET Framework 4 ve 4.5'e Eklenen CLR Barındırma Arabirimleri
ms.date: 03/30/2017
helpviewer_keywords:
- hosting interfaces [.NET Framework], version 4
- .NET Framework 4, hosting interfaces
- interfaces [.NET Framework hosting], version 4
ms.assetid: f6af6116-f5b0-4bda-a276-fffdba70893d
ms.openlocfilehash: a524c0b0e01fbde95ce2341874511960b3e5738e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616859"
---
# <a name="clr-hosting-interfaces-added-in-the-net-framework-4-and-45"></a>.NET Framework 4 ve 4.5'e Eklenen CLR Barındırma Arabirimleri
Bu bölümde, yönetilmeyen ana bilgisayarların .NET Framework 4, .NET Framework 4,5 ve sonraki sürümlerindeki ortak dil çalışma zamanını (CLR) bütünleştirmek için kullanabileceği arabirimler açıklanmaktadır. Bu arabirimler, bir ana bilgisayarın çalışma zamanını yapılandırmak ve bir işleme yüklemek için yöntemler sağlar.  
  
 .NET Framework 4 ' te başlayarak, tüm barındırma arabirimleri aşağıdaki özelliklere sahiptir:  
  
- Yaşam süresi yönetimi ( `AddRef` ve `Release` ), kapsülleme (örtük bağlam) ve com ile kullanılır `QueryInterface` .  
  
- , Veya gibi COM türlerini kullanmaz `BSTR` `SAFEARRAY` `VARIANT` .  
  
- [Cocreateınstance işlevini](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)kullanan hiçbir Grup modeli, toplama veya kayıt defteri etkinleştirmesi yoktur.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [ICLRAppDomainResourceMonitor Arabirimi](iclrappdomainresourcemonitor-interface.md)  
 Bir uygulama etki alanının belleğini ve CPU kullanımını denetleyen yöntemler sağlar.  
  
 [ICLRDomainManager Arabirimi](iclrdomainmanager-interface.md)  
 Ana bilgisayarın varsayılan uygulama etki alanını başlatmak için kullanılacak uygulama etki alanı yöneticisini belirtmesini ve başlatma özelliklerini belirtmesini sağlar.  
  
 [ICLRGCManager2 Arabirimi](iclrgcmanager2-interface.md)  
 , Bir konağın çöp toplama segmentinin boyutunu ve çöp toplama sisteminin 1. kuşak en büyük boyut olan 0 ' dan büyük değerlere ayarlanmasını sağlayan [SetGCStartupLimitsEx](iclrgcmanager2-setgcstartuplimitsex-method.md) yöntemini sağlar `DWORD` .  
  
 [ICLRMetaHost Arabirimi](iclrmetahost-interface.md)  
 CLR 'nin belirli bir sürümünü döndüren, tüm yüklü CLRs 'leri listeleme, tüm işlem içi çalışma zamanlarını listeleme, etkinleştirme arabirimini geri döndürme ve bir derlemeyi derlemek için kullanılan CLR sürümünü bulma yöntemlerini sağlar.  
  
 [ICLRMetaHostPolicy Arabirimi](iclrmetahostpolicy-interface.md)  
 İlke ölçütlerini, yönetilen derlemeyi, sürümü ve yapılandırma dosyasını temel alan bir CLR arabirimi sağlayan [GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) metodunu sağlar.  
  
 [ICLRRuntimeInfo Arabirimi](iclrruntimeinfo-interface.md)  
 Sürüm, dizin ve yükleme durumu dahil olmak üzere belirli bir çalışma zamanı hakkında bilgi döndüren yöntemler sağlar.  
  
 [ICLRStrongName Arabirimi](iclrstrongname-interface.md)  
 Derlemeleri tanımlayıcı adlarla imzalamak için temel genel statik işlevler sağlar. Tüm [ICLRStrongName](iclrstrongname-interface.md) YÖNTEMLERI standart com HResults döndürür.  
  
 [ICLRStrongName2 Arabirimi](iclrstrongname2-interface.md)  
 , SHA-2 güvenli karma algoritmaları grubunu (SHA-256, SHA-384 ve SHA-512) kullanarak tanımlayıcı adlar oluşturma olanağı sağlar.  
  
 [ICLRTask2 Arabirimi](iclrtask2-interface.md)  
 [ICLRTask arabiriminin](iclrtask-interface.md)tüm işlevlerini sağlar; Ayrıca, geçerli iş parçacığında iş parçacığı iptal vermesinin ertelenmesini sağlayan yöntemler sağlar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Kullanım Dışı CLR Barındırma Arabirimleri ve Yardımcı Sınıfları](deprecated-clr-hosting-interfaces-and-coclasses.md)  
 1,0 ve 1,1 .NET Framework sürümleriyle birlikte sunulan barındırma arabirimlerini açıklar.  
  
 [CLR Barındırma Arabirimleri](clr-hosting-interfaces.md)  
 2,0, 3,0 ve 3,5 .NET Framework sürümleriyle birlikte sunulan barındırma arabirimlerini açıklar.  
  
 [Barındırma](index.md)  
 .NET Framework barındırılmasını tanıtır.
