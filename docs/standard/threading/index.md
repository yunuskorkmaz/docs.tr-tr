---
title: Yönetilen İş Parçacığı Oluşturma
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 7b46a7d9-c6f1-46d1-a947-ae97471bba87
ms.openlocfilehash: e4c19b664e8fc040fdc4a284b30f6104d676088d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279160"
---
# <a name="managed-threading"></a>Yönetilen İş Parçacığı Oluşturma
Tek bir işlemciye veya birkaç kullanıcıya sahip bilgisayarlar için geliştirme olsanız da, uygulama şu anda başka bir iş yapıyor olsa bile, uygulamanızın kullanıcıyla en iyi yanıt verme etkileşimini sağlamasını istersiniz. Birden çok iş parçacığının kullanılması, uygulamanızı kullanıcıya yanıt vermenin en güçlü yöntemlerinden biridir ve aynı zamanda Kullanıcı olayları sırasında veya hatta içinde işlemciyi kullanır. Bu bölümde iş parçacığı temel kavramları tanıtılırken, yönetilen iş parçacığı kavramlarıyla ve yönetilen iş parçacığı kullanımıyla odaklanır.  
  
> [!NOTE]
> .NET Framework 4 ' ten itibaren, çok iş parçacıklı programlama, <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> sınıfları, [paralel LINQ (PLINQ)](../parallel-programming/introduction-to-plinq.md), ad alanındaki yeni eşzamanlı koleksiyon sınıfları <xref:System.Collections.Concurrent?displayProperty=nameWithType> ve iş parçacıkları yerine görev kavramını temel alan yeni bir programlama modeli ile büyük ölçüde basitleştirilmiştir. Daha fazla bilgi için bkz. [paralel programlama](../parallel-programming/index.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Yönetilen İş Parçacığı Oluşturma Temelleri](managed-threading-basics.md)  
 Yönetilen iş parçacığına genel bir bakış sağlar ve birden çok iş parçacığının ne zaman kullanılacağını açıklar.  
  
 [Iş parçacıkları ve Iş parçacığı kullanma](using-threads-and-threading.md)  
 İş parçacıklarını oluşturmayı, başlatmayı, duraklatmayı, sürdürmeyi ve iptal etmeyi açıklar.  
  
 [Yönetilen İş Parçacığı Oluşturma En İyi Yöntemleri](managed-threading-best-practices.md)  
 Eşitleme düzeylerini, kilitlenmeleri ve yarış durumlarını ve diğer iş parçacığı sorunlarını açıklar.  
  
 [İş parçacığı nesneleri ve özellikleri](threading-objects-and-features.md)  
 İş parçacıklarının etkinliklerini ve farklı iş parçacıklarında erişilen nesnelerin verilerini eşleştirmek için kullanabileceğiniz yönetilen sınıfları açıklar ve iş parçacığı havuzu iş parçacıkları için bir genel bakış sağlar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Threading>  
 Yönetilen iş parçacıklarını kullanma ve eşitleme için sınıflar içerir.  
  
 <xref:System.Collections.Concurrent>  
 Birden çok iş parçacığı ile kullanım için güvenli olan koleksiyon sınıflarını içerir.  
  
 <xref:System.Threading.Tasks>  
 Eşzamanlı işleme görevlerinin oluşturulması ve zamanlanması için sınıflar içerir.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Uygulama Etki Alanları](../../framework/app-domains/application-domains.md)  
 Uygulama etki alanlarına ve bunların ortak dil altyapısı tarafından kullanımına ilişkin bir genel bakış sağlar.  
  
 [Zaman uyumsuz dosya g/ç](../io/asynchronous-file-i-o.md)  
 Zaman uyumsuz I/O'nun performans avantajlarını ve temek işleyişini açıklar.  
  
 [Görev Tabanlı Zaman Uyumsuz Desen (TAP)](../asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 .NET 'te zaman uyumsuz programlama için önerilen modele genel bakış sağlar.  
  
 [Zaman Uyumlu Metotları Zaman Uyumsuz Olarak Çağırma](../asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 Temsilcilerin yerleşik özellikleri kullanılarak iş parçacığı havuzu iş parçacıklarında yöntemlerin nasıl çağrılacağını açıklar.  
  
 [Paralel programlama](../parallel-programming/index.md)  
 Uygulamalarda birden çok iş parçacığının kullanımını kolaylaştıran paralel programlama kitaplıklarını açıklar.  
  
 [Paralel LINQ (PLINQ)](../parallel-programming/introduction-to-plinq.md)  
 Birden çok işlemcinin avantajlarından yararlanmak için sorguları paralel olarak çalıştırmaya yönelik bir sistem açıklar.
