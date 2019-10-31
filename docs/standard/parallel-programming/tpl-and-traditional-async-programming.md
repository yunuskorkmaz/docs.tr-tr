---
title: TPL ve Geleneksel .NET Framework Zaman Uyumsuz Programlama
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, with other asynchronous models
ms.assetid: e7b31170-a156-433f-9f26-b1fc7cd1776f
ms.openlocfilehash: 27766c10d0624b5eda8256a3211662036a1b16b3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139943"
---
# <a name="tpl-and-traditional-net-framework-asynchronous-programming"></a>TPL ve Geleneksel .NET Framework Zaman Uyumsuz Programlama
.NET Framework g/ç 'ye ve işlem ile bağlantılı zaman uyumsuz işlemleri gerçekleştirmek için aşağıdaki iki standart deseni sağlar:  
  
- Zaman uyumsuz işlemlerin, <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> ve <xref:System.IO.Stream.EndRead%2A?displayProperty=nameWithType>gibi bir dizi BEGIN/End yöntemi ile temsil edildiği zaman uyumsuz programlama modeli (APM).  
  
- Zaman uyumsuz işlemlerin, *OperationName*Async ve *OperationName*tamamlandı adlı bir yöntem/olay çifti tarafından temsil edildiği olay tabanlı zaman uyumsuz model (EAP), örneğin, <xref:System.Net.WebClient.DownloadStringAsync%2A?displayProperty=nameWithType> ve <xref:System.Net.WebClient.DownloadStringCompleted?displayProperty=nameWithType>. (EAP .NET Framework sürüm 2,0 ' de tanıtılmıştı.)  
  
 Görev paralel kitaplığı (TPL), zaman uyumsuz desenlerden biriyle birlikte çeşitli şekillerde kullanılabilir. Hem APM hem de EAP işlemlerini bir görev olarak bir işlem halinde sunabilir veya APM düzenlerini açığa çıkarmak, ancak bunları dahili olarak uygulamak için görev nesnelerini kullanmak için kullanabilirsiniz. Her iki senaryoda, görev nesnelerini kullanarak kodu basitleştirebilir ve aşağıdaki yararlı işlevlerden yararlanabilirsiniz:  
  
- Görev devamlılıkları biçiminde geri çağırmaları, görev başladıktan sonra istediğiniz zaman kaydedin.  
  
- Bir `Begin_` yöntemine yanıt olarak yürütülen birden çok işlemi, <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> ve <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> yöntemlerini ya da <xref:System.Threading.Tasks.Task.WaitAll%2A> yöntemini ya da <xref:System.Threading.Tasks.Task.WaitAny%2A> yöntemini kullanarak koordine edin.  
  
- Aynı görev nesnesinde zaman uyumsuz g/ç 'ye ve işlem ile bağlantılı işlemleri kapsülleyebilirsiniz.  
  
- Görev nesnesinin durumunu izleyin.  
  
- <xref:System.Threading.Tasks.TaskCompletionSource%601>kullanarak bir işlemin durumunu bir görev nesnesine sıralama.  
  
## <a name="wrapping-apm-operations-in-a-task"></a>APM İşlemlerini Bir Görevle Sarma  
 Hem <xref:System.Threading.Tasks.TaskFactory?displayProperty=nameWithType> hem de <xref:System.Threading.Tasks.TaskFactory%601?displayProperty=nameWithType> sınıfları, bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> örneğinde APM başlangıç/bitiş yöntemi çiftini kapsületmenize olanak tanıyan <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> yöntemlerinin çeşitli yüklerini sağlar. Çeşitli aşırı yüklemeler sıfır ile üç giriş parametresine sahip herhangi bir BEGIN/End Yöntem çiftini sağlar.  
  
 Bir değer döndüren `End` yöntemlerine sahip çiftler için (Visual Basic`Function`), <xref:System.Threading.Tasks.Task%601>oluşturan <xref:System.Threading.Tasks.TaskFactory%601> yöntemleri kullanın. Void (`Sub` Visual Basic) döndüren `End` yöntemler için, <xref:System.Threading.Tasks.Task>oluşturan <xref:System.Threading.Tasks.TaskFactory> yöntemleri kullanın.  
  
 `Begin` yönteminin üçten fazla parametresi olduğu veya `ref` veya `out` parametreleri içerdiği bazı durumlarda, yalnızca `End` yöntemini kapsülleyen ek `FromAsync` aşırı yüklemeler sağlanır.  
  
 Aşağıdaki örnek, <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> ve <xref:System.IO.FileStream.EndRead%2A?displayProperty=nameWithType> yöntemleriyle eşleşen `FromAsync` aşırı yüklemesinin imzasını gösterir. Bu aşırı yükleme, aşağıdaki gibi üç giriş parametresi alır.  
  
 [!code-csharp[FromAsync#01](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#01)]
 [!code-vb[FromAsync#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#01)]  
  
 İlk parametre, <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> yönteminin imzasıyla eşleşen bir <xref:System.Func%606> temsilcisidir. İkinci parametre bir <xref:System.IAsyncResult> alan ve bir `TResult`döndüren <xref:System.Func%602> temsilcisidir. <xref:System.IO.FileStream.EndRead%2A> bir tamsayı döndürdüğünden, derleyici `TResult` türünü <xref:System.Int32> olarak ve görevin türünü <xref:System.Threading.Tasks.Task>olarak algılar. Son dört parametre <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> yöntemi ile aynıdır:  
  
- Dosya verilerinin depolanması için gereken arabellek.  
  
- Arabellekte veri yazmaya başlayabileceğiniz fark.  
  
- Dosyadan okunacak maksimum veri miktarı.  
  
- Geri çağırmaya geçirilecek Kullanıcı tanımlı durum verilerini depolayan isteğe bağlı bir nesne.  
  
### <a name="using-continuewith-for-the-callback-functionality"></a>Geri Çağırma İşlevi İçin ContinueWith Kullanma  
 Dosyadaki verilere erişmeniz gerekiyorsa, yalnızca bayt sayısının aksine <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> yöntemi yeterli değildir. Bunun yerine, `Result` özelliği dosya verilerini içeren <xref:System.Threading.Tasks.Task>kullanın. Bunu, özgün göreve bir devamlılık ekleyerek yapabilirsiniz. Devamlılık, genellikle <xref:System.AsyncCallback> temsilcisi tarafından gerçekleştirilecek işi gerçekleştirir. Öncül tamamlandığında çağrılır ve veri arabelleği doldurulmuştur. (<xref:System.IO.FileStream> nesne döndürülmeden önce kapatılmalıdır.)  
  
 Aşağıdaki örnek, <xref:System.IO.FileStream> sınıfının BeginRead/EndRead çiftini kapsülleyen bir <xref:System.Threading.Tasks.Task> nasıl dönebileceğini gösterir.  
  
 [!code-csharp[FromAsync#03](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#03)]
 [!code-vb[FromAsync#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#03)]  
  
 Yöntemi daha sonra aşağıdaki gibi çağrılabilir.  
  
 [!code-csharp[FromAsync#04](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#04)]
 [!code-vb[FromAsync#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#04)]  
  
### <a name="providing-custom-state-data"></a>Özel Durum Verileri Sağlama  
 Tipik <xref:System.IAsyncResult> işlemlerinde, <xref:System.AsyncCallback> temsilciniz bazı özel durum verileri gerektiriyorsa, bu dosyayı `Begin` yöntemindeki son parametreye geçirmeniz gerekir, böylece veriler sonunda geri çağırmaya geçirilen <xref:System.IAsyncResult> nesnesine paketlenebilir yöntemidir. `FromAsync` yöntemleri kullanıldığında bu genellikle gerekli değildir. Özel veriler devamlılık ile biliniyorsa, bu, doğrudan devamlılık temsilcisinde yakalanabilir. Aşağıdaki örnek, önceki örneğe benzer, ancak öncül öğesinin `Result` özelliğini incelemek yerine, devamlılık Kullanıcı temsilcisi tarafından doğrudan erişilebilen özel durum verilerini inceler.  
  
 [!code-csharp[FromAsync#05](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#05)]
 [!code-vb[FromAsync#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#05)]  
  
### <a name="synchronizing-multiple-fromasync-tasks"></a>Birden Çok FromAsync Görevini Eşitleme  
 Statik <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> ve <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> yöntemleri, `FromAsync` yöntemleriyle birlikte kullanıldığında ek esneklik sağlar. Aşağıdaki örnekte, birden çok zaman uyumsuz g/ç işleminin nasıl başlatılacağı ve sonra devamlılığını yürütmeden önce bunların tümünün tamamlanmasını bekleme işlemi gösterilmektedir.  
  
 [!code-csharp[FromAsync#06](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#06)]
 [!code-vb[FromAsync#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#06)]  
  
### <a name="fromasync-tasks-for-only-the-end-method"></a>Yalnızca End Yöntemi İçin FromAsync Görevleri  
 `Begin` yöntemi üçten fazla giriş parametresi gerektiren veya `ref` veya `out` parametrelere sahip olduğu durumlarda, `FromAsync` aşırı yüklemeleri (örneğin, yalnızca <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%28System.IAsyncResult%2CSystem.Func%7BSystem.IAsyncResult%2C%600%7D%29?displayProperty=nameWithType>yöntemini temsil eden `End`) kullanabilirsiniz. Bu yöntemler Ayrıca, <xref:System.IAsyncResult> geçirileceği ve bir görevde kapsüllemek istediğiniz herhangi bir senaryoda da kullanılabilir.  
  
 [!code-csharp[FromAsync#07](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#07)]
 [!code-vb[FromAsync#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#07)]  
  
### <a name="starting-and-canceling-fromasync-tasks"></a>FromAsync Görevlerini Başlatma ve İptal Eme  
 Bir `FromAsync` yöntemi tarafından döndürülen görev, WaitingForActivation durumuna sahiptir ve görev oluşturulduktan sonra sistem tarafından bir noktada başlatılır. Bu tür bir görevde başlangıç çağrısına çalışırsanız, bir özel durum oluşturulur.  
  
 Temel alınan .NET Framework API 'Leri Şu anda dosyanın veya ağ g/ç 'nin devam eden iptal işlemini desteklemediği için `FromAsync` görevini iptal edemezsiniz. `FromAsync` çağrısını kapsülleyen bir yönteme iptal etme işlevi ekleyebilirsiniz, ancak `FromAsync` çağrılmadan önce veya tamamlandıktan sonra (örneğin, bir devamlılık görevinde) yalnızca iptalle yanıt verebilirsiniz.  
  
 <xref:System.Net.WebClient>, örneğin, EAP 'yi destekleyen bazı sınıflar, iptalleri destekler ve bu yerel iptal işlevini iptal belirteçlerini kullanarak tümleştirebilirsiniz.  
  
## <a name="exposing-complex-eap-operations-as-tasks"></a>Karmaşık EAP İşlemlerini Görev Olarak Ortaya Çıkarma  
 TPL, olay tabanlı bir zaman uyumsuz işlemi, `FromAsync` Yöntem ailesiyle <xref:System.IAsyncResult> deseninin sarmaladığı şekilde kapsüllemek için özel olarak tasarlanan herhangi bir yöntem sağlamaz. Ancak, TPL, <xref:System.Threading.Tasks.Task%601>gibi herhangi bir rastgele işlem kümesini temsil etmek için kullanılabilen <xref:System.Threading.Tasks.TaskCompletionSource%601?displayProperty=nameWithType> sınıfını sağlar. İşlemler zaman uyumlu veya zaman uyumsuz olabilir ve g/ç ile bağlantılı ya da işlem ile veya her ikisi de olabilir.  
  
 Aşağıdaki örnek, istemci koduna temel bir <xref:System.Threading.Tasks.Task%601>olarak bir dizi zaman uyumsuz <xref:System.Net.WebClient> işlemleri göstermek için <xref:System.Threading.Tasks.TaskCompletionSource%601> nasıl kullanacağınızı gösterir. Yöntemi, aranacak bir dizi Web URL 'si, bir terim veya ad girmenizi sağlar ve sonra arama teriminin her sitede oluşma sayısını döndürür.  
  
 [!code-csharp[FromAsync#10](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/snippet10.cs#10)]
 [!code-vb[FromAsync#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/snippet10.vb#10)]  
  
 Ek özel durum işleme içeren ve istemci kodundan yöntemin nasıl çağrılacağını gösteren daha kapsamlı bir örnek için bkz. [nasıl yapılır: bir görevde EAP düzenlerini sarın](../../../docs/standard/parallel-programming/how-to-wrap-eap-patterns-in-a-task.md).  
  
 Bir <xref:System.Threading.Tasks.TaskCompletionSource%601> tarafından oluşturulan herhangi bir görevin, bu TaskCompletionSource tarafından başlatılacağını ve bu nedenle kullanıcı kodunun bu görevde Start yöntemini çağırmamalıdır olduğunu unutmayın.  
  
## <a name="implementing-the-apm-pattern-by-using-tasks"></a>Görevleri Kullanarak APM Desenini Uygulama  
 Bazı senaryolarda, bir API 'de BEGIN/End Yöntem çiftleri kullanılarak <xref:System.IAsyncResult> modelini doğrudan kullanıma sunmak istenebilir. Örneğin, var olan API 'lerle tutarlılığı sürdürmek isteyebilirsiniz veya bu kalıbı gerektiren otomatikleştirilmiş araçlara sahip olabilirsiniz. Bu gibi durumlarda, APM deseninin dahili olarak nasıl uygulandığını basitleştirmek için görevleri kullanabilirsiniz.  
  
 Aşağıdaki örnek, uzun süreli bir işlem ile sınırlı bir yöntem için APM BEGIN/End Yöntem çiftini uygulamak üzere görevlerin nasıl kullanılacağını gösterir.  
  
 [!code-csharp[FromAsync#09](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#09)]
 [!code-vb[FromAsync#09](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#09)]  
  
## <a name="using-the-streamextensions-sample-code"></a>StreamExtensions Örnek Kodunu Kullanma  
 [.NET Framework 4 Ile paralel programlama Için örnek](https://code.msdn.microsoft.com/ParExtSamples)olarak, Streamextensions.cs dosyası, zaman uyumsuz dosya ve ağ g/ç için görev nesnelerini kullanan çeşitli başvuru uygulamaları içerir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Görev Paralel Kitaplığı (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
