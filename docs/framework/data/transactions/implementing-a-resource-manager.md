---
title: Kaynak Yöneticisi uygulama
ms.date: 03/30/2017
ms.assetid: d5c153f6-4419-49e3-a5f1-a50ae4c81bf3
ms.openlocfilehash: f64a729f49d546dd16c25a2be1f9bd64a2ca8f63
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205956"
---
# <a name="implementing-a-resource-manager"></a>Kaynak Yöneticisi uygulama
Bir işlemde kullanılan her kaynak, eylemleri bir işlem yöneticisi tarafından koordine edilen bir kaynak yöneticisi tarafından yönetilir. Kaynak yöneticileri, uygulamayı kararlılık ve yalıtıma garantisi sağlamak için işlem yöneticisiyle birlikte çalışır. Microsoft SQL Server, kalıcı ileti sıraları, bellek içi karma tabloları kaynak yöneticilerinin tüm örnekleri mevcuttur.  
  
 Kalıcı veya geçici Veri Kaynağı Yöneticisi yönetir. Süreklilik (veya tersine volatility) kaynak yöneticisi kaynak yöneticisi hatası kurtarma destekleyip başvuruyor. Bir Kaynak Yöneticisi hata kurtarmayı destekliyorsa, Aşama 1 sırasında verileri dayanıklı depolamaya (hazırla) devam ettirir. Bu, Resource Manager kapalıysa, kurtarma sonrasında işlemde yeniden listeleme ve bildirimlere göre uygun eylemleri gerçekleştirmenize olanak sağlar işlem yöneticisinden alındı. Genel olarak, geçici kaynak yöneticileri bellek içi veri yapısı (örneğin, bellek içi bir işlem Hashtable) gibi geçici kaynakları yönetir ve dayanıklı kaynak yöneticileri, daha kalıcı bir yedekleme deposuna sahip kaynakları yönetir (örneğin, yedekleme deposu disk olan veritabanı).  
  
 Bir kaynağın bir işleme katılmasını sağlamak için, işlem içinde listelenmesi gerekir. Sınıfı <xref:System.Transactions.Transaction> , bu işlevselliği sağlayan, adları **Listeleme** ile başlayan bir yöntemler kümesini tanımlar. Farklı **Listeleme** yöntemleri, bir kaynak yöneticisi 'nin sahip olabileceği farklı kayıt türlerine karşılık gelir. Özellikle, kullandığınız <xref:System.Transactions.Transaction.EnlistVolatile%2A> geçici kaynaklar için yöntemleri ve <xref:System.Transactions.Transaction.EnlistDurable%2A> kalıcı kaynaklar için yöntem. Kullanılacak karar sonra kolaylık <xref:System.Transactions.Transaction.EnlistDurable%2A> veya <xref:System.Transactions.Transaction.EnlistVolatile%2A> , kaynağın süreklilik desteğini tabanlı yöntemi, iki aşaması yürütme içinde (2PC) uygulayarak katılmak için kaynak listeleme <xref:System.Transactions.IEnlistmentNotification> , kaynak yöneticisi için arabirim. 2PC hakkında daha fazla bilgi için bkz. [tek aşamalı ve çok aşamalı bir işlem](committing-a-transaction-in-single-phase-and-multi-phase.md)yürütme.  
  
 Kaynak Yöneticisi, işlem tamamlandığında veya durdurulduğunda işlem yöneticisinden geri çağırmaları almasını sağlar. Bir örneği yok <xref:System.Transactions.IEnlistmentNotification> başına liste. Genellikle, işlem başına bir kayıt vardır ancak bir kaynak yöneticisi aynı işlemde birden çok kez Listeleme işlemini seçebilir.  
  
 Kayıt sonrasında, Resource Manager işlemin isteklerine yanıt verir. Dayanıklı bir kaynak yöneticisi, yönettiği kaynaklar üzerinde hareketin işini geri alma veya yeniden yapma izni vermek için yeterli bilgi depolar. Bunu yapmak için birçok yolu vardır; Veri sürümlerini saklama veya değişiklikleri bir günlük tutma iki ortak teknikler mevcuttur.  
  
 Uygulama işlemi tamamlandığında, işlem Yöneticisi iki aşamalı tamamlama protokolünü başlatır. İşlem Yöneticisi önce, kayıt işlemini yürütmek üzere hazırlanmışsa, her bir kayıtlı kaynak yöneticisini önce sorar. Resource Manager 'ın işlemeye hazırlanması gerekir — işlemi yürütmek veya işlemi iptal etmek için kendisini yeniden hazırlar.  
  
 Böylece sistem başarısız olsa bile Kaynak Yöneticisi, kurtarabilirsiniz hazırla aşamasında, eski ve yeni veri kalıcı Kaynak Yöneticisi tutarlı depolama kaydeder. Resource Manager hazırlanıp, işlem yöneticisine işleme veya işlemin iptal edilip edilmeyeceğini bildiren oya bildirir. Herhangi bir kaynak yöneticisi hazırlanmak üzere bir hata bildirirse, işlem yöneticisi her kaynak yöneticisi için bir geri alma komutu gönderir ve uygulamaya yapılan işleme başarısızlığını gösterir.  
  
 Hazırlandıktan sonra Kaynak Yöneticisi, Aşama 2 ' de işlem yöneticisi 'nden bir işleme veya iptal geri araması yapana kadar beklemeniz gerekir. Genel olarak, bir saniyenin tüm hazırla ve yürütme protokol tamamlar. Sistem veya iletişim hatası yoksa, tamamlama veya iptal bildirimi dakika veya saat için gelebilir değil. Bu süre boyunca, Kaynak Yöneticisi işlemin sonucu hakkında şüphedir. İşlemin uygulanıp tamamlanmadığı veya durdurulmadığını bilmez. Kaynak Yöneticisi bir işlem hakkında şüpheli durumdayken, işlem kilitli tutarak verilerin değiştirilmesini korur, böylece bu değişiklikler diğer işlemlerden de yalıtıyor.  
  
 Bir kaynak yöneticisi başarısız olduğunda, hata öncesinde hazırlananlar veya taahhütler hariç tüm kayıtlı işlemleri iptal edilir. Kalıcı bir kaynak yöneticisi yeniden başlatıldığında, hazırlama aşamasında yazılan hazırlama bilgilerini alarak yönettiği kaynakların taahhüt durumunu yeniden oluşturur ve bu işlemleri buna göre kaydeder veya iptal eder.  
  
 Özet olarak, iki aşamalı tamamlama Protokolü ve kaynak yöneticileri, işlemleri atomik ve dayanıklı hale getirmek için birleştirir.  
  
 <xref:System.Transactions.Transaction> Sınıfı sağlar <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> bir Promotable tek aşaması liste'nı (PSPE) listeleme yöntemi. Bu, dayanıklı bir kaynak yöneticisinin (RM), daha sonra gerekirse MSDTC tarafından yönetilmek üzere ilerletilebilecek bir işlem barındırarak "sahip" olmasını sağlar. Bunun hakkında daha fazla bilgi için bkz. [tek aşamalı tamamlama ve promotable tek aşamalı bildirimi kullanarak iyileştirme](optimization-spc-and-promotable-spn.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 Genel olarak kaynak yöneticisi tarafından izlenen adımları aşağıdaki konulara özetlenmiştir.  
  
 [Bir İşlemde Kaynakları Katılımcı Olarak Kaydetme](enlisting-resources-as-participants-in-a-transaction.md)  
  
 Kalıcı veya geçici bir kaynağın bir işlemde nasıl listelenmesi gerektiğini açıklar.  
  
 [Tek Aşamalı ve Çok Aşamalı İşlem Gerçekleştirme](committing-a-transaction-in-single-phase-and-multi-phase.md)  
  
 Bildirim Kaydet ve yürütme hazırlamak için bir kaynak yöneticisi nasıl yanıt vereceğini açıklar.  
  
 [Kurtarma Gerçekleştirme](performing-recovery.md)  
  
 Nasıl sürekli Kaynak Yöneticisi hata verdi kurtarır açıklar.  
  
 [Kaynaklara Erişimde Güvenlik Güven Düzeyleri](security-trust-levels-in-accessing-resources.md)  
  
 System. Transactions için üç güven düzeyinin, <xref:System.Transactions> kullanıma sunan kaynak türleri üzerinde erişimi nasıl kısıtlayabileceğini açıklar.  
  
 [Tek Aşamalı İşleme ve Yükseltilebilir Tek Aşamalı Bildirim kullanarak en iyi duruma getirme](optimization-spc-and-promotable-spn.md)  
  
 Kaynak yöneticileri uygulamalar için kullanılabilir olan en iyi hale getirme yöntemleri açıklar.
