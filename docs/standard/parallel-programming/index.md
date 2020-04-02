---
title: .NET içinde Paralel Programlama
ms.date: 09/12/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- parallel programming
ms.assetid: 4d83c690-ad2d-489e-a2e0-b85b898a672d
ms.openlocfilehash: 75f5ded48acfb82b0327ead3880ee23e6ef4bc2f
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588159"
---
# <a name="parallel-programming-in-net"></a>.NET içinde Paralel Programlama

Birçok kişisel bilgisayar ve iş istasyonu, birden çok iş parçacığının aynı anda yürütülmesini sağlayan birden çok CPU çekirdeğine sahiptir. Donanımdan yararlanmak için, çalışmanızı birden çok işlemciye dağıtmak için kodunuzu paralelleştirebilirsiniz.

Geçmişte, paralel hale getirme için iş parçacıklarının ve kilitlerin düşük düzeyde kullanımı gerekiyordu. Visual Studio ve .NET Framework, çalışma zamanı, sınıf kitaplığı türleri ve tanılama araçları sağlayarak paralel programlama desteğini artırır. .NET Framework 4 ile tanıtılan bu özellikler paralel geliştirmeyi basitleştirir. Doğrudan iş parçacıkları veya iş parçacığı havuzu ile çalışmak zorunda kalmadan doğal bir deyim içinde verimli, ince taneli ve ölçeklenebilir paralel kod yazabilirsiniz.

Aşağıdaki örnekte,.NET Framework'deki paralel programlama mimarisine üst düzey bir genel bakış vereme:

![.NET Paralel Programlama Mimarisi](./media/tpl-architecture.png)

## <a name="related-topics"></a>İlgili Konular

|Teknoloji|Açıklama|
|----------------|-----------------|
|[Görev Paralel Kitaplığı (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)|<xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> Sınıf için, paralel sürümleri `For` ve `ForEach` döngüleri içeren belgeler sağlar ve ayrıca asynchronous işlemleri ifade etmek için tercih edilen yolu temsil eden <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> sınıf için.|
|[Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)|LINQ to Objects'in birçok senaryoda performansı önemli ölçüde artıran paralel bir uygulaması.|
|[Paralel Programlama için Veri Yapıları](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)|İş parçacığı güvenli koleksiyon sınıfları, hafif eşitleme türleri ve yavaş başlatma türlerine yönelik belgeler için bağlantılar sağlar.|
|[Paralel Tanılama Araçları](../../../docs/standard/parallel-programming/parallel-diagnostic-tools.md)|Görevler ve paralel yığınlar için Visual Studio hata ayıklama pencereleri ve [Eşzamanlılık Görselleştiricisi](/visualstudio/profiling/concurrency-visualizer)için belgelere bağlantılar sağlar.|
|[PLINQ ve TPL için Özel Bölümleyiciler](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)|Bölümleyicilerin nasıl çalıştığını ve varsayılan bölümleyicilerin nasıl yapılandırılacağını veya nasıl yeni bir bölümleyicinin oluşturulacağını açıklar.|
|[Görev Zamanlayıcıları](xref:System.Threading.Tasks.TaskScheduler)|Planlayıcıların nasıl çalıştığını ve varsayılan planlayıcıların nasıl yapılandırılması gerektiğini açıklar.|
|[PLINQ ve TPL'deki Lambda İfadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)|C# ve Visual Basic'teki lambda ifadelerine kısa bir genel bakış sunar ve PLINQ ve Görev Paralel Kitaplığı'nda nasıl kullanıldıklarını gösterir.|
|[Daha Fazla Bilgi İçin](../../../docs/standard/parallel-programming/for-further-reading-parallel-programming.md)|.NET'te paralel programlama için ek bilgi ve örnek kaynaklara bağlantılar sağlar.|

## <a name="see-also"></a>Ayrıca bkz.

- [Async Genel Bakış](../async.md)
- [Yönetilen İş Parçacığı](../threading/index.md)
