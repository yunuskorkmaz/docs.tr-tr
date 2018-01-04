---
title: TPL ve Geleneksel .NET Framework Zaman Uyumsuz Programlama
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: tasks, with other asynchronous models
ms.assetid: e7b31170-a156-433f-9f26-b1fc7cd1776f
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 50c4f9cfeb135f1046fbb427585897ca99248afd
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="tpl-and-traditional-net-framework-asynchronous-programming"></a>TPL ve Geleneksel .NET Framework Zaman Uyumsuz Programlama
.NET Framework g/Ç-bağlı ve işlem bağlı zaman uyumsuz işlemleri gerçekleştirmek için aşağıdaki iki standart desenler sağlar:  
  
-   Zaman uyumsuz programlama modeli (içinde zaman uyumsuz işlemleri temsil edilen bir başlangıç/bitiş yöntemleri çifti tarafından gibi APM), <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> ve <xref:System.IO.Stream.EndRead%2A?displayProperty=nameWithType>.  
  
-   İçinde zaman uyumsuz işlemleri temsil adlandırıldığı yöntemi/olay çifti tarafından olay tabanlı zaman uyumsuz desen (EAP) *OperationName*zaman uyumsuz ve *OperationName*tamamlandı, örneğin, <xref:System.Net.WebClient.DownloadStringAsync%2A?displayProperty=nameWithType> ve <xref:System.Net.WebClient.DownloadStringCompleted?displayProperty=nameWithType>. (EAP .NET Framework sürüm 2.0 sunulmuştur.)  
  
 Görev paralel kitaplığı (TPL) ya da zaman uyumsuz desenleri ile birlikte çeşitli şekillerde kullanılabilir. Kitaplık tüketicilere görevleri olarak hem APM hem de EAP işlemleri getirebilir veya APM desenleri kullanıma ancak dahili olarak uygulamak için görev nesneleri kullanın. Görev nesneleri kullanarak her iki senaryolarda kodu basitleştirmek ve aşağıdaki yararlı işlevsellikten yararlanmak:  
  
-   Geri aramalar, görev başlatıldıktan sonra herhangi bir zamanda görev devamlılıklar biçiminde kaydedin.  
  
-   Yanıt olarak yürütülen birden çok işlemlerini koordine bir `Begin_` kullanarak yöntemi <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> ve <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> yöntemleri veya <xref:System.Threading.Tasks.Task.WaitAll%2A> yöntemi veya <xref:System.Threading.Tasks.Task.WaitAny%2A> yöntemi.  
  
-   Zaman uyumsuz g/Ç-bağlı ve işlem bağlı işlemleri aynı görev nesnesindeki kapsüller.  
  
-   Görev nesnenin durumunu izleyin.  
  
-   Bir görev nesnesi için bir işlemin durumunu kullanarak sıralama <xref:System.Threading.Tasks.TaskCompletionSource%601>.  
  
