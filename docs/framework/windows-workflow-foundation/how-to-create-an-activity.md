---
title: "Nasıl yapılır: bir etkinlik oluşturmak"
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
ms.assetid: c09b1e99-21b5-4d96-9c04-ec31db3f4436
caps.latest.revision: "39"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4a3b9698d6a060120addff52e6600916a2de19fc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-an-activity"></a>Nasıl yapılır: bir etkinlik oluşturmak
Etkinliklerin davranışını çekirdek biriminin olduğundan [!INCLUDE[wf1](../../../includes/wf1-md.md)]. Yönetilen kodda bir etkinlik yürütme mantığını uygulanabilir veya diğer etkinlikleri kullanarak uygulanabilir. Bu konuda iki etkinlik oluşturma gösterilir. İlk etkinlik, yürütme mantığını uygulamak için kod kullanan basit bir etkinliktir. İkinci etkinlik uyarlamasını diğer etkinlikleri kullanarak tanımlanır. Bu etkinlikler içindeki adımları izleyerek öğreticide kullanılır.  
  
> [!NOTE]
>  Öğreticinin tamamlanmış bir sürümünü indirmek için bkz: [Windows Workflow Foundation (WF45) - başlangıç Öğreticisi](http://go.microsoft.com/fwlink/?LinkID=248976).  
  
### <a name="to-create-the-activity-library-project"></a>Etkinlik kitaplığı projesi oluşturmak için  
  
1.  Açık [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] ve **yeni**, **proje** gelen **dosya** menüsü.  
  
2.  Genişletme **diğer proje türleri** düğümünde **yüklü**, **şablonları** listesinde ve seçin **Visual Studio çözümleri**.  
  
3.  Seçin **boş çözüm** gelen **Visual Studio çözümleri** listesi. Emin **.NET Framework 4.5** .NET Framework sürüm aşağı açılan listesinde seçilir. Tür `WF45GettingStartedTutorial` içinde **adı** kutusuna ve ardından **Tamam**.  
  
4.  Sağ **WF45GettingStartedTutorial** içinde **Çözüm Gezgini** ve **Ekle**, **yeni proje**.  
  
    > [!TIP]
    >  Varsa **Çözüm Gezgini** penceresi görüntülenmez, seçin **Çözüm Gezgini** gelen **Görünüm** menüsü.  
  
5.  İçinde **yüklü** düğümü, select **Visual C#**, **iş akışı** (veya **Visual Basic**, **iş akışı**). Emin **.NET Framework 4.5** seçildiyse [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] sürüm aşağı açılan listesi. Seçin **etkinlik Kitaplığı** gelen **iş akışı** listesi. Tür `NumberGuessWorkflowActivities` içinde **adı** kutusuna ve ardından **Tamam**.  
  
    > [!NOTE]
    >  Hangi programlama dili bağlı olarak birincil dilinde olarak yapılandırılan [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], **Visual C#** veya **Visual Basic** düğümü altında olabilir **diğer diller**düğümünde **yüklü** düğümü.  
  
6.  Sağ **Activity1.xaml** içinde **Çözüm Gezgini** ve **silmek**. Tıklatın **Tamam** onaylamak için.  
  
### <a name="to-create-the-readint-activity"></a>ReadInt etkinlik oluşturmak için  
  
1.  Seçin **Yeni Öğe Ekle** gelen **proje** menüsü.  
  
2.  İçinde **yüklü**, **ortak öğeler** düğümü, select **iş akışı**. Seçin **kodunu aktivite** gelen **iş akışı** listesi.  
  
3.  Tür `ReadInt` içine **adı** kutusuna ve ardından **Ekle**.  
  
4.  Varolan `ReadInt` aşağıdaki tanımını tanımıyla.  
  
     [!code-csharp[CFX_WF_GettingStarted#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/readint.cs#1)]
     [!code-vb[CFX_WF_GettingStarted#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/readint.vb#1)]  
  
    > [!NOTE]
    >  `ReadInt` Etkinlik türer <xref:System.Activities.NativeActivity%601> yerine <xref:System.Activities.CodeActivity>, kod etkinlik şablonu için varsayılan değerdir. <xref:System.Activities.CodeActivity%601>Etkinlik aracılığıyla kullanıma sunulan tek bir sonuç sağlıyorsa kullanılabilir <xref:System.Activities.Activity%601.Result%2A> bağımsız değişkeni, ancak <xref:System.Activities.CodeActivity%601> kullanımı yer işaretleri, bu nedenle desteklemiyor <xref:System.Activities.NativeActivity%601> kullanılır.  
  
### <a name="to-create-the-prompt-activity"></a>Komut istemi etkinlik oluşturmak için  
  
1.  Projeyi oluşturmak için CTRL+SHIFT+B tuşlarına basın. Proje etkinleştirir oluşturma `ReadInt` etkinlik bu projede bu adımdaki özel etkinlik oluşturmak için kullanılacak.  
  
2.  Seçin **Yeni Öğe Ekle** gelen **proje** menüsü.  
  
3.  İçinde **yüklü**, **ortak öğeler** düğümü, select **iş akışı**. Seçin **etkinlik** gelen **iş akışı** listesi.  
  
4.  Tür `Prompt` içine **adı** kutusuna ve ardından **Ekle**.  
  
5.  Çift **Prompt.xaml** içinde **Çözüm Gezgini** zaten görüntülenmiyorsa, Tasarımcısı'nda görüntülenecek.  
  
6.  Tıklatın **bağımsız değişkenleri** görüntülenecek etkinlik Tasarımcısı sol tarafındaki **bağımsız değişkenleri** bölmesi.  
  
7.  Tıklatın **bağımsız değişkeni oluşturma**.  
  
8.  Tür `BookmarkName` içine **adı** kutusunda **içinde** gelen **yönü** aşağı açılan listesinden, **dize** gelen**Bağımsız değişken türü** aşağı açılan liste ve bağımsız değişkeni kaydetmek için ENTER tuşuna basın.  
  
9. Tıklatın **bağımsız değişkeni oluşturma**.  
  
10. Türü `Result` içine **adı** altında yeni eklenen kutusuna `BookmarkName` bağımsız değişkeni, select **çıkışı** gelen **yönü** aşağı açılan listesinde, seçin **Int32** gelen **bağımsız değişken türü** aşağı açılan liste ve ENTER tuşuna BASIN.  
  
11. Tıklatın **bağımsız değişkeni oluşturma**.  
  
12. Tür `Text` içine **adı** kutusunda **içinde** gelen **yönü** aşağı açılan listesinden, **dize** gelen**Bağımsız değişken türü** aşağı açılan liste ve bağımsız değişkeni kaydetmek için ENTER tuşuna basın.  
  
     Bu üç bağımsız değişken için karşılık gelen bağımsız bağlı <xref:System.Activities.Statements.WriteLine> ve `ReadInt` eklenen etkinlikler `Prompt` aşağıdaki adımlarda etkinlik.  
  
13. Tıklatın **bağımsız değişkenleri** kapatmak için etkinlik Tasarımcısı sol tarafındaki **bağımsız değişkenleri** bölmesi.  
  
14. Sürükleme bir **dizisi** etkinliğinden **akış denetimi** bölümünü **araç** ve üzerine bırakın **etkinliğini Drop burada** etiketi **Komut istemi** etkinlik Tasarımcısı.  
  
    > [!TIP]
    >  Varsa **araç** penceresi görüntülenmez, seçin **araç** gelen **Görünüm** menüsü.  
  
15. Sürükleme bir **WriteLine** etkinliğinden **Temelleri** bölümünü **araç** ve üzerine bırakın **etkinliğini Drop burada** etiketi **Dizisi** etkinlik.  
  
16. Bağlama **metin** bağımsız değişkeni **WriteLine** etkinliğe **metin** bağımsız değişkeni **komut istemi** yazarak etkinlik `Text` içine **bir C# ifadesi girin** veya **bir VB ifadesi girin** kutusunda **özellikleri** iki kez anahtar penceresi ve ardından SEKME tuşuna basın. Bu, IntelliSense listesi üyeleri penceresini kapatır ve seçim özelliği devre dışı taşıyarak özellik değeri kaydeder. Bu özellik yazarak da ayarlanabilir `Text` içine **bir C# ifadesi girin** veya **bir VB ifadesi girin** etkinliğini kutusu.  
  
    > [!TIP]
    >  Varsa **Özellikler penceresini** görüntülenen, select değil **Özellikler penceresini** gelen **Görünüm** menüsü.  
  
17. Sürükleme bir **readInt** etkinliğinden **NumberGuessWorkflowActivities** bölümünü **araç** sürükleyip bırakın **dizisi** onun aşağıdaki şekilde etkinlik **WriteLine** etkinlik.  
  
18. Bağlama **YerİşaretiAdı** bağımsız değişkeni **readInt** etkinliğe **YerİşaretiAdı** bağımsız değişkeni **komut istemi** yazaraketkinliği`BookmarkName` içine **bir VB ifadesi girin** kutusunun sağındaki **YerİşaretiAdı** değişkeninde **Özellikler penceresini**ve ardından iki SEKME tuşuna basın IntelliSense listesi üyeleri penceresini kapatın ve özelliğini kaydetmek için zaman.  
  
19. Bağlama **sonuç** bağımsız değişkeni **readInt** etkinliğe **sonuç** bağımsız değişkeni **komut istemi** yazarak etkinlik `Result` içine **bir VB ifadesi girin** kutusunun sağındaki **sonuç** değişkeninde **Özellikler penceresini**ve ardından SEKME tuşuna iki kez basın.  
  
20. Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
     Öğreticide, bir sonraki adım için bu etkinlikleri kullanarak bir iş akışı oluşturmak yönergeler bkz [nasıl yapılır: bir iş akışı oluşturmak](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Activities.CodeActivity>  
 <xref:System.Activities.NativeActivity%601>  
 [Özel Etkinlikler Tasarlama ve Uygulama](../../../docs/framework/windows-workflow-foundation/designing-and-implementing-custom-activities.md)  
 [Başlangıç Öğreticisi](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [Nasıl yapılır: İş Akışı Oluşturma](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md)  
 [Özel Etkinlik Tasarımcısında ExpressionTextBox Kullanma](../../../docs/framework/windows-workflow-foundation/samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)
