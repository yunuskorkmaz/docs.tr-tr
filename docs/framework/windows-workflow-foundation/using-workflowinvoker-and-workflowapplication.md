---
title: Workflowınvoker ve WorkflowApplication kullanma
ms.date: 03/30/2017
ms.assetid: cd0e583c-a3f9-4fa2-b247-c7b3368c48a7
ms.openlocfilehash: 29d152cd6011fb3b55aae60726d095dc44dd23a5
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707696"
---
# <a name="using-workflowinvoker-and-workflowapplication"></a>Workflowınvoker ve WorkflowApplication kullanma
Windows Workflow Foundation (WF) iş akışları barındırma çeşitli yöntemler sunar. <xref:System.Activities.WorkflowInvoker> bir yöntem çağrısının olan ve kalıcılığı kullanmayan yalnızca iş akışları için kullanılabilir gibi bir iş akışı çalıştırmak için basit bir yol sağlar. <xref:System.Activities.WorkflowApplication> yaşam döngüsü olayları, yürütme denetimi, yer imi sürdürme ve Kalıcılık bildirimi içeren iş akışlarını yürütmek için daha zengin bir model sağlar. <xref:System.ServiceModel.Activities.WorkflowServiceHost> Mesajlaşma etkinlikleri için destek sağlar ve öncelikli olarak iş akışı Hizmetleri ile kullanılır. Bu konu ile iş akışı barındırma için tanıtır <xref:System.Activities.WorkflowInvoker> ve <xref:System.Activities.WorkflowApplication>. İş akışlarıyla barındırma hakkında daha fazla bilgi için <xref:System.ServiceModel.Activities.WorkflowServiceHost>, bkz: [iş akışı Hizmetleri](../wcf/feature-details/workflow-services.md) ve [iş akışı hizmetlerini barındırma genel bakış](../wcf/feature-details/hosting-workflow-services-overview.md).  
  
## <a name="using-workflowinvoker"></a>Workflowınvoker kullanma  
 <xref:System.Activities.WorkflowInvoker> bir yöntem çağrısının değilmiş gibi bir iş akışını yürütmek için bir model sağlar. Bir iş akışı kullanılarak çağrılacak <xref:System.Activities.WorkflowInvoker>, çağrı <xref:System.Activities.WorkflowInvoker.Invoke%2A> yöntemi ve çağırmak için iş akışının iş akışı tanımı geçirin. Bu örnekte, bir <xref:System.Activities.Statements.WriteLine> etkinliği kullanarak çağrıldığında <xref:System.Activities.WorkflowInvoker>.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#1](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#1)]  
  
 Bir iş akışı kullanarak çağrıldığında <xref:System.Activities.WorkflowInvoker>, iş akışını çağıran iş parçacığında yürütülür ve <xref:System.Activities.WorkflowInvoker.Invoke%2A> yöntemi, iş akışı herhangi bir boşta kalma süresi de dahil olmak üzere tamamlanıncaya kadar engeller. İş akışı tamamlamalısınız bir zaman aşımı aralığı yapılandırmak için aşağıdakilerden birini kullanın: <xref:System.Activities.WorkflowInvoker.Invoke%2A> alan aşırı yüklemeler bir <xref:System.TimeSpan> parametresi. Bu örnekte, iki farklı zaman aşımı aralığı ile bir iş akışı çağrılır. İlk iş akışı tamamlandıktan, ancak ikinci desteklemez.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#50](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#50)]  
  
> [!NOTE]
>  <xref:System.TimeoutException> Yalnızca yürütme sırasında iş akışı boş olur ve zaman aşımı aralığı sona erdiğinde, oluşturulur. İş akışı boş hale gelmezse, tamamlamak için belirtilen zaman aşımı aralığından daha uzun sürer bir iş akışı başarıyla tamamlar.  
  
 <xref:System.Activities.WorkflowInvoker> Ayrıca Invoke yöntemi zaman uyumsuz sürümlerini sağlar. Daha fazla bilgi için bkz. <xref:System.Activities.WorkflowInvoker.InvokeAsync%2A> ve <xref:System.Activities.WorkflowInvoker.BeginInvoke%2A>.  
  
