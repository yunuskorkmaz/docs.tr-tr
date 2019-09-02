---
title: System.Transactions Tarafından Sağlanan Özellikler
ms.date: 03/30/2017
ms.assetid: e458cef9-63b5-4401-b448-1536dcd9d9e5
ms.openlocfilehash: c3ef924edf34ae19be9eace85aaee5340025de7d
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205967"
---
# <a name="features-provided-by-systemtransactions"></a>System.Transactions Tarafından Sağlanan Özellikler
Bu bölümde, <xref:System.Transactions> kendi işlem uygulamanızı ve Resource Manager 'ı yazmak için ad alanı tarafından sunulan özellikleri nasıl kullanabileceğiniz açıklanmaktadır. Özellikle, bu bölüm bir veya birden çok katılımcı ile bir işlem (yerel veya dağıtılmış) oluşturmayı ve katılmayı ele alır.  
  
## <a name="overview-of-systemtransactions"></a>System. Transactions 'a genel bakış  
 <xref:System.Transactions> Ad alanındaki sınıflar tarafından sunulan altyapı, SQL Server, ADO.net, Message Queuing (MSMQ) ve Microsoft Dağıtılmış işleminde başlatılan işlemleri destekleyerek, işlem programlamanın basit ve etkili olmasını sağlar. Düzenleyici (MSDTC). Ad alanı, <xref:System.Transactions.Transaction> sınıfı kullanan bir açık programlama modeli ve ayrıca, işlem altyapısı tarafından otomatik olarak yönetilen <xref:System.Transactions.TransactionScope> sınıfı kullanarak örtülü programlama modeli sağlar. <xref:System.Transactions> Bu iki modeli kullanarak bir işlem uygulaması oluşturma hakkında daha fazla bilgi için bkz. [Işlem uygulaması yazma](writing-a-transactional-application.md).  
  
 <xref:System.Transactions> Ad alanı türleri için bir kaynak yöneticisi uygulamak de sağlar. Kaynak Yöneticisi bir işlemde kullanılan dayanıklı veya geçici verileri yönetir ve uygulamayı bir kararlılık ve yalıtıma garantisi sağlamak için işlem yöneticisiyle birlikte çalışır. <xref:System.Transactions> Altyapı tarafından sunulan işlem yöneticisi birden çok geçici kaynak veya tek bir dayanıklı kaynak içeren işlemleri destekler. Kaynak Yöneticisi uygulama hakkında daha fazla bilgi için bkz. [uygulama kaynak yöneticisi](implementing-a-resource-manager.md).  
  
 İşlem Yöneticisi ayrıca, ek bir dayanıklı Kaynak Yöneticisi bir işlemle kendisini listelediğinden, DTC gibi disk tabanlı bir işlem yöneticisiyle koordine ederek, yerel işlemleri dağıtılmış işlemlere da saydam şekilde ilerletir. <xref:System.Transactions> Altyapının gelişmiş performans sağladığı iki anahtar yolu vardır.  
  
- Bir işlem birden çok dağıtılmış kaynağa yayıldığında <xref:System.Transactions> altyapının yalnızca MSDTC 'yi almasını sağlayan dinamik yükseltme. Dinamik yükseltme hakkında daha fazla bilgi için. [Işlem yönetimi yükseltme](transaction-management-escalation.md) konusuna bakın.  
  
- Bir veritabanı gibi bir kaynağın, işleme katılan tek varlıktır durumunda işlemin sahipliğini almasına izin veren promotable, kayıtlar. Daha sonra, gerekirse, <xref:System.Transactions> altyapı işlemin yönetimini MSDTC 'ye de gönderebilir. Bu, daha fazla MSDTC kullanma olasılığını azaltır. Promotable[kaydı, tek aşamalı işleme ve promotable tek aşamalı bildirimi kullanılarak](optimization-spc-and-promotable-spn.md)konu iyileştirmede derinlemesine anlatılacaktır.  
  
 Ad <xref:System.Transactions> alanı, sunduğu kaynak türlerine erişimi kısıtlayan, üç güven düzeyi olan allowpartiallytrustedçağıranı (aptca), DistributedTransactionPermission (DTP) ve tam güven düzeyini tanımlar. Çeşitli güven düzeyleri hakkında daha fazla bilgi için bkz. [kaynaklara erişim Içindeki güvenlik güven düzeyleri](security-trust-levels-in-accessing-resources.md).  
  
## <a name="in-this-section"></a>Bu bölümde  
  
### <a name="writing-a-transactional-application"></a>Işlem uygulaması yazma  
 Ad <xref:System.Transactions> alanı, işlem uygulamaları oluşturmak için iki model sağlar. [İşlem kapsamını kullanarak örtük bir işlem uygulamak](implementing-an-implicit-transaction-using-transaction-scope.md) , <xref:System.Transactions> ad alanının <xref:System.Transactions.TransactionScope> sınıfını kullanarak örtük işlemler oluşturmayı nasıl desteklediğini açıklar.  
  
 [CommittableTransaction kullanılarak açık bir işlem uygulamak](implementing-an-explicit-transaction-using-committabletransaction.md) , <xref:System.Transactions> ad alanının <xref:System.Transactions.CommittableTransaction> sınıfı kullanılarak açık işlemler oluşturmayı nasıl desteklediğini açıklar.  
  
 İşlemsel uygulama yazmayı kapsayan ek konular için bkz. [bir Işlem uygulaması yazma](writing-a-transactional-application.md).  
  
### <a name="implementing-a-resource-manager"></a>Bir kaynak yöneticisi uygulama  
 Bir işleme katılabileceğiniz bir kaynak yöneticisi uygulamak için bkz. [uygulama kaynak yöneticisi](implementing-a-resource-manager.md). Bu bölüm bir kaynağın kayıt işlemini, bir işlem yürüten, hatadan sonra kurtarmaya ve en iyi duruma getirme en iyi yöntemlerini ele alır.
