---
title: WorkflowInvoker ve WorkflowApplication Kullanma
description: Bu makalede, Windows Workflow Foundation ' de Workflowwınvoker ve WorkflowApplication kullanılarak barındırılan iş akışı açıklanmaktadır.
ms.date: 03/30/2017
ms.assetid: cd0e583c-a3f9-4fa2-b247-c7b3368c48a7
ms.openlocfilehash: 50ad291bc73818092e7a08d489d6860636f9c379
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421325"
---
# <a name="using-workflowinvoker-and-workflowapplication"></a>WorkflowInvoker ve WorkflowApplication Kullanma
Windows Workflow Foundation (WF), iş akışlarını barındırmak için çeşitli yöntemler sağlar. <xref:System.Activities.WorkflowInvoker>bir iş akışını Yöntem çağrısı gibi çağırmak için basit bir yol sağlar ve yalnızca kalıcılığı kullanmayan iş akışları için kullanılabilir. <xref:System.Activities.WorkflowApplication>yaşam döngüsü olayları, yürütme denetimi, yer işareti sürdürme ve kalıcılık bildirimini içeren iş akışlarını yürütmek için daha zengin bir model sağlar. <xref:System.ServiceModel.Activities.WorkflowServiceHost>ileti etkinlikleri için destek sağlar ve öncelikle iş akışı hizmetleriyle birlikte kullanılır. Bu konu, ve ile barındırma iş akışını <xref:System.Activities.WorkflowInvoker> tanıtır <xref:System.Activities.WorkflowApplication> . İle iş akışlarını barındırma hakkında daha fazla bilgi için <xref:System.ServiceModel.Activities.WorkflowServiceHost> bkz. [Workflow Services](../wcf/feature-details/workflow-services.md) ve [barındırma Iş akışı hizmetlerine genel bakış](../wcf/feature-details/hosting-workflow-services-overview.md).  
  
