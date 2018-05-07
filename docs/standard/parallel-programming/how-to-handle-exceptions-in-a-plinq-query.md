---
title: 'Nasıl yapılır: PLINQ Sorgusunda Özel Durumları İşleme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to handle exceptions
ms.assetid: 8d56ff9b-a571-4d31-b41f-80c0b51b70a5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 162ef3849f025cae9196c2f595634f82cfc782df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-handle-exceptions-in-a-plinq-query"></a>Nasıl yapılır: PLINQ Sorgusunda Özel Durumları İşleme
Bu konudaki ilk örnek nasıl işleneceğini gösterir <xref:System.AggregateException?displayProperty=nameWithType> , durum ile bir PLINQ sorgusu yürütüldüğünde. İkinci örnek try-catch bloklarını temsilciler içinde özel durumun nerede için mümkün olduğunca yakın put gösterilmektedir. Oluşur ve büyük olasılıkla sorgu yürütme devam hemen bu şekilde, siz bunları yakalayabilir. Özel durum oluşturulduktan sonra bazı öğeleri işlemek bir sorgu devam edebilir mümkündür ne zaman özel durumlar oluşturan geri katılma akışa Kabarcık izin verilir.  
  
 Bazı durumlarda PLINQ sıralı yürütme geri döner ve bir özel durum gerçekleştiğinde, özel durum doğrudan yayılan ve sarmalanmış olmayan bir <xref:System.AggregateException>. Ayrıca, <xref:System.Threading.ThreadAbortException>s her zaman yayılır doğrudan.  
  
> [!NOTE]
>  "Sadece kendi kodumu" etkinleştirildiğinde, Visual Studio, özel durum oluşturur satır başı ve "özel durum kullanıcı kodu tarafından işlenmiyor." diyen bir hata iletisi görüntülenir Bu hata zararsız kaynaklanır. Buradan devam etmek için F5 tuşuna basın ve aşağıdaki örneklerde gösterildiği özel durum işleme davranışı bakın. Visual Studio ilk hatada kesilmesini önlemek için yalnızca altında "Sadece kendi kodumu" onay kutusunun işaretini **Araçlar, seçenekleri, hata ayıklama, genel**.  
>   
>  Bu örnek kullanım göstermeye yöneliktir ve eşdeğer sıralı LINQ daha hızlı nesneleri sorguya çalışmayabilir. Speedup hakkında daha fazla bilgi için bkz: [Plınq'te hızlandırmayı anlama](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Örnek  
 Bu örnek herhangi yakalamak üzere Sorguyu yürüten kod geçici try-catch bloklarını put gösterilmektedir <xref:System.AggregateException?displayProperty=nameWithType>oluşturulan s.  
  
 [!code-csharp[PLINQ#41](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#41)]
 [!code-vb[PLINQ#41](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#41)]  
  
 Özel durum oluşturulduktan sonra bu örnekte, sorgu devam edemiyor. Özel durum, uygulama kodunuzun yakalar zamanına göre PLINQ sorgu tüm iş parçacıklarında zaten durduruldu.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir temsilci bir özel durum yakalama ve sorgu yürütmesi ile devam etmek mümkün kılmak için bir try-catch bloğu koymak gösterilmektedir.  
  
 [!code-csharp[PLINQ#42](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#42)]
 [!code-vb[PLINQ#42](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#42)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
-   Derlemek ve bu örnekleri çalıştırmak için bunları PLINQ veri örneği örneği kopyalayın ve Main yöntemini çağırın.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Böylece programınızı durumu bozuk olmayan işlemek nasıl bilmiyorsanız bir özel durum catch değil.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Linq.ParallelEnumerable>  
 [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
