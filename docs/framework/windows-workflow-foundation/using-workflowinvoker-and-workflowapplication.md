---
title: WorkflowInvoker ve WorkflowApplication Kullanma
ms.date: 03/30/2017
ms.assetid: cd0e583c-a3f9-4fa2-b247-c7b3368c48a7
ms.openlocfilehash: ffb8277d9b1b7369ada7add36cd833a64acbaa7d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962206"
---
# <a name="using-workflowinvoker-and-workflowapplication"></a>WorkflowInvoker ve WorkflowApplication Kullanma
Windows Workflow Foundation (WF), iş akışlarını barındırmak için çeşitli yöntemler sağlar. <xref:System.Activities.WorkflowInvoker>bir iş akışını Yöntem çağrısı gibi çağırmak için basit bir yol sağlar ve yalnızca kalıcılığı kullanmayan iş akışları için kullanılabilir. <xref:System.Activities.WorkflowApplication>yaşam döngüsü olayları, yürütme denetimi, yer işareti sürdürme ve kalıcılık bildirimini içeren iş akışlarını yürütmek için daha zengin bir model sağlar. <xref:System.ServiceModel.Activities.WorkflowServiceHost>ileti etkinlikleri için destek sağlar ve öncelikle iş akışı hizmetleriyle birlikte kullanılır. Bu konu, ve <xref:System.Activities.WorkflowInvoker> <xref:System.Activities.WorkflowApplication>ile barındırma iş akışını tanıtır. İle <xref:System.ServiceModel.Activities.WorkflowServiceHost>iş akışlarını barındırma hakkında daha fazla bilgi için bkz. [Workflow Services](../wcf/feature-details/workflow-services.md) ve [barındırma iş akışı hizmetlerine genel bakış](../wcf/feature-details/hosting-workflow-services-overview.md).  
  
## <a name="using-workflowinvoker"></a>Workflowınitialvoker kullanma  
 <xref:System.Activities.WorkflowInvoker>bir iş akışını bir yöntem çağrısı gibi yürütmek için bir model sağlar. Kullanarak <xref:System.Activities.WorkflowInvoker>bir iş akışını çağırmak için <xref:System.Activities.WorkflowInvoker.Invoke%2A> yöntemini çağırın ve çağırmak için iş akışının iş akışı tanımını geçirin. Bu örnekte, kullanılarak <xref:System.Activities.Statements.WriteLine> <xref:System.Activities.WorkflowInvoker>bir etkinlik çağrılır.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#1](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#1)]  
  
 Kullanılarak <xref:System.Activities.WorkflowInvoker>bir iş akışı çağrıldığında, iş akışı çağıran iş parçacığı üzerinde yürütülür <xref:System.Activities.WorkflowInvoker.Invoke%2A> ve herhangi bir boşta kalma süresi dahil, iş akışı tamamlanana kadar engeller. İş akışının tamamlaması gereken bir zaman aşımı aralığı yapılandırmak için, bir <xref:System.Activities.WorkflowInvoker.Invoke%2A> <xref:System.TimeSpan> parametre alan aşırı yüklemelerden birini kullanın. Bu örnekte, bir iş akışı iki farklı zaman aşımı aralıklarıyla iki kez çağırılır. İlk iş akışı tamamlanmıyor ancak ikincisi.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#50](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#50)]  
  
> [!NOTE]
> <xref:System.TimeoutException> Yalnızca zaman aşımı aralığı geçtiğinde ve iş akışı yürütme sırasında boşta kaldığında oluşturulur. İş akışı boşta kalırsa, tamamlanması için belirtilen zaman aşımı aralığından daha uzun süren bir iş akışı başarıyla tamamlanır.  
  
 <xref:System.Activities.WorkflowInvoker>Ayrıca Invoke yönteminin zaman uyumsuz sürümlerini sağlar. Daha fazla bilgi için bkz. <xref:System.Activities.WorkflowInvoker.InvokeAsync%2A> ve <xref:System.Activities.WorkflowInvoker.BeginInvoke%2A>.  
  
