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
ms.openlocfilehash: 416ed968d9fe2b7149c90fb6d1fa37547db735dc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962505"
---
# <a name="how-to-handle-exceptions-in-a-plinq-query"></a>Nasıl yapılır: PLINQ Sorgusunda Özel Durumları İşleme
Bu konudaki ilk örnek, <xref:System.AggregateException?displayProperty=nameWithType> çalıştırıldığında PLINQ sorgusundan oluşturulabilecek öğesinin nasıl işleneceğini gösterir. İkinci örnek, temsilcilerin içindeki try-catch bloklarının, özel durumun oluştuğu yere mümkün olduğunca yakın şekilde nasıl yerleştirileceğini gösterir. Bu şekilde, bunları gerçekleştikleri anda yakalayabilir ve muhtemelen sorgu yürütmeye devam edebilirsiniz. Özel durumların katılan iş parçacığına balon ekleme yapmasına izin verildiğinde, bir sorgu özel durum oluşturulduktan sonra bazı öğeleri işlemeye devam edebilir.  
  
 PLıNQ, sıralı yürütmeye geri düştüğünde bazı durumlarda özel durum ortaya çıkabilir ve bir <xref:System.AggregateException>özel durum oluşur. Ayrıca, <xref:System.Threading.ThreadAbortException>s her zaman doğrudan yayılır.  
  
> [!NOTE]
> "Yalnızca kendi kodum" etkinleştirildiğinde, Visual Studio özel durumu oluşturan satıra kesilir ve "özel durum Kullanıcı kodu tarafından işlenmiyor" yazan bir hata mesajı görüntüler. Bu hata zararsız. F5 tuşuna basarak bu uygulamadan devam edebilir ve aşağıdaki örneklerde gösterilen özel durum işleme davranışına bakabilirsiniz. Visual Studio 'Nun ilk hatada kesilmesini engellemek için **Araçlar, Seçenekler, hata ayıklama, genel**altında "yalnızca kendi kodum" onay kutusunun işaretini kaldırmanız yeterlidir.  
>   
>  Bu örnek, kullanımı göstermeye yöneliktir ve eşdeğer sıralı LINQ to Objects sorgusundan daha hızlı çalışmayabilir. Hızlı yedekleme hakkında daha fazla bilgi için bkz. [PLıNQ 'Te hızlı hızlandırı anlama](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Örnek  
 Bu örnek, her türlü <xref:System.AggregateException?displayProperty=nameWithType>oluşturulan öğeleri yakalamak için sorguyu yürüten kodun çevresine try-catch bloklarının nasıl yerleştirileceğini gösterir.  
  
 [!code-csharp[PLINQ#41](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#41)]
 [!code-vb[PLINQ#41](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#41)]  
  
 Bu örnekte, özel durum oluşturulduktan sonra sorgu devam edemez. Uygulama kodunuzun özel durumu yakalamasına göre PLıNQ, sorguyu tüm iş parçacıklarında zaten durdurdu.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir özel durum yakalamak ve sorgu yürütmeye devam etmek için bir temsilciye bir try-catch bloğunun nasıl yerleştirileceğini gösterir.  
  
 [!code-csharp[PLINQ#42](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#42)]
 [!code-vb[PLINQ#42](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#42)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
- Bu örnekleri derlemek ve çalıştırmak için onları PLıNQ veri örneği örneğine kopyalayın ve Main 'den yöntemi çağırın.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Programınızın durumunu bozmadığınız için nasıl işleneceğini bilmiyorsanız bir özel durum yakalamayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq.ParallelEnumerable>
- [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
