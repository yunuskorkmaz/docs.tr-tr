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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139943"
---
# <a name="tpl-and-traditional-net-framework-asynchronous-programming"></a>TPL ve Geleneksel .NET Framework Zaman Uyumsuz Programlama
.NET Framework, G/Ç bağlı ve işlem le bağlı eşzamanlı işlemleri gerçekleştirmek için aşağıdaki iki standart desen sağlar:  
  
- Asynchronous Programlama Modeli (APM), hangi asynchronous işlemleri gibi <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> Begin /End yöntemleri <xref:System.IO.Stream.EndRead%2A?displayProperty=nameWithType>bir çift tarafından temsil edilir ve .  
  
- Asenkron *işlemlerinin,* örneğin OperationName Async ve *OperationName*Completed adlı bir yöntem/olay çifti tarafından temsil edildiği olay tabanlı eşzamanlı <xref:System.Net.WebClient.DownloadStringAsync%2A?displayProperty=nameWithType> <xref:System.Net.WebClient.DownloadStringCompleted?displayProperty=nameWithType>desen (EAP) ve . (EAP .NET Framework sürümü 2.0 tanıtıldı.)  
  
 Görev Paralel Kitaplığı (TPL), asynchronous desenleri ile birlikte çeşitli şekillerde kullanılabilir. Hem APM hem de EAP işlemlerini kitaplık tüketicilerine Görevler olarak gösterebilirsiniz veya APM desenlerini ortaya çıkarabilir, ancak bunları dahili olarak uygulamak için Görev nesnelerini kullanabilirsiniz. Her iki senaryoda da Görev nesnelerini kullanarak kodu basitleştirebilir ve aşağıdaki yararlı işlevlerden yararlanabilirsiniz:  
  
- Görev başladıktan sonra herhangi bir zamanda, görev devamları şeklinde geri aramaları kaydedin.  
  
- Bir `Begin_` <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> yönteme yanıt olarak, yöntemleri veya <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> yöntemi veya <xref:System.Threading.Tasks.Task.WaitAll%2A> <xref:System.Threading.Tasks.Task.WaitAny%2A> yöntemi kullanarak birden çok işlemi koordine edin.  
  
- Aynı Görev nesnesinde eşzamanlı G/Ç ve bilgi işlem lerini kapsülle.  
  
- Görev nesnesinin durumunu izleyin.  
  
- Bir görev nesnesine bir işlem durumunu <xref:System.Threading.Tasks.TaskCompletionSource%601>kullanarak mareşal.  
  