### <a name="setting-input-arguments-of-a-workflow"></a>Bir Iş akışının giriş bağımsız değişkenlerini ayarlama  
 Veriler, iş akışının giriş bağımsız değişkenlerine eşlenen bağımsız değişken adına göre anahtarlı giriş parametrelerinin bir sözlüğünü kullanarak bir iş akışına geçirilebilir. Bu örnekte, bir <xref:System.Activities.Statements.WriteLine> çağırılır ve <xref:System.Activities.Statements.WriteLine.Text%2A> bağımsız değişkeninin değeri giriş parametrelerinin sözlüğü kullanılarak belirtilir.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#3](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#3)]  
  
### <a name="retrieving-output-arguments-of-a-workflow"></a>Bir Iş akışının çıkış bağımsız değişkenlerini alma  
 Bir iş akışının çıkış parametreleri, çağrısından <xref:System.Activities.WorkflowInvoker.Invoke%2A>döndürülen çıktılar sözlüğü kullanılarak elde edilebilir. Aşağıdaki örnek, iki giriş bağımsız değişkenine ve iki çıkış `Divide` bağımsız değişkenine sahip tek bir etkinlikten oluşan bir iş akışını çağırır. İş akışı çağrıldığında, `arguments` her giriş bağımsız değişkeninin değerlerini içeren sözlük geçirilir ve bağımsız değişken adına göre anahtarlanır. Çağrısı `Invoke` döndürüldüğünde, her çıkış bağımsız değişkeni `outputs` sözlükte döndürülür ve bağımsız değişken adına göre anahtarlanır.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#120](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#120)]  
  
 [!code-csharp[CFX_WorkflowInvokerExample#20](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#20)]  
  
 <xref:System.Activities.ActivityWithResult>İş akışı, `CodeActivity<TResult>` <xref:System.Activities.Activity%601.Result%2A> `Invoke` veya `Activity<TResult>`gibi öğesinden türetilse ve iyi tanımlanmış çıkış bağımsız değişkenine ek olarak çıkış bağımsız değişkenleri varsa,, ' ın genel olmayan bir aşırı yüklemesi, ek bağımsız değişkenler. Bunu yapmak için geçirilen `Invoke` iş akışı tanımının türünde <xref:System.Activities.Activity>olması gerekir. `Divide` Bu örnekte `CodeActivity<int>` ,etkinlik`Invoke` öğesinden türetilir, ancak ' ın genel olmayan bir aşırı yüklemesinin, tek bir dönüş değeri yerine bağımsız değişkenlerin bir sözlüğünü döndüren kullanıldığı şekildebildirilmiştir.<xref:System.Activities.Activity>  
  
 [!code-csharp[CFX_WorkflowInvokerExample#121](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#121)]  
  
 [!code-csharp[CFX_WorkflowInvokerExample#21](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#21)]  
  
## <a name="using-workflowapplication"></a>WorkflowApplication kullanma  
 <xref:System.Activities.WorkflowApplication>iş akışı örneği yönetimi için zengin bir özellikler kümesi sağlar. <xref:System.Activities.WorkflowApplication>, çalışma zamanını kapsülleyen gerçek <xref:System.Activities.Hosting.WorkflowInstance>iş parçacığı güvenli proxy 'si olarak davranır ve iş akışı örnekleri oluşturma ve yükleme, duraklatma ve sürdürme, sonlandırma ve yaşam döngüsü olaylarının bildirilmesi için yöntemler sağlar. <xref:System.Activities.WorkflowApplication> Kullanarak<xref:System.Activities.WorkflowApplication>bir iş akışını çalıştırmak için, istediğiniz yaşam döngüsü olaylarına abone olun, iş akışını başlatın ve sonra bitmesini bekleyin. Bu örnekte, bir <xref:System.Activities.Statements.WriteLine> etkinlikten oluşan bir iş akışı tanımı oluşturulur <xref:System.Activities.WorkflowApplication> ve belirtilen iş akışı tanımı kullanılarak oluşturulur. <xref:System.Activities.WorkflowApplication.Completed%2A>, iş akışı tamamlandığında konağa bildirilecek şekilde işlenir, iş akışı öğesine <xref:System.Activities.WorkflowApplication.Run%2A>çağrısıyla başlatılır ve sonra konağın iş akışının tamamlanmasını bekler. İş akışı tamamlandığında, <xref:System.Threading.AutoResetEvent> ayarlanır ve konak uygulama, aşağıdaki örnekte gösterildiği gibi yürütmeyi sürdürür.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#31](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#31)]  
  
### <a name="workflowapplication-lifecycle-events"></a>WorkflowApplication yaşam döngüsü olayları  
 <xref:System.Activities.WorkflowApplication.Completed%2A>Uygulamasına ek olarak, bir iş akışı kaldırıldığında (<xref:System.Activities.WorkflowApplication.Idle%2A> <xref:System.Activities.WorkflowApplication.Unloaded%2A>), iptal edilen (<xref:System.Activities.WorkflowApplication.Aborted%2A>), boşta (ve <xref:System.Activities.WorkflowApplication.PersistableIdle%2A>) veya işlenmeyen bir özel durum oluştuğunda<xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>(), ana bilgisayar yazarlarına bildirim uygulanabilir. İş akışı uygulaması geliştiricileri, aşağıdaki örnekte gösterildiği gibi bu bildirimleri işleyebilir ve uygun eylemi gerçekleştirebilir.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#32](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#32)]  
  
### <a name="setting-input-arguments-of-a-workflow"></a>Bir Iş akışının giriş bağımsız değişkenlerini ayarlama  
 Veriler, kullanılırken <xref:System.Activities.WorkflowInvoker>verilerin geçirildiği yönteme benzer şekilde, bir parametre sözlüğü kullanılarak başlatıldığı için bir iş akışına geçirilebilir. Sözlükteki her öğe, belirtilen iş akışının giriş bağımsız değişkeniyle eşlenir. Bu örnekte, bir <xref:System.Activities.Statements.WriteLine> etkinlikten oluşan bir iş akışı çağrılır <xref:System.Activities.Statements.WriteLine.Text%2A> ve bağımsız değişkeni giriş parametrelerinin sözlüğü kullanılarak belirtilir.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#30](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#30)]  
  
### <a name="retrieving-output-arguments-of-a-workflow"></a>Bir Iş akışının çıkış bağımsız değişkenlerini alma  
 Bir iş akışı tamamlandığında, <xref:System.Activities.WorkflowApplication.Completed%2A> <xref:System.Activities.WorkflowApplicationCompletedEventArgs.Outputs%2A?displayProperty=nameWithType> sözlüğe erişerek herhangi bir çıkış bağımsız değişkeni işleyicide alınabilir. Aşağıdaki örnek kullanarak <xref:System.Activities.WorkflowApplication>bir iş akışı barındırır. Örnek, tek `DiceRoll` bir etkinlikten oluşan iş akışı tanımı kullanılarak oluşturulur. <xref:System.Activities.WorkflowApplication> `DiceRoll` Etkinliğin, zar alma işleminin sonuçlarını temsil eden iki çıkış bağımsız değişkeni vardır. İş akışı tamamlandığında, çıktılar <xref:System.Activities.WorkflowApplication.Completed%2A> işleyicide alınır.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#130](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#130)]  
  
 [!code-csharp[CFX_WorkflowApplicationExample#21](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#21)]  
  
> [!NOTE]
> <xref:System.Activities.WorkflowApplication>ve <xref:System.Activities.WorkflowInvoker> giriş bağımsız değişkenlerinin sözlüğünü alın ve `out` bağımsız değişkenlerin sözlüğünü döndürün. Bu sözlük parametreleri, özellikleri ve dönüş değerleri türündedir `IDictionary<string, object>`. Öğesine geçirilen sözlük sınıfının gerçek örneği, uygulayan `IDictionary<string, object>`herhangi bir sınıf olabilir. Bu örneklerde, `Dictionary<string, object>` kullanılır. Sözlükler hakkında daha fazla bilgi için bkz <xref:System.Collections.Generic.IDictionary%602> . <xref:System.Collections.Generic.Dictionary%602>ve.  
  
### <a name="passing-data-into-a-running-workflow-using-bookmarks"></a>Yer Imlerini kullanarak çalışan bir Iş akışına veri geçirme  
 Yer işaretleri, bir etkinliğin çok büyük bir süre içinde çalışmaya devam edeceği ve çalışan bir iş akışı örneğine veri geçirme mekanizması olan mekanizmadır. Bir etkinlik veri bekliyorsa, aşağıdaki örnekte gösterildiği gibi bir <xref:System.Activities.Bookmark> etkinlik oluşturup, devam <xref:System.Activities.Bookmark> edildiğinde çağrılacak bir geri çağırma yöntemi kaydedebilir.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#15](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#15)]  
  
 Yürütüldüğünde `ReadLine` , etkinlik bir <xref:System.Activities.Bookmark>oluşturur, bir geri çağırma kaydeder <xref:System.Activities.Bookmark> ve devam etmek için bekler. Devam `ReadLine` edildiğinde etkinlik <xref:System.Activities.Bookmark> ,<xref:System.Activities.Activity%601.Result%2A> ile geçilen verileri bağımsız değişkenine atar. Bu örnekte, `ReadLine` etkinliğin Kullanıcı adını toplayıp konsol penceresinde görüntülemesi için etkinliğini kullanan bir iş akışı oluşturulur.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#22](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#22)]  
  
 Etkinlik yürütüldüğünde, adlandırılmış bir <xref:System.Activities.Bookmark> adı `UserName` oluşturur ve sonra yer işaretinin sürdürülmesini bekler. `ReadLine` Konak, istenen verileri toplar ve ardından devam ettirir <xref:System.Activities.Bookmark>. İş akışı devam eder, adı görüntüler ve sonra tamamlar.  
  
 Konak uygulama, etkin bir yer işareti olup olmadığını anlamak için iş akışını inceleyebilir. Bunu <xref:System.Activities.WorkflowApplication.GetBookmarks%2A> , bir <xref:System.Activities.WorkflowApplication> örneğin yöntemini çağırarak veya <xref:System.Activities.WorkflowApplication.Idle%2A> işleyicide inceleyerek <xref:System.Activities.WorkflowApplicationIdleEventArgs> yapabilir.  
  
 Aşağıdaki kod örneği, yer işareti sürdürülmeye başlamadan önce etkin yer işaretlerinin numaralandırılmasının dışında, önceki örneğe benzer. İş akışı başlatılır <xref:System.Activities.Bookmark> ve oluşturulduktan sonra iş akışı <xref:System.Activities.WorkflowApplication.GetBookmarks%2A> boşta kaldığında çağrılır. İş akışı tamamlandığında, konsola aşağıdaki çıktı görüntülenir.  
  
 **Adınız ne?**  
**BookmarkName: Kullanıcı adı-OwnerDisplayName: ReadLine**   
**Steve**   
**Merhaba, emre**

[!code-csharp[CFX_WorkflowApplicationExample#14](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#14)]  
  
 Aşağıdaki kod örneği, bir <xref:System.Activities.WorkflowApplicationIdleEventArgs> <xref:System.Activities.WorkflowApplication> örneğin <xref:System.Activities.WorkflowApplication.Idle%2A> işleyicisine geçirilen ' i inceler. Bu örnekte <xref:System.Activities.Bookmark> `EnterGuess`, boşta duran iş akışı, adlı `ReadInt`bir etkinliğe ait olan bir ada sahip bir ada sahip. Bu kod örneği, [nasıl yapılacağını temel alarak: Başlangıç öğreticisinin](how-to-run-a-workflow.md)bir parçası olan iş akışını çalıştırın [](getting-started-tutorial.md). Bu adımdaki <xref:System.Activities.WorkflowApplication.Idle%2A> işleyici bu örnekteki kodu içerecek şekilde değiştirilirse aşağıdaki çıktı görüntülenir.  
  
 **BookmarkName: Entertahminin-OwnerDisplayName: ReadInt**
 
 [!code-csharp[CFX_WorkflowApplicationExample#2](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#2)]  
  
## <a name="summary"></a>Özet  
 <xref:System.Activities.WorkflowInvoker>iş akışlarını çağırmak için basit bir yol sağlar ve bir iş akışının başlangıcında veri geçirme ve tamamlanan bir iş akışından veri ayıklama için yöntemler sağlasa da, kullanılabilecek olan daha karmaşık senaryolar <xref:System.Activities.WorkflowApplication> sağlamaz.
