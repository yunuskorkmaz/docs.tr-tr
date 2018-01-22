---
title: "Nasıl yapılır: Güvenli Oturumlarla İletileri Güvenli Hale Getirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aee33e50-936f-4486-9ca8-c1520c19a62d
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 2604b9dacf11b9971b10d23d9a807092ddf07830
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-secure-messages-within-reliable-sessions"></a>Nasıl yapılır: Güvenli Oturumlarla İletileri Güvenli Hale Getirme

Bu konuda bu tür bir oturum desteği sistem tarafından sağlanan bağlamalar, ancak varsayılan kullanarak güvenilir bir oturumu içinde değiştirilen iletileri için ileti düzeyi güvenlik etkinleştirmek için gereken adımlar açıklanır. Güvenli, güvenilir oturum kodu kullanarak imperatively ya da bildirimli olarak yapılandırma dosyasında etkinleştirin. Bu yordam, güvenli, güvenilir oturum etkinleştirmek için istemci ve hizmet yapılandırma dosyalarını kullanır.

Bu yordam, aşağıdaki üç anahtar görevleri oluşur:

1. İstemci ve hizmet iletileri güvenilir oturum içinde exchange belirtin.

1. İleti düzeyi güvenlik güvenilir oturum içinde gerektirir.

1. İstemci hizmetiyle kimlik doğrulaması için kullanması gereken istemci kimlik bilgisi türü belirtin.

Uç nokta yapılandırma öğesi içerir ilk görevde önemli bir `bindingConfiguration` (Bu örnekte) adlı bir bağlama yapılandırması başvuran özniteliği `MessageSecurity`. [  **\<Bağlama >** ](../../../../docs/framework/misc/binding.md) yapılandırma öğesi sonra ayarlayarak güvenilir oturumlar etkinleştirmek için bu ad başvuran `enabled` özniteliği [  **\<reliableSession >** ](http://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) öğesine `true`. Sıralı teslim Güvenceleri güvenilir oturum içinde ayarlayarak kullanılabilir olmasını gerektiren `ordered` özniteliğini `true`.

Bu yapılandırma yordamı temel örnek kaynak kopyası için bkz: [WS güvenilir oturum](../../../../docs/framework/wcf/samples/ws-reliable-session.md).

İkinci görev temel öğeler ayarlayarak yapılır `mode` özniteliği  **\<Güvenlik >** öğesi içinde yer alan  **\<bağlama >** öğesi, istemci ve hizmet için `Message`.

Üçüncü görev temel öğeler ayarlayarak yapılır `clientCredentialType` özniteliği  **\<ileti >** öğesi içinde yer alan  **\<Güvenlik >** öğesi, istemci ve hizmet için `Certificate`.

> [!NOTE]
> İleti güvenliği ile güvenilir oturumlar kullanırken, ilk başarısızlık durumunda bir özel durum atma yerine bir zaman aşımı gerçekleşene kadar kimliği doğrulanmamış bir istemci kimlik doğrulaması güvenilir Mesajlaşma çalışır.

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a>Güvenilir oturum kullanmak için bir WSHttpBinding hizmetini yapılandırma

Bu yordamda açıklanan [nasıl yapılır: Exchange iletileri içinde bir güvenilir oturum](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a>Güvenilir oturum kullanmak için bir WSHttpBinding istemciyi Yapılandırma

Bu yordamda açıklanan [nasıl yapılır: Exchange iletileri içinde bir güvenilir oturum](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).

### <a name="set-the-mode-and-clientcredentialtype-in-configuration"></a>Mod ve ClientCredentialType yapılandırmasında ayarlayın

1. Bir uygun bağlama öğesi ekleme [  **\<bağlamaları >** ](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) yapılandırma dosyası öğesi. Aşağıdaki örnek, bir [  **\<wsHttpBinding >** ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) öğesi.

1. Ekleme bir  **\<bağlama >** öğesi ve kümesi kendi `name` öznitelik için uygun bir değer. Örnek adı kullanır `MessageSecurity`.

1. Ekleme bir  **\<Güvenlik >** öğesi ve kümesi `mode` özniteliğini `Message`.

1. İçinde  **\<Güvenlik >** öğesi ekleme bir  **\<ileti >** öğesi ve kümesi `clientCredentialType` özniteliğini `Certificate`.

```xml
<wsHttpBinding>
  <binding name="MessageSecurity">
    <security mode="Message">
      <message clientCredentialType="Certificate" />
    </security>
  </binding>
</wsHttpBinding>
```
