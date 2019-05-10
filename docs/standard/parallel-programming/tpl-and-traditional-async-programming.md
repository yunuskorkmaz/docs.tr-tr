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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 57f274d55ba5723ce8e0b51a7a39e98e95855e28
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64653920"
---
# <a name="tpl-and-traditional-net-framework-asynchronous-programming"></a>TPL ve Geleneksel .NET Framework Zaman Uyumsuz Programlama
.NET Framework, ı/O-bağlı ve hesaplama bağlantılı zaman uyumsuz işlemleri gerçekleştirmek için aşağıdaki iki standart desenler sağlar:  
  
- Zaman uyumsuz programlama modeli (içinde zaman uyumsuz işlemleri temsil edilir başlangıç/bitiş yöntemlerin bir çifti tarafından gibi APM), <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> ve <xref:System.IO.Stream.EndRead%2A?displayProperty=nameWithType>.  
  
- Zaman uyumsuz işlemler adlandırılmış bir yöntemi/olay çifti tarafından gösterilir olay tabanlı zaman uyumsuz desen (EAP) *OperationName*zaman uyumsuz ve *OperationName*, örneğin, tamamlanmış <xref:System.Net.WebClient.DownloadStringAsync%2A?displayProperty=nameWithType> ve <xref:System.Net.WebClient.DownloadStringCompleted?displayProperty=nameWithType>. (.NET Framework 2.0 sürümünde EAP başlamıştır.)  
  
 Görev paralel kitaplığı (TPL), ya da zaman uyumsuz desenleri ile çeşitli yollarla birlikte kullanılabilir. APM hem de EAP işlemlerini görev olarak kitaplığı tüketicilere getirebilir veya APM desenleri kullanıma sunar ancak bunları dahili olarak uygulamak için görev nesnelerinin kullanın. Kullanarak görev nesnelerinin her iki senaryoda kodu basitleştirmek ve aşağıdaki kullanışlı işlevsellik yararlanın:  
  
- Geri çağırmalar görev başlatıldıktan sonra herhangi bir zamanda görev devamlılıkları biçiminde kaydedin.  
  
- Yanıt olarak yürütülen birden çok işlemleri koordine bir `Begin_` yöntemi kullanarak <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> ve <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> yöntemleri veya <xref:System.Threading.Tasks.Task.WaitAll%2A> yöntemi veya <xref:System.Threading.Tasks.Task.WaitAny%2A> yöntemi.  
  
- Aynı görev nesnesi içinde zaman uyumsuz ı/O-bağlı ve hesaplama bağlantılı işlemler kapsüller.  
  
- Görev nesnesi durumunu izleyin.  
  
- Bir görev nesnesi için bir işlemin durumunu kullanarak sıralama <xref:System.Threading.Tasks.TaskCompletionSource%601>.  
  
