---
title: WorkflowInvoker ve WorkflowApplication kullanma
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cd0e583c-a3f9-4fa2-b247-c7b3368c48a7
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 90999867ee1dd678e279832d73d7ecaaa416fe7b
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="using-workflowinvoker-and-workflowapplication"></a>WorkflowInvoker ve WorkflowApplication kullanma
Windows Workflow Foundation (WF) iş akışı barındırma çeşitli yöntemler sağlar. <xref:System.Activities.WorkflowInvoker> yöntem çağrısı sırasında ve Kalıcılık kullanmayan yalnızca iş akışları için kullanılabilir gibi bir iş akışı çağırma için basit bir yol sağlar. <xref:System.Activities.WorkflowApplication> yaşam döngüsü olayları, yürütme denetimi, yer işareti sürdürme ve kalıcılığı bildirimi içeren iş akışlarını yürütmek için daha zengin bir modeli sağlar. <xref:System.ServiceModel.Activities.WorkflowServiceHost> Mesajlaşma etkinlikleri için destek sağlar ve iş akışı Hizmetleri ile birincil olarak kullanılır. Bu konu ile iş akışı barındırma için tanıtır <xref:System.Activities.WorkflowInvoker> ve <xref:System.Activities.WorkflowApplication>. [!INCLUDE[crabout](../../../includes/crabout-md.md)] iş akışlarıyla barındırma <xref:System.ServiceModel.Activities.WorkflowServiceHost>, bkz: [iş akışı Hizmetleri](../../../docs/framework/wcf/feature-details/workflow-services.md) ve [iş akışı hizmetleri genel bakış barındırma](../../../docs/framework/wcf/feature-details/hosting-workflow-services-overview.md).  
  
## <a name="using-workflowinvoker"></a>WorkflowInvoker kullanma  
 <xref:System.Activities.WorkflowInvoker> yöntem çağrısı değilmiş gibi bir iş akışını yürütmek için bir model sağlar. Kullanarak bir iş akışının çağırmak için <xref:System.Activities.WorkflowInvoker>, çağrı <xref:System.Activities.WorkflowInvoker.Invoke%2A> yöntemi ve iş akışının çağırmak için iş akışı tanımını geçirin. Bu örnekte, bir <xref:System.Activities.Statements.WriteLine> etkinliğini kullanarak çağrıldığında <xref:System.Activities.WorkflowInvoker>.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#1)]  
  
 Bir iş akışı kullanarak çağrıldığında <xref:System.Activities.WorkflowInvoker>, iş akışını çağıran iş parçacığında yürütür ve <xref:System.Activities.WorkflowInvoker.Invoke%2A> yöntemi, iş akışı herhangi boşta kalma süresi dahil olmak üzere, tamamlanana kadar engeller. İş akışı tamamlanmalıdır bir zaman aşımı aralığı yapılandırmak için aşağıdakilerden birini kullanın <xref:System.Activities.WorkflowInvoker.Invoke%2A> alan aşırı bir <xref:System.TimeSpan> parametresi. Bu örnekte, iki farklı zaman aşımı aralığı ile bir iş akışı çağrılır. İlk iş akışı complets ancak ikinci desteklemez.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#50](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#50)]  
  
> [!NOTE]
>  <xref:System.TimeoutException> Yalnızca zaman aşımı aralığı geçtikten ve iş akışı yürütme sırasında boşta duruma dönerse oluşturulur. İş akışı boşta değil tamamlamak için belirtilen zaman aşımı aralığından daha uzun sürer bir iş akışı başarıyla tamamlar.  
  
 <xref:System.Activities.WorkflowInvoker> Invoke yöntemi zaman uyumsuz sürümlerini de sağlar. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] <xref:System.Activities.WorkflowInvoker.InvokeAsync%2A> ve <xref:System.Activities.WorkflowInvoker.BeginInvoke%2A>.  
  
