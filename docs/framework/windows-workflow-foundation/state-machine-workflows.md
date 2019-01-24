---
title: Durum makinesi iş akışları
ms.date: 03/30/2017
ms.assetid: 344caacd-bf3b-4716-bd5a-eca74fc5a61d
ms.openlocfilehash: 89819f6b37fdaf601cf4e8b99fd5156c8e40af99
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521302"
---
# <a name="state-machine-workflows"></a>Durum makinesi iş akışları
Bir Durum makinesi programlar geliştirmek için iyi bilinen bir örnektir. <xref:System.Activities.Statements.StateMachine> Etkinliği ile birlikte <xref:System.Activities.Statements.State>, <xref:System.Activities.Statements.Transition>, ve diğer etkinlikleri Durum makinesi iş akışı programlar oluşturmak için kullanılabilir. Bu konu, durum makine iş akışları oluşturmaya genel bir bakış sağlar.  
  
## <a name="state-machine-workflow-overview"></a>Durum makinesi iş akışı genel bakış  
 Durum makinesi iş akışları ile iş akışınızı olay denetimli bir şekilde modelleyebilir modelleme stil sağlayın. A <xref:System.Activities.Statements.StateMachine> etkinliğin durumları içeren ve durum makinesinin mantığı oluşturma ve olabilir, geçişleri bir etkinlik kullanıldığında her yerde kullanılabilir. Durum makinesi çalışma zamanı'nda birkaç sınıfı vardır:  
  
-   <xref:System.Activities.Statements.StateMachine>  
  
-   <xref:System.Activities.Statements.State>  
  
