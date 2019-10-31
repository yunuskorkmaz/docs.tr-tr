---
title: Yönetilmeyen kodla birlikte çalışma
ms.date: 01/17/2018
helpviewer_keywords:
- unmanaged code, interoperation
- managed code, interoperation with unmanaged code
- .NET Framework, interoperation with unmanaged code
- unmanaged code
- interoperation with unmanaged code
- interoperation with unmanaged code, about interoperation
- components [.NET Framework], interoperation with unmanaged code
ms.assetid: ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258
ms.openlocfilehash: cdd8d2781331956289d2b74162e653ba1ee8fad6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73114233"
---
# <a name="interoperating-with-unmanaged-code"></a>Yönetilmeyen kodla birlikte çalışma

.NET Framework, COM bileşenleri, COM+ Hizmetleri, dış tür kitaplıkları ve birçok işletim sistemi hizmeti ile etkileşimi yükseltir. Veri türleri, yöntem imzaları ve hata işleme mekanizmaları, yönetilen ve yönetilmeyen nesne modelleri arasında farklılık gösterir. .NET Framework bileşenleri ve yönetilmeyen kod arasında birlikte çalışabilirlik kolaylaştırmak ve geçiş yolunu kolaylaştırmak için, ortak dil çalışma zamanı hem istemcilerden hem de sunuculardan bu nesne modellerindeki farklılıkları önler.

Çalışma zamanının denetimi altında yürütülen koda yönetilen kod denir. Buna karşılık, çalışma zamanının dışında çalışan koda yönetilmeyen kod denir. COM bileşenleri, ActiveX arabirimleri ve Windows API işlevleri, yönetilmeyen koda örnektir.

## <a name="in-this-section"></a>Bu bölümde

[COM Bileşenlerini .NET Framework'te Gösterme](exposing-com-components.md)  
.NET Framework uygulamalardan COM bileşenlerinin nasıl kullanılacağını açıklar.

[.NET Framework Bileşenlerini COM'da Gösterme](exposing-dotnet-components-to-com.md)  
COM uygulamalarından .NET Framework bileşenlerinin nasıl kullanılacağını açıklar.

[Yönetilmeyen DLL İşlevlerini Kullanma](consuming-unmanaged-dll-functions.md)  
Platform Invoke kullanılarak yönetilmeyen DLL işlevlerinin nasıl çağrılacağını açıklar.

[Birlikte Çalışma için Hazırlama](interop-marshaling.md)  
COM birlikte çalışma ve platform çağırma için hazırlamayı açıklar.

[Nasıl yapılır: HRESULTs ve Özel Durumları Eşleme](how-to-map-hresults-and-exceptions.md)  
Özel durumlar ve HRESULTs arasındaki eşlemeyi açıklar.

[COM Sarmalayıcıları](com-wrappers.md)  
COM birlikte çalışma tarafından sunulan sarmalayıcıları açıklar.

[Tür Eşdeğerliği ve Katıştırılmış Birlikte Çalışma Türleri](type-equivalence-and-embedded-interop-types.md)  
COM türleri için tür bilgilerinin derlemelerde nasıl gömülü olduğunu ve ortak dil çalışma zamanının gömülü COM türlerinin denklik düzeyini nasıl belirlediğini açıklar.

[Nasıl yapılır: Tlbimp.exe Kullanarak Birincil Birlikte Çalışma Bütünleştirilmiş Kodları Oluşturma](how-to-generate-primary-interop-assemblies-using-tlbimp-exe.md)  
*Tlbimp. exe* (tür kitaplığı alma) kullanarak birincil birlikte çalışma derlemelerinin nasıl oluşturulacağını açıklar.

[Nasıl yapılır: Birincil Birlikte Çalışma Bütünleştirilmiş Kodlarını Kaydetme](how-to-register-primary-interop-assemblies.md)  
Projelerinizde başvurmadan önce birincil birlikte çalışma derlemelerinin nasıl kaydedileceği açıklanmaktadır.

[Kayıtsız COM Birlikte Çalışma](registration-free-com-interop.md)  
COM birlikte çalışabilirliğine Windows kayıt defteri kullanmadan bileşenleri nasıl etkinleştirebileceği açıklanmaktadır.

[Nasıl yapılır: Kayıtsız Etkinleştirme için .NET Framework Tabanlı COM Bileşenlerini Yapılandırma](configure-net-framework-based-com-components-for-reg.md)  
Bir uygulama bildirimi oluşturmayı ve bir bileşen bildirimi oluşturmayı ve eklemeyi açıklar.
