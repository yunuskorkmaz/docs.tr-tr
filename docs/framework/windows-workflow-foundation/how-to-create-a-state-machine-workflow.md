---
title: 'Nasıl yapılır: Durum Makinesi İş Akışı Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3ec60e8f-fad4-493e-a426-e7962d7aee8c
ms.openlocfilehash: 451f9581ae997ad86fee968fa978713db2049455
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044395"
---
# <a name="how-to-create-a-state-machine-workflow"></a>Nasıl yapılır: Durum Makinesi İş Akışı Oluşturma
İş akışları, yerleşik etkinliklerin yanı sıra özel etkinliklerden de oluşturulabilir. Bu konu, <xref:System.Activities.Statements.StateMachine> etkinlik gibi yerleşik etkinlikleri ve önceki [nasıl yapılacağı özel etkinlikleri kullanan bir iş akışı oluşturma ile ilgili adımları izleyerek yapılır: Etkinlik](how-to-create-an-activity.md) konusu oluşturun. İş akışı, sayıyı tahmin eden bir oyunu modelleyen.  
  
> [!NOTE]
> Başlangıç öğreticisindeki her konu, önceki konulara bağlıdır. Bu konuyu tamamlayabilmeniz için öncelikle [şunları yapmanız gerekir: Etkinlik](how-to-create-an-activity.md)oluşturun.  
  
