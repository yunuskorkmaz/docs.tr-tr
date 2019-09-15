---
title: NativeActivity Temel Sınıfı
ms.date: 03/30/2017
ms.assetid: 254a4c50-425b-426d-a32f-0f7234925bac
ms.openlocfilehash: 604535e39937a75c6d268cf1abbc90dbcd506a16
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989559"
---
# <a name="nativeactivity-base-class"></a>NativeActivity Temel Sınıfı

<xref:System.Activities.NativeActivity>, korumalı Oluşturucusu olan soyut bir sınıftır. Benzer <xref:System.Activities.CodeActivity>şekilde <xref:System.Activities.NativeActivity> , bir<xref:System.Activities.NativeActivity.Execute%2A> yöntemi uygulayarak kesinlik davranışı yazmak için kullanılır. Aksine <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> yöntemine geçirilen <xref:System.Activities.NativeActivityContext> nesne aracılığıyla iş akışı çalışma zamanının tüm sunulan özelliklerine erişimi vardır. <xref:System.Activities.NativeActivity.Execute%2A>

## <a name="using-nativeactivitycontext"></a>NativeActivityContext kullanma
 İş akışı çalışma zamanının özelliklerine, türünün <xref:System.Activities.NativeActivity.Execute%2A> <xref:System.Activities.NativeActivityContext>' nin üyelerini `context` kullanarak yönteminin içinden erişilebilir. Aracılığıyla <xref:System.Activities.NativeActivityContext> kullanılabilen özellikler şunları içerir:

- Bağımsız değişkenlerin ve değişkenlerin alınması ve ayarlanması.

- İle alt etkinlikleri zamanlama<xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>

- Kullanılarak <xref:System.Activities.NativeActivityContext.Abort%2A>Etkinlik yürütme durduruluyor.

- <xref:System.Activities.NativeActivityContext.CancelChild%2A> Ve<xref:System.Activities.NativeActivityContext.CancelChildren%2A>kullanarak alt yürütme iptal ediliyor.

- <xref:System.Activities.NativeActivityContext.CreateBookmark%2A> ,<xref:System.Activities.NativeActivityContext.RemoveBookmark%2A>Ve gibi<xref:System.Activities.NativeActivityContext.ResumeBookmark%2A>yöntemler kullanılarak etkinlik yer işaretlerine erişin.

- Kullanarak <xref:System.Activities.CodeActivityContext.Track%2A>özel izleme özellikleri.

- <xref:System.Activities.CodeActivityContext.GetProperty%2A> Ve<xref:System.Activities.NativeActivityContext.GetValue%2A>kullanarak etkinliğin yürütme özelliklerine ve değer özelliklerine erişin.

- <xref:System.Activities.NativeActivityContext.ScheduleAction%2A> Ve<xref:System.Activities.NativeActivityContext.ScheduleFunc%2A>kullanarak etkinlik eylemlerini ve işlevleri zamanlama.

### <a name="to-create-a-custom-activity-that-inherits-from-nativeactivity"></a>NativeActivity 'den devralan özel etkinlik oluşturmak için

1. OpenVisual Studio 2010.

2. **Dosya**, **Yeni**ve ardından **Proje**' yi seçin. **Proje türleri** penceresinde **Visual C#**  altında **iş akışı 4,0** ' i seçin ve **v2010** düğümünü seçin. **Şablonlar** penceresinde **etkinlik kitaplığı** ' nı seçin. Yeni proje Merhaba etkinliğini adlandırın.

3. Merhaba etkinlik projesinde Activity1. xaml öğesine sağ tıklayın ve **Sil**' i seçin.

4. Merhaba etkinlik projesine sağ tıklayın ve **Ekle**' yi ve ardından **sınıf**' ı seçin. Yeni sınıfı HelloActivity.cs olarak adlandırın.

5. HelloActivity.cs dosyasında aşağıdaki `using` yönergeleri ekleyin.

    ```csharp
    using System.Activities;
    using System.Activities.Statements;
    ```

6. Sınıf bildirimine bir temel sınıf ekleyerek <xref:System.Activities.NativeActivity> yeni sınıfın öğesinden devralmasını sağlayın.

    ```csharp
    class HelloActivity : NativeActivity
    ```

7. Bir <xref:System.Activities.NativeActivity.Execute%2A> Yöntem ekleyerek sınıfa işlevsellik ekleyin.

    ```csharp
    protected override void Execute(NativeActivityContext context)
    {
        Console.WriteLine("Hello World!");
    }
    ```

8. <xref:System.Activities.NativeActivity.CacheMetadata%2A> Yöntemi geçersiz kılın ve iş akışı çalışma zamanının özel etkinliğin değişkenleri, bağımsız değişkenleri, alt öğeleri ve Temsilciler hakkında bilgi almasına izin vermek için uygun ekleme yöntemini çağırın. Daha fazla bilgi için <xref:System.Activities.NativeActivityMetadata> sınıfına bakın.

9. Bir yer işareti zamanlamak için nesnesinikullanın.<xref:System.Activities.NativeActivityContext> Bir <xref:System.Activities.WorkflowApplicationIdleEventArgs.Bookmarks%2A> yer işaretinin oluşturulması, zamanlanzamanlaması ve sürdürülmesine ilişkin ayrıntılar için bkz.

    ```csharp
    protected override void Execute(NativeActivityContext context)
        {
            // Create a Bookmark and wait for it to be resumed.
            context.CreateBookmark(BookmarkName.Get(context),
                new BookmarkCallback(OnResumeBookmark));
        }
    ```
