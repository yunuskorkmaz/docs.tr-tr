---
title: 'Nasıl yapılır: İş Akışı Çalıştırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f814ff82-fe2b-4614-aebb-b768c3e61179
ms.openlocfilehash: c47e1ba89179b38055244c01507318836c899fda
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65637515"
---
# <a name="how-to-run-a-workflow"></a>Nasıl yapılır: İş Akışı Çalıştırma
Bu konu, Windows Workflow Foundation çalışmaya başlama Öğreticisi devamı niteliğindedir ve bir iş akışı ana bilgisayarı oluşturun ve önceki tanımlanan iş akışı çalıştırma anlatılmaktadır [nasıl yapılır: Bir iş akışı oluşturmak](how-to-create-a-workflow.md) konu.

> [!NOTE]
>  Önceki konularıyla ilgili her konuda Başlarken Öğreticisi bağlıdır. Önce tamamlamanız için bu konuyu tamamlamak için [nasıl yapılır: Bir etkinlik oluşturursunuz](how-to-create-an-activity.md) ve [nasıl yapılır: Bir iş akışı oluşturmak](how-to-create-a-workflow.md).

> [!NOTE]
>  Öğreticinin tamamlanmış bir sürümünü indirmek için bkz [Windows Workflow Foundation (WF45) - başlangıç Öğreticisi](https://go.microsoft.com/fwlink/?LinkID=248976).  
  
### <a name="to-create-the-workflow-host-project"></a>İş akışı ana projeyi oluşturmak için  
  
1. Çözüm önceki açın [nasıl yapılır: Bir etkinlik oluşturursunuz](how-to-create-an-activity.md) Visual Studio 2012 kullanarak konu.  
  
2. Sağ **WF45GettingStartedTutorial** çözümde **Çözüm Gezgini** seçip **Ekle**, **yeni proje**.  
  
    > [!TIP]
    >  Varsa **Çözüm Gezgini** penceresi görüntülenmiyorsa, seçin **Çözüm Gezgini** gelen **görünümü** menüsü.

3. İçinde **yüklü** düğümünü **Visual C#**, **iş akışı** (veya **Visual Basic**, **iş akışı**).

    > [!NOTE]
    >  Hangi programlama diline bağlı olarak, Visual Studio'da birincil dili olarak yapılandırılmış **Visual C#** veya **Visual Basic** düğümü altında olabilir **diğer diller** düğümünde **yüklü** düğümü.

     Emin **.NET Framework 4.5** .NET Framework sürüm aşağı açılan listeden seçilen. Seçin **iş akışı konsol uygulaması** gelen **iş akışı** listesi. Tür `NumberGuessWorkflowHost` içine **adı** kutusuna ve tıklatın **Tamam**. Bu destek barındırma temel iş akışı ile bir başlangıç akışı uygulaması oluşturur. Bu temel barındırma kodu değiştirilebilir ve iş akışı uygulamayı çalıştırmak için kullanılır.

4. Yeni eklenen sağ **NumberGuessWorkflowHost** projesi **Çözüm Gezgini** seçip **Başvuru Ekle**. Seçin **çözüm** gelen **Başvuru Ekle** listesinde, yanında onay **NumberGuessWorkflowActivities**ve ardından **Tamam** .

5. Sağ **Workflow1.xaml** içinde **Çözüm Gezgini** ve **Sil**. Tıklayın **Tamam** onaylamak için.

### <a name="to-modify-the-workflow-hosting-code"></a>İş akışı barındırma kodunu değiştirmek için

1. Çift **Program.cs** veya **Module1.vb** içinde **Çözüm Gezgini** seçerek kodu görüntüleyin.

    > [!TIP]
    >  Varsa **Çözüm Gezgini** penceresi görüntülenmiyorsa, seçin **Çözüm Gezgini** gelen **görünümü** menüsü.

     Bu proje kullanılarak oluşturulduğundan **iş akışı konsol uygulaması** şablon **Program.cs** veya **Module1.vb** aşağıdaki temel iş akışı barındırma içerir kodu.

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

     Bu barındırma kodu kullanan oluşturulan <xref:System.Activities.WorkflowInvoker>. <xref:System.Activities.WorkflowInvoker> bir yöntem çağrısının olan ve kalıcılığı kullanmayan yalnızca iş akışları için kullanılabilir gibi bir iş akışı çalıştırmak için basit bir yol sağlar. <xref:System.Activities.WorkflowApplication> yaşam döngüsü olayları, yürütme denetimi, yer imi sürdürme ve Kalıcılık bildirimi içeren iş akışlarını yürütmek için daha zengin bir model sağlar. Bu örnekte yer işaretleri ve <xref:System.Activities.WorkflowApplication> iş akışı barındırma için kullanılır. Aşağıdaki `using` veya **içeri aktarmalar** en üstündeki deyimi **Program.cs** veya **Module1.vb** varolan aşağıda **kullanarak** veya **içeri aktarmalar** deyimleri.

    ```vb
    Imports NumberGuessWorkflowActivities
    Imports System.Threading
    ```

    ```csharp
    using NumberGuessWorkflowActivities;
    using System.Threading;
    ```

     Kullanan kod satırlarını değiştirin <xref:System.Activities.WorkflowInvoker> aşağıdaki temel ile <xref:System.Activities.WorkflowApplication> kod barındırma. Bu örnek kodu barındıran barındırma ve bir iş akışı çağırırken temel adımları gösterir, ancak henüz başarıyla bu konudan iş akışı çalıştırmak için işlevsellik içermiyor. Aşağıdaki adımlarda, bu temel kod değiştirilir ve uygulama tamamlanana kadar ek özellikler eklenir.

    > [!NOTE]
    >  Lütfen değiştirin `Workflow1` ile bu örneklerde `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, veya `StateMachineNumberGuessWorkflow`önceki tamamlanan iş akışı bağlı olarak [nasıl yapılır: Bir iş akışı oluşturmak](how-to-create-a-workflow.md) adım. Değil değiştirirseniz `Workflow1` deneyin ve derlediğinizde veya iş akışı çalıştırma derleme hataları alırsınız.

     [!code-csharp[CFX_WF_GettingStarted#4](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#4)]
     [!code-vb[CFX_WF_GettingStarted#4](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#4)]

     Bu kod oluşturur bir <xref:System.Activities.WorkflowApplication>, üç iş akışı yaşam döngüsü olayları kaydeder, iş akışı için bir çağrı ile başlar <xref:System.Activities.WorkflowApplication.Run%2A>ve sonra tamamlamak iş akışı için bekler. İş akışı tamamlandığında <xref:System.Threading.AutoResetEvent> kümesi ve ana bilgisayar uygulaması tamamlar.

### <a name="to-set-input-arguments-of-a-workflow"></a>Bir iş akışının giriş bağımsız değişkenleri ayarlamak için

1. Üstüne aşağıdaki ifadeyi ekleyin **Program.cs** veya **Module1.vb** varolan aşağıda `using` veya `Imports` deyimleri.

     [!code-csharp[CFX_WF_GettingStarted#5](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#5)]
     [!code-vb[CFX_WF_GettingStarted#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#5)]

2. Yeni oluşturan kod satırına değiştirin <xref:System.Activities.WorkflowApplication> aşağıdaki kodla oluşturur ve oluşturulduğu sırada iş akışına parametreleri sözlüğü geçirir.

    > [!NOTE]
    >  Lütfen değiştirin `Workflow1` ile bu örneklerde `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, veya `StateMachineNumberGuessWorkflow`önceki tamamlanan iş akışı bağlı olarak [nasıl yapılır: Bir iş akışı oluşturmak](how-to-create-a-workflow.md) adım. Değil değiştirirseniz `Workflow1` deneyin ve derlediğinizde veya iş akışı çalıştırma derleme hataları alırsınız.

     [!code-csharp[CFX_WF_GettingStarted#6](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]

     Bu sözlüğün bir anahtar ile bir öğe içeren `MaxNumber`. İş akışının Kök etkinlik bağımsız değişkenler girişi için giriş sözlüğündeki anahtarları karşılık gelir. `MaxNumber` İş akışı tarafından rastgele oluşturulan sayı için üst sınır belirlemek için kullanılır.

### <a name="to-retrieve-output-arguments-of-a-workflow"></a>Bir iş akışının çıkış değişkenlerini almak için

1. Değiştirme <xref:System.Activities.WorkflowApplication.Completed%2A> almak ve iş akışı tarafından kullanılan kapatır sayısını görüntülemek için işleyici.

     [!code-csharp[CFX_WF_GettingStarted#7](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#7)]
     [!code-vb[CFX_WF_GettingStarted#7](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#7)]

### <a name="to-resume-a-bookmark"></a>Bir yer işareti sürdürmek için

1. Üstüne aşağıdaki kodu ekleyin `Main` varolan sonra yöntemi <xref:System.Threading.AutoResetEvent> bildirimi.

     [!code-csharp[CFX_WF_GettingStarted#8](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#8)]
     [!code-vb[CFX_WF_GettingStarted#8](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#8)]

2. Aşağıdaki <xref:System.Activities.WorkflowApplication.Idle%2A> işleyici hemen altındaki mevcut üç iş akışı yaşam döngüsü işleyiciler `Main`.

     [!code-csharp[CFX_WF_GettingStarted#9](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#9)]
     [!code-vb[CFX_WF_GettingStarted#9](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#9)]

     Bu işleyici iş akışı için bir sonraki tahmin, bekleyen boşta olur her zaman çağrılır ve `idleAction` <xref:System.Threading.AutoResetEvent> ayarlanır. Sonraki adımda kod `idleEvent` ve `syncEvent` iş akışı için sonraki tahmin bekliyor veya tamamlandığında belirlemek için.

    > [!NOTE]
    >  Bu örnekte, ana bilgisayar uygulaması otomatik sıfırlama olayları kullanan <xref:System.Activities.WorkflowApplication.Completed%2A> ve <xref:System.Activities.WorkflowApplication.Idle%2A> ana uygulama iş akışı ilerlemesini ile eşitlemek için işleyiciler. Blok ve iş akışının bir yer işareti devam etmeden önce boşta beklemesi gerekli değildir, ancak bu örnekte ana iş akışının tamamını olup veya kullanarakdahafazlakullanıcıgirdisiolupbekliyorolduğunubilmesiiçineşitlemeolaylarıgereklidir<xref:System.Activities.Bookmark>. Daha fazla bilgi için [yer işaretleri](bookmarks.md).

3. Çağrısını kaldırın `WaitOne`, sürdürme ve kullanıcı girişleri toplamak için kodu değiştirin <xref:System.Activities.Bookmark>.

     Aşağıdaki kod satırını kaldırın.

     [!code-csharp[CFX_WF_GettingStarted#10](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#10)]
     [!code-vb[CFX_WF_GettingStarted#10](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#10)]

     Aşağıdaki örnek ile değiştirin.

     [!code-csharp[CFX_WF_GettingStarted#11](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#11)]
     [!code-vb[CFX_WF_GettingStarted#11](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#11)]

## <a name="BKMK_ToRunTheApplication"></a> Derleme ve uygulamayı çalıştırmak için

1. Sağ **NumberGuessWorkflowHost** içinde **Çözüm Gezgini** seçip **başlangıç projesi olarak ayarla**.

2. Derleme ve uygulamayı çalıştırmak için CTRL + F5 tuşlarına basın. Mümkün olduğunca az kapatır, sayısını tahmin etmeye çalışır.

     İş akışının diğer stilleri biri ile bir uygulamayı denemek için değiştirin `Workflow1` oluşturan kodu içinde <xref:System.Activities.WorkflowApplication> ile `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, veya `StateMachineNumberGuessWorkflow`istediğiniz hangi iş akışı stili bağlı olarak.

     [!code-csharp[CFX_WF_GettingStarted#6](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]

     Kalıcılık bir iş akışı uygulamaya ekleme hakkında yönergeler görmek için bir sonraki konu [nasıl yapılır: Oluşturma ve uzun süre çalışan iş akışı](how-to-create-and-run-a-long-running-workflow.md).

## <a name="example"></a>Örnek
 Aşağıdaki örnek için tam kodu, `Main` yöntemi.

> [!NOTE]
>  Lütfen değiştirin `Workflow1` ile bu örneklerde `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, veya `StateMachineNumberGuessWorkflow`önceki tamamlanan iş akışı bağlı olarak [nasıl yapılır: Bir iş akışı oluşturmak](how-to-create-a-workflow.md) adım. Değil değiştirirseniz `Workflow1` deneyin ve derlediğinizde veya iş akışı çalıştırma derleme hataları alırsınız.

 [!code-csharp[CFX_WF_GettingStarted#12](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#12)]
 [!code-vb[CFX_WF_GettingStarted#12](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#12)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Activities.WorkflowApplication>
- <xref:System.Activities.Bookmark>
- [Windows Workflow Foundation Programlama](programming.md)
- [Başlangıç Öğreticisi](getting-started-tutorial.md)
- [Nasıl yapılır: Bir iş akışı oluşturma](how-to-create-a-workflow.md)
- [Nasıl yapılır: Oluşturma ve uzun süre çalışan iş akışı](how-to-create-and-run-a-long-running-workflow.md)
- [Bir iş akışında giriş bekleme](waiting-for-input-in-a-workflow.md)
- [İş Akışları Barındırma](hosting-workflows.md)