## <a name="wrapping-apm-operations-in-a-task"></a>APM İşlemlerini Bir Görevle Sarma  
 Hem <xref:System.Threading.Tasks.TaskFactory?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.TaskFactory%601?displayProperty=nameWithType> sınıfları sağlayan birçok aşırı <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> olanak tanıyan yöntemler kapsülleyen bir APM başlangıç/bitiş yöntemi çiftinin bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> örneği. Çeşitli aşırı üç giriş parametreleri için sıfır sahip herhangi bir başlangıç/bitiş yöntemi çifti uyum sağlamak.  
  
 Sahip çiftleri için `End` bir değer döndüren yöntemler (`Function` Visual Basic'te), yöntemleri kullanın <xref:System.Threading.Tasks.TaskFactory%601> oluşturan bir <xref:System.Threading.Tasks.Task%601>. İçin `End` void döndüren yöntemler (`Sub` Visual Basic'te), yöntemleri kullanın <xref:System.Threading.Tasks.TaskFactory> oluşturan bir <xref:System.Threading.Tasks.Task>.  
  
 Bu birkaç durumlarda için `Begin` yöntemi üçten fazla parametre yok ya da içeren `ref` veya `out` parametreleri, ek `FromAsync` yalnızca kapsülleyen aşırı `End` yöntemi sağlanır.  
  
 İmza için aşağıdaki örnekte `FromAsync` eşleşen aşırı <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> ve <xref:System.IO.FileStream.EndRead%2A?displayProperty=nameWithType> yöntemleri. Bu aşırı üç giriş parametreleri aşağıdaki gibi alır.  
  
 [!code-csharp[FromAsync#01](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#01)]
 [!code-vb[FromAsync#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#01)]  
  
 İlk parametre bir <xref:System.Func%606> imzası eşleşen temsilci <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> yöntemi. İkinci parametre bir <xref:System.Func%602> geçen temsilci bir <xref:System.IAsyncResult> ve döndüren bir `TResult`. Çünkü <xref:System.IO.FileStream.EndRead%2A> bir tamsayı döndürür, derleyici oluşturur türünü `TResult` olarak <xref:System.Int32> ve görev olarak türünü <xref:System.Threading.Tasks.Task>. Son dört parametre için de aynı <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> yöntemi:  
  
-   Dosya verilerini depolamak üzere arabelleği.  
  
-   Veri yazma başlanan arabellek uzaklığı.  
  
-   Maksimum veri dosyasından okunamıyor.  
  
-   İçin geri geçirmek için kullanıcı tanımlı Durum verilerini depolayan isteğe bağlı bir nesne.  
  
### <a name="using-continuewith-for-the-callback-functionality"></a>Geri Çağırma İşlevi İçin ContinueWith Kullanma  
 Bayt sayısını aksine dosyasındaki verilere erişimi gerekiyorsa <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> yöntemi yeterli değildir. Bunun yerine, kullanın <xref:System.Threading.Tasks.Task>, `Result` özelliği dosya verilerini içerir. Özgün görevi bir devamlılık ekleyerek bunu yapabilirsiniz. Genellikle tarafından gerçekleştirilen iş devamlılığı gerçekleştirir <xref:System.AsyncCallback> temsilci. Antecedent tamamlandığında ve veri arabelleği dolu çağrılır. ( <xref:System.IO.FileStream> Nesne döndürmeden önce kapatılması gerekir.)  
  
 Aşağıdaki örnekte nasıl döndürüleceğini gösterir bir <xref:System.Threading.Tasks.Task> BeginRead/EndRead çifti yalıtır <xref:System.IO.FileStream> sınıfı.  
  
 [!code-csharp[FromAsync#03](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#03)]
 [!code-vb[FromAsync#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#03)]  
  
 Yönteminin ardından, aşağıdaki gibi çağrılabilir.  
  
 [!code-csharp[FromAsync#04](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#04)]
 [!code-vb[FromAsync#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#04)]  
  
### <a name="providing-custom-state-data"></a>Özel Durum Verileri Sağlama  
 Tipik <xref:System.IAsyncResult> işlemleri, varsa, <xref:System.AsyncCallback> temsilci gerektiren bazı özel durumu verileri, içinde son parametre geçirir zorunda `Begin` yöntemi, böylece veriler içine paketlenmiş <xref:System.IAsyncResult> sonunda nesnesi geri çağırma yöntemi geçirildi. Bu genellikle ne zaman gerekli değil `FromAsync` yöntemleri kullanılır. Ardından özel verileri devamlılık biliniyorsa doğrudan devamlılık temsilci yakalanır. Önceki örnekte, aşağıdaki örneğe benzer ancak inceleniyor yerine `Result` özelliği nın devamlılık devamlılık kullanıcı temsilciye doğrudan erişilemez özel durumu verilerini inceler.  
  
 [!code-csharp[FromAsync#05](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#05)]
 [!code-vb[FromAsync#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#05)]  
  
### <a name="synchronizing-multiple-fromasync-tasks"></a>Birden Çok FromAsync Görevini Eşitleme  
 Statik <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> ve <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> yöntemleri ile birlikte kullanıldığında eklenen esneklik sağlamak `FromAsync` yöntemleri. Aşağıdaki örnek, birden çok zaman uyumsuz g/ç işlemleri başlatmak ve bunların tümü devamlılık çalıştırmadan önce tamamlanması için bekleyin gösterilmektedir.  
  
 [!code-csharp[FromAsync#06](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#06)]
 [!code-vb[FromAsync#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#06)]  
  
### <a name="fromasync-tasks-for-only-the-end-method"></a>Yalnızca End Yöntemi İçin FromAsync Görevleri  
 Bu birkaç durumlarda için `Begin` yöntemi üçten fazla giriş parametreleri gerektirir ya da sahip `ref` veya `out` kullanabileceğiniz parametreler `FromAsync` overloads, örneğin, <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%28System.IAsyncResult%2CSystem.Func%7BSystem.IAsyncResult%2C%600%7D%29?displayProperty=nameWithType>, yalnızca temsileden`End`yöntemi. Bu yöntemler de geçirilen herhangi bir senaryoda kullanılabilir bir <xref:System.IAsyncResult> ve bir görevde kapsülleyen istiyor.  
  
 [!code-csharp[FromAsync#07](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#07)]
 [!code-vb[FromAsync#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#07)]  
  
### <a name="starting-and-canceling-fromasync-tasks"></a>FromAsync Görevlerini Başlatma ve İptal Eme  
 Tarafından döndürülen görev bir `FromAsync` yöntemi WaitingForActivation durumuna sahip ve görev oluşturulduktan sonra belirli bir noktada sistem tarafından başlatılır. Bu tür bir görev Başlat çağırmayı denerseniz, bir özel durum oluşturulur.  
  
 İptal edemezsiniz bir `FromAsync` temel .NET Framework API'ları şu anda desteklemediği sürüyor iptal dosyasının veya g/ç ağ çünkü görev. İptal işlevselliğini kapsülleyen bir yönteme ekleyebilirsiniz bir `FromAsync` çağrısı, ancak yalnızca yanıt verebilmesini önce iptali `FromAsync` çağrılan veya sonra (örneğin, bir devamlılık görevi) tamamlandı.  
  
 EAP, örneğin, destekleyen bazı sınıfları <xref:System.Net.WebClient>, iptali desteklemek ve iptal belirteçleri kullanarak yerel iptal işlevselliğini tümleştirebilirsiniz.  
  
## <a name="exposing-complex-eap-operations-as-tasks"></a>Karmaşık EAP İşlemlerini Görev Olarak Ortaya Çıkarma  
 TPL olay tabanlı zaman uyumsuz bir işlem aynı kapsüllemek için özellikle tasarlanmış herhangi bir yöntem sağlamaz biçimi `FromAsync` yöntemleri kaydırma ailesi <xref:System.IAsyncResult> düzeni. Ancak, TPL sağlamak <xref:System.Threading.Tasks.TaskCompletionSource%601?displayProperty=nameWithType> herhangi bir rastgele kümesi işlemlerinin temsil etmek için kullanılan sınıf bir <xref:System.Threading.Tasks.Task%601>. İşlem zaman uyumlu veya zaman uyumsuz olabilir ve g/ç bağlı veya bağlı işlem ya da hem olabilir.  
  
 Aşağıdaki örnekte nasıl kullanılacağını gösteren bir <xref:System.Threading.Tasks.TaskCompletionSource%601> zaman uyumsuz bir dizi kullanıma sunmak için <xref:System.Net.WebClient> işlemleri için temel olarak istemci kodu <xref:System.Threading.Tasks.Task%601>. Yöntem Web URL'leri ve bir terim veya adı aramak için bir dizi girmenizi sağlar ve her sitede arama terimi oluşur sayısını döndürür.  
  
 [!code-csharp[FromAsync#10](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/snippet10.cs#10)]
 [!code-vb[FromAsync#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/snippet10.vb#10)]  
  
 Ek özel durum işleme içerir ve istemci kodundan yöntem çağrısının nasıl gerçekleştireceğini, daha kapsamlı bir örnek için bkz: [nasıl yapılır: bir görevde EAP desenlerini sarmalama](../../../docs/standard/parallel-programming/how-to-wrap-eap-patterns-in-a-task.md).  
  
 Unutmayın herhangi, görev olduğunu tarafından oluşturulan bir <xref:System.Threading.Tasks.TaskCompletionSource%601> bu TaskCompletionSource tarafından başlatılır ve bu nedenle, kullanıcı kodu Start yöntemi bu göreve çağırmalıdır değil.  
  
## <a name="implementing-the-apm-pattern-by-using-tasks"></a>Görevleri Kullanarak APM Desenini Uygulama  
 Bazı senaryolarda, doğrudan kullanıma sunmak için tercih edilebilir <xref:System.IAsyncResult> başlangıç/bitiş yöntemi çiftleri bir API kullanarak düzeni. Örneğin, var olan API'leri ile tutarlılık sağlamak isteyebilirsiniz veya bu deseni gerektiren araçları otomatik. Böyle durumlarda, görevleri, APM düzeni dahili olarak nasıl uygulandığını basitleştirmek için kullanabilirsiniz.  
  
 Aşağıdaki örnek görevleri uzun süre çalışan işlem bağlı yöntemi için bir APM başlangıç/bitiş yöntemi çifti uygulamak için nasıl kullanılacağını gösterir.  
  
 [!code-csharp[FromAsync#09](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#09)]
 [!code-vb[FromAsync#09](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#09)]  
  
## <a name="using-the-streamextensions-sample-code"></a>StreamExtensions Örnek Kodunu Kullanma  
 Streamextensions.cs dosya [paralel programlama ile .NET Framework 4 için örnek](http://go.microsoft.com/fwlink/?LinkID=165717) MSDN Web sitesinde görev nesneleri için zaman uyumsuz dosyasını kullanın ve ağ g/ç çeşitli başvuru uygulamalarını içerir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görev Paralel Kitaplığı (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
