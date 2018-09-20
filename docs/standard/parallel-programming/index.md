---
title: .NET içinde Paralel Programlama
ms.date: 09/12/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- parallel programming
ms.assetid: 4d83c690-ad2d-489e-a2e0-b85b898a672d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3d1cd0b797373da4cab59484e3e6302927d821ed
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46320626"
---
# <a name="parallel-programming-in-net"></a>.NET içinde Paralel Programlama

Birçok Kişisel bilgisayarları ve iş istasyonları, birden çok iş parçacığının aynı anda yürütülmesini sağlayan birden çok CPU çekirdeği var. Donanım yararlanmak için kodunuzu iş birden çok işlemci arasında dağıtacak şekilde paralel hale getirebilirsiniz.

Geçmişte, paralel hale getirme için iş parçacıklarının ve kilitlerin düşük düzeyde kullanımı gerekiyordu. Visual Studio ve .NET Framework, bir çalışma zamanı, sınıf kitaplığı türleri ve tanılama araçları sağlayarak paralel programlama için destek geliştirin. .NET Framework 4 ile tanıtılan, bu özellikler için paralel geliştirmeyi basitleştirir. Doğrudan iş parçacıkları veya iş parçacığı havuzuyla çalışmak zorunda kalmadan doğal bir ifadede etkili, ayrıntılı ve ölçeklenebilir paralel kod yazabilirsiniz.

Aşağıdaki çizim, .NET Framework'te paralel programlama mimarisi üst düzey bir genel bakış sağlar:

![.NET paralel programlama mimarisi](./media/tpl-architecture.png)

## <a name="related-topics"></a>İlgili Konular

|Teknoloji|Açıklama|
|----------------|-----------------|
|[Görev Paralel Kitaplığı (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)|İçin belgeler sağlar <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> paralel sürümlerini içeren sınıf `For` ve `ForEach` döngüleri, için ve ayrıca <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> zaman uyumsuz işlemleri ifade etmenin tercih edilen yolu temsil eden sınıf.|
|[Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)|LINQ to Objects'in birçok senaryoda performansı önemli ölçüde artıran paralel bir uygulaması.|
|[Paralel Programlama için Veri Yapıları](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)|İş parçacığı güvenli koleksiyon sınıfları, hafif eşitleme türleri ve yavaş başlatma türlerine yönelik belgeler için bağlantılar sağlar.|
|[Paralel Tanılama Araçları](../../../docs/standard/parallel-programming/parallel-diagnostic-tools.md)|Ve görevler ve Paralel Yığınlar için Visual Studio hata ayıklayıcı windows belgelerine bağlantılar sağlar [eşzamanlılık görselleştiricisi](/visualstudio/profiling/concurrency-visualizer).|
|[PLINQ ve TPL için Özel Bölümleyiciler](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)|Bölümleyicilerin nasıl çalıştığını ve varsayılan bölümleyicilerin nasıl yapılandırılacağını veya nasıl yeni bir bölümleyicinin oluşturulacağını açıklar.|
|[Görev zamanlayıcılar](https://msdn.microsoft.com/library/638f8ea5-21db-47a2-a934-86e1e961bf65)|Planlayıcıların nasıl çalıştığını ve varsayılan planlayıcıların nasıl yapılandırılması gerektiğini açıklar.|
|[PLINQ ve TPL'deki Lambda İfadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)|C# ve Visual Basic'teki lambda ifadelerine kısa bir genel bakış sunar ve PLINQ ve Görev Paralel Kitaplığı'nda nasıl kullanıldıklarını gösterir.|
|[Daha Fazla Bilgi İçin](../../../docs/standard/parallel-programming/for-further-reading-parallel-programming.md)|.NET içinde paralel programlama için ek bilgi ve örnek kaynaklar için bağlantılar sağlar.|

## <a name="see-also"></a>Ayrıca bkz.

- [Zaman uyumsuz genel bakış](../async.md)
- [Yönetilen iş parçacığı oluşturma](../threading/index.md)
