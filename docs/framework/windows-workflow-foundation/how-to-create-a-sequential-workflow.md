---
title: "Nasıl yapılır: Sıralı iş akışı oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 5280e816-ae17-48c4-8de0-a1e6895dd8f0
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 285450f3c9e724bcf449f638ee1922751c9cebaf
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-sequential-workflow"></a>Nasıl yapılır: Sıralı iş akışı oluşturma
İş akışları yerleşik etkinliklerden yanı sıra özel etkinliklerden oluşturulabilir. Bu konudaki adımları hem yerleşik etkinlikler gibi kullanan bir iş akışı oluşturma aracılığıyla <xref:System.Activities.Statements.Sequence> etkinliği ve önceki özel etkinlikler [nasıl yapılır: bir etkinlik oluşturmak](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) konu. Sayı tahmin eden oyun iş akışını modeller.  
  
> [!NOTE]
>  Başlarken Öğreticisi her bir konuda önceki konularda bağlıdır. Bu konuda tamamlamak için önce tamamlamanız gereken [nasıl yapılır: bir etkinlik oluşturmak](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).  
  
> [!NOTE]
>  Öğreticinin tamamlanmış bir sürümünü indirmek için bkz: [Windows Workflow Foundation (WF45) - başlangıç Öğreticisi](http://go.microsoft.com/fwlink/?LinkID=248976).  
  
### <a name="to-create-the-workflow"></a>İş akışını oluşturmak için  
  
1.  Sağ **NumberGuessWorkflowActivities** içinde **Çözüm Gezgini** seçip **Ekle**, **yeni öğe**.  
  
2.  İçinde **yüklü**, **ortak öğeler** düğümü, select **iş akışı**. Seçin **etkinlik** gelen **iş akışı** listesi.  
  
3.  Tür `SequentialNumberGuessWorkflow` içine **adı** kutusuna ve tıklatın **Ekle**.  
  
4.  Sürükleme bir **dizisi** etkinliğinden **akış denetimi** bölümünü **araç** ve üzerine bırakın **etkinliğini Drop burada** üzerindeki etiket İş akışı tasarım yüzeyi.  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a>İş akışı değişkenleri ve bağımsız değişkenler oluşturmak için  
  
1.  Çift **SequentialNumberGuessWorkflow.xaml** içinde **Çözüm Gezgini** zaten görüntülenmiyorsa, iş akışı Tasarımcısı'nda görüntülemek için.  
  
2.  Tıklatın **bağımsız değişkenleri** görüntülemek için iş akışı Tasarımcısı sol tarafındaki **bağımsız değişkenleri** bölmesi.  
  
3.  Tıklatın **bağımsız değişkeni oluşturma**.  
  
4.  Tür `MaxNumber` içine **adı** kutusunda **içinde** gelen **yönü** aşağı açılan listesinden, **Int32** gelen**Bağımsız değişken türü** aşağı açılan liste ve bağımsız değişkeni kaydetmek için ENTER tuşuna basın.  
  
5.  Tıklatın **bağımsız değişkeni oluşturma**.  
  
6.  Tür `Turns` içine **adı** altında yeni eklenen kutusuna `MaxNumber` bağımsız değişkeni, select **çıkışı** gelen **yönü** aşağı açılan listesinden,  **Int32** gelen **bağımsız değişken türü** aşağı açılan liste ve ENTER tuşuna BASIN.  
  
7.  Tıklatın **bağımsız değişkenleri** kapatmak için etkinlik Tasarımcısı sol tarafındaki **bağımsız değişkenleri** bölmesi.  
  
8.  Tıklatın **değişkenleri** görüntülemek için iş akışı Tasarımcısı sol tarafındaki **değişkenleri** bölmesi.  
  
9. Tıklatın **değişken oluşturma**.  
  
    > [!TIP]
    >  Yoksa **oluşturma değişken** kutusu görüntülenir, tıklatın **dizisi** seçmek için iş akışı Tasarımcısı yüzey üzerinde etkinlik.  
  
10. Tür `Guess` içine **adı** kutusunda **Int32** gelen **değişken türü** aşağı açılan liste ve değişkeni kaydetmek için ENTER tuşuna basın.  
  
11. Tıklatın **değişken oluşturma**.  
  
12. Tür `Target` içine **adı** kutusunda **Int32** gelen **değişken türü** aşağı açılan liste ve değişkeni kaydetmek için ENTER tuşuna basın.  
  
13. Tıklatın **değişkenleri** kapatmak için etkinlik Tasarımcısı sol tarafındaki **değişkenleri** bölmesi.  
  
### <a name="to-add-the-workflow-activities"></a>İş akışı etkinlikleri eklemek için  
  
1.  Sürükleme bir **atamak** etkinliğinden **Temelleri** bölümünü **araç** ve üzerine bırakın **dizisi** etkinlik. Tür `Target` içine **için** kutusu ve aşağıdaki ifadesine **bir C# ifadesi girin** veya **bir VB ifadesi girin** kutusu.  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  Varsa **araç** penceresi görüntülenmez, seçin **araç** gelen **Görünüm** menüsü.  
  
2.  Sürükleme bir **DoWhile** etkinliğinden **akış denetimi** bölümünü **araç** ve aşağıda olmasını sağlamak iş akışında bırakma **Ata** Etkinlik.  
  
3.  İçine aşağıdaki ifadeyi yazın **DoWhile** etkinliğin **koşulu** özellik değeri kutusu.  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
     A <xref:System.Activities.Statements.DoWhile> etkinlik kendi alt etkinlikleri yürütür ve ardından değerlendirir kendi <xref:System.Activities.Statements.DoWhile.Condition%2A>. Varsa <xref:System.Activities.Statements.DoWhile.Condition%2A> değerlendiren `True`, ardından aktivitelerde <xref:System.Activities.Statements.DoWhile> yeniden yürütün. Bu örnekte, kullanıcının tahmin değerlendirilir ve <xref:System.Activities.Statements.DoWhile> tahmin doğru olana kadar devam eder.  
  
4.  Sürükleme bir **komut istemi** etkinliğinden **NumberGuessWorkflowActivities** bölümünü **araç** sürükleyip bırakın **DoWhile** etkinliği Önceki adımda.  
  
5.  İçinde **Özellikler penceresini**, türü `"EnterGuess"` tırnak işaretleri içine dahil **YerİşaretiAdı** özellik değeri kutusu **komut istemi** etkinlik. Tür `Guess` içine **sonuç** özelliği değeri kutusunu ve içine aşağıdaki ifadeyi yazın **metin** özellik kutusu.  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    >  Varsa **Özellikler penceresini** görüntülenen, select değil **Özellikler penceresini** gelen **Görünüm** menüsü.  
  
6.  Sürükleme bir **atamak** etkinliğinden **Temelleri** bölümünü **araç** sürükleyip bırakın **DoWhile** onun aşağıdaki şekilde etkinliği **Komut istemi** etkinlik.  
  
    > [!NOTE]
    >  Bıraktığınız zaman **atamak** etkinliği, nasıl iş akışı Tasarımcısı'nı otomatik olarak ekler Not bir **dizisi** her ikisi de içerecek şekilde etkinlik **komut istemi** etkinliği ve yeni eklenen **Atamak** etkinlik.  
  
7.  Tür `Turns` içine **için** kutusu ve `Turns + 1` içine **bir C# ifadesi girin** veya **bir VB ifadesi girin** kutusu.  
  
8.  Sürükleme bir **varsa** etkinliğinden **akış denetimi** bölümünü **araç** sürükleyip bırakın **dizisi** onun aşağıdaki şekilde etkinliği Yeni eklenen **atamak** etkinlik.  
  
9. İçine aşağıdaki ifadeyi yazın **varsa** etkinliğin **koşulu** özellik değeri kutusu.  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
10. Başka bir sürükleyin **varsa** etkinliğinden **akış denetimi** bölümünü **araç** sürükleyip bırakın **sonra** ilkbölümünü**Varsa** etkinlik.  
  
11. Aşağıdaki ifade yeni eklenen yazın **varsa** etkinliğin **koşulu** özellik değeri kutusu.  
  
    ```
    Guess < Target  
    ```  
  
12. İki **WriteLine** etkinliklerden **Temelleri** bölümünü **araç** ve böylece içinde biridir bırakın **sonra** bölümü Yeni eklenen **varsa** etkinliği ve bir **Else** bölümü.  
  
13. Tıklatın **WriteLine** etkinliğinde **sonra** seçmek için bölümünde ve içine aşağıdaki ifadeyi yazın **metin** özellik değeri kutusu.  
  
    ```vb  
    "Your guess is too low."  
    ```  
  
14. Tıklatın **WriteLine** etkinliğinde **Else** seçmek için bölümünde ve içine aşağıdaki ifadeyi yazın **metin** özellik değeri kutusu.  
  
    ```vb  
    "Your guess is too high."  
    ```  
  
     Aşağıdaki örnek, tamamlanan iş akışı gösterilmektedir.  
  
     ![Sıralı iş akışı tamamlandı](../../../docs/framework/windows-workflow-foundation/media/wfsequentialgettingstartedtutorialcomplete.JPG "WFSequentialGettingStartedTutorialComplete")  
  
### <a name="to-build-the-workflow"></a>İş akışı oluşturmak için  
  
1.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
     İş akışını çalıştırmak yönergeler Lütfen görmek için sonraki konuyu [nasıl yapılır: bir iş akışını çalıştırma](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md). Zaten tamamladıysanız [nasıl yapılır: bir iş akışını çalıştırma](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) adım farklı bir iş akışı stil ile ve çalıştırmak bu adımı sıralı iş akışını kullanarak istediğiniz, için İleri atlayabilirsiniz [oluşturmak veuygulamayıçalıştırmakiçin](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication)bölümünü [nasıl yapılır: bir iş akışını çalıştırma](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Activities.Statements.Flowchart>  
 <xref:System.Activities.Statements.FlowDecision>  
 [Windows Workflow Foundation programlama](../../../docs/framework/windows-workflow-foundation/programming.md)  
 [İş akışları tasarlama](../../../docs/framework/windows-workflow-foundation/designing-workflows.md)  
 [Başlangıç Öğreticisi](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [Nasıl yapılır: bir etkinlik oluşturmak](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)  
 [Nasıl yapılır: bir iş akışını çalıştırma](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)
