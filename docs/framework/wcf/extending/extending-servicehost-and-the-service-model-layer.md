---
title: ServiceHost Hizmet Modeli Katmanını Genişletme
ms.date: 03/30/2017
helpviewer_keywords:
- extending service models [WCF]
ms.assetid: 954c138a-1cd0-45a0-8abe-e4d2b8ff5400
ms.openlocfilehash: e370316cd121f49953e00e83dfc9d2aec17de1e8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795731"
---
# <a name="extending-servicehost-and-the-service-model-layer"></a>ServiceHost Hizmet Modeli Katmanını Genişletme
Hizmet modeli katmanı, temel alınan kanallara ait gelen iletileri çekmekten, bunları uygulama kodundaki Yöntem etkinleştirmeleri içine çevirerek ve sonuçları çağırana geri göndererek sorumludur. Hizmet modeli uzantıları, istemci veya dağıtıcı işlevselliği, özel davranışlar, ileti ve parametre yakaalımı ve diğer genişletilebilirlik işlevleriyle ilgili yürütme veya iletişim davranışlarını ve özellikleri değiştirir veya uygular.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [İstemcileri Genişletme](extending-clients.md)  
 İstemci çalışma zamanının yanı sıra özel uzantılarınızı istemci uygulamalarına ekleyebileceğiniz sınıfları ele geçirebilir ve değiştirebilen arabirimlerini açıklar. Örneğin, özel istemci ileti günlüğü gerçekleştirebilir, özel ileti serileştirme gerçekleştirebilir ve bu şekilde devam edebilirsiniz.  
  
 [Dağıtıcıları Genişletme](extending-dispatchers.md)  
 Hizmet çalışma zamanını ele geçirebilir ve değiştirebilen arabirimleri ve hizmet uygulamalarına özel uzantılarınızı ekleyebileceğiniz sınıfları açıklar. Örneğin, özel hizmet günlüğü, hizmet tarafı ileti doğrulama, Özel gönderme vb. gerçekleştirebilirsiniz.  
  
 [Genişletilebilen Nesneler](extensible-objects.md)  
 Beş Genişletilebilir nesneyi ve <xref:System.ServiceModel.IExtensibleObject%601> kalıbı açıklar. Genişletilebilir nesne stili, mevcut çalışma zamanı sınıflarını yeni işlevlerle genişletmek veya bir nesneye yeni durum eklemek için kullanılır. Genişletilebilir nesnelerden birine bağlı olan uzantılar, paylaşılan durum ve işlevlere, bunlara erişebilen ortak bir Genişletilebilir nesneye eklenen işlevlere erişmek için işleme sırasındaki çok farklı aşamalar üzerinde davranışları etkinleştirin.  
  
 [Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme](configuring-and-extending-the-runtime-with-behaviors.md)  
 WCF çalışma zamanında ayarları değiştirmek veya uzantıları eklemek için davranışları kullanırsınız. WCF, hizmet ve işlemlerin azalmasını, örneklemesini ve diğer birçok yönünü denetlemek için sistem tarafından uygulanan davranışları içerir. Bu bölümde, kendi özel davranışlarınızın nasıl oluşturulduğu ve bunların hem programlı olarak hem de yapılandırma dosyalarını kullanarak kullanılabilir hale nasıl kullanılacağı açıklanmaktadır.  
  
 [ServiceHostFactory Kullanarak Barındırmayı Genişletme](extending-hosting-using-servicehostfactory.md)  
 Konak ortamını özelleştirmek için <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType> <xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=nameWithType> sınıfların <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>nasıl genişletileceğini, ve kullanılacağını açıklar.  
  
## <a name="reference"></a>Başvuru  
  
## <a name="related-sections"></a>İlgili Bölümler
