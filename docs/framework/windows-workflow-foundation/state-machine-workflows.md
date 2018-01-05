---
title: "Durum makinesi iş akışları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 344caacd-bf3b-4716-bd5a-eca74fc5a61d
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8f28c0c4956c5e32dac204a99967ddd4b6352484
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="state-machine-workflows"></a>Durum makinesi iş akışları
Durum makinesinin programlar geliştirmek için iyi bilinen bir örnektir. <xref:System.Activities.Statements.StateMachine> Etkinliği ile birlikte <xref:System.Activities.Statements.State>, <xref:System.Activities.Statements.Transition>, ve diğer etkinlikleri Durum makinesi iş akışı programları oluşturmak için kullanılabilir. Bu konu durumu makine iş akışları oluşturma genel bir bakış sağlar.  
  
## <a name="state-machine-workflow-overview"></a>Durum makinesi iş akışı genel bakış  
 Durum makinesi iş akışları ile iş akışınızı olay denetimli bir şekilde model model stil sağlayın. A <xref:System.Activities.Statements.StateMachine> etkinlik içerir durumları ve durum makinesinin mantığı oluşturan ve olabilir geçişleri aktivite kullanılabilir herhangi bir yerde kullanılır. Durum makine çalışma zamanı'nda birkaç sınıfları şunlardır:  
  
-   <xref:System.Activities.Statements.StateMachine>  
  
-   <xref:System.Activities.Statements.State>  
  
