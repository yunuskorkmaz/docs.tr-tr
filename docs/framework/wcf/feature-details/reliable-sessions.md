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
ms.openlocfilehash: 910ad952192243c6aa8a79417ad711d8c2a4ba2e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84590546"
---
# <a name="reliable-sessions"></a>Güvenilir oturumlar

Bu bölümde, bir Windows Communication Foundation (WCF) güvenilir oturumunun ne olduğu, ne için kullanıldığı, ne zaman ve nasıl kullanılacağı, hangi bağlama yapılandırmalarının desteklediği ve en iyi yöntemlere yönelik işaretçiler açıklanmaktadır. Aşağıdaki tabloda, bu bölümdeki temel noktalara ve ilgili konulara ilişkin ayrıntılar özetlenmektedir.

Güvenilir oturum WCF, uç noktalar arasında gönderilen iletilerin SOAP veya aktarım aracıları arasında aktarılmasını ve yalnızca bir kez ve isteğe bağlı olarak, gönderildikleri sırada gönderilmesini sağlayan özellikler sunar.

WCF uygulamasıyla güvenilir bir oturum kullanmak için, varsayılan olarak veya bir seçenek olarak güvenilir bir oturumu destekleyen WCF 'de sistem tarafından belirtilen bağlamalardan birini kullanın veya oturumu destekleyen kendi özel bağlamalarınızı oluşturun.

## <a name="in-this-section"></a>Bu Bölümde

[Güvenilir oturumlara genel bakış](reliable-sessions-overview.md) Güvenilir oturumları, ne zaman kullanılacağını, güvenilir oturumları destekleyen farklı bağlamaları ve bunların nasıl çalıştığını açıklar.

[Nasıl yapılır: güvenilir bir oturum Içindeki Iletileri değiştirme](how-to-exchange-messages-within-a-reliable-session.md) Yapılandırmada belirtilen özel bir bağlama kullanılarak HTTP üzerinden güvenilir bir oturumun nasıl oluşturulacağını açıklar.

[Nasıl yapılır: güvenilir oturumlarda Iletileri güvenli hale getirme](how-to-secure-messages-within-reliable-sessions.md) Güvenilir bir oturumun nasıl güvence altına alınacağını açıklar.

[Nasıl yapılır: https Ile özel bir güvenilir oturum bağlama oluşturma](how-to-create-a-custom-reliable-session-binding-with-https.md) HTTPS üzerinden güvenilir bir oturumun nasıl oluşturulacağını açıklar.

[Güvenilir Oturumlar Için En Iyi uygulamalar](best-practices-for-reliable-sessions.md) Güvenilir bir oturum kullanımıyla ilişkili en iyi uygulamalardan bazılarını açıklar.

## <a name="reference"></a>Başvuru

<xref:System.ServiceModel.ReliableSession>

## <a name="see-also"></a>Ayrıca bkz.

- [Kuyruklar ve Güvenilir Oturumlar](queues-and-reliable-sessions.md)
- [Oturumlar, Örnek Oluşturma ve Eşzamanlılık](sessions-instancing-and-concurrency.md)
