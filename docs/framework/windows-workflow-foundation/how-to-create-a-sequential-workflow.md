---
title: 'Nasıl yapılır: Akış Çizelgesi İş Akışı Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5280e816-ae17-48c4-8de0-a1e6895dd8f0
ms.openlocfilehash: d94843e696848010791b1e22d06e4852d35bc68e
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044417"
---
# <a name="how-to-create-a-sequential-workflow"></a>Nasıl yapılır: Akış Çizelgesi İş Akışı Oluşturma

İş akışları, yerleşik etkinliklerin yanı sıra özel etkinliklerden de oluşturulabilir. Bu konu, <xref:System.Activities.Statements.Sequence> etkinlik gibi yerleşik etkinlikleri ve önceki [nasıl yapılacağı özel etkinlikleri kullanan bir iş akışı oluşturma ile ilgili adımları izleyerek yapılır: Etkinlik](how-to-create-an-activity.md) konusu oluşturun. İş akışı, sayıyı tahmin eden bir oyunu modelleyen.

> [!NOTE]
> Başlangıç öğreticisindeki her konu, önceki konulara bağlıdır. Bu konuyu tamamlayabilmeniz için öncelikle [şunları yapmanız gerekir: Etkinlik](how-to-create-an-activity.md)oluşturun.

> [!NOTE]
> Öğreticinin tamamlanmış bir sürümünü indirmek için, bkz. [Windows Workflow Foundation (WF45)-Başlangıç Öğreticisi](https://go.microsoft.com/fwlink/?LinkID=248976).

## <a name="to-create-the-workflow"></a>İş akışını oluşturmak için

1. **Çözüm Gezgini** 'de **NumberGuessWorkflowActivities** öğesine sağ tıklayın ve **Ekle**, **Yeni öğe**' yi seçin.

2. **Yüklü**, **ortak öğeler** düğümünde **iş akışı**' nı seçin. **Iş akışı** listesinden **etkinlik** ' i seçin.

3. Ad `SequentialNumberGuessWorkflow` kutusuna yazın ve **Ekle**' ye tıklayın.

4. **Araç kutusunun** **Denetim akışı** bölümünden bir **sıra** etkinliğini sürükleyin ve iş akışı tasarım yüzeyinde **buraya bırakma etkinliği** etiketini bırakın.

## <a name="to-create-the-workflow-variables-and-arguments"></a>İş akışı değişkenlerini ve bağımsız değişkenleri oluşturmak için

1. Henüz görüntülenmiyorsa, iş akışını tasarımcıda göstermek için **Çözüm Gezgini** içinde **SequentialNumberGuessWorkflow. xaml** öğesine çift tıklayın.

2. **Bağımsız değişkenler** bölmesini göstermek için iş akışı Tasarımcısı ' nın sol alt tarafındaki **bağımsız değişkenler** ' e tıklayın.

3. **Bağımsız değişken Oluştur**' a tıklayın.

4. Ad `MaxNumber` kutusuna yazın , **Yön** açılan listesinden **'** i seçin, **bağımsız değişken türü** açılan listesinden **Int32** ' i seçin ve ardından bağımsız değişkeni kaydetmek için ENTER tuşuna basın.

5. **Bağımsız değişken Oluştur**' a tıklayın.

6. Yeni `Turns` eklenen bağımsız`MaxNumber` değişkenin altında bulunan ad kutusuna yazın, Yön açılan listesinden Seç ' i seçin, **bağımsız değişken türü** açılan listesinden Int32 ' i seçin ve ardından ENTER tuşuna basın.

7. **Bağımsız değişkenler** bölmesini kapatmak için etkinlik tasarımcısının sol alt tarafındaki **bağımsız değişkenler** ' e tıklayın.

8. **Değişkenler** bölmesini göstermek için iş akışı Tasarımcısı ' nın sol alt tarafındaki **değişkenler** ' e tıklayın.

9. **Değişken Oluştur**' a tıklayın.

    > [!TIP]
    > **Değişken Oluştur** kutusu görüntülenmiyorsa, iş akışı Tasarımcısı yüzeyinde **dizi** etkinliğine tıklayarak seçin.

10. Ad `Guess` kutusuna yazın , **değişken türü** açılır listesinden **Int32** ' i seçin ve ardından değişkeni kaydetmek için ENTER tuşuna basın.

11. **Değişken Oluştur**' a tıklayın.

12. Ad `Target` kutusuna yazın , **değişken türü** açılır listesinden **Int32** ' i seçin ve ardından değişkeni kaydetmek için ENTER tuşuna basın.

13. **Değişkenler** bölmesini kapatmak için etkinlik tasarımcısının sol alt tarafındaki **değişkenler** ' e tıklayın.

## <a name="to-add-the-workflow-activities"></a>İş akışı etkinliklerini eklemek için

1. **Araç kutusu** ' nu **temel elemanlar** bölümünden bir **atama** etkinliği sürükleyin ve **dizi** etkinliğine bırakın. Buraya `Target` yazın veya bir  **C# ifade girin** veya bir **vb ifadesi girin** .

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

     Bir <xref:System.Activities.Statements.DoWhile> etkinlik, alt etkinliklerini yürütür ve sonra <xref:System.Activities.Statements.DoWhile.Condition%2A>değerlendirir. <xref:System.Activities.Statements.DoWhile.Condition%2A> Olarak <xref:System.Activities.Statements.DoWhile> değerlendirilirse, içindeki etkinlikler yeniden yürütün. `True` Bu örnekte, kullanıcının tahmini değerlendirilir ve <xref:System.Activities.Statements.DoWhile> tahmin doğru olana kadar devam eder.

4. **Araç kutusunun** **NumberGuessWorkflowActivities** bölümünden bir **istem** etkinliğini sürükleyin ve önceki adımda **DoWhile** etkinliğinde bırakın.

5. **Özellikler penceresinde**, **komut istemi** etkinliğinin `"EnterGuess"` **BookmarkName** Özellik değeri kutusuna tırnak işareti ekleme yazın. Sonuç `Guess` özelliği değeri kutusuna yazın ve **metin** özellik kutusuna aşağıdaki ifadeyi yazın.

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

7. To `Turns` kutusuna ve `Turns + 1` **bir C# ifade girin** veya bir **vb ifadesi girin** kutusuna yazın.

8. **Araç kutusunun** **Denetim akışı** bölümünden bir **IF** etkinliği sürükleyin ve yeni eklenen **atama** etkinliğinin ardından onu **sıra** etkinliğine bırakın.

9. **IF** etkinliğinin **koşul** özelliği değeri kutusuna aşağıdaki ifadeyi yazın.

    ```vb
    Guess <> Target
    ```

    ```csharp
    Guess != Target
    ```

10. **Araç kutusunun** **Denetim akışı** bölümünden başka bir etkinlik **varsa** , **sonra** da ilk **IF** etkinliğinin bölümüne sürükleyin.

11. Yeni eklenen etkinliğin **koşul** özelliği değeri kutusuna aşağıdaki ifadeyi yazın.

    ```
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

     İş akışının nasıl çalıştırılacağı hakkında yönergeler için lütfen sonraki konuya [bakın: Bir Iş akışı](how-to-run-a-workflow.md)çalıştırın. ' Nin [nasıl yapılacağını zaten tamamladıysanız: Farklı bir iş](how-to-run-a-workflow.md) akışı stili ile bir iş akışı adımı çalıştırın ve bu adımda [](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) [sıralı iş akışını kullanarak çalıştırmak istiyorsanız, nasıl yapılır: Bir Iş akışı](how-to-run-a-workflow.md)çalıştırın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [Windows Workflow Foundation Programlama](programming.md)
- [İş Akışları Tasarlama](designing-workflows.md)
- [Başlangıç Öğreticisi](getting-started-tutorial.md)
- [Nasıl yapılır: Etkinlik oluşturma](how-to-create-an-activity.md)
- [Nasıl yapılır: Iş akışı çalıştırma](how-to-run-a-workflow.md)
