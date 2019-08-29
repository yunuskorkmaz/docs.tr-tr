---
title: IDisposable uygulayan nesneleri kullanma
ms.date: 04/07/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dispose method
- try/finally block
- garbage collection, encapsulating resources
ms.assetid: 81b2cdb5-c91a-4a31-9c83-eadc52da5cf0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f165ab5b79abbc2b5464f40a27a580d26af163a
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106947"
---
# <a name="using-objects-that-implement-idisposable"></a>IDisposable uygulayan nesneleri kullanma

Ortak dil çalışma zamanının atık toplayıcısı, yönetilen nesneler tarafından kullanılan belleği geri kazanır, ancak yönetilmeyen kaynakları kullanan türler, bu yönetilmeyen kaynaklara <xref:System.IDisposable> ayrılan belleğin geri kazanılmaya izin vermek için arabirimini uygular. Uygulayan <xref:System.IDisposable>bir nesneyi kullanmayı bitirdiğinizde <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> nesnenin uygulamasını çağırmanız gerekir. Bunu iki yoldan biriyle yapabilirsiniz:  
  
- İfadesiyle veya VisualBasic`Using`ifadesiyle. C# `using`  
  
- Bir `try/finally` blok uygulayarak.  

## <a name="the-using-statement"></a>Using deyimi

`using` C# İçindeki ve`Using` içindeki deyimindeki bir nesne oluşturmak ve temizlemek için yazmanız gereken kodu basitleştirecek Visual Basic. `using` Deyimi bir veya daha fazla kaynak edinir, belirttiğiniz deyimleri yürütür ve nesneyi otomatik olarak atar. Ancak, `using` ifade yalnızca oluşturuldukları yöntemin kapsamı içinde kullanılan nesneler için yararlıdır.  
  
Aşağıdaki örnek, bir `using` <xref:System.IO.StreamReader?displayProperty=nameWithType> nesnesi oluşturmak ve serbest bırakmak için ifadesini kullanır.  
  
[!code-csharp[Conceptual.Disposable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using1.cs#1)]
[!code-vb[Conceptual.Disposable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using1.vb#1)]  
  
<xref:System.IO.StreamReader> Sınıfı, yönetilmeyen bir kaynak kullandığını gösteren <xref:System.IDisposable> arabirimini uygulasa da, <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> örneğin yöntemi açıkça çağırmadığını unutmayın. C# Veya Visual Basic Derleyicisi `using` deyimle karşılaştığında, açıkça bir `try/finally` blok içeren aşağıdaki koda denk olan ara dili (IL) yayar.  
  
[!code-csharp[Conceptual.Disposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using3.cs#3)]
[!code-vb[Conceptual.Disposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using3.vb#3)]  
  
Deyim Ayrıca, iç içe geçmiş `using` deyimlere dahili olarak eşdeğer olan tek bir deyimde birden fazla kaynak elde etmenizi sağlar. C# `using` Aşağıdaki örnek iki farklı dosyanın <xref:System.IO.StreamReader> içeriğini okumak için iki nesne örneği oluşturur.  
  
[!code-csharp[Conceptual.Disposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using4.cs#4)]

## <a name="tryfinally-block"></a>Try/finally bloğu

Bir `try/finally` `using` deyime bir blok sarmalama yerine, `try/finally` bloğu doğrudan uygulamayı seçebilirsiniz. Bu sizin kişisel kodlama stiliniz olabilir veya bunu aşağıdaki nedenlerden biri dolayısıyla yapmak isteyebilirsiniz:  
  
- Blokta`try` oluşan tüm `catch` özel durumları işlemek üzere bir blok eklemek için. Aksi takdirde, bir `using` `try/catch` blok yoksa `using` blok içinde oluşturulan özel durumlar olduğu gibi, ifadesiyle oluşturulan tüm özel durumlar da işlenmez.  
  
- Kapsamı, içinde bildirildiği bloğa yerel <xref:System.IDisposable> olmayan uygulayan bir nesne örneğini oluşturmak için.  
  
`try/catch/finally` Aşağıdaki örnek, bir <xref:System.IO.StreamReader> nesnenin örneğini oluşturma, kullanma ve atma, <xref:System.IO.StreamReader> Oluşturucu ve <xref:System.IO.StreamReader.ReadToEnd%2A> yöntemi tarafından oluşturulan özel durumları işlemek için bir blok kullanması dışında, önceki örneğe benzer. `finally` Bloktaki kodun, <xref:System.IDisposable> yöntemi<xref:System.IDisposable.Dispose%2A> çağırmadan önce değil `null` , uygulayan nesnenin olmadığını kontrol ettiğini unutmayın. Bunun başarısız olması, çalışma zamanında bir <xref:System.NullReferenceException> özel durum oluşmasına neden olabilir.  
  
[!code-csharp[Conceptual.Disposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using5.cs#6)]
[!code-vb[Conceptual.Disposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using5.vb#6)]  
  
Programlama diliniz bir `using` ifadeyi desteklemediğinden, ancak <xref:System.IDisposable.Dispose%2A> yönteme doğrudan çağrı yapmasına izin vereceğinden, `try/finally` bir blok uygulamayı uygulamayı veya uygulamayı tercih etmeniz gerekiyorsa, bu temel kalıbı izleyebilirsiniz. 
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilmeyen Kaynakları Temizleme](../../../docs/standard/garbage-collection/unmanaged.md)
- [using deyimleri (C# başvuru)](../../csharp/language-reference/keywords/using-statement.md)
- [Using deyimleri (Visual Basic)](../../visual-basic/language-reference/statements/using-statement.md)
