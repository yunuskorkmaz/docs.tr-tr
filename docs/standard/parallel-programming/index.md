---
title: .NET içinde Paralel Programlama
description: .NET ' te paralel programlama hakkında bilgi edinin. .Net geliştirmeyi basitleştirmek için .NET çalışma zamanı, sınıf kitaplığı türleri ve tanılama araçları kullanın.
ms.date: 09/12/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- parallel programming
ms.assetid: 4d83c690-ad2d-489e-a2e0-b85b898a672d
ms.openlocfilehash: 02087cf58720388c64d8aba5424db0b54828219a
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2020
ms.locfileid: "84661971"
---
# <a name="parallel-programming-in-net"></a>.NET içinde Paralel Programlama

Birçok kişisel bilgisayar ve iş istasyonunda birden çok iş parçacığının aynı anda yürütülmesini sağlayan birden çok CPU çekirdeği vardır. Donanımdan yararlanmak için kodunuzu birden çok işlemciye dağıtmak üzere paralel hale getirmek yapabilirsiniz.

Geçmişte, paralel hale getirme için iş parçacıklarının ve kilitlerin düşük düzeyde kullanımı gerekiyordu. Visual Studio ve .NET Framework, bir çalışma zamanı, sınıf kitaplığı türleri ve tanılama araçları sağlayarak paralel programlama desteğini geliştirir. .NET Framework 4 ile tanıtılan bu özellikler paralel geliştirmeyi basitleştirir. Doğrudan iş parçacıklarıyla veya iş parçacığı havuzuyla çalışmak zorunda kalmadan doğal bir deyim içinde etkili, hassas ve ölçeklenebilir paralel kod yazabilirsiniz.

Aşağıdaki çizimde .NET Framework paralel programlama mimarisine üst düzey bir genel bakış sunulmaktadır:

![.NET paralel programlama mimarisi](./media/tpl-architecture.png)

## <a name="related-topics"></a>İlgili Konular

|Teknoloji|Description|
|----------------|-----------------|
|[Görev Paralel Kitaplığı (TPL)](task-parallel-library-tpl.md)|, <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> `For` Ve `ForEach` döngülerinin paralel sürümlerini ve ayrıca, <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> zaman uyumsuz işlemleri hızlı bir şekilde ifade etmek için tercih edilen yolu temsil eden sınıfı için belgeler sağlar.|
|[Paralel LINQ (PLINQ)](introduction-to-plinq.md)|LINQ to Objects'in birçok senaryoda performansı önemli ölçüde artıran paralel bir uygulaması.|
|[Paralel programlama için veri yapıları](data-structures-for-parallel-programming.md)|İş parçacığı güvenli koleksiyon sınıfları, hafif eşitleme türleri ve yavaş başlatma türlerine yönelik belgeler için bağlantılar sağlar.|
|[Paralel Tanılama Araçları](parallel-diagnostic-tools.md)|Görevler ve paralel yığınlar için Visual Studio hata ayıklayıcısı pencereleri ve [Eşzamanlılık görselleştiricisi](/visualstudio/profiling/concurrency-visualizer)için belgelere bağlantılar sağlar.|
|[PLıNQ ve TPL için Özel Bölümleyiciler](custom-partitioners-for-plinq-and-tpl.md)|Bölümleyicilerin nasıl çalıştığını ve varsayılan bölümleyicilerin nasıl yapılandırılacağını veya nasıl yeni bir bölümleyicinin oluşturulacağını açıklar.|
|[Görev zamanlayıcılar](xref:System.Threading.Tasks.TaskScheduler)|Planlayıcıların nasıl çalıştığını ve varsayılan planlayıcıların nasıl yapılandırılması gerektiğini açıklar.|
|[PLıNQ ve TPL 'deki lambda Ifadeleri](lambda-expressions-in-plinq-and-tpl.md)|C# ve Visual Basic'teki lambda ifadelerine kısa bir genel bakış sunar ve PLINQ ve Görev Paralel Kitaplığı'nda nasıl kullanıldıklarını gösterir.|
|[Daha Fazla Bilgi İçin](for-further-reading-parallel-programming.md)|.NET ' te paralel programlama için ek bilgi ve örnek kaynaklara bağlantılar sağlar.|

## <a name="see-also"></a>Ayrıca bkz.

- [Zaman uyumsuz genel bakış](../async.md)
- [Yönetilen Iş parçacığı](../threading/index.md)
