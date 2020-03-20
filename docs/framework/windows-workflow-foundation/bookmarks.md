---
title: Yer Imleri - WF
ms.date: 03/30/2017
ms.assetid: 9b51a346-09ae-455c-a70a-e2264ddeb9e2
ms.openlocfilehash: c5bd8130ee623599e80014777baf92986c3b6969
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183017"
---
# <a name="bookmarks"></a>Yer İşaretleri
Yer imleri, bir etkinliğin iş akışı iş parçacığına tutunmadan girişi pasif olarak beklemesini sağlayan mekanizmadır. Bir etkinlik uyarıcı beklediğini niçin işaret verdiğinde, bir yer imi oluşturabilir. Bu, çalışma süresine, şu anda yürütülen yöntem (oluşturdu) <xref:System.Activities.Bookmark>döndürülmüş olsa bile etkinliğin yürütülmesinin tamamlanmış olarak kabul edilmemesi gerektiğini gösterir.  
  
## <a name="bookmark-basics"></a>Yer Imi Temelleri  
 A, <xref:System.Activities.Bookmark> iş akışı örneği içinde yürütmenin sürdürülebileceği (ve girişin teslim edilebildiği) bir noktayı temsil eder. Genellikle, a <xref:System.Activities.Bookmark> bir ad verilir ve dış (ana bilgisayar veya uzantı) kodu ilgili verilerle yer imini devam ından sorumludur. A <xref:System.Activities.Bookmark> başlatıldığında, iş akışı çalışma zamanı, <xref:System.Activities.BookmarkCallback> oluşturuldurduğu <xref:System.Activities.Bookmark> anda onunla ilişkili olan temsilciyi zamanlar.  
  
## <a name="bookmark-options"></a>Yer Imi Seçenekleri  
 Sınıf <xref:System.Activities.BookmarkOptions> oluşturulan türü <xref:System.Activities.Bookmark> belirtir. Olası olmayan birbirini dışlamayan <xref:System.Activities.BookmarkOptions.None>değerler <xref:System.Activities.BookmarkOptions.MultipleResume>, <xref:System.Activities.BookmarkOptions.NonBlocking>ve . Tam <xref:System.Activities.BookmarkOptions.None>olarak bir kez <xref:System.Activities.Bookmark> devam etmesi beklenen bir oluşturma yaparken varsayılan kullanın. Birden <xref:System.Activities.BookmarkOptions.MultipleResume> çok <xref:System.Activities.Bookmark> kez yeniden başlatılabilen bir oluşturma yaparken kullanın. Hiçbir <xref:System.Activities.BookmarkOptions.NonBlocking> zaman <xref:System.Activities.Bookmark> başlatılmayan bir şey oluştururken kullanın. Varsayılan <xref:System.Activities.BookmarkOptions>kullanılarak oluşturulan yer <xref:System.Activities.BookmarkOptions.NonBlocking> imlerinden farklı olarak, yer imleri bir etkinliğin tamamlanmasını engellemez.  
  
## <a name="bookmark-resumption"></a>Yer Ii Devamı  
 Yer <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> imleri, aşırı yüklerden birini kullanarak iş akışı dışında kodla yeniden başlatılabilir. Bu örnekte, `ReadLine` bir etkinlik oluşturulur. Yürütüldüğünde, `ReadLine` etkinlik bir <xref:System.Activities.Bookmark>, geri arama kaydeder ve sonra <xref:System.Activities.Bookmark> devam etmesini bekler. Devam ettiğinde, `ReadLine` etkinlik <xref:System.Activities.Bookmark> <xref:System.Activities.Activity%601.Result%2A> bağımsız değişkeniyle geçirilen verileri atar.  
  
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
  
 Bu örnekte, kullanıcının `ReadLine` adını toplamak ve konsol penceresine görüntülemek için etkinliği kullanan bir iş akışı oluşturulur. Ana bilgisayar uygulaması, girdiyi toplama fiili işini gerçekleştirir ve <xref:System.Activities.Bookmark>devam ederek iş akışına aktarın.  
  
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
  
 `ReadLine` Etkinlik yürütüldüğünde, bir <xref:System.Activities.Bookmark> ad `UserName` ve ardından yer işaretinin devam etmesini bekler. Ana bilgisayar istenen verileri toplar ve <xref:System.Activities.Bookmark>sonra . İş akışı devam eder, adı görüntüler ve tamamlar. Yer imi devam ı ile ilgili olarak eşitleme kodu gerekmemektedir. A <xref:System.Activities.Bookmark> yalnızca iş akışı boştayken ve iş akışı boşta değilse, iş <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> akışı boşalana kadar çağrıyı engeller.  
  
## <a name="bookmark-resumption-result"></a>Yer Ii Devamı Sonucu  
 <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A>yer <xref:System.Activities.BookmarkResumptionResult> imi yeniden başlama isteğinin sonuçlarını belirtmek için numaralandırma değerini döndürür. Olası iade değerleri <xref:System.Activities.BookmarkResumptionResult.Success> <xref:System.Activities.BookmarkResumptionResult.NotReady>, <xref:System.Activities.BookmarkResumptionResult.NotFound>ve . Ana bilgisayarlar ve uzantılar, nasıl devam edileceğine karar vermek için bu değeri kullanabilir.
