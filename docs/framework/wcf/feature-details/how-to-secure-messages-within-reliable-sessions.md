---
title: 'Nasıl yapılır: Güvenli Oturumlarla İletileri Güvenli Hale Getirme'
ms.date: 03/30/2017
ms.assetid: aee33e50-936f-4486-9ca8-c1520c19a62d
ms.openlocfilehash: edff27fe9649387c1922c34e72ef59d615e52b90
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141670"
---
# <a name="how-to-secure-messages-within-reliable-sessions"></a>Nasıl yapılır: Güvenli Oturumlarla İletileri Güvenli Hale Getirme

Bu konu, bu tür bir oturumu destekleyen, ancak varsayılan olarak değil, sistem tarafından belirtilen bağlamalardan birini kullanarak güvenilir bir oturumda değiştirilen iletiler için ileti düzeyi güvenliği etkinleştirmek için gereken adımları açıklar. Yapılandırma dosyasında kod kullanarak güvenli, güvenilir bir oturumu imperatively veya bildirimli olarak etkinleştirin. Bu yordam, güvenli, güvenilir oturumu etkinleştirmek için istemci ve hizmet yapılandırma dosyalarını kullanır.

Bu yordam aşağıdaki üç temel görevden oluşur:

1. İstemci ve hizmet iletilerinin güvenilir bir oturum içinde Exchange 'e ait olduğunu belirtin.

1. Güvenilir oturum içinde ileti düzeyinde güvenlik gerektir.

1. İstemcinin, hizmette kimlik doğrulaması yapmak için kullanması gereken istemci kimlik bilgisi türünü belirtin.

Uç nokta yapılandırma öğesinin, adlı bir bağlama yapılandırmasına (Bu örnekte `MessageSecurity`) başvuran bir `bindingConfiguration` özniteliği içerdiği ilk görevde önemlidir. [ **\<bağlama >** ](../../configure-apps/file-schema/wcf/bindings.md) yapılandırma öğesi, [ **\<reliablesession >** ](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) öğesinin `enabled` özniteliğini `true`olarak ayarlayarak güvenilir oturumları etkinleştirmek için bu ada başvurur. `ordered` özniteliğini `true`olarak ayarlayarak, sıralı teslimat güvenlerini güvenilir bir oturum dahilinde kullanılabilir olmasını zorunlu kılabilirsiniz.

Bu yapılandırma yordamının temel aldığı örnek kaynak kopyası için, bkz. [WS güvenilir oturumu](../../../../docs/framework/wcf/samples/ws-reliable-session.md).

İkinci görevin temel öğeleri, istemci ve hizmetin **\<binding >** öğesinde bulunan **\<security >** öğesinin `mode` özniteliği `Message`' a ayarlanarak gerçekleştirilir.

Üçüncü görevin temel öğeleri, istemci ve hizmetin **\<güvenlik >** öğesinde bulunan **\<message >** öğesinin `clientCredentialType` özniteliği `Certificate`olarak ayarlanarak gerçekleştirilir.

> [!NOTE]
> Güvenilir oturumlarla ileti güvenliği kullanılırken, ilk hata durumunda özel durum oluşturmak yerine bir zaman aşımı gerçekleşene kadar, güvenilir mesajlaşma kimliği doğrulanmamış bir istemcinin kimliğini doğrulamaya çalışır.

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a>Güvenli bir oturum kullanmak için bir WSHttpBinding ile hizmeti yapılandırma

Bu yordam, [nasıl yapılır: güvenilir bir oturumda Ileti alışverişi konusunda](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md)açıklanmaktadır.

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a>Güvenli bir oturum kullanmak için istemciyi bir WSHttpBinding ile yapılandırma

Bu yordam, [nasıl yapılır: güvenilir bir oturumda Ileti alışverişi konusunda](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md)açıklanmaktadır.

### <a name="set-the-mode-and-clientcredentialtype-in-configuration"></a>Yapılandırmada Mode ve ClientCredentialType ayarla

1. Yapılandırma dosyasının [ **\<bindings >** ](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) öğesine uygun bir bağlama öğesi ekleyin. Aşağıdaki örnek [ **\<wsHttpBinding >** ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) öğesi ekler.

1. **\<bağlama >** öğesi ekleyin ve `name` özniteliğini uygun bir değere ayarlayın. Örnek, `MessageSecurity`adını kullanır.

1. \<bir **güvenlik >** öğesi ekleyin ve `mode` özniteliğini `Message`olarak ayarlayın.

1. **\<security >** öğesi içinde, bir **\<ileti >** öğesi ekleyin ve `clientCredentialType` özniteliğini `Certificate`olarak ayarlayın.

```xml
<wsHttpBinding>
  <binding name="MessageSecurity">
    <security mode="Message">
      <message clientCredentialType="Certificate" />
    </security>
  </binding>
</wsHttpBinding>
```
