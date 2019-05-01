---
title: İşlem Modelleri
ms.date: 03/30/2017
ms.assetid: 48a8bc1b-128b-4cf1-a421-8cc73223c340
ms.openlocfilehash: 8731b72d0657aa420dbb020e216c3af059916ce9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62050785"
---
# <a name="transaction-models"></a>İşlem Modelleri
Bu konuda, işlem programlama modelleri ve Microsoft'un sağladığı altyapı bileşenleri arasındaki ilişkiyi açıklar.  
  
 İşlemleri Windows Communication Foundation (WCF) kullanırken, farklı işlem modelleri arasında belirlenmemesi, ancak bunun yerine, tümleşik ve tutarlı bir modeli farklı katmanına işletim olduğunu anlamak önemlidir.  
  
 Aşağıdaki bölümlerde, üç birincil işlem bileşeni açıklanmaktadır.  
  
## <a name="windows-communication-foundation-transactions"></a>Windows Communication Foundation işlemleri  
 İşlem desteği, WCF işlem hizmetlerinizi yazmanızı sağlar. Ayrıca, WS-AtomicTransaction (WS-AT) protokolü için kendi destek ile uygulamaların WCF ya da üçüncü taraf teknolojisi kullanılarak oluşturulan Web Hizmetleri için işlem akabilir.  
  
 Bir WCF hizmeti veya uygulaması, WCF işlem özellikleri öznitelikleri ve bildirimli olarak nasıl ve ne zaman altyapı oluşturmak, akış ve eşitleme işlemleri belirtmek için yapılandırma sağlar.  
  
## <a name="systemtransactions-transactions"></a>System.Transactions işlem  
 <xref:System.Transactions> Ad alanı, temel hem bir açık bir programlama modeli sağlar <xref:System.Transactions.Transaction> sınıfı, aynı zamanda örtük bir programlama modeli kullanarak <xref:System.Transactions.TransactionScope> , altyapı otomatik olarak yönetir işlemleri sınıfı.  
  
 Bu iki modeli kullanarak bir işlem uygulama oluşturma hakkında daha fazla bilgi için bkz. [bir işlem uygulama yazma](https://go.microsoft.com/fwlink/?LinkId=94947).  
  
 Bir WCF hizmeti veya uygulamayı <xref:System.Transactions> hareketleri içinde bir istemci uygulaması oluşturma ve gerektiğinde, hizmet içinde bir işlem ile açıkça etkileşim kurmak için kullanabileceğiniz bir programlama modeli sağlar.  
  
## <a name="msdtc-transactions"></a>MSDTC işlem  
 Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) dağıtılmış işlemler için destek sağlayan bir işlem yöneticisidir.  
  
 Daha fazla bilgi için [DTC Programcının Başvurusu](https://go.microsoft.com/fwlink/?LinkId=94948).  
  
 Bir WCF hizmeti veya uygulamayı MSDTC koordinasyonu bir istemci veya hizmet içinde oluşturulan işlem için altyapı sağlar.
