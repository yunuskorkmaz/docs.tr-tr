---
title: Durum Makinesi İş Akışları
ms.date: 03/30/2017
ms.assetid: 344caacd-bf3b-4716-bd5a-eca74fc5a61d
ms.openlocfilehash: 7b655208f4cc8274cdc5a8dad68ff1fa9eaad5ef
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948992"
---
# <a name="state-machine-workflows"></a>Durum Makinesi İş Akışları
Durum makinesi, program geliştirmeye yönelik iyi bilinen bir paradigma sahiptir. Etkinlik,, ve diğer <xref:System.Activities.Statements.State> <xref:System.Activities.Statements.Transition>etkinliklerle birlikte durum makinesi iş akışı programları oluşturmak için kullanılabilir. <xref:System.Activities.Statements.StateMachine> Bu konuda, durum makinesi iş akışları oluşturmaya genel bakış sunulmaktadır.  
  
## <a name="state-machine-workflow-overview"></a>Durum makinesi Iş akışına genel bakış  
 Durum makinesi iş akışları, iş akışınızı olay odaklı şekilde modellenebilen bir modelleme stili sağlar. <xref:System.Activities.Statements.StateMachine> Etkinlik, durum makinesinin mantığını oluşturan durumlar ve geçişleri içerir ve bir etkinliğin kullanılabileceği her yerde kullanılabilir. Durum makinesi çalışma zamanında birkaç sınıf vardır:  
  
- <xref:System.Activities.Statements.StateMachine>  
  
- <xref:System.Activities.Statements.State>  
  
- <xref:System.Activities.Statements.Transition>  
  
 Bir durum makinesi iş akışı oluşturmak için, bir <xref:System.Activities.Statements.StateMachine> etkinliğe durumlar eklenir ve geçişler, durumlar arasındaki akışı kontrol etmek için kullanılır. Aşağıdaki ekran görüntüsünde, Başlangıç [ [öğreticisinde](getting-started-tutorial.md) nasıl yapılır: Durum makinesi iş akışı](how-to-create-a-state-machine-workflow.md)oluşturma, üç durumlu ve üç geçiş içeren bir durum makinesi iş akışını gösterir. **Başlatma hedefi** başlangıç durumudur ve iş akışındaki ilk durumu temsil eder. Bu, **Başlangıç** düğümünden bu satıra satır başına atanır. İş akışındaki son durum **FinalState**olarak adlandırılır ve iş akışının tamamlandığı noktayı temsil eder.  
  
 ![Tamamlanan durum makinesi iş akışını gösteren çizim.](./media/state-machine-workflows/complete-state-machine-workflow.jpg)  
  
 Bir durum makinesi iş akışı bir ve yalnızca bir başlangıç durumuna ve en az bir son duruma sahip olmalıdır. Son durum olmayan her durum en az bir geçişe sahip olmalıdır. Aşağıdaki bölümlerde durum ve geçişlerin oluşturulması ve yapılandırılması ele alınmaktadır.  
  
## <a name="creating-and-configuring-states"></a>Durum oluşturma ve yapılandırma  
 Bir <xref:System.Activities.Statements.State> durum makinesinin içinde olabilecek bir durumu temsil eder. Bir iş akışına <xref:System.Activities.Statements.State> bir eklemek için, **durum** etkinlik tasarımcısını **araç kutusunun** <xref:System.Activities.Statements.StateMachine> **durum makinesi** bölümünden sürükleyin [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] ve yüzeyde bir etkinliğin üzerine bırakın.  
  
 ![Araç kutusunun durum makinesi bölümünün ekran görüntüsü.](./media/state-machine-workflows/state-machine-section-toolbox.jpg)  
  
 Durumu **Başlangıç durumu**olarak yapılandırmak için, duruma sağ tıklayın ve **Başlangıç durumu olarak ayarla**' yı seçin. Ayrıca, geçerli bir başlangıç durumu yoksa, iş akışının en üstündeki **Başlangıç** düğümünden istenen duruma kadar bir çizgi sürüklenerek ilk durum belirlenebilir. Bir <xref:System.Activities.Statements.StateMachine> etkinlik iş akışı tasarımcısına bırakıldığında, **State1**adlı bir başlangıç durumuyla önceden yapılandırılmıştır. Bir durum makinesi iş akışı bir ve yalnızca bir başlangıç durumuna sahip olmalıdır.  
  
 Durum makinesindeki sonlandırma durumunu temsil eden bir durum, son durum olarak adlandırılır. Son durum, <xref:System.Activities.Statements.State.IsFinal%2A> özelliği olarak `true`ayarlanmış, etkinliği olmayan <xref:System.Activities.Statements.State.Exit%2A> ve bundan kaynaklanan hiçbir geçiş olmayan bir durumdur. Bir iş akışına son durum eklemek için, **araç kutusunun** <xref:System.Activities.Statements.StateMachine> **durum makinesi** bölümünden bir **sonlandırmadurumu** etkinlik tasarımcısını sürükleyin ve [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] yüzeyi bir etkinliğin üzerine bırakın. Bir durum makinesi iş akışında en az bir son durum olmalıdır.  
  
