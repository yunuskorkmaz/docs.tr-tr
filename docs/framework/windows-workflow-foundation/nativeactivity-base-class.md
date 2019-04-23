---
title: NativeActivity Temel Sınıfı
ms.date: 03/30/2017
ms.assetid: 254a4c50-425b-426d-a32f-0f7234925bac
ms.openlocfilehash: f718d247e7110b46cdd13038c7c93c1e45612c75
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59296595"
---
# <a name="nativeactivity-base-class"></a>NativeActivity Temel Sınıfı

<xref:System.Activities.NativeActivity> korumalı Oluşturucu ile soyut bir sınıftır. Gibi <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> uygulayarak kesinlik temelli davranışı yazmak için kullanılan bir <xref:System.Activities.NativeActivity.Execute%2A> yöntemi. Farklı <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> iş akışı çalışma zamanı kullanıma sunulan tüm özelliklere erişebilir <xref:System.Activities.NativeActivityContext> geçirilen nesne <xref:System.Activities.NativeActivity.Execute%2A> yöntemi.

## <a name="using-nativeactivitycontext"></a>NativeActivityContext kullanma
 İş akışı çalışma zamanı özellikleri içinden erişilebilir <xref:System.Activities.NativeActivity.Execute%2A> üyeleri kullanarak yöntemi `context` türünde parametre <xref:System.Activities.NativeActivityContext>. Aracılığıyla kullanılabilen özellikleri <xref:System.Activities.NativeActivityContext> şunları içerir:

-   Alma ve bağımsız değişkenler ve değişkenleri ayarlama.

-   Bağımlı etkinliklerle zamanlama <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>

-   Etkinlik yürütme durduruluyor kullanarak <xref:System.Activities.NativeActivityContext.Abort%2A>.

-   Yürütme kullanarak alt iptal etme <xref:System.Activities.NativeActivityContext.CancelChild%2A> ve <xref:System.Activities.NativeActivityContext.CancelChildren%2A>.

-   Bu tür yöntemler olarak kullanarak etkinlik yer işaretleri erişim <xref:System.Activities.NativeActivityContext.CreateBookmark%2A>, <xref:System.Activities.NativeActivityContext.RemoveBookmark%2A>, ve <xref:System.Activities.NativeActivityContext.ResumeBookmark%2A>.

-   Özel İzleme özelliklerini kullanarak <xref:System.Activities.CodeActivityContext.Track%2A>.

-   Etkinlik yürütme özellikleri ve değer özellikleri kullanarak erişim <xref:System.Activities.CodeActivityContext.GetProperty%2A> ve <xref:System.Activities.NativeActivityContext.GetValue%2A>.

-   Etkinlik eylemleri ve işlevleri kullanarak zamanlama <xref:System.Activities.NativeActivityContext.ScheduleAction%2A> ve <xref:System.Activities.NativeActivityContext.ScheduleFunc%2A>.

### <a name="to-create-a-custom-activity-that-inherits-from-nativeactivity"></a>NativeActivity devralan bir özel etkinlik oluşturmak için

1. OpenVisual Studio 2010.

2. Seçin **dosya**, **yeni**, ardından **proje**. Seçin **Workflow 4.0** altında **Visual C#** içinde **proje türleri** penceresi ve select **v2010** düğümü. Seçin **etkinlik Kitaplığı** içinde **şablonları** penceresi. Yeni Proje HelloActivity adı.

3. Gt;activity1.XAML HelloActivity projeye sağ tıklayıp **Sil**.

4. HelloActivity projeye sağ tıklayıp **Ekle**, ardından **sınıfı**. Yeni bir sınıf HelloActivity.cs adı.

5. HelloActivity.cs dosyasına aşağıdakileri ekleyin `using` yönergeleri.

    ```csharp
    using System.Activities;
    using System.Activities.Statements;
    ```

6. Devralınan yeni bir sınıf olun <xref:System.Activities.NativeActivity> için sınıf bildiriminin bir temel sınıf ekleyerek.

    ```csharp
    class HelloActivity : NativeActivity
    ```

7. Ekleyerek sınıfına işlevsellik ekleme bir <xref:System.Activities.NativeActivity.Execute%2A> yöntemi.

    ```csharp
    protected override void Execute(NativeActivityContext context)
    {
        Console.WriteLine("Hello World!");
    }
    ```

8. Geçersiz kılma <xref:System.Activities.NativeActivity.CacheMetadata%2A> yöntemi ve özel etkinliğin değişkenleri, bağımsız değişkenler, alt ve temsilciler hakkında bilmeniz iş akışı çalışma zamanı izin vermek için uygun Ekle yöntemi çağrısı. Daha fazla bilgi için <xref:System.Activities.NativeActivityMetadata> sınıfı.

9. Kullanım <xref:System.Activities.NativeActivityContext> bir yer işareti zamanlamak için nesne. Bkz: <xref:System.Activities.WorkflowApplicationIdleEventArgs.Bookmarks%2A> oluşturma hakkında ayrıntılar için zamanlamak ve bir yer işareti devam edin.

    ```
    protected override void Execute(NativeActivityContext context)
        {
            // Create a Bookmark and wait for it to be resumed.
            context.CreateBookmark(BookmarkName.Get(context),
                new BookmarkCallback(OnResumeBookmark));
        }
    ```