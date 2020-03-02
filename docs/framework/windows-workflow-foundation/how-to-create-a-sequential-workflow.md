---
title: 'Nasıl yapılır: Akış Çizelgesi İş Akışı Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5280e816-ae17-48c4-8de0-a1e6895dd8f0
ms.openlocfilehash: 61e3f01b1259536ff15d71526e91aef42069722e
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989699"
---
# <a name="how-to-create-a-sequential-workflow"></a>Nasıl yapılır: Akış Çizelgesi İş Akışı Oluşturma

İş akışları, yerleşik etkinliklerin yanı sıra özel etkinliklerden de oluşturulabilir. Bu konu, <xref:System.Activities.Statements.Sequence> etkinliği gibi yerleşik etkinlikleri ve önceki [özel etkinlikleri kullanan bir iş akışı oluşturma adımları ile nasıl yapılır: Etkinlik](how-to-create-an-activity.md) konu başlığı oluşturun. İş akışı, sayıyı tahmin eden bir oyunu modelleyen.

> [!NOTE]
> Başlangıç öğreticisindeki her konu, önceki konulara bağlıdır. Bu konuyu tamamlayabilmeniz için öncelikle [nasıl yapılacağını tamamlamalısınız: Etkinlik](how-to-create-an-activity.md)oluşturun.

