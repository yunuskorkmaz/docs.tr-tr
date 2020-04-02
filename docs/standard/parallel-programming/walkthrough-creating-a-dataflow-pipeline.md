---
title: 'İzlenecek Yol: Veri Akışı Ardışık Düzeni Oluşturma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dataflow pipelines, creating with TPL
- Task Parallel Library, dataflows
- TPL dataflow library, creating dataflow pipeline
ms.assetid: 69308f82-aa22-4ac5-833d-e748533b58e8
ms.openlocfilehash: 339365381b1fa2c777cead3c75bfe783f7af800e
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588284"
---
# <a name="walkthrough-creating-a-dataflow-pipeline"></a>İzlenecek Yol: Veri Akışı Ardışık Düzeni Oluşturma
Kaynak bloklardan <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A?displayProperty=nameWithType>ileti <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A?displayProperty=nameWithType>almak <xref:System.Threading.Tasks.Dataflow.DataflowBlock.TryReceive%2A?displayProperty=nameWithType> için , ve yöntemleri kullanabiliyor olsada, ileti bloklarını *da bir veri akışı ardışık alanı*oluşturmak için bağlayabilirsiniz. Veri akışı ardışık bir dizi bileşen veya *veri akışı blokları,* her biri daha büyük bir hedefe katkıda bulunan belirli bir görev gerçekleştirir. Veri akışı ardışık bir veri akışı bloğundaki her veri akışı bloğu, başka bir veri akışı bloğundan ileti aldığında işi gerçekleştirir. Buna benzetme otomobil üretimi için bir montaj hattıdır. Her araç montaj hattından geçerken, bir istasyon çerçeveyi monte eder, bir sonraki motor ayükler, ve saire. Montaj hattı birden fazla aracın aynı anda monte edilmesini sağladığından, tüm araçların birer birer monte edilmesinden daha iyi iş elde edilmesini sağlar.

 Bu belge, *Homer'ın İlilia* kitabını bir web sitesinden indiren ve metni tek tek sözcükleri ilk sözcüğün karakterlerini tersine çeviren sözcüklerle eşleştirmek için arayan bir veri akışı ardışık hattını gösterir. Bu belgede veri akışı ardışık düzeninin oluşturulması aşağıdaki adımlardan oluşur:  
  
1. Ardışık akatoya katılan veri akışı bloklarını oluşturun.  
  
2. Her veri akışı bloğunu ardışık ardışık alandaki bir sonraki bloya bağlayın. Her blok, ardışık ardışık ardışık alan önceki bloğun çıktısını girdi olarak alır.  
  
3. Her veri akışı bloğu için, önceki blok tamamlandıktan sonra tamamlanan duruma sonraki bloğu ayarlayan bir devam görevi oluşturun.  
  
4. Veri boru hattının başına gönderin.  
  
5. Boru hattının başını tamamlanmış olarak işaretleyin.  
  
6. Boru hattının tüm işleri tamamlamasını bekleyin.  
  
