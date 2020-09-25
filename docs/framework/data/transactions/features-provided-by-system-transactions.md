---
title: System.Transactions Tarafından Sağlanan Özellikler
description: Kendi işlem uygulamanızı ve Resource Manager 'ı yazmak için .NET 'teki System. Transactions ad alanı tarafından sunulan özellikleri gözden geçirin.
ms.date: 03/30/2017
ms.assetid: e458cef9-63b5-4401-b448-1536dcd9d9e5
ms.openlocfilehash: 27c6224530b4faa1ada93db8147f9334f38b93ab
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91182928"
---
# <a name="features-provided-by-systemtransactions"></a>System.Transactions Tarafından Sağlanan Özellikler

Bu bölümde, <xref:System.Transactions> kendi işlem uygulamanızı ve Resource Manager 'ı yazmak için ad alanı tarafından sunulan özellikleri nasıl kullanabileceğiniz açıklanmaktadır. Özellikle, bu bölüm bir veya birden çok katılımcı ile bir işlem (yerel veya dağıtılmış) oluşturmayı ve katılmayı ele alır.  
  
## <a name="overview-of-systemtransactions"></a>System. Transactions 'a genel bakış  

 Ad alanındaki sınıflar tarafından sunulan altyapı, <xref:System.Transactions> SQL Server, ADO.net, Message Queuing (MSMQ) ve Microsoft Dağıtılmış işlem Düzenleyicisi (MSDTC) ' de başlatılan işlemleri destekleyerek, işlem programlamanın basit ve etkili olmasını sağlar. <xref:System.Transactions>Ad alanı, sınıfı kullanan bir açık programlama modeli <xref:System.Transactions.Transaction> ve ayrıca, <xref:System.Transactions.TransactionScope> işlem altyapısı tarafından otomatik olarak yönetilen sınıfı kullanarak örtülü programlama modeli sağlar. Bu iki modeli kullanarak bir işlem uygulaması oluşturma hakkında daha fazla bilgi için bkz. [Işlem uygulaması yazma](writing-a-transactional-application.md).  
  
 <xref:System.Transactions> Ad alanı türleri için bir kaynak yöneticisi uygulamak de sağlar. Kaynak Yöneticisi bir işlemde kullanılan dayanıklı veya geçici verileri yönetir ve uygulamayı bir kararlılık ve yalıtıma garantisi sağlamak için işlem yöneticisiyle birlikte çalışır. Altyapı tarafından sunulan işlem yöneticisi <xref:System.Transactions> birden çok geçici kaynak veya tek bir dayanıklı kaynak içeren işlemleri destekler. Kaynak Yöneticisi uygulama hakkında daha fazla bilgi için bkz. [uygulama kaynak yöneticisi](implementing-a-resource-manager.md).  
  
 İşlem Yöneticisi ayrıca, ek bir dayanıklı Kaynak Yöneticisi bir işlemle kendisini listelediğinden, DTC gibi disk tabanlı bir işlem yöneticisiyle koordine ederek, yerel işlemleri dağıtılmış işlemlere da saydam şekilde ilerletir. <xref:System.Transactions>Altyapının gelişmiş performans sağladığı iki anahtar yolu vardır.  
  
- <xref:System.Transactions>Bir işlem birden çok dağıtılmış kaynağa yayıldığında altyapının yalnızca MSDTC 'yi almasını sağlayan dinamik yükseltme. Dinamik yükseltme hakkında daha fazla bilgi için. [Işlem yönetimi yükseltme](transaction-management-escalation.md) konusuna bakın.  
  
- Bir veritabanı gibi bir kaynağın, işleme katılan tek varlıktır durumunda işlemin sahipliğini almasına izin veren promotable, kayıtlar. Daha sonra, gerekirse, <xref:System.Transactions> altyapı işlemin YÖNETIMINI MSDTC 'ye de gönderebilir. Bu, daha fazla MSDTC kullanma olasılığını azaltır. Promotable[kaydı, tek aşamalı işleme ve promotable tek aşamalı bildirimi kullanılarak konu iyileştirmede](optimization-spc-and-promotable-spn.md)derinlemesine anlatılacaktır.  
  
 <xref:System.Transactions>Ad alanı, sunduğu kaynak türlerine erişimi kısıtlayan, üç güven düzeyi olan Allowpartiallytrustedçağıranı (APTCA), DistributedTransactionPermission (DTP) ve tam güven düzeyini tanımlar. Çeşitli güven düzeyleri hakkında daha fazla bilgi için bkz. [kaynaklara erişim Içindeki güvenlik güven düzeyleri](security-trust-levels-in-accessing-resources.md).  
  
## <a name="in-this-section"></a>Bu bölümde  
  
### <a name="writing-a-transactional-application"></a>Işlem uygulaması yazma  

 <xref:System.Transactions>Ad alanı, işlem uygulamaları oluşturmak için iki model sağlar. [Işlem kapsamını kullanarak örtük bir Işlem uygulamak](implementing-an-implicit-transaction-using-transaction-scope.md) , <xref:System.Transactions> ad alanının sınıfını kullanarak örtük işlemler oluşturmayı nasıl desteklediğini açıklar <xref:System.Transactions.TransactionScope> .  
  
 [CommittableTransaction kullanılarak açık bir Işlem uygulamak](implementing-an-explicit-transaction-using-committabletransaction.md) , <xref:System.Transactions> ad alanının sınıfı kullanılarak açık işlemler oluşturmayı nasıl desteklediğini açıklar <xref:System.Transactions.CommittableTransaction> .  
  
 İşlemsel uygulama yazmayı kapsayan ek konular için bkz. [bir Işlem uygulaması yazma](writing-a-transactional-application.md).  
  
### <a name="implementing-a-resource-manager"></a>Bir kaynak yöneticisi uygulama  

 Bir işleme katılabileceğiniz bir kaynak yöneticisi uygulamak için bkz. [uygulama kaynak yöneticisi](implementing-a-resource-manager.md). Bu bölüm bir kaynağın kayıt işlemini, bir işlem yürüten, hatadan sonra kurtarmaya ve en iyi duruma getirme en iyi yöntemlerini ele alır.
