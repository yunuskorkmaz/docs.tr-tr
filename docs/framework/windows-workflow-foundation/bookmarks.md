---
title: Bookmarks1
ms.date: 03/30/2017
ms.assetid: 9b51a346-09ae-455c-a70a-e2264ddeb9e2
ms.openlocfilehash: 8b7ca9549327087e30d6c72a8b784aa37ad09f3c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774161"
---
# <a name="bookmarks"></a>Yer İşaretleri
Yer işaretleri, bir iş akışı iş parçacığı tutulmadan giriş yordamlarınıza beklenecek bir etkinlik sağlayan mekanizmasıdır. Bir etkinlik için stimulus beklediğini bildirir, bir yer işareti oluşturabilir. Bu etkinlik yürütme tam olarak değerlendirilmesi gerektiğini değil çalışma zamanının gösterir bile yürütülmekte yöntemi (oluşturulduğu <xref:System.Activities.Bookmark>) döndürür.  
  
## <a name="bookmark-basics"></a>Yer işareti temelleri  
 A <xref:System.Activities.Bookmark> bir iş akışı örneği içinde bir noktaya hangi yürütme devam ettirilebilir (ve hangi girdi dağıtılabilecek aracılığıyla) temsil eder. Genellikle, bir <xref:System.Activities.Bookmark> bir ad verilir ve dış kod (konak veya uzantısı), yer işareti ile ilgili verileri işlemini sürdürmek için sorumludur. Olduğunda bir <xref:System.Activities.Bookmark> sürdürülür, iş akışı çalışma zamanı zamanlamaları <xref:System.Activities.BookmarkCallback> ile ilişkili temsilci <xref:System.Activities.Bookmark> oluşturulduğu zaman.  
  
## <a name="bookmark-options"></a>Yer işareti seçenekleri  
 <xref:System.Activities.BookmarkOptions> Sınıf türünü belirten <xref:System.Activities.Bookmark> oluşturuluyor. Mümkün olmayan birbirini dışlayan değerler <xref:System.Activities.BookmarkOptions.None>, <xref:System.Activities.BookmarkOptions.MultipleResume>, ve <xref:System.Activities.BookmarkOptions.NonBlocking>. Kullanım <xref:System.Activities.BookmarkOptions.None>, oluştururken varsayılan bir <xref:System.Activities.Bookmark> tam bir kez devam ettirilemedi beklenmektedir. Kullanım <xref:System.Activities.BookmarkOptions.MultipleResume> oluştururken bir <xref:System.Activities.Bookmark> birden çok kez ettirilebilir. Kullanım <xref:System.Activities.BookmarkOptions.NonBlocking> oluştururken bir <xref:System.Activities.Bookmark> , hiçbir zaman sürdürüldü. Varsayılan değer kullanılarak oluşturulan yer işaretleri aksine <xref:System.Activities.BookmarkOptions>, <xref:System.Activities.BookmarkOptions.NonBlocking> yer işaretleri engel olmaz bir etkinliğin tamamlanmasını.  
  
## <a name="bookmark-resumption"></a>Yer imi sürdürme  
 Yer işaretleri, kod dışında birini kullanarak bir iş akışı tarafından ettirilebilir <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> aşırı yüklemeleri. Bu örnekte, bir `ReadLine` etkinlik oluşturulur. Yürütüldüğünde, `ReadLine` etkinliği oluşturur bir <xref:System.Activities.Bookmark>, bir geri çağırma kaydeder ve sonra bekler <xref:System.Activities.Bookmark> olarak devam eder. Bunu devam ettirildiğinde `ReadLine` etkinlik ile geçirilen verileri atar <xref:System.Activities.Bookmark> için kendi <xref:System.Activities.Activity%601.Result%2A> bağımsız değişken.  
  
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
  
 Bu örnekte, bir iş akışı kullanan oluşturulur `ReadLine` kullanıcı adını toplamak ve konsol penceresinde görüntülemek için etkinlik. Konak uygulama giriş toplama asıl işi yapar ve iş akışını sürdürme tarafından geçirir <xref:System.Activities.Bookmark>.  
  
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
  
 Zaman `ReadLine` etkinlik yürütüldüğünde, oluşturur bir <xref:System.Activities.Bookmark> adlı `UserName` ve devam ettirilemedi yer işareti için bekler. Konak istenen verileri toplar ve ardından devam ettirir <xref:System.Activities.Bookmark>. İş akışını sürdürür, adını gösterir ve tamamlandıktan sonra. Hiçbir eşitleme kodu yer işaretinin sürdürme açısından gerekli olduğuna dikkat edin. A <xref:System.Activities.Bookmark> iş akışı boştayken sürdürülebilir ve iş akışı değilse, boşta, çağrı <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> iş akışı boşta olana kadar engeller.  
  
## <a name="bookmark-resumption-result"></a>Yer imi sürdürme sonucu  
 <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> döndürür bir <xref:System.Activities.BookmarkResumptionResult> yer imi sürdürme isteğin sonuçlarını gösteren numaralandırma değeri. Olası dönüş değerleri <xref:System.Activities.BookmarkResumptionResult.Success>, <xref:System.Activities.BookmarkResumptionResult.NotReady>, ve <xref:System.Activities.BookmarkResumptionResult.NotFound>. Konakları ve uzantıları bu değeri nasıl ilerleyeceğiniz belirlemek için kullanabilirsiniz.
