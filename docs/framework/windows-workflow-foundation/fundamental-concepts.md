---
title: "Temel Windows iş akışı kavramları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e930e80-5060-45d2-8a7a-95c0690105d4
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fca570f661b1867737cc3af295aff5fd8d4cd5ec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="fundamental-windows-workflow-concepts"></a>Temel Windows iş akışı kavramları
İş akışı geliştirme [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] bazı geliştiriciler için yeni kavramları kullanır. Bu konuda bazı kavramlar ve nasıl uygulandığı açıklanmaktadır.  
  
## <a name="workflows-and-activities"></a>İş akışları ve etkinlikler  
 Bir iş akışı bir işlem modellerin yapılandırılmış eylemleri koleksiyonudur. Her eylem iş akışı içinde bir etkinlik olarak modellenir. Bir ana bilgisayar kullanarak bir iş akışı ile etkileşime giren <xref:System.Activities.WorkflowInvoker> bir yöntem değilmiş gibi bir iş akışı çağırma için <xref:System.Activities.WorkflowApplication> bir tek iş akışı örneğini yürütmeyi üzerinde açık denetim için ve <xref:System.ServiceModel.WorkflowServiceHost> için çok örnekli ileti tabanlı etkileşimleri senaryoları. İş akışının adımları etkinliklerin hiyerarşi olarak tanımlandığından hiyerarşideki en üstteki etkinliği iş akışını tanımlamak için söylenebilir. Bu hiyerarşi modeli açık gerçekleşir `SequentialWorkflow` ve `StateMachineWorkflow` önceki sürümlerden sınıfları. Etkinlikler kendilerini diğer etkinlikler koleksiyon olarak geliştirilen (kullanarak <xref:System.Activities.Activity> olarak genellikle XAML kullanılarak tanımlanmış bir taban sınıf) veya kullanılarak oluşturulan özel <xref:System.Activities.CodeActivity> çalışma veri erişimi için veya kullanarakkullanabileceğisınıfı<xref:System.Activities.NativeActivity> iş akışı çalışma zamanı etkinlik Yazar derecesini gösterir sınıfı. Etkinlikler kullanılarak geliştirilmiş <xref:System.Activities.CodeActivity> ve <xref:System.Activities.NativeActivity> C# gibi CLR uyumlu dilleri kullanılarak oluşturulur.  
  
## <a name="activity-data-model"></a>Etkinlik veri modeli  
 Etkinlikler depolamak ve aşağıdaki tabloda gösterilen türlerini kullanarak veri paylaşımı.  
  
|||  
|-|-|  
|Değişken|Verileri bir etkinlikte depolar.|  
|Bağımsız Değişken|Verileri içine ve dışına bir etkinlik taşır.|  
|İfade|Bağımsız değişken bağlantılarında kullanılan yükseltilmiş bir dönüş değeri olmayan bir etkinliği.|  
  
## <a name="workflow-runtime"></a>İş akışı çalışma zamanı  
 İş akışı çalışma zamanı, iş akışlarını yürütmek ortamıdır. <xref:System.Activities.WorkflowInvoker>bir iş akışını yürütmek için kolay bir yoludur. Konağın kullandığı <xref:System.Activities.WorkflowInvoker> aşağıdaki için:  
  
-   Zaman uyumlu olarak bir iş akışının çağırmak için.  
  
-   Giriş sağlamak ya da bir iş akışından çıkış almak için.  
  
-   Etkinlikler tarafından kullanılacak uzantıları eklemek için.  
  
 <xref:System.Activities.ActivityInstance>ana bilgisayarları çalışma zamanı ile etkileşim kurmak için kullandığı iş parçacığı proxy olduğunda. Konağın kullandığı <xref:System.Activities.ActivityInstance> aşağıdaki için:  
  
-   Bunu oluşturarak veya bir örnek mağazadan yüklenirken örneğini almak için.  
  
