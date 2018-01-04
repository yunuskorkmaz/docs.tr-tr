---
title: "Nasıl yapılır: bir akış iş akışı oluşturma"
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
ms.assetid: 185d7aea-68a6-4bd8-adde-45050f33170a
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2b7a8eab16b089597eecc03896f86827aae1ad85
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-flowchart-workflow"></a>Nasıl yapılır: bir akış iş akışı oluşturma
İş akışları yerleşik etkinliklerden yanı sıra özel etkinliklerden oluşturulabilir. Bu konudaki adımları hem yerleşik etkinlikler gibi kullanan bir iş akışı oluşturma aracılığıyla <xref:System.Activities.Statements.Flowchart> etkinliği ve önceki özel etkinlikler [nasıl yapılır: bir etkinlik oluşturmak](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) konu. Sayı tahmin eden oyun iş akışını modeller.  
  
> [!NOTE]
>  Başlarken Öğreticisi her bir konuda önceki konularda bağlıdır. Bu konuda tamamlamak için önce tamamlamanız gereken [nasıl yapılır: bir etkinlik oluşturmak](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).  
  
> [!NOTE]
>  Öğreticinin tamamlanmış bir sürümünü indirmek için bkz: [Windows Workflow Foundation (WF45) - başlangıç Öğreticisi](http://go.microsoft.com/fwlink/?LinkID=248976).  
  
### <a name="to-create-the-workflow"></a>İş akışını oluşturmak için  
  
1.  Sağ **NumberGuessWorkflowActivities** içinde **Çözüm Gezgini** seçip **Ekle**, **yeni öğe**.  
  
2.  İçinde **yüklü**, **ortak öğeler** düğümü, select **iş akışı**. Seçin **etkinlik** gelen **iş akışı** listesi.  
  
3.  Tür `FlowchartNumberGuessWorkflow` içine **adı** kutusuna ve tıklatın **Ekle**.  
  
4.  Sürükleme bir **akış çizelgesi** etkinliğinden **akış çizelgesi** bölümünü **araç** ve üzerine bırakın **etkinliğini Drop burada** üzerindeki etiket İş akışı tasarım yüzeyi.  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a>İş akışı değişkenleri ve bağımsız değişkenler oluşturmak için  
  
1.  Çift **FlowchartNumberGuessWorkflow.xaml** içinde **Çözüm Gezgini** zaten görüntülenmiyorsa, iş akışı Tasarımcısı'nda görüntülemek için.  
  
2.  Tıklatın **bağımsız değişkenleri** görüntülemek için iş akışı Tasarımcısı sol tarafındaki **bağımsız değişkenleri** bölmesi.  
  
3.  Tıklatın **bağımsız değişkeni oluşturma**.  
  
4.  Tür `MaxNumber` içine **adı** kutusunda **içinde** gelen **yönü** aşağı açılan listesinden, **Int32** gelen**Bağımsız değişken türü** aşağı açılan liste ve bağımsız değişkeni kaydetmek için ENTER tuşuna basın.  
  
5.  Tıklatın **bağımsız değişkeni oluşturma**.  
  
6.  Tür `Turns` içine **adı** altında yeni eklenen kutusuna `MaxNumber` bağımsız değişkeni, select **çıkışı** gelen **yönü** aşağı açılan listesinden,  **Int32** gelen **bağımsız değişken türü** aşağı açılan liste ve ENTER tuşuna BASIN.  
  
7.  Tıklatın **bağımsız değişkenleri** kapatmak için etkinlik Tasarımcısı sol tarafındaki **bağımsız değişkenleri** bölmesi.  
  
8.  Tıklatın **değişkenleri** görüntülemek için iş akışı Tasarımcısı sol tarafındaki **değişkenleri** bölmesi.  
  
9. Tıklatın **değişken oluşturma**.  
  
    > [!TIP]
    >  Yoksa **oluşturma değişken** kutusu görüntülenir, tıklatın <xref:System.Activities.Statements.Flowchart> seçmek için iş akışı Tasarımcısı yüzey üzerinde etkinlik.  
  
10. Tür `Guess` içine **adı** kutusunda **Int32** gelen **değişken türü** aşağı açılan liste ve değişkeni kaydetmek için ENTER tuşuna basın.  
  
11. Tıklatın **değişken oluşturma**.  
  
12. Tür `Target` içine **adı** kutusunda **Int32** gelen **değişken türü** aşağı açılan liste ve değişkeni kaydetmek için ENTER tuşuna basın.  
  
13. Tıklatın **değişkenleri** kapatmak için etkinlik Tasarımcısı sol tarafındaki **değişkenleri** bölmesi.  
  
### <a name="to-add-the-workflow-activities"></a>İş akışı etkinlikleri eklemek için  
  
1.  Sürükle bir **atamak** etkinliğinden **Temelleri** bölümünü **araç** ve üzerine gelin, üzerinden **Başlat** en üstünde olduğu düğümü Akış Çizelgesi. Zaman **atamak** etkinliktir üzerinden **Başlat** düğümü, üç üçgenler etrafında görünür **Başlat** düğümü. Bırakma **atamak** doğrudan aşağıdaki üçgen faaliyete **Başlat** düğümü. Bu iki öğeyi birbirine bağlamak ve atar **atamak** etkinlik akış ilk etkinlik olarak.  
  
    > [!NOTE]
    >  Etkinlikler de başlangıç etkinliği iş akışı olarak el ile etkinlik başlangıç düğümü bağlayarak belirtilebilir. Bunu yapmak için fareyi üzerine gelerek **Başlat** düğümü, fare üzerinden olduğunda görüntülenen dikdörtgenler birini tıklatın **Başlat** düğümü ve bağlanma satır istenen etkinlik aşağı kaydırın ve aşağıdakilerden birini bırakma sürükleyin görünen dikdörtgenler. Ayrıca belirleyebilirsiniz ve BT sağ tıklayarak ve seçme başlangıç etkinliği gibi etkinlik **Başlat düğüm kümesi**.  
  
2.  Tür `Target` içine **için** kutusu ve aşağıdaki ifadesine **bir C# ifadesi girin** veya **bir VB ifadesi girin** kutusu.  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  Varsa **araç** penceresi görüntülenmez, seçin **araç** gelen **Görünüm** menüsü.  
  
3.  Sürükleme bir **komut istemi** etkinliğinden **NumberGuessWorkflowActivities** bölümünü **araç**, aşağıdaki bırakma **atamak** etkinliği Önceki adım ve bağlanın **komut istemi** etkinliğe **atamak** etkinlik. İki etkinlik bağlanmak için üç yolu vardır. Bıraktığınız gibi bunları bağlamak için ilk yoludur **komut istemi** iş akışı etkinliği. Sürüklediğiniz gibi **komut istemi** iş akışına aktivite üzerine gelin, üzerinden **atamak** etkinliği ve ne zaman görünür dört üçgenler birini üzerine bırakın **komut istemi** etkinliktir üzerinden **atamak** etkinlik. Bırakmak için ikinci yoludur **komut istemi** etkinliği iş akışı istenen konuma üzerine. Fare ardından üzerine gelerek **atamak** etkinliği ve sürükleme aşağı görünüyor dikdörtgenler birini **komut istemi** etkinlik. Böylece bağlanma satır fareyi sürükleyin **atamak** etkinlik dikdörtgen birine bağlayan **komut istemi** etkinliği ve ardından yayın fare düğmesini. Üçüncü yolu çok hariç sürükleyerek yerine ilk yol benzer **komut istemi** etkinliğinden **araç**, konumundan iş akışı tasarım yüzeyine sürükleyin, getirin **Ata** etkinliği ve görünür üçgenler birini üzerine bırakın.  
  
4.  İçinde **Özellikler penceresini** için **komut istemi** etkinliği, türü `"EnterGuess"` tırnak işaretleri içine dahil **YerİşaretiAdı** özellik değeri kutusu. Tür `Guess` içine **sonuç** özelliği değeri kutusunu ve içine aşağıdaki ifadeyi yazın **metin** özellik kutusu.  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    >  Varsa **Özellikler penceresini** görüntülenen, select değil **Özellikler penceresini** gelen **Görünüm** menüsü.  
  
5.  Sürükleme bir **atamak** etkinliğinden **Temelleri** bölümünü **araç** ve olmasınısağlamaköncekiadımdaaçıklananyöntemlerdenbirinikullanarakbağlanın **Komut İstemi** etkinlik.  
  
6.  Tür `Turns` içine **için** kutusu ve `Turns + 1` içine **bir C# ifadesi girin** veya **bir VB ifadesi girin** kutusu.  
  
7.  Sürükleme bir **FlowDecision** gelen **akış çizelgesi** bölümünü **araç** ve aşağıdaki bağlanmak **atamak** etkinlik. İçinde **Özellikler penceresini**, içine aşağıdaki ifadeyi yazın **koşulu** özellik değeri kutusu.  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
8.  Başka bir sürükleyin **FlowDecision** etkinliğinden **araç** ve birinci bırakın. Etiketli dikdörtgen sürükleyerek iki etkinlik bağlanmak **False** üstte **FlowDecision** dikdörtgen etkinliğe ikinci üstündeki **FlowDecision**etkinlik.  
  
    > [!TIP]
    >  Görmüyorsanız, **True** ve **False** üzerinde etiketler **FlowDecision**, fare üzerine gelerek **FlowDecision**.  
  
9. İkinci tıklatın **FlowDecision** etkinliği seçin. İçinde **Özellikler penceresini**, içine aşağıdaki ifadeyi yazın **koşulu** özellik değeri kutusu.  
  
    ```
    Guess < Target  
    ```  
  
10. İki **WriteLine** etkinliklerden **Temelleri** bölümünü **araç** ve böylece yan yana iki oldukları bırakın **FlowDecision**  etkinlikler. Bağlanma **True** alt eylem **FlowDecision** etkinliğe soldaki **WriteLine** etkinliği ve **False** eyleme en sağdaki **WriteLine** etkinlik.  
  
11. Soldaki tıklatın **WriteLine** seçin ve içine aşağıdaki ifadeyi yazın etkinlik **metin** özellik değeri kutusunda **Özellikler penceresini**.  
  
    ```
    "Your guess is too low."  
    ```  
  
12. Bağlantı **WriteLine** sol tarafına **komut istemi** üstüne etkinliğini.  
  
13. En sağdaki tıklatın **WriteLine** seçin ve içine aşağıdaki ifadeyi yazın etkinlik **metin** özellik değeri kutusunda **Özellikler penceresini**.  
  
    ```
    "Your guess is too high."  
    ```  
  
14. Bağlantı **WriteLine** etkinliğinin sağ tarafına **komut istemi** üstündeki etkinlik.  
  
     Aşağıdaki örnek, tamamlanan iş akışı gösterilmektedir.  
  
     ![Windows Workflow Foundation tamamlandı](../../../docs/framework/windows-workflow-foundation/media/gettingstartedtutorialcompletedflowchart.PNG "GettingStartedTutorialCompletedFlowchart")  
  
### <a name="to-build-the-workflow"></a>İş akışı oluşturmak için  
  
1.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
     İş akışını çalıştırmak yönergeler Lütfen görmek için sonraki konuyu [nasıl yapılır: bir iş akışını çalıştırma](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md). Zaten tamamladıysanız [nasıl yapılır: bir iş akışını çalıştırma](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) adım farklı bir iş akışı stil ile ve çalıştırmak bu adımı akış iş akışını kullanarak istediğiniz, için İleri atlayabilirsiniz [oluşturmak veuygulamayıçalıştırmakiçin](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication)bölümünü [nasıl yapılır: bir iş akışını çalıştırma](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Activities.Statements.Flowchart>  
 <xref:System.Activities.Statements.FlowDecision>  
 [Windows Workflow Foundation Programlama](../../../docs/framework/windows-workflow-foundation/programming.md)  
 [İş Akışları Tasarlama](../../../docs/framework/windows-workflow-foundation/designing-workflows.md)  
 [Başlangıç Öğreticisi](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [Nasıl Yapılır: Etkinlik Oluşturma](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)  
 [Nasıl yapılır: İş Akışı Çalıştırma](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)
