---
title: "İşlem Modelleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48a8bc1b-128b-4cf1-a421-8cc73223c340
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7c74b1826ca280ba05420449758cdbb84dac3e93
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="transaction-models"></a>İşlem Modelleri
Bu konu, işlem programlama modelleri ve Microsoft'un sağladığı altyapı bileşenleri arasındaki ilişkiyi açıklar.  
  
 İşlemlerde kullanırken [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], farklı işlem modelleri arasında seçmezseniz, ancak bunun yerine tümleşik ve tutarlı bir modeli farklı katmanlar işletim olduğunu anlamak önemlidir.  
  
 Aşağıdaki bölümlerde üç birincil hareket bileşenlerini açıklar.  
  
## <a name="windows-communication-foundation-transactions"></a>Windows Communication Foundation işlemleri  
 İşlem desteği, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] işlem Hizmetleri yazma sağlar. Ayrıca, WS-AtomicTransaction (WS-AT) protokolü için kendi desteği ile uygulamaları işlemleri kullanarak yerleşik Web hizmetlerine akabilir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] veya üçüncü taraf teknolojisi.  
  
 İçinde bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet veya uygulama [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] öznitelikleri ve bildirimli olarak nasıl ve ne zaman altyapı oluşturmak, akış ve işlemleri eşitlemek belirtmek için yapılandırma işlem özellikleri sağlar.  
  
## <a name="systemtransactions-transactions"></a>System.Transactions işlemleri  
 <xref:System.Transactions> Ad alanı, temel alan hem bir açık programlama modeli sağlar <xref:System.Transactions.Transaction> sınıfı yanı sıra örtük bir programlama modeli kullanarak <xref:System.Transactions.TransactionScope> içinde altyapı otomatik olarak yönetir işlemleri sınıfı.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Bu iki modeli kullanarak bir işlem uygulaması oluşturmak için bkz: nasıl [işlem uygulaması yazma](http://go.microsoft.com/fwlink/?LinkId=94947).  
  
 İçinde bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet veya uygulama <xref:System.Transactions> hareketleri içinde bir istemci uygulaması oluşturmak ve gerektiğinde, hizmet içinde açıkça bir işlem ile etkileşmek için programlama modeli sağlar.  
  
## <a name="msdtc-transactions"></a>MSDTC işlemleri  
 Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) dağıtılmış işlemler için destek sağlayan bir işlem yöneticisidir.  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][DTC Programcının Başvurusu](http://go.microsoft.com/fwlink/?LinkId=94948).  
  
 İçinde bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet veya uygulama, MSDTC gerekli altyapıyı sunar. bir istemci veya hizmet içinde oluşturulan işlem koordinasyonu için.
