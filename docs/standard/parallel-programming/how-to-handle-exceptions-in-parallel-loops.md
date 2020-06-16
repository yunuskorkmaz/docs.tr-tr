---
title: 'Nasıl yapılır: Paralel Döngülerde Özel Durumları İşleme'
description: .NET 'teki paralel Döngülerde özel durumları nasıl işleyeceğinizi öğrenin. Bir System. AggregateException içindeki döngüden tüm özel durumların nasıl sarılacağını gösteren bir örnek görürsünüz.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel loops, how to handle exceptions
ms.assetid: 512f0d5a-4636-4875-b766-88f20044f143
ms.openlocfilehash: 61c22d6e82282f8aeb54818c813d4489e3bc9641
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768982"
---
# <a name="how-to-handle-exceptions-in-parallel-loops"></a>Nasıl yapılır: Paralel Döngülerde Özel Durumları İşleme
<xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>Ve <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> aşırı yüklemelerin, oluşturulan özel durumları işlemek için özel bir mekanizması yoktur. Bu şekilde, düzenli `for` ve `foreach` döngülere ( `For` ve `For Each` Visual Basic) benzeirler; işlenmeyen bir özel durum, çalışmakta olan tüm yinelemeler sona erdiğinde döngünün sonlandırılmasına neden olur.
  
 Paralel döngülere kendi özel durum işleme mantığınızı eklediğinizde, benzer özel durumların aynı anda birden çok iş parçacığında oluşturulması ve bir iş parçacığında oluşan bir özel durumun başka bir iş parçacığında başka bir özel durumun oluşturulmasına neden olduğu büyük/küçük harf işleme. İçindeki döngüden tüm özel durumları sarmalayarak her iki durumu da işleyebilirsiniz <xref:System.AggregateException?displayProperty=nameWithType> . Aşağıdaki örnekte olası bir yaklaşım gösterilmektedir.  
  
> [!NOTE]
> "Yalnızca kendi kodum" etkinleştirildiğinde, bazı durumlarda Visual Studio özel durumu oluşturan satıra kesilir ve "özel durum Kullanıcı kodu tarafından işlenmiyor" yazan bir hata mesajı görüntüler. Bu hata zararsız. F5 tuşuna basarak bu uygulamadan devam edebilir ve aşağıdaki örnekte gösterilen özel durum işleme davranışına bakabilirsiniz. Visual Studio 'Nun ilk hatada kesilmesini engellemek için **Araçlar, Seçenekler, hata ayıklama, genel**altında "yalnızca kendi kodum" onay kutusunun işaretini kaldırmanız yeterlidir.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, tüm özel durumlar yakalandıktan sonra bir <xref:System.AggregateException?displayProperty=nameWithType> oluşturulur. Çağıran, hangi özel durumların işleneceğini karar verebilir.  
  
 [!code-csharp[TPL_Exceptions#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#08)]
 [!code-vb[TPL_Exceptions#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionsinloops.vb#08)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri paralelliği](data-parallelism-task-parallel-library.md)
- [PLıNQ ve TPL 'deki lambda Ifadeleri](lambda-expressions-in-plinq-and-tpl.md)