## <a name="prerequisites"></a>Ön koşullar  
 Bu izbiyi başlatmadan önce [Veri Akışı'nı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) okuyun.  
  
## <a name="creating-a-console-application"></a>Konsol Uygulaması Oluşturma  
 Visual Studio'da Visual C# veya Visual Basic Console Application projesi oluşturun. System.Threading.Tasks.Dataflow NuGet paketini yükleyin.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

 Temel uygulamayı oluşturmak için projenize aşağıdaki kodu ekleyin.  
  
 [!code-csharp[TPLDataflow_Palindromes#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#2)]
 [!code-vb[TPLDataflow_Palindromes#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromesemptymain.vb#2)]  
  
## <a name="creating-the-dataflow-blocks"></a>Veri Akışı Bloklarını Oluşturma  
 Ardışık yapıya `Main` katılan veri akışı blokları oluşturmak için yönteme aşağıdaki kodu ekleyin. Aşağıdaki tablo, ardışık hattın her üyesinin rolünü özetler.  
  
 [!code-csharp[TPLDataflow_Palindromes#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#3)]
 [!code-vb[TPLDataflow_Palindromes#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#3)]  
  
|Üye|Tür|Açıklama|  
|------------|----------|-----------------|  
|`downloadString`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Kitap metnini Web'den indirir.|  
|`createWordList`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Kitap metnini bir dizi sözcük olarak ayırır.|  
|`filterWordList`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Sözcük dizisinden kısa sözcükleri ve yinelenenleri kaldırır.|  
|`findReversedWords`|<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>|Terssözcüğü sözcük dizisinde de yer alan filtre uygulanmış sözcük dizisi koleksiyonundaki tüm sözcükleri bulur.|  
|`printReversedWords`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|Sözcükleri ve karşılık gelen ters sözcükleri konsola görüntüler.|  
  
 Bu örnekte veri akışı ardışık ardışık birden çok adımı tek bir adımda birleştirebilseniz de, örnek, daha büyük bir görevi gerçekleştirmek için birden çok bağımsız veri akışı görevi oluşturma kavramını göstermektedir. Örnek, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> ardışık her üyenin giriş verilerinde bir işlem gerçekleştirmesini ve sonuçları ardışık ardışık işlemdeki bir sonraki adıma göndermesini sağlamak için kullanılır. Her `findReversedWords` giriş için birden <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> çok bağımsız çıkış ürettiği için ardışık hattın üyesi bir nesnedir. Boru hattının kuyruğu, `printReversedWords`girdisi üzerinde bir eylem gerçekleştirdiği ve bir sonuç oluşturmadığı için bir <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> nesnedir.  
  
## <a name="forming-the-pipeline"></a>Boru Hattının Oluşturulması  
 Her bloğu ardışık ardışık alandaki bir sonraki bloya bağlamak için aşağıdaki kodu ekleyin.  
  
 Bir kaynak <xref:System.Threading.Tasks.Dataflow.DataflowBlock.LinkTo%2A> veri akışı bloğunu hedef veri akışı bloğuna bağlama yöntemini çağırdığınızda, kaynak veri akışı bloğu veri kullanılabilir hale geldikçe verileri hedef bloya yalar. Ayrıca, ardışık hatlar bir blok doğru, başarılı veya başarısız tamamlanması ayarlanmış sağlarsanız, <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions> ardışık bir sonraki blok tamamlanmasına neden olacaktır. <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions.PropagateCompletion>
  
 [!code-csharp[TPLDataflow_Palindromes#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#4)]
 [!code-vb[TPLDataflow_Palindromes#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#4)]  
  
## <a name="posting-data-to-the-pipeline"></a>Veri Boru Hattına Gönderme  
 Veri akışı boru hattının başına *Homer Iliad* kitabının URL'sini göndermek için aşağıdaki kodu ekleyin.  
  
 [!code-csharp[TPLDataflow_Palindromes#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#6)]
 [!code-vb[TPLDataflow_Palindromes#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#6)]  
  
 Bu örnek, ardışık hattın başına eşzamanlı olarak veri göndermek için kullanılır. <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A?displayProperty=nameWithType> Veri <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A?displayProperty=nameWithType> akışı düğümüne eş senkronize bir şekilde göndermeniz gerektiğinde yöntemi kullanın.  
  
## <a name="completing-pipeline-activity"></a>Boru Hattı Faaliyetinin Tamamlanması  
 Tamamlanan ardışık ardışık başlığı işaretlemek için aşağıdaki kodu ekleyin. Boru hattının başı, tüm arabelleğe alınan iletileri işledikten sonra tamamlanmasını yayar.
  
 [!code-csharp[TPLDataflow_Palindromes#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#7)]
 [!code-vb[TPLDataflow_Palindromes#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#7)]  
  
 Bu örnek, işlenecek veri akışı ardışık ardışık aracılığıyla bir URL gönderir. Bir ardışık sistem aracılığıyla birden fazla giriş <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A?displayProperty=nameWithType> gönderirseniz, tüm girişi gönderdikten sonra yöntemi arayın. Uygulamanızın verilerin artık kullanılamadığı iyi tanımlanmış bir noktası yoksa veya uygulamanın ardışık noktanın tamamlanmasını beklemesi gerekmiyorsa bu adımı atlayabilirsiniz.  
  
## <a name="waiting-for-the-pipeline-to-finish"></a>Boru Hattının Bitmesini Bekliyor  
 Ardışık nedenin bitmesini beklemek için aşağıdaki kodu ekleyin. Boru hattının kuyruğu bittiğinde genel işlem tamamlanır.  
  
 [!code-csharp[TPLDataflow_Palindromes#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#8)]
 [!code-vb[TPLDataflow_Palindromes#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#8)]  
  
 Herhangi bir iş parçacığından veya aynı anda birden çok iş parçacığından veri akışının tamamlanmasını bekleyebilirsiniz.  
  
## <a name="the-complete-example"></a>Tam Örnek  
 Aşağıdaki örnek, bu izbin tam kodunu gösterir.  
  
 [!code-csharp[TPLDataflow_Palindromes#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#1)]
 [!code-vb[TPLDataflow_Palindromes#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#1)]  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bu örnek, veri akışı ardışık aracılığıyla işlemek için bir URL gönderir. Bir boru hattı üzerinden birden fazla giriş değeri gönderirseniz, uygulamanıza parçaların bir otomobil fabrikasında nasıl hareket edebileceğini andıran bir paralellik biçimi getirebilirsiniz. Ardışık işlemin ilk üyesi sonucunu ikinci üyeye gönderdiğinde, ikinci üye ilk sonucu işlerken başka bir öğeyi paralel olarak işleyebilir.  
  
 Veri akışı ardışık lıkları kullanılarak elde edilen paralellik kaba *taneli paralellik* olarak bilinir, çünkü genellikle daha az, daha büyük görevlerden oluşur. Ayrıca, veri akışı ardışık bir işlem de küçük, kısa çalışan görevlerin daha *ince taneli paralellikkk.* Bu örnekte, `findReversedWords` ardışık yapının üyesi, çalışma listesindeki birden çok öğeyi paralel olarak işlemek için [PLINQ](introduction-to-plinq.md) kullanır. Kaba taneli bir boru hattında ince taneli paralellik kullanımı genel iş ortalığını artırabilir.  
  
 Ayrıca, *veri akışı ağı*oluşturmak için bir kaynak veri akışı bloğunu birden çok hedef bloğuna bağlayabilirsiniz. <xref:System.Threading.Tasks.Dataflow.DataflowBlock.LinkTo%2A> Yöntemin aşırı yüklenen sürümü, <xref:System.Predicate%601> hedef bloğun her iletiyi değerine göre kabul edip etmediğini tanımlayan bir nesne alır. Kaynak olarak hareket eden çoğu veri akışı bloğu türü, bloklardan biri bu iletiyi kabul edene kadar bağlı hedef bloklara bağlı oldukları sırada ileti sunar. Bu filtreleme mekanizmasını kullanarak, belirli verileri bir yol ve diğer veriler üzerinden başka bir yol üzerinden yönlendiren bağlı veri akışı blokları sistemleri oluşturabilirsiniz. Veri akışı ağı oluşturmak için filtreleme kullanan [bir](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md)örnek için bkz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
