---
title: 'Temel İletişimler: Web Barındırma Desteği'
ms.date: 03/30/2017
ms.assetid: 034c501f-96f9-4ef7-9602-3ac21788fd3e
ms.openlocfilehash: 8ee107ffcb9fab629541ce004d1c587fcad652c8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61998718"
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
