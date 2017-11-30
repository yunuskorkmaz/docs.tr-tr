---
title: . NET'te paralel programlama
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: parallel programming
ms.assetid: 4d83c690-ad2d-489e-a2e0-b85b898a672d
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e061508b6b74e81b79ab7d53b0277afd38072635
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="parallel-programming-in-net"></a>. NET'te paralel programlama
Birçok kişisel bilgisayar ve iş istasyonunun, birden çok iş parçacığının aynı anda yürütülmesini sağlayan iki veya dört çekirdeği (yani CPU'su) vardır. Yakın gelecekte bilgisayarların önemli ölçüde daha fazla çekirdeğe sahip olacağı tahmin edilmektedir. Bugünün ve yarının donanımlarından yararlanmak için kodunuzu işi birden fazla işlemci arasında dağıtacak şekilde paralel hale getirebilirsiniz. Geçmişte, paralel hale getirme için iş parçacıklarının ve kilitlerin düşük düzeyde kullanımı gerekiyordu. [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)]ve [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] yeni bir çalışma zamanı, yeni sınıf kitaplığı türleri ve yeni tanılama araçları sağlayarak Paralel Programlama Desteği geliştirir. Bu özellikler, doğrudan iş parçacıkları veya iş parçacığı havuzuyla çalışmak zorunda kalmadan doğal bir ifadede etkili, ayrıntılı ve ölçeklenebilir paralel kod yazmanız için paralel geliştirmeyi basitleştirir. Aşağıdaki çizimde paralel programlama mimarisinde üst düzey bir genel bakış sağlayan [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].  
  
 ![.NET paralel programlama mimarisi](../../../docs/standard/parallel-programming/media/tpl-architecture.png "TPL_Architecture")  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Teknoloji|Açıklama|  
|----------------|-----------------|  
|[Görev paralel kitaplığı (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)|İçin belgeler sağlar <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> paralel sürümlerini içerir sınıfı `For` ve `ForEach` döngüler, için ve ayrıca <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> zaman uyumsuz işlemleri ifade etmek için tercih edilen yöntem temsil eden sınıf.|  
|[Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)|LINQ to Objects'in birçok senaryoda performansı önemli ölçüde artıran paralel bir uygulaması.|  
|[Paralel programlama için veri yapıları](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)|İş parçacığı güvenli koleksiyon sınıfları, hafif eşitleme türleri ve yavaş başlatma türlerine yönelik belgeler için bağlantılar sağlar.|  
|[Paralel tanılama araçları](../../../docs/standard/parallel-programming/parallel-diagnostic-tools.md)|Görevler ve Paralel Yığınlar için Visual Studio hata ayıklayıcısı windows belgelerine ait bağlantılar sağlanmıştır ve [eşzamanlılık görselleştiricisi](/visualstudio/profiling/concurrency-visualizer), oluşan bir dizi görünümlerinde ve [!INCLUDE[vsprvsts](../../../includes/vsprvsts-md.md)] hata ayıklama ve ayarlamak için kullanabileceğiniz Profil Oluşturucu paralel kod performansını.|  
|[PLINQ ve TPL için özel Bölümleyiciler](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)|Bölümleyicilerin nasıl çalıştığını ve varsayılan bölümleyicilerin nasıl yapılandırılacağını veya nasıl yeni bir bölümleyicinin oluşturulacağını açıklar.|  
|[Görev zamanlayıcılar](http://msdn.microsoft.com/library/638f8ea5-21db-47a2-a934-86e1e961bf65)|Planlayıcıların nasıl çalıştığını ve varsayılan planlayıcıların nasıl yapılandırılması gerektiğini açıklar.|  
|[PLINQ ve TPL'deki lambda ifadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)|C# ve Visual Basic'teki lambda ifadelerine kısa bir genel bakış sunar ve PLINQ ve Görev Paralel Kitaplığı'nda nasıl kullanıldıklarını gösterir.|  
|[Daha fazla bilgi için](../../../docs/standard/parallel-programming/for-further-reading-parallel-programming.md)|.NET Framework'te paralel programlamaya yönelik ek belgeler ve örnek kaynaklar için bağlantılar sağlar.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Paralel programlama için desenleri: anlama ve uygulama paralel .NET Framework 4 desenler](http://go.microsoft.com/fwlink/?LinkID=185142)  
 [.NET Framework ile paralel programlama için örnek](http://code.msdn.microsoft.com/Samples-for-Parallel-b4b76364)
