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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73127510"
---
# <a name="threads-and-threading"></a>İş parçacıkları ve iş parçacığı

Çoklu iş parçacığı, uygulamanızın yanıt verme yeteneğini artırmanıza ve uygulamanız çok işlemcili veya çok çekirdekli bir sistemde çalışıyorsa, üretim işlemini artırmanıza olanak tanır.

## <a name="processes-and-threads"></a>İşlemler ve iş parçacıkları

*İşlem* yürütme programıdır. İşletim sistemi, yürütülmekte olan uygulamaları ayırmak için işlemleri kullanır. *İş parçacığı,* işletim sisteminin işlemci süresini ayırdığı temel birimdir. Her iş parçacığının bir [zamanlama önceliği](scheduling-threads.md) vardır ve iş parçacığının yürütülmesi duraklatıldığında iş parçacığı bağlamını kaydetmek için sistemin kullandığı bir yapı kümesi tutar. İş parçacığı bağlamı, iş parçacığının CPU kayıtları ve yığını kümesi de dahil olmak üzere yürütmeyi sorunsuz bir şekilde devam ettirmek için gereken tüm bilgileri içerir. Bir işlem bağlamında birden çok iş parçacığı çalıştırılabilir. Bir işlemin tüm iş parçacıkları sanal adres alanını paylaşır. İş parçacığı, şu anda başka bir iş parçacığı tarafından yürütülmekte olan parçalar da dahil olmak üzere program kodunun herhangi bir bölümünü yürütebilir.

> [!NOTE]
> .NET Framework, *uygulama etki alanlarının*kullanımıyla bir işlem içindeki uygulamaları yalıtmak için bir yol sağlar. (Uygulama etki alanları .NET Core'da kullanılamaz.) Daha fazla bilgi için, [Uygulama etki alanları](../../framework/app-domains/application-domains.md) makalesinin Uygulama etki alanları ve iş [parçacıkları](../../framework/app-domains/application-domains.md#application-domains-and-threads) bölümüne bakın.

Varsayılan olarak, bir .NET programı genellikle *birincil* iş parçacığı olarak adlandırılan tek bir iş parçacığı ile başlatılır. Ancak, birincil iş parçacığı ile paralel veya aynı anda kod yürütmek için ek iş parçacıkları oluşturabilirsiniz. Bu iş parçacıkları genellikle *alt* iş parçacığı olarak adlandırılır.

## <a name="when-to-use-multiple-threads"></a>Birden çok iş parçacığı ne zaman kullanılır?

Uygulamanızın yanıt verme yeteneğini artırmak ve uygulamanın masını artırmak için çok işlemcili veya çok çekirdekli bir sistemden yararlanmak için birden çok iş parçacığı kullanırsınız.

Birincil iş parçacığının kullanıcı arabirimi öğelerinden sorumlu olduğu ve kullanıcı eylemlerine yanıt veren bir masaüstü uygulaması düşünün. Aksi takdirde birincil iş parçacığı işgal edecek ve kullanıcı arabirimini yanıt vermeyen yapmak zaman alıcı işlemleri gerçekleştirmek için alt iş parçacığı kullanın. Ayrıca, gelen iletilere veya olaylara daha duyarlı olması için ağ veya aygıt iletişimi için özel bir iş parçacığı kullanabilirsiniz.

Programınız paralel olarak yapılabilecek işlemleri gerçekleştirirse, bu işlemleri ayrı iş parçacıklarında gerçekleştirerek ve programı çok işlemcili veya çok çekirdekli bir sistemde çalıştırarak toplam yürütme süresi azaltılabilir. Böyle bir sistemde, çoklu iş parçacığı kullanımı artan yanıt ile birlikte iş parçacığı artırabilir.

## <a name="how-to-use-multithreading-in-net"></a>.NET'te çoklu iş parçacığı nasıl kullanılır?

.NET Framework 4'ten başlayarak, çoklu iş parçacığı kullanmanın önerilen yolu [Görev Paralel Kitaplığı (TPL)](../parallel-programming/task-parallel-library-tpl.md) ve [Paralel LINQ (PLINQ)](../parallel-programming/parallel-linq-plinq.md)kullanmaktır. Daha fazla bilgi için [Paralel programlamaya](../parallel-programming/index.md)bakın.

Hem TPL hem de PLINQ iş parçacıklarına <xref:System.Threading.ThreadPool> güvenir. Sınıf, <xref:System.Threading.ThreadPool?displayProperty=nameWithType> bir .NET uygulaması ve bir işçi iş parçacığı havuzu sağlar. İş parçacığı havuzu iş parçacığı iş parçacığı da kullanabilirsiniz. Daha fazla bilgi için [yönetilen iş parçacığı havuzuna](the-managed-thread-pool.md)bakın.

Sonunda, yönetilen bir <xref:System.Threading.Thread?displayProperty=nameWithType> iş parçacığı temsil eden sınıfı kullanabilirsiniz. Daha fazla bilgi için [bkz.](using-threads-and-threading.md)

Paylaşılan bir kaynağa erişmek için birden çok iş parçacığı gerekebilir. Kaynağı bozulmamış bir durumda tutmak ve yarış koşullarından kaçınmak için iş parçacığı erişimini eşitlemeniz gerekir. Ayrıca, birden çok iş parçacığı etkileşimini koordine etmek isteyebilirsiniz. .NET, paylaşılan bir kaynağa erişimi eşitlemek veya iş parçacığı etkileşimini koordine etmek için kullanabileceğiniz bir dizi tür sağlar. Daha fazla bilgi için, [senkronizasyon ilkel Genel Bakış](overview-of-synchronization-primitives.md)bakın.

İş parçacıklarında özel durumları işleyebilir. İş parçacıklarındaki işlenmemiş özel durumlar genellikle işlemi sonlandırır. Daha fazla bilgi için [yönetilen iş parçacıklarındaki Özel Durumlar'a](exceptions-in-managed-threads.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [İş parçacığı nesneleri ve özellikleri](threading-objects-and-features.md)
- [Yönetilen iş parçacığı en iyi uygulamalar](managed-threading-best-practices.md)
- [.NET'te Paralel İşleme, Eşzamanlılık ve Async Programlama](../parallel-processing-and-concurrency.md)
- [Süreçler ve İş Parçacıkları Hakkında](/windows/desktop/procthread/about-processes-and-threads)
