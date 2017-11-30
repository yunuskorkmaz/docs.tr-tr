---
title: "NativeActivity taban sınıfı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 254a4c50-425b-426d-a32f-0f7234925bac
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 22c9557c53c15fef3ca8dee4a0f665d333c5ffe4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="nativeactivity-base-class"></a>NativeActivity taban sınıfı
<xref:System.Activities.NativeActivity>soyut bir sınıf korumalı Oluşturucu ile ilgilidir. Gibi <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> uygulayarak kesinlik temelli davranışı yazmak için kullanılan bir <xref:System.Activities.NativeActivity.Execute%2A> yöntemi. Farklı <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> tüm iş akışı çalışma zamanı sunulan özelliklerini erişimi <xref:System.Activities.NativeActivityContext> nesne geçirilen <xref:System.Activities.NativeActivity.Execute%2A> yöntemi.  
  
## <a name="using-nativeactivitycontext"></a>NativeActivityContext kullanma  
 İş akışı çalışma zamanı özelliklerini erişilebilir içinden <xref:System.Activities.NativeActivity.Execute%2A> üyeleri kullanarak yöntemi `context` parametresinin türü <xref:System.Activities.NativeActivityContext>. Aracılığıyla kullanılabilen özelliklerin <xref:System.Activities.NativeActivityContext> şunları içerir:  
  
-   Alma ve bağımsız değişkenleri ve değişkenleri ayarlama.  
  
-   Bağımlı etkinliklerle planlama<xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>  
  
-   Durduruluyor etkinlik kullanılarak yürütme <xref:System.Activities.NativeActivityContext.Abort%2A>.  
  
-   İptal etme alt kullanılarak yürütme <xref:System.Activities.NativeActivityContext.CancelChild%2A> ve <xref:System.Activities.NativeActivityContext.CancelChildren%2A>.  
  
-   Etkinlik yer işaretleri gibi yöntemlerle olarak erişim <xref:System.Activities.NativeActivityContext.CreateBookmark%2A>, <xref:System.Activities.NativeActivityContext.RemoveBookmark%2A>, ve <xref:System.Activities.NativeActivityContext.ResumeBookmark%2A>.  
  
-   Özel İzleme özelliklerini kullanarak <xref:System.Activities.CodeActivityContext.Track%2A>.  
  
-   Etkinliğin yürütme özellikleri ve değer özelliklerini kullanarak erişim <xref:System.Activities.CodeActivityContext.GetProperty%2A> ve <xref:System.Activities.NativeActivityContext.GetValue%2A>.  
  
-   Etkinlik eylemleri ve işlevleri kullanarak zamanlama <xref:System.Activities.NativeActivityContext.ScheduleAction%2A> ve <xref:System.Activities.NativeActivityContext.ScheduleFunc%2A>.  
  
#### <a name="to-create-a-custom-activity-that-inherits-from-nativeactivity"></a>NativeActivity devralan bir özel etkinlik oluşturmak için  
  
1.  Açık[!INCLUDE[vs2010](../../../includes/vs2010-md.md)].  
  
2.  Seçin **dosya**, **yeni**ve ardından **proje**. Seçin **Workflow 4.0** altında **Visual C#** içinde **proje türleri** penceresi ve select **v2010** düğümü. Seçin **etkinlik Kitaplığı** içinde **şablonları** penceresi. Yeni Proje HelloActivity olarak adlandırın.  
  
3.  Activity1.XAML HelloActivity projeye sağ tıklayıp **silmek**.  
  
4.  HelloActivity projesine sağ tıklatın ve **Ekle**ve ardından **sınıfı**. Yeni sınıf HelloActivity.cs olarak adlandırın.  
  
5.  Aşağıdaki HelloActivity.cs dosyasına ekleyin `using` yönergeleri.  
  
    ```csharp  
    using System.Activities;  
    using System.Activities.Statements;  
    ```  
  
6.  Devralınan yeni sınıf olun <xref:System.Activities.NativeActivity> bir taban sınıfı için sınıf bildirimi ekleyerek.  
  
    ```csharp  
    class HelloActivity : NativeActivity  
    ```  
  
7.  İşlevselliği sınıfa ekleyerek bir <xref:System.Activities.NativeActivity.Execute%2A> yöntemi.  
  
    ```csharp  
    protected override void Execute(NativeActivityContext context)  
    {  
        Console.WriteLine("Hello World!");  
    }  
    ```  
  
8.  Geçersiz kılma <xref:System.Activities.NativeActivity.CacheMetadata%2A> yöntemi ve özel etkinliğin değişkenleri, bağımsız değişkenler, alt ve temsilciler hakkında bilmeniz iş akışı çalışma zamanı izin vermek için uygun Ekle yöntemini çağırın. Daha fazla bilgi için bkz: <xref:System.Activities.NativeActivityMetadata> sınıfı.  
  
9. Kullanım <xref:System.Activities.NativeActivityContext> yer işareti zamanlamak için nesne. Bkz: <xref:System.Activities.WorkflowApplicationIdleEventArgs.Bookmarks%2A> nasıl oluşturulacağı hakkında bilgi için zamanlamak ve bir yer işareti devam edin.  
  
    ```  
    protected override void Execute(NativeActivityContext context)  
        {  
            // Create a Bookmark and wait for it to be resumed.  
            context.CreateBookmark(BookmarkName.Get(context),   
                new BookmarkCallback(OnResumeBookmark));  
        }  
    ```
