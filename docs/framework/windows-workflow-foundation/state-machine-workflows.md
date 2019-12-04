---
title: Durum Makinesi İş Akışları
ms.date: 03/30/2017
ms.assetid: 344caacd-bf3b-4716-bd5a-eca74fc5a61d
ms.openlocfilehash: e27b9bdc43ec13e90325f5e709c5c97758daa58c
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74710905"
---
# <a name="state-machine-workflows"></a>Durum Makinesi İş Akışları
Durum makinesi, program geliştirmeye yönelik iyi bilinen bir paradigma sahiptir. <xref:System.Activities.Statements.StateMachine> etkinliği, <xref:System.Activities.Statements.State>, <xref:System.Activities.Statements.Transition>ve diğer etkinliklerle birlikte durum makinesi iş akışı programları oluşturmak için kullanılabilir. Bu konuda, durum makinesi iş akışları oluşturmaya genel bakış sunulmaktadır.  
  
## <a name="state-machine-workflow-overview"></a>Durum makinesi Iş akışına genel bakış  
 Durum makinesi iş akışları, iş akışınızı olay odaklı şekilde modellenebilen bir modelleme stili sağlar. Bir <xref:System.Activities.Statements.StateMachine> etkinlik, durum makinesinin mantığını oluşturan durumlar ve geçişleri içerir ve bir etkinliğin kullanılabileceği her yerde kullanılabilir. Durum makinesi çalışma zamanında birkaç sınıf vardır:  
  
- <xref:System.Activities.Statements.StateMachine>  
  
- <xref:System.Activities.Statements.State>  
  
- <xref:System.Activities.Statements.Transition>  
  
 Bir durum makinesi iş akışı oluşturmak için, durumlar <xref:System.Activities.Statements.StateMachine> etkinliğe eklenir ve geçişler, durumlar arasındaki akışı denetler. Aşağıdaki ekran görüntüsünde, kullanmaya başlama [öğreticisinde](getting-started-tutorial.md) [nasıl yapılır: durum makinesi iş akışı oluşturma](how-to-create-a-state-machine-workflow.md), üç durumlu ve üç geçiş içeren bir durum makinesi iş akışını gösterir. **Başlatma hedefi** başlangıç durumudur ve iş akışındaki ilk durumu temsil eder. Bu, **Başlangıç** düğümünden bu satıra satır başına atanır. İş akışındaki son durum **FinalState**olarak adlandırılır ve iş akışının tamamlandığı noktayı temsil eder.  
  
 ![Tamamlanan durum makinesi iş akışını gösteren çizim.](./media/state-machine-workflows/complete-state-machine-workflow.jpg)  
  
 Bir durum makinesi iş akışı bir ve yalnızca bir başlangıç durumuna ve en az bir son duruma sahip olmalıdır. Son durum olmayan her durum en az bir geçişe sahip olmalıdır. Aşağıdaki bölümlerde durum ve geçişlerin oluşturulması ve yapılandırılması ele alınmaktadır.  
  
## <a name="creating-and-configuring-states"></a>Durum oluşturma ve yapılandırma  
 <xref:System.Activities.Statements.State>, bir durum makinesinin içinde olabilen bir durumu temsil eder. Bir iş akışına <xref:System.Activities.Statements.State> eklemek için, **durum** etkinlik tasarımcısını **araç kutusunun** **durum makinesi** bölümünden sürükleyin ve Windows iş akışı Tasarımcısı yüzeyinde bir <xref:System.Activities.Statements.StateMachine> etkinliğine bırakın.  
  
 ![Araç kutusunun durum makinesi bölümünün ekran görüntüsü.](./media/state-machine-workflows/state-machine-section-toolbox.jpg)  
  
 Durumu **Başlangıç durumu**olarak yapılandırmak için, duruma sağ tıklayın ve **Başlangıç durumu olarak ayarla**' yı seçin. Ayrıca, geçerli bir başlangıç durumu yoksa, iş akışının en üstündeki **Başlangıç** düğümünden istenen duruma kadar bir çizgi sürüklenerek ilk durum belirlenebilir. Bir <xref:System.Activities.Statements.StateMachine> etkinliği iş akışı tasarımcısına bırakıldığında, **State1**adlı bir başlangıç durumuyla önceden yapılandırılmıştır. Bir durum makinesi iş akışı bir ve yalnızca bir başlangıç durumuna sahip olmalıdır.  
  
 Durum makinesindeki sonlandırma durumunu temsil eden bir durum, son durum olarak adlandırılır. Son durum, <xref:System.Activities.Statements.State.IsFinal%2A> özelliği `true`olarak ayarlanan, <xref:System.Activities.Statements.State.Exit%2A> etkinliği olmayan ve bundan kaynaklı hiçbir geçiş olmayan bir durumdur. Bir iş akışına son durum eklemek için, **araç kutusunun** **durum makinesi** bölümünden bir **sonlandırmadurumu** etkinlik tasarımcısını sürükleyin ve Windows iş akışı Tasarımcısı yüzeyinde <xref:System.Activities.Statements.StateMachine> bir etkinliğe bırakın. Bir durum makinesi iş akışında en az bir son durum olmalıdır.  
  
