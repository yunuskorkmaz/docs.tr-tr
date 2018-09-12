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
ms.openlocfilehash: b74e60daced88050413855070c880cd6c1cebfb1
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44514494"
---
# <a name="walkthrough-creating-a-dataflow-pipeline"></a>İzlenecek Yol: Veri Akışı Ardışık Düzeni Oluşturma
Hizmetini kullanıyor olsanız da <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A?displayProperty=nameWithType>, ve <xref:System.Threading.Tasks.Dataflow.DataflowBlock.TryReceive%2A?displayProperty=nameWithType> ileti almak için yöntemler kaynak Bloklar, ileti blokları forma bağlanabilir bir *veri akışı işlem hattı*. Bir veri akışı ardışık düzeni bileşenleri dizisidir veya *veri akışı bloklarının*, her biri, daha büyük bir hedefe katkıda bulunan belirli bir görevi gerçekleştirir. Başka bir veri akışı bloğundan bir ileti aldığında, her veri akışı bloğu veri akışı ardışık düzeninde çalışma gerçekleştirir. Bu bir benzerliği otomobil üretimde montaj ' dir. Her araç montaj hattı geçerken çerçevenin bir istasyondan birleştirir, altyapısı ve benzeri bir yükler. Bir montaj hattı aynı anda birleştirilmeleri birden çok araçları sağladığından, aynı anda tüm araçlar bir birleştirme daha iyi aktarım hızı sağlar.

 Bu belge, kitap indiren bir veri akışı işlem hattı gösterir *Homer Iliad* kelimeler ile eşleştirilecek metin bir Web sitesi ve aramalar ilk sözcüğün karakterleri, ters sözcükleri. Bu belgedeki veri akışı Ardışık düzenin oluşturulması aşağıdaki adımlardan oluşur:  
  
1.  Katılan veri akışı bloklarının, işlem hattı oluşturun.  
  
2.  Her veri akışı bloğu ardışık düzende sonraki bloğu bağlanın. Her blok, işlem hattı, önceki blok çıktısını girdi olarak alır.  
  
3.  Her veri akışı bloğu için önceki blok sonlandırıldıktan sonra sonraki bloğu tamamlanmış duruma ayarlar bir devamlılık görevi oluşturun.  
  
4.  Veri işlem hattının karşılaştırması gönderin.  
  
5.  İşlem hattının baş tamamlandı olarak işaretleyebilirsiniz.  
  
6.  Tüm işi tamamlamak işlem hattı için bekleyin.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Okuma [veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) bu kılavuza başlamadan önce.  
  
