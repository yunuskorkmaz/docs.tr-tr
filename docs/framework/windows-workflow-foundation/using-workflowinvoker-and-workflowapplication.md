---
title: WorkflowInvoker ve WorkflowApplication Kullanma
ms.date: 03/30/2017
ms.assetid: cd0e583c-a3f9-4fa2-b247-c7b3368c48a7
ms.openlocfilehash: 5d09fc3c902b1993b32edf3e9f92393433281636
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182697"
---
# <a name="using-workflowinvoker-and-workflowapplication"></a>WorkflowInvoker ve WorkflowApplication Kullanma
Windows İş Akışı Temeli (WF), iş akışlarını barındırmak için çeşitli yöntemler sağlar. <xref:System.Activities.WorkflowInvoker>bir yöntem çağrısı gibi bir iş akışı çağırmak için basit bir yol sağlar ve yalnızca kalıcılık kullanmayan iş akışları için kullanılabilir. <xref:System.Activities.WorkflowApplication>yaşam döngüsü olaylarının bildirimini, yürütme denetimini, yer imi yeniden başlatılmasını ve kalıcılığı içeren iş akışlarını yürütmek için daha zengin bir model sağlar. <xref:System.ServiceModel.Activities.WorkflowServiceHost>ileti etkinlikleri için destek sağlar ve öncelikle iş akışı hizmetleri ile kullanılır. Bu konu ile <xref:System.Activities.WorkflowInvoker> iş akışı barındırma <xref:System.Activities.WorkflowApplication>ve tanıttı. İş akışlarını barındırma hakkında <xref:System.ServiceModel.Activities.WorkflowServiceHost>daha fazla bilgi için bkz: [İş Akışı Hizmetleri](../wcf/feature-details/workflow-services.md) ve Barındırma İş Akışı Hizmetlerine Genel [Bakış.](../wcf/feature-details/hosting-workflow-services-overview.md)  
  
## <a name="using-workflowinvoker"></a>İş Akışını KullanmaInvoker  
 <xref:System.Activities.WorkflowInvoker>bir yöntem çağrısı gibi bir iş akışı yürütmek için bir model sağlar. Kullanarak <xref:System.Activities.WorkflowInvoker>bir iş akışı çağırmak <xref:System.Activities.WorkflowInvoker.Invoke%2A> için, yöntemi arayın ve çağırmak için iş akışının iş akışı tanımında geçirin. Bu örnekte, <xref:System.Activities.Statements.WriteLine> bir etkinlik <xref:System.Activities.WorkflowInvoker>kullanılarak çağrılır.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#1](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#1)]  
  
 Bir iş akışı kullanılarak <xref:System.Activities.WorkflowInvoker>çağrıldığınızda, iş akışı arama iş <xref:System.Activities.WorkflowInvoker.Invoke%2A> parçacığı üzerinde yürütür ve iş akışı tamamlanana kadar yöntem bloklar, herhangi bir boşta zaman da dahil olmak üzere. İş akışının tamamlanması gereken bir zaman aralığını yapılandırmak <xref:System.Activities.WorkflowInvoker.Invoke%2A> <xref:System.TimeSpan> için, parametre alan aşırı yüklerden birini kullanın. Bu örnekte, iki farklı zaman aralığıyla bir iş akışı iki kez çağrılır. İlk iş akışı tamamlar, ancak ikinci değil.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#50](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#50)]  
  
> [!NOTE]
> Yalnızca <xref:System.TimeoutException> zaman aşımı aralığı atılırsa ve iş akışı yürütme sırasında boşta kalırsa atılır. İş akışı boşta kalmazsa, tamamlanması belirtilen zaman aşımı aralığından daha uzun süren bir iş akışı başarıyla tamamlar.  
  
 <xref:System.Activities.WorkflowInvoker>çağırma yönteminin eşzamanlı sürümlerini de sağlar. Daha fazla bilgi için <xref:System.Activities.WorkflowInvoker.InvokeAsync%2A> ve <xref:System.Activities.WorkflowInvoker.BeginInvoke%2A> bölümlerine bakın.  
  
