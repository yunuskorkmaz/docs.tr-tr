---
title: "System.Transactions tarafından sağlanan özellikleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e458cef9-63b5-4401-b448-1536dcd9d9e5
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: be3e2fec5d6859b38ae149e50fd1fe82838d8e08
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="features-provided-by-systemtransactions"></a>System.Transactions tarafından sağlanan özellikleri
Bu bölümde tarafından sağlanan özellikleri nasıl kullanabileceğinizi açıklar <xref:System.Transactions> işlem kendi uygulama ve Kaynak Yöneticisi yazmak için ad alanı. Özellikle, bu bölümde nasıl oluşturulacağı ve bir veya birden çok katılımcı olan işlem (yerel veya dağıtılmış) katılma ele alınmaktadır.  
  
## <a name="overview-of-systemtransactions"></a>System.Transactions genel bakış  
 Sınıflar tarafından sağlanan altyapıyı <xref:System.Transactions> ad alanı yapar işlem programlama basit ve verimli SQL Server, ADO.NET, Message Queuing (MSMQ) ve Microsoft Dağıtılmış işlem tarafından başlatılan işlemleri destekleme tarafından Düzenleyicisi (MSDTC). <xref:System.Transactions> Ad alanı, temel alan hem bir açık programlama modeli sağlar <xref:System.Transactions.Transaction> sınıfı yanı sıra örtük bir programlama modeli kullanarak <xref:System.Transactions.TransactionScope> hangi işlemleri otomatik olarak yönetilir altyapısı tarafından sınıfı. Bu iki modeli kullanarak bir işlem uygulaması oluşturma hakkında daha fazla bilgi için bkz: [işlem uygulaması yazma](../../../../docs/framework/data/transactions/writing-a-transactional-application.md).  
  
 <xref:System.Transactions> Ad alanı türleri için bir kaynak yöneticisi uygulamak de sağlar. Kaynak Yöneticisi uygulama kararlılık ve yalıtım garantisi ile sağlamak için bir işlem ve işlem yöneticisi işbirliği içinde iş kullanılan kalıcı veya geçici veri yönetir. Tarafından sağlanan işlem yöneticisi <xref:System.Transactions> altyapısını birden çok volatile kaynakları veya tek bir dayanıklı kaynak içeren işlemlerin destekler. Kaynak Yöneticisi uygulama ile ilgili daha fazla bilgi için bkz: [Resource Manager uygulama](../../../../docs/framework/data/transactions/implementing-a-resource-manager.md).  
  
 İşlem Yöneticisi'ni bir ek sağlam kaynak yöneticisi olan bir işlem kendisi kaydeder, DTC gibi bir disk tabanlı işlem yöneticisiyle iletişime geçerek dağıtılmış işlemler için yerel işlemler de şeffaf bir şekilde iletir. İki anahtar yolla, <xref:System.Transactions> altyapı, Gelişmiş performans sunar.  
  
-   Sağlar dinamik yükseltme <xref:System.Transactions> altyapı birden fazla dağıtılmış kaynak üzerinde bir işlemi yayıldığında MSDTC yalnızca ilgilenir. Dinamik yükseltme hakkında daha fazla bilgi için. bkz: [işlem yönetimi yükseltme](../../../../docs/framework/data/transactions/transaction-management-escalation.md) konu.  
  
-   İşlemde katılan yalnızca varlık ise işlem sahipliğini almak için bir veritabanı gibi bir kaynak veren yükseltilebilir listeler. Daha sonra gerekirse, <xref:System.Transactions> altyapı hala MSDTC harekete yönetim ilerletebilir. Bu, daha fazla MSDTC kullanma olasılığını azaltır. Yükseltilebilir kayıtlar konusunda ayrıntılı ele alınmıştır[tek aşaması kaydetmek ve yükseltilebilir tek aşaması bildirim kullanarak en iyi duruma getirme](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md).  
  
 <xref:System.Transactions> Ad alanını tanımlayan üç güven düzeyleri - AllowPartiallyTrustedCallers (APTCA), DistributedTransactionPermission(DTP) ve kısıtlama tam güven - erişim kaynak türleri bu açığa çıkarır. Çeşitli hakkında daha fazla bilgi için güven düzeyleri, bkz: [kaynaklar erişim güvenlik güven düzeylerini](../../../../docs/framework/data/transactions/security-trust-levels-in-accessing-resources.md).  
  
## <a name="in-this-section"></a>Bu bölümde  
  
### <a name="writing-a-transactional-application"></a>İşlem uygulaması yazma  
 <xref:System.Transactions> Ad alanı, işlemsel uygulamaları oluşturmak için iki modeli sağlar. [Örtük bir işlem kapsamı kullanarak işlem uygulama](../../../../docs/framework/data/transactions/implementing-an-implicit-transaction-using-transaction-scope.md) açıklar nasıl <xref:System.Transactions> ad alanı destekleyen kullanarak örtük hareketleri oluşturma <xref:System.Transactions.TransactionScope> sınıfı.  
  
 [Açık bir CommittableTransaction kullanarak işlem uygulama](../../../../docs/framework/data/transactions/implementing-an-explicit-transaction-using-committabletransaction.md) açıklar nasıl <xref:System.Transactions> ad alanı destekleyen açık işlemleri kullanarak oluşturma <xref:System.Transactions.CommittableTransaction> sınıfı.  
  
 İşlem uygulaması yazma kapsayan ek konular için bkz: [işlem uygulaması yazma](../../../../docs/framework/data/transactions/writing-a-transactional-application.md).  
  
### <a name="implementing-a-resource-manager"></a>Bir kaynak yöneticisi uygulama  
 Bir işlem içinde katılabilmesi için bir kaynak yöneticisi uygulamak için bkz: [Resource Manager uygulama](../../../../docs/framework/data/transactions/implementing-a-resource-manager.md). Bu bölüm, bir işlem hatası ve en iyi uygulamaları iyileştirme sonra kurtarma yürüten bir kaynak kaydı içerir.
