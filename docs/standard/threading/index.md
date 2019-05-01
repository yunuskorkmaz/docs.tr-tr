---
title: Yönetilen İş Parçacığı Oluşturma
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 7b46a7d9-c6f1-46d1-a947-ae97471bba87
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c6447cd37e4718093acfb3a0e2db053c13a027d3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62015149"
---
# <a name="managed-threading"></a>Yönetilen İş Parçacığı Oluşturma
Bir işlemci veya birçok bilgisayarla geliştirmekte olduğunuz olup olmadığını uygulama şu anda diğer iş yapıyor olsanız bile, uygulamanızın en hızlı yanıt veren kullanıcı etkileşimi sağlamak istersiniz. Birden çok iş parçacığı yürütme kullanmaktır, uygulamanızın kullanıcı yanıt veren tutun ve aynı anda en güçlü yollarından biri işlemci arasında veya kullanıcı olayları sırasında bile kullanın. Bu bölümde, iş parçacığı temel kavramları açıklar, ancak yönetilen iş parçacığı kavramları ve yönetilen iş parçacığı kullanarak odaklanır.  
  
> [!NOTE]
>  İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], çok iş parçacıklı programlama ile Basitleştirilmiş büyük ölçüde <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> sınıfları [paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md), yeni eşzamanlı koleksiyon sınıflarını içinde <xref:System.Collections.Concurrent?displayProperty=nameWithType> ad alanı ve iş parçacıkları yerine görevleri kavramını temel alarak yeni bir programlama modeli. Daha fazla bilgi için [paralel programlama](../../../docs/standard/parallel-programming/index.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Yönetilen İş Parçacığı Oluşturma Temelleri](../../../docs/standard/threading/managed-threading-basics.md)  
 Yönetilen iş parçacığı genel bir bakış sağlar ve ne zaman birden çok iş parçacığı kullanılacağını açıklar.  
  
 [İş Parçacıkları ve İş Parçacığı Oluşturmayı Kullanma](../../../docs/standard/threading/using-threads-and-threading.md)  
 Oluşturma, Başlat, duraklatma, sürdürme ve iş parçacıklarını durdurma açıklanmaktadır.  
  
 [Yönetilen İş Parçacığı Oluşturma En İyi Yöntemleri](../../../docs/standard/threading/managed-threading-best-practices.md)  
 Düzeyleri açıklar, eşitleme sorunları nasıl Kilitlenmeler ve yarış durumları ve diğer iş parçacığı önlemek.  
  
 [İş Parçacığı Nesneleri ve Özellikleri](../../../docs/standard/threading/threading-objects-and-features.md)  
 İş parçacıkları etkinliklerini ve nesnelerin farklı iş parçacıklarında erişilen verileri eşitlemek için kullanabileceğiniz yönetilen sınıfları açıklar ve iş parçacığı havuzu iş parçacıkları genel bir bakış sağlar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Threading>  
 Yönetilen iş parçacıklarını eşitleme ve kullanma için sınıflar içerir.  
  
 <xref:System.Collections.Concurrent>  
 Birden çok iş parçacığı ile kullanmak için güvenli koleksiyon sınıfları içerir.  
  
 <xref:System.Threading.Tasks>  
 Oluşturma ve eş zamanlı işleme görevleri zamanlamak için sınıflar içerir.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Uygulama Etki Alanları](../../../docs/framework/app-domains/application-domains.md)  
 Uygulama etki alanları ve bunların kullanılması ortak dil altyapısı tarafından genel bir bakış sağlar.  
  
 [Zaman Uyumsuz Dosya G/Ç](../../../docs/standard/io/asynchronous-file-i-o.md)  
 Zaman uyumsuz I/O'nun performans avantajlarını ve temek işleyişini açıklar.  
  
 [Görev Tabanlı Zaman Uyumsuz Desen (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 . NET'te zaman uyumsuz programlama için önerilen düzene genel bir bakış sağlar.  
  
 [Zaman Uyumlu Metotları Zaman Uyumsuz Olarak Çağırma](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 Temsilciler'ın yerleşik özelliklerini kullanarak havuzu iş parçacıkları iş parçacığı üzerinde yöntemleri çağırmak nasıl açıklar.  
  
 [Paralel Programlama](../../../docs/standard/parallel-programming/index.md)  
 Paralel Programlama uygulamalarda birden çok iş parçacığı kullanımını basitleştiren kitaplıkları açıklar.  
  
 [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 Birden çok işlemci yararlanmak için paralel sorgular çalıştırmak için bir sistem açıklar.
