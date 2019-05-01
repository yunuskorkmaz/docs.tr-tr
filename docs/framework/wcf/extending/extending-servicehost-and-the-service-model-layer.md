---
title: ServiceHost Hizmet Modeli Katmanını Genişletme
ms.date: 03/30/2017
helpviewer_keywords:
- extending service models [WCF]
ms.assetid: 954c138a-1cd0-45a0-8abe-e4d2b8ff5400
ms.openlocfilehash: 9e08b5b7b11848262d2cb7b6ed5715799d597889
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991776"
---
# <a name="extending-servicehost-and-the-service-model-layer"></a>ServiceHost Hizmet Modeli Katmanını Genişletme
Hizmet modeli katmanını çağırana geri göndererek arka plandaki kanal gelen iletileri çekerek ve bunları yöntem çağrıları uygulama kodunda içine çevirme sorumludur. Hizmet modeli uzantıları değiştirebilir veya yürütme veya iletişim davranışı ve istemci veya dağıtıcı işlevi, özel davranışlar, ileti ve parametre durdurma ve diğer genişletilebilirlik işlevlerini içeren özellikler uygular.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [İstemcileri Genişletme](../../../../docs/framework/wcf/extending/extending-clients.md)  
 Uzantılarınızı özel istemci uygulamalarında ekleyebilirsiniz sınıfları yanı sıra istemci çalışma zamanı değiştirmek ve arabirimler açıklanmaktadır. Örneğin, özel istemci ileti günlüğe kaydetmeyi gerçekleştirmek, özel ileti serileştirme yapmak ve benzeri.  
  
 [Dağıtıcıları Genişletme](../../../../docs/framework/wcf/extending/extending-dispatchers.md)  
 İçinde özel uzantılarınızı hizmet uygulamalarını ekleyebilirsiniz sınıfları yanı sıra, hizmet çalışma zamanı değiştirmek ve arabirimler açıklanmaktadır. Örneğin, özel hizmet günlüğü, hizmet tarafı ileti doğrulama, özel gönderme ve benzeri gerçekleştirebilirsiniz.  
  
 [Genişletilebilen Nesneler](../../../../docs/framework/wcf/extending/extensible-objects.md)  
 Beş genişletilebilen nesneler açıklar ve <xref:System.ServiceModel.IExtensibleObject%601> deseni. Genişletilebilir nesne düzeni ya da var olan çalışma zamanı sınıflar yeni işlevlerle genişletmek veya bir nesneye yeni bir durum eklemek için kullanılır. Genişletilebilen nesneler birine bağlı uzantılar, paylaşılan durum ve işlevselliği, erişimleri olan bir ortak Genişletilebilir nesnesine erişmek için işleme çok farklı aşamalarında davranışları etkinleştirin.  
  
 [Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)  
 Ayarları değiştirmek veya WCF çalışma zamanı'nda uzantıları eklemek için davranışları kullanın. WCF sistem uygulanan davranış azaltma, depolamasına ve birçok diğer yönleri Hizmetleri ve işlemleri denetleme içerir. Bu bölümde, kendi özel davranışlarınızı ve bunları program aracılığıyla her iki kullanmak için kullanılabilir hale getirme ve yapılandırma dosyalarını kullanarak nasıl oluşturulacağı açıklanmaktadır.  
  
 [ServiceHostFactory Kullanarak Barındırmayı Genişletme](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)  
 Nasıl genişletileceğini açıklar <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType>, <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>ve <xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=nameWithType> konak ortamı özelleştirmek için sınıflar.  
  
## <a name="reference"></a>Başvuru  
  
## <a name="related-sections"></a>İlgili Bölümler
