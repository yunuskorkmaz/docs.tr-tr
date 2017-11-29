---
title: "Yönetilmeyen Kod ile Birlikte Çalışma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
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
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2db5b8c2425637e24086f54e8ef69b0e5aac3633
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="interoperating-with-unmanaged-code"></a>Yönetilmeyen Kod ile Birlikte Çalışma
.NET Framework COM bileşenleri, COM + Hizmetleri, dış tür kitaplıklarını ve birçok işletim sistemi Hizmetleri ile etkileşim yükseltir. Veri türleri, yöntem imzaları ve hata işleme mekanizmaları yönetilen ve yönetilmeyen nesne modelleri arasında farklılık gösterir. Yönetilmeyen kod ile .NET Framework bileşenleri arasındaki birlikte çalışabilirlik basitleştirmek ve geçiş yolunun kolaylaştırmak için istemciler ve sunucular bu nesne modelleri farklılıkları ortak dil çalışma zamanı gizler.  
  
 Çalışma zamanı denetiminde yürütülen kodu yönetilen kod adı verilir. Buna karşılık, çalışma zamanı dışında çalışan kod yönetilmeyen kod denir. COM bileşenlerini, ActiveX arabirimleri ve Win32 API işlevleri yönetilmeyen kod gösterilebilir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Yönetilmeyen kod nasıl yapılır konuları ile birlikte çalışma](http://msdn.microsoft.com/en-us/ec21c6e1-e233-4cd9-95ae-b9b9cf807f9d)  
 Yönetilmeyen kod ile birlikte çalışma için kavramsal belgelerinde bulunan tüm nasıl yapılır konuları için bağlantılar sağlar.  
  
 [COM bileşenlerini .NET Framework'te gösterme](../../../docs/framework/interop/exposing-com-components.md)  
 .NET Framework uygulamalarında COM bileşenlerini kullanmayı açıklar.  
  
 [.NET Framework bileşenlerini COM'da gösterme](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 COM uygulamaları .NET Framework bileşenlerini kullanmayı açıklar.  
  
 [Yönetilmeyen DLL işlevlerini kullanma](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 Yönetilmeyen çağrılacağını açıklar platformu kullanılarak DLL işlevleri çağırma.  
  
 [Birlikte çalışma için tasarım konuları](http://msdn.microsoft.com/en-us/b59637f6-fe35-40d6-ae72-901e7a707689)  
 Tümleşik COM bileşenlerini yazmak için ipuçları verilmektedir.  
  
 [Birlikte çalışma hazırlama](../../../docs/framework/interop/interop-marshaling.md)  
 COM birlikte çalışma ve platform çağırma için hazırlamayı açıklar.  
  
 [Nasıl yapılır: HRESULTs ve özel durumları eşleme](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md)  
 Özel durumlar ve HRESULTs arasında eşleme açıklar.  
  
 [Genel türler kullanma birlikte çalışma](http://msdn.microsoft.com/en-us/26b88e03-085b-4b53-94ba-a5a9c709ce58)  
 COM birlikte çalışma içinde kullanıldığında genel türler davranışını tanımlar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Gelişmiş COM birlikte çalışabilirliği](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 COM bileşenlerini .NET Framework uygulamasına ekleme hakkında daha fazla bilgi için bağlantılar sağlar.
