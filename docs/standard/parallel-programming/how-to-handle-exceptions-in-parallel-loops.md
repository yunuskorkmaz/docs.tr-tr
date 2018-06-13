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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 11ba240d71287be91bd0b4b40a2cb69f6e2808d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33580555"
---
# <a name="how-to-handle-exceptions-in-parallel-loops"></a>Nasıl yapılır: Paralel Döngülerde Özel Durumları İşleme
<xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> Ve <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> aşırı durum özel durumları işlemek için herhangi bir özel mekanizma sahip değil. Bu bakımdan, bunlar normal benzer `for` ve `foreach` döngüleri (`For` ve `For Each` Visual Basic'te); işlenmeyen bir özel durum hemen sonlandırmak döngü neden olur.  
  
 Paralel döngüler, hangi benzer birden çok iş parçacığı üzerinde eşzamanlı olarak özel durumlar çalışması ve bir iş parçacığı üzerinde oluşturulan bir özel başka bir durum başka bir özel duruma neden olan durumu işlemek için kendi özel durum işleme mantığı eklediğinizde iş parçacığı. Döngüde tüm özel durumlar kaydırma tarafından her iki durumda işleyebilecek bir <xref:System.AggregateException?displayProperty=nameWithType>. Aşağıdaki örnek, bir olası yaklaşım gösterir.  
  
> [!NOTE]
>  "Sadece kendi kodumu" etkinleştirildiğinde, Visual Studio bazı durumlarda, özel durum oluşturur satır başı ve "özel durum kullanıcı kodu tarafından işlenmiyor." diyen bir hata iletisi görüntülenir Bu hata zararsız kaynaklanır. Buradan devam etmek için F5 tuşuna basın ve aşağıdaki örnekte gösterilen özel durum işleme davranışı bakın. Visual Studio ilk hatada kesilmesini önlemek için yalnızca altında "Sadece kendi kodumu" onay kutusunun işaretini **Araçlar, seçenekleri, hata ayıklama, genel**.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, tüm özel durum yakalandı ve ardından sarmalanmış bir <xref:System.AggregateException?displayProperty=nameWithType> hangi oluşur. Arayan hangi özel durumları işlemek için karar verebilirsiniz.  
  
 [!code-csharp[TPL_Exceptions#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#08)]
 [!code-vb[TPL_Exceptions#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionsinloops.vb#08)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Paralelliği](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [PLINQ ve TPL'deki Lambda İfadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
