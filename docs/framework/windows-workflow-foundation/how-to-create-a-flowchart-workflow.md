---
title: 'Nasıl yapılır: Akış Çizelgesi İş Akışı Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 185d7aea-68a6-4bd8-adde-45050f33170a
ms.openlocfilehash: 0faf4d77b1ea2881ba8e029d544f2e42cf552349
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989681"
---
# <a name="how-to-create-a-flowchart-workflow"></a>Nasıl yapılır: Akış Çizelgesi İş Akışı Oluşturma
İş akışları, yerleşik etkinliklerin yanı sıra özel etkinliklerden de oluşturulabilir. Bu konu, <xref:System.Activities.Statements.Flowchart> etkinlik gibi yerleşik etkinlikleri ve önceki [nasıl yapılacağı özel etkinlikleri kullanan bir iş akışı oluşturma ile ilgili adımları izleyerek yapılır: Etkinlik](how-to-create-an-activity.md) konusu oluşturun. İş akışı, sayıyı tahmin eden bir oyunu modelleyen.  
  
> [!NOTE]
> Başlangıç öğreticisindeki her konu, önceki konulara bağlıdır. Bu konuyu tamamlayabilmeniz için öncelikle [şunları yapmanız gerekir: Etkinlik](how-to-create-an-activity.md)oluşturun.  
  
