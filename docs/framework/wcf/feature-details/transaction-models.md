---
title: İşlem Modelleri
ms.date: 03/30/2017
ms.assetid: 48a8bc1b-128b-4cf1-a421-8cc73223c340
ms.openlocfilehash: 9efe8c6994cc80957b707bbae0885a3c5896f70a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33499030"
---
# <a name="transaction-models"></a>İşlem Modelleri
Bu konu, işlem programlama modelleri ve Microsoft'un sağladığı altyapı bileşenleri arasındaki ilişkiyi açıklar.  
  
 İşlemleri Windows Communication Foundation (WCF) kullanırken, farklı işlem modelleri arasında seçmezseniz, ancak bunun yerine tümleşik ve tutarlı bir modeli farklı katmanlar işletim olduğunu anlamak önemlidir.  
  
 Aşağıdaki bölümlerde üç birincil hareket bileşenlerini açıklar.  
  
## <a name="windows-communication-foundation-transactions"></a>Windows Communication Foundation işlemleri  
 İşlem desteği, WCF işlem Hizmetleri yazma sağlar. Ayrıca, WS-AtomicTransaction (WS-AT) protokolü için kendi desteği ile uygulamaları WCF veya üçüncü taraf teknolojisi kullanılarak oluşturulmuş Web hizmetlerine işlemleri akabilir.  
  
 Bir WCF hizmeti veya uygulamayı WCF işlem özellikleri öznitelikleri ve bildirimli olarak nasıl ve ne zaman altyapı oluşturmak, akış ve işlemleri eşitlemek belirtmek için yapılandırmasını sağlar.  
  
## <a name="systemtransactions-transactions"></a>System.Transactions işlemleri  
 <xref:System.Transactions> Ad alanı, temel alan hem bir açık programlama modeli sağlar <xref:System.Transactions.Transaction> sınıfı yanı sıra örtük bir programlama modeli kullanarak <xref:System.Transactions.TransactionScope> içinde altyapı otomatik olarak yönetir işlemleri sınıfı.  
  
 Bu iki modeli kullanarak bir işlem uygulaması oluşturma hakkında daha fazla bilgi için bkz: [işlem uygulaması yazma](http://go.microsoft.com/fwlink/?LinkId=94947).  
  
 Bir WCF hizmeti veya uygulamayı <xref:System.Transactions> hareketleri içinde bir istemci uygulaması oluşturmak ve gerektiğinde, hizmet içinde açıkça bir işlem ile etkileşmek için programlama modeli sağlar.  
  
## <a name="msdtc-transactions"></a>MSDTC işlemleri  
 Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) dağıtılmış işlemler için destek sağlayan bir işlem yöneticisidir.  
  
 Daha fazla bilgi için bkz: [DTC Programcının Başvurusu](http://go.microsoft.com/fwlink/?LinkId=94948).  
  
 Bir WCF hizmeti veya uygulamayı MSDTC bir istemci veya hizmet içinde oluşturulan işlem koordinasyonu için altyapı sağlar.