-   <xref:System.Activities.Statements.Transition>  
  
 Bir Durum makinesi iş akışı oluşturmak için durumları eklenir bir <xref:System.Activities.Statements.StateMachine> etkinlik ve geçişleri kullanılır durumlar arasında akışını denetleme. Aşağıdaki ekran görüntüsünde, gelen [başlangıç Öğreticisi](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md) adım [nasıl yapılır: Bir Durum makinesi iş akışı oluşturma](../../../docs/framework/windows-workflow-foundation/how-to-create-a-state-machine-workflow.md), üç durumları ve geçişleri üç olan bir Durum makinesi iş akışı gösterilmektedir. **Hedef başlatmak** ilk durumudur ve iş akışındaki ilk duruma temsil eder. Bu satırın içinden baştaki tarafından belirlenen **Başlat** düğümü. Son durum iş akışında adlı **FinalState**ve iş akışı tamamlandığında noktasını temsil eder.  
  
 ![Durum makinesi iş akışı tamamlandı](../../../docs/framework/windows-workflow-foundation/media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")  
  
 Bir Durum makinesi iş akışı, bir ve yalnızca bir ilk durumu ve en az bir son duruma sahip olmalıdır. Son durum değil. her durum, en az bir geçiş olması gerekir. Aşağıdaki bölümlerde, oluşturma ve durumları ve geçişleri yapılandırma kapsar.  
  
## <a name="creating-and-configuring-states"></a>Oluşturma ve durumları yapılandırma  
 A <xref:System.Activities.Statements.State> içinde bir Durum makinesi olabilir bir durumu temsil eder. Eklemek için bir <xref:System.Activities.Statements.State> bir iş akışına sürükleyin **durumu** etkinlik Tasarımcısı'ndan **Durum makinesi** bölümünü **araç kutusu** üzerine bırakın bir <xref:System.Activities.Statements.StateMachine> Etkinlik [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] yüzeyi.  
  
 ![WF4 Durum makine etkinlikleri](../../../docs/framework/windows-workflow-foundation/media/netframework4platformupdate1statemachineactivities.jpg "NETFramework4PlatformUpdate1StateMachineActivities")  
  
 Bir durum olarak yapılandırmak için **ilk durumu**, durumu sağ tıklayıp **başlangıç durumuna ayarla**. Geçerli bir ilk durumu olmadan varsa, ek olarak, ilk durumuna bir çizgi sürükleyerek belirlenebilir **Başlat** istenen duruma iş akışının üst düğüm. Olduğunda bir <xref:System.Activities.Statements.StateMachine> etkinlik iş akışı Tasarımcısı bırakılan, adlandırılmış bir ilk durumu ile önceden yapılandırılmış **State1**. Bir Durum makinesi iş akışı bir ve yalnızca bir ilk duruma sahip olmalıdır.  
  
 Bir durum makinesindeki bir sonlandırıcı durumunu temsil eden bir durum, son durum adı verilir. Bir son duruma sahip bir durumdur, <xref:System.Activities.Statements.State.IsFinal%2A> özelliğini `true`, hiçbir <xref:System.Activities.Statements.State.Exit%2A> etkinlik ve bundan kaynaklanan hiçbir geçişler. Bir son duruma bir iş akışına eklemek için sürükleyin bir **FinalState** etkinlik Tasarımcısı'ndan **Durum makinesi** bölümünü **araç kutusu** üzerine bırakın bir <xref:System.Activities.Statements.StateMachine> etkinliği [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] yüzeyi. Bir Durum makinesi iş akışı en az bir son duruma sahip olmalıdır.  
  
### <a name="configuring-entry-and-exit-actions"></a>Giriş ve çıkış eylemleri yapılandırma  
 Bir durum olabilir bir <xref:System.Activities.Statements.State.Entry%2A> ve <xref:System.Activities.Statements.State.Exit%2A> eylem. (Son bir durum yapılandırılmış bir durum, yalnızca bir giriş eylem olabilir). Bir iş akışı örneği bir duruma girdiğinde, herhangi bir etkinlik girişi uygulamada yürütün. Giriş Eylem tamamlandığında Tetikleyiciler durumun geçişleri için zamanlanır. Geçiş sırasında başka bir duruma Onaylandı, etkinlikler, çıkış eyleminde yürütülür, durumu geçişleri aynı duruma geri bile. Çıkış eylemi tamamlandıktan sonra etkinlikler, geçiş'ın eylem yürütme ve ardından yeni bir durum için geçirilir ve giriş eylemlerini planlanır.  
  
> [!NOTE]
>  Bir Durum makinesi iş akışı hata ayıklama sırasında kesme noktaları, Durum makinesi iş akışı iller ve kök Durum makinesi etkinlik yerleştirilebilir. Doğrudan geçişleri üzerinde kesme noktaları yerleştirilebilir ancak durumları ve geçişleri içinde yer alan tüm etkinliklerde yerleştirilebilir.  
  
## <a name="creating-and-configuring-transitions"></a>Oluşturma ve geçişler yapılandırma  
 Tüm durumlar en az bir geçişin, tüm geçişler olmayabilir son bir durumu dışında olması gerekir. Geçişler, bir durum için bir Durum makinesi iş akışı eklenir veya durumu bırakılan gibi bunlar oluşturulabilir sonra eklenebilir.  
  
 Eklemek için bir <xref:System.Activities.Statements.State> ve bir geçiş tek adımda Sürükle oluşturmak bir **durumu** etkinliğinden **Durum makinesi** bölümünü **araç kutusu** ve onu kutucuğunun üzerine gelin başka bir durumda İş Akışı Tasarımcısı'nda. Zaman sürüklenen <xref:System.Activities.Statements.State> başka bir özelliktir <xref:System.Activities.Statements.State>, dört üçgenler diğer görünür <xref:System.Activities.Statements.State>. Varsa <xref:System.Activities.Statements.State> bırakılan dört üçgenler birini durumu makineye eklenir ve bir geçiş kaynak sunucudan oluşturulan <xref:System.Activities.Statements.State> bırakılan hedefe <xref:System.Activities.Statements.State>. Daha fazla bilgi için [Transition etkinlik Tasarımcısı](/visualstudio/workflow-designer/transition-activity-designer).  
  
 Bir durum eklendikten sonra bir geçiş oluşturmak için iki seçenek vardır. İlk seçenek, durum iş akışı tasarımcısının yüzeyine sürükleyin ve üzerinde var olan bir duruma getirin ve bırakma noktalarından birine doğrudan oluşturmaktır. Bu önceki bölümde açıklanan yöntemi için çok benzer. Ayrıca, fare istenen kaynak durumu gelin ve istenen hedef duruma bir satıra sürükleyin.  
  
> [!NOTE]
>  Kadar 76 geçiş iş akışı Tasarımcısı'nı kullanarak oluşturulan bir durum makinesindeki tek bir durumda olabilir. İş Akışı Tasarımcısı dışında oluşturulan bir durum geçişlerini sınırı yalnızca sistem kaynaklarının yetersizliği sınırlıdır.  
  
 Bir geçiş olabilir bir <xref:System.Activities.Statements.Transition.Trigger%2A>, <xref:System.Activities.Statements.Transition.Condition%2A>ve bir <xref:System.Activities.Statements.Transition.Action%2A>. Geçiş 's <xref:System.Activities.Statements.Transition.Trigger%2A> zaman zamanlanmış geçiş ait kaynak durumu'nın <xref:System.Activities.Statements.State.Entry%2A> eylem tamamlandığında. Genellikle <xref:System.Activities.Statements.Transition.Trigger%2A> bazı olayın meydana gelmesine türü için bekleyen bir etkinliktir ancak herhangi bir etkinliği ya da hiç etkinlik hiç olabilir. Bir kez <xref:System.Activities.Statements.Transition.Trigger%2A> etkinlik tamamlandıktan sonra <xref:System.Activities.Statements.Transition.Condition%2A>, varsa değerlendirilir. Yoksa hiçbir <xref:System.Activities.Statements.Transition.Trigger%2A> etkinlik sonra <xref:System.Activities.Statements.Transition.Condition%2A> hemen değerlendirilir. İçin değerlendirilen koşul yoksa `false`, geçişi iptal ve <xref:System.Activities.Statements.Transition.Trigger%2A> etkinliği durumundan tüm geçişler için işlemi yeniden zamanlanacak. Geçerli geçişi, aynı kaynak duruma paylaşan diğer geçişleri varsa bu <xref:System.Activities.Statements.Transition.Trigger%2A> eylemleri iptal ve de yeniden Planlanacak. Varsa <xref:System.Activities.Statements.Transition.Condition%2A> değerlendiren `true`, veya herhangi bir koşul yoktur sonra <xref:System.Activities.Statements.State.Exit%2A> kaynak durumu, eylemi yürütülür ve ardından <xref:System.Activities.Statements.Transition.Action%2A> geçişin yürütülür. Zaman <xref:System.Activities.Statements.Transition.Action%2A> tamamlandıktan, Denetim geçtiği **hedef** durumu  
  
 Sık kullanılan bir tetikleyici paylaşan geçişleri paylaşılan tetikleyici geçişi bilinir. Paylaşılan tetikleyici geçişi grubundaki her geçiş benzersiz bir ancak aynı tetikleyici sahip <xref:System.Activities.Statements.Transition.Condition%2A> ve eylem. Geçiş için ek eylemler eklemek ve paylaşılan bir geçiş oluşturmak için istenen geçiş başlangıcını gösteren daireye tıklayın ve istenen duruma sürükleyin. Aynı tetikleyici olarak ilk geçiş yeni geçişi paylaşır, ancak benzersiz bir koşulu ve eylem gerekir. Paylaşılan geçişleri de oluşturulabilir gelen geçiş Tasarımcısı'nda tıklayarak **paylaşılan tetikleyici geçişi Ekle** geçiş Tasarımcısı'nı seçip ardından istediğiniz hedef durumu alt kısmındaki  **Bağlanmak için kullanılabilir durumları** açılır.  
  
> [!NOTE]
>  Unutmayın <xref:System.Activities.Statements.Transition.Condition%2A> değerlendiren bir geçişin `False` (veya tüm koşulları bir paylaşılan tetikleyici geçişi için değerlendirmek `False`), geçiş gerçekleşmez ve tüm tetikleyiciler durumundan tüm geçişler için olacaktır işlemi yeniden zamanlanacak.  
  
 Durum makine iş akışları oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Bir Durum makinesi iş akışı oluşturmak](../../../docs/framework/windows-workflow-foundation/how-to-create-a-state-machine-workflow.md), [StateMachine etkinlik Tasarımcısı](/visualstudio/workflow-designer/statemachine-activity-designer), [State etkinlik Tasarımcısı](/visualstudio/workflow-designer/state-activity-designer), [FinalState etkinlik Tasarımcısı](/visualstudio/workflow-designer/finalstate-activity-designer)ve [Geçiş etkinlik Tasarımcısı](/visualstudio/workflow-designer/transition-activity-designer).  
  