> [!NOTE]
> Öğreticinin tamamlanmış bir sürümünü indirmek için, bkz. [Windows Workflow Foundation (WF45)-Başlangıç Öğreticisi](https://go.microsoft.com/fwlink/?LinkID=248976).  
  
### <a name="to-create-the-workflow"></a>İş akışını oluşturmak için  
  
1. **Çözüm Gezgini** 'de **NumberGuessWorkflowActivities** öğesine sağ tıklayın ve **Ekle**, **Yeni öğe**' yi seçin.  
  
2. **Yüklü**, **ortak öğeler** düğümünde **iş akışı**' nı seçin. **Iş akışı** listesinden **etkinlik** ' i seçin.  
  
3. Ad `FlowchartNumberGuessWorkflow` kutusuna yazın ve **Ekle**' ye tıklayın.  
  
4. **Araç çubuğu** ' nın **akış çizelgesi** ' nden bir **akış çizelgesi** etkinliği sürükleyin ve iş akışı tasarım yüzeyinde **buraya bırakma etkinliği** etiketini bırakın.  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a>İş akışı değişkenlerini ve bağımsız değişkenleri oluşturmak için  
  
1. Henüz görüntülenmiyorsa, iş akışını tasarımcıda göstermek için **Çözüm Gezgini** Içinde **FlowchartNumberGuessWorkflow. xaml** öğesine çift tıklayın.  
  
2. **Bağımsız değişkenler** bölmesini göstermek için iş akışı Tasarımcısı ' nın sol alt tarafındaki **bağımsız değişkenler** ' e tıklayın.  
  
3. **Bağımsız değişken Oluştur**' a tıklayın.  
  
4. Ad `MaxNumber` kutusuna yazın , **Yön** açılan listesinden **'** i seçin, **bağımsız değişken türü** açılan listesinden **Int32** ' i seçin ve ardından bağımsız değişkeni kaydetmek için ENTER tuşuna basın.  
  
5. **Bağımsız değişken Oluştur**' a tıklayın.  
  
6. Yeni `Turns` eklenen bağımsız değişkenin altında bulunan ad kutusuna yazın, Yön açılan listesinden Seç ' i seçin, bağımsız değişken türü açılan listesinden Int32 ' i seçin ve ardından ENTER tuşuna basın. `MaxNumber`  
  
7. **Bağımsız değişkenler** bölmesini kapatmak için etkinlik tasarımcısının sol alt tarafındaki **bağımsız değişkenler** ' e tıklayın.  
  
8. **Değişkenler** bölmesini göstermek için iş akışı Tasarımcısı ' nın sol alt tarafındaki **değişkenler** ' e tıklayın.  
  
9. **Değişken Oluştur**' a tıklayın.  
  
    > [!TIP]
    > **Değişken Oluştur** kutusu görüntülenmiyorsa, iş akışı Tasarımcısı yüzeyinde <xref:System.Activities.Statements.Flowchart> etkinlik ' i tıklatarak seçin.  
  
10. Ad `Guess` kutusuna yazın , **değişken türü** açılır listesinden **Int32** ' i seçin ve ardından değişkeni kaydetmek için ENTER tuşuna basın.  
  
11. **Değişken Oluştur**' a tıklayın.  
  
12. Ad `Target` kutusuna yazın , **değişken türü** açılır listesinden **Int32** ' i seçin ve ardından değişkeni kaydetmek için ENTER tuşuna basın.  
  
13. **Değişkenler** bölmesini kapatmak için etkinlik tasarımcısının sol alt tarafındaki **değişkenler** ' e tıklayın.  
  
### <a name="to-add-the-workflow-activities"></a>İş akışı etkinliklerini eklemek için  
  
1. **Araç kutusunun** **temel elemanlar** bölümünden bir **atama** etkinliği sürükleyin ve akış çizelgesinin en üstünde bulunan **Başlangıç** düğümünün üzerine gelin. **Atama** etkinliği **Başlangıç** düğümünden üstündeyken, **Başlangıç** düğümü etrafında üç üçgen görünür. **Ata** etkinliğini **Başlangıç** düğümünün doğrudan altındaki üçgende bırakın. Bu, iki öğeyi birbirine bağlar ve **atama** etkinliğini akış çizelgesinde ilk etkinlik olarak belirler.  
  
    > [!NOTE]
    > Etkinlikler, iş akışındaki başlangıç etkinliği olarak, etkinlik etkinliklerini başlangıç düğümüne el ile bağlayarak da belirtilebilir. Bunu yapmak için, fareyi **Başlangıç** düğümünün üzerine getirin, fare **Başlangıç** düğümünün üzerindeyken görüntülenen dikdörtgenlerden birine tıklayın ve bağlama satırı ' nı istenen etkinliğe sürükleyin ve görüntülenen dikdörtgenlerden birine bırakın. Ayrıca, bir etkinliği sağ tıklayıp **başlangıç düğümü olarak ayarla**' yı seçerek başlangıç etkinliği olarak da belirleyebilirsiniz.  
  
2. Buraya `Target` yazın veya bir  **C# ifade girin** veya bir **vb ifadesi girin** .  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    > **Araç kutusu** penceresi görüntülenmiyorsa, **Görünüm** menüsünden **araç kutusu** ' nu seçin.  
  
3. **Araç kutusu**'Nun **NumberGuessWorkflowActivities** bölümünden bir **istem** etkinliğini sürükleyin, önceki adımdan **atama** etkinliğinin altına bırakın ve **istem** etkinliğini **ata** etkinliğine bağlayın. İki etkinliği bağlamak için üç yol vardır. İlk yöntem, iş akışı üzerinde **istem** etkinliğini bıraktığınızda bunları birbirine bağlamanız gerekir. **İstem** etkinliğini iş akışına sürüklerken, **ata** etkinliğinin üzerine gelin ve **Prompt** etkinliği **ata** etkinliğinin üzerindeyken görüntülenen dört üçgenden birine bırakın. İkinci yol, **Prompt** etkinliğinin istenen konumdaki iş akışına düşürülme yöntemidir. Ardından, fareyi **ata** etkinliğinin üzerine getirin ve **komut istemi** etkinliğine aşağı doğru görünen dikdörtgenlerden birini sürükleyin. **Ata** etkinliğinin bağlantı çizgisinin, **istem** etkinliğinin dikdörtgenlerinin birine bağlanmasını sağlamak için fareyi sürükleyin, sonra fare düğmesini bırakın. Üçüncü yol, **araç kutusu**'ndan **istem** etkinliğini sürüklemek yerine, iş akışı tasarım yüzeyindeki konumundan sürükledikten sonra **atama** etkinliğinin üzerine getirdiğinizde ve bunu bir ' dan birine bırakarak görüntülenen üçgenler.  
  
4. **İstem** etkinliğinin **Özellikler penceresinde** , tırnak işareti **adı** Özellik değeri `"EnterGuess"` kutusuna tırnak işareti ekleme yazın. Sonuç `Guess` özelliği değeri kutusuna yazın ve **metin** özellik kutusuna aşağıdaki ifadeyi yazın.  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    > **Özellikler penceresi** görüntülenmiyorsa, **Görünüm** menüsünden **Özellikler penceresi** ' ni seçin.  
  
5. **Araç kutusunun** **temel elemanlar** bölümünden bir **atama** etkinliği sürükleyin ve bu eylemi, önceki adımda açıklanan yöntemlerden birini kullanarak bağlayın, böylece **istem** etkinliğinin altında olur.  
  
6. To `Turns` kutusuna ve `Turns + 1` **bir C# ifade girin** veya bir **vb ifadesi girin** kutusuna yazın.  
  
7. **Araç kutusunun** **akış çizelgesi** bölümünden bir **flowkararı** sürükleyin ve **assign** etkinliğinin altına bağlayın. **Özellikler penceresinde**, **koşul** özelliği değeri kutusuna aşağıdaki ifadeyi yazın.  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
8. **Araç kutusu** 'ndan başka bir **flowkarar** etkinliği sürükleyin ve ilk birinin altına bırakın. En üstteki **Flowkararı** etkinliğinde **false** etiketli dikdörtgenden ikinci **flowkarar** etkinliğinin en üstündeki dikdörtgene sürükleyerek iki etkinliği bağlayın.  
  
    > [!TIP]
    > **Flowkararı**üzerinde **doğru** ve **yanlış** etiketlerini görmüyorsanız, fareyi **flowkararı**üzerine getirin.  
  
9. İkinci **Flowkarar** etkinliğine tıklayarak seçin. **Özellikler penceresinde**, **koşul** özelliği değeri kutusuna aşağıdaki ifadeyi yazın.  
  
    ```text
    Guess < Target
    ```  
  
10. İki **WriteLine** etkinliğini **araç kutusunun** **temel öğeler** bölümünden sürükleyin ve iki **flowkarar** etkinliklerinin altında yan yana olacak şekilde bırakın. En alttaki **Flowkarar** etkinliğinin **doğru** eylemini en soldaki **WriteLine** etkinliğine ve **false** eylemini en sağdaki **WriteLine** etkinliğine bağlayın.  
  
11. En soldaki **WriteLine** etkinliğine tıklayarak bunu seçin ve **Özellikler penceresindeki** **metin** özelliği değeri kutusuna aşağıdaki ifadeyi yazın.  
  
    ```text
    "Your guess is too low."  
    ```  
  
12. **WriteLine** 'ı Yukarıdaki **istem** etkinliğinin sol tarafına bağlayın.  
  
13. Bunu seçmek için en sağdaki **WriteLine** etkinliğine tıklayın ve **Özellikler penceresindeki** **metin** özelliği değeri kutusuna aşağıdaki ifadeyi yazın.  
  
    ```text
    "Your guess is too high."  
    ```  
  
14. **WriteLine** etkinliğini Yukarıdaki **istem** etkinliğinin sağ tarafına bağlayın.  
  
     Aşağıdaki örnekte tamamlanan iş akışı gösterilmektedir.  
  
     ![Tamamlanmış bir Windows Workflow Foundation akış çizelgesi gösteren diyagram.](./media/how-to-create-a-flowchart-workflow/completed-windows-workflow-flowchart.png)  
  
### <a name="to-build-the-workflow"></a>İş akışını derlemek için  
  
1. Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
     İş akışının nasıl çalıştırılacağı hakkında yönergeler için lütfen sonraki konuya [bakın: Bir Iş akışı](how-to-run-a-workflow.md)çalıştırın. ' Nin [nasıl yapılacağını zaten tamamladıysanız: Farklı bir iş](how-to-run-a-workflow.md) akışı stili ile bir iş akışı adımı çalıştırın ve bu adımda akış çizelgesi iş akışını [kullanarak çalıştırmak istiyorsanız,](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) [nasıl yapılır: Bir Iş akışı](how-to-run-a-workflow.md)çalıştırın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [Windows Workflow Foundation Programlama](programming.md)
- [İş Akışları Tasarlama](designing-workflows.md)
- [Başlangıç Öğreticisi](getting-started-tutorial.md)
- [Nasıl yapılır: Etkinlik oluşturma](how-to-create-an-activity.md)
- [Nasıl yapılır: Iş akışı çalıştırma](how-to-run-a-workflow.md)
