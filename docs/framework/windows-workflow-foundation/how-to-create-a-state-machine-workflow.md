---
title: 'Nasıl yapılır: Durum Makinesi İş Akışı Oluşturma'
description: Bu makale, StateMachine etkinliği ve özel etkinlikler gibi yerleşik etkinlikleri kullanan bir iş akışı oluşturur.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3ec60e8f-fad4-493e-a426-e7962d7aee8c
ms.openlocfilehash: 8a9342c07c15d65df0310c0cb35b4b2c6f2ba686
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419661"
---
# <a name="how-to-create-a-state-machine-workflow"></a>Nasıl yapılır: Durum Makinesi İş Akışı Oluşturma
İş akışları, yerleşik etkinliklerin yanı sıra özel etkinliklerden de oluşturulabilir. Bu konu, etkinlik gibi yerleşik etkinlikleri <xref:System.Activities.Statements.StateMachine> ve önceki [nasıl yapılır: etkinlik oluşturma](how-to-create-an-activity.md) konusunun özel etkinliklerini kullanan bir iş akışı oluşturmaya yönelik adımları açıklamaktadır. İş akışı, sayıyı tahmin eden bir oyunu modelleyen.  
  
> [!NOTE]
> Başlangıç öğreticisindeki her konu, önceki konulara bağlıdır. Bu konuyu tamamlayabilmeniz için öncelikle [nasıl yapılır: etkinlik oluşturma](how-to-create-an-activity.md)' yı tamamlamalısınız.  
  
