---
description: 'Daha fazla bilgi edinin: temel Iletişimler: Webhost desteği'
title: 'Temel İletişimler: Web Barındırma Desteği'
ms.date: 03/30/2017
ms.assetid: 034c501f-96f9-4ef7-9602-3ac21788fd3e
ms.openlocfilehash: c132527caf4d08b7423ff8af9442ca609d4e645f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99686524"
---
# <a name="core-communications-webhost-support"></a>Temel İletişimler: Web Barındırma Desteği

Bu konu, Webhost desteği tarafından oluşturulan tüm özel durumları listeler.

## <a name="exception-list"></a>Özel durum listesi

|Kaynak kodu|Kaynak dizesi|
|-------------------|---------------------|
|Hosting_CompatibilityServiceNotHosted|Bu hizmet ASP.NET uyumluluğu gerektirir. Ayrıca IIS 'de barındırılmalıdır. ASP.NET uyumluluğu etkinleştirilmiş olarak hizmeti IIS 'de barındırın Web.config veya AspNetCompatibilityRequirementsAttribute. AspNetCompatibilityRequirementsMode özelliğini gerekenden farklı bir değere ayarlayın.|
|Hosting_ListenerNotFoundForActivationInRecycling|Belirtilen adreste etkin olarak dinleme yapan kanal yok. Bir uygulama geri dönüştürüldükten sonra hizmet kapalıdır.|
|Hosting_NonHTTPInCompatibilityMode|ASP.NET uyumluluğu altında desteklenen tek protokoller HTTP ve HTTPS 'DIR. Belirtilen uç noktayı kaldırın veya uygulama için ASP.NET uyumluluğunu devre dışı bırakın.|
|Hosting_ProcessNotExecutingUnderHostedContext|Belirtilen barındırma işlemi, geçerli barındırma ortamı içinde çağrılamaz. Bu API, çağıran uygulamanın Internet Information Services veya Windows Işlem etkinleştirme hizmetinde barındırılmasını gerektirir.|
|Hosting_ServiceCompatibilityRequire|Hizmet, ASP.NET uyumluluğu gerektirdiğinden etkinleştirilemiyor. ASP.NET uyumluluğu Bu uygulama için etkinleştirilmemiş. Web.config dosyasında ASP.NET uyumluluğunu etkinleştirin ya da AspNetCompatibilityRequirementsAttribute. AspNetCompatibility ' i ayarlayın.|
