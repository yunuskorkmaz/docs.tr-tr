---
title: 'Nasıl yapılır: Akış Çizelgesi İş Akışı Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 185d7aea-68a6-4bd8-adde-45050f33170a
ms.openlocfilehash: 15cf94d5ea191435723f754f35e43d65632142e2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59311207"
---
# <a name="how-to-create-a-flowchart-workflow"></a>Nasıl yapılır: Akış Çizelgesi İş Akışı Oluşturma
İş akışları yerleşik etkinliklerden yanı sıra özel etkinliklerden oluşturulabilir. Bu konu başlığı altında adımlar hem yerleşik etkinlikler gibi kullanan bir iş akışı oluşturma işleminde <xref:System.Activities.Statements.Flowchart> etkinliği ve özel etkinlikler önceki [nasıl yapılır: Bir etkinlik oluşturursunuz](how-to-create-an-activity.md) konu. İş akışı sayısını tahmin eden oyun modelleri.  
  
> [!NOTE]
>  Önceki konularıyla ilgili her konuda Başlarken Öğreticisi bağlıdır. Bu konuyu tamamlamak için önce tamamlamanız gereken [nasıl yapılır: Bir etkinlik oluşturursunuz](how-to-create-an-activity.md).  
  
> [!NOTE]
>  Öğreticinin tamamlanmış bir sürümünü indirmek için bkz [Windows Workflow Foundation (WF45) - başlangıç Öğreticisi](https://go.microsoft.com/fwlink/?LinkID=248976).  
  
### <a name="to-create-the-workflow"></a>İş akışını oluşturmak için  
  
1. Sağ **NumberGuessWorkflowActivities** içinde **Çözüm Gezgini** seçip **Ekle**, **yeni öğe**.  
  
2. İçinde **yüklü**, **ortak öğeler** düğümünü **iş akışı**. Seçin **etkinlik** gelen **iş akışı** listesi.  
  
3. Tür `FlowchartNumberGuessWorkflow` içine **adı** kutusuna ve tıklatın **Ekle**.  
  
4. Sürükle bir **akış** etkinliğinden **akış** bölümünü **araç kutusu** üzerine bırakın **bırak etkinliği Buraya** üzerindeki etiket İş akışı tasarım yüzeyi.  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a>Bağımsız değişkenler ve iş akışı değişkenlerini oluşturmak için  
  
1. Çift **FlowchartNumberGuessWorkflow.xaml** içinde **Çözüm Gezgini** zaten görüntülenmiyorsa, iş akışı Tasarımcısı'nda görüntülenecek.  
  
2. Tıklayın **bağımsız değişkenleri** sol alt tarafında görüntülenecek iş akışı Tasarımcısı **bağımsız değişkenleri** bölmesi.  
  
3. Tıklayın **bağımsız değişken oluşturma**.  
  
4. Tür `MaxNumber` içine **adı** kutusunda **içinde** gelen **yönü** aşağı açılan listesinden **Int32** gelen**Bağımsız değişken türü** aşağı açılan liste ve bağımsız değişkeni kaydetmek için ENTER tuşuna basın.  
  
5. Tıklayın **bağımsız değişken oluşturma**.  
  
6. Tür `Turns` içine **adı** altında yeni eklenen kutusunu `MaxNumber` bağımsız değişkeni, select **kullanıma** gelen **yönü** aşağı açılan listesinden  **Int32** gelen **bağımsız değişken türü** aşağı açılan liste ve ENTER tuşuna basın.  
  
7. Tıklayın **bağımsız değişkenleri** etkinlik Tasarımcısı kapatmak için sol alt tarafında **bağımsız değişkenleri** bölmesi.  
  
8. Tıklayın **değişkenleri** sol alt tarafında görüntülenecek iş akışı Tasarımcısı **değişkenleri** bölmesi.  
  
9. Tıklayın **değişken oluşturma**.  
  
    > [!TIP]
    >  Hayır ise **oluşturma değişken** kutusu görüntülenir, tıklayın <xref:System.Activities.Statements.Flowchart> seçmek için iş akışı Tasarımcı yüzeyine etkinliği.  
  
10. Tür `Guess` içine **adı** kutusunda **Int32** gelen **değişken türü** aşağı açılan liste ve değişkeni kaydetmek için ENTER tuşuna basın.  
  
11. Tıklayın **değişken oluşturma**.  
  
12. Tür `Target` içine **adı** kutusunda **Int32** gelen **değişken türü** aşağı açılan liste ve değişkeni kaydetmek için ENTER tuşuna basın.  
  
13. Tıklayın **değişkenleri** etkinlik Tasarımcısı kapatmak için sol alt tarafında **değişkenleri** bölmesi.  
  
### <a name="to-add-the-workflow-activities"></a>İş akışı etkinlikleri eklemek için  
  
1. Sürükle bir **atama** etkinliğinden **Temelleri** bölümünü **araç kutusu** ve onu kutucuğunun üzerine gelin **Başlat** üstünde olan düğüm Akış Çizelgesi. Zaman **atama** etkinliktir üzerinden **Başlat** düğüm, üç üçgenler geçici olarak görünür **Başlat** düğümü. DROP **atama** doğrudan aşağıdaki üçgen faaliyete **Başlat** düğümü. Bu iki öğeyi birbirine bağlamak ve atar **atama** akış ilk etkinlik olarak etkinlik.  
  
    > [!NOTE]
    >  Etkinlikler de başlangıç etkinliği iş akışı olarak el ile etkinlik başlangıç düğümüne bağlayarak belirtilebilir. Bunu yapmak için fareyi üzerine **Başlat** düğümü, fareyi üzerine geldiğinde görünen dikdörtgen birine tıklayın **Başlat** düğümü ile bağlanma ve satır aşağı istenen etkinlik birinde bırakın sürükleyin görünen dikdörtgen. Ayrıca bir etkinliğin başlangıç etkinliği olarak BT sağ tıklayıp seçerek belirleyebilirsiniz **başlangıç düğümü olarak ayarlamak**.  
  
2. Tür `Target` içine **için** kutusu ve içine aşağıdaki ifade **bir C# ifadesi girin** veya **zadejte Výraz jazyka vb.** kutusu.  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  Varsa **araç kutusu** penceresi görüntülenmiyorsa, seçin **araç kutusu** gelen **görünümü** menüsü.  
  
3. Sürükle bir **istemi** etkinliğinden **NumberGuessWorkflowActivities** bölümünü **araç kutusu**, aşağıdaki açılan **atama** etkinliği Önceki adım ve connect **komut istemi** etkinliğini **atama** etkinlik. İki etkinliği bağlanmak için üç yolu vardır. Bıraktığınız gibi bunları bağlamak için ilk yoludur **istemi** iş akışı etkinliği. Sürüklediğiniz gibi **komut istemi** etkinlik iş akışı için bunu kutucuğunun üzerine gelin **atama** etkinlik görünür dört üçgenler birini üzerine bırakın **istemi** Etkinlik bittikten **atama** etkinlik. Bırakmak ikinci yoludur **istemi** etkinlik iş akışı istenen konuma sürükleyin. Fareyi üzerine ardından **atama** etkinliği ve dikdörtgenlerden görünen aşağı sürükleyin **istemi** etkinlik. Fareyi sürükleyin, böylece bağlanma satır gelen **atama** etkinlik bağlayan bir dikdörtgen **istemi** etkinliği ve ardından sürüm fare düğmesini. Üçüncü yolu çok hariç sürükleyerek yerine ilk yol benzer **istemi** etkinliğinden **araç kutusu**, iş akışı tasarım yüzeyinde konumundan sürükleyin, gelin **Ata** etkinliği ve görüntülenen üçgenler birini üzerine bırakın.  
  
4. İçinde **Özellikler penceresi** için **istemi** etkinliği, türü `"EnterGuess"` tırnak işaretleri içine dahil **YerİşaretiAdı** özellik değer kutusu. Tür `Guess` içine **sonucu** özellik değer kutusu ve içine aşağıdaki ifadeyi yazın **metin** özellik kutusu.  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    >  Varsa **Özellikler penceresi** görüntülenen, select değil **Özellikler penceresi** gelen **görünümü** menüsü.  
  
5. Sürükle bir **atama** etkinliğinden **Temelleri** bölümünü **araç kutusu** ve olmasıöncekiadımdaaçıklananyöntemlerdenbirinikullanarakbağlanma **Komut İstemi** etkinlik.  
  
6. Tür `Turns` içine **için** kutusu ve `Turns + 1` içine **bir C# ifadesi girin** veya **zadejte Výraz jazyka vb.** kutusu.  
  
7. Sürükleme bir **FlowDecision** gelen **akış** bölümünü **araç kutusu** ve aşağıdaki bağlantı **atama** etkinlik. İçinde **Özellikler penceresi**, içine aşağıdaki ifadeyi yazın **koşul** özellik değer kutusu.  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
8. Başka bir sürükleyin **FlowDecision** etkinliğinden **araç kutusu** ilki bırakın. Etiketli dikdörtgenden sürükleyerek iki etkinliklerini bağlama **False** üst **FlowDecision** dikdörtgen etkinliğe ikinci üst kısmındaki **FlowDecision**etkinlik.  
  
    > [!TIP]
    >  Görmüyorsanız, **True** ve **False** üzerinde etiketler **FlowDecision**, fareyi üzerine **FlowDecision**.  
  
9. İkinci tıklama **FlowDecision** etkinliği seçin. İçinde **Özellikler penceresi**, içine aşağıdaki ifadeyi yazın **koşul** özellik değer kutusu.  
  
    ```
    Guess < Target  
    ```  
  
10. İki **WriteLine** etkinlikten **Temelleri** bölümünü **araç kutusu** ve bunlar yan yana iki altında olacak şekilde bırakın **FlowDecision**  etkinlikler. Bağlanmak **True** alt eylem **FlowDecision** etkinliğini en soldaki **WriteLine** etkinliği ve **False** eylemi en sağdaki **WriteLine** etkinlik.  
  
11. En soldaki tıklayın **WriteLine** etkinliği seçin ve içine aşağıdaki ifadeyi yazın **metin** özellik değeri kutusunda **Özellikler penceresi**.  
  
    ```
    "Your guess is too low."  
    ```  
  
12. Connect **WriteLine** sol tarafına **istemi** üzerinde etkinlik.  
  
13. En sağdaki tıklayın **WriteLine** etkinliği seçin ve içine aşağıdaki ifadeyi yazın **metin** özellik değeri kutusunda **Özellikler penceresi**.  
  
    ```
    "Your guess is too high."  
    ```  
  
14. Bağlama **WriteLine** etkinliğinin sağındaki **istemi** üstündeki etkinlik.  
  
     Aşağıdaki örnekte, tamamlanmış bir iş akışı gösterilmektedir.  
  
     ![Windows Workflow Foundation tamamlandı](./media/gettingstartedtutorialcompletedflowchart.PNG "GettingStartedTutorialCompletedFlowchart")  
  
### <a name="to-build-the-workflow"></a>İş akışı oluşturmak için  
  
1. Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
     Lütfen iş akışının nasıl çalıştırılacağını yönergeleri görmek için bir sonraki konu [nasıl yapılır: İş akışı çalıştırma](how-to-run-a-workflow.md). Zaten tamamladıysanız [nasıl yapılır: İş akışı çalıştırma](how-to-run-a-workflow.md) adım iş akışı farklı bir stil ve çalıştırmak bu adımdaki akış çizelgesi iş akışı kullanarak istediğiniz, atlayın [uygulaması derleme ve çalıştırma için](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) bölümünü [nasıl yapılır: İş akışı çalıştırma](how-to-run-a-workflow.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [Windows Workflow Foundation Programlama](programming.md)
- [İş Akışları Tasarlama](designing-workflows.md)
- [Başlangıç Öğreticisi](getting-started-tutorial.md)
- [Nasıl yapılır: Bir etkinlik oluşturma](how-to-create-an-activity.md)
- [Nasıl yapılır: İş akışı çalıştırma](how-to-run-a-workflow.md)