### <a name="configuring-entry-and-exit-actions"></a>Giriş ve çıkış eylemlerini yapılandırma  
 Bir durum bir <xref:System.Activities.Statements.State.Entry%2A> <xref:System.Activities.Statements.State.Exit%2A> ve bir eyleme sahip olabilir. (Son durum olarak yapılandırılan bir durum yalnızca bir giriş eylemine sahip olabilir). Bir iş akışı örneği bir durum girdiğinde, giriş eyleminde herhangi bir etkinlik yürütülür. Giriş eylemi tamamlandığında, durum geçişleri için Tetikleyiciler zamanlanır. Başka bir duruma geçiş onaylanırsa, durum aynı duruma geri geçirse bile, çıkış Eylemdeki etkinlikler yürütülür. Çıkış eylemi tamamlandıktan sonra, geçiş eyleminin içindeki etkinlikler yürütülür ve ardından yeni durum ' a geçirilir ve giriş eylemleri zamanlanır.  
  
> [!NOTE]
> Bir durum makinesi iş akışında hata ayıklarken, kesme noktaları kök durum makinesi etkinliğine ve durum makinesi iş akışı içindeki durumlara yerleştirilebilecek. Kesme noktaları doğrudan geçişlere yerleştirilmeyebilir, ancak durumlar ve geçişler içindeki etkinliklere dahil edilebilir.  
  
## <a name="creating-and-configuring-transitions"></a>Geçişleri oluşturma ve yapılandırma  
 Herhangi bir geçişi olmayan son durum dışında, tüm durumlar en az bir geçişe sahip olmalıdır. Bir durum makine iş akışına bir durum eklendikten sonra geçişler eklenebilir veya durum bırakılmakta olduğundan oluşturulabilir.  
  
 Bir adımda bir <xref:System.Activities.Statements.State> geçiş eklemek ve bir geçiş oluşturmak için, **araç kutusunun** **durum makinesi** bölümünden bir **durum** etkinliği sürükleyin ve iş akışı tasarımcısında başka bir durum üzerine gelin. Sürüklenen <xref:System.Activities.Statements.State> bir diğerinin <xref:System.Activities.Statements.State>üzerindeyken, diğerinin <xref:System.Activities.Statements.State>etrafında dört üçgen görünür. Dört üçgenden birine bırakıldığında, durum makinesine eklenir ve kaynaktan <xref:System.Activities.Statements.State> bırakılan hedefe <xref:System.Activities.Statements.State>bir geçiş oluşturulur. <xref:System.Activities.Statements.State> Daha fazla bilgi için bkz. [geçiş etkinlik Tasarımcısı](/visualstudio/workflow-designer/transition-activity-designer).  
  
 Bir durum eklendikten sonra bir geçiş oluşturmak için iki seçenek vardır. İlk seçenek, durumu iş akışı Tasarımcısı yüzeyinden sürüklemektir ve var olan bir durum üzerine getirip bırakma noktalarından birine bırakabilir. Bu, önceki bölümde açıklanan yönteme çok benzer. Ayrıca, fare işaretçisini istenen kaynak durumunun üzerine getirip bir çizgiyi istediğiniz hedef durumuna sürükleyebilirsiniz.  
  
> [!NOTE]
> Bir durum makinesindeki tek bir durum, iş akışı Tasarımcısı kullanılarak oluşturulan en fazla 76 geçişine sahip olabilir. Tasarımcı dışında oluşturulan iş akışları için bir durum geçişleri sınırı yalnızca sistem kaynaklarıyla sınırlıdır.  
  
 Bir geçişte <xref:System.Activities.Statements.Transition.Trigger%2A> <xref:System.Activities.Statements.Transition.Condition%2A>,, ve <xref:System.Activities.Statements.Transition.Action%2A>bir olabilir. Geçişin kaynak <xref:System.Activities.Statements.Transition.Trigger%2A> <xref:System.Activities.Statements.State.Entry%2A> durumunun eylemi tamamlandığında bir geçiş zamanlanır. Genellikle, <xref:System.Activities.Statements.Transition.Trigger%2A> bazı olay türlerinin gerçekleşmesini bekleyen bir etkinliktir, ancak herhangi bir etkinlik olabilir veya hiç etkinlik olmaz. <xref:System.Activities.Statements.Transition.Trigger%2A> Etkinlik tamamlandıktan<xref:System.Activities.Statements.Transition.Condition%2A>sonra, varsa, değerlendirilir. Etkinlik yoksa, <xref:System.Activities.Statements.Transition.Condition%2A> hemen değerlendirilir. <xref:System.Activities.Statements.Transition.Trigger%2A> Koşul olarak `false`değerlendirilirse, geçiş iptal edilir <xref:System.Activities.Statements.Transition.Trigger%2A> ve durumdan gelen tüm geçişler için etkinlik yeniden çizelgelenir. Geçerli geçiş ile aynı kaynak durumunu paylaşan başka geçişler varsa, bu <xref:System.Activities.Statements.Transition.Trigger%2A> eylemler iptal edilir ve aynı zamanda yeniden çizelgelenir. <xref:System.Activities.Statements.Transition.Condition%2A> Olarak <xref:System.Activities.Statements.State.Exit%2A> <xref:System.Activities.Statements.Transition.Action%2A> değerlendirilirse veya koşul yoksa, kaynak durumu eylemi yürütülür ve sonra geçişin yürütülmesi yürütülür. `true` Tamamlandığında, denetim hedef durumuna geçer <xref:System.Activities.Statements.Transition.Action%2A>  
  
 Ortak bir tetikleyiciyi paylaşan geçişler, paylaşılan tetikleyici geçişleri olarak bilinir. Paylaşılan tetikleyici geçişleri grubundaki her geçiş aynı tetikleyiciye sahiptir, ancak benzersiz <xref:System.Activities.Statements.Transition.Condition%2A> bir işlemdir. Bir geçişe ek eylemler eklemek ve paylaşılan bir geçiş oluşturmak için, istenen geçişin başlangıcını belirten daireye tıklayın ve istediğiniz duruma sürükleyin. Yeni geçiş, başlangıç geçişi olarak aynı tetikleyiciyi paylaşır, ancak benzersiz bir koşula ve eyleme sahip olur. Paylaşılan geçişler, geçiş Tasarımcısı ' nın altında **Paylaşılan tetikleyici geçişi ekle** ' ye tıklayıp, ardından **bağlantı kurmak için kullanılabilir durumlar** ' da istenen hedef durumu seçilerek geçiş Tasarımcısı içinden da oluşturulabilir açılır liste.  
  
