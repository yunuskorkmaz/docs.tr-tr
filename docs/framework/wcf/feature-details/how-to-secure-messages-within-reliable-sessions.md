---
title: 'Nasıl yapılır: Güvenli Oturumlarla İletileri Güvenli Hale Getirme'
ms.date: 03/30/2017
ms.assetid: aee33e50-936f-4486-9ca8-c1520c19a62d
ms.openlocfilehash: cec9356467886be022d05ead55d5cb6ccddcd838
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558686"
---
# <a name="how-to-secure-messages-within-reliable-sessions"></a>Nasıl yapılır: Güvenli Oturumlarla İletileri Güvenli Hale Getirme

Bu konu, bu tür bir oturumu destekleyen, ancak varsayılan olarak değil, sistem tarafından belirtilen bağlamalardan birini kullanarak güvenilir bir oturumda değiştirilen iletiler için ileti düzeyi güvenliği etkinleştirmek için gereken adımları açıklar. Yapılandırma dosyasında kod kullanarak güvenli, güvenilir bir oturumu imperatively veya bildirimli olarak etkinleştirin. Bu yordam, güvenli, güvenilir oturumu etkinleştirmek için istemci ve hizmet yapılandırma dosyalarını kullanır.

Bu yordam aşağıdaki üç temel görevden oluşur:

1. İstemci ve hizmet iletilerinin güvenilir bir oturum içinde Exchange 'e ait olduğunu belirtin.

1. Güvenilir oturum içinde ileti düzeyinde güvenlik gerektir.

1. İstemcinin, hizmette kimlik doğrulaması yapmak için kullanması gereken istemci kimlik bilgisi türünü belirtin.

Uç nokta yapılandırma öğesinin adlı bir bağlama yapılandırmasına başvuran bir öznitelik içerdiği ilk görevde `bindingConfiguration` (Bu örnekte) önemlidir `MessageSecurity` . [**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md)Sonra yapılandırma öğesi, `enabled` öğesinin özniteliğini olarak ayarlayarak güvenilir oturumları etkinleştirmek için bu ada başvurur [**\<reliableSession>**](/previous-versions/ms731375(v=vs.90)) `true` . Özniteliğini olarak ayarlayarak, sıralı teslimat güveninin güvenilir bir oturum dahilinde kullanılabilir olmasını zorunlu kılabilirsiniz `ordered` `true` .

Bu yapılandırma yordamının temel aldığı örnek kaynak kopyası için, bkz. [WS güvenilir oturumu](../samples/ws-reliable-session.md).

İkinci görevin temel öğeleri, `mode` **\<security>** **\<binding>** istemci ve hizmetin öğesinde bulunan öğesinin özniteliği olarak ayarlanarak gerçekleştirilir `Message` .

Üçüncü görevin temel öğeleri, `clientCredentialType` **\<message>** **\<security>** istemci ve hizmetin öğesinde bulunan öğesinin özniteliği ayarlanarak gerçekleştirilir `Certificate` .

> [!NOTE]
> Güvenilir oturumlarla ileti güvenliği kullanılırken, ilk hata durumunda özel durum oluşturmak yerine bir zaman aşımı gerçekleşene kadar, güvenilir mesajlaşma kimliği doğrulanmamış bir istemcinin kimliğini doğrulamaya çalışır.

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a>Güvenli bir oturum kullanmak için bir WSHttpBinding ile hizmeti yapılandırma

Bu yordam, [nasıl yapılır: güvenilir bir oturumda Ileti alışverişi konusunda](how-to-exchange-messages-within-a-reliable-session.md)açıklanmaktadır.

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a>Güvenli bir oturum kullanmak için istemciyi bir WSHttpBinding ile yapılandırma

Bu yordam, [nasıl yapılır: güvenilir bir oturumda Ileti alışverişi konusunda](how-to-exchange-messages-within-a-reliable-session.md)açıklanmaktadır.

### <a name="set-the-mode-and-clientcredentialtype-in-configuration"></a>Yapılandırmada Mode ve ClientCredentialType ayarla

1. Yapılandırma dosyasının öğesine uygun bir bağlama öğesi ekleyin [**\<bindings>**](../../configure-apps/file-schema/wcf/bindings.md) . Aşağıdaki örnek bir öğesi ekler [**\<wsHttpBinding>**](../../configure-apps/file-schema/wcf/wshttpbinding.md) .

1. Bir **\<binding>** öğesi ekleyin ve `name` özniteliğini uygun bir değere ayarlayın. Örnek, adını kullanır `MessageSecurity` .

1. Bir **\<security>** öğesi ekleyin ve `mode` özniteliğini olarak ayarlayın `Message` .

1. Öğesi içinde **\<security>** , bir öğesi ekleyin **\<message>** ve `clientCredentialType` özniteliğini olarak ayarlayın `Certificate` .

```xml
<wsHttpBinding>
  <binding name="MessageSecurity">
    <security mode="Message">
      <message clientCredentialType="Certificate" />
    </security>
  </binding>
</wsHttpBinding>
```
