---
title: Temel Windows Workflow Kavramları
ms.date: 03/30/2017
ms.assetid: 0e930e80-5060-45d2-8a7a-95c0690105d4
ms.openlocfilehash: ce17e5436ecff1937db605450d187184df9104a5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945671"
---
# <a name="fundamental-windows-workflow-concepts"></a>Temel Windows Workflow Kavramları
İş akışı geliştirme [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] bazı geliştiriciler için yeni kavramları kullanır. Bu konuda bazı kavramları ve nasıl uygulandığı açıklanmaktadır.  
  
## <a name="workflows-and-activities"></a>İş akışları ve etkinlikler  
 Bir iş akışı, bir işlem modelleri yapılandırılmış eylemleri koleksiyonudur. İş akışındaki her eylem bir etkinlik modellenir. Bir konak kullanarak bir iş akışı ile etkileşime giren <xref:System.Activities.WorkflowInvoker> bir yöntemi gibi bir iş akışını çağırmak için <xref:System.Activities.WorkflowApplication> yürütme gibi tek bir iş akışı örneği üzerinde açık denetim ve <xref:System.ServiceModel.WorkflowServiceHost> için çok örnekli ileti tabanlı etkileşimleri Senaryo. İş akışının adımları etkinliklerin bir hiyerarşi tanımlı olduğundan, iş akışı tanımlamak için hiyerarşideki en üst etkinlik söylenebilir. Bu hiyerarşi modeli açık gerçekleşmeden `SequentialWorkflow` ve `StateMachineWorkflow` önceki sürümlerden sınıfları. Etkinlikleri kendilerini diğer etkinliklerin bir koleksiyon olarak geliştirilen (kullanarak <xref:System.Activities.Activity> sınıf genellikle XAML kullanarak tanımlanan, bir temel olarak) veya kullanılarak oluşturulan özel <xref:System.Activities.CodeActivity> çalışma zamanı veri erişimi için veya kullanarakkullanabileceğinizsınıfı<xref:System.Activities.NativeActivity> iş akışı çalışma zamanı etkinlik Yazar kapsamını sunan sınıfı. Etkinlikler kullanılarak geliştirilmiş <xref:System.Activities.CodeActivity> ve <xref:System.Activities.NativeActivity> C# gibi CLR-uyumlu dilin kullanılarak oluşturulur.  
  
## <a name="activity-data-model"></a>Etkinlik veri modeli  
 Etkinlikler, depolamak ve aşağıdaki tabloda gösterilen türleri ile veri paylaşabilir.  
  
|||  
|-|-|  
|Değişken|Bir etkinlik verilerini depolar.|  
|Bağımsız Değişken|Veri ekleme çıkarma bir etkinlik taşır.|  
|İfade|Bir etkinlik bağımsız değişkeni bağlamalarında kullanılan yükseltilmiş bir dönüş değerine sahip.|  
  
## <a name="workflow-runtime"></a>İş akışı çalışma zamanı  
 İş akışı çalışma zamanı içinde iş akışları yürütme ortamıdır. <xref:System.Activities.WorkflowInvoker> bir iş akışını yürütmek için en basit yoludur. Konağın kullandığı <xref:System.Activities.WorkflowInvoker> aşağıdakiler:  
  
- Zaman uyumlu bir iş akışını çağırmak için.  
  
- Giriş sağlamak veya bir iş akışından çıkış almak için.  
  
- Etkinlikleri tarafından kullanılmak üzere uzantıları eklemek için.  
  
 <xref:System.Activities.ActivityInstance> Konaklar çalışma zamanı ile etkileşim kurmak için kullanabileceğiniz bir iş parçacığı Ara sunucudur. Konağın kullandığı <xref:System.Activities.ActivityInstance> aşağıdakiler:  
  
- Oluşturma veya bir örnek deposundan yüklenirken örneğini almak için.  
  
- Örnek yaşam döngüsü olaylarını almak.  
  
- İş akışının yürütülmesini denetlemek için.  
  
- Giriş sağlamak veya bir iş akışından çıkış almak için.  
  
- Bir iş akışı devamlılık sinyal ve değerleri iş akışına aktarmak için.  
  
- İş akışı verileri kalıcı hale getirmek için.  
  
- Etkinlikleri tarafından kullanılmak üzere uzantıları eklemek için.  
  
 Etkinlikler, uygun kullanarak iş akışı çalışma zamanı ortamı erişim elde edersiniz <xref:System.Activities.ActivityContext> gibi türetilmiş bir sınıf, <xref:System.Activities.NativeActivityContext> veya <xref:System.Activities.CodeActivityContext>. Bunlar bu bağımsız değişkenleri ve değişkenlerini çözmek için alt etkinlikler zamanlamak için ve birçok diğer amaçlar için kullanır.  
  
## <a name="services"></a>Hizmetler  
 İş akışları uygulamak ve mesajlaşma etkinlikleri kullanma zamanı gevşek bağlanmış hizmetlerine erişmek için doğal bir yol sağlar. Mesajlaşma etkinlikleri WCF yerleşiktir ve veri ekleme çıkarma iş akışı almak için kullanılan birincil mekanizmadır. Mesajlaşma etkinlikleri birlikte ileti değişim deseni, istediğiniz herhangi bir türden model oluşturabilirsiniz. Daha fazla bilgi için [Mesajlaşma etkinlikleri](../wcf/feature-details/messaging-activities.md). İş akışı hizmetlerini kullanarak barındırılır <xref:System.ServiceModel.Activities.WorkflowServiceHost> sınıfı. Daha fazla bilgi için [iş akışı hizmetlerini barındırma genel bakış](../wcf/feature-details/hosting-workflow-services-overview.md). İş akışı hizmetleri hakkında daha fazla bilgi için bkz: [iş akışı Hizmetleri](../wcf/feature-details/workflow-services.md)  
  
## <a name="persistence-unloading-and-long-running-workflows"></a>Kalıcılık, kaldırma ve uzun süre çalışan iş akışları  
 Windows iş akışı sağlayarak uzun süreli reaktif programlarını geliştirme kolaylaştırır:  
  
- Dış giriş erişim etkinlikler.  
  
- Oluşturma olanağı <xref:System.Activities.Bookmark> konak dinleyici tarafından devam ettirilebilir nesneleri.  
  
- Bir iş akışının veriyi kalıcı olarak kaldırma iş akışı ve yeniden yükleyin ve işlemin sürdürülmesini yanıt akışında yeniden etkinleştirme olanağı <xref:System.Activities.Bookmark> belirli bir iş akışı nesneleri.  
  
 Bir iş akışı etkinlikleri yürütmek için daha fazla hiç etkinlik yok veya tüm kadar şu anda yürütülen etkinlikler için giriş bekleyen kadar sürekli olarak yürütür. Bu ikinci durumda, iş akışı boş. Boşta sahiplikten iş akışları kaldırmak bir konak için ortak olan ve bir ileti olduğunda yürütme devam etmek için bunları yeniden ulaşır. <xref:System.ServiceModel.Activities.WorkflowServiceHost> Bu özellik için işlevsellik sağlar ve Genişletilebilir bir kaldırma İlkesi sağlar. Geçici bir durum verilerini veya kalıcı yapılamıyor diğer veri bloklarını yürütme için onu kullanarak kalıcı olmasını değil bir etkinlik bir konağa belirtir <xref:System.Activities.NoPersistHandle>. Bir iş akışı kullanarak, veri kalıcı depolama ortamı için de açıkça kalıcı <xref:System.Activities.Statements.Persist> etkinlik.
