---
title: "Güvenilir oturumlar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Windows Communication Foundation, sessions and instances
- WCF, sessions and instances
- sessions and instances [WCF]
helpviewer_keywords:
- instances [WCF]
- sessions [WCF]
ms.assetid: 143951b3-3aa0-4540-b4b7-d33e77e874a1
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 53bb63fbbcf92650085514118a5e9464ab2dea30
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="reliable-sessions"></a>Güvenilir oturumlar

Bu bölümde açıklanmaktadır bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] güvenilir oturum olduğundan, ne, nasıl kullanıldığı ve ne zaman kullanmak için hangi bağlama yapılandırmaları destekliyorsa ve işaretçilerde en iyi uygulamalar. Önemli noktaları ve bu bölümdeki ilgili konular hakkında ayrıntılar aşağıdaki tabloda özetlenmiştir.

Güvenilir oturum [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uç noktaları arasında gönderilen iletileri SOAP veya taşıma aracılar aktarılır ve yalnızca bir kez ve isteğe bağlı olarak, bunlar gönderildiği adres aynı sırayla teslim sağlayarak featrues sağlar.

Güvenilir bir oturum ile kullanmak için bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulamanın, aşağıdakilerden birini kullanın sistem tarafından sağlanan bağlamalar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] , varsayılan olarak veya bir seçenek olarak güvenilir oturum desteklemek veya oturumu destekler, kendi özel bağlama oluşturma.

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
[Oturumlar, örnek oluşturma ve eşzamanlılık](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)
