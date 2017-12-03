---
title: Bookmarks1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b51a346-09ae-455c-a70a-e2264ddeb9e2
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ebd6586500c82144f7bceca01dea278a76759b1f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="bookmarks"></a>Yer işaretleri
Yer işaretleri pasif olarak giriş için bir iş akışı iş parçacığı tutmadan beklemek için bir etkinlik sağlayan sistemdir. Bir etkinlik için stimulus beklediğini bildirir, bir yer işareti oluşturabilirsiniz. Bu etkinliğin yürütme tam düşünülmemelidir, çalışma zamanı gösterir bile şu anda yürütülen yöntemi (oluşturulduğu <xref:System.Activities.Bookmark>) döndürür.  
  
## <a name="bookmark-basics"></a>Yer işareti temelleri  
 A <xref:System.Activities.Bookmark> noktası hangi yürütme devam ettirilebilir (ve hangi girdi teslim edilebilir aracılığıyla) içinde bir iş akışı örneği temsil eder. Genellikle, bir <xref:System.Activities.Bookmark> bir ad verilir ve dış (ana bilgisayar veya uzantısı) kod yer ilgili verilerle birlikte yeniden başlatma için sorumlu. Zaman bir <xref:System.Activities.Bookmark> devam ettirildiğinde, iş akışı çalışma zamanı zamanlamaları <xref:System.Activities.BookmarkCallback> ile ilişkili temsilci <xref:System.Activities.Bookmark> ile oluşturulma zamanında.  
  
## <a name="bookmark-options"></a>Yer işareti seçenekleri  
 <xref:System.Activities.BookmarkOptions> Sınıfı türünü belirten <xref:System.Activities.Bookmark> oluşturuluyor. Olası olmayan birbirini dışlayan değerleri <xref:System.Activities.BookmarkOptions.None>, <xref:System.Activities.BookmarkOptions.MultipleResume>, ve <xref:System.Activities.BookmarkOptions.NonBlocking>. Kullanım <xref:System.Activities.BookmarkOptions.None>, oluştururken varsayılan olarak bir <xref:System.Activities.Bookmark> tam olarak bir kez sürdürülmesini bekleniyordu. Kullanım <xref:System.Activities.BookmarkOptions.MultipleResume> oluştururken bir <xref:System.Activities.Bookmark> , sürdürüldü birden çok kez. Kullanım <xref:System.Activities.BookmarkOptions.NonBlocking> oluştururken bir <xref:System.Activities.Bookmark> , hiçbir zaman sürdürüldü. Yer işaretleri varsayılan kullanılarak oluşturulan aksine <xref:System.Activities.BookmarkOptions>, <xref:System.Activities.BookmarkOptions.NonBlocking> yer işaretleri engel olmaz aktivite tamamlamanızı.  
  
## <a name="bookmark-resumption"></a>Yer işareti sürdürme  
 Yer işaretleri sürdürüldü birini kullanarak bir iş akışı dışında bir kod tarafından <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> aşırı. Bu örnekte, bir `ReadLine` etkinlik oluşturulur. Çalıştırıldığında, `ReadLine` aktivite oluşturan bir <xref:System.Activities.Bookmark>, bir geri çağırma kaydeder ve sonra bekler <xref:System.Activities.Bookmark> olarak devam eder. Ettirildiğinde, `ReadLine` etkinlik atar ile geçirilen verileri <xref:System.Activities.Bookmark> için kendi <xref:System.Activities.Activity%601.Result%2A> bağımsız değişkeni.  
  
```csharp  
public sealed class ReadLine : NativeActivity<string>  
{  
    [RequiredArgument]  
    public  InArgument<string> BookmarkName { get; set; }  
  
    protected override void Execute(NativeActivityContext context)  
    {  
        // Create a Bookmark and wait for it to be resumed.  
        context.CreateBookmark(BookmarkName.Get(context),   
            new BookmarkCallback(OnResumeBookmark));  
    }  
  
    // NativeActivity derived activities that do asynchronous operations by calling   
    // one of the CreateBookmark overloads defined on System.Activities.NativeActivityContext   
    // must override the CanInduceIdle property and return true.  
    protected override bool CanInduceIdle  
    {  
        get { return true; }  
    }  
  
    public void OnResumeBookmark(NativeActivityContext context, Bookmark bookmark, object obj)  
    {  
        // When the Bookmark is resumed, assign its value to  
        // the Result argument.  
        Result.Set(context, (string)obj);  
    }  
}  
```  
  
 Bu örnekte, bir iş akışı kullanan oluşturulur `ReadLine` kullanıcı adını toplamak ve konsol penceresine görüntülemek için etkinliği. Konak uygulama giriş toplama asıl işi yapar ve devam ettirme tarafından iş akışına geçirir <xref:System.Activities.Bookmark>.  
  
```csharp  
Variable<string> name = new Variable<string>  
{  
    Name = "name"  
};  
  
Activity wf = new Sequence  
{  
    Variables =  
    {  
        name  
    },  
    Activities =  
    {  
        new WriteLine()  
        {  
            Text = "What is your name?"  
        },  
        new ReadLine()  
        {  
            BookmarkName = "UserName",  
            Result = name  
        },  
        new WriteLine()  
        {  
            Text = new InArgument<string>((env) => "Hello, " + name.Get(env))  
        }  
    }  
};  
  
AutoResetEvent syncEvent = new AutoResetEvent(false);  
  
// Create the WorkflowApplication using the desired  
// workflow definition.  
WorkflowApplication wfApp = new WorkflowApplication(wf);  
  
// Handle the desired lifecycle events.  
wfApp.Completed = delegate(WorkflowApplicationCompletedEventArgs e)  
{  
    // Signal the host that the workflow is complete.  
    syncEvent.Set();  
};  
  
// Start the workflow.  
wfApp.Run();  
  
// Collect the user's name and resume the bookmark.  
// Bookmark resumption only occurs when the workflow  
// is idle. If a call to ResumeBookmark is made and the workflow  
// is not idle, ResumeBookmark blocks until the workflow becomes  
// idle before resuming the bookmark.  
wfApp.ResumeBookmark("UserName", Console.ReadLine());  
  
// Wait for Completed to arrive and signal that  
// the workflow is complete.  
syncEvent.WaitOne();  
```  
  
 Zaman `ReadLine` etkinlik yürütülürse, oluşturduğu bir <xref:System.Activities.Bookmark> adlı `UserName` ve yer işareti devam ettirilebilir bekler. Ana bilgisayar istenen verileri toplar ve ardından sürdürür <xref:System.Activities.Bookmark>. İş akışını sürdürür, adını görüntüler ve sonra tamamlar. Hiçbir eşitleme kodu yer işareti sürdürme açısından gerekli olduğunu unutmayın. A <xref:System.Activities.Bookmark> iş akışı boştayken ettirilebilir ve iş akışı değilse, boşta, çağrısı <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> iş akışı boşta olana kadar engeller.  
  
## <a name="bookmark-resumption-result"></a>Yer işareti sürdürme sonucu  
 <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A>döndüren bir <xref:System.Activities.BookmarkResumptionResult> yer işareti sürdürme isteği sonuçlarını göstermek için numaralandırma değeri. Olası dönüş değerleri <xref:System.Activities.BookmarkResumptionResult.Success>, <xref:System.Activities.BookmarkResumptionResult.NotReady>, ve <xref:System.Activities.BookmarkResumptionResult.NotFound>. Konaklar ve uzantıları bu değerin nasıl ilerleyeceğiniz belirlemek için kullanabilirsiniz.
