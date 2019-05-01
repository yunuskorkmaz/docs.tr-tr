---
title: Güvenilir oturumlar
ms.date: 03/30/2017
f1_keywords:
- Windows Communication Foundation, sessions and instances
- WCF, sessions and instances
- sessions and instances [WCF]
helpviewer_keywords:
- instances [WCF]
- sessions [WCF]
ms.assetid: 143951b3-3aa0-4540-b4b7-d33e77e874a1
ms.openlocfilehash: 9a2cd06c4c5a73d9fb5c4c7f09632e10c3eb0d87
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991165"
---
# <a name="reliable-sessions"></a>Güvenilir oturumlar

Bu bölümde, hangi bir Windows Communication Foundation (güvenilir oturum WCF), ne, nasıl kullanıldığı ve ne zaman kullanmak için hangi bağlama yapılandırmaları destekliyorsa ve işaretçilerde en iyi uygulamalar açıklanmaktadır. Önemli noktaları ve bu bölümdeki ilgili konular hakkında ayrıntıları aşağıdaki tabloda özetlenmiştir.

Güvenilir oturum WCF uç noktaları arasında gönderilen iletilerin SOAP veya aktarım aracılar arasında aktarılır ve yalnızca bir kez ve isteğe bağlı olarak, hangi gönderildikleri sırayla teslim sağlama özellikleri sağlar.

Güvenilir oturum WCF uygulamayla kullanmak için varsayılan olarak veya isteğe bağlı olarak bir güvenilir oturum destekleyen sistem tarafından sağlanan bağlamalar wcf'de birini kullanın veya oturumu destekler, kendi özel bağlama oluşturabilirsiniz.

## <a name="in-this-section"></a>Bu Bölümde

[Güvenilir oturumlar genel bakış](../../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md) güvenilir oturumlar açıklar bunların güvenilir oturumları destekleyen farklı bağlamaları ne zaman kullanılacağı ve nasıl çalıştıkları.

[Nasıl yapılır: Exchange ileti içinde bir güvenilir oturum](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md) yapılandırmasında belirtilen özel bir bağlama kullanarak HTTP üzerinden bir güvenilir oturum oluşturmayı açıklar.

[Nasıl yapılır: Güvenilir oturumlar iletilerinde güvenli](../../../../docs/framework/wcf/feature-details/how-to-secure-messages-within-reliable-sessions.md) güvenilir oturum güvenliğinin nasıl sağlanacağını açıklar.

[Nasıl yapılır: HTTPS ile özel güvenilir oturum bağlama oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md) HTTPS üzerinden bir güvenilir oturum oluşturmayı açıklar.

[En iyi uygulamalar için güvenilir oturumlar](../../../../docs/framework/wcf/feature-details/best-practices-for-reliable-sessions.md) bazı güvenilir oturum kullanmayla ilişkili en iyi uygulamalar açıklanmaktadır.

## <a name="reference"></a>Başvuru

<xref:System.ServiceModel.ReliableSession>

## <a name="see-also"></a>Ayrıca bkz.

- [Kuyruklar ve Güvenilir Oturumlar](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)
- [Oturumlar, Örnek Oluşturma ve Eşzamanlılık](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)
