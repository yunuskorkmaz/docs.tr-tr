---
title: Internet Information Services'te Barındırma
ms.date: 03/30/2017
helpviewer_keywords:
- hosting services [WCF], IIS
ms.assetid: ddae14e8-143c-442d-b660-2046809b2d43
ms.openlocfilehash: 7bfdf2b057c791da7e15619d69c0314557944093
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555841"
---
# <a name="host-in-internet-information-services"></a>Internet Information Services 'de barındırma

Windows Communication Foundation (WCF) hizmetlerini barındırmak için bir seçenek Internet Information Services (IIS) uygulamasının içindedir. Bu barındırma modeli, ASP.NET ve ASP.NET Web Hizmetleri (ASMX) Web Hizmetleri tarafından kullanılan modele benzerdir.

## <a name="versions-of-iis"></a>IIS sürümleri

WCF aşağıdaki işletim sistemlerinde IIS 'nin aşağıdaki sürümlerinde barındırılabilir:

- Windows XP SP2 üzerinde IIS 5,1. Bu ortam, daha sonra Windows Server 2003 gibi bir sunucu işletim sisteminde dağıtılan IIS tarafından barındırılan uygulamaların tasarımı ve geliştirilmesi için yararlıdır.

- Windows Server 2003 üzerinde IIS 6,0. IIS 6,0, geliştirilmiş ölçeklenebilirlik, güvenilirlik ve uygulama yalıtımı sunan gelişmiş bir işlem modeli sağlar. Bu ortam, yalnızca HTTP iletişimini kullanan WCF hizmetlerinin üretim dağıtımı için uygundur.

- Windows Vista ve Windows Server 2008 üzerinde IIS 7,0. IIS 7,0, IIS 6,0 ile aynı gelişmiş işlem modelini sağlar, ancak Windows Işlem etkinleştirme hizmeti 'ni (WAS) HTTP dışındaki protokollerde etkinleştirme ve ağ iletişimine olanak tanımak için kullanır. Bu ortam, WCF tarafından desteklenen herhangi bir ağ protokolü üzerinden iletişim kuran WCF Hizmetleri geliştirmesi için uygundur (HTTP, net. TCP, net. pipe ve net. MSMQ dahil). WAS hakkında daha fazla bilgi için bkz. [Windows Işlem etkinleştirme hizmetinde barındırma](hosting-in-windows-process-activation-service.md).

- [Windows Server AppFabric](/previous-versions/appfabric/ff384253(v=azure.10)) , NET4 WCF ve WF hizmetleri için zengin bir uygulama barındırma ortamı sağlamak üzere IIS 7,0 ve Windows Işlem etkinleştirme HIZMETI (was) ile birlikte çalışarak. Bu avantajlar arasında işlem yaşam döngüsü yönetimi, işlem geri dönüşümü, paylaşılan barındırma, hızlı hata koruması, işlem orphaning, isteğe bağlı etkinleştirme ve sistem durumu izleme sayılabilir. Ayrıntılı bilgi için bkz. [AppFabric barındırma özellikleri](/previous-versions/appfabric/ee677189(v=azure.10)) ve [AppFabric barındırma kavramları](/previous-versions/appfabric/ee677371(v=azure.10)).

## <a name="benefits-of-iis-hosting"></a>IIS barındırma 'nın avantajları

WCF hizmetlerinin IIS 'de barındırılması birkaç avantaj sunar:

- IIS 'de barındırılan WCF Hizmetleri, ASP.NET uygulamaları ve ASMX dahil olmak üzere başka bir IIS uygulaması türü gibi dağıtılır ve yönetilir.

- IIS, barındırılan uygulamaların güvenilirliğini artırmak için işlem etkinleştirme, sistem durumu yönetimi ve geri dönüşüm özellikleri sağlar.

- ASP.NET gibi, ASP.NET 'de barındırılan WCF Hizmetleri, geliştirilmiş sunucu yoğunluğu ve ölçeklenebilirlik için ortak bir çalışan işlemde birden fazla uygulamanın bulunduğu ASP.NET paylaşılan barındırma modelinden faydalanabilir.

- IIS 'de barındırılan WCF Hizmetleri, barındırılan hizmetlerin geliştirilmesini ve dağıtılmasını kolaylaştıran ASP.NET 2,0 ile aynı dinamik derleme modelini kullanır.

IIS 'de WCF Hizmetleri barındırmaya karar verirken IIS 5,1 ve IIS 6,0 ' nin yalnızca HTTP iletişimi ile sınırlı olduğunu unutmamak önemlidir. Barındırma ortamı seçme hakkında daha fazla bilgi için bkz. [barındırma hizmetleri](../hosting-services.md).

## <a name="deploy-an-iis-hosted-wcf-service"></a>IIS tarafından barındırılan bir WCF hizmeti dağıtma

IIS tarafından barındırılan bir WCF hizmetini geliştirme ve dağıtma aşağıdaki görevlerden oluşur:

- IIS, ASP.NET, WCF ve WCF HTTP Etkinleştirme bileşeninin doğru bir şekilde yüklendiğinden ve kaydedildiğinden emin olun.

- Yeni bir IIS uygulaması oluşturun veya var olan bir ASP.NET uygulamasını yeniden kullanın.

- WCF hizmeti için bir. svc dosyası oluşturun.

- Hizmet uygulamasını IIS uygulamasına dağıtın.

- WCF hizmetini yapılandırın.

Bu görevlerin her biri hakkında bir tartışma için bkz. [Internet Information Services barındırılan BIR WCF hizmetini dağıtma](deploying-an-internet-information-services-hosted-wcf-service.md).

## <a name="wcf-services-and-aspnet"></a>WCF Hizmetleri ve ASP.NET

WCF Hizmetleri, ASP.NET ile yan yana veya ASP.NET uyumluluk modunda, hizmetlerin ASP.NET Web uygulaması platformu tarafından sunulan özelliklerden tam olarak yararlanabilme biçiminde barındırılabilir. Bu özelliklerin bir açıklaması için bkz. [WCF Hizmetleri ve ASP.net](wcf-services-and-aspnet.md).

## <a name="see-also"></a>Ayrıca bkz.

- [ServiceHostFactory Kullanarak Barındırmayı Genişletme](../extending/extending-hosting-using-servicehostfactory.md)
- [Internet Information Services Tarafından Barındırılan Bir WCF Hizmeti Dağıtma](deploying-an-internet-information-services-hosted-wcf-service.md)
- [WCF Hizmetleri ve ASP.NET](wcf-services-and-aspnet.md)
- [Internet Information Services Barındırma En İyi Uygulamaları](internet-information-services-hosting-best-practices.md)
- [Windows Communication Foundation için Internet Information Services 7.0'ı Yapılandırma](configuring-iis-for-wcf.md)
- [Windows Server App Fabric barındırma özellikleri](/previous-versions/appfabric/ee677189(v=azure.10))
