---
title: 'Temel İletişimler: Web Barındırma Desteği'
ms.date: 03/30/2017
ms.assetid: 034c501f-96f9-4ef7-9602-3ac21788fd3e
ms.openlocfilehash: 8ee107ffcb9fab629541ce004d1c587fcad652c8
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2018
ms.locfileid: "42752293"
---
# <a name="core-communications-webhost-support"></a>Temel İletişimler: Web Barındırma Desteği

Bu konu, Web barındırma desteği tarafından oluşturulan tüm özel durumları listeler.

## <a name="exception-list"></a>Özel durum listesi

|Kaynak kodu|Kaynak dizesi|
|-------------------|---------------------|
|Hosting_CompatibilityServiceNotHosted|Bu hizmet, ASP.NET uyumluluk gerektirir. IIS de barındırılan gerekir. Her iki ana bilgisayar hizmeti IIS ile ASP.NET Uyumluluk Web.config dosyasında açık veya AspNetCompatibilityRequirementsAttribute.AspNetCompatibilityRequirementsMode özelliği gerekli dışında bir değere ayarlayın.|
|Hosting_ListenerNotFoundForActivationInRecycling|Kanal, etkin bir şekilde belirtilen adresteki dinliyor. Uygulama geri dönüştürme, hizmeti kapalı.|
|Hosting_NonHTTPInCompatibilityMode|ASP.NET uyumluluğu altında desteklenen yalnızca HTTP ve HTTPS kurallarıdır. Belirtilen uç noktası kaldırın veya uygulama için ASP.NET uyumluluk devre dışı bırakın.|
|Hosting_ProcessNotExecutingUnderHostedContext|Belirtilen barındırma işlemi geçerli barındırma ortamı içinden çağrılamaz. Bu API, çağıran uygulama Internet Information Services veya Windows İşlem Etkinleştirme hizmeti barındırılması gerekir.|
|Hosting_ServiceCompatibilityRequire|ASP.NET uyumluluğu gerektirdiğinden hizmeti etkinleştirilemiyor. Bu uygulama için ASP.NET uyumluluk etkin değil. Web.config dosyasında ASP.NET uyumluluk sağlamak ya da AspNetCompatibilityRequirementsAttribute.AspNetCompatibility ayarlayın.|
