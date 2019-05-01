---
title: Kaynak Yöneticisi uygulama
ms.date: 03/30/2017
ms.assetid: d5c153f6-4419-49e3-a5f1-a50ae4c81bf3
ms.openlocfilehash: f3e29dae095fbe56181cf7b67787c1044efa07ae
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793711"
---
# <a name="implementing-a-resource-manager"></a>Kaynak Yöneticisi uygulama
Bir işlemde kullanılan her kaynak eylemlerini bir işlem yöneticisi tarafından düzenlenir bir kaynak yöneticisi tarafından yönetilir. Kaynak yöneticileri kararlılık ve yalıtım uygulama sağlamak için hareket yöneticisi ile işbirliği içinde çalışın. Microsoft SQL Server, kalıcı ileti sıraları, bellek içi karma tabloları kaynak yöneticilerinin tüm örnekleri mevcuttur.  
  
 Kalıcı veya geçici Veri Kaynağı Yöneticisi yönetir. Süreklilik (veya tersine volatility) kaynak yöneticisi kaynak yöneticisi hatası kurtarma destekleyip başvuruyor. Bir kaynak yöneticisi hatası kurtarma destekliyorsa, aşama 1 sırasında veri kalıcı depolama devam (Hazırla) sağlayacak şekilde kaynak yöneticisi kalırsa, onu kurtarma sonra işlemi yeniden listeleme ve bildirimlere dayalı uygun eylemleri gerçekleştirin İşlem Yöneticisi'nden aldı. Genel olarak, geçici kaynak yöneticileri bir bellek içi veri yapısı (örneğin, bir bellek içi hareket gerçekleşti-karma tablosu) gibi geçici kaynaklarını yönetmek ve kalıcı kaynak yöneticileri daha kalıcı bir yedekleme deposu sahip kaynakları yönetin (örneğin, bir Veritabanı) yedekleme deposu ayarlanmış olan bir disktir.  
  
 Bir işlemde bir kaynak için sırada bu işleme gerekir. <xref:System.Transactions.Transaction> Sınıfı tanımlayan bir dizi yöntem adları ile başlayan **Enlist** bu işlevselliği sağlar. Farklı **Enlist** yöntemleri karşılık farklı türde bir kaynak yöneticisi olabilir liste için. Özellikle, kullandığınız <xref:System.Transactions.Transaction.EnlistVolatile%2A> geçici kaynaklar için yöntemleri ve <xref:System.Transactions.Transaction.EnlistDurable%2A> kalıcı kaynaklar için yöntem. Kullanılacak karar sonra kolaylık <xref:System.Transactions.Transaction.EnlistDurable%2A> veya <xref:System.Transactions.Transaction.EnlistVolatile%2A> , kaynağın süreklilik desteğini tabanlı yöntemi, iki aşaması yürütme içinde (2PC) uygulayarak katılmak için kaynak listeleme <xref:System.Transactions.IEnlistmentNotification> , kaynak yöneticisi için arabirim. 2PC hakkında daha fazla bilgi için bkz. [tek aşamalı ve çok aşamalı bir işlem Sistemi'ne](../../../../docs/framework/data/transactions/committing-a-transaction-in-single-phase-and-multi-phase.md).  
  
 Kaydetme tarafından kaynak yöneticisi işlem tamamlandığında veya iptal edildiğinde bu işlem Yöneticisi'nden geri çağırmaları alır sağlar. Bir örneği yok <xref:System.Transactions.IEnlistmentNotification> başına liste. Genellikle, işlem başına bir liste yoktur ancak bir kaynak yöneticisi birden çok kez aynı işleme seçebilirsiniz.  
  
 Liste sonra kaynak yöneticisi hareketin isteklerine yanıt verir. Kalıcı Kaynak Yöneticisi yönettiği geri almak veya kaynaklar hareketin iş Yinele olanak tanımak için yeterli bilgi depolar. Bunu yapmak için birçok yolu vardır; Veri sürümlerini saklama veya değişiklikleri bir günlük tutma iki ortak teknikler mevcuttur.  
  
 Uygulama hareketi tamamlar olduğunda işlem yöneticisi iki aşamalı tamamlama protokolü başlatır. İşlem yöneticisi hareketi tamamlamak için hazırlanmış olmadığını her kayıtlı Kaynak Yöneticisi ilk ister. Kaynak Yöneticisi tamamlamaya hazırlamalısınız — tamamlama veya işlem durdurma kendisine onu hazırlar.  
  
 Böylece sistem başarısız olsa bile Kaynak Yöneticisi, kurtarabilirsiniz hazırla aşamasında, eski ve yeni veri kalıcı Kaynak Yöneticisi tutarlı depolama kaydeder. Kaynak Yöneticisi hazırlayabilirsiniz, kendi oy tamamlama veya işlem iptal verilip üzerinde hareket yöneticisi bildirir. Herhangi bir kaynak yöneticisi hazırlamak için bir hata bildirirse, hareket yöneticisi her kaynak yöneticisi için bir geri alma komutu gönderir ve uygulama için yürütme başarısız gösterir.  
  
 Hazır sonra bir kaynak yöneticisi bir tamamlama alır kadar bekleyin veya geri çağırma işlemi Yöneticisi'nden Aşama 2 durdurma. Genel olarak, bir saniyenin tüm hazırla ve yürütme protokol tamamlar. Sistem veya iletişim hatası yoksa, tamamlama veya iptal bildirimi dakika veya saat için gelebilir değil. Bu süre zarfında kaynak işlemin sonucu hakkında şüpheli yöneticisidir. İşlem kaydedilmiş veya iptal emin değilseniz. Kaynak Yöneticisi bir işlem hakkında şüpheli olsa da, dolayısıyla bu değişiklikleri diğer işlemler ayırma kilitli işlem tutarak değiştirilen verileri korur.  
  
 Bir kaynak yöneticisi başarısız olduğunda, tüm kayıtlı hareketlerini hazır ya da önce hatası kaydedilen olanlar dışında iptal edilir. Kalıcı Kaynak Yöneticisi yeniden başlatıldığında alarak hazırla aşamasında yazılmış hazırla bilgilerini yöneten kaynakları taahhüt durumunu yeniden yapılandırılacağını ve yürütmeleri veya buna göre bu işlemleri durdurur.  
  
 Özet olarak, kararlı ve sürekli işlemleri yapmak için iki aşamalı tamamlama protokolü ve kaynak yöneticileri birleştirin.  
  
 <xref:System.Transactions.Transaction> Sınıfı sağlar <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> bir Promotable tek aşaması liste'nı (PSPE) listeleme yöntemi. Bu bir kalıcı Kaynak Yöneticisi (ana bilgisayar ve "daha sonra gerekirse MSDTC tarafından yönetilmek üzere ilerletilmiş bir işlem sahibi" RM) sağlar. Bunun hakkında daha fazla bilgi için bkz. [tek aşamalı işleme ve yükseltilebilir tek aşamalı bildirim kullanarak en iyi duruma getirme](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 Genel olarak kaynak yöneticisi tarafından izlenen adımları aşağıdaki konulara özetlenmiştir.  
  
 [Bir İşlemde Kaynakları Katılımcı Olarak Kaydetme](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md)  
  
 Nasıl sürekli veya geçici bir kaynak bir işleme açıklar.  
  
 [Tek Aşamalı ve Çok Aşamalı İşlem Gerçekleştirme](../../../../docs/framework/data/transactions/committing-a-transaction-in-single-phase-and-multi-phase.md)  
  
 Bildirim Kaydet ve yürütme hazırlamak için bir kaynak yöneticisi nasıl yanıt vereceğini açıklar.  
  
 [Kurtarma Gerçekleştirme](../../../../docs/framework/data/transactions/performing-recovery.md)  
  
 Nasıl sürekli Kaynak Yöneticisi hata verdi kurtarır açıklar.  
  
 [Kaynaklara Erişimde Güvenlik Güven Düzeyleri](../../../../docs/framework/data/transactions/security-trust-levels-in-accessing-resources.md)  
  
 Nasıl üç System.Transactions için güven düzeyleri kaynakları türlerini erişimini kısıtlamak açıklayan, <xref:System.Transactions> kullanıma sunar.  
  
 [Tek Aşamalı İşleme ve Yükseltilebilir Tek Aşamalı Bildirim kullanarak en iyi duruma getirme](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md)  
  
 Kaynak yöneticileri uygulamalar için kullanılabilir olan en iyi hale getirme yöntemleri açıklar.