## <a name="wrapping-apm-operations-in-a-task"></a>APM İşlemlerini Bir Görevle Sarma  
 Hem <xref:System.Threading.Tasks.TaskFactory?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.TaskFactory%601?displayProperty=nameWithType> sınıfları ilişkin çeşitli aşırı yükler sağlar <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> olanak tanıyan yöntemler kapsülleyen bir APM başlangıç/bitiş yöntemi çifti birinde <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> örneği. Çeşitli aşırı üç giriş parametreleri için sıfır olan herhangi bir başlangıç/bitiş yöntemi çifti uyum sağlamak.  
  
 Sahip çiftleri için `End` bir değer döndüren yöntemler (`Function` Visual Basic'te), yöntemi kullanarak <xref:System.Threading.Tasks.TaskFactory%601> oluşturan bir <xref:System.Threading.Tasks.Task%601>. İçin `End` void döndüren yöntemler (`Sub` Visual Basic'te), yöntemi kullanarak <xref:System.Threading.Tasks.TaskFactory> oluşturan bir <xref:System.Threading.Tasks.Task>.  
  
 Bu birkaç durumda için `Begin` yöntemi üçten fazla parametre yoksa ya da içeren `ref` veya `out` ek parametreler `FromAsync` yalnızca kapsayan aşırı `End` yöntemi sağlanır.  
  
 Aşağıdaki örnek, imzası gösterir `FromAsync` eşleşen aşırı yükleme <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> ve <xref:System.IO.FileStream.EndRead%2A?displayProperty=nameWithType> yöntemleri. Bu aşırı yükleme gibi üç giriş parametrelerini alır.  
  
 [!code-csharp[FromAsync#01](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#01)]
 [!code-vb[FromAsync#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#01)]  
  
 İlk parametre bir <xref:System.Func%606> imzası eşleşen temsilci <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> yöntemi. İkinci parametre bir <xref:System.Func%602> alan temsilci bir <xref:System.IAsyncResult> ve döndüren bir `TResult`. Çünkü <xref:System.IO.FileStream.EndRead%2A> bir tamsayı döndürür, derleyici türünü çıkarsar `TResult` olarak <xref:System.Int32> ve görev olarak türünü <xref:System.Threading.Tasks.Task>. Son dört parametre penceresindekilerle aynıdır <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> yöntemi:  
  
- Dosya verilerini depolamak için arabellek.  
  
- Veri yazmaya başlanacak arabellek uzaklığı.  
  
- En fazla dosyadan okunan veri miktarı.  
  
- Geri çağırmaya geçirilecek kullanıcı tanımlı Durum verilerini depolayan isteğe bağlı bir nesne.  
  
### <a name="using-continuewith-for-the-callback-functionality"></a>Geri Çağırma İşlevi İçin ContinueWith Kullanma  
 Bayt sayısını değil dosya verilerine erişim gerekiyorsa <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> yöntemi yeterli değildir. Bunun yerine, <xref:System.Threading.Tasks.Task>, olan `Result` özelliği, dosya verilerini içerir. Özgün göreve bir devamlılık ekleyerek bunu yapabilirsiniz. Devamlılığın genellikle tarafından gerçekleştirilen işi yapar <xref:System.AsyncCallback> temsilci. Öncül görev tamamlandıktan ve veri arabelleği dolu olduğunda çağrılır. ( <xref:System.IO.FileStream> Nesnesini döndürmeden önce kapatılması.)  
  
 Aşağıdaki örnek nasıl döndürüleceğini gösterir. bir <xref:System.Threading.Tasks.Task> BeginRead/EndRead çiftinin kapsülleyen <xref:System.IO.FileStream> sınıfı.  
  
 [!code-csharp[FromAsync#03](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#03)]
 [!code-vb[FromAsync#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#03)]  
  
 Yöntemi daha sonra aşağıdaki gibi çağrılabilir.  
  
 [!code-csharp[FromAsync#04](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#04)]
 [!code-vb[FromAsync#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#04)]  
  
### <a name="providing-custom-state-data"></a>Özel Durum Verileri Sağlama  
 Tipik <xref:System.IAsyncResult> işlemleri varsa, <xref:System.AsyncCallback> temsilci gerektiren bazı özel durumu verilerini, içinde son parametresinde üzerinden geçirmek zorunda `Begin` yöntemi, böylece verileri halinde paketlenmiş <xref:System.IAsyncResult> sonunda nesne geri çağırma yöntemine geçirilen. Bu genellikle zaman gerekli değildir `FromAsync` yöntemleri kullanılır. Ardından özel veri devama biliniyorsa, doğrudan devamlılık temsilcisi yakalanabilir. Önceki örnekte, aşağıdaki örneğe benzer ancak İnceleme yerine `Result` Öncül özelliği, devamlılık inceler devamlılığın kullanıcı temsilcisine doğrudan erişilebilen özel durumu verileri.  
  
 [!code-csharp[FromAsync#05](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#05)]
 [!code-vb[FromAsync#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#05)]  
  
### <a name="synchronizing-multiple-fromasync-tasks"></a>Birden Çok FromAsync Görevini Eşitleme  
 Statik <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> ve <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> yöntemleri ile birlikte kullanıldığında ek esneklik sağlamak `FromAsync` yöntemleri. Aşağıdaki örnek, birden çok zaman uyumsuz g/ç işlemleri başlatmak ve tüm bunları devamlılığın yürütmeden önce tamamlanması için bekleyin gösterilmektedir.  
  
 [!code-csharp[FromAsync#06](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#06)]
 [!code-vb[FromAsync#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#06)]  
  
### <a name="fromasync-tasks-for-only-the-end-method"></a>Yalnızca End Yöntemi İçin FromAsync Görevleri  
 Bu birkaç durumda için `Begin` yöntemi üçten fazla giriş parametrelerine gereksinim duyar ya da sahip `ref` veya `out` kullanabileceğiniz parametreler `FromAsync` , örneğin, aşırı <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%28System.IAsyncResult%2CSystem.Func%7BSystem.IAsyncResult%2C%600%7D%29?displayProperty=nameWithType>, yalnızca temsileden`End`yöntemi. Bu yöntemler de geçirilen tüm senaryoda kullanılabilir bir <xref:System.IAsyncResult> ve bir görevde yalıtılacak istiyor.  
  
 [!code-csharp[FromAsync#07](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#07)]
 [!code-vb[FromAsync#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#07)]  
  
### <a name="starting-and-canceling-fromasync-tasks"></a>FromAsync Görevlerini Başlatma ve İptal Eme  
 Tarafından döndürülen görev bir `FromAsync` yöntemi WaitingForActivation durumuna sahip ve bir görev oluşturduktan sonra belirli bir noktada sistem tarafından başlatılır. Bu tür bir görev Başlat'ı çağırmak çalışırsanız, bir özel durum oluşturulur.  
  
 İptal edilemez bir `FromAsync` görev temel .NET Framework API'ları şu anda desteklemez dosya iptali sürüyor veya ağ g/ç nedeniyle. İptal işlevi kapsülleyen bir yönteme ekleyebileceğiniz bir `FromAsync` çağrısı, ancak yalnızca yanıtlayabilir iptalden önce için `FromAsync` çağrılan veya sonra (örneğin, bir devamlılık görevi içinde) tamamlandı.  
  
 EAP, örneğin, destekleyen bazı sınıflar <xref:System.Net.WebClient>, iptali desteklemek ve iptal belirteçlerini kullanarak yerel iptal işlevselliği tümleştirebilirsiniz.  
  
## <a name="exposing-complex-eap-operations-as-tasks"></a>Karmaşık EAP İşlemlerini Görev Olarak Ortaya Çıkarma  
 TPL, olay tabanlı zaman uyumsuz bir işlemde aynı yalıtılacak özel olarak tasarlanmış herhangi bir yöntem sağlamaz biçimi `FromAsync` yöntemleri kaydırma ailesi <xref:System.IAsyncResult> deseni. Ancak, TPL sağlamasına <xref:System.Threading.Tasks.TaskCompletionSource%601?displayProperty=nameWithType> herhangi bir rastgele operations kümesi temsil etmek için kullanılan sınıfı bir <xref:System.Threading.Tasks.Task%601>. İşlem zaman uyumlu veya zaman uyumsuz olabilir ve g/ç veya hesaplama bağlantılı ya da her ikisini de olabilir.  
  
 Aşağıdaki örnek nasıl kullanılacağını gösterir. bir <xref:System.Threading.Tasks.TaskCompletionSource%601> zaman uyumsuz bir dizi kullanıma sunmak için <xref:System.Net.WebClient> işlemleri için temel olarak istemci kodu <xref:System.Threading.Tasks.Task%601>. Yöntemi, bir dizi Web URL'leri ve bir terim veya adı aranacak girmenize olanak tanır ve her sitede arama terimi gerçekleşir sayısını döndürür.  
  
 [!code-csharp[FromAsync#10](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/snippet10.cs#10)]
 [!code-vb[FromAsync#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/snippet10.vb#10)]  
  
 Ek özel durum işleme içerir ve istemci kodundan yöntemi çağırma işlemi gösterilmektedir, daha kapsamlı bir örnek için bkz. [nasıl yapılır: Bir görevde EAP desenlerini sarmalama](../../../docs/standard/parallel-programming/how-to-wrap-eap-patterns-in-a-task.md).  
  
 Unutmayın herhangi, görev, tarafından oluşturulan bir <xref:System.Threading.Tasks.TaskCompletionSource%601> bu TaskCompletionSource tarafından başlatılır ve bu nedenle, kullanıcı kodu başlangıç yöntemi bu göreve çağırmamanız gerekir.  
  
## <a name="implementing-the-apm-pattern-by-using-tasks"></a>Görevleri Kullanarak APM Desenini Uygulama  
 Bazı senaryolarda, doğrudan kullanıma sunmak için ilki arzu edilebilir <xref:System.IAsyncResult> başlangıç/bitiş yöntemi çiftleri kullanarak bir API'de deseni. Örneğin, var olan API'leri ile tutarlılık sağlamak isteyebilirsiniz veya bu düzeni gerektiren araçları otomatik. Böyle durumlarda, görevleri APM desenini dahili olarak nasıl uygulandığını basitleştirmek için kullanabilirsiniz.  
  
 Aşağıdaki örnek, bir APM başlangıç/bitiş yöntemi çifti için bir uzun süre çalışan işlem bağlı yöntemi uygulamak için görevleri kullanmayı gösterir.  
  
 [!code-csharp[FromAsync#09](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#09)]
 [!code-vb[FromAsync#09](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#09)]  
  
## <a name="using-the-streamextensions-sample-code"></a>StreamExtensions Örnek Kodunu Kullanma  
 Streamextensions.cs dosya [.NET Framework 4 ile paralel programlama için örnekler](https://code.msdn.microsoft.com/ParExtSamples), görev nesnelerinin için zaman uyumsuz dosya ve ağ g/ç birkaç başvuru uygulamaları içerir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Görev Paralel Kitaplığı (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
