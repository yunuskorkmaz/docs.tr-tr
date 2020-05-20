---
title: 'Nasıl yapılır: İş Akışı Çalıştırma'
description: Bu makalede, bir iş akışı konağını oluşturma ve bu Windows Workflow Foundation öğretici serisinde önceki bir makalede tanımlanan iş akışını çalıştırma gösterilmektedir.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f814ff82-fe2b-4614-aebb-b768c3e61179
ms.openlocfilehash: 86062dd5147e6e354833928fd98bd1f6b5de9114
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421507"
---
# <a name="how-to-run-a-workflow"></a>Nasıl yapılır: İş Akışı Çalıştırma
Bu konu, kullanmaya başlama öğreticisini Windows Workflow Foundation ve bir iş akışı konağının nasıl oluşturulduğunu ve önceki [nasıl yapılır: Iş akışı oluşturma](how-to-create-a-workflow.md) konusunda tanımlanan iş akışını nasıl çalıştıracağınızı açıklar.

> [!NOTE]
> Başlangıç öğreticisindeki her konu, önceki konulara bağlıdır. Bu konuyu tamamlayabilmeniz için öncelikle [nasıl yapılır: etkinlik oluşturma](how-to-create-an-activity.md) ve [nasıl yapılır: iş akışı oluşturma](how-to-create-a-workflow.md)' yı tamamlamalısınız.