> [!NOTE]
> Öğreticinin tamamlanmış bir sürümünü indirmek için, bkz. [Windows Workflow Foundation (WF45)-Başlangıç Öğreticisi](https://go.microsoft.com/fwlink/?LinkID=248976).  
  
### <a name="to-create-the-workflow"></a>İş akışını oluşturmak için  
  
1. **Çözüm Gezgini** 'de **NumberGuessWorkflowActivities** öğesine sağ tıklayın ve **Ekle**, **Yeni öğe**' yi seçin.  
  
2. **Yüklü**, **ortak öğeler** düğümünde **iş akışı**' nı seçin. **Iş akışı** listesinden **etkinlik** ' i seçin.  
  
3. `StateMachineNumberGuessWorkflow` **Ad** kutusuna yazın ve **Ekle**' ye tıklayın.  
  
4. **Araç kutusunun** **durum makinesi** ' nden bir **StateMachine** etkinliğini sürükleyin ve iş akışı tasarım yüzeyinde **buraya bırakma etkinliği** etiketini bırakın.  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a>İş akışı değişkenlerini ve bağımsız değişkenleri oluşturmak için  
  
1. Henüz görüntülenmiyorsa, iş akışını tasarımcıda göstermek için **Çözüm Gezgini** Içindeki **StateMachineNumberGuessWorkflow. xaml** öğesine çift tıklayın.  
  
2. **Bağımsız değişkenler** bölmesini göstermek için iş akışı Tasarımcısı ' nın sol alt tarafındaki **bağımsız değişkenler** ' e tıklayın.  
  
3. **Bağımsız değişken Oluştur**' a tıklayın.  
  
4. `MaxNumber` **Ad** kutusuna yazın, **Yön** açılan listesinden **'** i seçin, **bağımsız değişken türü** açılan listesinden **ıNT32** ' i seçin ve ardından bağımsız değişkeni kaydetmek için ENTER tuşuna basın.  
  
5. **Bağımsız değişken Oluştur**' a tıklayın.  
  
6. `Turns`Yeni eklenen bağımsız değişkenin altında bulunan **ad** kutusuna yazın `MaxNumber` , **Yön** açılan listesinden Seç **Out** ' i seçin, **bağımsız değişken türü** açılan listesinden **Int32** ' i seçin ve ardından ENTER tuşuna basın.  
  
7. **Bağımsız değişkenler** bölmesini kapatmak için etkinlik tasarımcısının sol alt tarafındaki **bağımsız değişkenler** ' e tıklayın.  
  
8. **Değişkenler** bölmesini göstermek için iş akışı Tasarımcısı ' nın sol alt tarafındaki **değişkenler** ' e tıklayın.  
  
9. **Değişken Oluştur**' a tıklayın.  
  
    > [!TIP]
    > **Değişken Oluştur** kutusu görüntülenmiyorsa, <xref:System.Activities.Statements.StateMachine> iş akışı Tasarımcısı yüzeyinde etkinlik ' i tıklatarak seçin.  
  
10. `Guess` **Ad** kutusuna yazın, **değişken türü** açılır listesinden **Int32** ' i seçin ve ardından değişkeni kaydetmek için ENTER tuşuna basın.  
  
11. **Değişken Oluştur**' a tıklayın.  
  
12. `Target` **Ad** kutusuna yazın, **değişken türü** açılır listesinden **Int32** ' i seçin ve ardından değişkeni kaydetmek için ENTER tuşuna basın.  
  
13. **Değişkenler** bölmesini kapatmak için etkinlik tasarımcısının sol alt tarafındaki **değişkenler** ' e tıklayın.  
  
### <a name="to-add-the-workflow-activities"></a>İş akışı etkinliklerini eklemek için  
  
1. Seçmek için **State1** öğesine tıklayın. **Özellikler penceresinde** **DisplayName** olarak değiştirin `Initialize Target` .  
  
    > [!TIP]
    > **Özellikler penceresi** görüntülenmiyorsa, **Görünüm** menüsünden **Özellikler penceresi** ' ni seçin.  
  
2. İş akışı tasarımcısında yeni yeniden adlandırılmış **başlatma hedefini** açmak için çift tıklayın.  
  
3. **Araç kutusunun** **temel öğeler** bölümünden bir **atama** etkinliği sürükleyin ve durumun **giriş** bölümüne bırakın. `Target` **Bir C# ifadesi girin** veya bir **vb ifadesi girin** kutusuna **to** kutusuna ve aşağıdaki ifadeye yazın.  
  
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
  
6. Seçmek için **State1** ' e tıklayın, **DisplayName** olarak değiştirin `Enter Guess` ve ardından iş akışı tasarımcısında duruma çift tıklayarak genişletin.  
  
7. **Araç kutusunun** **temel öğeler** bölümünden bir **WriteLine** etkinliği sürükleyin ve durumun **giriş** bölümüne bırakın.  
  
8. **WriteLine**'ın **Text** özellik kutusuna aşağıdaki ifadeyi yazın.  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
9. **Araç kutusu** ' nu **temel elemanlar** bölümünden bir **atama** etkinliği sürükleyin ve durumun **Çıkış** bölümüne bırakın.  
  
10. `Turns` **To** kutusuna ve `Turns + 1` **bir C# IFADESI girin** veya **bir vb ifadesi kutusu girin** .  
  
11. İş akışı Tasarımcısı ' nın en üstünde bulunan içerik haritası ' nda **StateMachine** ' e tıklayarak iş akışı tasarımcısında genel durum makinesi görünümüne geri dönün.  
  
12. **Araç kutusunun** **durum makinesi** ' nden bir **FinalState** etkinliği sürükleyin **, tahmin etme** durumunun üzerine gelin ve **tahmin ve** **sonlandırmasız**değer arasında bir geçiş oluşturulacak şekilde, **tahmin durumu gir** ' in sağında görüntülenen üçgenin üzerine bırakın.  
  
13. Geçişin varsayılan adı **T2**'dir. İş akışı tasarımcısında geçişe tıklayarak seçin ve **DisplayName** değerini **tahmin**olarak ayarlayın. Ardından, **sonlandırıdurumu**' na tıklayıp seçin ve tam geçiş adının iki durumdan birinin üzerine bulunmadığından görüntülenecek bir oda olması için sağa sürükleyin. Bu, öğreticideki kalan adımların tamamlanmasını daha kolay hale getirir.  
  
14. İş akışı tasarımcısında yeni yeniden adlandırılmış **tahmin doğru** geçişine çift tıklayarak genişletin.  
  
15. **Araç kutusunun** **NumberGuessWorkflowActivities** bölümünden **readInt** etkinliğini sürükleyin ve geçişin **tetikleyici** bölümüne bırakın.  
  
16. **ReadInt** etkinliğinin **Özellikler penceresinde** , `"EnterGuess"` tırnak işareti **adı** Özellik değeri kutusuna tırnak işareti dahil yazın ve `Guess` **sonuç** özelliği değeri kutusuna yazın  
  
17. **Tahmin doğru** geçişinin **koşul** özelliği değeri kutusuna aşağıdaki ifadeyi yazın.  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
18. İş akışı Tasarımcısı ' nın en üstünde bulunan içerik haritası ' nda **StateMachine** ' e tıklayarak iş akışı tasarımcısında genel durum makinesi görünümüne geri dönün.  
  
    > [!NOTE]
    > Tetikleyici olayı alındığında ve varsa, olarak değerlendirilen bir geçiş gerçekleşir <xref:System.Activities.Statements.Transition.Condition%2A> `True` . Bu geçiş için, Kullanıcı `Guess` rastgele oluşturulmuş ile eşleşiyorsa `Target` Denetim **sonlandırna** geçer ve iş akışı tamamlanır.  
  
19. Tahminin doğru olup olmadığına bağlı olarak, iş akışı, başka bir TRY için **FinalState** 'e ya da tahmin durumuna **gir** 'e geçiş yapılmalıdır. Her iki geçiş de, kullanıcının tahminin **readInt** etkinliği aracılığıyla alınması için bekleyen tetikleyiciyi paylaşır. Buna paylaşılan geçiş adı verilir. Paylaşılan bir geçiş oluşturmak için, **tahmin doğru** geçişinin başlangıcını belirten daireye tıklayın ve istediğiniz duruma sürükleyin. Bu durumda, geçiş bir kendinden geçiştir, bu nedenle **tahmin doğru** geçişinin başlangıç noktasını sürükleyin ve **tahmin** durumunun sonuna geri bırakın. Geçişi oluşturduktan sonra iş akışı tasarımcısında seçin ve **DisplayName** özelliğini **tahmin yanlış**olarak ayarlayın.  
  
    > [!NOTE]
    > Paylaşılan geçişler, geçiş Tasarımcısı ' nın altında **Paylaşılan tetikleyici geçişi ekle** ' ye tıklayarak geçiş Tasarımcısı içinden de oluşturulabilir ve sonra, bağlantı açılan listesinden, **kullanılabilir durumlar** ' da istenen hedef durumu seçebilirsiniz.  
  
    > [!NOTE]
    > <xref:System.Activities.Statements.Transition.Condition%2A>Bir geçiş işleminin `false` (veya paylaşılan bir tetikleyici geçişinin tüm koşullarını değerlendirmesi `false` ) değerlendirilirse, geçişin gerçekleşmeyeceğini ve durumdan gelen tüm geçişlerin her tetikleyicisinin yeniden planlanacağını unutmayın. Bu öğreticide, koşulların yapılandırıldığı şekilde bu durum gerçekleşmemelidir (tahminin doğru veya hatalı olması için özel eylemlerdir).  
  
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
  
    ```text
    Guess < Target
    ```  
  
24. **Araç kutusu** ' **nu** **temel elemanlar** bölümünden iki **WriteLine** etkinliği sürükleyin ve bir tane, bir diğeri **ise** **Else** bölümünde olacak şekilde bırakın.  
  
25. **Daha sonra** seçmek Için bölümünde **WriteLine** etkinliğine tıklayın ve **metin** özelliği değeri kutusuna aşağıdaki ifadeyi yazın.  
  
    ```text
    "Your guess is too low."  
    ```  
  
26. Bunu seçmek için **Else** bölümünde **WriteLine** etkinliğine tıklayın ve **metin** özelliği değeri kutusuna aşağıdaki ifadeyi yazın.  
  
    ```text
    "Your guess is too high."  
    ```  
  
27. İş akışı Tasarımcısı ' nın en üstünde bulunan içerik haritası ' nda **StateMachine** ' e tıklayarak iş akışı tasarımcısında genel durum makinesi görünümüne geri dönün.  
  
     Aşağıdaki örnekte tamamlanan iş akışı gösterilmektedir.  
  
     ![Tamamlanan durum makinesi iş akışını gösteren çizim.](./media/how-to-create-a-state-machine-workflow/complete-state-machine-workflow.jpg)  
  
### <a name="to-build-the-workflow"></a>İş akışını derlemek için  
  
1. Çözümü derlemek için CTRL+SHIFT+B'ye basın.  
  
     İş akışının nasıl çalıştırılacağı hakkında yönergeler için, bkz. [nasıl yapılır: Iş akışını çalıştırma](how-to-run-a-workflow.md). [Nasıl yapılır: bir](how-to-run-a-workflow.md) iş akışı adımını farklı bir iş akışı ile çalıştırma ve bu adımdaki durum makinesi iş akışını kullanarak çalıştırmak istediğinizde, nasıl [yapılır: iş akışı çalıştırma](how-to-run-a-workflow.md)konusunun [Uygulama bölümünü derlemek ve çalıştırmak için](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) ' a atlayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [Windows Workflow Foundation Programlama](programming.md)
- [İş Akışları Tasarlama](designing-workflows.md)
- [Başlangıç Öğreticisi](getting-started-tutorial.md)
- [Nasıl Yapılır: Etkinlik Oluşturma](how-to-create-an-activity.md)
- [Nasıl yapılır: İş Akışı Çalıştırma](how-to-run-a-workflow.md)