> [!NOTE]
> Bir geçiş `False` `False`işleminin (veya paylaşılan bir tetikleyici geçişinin tüm koşullarını değerlendirmesi) değerlendirilirse, geçişin gerçekleşmeyeceğini ve durumdan gelen tüm geçişler için tüm tetikleyicilerinin olacağını unutmayın. <xref:System.Activities.Statements.Transition.Condition%2A> zamanlandı.  
  
 Durum makinesi iş akışları oluşturma hakkında daha fazla bilgi için [bkz. nasıl yapılır: Bir durum makinesi iş akışı](how-to-create-a-state-machine-workflow.md), [StateMachine etkinlik Tasarımcısı](/visualstudio/workflow-designer/statemachine-activity-designer), [durum etkinlik Tasarımcısı](/visualstudio/workflow-designer/state-activity-designer), [FinalState etkinlik Tasarımcısı](/visualstudio/workflow-designer/finalstate-activity-designer)ve [geçiş etkinlik Tasarımcısı](/visualstudio/workflow-designer/transition-activity-designer)oluşturun.  
  
## <a name="state-machine-terminology"></a>Durum makinesi terminolojisi  
 Bu bölüm, bu konu başlığı altında kullanılan durum makinesi sözlüğünü tanımlar.  
  
 Durum  
 Bir durum makinesini oluşturan temel birim. Bir durum makinesi belirli bir zamanda tek bir durumda olabilir.  
  
 Giriş eylemi  
 Durum girilirken yürütülen bir etkinlik  
  
 Çıkış eylemi  
 Durumdan çıkarken yürütülen bir etkinlik  
  
 Transition  
 Bir durum makinesinin belirli bir türdeki bir olay oluşumuna yönelik tüm yanıtını temsil eden iki durum arasında yönlendirilmiş bir ilişki.  
  
 Paylaşılan geçiş  
 Kaynak durumunu paylaşan ve bir veya daha fazla geçişle tetikleyen, ancak benzersiz bir koşul ve eyleme sahip olan bir geçiş.  
  
 Tetikleyici  
 Bir geçişin oluşmasına neden olan tetikleme etkinliği.  
  
 Koşul  
 Geçişin tamamlanmasını sağlamak için tetikleyici oluştuktan `true` sonra değerlendirilmesi gereken bir kısıtlama.  
  
 Geçiş eylemi  
 Belirli bir geçiş gerçekleştirilirken yürütülen bir etkinlik.  
  
 Koşullu geçiş  
 Açık koşula sahip bir geçiş.  
  
 Kendi kendine geçiş  
 Bir durumdan kendine geçişli bir geçiş.  
  
 İlk durum  
 Durum makinesinin başlangıç noktasını temsil eden bir durum.  
  
 Son durum  
 Durum makinesinin tamamlandığını temsil eden bir durum.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Durum makinesi Iş akışı oluşturma](how-to-create-a-state-machine-workflow.md)
- [StateMachine Etkinlik Tasarımcısı](/visualstudio/workflow-designer/statemachine-activity-designer)
- [State Etkinlik Tasarımcısı](/visualstudio/workflow-designer/state-activity-designer)
- [FinalState Etkinlik Tasarımcısı](/visualstudio/workflow-designer/finalstate-activity-designer)
- [Transition Etkinlik Tasarımcısı](/visualstudio/workflow-designer/transition-activity-designer)
