---
title: 'Nasıl yapılır: Sıralı iş akışı oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5280e816-ae17-48c4-8de0-a1e6895dd8f0
ms.openlocfilehash: 33a4d6f7db140023bc33839fec7d5e28b7f5fe51
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54547312"
---
# <a name="how-to-create-a-sequential-workflow"></a>Nasıl yapılır: Sıralı iş akışı oluşturma
İş akışları yerleşik etkinliklerden yanı sıra özel etkinliklerden oluşturulabilir. Bu konu başlığı altında adımlar hem yerleşik etkinlikler gibi kullanan bir iş akışı oluşturma işleminde <xref:System.Activities.Statements.Sequence> etkinliği ve özel etkinlikler önceki [nasıl yapılır: Bir etkinlik oluşturursunuz](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) konu. İş akışı sayısını tahmin eden oyun modelleri.  
  
> [!NOTE]
>  Önceki konularıyla ilgili her konuda Başlarken Öğreticisi bağlıdır. Bu konuyu tamamlamak için önce tamamlamanız gereken [nasıl yapılır: Bir etkinlik oluşturursunuz](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).  
  
> [!NOTE]
>  Öğreticinin tamamlanmış bir sürümünü indirmek için bkz [Windows Workflow Foundation (WF45) - başlangıç Öğreticisi](https://go.microsoft.com/fwlink/?LinkID=248976).  
  
### <a name="to-create-the-workflow"></a>İş akışını oluşturmak için  
  
1.  Sağ **NumberGuessWorkflowActivities** içinde **Çözüm Gezgini** seçip **Ekle**, **yeni öğe**.  
  
2.  İçinde **yüklü**, **ortak öğeler** düğümünü **iş akışı**. Seçin **etkinlik** gelen **iş akışı** listesi.  
  
3.  Tür `SequentialNumberGuessWorkflow` içine **adı** kutusuna ve tıklatın **Ekle**.  
  
4.  Sürükle bir **dizisi** etkinliğinden **akış denetimi** bölümünü **araç kutusu** üzerine bırakın **Buraya Bırak etkinlik** üzerindeki etiket İş akışı tasarım yüzeyi.  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a>Bağımsız değişkenler ve iş akışı değişkenlerini oluşturmak için  
  
1.  Çift **SequentialNumberGuessWorkflow.xaml** içinde **Çözüm Gezgini** zaten görüntülenmiyorsa, iş akışı Tasarımcısı'nda görüntülenecek.  
  
2.  Tıklayın **bağımsız değişkenleri** sol alt tarafında görüntülenecek iş akışı Tasarımcısı **bağımsız değişkenleri** bölmesi.  
  
3.  Tıklayın **bağımsız değişken oluşturma**.  
  
4.  Tür `MaxNumber` içine **adı** kutusunda **içinde** gelen **yönü** aşağı açılan listesinden **Int32** gelen**Bağımsız değişken türü** aşağı açılan liste ve bağımsız değişkeni kaydetmek için ENTER tuşuna basın.  
  
5.  Tıklayın **bağımsız değişken oluşturma**.  
  
6.  Tür `Turns` içine **adı** altında yeni eklenen kutusunu `MaxNumber` bağımsız değişkeni, select **kullanıma** gelen **yönü** aşağı açılan listesinden  **Int32** gelen **bağımsız değişken türü** aşağı açılan liste ve ENTER tuşuna basın.  
  
7.  Tıklayın **bağımsız değişkenleri** etkinlik Tasarımcısı kapatmak için sol alt tarafında **bağımsız değişkenleri** bölmesi.  
  
8.  Tıklayın **değişkenleri** sol alt tarafında görüntülenecek iş akışı Tasarımcısı **değişkenleri** bölmesi.  
  
9. Tıklayın **değişken oluşturma**.  
  
    > [!TIP]
    >  Hayır ise **oluşturma değişken** kutusu görüntülenir, tıklayın **dizisi** seçmek için iş akışı Tasarımcı yüzeyine etkinliği.  
  
10. Tür `Guess` içine **adı** kutusunda **Int32** gelen **değişken türü** aşağı açılan liste ve değişkeni kaydetmek için ENTER tuşuna basın.  
  
11. Tıklayın **değişken oluşturma**.  
  
12. Tür `Target` içine **adı** kutusunda **Int32** gelen **değişken türü** aşağı açılan liste ve değişkeni kaydetmek için ENTER tuşuna basın.  
  
13. Tıklayın **değişkenleri** etkinlik Tasarımcısı kapatmak için sol alt tarafında **değişkenleri** bölmesi.  
  
### <a name="to-add-the-workflow-activities"></a>İş akışı etkinlikleri eklemek için  
  
1.  Sürükleme bir **atama** etkinliğinden **Temelleri** bölümünü **araç kutusu** üzerine bırakın **dizisi** etkinlik. Tür `Target` içine **için** kutusu ve içine aşağıdaki ifade **bir C# ifadesi girin** veya **zadejte Výraz jazyka vb.** kutusu.  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  Varsa **araç kutusu** penceresi görüntülenmiyorsa, seçin **araç kutusu** gelen **görünümü** menüsü.  
  
2.  Sürükleme bir **DoWhile** etkinliğinden **akış denetimi** bölümünü **araç kutusu** ve böylece altına iş akışını bırakın **atama** Etkinlik.  
  
3.  İçine aşağıdaki ifadeyi yazın **DoWhile** etkinliğin **koşul** özellik değer kutusu.  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
     A <xref:System.Activities.Statements.DoWhile> etkinlik kendi alt etkinlikleri yürütür ve ardından değerlendirir, <xref:System.Activities.Statements.DoWhile.Condition%2A>. Varsa <xref:System.Activities.Statements.DoWhile.Condition%2A> değerlendiren `True`, etkinlikler, ardından <xref:System.Activities.Statements.DoWhile> tekrar yürütün. Bu örnekte, kullanıcının tahmin değerlendirilir ve <xref:System.Activities.Statements.DoWhile> tahmin doğru olana kadar devam eder.  
  
4.  Sürükleme bir **istemi** etkinliğinden **NumberGuessWorkflowActivities** bölümünü **araç kutusu** sürükleyip **DoWhile** etkinliği Önceki adımda.  
  
5.  İçinde **Özellikler penceresi**, türü `"EnterGuess"` tırnak işaretleri içine dahil **YerİşaretiAdı** özellik değer kutusu **istemi** etkinlik. Tür `Guess` içine **sonucu** özellik değer kutusu ve içine aşağıdaki ifadeyi yazın **metin** özellik kutusu.  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    >  Varsa **Özellikler penceresi** görüntülenen, select değil **Özellikler penceresi** gelen **görünümü** menüsü.  
  
6.  Sürükle bir **atama** etkinliğinden **Temelleri** bölümünü **araç kutusu** sürükleyip **DoWhile** BT'nin böylece etkinliği **İstemi** etkinlik.  
  
    > [!NOTE]
    >  Bıraktığınız zaman **atama** etkinliği, Not nasıl iş akışı Tasarımcısı otomatik olarak ekler bir **dizisi** hem de içerecek şekilde etkinlik **istemi** etkinliği ve yeni eklenen **Atama** etkinlik.  
  
7.  Tür `Turns` içine **için** kutusu ve `Turns + 1` içine **bir C# ifadesi girin** veya **zadejte Výraz jazyka vb.** kutusu.  
  
8.  Sürükle bir **varsa** etkinliğinden **akış denetimi** bölümünü **araç kutusu** sürükleyip **dizisi** BT'nin böylece etkinliği Yeni eklenen **atama** etkinlik.  
  
9. İçine aşağıdaki ifadeyi yazın **varsa** etkinliğin **koşul** özellik değer kutusu.  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
10. Başka bir sürükleyin **varsa** etkinliğinden **akış denetimi** bölümünü **araç kutusu** sürükleyip **ardından** ilkbölümünü**Varsa** etkinlik.  
  
11. Yeni eklenen aşağıdaki ifadeyi yazın **varsa** etkinliğin **koşul** özellik değer kutusu.  
  
    ```
    Guess < Target  
    ```  
  
12. İki **WriteLine** etkinlikten **Temelleri** bölümünü **araç kutusu** ve böylece bir yer bırakın **ardından** bölümü Yeni eklenen **varsa** etkinliği ve bir **Else** bölümü.  
  
13. Tıklayın **WriteLine** etkinliğinde **ardından** seçmek için bölüm ve içine aşağıdaki ifadeyi yazın **metin** özellik değer kutusu.  
  
    ```vb  
    "Your guess is too low."  
    ```  
  
14. Tıklayın **WriteLine** etkinliğinde **Else** seçmek için bölüm ve içine aşağıdaki ifadeyi yazın **metin** özellik değer kutusu.  
  
    ```vb  
    "Your guess is too high."  
    ```  
  
     Aşağıdaki örnekte, tamamlanmış bir iş akışı gösterilmektedir.  
  
     ![Sıralı iş akışı tamamlandı](../../../docs/framework/windows-workflow-foundation/media/wfsequentialgettingstartedtutorialcomplete.JPG "WFSequentialGettingStartedTutorialComplete")  
  
### <a name="to-build-the-workflow"></a>İş akışı oluşturmak için  
  
1.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
     Lütfen iş akışının nasıl çalıştırılacağını yönergeleri görmek için bir sonraki konu [nasıl yapılır: İş akışı çalıştırma](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md). Zaten tamamladıysanız [nasıl yapılır: İş akışı çalıştırma](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) adım iş akışı farklı bir stil ve çalıştırmak bu adımdaki sıralı iş akışı kullanarak istediğiniz, atlayın [uygulaması derleme ve çalıştırma için](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication) bölümünü [nasıl yapılır: İş akışı çalıştırma](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [Windows Workflow Foundation Programlama](../../../docs/framework/windows-workflow-foundation/programming.md)
- [İş Akışları Tasarlama](../../../docs/framework/windows-workflow-foundation/designing-workflows.md)
- [Başlangıç Öğreticisi](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)
- [Nasıl yapılır: Bir etkinlik oluşturma](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)
- [Nasıl yapılır: İş akışı çalıştırma](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)
