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
ms.openlocfilehash: 4b1a72a2b2443b419ea4f4b036664fb5f8932096
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638336"
---
# <a name="how-to-handle-exceptions-in-a-plinq-query"></a>Nasıl yapılır: PLINQ Sorgusunda Özel Durumları İşleme
Bu konudaki ilk örnek nasıl işleneceğini gösterir <xref:System.AggregateException?displayProperty=nameWithType> , durum konumundan bir PLINQ sorgusu yürütüldüğünde. İkinci örnek, try-catch bloklarını temsilciler içinde özel durumun olduğu için mümkün olduğunca yakın yerleştirin gösterilmektedir. Oluşur ve büyük olasılıkla sorgu yürütmeye devam et hemen sonra bu şekilde, siz bunları yakalayabilir. Ne zaman bir sorgu özel durum oluştuktan sonra bazı öğeleri işlemeye devam edebilir mümkündür özel durumları ayarlama geri katılan iş parçacığına Kabarcık halinde çıkmasına izin verilmez.  
  
 Bazı durumlarda PLINQ sıralı yürütme için geri döner ve özel bir durum oluştuğunda, özel durum doğrudan yayılır ve sarmalanmış değil bir <xref:System.AggregateException>. Ayrıca, <xref:System.Threading.ThreadAbortException>s her zaman yayılır doğrudan.  
  
> [!NOTE]
>  "Yalnızca kendi kodum" etkin olduğunda, Visual Studio özel durum oluşturan satırda bölme ve "özel durum kullanıcı kodu tarafından işlenmemiş." diyen bir hata iletisini görüntüler Bu hata zararsızdır. Buradan devam etmek için F5 tuşuna basın ve aşağıdaki örneklerde gösterilen özel durum işleme davranışını bakın. Visual Studio'nun çalışmasının ilk hatada kesilmesini önlemek için yalnızca "Yalnızca kendi kodum" onay kutusunun işaretini kaldırın **Araçlar, Seçenekler, hata ayıklama, genel**.  
>   
>  Bu örnek, kullanımını göstermek için tasarlanmıştır ve nesneleri sorgu için eşdeğer sıralı LINQ daha hızlı çalışmayabilir. Hızlandırmayı hakkında daha fazla bilgi için bkz: [plınq'te hızlandırmayı anlama](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Örnek  
 Bu örnek nasıl herhangi yakalamak için sorgu yürütülen kod etrafında try-catch blokları yerleştirin gösterir <xref:System.AggregateException?displayProperty=nameWithType>oluşturulan s.  
  
 [!code-csharp[PLINQ#41](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#41)]
 [!code-vb[PLINQ#41](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#41)]  
  
 Bu örnekte, özel durum oluştuktan sonra sorgu devam edemiyor. Zaman uygulama kodunuzun özel durumu yakalar, PLINQ sorguyu tüm iş parçacıkları üzerinde zaten durduruldu.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir özel durum yakalamak ve sorgu yürütme ile devam etmek mümkün kılmak için bir temsilci bir try-catch bloğu koymak gösterilmektedir.  
  
 [!code-csharp[PLINQ#42](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#42)]
 [!code-vb[PLINQ#42](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#42)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
- Derleme ve bu örnekleri çalıştırmak için bunları PLINQ veri örneği örneği kopyalayın ve Main yöntemini çağırın.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Programınızın durumunu bozmadığından emin, ne yapılacağını bilmediği sürece bir özel durum yakalamayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq.ParallelEnumerable>
- [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
