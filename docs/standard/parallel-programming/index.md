---
title: .NET içinde Paralel Programlama
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- parallel programming
ms.assetid: 4d83c690-ad2d-489e-a2e0-b85b898a672d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ea32ee89e20a1716b988a219dce221edec7c8917
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="parallel-programming-in-net"></a>.NET içinde Paralel Programlama

Birçok kişisel bilgisayarlar ve iş istasyonlarında aynı anda yürütülebilecek birden çok iş parçacığı etkinleştirmek birkaç CPU çekirdeği vardır. Yakın gelecekte bilgisayarların önemli ölçüde daha fazla çekirdeğe sahip olacağı tahmin edilmektedir. Bugünün ve yarının donanımlarından yararlanmak için kodunuzu işi birden fazla işlemci arasında dağıtacak şekilde paralel hale getirebilirsiniz. Geçmişte, paralel hale getirme için iş parçacıklarının ve kilitlerin düşük düzeyde kullanımı gerekiyordu. Visual Studio 2010 ve .NET Framework 4 Paralel Programlama Desteği yeni bir çalışma zamanı, yeni sınıf kitaplığı türleri ve yeni tanılama araçları sağlayarak geliştirin. Bu özellikler, doğrudan iş parçacıkları veya iş parçacığı havuzuyla çalışmak zorunda kalmadan doğal bir ifadede etkili, ayrıntılı ve ölçeklenebilir paralel kod yazmanız için paralel geliştirmeyi basitleştirir. Aşağıdaki çizimde, .NET Framework 4'te paralel programlama mimarisi üst düzey bir genel bakış sağlar.
  
 ![.NET paralel programlama mimarisi](./media/tpl-architecture.png "TPL_Architecture")  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Teknoloji|Açıklama|  
|----------------|-----------------|  
|[Görev Paralel Kitaplığı (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)|İçin belgeler sağlar <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> paralel sürümlerini içerir sınıfı `For` ve `ForEach` döngüler, için ve ayrıca <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> zaman uyumsuz işlemleri ifade etmek için tercih edilen yöntem temsil eden sınıf.|  
|[Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)|LINQ to Objects'in birçok senaryoda performansı önemli ölçüde artıran paralel bir uygulaması.|  
|[Paralel Programlama için Veri Yapıları](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)|İş parçacığı güvenli koleksiyon sınıfları, hafif eşitleme türleri ve yavaş başlatma türlerine yönelik belgeler için bağlantılar sağlar.|  
|[Paralel Tanılama Araçları](../../../docs/standard/parallel-programming/parallel-diagnostic-tools.md)|Görevler ve Paralel Yığınlar için Visual Studio hata ayıklayıcısı windows belgelerine ait bağlantılar sağlanmıştır ve [eşzamanlılık görselleştiricisi](/visualstudio/profiling/concurrency-visualizer), oluşan bir dizi görünümlerinde ve [!INCLUDE[vsprvsts](../../../includes/vsprvsts-md.md)] hata ayıklama ve ayarlamak için kullanabileceğiniz Profil Oluşturucu paralel kod performansını.|  
|[PLINQ ve TPL için Özel Bölümleyiciler](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)|Bölümleyicilerin nasıl çalıştığını ve varsayılan bölümleyicilerin nasıl yapılandırılacağını veya nasıl yeni bir bölümleyicinin oluşturulacağını açıklar.|  
|[Görev zamanlayıcılar](http://msdn.microsoft.com/library/638f8ea5-21db-47a2-a934-86e1e961bf65)|Planlayıcıların nasıl çalıştığını ve varsayılan planlayıcıların nasıl yapılandırılması gerektiğini açıklar.|  
|[PLINQ ve TPL'deki Lambda İfadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)|C# ve Visual Basic'teki lambda ifadelerine kısa bir genel bakış sunar ve PLINQ ve Görev Paralel Kitaplığı'nda nasıl kullanıldıklarını gösterir.|  
|[Daha Fazla Bilgi İçin](../../../docs/standard/parallel-programming/for-further-reading-parallel-programming.md)|. NET'te paralel programlama için ek bilgi ve örnek kaynaklara bağlantılar sağlar.|  

## <a name="see-also"></a>Ayrıca bkz.  
 [Zaman uyumsuz genel bakış](../async.md)  
 [Yönetilen iş parçacığı oluşturma](../threading/index.md)  
