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
ms.openlocfilehash: e71c609b500bc6771c405cfb6f4ac14923cc3939
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507552"
---
# <a name="tpl-and-traditional-net-framework-asynchronous-programming"></a>TPL ve Geleneksel .NET Framework Zaman Uyumsuz Programlama
.NET Framework g/ç 'ye ve işlem ile bağlantılı zaman uyumsuz işlemleri gerçekleştirmek için aşağıdaki iki standart deseni sağlar:  
  
- Zaman uyumsuz işlemlerin, <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> ve <xref:System.IO.Stream.EndRead%2A?displayProperty=nameWithType>gibi bir dizi BEGIN/End yöntemi ile temsil edildiği zaman uyumsuz programlama modeli (APM).  
  
- Zaman uyumsuz işlemlerin, *OperationName*zaman uyumsuz ve *OperationName*tamamlandı adlı bir yöntem/olay çifti tarafından temsil edildiği olay tabanlı zaman uyumsuz model (EAP) <xref:System.Net.WebClient.DownloadStringAsync%2A?displayProperty=nameWithType> ve örneğin ve <xref:System.Net.WebClient.DownloadStringCompleted?displayProperty=nameWithType>. (EAP .NET Framework sürüm 2,0 ' de tanıtılmıştı.)  
  
 Görev paralel kitaplığı (TPL), zaman uyumsuz desenlerden biriyle birlikte çeşitli şekillerde kullanılabilir. Hem APM hem de EAP işlemlerini bir görev olarak bir işlem halinde sunabilir veya APM düzenlerini açığa çıkarmak, ancak bunları dahili olarak uygulamak için görev nesnelerini kullanmak için kullanabilirsiniz. Her iki senaryoda, görev nesnelerini kullanarak kodu basitleştirebilir ve aşağıdaki yararlı işlevlerden yararlanabilirsiniz:  
  
- Görev devamlılıkları biçiminde geri çağırmaları, görev başladıktan sonra istediğiniz zaman kaydedin.  
  
- <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> Ve <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> yöntemlerini <xref:System.Threading.Tasks.Task.WaitAll%2A> ya da yöntemini veya <xref:System.Threading.Tasks.Task.WaitAny%2A> yöntemini kullanarak bir `Begin_` yönteme yanıt olarak yürütülen birden çok işlemi koordine edin.  
  
- Aynı görev nesnesinde zaman uyumsuz g/ç 'ye ve işlem ile bağlantılı işlemleri kapsülleyebilirsiniz.  
  
- Görev nesnesinin durumunu izleyin.  
  
- Kullanarak <xref:System.Threading.Tasks.TaskCompletionSource%601>bir işlemin durumunu bir görev nesnesine göre sıralama.  
  
## <a name="wrapping-apm-operations-in-a-task"></a>APM İşlemlerini Bir Görevle Sarma  
 <xref:System.Threading.Tasks.TaskFactory?displayProperty=nameWithType> Ve <xref:System.Threading.Tasks.TaskFactory%601?displayProperty=nameWithType> <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A?displayProperty=nameWithType> sınıflarının her IKISI de, bir <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> örneğinde APM başlangıç/bitiş yöntemi çiftini kapsületmenize olanak sağlayan ve yöntemlerinin birkaç aşırı yüklemesini sağlar. Çeşitli aşırı yüklemeler sıfır ile üç giriş parametresine sahip herhangi bir BEGIN/End Yöntem çiftini sağlar.  
  
 `End` Bir değer döndüren metotlara sahip çiftler için (`Function` Visual Basic), oluşturma içindeki <xref:System.Threading.Tasks.TaskFactory%601> yöntemleri kullanın. <xref:System.Threading.Tasks.Task%601> Void `End` döndüren yöntemler (`Sub` Visual Basic) için, oluşturma içindeki <xref:System.Threading.Tasks.TaskFactory> yöntemleri kullanın. <xref:System.Threading.Tasks.Task>  
  
 `Begin` Yöntemin üçten fazla parametresi olduğu `ref` veya ya da `out` parametre içerdiği bazı durumlarda, yalnızca `FromAsync` `End` yöntemi kapsülleyen ek aşırı yüklemeler sağlanır.  
  
 Aşağıdaki örnek, `FromAsync` <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> ve <xref:System.IO.FileStream.EndRead%2A?displayProperty=nameWithType> yöntemleriyle eşleşen aşırı yükleme imzasını gösterir. Bu aşırı yükleme, aşağıdaki gibi üç giriş parametresi alır.  
  
 [!code-csharp[FromAsync#01](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#01)]
 [!code-vb[FromAsync#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#01)]  
  
 İlk parametre, <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> yönteminin imzasıyla <xref:System.Func%606> eşleşen bir temsilcisidir. İkinci parametre <xref:System.IAsyncResult> ' a `TResult`sahip <xref:System.Func%602> olan ve döndüren bir temsilcisidir. , <xref:System.IO.FileStream.EndRead%2A> Bir tamsayı döndürdüğünden, derleyici türü `TResult` olarak <xref:System.Int32> ve görevin türünü olarak <xref:System.Threading.Tasks.Task>algılar. Son dört parametre, <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> yöntemindeki olanlarla aynıdır:  
  
- Dosya verilerinin depolanması için gereken arabellek.  
  
- Arabellekte veri yazmaya başlayabileceğiniz fark.  
  
- Dosyadan okunacak maksimum veri miktarı.  
  
- Geri çağırmaya geçirilecek Kullanıcı tanımlı durum verilerini depolayan isteğe bağlı bir nesne.  
  
### <a name="using-continuewith-for-the-callback-functionality"></a>Geri Çağırma İşlevi İçin ContinueWith Kullanma  
 Dosyadaki verilere erişmeniz gerekiyorsa, yalnızca bayt sayısının aksine, <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> yöntem yeterli değildir. Bunun yerine, <xref:System.Threading.Tasks.Task> `Result` özelliği dosya verilerini içeren özelliğini kullanın. Bunu, özgün göreve bir devamlılık ekleyerek yapabilirsiniz. Devamlılık, genellikle <xref:System.AsyncCallback> temsilci tarafından gerçekleştirilen işi gerçekleştirir. Öncül tamamlandığında çağrılır ve veri arabelleği doldurulmuştur. ( <xref:System.IO.FileStream> Nesne döndürülmeden önce kapatılmalıdır.)  
  
 Aşağıdaki örnek, <xref:System.Threading.Tasks.Task> <xref:System.IO.FileStream> sınıfının BeginRead/EndRead çiftini kapsülleyen bir öğesinin nasıl dönebileceğini göstermektedir.  
  
 [!code-csharp[FromAsync#03](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#03)]
 [!code-vb[FromAsync#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#03)]  
  
 Yöntemi daha sonra aşağıdaki gibi çağrılabilir.  
  
 [!code-csharp[FromAsync#04](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#04)]
 [!code-vb[FromAsync#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#04)]  
  
### <a name="providing-custom-state-data"></a>Özel Durum Verileri Sağlama  
 Tipik <xref:System.IAsyncResult> işlemlerde, <xref:System.AsyncCallback> temsilciniz bazı özel durum verileri gerektiriyorsa, verileri, sonunda geri çağırma yöntemine geçirilen `Begin` <xref:System.IAsyncResult> nesne içine paketlenebilmeleri için, metodun son parametresinden geçiş yapmanız gerekir. `FromAsync` Yöntemler kullanıldığında bu genellikle gerekli değildir. Özel veriler devamlılık ile biliniyorsa, bu, doğrudan devamlılık temsilcisinde yakalanabilir. Aşağıdaki örnek, önceki örneğe benzer, ancak öncül öğesinin `Result` özelliğini incelemek yerine, devamlılık Kullanıcı temsilcisi tarafından doğrudan erişilebilen özel durum verilerini inceler.  
  
 [!code-csharp[FromAsync#05](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#05)]
 [!code-vb[FromAsync#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#05)]  
  
### <a name="synchronizing-multiple-fromasync-tasks"></a>Birden Çok FromAsync Görevini Eşitleme  
 Statik <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> ve <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> yöntemleri, `FromAsync` yöntemleriyle birlikte kullanıldığında ek esneklik sağlar. Aşağıdaki örnekte, birden çok zaman uyumsuz g/ç işleminin nasıl başlatılacağı ve sonra devamlılığını yürütmeden önce bunların tümünün tamamlanmasını bekleme işlemi gösterilmektedir.  
  
 [!code-csharp[FromAsync#06](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#06)]
 [!code-vb[FromAsync#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#06)]  
  
### <a name="fromasync-tasks-for-only-the-end-method"></a>Yalnızca End Yöntemi İçin FromAsync Görevleri  
 `Begin` Yöntemi `ref` üçten fazla giriş parametresi veya ya `out` da parametre gerektiren bu birkaç durum için, yalnızca `FromAsync` <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%28System.IAsyncResult%2CSystem.Func%7BSystem.IAsyncResult%2C%600%7D%29?displayProperty=nameWithType> `End` yöntemini temsil eden (örneğin,) aşırı yüklemeleri kullanabilirsiniz. Bu yöntemler Ayrıca, kendisine geçirilen ve bir görevde kapsüllemek istediğiniz herhangi bir <xref:System.IAsyncResult> senaryoda da kullanılabilir.  
  
 [!code-csharp[FromAsync#07](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#07)]
 [!code-vb[FromAsync#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#07)]  
  
### <a name="starting-and-canceling-fromasync-tasks"></a>FromAsync Görevlerini Başlatma ve İptal Eme  
 Bir `FromAsync` yöntem tarafından döndürülen görev, WaitingForActivation durumuna sahiptir ve bu görev oluşturulduktan sonra sistem tarafından bir noktada başlatılır. Bu tür bir görevde başlangıç çağrısına çalışırsanız, bir özel durum oluşturulur.  
  
 Temeldeki .NET Framework API 'Leri `FromAsync` , dosyanın veya ağ g/ç 'nin devam eden iptal işlemini desteklemediği için bir görevi iptal edemezsiniz. `FromAsync` Çağrıyı kapsülleyen bir yönteme iptal etme işlevselliği ekleyebilirsiniz, ancak yalnızca iptalden önce `FromAsync` veya tamamlandıktan sonra (örneğin, bir devamlılık görevinde) yanıt verebilirsiniz.  
  
 Örneğin, <xref:System.Net.WebClient>EAP 'yi destekleyen bazı sınıflar, iptali destekler ve iptal belirteçlerini kullanarak bu yerel iptal işlevselliğini tümleştirebilirsiniz.  
  
## <a name="exposing-complex-eap-operations-as-tasks"></a>Karmaşık EAP İşlemlerini Görev Olarak Ortaya Çıkarma  
 TPL, olay tabanlı bir zaman uyumsuz işlemi, yöntem `FromAsync` <xref:System.IAsyncResult> ailesünün sarmaladığı şekilde kapsüllemek için özel olarak tasarlanan herhangi bir yöntem sağlamaz. Ancak, TPL, bir olarak herhangi <xref:System.Threading.Tasks.TaskCompletionSource%601?displayProperty=nameWithType> bir <xref:System.Threading.Tasks.Task%601>rastgele işlem kümesini temsil etmek için kullanılabilen sınıfını sağlar. İşlemler zaman uyumlu veya zaman uyumsuz olabilir ve g/ç ile bağlantılı ya da işlem ile veya her ikisi de olabilir.  
  
 Aşağıdaki örnek, bir <xref:System.Threading.Tasks.TaskCompletionSource%601> dizi zaman uyumsuz <xref:System.Net.WebClient> işlemleri bir temel <xref:System.Threading.Tasks.Task%601>olarak istemci koduna göstermek için nasıl kullanılacağını gösterir. Yöntemi, aranacak bir dizi Web URL 'si, bir terim veya ad girmenizi sağlar ve sonra arama teriminin her sitede oluşma sayısını döndürür.  
  
 [!code-csharp[FromAsync#10](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/snippet10.cs#10)]
 [!code-vb[FromAsync#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/snippet10.vb#10)]  
  
 Ek özel durum işleme içeren ve istemci kodundan yöntemin nasıl çağrılacağını gösteren daha kapsamlı bir örnek için bkz. [nasıl yapılır: bir görevde EAP düzenlerini sarın](../../../docs/standard/parallel-programming/how-to-wrap-eap-patterns-in-a-task.md).  
  
 Tarafından oluşturulan herhangi bir <xref:System.Threading.Tasks.TaskCompletionSource%601> görevin, bu TaskCompletionSource tarafından başlatılacağını ve bu nedenle kullanıcı kodunun bu görevde Start yöntemini çağırmamalıdır olduğunu unutmayın.  
  
## <a name="implementing-the-apm-pattern-by-using-tasks"></a>Görevleri Kullanarak APM Desenini Uygulama  
 Bazı senaryolarda, bir API 'de BEGIN/End Yöntem çiftleri kullanılarak <xref:System.IAsyncResult> doğrudan model kullanıma sunulmasının istenebilir. Örneğin, var olan API 'lerle tutarlılığı sürdürmek isteyebilirsiniz veya bu kalıbı gerektiren otomatikleştirilmiş araçlara sahip olabilirsiniz. Bu gibi durumlarda, APM deseninin dahili olarak nasıl uygulandığını basitleştirmek için görevleri kullanabilirsiniz.  
  
 Aşağıdaki örnek, uzun süreli bir işlem ile sınırlı bir yöntem için APM BEGIN/End Yöntem çiftini uygulamak üzere görevlerin nasıl kullanılacağını gösterir.  
  
 [!code-csharp[FromAsync#09](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#09)]
 [!code-vb[FromAsync#09](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#09)]  
  
## <a name="using-the-streamextensions-sample-code"></a>StreamExtensions Örnek Kodunu Kullanma  
 [.NET Standard Parallel Extensions ek](/samples/dotnet/samples/parallel-programming-extensions-extras-cs/) deposundaki *StreamExtensions.cs* dosyası, zaman uyumsuz dosya ve ağ g/ç için nesneleri `Task` kullanan çeşitli başvuru uygulamaları içerir.
  
## <a name="see-also"></a>Ayrıca bkz.

- [Görev Paralel Kitaplığı (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