> [!NOTE]
> Öğreticinin tamamlanmış bir sürümünü indirmek için, bkz. [Windows Workflow Foundation (WF45)-Başlangıç Öğreticisi](https://go.microsoft.com/fwlink/?LinkID=248976).  
  
### <a name="to-create-the-workflow-host-project"></a>İş akışı konak projesi oluşturmak için  
  
1. Önceki [nasıl yapılır:](how-to-create-an-activity.md) Visual Studio 2012 kullanarak etkinlik oluşturma konusunun çözümünü açın.  
  
2. **Çözüm Gezgini** 'de **WF45GettingStartedTutorial** çözümüne sağ tıklayın ve **Ekle**, **Yeni proje**' yi seçin.  
  
    > [!TIP]
    > **Çözüm Gezgini** penceresi görüntülenmiyorsa, **Görünüm** menüsünden **Çözüm Gezgini** ' i seçin.

3. **Yüklü** düğümde, **Visual C#**, **iş akışı** (veya **Visual Basic**, **iş akışı**) öğesini seçin.

    > [!NOTE]
    > Visual Studio 'da birincil dil olarak yapılandırılmış programlama diline bağlı olarak, **Visual C#** veya **Visual Basic** düğümü **yüklü** düğümdeki **diğer diller** düğümü altında olabilir.

     **.NET Framework 4,5** ' nin .NET Framework sürüm açılan listesinde seçildiğinden emin olun. **İş akışı listesinden iş** akışı **konsol uygulaması** ' nı seçin. `NumberGuessWorkflowHost` **Ad** kutusuna yazın ve **Tamam**' a tıklayın. Bu, temel iş akışı barındırma desteğiyle bir başlatıcı iş akışı uygulaması oluşturur. Bu temel barındırma kodu değiştirilir ve iş akışı uygulamasını çalıştırmak için kullanılır.

4. **Çözüm Gezgini** ' de yeni eklenen **Numberguessworkflowwhost** projesine sağ tıklayın ve **Başvuru Ekle**' yi seçin. **Başvuru Ekle** listesinden **çözüm** ' i seçin, **NumberGuessWorkflowActivities**yanındaki onay kutusunu işaretleyin ve ardından **Tamam**' a tıklayın.

5. **Çözüm Gezgini** 'de **Workflow1. xaml** öğesine sağ tıklayın ve **Sil**' i seçin. Onaylamak için **Tamam** ' ı tıklatın.

### <a name="to-modify-the-workflow-hosting-code"></a>İş akışı barındırma kodunu değiştirmek için

1. Kodu göstermek için **Çözüm Gezgini** 'de **program.cs** veya **Module1. vb** öğesine çift tıklayın.

    > [!TIP]
    > **Çözüm Gezgini** penceresi görüntülenmiyorsa, **Görünüm** menüsünden **Çözüm Gezgini** ' i seçin.

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

     Oluşturulan bu barındırma kodu kullanılır <xref:System.Activities.WorkflowInvoker> . <xref:System.Activities.WorkflowInvoker>bir iş akışını Yöntem çağrısı gibi çağırmak için basit bir yol sağlar ve yalnızca kalıcılığı kullanmayan iş akışları için kullanılabilir. <xref:System.Activities.WorkflowApplication>yaşam döngüsü olaylarının, yürütme denetiminin, yer işaretinin sürdürme ve kalıcılığın bildirimini içeren iş akışlarını yürütmek için daha zengin bir model sağlar. Bu örnek, yer işaretlerini kullanır ve <xref:System.Activities.WorkflowApplication> iş akışını barındırmak için kullanılır. `using`Var olan **using** veya **Imports** deyimlerinin altındaki **program.cs** veya **Module1. vb** üst kısmına aşağıdaki veya **Imports** deyimini ekleyin.

    ```vb
    Imports NumberGuessWorkflowActivities
    Imports System.Threading
    ```

    ```csharp
    using NumberGuessWorkflowActivities;
    using System.Threading;
    ```

     <xref:System.Activities.WorkflowInvoker>Aşağıdaki temel barındırma koduyla kullanılan kod satırlarını değiştirin <xref:System.Activities.WorkflowApplication> . Bu örnek barındırma kodu, bir iş akışını barındırmak ve çağırmak için temel adımları gösterir, ancak henüz bu konudan iş akışını başarıyla çalıştırmaya yönelik işlevselliği içermez. Aşağıdaki adımlarda, bu temel kod değiştirilir ve uygulama tamamlanana kadar ek özellikler eklenir.

    > [!NOTE]
    > Lütfen `Workflow1` `FlowchartNumberGuessWorkflow` `SequentialNumberGuessWorkflow` `StateMachineNumberGuessWorkflow` önceki [nasıl yapılır: iş akışı adımı oluşturma](how-to-create-a-workflow.md) adımında tamamladığınız iş akışına bağlı olarak, bu örneklerde, veya ile değiştirin. `Workflow1`' Yi değiştirip iş akışını oluşturup oluştururken veya çalıştırdığınızda yapı hataları alırsınız.

     [!code-csharp[CFX_WF_GettingStarted#4](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#4)]
     [!code-vb[CFX_WF_GettingStarted#4](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#4)]

     Bu kod bir oluşturur <xref:System.Activities.WorkflowApplication> , üç iş akışı yaşam döngüsü olayına abone olur, bir çağrısıyla iş akışını başlatır <xref:System.Activities.WorkflowApplication.Run%2A> ve sonra iş akışının tamamlanmasını bekler. İş akışı tamamlandığında, <xref:System.Threading.AutoResetEvent> ayarlanır ve ana bilgisayar uygulaması tamamlanır.

### <a name="to-set-input-arguments-of-a-workflow"></a>Bir iş akışının giriş bağımsız değişkenlerini ayarlamak için

1. Aşağıdaki deyimi, var olan or deyimlerinin altındaki **program.cs** veya **Module1. vb** öğesinin üstüne ekleyin `using` `Imports` .

     [!code-csharp[CFX_WF_GettingStarted#5](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#5)]
     [!code-vb[CFX_WF_GettingStarted#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#5)]

2. Yeni oluşturan kod satırını, <xref:System.Activities.WorkflowApplication> oluşturulduğunda iş akışına bir parametre sözlüğü oluşturup ileten aşağıdaki kodla değiştirin.

    > [!NOTE]
    > Lütfen `Workflow1` `FlowchartNumberGuessWorkflow` `SequentialNumberGuessWorkflow` `StateMachineNumberGuessWorkflow` önceki [nasıl yapılır: iş akışı adımı oluşturma](how-to-create-a-workflow.md) adımında tamamladığınız iş akışına bağlı olarak, bu örneklerde, veya ile değiştirin. `Workflow1`' Yi değiştirip iş akışını oluşturup oluştururken veya çalıştırdığınızda yapı hataları alırsınız.

     [!code-csharp[CFX_WF_GettingStarted#6](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]

     Bu sözlük, anahtarı olan bir öğesi içerir `MaxNumber` . Giriş sözlüğündeki anahtarlar, iş akışının kök etkinliğinin giriş bağımsız değişkenlerine karşılık gelir. `MaxNumber`, rastgele oluşturulan sayı için üst sınırı belirlemede iş akışı tarafından kullanılır.

### <a name="to-retrieve-output-arguments-of-a-workflow"></a>Bir iş akışının çıkış bağımsız değişkenlerini almak için

1. İşleyiciyi, <xref:System.Activities.WorkflowApplication.Completed%2A> iş akışı tarafından kullanılan dönüşler sayısını almak ve görüntüleyecek şekilde değiştirin.

     [!code-csharp[CFX_WF_GettingStarted#7](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#7)]
     [!code-vb[CFX_WF_GettingStarted#7](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#7)]

### <a name="to-resume-a-bookmark"></a>Bir yer işaretini sürdürülmesi için

1. Aşağıdaki kodu, `Main` mevcut bildiriminden hemen sonra yönteminin en üstüne ekleyin <xref:System.Threading.AutoResetEvent> .

     [!code-csharp[CFX_WF_GettingStarted#8](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#8)]
     [!code-vb[CFX_WF_GettingStarted#8](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#8)]

2. <xref:System.Activities.WorkflowApplication.Idle%2A>' De var olan üç iş akışı yaşam döngüsü işleyicisinin hemen altına aşağıdaki işleyiciyi ekleyin `Main` .

     [!code-csharp[CFX_WF_GettingStarted#9](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#9)]
     [!code-vb[CFX_WF_GettingStarted#9](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#9)]

     Her iş akışı bir sonraki tahmin için bekleme durumunda olduğunda, bu işleyici çağrılır ve `idleAction` <xref:System.Threading.AutoResetEvent> ayarlanır. Aşağıdaki adımdaki kod, `idleEvent` `syncEvent` iş akışının bir sonraki tahmin için mi beklediğini yoksa tamamlanıp tamamlanmadığını mı öğrenmek için ve kullanır.

    > [!NOTE]
    > Bu örnekte, ana bilgisayar uygulaması, ve işleyicilerinde otomatik sıfırlama olaylarını kullanarak <xref:System.Activities.WorkflowApplication.Completed%2A> <xref:System.Activities.WorkflowApplication.Idle%2A> konak uygulamasını iş akışının ilerlemesiyle eşitler. Bir yer işaretine devam etmeden önce iş akışının boşta hale gelmesini engellemek ve beklemek gerekli değildir, ancak bu örnekte, konağın iş akışının tamamlanıp tamamlanmadığını veya kullanarak daha fazla kullanıcı girişi beklediğini bilmesi için eşitleme olayları gereklidir <xref:System.Activities.Bookmark> . Daha fazla bilgi için bkz. [yer işaretleri](bookmarks.md).

3. ' A çağrıyı kaldırın `WaitOne` ve kullanıcıdan giriş toplamak için kodu kodla değiştirin ve ' ı sürdürülemez <xref:System.Activities.Bookmark> .

     Aşağıdaki kod satırını kaldırın.

     [!code-csharp[CFX_WF_GettingStarted#10](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#10)]
     [!code-vb[CFX_WF_GettingStarted#10](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#10)]

     Aşağıdaki örnekle değiştirin.

     [!code-csharp[CFX_WF_GettingStarted#11](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#11)]
     [!code-vb[CFX_WF_GettingStarted#11](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#11)]

## <a name="to-build-and-run-the-application"></a><a name="BKMK_ToRunTheApplication"></a>Uygulamayı derlemek ve çalıştırmak için

1. **Çözüm Gezgini** Için **Numberguessworkflowwhost** öğesine sağ tıklayın ve **Başlangıç projesi olarak ayarla**' yı seçin.

2. Uygulamayı derlemek ve çalıştırmak için CTRL + F5 tuşlarına basın. Sayıyı olabildiğince az sürede tahmin etmeye çalışın.

     Uygulamayı diğer iş akışı stillerinden biriyle denemek için, `Workflow1` veya ile oluşturan kodda, ya da istediğiniz <xref:System.Activities.WorkflowApplication> `FlowchartNumberGuessWorkflow` `SequentialNumberGuessWorkflow` `StateMachineNumberGuessWorkflow` iş akışı stiline bağlı olarak öğesini değiştirin.

     [!code-csharp[CFX_WF_GettingStarted#6](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]

     Bir iş akışı uygulamasına Kalıcılık ekleme hakkında yönergeler için, bir sonraki konuya bkz. [nasıl yapılır: uzun süre çalışan bir Iş akışı oluşturma ve çalıştırma](how-to-create-and-run-a-long-running-workflow.md).

## <a name="example"></a>Örnek
 Aşağıdaki örnek, yöntemi için kod listesinin Tamamdır `Main` .

> [!NOTE]
> Lütfen `Workflow1` `FlowchartNumberGuessWorkflow` `SequentialNumberGuessWorkflow` `StateMachineNumberGuessWorkflow` önceki [nasıl yapılır: iş akışı adımı oluşturma](how-to-create-a-workflow.md) adımında tamamladığınız iş akışına bağlı olarak, bu örneklerde, veya ile değiştirin. `Workflow1`' Yi değiştirip iş akışını oluşturup oluştururken veya çalıştırdığınızda yapı hataları alırsınız.

 [!code-csharp[CFX_WF_GettingStarted#12](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#12)]
 [!code-vb[CFX_WF_GettingStarted#12](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#12)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Activities.WorkflowApplication>
- <xref:System.Activities.Bookmark>
- [Windows Workflow Foundation Programlama](programming.md)
- [Başlangıç Öğreticisi](getting-started-tutorial.md)
- [Nasıl yapılır: İş Akışı Oluşturma](how-to-create-a-workflow.md)
- [Nasıl yapılır: Uzun Süre Çalışan İş Akışı Oluşturma ve Çalıştırma](how-to-create-and-run-a-long-running-workflow.md)
- [Bir iş akışında giriş bekleme](waiting-for-input-in-a-workflow.md)
- [İş Akışları Barındırma](hosting-workflows.md)