### <a name="setting-input-arguments-of-a-workflow"></a>Ayar giriş bağımsız değişkenleri bir iş akışı  
 Veri Sözlüğü eşleyen bir iş akışı giriş bağımsız değişkenleri, bağımsız değişken adına göre anahtarlanır giriş parametrelerini kullanarak bir iş akışı içinde geçirilebilir. Bu örnekte, bir <xref:System.Activities.Statements.WriteLine> çağrılır ve değeri kendi <xref:System.Activities.Statements.WriteLine.Text%2A> bağımsız değişkeni, girdi parametrelerinin sözlüğünü kullanarak belirtilir.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#3](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#3)]  
  
### <a name="retrieving-output-arguments-of-a-workflow"></a>Çıkış değişkenleri bir iş akışı alınıyor  
 Bir iş akışının çıkış parametreleri çağrısından döndürülen çıkış sözlüğünü kullanarak elde edilebilir <xref:System.Activities.WorkflowInvoker.Invoke%2A>. Aşağıdaki örnek tek bir oluşan bir iş akışını çağırır `Divide` iki giriş bağımsız değişkenleri ve iki bağımsız değişken çıkış, etkinlik. İş akışı çağrıldığında `arguments` her bağımsız değişken, bağımsız değişken adına göre anahtarlanır giriş değerlerini içeren sözlük geçirilir. Zaman çağrısı `Invoke` döndürür, her çıkış bağımsız değişkeni döndürülür `outputs` da bağımsız değişken adına göre anahtarlanır sözlüğü.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#120](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#120)]  
  
 [!code-csharp[CFX_WorkflowInvokerExample#20](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#20)]  
  
 İş akışı türetildiği varsa <xref:System.Activities.ActivityWithResult>, gibi `CodeActivity<TResult>` veya `Activity<TResult>`, ve iyi tanımlanmış yanı sıra çıkış değişkenlerini <xref:System.Activities.Activity%601.Result%2A> çıkış bağımsız değişkeni, genel olmayan aşırı yüklemesini `Invoke` almak için kullanılması gerekir Ek bağımsız değişkenler. Bunu yapmak için yöntemlere iş akışı tanımı geçirilen `Invoke` türünde olmalıdır <xref:System.Activities.Activity>. Bu örnekte `Divide` etkinlik türetilir `CodeActivity<int>`, olarak bildirilmiş ancak <xref:System.Activities.Activity> genel olmayan bir aşırı yükleme böylece `Invoke` olan kullanılan bağımsız değişkenler tek bir dönüş değeri yerine bir sözlüğü döndürür.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#121](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#121)]  
  
 [!code-csharp[CFX_WorkflowInvokerExample#21](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#21)]  
  
## <a name="using-workflowapplication"></a>WorkflowApplication kullanma  
 <xref:System.Activities.WorkflowApplication> İş akışı örnek yönetimi için zengin bir özellikler kümesi sağlar. <xref:System.Activities.WorkflowApplication> Gerçek iş parçacığı güvenli proxy görevi gören <xref:System.Activities.Hosting.WorkflowInstance>, çalışma zamanını saklar ve oluşturma ve iş akışı örneği yükleniyor, duraklatma ve sürdürme, sonlandırma ve yaşam döngüsü olaylarını bildirilmesi için yöntemler sağlar. Kullanan bir iş akışında çalıştırmak için <xref:System.Activities.WorkflowApplication> oluşturduğunuz <xref:System.Activities.WorkflowApplication>, istenen yaşam döngüsü olaylara abone olma, iş akışını başlatmak ve bitmesini bekleyin. Bu örnekte, bir iş akışı tanımı, oluşur bir <xref:System.Activities.Statements.WriteLine> etkinlik oluşturulur ve <xref:System.Activities.WorkflowApplication> belirtilen iş akışı tanımı kullanılarak oluşturulur. <xref:System.Activities.WorkflowApplication.Completed%2A> olan iş akışı tamamlandığında konak bildirilir için işlenen, bir çağrı iş akışı başlatılır <xref:System.Activities.WorkflowApplication.Run%2A>, ve ardından konak tamamlamak iş akışı için bekler. İş akışı tamamlandığında <xref:System.Threading.AutoResetEvent> kümesi ve ana bilgisayar aşağıdaki örnekte gösterildiği gibi uygulama yürütme, devam.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#31](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#31)]  
  
### <a name="workflowapplication-lifecycle-events"></a>WorkflowApplication yaşam döngüsü olayları  
 Ek olarak <xref:System.Activities.WorkflowApplication.Completed%2A>, konak yazarları bildirim iş akışı kaldırıldığında (<xref:System.Activities.WorkflowApplication.Unloaded%2A>), durduruldu (<xref:System.Activities.WorkflowApplication.Aborted%2A>), boş olur (<xref:System.Activities.WorkflowApplication.Idle%2A> ve <xref:System.Activities.WorkflowApplication.PersistableIdle%2A>), veya işlenmeyen bir özel durum oluşur (<xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>). İş akışı uygulama geliştiricileri, bu bildirimleri işlemek ve uygun eylemi, aşağıdaki örnekte gösterildiği gibi gerçekleştirin.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#32](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#32)]  
  
### <a name="setting-input-arguments-of-a-workflow"></a>Ayar giriş bağımsız değişkenleri bir iş akışı  
 Veri parametrelerinin bir sözlük kullanılarak başlatıldığında gibi bir iş akışında geçirilebilir, benzer şekilde veriler kullanılırken geçirilen <xref:System.Activities.WorkflowInvoker>. Her bir öğe sözlükte, belirtilen iş akışı giriş bağımsız değişkeni eşler. Bu örnekte, bir iş akışı, oluşur bir <xref:System.Activities.Statements.WriteLine> etkinlik çağrılır ve kendi <xref:System.Activities.Statements.WriteLine.Text%2A> bağımsız değişkeni, girdi parametrelerinin sözlüğünü kullanarak belirtilir.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#30](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#30)]  
  
### <a name="retrieving-output-arguments-of-a-workflow"></a>Çıkış değişkenleri bir iş akışı alınıyor  
 İçinde bir iş akışı tamamlandığında, herhangi bir çıkış bağımsız değişkeni alınabilir <xref:System.Activities.WorkflowApplication.Completed%2A> erişerek işleyici <xref:System.Activities.WorkflowApplicationCompletedEventArgs.Outputs%2A?displayProperty=nameWithType> sözlüğü. Aşağıdaki örnek, bir iş akışı kullanarak barındıran <xref:System.Activities.WorkflowApplication>. A <xref:System.Activities.WorkflowApplication> örneği içeren bir tek bir iş akışı tanımı kullanılarak oluşturulan `DiceRoll` etkinlik. `DiceRoll` Etkinlik dice toplama işleminin sonuçlarını temsil eden iki çıkış bağımsız değişkeni vardır. İş akışı tamamlandığında çıktısı alınır <xref:System.Activities.WorkflowApplication.Completed%2A> işleyici.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#130](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#130)]  
  
 [!code-csharp[CFX_WorkflowApplicationExample#21](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#21)]  
  
> [!NOTE]
>  <xref:System.Activities.WorkflowApplication> ve <xref:System.Activities.WorkflowInvoker> giriş bağımsız değişkeni sözlüğü almak ve bir sözlüğü döndürür `out` bağımsız değişkenler. Bu sözlük parametreleri, özellikler ve dönüş değerleri tipindedir `IDictionary<string, object>`. Gerçek geçirilen dictionary sınıfı örneğini uygulayan sınıf olabilir `IDictionary<string, object>`. Bu örneklerde `Dictionary<string, object>` kullanılır. Sözlükler hakkında daha fazla bilgi için bkz: <xref:System.Collections.Generic.IDictionary%602> ve <xref:System.Collections.Generic.Dictionary%602>.  
  
### <a name="passing-data-into-a-running-workflow-using-bookmarks"></a>Geçirme verilerini bir çalışan iş akışı yer işaretlerini kullanma  
 Yer işaretleri, bir etkinlik yordamlarınıza devam ettirilemedi bekleyebilir ve içinde çalışan bir iş akışı örneği verileri geçirmek için bir mekanizma olan mekanizmasıdır. Bir etkinlik verilerini bekliyorsa oluşturabilirsiniz bir <xref:System.Activities.Bookmark> ve ne zaman çağrılacak bir geri arama yöntemi kaydedin <xref:System.Activities.Bookmark> , aşağıdaki örnekte gösterildiği gibi sürdürülür.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#15](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#15)]  
  
 Yürütüldüğünde, `ReadLine` etkinliği oluşturur bir <xref:System.Activities.Bookmark>, bir geri çağırma kaydeder ve sonra bekler <xref:System.Activities.Bookmark> olarak devam eder. Bunu devam ettirildiğinde `ReadLine` etkinlik ile geçirilen verileri atar <xref:System.Activities.Bookmark> için kendi <xref:System.Activities.Activity%601.Result%2A> bağımsız değişken. Bu örnekte, bir iş akışı kullanan oluşturulur `ReadLine` kullanıcı adını toplamak ve konsol penceresinde görüntülemek için etkinlik.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#22](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#22)]  
  
 Zaman `ReadLine` etkinlik yürütüldüğünde, oluşturur bir <xref:System.Activities.Bookmark> adlı `UserName` ve devam ettirilemedi yer işareti için bekler. Konak istenen verileri toplar ve ardından devam ettirir <xref:System.Activities.Bookmark>. İş akışını sürdürür, adını gösterir ve tamamlandıktan sonra.  
  
 Ana bilgisayar uygulaması işaretlerini etkin olup olmadığını belirlemek için iş akışı inceleyebilirsiniz. Bunu çağırarak yapabilirsiniz <xref:System.Activities.WorkflowApplication.GetBookmarks%2A> yöntemi bir <xref:System.Activities.WorkflowApplication> örneği veya göre inceleyerek <xref:System.Activities.WorkflowApplicationIdleEventArgs> içinde <xref:System.Activities.WorkflowApplication.Idle%2A> işleyici.  
  
 Aşağıdaki kod örneği önceki örnekteki gibi etkin yer işaretleri, yer işareti sürdürüldü önce numaralandırılır dışında aynıdır. İş akışı başlatıldığında, bir kez <xref:System.Activities.Bookmark> oluşturulur ve iş akışı boşta giden <xref:System.Activities.WorkflowApplication.GetBookmarks%2A> çağrılır. İş akışı tamamlandığında, aşağıdaki çıktıyı konsola görüntülenir.  
  
 **Adınız ne?**  
**YerİşaretiAdı: Kullanıcı adı - OwnerDisplayName: ReadLine**   
**Steve**   
**Merhaba, Steve**

[!code-csharp[CFX_WorkflowApplicationExample#14](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#14)]  
  
 Aşağıdaki kod örneği inceler <xref:System.Activities.WorkflowApplicationIdleEventArgs> yöntemlere geçirilen <xref:System.Activities.WorkflowApplication.Idle%2A> işleyicisinde bir <xref:System.Activities.WorkflowApplication> örneği. Bu örnekte, boşta giden iş akışı olan bir <xref:System.Activities.Bookmark> adıyla `EnterGuess`, adlı bir etkinlik tarafından sahip olunan `ReadInt`. Bu kod örneği, devre dışı tabanlı [nasıl yapılır: İş akışı çalıştırma](how-to-run-a-workflow.md), parçası olduğu [başlangıç Öğreticisi](getting-started-tutorial.md). Varsa <xref:System.Activities.WorkflowApplication.Idle%2A> işleyici bu adımda, bu örnekteki kod içerecek şekilde değiştirildiğinde, aşağıdaki çıktısı görüntülenir.  
  
 **YerİşaretiAdı: EnterGuess - OwnerDisplayName: ReadInt**
 
 [!code-csharp[CFX_WorkflowApplicationExample#2](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#2)]  
  
## <a name="summary"></a>Özet  
 <xref:System.Activities.WorkflowInvoker> İş akışları çağırmak için basit bir yol sağlar ve bir iş akışının başlangıcında verileri geçirme ve tamamlanan bir iş akışından veri ayıklamak için yöntemler sağlar, ancak bu daha karmaşık senaryolarda nerede olduğu sağlamaz <xref:System.Activities.WorkflowApplication> kullanılabilir.
