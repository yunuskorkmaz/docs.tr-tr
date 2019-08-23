---
title: 'Nasıl yapılır: İş Akışı Çalıştırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f814ff82-fe2b-4614-aebb-b768c3e61179
ms.openlocfilehash: 3badda7afeb25b44b0de574f97452d05efe75bfc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962282"
---
# <a name="how-to-run-a-workflow"></a>Nasıl yapılır: İş Akışı Çalıştırma
Bu konu, başlangıç öğreticisini Windows Workflow Foundation ve bir iş akışı konağının nasıl oluşturulacağını ve önceki [nasıl yapılır: Bir iş akışı](how-to-create-a-workflow.md) konusu oluşturun.

> [!NOTE]
> Başlangıç öğreticisindeki her konu, önceki konulara bağlıdır. Bu konuyu tamamlayabilmeniz için öncelikle [şunları yapmanız gerekir: Etkinlik](how-to-create-an-activity.md) oluşturun ve [şunları yapın: Bir Iş akışı](how-to-create-a-workflow.md)oluşturun.

> [!NOTE]
> Öğreticinin tamamlanmış bir sürümünü indirmek için, bkz. [Windows Workflow Foundation (WF45)-Başlangıç Öğreticisi](https://go.microsoft.com/fwlink/?LinkID=248976).  
  
### <a name="to-create-the-workflow-host-project"></a>İş akışı konak projesi oluşturmak için  
  
1. Çözümü önceki [konumundan açın: Visual Studio 2012](how-to-create-an-activity.md) kullanarak bir etkinlik konusu oluşturun.  
  
2. **Çözüm Gezgini** 'de **WF45GettingStartedTutorial** çözümüne sağ tıklayın ve **Ekle**, **Yeni proje**' yi seçin.  
  
    > [!TIP]
    >  **Çözüm Gezgini** penceresi görüntülenmiyorsa, **Görünüm** menüsünden **Çözüm Gezgini** ' i seçin.

3. **Yüklü** düğümde, **C#görsel**, **iş akışı** (veya **Visual Basic**, **iş akışı**) öğesini seçin.

    > [!NOTE]
    > Visual Studio 'da birincil dil olarak yapılandırılmış programlama diline bağlı olarak, **Visual C#**  veya **Visual Basic** düğümü **yüklü** düğümdeki **diğer diller** düğümü altında olabilir.

     **.NET Framework 4,5** ' nin .NET Framework sürüm açılan listesinde seçildiğinden emin olun. İş akışı listesinden iş akışı **konsol uygulaması** ' nı seçin. Ad `NumberGuessWorkflowHost` kutusuna yazın ve **Tamam**' a tıklayın. Bu, temel iş akışı barındırma desteğiyle bir başlatıcı iş akışı uygulaması oluşturur. Bu temel barındırma kodu değiştirilir ve iş akışı uygulamasını çalıştırmak için kullanılır.

4. **Çözüm Gezgini** ' de yeni eklenen **Numberguessworkflowwhost** projesine sağ tıklayın ve **Başvuru Ekle**' yi seçin. **Başvuru Ekle** listesinden **çözüm** ' i seçin, **NumberGuessWorkflowActivities**yanındaki onay kutusunu işaretleyin ve ardından **Tamam**' a tıklayın.

5. **Çözüm Gezgini** 'de **Workflow1. xaml** öğesine sağ tıklayın ve **Sil**' i seçin. Onaylamak için **Tamam** ' ı tıklatın.

### <a name="to-modify-the-workflow-hosting-code"></a>İş akışı barındırma kodunu değiştirmek için

1. Kodu göstermek için **Çözüm Gezgini** 'de **program.cs** veya **Module1. vb** öğesine çift tıklayın.

    > [!TIP]
    >  **Çözüm Gezgini** penceresi görüntülenmiyorsa, **Görünüm** menüsünden **Çözüm Gezgini** ' i seçin.

     Bu proje **Iş akışı konsol uygulaması** şablonu kullanılarak oluşturulduğundan, **program.cs** veya **Module1. vb** , aşağıdaki temel iş akışı barındırma kodunu içerir.

    ```vb
    ' Create and cache the workflow definition.
    Dim workflow1 As Activity = New Workflow1()
    WorkflowInvoker.Invoke(workflow1)
    ```

    ```csharp
    // Create and cache the workflow definition.
    Activity workflow1 = new Workflow1();
    WorkflowInvoker.Invoke(workflow1);
    ```

     Oluşturulan bu barındırma kodu kullanılır <xref:System.Activities.WorkflowInvoker>. <xref:System.Activities.WorkflowInvoker>bir iş akışını Yöntem çağrısı gibi çağırmak için basit bir yol sağlar ve yalnızca kalıcılığı kullanmayan iş akışları için kullanılabilir. <xref:System.Activities.WorkflowApplication>yaşam döngüsü olaylarının, yürütme denetiminin, yer işaretinin sürdürme ve kalıcılığın bildirimini içeren iş akışlarını yürütmek için daha zengin bir model sağlar. Bu örnek, yer işaretlerini <xref:System.Activities.WorkflowApplication> kullanır ve iş akışını barındırmak için kullanılır. Var `using` olan **using** veya **Imports** deyimlerinin altındaki **program.cs** veya **Module1. vb** üst kısmına aşağıdaki veya **Imports** deyimini ekleyin.

    ```vb
    Imports NumberGuessWorkflowActivities
    Imports System.Threading
    ```

    ```csharp
    using NumberGuessWorkflowActivities;
    using System.Threading;
    ```

     Aşağıdaki temel <xref:System.Activities.WorkflowInvoker> <xref:System.Activities.WorkflowApplication> barındırma koduyla kullanılan kod satırlarını değiştirin. Bu örnek barındırma kodu, bir iş akışını barındırmak ve çağırmak için temel adımları gösterir, ancak henüz bu konudan iş akışını başarıyla çalıştırmaya yönelik işlevselliği içermez. Aşağıdaki adımlarda, bu temel kod değiştirilir ve uygulama tamamlanana kadar ek özellikler eklenir.

    > [!NOTE]
    > Lütfen bu `Workflow1` örneklerde, önceki `FlowchartNumberGuessWorkflow` `StateMachineNumberGuessWorkflow` `SequentialNumberGuessWorkflow` adımdatamamladığınızişakışınabağlıolarak,[veya ile değiştirin: Bir iş akışı](how-to-create-a-workflow.md) adımı oluşturun. ' Yi değiştirip `Workflow1` iş akışını oluşturup oluştururken veya çalıştırdığınızda yapı hataları alırsınız.

     [!code-csharp[CFX_WF_GettingStarted#4](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#4)]
     [!code-vb[CFX_WF_GettingStarted#4](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#4)]

     Bu kod bir <xref:System.Activities.WorkflowApplication>oluşturur, üç iş akışı yaşam döngüsü olayına abone olur, bir <xref:System.Activities.WorkflowApplication.Run%2A>çağrısıyla iş akışını başlatır ve sonra iş akışının tamamlanmasını bekler. İş akışı tamamlandığında, <xref:System.Threading.AutoResetEvent> ayarlanır ve ana bilgisayar uygulaması tamamlanır.

### <a name="to-set-input-arguments-of-a-workflow"></a>Bir iş akışının giriş bağımsız değişkenlerini ayarlamak için

1. Aşağıdaki deyimi, var olan `using` or `Imports` deyimlerinin altındaki **program.cs** veya **Module1. vb** öğesinin üstüne ekleyin.

     [!code-csharp[CFX_WF_GettingStarted#5](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#5)]
     [!code-vb[CFX_WF_GettingStarted#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#5)]

2. Yeni <xref:System.Activities.WorkflowApplication> oluşturan kod satırını, oluşturulduğunda iş akışına bir parametre sözlüğü oluşturup ileten aşağıdaki kodla değiştirin.

    > [!NOTE]
    > Lütfen bu `Workflow1` örneklerde, önceki `FlowchartNumberGuessWorkflow` `StateMachineNumberGuessWorkflow` `SequentialNumberGuessWorkflow` adımdatamamladığınızişakışınabağlıolarak,[veya ile değiştirin: Bir iş akışı](how-to-create-a-workflow.md) adımı oluşturun. ' Yi değiştirip `Workflow1` iş akışını oluşturup oluştururken veya çalıştırdığınızda yapı hataları alırsınız.

     [!code-csharp[CFX_WF_GettingStarted#6](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]

     Bu sözlük, `MaxNumber`anahtarı olan bir öğesi içerir. Giriş sözlüğündeki anahtarlar, iş akışının kök etkinliğinin giriş bağımsız değişkenlerine karşılık gelir. `MaxNumber`, rastgele oluşturulan sayı için üst sınırı belirlemede iş akışı tarafından kullanılır.

### <a name="to-retrieve-output-arguments-of-a-workflow"></a>Bir iş akışının çıkış bağımsız değişkenlerini almak için

1. <xref:System.Activities.WorkflowApplication.Completed%2A> İşleyiciyi, iş akışı tarafından kullanılan dönüşler sayısını almak ve görüntüleyecek şekilde değiştirin.

     [!code-csharp[CFX_WF_GettingStarted#7](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#7)]
     [!code-vb[CFX_WF_GettingStarted#7](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#7)]

### <a name="to-resume-a-bookmark"></a>Bir yer işaretini sürdürülmesi için

1. Aşağıdaki kodu, mevcut `Main` <xref:System.Threading.AutoResetEvent> bildiriminden hemen sonra yönteminin en üstüne ekleyin.

     [!code-csharp[CFX_WF_GettingStarted#8](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#8)]
     [!code-vb[CFX_WF_GettingStarted#8](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#8)]

2. ' De <xref:System.Activities.WorkflowApplication.Idle%2A> `Main`var olan üç iş akışı yaşam döngüsü işleyicisinin hemen altına aşağıdaki işleyiciyi ekleyin.

     [!code-csharp[CFX_WF_GettingStarted#9](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#9)]
     [!code-vb[CFX_WF_GettingStarted#9](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#9)]

     Her iş akışı bir sonraki tahmin için bekleme durumunda olduğunda, bu işleyici çağrılır ve `idleAction` <xref:System.Threading.AutoResetEvent> ayarlanır. Aşağıdaki adımdaki kod, iş akışının bir `idleEvent` sonraki `syncEvent` tahmin için mi beklediğini yoksa tamamlanıp tamamlanmadığını mı öğrenmek için ve kullanır.

    > [!NOTE]
    > Bu örnekte, ana bilgisayar uygulaması, <xref:System.Activities.WorkflowApplication.Completed%2A> ve <xref:System.Activities.WorkflowApplication.Idle%2A> işleyicilerinde otomatik sıfırlama olaylarını kullanarak konak uygulamasını iş akışının ilerlemesiyle eşitler. Blok ve iş akışının bir yer işareti devam etmeden önce boşta beklemesi gerekli değildir, ancak bu örnekte ana iş akışının tamamını olup veya kullanarakdahafazlakullanıcıgirdisiolupbekliyorolduğunubilmesiiçineşitlemeolaylarıgereklidir<xref:System.Activities.Bookmark>. Daha fazla bilgi için bkz. [yer işaretleri](bookmarks.md).

3. `WaitOne`' A çağrıyı kaldırın ve kullanıcıdan giriş toplamak için kodu kodla değiştirin ve ' ı <xref:System.Activities.Bookmark>sürdürülemez.

     Aşağıdaki kod satırını kaldırın.

     [!code-csharp[CFX_WF_GettingStarted#10](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#10)]
     [!code-vb[CFX_WF_GettingStarted#10](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#10)]

     Aşağıdaki örnekle değiştirin.

     [!code-csharp[CFX_WF_GettingStarted#11](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#11)]
     [!code-vb[CFX_WF_GettingStarted#11](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#11)]

## <a name="BKMK_ToRunTheApplication"></a>Uygulamayı derlemek ve çalıştırmak için

1. **Çözüm Gezgini** Için **Numberguessworkflowwhost** öğesine sağ tıklayın ve **Başlangıç projesi olarak ayarla**' yı seçin.

2. Uygulamayı derlemek ve çalıştırmak için CTRL + F5 tuşlarına basın. Sayıyı olabildiğince az sürede tahmin etmeye çalışın.

     Uygulamayı diğer iş akışı stillerinden biriyle denemek için `Workflow1` , veya <xref:System.Activities.WorkflowApplication> ile `FlowchartNumberGuessWorkflow` `SequentialNumberGuessWorkflow`oluşturan kodda, ya `StateMachineNumberGuessWorkflow`da istediğiniz iş akışı stiline bağlı olarak öğesini değiştirin.

     [!code-csharp[CFX_WF_GettingStarted#6](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]

     Bir iş akışı uygulamasına Kalıcılık ekleme hakkında yönergeler için, bir sonraki konuya [bkz. nasıl yapılır: Uzun süre çalışan bir Iş akışı](how-to-create-and-run-a-long-running-workflow.md)oluşturun ve çalıştırın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, `Main` yöntemi için kod listesinin tamamdır.

> [!NOTE]
> Lütfen bu `Workflow1` örneklerde, önceki `FlowchartNumberGuessWorkflow` `StateMachineNumberGuessWorkflow` `SequentialNumberGuessWorkflow` adımdatamamladığınızişakışınabağlıolarak,[veya ile değiştirin: Bir iş akışı](how-to-create-a-workflow.md) adımı oluşturun. ' Yi değiştirip `Workflow1` iş akışını oluşturup oluştururken veya çalıştırdığınızda yapı hataları alırsınız.

 [!code-csharp[CFX_WF_GettingStarted#12](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#12)]
 [!code-vb[CFX_WF_GettingStarted#12](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#12)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Activities.WorkflowApplication>
- <xref:System.Activities.Bookmark>
- [Windows Workflow Foundation Programlama](programming.md)
- [Başlangıç Öğreticisi](getting-started-tutorial.md)
- [Nasıl yapılır: Iş akışı oluşturma](how-to-create-a-workflow.md)
- [Nasıl yapılır: Uzun süre çalışan bir Iş akışı oluşturma ve çalıştırma](how-to-create-and-run-a-long-running-workflow.md)
- [Bir iş akışında giriş bekleme](waiting-for-input-in-a-workflow.md)
- [İş Akışları Barındırma](hosting-workflows.md)
