---
title: 'Nasıl yapılır: bir etkinliği oluşturma'
ms.date: 09/14/2018
dev_langs:
- csharp
- vb
ms.assetid: c09b1e99-21b5-4d96-9c04-ec31db3f4436
ms.openlocfilehash: 8aa6900b26bbe9f77fe0802a7929febe5af61269
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48779913"
---
# <a name="how-to-create-an-activity"></a>Nasıl yapılır: bir etkinliği oluşturma

Etkinlikleri olan çekirdek birimi davranış [!INCLUDE[wf1](../../../includes/wf1-md.md)]. Bir etkinlik yürütülme mantığı yönetilen kodda uygulanabilir veya diğer etkinlikleri kullanarak uygulanabilir. Bu konu, iki etkinliği oluşturma işlemini gösterir. İlk Etkinlik yürütme mantığını uygulamak için kodu kullanan basit bir etkinliktir. İkinci etkinlik uygulaması, diğer etkinlikleri kullanarak tanımlanır. Bu etkinlikler, aşağıdaki adımlarda öğreticide kullanılır.

> [!NOTE]
> Öğreticinin tamamlanmış bir sürümünü indirmek için bkz [Windows Workflow Foundation (WF45) - başlangıç Öğreticisi](https://go.microsoft.com/fwlink/?LinkID=248976).

## <a name="create-the-activity-library-project"></a>Etkinlik kitaplığı projesi oluşturun

1.  Visual Studio açıp seçin **yeni** > **proje** gelen **dosya** menüsü.

2.  İçinde **yeni proje** iletişim altında **yüklü** kategorisi, select **Visual C#** > **iş akışı** (veya **Visual Basic** > **iş akışı**).

    > [!NOTE]
    > Görmüyorsanız **iş akışı** şablon kategorisi yüklemeniz gerekebilir **Windows Workflow Foundation** Visual Studio bileşen. Seçin **açık Visual Studio yükleyicisi** sol tarafındaki bağlantıyı **yeni proje** iletişim. Visual Studio Yükleyicisi'nde seçin **tek tek bileşenler** sekmesi. Ardından, altında **geliştirme etkinliklerini** kategorisi seçin **Windows Workflow Foundation** bileşeni. Seçin **Değiştir** bileşeni.

3. Seçin **etkinlik Kitaplığı** proje şablonu. Tür `NumberGuessWorkflowActivities` içinde **adı** kutusuna ve ardından **Tamam**.

4.  Sağ **gt;activity1.XAML** içinde **Çözüm Gezgini** ve **Sil**. Tıklayın **Tamam** onaylamak için.

## <a name="create-the-readint-activity"></a>ReadInt etkinliği oluşturma

1.  Seçin **Yeni Öğe Ekle** gelen **proje** menüsü.

2.  İçinde **yüklü** > **ortak öğeler** düğümünü **iş akışı**. Seçin **kod etkinliği** gelen **iş akışı** listesi.

3.  Tür `ReadInt` içine **adı** kutusuna ve ardından **Ekle**.

4.  Varolan `ReadInt` aşağıdaki tanımını tanımıyla.

     [!code-csharp[CFX_WF_GettingStarted#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/readint.cs#1)]
     [!code-vb[CFX_WF_GettingStarted#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/readint.vb#1)]

    > [!NOTE]
    > `ReadInt` Etkinlik türetilir <xref:System.Activities.NativeActivity%601> yerine <xref:System.Activities.CodeActivity>, kod etkinlik şablonu için varsayılan değerdir. <xref:System.Activities.CodeActivity%601> Etkinlik aracılığıyla sunulan tek bir sonuç sağlıyorsa kullanılabilir <xref:System.Activities.Activity%601.Result%2A> bağımsız değişkeni, ancak <xref:System.Activities.CodeActivity%601> kullanımı yer işaretleri, bu nedenle desteklemiyor <xref:System.Activities.NativeActivity%601> kullanılır.

## <a name="create-the-prompt-activity"></a>Komut istemi etkinliği oluşturma

1.  Tuşuna **Ctrl**+**Shift**+**B** Projeyi derlemek için. Proje etkinleştirir oluşturmaya `ReadInt` etkinlik bu projede Bu adımdan özel etkinlik oluşturmak için kullanılacak.

2.  Seçin **Yeni Öğe Ekle** gelen **proje** menüsü.

3.  İçinde **yüklü** > **ortak öğeler** düğümünü **iş akışı**. Seçin **etkinlik** gelen **iş akışı** listesi.

4.  Tür `Prompt` içine **adı** kutusuna ve ardından **Ekle**.

5.  Çift **Prompt.xaml** içinde **Çözüm Gezgini** zaten görüntülenmiyorsa, tasarımcıda görüntülenecek.

6.  Tıklayın **bağımsız değişkenleri** sol alt tarafında görüntülenecek etkinlik Tasarımcısı **bağımsız değişkenleri** bölmesi.

7.  Tıklayın **bağımsız değişken oluşturma**.

8.  Tür `BookmarkName` içine **adı** kutusunda **içinde** gelen **yönü** aşağı açılan listesinden **dize** gelen**Bağımsız değişken türü** aşağı açılan liste ve ENTER tuşuna **Enter** bağımsız değişkeni kaydetmek için.

9. Tıklayın **bağımsız değişken oluşturma**.

10. Tür `Result` içine **adı** altında yeni eklenen kutusunu `BookmarkName` bağımsız değişkeni, select **kullanıma** gelen **yönü** aşağı açılan listesinde seçin **Int32** gelen **bağımsız değişken türü** aşağı açılan liste ve ENTER tuşuna **Enter**.

11. Tıklayın **bağımsız değişken oluşturma**.

12. Tür `Text` içine **adı** kutusunda **içinde** gelen **yönü** aşağı açılan listesinden **dize** gelen**Bağımsız değişken türü** aşağı açılan liste ve ENTER tuşuna **Enter** bağımsız değişkeni kaydetmek için.

     Bu üç bağımsız değişken için karşılık gelen bağımsız bağlı <xref:System.Activities.Statements.WriteLine> ve `ReadInt` eklenen etkinlikler `Prompt` aşağıdaki adımlarda etkinlik.

13. Tıklayın **bağımsız değişkenleri** etkinlik Tasarımcısı kapatmak için sol alt tarafında **bağımsız değişkenleri** bölmesi.

14. Sürükle bir **dizisi** etkinliğinden **akış denetimi** bölümünü **araç kutusu** üzerine bırakın **Buraya Bırak etkinlik** etiketi **İstemi** etkinlik Tasarımcısı.

    > [!TIP]
    > Varsa **araç kutusu** penceresi görüntülenmiyorsa, seçin **araç kutusu** gelen **görünümü** menüsü.

15. Sürükle bir **WriteLine** etkinliğinden **Temelleri** bölümünü **araç kutusu** üzerine bırakın **Buraya Bırak etkinlik** etiketi **Dizisi** etkinlik.

16. Bağlama **metin** bağımsız değişkeni **WriteLine** etkinliğini **metin** bağımsız değişkeni **istemi** yazarak etkinlik `Text` içine **bir C# ifadesi girin** veya **zadejte Výraz jazyka vb.** kutusunda **özellikleri** penceresi ve ENTER tuşuna **sekmesini** iki kez anahtarı. Bu, IntelliSense listesi üyeleri penceresi kapatılır ve özellik değeri özelliği devre dışı seçim taşıyarak kaydeder. Bu özellik ayrıca yazarak ayarlanabilir `Text` içine **bir C# ifadesi girin** veya **zadejte Výraz jazyka vb.** etkinlik çubuğundaki.

    > [!TIP]
    > Varsa **Özellikler penceresi** görüntülenen, select değil **Özellikler penceresi** gelen **görünümü** menüsü.

17. Sürükleme bir **readInt** etkinliğinden **NumberGuessWorkflowActivities** bölümünü **araç kutusu** sürükleyip **dizisi** Böylece onun etkinlik **WriteLine** etkinlik.

18. Bağlama **YerİşaretiAdı** bağımsız değişkeni **readInt** etkinliğini **YerİşaretiAdı** bağımsız değişkeni **istemi** yazaraketkinliği`BookmarkName` içine **zadejte Výraz jazyka vb.** kutusunun sağındaki **YerİşaretiAdı** değişkeninde **Özellikler penceresi**ve tuşuna**Sekmesini** anahtar IntelliSense liste üyelerini penceresini kapatın ve özelliğini kaydetmek için iki kez.

19. Bağlama **sonucu** bağımsız değişkeni **readInt** etkinliğini **sonucu** bağımsız değişkeni **istemi** yazarak etkinlik `Result` içine **zadejte Výraz jazyka vb.** kutusunun sağındaki **sonucu** değişkeninde **Özellikler penceresi**ve tuşuna **sekmesi** anahtar iki kez.

20. Tuşuna **Ctrl**+**Shift**+**B** çözümü derlemek için.

## <a name="next-steps"></a>Sonraki adımlar

Öğreticide, bir sonraki adım için bkz. Bu etkinlikleri kullanarak bir iş akışı oluşturmak yönergeler [nasıl yapılır: bir iş akışı oluşturmak](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Activities.CodeActivity>
- <xref:System.Activities.NativeActivity%601>
- [Özel Etkinlikler Tasarlama ve Uygulama](../../../docs/framework/windows-workflow-foundation/designing-and-implementing-custom-activities.md)
- [Başlangıç Öğreticisi](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)
- [Nasıl yapılır: İş Akışı Oluşturma](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md)
- [Özel Etkinlik Tasarımcısında ExpressionTextBox Kullanma](../../../docs/framework/windows-workflow-foundation/samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)