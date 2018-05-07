---
title: 'Nasıl yapılır: bir iş akışını çalıştırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f814ff82-fe2b-4614-aebb-b768c3e61179
ms.openlocfilehash: 704527bde2ac6bf555d40db836baf938c0c5cd96
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-run-a-workflow"></a>Nasıl yapılır: bir iş akışını çalıştırma
Bu konu, Windows Workflow Foundation Başlarken Öğreticisi devamıdır ve bir iş akışı ana bilgisayarı oluşturmak ve önceki tanımlanan iş akışını çalıştırmak nasıl ele [nasıl yapılır: bir iş akışı oluşturmak](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) konu.  
  
> [!NOTE]
>  Başlarken Öğreticisi her bir konuda önceki konularda bağlıdır. Bu konunun ilk tamamlanmalıdır tamamlamak için [nasıl yapılır: bir etkinlik oluşturmak](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) ve [nasıl yapılır: bir iş akışı oluşturmak](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md).  
  
> [!NOTE]
>  Öğreticinin tamamlanmış bir sürümünü indirmek için bkz: [Windows Workflow Foundation (WF45) - başlangıç Öğreticisi](http://go.microsoft.com/fwlink/?LinkID=248976).  
  
### <a name="to-create-the-workflow-host-project"></a>İş akışı konak projesi oluşturmak için  
  
1.  Çözüm önceki açın [nasıl yapılır: bir etkinlik oluşturmak](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) kullanarak konu [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].  
  
2.  Sağ **WF45GettingStartedTutorial** çözümde **Çözüm Gezgini** seçip **Ekle**, **yeni proje**.  
  
    > [!TIP]
    >  Varsa **Çözüm Gezgini** penceresi görüntülenmez, seçin **Çözüm Gezgini** gelen **Görünüm** menüsü.  
  
3.  İçinde **yüklü** düğümü, select **Visual C#**, **iş akışı** (veya **Visual Basic**, **iş akışı**).  
  
    > [!NOTE]
    >  Visual Studio'da birincil dili olarak programlama dili bağlı olarak yapılandırılmış **Visual C#** veya **Visual Basic** düğümü altında olabilir **diğer diller** düğümünde **yüklü** düğümü.  
  
     Emin **.NET Framework 4.5** .NET Framework sürüm aşağı açılan listesinde seçilir. Seçin **iş akışı konsol uygulaması** gelen **iş akışı** listesi. Tür `NumberGuessWorkflowHost` içine **adı** kutusuna ve tıklatın **Tamam**. Bu destek barındırma temel iş akışı ile başlangıç iş akışı uygulaması oluşturur. Bu temel barındırma kodu değiştirilebilir ve iş akışı uygulamayı çalıştırmak için kullanılır.  
  
4.  Yeni eklenen sağ **NumberGuessWorkflowHost** proje **Çözüm Gezgini** seçip **Başvuru Ekle**. Seçin **çözüm** gelen **Başvuru Ekle** listesinde, yanındaki onay kutusunu işaretleyin **NumberGuessWorkflowActivities**ve ardından **Tamam** .  
  
5.  Sağ **Workflow1.xaml** içinde **Çözüm Gezgini** ve **silmek**. Tıklatın **Tamam** onaylamak için.  
  
### <a name="to-modify-the-workflow-hosting-code"></a>Kod barındırma iş akışını değiştirmek için  
  
1.  Çift **Program.cs** veya **Module1.vb** içinde **Çözüm Gezgini** kodunu görüntülemek için.  
  
    > [!TIP]
    >  Varsa **Çözüm Gezgini** penceresi görüntülenmez, seçin **Çözüm Gezgini** gelen **Görünüm** menüsü.  
  
     Bu proje kullanarak oluşturulduğundan **iş akışı konsol uygulaması** şablon **Program.cs** veya **Module1.vb** aşağıdaki temel iş akışı barındırma içerir kod.  
  
    ```vb  
    ' Create and cache the workflow definition  
    Activity workflow1 = new Workflow1()  
    WorkflowInvoker.Invoke(workflow1)  
    ```  
  
    ```csharp  
    // Create and cache the workflow definition  
    Activity workflow1 = new Workflow1();  
    WorkflowInvoker.Invoke(workflow1);  
    ```  
  
     Bu barındırma kodu kullandığı oluşturulan <xref:System.Activities.WorkflowInvoker>. <xref:System.Activities.WorkflowInvoker> yöntem çağrısı sırasında ve Kalıcılık kullanmayan yalnızca iş akışları için kullanılabilir gibi bir iş akışı çağırma için basit bir yol sağlar. <xref:System.Activities.WorkflowApplication> yaşam döngüsü olayları, yürütme denetimi, yer işareti sürdürme ve kalıcılığı bildirimi içeren iş akışlarını yürütmek için daha zengin bir modeli sağlar. Bu örnekte yer işaretleri kullanır ve <xref:System.Activities.WorkflowApplication> iş akışı barındırmak için kullanılır. Aşağıdakileri ekleyin `using` veya **içeri aktarmalar** deyimi en üstündeki **Program.cs** veya **Module1.vb** varolan aşağıda **kullanarak** veya **içeri aktarmalar** deyimleri.  
  
    ```vb  
    Imports NumberGuessWorkflowActivities  
    Imports System.Threading  
    ```  
  
    ```csharp  
    using NumberGuessWorkflowActivities;  
    using System.Threading;  
    ```  
  
     Kullanın kod satırlarını Değiştir <xref:System.Activities.WorkflowInvoker> aşağıdaki basic ile <xref:System.Activities.WorkflowApplication> kod barındırma. Bu örnek kodu barındırma barındırma ve bir iş akışı çağırma için temel adımlar gösterilmektedir, ancak henüz başarılı bir şekilde bu konudan iş akışını çalıştırmak için işlevsellik içermiyor. Aşağıdaki adımlarda bu temel kod değiştirilebilir ve uygulama işlemi tamamlanana kadar ek özellikler eklenir.  
  
    > [!NOTE]
    >  Lütfen değiştirin `Workflow1` ile bu örneklerde `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, veya `StateMachineNumberGuessWorkflow`önceki tamamlanan iş akışı bağlı olarak [nasıl yapılır: bir iş akışı oluşturmak](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) adım. Yerini varsa `Workflow1` deneyin ve yapı veya iş akışını çalıştırdığınızda derleme hataları alırsınız.  
  
     [!code-csharp[CFX_WF_GettingStarted#4](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#4)]
     [!code-vb[CFX_WF_GettingStarted#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#4)]  
  
     Bu kod oluşturur bir <xref:System.Activities.WorkflowApplication>, üç iş akışı yaşam döngüsü olayları kaydeder, iş akışı için bir çağrı ile başlayan <xref:System.Activities.WorkflowApplication.Run%2A>ve sonra tamamlamak iş akışı için bekler. İş akışı tamamlandığında <xref:System.Threading.AutoResetEvent> ayarlanır ve ana bilgisayar uygulaması tamamlar.  
  
### <a name="to-set-input-arguments-of-a-workflow"></a>Giriş bağımsız değişkenleri bir iş akışının ayarlamak için  
  
1.  En üstünde aşağıdaki deyimine **Program.cs** veya **Module1.vb** varolan aşağıda `using` veya `Imports` deyimleri.  
  
     [!code-csharp[CFX_WF_GettingStarted#5](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#5)]
     [!code-vb[CFX_WF_GettingStarted#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#5)]  
  
2.  Yeni oluşturulan kod satırı değiştirin <xref:System.Activities.WorkflowApplication> aşağıdaki kodla oluşturur ve oluşturulduğunda iş akışına parametreleri sözlüğü geçirir.  
  
    > [!NOTE]
    >  Lütfen değiştirin `Workflow1` ile bu örneklerde `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, veya `StateMachineNumberGuessWorkflow`önceki tamamlanan iş akışı bağlı olarak [nasıl yapılır: bir iş akışı oluşturmak](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) adım. Yerini varsa `Workflow1` deneyin ve yapı veya iş akışını çalıştırdığınızda derleme hataları alırsınız.  
  
     [!code-csharp[CFX_WF_GettingStarted#6](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]  
  
     Tek bir öğe anahtarı ile bu sözlük içeren `MaxNumber`. Giriş sözlüğündeki anahtarları bağımsız değişkenler iş akışı Kök etkinlik üzerinde giriş karşılık gelir. `MaxNumber` İş akışı tarafından rastgele oluşturulmuş sayısı için üst sınır belirlemek için kullanılır.  
  
### <a name="to-retrieve-output-arguments-of-a-workflow"></a>Bir iş akışının çıkış değişkenlerini almak için  
  
1.  Değiştirme <xref:System.Activities.WorkflowApplication.Completed%2A> almak ve iş akışı tarafından kullanılan kapatır sayısını görüntülemek için işleyici.  
  
     [!code-csharp[CFX_WF_GettingStarted#7](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#7)]
     [!code-vb[CFX_WF_GettingStarted#7](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#7)]  
  
### <a name="to-resume-a-bookmark"></a>Yer işareti sürdürmek için  
  
1.  En üstte aşağıdaki kodu ekleyin `Main` varolan sonra yöntemi <xref:System.Threading.AutoResetEvent> bildirimi.  
  
     [!code-csharp[CFX_WF_GettingStarted#8](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#8)]
     [!code-vb[CFX_WF_GettingStarted#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#8)]  
  
2.  Aşağıdakileri ekleyin <xref:System.Activities.WorkflowApplication.Idle%2A> varolan üç iş akışı yaşam döngüsü işleyiciler hemen altındaki işleyici `Main`.  
  
     [!code-csharp[CFX_WF_GettingStarted#9](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#9)]
     [!code-vb[CFX_WF_GettingStarted#9](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#9)]  
  
     İş akışı için sonraki tahmin, bekleyen boşta her zaman bu işleyici olarak adlandırılır ve `idleAction` <xref:System.Threading.AutoResetEvent> ayarlanır. Sonraki adımda kodu kullanan `idleEvent` ve `syncEvent` iş akışı için sonraki tahmin bekliyor veya tamamlandıktan belirlemek için.  
  
    > [!NOTE]
    >  Bu örnekte, ana bilgisayar uygulamasını otomatik sıfırlama olayları kullanan <xref:System.Activities.WorkflowApplication.Completed%2A> ve <xref:System.Activities.WorkflowApplication.Idle%2A> konak uygulama iş akışı ilerleme ile eşitlemek için işleyiciler. Engelleme ve boşta durumuna yer işareti devam etmeden önce iş akışı için beklemek gerekli değildir, ancak bu örnekte, iş akışını tam olup veya kullanarakdahafazlakullanıcıgirdisiolupbekliyorkonakbilmesiiçineşitlemeolaylarıgereklidir<xref:System.Activities.Bookmark>. Daha fazla bilgi için bkz: [yer işaretleri](../../../docs/framework/windows-workflow-foundation/bookmarks.md).  
  
3.  Çağrı kaldırmak `WaitOne`ve kullanıcı ve sürdürme giriş toplamak için kod ile değiştirin <xref:System.Activities.Bookmark>.  
  
     Aşağıdaki kod satırını kaldırın.  
  
     [!code-csharp[CFX_WF_GettingStarted#10](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#10)]
     [!code-vb[CFX_WF_GettingStarted#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#10)]  
  
     Aşağıdaki örnek ile değiştirin.  
  
     [!code-csharp[CFX_WF_GettingStarted#11](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#11)]
     [!code-vb[CFX_WF_GettingStarted#11](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#11)]  
  
##  <a name="BKMK_ToRunTheApplication"></a> Derleme ve uygulamayı çalıştırmak için  
  
1.  Sağ **NumberGuessWorkflowHost** içinde **Çözüm Gezgini** seçip **başlangıç projesi olarak ayarla**.  
  
2.  Derleme ve uygulamayı çalıştırmak için CTRL + F5 tuşuna basın. Mümkün olduğunca az tasarrufludur sayısını tahmin etmeye çalışın.  
  
     Diğer stilleri biri ile uygulama iş akışının denemek için değiştirme `Workflow1` oluşturan kodu <xref:System.Activities.WorkflowApplication> ile `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, veya `StateMachineNumberGuessWorkflow`istediğiniz hangi iş akışı stili bağlı olarak.  
  
     [!code-csharp[CFX_WF_GettingStarted#6](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]  
  
     Kalıcılığı bir iş akışı uygulamasına ekleme hakkında yönergeler görmek için sonraki konu [nasıl yapılır: oluşturun ve uzun çalışan iş akışını çalıştırma](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, için listeleme eksiksiz koddur `Main` yöntemi.  
  
> [!NOTE]
>  Lütfen değiştirin `Workflow1` ile bu örneklerde `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, veya `StateMachineNumberGuessWorkflow`önceki tamamlanan iş akışı bağlı olarak [nasıl yapılır: bir iş akışı oluşturmak](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) adım. Yerini varsa `Workflow1` deneyin ve yapı veya iş akışını çalıştırdığınızda derleme hataları alırsınız.  
  
 [!code-csharp[CFX_WF_GettingStarted#12](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#12)]
 [!code-vb[CFX_WF_GettingStarted#12](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#12)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Activities.WorkflowApplication>  
 <xref:System.Activities.Bookmark>  
 [Windows Workflow Foundation Programlama](../../../docs/framework/windows-workflow-foundation/programming.md)  
 [Başlangıç Öğreticisi](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [Nasıl yapılır: İş Akışı Oluşturma](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md)  
 [Nasıl yapılır: Uzun Süre Çalışan İş Akışı Oluşturma ve Çalıştırma](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md)  
 [Bir iş akışında giriş bekleme](../../../docs/framework/windows-workflow-foundation/waiting-for-input-in-a-workflow.md)  
 [İş Akışları Barındırma](../../../docs/framework/windows-workflow-foundation/hosting-workflows.md)
