---
title: "Yönetilmeyen kod ile birlikte çalışma"
ms.date: 01/17/2018
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
helpviewer_keywords:
- unmanaged code, interoperation
- managed code, interoperation with unmanaged code
- .NET Framework, interoperation with unmanaged code
- unmanaged code
- interoperation with unmanaged code
- interoperation with unmanaged code, about interoperation
- components [.NET Framework], interoperation with unmanaged code
ms.assetid: ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 38c569633304ed9e6f86e7a04ef7b0dfa79b6704
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="interoperating-with-unmanaged-code"></a>Yönetilmeyen kod ile birlikte çalışma

.NET Framework COM bileşenleri, COM + Hizmetleri, dış tür kitaplıklarını ve birçok işletim sistemi Hizmetleri ile etkileşim yükseltir. Veri türleri, yöntem imzaları ve hata işleme mekanizmaları yönetilen ve yönetilmeyen nesne modelleri arasında farklılık gösterir. Yönetilmeyen kod ile .NET Framework bileşenleri arasındaki birlikte çalışabilirlik basitleştirmek ve geçiş yolunun kolaylaştırmak için istemciler ve sunucular bu nesne modelleri farklılıkları ortak dil çalışma zamanı gizler.

Çalışma zamanı denetiminde yürütülen kodu yönetilen kod adı verilir. Buna karşılık, çalışma zamanı dışında çalışan kod yönetilmeyen kod denir. COM bileşenlerini, ActiveX arabirimleri ve Win32 API işlevleri yönetilmeyen kod gösterilebilir.

## <a name="in-this-section"></a>Bu bölümde

[COM Bileşenlerini .NET Framework'te Gösterme](exposing-com-components.md)  
.NET Framework uygulamalarında COM bileşenlerini kullanmayı açıklar.

[.NET Framework Bileşenlerini COM'da Gösterme](exposing-dotnet-components-to-com.md)  
COM uygulamaları .NET Framework bileşenlerini kullanmayı açıklar.

[Yönetilmeyen DLL İşlevlerini Kullanma](consuming-unmanaged-dll-functions.md)  
Yönetilmeyen çağrılacağını açıklar platformu kullanılarak DLL işlevleri çağırma.

[Birlikte Çalışma için Hazırlama](interop-marshaling.md)  
COM birlikte çalışma ve platform çağırma için hazırlamayı açıklar.

[Nasıl yapılır: HRESULTs ve Özel Durumları Eşleme](how-to-map-hresults-and-exceptions.md)  
Özel durumlar ve HRESULTs arasında eşleme açıklar.

[COM Sarmalayıcıları](com-wrappers.md)  
COM birlikte çalışma tarafından sağlanan sarmalayıcıları açıklar.

[Tür Eşdeğerliği ve Katıştırılmış Birlikte Çalışma Türleri](type-equivalence-and-embedded-interop-types.md)  
Derlemeleri COM türleri için tür bilgisi nasıl katıştırılır ve ortak dil çalışma zamanı katıştırılmış COM türlerini eşdeğer nasıl belirlediğini açıklar.

[Nasıl yapılır: Tlbimp.exe Kullanarak Birincil Birlikte Çalışma Bütünleştirilmiş Kodları Oluşturma](how-to-generate-primary-interop-assemblies-using-tlbimp-exe.md)  
Kullanarak birincil birlikte çalışma derlemeleri üretmek açıklar *Tlbimp.exe* (tür kitaplığı içeri Aktarıcı).

[Nasıl yapılır: Birincil Birlikte Çalışma Bütünleştirilmiş Kodlarını Kaydetme](how-to-register-primary-interop-assemblies.md)  
Birincil birlikte çalışma derlemeleri projelerinizde başvuru önce kaydetmeniz açıklar.

[Kayıtsız COM Birlikte Çalışma](registration-free-com-interop.md)  
Windows Kayıt Defteri'ni kullanarak olmadan COM birlikte çalışma bileşenleri nasıl etkinleştirebilir açıklar.

[Nasıl yapılır: Kayıtsız Etkinleştirme için .NET Framework Tabanlı COM Bileşenlerini Yapılandırma](configure-net-framework-based-com-components-for-reg.md)  
Bir uygulama bildirimi oluşturmak ve oluşturmak ve bir bileşen bildirimi katıştırmak açıklar.
