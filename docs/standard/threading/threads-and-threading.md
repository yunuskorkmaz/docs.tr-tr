---
title: İş parçacıkları ve iş parçacığı oluşturma
ms.date: 11/08/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- multiple threads
- threading [.NET]
- threading [.NET], multiple threads
ms.assetid: 5baac3aa-e603-4fa6-9f89-0f2c1084e6b1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 095bd92921c9cd54d3a7d97ed07b35526b85c57f
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53147691"
---
# <a name="threads-and-threading"></a>İş parçacıkları ve iş parçacığı oluşturma

Çoklu iş parçacığı kullanımı, uygulamanızın yanıt verme hızını artırmak ve uygulamanız bir çok işlemcili veya çok çekirdekli sisteminde çalışıyorsa, verimliliği artırmak sağlar.

## <a name="processes-and-threads"></a>İşlemler ve iş parçacıkları

A *işlem* yürütülen bir programdır. Bir işletim sistemi süreçleri yürütülmekte olan uygulamaları ayırmak için kullanır. A *iş parçacığı* bir işletim sistemi için işlemci süresi ayırdığı temel birimidir. Her iş parçacığı bir [zamanlama önceliği](scheduling-threads.md) ve yapıları sistem kullanır iş parçacığı yürütme duraklatıldığında iş parçacığı bağlamını kaydetmek için bir dizi korur. İş parçacığı bağlamını iş parçacığı yürütme iş parçacığının dizi CPU kaydeder ve yığını da dahil olmak üzere, sorunsuz bir şekilde devam etmek için gereken tüm bilgileri içerir. Birden çok iş parçacığı bir işlem bağlamında çalıştırabilirsiniz. Tüm iş parçacıklarının bir işlemin sanal adres alanı paylaşın. Bir iş parçacığı başka bir iş parçacığı tarafından şu anda yürütülmekte olan bölümleri dahil olmak üzere program kodu herhangi bir bölümünü yürütebilir.

> [!NOTE]
> .NET Framework kullanarak bir işlem içinde uygulamaları yalıtmak için bir yol sağlar *uygulama etki alanları*. (Uygulama etki alanları, .NET Core üzerinde kullanılamaz.) Daha fazla bilgi için [uygulama etki alanları ve iş parçacıkları](../../framework/app-domains/application-domains.md#application-domains-and-threads) bölümünü [uygulama etki alanları](../../framework/app-domains/application-domains.md) makalesi.

Varsayılan olarak, genellikle olarak adlandırılan tek bir iş parçacığı ile bir .NET programı başlatıldığında *birincil* iş parçacığı. Ancak, bu kod paralel veya birincil iş parçacığının aynı anda yürütmek için ek iş parçacıkları oluşturabilirsiniz. Bu iş parçacıkları genellikle adlı *çalışan* iş parçacıkları.

## <a name="when-to-use-multiple-threads"></a>Birden çok iş parçacığı kullanma zamanı

Uygulamanızın yanıt hızını artırmak ve uygulamanın aktarım hızını artırmak için çok işlemcili veya çok çekirdekli bir sistem yararlanmak için birden çok iş parçacığı kullanın.

Birincil iş parçacığı için kullanıcı arabirimi öğeleri sorumludur ve kullanıcı eylemlerine yanıt veren bir masaüstü uygulaması göz önünde bulundurun. Çalışan iş parçacıkları, aksi takdirde, birincil iş parçacığı kaplar ve kullanıcı arabirimi yanıt vermemesine uzun süren işlemleri gerçekleştirmek için kullanın. Ağ veya cihaz iletişimi için adanmış bir iş parçacığı, daha hızlı yanıt için gelen iletileri veya olayları için de kullanabilirsiniz.

Programınızı yapılabilir işlemleri paralel olarak gerçekleştirir, bu işlemleri ayrı iş parçacıkları ve çok işlemcili veya çok çekirdekli bir sistemde program çalıştırarak toplam yürütme zamanının azaltılabilir. Çoklu iş parçacığı kullanımı olabilir bu tür bir sistemde kullanın artan yanıt hızını yanı sıra aktarım hızını artırın.

## <a name="how-to-use-multithreading-in-net"></a>Nasıl kullanılacağını. NET'te çoklu iş parçacığı kullanımı

.NET Framework 4 ile başlayarak, çoklu iş parçacığı kullanmak için önerilen yöntem kullanmaktır [görev paralel kitaplığı (TPL)](../parallel-programming/task-parallel-library-tpl.md) ve [paralel LINQ (PLINQ)](../parallel-programming/parallel-linq-plinq.md). Daha fazla bilgi için [paralel programlama](../parallel-programming/index.md).

TPL hem de PLINQ Bel <xref:System.Threading.ThreadPool> iş parçacıkları. <xref:System.Threading.ThreadPool?displayProperty=nameWithType> Sınıfı çalışan iş parçacığı havuzu ile bir .NET uygulamasını sağlar. İş parçacığı havuzu iş parçacıkları de kullanabilirsiniz. Daha fazla bilgi için [yönetilen iş parçacığı havuzu](the-managed-thread-pool.md).

En son olarak, kullanabileceğiniz <xref:System.Threading.Thread?displayProperty=nameWithType> yönetilen iş parçacığı temsil eden sınıf. Daha fazla bilgi için [kullanarak iş parçacıkları ve iş parçacığı](using-threads-and-threading.md).

Birden çok iş parçacığı, paylaşılan bir kaynağa erişmesi gerekebilir. Kaynak bozulmamış bir durumda tutmak ve yarış durumları önlemek için iş parçacığı erişimi eşitlemeniz gerekir. Birden çok iş parçacığı etkileşimi koordine etmek isteyebilirsiniz. .NET, bir dizi paylaşılan bir kaynağa erişimi eşitleme veya iş parçacığı etkileşim koordine etmek için kullanabileceğiniz türleri sağlar. Daha fazla bilgi için [eşitleme temellerine genel bakış](overview-of-synchronization-primitives.md).

İş parçacıklarında özel durumlar işleyin. İşlenmeyen özel durumları iş parçacıkları genellikle işlemi sonlandırın. Daha fazla bilgi için [yönetilen iş parçacıklarında özel durumlar](exceptions-in-managed-threads.md).

## <a name="see-also"></a>Ayrıca bkz.

- [İş parçacığı nesneleri ve özellikleri](threading-objects-and-features.md)
- [Yönetilen iş parçacığı oluşturma en iyi yöntemleri](managed-threading-best-practices.md)
- [Paralel işleme, eşzamanlılık ve. NET'te zaman uyumsuz programlama](../parallel-processing-and-concurrency.md)
- [İşlemler ve iş parçacıkları hakkında](/windows/desktop/procthread/about-processes-and-threads)