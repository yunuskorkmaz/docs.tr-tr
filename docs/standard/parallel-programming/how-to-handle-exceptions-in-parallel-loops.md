---
title: 'Nasıl yapılır: Paralel Döngülerde Özel Durumları İşleme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel loops, how to handle exceptions
ms.assetid: 512f0d5a-4636-4875-b766-88f20044f143
ms.openlocfilehash: 5d108937e6ab2483cd1633d4b398c1e250f5c098
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77453019"
---
# <a name="how-to-handle-exceptions-in-parallel-loops"></a>Nasıl yapılır: Paralel Döngülerde Özel Durumları İşleme
Ve <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> aşırı yüklemeler, atılabilecek özel durumları işlemek için özel bir mekanizmaya sahip değildir. Bu bakımdan, normal `for` `foreach` ve döngülere benzerler (`For` ve `For Each` Visual Basic'te); işlenmemiş bir özel durum, şu anda çalışan tüm yinelemeler biter bitmez döngünün sonlandırılmasına neden olur.
  
 Paralel döngülere kendi özel durum işleme mantığınızı eklediğinizde, aynı anda birden çok iş parçacığına benzer özel durumların atılabileceği ve bir iş parçacığına atılan özel durumun başka bir özel durum diğerine atılmasına neden olduğu durumu işleme Iş parçacığı. Döngüdeki tüm özel durumları bir <xref:System.AggregateException?displayProperty=nameWithType>'de saran her iki servis vakasını da işleyebilirsiniz. Aşağıdaki örnek, olası bir yaklaşımı gösterir.  
  
> [!NOTE]
> "Yalnızca Kodum" etkinleştirildiğinde, bazı durumlarda Visual Studio özel durumu oluşturan satırda kırılır ve "kullanıcı kodu tarafından işlenmemiş özel durum" yazan bir hata iletisi görüntüler. Bu hata iyi huylu. Devam etmek için F5 tuşuna basabilir ve aşağıdaki örnekte gösterilen özel durum işleme davranışını görebilirsiniz. Visual Studio'nun ilk hatayı kırmasını önlemek **için, Araçlar, Seçenekler, Hata Ayıklama, Genel**altında "Sadece Kodum" onay kutusunun işaretlerini kaldırın.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, tüm özel durumlar yakalanır ve <xref:System.AggregateException?displayProperty=nameWithType> sonra atılan bir sarılır. Arayan, hangi özel durumların işleyeceğini belirleyebilir.  
  
 [!code-csharp[TPL_Exceptions#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#08)]
 [!code-vb[TPL_Exceptions#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionsinloops.vb#08)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Paralelliği](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [PLINQ ve TPL'deki Lambda İfadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