### <a name="configuring-entry-and-exit-actions"></a>Giriş ve çıkış eylemlerini yapılandırma  
 Bir durum <xref:System.Activities.Statements.State.Entry%2A> ve <xref:System.Activities.Statements.State.Exit%2A> eylemine sahip olabilir. (Son durum olarak yapılandırılan bir durum yalnızca bir giriş eylemine sahip olabilir). Bir iş akışı örneği bir durum girdiğinde, giriş eyleminde herhangi bir etkinlik yürütülür. Giriş eylemi tamamlandığında, durum geçişleri için Tetikleyiciler zamanlanır. Başka bir duruma geçiş onaylanırsa, durum aynı duruma geri geçirse bile, çıkış Eylemdeki etkinlikler yürütülür. Çıkış eylemi tamamlandıktan sonra, geçiş eyleminin içindeki etkinlikler yürütülür ve ardından yeni durum ' a geçirilir ve giriş eylemleri zamanlanır.  
  
> [!NOTE]
> Bir durum makinesi iş akışında hata ayıklarken, kesme noktaları kök durum makinesi etkinliğine ve durum makinesi iş akışı içindeki durumlara yerleştirilebilecek. Kesme noktaları doğrudan geçişlere yerleştirilmeyebilir, ancak durumlar ve geçişler içindeki etkinliklere dahil edilebilir.  
  
## <a name="creating-and-configuring-transitions"></a>Geçişleri oluşturma ve yapılandırma  
 Herhangi bir geçişi olmayan son durum dışında, tüm durumlar en az bir geçişe sahip olmalıdır. Bir durum makine iş akışına bir durum eklendikten sonra geçişler eklenebilir veya durum bırakılmakta olduğundan oluşturulabilir.  
  
 Bir adımda <xref:System.Activities.Statements.State> eklemek ve bir geçiş oluşturmak için, **araç kutusunun** **durum makinesi** bölümünden bir **durum** etkinliği sürükleyin ve iş akışı tasarımcısında başka bir durum üzerine gelin. Sürüklenen <xref:System.Activities.Statements.State> başka bir <xref:System.Activities.Statements.State>üzerinde olduğunda, diğer <xref:System.Activities.Statements.State>etrafında dört üçgen görünür. <xref:System.Activities.Statements.State> dört üçgenden birine bırakıldığında, bu durum makineye eklenir ve kaynak <xref:System.Activities.Statements.State>, bırakılan hedef <xref:System.Activities.Statements.State>bir geçiş oluşturulur. Daha fazla bilgi için bkz. [geçiş etkinlik Tasarımcısı](/visualstudio/workflow-designer/transition-activity-designer).  
  
 Bir durum eklendikten sonra bir geçiş oluşturmak için iki seçenek vardır. İlk seçenek, durumu iş akışı Tasarımcısı yüzeyinden sürüklemektir ve var olan bir durum üzerine getirip bırakma noktalarından birine bırakabilir. Bu, önceki bölümde açıklanan yönteme çok benzer. Ayrıca, fare işaretçisini istenen kaynak durumunun üzerine getirip bir çizgiyi istediğiniz hedef durumuna sürükleyebilirsiniz.  
  