### <a name="setting-input-arguments-of-a-workflow"></a>Bir iş akışının ayarı giriş bağımsız değişkenleri  
 Veri akışının giriş bağımsız değişkeni için eşleme bağımsız değişken adıyla anahtarlı giriş parametreleri sözlüğü kullanarak bir iş akışı içine geçirilebilir. Bu örnekte, bir <xref:System.Activities.Statements.WriteLine> çağrılır ve değeri kendi <xref:System.Activities.Statements.WriteLine.Text%2A> bağımsız değişkeni, giriş parametreleri sözlüğünü kullanarak belirtilir.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#3](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#3)]  
  
### <a name="retrieving-output-arguments-of-a-workflow"></a>Bir iş akışının çıkış değişkenlerini alınıyor  
 Bir iş akışının çıkış parametreleri için çağrısından döndürülen çıkışları sözlüğünü kullanarak elde edilebilir <xref:System.Activities.WorkflowInvoker.Invoke%2A>. Aşağıdaki örnek bir tek oluşan bir iş akışını çağırır `Divide` iki bağımsız değişken giriş ve iki bağımsız değişken çıkış, etkinlik. İş akışı çağrıldığında, `arguments` sözlük her bağımsız değişkeni, değişken adına göre anahtarlı giriş değerlerini içeren geçirilir. Zaman çağrısı `Invoke` döndürür, her bir çıkış bağımsız değişkeni döndürülür `outputs` de bağımsız değişken adıyla anahtarlı sözlük.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#120](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#120)]  
  
 [!code-csharp[CFX_WorkflowInvokerExample#20](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#20)]  
  
 İş akışı türetilen varsa <xref:System.Activities.ActivityWithResult>, gibi `CodeActivity<TResult>` veya `Activity<TResult>`, ve iyi tanımlanmış ek olarak bir çıkış bağımsız değişken <xref:System.Activities.Activity%601.Result%2A> çıkış bağımsız değişkeni, genel olmayan aşırı yüklemesini `Invoke` almak için kullanılması gerekir Ek bağımsız değişkenler. Bunu yapmak için içine iş akışı tanımı geçirilen `Invoke` türünde olmalıdır <xref:System.Activities.Activity>. Bu örnekte `Divide` etkinlik türetilir `CodeActivity<int>`, olarak bildirilen ancak <xref:System.Activities.Activity> genel olmayan aşırı yükleme böylece `Invoke` olan bağımsız değişkenler tek bir dönüş değeri yerine bir sözlüğü döndürür kullanılır.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#121](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#121)]  
  
 [!code-csharp[CFX_WorkflowInvokerExample#21](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#21)]  
  
## <a name="using-workflowapplication"></a>WorkflowApplication kullanma  
 <xref:System.Activities.WorkflowApplication> İş akışı örneği yönetimi için zengin bir özellikler kümesi sağlar. <xref:System.Activities.WorkflowApplication> Gerçek iş parçacığı güvenli proxy görevi gören <xref:System.Activities.Hosting.WorkflowInstance>, hangi çalışma zamanı yalıtır ve oluşturma ve iş akışı örneği yükleniyor, duraklatma ve sürdürme, sonlandırma ve yaşam döngüsü olayları bildirilmesi için yöntemler sağlar. Bir iş akışını kullanarak çalıştırmak için <xref:System.Activities.WorkflowApplication> oluşturduğunuz <xref:System.Activities.WorkflowApplication>, istenen yaşam döngüsü olaylara abone olma, iş akışını başlatmak ve ardından bitmesini bekleyin. Bu örnekte, bir iş akışı tanımı, oluşur bir <xref:System.Activities.Statements.WriteLine> etkinlik oluşturulur ve bir <xref:System.Activities.WorkflowApplication> belirtilen iş akışı tanımı kullanılarak oluşturulur. <xref:System.Activities.WorkflowApplication.Completed%2A> olan iş akışı tamamlandığında konak bildirilir şekilde ele, çağrı iş akışı başlatıldığında <xref:System.Activities.WorkflowApplication.Run%2A>, ve konak tamamlamak iş akışı için bekler. İş akışı tamamlandığında <xref:System.Threading.AutoResetEvent> ayarlanır ve ana bilgisayar aşağıdaki örnekte gösterildiği gibi uygulama yürütme devam.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#31](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#31)]  
  
### <a name="workflowapplication-lifecycle-events"></a>WorkflowApplication yaşam döngüsü olayları  
 Ek olarak <xref:System.Activities.WorkflowApplication.Completed%2A>, konak yazarları bildirim bir iş akışı kaldırıldığında (<xref:System.Activities.WorkflowApplication.Unloaded%2A>), iptal edildi (<xref:System.Activities.WorkflowApplication.Aborted%2A>), boş olur (<xref:System.Activities.WorkflowApplication.Idle%2A> ve <xref:System.Activities.WorkflowApplication.PersistableIdle%2A>), veya işlenmeyen bir özel durum oluşur (<xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>). İş akışı uygulama geliştiricileri, bu bildirimler işlemek ve aşağıdaki örnekte gösterildiği gibi uygun eylemi gerçekleştirin.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#32](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#32)]  
  
### <a name="setting-input-arguments-of-a-workflow"></a>Bir iş akışının ayarı giriş bağımsız değişkenleri  
 Veri parametreleri sözlüğü kullanarak başlatıldığından gibi bir iş akışı ile geçirilebilir, benzer şekilde veriler kullanırken geçirilen <xref:System.Activities.WorkflowInvoker>. Her öğe sözlükte belirtilen iş akışının giriş bağımsız değişkeni için eşler. Bu örnekte, bir iş akışı, oluşur bir <xref:System.Activities.Statements.WriteLine> etkinlik çağrılır ve kendi <xref:System.Activities.Statements.WriteLine.Text%2A> bağımsız değişkeni, giriş parametreleri sözlüğünü kullanarak belirtilir.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#30](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#30)]  
  
### <a name="retrieving-output-arguments-of-a-workflow"></a>Bir iş akışının çıkış değişkenlerini alınıyor  
 İçinde bir iş akışı tamamlandığında, herhangi bir çıktı bağımsız değişkeni alınabilir <xref:System.Activities.WorkflowApplication.Completed%2A> erişerek işleyici <xref:System.Activities.WorkflowApplicationCompletedEventArgs.Outputs%2A?displayProperty=nameWithType> sözlük. Aşağıdaki örnek iş akışı kullanarak barındıran <xref:System.Activities.WorkflowApplication>. A <xref:System.Activities.WorkflowApplication> örneği, bir tek oluşan bir iş akışı tanımı kullanılarak yapılandırılmıştır `DiceRoll` etkinlik. `DiceRoll` Etkinlik bölmek toplama işleminin sonuçlarını temsil eden iki çıkış bağımsız değişkeni vardır. İş akışı tamamlandığında, çıkış olarak alınır <xref:System.Activities.WorkflowApplication.Completed%2A> işleyicisi.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#130](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#130)]  
  
 [!code-csharp[CFX_WorkflowApplicationExample#21](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#21)]  
  
> [!NOTE]
>  <xref:System.Activities.WorkflowApplication> ve <xref:System.Activities.WorkflowInvoker> giriş bağımsız değişkeni sözlüğü almak ve bir sözlüğü döndürür `out` bağımsız değişkenler. Bu sözlük parametreler, özellikleri ve dönüş değerleri türünde olduğundan `IDictionary<string, object>`. Geçirilen dictionary sınıfı gerçek örneğini uygulayan herhangi bir sınıf olabilir `IDictionary<string, object>`. Bu örneklerde `Dictionary<string, object>` kullanılır. [!INCLUDE[crabout](../../../includes/crabout-md.md)] sözlük, bkz: <xref:System.Collections.Generic.IDictionary%602> ve <xref:System.Collections.Generic.Dictionary%602>.  
  
### <a name="passing-data-into-a-running-workflow-using-bookmarks"></a>Yer işaretlerini kullanma çalışan akışına veri geçirme  
 Yer işaretleri, bir etkinlik pasif olarak sürdürülmesini beklemek ve çalışan bir iş akışı örneğine veri geçirme için bir mekanizma olan bir sistemdir. Bir etkinlik için verileri bekliyorsa oluşturabilirsiniz bir <xref:System.Activities.Bookmark> ve ne zaman çağrılacak bir geri çağırma yöntemi kaydedilmeye <xref:System.Activities.Bookmark> , aşağıdaki örnekte gösterildiği gibi sürdürülür.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#15](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#15)]  
  
 Çalıştırıldığında, `ReadLine` aktivite oluşturan bir <xref:System.Activities.Bookmark>, bir geri çağırma kaydeder ve sonra bekler <xref:System.Activities.Bookmark> olarak devam eder. Ettirildiğinde, `ReadLine` etkinlik atar ile geçirilen verileri <xref:System.Activities.Bookmark> için kendi <xref:System.Activities.Activity%601.Result%2A> bağımsız değişkeni. Bu örnekte, bir iş akışı kullanan oluşturulur `ReadLine` kullanıcı adını toplamak ve konsol penceresine görüntülemek için etkinliği.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#22](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#22)]  
  
 Zaman `ReadLine` etkinlik yürütülürse, oluşturduğu bir <xref:System.Activities.Bookmark> adlı `UserName` ve yer işareti devam ettirilebilir bekler. Ana bilgisayar istenen verileri toplar ve ardından sürdürür <xref:System.Activities.Bookmark>. İş akışını sürdürür, adını görüntüler ve sonra tamamlar.  
  
 Ana bilgisayar uygulamasını herhangi etkin yer işaretleri olup olmadığını belirlemek için iş akışı inceleyebilirsiniz. Bunu çağırarak yapabilirsiniz <xref:System.Activities.WorkflowApplication.GetBookmarks%2A> yöntemi bir <xref:System.Activities.WorkflowApplication> örneği veya göre İnceleme <xref:System.Activities.WorkflowApplicationIdleEventArgs> içinde <xref:System.Activities.WorkflowApplication.Idle%2A> işleyicisi.  
  
 Yer işareti sürdürüldü önce etkin yer işaretleri numaralandırılır aşağıdaki kod örneğinde önceki örnek gibi olmasıdır. İş akışı başlatıldığında, bir kez <xref:System.Activities.Bookmark> oluşturulur ve iş akışı boşta girer <xref:System.Activities.WorkflowApplication.GetBookmarks%2A> olarak adlandırılır. İş akışı tamamlandığında aşağıdaki çıktıyı konsola görüntülenir.  
  
 **Adınız ne?**  
**YerİşaretiAdı: Kullanıcı adı - OwnerDisplayName: ReadLine**   
**Steve**   
**Merhaba, Steve**

[!code-csharp[CFX_WorkflowApplicationExample#14](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#14)]  
  
 Aşağıdaki kod örneğinde inceler <xref:System.Activities.WorkflowApplicationIdleEventArgs> içine geçirilen <xref:System.Activities.WorkflowApplication.Idle%2A> işleyicisine bir <xref:System.Activities.WorkflowApplication> örneği. Bu örnekte boşta giderek iş akışı olan bir <xref:System.Activities.Bookmark> adıyla `EnterGuess`, adlandırılmış bir etkinlik tarafından sahip olunan `ReadInt`. Bu kod örneği kapatarak dayalı [nasıl yapılır: bir iş akışını çalıştırma](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md), parçası olduğu [başlangıç Öğreticisi](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md). Varsa <xref:System.Activities.WorkflowApplication.Idle%2A> işleyici bu adımda değiştiren Bu örnekte koddan içerecek şekilde, aşağıdaki çıktısı görüntülenir.  
  
 **YerİşaretiAdı: EnterGuess - OwnerDisplayName: readInt**
 
 [!code-csharp[CFX_WorkflowApplicationExample#2](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#2)]  
  
## <a name="summary"></a>Özet  
 <xref:System.Activities.WorkflowInvoker> İş akışları, çağırmak için basit bir yol sağlar ve bir iş akışının başlangıcında veri geçirme ve tamamlanmış bir iş akışından veri ayıklama için yöntemler sağlar ancak bu daha karmaşık senaryolar için nereye olduğu sağlamaz <xref:System.Activities.WorkflowApplication> kullanılabilir.