> [!NOTE]
> Öğreticinin tamamlanmış bir sürümünü indirmek için, bkz. [Windows Workflow Foundation (WF45)-Başlangıç Öğreticisi](https://go.microsoft.com/fwlink/?LinkID=248976).

## <a name="to-create-the-workflow"></a>İş akışını oluşturmak için

1. **Çözüm Gezgini** 'de **NumberGuessWorkflowActivities** öğesine sağ tıklayın ve **Ekle**, **Yeni öğe**' yi seçin.

2. **Yüklü**, **ortak öğeler** düğümünde **iş akışı**' nı seçin. **Iş akışı** listesinden **etkinlik** ' i seçin.

3. **Ad** kutusuna `SequentialNumberGuessWorkflow` yazın ve **Ekle**' ye tıklayın.

4. **Araç kutusunun** **Denetim akışı** bölümünden bir **sıra** etkinliğini sürükleyin ve iş akışı tasarım yüzeyinde **buraya bırakma etkinliği** etiketini bırakın.

## <a name="to-create-the-workflow-variables-and-arguments"></a>İş akışı değişkenlerini ve bağımsız değişkenleri oluşturmak için

1. Henüz görüntülenmiyorsa, iş akışını tasarımcıda göstermek için **Çözüm Gezgini** içinde **SequentialNumberGuessWorkflow. xaml** öğesine çift tıklayın.

2. **Bağımsız değişkenler** bölmesini göstermek için iş akışı Tasarımcısı ' nın sol alt tarafındaki **bağımsız değişkenler** ' e tıklayın.

3. **Bağımsız değişken Oluştur**' a tıklayın.

4. **Ad** kutusuna `MaxNumber` yazın, **Yön** açılan listesinden Seç ' i seçin, **bağımsız değişken türü** açılan listesinden **Int32** ' **i seçin ve** sonra bağımsız değişkeni kaydetmek için ENTER tuşuna basın.

5. **Bağımsız değişken Oluştur**' a tıklayın.

6. Yeni eklenen `MaxNumber` bağımsız değişkeninin altında bulunan **ad** kutusuna `Turns` yazın, **Yön** açılan **listesinden Seç ' i seçin,** **bağımsız değişken türü** AÇıLAN listesinden **Int32** ' yi seçin ve ardından ENTER tuşuna basın.

7. **Bağımsız değişkenler** bölmesini kapatmak için etkinlik tasarımcısının sol alt tarafındaki **bağımsız değişkenler** ' e tıklayın.

8. **Değişkenler** bölmesini göstermek için iş akışı Tasarımcısı ' nın sol alt tarafındaki **değişkenler** ' e tıklayın.

9. **Değişken Oluştur**' a tıklayın.

    > [!TIP]
    > **Değişken Oluştur** kutusu görüntülenmiyorsa, iş akışı Tasarımcısı yüzeyinde **dizi** etkinliğine tıklayarak seçin.

10. **Ad** kutusuna `Guess` yazın, **değişken türü** açılır listesinden **Int32** ' i SEÇIN ve ardından değişkeni kaydetmek için ENTER tuşuna basın.

11. **Değişken Oluştur**' a tıklayın.

12. **Ad** kutusuna `Target` yazın, **değişken türü** açılır listesinden **Int32** ' i SEÇIN ve ardından değişkeni kaydetmek için ENTER tuşuna basın.

13. **Değişkenler** bölmesini kapatmak için etkinlik tasarımcısının sol alt tarafındaki **değişkenler** ' e tıklayın.

## <a name="to-add-the-workflow-activities"></a>İş akışı etkinliklerini eklemek için

1. **Araç kutusu** ' nu **temel elemanlar** bölümünden bir **atama** etkinliği sürükleyin ve **dizi** etkinliğine bırakın. **Bir C# ifade gırın** veya bir **vb ifadesi girin** kutusuna **to** kutusuna `Target` ve aşağıdaki ifadeyi yazın.

    ```vb
    New System.Random().Next(1, MaxNumber + 1)
    ```

    ```csharp
    new System.Random().Next(1, MaxNumber + 1)
    ```

    > [!TIP]
    > **Araç kutusu** penceresi görüntülenmiyorsa, **Görünüm** menüsünden **araç kutusu** ' nu seçin.

2. **Araç kutusunun** **Denetim akışı** bölümünden bir **DoWhile** etkinliği sürükleyin ve **ata** etkinliğinin altında olması için iş akışına bırakın.

3. **DoWhile** etkinliğinin **koşul** özelliği değeri kutusuna aşağıdaki ifadeyi yazın.

    ```vb
    Guess <> Target
    ```

    ```csharp
    Guess != Target
    ```

     <xref:System.Activities.Statements.DoWhile> bir etkinlik, alt etkinliklerini yürütür ve sonra <xref:System.Activities.Statements.DoWhile.Condition%2A>değerlendirir. <xref:System.Activities.Statements.DoWhile.Condition%2A> `True`değerlendirilirse <xref:System.Activities.Statements.DoWhile> etkinlikler yeniden yürütülür. Bu örnekte, kullanıcının tahmini değerlendirilir ve <xref:System.Activities.Statements.DoWhile> tahmin doğru olana kadar devam eder.

4. **Araç kutusunun** **NumberGuessWorkflowActivities** bölümünden bir **istem** etkinliğini sürükleyin ve önceki adımda **DoWhile** etkinliğinde bırakın.

5. **Özellikler penceresinde**, **komut Istemi** etkinliğinin **BookmarkName** özellik değeri kutusuna tırnak işareti dahil `"EnterGuess"` yazın. **Sonuç** özelliği değeri kutusuna `Guess` yazın ve **metin** özellik kutusuna aşağıdaki ifadeyi yazın.

    ```vb
    "Please enter a number between 1 and " & MaxNumber
    ```

    ```csharp
    "Please enter a number between 1 and " + MaxNumber
    ```

    > [!TIP]
    > **Özellikler penceresi** görüntülenmiyorsa, **Görünüm** menüsünden **Özellikler penceresi** ' ni seçin.

6. **Araç kutusu** ' nın **temel öğeler** bölümünden bir **atama** etkinliği sürükleyin ve **istem** etkinliğini takip etmek için **DoWhile** etkinliğine bırakın.

    > [!NOTE]
    > **Ata** etkinliğini bıraktığınızda, iş akışı tasarımcısının hem **istem** etkinliğini hem de yeni eklenen **atama** etkinliğini içerecek şekilde bir **dizi** etkinliği nasıl otomatik olarak eklediğini aklınızda bulundurın.

7. **To** kutusuna `Turns` yazın ve  **C# BIR ifade girin** veya bir **vb ifadesi girin** kutusuna `Turns + 1`.

8. **Araç kutusunun** **Denetim akışı** bölümünden bir **IF** etkinliği sürükleyin ve yeni eklenen **atama** etkinliğinin ardından onu **sıra** etkinliğine bırakın.

9. **IF** etkinliğinin **koşul** özelliği değeri kutusuna aşağıdaki ifadeyi yazın.

    ```vb
    Guess <> Target
    ```

    ```csharp
    Guess != Target
    ```

10. **Araç kutusunun** **Denetim akışı** bölümünden başka bir etkinlik **varsa** , **sonra** da ilk **IF** etkinliğinin bölümüne sürükleyin.

11. Yeni **eklenen etkinliğin** **koşul** özelliği değeri kutusuna aşağıdaki ifadeyi yazın.

    ```text
    Guess < Target
    ```

12. **Araç kutusu** ' **nu** **temel elemanlar** bölümünden iki **WriteLine** etkinliği sürükleyin ve bir birinin yeni eklenen **IF** etkinliğinin bölümünde ve diğeri ise **Else** bölümünde olması için bırakın.

13. **Daha sonra** seçmek Için bölümünde **WriteLine** etkinliğine tıklayın ve **metin** özelliği değeri kutusuna aşağıdaki ifadeyi yazın.

    ```text
    "Your guess is too low."
    ```

14. Bunu seçmek için **Else** bölümünde **WriteLine** etkinliğine tıklayın ve **metin** özelliği değeri kutusuna aşağıdaki ifadeyi yazın.

    ```text
    "Your guess is too high."
    ```

     Aşağıdaki örnek tamamlanan iş akışını göstermektedir:

     ![Tamamlanmış sıralı iş akışını gösteren ekran görüntüsü.](./media/how-to-create-a-sequential-workflow/complete-sequential-workflow.jpg)

## <a name="to-build-the-workflow"></a>İş akışını derlemek için

1. Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.

     İş akışının nasıl çalıştırılacağı hakkında yönergeler için bkz. bir sonraki konu, [nasıl yapılır: ](how-to-run-a-workflow.md)Iş akışı çalıştırın. [Şu anda tamamladıysanız: Farklı bir iş akışı stiliyle Iş akışı](how-to-run-a-workflow.md) adımı çalıştırın ve bu adımdaki sıralı iş akışını [kullanarak çalıştırmak istiyorsanız,](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) [nasıl yapılır: Iş akışı çalıştırın](how-to-run-a-workflow.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [Windows Workflow Foundation Programlama](programming.md)
- [İş Akışları Tasarlama](designing-workflows.md)
- [Başlangıç Öğreticisi](getting-started-tutorial.md)
- [Nasıl yapılır: Etkinlik](how-to-create-an-activity.md) oluşturma
- [Nasıl yapılır: Iş akışı çalıştırma](how-to-run-a-workflow.md)
