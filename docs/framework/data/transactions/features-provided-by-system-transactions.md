---
title: System.Transactions Tarafından Sağlanan Özellikler
ms.date: 03/30/2017
ms.assetid: e458cef9-63b5-4401-b448-1536dcd9d9e5
ms.openlocfilehash: 6fc20f8249f37f69689fb3fc6b3144792badad3c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793698"
---
# <a name="features-provided-by-systemtransactions"></a>System.Transactions Tarafından Sağlanan Özellikler
Bu bölümde tarafından sağlanan özellikleri nasıl kullanabileceğiniz açıklanmaktadır <xref:System.Transactions> kendi işlem uygulama ve Kaynak Yöneticisi yazmak için ad alanı. Özellikle, bu bölüm, oluşturma ve bir işlemde (yerel veya dağıtılmış) bir veya birden fazla katılımcıları ile katılmak kapsar.  
  
## <a name="overview-of-systemtransactions"></a>System.Transactions genel bakış  
 Sınıfları tarafından sunulan altyapıyı <xref:System.Transactions> ad alanı yaptığı işlem programlama basit ve etkili SQL Server, ADO.NET, Message Queuing (MSMQ) ve Microsoft Dağıtılmış işlem tarafından başlatılan işlemleri destekleyerek Düzenleyicisi (MSDTC). <xref:System.Transactions> Ad alanı, temel hem bir açık bir programlama modeli sağlar <xref:System.Transactions.Transaction> sınıfı, aynı zamanda örtük bir programlama modeli kullanarak <xref:System.Transactions.TransactionScope> içinde işlemleri otomatik olarak yönetilir altyapısı tarafından sınıfı. Bu iki modeli kullanarak bir işlem uygulama oluşturma hakkında daha fazla bilgi için bkz. [bir işlem uygulama yazma](../../../../docs/framework/data/transactions/writing-a-transactional-application.md).  
  
 <xref:System.Transactions> Ad alanı türleri için bir kaynak yöneticisi uygulamak de sağlar. İşlem ve iş hareket yöneticisi ile işbirliği yaparak kararlılık ve yalıtım uygulama sağlamak için kullanılan kalıcı veya geçici Veri Kaynağı Yöneticisi yönetir. Tarafından sağlanan işlem yöneticisi <xref:System.Transactions> birden çok geçici kaynakları veya tek bir kalıcı kaynağı içeren hareketleri altyapısını destekler. Kaynak Yöneticisi uygulama ile ilgili daha fazla bilgi için bkz: [Kaynak Yöneticisi uygulama](../../../../docs/framework/data/transactions/implementing-a-resource-manager.md).  
  
 İşlem Yöneticisi DTC gibi bir disk tabanlı hareket yöneticisi ile bir ek kalıcı Kaynak Yöneticisi ile bir işlem kendisini kaydeder olduğunda eşgüdümünü sağlayarak dağıtılmış işlemler için yerel işlemler de saydam bir şekilde iletir. Anahtar iki yolu vardır, <xref:System.Transactions> Gelişmiş performans altyapı sağlar.  
  
- Sağlar dinamik yükseltme <xref:System.Transactions> altyapı bir işlemde birden çok dağıtılmış kaynaklara yayıldığında MSDTC yalnızca ilgilenir. Dinamik yükseltme hakkında daha fazla bilgi için. bkz: [işlem yönetim yükseltme](../../../../docs/framework/data/transactions/transaction-management-escalation.md) konu.  
  
- İşlem sırasında katılan yalnızca varlık ise işlem sahipliği veritabanı gibi bir kaynak veren promotable listeler. Gerekirse, <xref:System.Transactions> altyapı yine de yönetim MSDTC hareketin İlerlet. Bu, daha fazla MSDTC kullanma olasılığını azaltır. Promotable liste kapsamdaki konudaki derinliği[tek aşamalı işleme ve yükseltilebilir tek aşamalı bildirim kullanarak en iyi duruma getirme](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md).  
  
 <xref:System.Transactions> AllowPartiallyTrustedCallers (APTCA), DistributedTransactionPermission(DTP) ve kısıtlamak tam güven - erişim kaynak türleri için onu kullanıma sunan - ad alanı, üç güven düzeyleri tanımlar. Çeşitli hakkında daha fazla bilgi için güven düzeyleri bkz [güvenlik güven düzeyleri kaynakları erişme](../../../../docs/framework/data/transactions/security-trust-levels-in-accessing-resources.md).  
  
## <a name="in-this-section"></a>Bu bölümde  
  
### <a name="writing-a-transactional-application"></a>Bir işlem uygulama yazma  
 <xref:System.Transactions> Ad alanı, işlem uygulamaları oluşturmak için iki modeli sağlar. [İşlem kapsamı kullanarak örtük işlem uygulama](../../../../docs/framework/data/transactions/implementing-an-implicit-transaction-using-transaction-scope.md) açıklar nasıl <xref:System.Transactions> ad alanı destekler kullanarak örtük işlemleri oluşturma <xref:System.Transactions.TransactionScope> sınıfı.  
  
 [CommittableTransaction kullanarak belirtik işlem uygulama](../../../../docs/framework/data/transactions/implementing-an-explicit-transaction-using-committabletransaction.md) açıklar nasıl <xref:System.Transactions> ad alanı destekler kullanarak açık işlemleri oluşturma <xref:System.Transactions.CommittableTransaction> sınıfı.  
  
 Bir işlem uygulama yazma kapsayan ek için bkz: [bir işlem uygulama yazma](../../../../docs/framework/data/transactions/writing-a-transactional-application.md).  
  
### <a name="implementing-a-resource-manager"></a>Bir kaynak yöneticisi uygulama  
 Bir işlemde katılabilir bir kaynak yöneticisi uygulamak için bkz: [Kaynak Yöneticisi uygulama](../../../../docs/framework/data/transactions/implementing-a-resource-manager.md). Bu bölüm, bir işlem hatası ve en iyi duruma getirme en iyi uygulamalar sonra kurtarma Sistemi'ne bir kaynak liste kapsar.