## <a name="using-workflowinvoker"></a>Workflowınitialvoker kullanma  
 <xref:System.Activities.WorkflowInvoker>bir iş akışını bir yöntem çağrısı gibi yürütmek için bir model sağlar. Kullanarak bir iş akışını çağırmak için <xref:System.Activities.WorkflowInvoker> yöntemini çağırın <xref:System.Activities.WorkflowInvoker.Invoke%2A> ve çağırmak için iş akışının iş akışı tanımını geçirin. Bu örnekte, kullanılarak bir <xref:System.Activities.Statements.WriteLine> etkinlik çağrılır <xref:System.Activities.WorkflowInvoker> .  
  
 [!code-csharp[CFX_WorkflowInvokerExample#1](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#1)]  
  
 Kullanılarak bir iş akışı çağrıldığında, iş akışı <xref:System.Activities.WorkflowInvoker> çağıran iş parçacığı üzerinde yürütülür ve <xref:System.Activities.WorkflowInvoker.Invoke%2A> herhangi bir boşta kalma süresi dahil, iş akışı tamamlanana kadar engeller. İş akışının tamamlaması gereken bir zaman aşımı aralığı yapılandırmak için, <xref:System.Activities.WorkflowInvoker.Invoke%2A> bir parametre alan aşırı yüklemelerden birini kullanın <xref:System.TimeSpan> . Bu örnekte, bir iş akışı iki farklı zaman aşımı aralıklarıyla iki kez çağırılır. İlk iş akışı tamamlanmıyor ancak ikincisi.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#50](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#50)]  
  
> [!NOTE]
> <xref:System.TimeoutException>Yalnızca zaman aşımı aralığı geçtiğinde ve iş akışı yürütme sırasında boşta kaldığında oluşturulur. İş akışı boşta kalırsa, tamamlanması için belirtilen zaman aşımı aralığından daha uzun süren bir iş akışı başarıyla tamamlanır.  
  
 <xref:System.Activities.WorkflowInvoker>Ayrıca Invoke yönteminin zaman uyumsuz sürümlerini sağlar. Daha fazla bilgi için <xref:System.Activities.WorkflowInvoker.InvokeAsync%2A> ve <xref:System.Activities.WorkflowInvoker.BeginInvoke%2A> bölümlerine bakın.  
  
### <a name="setting-input-arguments-of-a-workflow"></a>Bir Iş akışının giriş bağımsız değişkenlerini ayarlama  
 Veriler, iş akışının giriş bağımsız değişkenlerine eşlenen bağımsız değişken adına göre anahtarlı giriş parametrelerinin bir sözlüğünü kullanarak bir iş akışına geçirilebilir. Bu örnekte, bir <xref:System.Activities.Statements.WriteLine> çağırılır ve <xref:System.Activities.Statements.WriteLine.Text%2A> bağımsız değişkeninin değeri giriş parametrelerinin sözlüğü kullanılarak belirtilir.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#3](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#3)]  
  
### <a name="retrieving-output-arguments-of-a-workflow"></a>Bir Iş akışının çıkış bağımsız değişkenlerini alma  
 Bir iş akışının çıkış parametreleri, çağrısından döndürülen çıktılar sözlüğü kullanılarak elde edilebilir <xref:System.Activities.WorkflowInvoker.Invoke%2A> . Aşağıdaki örnek, `Divide` iki giriş bağımsız değişkenine ve iki çıkış bağımsız değişkenine sahip tek bir etkinlikten oluşan bir iş akışını çağırır. İş akışı çağrıldığında, `arguments` her giriş bağımsız değişkeninin değerlerini içeren sözlük geçirilir ve bağımsız değişken adına göre anahtarlanır. Çağrısı döndürüldüğünde `Invoke` , her çıkış bağımsız değişkeni `outputs` Sözlükte döndürülür ve bağımsız değişken adına göre anahtarlanır.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#120](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#120)]  
  
 [!code-csharp[CFX_WorkflowInvokerExample#20](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#20)]  
  
 İş akışı, veya gibi öğesinden türetilse <xref:System.Activities.ActivityWithResult> `CodeActivity<TResult>` `Activity<TResult>` ve iyi tanımlanmış çıkış bağımsız değişkenine ek olarak çıkış bağımsız değişkenleri varsa <xref:System.Activities.Activity%601.Result%2A> , ek bağımsız değişkenleri almak için öğesinin genel olmayan bir aşırı yüklemesi `Invoke` kullanılması gerekir. Bunu yapmak için geçirilen iş akışı tanımının `Invoke` türünde olması gerekir <xref:System.Activities.Activity> . Bu örnekte `Divide` , etkinlik öğesinden türetilir `CodeActivity<int>` , ancak ' <xref:System.Activities.Activity> ın genel olmayan bir aşırı yüklemesinin `Invoke` , tek bir dönüş değeri yerine bağımsız değişkenlerin bir sözlüğünü döndüren kullanıldığı şekilde bildirilmiştir.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#121](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#121)]  
  
 [!code-csharp[CFX_WorkflowInvokerExample#21](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#21)]  
  
## <a name="using-workflowapplication"></a>WorkflowApplication kullanma  
 <xref:System.Activities.WorkflowApplication>iş akışı örneği yönetimi için zengin bir özellikler kümesi sağlar. <xref:System.Activities.WorkflowApplication>, çalışma zamanını kapsülleyen gerçek iş parçacığı güvenli proxy 'si olarak davranır <xref:System.Activities.Hosting.WorkflowInstance> ve iş akışı örnekleri oluşturma ve yükleme, duraklatma ve sürdürme, sonlandırma ve yaşam döngüsü olaylarının bildirilmesi için yöntemler sağlar. Kullanarak bir iş akışını çalıştırmak için, <xref:System.Activities.WorkflowApplication> <xref:System.Activities.WorkflowApplication> istediğiniz yaşam döngüsü olaylarına abone olun, iş akışını başlatın ve sonra bitmesini bekleyin. Bu örnekte, bir etkinlikten oluşan bir iş akışı tanımı <xref:System.Activities.Statements.WriteLine> oluşturulur ve <xref:System.Activities.WorkflowApplication> belirtilen iş akışı tanımı kullanılarak oluşturulur. <xref:System.Activities.WorkflowApplication.Completed%2A>, iş akışı tamamlandığında konağa bildirilecek şekilde işlenir, iş akışı öğesine çağrısıyla başlatılır <xref:System.Activities.WorkflowApplication.Run%2A> ve sonra konağın iş akışının tamamlanmasını bekler. İş akışı tamamlandığında, <xref:System.Threading.AutoResetEvent> ayarlanır ve konak uygulama, aşağıdaki örnekte gösterildiği gibi yürütmeyi sürdürür.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#31](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#31)]  
  
### <a name="workflowapplication-lifecycle-events"></a>WorkflowApplication yaşam döngüsü olayları  
 Uygulamasına ek olarak <xref:System.Activities.WorkflowApplication.Completed%2A> , bir iş akışı kaldırıldığında ( <xref:System.Activities.WorkflowApplication.Unloaded%2A> ), iptal edilen ( <xref:System.Activities.WorkflowApplication.Aborted%2A> ), boşta ( <xref:System.Activities.WorkflowApplication.Idle%2A> ve) <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> veya işlenmeyen bir özel durum oluştuğunda <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> (), ana bilgisayar yazarlarına bildirim uygulanabilir. İş akışı uygulaması geliştiricileri, aşağıdaki örnekte gösterildiği gibi bu bildirimleri işleyebilir ve uygun eylemi gerçekleştirebilir.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#32](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#32)]  
  
### <a name="setting-input-arguments-of-a-workflow"></a>Bir Iş akışının giriş bağımsız değişkenlerini ayarlama  
 Veriler, kullanılırken verilerin geçirildiği yönteme benzer şekilde, bir parametre sözlüğü kullanılarak başlatıldığı için bir iş akışına geçirilebilir <xref:System.Activities.WorkflowInvoker> . Sözlükteki her öğe, belirtilen iş akışının giriş bağımsız değişkeniyle eşlenir. Bu örnekte, bir etkinlikten oluşan bir iş akışı <xref:System.Activities.Statements.WriteLine> çağrılır ve <xref:System.Activities.Statements.WriteLine.Text%2A> bağımsız değişkeni giriş parametrelerinin sözlüğü kullanılarak belirtilir.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#30](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#30)]  
  
### <a name="retrieving-output-arguments-of-a-workflow"></a>Bir Iş akışının çıkış bağımsız değişkenlerini alma  
 Bir iş akışı tamamlandığında, sözlüğe erişerek herhangi bir çıkış bağımsız değişkeni <xref:System.Activities.WorkflowApplication.Completed%2A> işleyicide alınabilir <xref:System.Activities.WorkflowApplicationCompletedEventArgs.Outputs%2A?displayProperty=nameWithType> . Aşağıdaki örnek kullanarak bir iş akışı barındırır <xref:System.Activities.WorkflowApplication> . <xref:System.Activities.WorkflowApplication>Örnek, tek bir etkinlikten oluşan iş akışı tanımı kullanılarak oluşturulur `DiceRoll` . `DiceRoll`Etkinliğin, zar alma işleminin sonuçlarını temsil eden iki çıkış bağımsız değişkeni vardır. İş akışı tamamlandığında, çıktılar <xref:System.Activities.WorkflowApplication.Completed%2A> işleyicide alınır.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#130](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#130)]  
  
 [!code-csharp[CFX_WorkflowApplicationExample#21](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#21)]  
  
> [!NOTE]
> <xref:System.Activities.WorkflowApplication>ve <xref:System.Activities.WorkflowInvoker> giriş bağımsız değişkenlerinin sözlüğünü alın ve `out` bağımsız değişkenlerin sözlüğünü döndürün. Bu sözlük parametreleri, özellikleri ve dönüş değerleri türündedir `IDictionary<string, object>` . Öğesine geçirilen sözlük sınıfının gerçek örneği, uygulayan herhangi bir sınıf olabilir `IDictionary<string, object>` . Bu örneklerde, `Dictionary<string, object>` kullanılır. Sözlükler hakkında daha fazla bilgi için bkz <xref:System.Collections.Generic.IDictionary%602> <xref:System.Collections.Generic.Dictionary%602> . ve.  
  
### <a name="passing-data-into-a-running-workflow-using-bookmarks"></a>Yer Imlerini kullanarak çalışan bir Iş akışına veri geçirme  
 Yer işaretleri, bir etkinliğin çok büyük bir süre içinde çalışmaya devam edeceği ve çalışan bir iş akışı örneğine veri geçirme mekanizması olan mekanizmadır. Bir etkinlik veri bekliyorsa, aşağıdaki örnekte gösterildiği gibi bir etkinlik oluşturup, <xref:System.Activities.Bookmark> devam edildiğinde çağrılacak bir geri çağırma yöntemi kaydedebilir <xref:System.Activities.Bookmark> .  
  
 [!code-csharp[CFX_WorkflowApplicationExample#15](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#15)]  
  
 Yürütüldüğünde, `ReadLine` etkinlik bir oluşturur, bir <xref:System.Activities.Bookmark> geri çağırma kaydeder ve <xref:System.Activities.Bookmark> devam etmek için bekler. Devam edildiğinde `ReadLine` etkinlik, ile geçilen verileri <xref:System.Activities.Bookmark> <xref:System.Activities.Activity%601.Result%2A> bağımsız değişkenine atar. Bu örnekte, `ReadLine` etkinliğin Kullanıcı adını toplayıp konsol penceresinde görüntülemesi için etkinliğini kullanan bir iş akışı oluşturulur.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#22](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#22)]  
  
 `ReadLine`Etkinlik yürütüldüğünde, <xref:System.Activities.Bookmark> adlandırılmış bir adı oluşturur `UserName` ve sonra yer işaretinin sürdürülmesini bekler. Konak, istenen verileri toplar ve ardından devam ettirir <xref:System.Activities.Bookmark> . İş akışı devam eder, adı görüntüler ve sonra tamamlar.  
  
 Konak uygulama, etkin bir yer işareti olup olmadığını anlamak için iş akışını inceleyebilir. Bunu, <xref:System.Activities.WorkflowApplication.GetBookmarks%2A> bir örneğin yöntemini çağırarak <xref:System.Activities.WorkflowApplication> veya <xref:System.Activities.WorkflowApplicationIdleEventArgs> <xref:System.Activities.WorkflowApplication.Idle%2A> işleyicide inceleyerek yapabilir.  
  
 Aşağıdaki kod örneği, yer işareti sürdürülmeye başlamadan önce etkin yer işaretlerinin numaralandırılmasının dışında, önceki örneğe benzer. İş akışı başlatılır ve oluşturulduktan sonra <xref:System.Activities.Bookmark> iş akışı boşta kaldığında <xref:System.Activities.WorkflowApplication.GetBookmarks%2A> çağrılır. İş akışı tamamlandığında, konsola aşağıdaki çıktı görüntülenir.  
  
 **Adınız ne?**  
**BookmarkName: username-OwnerDisplayName: ReadLine** 
 **Emre** 
 **Merhaba, emre**

[!code-csharp[CFX_WorkflowApplicationExample#14](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#14)]  
  
 Aşağıdaki kod örneği, <xref:System.Activities.WorkflowApplicationIdleEventArgs> <xref:System.Activities.WorkflowApplication.Idle%2A> bir örneğin işleyicisine geçirilen ' i inceler <xref:System.Activities.WorkflowApplication> . Bu örnekte, boşta duran iş akışı <xref:System.Activities.Bookmark> `EnterGuess` , adlı bir etkinliğe ait olan bir ada sahip bir ada sahip `ReadInt` . Bu kod örneği, nasıl yapılacağını temel alıyor: Başlangıç [öğreticisinin](getting-started-tutorial.md)bir parçası olan [iş akışını çalıştırma](how-to-run-a-workflow.md). <xref:System.Activities.WorkflowApplication.Idle%2A>Bu adımdaki işleyici bu örnekteki kodu içerecek şekilde değiştirilirse aşağıdaki çıktı görüntülenir.  
  
 **BookmarkName: Entertahminin-OwnerDisplayName: readInt**

 [!code-csharp[CFX_WorkflowApplicationExample#2](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#2)]  
  
## <a name="summary"></a>Özet  
 <xref:System.Activities.WorkflowInvoker>iş akışlarını çağırmak için basit bir yol sağlar ve bir iş akışının başlangıcında veri geçirme ve tamamlanan bir iş akışından veri ayıklama için yöntemler sağlasa da, kullanılabilecek olan daha karmaşık senaryolar sağlamaz <xref:System.Activities.WorkflowApplication> .
