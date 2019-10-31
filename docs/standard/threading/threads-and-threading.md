---
title: İş parçacıkları ve iş parçacığı
ms.date: 11/08/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- multiple threads
- threading [.NET]
- threading [.NET], multiple threads
ms.assetid: 5baac3aa-e603-4fa6-9f89-0f2c1084e6b1
ms.openlocfilehash: ad36789579b95e0129e402765194b9f5e45a4cc1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127510"
---
# <a name="threads-and-threading"></a>İş parçacıkları ve iş parçacığı

Çoklu iş parçacığı uygulamanızın yanıt hızını artırmanıza olanak tanır ve uygulamanız çok işlemcili veya çok çekirdekli bir sistemde çalışıyorsa, verimini artırın.

## <a name="processes-and-threads"></a>Süreçler ve iş parçacıkları

*İşlem* yürütülen bir programdır. Bir işletim sistemi, yürütülmekte olan uygulamaları ayırmak için süreçler kullanır. *İş parçacığı* , bir işletim sisteminin işlemci süresini ayırdığı temel birimdir. Her iş parçacığı bir [zamanlama önceliğine](scheduling-threads.md) sahiptir ve sistemin iş parçacığı yürütme duraklatıldığında iş parçacığı bağlamını kaydetmek için kullandığı bir yapı kümesi tutar. İş parçacığı bağlamı, iş parçacığının CPU kayıtları ve yığın kümesi de dahil olmak üzere yürütmeyi sorunsuz bir şekilde sürdürmeniz için gereken tüm bilgileri içerir. Bir işlem bağlamında birden çok iş parçacığı çalıştırılabilir. Bir işlemin tüm iş parçacıkları sanal adres alanını paylaşır. Bir iş parçacığı, şu anda başka bir iş parçacığı tarafından yürütülen parçalar dahil olmak üzere program kodunun herhangi bir bölümünü yürütebilir.

> [!NOTE]
> .NET Framework, *uygulama etki alanlarının*kullanımıyla bir işlem içindeki uygulamaları yalıtmak için bir yol sağlar. (Uygulama etki alanları .NET Core 'da kullanılamaz.) Daha fazla bilgi için [uygulama etki alanları](../../framework/app-domains/application-domains.md) makalesinin [uygulama etki alanları ve iş parçacıkları](../../framework/app-domains/application-domains.md#application-domains-and-threads) bölümüne bakın.

Varsayılan olarak, bir .NET programı, genellikle *birincil* iş parçacığı olarak adlandırılan tek bir iş parçacığıyla başlatılır. Ancak, birincil iş parçacığıyla kodu paralel veya eşzamanlı olarak yürütmek için ek iş parçacıkları oluşturabilir. Bu iş parçacıkları genellikle *çalışan* iş parçacıkları olarak adlandırılır.

## <a name="when-to-use-multiple-threads"></a>Birden çok iş parçacığı ne zaman kullanılır

Uygulamanın yanıt hızını artırmak ve uygulamanın aktarım hızını artırmak için çok işlemcili veya çok çekirdekli bir sistemden yararlanmak üzere birden fazla iş parçacığı kullanırsınız.

Birincil iş parçacığının kullanıcı arabirimi öğelerinden sorumlu olduğu ve kullanıcı eylemlerine yanıt verdiği bir masaüstü uygulaması düşünün. Aksi takdirde, birincil iş parçacığını kaplayacağından ve Kullanıcı arabiriminin yanıt vermemesine neden olacak zaman alan işlemleri gerçekleştirmek için çalışan iş parçacıklarını kullanın. Ayrıca, gelen iletilere veya olaylara daha fazla yanıt vermek için ağ veya cihaz iletişimi için adanmış bir iş parçacığı kullanabilirsiniz.

Programınız paralel olarak yapılabilen işlemler gerçekleştiriyorsa, toplam yürütme süresi ayrı iş parçacıklarında bu işlemler gerçekleştirerek ve programı çok işlemcili veya çok çekirdekli bir sistemde çalıştırarak bu işlemleri azalyabilirler. Böyle bir sistemde çoklu iş parçacığı kullanımı, artan yanıt hızını artırır.

## <a name="how-to-use-multithreading-in-net"></a>.NET ' te çoklu iş parçacığı kullanımı

.NET Framework 4 ' ü kullanmaya başlayarak, çoklu iş parçacığı kullanmanın önerilen yolu, [görev paralel kitaplığı (TPL)](../parallel-programming/task-parallel-library-tpl.md) ve [paralel LINQ (PLINQ)](../parallel-programming/parallel-linq-plinq.md)kullanmaktır. Daha fazla bilgi için bkz. [paralel programlama](../parallel-programming/index.md).

TPL ve PLıNQ her ikisi de <xref:System.Threading.ThreadPool> iş parçacıklarını kullanır. <xref:System.Threading.ThreadPool?displayProperty=nameWithType> sınıfı, bir çalışan iş parçacığı havuzu içeren bir .NET uygulaması sağlar. İş parçacığı havuzu iş parçacıklarını da kullanabilirsiniz. Daha fazla bilgi için bkz. [yönetilen iş parçacığı havuzu](the-managed-thread-pool.md).

Son olarak, yönetilen bir iş parçacığını temsil eden <xref:System.Threading.Thread?displayProperty=nameWithType> sınıfını kullanabilirsiniz. Daha fazla bilgi için bkz. [iş parçacıklarını ve iş parçacığını kullanma](using-threads-and-threading.md).

Birden çok iş parçacığının paylaşılan bir kaynağa erişmesi gerekebilir. Kaynağı bozulmamış durumda tutmak ve yarış koşullarından kaçınmak için iş parçacığı erişimini eşitlemeniz gerekir. Ayrıca, birden çok iş parçacığının etkileşimini koordine etmek isteyebilirsiniz. .NET, paylaşılan bir kaynağa erişimi veya koordinat iş parçacığı etkileşimini eşleştirmek için kullanabileceğiniz bir dizi tür sağlar. Daha fazla bilgi için bkz. [eşitleme temel bilgilerine genel bakış](overview-of-synchronization-primitives.md).

İş parçacıklarında özel durumları işleyin. İş parçacıklarında işlenmeyen özel durumlar genellikle işlemi sonlandırır. Daha fazla bilgi için bkz. [yönetilen iş parçacıklarında özel durumlar](exceptions-in-managed-threads.md).

## <a name="see-also"></a>Ayrıca bkz.

- [İş parçacığı nesneleri ve özellikleri](threading-objects-and-features.md)
- [Yönetilen iş parçacığı en iyi uygulamaları](managed-threading-best-practices.md)
- [.NET ' te paralel Işleme, eşzamanlılık ve zaman uyumsuz programlama](../parallel-processing-and-concurrency.md)
- [Süreçler ve Iş parçacıkları hakkında](/windows/desktop/procthread/about-processes-and-threads)
