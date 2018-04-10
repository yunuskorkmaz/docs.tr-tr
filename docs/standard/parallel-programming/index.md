---
title: .NET içinde Paralel Programlama
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parallel programming
ms.assetid: 4d83c690-ad2d-489e-a2e0-b85b898a672d
caps.latest.revision: 19
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c0ea65b0a61719c85ab1da53bcc99f5d43a3210b
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="parallel-programming-in-net"></a>.NET içinde Paralel Programlama
Birçok kişisel bilgisayar ve iş istasyonunun, birden çok iş parçacığının aynı anda yürütülmesini sağlayan iki veya dört çekirdeği (yani CPU'su) vardır. Yakın gelecekte bilgisayarların önemli ölçüde daha fazla çekirdeğe sahip olacağı tahmin edilmektedir. Bugünün ve yarının donanımlarından yararlanmak için kodunuzu işi birden fazla işlemci arasında dağıtacak şekilde paralel hale getirebilirsiniz. Geçmişte, paralel hale getirme için iş parçacıklarının ve kilitlerin düşük düzeyde kullanımı gerekiyordu. [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)] ve [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] yeni bir çalışma zamanı, yeni sınıf kitaplığı türleri ve yeni tanılama araçları sağlayarak Paralel Programlama Desteği geliştirir. Bu özellikler, doğrudan iş parçacıkları veya iş parçacığı havuzuyla çalışmak zorunda kalmadan doğal bir ifadede etkili, ayrıntılı ve ölçeklenebilir paralel kod yazmanız için paralel geliştirmeyi basitleştirir. Aşağıdaki çizimde paralel programlama mimarisinde üst düzey bir genel bakış sağlayan [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].  
  
 ![.NET paralel programlama mimarisi](../../../docs/standard/parallel-programming/media/tpl-architecture.png "TPL_Architecture")  
  
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
|[Daha Fazla Bilgi İçin](../../../docs/standard/parallel-programming/for-further-reading-parallel-programming.md)|.NET Framework'te paralel programlamaya yönelik ek belgeler ve örnek kaynaklar için bağlantılar sağlar.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Paralel programlama için desenleri: anlama ve uygulama paralel .NET Framework 4 desenler](https://www.microsoft.com/download/details.aspx?id=19222)  
 [.NET Framework ile paralel programlama için örnek](http://code.msdn.microsoft.com/Samples-for-Parallel-b4b76364)
