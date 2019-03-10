---
title: 'Nasıl yapılır: Bir Durum makinesi iş akışı oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3ec60e8f-fad4-493e-a426-e7962d7aee8c
ms.openlocfilehash: d3ec8c1b8c9b30a23dacabeb033d525c34709931
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708268"
---
# <a name="how-to-create-a-state-machine-workflow"></a>Nasıl yapılır: Bir Durum makinesi iş akışı oluşturma
İş akışları yerleşik etkinliklerden yanı sıra özel etkinliklerden oluşturulabilir. Bu konu başlığı altında adımlar hem yerleşik etkinlikler gibi kullanan bir iş akışı oluşturma işleminde <xref:System.Activities.Statements.StateMachine> etkinliği ve özel etkinlikler önceki [nasıl yapılır: Bir etkinlik oluşturursunuz](how-to-create-an-activity.md) konu. İş akışı sayısını tahmin eden oyun modelleri.  
  
> [!NOTE]
>  Önceki konularıyla ilgili her konuda Başlarken Öğreticisi bağlıdır. Bu konuyu tamamlamak için önce tamamlamanız gereken [nasıl yapılır: Bir etkinlik oluşturursunuz](how-to-create-an-activity.md).  
  
> [!NOTE]
>  Öğreticinin tamamlanmış bir sürümünü indirmek için bkz [Windows Workflow Foundation (WF45) - başlangıç Öğreticisi](https://go.microsoft.com/fwlink/?LinkID=248976).  
  
### <a name="to-create-the-workflow"></a>İş akışını oluşturmak için  
  
1.  Sağ **NumberGuessWorkflowActivities** içinde **Çözüm Gezgini** seçip **Ekle**, **yeni öğe**.  
  
2.  İçinde **yüklü**, **ortak öğeler** düğümünü **iş akışı**. Seçin **etkinlik** gelen **iş akışı** listesi.  
  
3.  Tür `StateMachineNumberGuessWorkflow` içine **adı** kutusuna ve tıklatın **Ekle**.  
  
4.  Sürükle bir **StateMachine** etkinliğinden **Durum makinesi** bölümünü **araç kutusu** üzerine bırakın **Buraya Bırak etkinlik** üzerindeki etiket İş akışı tasarım yüzeyi.  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a>Bağımsız değişkenler ve iş akışı değişkenlerini oluşturmak için  
  
1.  Çift **StateMachineNumberGuessWorkflow.xaml** içinde **Çözüm Gezgini** zaten görüntülenmiyorsa, iş akışı Tasarımcısı'nda görüntülenecek.  
  
2.  Tıklayın **bağımsız değişkenleri** sol alt tarafında görüntülenecek iş akışı Tasarımcısı **bağımsız değişkenleri** bölmesi.  
  
3.  Tıklayın **bağımsız değişken oluşturma**.  
  
4.  Tür `MaxNumber` içine **adı** kutusunda **içinde** gelen **yönü** aşağı açılan listesinden **Int32** gelen**Bağımsız değişken türü** aşağı açılan liste ve bağımsız değişkeni kaydetmek için ENTER tuşuna basın.  
  
5.  Tıklayın **bağımsız değişken oluşturma**.  
  
6.  Tür `Turns` içine **adı** altında yeni eklenen kutusunu `MaxNumber` bağımsız değişkeni, select **kullanıma** gelen **yönü** aşağı açılan listesinden  **Int32** gelen **bağımsız değişken türü** aşağı açılan liste ve ENTER tuşuna basın.  
  
7.  Tıklayın **bağımsız değişkenleri** etkinlik Tasarımcısı kapatmak için sol alt tarafında **bağımsız değişkenleri** bölmesi.  
  
8.  Tıklayın **değişkenleri** sol alt tarafında görüntülenecek iş akışı Tasarımcısı **değişkenleri** bölmesi.  
  
9. Tıklayın **değişken oluşturma**.  
  
    > [!TIP]
    >  Hayır ise **oluşturma değişken** kutusu görüntülenir, tıklayın <xref:System.Activities.Statements.StateMachine> seçmek için iş akışı Tasarımcı yüzeyine etkinliği.  
  
10. Tür `Guess` içine **adı** kutusunda **Int32** gelen **değişken türü** aşağı açılan liste ve değişkeni kaydetmek için ENTER tuşuna basın.  
  
11. Tıklayın **değişken oluşturma**.  
  
12. Tür `Target` içine **adı** kutusunda **Int32** gelen **değişken türü** aşağı açılan liste ve değişkeni kaydetmek için ENTER tuşuna basın.  
  
13. Tıklayın **değişkenleri** etkinlik Tasarımcısı kapatmak için sol alt tarafında **değişkenleri** bölmesi.  
  
### <a name="to-add-the-workflow-activities"></a>İş akışı etkinlikleri eklemek için  
  
1.  Tıklayın **State1** seçin. İçinde **Özellikler penceresi**, değiştirme **DisplayName** için `Initialize Target`.  
  
    > [!TIP]
    >  Varsa **Özellikler penceresi** görüntülenen, select değil **Özellikler penceresi** gelen **görünümü** menüsü.  
  
2.  Yeni adı çift **başlatmak hedef** genişletmek için iş akışı tasarımcısında durum.  
  
3.  Sürükle bir **atama** etkinliğinden **Temelleri** bölümünü **araç kutusu** üzerine bırakın **giriş** durumu bölümü. Tür `Target` içine **için** kutusu ve içine aşağıdaki ifade **bir C# ifadesi girin** veya **zadejte Výraz jazyka vb.** kutusu.  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  Varsa **araç kutusu** penceresi görüntülenmiyorsa, seçin **araç kutusu** gelen **görünümü** menüsü.  
  
4.  İade için genel durum makinesi iş akışı Tasarımcısı görünümünde tıklayarak **StateMachine** alan içerik haritasındaki iş akışı Tasarımcısı üst kısmında görüntüler.  
  
5.  Sürükle bir **durumu** etkinliğinden **Durum makinesi** bölümünü **araç kutusu** iş akışı tasarımcıya ve onu kutucuğunun üzerine gelin **hedefBaşlat** durumu. Dört üçgenler geçici olarak görüneceğini unutmayın **başlatmak hedef** üzerine yeni bir durum olduğunda durumu. Yeni durumunu hemen aşağıdadır üçgen bırak **başlatmak hedef** durumu. Bu iş akışı üzerine yeni durum yerleştirir ve bir geçiş oluşturur **başlatmak hedef** yeni durumu için durum.  
  
6.  Tıklayın **State1** seçmek için değiştirme **DisplayName** için `Enter Guess`ve genişletmek için iş akışı tasarımcısında durumu çift tıklayın.  
  
7.  Sürükle bir **WriteLine** etkinliğinden **Temelleri** bölümünü **araç kutusu** üzerine bırakın **giriş** durumu bölümü.  
  
8.  İçine aşağıdaki ifadeyi yazın **metin** özelliği **WriteLine**.  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
9. Sürükle bir **atama** etkinliğinden **Temelleri** bölümünü **araç kutusu** üzerine bırakın **çıkış** durumu bölümü.  
  
10. Tür `Turns` içine **için** kutusu ve `Turns + 1` içine **bir C# ifadesi girin** veya **zadejte Výraz jazyka vb.** kutusu.  
  
11. İade için genel durum makinesi iş akışı Tasarımcısı görünümünde tıklayarak **StateMachine** alan içerik haritasındaki iş akışı Tasarımcısı üst kısmında görüntüler.  
  
12. Sürükleme bir **FinalState** etkinliğinden **Durum makinesi** bölümünü **araç kutusu**, onu kutucuğunun üzerine gelin **girin tahmin** durum ve bırakın sağ tarafında görünür üçgen üzerine **girin tahmin** arasında geçiş oluşturulan durum **girin tahmin** ve **FinalState**.  
  
13. Geçiş varsayılan addır **T2**. Geçiş iş akışı tasarımcısında seçin ve ayarlamak için tıklayın, **DisplayName** için **doğru tahmin**. Ardından tıklayıp **FinalState**ve böylece ya da iki durum planlamanızda olmadan görüntülenecek tam geçiş adı için yer sağa sürükleyin. Bu öğreticinin geri kalan adımları tamamlamak kolaylaştırır.  
  
14. Yeni adı çift **doğru tahmin** genişletmek için iş akışı tasarımcısında geçiş.  
  
15. Sürükleme bir **readInt** etkinliğinden **NumberGuessWorkflowActivities** bölümünü **araç kutusu** sürükleyip **tetikleyici** bölümü geçişin.  
  
16. İçinde **Özellikler penceresi** için **readInt** etkinliği, türü `"EnterGuess"` tırnak işaretleri içine dahil **YerİşaretiAdı** özellik değer kutusu ile tür `Guess`içine **sonucu** özellik değer kutusu  
  
17. İçine aşağıdaki ifadeyi yazın **doğru tahmin** geçiş'ın **koşul** özellik değer kutusu.  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
18. İade için genel durum makinesi iş akışı Tasarımcısı görünümünde tıklayarak **StateMachine** alan içerik haritasındaki iş akışı Tasarımcısı üst kısmında görüntüler.  
  
    > [!NOTE]
    >  Bir geçiş Tetikleyici olayı alındığında gerçekleşir ve <xref:System.Activities.Statements.Transition.Condition%2A>, varsa, değerlendiren `True`. Bu geçiş için kullanıcının `Guess` rastgele oluşturulmuş eşleşen `Target`, Denetim geçer sonra **FinalState** ve iş akışının tamamlanmasının.  
  
19. Tahmin doğru olup olmamasına bağlı olarak, iş akışı ya da geçiş **FinalState** veya yeniden **girin tahmin** başka bir deneme için durum. Her iki geçişler aracılığıyla alınacak kullanıcının tahmin bekleniyor, aynı tetikleyici paylaşmak **readInt** etkinlik. Bu, paylaşılan bir geçiş adı verilir. Paylaşılan bir geçiş oluşturmak için başlangıcını gösteren daireye tıklayın **doğru tahmin** geçiş ve istenen duruma sürükleyin. Bu durumda geçiş kendi kendine bir geçiş, başlangıç noktası olarak bu nedenle sürükleyin **doğru tahmin** geçiş ve alt geri bırakın **girin tahmin** durumu. Geçiş oluşturduktan sonra iş akışı Tasarımcısı'nda seçin ve ayarlayın, **DisplayName** özelliğini **yanlış tahmin**.  
  
    > [!NOTE]
    >  Paylaşılan geçişleri de oluşturulabilir gelen geçiş Tasarımcısı'nda tıklayarak **paylaşılan tetikleyici geçişi Ekle** geçiş Tasarımcısı'nı seçip ardından istediğiniz hedef durumu alt kısmındaki  **Bağlanmak için kullanılabilir durumları** açılır.  
  
    > [!NOTE]
    >  Unutmayın <xref:System.Activities.Statements.Transition.Condition%2A> değerlendiren bir geçişin `false` (veya tüm koşulları bir paylaşılan tetikleyici geçişi için değerlendirmek `false`), geçiş gerçekleşmez ve tüm tetikleyiciler durumundan tüm geçişler için olacaktır işlemi yeniden zamanlanacak. Bu öğreticide, bu durum koşulları yapılandırılmış yol nedeniyle meydana olamaz (tahmin doğru veya yanlış olup belirli eylemler uyguluyoruz).  
  
20. Çift **yanlış tahmin** genişletmek için iş akışı tasarımcısında geçiş. Unutmayın **tetikleyici** aynı zaten ayarlanmış **readInt** tarafından kullanılan etkinlik **doğru tahmin** geçiş.  
  
21. İçine aşağıdaki ifadeyi yazın **koşul** özellik değer kutusu.  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
22. Sürükle bir **varsa** etkinliğinden **akış denetimi** bölümünü **araç kutusu** sürükleyip **eylem** geçişin bölümü.  
  
23. İçine aşağıdaki ifadeyi yazın **varsa** etkinliğin **koşul** özellik değer kutusu.  
  
    ```
    Guess < Target  
    ```  
  
24. İki **WriteLine** etkinlikten **Temelleri** bölümünü **araç kutusu** ve böylece bir yer bırakın **ardından** bölümü **varsa** etkinliği ve bir **Else** bölümü.  
  
25. Tıklayın **WriteLine** etkinliğinde **ardından** seçmek için bölüm ve içine aşağıdaki ifadeyi yazın **metin** özellik değer kutusu.  
  
    ```
    "Your guess is too low."  
    ```  
  
26. Tıklayın **WriteLine** etkinliğinde **Else** seçmek için bölüm ve içine aşağıdaki ifadeyi yazın **metin** özellik değer kutusu.  
  
    ```
    "Your guess is too high."  
    ```  
  
27. İade için genel durum makinesi iş akışı Tasarımcısı görünümünde tıklayarak **StateMachine** alan içerik haritasındaki iş akışı Tasarımcısı üst kısmında görüntüler.  
  
     Aşağıdaki örnekte, tamamlanmış bir iş akışı gösterilmektedir.  
  
     ![Durum makinesi iş akışı tamamlandı](./media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")  
  
### <a name="to-build-the-workflow"></a>İş akışı oluşturmak için  
  
1.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
     Lütfen iş akışının nasıl çalıştırılacağını yönergeleri görmek için bir sonraki konu [nasıl yapılır: İş akışı çalıştırma](how-to-run-a-workflow.md). Zaten tamamladıysanız [nasıl yapılır: İş akışı çalıştırma](how-to-run-a-workflow.md) adım iş akışı farklı bir stil ve çalıştırmak bu adım durum makine iş akışını kullanarak istediğiniz, atlayın [uygulaması derleme ve çalıştırma için](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) bölümünü [nasıl yapılır: İş akışı çalıştırma](how-to-run-a-workflow.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [Windows Workflow Foundation Programlama](programming.md)
- [İş Akışları Tasarlama](designing-workflows.md)
- [Başlangıç Öğreticisi](getting-started-tutorial.md)
- [Nasıl yapılır: Bir etkinlik oluşturma](how-to-create-an-activity.md)
- [Nasıl yapılır: İş akışı çalıştırma](how-to-run-a-workflow.md)
