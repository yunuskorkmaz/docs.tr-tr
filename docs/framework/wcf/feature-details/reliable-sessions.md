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
ms.openlocfilehash: 396c76cbdb8eada881a5c87edfc2500dcdab3ad4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="reliable-sessions"></a>Güvenilir oturumlar

Bu bölümde, hangi bir Windows Communication Foundation (güvenilir oturum WCF), ne, nasıl kullanıldığı ve ne zaman kullanmak için hangi bağlama yapılandırmaları destekliyorsa ve işaretçilerde en iyi uygulamalar açıklanmaktadır. Önemli noktaları ve bu bölümdeki ilgili konular hakkında ayrıntılar aşağıdaki tabloda özetlenmiştir.

Güvenilir oturum WCF uç noktaları arasında gönderilen iletileri SOAP veya taşıma aracılar aktarılır ve yalnızca bir kez ve isteğe bağlı olarak, hangi gönderildikleri sırayla teslim edilir sağlayarak featrues sağlar.

Güvenilir oturum bir WCF uygulaması ile kullanmak için WCF'de varsayılan olarak veya bir seçenek olarak güvenilir oturum destekleyen sistem tarafından sağlanan bağlamaları birini kullanın veya oturumu destekler, kendi özel bağlama oluşturma.

## <a name="in-this-section"></a>Bu Bölümde

[Güvenilir oturumlar genel bakış](../../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md)   
Güvenilir oturumlar açıklar bunların güvenilir oturumlar destek farklı bağlamaları ne zaman kullanılacağı ve nasıl çalışırlar.

[Nasıl yapılır: bir güvenilir oturum içinde iletileri Exchange](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md)   
Yapılandırmada belirtilen özel bağlama kullanma HTTP üzerinden bir güvenilir oturum oluşturmayı açıklar.

[Nasıl yapılır: oturumlarla iletileri güvenli](../../../../docs/framework/wcf/feature-details/how-to-secure-messages-within-reliable-sessions.md)   
Güvenilir oturum güvenli açıklar.

[Nasıl yapılır: HTTPS ile özel bir güvenilir oturum bağlama oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md)   
HTTPS üzerinden güvenli bir oturum oluşturmayı açıklar.

[Güvenilir oturumlar için en iyi yöntemler](../../../../docs/framework/wcf/feature-details/best-practices-for-reliable-sessions.md)   
Güvenilir oturum kullanmayla ilişkili en iyi uygulamaları bazıları açıklanmaktadır.

## <a name="reference"></a>Başvuru

<xref:System.ServiceModel.ReliableSession>

## <a name="see-also"></a>Ayrıca Bkz.

[Kuyruklar ve güvenilir oturumlar](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)   
[Oturumlar, Örnek Oluşturma ve Eşzamanlılık](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)
