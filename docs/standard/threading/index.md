---
title: "Yönetilen İş Parçacığı Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 7b46a7d9-c6f1-46d1-a947-ae97471bba87
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 61cd2317b5690573532af2a25c0b84b1fe136fd9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="managed-threading"></a>Yönetilen İş Parçacığı Oluşturma
Bir işlemci veya birkaç sahip bilgisayarlar için geliştirdiğiniz olup olmadığını uygulama şu anda diğer iş yaptığını olsa bile kullanıcının en esnek etkileşim sağlamak için uygulamanızın istiyor. Birden çok iş parçacığı yürütme kullanmaktır, uygulamanızın yanıt vereceğini kullanıcıya tutun ve aynı anda yapmak için en güçlü şekilde arasındaki veya kullanıcı olayları sırasında bile işlemcinin kullanın. Bu bölüm iş parçacığı oluşturma temel kavramları tanıtır olsa da, yönetilen kavramları iş parçacığı oluşturma ve yönetilen iş parçacığı kullanarak odaklanır.  
  
> [!NOTE]
>  İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], birden çok iş parçacıklı programlama ile Basitleştirilmiş büyük ölçüde <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> sınıfları [paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md), yeni eşzamanlı koleksiyon sınıfları <xref:System.Collections.Concurrent?displayProperty=nameWithType> ad alanı ve iş parçacıkları yerine görevleri kavramı dayalı yeni bir programlama modeli. Daha fazla bilgi için bkz: [paralel programlama](../../../docs/standard/parallel-programming/index.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Yönetilen iş parçacığı oluşturma temelleri](../../../docs/standard/threading/managed-threading-basics.md)  
 Yönetilen iş parçacığı oluşturma genel bir bakış sağlar ve ne zaman birden çok iş parçacığı kullanılacağı açıklanır.  
  
 [İş parçacığı kullanma ve iş parçacığı oluşturma](../../../docs/standard/threading/using-threads-and-threading.md)  
 Oluştur, Başlat, duraklatma, sürdürme ve iş parçacıklarını durdurma açıklanmaktadır.  
  
 [Yönetilen iş parçacığı oluşturma en iyi uygulamalar](../../../docs/standard/threading/managed-threading-best-practices.md)  
 Eşitleme, Kilitlenmeler ve yarış durumları, tek işlemcili önlemenin ve çok işlemcili bilgisayarlar ve diğer iş parçacığı oluşturma sorunları düzeylerini açıklanır.  
  
 [İş parçacığı nesneleri ve özellikleri](../../../docs/standard/threading/threading-objects-and-features.md)  
 İş parçacığı etkinliklerini ve farklı iş parçacıklarında erişilen nesneler verileri eşitlemek için kullanabileceğiniz yönetilen sınıflar açıklar ve iş parçacığı havuzu iş parçacıkları genel bir bakış sağlar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Threading>  
 Kullanarak ve yönetilen iş parçacıklarını eşitleme için sınıflar içerir.  
  
 <xref:System.Collections.Concurrent>  
 Birden çok iş parçacığı ile kullanmak için güvenli koleksiyon sınıfları içerir.  
  
 <xref:System.Threading.Tasks>  
 Oluşturma ve eş zamanlı işleme görevlerini zamanlama için sınıflar içerir.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Uygulama etki alanları](../../../docs/framework/app-domains/application-domains.md)  
 Uygulama etki alanları ve bunların kullanılması ortak dil altyapısı tarafından genel bir bakış sağlar.  
  
 [Zaman uyumsuz dosya g/ç](../../../docs/standard/io/asynchronous-file-i-o.md)  
 Zaman uyumsuz I/O'nun performans avantajlarını ve temek işleyişini açıklar.  
  
 [Olay tabanlı zaman uyumsuz desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 Zaman uyumsuz programlama genel bir bakış sağlar.  
  
 [Zaman uyumlu yöntemleri zaman uyumsuz olarak çağırma](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 İş parçacığı üzerinde temsilciler yerleşik özelliklerini kullanarak havuzu iş parçacıkları yöntemlerini çağırmaya açıklanmaktadır.  
  
 [Paralel Programlama](../../../docs/standard/parallel-programming/index.md)  
 Paralel uygulamalar içindeki birden çok iş parçacığı kullanımını kolaylaştırmak kitaplıkları programlama açıklar.  
  
 [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 Birden çok işlemci yararlanmak için paralel sorgular çalıştırmak için bir sistem açıklar.
