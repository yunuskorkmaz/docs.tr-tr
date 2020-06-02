---
title: 'İzlenecek yol: Veri Akışı Ardışık Düzeni Oluşturma'
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
ms.openlocfilehash: cfe3296815dc344b0d9d1f7bad1ab4a130380e2b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84284617"
---
# <a name="walkthrough-creating-a-dataflow-pipeline"></a>İzlenecek yol: Veri Akışı Ardışık Düzeni Oluşturma
<xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Dataflow.DataflowBlock.TryReceive%2A?displayProperty=nameWithType> Kaynak bloklarında ileti almak için,, ve yöntemlerini kullanabilseniz de, bir *veri akışı işlem hattı*oluşturmak için ileti bloklarını da bağlayabilirsiniz. Veri akışı işlem hattı, her biri daha büyük bir hedefe katkıda bulunan belirli bir görevi gerçekleştiren bir dizi bileşenden veya *veri akışı bloklarıdır*. Bir veri akışı ardışık düzeninde bulunan her veri akışı bloğu, başka bir veri akışı bloğundan bir ileti aldığında iş gerçekleştirir. Buna bir benzerleme vurguladı, otomobil üretimi için bir derleme satırdır. Her bir araç derleme satırından geçtiğinde, bir istasyon çerçeveyi ayrıştırır, bir sonraki altyapı altyapıyı yüklerse ve bu şekilde devam eder. Bir derleme çizgisi birden çok taşıtın aynı anda birleştirilmesini sağladığından, her seferinde bir tane olmak üzere tüm araçlar derlenenden daha iyi bir aktarım hızı sağlar.

 Bu belgede, bir Web sitesinden *Homer 'in* bulunduğu kitabı yükleyen ve metni, ilk sözcüğün karakterlerini tersine çevrilmiş sözcüklerle tek tek sözcüklerle eşleşecek şekilde arayan bir veri akışı işlem hattı gösterilmektedir. Bu belgedeki veri akışı işlem hattının konusu aşağıdaki adımlardan oluşur:  
  
1. Ardışık düzene katılan veri akışı bloklarını oluşturun.  
  
2. Her veri akışı bloğunu ardışık düzendeki bir sonraki bloğa bağlayın. Her blok, işlem hattındaki önceki bloğun çıkışını girdi olarak alır.  
  
3. Her veri akışı bloğu için, önceki blok bittikten sonra sonraki bloğu tamamlandı durumuna ayarlayan bir devam görevi oluşturun.  
  
4. İşlem hattının baş bir yanındaki verileri gönderin.  
  
5. İşlem hattının başını tamamlandı olarak işaretleyin.  
  
6. İşlem hattının tüm işleri tamamlamasını bekleyin.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu yönergeyi başlamadan önce [veri akışını](dataflow-task-parallel-library.md) okuyun.  
  