-   <xref:System.Activities.Statements.Transition>  
  
 Bir Durum makinesi iş akışı oluşturmak için durumları eklenir bir <xref:System.Activities.Statements.StateMachine> etkinliği ve geçişleri kullanıldığını durumlarındaki akışını denetlemek. Aşağıdaki ekran görüntüsü gelen [başlangıç Öğreticisi](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md) adım [nasıl yapılır: bir Durum makinesi iş akışı oluşturmak](../../../docs/framework/windows-workflow-foundation/how-to-create-a-state-machine-workflow.md), üç durumdan ve üç geçişler içeren bir Durum makinesi iş akışının gösterir. **Hedef başlatma** başlangıç durum ve iş akışındaki ilk durumunu temsil eder. Bu içinden baştaki satır tarafından belirlenmiş **Başlat** düğümü. Son durum iş akışında adlı **son durum**ve iş akışı tamamlandığında noktasını temsil eder.  
  
 ![Durum makinesi iş akışı tamamlandı](../../../docs/framework/windows-workflow-foundation/media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")  
  
 Bir Durum makinesi iş akışı, tek bir ilk durumu ve en az bir son durum olması gerekir. Bir son durumuna her durumu en az bir geçiş olması gerekir. Aşağıdaki bölümlerde, oluşturma ve durumları ve geçişleri yapılandırma kapsar.  
  
## <a name="creating-and-configuring-states"></a>Oluşturma ve durumlarını yapılandırma  
 A <xref:System.Activities.Statements.State> içinde Durum makinesi olabilen içinde bir durumu temsil eder. Eklemek için bir <xref:System.Activities.Statements.State> bir iş akışına sürükleyin **durumu** etkinlik Tasarımcısı'ndan **Durum makinesi** bölümünü **araç** ve üzerine bırakın bir <xref:System.Activities.Statements.StateMachine> faaliyete [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] yüzeyini.  
  
 ![WF4 Durum makine etkinlikleri](../../../docs/framework/windows-workflow-foundation/media/netframework4platformupdate1statemachineactivities.jpg "NETFramework4PlatformUpdate1StateMachineActivities")  
  
 Bir durum olarak yapılandırmak için **ilk durumu**durumu sağ tıklatın ve seçin **ilk durumuna ayarla**. Geçerli bir ilk durum yok ise, ayrıca, ilk durumu bir satırından sürükleyerek belirlenebilir **Başlat** istenen durumu iş akışını üst düğüm. Zaman bir <xref:System.Activities.Statements.StateMachine> etkinliği iş akışı Tasarımcısı bırakıldı, bir başlangıç durumu adlı önceden yapılandırılmış **State1**. Bir Durum makinesi iş akışı bir ve yalnızca bir ilk duruma sahip olmalıdır.  
  
 Durum makinesinin sonlandırma durumunda temsil eden bir durumu, son durum adı verilir. Son durumuna sahip bir durumdur, <xref:System.Activities.Statements.State.IsFinal%2A> özelliğini `true`, hiçbir <xref:System.Activities.Statements.State.Exit%2A> etkinliği ve ondan kaynaklanan hiçbir geçişler. Bir iş akışına bir son duruma eklemek için sürükleyin bir **son durum** etkinlik Tasarımcısı'ndan **Durum makinesi** bölümünü **araç** ve üzerine bırakın bir <xref:System.Activities.Statements.StateMachine> etkinliği [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] yüzeyini. Bir Durum makinesi iş akışı en az bir son duruma sahip olmalıdır.  
  
### <a name="configuring-entry-and-exit-actions"></a>Giriş ve çıkış eylemleri yapılandırma  
 Bir durum olabilir bir <xref:System.Activities.Statements.State.Entry%2A> ve bir <xref:System.Activities.Statements.State.Exit%2A> eylem. (Bir son duruma yapılandırılmış bir durumda yalnızca bir giriş eylem olabilir). Bir iş akışı örneği bir duruma girdiğinde, hiç etkinlik girişi uygulamada yürütün. Giriş Eylem tamamlandığında durumun geçişler için Tetikleyicileri zamanlanır. Geçiş zaman başka bir durum Onaylandı, çıkış eylem etkinlikler çalıştırılır, durumu geçişleri aynı duruma geri olsa bile. Çıkış eylem tamamlandıktan sonra geçiş kullanıcının eylemde etkinlikleri yürütmek ve ardından yeni bir durum için geçişi ve giriş eylemlerini planlanır.  
  
> [!NOTE]
>  Bir Durum makinesi iş akışı hata ayıklama sırasında kök durumu makine etkinliği ve Durum makinesi iş akışı içinde durumları kesme noktaları yerleştirilebilir. Kesme noktaları geçişlerinin doğrudan yerleştirilebilir değildir, ancak durumları ve geçişleri içinde yer alan tüm etkinliklerde yerleştirilebilir.  
  
## <a name="creating-and-configuring-transitions"></a>Oluşturma ve yapılandırma geçişleri  
 Tüm durumları en az bir geçiş, tüm geçişler olmayabilir son bir durum dışında olması gerekir. Geçişler, bir durum Durum makinesi iş akışı için eklenene veya durumu bırakılan gibi bunlar oluşturulabilir sonra eklenebilir.  
  
 Eklemek için bir <xref:System.Activities.Statements.State> ve tek bir adımda Sürükle bir geçiş oluşturmak bir **durumu** etkinliğinden **Durum makinesi** bölümünü **araç** ve üzerine gelin, başka bir durumda üzerinden İş Akışı Tasarımcısı'nda. Zaman sürüklenen <xref:System.Activities.Statements.State> başka bir <xref:System.Activities.Statements.State>, dört üçgenler diğer görünür <xref:System.Activities.Statements.State>. Varsa <xref:System.Activities.Statements.State> bırakılır dört üçgenler birini için durum makinesinin eklenir ve bir geçiş kaynak sunucudan oluşturulan <xref:System.Activities.Statements.State> bırakılan hedefe <xref:System.Activities.Statements.State>. Daha fazla bilgi için bkz: [geçiş etkinlik Tasarımcısı](/visualstudio/workflow-designer/transition-activity-designer).  
  
 Bir durum eklendikten sonra bir geçiş oluşturmak için iki seçenek vardır. İlk seçenek, iş akışı Tasarımcısı yüzeyden durumu sürükleyin ve üzerinde var olan bir duruma getirin ve açılan noktalarından birini bırakma oluşturmaktır. Bu önceki bölümde açıklanan yöntemi için çok benzer. Fare üzerinde istenen kaynak durumu üzerine gelin ve bir satır için istenen hedef durumu sürükleyin.  
  
> [!NOTE]
>  İş Akışı Tasarımcısı'nı kullanarak oluşturulan kadar 76 geçişleri Durum makinesi tek bir durumda olabilir. Tasarımcı dışında oluşturulan iş akışı için bir durum için geçişleri sınırını yalnızca sistem kaynaklarının yetersizliği sınırlıdır.  
  
 Bir geçiş olabilir bir <xref:System.Activities.Statements.Transition.Trigger%2A>, <xref:System.Activities.Statements.Transition.Condition%2A>ve bir <xref:System.Activities.Statements.Transition.Action%2A>. Geçiş 's <xref:System.Activities.Statements.Transition.Trigger%2A> zaman zamanlanmış geçişi ait kaynak durumun <xref:System.Activities.Statements.State.Entry%2A> eylemdir tamamlandı. Genellikle <xref:System.Activities.Statements.Transition.Trigger%2A> bazı gerçekleşmesi için olay türü için bekleyeceği aktivite ancak herhangi bir etkinlik veya hiçbir etkinlik hiç olabilir. Bir kez <xref:System.Activities.Statements.Transition.Trigger%2A> etkinlik tamamlandığında <xref:System.Activities.Statements.Transition.Condition%2A>, varsa, değerlendirilir. Varsa hiçbir <xref:System.Activities.Statements.Transition.Trigger%2A> etkinlik sonra <xref:System.Activities.Statements.Transition.Condition%2A> hemen değerlendirilir. Koşul değerlendirilirse `false`, geçiş işlemi iptal edildi ve <xref:System.Activities.Statements.Transition.Trigger%2A> etkinlik durumu tüm geçişler için yeniden. Geçerli geçişi, aynı kaynak duruma paylaşan diğer geçişleri varsa bu <xref:System.Activities.Statements.Transition.Trigger%2A> Eylemler iptal ve de yeniden. Varsa <xref:System.Activities.Statements.Transition.Condition%2A> değerlendiren `true`, veya herhangi bir koşul sonra <xref:System.Activities.Statements.State.Exit%2A> kaynak durumu, eylemi yürütülürse ve ardından <xref:System.Activities.Statements.Transition.Action%2A> geçişin yürütülür. Zaman <xref:System.Activities.Statements.Transition.Action%2A> tamamlandığında, Denetim geçtiği **hedef** durumu  
  
 Ortak bir tetikleyici paylaşmak geçişleri paylaşılan tetikleyici geçişler bilinir. Paylaşılan tetikleyici geçişleri grubundaki her geçiş benzersiz bir ancak aynı tetikleyicisine sahip <xref:System.Activities.Statements.Transition.Condition%2A> ve eylem. Bir geçiş için ek eylemler ekleyin ve paylaşılan bir geçiş oluşturmak için istenen geçiş başlangıcını gösterir daireye tıklayın ve belirtilen istenen duruma sürükleyin. Yeni geçiş aynı tetikleyici ilk geçiş olarak paylaşır, ancak benzersiz bir koşul veya eylem sahip olur. Paylaşılan geçişleri de oluşturulabilir gelen geçiş Tasarımcısı'nda tıklayarak **paylaşılan tetikleyici geçiş Ekle** geçiş Tasarımcısı'nı ve ardından istenen hedef durumundan seçerek altındaki  **Bağlanmak için kullanılabilir durumları** açılır.  
  
> [!NOTE]
>  Unutmayın <xref:System.Activities.Statements.Transition.Condition%2A> bir geçişin değerlendiren `False` (veya bir paylaşılan tetikleyici geçiş koşulların tümü için değerlendirin `False`), geçiş gerçekleşmez ve durumundan tüm geçişler için tüm Tetikleyicileri olacaktır yeniden.  
  
 Durum makinesi iş akışları oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: Durum makinesi iş akışı oluşturmak](../../../docs/framework/windows-workflow-foundation/how-to-create-a-state-machine-workflow.md), [Durum makinesi etkinlik Tasarımcısı](/visualstudio/workflow-designer/statemachine-activity-designer), [durumu etkinlik Tasarımcısı](/visualstudio/workflow-designer/state-activity-designer), [Son durum etkinlik Tasarımcısı](/visualstudio/workflow-designer/finalstate-activity-designer), ve [geçiş etkinlik Tasarımcısı](/visualstudio/workflow-designer/transition-activity-designer).  
  