## <a name="wrapping-apm-operations-in-a-task"></a>APM İşlemlerini Bir Görevle Sarma  
 Hem <xref:System.Threading.Tasks.TaskFactory?displayProperty=nameWithType> <xref:System.Threading.Tasks.TaskFactory%601?displayProperty=nameWithType> sınıflar, <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A?displayProperty=nameWithType> bir veya <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> durumda bir APM Begin/End yöntem çiftini kapsüllemenize izin veren birkaç fazla yükleme ve yöntem sağlar. Çeşitli aşırı yüklemeler, sıfırdan üç e-giriş parametresine sahip herhangi bir Begin/End yöntem çiftini barındırır.  
  
 Bir değeri `End` döndüren yöntemleri olan`Function` çiftler için (Visual <xref:System.Threading.Tasks.TaskFactory%601> Basic'te), bir <xref:System.Threading.Tasks.Task%601>. Geçersiz `End` returneden yöntemler`Sub` için (Visual Basic'te), <xref:System.Threading.Tasks.TaskFactory> <xref:System.Threading.Tasks.Task>bir .  
  
 Yöntemin `Begin` üçten fazla parametreye veya içerdiği `ref` `out` veya parametreye sahip olduğu birkaç `End` durumda, yalnızca yöntemi kapsülleyen ek `FromAsync` aşırı yüklemeler sağlanır.  
  
 Aşağıdaki örnek, aşırı yükleme `FromAsync` nin imzasını <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> <xref:System.IO.FileStream.EndRead%2A?displayProperty=nameWithType> ve yöntemleriyle eşleşen imzayı gösterir. Bu aşırı yükleme aşağıdaki gibi üç giriş parametrealır.  
  
 [!code-csharp[FromAsync#01](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#01)]
 [!code-vb[FromAsync#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#01)]  
  
 İlk parametre, <xref:System.Func%606> yöntemin imzasıyla <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> eşleşen bir temsilcidir. İkinci parametre, <xref:System.Func%602> bir <xref:System.IAsyncResult> ' yi alan `TResult`ve bir . döndüren bir temsilcidir Bir <xref:System.IO.FileStream.EndRead%2A> karşıcı döndürdüklerinden, derleyici `TResult` görevin <xref:System.Int32> türünü ve türünü <xref:System.Threading.Tasks.Task>. Son dört parametre <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> yöntemdekilerle aynıdır:  
  
- Dosya verilerini depolamak için arabellek.  
  
- Veri yazmaya başlamak için arabellekteki ofset.  
  
- Dosyadan okunacak maksimum veri miktarı.  
  
- Kullanıcı tanımlı durum verilerini geri aramaya geçirmek üzere depolayan isteğe bağlı bir nesne.  
  
### <a name="using-continuewith-for-the-callback-functionality"></a>Geri Çağırma İşlevi İçin ContinueWith Kullanma  
 Yalnızca bayt sayısının aksine, dosyadaki verilere erişmeye ihtiyacınız varsa, <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> yöntem yeterli değildir. Bunun yerine, <xref:System.Threading.Tasks.Task> `Result` özelliği dosya verilerini içeren , kullanın. Bunu, özgün göreve bir devamı ekleyerek yapabilirsiniz. Devamı genellikle <xref:System.AsyncCallback> temsilci tarafından gerçekleştirilecek işi gerçekleştirir. Öncül tamamlandığında çağrılır ve veri arabelleği doldurulur. (Nesne <xref:System.IO.FileStream> dönmeden önce kapatılmalıdır.)  
  
 Aşağıdaki örnek, sınıfın BeginRead/EndRead çiftini içeren bir <xref:System.Threading.Tasks.Task> şeyin nasıl <xref:System.IO.FileStream> döndürüleceklerini gösterir.  
  
 [!code-csharp[FromAsync#03](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#03)]
 [!code-vb[FromAsync#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#03)]  
  
 Yöntem daha sonra aşağıdaki gibi çağrılabilir.  
  
 [!code-csharp[FromAsync#04](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#04)]
 [!code-vb[FromAsync#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#04)]  
  
### <a name="providing-custom-state-data"></a>Özel Durum Verileri Sağlama  
 Tipik <xref:System.IAsyncResult> işlemlerde, <xref:System.AsyncCallback> temsilciniz bazı özel durum verileri gerektiriyorsa, verilerin sonunda `Begin` geri arama yöntemine geçirilen <xref:System.IAsyncResult> nesneye paketlenebilmeleri için, bunu yöntemdeki son parametreden geçirmeniz gerekir. Yöntemler kullanıldığında bu genellikle `FromAsync` gerekli değildir. Özel verilerin devamı biliniyorsa, doğrudan devam temsilcisinde yakalanabilir. Aşağıdaki örnek önceki örneğe benzer, ancak öncül `Result` özelliğini incelemek yerine, devamı kullanıcı temsilcisi tarafından doğrudan erişilebilir özel durum verileri inceler.  
  
 [!code-csharp[FromAsync#05](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#05)]
 [!code-vb[FromAsync#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#05)]  
  
### <a name="synchronizing-multiple-fromasync-tasks"></a>Birden Çok FromAsync Görevini Eşitleme  
 Statik <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> ve <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> `FromAsync` yöntemler, yöntemlerle birlikte kullanıldığında ek esneklik sağlar. Aşağıdaki örnek, birden çok eşzamanlı G/Ç işlemini nasıl başlatabileceğinizi ve devamı gerçekleştirmeden önce bunların tamamlanmasını nasıl bekleyeceğinizi gösterir.  
  
 [!code-csharp[FromAsync#06](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#06)]
 [!code-vb[FromAsync#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#06)]  
  
### <a name="fromasync-tasks-for-only-the-end-method"></a>Yalnızca End Yöntemi İçin FromAsync Görevleri  
 Yöntemin `Begin` üçten fazla giriş parametresi gerektirdiği veya `ref` `out` varsa veya parametrelere `FromAsync` sahip olduğu birkaç <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%28System.IAsyncResult%2CSystem.Func%7BSystem.IAsyncResult%2C%600%7D%29?displayProperty=nameWithType>durumda, örneğin, yalnızca `End` yöntemi temsil eden aşırı yüklemeleri kullanabilirsiniz. Bu yöntemler, bir geçirilen <xref:System.IAsyncResult> ve bir Görev içinde kapsüllemek istediğiniz herhangi bir senaryoda da kullanılabilir.  
  
 [!code-csharp[FromAsync#07](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#07)]
 [!code-vb[FromAsync#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#07)]  
  
### <a name="starting-and-canceling-fromasync-tasks"></a>FromAsync Görevlerini Başlatma ve İptal Eme  
 Bir `FromAsync` yöntemle döndürülen görev, Bekleme Etkinleştirme durumuna sahiptir ve görev oluşturulduktan sonra bir noktada sistem tarafından başlatılır. Böyle bir görevde Başlat'ı aramayı denerseniz, bir özel durum yükseltilir.  
  
 Altta yatan `FromAsync` .NET Framework API'leri şu anda dosya veya ağ G/Ç'nin devam eden iptalini desteklemediği için bir görevi iptal edemezsiniz. Bir `FromAsync` aramayı kapsülleyen bir yönteme iptal işlevi ekleyebilirsiniz, ancak iptale yalnızca `FromAsync` çağrılmadan önce veya tamamlandıktan sonra (örneğin, bir devam görevinde) yanıt verebilirsiniz.  
  
 Örneğin, <xref:System.Net.WebClient>EAP'yi destekleyen bazı sınıflar, iptali destekler ve iptal belirteçlerini kullanarak bu yerel iptal işlevini tümleştirebilirsiniz.  
  
## <a name="exposing-complex-eap-operations-as-tasks"></a>Karmaşık EAP İşlemlerini Görev Olarak Ortaya Çıkarma  
 TPL, olay tabanlı bir eşzamanlı işlemi, yöntem `FromAsync` ailesinin <xref:System.IAsyncResult> deseni sardığı şekilde kapsüllemek için özel olarak tasarlanmış herhangi bir yöntem sağlamaz. Ancak, TPL <xref:System.Threading.Tasks.TaskCompletionSource%601?displayProperty=nameWithType> bir <xref:System.Threading.Tasks.Task%601>. İşlemler senkron veya eşzamanlı olabilir ve G/Ç'ye bağlı veya bilgisayara bağlı veya her ikisi de olabilir.  
  
 Aşağıdaki örnek, a <xref:System.Threading.Tasks.TaskCompletionSource%601> kümesini <xref:System.Net.WebClient> istemci koduna temel <xref:System.Threading.Tasks.Task%601>olarak ortaya çıkarmak için nasıl kullanılacağını gösterir. Yöntem, bir dizi Web URL'si ve aranacak bir terim veya ad girmenize olanak tanır ve ardından her sitede arama teriminin kaç kez oluştuğunu döndürür.  
  
 [!code-csharp[FromAsync#10](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/snippet10.cs#10)]
 [!code-vb[FromAsync#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/snippet10.vb#10)]  
  
 Ek özel durum işleme içeren ve istemci kodundan yöntemin nasıl çağrılılacağını gösteren daha eksiksiz bir örnek için [bkz.](../../../docs/standard/parallel-programming/how-to-wrap-eap-patterns-in-a-task.md)  
  
 Bir tarafından oluşturulan herhangi bir <xref:System.Threading.Tasks.TaskCompletionSource%601> görevin bu TaskCompletionSource tarafından başlatılacağını ve bu nedenle kullanıcı kodunun bu görevde Başlat yöntemini aramaması gerektiğini unutmayın.  
  
## <a name="implementing-the-apm-pattern-by-using-tasks"></a>Görevleri Kullanarak APM Desenini Uygulama  
 Bazı senaryolarda, bir API'de <xref:System.IAsyncResult> Begin/End yöntem çiftlerini kullanarak deseni doğrudan ortaya çıkarmak istenebilir. Örneğin, varolan API'lerle tutarlılığı korumak isteyebilirsiniz veya bu deseni gerektiren otomatik araçlarınız olabilir. Bu gibi durumlarda, APM deseni dahili olarak nasıl uygulandığını basitleştirmek için Görevler'i kullanabilirsiniz.  
  
 Aşağıdaki örnek, uzun süren bir işlem leziz yöntem için APM Begin/End yöntem çiftini uygulamak için görevlerin nasıl kullanılacağını gösterir.  
  
 [!code-csharp[FromAsync#09](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#09)]
 [!code-vb[FromAsync#09](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#09)]  
  
## <a name="using-the-streamextensions-sample-code"></a>StreamExtensions Örnek Kodunu Kullanma  
 Streamextensions.cs dosyası, [.NET Framework 4 ile Paralel Programlama](https://code.msdn.microsoft.com/ParExtSamples)Örnekleri,asynchronous dosya ve ağ G/Ç için Görev nesnelerini kullanan birkaç başvuru uygulaması içerir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Görev Paralel Kitaplığı (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