-   Örnek yaşam döngüsü olayları hakkında bildirim almak için.  
  
-   İş akışı yürütme denetlemek için.  
  
-   Giriş sağlamak ya da bir iş akışından çıkış almak için.  
  
-   Bir iş akışı devamlılık sinyal ve iş akışına değerleri geçirmek için.  
  
-   İş akışı veri kalıcı hale getirmek için.  
  
-   Etkinlikler tarafından kullanılacak uzantıları eklemek için.  
  
 Etkinlikler uygun kullanarak iş akışı çalışma zamanı ortamı elde <xref:System.Activities.ActivityContext> gibi türetilmiş bir sınıf, <xref:System.Activities.NativeActivityContext> veya <xref:System.Activities.CodeActivityContext>. Bu bağımsız değişkenler ve değişkenleri çözmek için alt etkinlikler zamanlamak için ve birçok başka amaçlarla kullanırlar.  
  
## <a name="services"></a>Hizmetler  
 İş akışları uygulamak ve mesajlaşma etkinlikleri kullanarak birbirine sıkı şekilde bağlı hizmetlere erişmek için doğal bir yolunu sağlar. Mesajlaşma etkinlikleri üzerinde oluşturulan [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] ve içine ve dışına bir iş akışı veri almak için kullanılan birincil sistemdir. İleti değişim deseni istediğiniz her türlü birlikte modellemek için Mesajlaşma etkinlikleri oluşturabilirsiniz. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]bkz: [Mesajlaşma etkinlikleri](../../../docs/framework/wcf/feature-details/messaging-activities.md). İş akışı Hizmetleri kullanılarak barındırılır <xref:System.ServiceModel.Activities.WorkflowServiceHost> sınıfı. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][İş akışı barındırma hizmetleri genel bakış](../../../docs/framework/wcf/feature-details/hosting-workflow-services-overview.md). [!INCLUDE[crabout](../../../includes/crabout-md.md)]İş akışı hizmetleri bakın [iş akışı Hizmetleri](../../../docs/framework/wcf/feature-details/workflow-services.md)  
  
## <a name="persistence-unloading-and-long-running-workflows"></a>Kalıcılık, kaldırma ve uzun süre çalışan iş akışları  
 Windows iş akışı sağlayarak uzun süre çalışan reaktif programları yazma kolaylaştırır:  
  
-   Dış giriş erişim etkinlikler.  
  
-   Oluşturma olanağı <xref:System.Activities.Bookmark> konak dinleyicisi tarafından devam ettirilebilir nesneleri.  
  
-   Bir iş akışının verilerini sürdürülmesi iş akışı kaldırma ve sonra yeniden yükleyin ve sürdürme yanıt akışında yeniden etkinleştirme olanağı <xref:System.Activities.Bookmark> belirli bir iş akışı nesneleri.  
  
 Bir iş akışı etkinlikleri yürütmek için daha fazla hiç etkinlik yok veya tüm kadar şu anda yürütülen etkinlikler için giriş bekleyen kadar sürekli olarak yürütür. Bu ikinci durumda, iş akışı boştadır. Boşta ilerlemiş iş akışları kaldırmak bir ana bilgisayar için ortak olan ve bunları bir ileti olduğunda yürütme devam etmek için yeniden ulaşır. <xref:System.ServiceModel.Activities.WorkflowServiceHost>Bu özellik için işlevsellik sağlar ve bir Genişletilebilir kaldırma İlkesi sağlar. Volatile durumu verilerini veya kalıcı yapılamıyor diğer verileri kullanan bloklarını yürütme için bir etkinlik bir konağa kullanarak kalıcı değil olduğunu gösterebilir <xref:System.Activities.NoPersistHandle>. Bir iş akışı kullanarak dayanıklı depolama ortamına verilerini de açıkça kalıcı <xref:System.Activities.Statements.Persist> etkinlik.
