---
title: TPL ve geleneksel .NET zaman uyumsuz programlama
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, with other asynchronous models
ms.assetid: e7b31170-a156-433f-9f26-b1fc7cd1776f
ms.openlocfilehash: 498bde82d05259bdc561d08819d024090b0417f0
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92688018"
---
# <a name="tpl-and-traditional-net-asynchronous-programming"></a>TPL ve geleneksel .NET zaman uyumsuz programlama

.NET, g/ç 'ye ve işlem ile sınırlı zaman uyumsuz işlemleri gerçekleştirmek için aşağıdaki iki standart deseni sağlar:  
  
- Zaman uyumsuz işlemlerin bir dizi BEGIN/End yöntemi ile temsil edildiği zaman uyumsuz programlama modeli (APM). Örneğin: <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> ve <xref:System.IO.Stream.EndRead%2A?displayProperty=nameWithType>.  
  
- Zaman uyumsuz işlemlerin ve adlı bir yöntem/olay çiftiyle temsil edildiği olay tabanlı zaman uyumsuz model (EAP) `<OperationName>Async` `<OperationName>Completed` . Örneğin: <xref:System.Net.WebClient.DownloadStringAsync%2A?displayProperty=nameWithType> ve <xref:System.Net.WebClient.DownloadStringCompleted?displayProperty=nameWithType>.
  
Görev paralel kitaplığı (TPL), zaman uyumsuz desenlerden biriyle birlikte çeşitli şekillerde kullanılabilir. Hem APM 'yi hem de EAP işlemlerini bir `Task` nesne olarak kitaplık tüketicilerine sunabilir veya APM düzenlerini açığa çıkarmak ancak `Task` nesneleri dahili olarak uygulamak için kullanabilirsiniz. Her iki senaryoda, nesneleri kullanarak `Task` kodu basitleştirebilir ve aşağıdaki yararlı işlevlerden yararlanabilirsiniz:  
  
- Görev devamlılıkları biçiminde geri çağırmaları, görev başladıktan sonra istediğiniz zaman kaydedin.  
  
- Ve yöntemlerini kullanarak bir yönteme yanıt olarak yürütülen birden çok işlemi koordine `Begin_` <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> edin <xref:System.Threading.Tasks.Task.WaitAll%2A> <xref:System.Threading.Tasks.Task.WaitAny%2A> .  
  
- Aynı nesne içindeki zaman uyumsuz g/ç 'ye ve işlem ile bağlantılı işlemleri kapsülleyebilirsiniz `Task` .  
  
- Nesnenin durumunu izleyin `Task` .  
  
- Kullanarak bir işlemin durumunu bir nesne için sıralama `Task` <xref:System.Threading.Tasks.TaskCompletionSource%601> .  
  
