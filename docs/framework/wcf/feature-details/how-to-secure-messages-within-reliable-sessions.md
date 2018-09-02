---
title: 'Nasıl yapılır: Güvenli Oturumlarla İletileri Güvenli Hale Getirme'
ms.date: 03/30/2017
ms.assetid: aee33e50-936f-4486-9ca8-c1520c19a62d
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 1592c9429e6cd425b86fa2b72bfebe977e18b048
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43406214"
---
# <a name="how-to-secure-messages-within-reliable-sessions"></a>Nasıl yapılır: Güvenli Oturumlarla İletileri Güvenli Hale Getirme

Bu konuda, bu tür bir oturumu destekleyen sistem tarafından sağlanan bağlamalar, ancak değil, varsayılan olarak kullanarak bir güvenilir oturum içinde değiştirilen iletileri için ileti düzeyi güvenliği etkinleştirmek için gereken adımlar açıklanmaktadır. Kesin kod kullanarak veya bildirimli olarak yapılandırma dosyasında bir güvenli, güvenilir oturum etkinleştirin. Bu yordam, güvenli, güvenilir oturum etkinleştirmek için hizmet ve istemci yapılandırma dosyalarını kullanır.

Bu yordam, aşağıdaki üç temel görevleri oluşur:

1. İstemci ve hizmet iletileri güvenilir bir oturumda exchange belirtin.

1. İleti düzeyi güvenliği, güvenilir oturum içinde gerektirir.

1. İstemci Hizmeti ile kimlik doğrulaması için kullanmanız gereken istemci kimlik bilgisi türü belirtin.

Uç nokta yapılandırma öğesi içeren ilk görevi önemli olduğu bir `bindingConfiguration` (Bu örnekte) adlı bir bağlama yapılandırmasını başvuran öznitelik `MessageSecurity`. [  **\<Bağlama >** ](../../../../docs/framework/misc/binding.md) yapılandırma öğesi daha sonra güvenilir oturumlar etkinleştirmek için bu ada başvuran `enabled` özniteliği [  **\<reliableSession >** ](https://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) öğesine `true`. Sıralı teslim Güvenceleri güvenilir bir oturumda ayarlayarak kullanılabilir olmasını gerektiren `ordered` özniteliğini `true`.

Bu yapılandırma yordamını tabanlı örnek kaynak kopyası için bkz: [WS güvenilir oturum](../../../../docs/framework/wcf/samples/ws-reliable-session.md).

İkinci görev temel öğelerini ayarlayarak yapılır `mode` özniteliği  **\<Güvenlik >** içerdiği öğesi  **\<bağlama >** öğe için hizmet ve istemci `Message`.

Üçüncü görev temel öğelerini ayarlayarak yapılır `clientCredentialType` özniteliği  **\<ileti >** içerdiği öğesi  **\<Güvenlik >** öğe için hizmet ve istemci `Certificate`.

> [!NOTE]
> İleti güvenliği ile güvenilir oturumlar kullanırken, bir zaman aşımı ilk başarısızlık durumunda bir özel durum atma yerine gerçekleşene kadar kimliği doğrulanmamış bir istemci kimlik doğrulaması güvenilir Mesajlaşma çalışır.

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a>Güvenilir oturum kullanılacak WSHttpBinding hizmetini yapılandırma

Bu yordamda açıklanan [nasıl yapılır: Exchange ileti içinde bir güvenilir oturum](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a>Güvenilir oturum kullanılacak WSHttpBinding istemciyi Yapılandırma

Bu yordamda açıklanan [nasıl yapılır: Exchange ileti içinde bir güvenilir oturum](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).

### <a name="set-the-mode-and-clientcredentialtype-in-configuration"></a>Yapılandırma modu ve ClientCredentialType ayarlayın

1. Uygun bağlama öğeye ekleme [  **\<bağlamaları >** ](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) yapılandırma dosyasının öğesi. Aşağıdaki örnek ekler bir [  **\<wsHttpBinding >** ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) öğesi.

1. Ekleme bir  **\<bağlama >** öğesi ve kümesi kendi `name` özniteliği için uygun bir değer. Örnek adı kullanan `MessageSecurity`.

1. Ekleme bir  **\<Güvenlik >** öğesi ve kümesi `mode` özniteliğini `Message`.

1. İçinde  **\<Güvenlik >** öğe, Ekle bir  **\<ileti >** öğesi ve kümesi `clientCredentialType` özniteliğini `Certificate`.

```xml
<wsHttpBinding>
  <binding name="MessageSecurity">
    <security mode="Message">
      <message clientCredentialType="Certificate" />
    </security>
  </binding>
</wsHttpBinding>
```
