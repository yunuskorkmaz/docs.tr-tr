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
ms.openlocfilehash: 12183f390a5178f038c6dd2122a72a33e31ae0ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457959"
---
# <a name="interoperating-with-unmanaged-code"></a>Yönetilmeyen kodla birlikte çalışma

.NET Framework, COM bileşenleri, COM+ hizmetleri, dış tür kitaplıkları ve birçok işletim sistemi hizmetiyle etkileşimi teşvik eder. Veri türleri, yöntem imzaları ve hata işleme mekanizmaları yönetilen ve yönetilmeyen nesne modelleri arasında değişir. .NET Framework bileşenleri ile yönetilmeyen kod arasındaki etkileşimi basitleştirmek ve geçiş yolunu kolaylaştırmak için, ortak dil çalışma süresi bu nesne modellerinden hem istemcilerden hem de sunuculardan gizlenir.

Çalışma zamanının denetimi altında çalışan koda yönetilen kod denir. Tersine, çalışma zamanı dışında çalışan kod yönetilmeyen kod olarak adlandırılır. COM bileşenleri, ActiveX arabirimleri ve Windows API işlevleri yönetilmeyen kod örnekleridir.

## <a name="in-this-section"></a>Bu bölümde

[COM Bileşenlerini .NET Framework'te Gösterme](exposing-com-components.md)  
.NET Framework uygulamalarından COM bileşenlerinin nasıl kullanılacağını açıklar.

[.NET Framework Bileşenlerini COM'da Gösterme](exposing-dotnet-components-to-com.md)  
COM uygulamalarından .NET Framework bileşenlerinin nasıl kullanılacağını açıklar.

[Yönetilmeyen DLL İşlevlerini Kullanma](consuming-unmanaged-dll-functions.md)  
Platform çağrısını kullanarak yönetilmeyen DLL işlevlerinin nasıl çağrılacağını açıklar.

[Birlikte Çalışma Hazırlama](interop-marshaling.md)  
COM interop ve platform çağırmak için mareşal açıklar.

[Nasıl yapılır: HRESULTs ve Özel Durumları Eşleme](how-to-map-hresults-and-exceptions.md)  
Özel durumlar ve HRESULTs arasındaki eşleme açıklar.

[Tür Eşdeğerliği ve Katıştırılmış Birlikte Çalışma Türleri](type-equivalence-and-embedded-interop-types.md)  
COM türleri için tür bilgilerinin derlemelere nasıl katıştırılmış olduğunu ve ortak dil çalışma zamanının katıştırılmış COM türlerinin eşdeğerliğini nasıl belirlediğini açıklar.

[Nasıl yapılır: Tlbimp.exe Kullanarak Birincil Birlikte Çalışma Derlemeleri Oluşturma](how-to-generate-primary-interop-assemblies-using-tlbimp-exe.md)  
*Tlbimp.exe* (Tip Kitaplığı İthalatçısı) kullanarak birincil interop derlemelerinin nasıl üretilmeye başlanır.

[Nasıl yapılır: Birincil Birlikte Çalışma Derlemelerini Kaydetme](how-to-register-primary-interop-assemblies.md)  
Projelerinizde başvuruda bulunamadan önce birincil interop derlemelerini nasıl kaydedebileceğinizi açıklar.

[Kayıtsız COM Birlikte Çalışma](registration-free-com-interop.md)  
COM interop'un Windows kayıt defterini kullanmadan bileşenleri nasıl etkinleştirebileceğini açıklar.

[Nasıl yapılır: Kayıtsız Etkinleştirme için .NET Framework Tabanlı COM Bileşenlerini Yapılandırma](configure-net-framework-based-com-components-for-reg.md)  
Uygulama bildiriminin nasıl oluşturulup oluşturulup yerleştirilen bileşen bildiriminin nasıl oluşturulup gömilenleri açıklar.

## <a name="related-sections"></a>İlgili bölümler

[COM Sarmalayıcıları](../../standard/native-interop/com-wrappers.md)  
COM interop tarafından sağlanan sarmalayıcıları açıklar.
