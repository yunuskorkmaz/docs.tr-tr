---
title: Yönetilen İş Parçacığı Oluşturma
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 7b46a7d9-c6f1-46d1-a947-ae97471bba87
ms.openlocfilehash: d6b8a0a4e16aa3169888958fa1376bfa61526dbd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73137938"
---
# <a name="managed-threading"></a>Yönetilen İş Parçacığı Oluşturma
İster bir işlemciye veya birkaç işlemciye sahip bilgisayarlar için geliştiriyor olun, uygulamanız şu anda başka bir iş yapıyor olsa bile, uygulamanızın kullanıcıyla en duyarlı etkileşimi sağlamasını istersiniz. Birden çok yürütme iş parçacığı kullanmak, uygulamanızın kullanıcıya yanıt vermesini sağlamanın ve aynı zamanda kullanıcı olayları arasında ve hatta sırasında işlemciyi kullanmanın en güçlü yollarından biridir. Bu bölümde iş parçacığı temel kavramları tanıtırken, yönetilen iş parçacığı kavramları ve yönetilen iş parçacığı kullanarak odaklanır.  
  
> [!NOTE]
> .NET Framework 4 ile başlayarak, çok iş parçacığı programlama <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> büyük ölçüde ve sınıflar, [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)ile basitleştirilmiş, <xref:System.Collections.Concurrent?displayProperty=nameWithType> ad alanında yeni eşzamanlı toplama sınıfları ve iş parçacığı yerine görev kavramına dayalı yeni bir programlama modeli. Daha fazla bilgi için [Bkz. Paralel Programlama.](../../../docs/standard/parallel-programming/index.md)  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Yönetilen İş Parçacığı Oluşturma Temelleri](../../../docs/standard/threading/managed-threading-basics.md)  
 Yönetilen iş parçacığına genel bir bakış sağlar ve birden çok iş parçacığının ne zaman kullanılacağını tartışır.  
  
 [İş Parçacığı ve İş Parçacığı kullanma](../../../docs/standard/threading/using-threads-and-threading.md)  
 İş iş parçacığı oluşturma, başlatma, duraklatma, devam etme ve iptal etme işlemini açıklar.  
  
 [Yönetilen İş Parçacığı Oluşturma En İyi Yöntemleri](../../../docs/standard/threading/managed-threading-best-practices.md)  
 Eşitleme düzeylerini, kilitlenmeleri ve yarış koşullarını nasıl önleyebildiğini ve diğer iş parçacığı sorunlarını tartışır.  
  
 [İş Parçacığı Nesneleri ve Özellikleri](../../../docs/standard/threading/threading-objects-and-features.md)  
 İş parçacıklarının etkinliklerini ve farklı iş parçacıklarında erişilen nesnelerin verilerini eşitlemek için kullanabileceğiniz yönetilen sınıfları açıklar ve iş parçacığı havuzu iş parçacıklarına genel bakış sağlar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Threading>  
 Yönetilen iş parçacıklarını kullanmak ve eşitlemek için sınıfları içerir.  
  
 <xref:System.Collections.Concurrent>  
 Birden çok iş parçacığı ile kullanım için güvenli toplama sınıfları içerir.  
  
 <xref:System.Threading.Tasks>  
 Eşzamanlı işleme görevleri oluşturmak ve zamanletmek için sınıfları içerir.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Uygulama Etki Alanları](../../../docs/framework/app-domains/application-domains.md)  
 Uygulama etki alanlarına ve Bunların Ortak Dil Altyapısı tarafından kullanımına genel bir bakış sağlar.  
  
 [Zaman Uyumsuz Dosya G/Ç](../../../docs/standard/io/asynchronous-file-i-o.md)  
 Zaman uyumsuz I/O'nun performans avantajlarını ve temek işleyişini açıklar.  
  
 [Görev Tabanlı Zaman Uyumsuz Desen (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 .NET'te eşzamanlı programlama için önerilen desenin genel görünümünü sağlar.  
  
 [Zaman Uyumlu Metotları Zaman Uyumsuz Olarak Çağırma](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 Temsilcilerin yerleşik özelliklerini kullanarak iş parçacığı havuzu iş parçacıklarındaki yöntemleri nasıl çağırılanın açıklar.  
  
 [Paralel Programlama](../../../docs/standard/parallel-programming/index.md)  
 Uygulamalarda birden çok iş parçacığı kullanımını basitleştiren paralel programlama kitaplıklarını açıklar.  
  
 [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 Birden çok işlemciden yararlanmak için sorguları paralel olarak çalıştırmak için bir sistem açıklar.