## <a name="wrap-apm-operations-in-a-task"></a>Bir görevde APM işlemlerini sarın  

 Ve sınıflarının her ikisi de, <xref:System.Threading.Tasks.TaskFactory?displayProperty=nameWithType> <xref:System.Threading.Tasks.TaskFactory%601?displayProperty=nameWithType> <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> bir veya örneğinde APM başlangıç/bitiş yöntemi çiftini kapsületmenize olanak sağlayan ve yöntemlerinin birkaç aşırı yüklemesini <xref:System.Threading.Tasks.Task> sağlar <xref:System.Threading.Tasks.Task%601> . Çeşitli aşırı yüklemeler sıfır ile üç giriş parametresine sahip herhangi bir BEGIN/End Yöntem çiftini sağlar.  
  
 Bir `End` değer döndüren metotlara (Visual Basic) sahip çiftler için `Function` , oluşturma içindeki yöntemleri kullanın <xref:System.Threading.Tasks.TaskFactory%601> <xref:System.Threading.Tasks.Task%601> . `End`Void döndüren Yöntemler ( `Sub` Visual Basic) için, oluşturma içindeki yöntemleri kullanın <xref:System.Threading.Tasks.TaskFactory> <xref:System.Threading.Tasks.Task> .  
  
 `Begin`Yöntemin üçten fazla parametresi olduğu veya `ref` ya da parametre içerdiği bazı durumlarda `out` , `FromAsync` yalnızca yöntemi kapsülleyen ek aşırı yüklemeler `End` sağlanır.  
  
 Aşağıdaki örnek `FromAsync` , ve yöntemleriyle eşleşen aşırı yükleme imzasını gösterir <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> <xref:System.IO.FileStream.EndRead%2A?displayProperty=nameWithType> .
  
 [!code-csharp[FromAsync#01](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#01)]
 [!code-vb[FromAsync#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#01)]  
  
Bu aşırı yükleme, aşağıdaki gibi üç giriş parametresi alır. İlk parametre, <xref:System.Func%606> yönteminin imzasıyla eşleşen bir temsilcisidir <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> . İkinci parametre <xref:System.Func%602> ' a sahip olan ve döndüren bir temsilcisidir <xref:System.IAsyncResult> `TResult` . <xref:System.IO.FileStream.EndRead%2A>, Bir tamsayı döndürdüğünden, derleyici türü `TResult` olarak <xref:System.Int32> ve görevin türünü olarak algılar <xref:System.Threading.Tasks.Task> . Son dört parametre, yöntemindeki olanlarla aynıdır <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> :  
  
- Dosya verilerinin depolanması için gereken arabellek.  
  
- Arabellekte veri yazmaya başlayabileceğiniz fark.  
  
- Dosyadan okunacak maksimum veri miktarı.  
  
- Geri çağırmaya geçirilecek Kullanıcı tanımlı durum verilerini depolayan isteğe bağlı bir nesne.  
  
### <a name="use-continuewith-for-the-callback-functionality"></a>Geri çağırma işlevselliği için devam 'ı kullanın

 Dosyadaki verilere erişmeniz gerekiyorsa, yalnızca bayt sayısının aksine, <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> Yöntem yeterli değildir. Bunun yerine, <xref:System.Threading.Tasks.Task> `Result` özelliği dosya verilerini içeren özelliğini kullanın. Bunu, özgün göreve bir devamlılık ekleyerek yapabilirsiniz. Devamlılık, genellikle temsilci tarafından gerçekleştirilen işi gerçekleştirir <xref:System.AsyncCallback> . Öncül tamamlandığında çağrılır ve veri arabelleği doldurulmuştur. ( <xref:System.IO.FileStream> Nesne döndürülmeden önce kapatılmalıdır.)  
  
 Aşağıdaki örnek, <xref:System.Threading.Tasks.Task> `BeginRead` / `EndRead` sınıfının çiftini kapsülleyen bir öğesinin nasıl dönebileceğini göstermektedir <xref:System.IO.FileStream> .  
  
 [!code-csharp[FromAsync#03](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#03)]
 [!code-vb[FromAsync#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#03)]  
  
 Yöntemi daha sonra aşağıdaki gibi çağrılabilir.  
  
 [!code-csharp[FromAsync#04](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#04)]
 [!code-vb[FromAsync#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#04)]  
  
### <a name="provide-custom-state-data"></a>Özel durum verisi sağlama

 Tipik <xref:System.IAsyncResult> işlemlerde, <xref:System.AsyncCallback> temsilciniz bazı özel durum verileri gerektiriyorsa, `Begin` verileri, <xref:System.IAsyncResult> sonunda geri çağırma yöntemine geçirilen nesne içine paketlenebilmeleri için, metodun son parametresinden geçiş yapmanız gerekir. Yöntemler kullanıldığında bu genellikle gerekli değildir `FromAsync` . Özel veriler devamlılık ile biliniyorsa, bu, doğrudan devamlılık temsilcisinde yakalanabilir. Aşağıdaki örnek, önceki örneğe benzer, ancak `Result` öncül öğesinin özelliğini incelemek yerine, devamlılık Kullanıcı temsilcisi tarafından doğrudan erişilebilen özel durum verilerini inceler.  
  
 [!code-csharp[FromAsync#05](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#05)]
 [!code-vb[FromAsync#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#05)]  
  
### <a name="synchronize-multiple-fromasync-tasks"></a>Birden çok FromAsync görevini senkronize etme

 Statik <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> ve <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> yöntemleri, yöntemleriyle birlikte kullanıldığında ek esneklik sağlar `FromAsync` . Aşağıdaki örnekte, birden çok zaman uyumsuz g/ç işleminin nasıl başlatılacağı ve sonra devamlılığını yürütmeden önce bunların tümünün tamamlanmasını bekleme işlemi gösterilmektedir.  
  
 [!code-csharp[FromAsync#06](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#06)]
 [!code-vb[FromAsync#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#06)]  
  
### <a name="fromasync-tasks-for-only-the-end-method"></a>Yalnızca End yöntemi için FromAsync görevleri

 `Begin`Yöntemi üçten fazla giriş parametresi veya ya da parametre gerektiren bu durumlarda, `ref` `out` `FromAsync` <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%28System.IAsyncResult%2CSystem.Func%7BSystem.IAsyncResult%2C%600%7D%29?displayProperty=nameWithType> yalnızca yöntemini temsil eden (örneğin,) aşırı yüklemeleri kullanabilirsiniz `End` . Bu yöntemler aynı zamanda, bir ' ın geçirildiği <xref:System.IAsyncResult> ve bir görevde kapsüllemek istediğiniz herhangi bir senaryoda de kullanılabilir.  
  
 [!code-csharp[FromAsync#07](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#07)]
 [!code-vb[FromAsync#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#07)]  
  
### <a name="start-and-cancel-fromasync-tasks"></a>FromAsync görevlerini başlatma ve iptal etme

 Bir yöntem tarafından döndürülen görevin `FromAsync` durumu vardır `WaitingForActivation` ve bu, görev oluşturulduktan sonra sistem tarafından bir noktada başlatılır. Bu tür bir görevde başlangıç çağrısına çalışırsanız, bir özel durum oluşturulur.  
  
 `FromAsync`Temel alınan .NET API 'leri Şu anda dosyanın veya ağ g/ç 'nin devam eden iptal işlemini desteklemediği için bir görevi iptal edemezsiniz. Çağrıyı kapsülleyen bir yönteme iptal etme işlevselliği ekleyebilirsiniz `FromAsync` , ancak yalnızca iptalden önce `FromAsync` veya tamamlandıktan sonra (örneğin, bir devamlılık görevinde) yanıt verebilirsiniz.  
  
 Örneğin, EAP 'yi destekleyen bazı sınıflar, <xref:System.Net.WebClient> iptali destekler ve iptal belirteçlerini kullanarak bu yerel iptal işlevselliğini tümleştirebilirsiniz.  
  
## <a name="expose-complex-eap-operations-as-tasks"></a>Karmaşık EAP işlemlerini görev olarak kullanıma sunma

 TPL, olay tabanlı bir zaman uyumsuz işlemi, `FromAsync` Yöntem ailesünün sarmaladığı şekilde kapsüllemek için özel olarak tasarlanan herhangi bir yöntem sağlamaz <xref:System.IAsyncResult> . Ancak, TPL, <xref:System.Threading.Tasks.TaskCompletionSource%601?displayProperty=nameWithType> bir olarak herhangi bir rastgele işlem kümesini temsil etmek için kullanılabilen sınıfını sağlar <xref:System.Threading.Tasks.Task%601> . İşlemler zaman uyumlu veya zaman uyumsuz olabilir ve g/ç ile bağlantılı ya da işlem ile veya her ikisi de olabilir.  
  
 Aşağıdaki örnek, bir <xref:System.Threading.Tasks.TaskCompletionSource%601> dizi zaman uyumsuz <xref:System.Net.WebClient> işlemleri bir temel olarak istemci koduna göstermek için nasıl kullanılacağını gösterir <xref:System.Threading.Tasks.Task%601> . Yöntemi, aranacak bir dizi Web URL 'si, bir terim veya ad girmenizi sağlar ve sonra arama teriminin her sitede oluşma sayısını döndürür.  
  
 [!code-csharp[FromAsync#10](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/snippet10.cs#10)]
 [!code-vb[FromAsync#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/snippet10.vb#10)]  
  
 Ek özel durum işleme içeren ve istemci kodundan yöntemin nasıl çağrılacağını gösteren daha kapsamlı bir örnek için bkz. [nasıl yapılır: bir görevde EAP düzenlerini sarın](how-to-wrap-eap-patterns-in-a-task.md).  
  
 Tarafından oluşturulan tüm görevlerin <xref:System.Threading.Tasks.TaskCompletionSource%601> Bu ve tarafından başlatılacağını unutmayın `TaskCompletionSource` , bu nedenle Kullanıcı kodu bu `Start` görevde yöntemi çağırmamalıdır.  
  
## <a name="implement-the-apm-pattern-by-using-tasks"></a>Görevleri kullanarak APM modelini uygulama

 Bazı senaryolarda, <xref:System.IAsyncResult> BIR API 'de BEGIN/End Yöntem çiftleri kullanılarak doğrudan model kullanıma sunulmasının istenebilir. Örneğin, var olan API 'lerle tutarlılığı sürdürmek isteyebilirsiniz veya bu kalıbı gerektiren otomatikleştirilmiş araçlara sahip olabilirsiniz. Bu gibi durumlarda, `Task` APM deseninin dahili olarak nasıl uygulandığını basitleştirmek için nesneleri kullanabilirsiniz.  
  
 Aşağıdaki örnek, uzun süreli bir işlem ile sınırlı bir yöntem için APM BEGIN/End Yöntem çiftini uygulamak üzere görevlerin nasıl kullanılacağını gösterir.  
  
 [!code-csharp[FromAsync#09](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#09)]
 [!code-vb[FromAsync#09](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#09)]  
  
## <a name="use-the-streamextensions-sample-code"></a>StreamExtensions örnek kodunu kullanma

 [.NET Standard Parallel Extensions ek](/samples/dotnet/samples/parallel-programming-extensions-extras-cs/) deposundaki *StreamExtensions.cs* dosyası, `Task` zaman uyumsuz dosya ve ağ g/ç için nesneleri kullanan çeşitli başvuru uygulamaları içerir.
  
## <a name="see-also"></a>Ayrıca bkz.

- [Görev Paralel Kitaplığı (TPL)](task-parallel-library-tpl.md)
