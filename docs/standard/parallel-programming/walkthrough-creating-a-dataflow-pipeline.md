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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e55d902971c5cea64cf14458f09e58fb47e2d0aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-creating-a-dataflow-pipeline"></a>İzlenecek Yol: Veri Akışı Ardışık Düzeni Oluşturma
Kullanabilirsiniz ancak <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A?displayProperty=nameWithType>, ve <xref:System.Threading.Tasks.Dataflow.DataflowBlock.TryReceive%2A?displayProperty=nameWithType> ileti almak için yöntemleri kaynak blokları, ileti blokları forma bağlanabilir bir *veri akışı ardışık düzenleri*. Bir veri akışı ardışık düzeni bileşenleri dizisidir veya *veri akışı blokları*, her biri daha büyük bir hedefe katkıda bulunan belirli bir görevi gerçekleştirir. Başka bir veri akışı bloğundan bir ileti aldığında, her bir veri akışı ardışık düzen veri akışı bloğunda çalışma gerçekleştirir. Benzetme bu otomobil üretim için bir derleme satırdır. Her araç derleme satırın geçerken bir istasyon çerçeve derler, bir sonraki altyapısı vb. yükler. Bir derleme satırı aynı anda birleştirilen birden çok taşıtlardan sağladığından, aynı anda tam taşıtlardan bir birleştirme daha iyi verimlilik sağlar.

 Bu belge rehberini yükler veri akışı ardışık gösterir *Homer Iliad* olan ayrı sözcükleri eşleştirmeye metin bir Web sitesi ve aramaları ilk word'ün karakterleri bu ters sözcükleri. Bu belgedeki veri akışı ardışık oluşturulması aşağıdaki adımlardan oluşur:  
  
1.  Katılmak veri akışı blokları ardışık düzeninde oluşturun.  
  
2.  Her veri akışı bloğu ardışık düzende sonraki bloğu bağlayın. Her bloğu giriş olarak önceki blok çıktısı ardışık düzeninde alır.  
  
3.  Her veri akışı bloğu için önceki blok bittikten sonra sonraki bloğu tamamlandı durumuna ayarlar devamlılık görevi oluşturun.  
  
4.  Ardışık Düzen head veri göndermek.  
  
5.  Ardışık Düzen head tamamlandı olarak işaretle.  
  
6.  Tüm iş tamamlamak ardışık düzeni için bekleyin.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Okuma [veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) bu kılavuza başlamadan önce.  
  