## <a name="creating-a-console-application"></a>Konsol Uygulaması Oluşturma  
 Visual Studio 'da, Visual C# veya Visual Basic konsol uygulaması projesi oluşturun. System. Threading. Tasks. Dataflow NuGet paketini yükler.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

 Temel uygulamayı oluşturmak için projenize aşağıdaki kodu ekleyin.  
  
 [!code-csharp[TPLDataflow_Palindromes#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#2)]
 [!code-vb[TPLDataflow_Palindromes#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromesemptymain.vb#2)]  
  
## <a name="creating-the-dataflow-blocks"></a>Veri akışı blokları oluşturma  
 İşlem hattına `Main` katılan veri akışı bloklarını oluşturmak için yöntemine aşağıdaki kodu ekleyin. Aşağıdaki tablo, işlem hattının her üyesinin rolünü özetler.  
  
 [!code-csharp[TPLDataflow_Palindromes#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#3)]
 [!code-vb[TPLDataflow_Palindromes#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#3)]  
  
|Üye|Tür|Description|  
|------------|----------|-----------------|  
|`downloadString`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Web 'den kitap metnini indirir.|  
|`createWordList`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Kitap metnini bir sözcük dizisine ayırır.|  
|`filterWordList`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Sözcük dizisinden kısa kelimeleri ve yinelenenleri kaldırır.|  
|`findReversedWords`|<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>|Filtrelenmiş sözcük dizisi koleksiyonundaki tüm kelimeleri, tersi de sözcük dizisinde gerçekleşen tüm sözcükleri bulur.|  
|`printReversedWords`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|Konsola kelimeleri ve karşılık gelen geri doğru sözcükleri görüntüler.|  
  
 Bu örnekteki veri akışı ardışık düzeninde birden çok adımı tek bir adımda birleştirebilseniz de, örnek daha büyük bir görevi gerçekleştirmek için birden çok bağımsız veri akışı görevi oluşturma kavramını gösterir. Örnek, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> işlem hattının her bir üyesini giriş verilerinde bir işlem gerçekleştirmek ve sonuçları ardışık düzen içindeki bir sonraki adıma göndermek için kullanır. `findReversedWords` <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> Her giriş için birden çok bağımsız çıkış oluşturduğundan işlem hattının üyesi bir nesnedir. İşlem hattının kuyruğu, `printReversedWords` <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> girişi üzerinde bir eylem gerçekleştirdiğinden ve sonuç üretmediğinden bir nesnesidir.  
  
## <a name="forming-the-pipeline"></a>İşlem hattını oluşturan  
 Her bloğu ardışık düzendeki bir sonraki bloğa bağlamak için aşağıdaki kodu ekleyin.  
  
 Kaynak veri akışı bloğunu <xref:System.Threading.Tasks.Dataflow.DataflowBlock.LinkTo%2A> hedef veri akışı bloğuna bağlamak için yöntemini çağırdığınızda, veriler kullanılabilir hale geldiğinde kaynak veri akışı bloğu verileri hedef bloğa yayar. Ayrıca <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions> <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions.PropagateCompletion> , true olarak ayarla seçeneğini belirtirseniz, işlem hattındaki bir bloğun başarılı veya başarısız tamamlanması, ardışık düzendeki bir sonraki bloğun tamamlanmasına neden olur.
  
 [!code-csharp[TPLDataflow_Palindromes#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#4)]
 [!code-vb[TPLDataflow_Palindromes#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#4)]  
  
## <a name="posting-data-to-the-pipeline"></a>İşlem hattına veri postalama  
 Veri akışı ardışık düzeninin baş adına *Homer 'nin* bulunduğu kitabın URL 'sini göndermek için aşağıdaki kodu ekleyin.  
  
 [!code-csharp[TPLDataflow_Palindromes#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#6)]
 [!code-vb[TPLDataflow_Palindromes#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#6)]  
  
 Bu örnek, işlem <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A?displayProperty=nameWithType> hattının baş ve zaman uyumlu olarak veri göndermek için kullanır. <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A?displayProperty=nameWithType>Veri akışı düğümüne zaman uyumsuz olarak veri göndermeniz gerektiğinde yöntemini kullanın.  
  
## <a name="completing-pipeline-activity"></a>Ardışık düzen etkinliği Tamamlanıyor  
 İşlem hattının başını tamamlandı olarak işaretlemek için aşağıdaki kodu ekleyin. İşlem hattının kafa, tüm arabellekli iletileri tamamladıktan sonra tamamlanmasını yayar.
  
 [!code-csharp[TPLDataflow_Palindromes#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#7)]
 [!code-vb[TPLDataflow_Palindromes#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#7)]  
  
 Bu örnek, işlenecek veri akışı işlem hattı aracılığıyla bir URL gönderir. Bir işlem hattı aracılığıyla birden fazla girdi gönderirseniz, <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A?displayProperty=nameWithType> Tüm girişi gönderdikten sonra yöntemi çağırın. Uygulamanızın verilerin artık kullanılamadığı bir iyi tanımlanmış noktası yoksa veya uygulamanın işlem hattının bitmesini beklemek zorunda olmaması durumunda bu adımı atlayabilirsiniz.  
  
## <a name="waiting-for-the-pipeline-to-finish"></a>İşlem hattının bitmesi bekleniyor  
 İşlem hattının bitmesini beklemek için aşağıdaki kodu ekleyin. İşlem hattının kuyruğu tamamlandığında genel işlem tamamlanmıştır.  
  
 [!code-csharp[TPLDataflow_Palindromes#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#8)]
 [!code-vb[TPLDataflow_Palindromes#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#8)]  
  
 Aynı anda herhangi bir iş parçacığından veya birden çok iş parçacığından veri akışı tamamlanmasını bekleyebilirsiniz.  
  
## <a name="the-complete-example"></a>Tam Örnek  
 Aşağıdaki örnekte bu izlenecek yol için tüm kod gösterilmektedir.  
  
 [!code-csharp[TPLDataflow_Palindromes#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#1)]
 [!code-vb[TPLDataflow_Palindromes#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#1)]  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bu örnek, veri akışı ardışık düzeninde işlemek için bir URL gönderir. Bir işlem hattı aracılığıyla birden fazla giriş değeri gönderirseniz, uygulamanızın bir otomobil fabrikası aracılığıyla nasıl taşınabileceğine benzer bir paralellik biçimini uygulamanıza ekleyebilirsiniz. İşlem hattının ilk üyesi, sonucunu ikinci üyeye gönderdiğinde, ikinci üye ilk sonucu işlediği için başka bir öğeyi paralel olarak işleyebilir.  
  
 Veri akışı işlem hatları kullanılarak elde edilen paralellik, genellikle daha az, daha büyük görevlerden oluştuğu için *kaba paralellik* olarak bilinir. Ayrıca, bir veri akışı ardışık düzeninde daha *hassas* , kısa süreli görevler de kullanabilirsiniz. Bu örnekte, `findReversedWords` işlem hattının üyesi [PLINQ](introduction-to-plinq.md) kullanarak iş listesinde birden çok öğeyi paralel olarak işleyebilir. Büyük bir işlem hattındaki hassas paralellik kullanımı genel performansı iyileştirebilir.  
  
 Ayrıca bir *veri akışı ağı*oluşturmak için, bir kaynak veri akışı bloğunu birden çok hedef bloğuna bağlayabilirsiniz. Yöntemin aşırı yüklü sürümü, <xref:System.Threading.Tasks.Dataflow.DataflowBlock.LinkTo%2A> <xref:System.Predicate%601> hedef bloğunun, her iletiyi değerine göre kabul edip etmediğini tanımlayan bir nesne alır. Kaynak olarak davranan çoğu veri akışı blok türü, herhangi bir blok iletiyi kabul edene kadar, bağlı oldukları sırada tüm bağlı hedef bloklara iletiler sunar. Bu filtreleme mekanizmasını kullanarak, başka bir yol aracılığıyla bir yol ve diğer veriler aracılığıyla belirli verileri yönlendirerek bağlantılı veri akışı blokları sistemleri oluşturabilirsiniz. Veri akışı ağı oluşturmak için filtreleme kullanan bir örnek için, bkz. [Izlenecek yol: Windows Forms uygulamasında veri akışı kullanma](walkthrough-using-dataflow-in-a-windows-forms-application.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri akışı](dataflow-task-parallel-library.md)
