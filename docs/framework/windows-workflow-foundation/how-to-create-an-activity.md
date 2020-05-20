---
title: 'Nasıl Yapılır: Etkinlik Oluşturma'
description: "Bu makalede, Workflow Foundation 'da iki etkinlik oluşturma gösterilmektedir: bir tane, mantığını uygulamak için kod kullanan ve diğeri diğer etkinlikleri kullanarak tanımlanmış."
ms.date: 09/14/2018
dev_langs:
- csharp
- vb
ms.assetid: c09b1e99-21b5-4d96-9c04-ec31db3f4436
ms.openlocfilehash: dae099d102b0c85d09a1ef8bcce56e8a9096bd20
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419596"
---
# <a name="how-to-create-an-activity"></a>Nasıl Yapılır: Etkinlik Oluşturma

Etkinlikler, içindeki temel davranış birimidir [!INCLUDE[wf1](../../../includes/wf1-md.md)] . Bir etkinliğin yürütme mantığı yönetilen kodda uygulanabilir veya diğer etkinlikler kullanılarak uygulanabilir. Bu konuda, iki etkinliğin nasıl oluşturulacağı gösterilmektedir. İlk etkinlik, yürütme mantığını uygulamak için kod kullanan basit bir etkinliktir. İkinci etkinliğin uygulanması diğer etkinlikler kullanılarak tanımlanır. Bu etkinlikler öğreticideki aşağıdaki adımlarda kullanılır.

