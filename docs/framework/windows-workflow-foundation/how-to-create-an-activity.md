---
title: 'Nasıl yapılır: bir etkinliği oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c09b1e99-21b5-4d96-9c04-ec31db3f4436
ms.openlocfilehash: deb1b6ca5c6fc996a015e32dd5e0c7b9bd6530fa
ms.sourcegitcommit: a368166a51e5204c0224fbf5e46476e3ed122817
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2018
ms.locfileid: "43332709"
---
# <a name="how-to-create-an-activity"></a>Nasıl yapılır: bir etkinliği oluşturma
Etkinlikleri olan çekirdek birimi davranış [!INCLUDE[wf1](../../../includes/wf1-md.md)]. Bir etkinlik yürütülme mantığı yönetilen kodda uygulanabilir veya diğer etkinlikleri kullanarak uygulanabilir. Bu konu, iki etkinliği oluşturma işlemini gösterir. İlk Etkinlik yürütme mantığını uygulamak için kodu kullanan basit bir etkinliktir. İkinci etkinlik uygulaması, diğer etkinlikleri kullanarak tanımlanır. Bu etkinlikler, aşağıdaki adımlarda öğreticide kullanılır.  
  
> [!NOTE]
>  Öğreticinin tamamlanmış bir sürümünü indirmek için bkz [Windows Workflow Foundation (WF45) - başlangıç Öğreticisi](https://go.microsoft.com/fwlink/?LinkID=248976).  
  
### <a name="to-create-the-activity-library-project"></a>Etkinlik kitaplığı projesi oluşturmak için  
  
1.  Açık [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] ve **yeni**, **proje** gelen **dosya** menüsü.  
  
2.  Genişletin **diğer proje türleri** düğümünde **yüklü**, **şablonları** listesinde ve seçin **Visual Studio çözümleri**.  
  
3.  Seçin **boş çözüm** gelen **Visual Studio çözümleri** listesi. Emin **.NET Framework 4.5** .NET Framework sürüm aşağı açılan listeden seçilen. Tür `WF45GettingStartedTutorial` içinde **adı** kutusuna ve ardından **Tamam**.  
  
4.  Sağ **WF45GettingStartedTutorial** içinde **Çözüm Gezgini** ve **Ekle**, **yeni proje**.  
  
    > [!TIP]
    >  Varsa **Çözüm Gezgini** penceresi görüntülenmiyorsa, seçin **Çözüm Gezgini** gelen **görünümü** menüsü.  
  
5.  İçinde **yüklü** düğümünü **Visual C#**, **iş akışı** (veya **Visual Basic**, **iş akışı**). Emin **.NET Framework 4.5** seçili [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] sürüm aşağı açılan listesi. Seçin **etkinlik Kitaplığı** gelen **iş akışı** listesi. Tür `NumberGuessWorkflowActivities` içinde **adı** kutusuna ve ardından **Tamam**.  
  
    > [!NOTE]
    >  Hangi programlama diline bağlı olarak, Visual Studio'da birincil dili olarak yapılandırılmış **Visual C#** veya **Visual Basic** düğümü altında olabilir **diğer diller** düğümünde **yüklü** düğümü.  
  
6.  Sağ **gt;activity1.XAML** içinde **Çözüm Gezgini** ve **Sil**. Tıklayın **Tamam** onaylamak için.  
  
### <a name="to-create-the-readint-activity"></a>ReadInt etkinlik oluşturmak için  
  
1.  Seçin **Yeni Öğe Ekle** gelen **proje** menüsü.  
  
2.  İçinde **yüklü**, **ortak öğeler** düğümünü **iş akışı**. Seçin **kod etkinliği** gelen **iş akışı** listesi.  
  
3.  Tür `ReadInt` içine **adı** kutusuna ve ardından **Ekle**.  
  
4.  Varolan `ReadInt` aşağıdaki tanımını tanımıyla.  
  
     [!code-csharp[CFX_WF_GettingStarted#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/readint.cs#1)]
     [!code-vb[CFX_WF_GettingStarted#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/readint.vb#1)]  
  
    > [!NOTE]
    >  `ReadInt` Etkinlik türetilir <xref:System.Activities.NativeActivity%601> yerine <xref:System.Activities.CodeActivity>, kod etkinlik şablonu için varsayılan değerdir. <xref:System.Activities.CodeActivity%601> Etkinlik aracılığıyla sunulan tek bir sonuç sağlıyorsa kullanılabilir <xref:System.Activities.Activity%601.Result%2A> bağımsız değişkeni, ancak <xref:System.Activities.CodeActivity%601> kullanımı yer işaretleri, bu nedenle desteklemiyor <xref:System.Activities.NativeActivity%601> kullanılır.  
  
### <a name="to-create-the-prompt-activity"></a>Komut istemi etkinlik oluşturmak için  
  
1.  Projeyi oluşturmak için CTRL+SHIFT+B tuşlarına basın. Proje etkinleştirir oluşturmaya `ReadInt` etkinlik bu projede Bu adımdan özel etkinlik oluşturmak için kullanılacak.  
  
2.  Seçin **Yeni Öğe Ekle** gelen **proje** menüsü.  
  
3.  İçinde **yüklü**, **ortak öğeler** düğümünü **iş akışı**. Seçin **etkinlik** gelen **iş akışı** listesi.  
  
4.  Tür `Prompt` içine **adı** kutusuna ve ardından **Ekle**.  
  
5.  Çift **Prompt.xaml** içinde **Çözüm Gezgini** zaten görüntülenmiyorsa, tasarımcıda görüntülenecek.  
  
6.  Tıklayın **bağımsız değişkenleri** sol alt tarafında görüntülenecek etkinlik Tasarımcısı **bağımsız değişkenleri** bölmesi.  
  
7.  Tıklayın **bağımsız değişken oluşturma**.  
  
8.  Tür `BookmarkName` içine **adı** kutusunda **içinde** gelen **yönü** aşağı açılan listesinden **dize** gelen**Bağımsız değişken türü** aşağı açılan liste ve bağımsız değişkeni kaydetmek için ENTER tuşuna basın.  
  
9. Tıklayın **bağımsız değişken oluşturma**.  
  
10. Tür `Result` içine **adı** altında yeni eklenen kutusunu `BookmarkName` bağımsız değişkeni, select **kullanıma** gelen **yönü** aşağı açılan listesinde seçin **Int32** gelen **bağımsız değişken türü** aşağı açılan liste ve ENTER tuşuna basın.  
  
11. Tıklayın **bağımsız değişken oluşturma**.  
  
12. Tür `Text` içine **adı** kutusunda **içinde** gelen **yönü** aşağı açılan listesinden **dize** gelen**Bağımsız değişken türü** aşağı açılan liste ve bağımsız değişkeni kaydetmek için ENTER tuşuna basın.  
  
     Bu üç bağımsız değişken için karşılık gelen bağımsız bağlı <xref:System.Activities.Statements.WriteLine> ve `ReadInt` eklenen etkinlikler `Prompt` aşağıdaki adımlarda etkinlik.  
  
13. Tıklayın **bağımsız değişkenleri** etkinlik Tasarımcısı kapatmak için sol alt tarafında **bağımsız değişkenleri** bölmesi.  
  
14. Sürükle bir **dizisi** etkinliğinden **akış denetimi** bölümünü **araç kutusu** üzerine bırakın **Buraya Bırak etkinlik** etiketi **İstemi** etkinlik Tasarımcısı.  
  
    > [!TIP]
    >  Varsa **araç kutusu** penceresi görüntülenmiyorsa, seçin **araç kutusu** gelen **görünümü** menüsü.  
  
15. Sürükle bir **WriteLine** etkinliğinden **Temelleri** bölümünü **araç kutusu** üzerine bırakın **Buraya Bırak etkinlik** etiketi **Dizisi** etkinlik.  
  
16. Bağlama **metin** bağımsız değişkeni **WriteLine** etkinliğini **metin** bağımsız değişkeni **istemi** yazarak etkinlik `Text` içine **bir C# ifadesi girin** veya **zadejte Výraz jazyka vb.** kutusunda **özellikleri** anahtar iki kez penceresi ve TAB tuşuna basın. Bu, IntelliSense listesi üyeleri penceresi kapatılır ve özellik değeri özelliği devre dışı seçim taşıyarak kaydeder. Bu özellik ayrıca yazarak ayarlanabilir `Text` içine **bir C# ifadesi girin** veya **zadejte Výraz jazyka vb.** etkinlik çubuğundaki.  
  
    > [!TIP]
    >  Varsa **Özellikler penceresi** görüntülenen, select değil **Özellikler penceresi** gelen **görünümü** menüsü.  
  
17. Sürükleme bir **readInt** etkinliğinden **NumberGuessWorkflowActivities** bölümünü **araç kutusu** sürükleyip **dizisi** Böylece onun etkinlik **WriteLine** etkinlik.  
  
18. Bağlama **YerİşaretiAdı** bağımsız değişkeni **readInt** etkinliğini **YerİşaretiAdı** bağımsız değişkeni **istemi** yazaraketkinliği`BookmarkName` içine **zadejte Výraz jazyka vb.** kutusunun sağındaki **YerİşaretiAdı** değişkeninde **Özellikler penceresi**ve ardından iki SEKME tuşuna basın IntelliSense liste üyelerini penceresini kapatın ve özelliğini kaydetmek için zaman.  
  
19. Bağlama **sonucu** bağımsız değişkeni **readInt** etkinliğini **sonucu** bağımsız değişkeni **istemi** yazarak etkinlik `Result` içine **zadejte Výraz jazyka vb.** kutusunun sağındaki **sonucu** değişkeninde **Özellikler penceresi**ve ardından SEKME tuşuna iki kez basın.  
  
20. Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
     Öğreticide, bir sonraki adım için bkz. Bu etkinlikleri kullanarak bir iş akışı oluşturmak yönergeler [nasıl yapılır: bir iş akışı oluşturmak](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Activities.CodeActivity>  
 <xref:System.Activities.NativeActivity%601>  
 [Özel Etkinlikler Tasarlama ve Uygulama](../../../docs/framework/windows-workflow-foundation/designing-and-implementing-custom-activities.md)  
 [Başlangıç Öğreticisi](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [Nasıl yapılır: İş Akışı Oluşturma](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md)  
 [Özel Etkinlik Tasarımcısında ExpressionTextBox Kullanma](../../../docs/framework/windows-workflow-foundation/samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)
