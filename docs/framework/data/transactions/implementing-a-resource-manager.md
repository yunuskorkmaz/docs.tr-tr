---
title: Kaynak Yöneticisi uygulama
ms.date: 03/30/2017
ms.assetid: d5c153f6-4419-49e3-a5f1-a50ae4c81bf3
ms.openlocfilehash: f3e29dae095fbe56181cf7b67787c1044efa07ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="implementing-a-resource-manager"></a>Kaynak Yöneticisi uygulama
Bir işlem içinde kullanılan her bir kaynağın eylemlerini bir işlem yöneticisi tarafından düzenlenir kaynak yöneticisi tarafından yönetilir. Kaynak yöneticileri uygulama kararlılık ve yalıtım garantisi ile sağlamak için işlem yöneticisi işbirliği içinde çalışır. Microsoft SQL Server, kalıcı ileti sıraları, bellek içi karma tabloları kaynak yöneticilerinin tüm örnekleri mevcuttur.  
  
 Kalıcı veya geçici Veri Kaynağı Yöneticisi yönetir. Süreklilik (veya tersine volatility) kaynak yöneticisi kaynak yöneticisi hatası kurtarma destekleyip başvuruyor. Kaynak Yöneticisi hatadan kurtarma destekliyorsa, aşama 1 sırasında verileri dayanıklı depolama devam (hazırlama) sağlayacak şekilde Kaynak Yöneticisi'ni kullanılamaz hale gelirse, Kurtarma sırasında işlemdeki yeniden listeleme ve bildirimlerini göre uygun eylemleri gerçekleştirin İşlem Yöneticisi'nden aldı. Genel olarak, geçici kaynak yöneticileri bir bellek içi veri yapısı (örneğin, bir bellek içi işlem yapılan işlem-hashtable) gibi volatile kaynakları yönetme ve dayanıklı kaynak yöneticileri yönetme daha kalıcı bir yedekleme deposu kaynakları (örneğin, bir Veritabanı), yedekleme deposu disktir.  
  
 Bir işlemde bir kaynak için sırayla işlem listesine gerekir. <xref:System.Transactions.Transaction> Sınıfı tanımlayan bir dizi yöntem ile başlar, adları **Enlist** bu işlevsellik sağlar. Farklı **Enlist** yöntemleri karşılık gelen bir Kaynak Yöneticisi'ni olabilir kaydı farklı türleri için. Özellikle, kullandığınız <xref:System.Transactions.Transaction.EnlistVolatile%2A> geçici kaynaklar için yöntemleri ve <xref:System.Transactions.Transaction.EnlistDurable%2A> kalıcı kaynaklar için yöntem. Kullanılacak karar sonra kolaylık <xref:System.Transactions.Transaction.EnlistDurable%2A> veya <xref:System.Transactions.Transaction.EnlistVolatile%2A> , kaynağın süreklilik desteğini tabanlı yöntemi, iki aşaması yürütme içinde (2PC) uygulayarak katılmak için kaynak listeleme <xref:System.Transactions.IEnlistmentNotification> , kaynak yöneticisi için arabirim. 2PC hakkında daha fazla bilgi için bkz: [tek aşamalı ve çok aşama işlemde yürüten](../../../../docs/framework/data/transactions/committing-a-transaction-in-single-phase-and-multi-phase.md).  
  
 Kaydetme tarafından işlem tamamlandığında veya iptal edildiğinde, İşlem Yöneticisi'nden geri aramalar alır, Kaynak Yöneticisi'ni sağlar. Bir örneği yok <xref:System.Transactions.IEnlistmentNotification> başına liste. Genellikle, işlem başına bir kaydı yoktur, ancak aynı işlemde birden çok kez listeleme bir Kaynak Yöneticisi'ni seçebilirsiniz.  
  
 Kaydı sonra Kaynak Yöneticisi'ni işlemdeki isteklerine yanıt verir. Sağlam Kaynak Yöneticisi yönettiği geri almak veya işlemdeki iş kaynaklarına Yinele izin vermek için yeterli bilgi depolar. Bunu yapmak için birçok yolu vardır; Veri sürümlerini saklama veya değişiklikleri bir günlük tutma iki ortak teknikler mevcuttur.  
  
 Uygulamanın işlem onayladığında, işlem yöneticisi iki aşamalı yürütme Protokolü başlatır. İşlem yöneticisi hareketi için hazırlanan varsa her kayıtlı Kaynak Yöneticisi'ni ilk sorar. Kaynak Yöneticisi'ni uygulamak hazırlamanız gerekir — yürütün veya işlem iptal kendisine onu hazırlar.  
  
 Böylece sistem başarısız olsa bile Kaynak Yöneticisi, kurtarabilirsiniz hazırla aşamasında, eski ve yeni veri kalıcı Kaynak Yöneticisi tutarlı depolama kaydeder. Kaynak Yöneticisi'ni hazırlayabilirsiniz, işlem yöneticisi, oylama mi tamamlanmaya veya işlem iptal bildirir. Herhangi bir kaynak yöneticisi hazırlama hatası bildirirse, işlem yöneticisi her kaynak yöneticisi için bir geri alma komutu gönderir ve uygulamaya yürütme başarısızlığını gösterir.  
  
 Hazırlanan sonra kaynak yöneticisi bir yürütme ulaşana kadar bekleyin veya Aşama 2 geri çağırma İşlem Yöneticisi'nden iptal gerekir. Genel olarak, bir saniyenin tüm hazırla ve yürütme protokol tamamlar. Sistem veya iletişim hatası yoksa, tamamlama veya iptal bildirimi dakika veya saat için gelebilir değil. Bu dönemde kaynak işlemin sonucuyla ilgili şüpheli yöneticisidir. İşlem yürütülmemiş veya durdurulmamış bilmez. Kaynak Yöneticisi'ni şüpheli bir işlem hakkında olsa da, böylece diğer işlemler bu değişikliklerden yalıtarak kilitli, işlem tutarak değiştirilen veriler tutar.  
  
 Kaynak Yöneticisi başarısız olduğunda, tüm kayıtlı hareketlerini hazırlanmış ya da hatasından önce kaydedilmiş dışında iptal edilir. Sağlam Kaynak Yöneticisi yeniden başlatıldığında, hazırlama aşamasında, yazılan prepare bilgileri alarak yönettiği kaynaklar kaydedilmiş durumunu yeniden yapılandırılacağını ve tamamlar veya bu işlemler buna uygun olarak iptal eder.  
  
 Özet olarak, kararlı ve sürekli işlemleri yapmak için iki aşamalı yürütme protokolü ve kaynak yöneticileri birleştirin.  
  
 <xref:System.Transactions.Transaction> Sınıfı sağlar <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> bir Promotable tek aşaması liste'nı (PSPE) listeleme yöntemi. Bu sağlam Kaynak Yöneticisi (RM barındırmak ve "gerekirse MSDTC tarafından yönetilecek daha sonra ilerletilen bir işlem kendi") sağlar. Bunun hakkında daha fazla bilgi için bkz: [tek aşaması kaydetmek ve yükseltilebilir tek aşaması bildirim kullanarak en iyi duruma getirme](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 Genel olarak kaynak yöneticisi tarafından izlenen adımları aşağıdaki konulara özetlenmiştir.  
  
 [Bir İşlemde Kaynakları Katılımcı Olarak Kaydetme](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md)  
  
 Kalıcı veya geçici bir kaynak bir işlem nasıl listesine açıklar.  
  
 [Tek Aşamalı ve Çok Aşamalı İşlem Gerçekleştirme](../../../../docs/framework/data/transactions/committing-a-transaction-in-single-phase-and-multi-phase.md)  
  
 Bildirim Kaydet ve yürütme hazırlamak için bir kaynak yöneticisi nasıl yanıt vereceğini açıklar.  
  
 [Kurtarma Gerçekleştirme](../../../../docs/framework/data/transactions/performing-recovery.md)  
  
 Nasıl sürekli Kaynak Yöneticisi hata verdi kurtarır açıklar.  
  
 [Kaynaklara Erişimde Güvenlik Güven Düzeyleri](../../../../docs/framework/data/transactions/security-trust-levels-in-accessing-resources.md)  
  
 Nasıl güven System.Transactions için üç düzeyde kaynakları türlerine erişimi kısıtlama açıklar, <xref:System.Transactions> kullanıma sunar.  
  
 [Tek Aşamalı İşleme ve Yükseltilebilir Tek Aşamalı Bildirim kullanarak en iyi duruma getirme](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md)  
  
 Kaynak yöneticileri uygulamalar için kullanılabilir olan en iyi hale getirme yöntemleri açıklar.