## <a name="state-machine-terminology"></a>Durum makinesi terminolojisi  
 Bu bölümde bu konu başlığı altında yaptığımız kullanılan durum makine sözlüğü tanımlar.  
  
 Durum  
 Bir Durum makinesi ölçeklemesini temel birim. Bir Durum makinesi, belirli bir zamanda bir durumda olabilir.  
  
 Giriş Eylem  
 Bir etkinlik durumu girerken yürütüldü  
  
 Çıkış eylemi  
 Bir etkinlik durumu çıkarken yürütüldü  
  
 geçiş  
 Bir olayın oluşmasını belli bir türdeki için durum makinesinin tam yanıtı temsil eden iki durum arasında yönlendirilmiş bir ilişki.  
  
 Paylaşılan geçiş  
 Bir veya daha fazla geçiş ile bir kaynak durumu ve tetikleyici paylaşan bir geçiş, benzersiz bir koşulu ve eylem ancak sahiptir.  
  
 Tetikleyici  
 Bir tetikleyici etkinliği geçiş oluşmasına neden olur.  
  
 Koşul  
 Hangi gerekir değerlendirmek için bir kısıtlama `true` tetikleyici Geçişi tamamlamak için sırayla gerçekleştikten sonra.  
  
 Geçiş eylemi  
 Belirli bir geçiş gerçekleştirirken yürütülen bir etkinlik.  
  
 Koşullu geçiş  
 Açık bir koşul ile geçiş.  
  
 Kendi kendine geçiş  
 Kendisine bir durumdan transits geçişi.  
  
 Başlangıç durumu  
 Durum makinesinin başlangıç noktasını temsil eden bir durumu.  
  
 Son durum  
 Durum makinesi tamamlama belirten bir durum.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: Bir Durum makinesi iş akışı oluşturma](../../../docs/framework/windows-workflow-foundation/how-to-create-a-state-machine-workflow.md)
- [StateMachine Etkinlik Tasarımcısı](/visualstudio/workflow-designer/statemachine-activity-designer)
- [State Etkinlik Tasarımcısı](/visualstudio/workflow-designer/state-activity-designer)
- [FinalState Etkinlik Tasarımcısı](/visualstudio/workflow-designer/finalstate-activity-designer)
- [Transition Etkinlik Tasarımcısı](/visualstudio/workflow-designer/transition-activity-designer)
