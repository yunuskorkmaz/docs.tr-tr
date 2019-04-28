---
title: Yönetilmeyen kod ile birlikte çalışma
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: edec95ea729fdf26e384b6658c241ca307e60851
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61643120"
---
# <a name="interoperating-with-unmanaged-code"></a>Yönetilmeyen kod ile birlikte çalışma

.NET Framework COM bileşenleri, COM + Hizmetleri, dış tür kitaplıkları ve birçok işletim sistemi Hizmetleri ile etkileşim yükseltir. Veri türleri, yöntem imzaları ve hata işleme düzenekleri yönetilen ve yönetilmeyen nesne modeli arasında farklılık gösterir. .NET Framework bileşenlerini ve yönetilmeyen kod arasındaki birlikte çalışabilirlik basitleştirin ve geçiş yolunun kolaylaştırmak için ortak dil çalışma zamanı istemcilerinden ve sunucuları bu nesne modellerini farklılıkları gizler.

Çalışma zamanı denetimi altında yürütülen kodu, yönetilen kod adı verilir. Buna karşılık, çalışma zamanı dışında çalışan kod, yönetilmeyen kod adı verilir. COM bileşenleri ve ActiveX arabirimleri Windows API işlevlerinde yönetilmeyen kod örnekleridir.

## <a name="in-this-section"></a>Bu bölümde

[COM Bileşenlerini .NET Framework'te Gösterme](exposing-com-components.md)  
.NET Framework uygulamalarında COM bileşenlerini kullanmayı açıklar.

[.NET Framework Bileşenlerini COM'da Gösterme](exposing-dotnet-components-to-com.md)  
COM uygulamaları .NET Framework bileşenlerini kullanmayı açıklar.

[Yönetilmeyen DLL İşlevlerini Kullanma](consuming-unmanaged-dll-functions.md)  
Yönetilmeyen çağrı açıklamaktadır platformunu kullanarak DLL işlevleri çağırma.

[Birlikte Çalışma için Hazırlama](interop-marshaling.md)  
COM birlikte çalışması ve platform çağırma için hazırlamayı açıklar.

[Nasıl yapılır: Harita HRESULTs ve özel durumları](how-to-map-hresults-and-exceptions.md)  
Özel durumlar ve HRESULT'ları arasındaki eşlemeyi tanımlar.

[COM Sarmalayıcıları](com-wrappers.md)  
COM birlikte çalışma tarafından sağlanan sarmalayıcıları açıklar.

[Tür Eşdeğerliği ve Katıştırılmış Birlikte Çalışma Türleri](type-equivalence-and-embedded-interop-types.md)  
COM türleri için tür bilgisi derlemelerde nasıl katıştırılır ve ortak dil çalışma zamanı katıştırılmış COM tür denklik etiketleneceğini nasıl açıklar.

[Nasıl yapılır: Tlbimp.exe kullanarak birincil birlikte çalışma derlemeleri oluşturma](how-to-generate-primary-interop-assemblies-using-tlbimp-exe.md)  
Kullanarak birincil birlikte çalışma derlemeleri oluşturmak nasıl açıklar *Tlbimp.exe* (tür kitaplığı içeri Aktarıcı).

[Nasıl yapılır: Birincil birlikte çalışma derlemelerini kaydetme](how-to-register-primary-interop-assemblies.md)  
Projelerinizde başvurabilirsiniz önce birincil birlikte çalışma derlemelerini kaydetme işlemini açıklamaktadır.

[Kayıtsız COM Birlikte Çalışma](registration-free-com-interop.md)  
Windows kayıt defteri kullanmadan COM birlikte çalışma bileşenlerini nasıl etkinleştirebilirsiniz açıklar.

[Nasıl yapılır: Kayıtsız etkinleştirme için .NET Framework tabanlı COM bileşenlerini yapılandırma](configure-net-framework-based-com-components-for-reg.md)  
Bir uygulama bildirimi oluşturma ve nasıl oluşturulacağı ve bileşen bildirim katıştırma açıklar.