## <a name="creating-a-console-application"></a>Bir konsol uygulaması oluşturma  
 Visual Studio'da bir Visual C# veya Visual Basic konsol uygulama projesi oluşturun. System.Threading.Tasks.Dataflow NuGet paketini yükleyin.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

 Aşağıdaki kodu temel uygulaması oluşturmak için projenize ekleyin.  
  
 [!code-csharp[TPLDataflow_Palindromes#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#2)]
 [!code-vb[TPLDataflow_Palindromes#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromesemptymain.vb#2)]  
  
## <a name="creating-the-dataflow-blocks"></a>Veri akışı blokları oluşturma  
 Aşağıdaki kodu ekleyin `Main` ardışık düzeninde katılmak veri akışı blokları oluşturma yöntemi. Aşağıdaki tabloda ardışık her üyesinin rolü özetlenmektedir.  
  
 [!code-csharp[TPLDataflow_Palindromes#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#3)]
 [!code-vb[TPLDataflow_Palindromes#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#3)]  
  
|Üye|Tür|Açıklama|  
|------------|----------|-----------------|  
|`downloadString`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Kitap metin Web sunucusundan indirir.|  
|`createWordList`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Kitap metin sözcük bir diziye ayırır.|  
|`filterWordList`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Kısa sözcükler kaldırır ve word diziden çoğaltır.|  
|`findReversedWords`|<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>|Geriye doğru da word dizisinde oluşur filtrelenmiş word dizi koleksiyondaki tüm sözcükleri bulur.|  
|`printReversedWords`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|Sözcükler ve karşılık gelen ters sözcükler konsola görüntüler.|  
  
 Bu örnekte veri akışı ardışık düzende birden çok adımı tek bir adımda içine birleştirebilir rağmen daha büyük bir görevi gerçekleştirmek için birden çok bağımsız veri akışı görev oluşturma kavramı örnek gösterilmektedir. Örnek kullanır <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> kendi giriş verilerini üzerinde bir işlemi gerçekleştirmek ve sonuçları sonraki adım ardışık düzeninde göndermek her üye ardışık etkinleştirmek için. `findReversedWords` Ardışık düzen üyesi olan bir <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> her giriş için birden çok bağımsız çıkış oluşturduğundan nesne. Ardışık Düzen kuyruğu `printReversedWords`, olan bir <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> kendi giriş, bir eylem gerçekleştirir ve bir sonuç üretmez çünkü nesne.  
  
## <a name="forming-the-pipeline"></a>Ardışık Düzen oluşturuluyor  
 Ardışık düzende sonraki bloğu blokların bağlanmak için aşağıdaki kodu ekleyin.  
  
 Çağırdığınızda <xref:System.Threading.Tasks.Dataflow.DataflowBlock.LinkTo%2A> yöntemi bir kaynak veri akışı bloğu bir hedef veri akışı blok kaynak veri akışı bloğu bağlanmak için hedef blok veri veri olarak kullanılabilir hale geldiğinde yayar. Ayrıca sağlarsanız, <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions> ile <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions.PropagateCompletion> ardışık düzeninde bir blok true, başarılı veya başarısız tamamlanmasından kümesine ardışık düzeninde sonraki bloğu tamamlanmasından neden olur.
  
 [!code-csharp[TPLDataflow_Palindromes#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#4)]
 [!code-vb[TPLDataflow_Palindromes#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#4)]  
  
## <a name="posting-data-to-the-pipeline"></a>Veri ardışık düzenine gönderme  
 Kitap URL'sini göndermek için aşağıdaki kodu ekleyin *Homer Iliad* veri akışı ardışık head için.  
  
 [!code-csharp[TPLDataflow_Palindromes#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#6)]
 [!code-vb[TPLDataflow_Palindromes#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#6)]  
  
 Bu örnekte <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A?displayProperty=nameWithType> ardışık düzen head için eş zamanlı olarak veri göndermek için. Kullanım <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A?displayProperty=nameWithType> yöntemi zaman uyumsuz olarak bir veri akışı düğüme veri göndermeniz gerekir.  
  
## <a name="completing-pipeline-activity"></a>Ardışık Düzen etkinlik Tamamlanıyor  
 Ardışık Düzen head tamamlandı olarak işaretlemek için aşağıdaki kodu ekleyin. Tüm arabelleğe alınan iletileri işledikten sonra ardışık head kendi tamamlama yayar.
  
 [!code-csharp[TPLDataflow_Palindromes#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#7)]
 [!code-vb[TPLDataflow_Palindromes#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#7)]  
  
 Bu örnekte, işlenmek üzere bir URL veri akışı ardışık düzeni aracılığıyla gönderilir. Birden fazla girişi bir ardışık düzen üzerinden gönderirseniz, çağrı <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A?displayProperty=nameWithType> tüm giriş gönderdikten sonra yöntemi. Uygulamanızın veri artık kullanılabilir olduğu iyi tanımlanmış noktası yok veya uygulama ardışık bitmesini bekleyin yok varsa bu adımı atlayabilirsiniz.  
  
## <a name="waiting-for-the-pipeline-to-finish"></a>Ardışık düzeni için bitiş bekleniyor  
 Ardışık bitmesini beklemek için aşağıdaki kodu ekleyin. Ardışık Düzen kuyruğu tamamlandığında ve genel işlemi tamamlandı.  
  
 [!code-csharp[TPLDataflow_Palindromes#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#8)]
 [!code-vb[TPLDataflow_Palindromes#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#8)]  
  
 Veri akışı tamamlanma hiçbir iş parçacığı veya birden çok iş parçacığı aynı anda bekleyebilirsiniz.  
  
## <a name="the-complete-example"></a>Tam Örnek  
 Aşağıdaki örnek, bu kılavuz tam kod gösterilir.  
  
 [!code-csharp[TPLDataflow_Palindromes#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#1)]
 [!code-vb[TPLDataflow_Palindromes#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#1)]  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bu örnek veri akışı ardışık düzen üzerinden işlemek için bir URL gönderir. Birden fazla giriş değeri bir ardışık düzeninden gönderirseniz, uygulamanıza bölümleri bir otomobil Fabrika nasıl hareket benzer bir form paralellik ortaya çıkarabilir. Ardışık düzenin ilk üye ikinci üye sonucu gönderdiğinde, ikinci üye ilk sonucu işlerken paralel başka bir öğe işleyebilir.  
  
 Veri akışı ardışık düzenleri kullanılarak elde edilir paralellik olarak bilinen *parçalı paralellik* genellikle daha az sayıda, daha büyük görevlerin oluştuğundan. Daha da kullanabilirsiniz *hassas paralellik* veri akışı ardışık düzeninde daha küçük, kısa süreli görevlerin. Bu örnekte, `findReversedWords` ardışık üyeyi kullanan [PLINQ](parallel-linq-plinq.md) paralel iş listesinde birden çok öğe işleyemedi. Parçalı ardışık düzeninde hassas paralellik kullanımını, genel üretilen işi artırabilir.  
  
 Kaynak veri akışı bloğu oluşturmak için birden çok hedef bloklarına bağlanabilir bir *veri akışı ağ*. Aşırı yüklü sürümünü <xref:System.Threading.Tasks.Dataflow.DataflowBlock.LinkTo%2A> metodu bir <xref:System.Predicate%601> hedef blok kendi değere göre her ileti kabul edip etmeyeceğini tanımlayan nesne. Kaynakları blokları biri bu iletiyi kabul edene kadar bunlar, bağlanmış sırayla tüm bağlı hedef blokları iletileri sunmak gibi davranacak çoğu veri akışı bloğu türleri. Bu filtreleme mekanizması kullanarak, belirli bir yol verilerine ve diğer verileri başka bir yol üzerinden doğrudan bağlı veri akışı blokları sistemlerinin oluşturabilirsiniz. Bir veri akışı ağ oluşturmak için filtreleme kullanan bir örnek için bkz: [izlenecek yol: veri akışı kullanarak bir Windows Forms uygulamasında](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
