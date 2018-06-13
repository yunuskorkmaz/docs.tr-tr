---
title: 'Nasıl yapılır: Durum makinesi iş akışı oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3ec60e8f-fad4-493e-a426-e7962d7aee8c
ms.openlocfilehash: 00f764421d3caf44d853d26d76c6b6d872ab1e3d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33520035"
---
# <a name="how-to-create-a-state-machine-workflow"></a>Nasıl yapılır: Durum makinesi iş akışı oluşturma
İş akışları yerleşik etkinliklerden yanı sıra özel etkinliklerden oluşturulabilir. Bu konudaki adımları hem yerleşik etkinlikler gibi kullanan bir iş akışı oluşturma aracılığıyla <xref:System.Activities.Statements.StateMachine> etkinliği ve önceki özel etkinlikler [nasıl yapılır: bir etkinlik oluşturmak](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) konu. Sayı tahmin eden oyun iş akışını modeller.  
  
> [!NOTE]
>  Başlarken Öğreticisi her bir konuda önceki konularda bağlıdır. Bu konuda tamamlamak için önce tamamlamanız gereken [nasıl yapılır: bir etkinlik oluşturmak](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).  
  
> [!NOTE]
>  Öğreticinin tamamlanmış bir sürümünü indirmek için bkz: [Windows Workflow Foundation (WF45) - başlangıç Öğreticisi](http://go.microsoft.com/fwlink/?LinkID=248976).  
  
### <a name="to-create-the-workflow"></a>İş akışını oluşturmak için  
  
1.  Sağ **NumberGuessWorkflowActivities** içinde **Çözüm Gezgini** seçip **Ekle**, **yeni öğe**.  
  
2.  İçinde **yüklü**, **ortak öğeler** düğümü, select **iş akışı**. Seçin **etkinlik** gelen **iş akışı** listesi.  
  
3.  Tür `StateMachineNumberGuessWorkflow` içine **adı** kutusuna ve tıklatın **Ekle**.  
  
4.  Sürükleme bir **Durum makinesi** etkinliğinden **Durum makinesi** bölümünü **araç** ve üzerine bırakın **etkinliğini Drop burada** üzerindeki etiket İş akışı tasarım yüzeyi.  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a>İş akışı değişkenleri ve bağımsız değişkenler oluşturmak için  
  
1.  Çift **StateMachineNumberGuessWorkflow.xaml** içinde **Çözüm Gezgini** zaten görüntülenmiyorsa, iş akışı Tasarımcısı'nda görüntülemek için.  
  
2.  Tıklatın **bağımsız değişkenleri** görüntülemek için iş akışı Tasarımcısı sol tarafındaki **bağımsız değişkenleri** bölmesi.  
  
3.  Tıklatın **bağımsız değişkeni oluşturma**.  
  
4.  Tür `MaxNumber` içine **adı** kutusunda **içinde** gelen **yönü** aşağı açılan listesinden, **Int32** gelen**Bağımsız değişken türü** aşağı açılan liste ve bağımsız değişkeni kaydetmek için ENTER tuşuna basın.  
  
5.  Tıklatın **bağımsız değişkeni oluşturma**.  
  
6.  Tür `Turns` içine **adı** altında yeni eklenen kutusuna `MaxNumber` bağımsız değişkeni, select **çıkışı** gelen **yönü** aşağı açılan listesinden,  **Int32** gelen **bağımsız değişken türü** aşağı açılan liste ve ENTER tuşuna BASIN.  
  
7.  Tıklatın **bağımsız değişkenleri** kapatmak için etkinlik Tasarımcısı sol tarafındaki **bağımsız değişkenleri** bölmesi.  
  
8.  Tıklatın **değişkenleri** görüntülemek için iş akışı Tasarımcısı sol tarafındaki **değişkenleri** bölmesi.  
  
9. Tıklatın **değişken oluşturma**.  
  
    > [!TIP]
    >  Yoksa **oluşturma değişken** kutusu görüntülenir, tıklatın <xref:System.Activities.Statements.StateMachine> seçmek için iş akışı Tasarımcısı yüzey üzerinde etkinlik.  
  
10. Tür `Guess` içine **adı** kutusunda **Int32** gelen **değişken türü** aşağı açılan liste ve değişkeni kaydetmek için ENTER tuşuna basın.  
  
11. Tıklatın **değişken oluşturma**.  
  
12. Tür `Target` içine **adı** kutusunda **Int32** gelen **değişken türü** aşağı açılan liste ve değişkeni kaydetmek için ENTER tuşuna basın.  
  
13. Tıklatın **değişkenleri** kapatmak için etkinlik Tasarımcısı sol tarafındaki **değişkenleri** bölmesi.  
  
### <a name="to-add-the-workflow-activities"></a>İş akışı etkinlikleri eklemek için  
  
1.  Tıklatın **State1** seçin. İçinde **Özellikler penceresini**, değiştirme **DisplayName** için `Initialize Target`.  
  
    > [!TIP]
    >  Varsa **Özellikler penceresini** görüntülenen, select değil **Özellikler penceresini** gelen **Görünüm** menüsü.  
  
2.  Yeni adlandırılan çift **başlatma hedef** genişletmek için iş akışı Tasarımcısı'nda durum.  
  
3.  Sürükle bir **atamak** etkinliğinden **Temelleri** bölümünü **araç** ve üzerine bırakın **girişi** bölüm durumu. Tür `Target` içine **için** kutusu ve aşağıdaki ifadesine **bir C# ifadesi girin** veya **bir VB ifadesi girin** kutusu.  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  Varsa **araç** penceresi görüntülenmez, seçin **araç** gelen **Görünüm** menüsü.  
  
4.  Dönmek için genel durum makine görünümünde iş akışı Tasarımcısı'nı tıklatarak **Durum makinesi** haritasındaki iş akışı Tasarımcısı'nı üstünde görüntüle.  
  
5.  Sürükle bir **durumu** etkinliğinden **Durum makinesi** bölümünü **araç** iş akışı tasarımcıya ve üzerine gelin, üzerinden **başlatma hedef** durumu. Dört üçgenler geçici görüntüleneceğini unutmayın **başlatma hedef** üzerinde yeni bir durum olduğunda durumu. Hemen aşağıdadır üçgen yeni durumunu bırakma **başlatma hedef** durumu. Bu iş akışı üzerine yeni durum yerleştirir ve bir geçiş oluşturur **başlatma hedef** yeni durumuna durum.  
  
6.  Tıklatın **State1** seçmek için değiştirme **DisplayName** için `Enter Guess`ve genişletmek için iş akışı Tasarımcısı'nda durumu çift tıklatın.  
  
7.  Sürükleme bir **WriteLine** etkinliğinden **Temelleri** bölümünü **araç** ve üzerine bırakın **giriş** bölüm durumu.  
  
8.  İçine aşağıdaki ifadeyi yazın **metin** özellik kutusuna **WriteLine**.  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
9. Sürükle bir **atamak** etkinliğinden **Temelleri** bölümünü **araç** ve üzerine bırakma **çıkış** bölüm durumu.  
  
10. Tür `Turns` içine **için** kutusu ve `Turns + 1` içine **bir C# ifadesi girin** veya **bir VB ifadesi girin** kutusu.  
  
11. Dönmek için genel durum makine görünümünde iş akışı Tasarımcısı'nı tıklatarak **Durum makinesi** haritasındaki iş akışı Tasarımcısı'nı üstünde görüntüle.  
  
12. Sürükleme bir **son durum** etkinliğinden **Durum makinesi** bölümünü **araç**, üzerine gelin, üzerinden **girin tahmin** durum ve bırakın sağ tarafında görünür üçgen üzerine **girin tahmin** arasında bir geçiş oluşturulan durum **girin tahmin** ve **son durum**.  
  
13. Geçiş varsayılan adı **T2**. Geçişi seçin ve ayarlamak için iş akışı Tasarımcısı'nda tıklatın, **DisplayName** için **tahmin doğru**. Ardından tıklatın ve seçin **son durum**ve iki durumlu birini kaplayan olmadan görüntülenecek tam geçiş adı yer olmasını sağlamak sağa sürükleyin. Bu, öğreticide kalan adımları tamamlamak daha kolay hale getirir.  
  
14. Yeni adlandırılan çift **tahmin doğru** geçiş genişletmek için iş akışı Tasarımcısı'nda.  
  
15. Sürükleme bir **readInt** etkinliğinden **NumberGuessWorkflowActivities** bölümünü **araç** sürükleyip bırakın **tetikleyici** bölümü geçişin.  
  
16. İçinde **Özellikler penceresini** için **readInt** etkinliği, türü `"EnterGuess"` tırnak işaretleri içine dahil **YerİşaretiAdı** özellik değeri kutusu ve türü `Guess`içine **sonuç** özellik değeri kutusu  
  
17. İçine aşağıdaki ifadeyi yazın **tahmin doğru** geçiş'ın **koşulu** özellik değeri kutusu.  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
18. Dönmek için genel durum makine görünümünde iş akışı Tasarımcısı'nı tıklatarak **Durum makinesi** haritasındaki iş akışı Tasarımcısı'nı üstünde görüntüle.  
  
    > [!NOTE]
    >  Tetik olayı alındığında bir geçiş oluşur ve <xref:System.Activities.Statements.Transition.Condition%2A>, varsa, değerlendiren `True`. Bu geçiş için kullanıcının `Guess` rastgele oluşturulmuş eşleşen `Target`, Denetim geçer sonra **son durum** ve iş akışı tamamlandığında.  
  
19. Tahmin doğru olup olmamasına bağlı olarak, iş akışı ya da geçiş **son durum** veya yeniden **girin tahmin** durum başka bir deneyin. Her iki geçişler aracılığıyla alınacak kullanıcının tahmin bekleniyor, aynı tetikleyici paylaşmak **readInt** etkinlik. Bu, paylaşılan bir geçiş adı verilir. Paylaşılan bir geçiş oluşturmak için başlangıcını gösterir daireyi tıklatın **tahmin doğru** geçer ve belirtilen istenen duruma sürükleyin. Bu durumda geçiş kendi başına bir geçiş, bu nedenle başlangıç noktası olarak sürükleyin **tahmin doğru** geçiş ve alt geri bırakma **girin tahmin** durumu. Geçiş oluşturduktan sonra iş akışı Tasarımcısı'nda seçin ve ayarlayın, **DisplayName** özelliğine **tahmin yanlış**.  
  
    > [!NOTE]
    >  Paylaşılan geçişleri de oluşturulabilir gelen geçiş Tasarımcısı'nda tıklayarak **paylaşılan tetikleyici geçiş Ekle** geçiş Tasarımcısı'nı ve ardından istenen hedef durumundan seçerek altındaki  **Bağlanmak için kullanılabilir durumları** açılır.  
  
    > [!NOTE]
    >  Unutmayın <xref:System.Activities.Statements.Transition.Condition%2A> bir geçişin değerlendiren `false` (veya bir paylaşılan tetikleyici geçiş koşulların tümü için değerlendirin `false`), geçiş gerçekleşmez ve durumundan tüm geçişler için tüm Tetikleyicileri olacaktır yeniden. Bu öğreticide, bu durum koşulları yapılandırılmış yol nedeniyle meydana olamaz (tahmin doğru veya yanlış olmasına için belirli eylemler uyguluyoruz).  
  
20. Çift **tahmin yanlış** geçiş genişletmek için iş akışı Tasarımcısı'nda. Unutmayın **tetikleyici** aynı zaten ayarlanmış **readInt** tarafından kullanılan etkinlik **tahmin doğru** geçiş.  
  
21. İçine aşağıdaki ifadeyi yazın **koşulu** özellik değeri kutusu.  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
22. Sürükle bir **varsa** etkinliğinden **akış denetimi** bölümünü **araç** sürükleyip bırakın **eylem** geçişi bölümü.  
  
23. İçine aşağıdaki ifadeyi yazın **varsa** etkinliğin **koşulu** özellik değeri kutusu.  
  
    ```
    Guess < Target  
    ```  
  
24. İki **WriteLine** etkinliklerden **Temelleri** bölümünü **araç** ve böylece içinde biridir bırakın **sonra** bölümü **varsa** etkinliği ve bir **Else** bölümü.  
  
25. Tıklatın **WriteLine** etkinliğinde **sonra** seçmek için bölümünde ve içine aşağıdaki ifadeyi yazın **metin** özellik değeri kutusu.  
  
    ```
    "Your guess is too low."  
    ```  
  
26. Tıklatın **WriteLine** etkinliğinde **Else** seçmek için bölümünde ve içine aşağıdaki ifadeyi yazın **metin** özellik değeri kutusu.  
  
    ```
    "Your guess is too high."  
    ```  
  
27. Dönmek için genel durum makine görünümünde iş akışı Tasarımcısı'nı tıklatarak **Durum makinesi** haritasındaki iş akışı Tasarımcısı'nı üstünde görüntüle.  
  
     Aşağıdaki örnek, tamamlanan iş akışı gösterilmektedir.  
  
     ![Durum makinesi iş akışı tamamlandı](../../../docs/framework/windows-workflow-foundation/media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")  
  
### <a name="to-build-the-workflow"></a>İş akışı oluşturmak için  
  
1.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
     İş akışını çalıştırmak yönergeler Lütfen görmek için sonraki konuyu [nasıl yapılır: bir iş akışını çalıştırma](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md). Zaten tamamladıysanız [nasıl yapılır: bir iş akışını çalıştırma](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) adım farklı bir iş akışı stil ile ve çalıştırmak bu adım Durum makinesi iş akışını kullanarak istediğiniz, için İleri atlayabilirsiniz [oluşturmak veuygulamayıçalıştırmakiçin](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication) bölümünü [nasıl yapılır: bir iş akışını çalıştırma](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Activities.Statements.Flowchart>  
 <xref:System.Activities.Statements.FlowDecision>  
 [Windows Workflow Foundation Programlama](../../../docs/framework/windows-workflow-foundation/programming.md)  
 [İş Akışları Tasarlama](../../../docs/framework/windows-workflow-foundation/designing-workflows.md)  
 [Başlangıç Öğreticisi](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [Nasıl Yapılır: Etkinlik Oluşturma](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)  
 [Nasıl yapılır: İş Akışı Çalıştırma](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)