> [!NOTE]
> Öğreticinin tamamlanmış bir sürümünü indirmek için, bkz. [Windows Workflow Foundation (WF45)-Başlangıç Öğreticisi](https://go.microsoft.com/fwlink/?LinkID=248976).

## <a name="create-the-activity-library-project"></a>Etkinlik kitaplığı projesi oluşturma

1. Visual Studio 'yu açın ve **New**  >  **Dosya** menüsünden Yeni**Proje** ' yi seçin.

2. **Yeni proje** iletişim kutusunda, **yüklü** kategori altında, **Visual C#**  >  **iş akışı** (veya **Visual Basic**  >  **iş akışı**) öğesini seçin.

    > [!NOTE]
    > **Iş akışı** şablonu kategorisini görmüyorsanız, Visual Studio 'nun **Windows Workflow Foundation** bileşenini yüklemeniz gerekebilir. **Yeni proje** iletişim kutusunun sol tarafındaki **Visual Studio yükleyicisi aç** bağlantısını seçin. Visual Studio Yükleyicisi, **tek tek bileşenler** sekmesini seçin. Ardından, **geliştirme etkinlikleri** kategorisi altında **Windows Workflow Foundation** bileşenini seçin. Bileşeni yüklemek için **Değiştir** ' i seçin.

3. **Etkinlik kitaplığı** proje şablonunu seçin. `NumberGuessWorkflowActivities` **Ad** kutusuna yazın ve ardından **Tamam**' a tıklayın.

4. **Çözüm Gezgini** 'de **Activity1. xaml** öğesine sağ tıklayın ve **Sil**' i seçin. Onaylamak için **Tamam** ' ı tıklatın.

## <a name="create-the-readint-activity"></a>ReadInt etkinliğini oluşturma

1. **Proje** menüsünden **Yeni öğe Ekle** ' yi seçin.

2. **Yüklü**  >  **ortak öğeler** düğümünde **iş akışı**' nı seçin. **Iş akışı** listesinden **kod etkinliği** ' ni seçin.

3. `ReadInt` **Ad** kutusuna yazın ve ardından **Ekle**' ye tıklayın.

4. Mevcut `ReadInt` tanımı aşağıdaki tanım ile değiştirin.

     [!code-csharp[CFX_WF_GettingStarted#1](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/readint.cs#1)]
     [!code-vb[CFX_WF_GettingStarted#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/readint.vb#1)]

    > [!NOTE]
    > `ReadInt`Etkinlik, <xref:System.Activities.NativeActivity%601> <xref:System.Activities.CodeActivity> kod etkinlik şablonu için varsayılan olan yerine öğesinden türetilir. <xref:System.Activities.CodeActivity%601>etkinlik bağımsız değişken aracılığıyla ortaya çıkarılan <xref:System.Activities.Activity%601.Result%2A> ancak <xref:System.Activities.CodeActivity%601> yer işaretlerinin kullanımını desteklemeyen tek bir sonuç sağlıyorsa, bu nedenle kullanılır <xref:System.Activities.NativeActivity%601> .

## <a name="create-the-prompt-activity"></a>Istem etkinliğini oluşturma

1. **Ctrl** + **Shift** + Projeyi derlemek için CTRL SHIFT**B** tuşlarına basın. Projeyi oluşturmak, bu `ReadInt` projedeki etkinliğin özel etkinlik oluşturmak için kullanılmasını sağlar.

2. **Proje** menüsünden **Yeni öğe Ekle** ' yi seçin.

3. **Yüklü**  >  **ortak öğeler** düğümünde **iş akışı**' nı seçin. **Iş akışı** listesinden **etkinlik** ' i seçin.

4. `Prompt` **Ad** kutusuna yazın ve ardından **Ekle**' ye tıklayın.

5. Daha önce görüntülenmiyorsa, tasarımcıda göstermek için **Çözüm Gezgini** **. xaml** öğesine çift tıklayın.

6. **Bağımsız değişkenler** bölmesini göstermek için etkinlik tasarımcısının sol alt tarafındaki **bağımsız değişkenler** ' e tıklayın.

7. **Bağımsız değişken Oluştur**' a tıklayın.

8. `BookmarkName` **Ad** kutusuna yazın, **Yön** açılan listesinden **'** ı seçin, **bağımsız değişken türü** açılan listesinden **dize** ' yi seçin ve sonra bağımsız değişkeni kaydetmek için **ENTER** tuşuna basın.

9. **Bağımsız değişken Oluştur**' a tıklayın.

10. `Result`Yeni eklenen bağımsız değişkenin altında bulunan **ad** kutusuna yazın `BookmarkName` , **Yön** açılan listesinden Seç **Out** ' i seçin, **bağımsız değişken türü** açılan listesinden **Int32** ' i seçin ve ardından **ENTER**tuşuna basın.

11. **Bağımsız değişken Oluştur**' a tıklayın.

12. `Text` **Ad** kutusuna yazın, **Yön** açılan listesinden **'** ı seçin, **bağımsız değişken türü** açılan listesinden **dize** ' yi seçin ve sonra bağımsız değişkeni kaydetmek için **ENTER** tuşuna basın.

     Bu üç bağımsız değişken, <xref:System.Activities.Statements.WriteLine> `ReadInt` Aşağıdaki adımlarda etkinliğe eklenen ve etkinliklerinin karşılık gelen bağımsız değişkenlerine bağlanır `Prompt` .

13. **Bağımsız değişkenler** bölmesini kapatmak için etkinlik tasarımcısının sol alt tarafındaki **bağımsız değişkenler** ' e tıklayın.

14. **Araç kutusunun** **Denetim akışı** bölümünden bir **dizi** etkinliği sürükleyin ve **sor** etkinlik Tasarımcısı ' nın **buradan bırakma etkinliği** etiketine bırakın.

    > [!TIP]
    > **Araç kutusu** penceresi görüntülenmiyorsa, **Görünüm** menüsünden **araç kutusu** ' nu seçin.

15. **Araç kutusu** ' nu **temel elemanlar** bölümünden bir **WriteLine** etkinliği sürükleyin ve **dizi** etkinliğinin **buraya bırakma etkinliğine** bırakın.

16. **WriteLine** etkinliğinin **metin** **bağımsız değişkenini,** **Prompt** `Text` **bir C# ifadesi girin** veya **Özellikler** penceresinde **bir vb ifadesi girin** ve ardından SEKME tuşuna iki kez basın ve ardından **sekme** tuşuna basın. Bu, IntelliSense liste üyeleri penceresini devre dışı bırakır ve seçimi özelliğin dışına taşıyarak özellik değerini kaydeder. Bu özellik ayrıca, `Text` **bir C# ifadesi girin** veya etkinliğin kendısı için **bir vb ifadesi** kutusu girerek ayarlanabilir.

    > [!TIP]
    > **Özellikler penceresi** görüntülenmiyorsa, **Görünüm** menüsünden **Özellikler penceresi** ' ni seçin.

17. **Araç kutusu** 'Nun **NumberGuessWorkflowActivities** bölümünden bir **readInt** etkinliği sürükleyin ve **WriteLine** etkinliğinin ardından onu **sıraya** koyun.

18. **ReadInt** etkinliğinin **BookmarkName** bağımsız değişkenini, **Prompt** **BookmarkName** `BookmarkName` **Özellikler penceresinde** **BookmarkName** bağımsız değişkeninin sağ tarafındaki **bir vb ifadesi girin** kutusuna yazarak istem etkinliğinin BookmarkName bağımsız değişkenine bağlayın ve sonra IntelliSense liste üyeleri penceresini kapatmak ve özelliği kaydetmek için iki kez **Tab** tuşuna basın.

19. **ReadInt** etkinliğinin **sonuç** bağımsız değişkenini, **Result** **Prompt** `Result` **Özellikler penceresinde** **sonuç** bağımsız değişkeninin sağ tarafındaki **bir vb ifadesi girin** kutusuna yazarak istem etkinliğinin sonuç bağımsız değişkenine bağlayın ve ardından **sekme** tuşuna iki kez basın.

20. **Ctrl** + **Shift** + Çözümü derlemek için CTRL SHIFT**B** tuşlarına basın.

## <a name="next-steps"></a>Sonraki adımlar

Bu etkinlikleri kullanarak iş akışı oluşturma yönergeleri için bkz. öğreticideki bir sonraki adım, [nasıl yapılır: Iş akışı oluşturma](how-to-create-a-workflow.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Activities.CodeActivity>
- <xref:System.Activities.NativeActivity%601>
- [Özel Etkinlikler Tasarlama ve Uygulama](designing-and-implementing-custom-activities.md)
- [Başlangıç Öğreticisi](getting-started-tutorial.md)
- [Nasıl yapılır: İş Akışı Oluşturma](how-to-create-a-workflow.md)
- [Özel Etkinlik Tasarımcısında ExpressionTextBox Kullanma](./samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)