> [!NOTE]
> Bir durum makinesindeki tek bir durum, iş akışı Tasarımcısı kullanılarak oluşturulan en fazla 76 geçişine sahip olabilir. Tasarımcı dışında oluşturulan iş akışları için bir durum geçişleri sınırı yalnızca sistem kaynaklarıyla sınırlıdır.  
  
 Bir geçişte <xref:System.Activities.Statements.Transition.Trigger%2A>, bir <xref:System.Activities.Statements.Transition.Condition%2A>ve bir <xref:System.Activities.Statements.Transition.Action%2A>olabilir. Geçişin kaynak durumunun <xref:System.Activities.Statements.State.Entry%2A> eylemi tamamlandığında bir geçişin <xref:System.Activities.Statements.Transition.Trigger%2A> zamanlanır. Genellikle <xref:System.Activities.Statements.Transition.Trigger%2A>, bazı olay türlerinin gerçekleşmesini bekleyen, ancak herhangi bir etkinlik veya hiç etkinlik olmadığı için bir etkinliktir. <xref:System.Activities.Statements.Transition.Trigger%2A> etkinliği tamamlandıktan sonra, varsa <xref:System.Activities.Statements.Transition.Condition%2A>değerlendirilir. <xref:System.Activities.Statements.Transition.Trigger%2A> etkinlik yoksa, <xref:System.Activities.Statements.Transition.Condition%2A> anında değerlendirilir. Koşul `false`olarak değerlendirilirse, geçiş iptal edilir ve durumdan gelen tüm geçişler için <xref:System.Activities.Statements.Transition.Trigger%2A> etkinliği yeniden çizelgelenir. Geçerli geçiş ile aynı kaynak durumunu paylaşan başka geçişler varsa, bu <xref:System.Activities.Statements.Transition.Trigger%2A> eylemler iptal edilir ve ayrıca yeniden çizelgelenir. <xref:System.Activities.Statements.Transition.Condition%2A> `true`değerlendirilirse veya bir koşul yoksa, kaynak durumunun <xref:System.Activities.Statements.State.Exit%2A> eylemi yürütülür ve sonra geçişin <xref:System.Activities.Statements.Transition.Action%2A> yürütülür. <xref:System.Activities.Statements.Transition.Action%2A> tamamlandığında, Denetim **hedef** durumuna geçer  
  
 Ortak bir tetikleyiciyi paylaşan geçişler, paylaşılan tetikleyici geçişleri olarak bilinir. Paylaşılan tetikleyici geçişleri grubundaki her geçişte aynı tetikleyici vardır, ancak benzersiz bir <xref:System.Activities.Statements.Transition.Condition%2A> ve eylem vardır. Bir geçişe ek eylemler eklemek ve paylaşılan bir geçiş oluşturmak için, istenen geçişin başlangıcını belirten daireye tıklayın ve istediğiniz duruma sürükleyin. Yeni geçiş, başlangıç geçişi olarak aynı tetikleyiciyi paylaşır, ancak benzersiz bir koşula ve eyleme sahip olur. Paylaşılan geçişler, geçiş Tasarımcısı ' nın altında **Paylaşılan tetikleyici geçişi ekle** ' ye tıklayarak geçiş Tasarımcısı içinden de oluşturulabilir ve sonra, bağlantı açılan listesinden, **kullanılabilir durumlar** ' da istenen hedef durumu seçebilirsiniz.  
  
> [!NOTE]
> Bir geçişin <xref:System.Activities.Statements.Transition.Condition%2A>, `False` (veya paylaşılan bir tetikleyici geçişinin tüm koşullarına `False`) değerlendirilirse, geçişin gerçekleşmeyeceğini ve durumdan tüm geçişlerin tüm tetikleyicilerinin yeniden planlanacağını unutmayın.  
  
 Durum makinesi iş akışları oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: durum makinesi Iş akışı](how-to-create-a-state-machine-workflow.md), [StateMachine etkinlik Tasarımcısı](/visualstudio/workflow-designer/statemachine-activity-designer), [durum etkinlik Tasarımcısı](/visualstudio/workflow-designer/state-activity-designer), [FinalState etkinlik Tasarımcısı](/visualstudio/workflow-designer/finalstate-activity-designer)ve [geçiş etkinlik Tasarımcısı](/visualstudio/workflow-designer/transition-activity-designer).  
  
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
  
 Tetikleyicinin  
 Bir geçişin oluşmasına neden olan tetikleme etkinliği.  
  
 Koşul  
 Geçişin tamamlanmasını sağlamak için tetikleyici oluştuktan sonra `true` değerlendirilmesi gereken bir kısıtlama.  
  
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

- [Nasıl yapılır: Durum Makinesi İş Akışı Oluşturma](how-to-create-a-state-machine-workflow.md)
- [StateMachine Etkinlik Tasarımcısı](/visualstudio/workflow-designer/statemachine-activity-designer)
- [State Etkinlik Tasarımcısı](/visualstudio/workflow-designer/state-activity-designer)
- [FinalState Etkinlik Tasarımcısı](/visualstudio/workflow-designer/finalstate-activity-designer)
- [Transition Etkinlik Tasarımcısı](/visualstudio/workflow-designer/transition-activity-designer)