## <a name="state-machine-terminology"></a>Durum makinesi terminolojisi  
 Bu bölümde, bu konu boyunca kullanılan durumu makine sözlüğü tanımlar.  
  
 Durum  
 Durum makinesi oluşturur temel birim. Durum makinesinin belirli bir zamanda bir durumda olabilir.  
  
 Giriş Eylem  
 Bir etkinlik durumu girerken yürütülebilir.  
  
 Çıkış eylemi  
 Bir etkinlik durumu çıkarken yürütülebilir.  
  
 geçiş  
 Tam bir yanıt durumu makinenin belirli bir türdeki bir olay bir örneğini temsil eden iki durumlu arasındaki yönlendirilmiş bir ilişki.  
  
 Paylaşılan geçiş  
 Kaynak durumu ve tetikleyici bir veya daha fazla geçiş ile paylaşır bir geçiş, benzersiz bir koşul veya eylem ancak vardır.  
  
 Tetikleyici  
 Bir geçişe oluşmasına neden tetikleme etkinliği.  
  
 Koşul  
 Değerlendirilmelidir bir kısıtlamasına `true` sırada Geçişi tamamlamak için tetikleyici gerçekleştikten sonra.  
  
 Geçiş eylemi  
 Belirli bir geçiş gerçekleştirirken yürütülen bir etkinlik.  
  
 Koşullu geçiş  
 Bir geçiş açık koşuluyla.  
  
 Kendi kendine geçiş  
 Bir durumdan kendisine transits bir geçiş.  
  
 İlk durumu  
 Durum makinesinin başlangıç noktasını temsil eden bir durumda.  
  
 Son durum  
 Durum makinesinin tamamlanmasından temsil eden bir durumda.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Durum Makinesi İş Akışı Oluşturma](../../../docs/framework/windows-workflow-foundation/how-to-create-a-state-machine-workflow.md)  
 [StateMachine Etkinlik Tasarımcısı](/visualstudio/workflow-designer/statemachine-activity-designer)  
 [State Etkinlik Tasarımcısı](/visualstudio/workflow-designer/state-activity-designer)  
 [FinalState Etkinlik Tasarımcısı](/visualstudio/workflow-designer/finalstate-activity-designer)  
 [Transition Etkinlik Tasarımcısı](/visualstudio/workflow-designer/transition-activity-designer)