### <a name="setting-input-arguments-of-a-workflow"></a>İş Akışının Giriş Bağımsız Değişkenlerini Ayarlama  
 Veriler, iş akışının giriş bağımsız değişkenlerine yapılan bu haritanın bağımsız değişken adına anahtarlanmış giriş parametreleri sözlüğü kullanılarak iş akışına aktarılabilir. Bu örnekte, <xref:System.Activities.Statements.WriteLine> bir çağrılır ve <xref:System.Activities.Statements.WriteLine.Text%2A> bağımsız değişkeninin değeri giriş parametreleri sözlüğü kullanılarak belirtilir.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#3](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#3)]  
  
### <a name="retrieving-output-arguments-of-a-workflow"></a>İş Akışının Çıktı Bağımsız Değişkenlerini Alma  
 İş akışının çıkış parametreleri, çağrıdan ''a <xref:System.Activities.WorkflowInvoker.Invoke%2A>döndürülen çıktılar sözlüğü kullanılarak elde edilebilir. Aşağıdaki örnek, iki giriş bağımsız değişkeni `Divide` ve iki çıktı bağımsız değişkeni olan tek bir etkinlikten oluşan bir iş akışı çağırır. İş akışı çağrıldığızaman, `arguments` bağımsız değişken adı ile anahtarlanmış her giriş bağımsız değişkeni için değerleri içeren sözlük geçirilir. Çağrı `Invoke` döndürdüğünde, her çıktı bağımsız `outputs` değişkeni sözlükte döndürülür ve bağımsız değişken adı ile de anahtarlanır.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#120](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#120)]  
  
 [!code-csharp[CFX_WorkflowInvokerExample#20](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#20)]  
  
 İş <xref:System.Activities.ActivityWithResult>akışı , örneğin, `CodeActivity<TResult>` veya `Activity<TResult>`, gibi türetilmiştir ve iyi tanımlanmış <xref:System.Activities.Activity%601.Result%2A> çıktı bağımsız değişkenine ek `Invoke` olarak çıktı bağımsız değişkenleri varsa, ek bağımsız değişkenleri almak için genel olmayan bir aşırı yük kullanılmalıdır. Bunu yapmak için, içine `Invoke` geçirilen iş akışı <xref:System.Activities.Activity>tanımı türünde olmalıdır. Bu örnekte `Divide` `CodeActivity<int>`etkinlik, tek bir iade <xref:System.Activities.Activity> değeri yerine bağımsız değişkenler `Invoke` sözlüğü döndüren genel olmayan bir aşırı yük ten türetilmiştir, ancak genel olmayan bir aşırı yük olarak bildirilir.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#121](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#121)]  
  
 [!code-csharp[CFX_WorkflowInvokerExample#21](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#21)]  
  
## <a name="using-workflowapplication"></a>İş Akışı Uygulamasını Kullanma  
 <xref:System.Activities.WorkflowApplication>iş akışı örneği yönetimi için zengin bir özellik kümesi sağlar. <xref:System.Activities.WorkflowApplication>çalışma zamanını kapsülleyen ve <xref:System.Activities.Hosting.WorkflowInstance>iş akışı örnekleri oluşturma ve yükleme, duraklatma ve sürdürme, sonlandırma ve yaşam döngüsü olaylarının bildirimi için yöntemler sağlayan gerçek , iş parçacığı güvenli proxy olarak hareket eder. Bir iş akışını <xref:System.Activities.WorkflowApplication> çalıştırmak için, istediğiniz yaşam döngüsü olaylarına abone <xref:System.Activities.WorkflowApplication>olun, iş akışını başlatın ve sonra tamamlanmasını bekleyin. Bu örnekte, bir etkinlikten oluşan <xref:System.Activities.Statements.WriteLine> bir iş <xref:System.Activities.WorkflowApplication> akışı tanımı oluşturulur ve belirtilen iş akışı tanımı kullanılarak bir oluşturulur. <xref:System.Activities.WorkflowApplication.Completed%2A>iş akışı tamamlandığında ana bilgisayar bildirilir, iş akışı <xref:System.Activities.WorkflowApplication.Run%2A>bir çağrı ile başlatılır ve sonra ana bilgisayar iş akışının tamamlanmasını bekler. İş akışı tamamlandığında, <xref:System.Threading.AutoResetEvent> ayarlanır ve ana bilgisayar uygulaması aşağıdaki örnekte gösterildiği gibi yürütmeye devam edebilir.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#31](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#31)]  
  
### <a name="workflowapplication-lifecycle-events"></a>İş AkışıUygulama Yaşam Döngüsü Etkinlikleri  
 Buna ek <xref:System.Activities.WorkflowApplication.Completed%2A>olarak, bir iş akışı boşaltıldığında ana<xref:System.Activities.WorkflowApplication.Unloaded%2A>bilgisayar yazarları bildirilebilir ( ), iptal (<xref:System.Activities.WorkflowApplication.Aborted%2A>), boşta olur (<xref:System.Activities.WorkflowApplication.Idle%2A> ve <xref:System.Activities.WorkflowApplication.PersistableIdle%2A>), veya işlenmemiş bir özel durum oluşur (<xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>). İş akışı uygulama geliştiricileri, aşağıdaki örnekte gösterildiği gibi bu bildirimleri işleyebilir ve uygun eylemi gerçekleştirebilir.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#32](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#32)]  
  
### <a name="setting-input-arguments-of-a-workflow"></a>İş Akışının Giriş Bağımsız Değişkenlerini Ayarlama  
 Veriler, parametre sözlüğü kullanılarak başlatıldıkça, veri kullanılırken <xref:System.Activities.WorkflowInvoker>geçirilen veriye benzer şekilde iş akışına aktarılabilir. Sözlükteki her öğe, belirtilen iş akışının giriş bağımsız değişkenini eşler. Bu örnekte, bir etkinlikten <xref:System.Activities.Statements.WriteLine> oluşan bir iş <xref:System.Activities.Statements.WriteLine.Text%2A> akışı çağrılır ve bağımsız değişkeni giriş parametreleri sözlüğü kullanılarak belirtilir.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#30](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#30)]  
  
### <a name="retrieving-output-arguments-of-a-workflow"></a>İş Akışının Çıktı Bağımsız Değişkenlerini Alma  
 Bir iş akışı tamamlandığında, sözlük erişerek <xref:System.Activities.WorkflowApplication.Completed%2A> <xref:System.Activities.WorkflowApplicationCompletedEventArgs.Outputs%2A?displayProperty=nameWithType> işleyicisi herhangi bir çıktı bağımsız değişkenleri alınabilir. Aşağıdaki örnekte kullanarak bir <xref:System.Activities.WorkflowApplication>iş akışı barındırıyor. Bir <xref:System.Activities.WorkflowApplication> örnek, tek `DiceRoll` bir etkinlikten oluşan bir iş akışı tanımı kullanılarak oluşturulur. Etkinlik, `DiceRoll` zar rulo işleminin sonuçlarını temsil eden iki çıktı bağımsız değişkeni vardır. İş akışı tamamlandığında, çıktılar <xref:System.Activities.WorkflowApplication.Completed%2A> işleyicide alınır.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#130](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#130)]  
  
 [!code-csharp[CFX_WorkflowApplicationExample#21](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#21)]  
  
> [!NOTE]
> <xref:System.Activities.WorkflowApplication>ve <xref:System.Activities.WorkflowInvoker> giriş bağımsız değişkenleri sözlüğü alın `out` ve bağımsız değişkenler sözlüğü döndürün. Bu sözlük parametreleri, özellikleri ve `IDictionary<string, object>`döndürme değerleri türündedir. Geçirilen sözlük sınıfının gerçek örneği uygulayan herhangi bir sınıf `IDictionary<string, object>`olabilir. Bu örneklerde `Dictionary<string, object>` kullanılır. Sözlükler hakkında daha fazla <xref:System.Collections.Generic.IDictionary%602> bilgi <xref:System.Collections.Generic.Dictionary%602>için bkz.  
  
### <a name="passing-data-into-a-running-workflow-using-bookmarks"></a>Yer Imlerini Kullanarak Verileri Çalışan İş Akışına Aktarma  
 Yer imleri, bir etkinliğin pasif olarak devam etmeyi bekleyebileceği ve verileri çalışan bir iş akışı örneğine aktarmak için bir mekanizma olduğu mekanizmadır. Bir etkinlik veri bekliyorsa, aşağıdaki <xref:System.Activities.Bookmark> örnekte gösterildiği gibi, bir <xref:System.Activities.Bookmark> geri arama yöntemi oluşturabilir ve devam edildiğinde çağrılacak bir geri arama yöntemi ni kaydedebilir.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#15](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#15)]  
  
 Yürütüldüğünde, `ReadLine` etkinlik bir <xref:System.Activities.Bookmark>, geri arama kaydeder ve sonra <xref:System.Activities.Bookmark> devam etmesini bekler. Devam ettiğinde, `ReadLine` etkinlik <xref:System.Activities.Bookmark> <xref:System.Activities.Activity%601.Result%2A> bağımsız değişkeniyle geçirilen verileri atar. Bu örnekte, kullanıcının `ReadLine` adını toplamak ve konsol penceresine görüntülemek için etkinliği kullanan bir iş akışı oluşturulur.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#22](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#22)]  
  
 `ReadLine` Etkinlik yürütüldüğünde, bir <xref:System.Activities.Bookmark> ad `UserName` ve ardından yer işaretinin devam etmesini bekler. Ana bilgisayar istenen verileri toplar ve <xref:System.Activities.Bookmark>sonra . İş akışı devam eder, adı görüntüler ve tamamlar.  
  
 Ana bilgisayar uygulaması, etkin yer imleri olup olmadığını belirlemek için iş akışını inceleyebilir. Bunu, <xref:System.Activities.WorkflowApplication.GetBookmarks%2A> bir <xref:System.Activities.WorkflowApplication> örneğin yöntemini arayarak veya <xref:System.Activities.WorkflowApplicationIdleEventArgs> <xref:System.Activities.WorkflowApplication.Idle%2A> işleyiciyi inceleyerek yapabilir.  
  
 Aşağıdaki kod örneği, yer imi devam etmeden önce etkin yer imlerinin numaralandırılmış olması dışında önceki örnek gibidir. İş akışı başlatılır ve <xref:System.Activities.Bookmark> oluşturulduktan ve iş akışı <xref:System.Activities.WorkflowApplication.GetBookmarks%2A> boşta kaldıktan sonra çağrılır. İş akışı tamamlandığında, aşağıdaki çıktı konsola görüntülenir.  
  
 **Adınız ne?**  
**Yer İşareti Adı: Kullanıcı Adı - OwnerDisplayName: ReadLine**
**Steve**
**Hello, Steve**

[!code-csharp[CFX_WorkflowApplicationExample#14](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#14)]  
  
 Aşağıdaki kod örneği, <xref:System.Activities.WorkflowApplicationIdleEventArgs> bir <xref:System.Activities.WorkflowApplication> örneğin <xref:System.Activities.WorkflowApplication.Idle%2A> işleyicisi içine geçirilen inceler. Bu örnekte boşta kalan <xref:System.Activities.Bookmark> iş akışının `EnterGuess`adı `ReadInt`, adlı bir faaliyete ait olan bir iş akışı vardır. Bu kod örneği, Başlangıç [Öğreticisinin](getting-started-tutorial.md)bir parçası olan [İş Akışını Çalıştırma: Nasıl Çalıştırılır'](how-to-run-a-workflow.md)a dayanır. Bu <xref:System.Activities.WorkflowApplication.Idle%2A> adımdaki işleyici bu örnekteki kodu içerecek şekilde değiştirilirse, aşağıdaki çıktı görüntülenir.  
  
 **Yer ImiAdı: EnterGuess - OwnerDisplayName: ReadInt**

 [!code-csharp[CFX_WorkflowApplicationExample#2](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#2)]  
  
## <a name="summary"></a>Özet  
 <xref:System.Activities.WorkflowInvoker>iş akışlarını çağırmak için hafif bir yol sağlar ve iş akışının başlangıcında veri aktarmak ve tamamlanmış bir iş akışından veri ayıklamak için <xref:System.Activities.WorkflowApplication> yöntemler sağlamasına rağmen, kullanılabilen daha karmaşık senaryolar sağlamaz.