## <a name="creating-a-console-application"></a>Bir konsol uygulaması oluşturma  
 Visual Studio'da bir Visual C# veya Visual Basic konsol uygulaması projesi oluşturun. System.Threading.Tasks.Dataflow NuGet paketini yükleyin.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

 Temel uygulama oluşturmak için projenize aşağıdaki kodu ekleyin.  
  
 [!code-csharp[TPLDataflow_Palindromes#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#2)]
 [!code-vb[TPLDataflow_Palindromes#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromesemptymain.vb#2)]  
  
## <a name="creating-the-dataflow-blocks"></a>Veri akışı blokları oluşturma  
 Aşağıdaki kodu ekleyin `Main` katılan veri akışı bloklarının işlem hattı oluşturmak için yöntemi. Aşağıdaki tablo, işlem hattının her üyesinin rol özetler.  
  
 [!code-csharp[TPLDataflow_Palindromes#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#3)]
 [!code-vb[TPLDataflow_Palindromes#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#3)]  
  
|Üye|Tür|Açıklama|  
|------------|----------|-----------------|  
|`downloadString`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Kitap metin, Web'den indirir.|  
|`createWordList`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Kitap metnin bir kelimelerin diziye ayırır.|  
|`filterWordList`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Kısa kelimeler kaldırır ve sözcük dizisinden çoğaltır.|  
|`findReversedWords`|<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>|Geriye doğru sözcük dizide da oluşur. filtrelenmiş sözcük dizisi koleksiyondaki tüm sözcükleri bulur.|  
|`printReversedWords`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|Sözcükleri ve karşılık gelen ters sözcükleri konsolda görüntüler.|  
  
 Bu örnekte veri akışı ardışık düzende birden çok adımlar bir adım birleştirebiliyordunuz ancak örnek daha büyük bir görevi gerçekleştirmek için birden çok bağımsız veri akışı görevleri oluşturma kavramı gösterir. Örnekte <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> kendi girdi verilerini bir işlem gerçekleştirmek ve sonuçları sonraki adım işlem hattında göndermek işlem hattı her üyesi etkinleştirmek için. `findReversedWords` İşlem hattı üyesi olan bir <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> her bir giriş için birden çok bağımsız çıkış ürettiği için nesne. İşlem hattı kuyruğu `printReversedWords`, olan bir <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> hücredeki girişe göre bir eylem gerçekleştiren ve bir sonuç üretmez çünkü nesne.  
  
## <a name="forming-the-pipeline"></a>İşlem hattı oluşturma  
 Ardışık düzende sonraki bloğu her blok bağlanmak için aşağıdaki kodu ekleyin.  
  
 Çağırdığınızda <xref:System.Threading.Tasks.Dataflow.DataflowBlock.LinkTo%2A> yöntemi bir kaynak veri akışı bloğu bir hedef veri akışı bloğu kaynak veri akışı bloğu bağlanmak için hedef blok için veri veri kullanılabilir olduğunda yayar. Ayrıca sağlarsanız <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions> ile <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions.PropagateCompletion> true, başarılı veya başarısız tamamlanmasıyla işlem hattındaki bir blok kümesine işlem hattında sonraki bloğun tamamlanma neden olur.
  
 [!code-csharp[TPLDataflow_Palindromes#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#4)]
 [!code-vb[TPLDataflow_Palindromes#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#4)]  
  
## <a name="posting-data-to-the-pipeline"></a>Veri işlem hattı için gönderme  
 Kitap URL'sini göndermek için aşağıdaki kodu ekleyin *Homer Iliad* veri akışı Ardışık düzenin karşılaştırması.  
  
 [!code-csharp[TPLDataflow_Palindromes#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#6)]
 [!code-vb[TPLDataflow_Palindromes#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#6)]  
  
 Bu örnekte <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A?displayProperty=nameWithType> eşzamanlı olarak veri işlem hattı başı göndermek için. Kullanım <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A?displayProperty=nameWithType> yöntemi zaman uyumsuz olarak bir veri akışı düğüme veri göndermesi gerekir.  
  
## <a name="completing-pipeline-activity"></a>İşlem hattı etkinliği Tamamlanıyor  
 İşlem hattının baş tamamlandı olarak işaretlemek için aşağıdaki kodu ekleyin. Arabelleğe alınan tüm iletileri işlediğinden sonra işlem hattını Başkanı tamamlanmasını yayar.
  
 [!code-csharp[TPLDataflow_Palindromes#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#7)]
 [!code-vb[TPLDataflow_Palindromes#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#7)]  
  
 Bu örnekte, işlenmek üzere bir URL veri akışı işlem hattı aracılığıyla gönderilir. Bir işlem hattı aracılığıyla birden fazla giriş gönderirseniz, çağrı <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A?displayProperty=nameWithType> tüm girişler gönderdikten sonra yöntemi. Uygulamanızın veri artık kullanılabilir olduğu iyi tanımlanmış hiçbir noktası varsa veya uygulama, işlem hattının son beklemek zorunda değildir, bu adımı atlayabilirsiniz.  
  
## <a name="waiting-for-the-pipeline-to-finish"></a>İşlem hattı bitirilmesi bekleniyor  
 İşlem hattının son beklemek için aşağıdaki kodu ekleyin. İşlem hattı kuyruğu tamamlandığında genel işlemi tamamlandı.  
  
 [!code-csharp[TPLDataflow_Palindromes#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#8)]
 [!code-vb[TPLDataflow_Palindromes#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#8)]  
  
 Veri akışı tamamlama herhangi bir iş parçacığı veya birden çok iş parçacığı aynı anda bekleyebilirsiniz.  
  
## <a name="the-complete-example"></a>Tam Örnek  
 Aşağıdaki örnek, bu izlenecek yol için tam kod gösterilmektedir.  
  
 [!code-csharp[TPLDataflow_Palindromes#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#1)]
 [!code-vb[TPLDataflow_Palindromes#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#1)]  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bu örnekte veri akışı ardışık düzende işlemek için bir URL gönderir. Bir işlem hattı aracılığıyla birden fazla giriş değeri gönderirseniz, uygulamanıza nasıl bölümleri otomobil bir Fabrika taşınmasını gerektirecek benzer bir form paralellik derecesi ortaya çıkarabilir. Ardışık düzenin ilk üye ikinci bir üyesine sonucunu gönderdiğinde, ikinci üyenin ilk sonuç işlediği gibi başka bir öğe paralel işleyebilir.  
  
 Veri akışı ardışık düzenleri kullanarak elde edebilirsiniz paralelliği olarak da bilinen *büyük parçalı paralellik* genellikle daha az sayıda, daha büyük görevler oluştuğundan. Daha da kullanabilirsiniz *hassas paralellik* daha küçük, kısa süreli görev bir veri akışı ardışık. Bu örnekte, `findReversedWords` işlem hattının üyeyi kullanan [PLINQ](parallel-linq-plinq.md) paralel çalışma listesinde birden çok öğe işlenecek. Parçalı bir işlem hattındaki hassas paralellik kullanımını genel performansını artırabilir.  
  
 Bir kaynak veri akışı bloğu oluşturmak için birden çok hedef bloğa bağlanabilir bir *veri akışı ağ*. Aşırı yüklenmiş sürümüne <xref:System.Threading.Tasks.Dataflow.DataflowBlock.LinkTo%2A> yöntemi bir <xref:System.Predicate%601> hedef blok, değerini temel alarak her iletiyi kabul edip etmeyeceğini tanımlayan nesne. Sırayla bloklarından bu iletiyi kabul edene kadar bunlar, bağlı tüm bağlı hedef bloklarına iletiler kaynakları sunan gibi davranacak çoğu veri akışı bloğu türleri. Bu filtreleme mekanizması kullanarak, belirli bir yol verilerine ve diğer verileri başka bir yol aracılığıyla doğrudan bağlanmış veri akışı bloğu sistemleri oluşturabilirsiniz. Bir veri akışı ağı oluşturmak için filtreleme kullanan bir örnek için bkz: [izlenecek yol: veri akışı kullanarak bir Windows Forms uygulamasındaki](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