> [!NOTE]
> Öğreticinin tamamlanmış bir sürümünü indirmek için, bkz. [Windows Workflow Foundation (WF45)-Başlangıç Öğreticisi](https://go.microsoft.com/fwlink/?LinkID=248976).  
  
### <a name="to-create-the-workflow"></a>İş akışını oluşturmak için  
  
1. **Çözüm Gezgini** 'de **NumberGuessWorkflowActivities** öğesine sağ tıklayın ve **Ekle**, **Yeni öğe**' yi seçin.  
  
2. **Yüklü**, **ortak öğeler** düğümünde **iş akışı**' nı seçin. **Iş akışı** listesinden **etkinlik** ' i seçin.  
  
3. Ad `StateMachineNumberGuessWorkflow` kutusuna yazın ve **Ekle**' ye tıklayın.  
  
4. **Araç kutusunun** **durum makinesi** ' nden bir **StateMachine** etkinliğini sürükleyin ve iş akışı tasarım yüzeyinde **buraya bırakma etkinliği** etiketini bırakın.  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a>İş akışı değişkenlerini ve bağımsız değişkenleri oluşturmak için  
  
1. Henüz görüntülenmiyorsa, iş akışını tasarımcıda göstermek için **Çözüm Gezgini** Içindeki **StateMachineNumberGuessWorkflow. xaml** öğesine çift tıklayın.  
  
2. **Bağımsız değişkenler** bölmesini göstermek için iş akışı Tasarımcısı ' nın sol alt tarafındaki **bağımsız değişkenler** ' e tıklayın.  
  
3. **Bağımsız değişken Oluştur**' a tıklayın.  
  
4. Ad `MaxNumber` kutusuna yazın , **Yön** açılan listesinden **'** i seçin, **bağımsız değişken türü** açılan listesinden **Int32** ' i seçin ve ardından bağımsız değişkeni kaydetmek için ENTER tuşuna basın.  
  
5. **Bağımsız değişken Oluştur**' a tıklayın.  
  
6. Yeni `Turns` eklenen bağımsız`MaxNumber` değişkenin altında bulunan ad kutusuna yazın, Yön açılan listesinden Seç ' i seçin, **bağımsız değişken türü** açılan listesinden Int32 ' i seçin ve ardından ENTER tuşuna basın.  
  
7. **Bağımsız değişkenler** bölmesini kapatmak için etkinlik tasarımcısının sol alt tarafındaki **bağımsız değişkenler** ' e tıklayın.  
  
8. **Değişkenler** bölmesini göstermek için iş akışı Tasarımcısı ' nın sol alt tarafındaki **değişkenler** ' e tıklayın.  
  
9. **Değişken Oluştur**' a tıklayın.  
  
    > [!TIP]
    > **Değişken Oluştur** kutusu görüntülenmiyorsa, iş akışı Tasarımcısı yüzeyinde <xref:System.Activities.Statements.StateMachine> etkinlik ' i tıklatarak seçin.  
  
10. Ad `Guess` kutusuna yazın , **değişken türü** açılır listesinden **Int32** ' i seçin ve ardından değişkeni kaydetmek için ENTER tuşuna basın.  
  
11. **Değişken Oluştur**' a tıklayın.  
  
12. Ad `Target` kutusuna yazın , **değişken türü** açılır listesinden **Int32** ' i seçin ve ardından değişkeni kaydetmek için ENTER tuşuna basın.  
  
13. **Değişkenler** bölmesini kapatmak için etkinlik tasarımcısının sol alt tarafındaki **değişkenler** ' e tıklayın.  
  
### <a name="to-add-the-workflow-activities"></a>İş akışı etkinliklerini eklemek için  
  
1. Seçmek için **State1** öğesine tıklayın. **Özellikler penceresinde** **DisplayName** olarak `Initialize Target`değiştirin.  
  
    > [!TIP]
    > **Özellikler penceresi** görüntülenmiyorsa, **Görünüm** menüsünden **Özellikler penceresi** ' ni seçin.  
  
2. İş akışı tasarımcısında yeni yeniden adlandırılmış **başlatma hedefini** açmak için çift tıklayın.  
  
3. **Araç kutusunun** **temel öğeler** bölümünden bir **atama** etkinliği sürükleyin ve durumun **giriş** bölümüne bırakın. Buraya `Target` yazın veya bir  **C# ifade girin** veya bir **vb ifadesi girin** .  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    > **Araç kutusu** penceresi görüntülenmiyorsa, **Görünüm** menüsünden **araç kutusu** ' nu seçin.  
  
4. İş akışı Tasarımcısı ' nın en üstünde bulunan içerik haritası ' nda **StateMachine** ' e tıklayarak iş akışı tasarımcısında genel durum makinesi görünümüne geri dönün.  
  
5. **Araç kutusunun** **durum makinesi** bölümünden bir **durum** etkinliğini, Iş akışı tasarımcısına sürükleyin ve **hedefi başlatma** durumuna getirin. Yeni durum bunun üzerinde olduğunda, **hedefi Başlat** durumunun etrafında dört üçgenin görüneceğini unutmayın. Yeni durumu, **başlatma hedefi** durumunun hemen altındaki üçgende bırakın. Bu, yeni durumu iş akışına koyar ve **hedef başlatma** durumundan yeni duruma bir geçiş oluşturur.  
  
6. Seçmek için **State1** ' e tıklayın, **DisplayName** olarak `Enter Guess`değiştirin ve ardından iş akışı tasarımcısında duruma çift tıklayarak genişletin.  
  
7. **Araç kutusunun** **temel öğeler** bölümünden bir **WriteLine** etkinliği sürükleyin ve durumun **giriş** bölümüne bırakın.  
  
8. **WriteLine**'ın **Text** özellik kutusuna aşağıdaki ifadeyi yazın.  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
9. **Araç kutusu** ' nu **temel elemanlar** bölümünden bir **atama** etkinliği sürükleyin ve durumun **Çıkış** bölümüne bırakın.  
  
10. To `Turns` kutusuna ve `Turns + 1` **bir C# ifade girin** veya bir **vb ifadesi girin** kutusuna yazın.  
  
11. İş akışı Tasarımcısı ' nın en üstünde bulunan içerik haritası ' nda **StateMachine** ' e tıklayarak iş akışı tasarımcısında genel durum makinesi görünümüne geri dönün.  
  
12. **Araç kutusunun** **durum makinesi** bölümünden bir **FinalState** etkinliği sürükleyin, **tahmin** etme durumunun üzerine gelin ve bir geçişin doğru olması için **tahmin** durumunun sağında görüntülenen üçgene bırakın **ENTER tahmini** ve **FinalState**arasında oluşturulur.  
  
13. Geçişin varsayılan adı **T2**'dir. İş akışı tasarımcısında geçişe tıklayarak seçin ve **DisplayName** değerini **tahmin**olarak ayarlayın. Ardından, **sonlandırıdurumu**' na tıklayıp seçin ve tam geçiş adının iki durumdan birinin üzerine bulunmadığından görüntülenecek bir oda olması için sağa sürükleyin. Bu, öğreticideki kalan adımların tamamlanmasını daha kolay hale getirir.  
  
14. İş akışı tasarımcısında yeni yeniden adlandırılmış **tahmin doğru** geçişine çift tıklayarak genişletin.  
  
15. **Araç kutusunun** **NumberGuessWorkflowActivities** bölümünden **readInt** etkinliğini sürükleyin ve geçişin **tetikleyici** bölümüne bırakın.  
  
16. **ReadInt** `"EnterGuess"` etkinliğinin **Özellikler penceresinde** , tırnak işareti **adı** Özellik değeri kutusuna tırnak işareti dahil yazın ve `Guess` **sonuç** özelliği değeri kutusuna yazın  
  
17. **Tahmin doğru** geçişinin **koşul** özelliği değeri kutusuna aşağıdaki ifadeyi yazın.  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
18. İş akışı Tasarımcısı ' nın en üstünde bulunan içerik haritası ' nda **StateMachine** ' e tıklayarak iş akışı tasarımcısında genel durum makinesi görünümüne geri dönün.  
  
    > [!NOTE]
    > Tetikleyici olayı alındığında ve <xref:System.Activities.Statements.Transition.Condition%2A>varsa, olarak `True`değerlendirilen bir geçiş gerçekleşir. Bu geçiş için, Kullanıcı `Guess` rastgele oluşturulmuş `Target`ile eşleşiyorsa denetim **sonlandırna** geçer ve iş akışı tamamlanır.  
  
19. Tahminin doğru olup olmadığına bağlı olarak, iş akışı, başka bir TRY için **FinalState** 'e ya da tahmin durumuna **gir** 'e geçiş yapılmalıdır. Her iki geçiş de, kullanıcının tahminin **readInt** etkinliği aracılığıyla alınması için bekleyen tetikleyiciyi paylaşır. Buna paylaşılan geçiş adı verilir. Paylaşılan bir geçiş oluşturmak için, **tahmin doğru** geçişinin başlangıcını belirten daireye tıklayın ve istediğiniz duruma sürükleyin. Bu durumda, geçiş bir kendinden geçiştir, bu nedenle **tahmin doğru** geçişinin başlangıç noktasını sürükleyin ve **tahmin** durumunun sonuna geri bırakın. Geçişi oluşturduktan sonra iş akışı tasarımcısında seçin ve **DisplayName** özelliğini **tahmin yanlış**olarak ayarlayın.  
  
    > [!NOTE]
    > Paylaşılan geçişler, geçiş Tasarımcısı ' nın altında **Paylaşılan tetikleyici geçişi ekle** ' ye tıklayıp, ardından **bağlantı kurmak için kullanılabilir durumlar** ' da istenen hedef durumu seçilerek geçiş Tasarımcısı içinden da oluşturulabilir açılır liste.  
  
    > [!NOTE]
    > Bir geçiş `false` `false`işleminin (veya paylaşılan bir tetikleyici geçişinin tüm koşullarını değerlendirmesi) değerlendirilirse, geçişin gerçekleşmeyeceğini ve durumdan gelen tüm geçişler için tüm tetikleyicilerinin olacağını unutmayın. <xref:System.Activities.Statements.Transition.Condition%2A> zamanlandı. Bu öğreticide, koşulların yapılandırıldığı şekilde bu durum gerçekleşmemelidir (tahminin doğru veya hatalı olması için özel eylemlerdir).  
  
20. İş akışı tasarımcısında **tahmin yanlış** geçişine çift tıklayarak genişletin. **Tetikleyicinin** , **tahmin doğru** geçişi tarafından kullanılan **readInt** etkinliğine zaten ayarlanmış olduğunu unutmayın.  
  
21. **Koşul** özelliği değeri kutusuna aşağıdaki ifadeyi yazın.  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
22. **Araç kutusunun** **Denetim akışı** bölümünden bir **IF** etkinliği sürükleyin ve geçişin **eylem** bölümüne bırakın.  
  
23. **IF** etkinliğinin **koşul** özelliği değeri kutusuna aşağıdaki ifadeyi yazın.  
  
    ```
    Guess < Target  
    ```  
  
24. **Araç kutusu** ' **nu** **temel elemanlar** bölümünden iki **WriteLine** etkinliği sürükleyin ve bir tane, bir diğeri **ise** **Else** bölümünde olacak şekilde bırakın.  
  
25. **Daha sonra** seçmek Için bölümünde **WriteLine** etkinliğine tıklayın ve **metin** özelliği değeri kutusuna aşağıdaki ifadeyi yazın.  
  
    ```
    "Your guess is too low."  
    ```  
  
26. Bunu seçmek için **Else** bölümünde **WriteLine** etkinliğine tıklayın ve **metin** özelliği değeri kutusuna aşağıdaki ifadeyi yazın.  
  
    ```
    "Your guess is too high."  
    ```  
  
27. İş akışı Tasarımcısı ' nın en üstünde bulunan içerik haritası ' nda **StateMachine** ' e tıklayarak iş akışı tasarımcısında genel durum makinesi görünümüne geri dönün.  
  
     Aşağıdaki örnekte tamamlanan iş akışı gösterilmektedir.  
  
     ![Tamamlanan durum makinesi iş akışını gösteren çizim.](./media/how-to-create-a-state-machine-workflow/complete-state-machine-workflow.jpg)  
  
### <a name="to-build-the-workflow"></a>İş akışını derlemek için  
  
1. Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
     İş akışının nasıl çalıştırılacağı hakkında yönergeler için lütfen sonraki konuya [bakın: Bir Iş akışı](how-to-run-a-workflow.md)çalıştırın. ' Nin [nasıl yapılacağını zaten tamamladıysanız: Farklı bir iş](how-to-run-a-workflow.md) akışı stiliyle iş akışı adımı çalıştırın ve bu adımda durum makinesi iş akışını kullanarak çalıştırmak istiyorsanız, [](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) [nasıl yapılır: Bir Iş akışı](how-to-run-a-workflow.md)çalıştırın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [Windows Workflow Foundation Programlama](programming.md)
- [İş Akışları Tasarlama](designing-workflows.md)
- [Başlangıç Öğreticisi](getting-started-tutorial.md)
- [Nasıl yapılır: Etkinlik oluşturma](how-to-create-an-activity.md)
- [Nasıl yapılır: Iş akışı çalıştırma](how-to-run-a-workflow.md)
