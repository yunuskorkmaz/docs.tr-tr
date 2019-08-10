---
title: Yer işaretleri-WF
ms.date: 03/30/2017
ms.assetid: 9b51a346-09ae-455c-a70a-e2264ddeb9e2
ms.openlocfilehash: a15a28cc39a4227765c238a6f2b86c72197f1a39
ms.sourcegitcommit: 9ee6cd851b6e176a5811ea28ed0d5935c71950f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68868923"
---
# <a name="bookmarks"></a>Yer İşaretleri
Yer işaretleri, bir etkinliğin bir iş akışı iş parçacığına sahip olmadan giriş için büyük bir süre beklemesini sağlayan mekanizmadır. Bir etkinlik, Stimulus için beklediğini işaret eder, bir yer işareti oluşturabilir. Bu, şu anda yürütülmekte olan Yöntem (tarafından oluşturulan <xref:System.Activities.Bookmark>) tarafından döndürülen çalışma zamanına etkinlik yürütmenin tamamlanma kabul edilmesi gerektiğini gösterir.  
  
## <a name="bookmark-basics"></a>Yer işareti temelleri  
 Bir <xref:System.Activities.Bookmark> iş akışı örneği içinde yürütmenin sürdürülebilecek (ve hangi girişin teslim edileceği) bir noktayı temsil eder. Genellikle, bir <xref:System.Activities.Bookmark> ad ve dış (konak veya uzantı) kodu, yer işaretinin ilgili verilerle sürdürülmesinden sorumludur. Bir <xref:System.Activities.Bookmark> devam edildiğinde, iş akışı çalışma zamanı, oluşturma <xref:System.Activities.BookmarkCallback> sırasında ilişkili <xref:System.Activities.Bookmark> temsilciyi zamanlar.  
  
## <a name="bookmark-options"></a>Yer işareti seçenekleri  
 Sınıf, oluşturulmakta <xref:System.Activities.Bookmark> olan türünü belirtir. <xref:System.Activities.BookmarkOptions> Birbirini dışlayan olası olmayan değerler, <xref:System.Activities.BookmarkOptions.None> <xref:System.Activities.BookmarkOptions.MultipleResume>ve <xref:System.Activities.BookmarkOptions.NonBlocking>' dir. Tam <xref:System.Activities.BookmarkOptions.None>olarak bir <xref:System.Activities.Bookmark> kez sürdürülmeleri beklenen, oluşturma işlemi varsayılan olan ' ı kullanın. Birden <xref:System.Activities.BookmarkOptions.MultipleResume> çok kez devam <xref:System.Activities.Bookmark> ettirilebilecek bir oluşturma sırasında kullanın. Hiçbir <xref:System.Activities.BookmarkOptions.NonBlocking> zaman sürdürülmeyebilir <xref:System.Activities.Bookmark> bir oluşturma sırasında kullanın. Varsayılan değer <xref:System.Activities.BookmarkOptions>kullanılarak oluşturulan yer işaretlerinin aksine <xref:System.Activities.BookmarkOptions.NonBlocking> , yer işaretleri bir etkinliğin tamamlanmasını engellemez.  
  
## <a name="bookmark-resumption"></a>Yer işareti sürdürme  
 Yer işaretleri, <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> aşırı yüklerden birini kullanan bir iş akışı dışındaki kodla devam edebilir. Bu örnekte, bir `ReadLine` etkinlik oluşturulur. Yürütüldüğünde `ReadLine` , etkinlik bir <xref:System.Activities.Bookmark>oluşturur, bir geri çağırma kaydeder <xref:System.Activities.Bookmark> ve devam etmek için bekler. Devam `ReadLine` edildiğinde etkinlik <xref:System.Activities.Bookmark> ,<xref:System.Activities.Activity%601.Result%2A> ile geçilen verileri bağımsız değişkenine atar.  
  
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
  
 Bu örnekte, `ReadLine` etkinliğin Kullanıcı adını toplayıp konsol penceresinde görüntülemesi için etkinliğini kullanan bir iş akışı oluşturulur. Ana bilgisayar uygulaması, <xref:System.Activities.Bookmark>giriş toplama işini gerçekleştirir ve devam ederek iş akışına geçirir.  
  
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
  
 Etkinlik yürütüldüğünde, adlandırılmış bir <xref:System.Activities.Bookmark> adı `UserName` oluşturur ve sonra yer işaretinin sürdürülmesini bekler. `ReadLine` Konak, istenen verileri toplar ve ardından devam ettirir <xref:System.Activities.Bookmark>. İş akışı devam eder, adı görüntüler ve sonra tamamlar. Yer işaretinin sürdürülmeye devam ettiğine ilişkin hiçbir eşitleme kodu gerekmediğini unutmayın. Yalnızca iş akışı boşta kaldığında devam <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> edebilirveişakışıboştadeğilseişakışıboştaolanakadarbloklarıçağırır.<xref:System.Activities.Bookmark>  
  
## <a name="bookmark-resumption-result"></a>Yer işareti sürdürme sonucu  
 <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A>Bookmark sürdürme <xref:System.Activities.BookmarkResumptionResult> isteğinin sonuçlarını göstermek için bir sabit listesi değeri döndürür. Olası dönüş değerleri, <xref:System.Activities.BookmarkResumptionResult.Success> <xref:System.Activities.BookmarkResumptionResult.NotReady>ve <xref:System.Activities.BookmarkResumptionResult.NotFound>' dir. Konaklar ve uzantılar, devam etmek için bu değeri kullanabilir.
