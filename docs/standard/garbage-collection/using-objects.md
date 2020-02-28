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
ms.openlocfilehash: c5232aa89064c514e71f3a18bc754159e9c9b15b
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78160292"
---
# <a name="using-objects-that-implement-idisposable"></a>IDisposable uygulayan nesneleri kullanma

Ortak dil çalışma zamanının atık toplayıcısı, yönetilen nesneler tarafından kullanılan belleği geri kazanır, ancak yönetilmeyen kaynakları kullanan türler, bu yönetilmeyen kaynaklara ayrılan belleğin geri kazanılmaya izin vermek için <xref:System.IDisposable> arabirimini uygular. <xref:System.IDisposable>uygulayan bir nesneyi kullanmayı bitirdiğinizde nesnenin <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> uygulamasını çağırmanız gerekir. Bunu iki yoldan biriyle yapabilirsiniz:  
  
- C# `using` ifadesiyle veya Visual Basic `Using` ifadesiyle.  
  
- `try/finally` bir blok uygulayarak.  

## <a name="the-using-statement"></a>Using deyimi

İçindeki `using` ve içindeki C# `Using` ifadesinde Visual Basic, bir nesneyi oluşturmak ve temizlemek için yazmanız gereken kodu basitleştirir. `using` deyimi bir veya daha fazla kaynak edinir, belirttiğiniz deyimleri yürütür ve nesneyi otomatik olarak atar. Ancak `using` deyimleri yalnızca oluşturuldukları yöntemin kapsamı içinde kullanılan nesneler için yararlıdır.  
  
Aşağıdaki örnek, bir <xref:System.IO.StreamReader?displayProperty=nameWithType> nesnesini oluşturmak ve serbest bırakmak için `using` ifadesini kullanır.  
  
[!code-csharp[Conceptual.Disposable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using1.cs#1)]
[!code-vb[Conceptual.Disposable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using1.vb#1)]  
  
<xref:System.IO.StreamReader> sınıfı, yönetilmeyen bir kaynak kullandığını gösteren <xref:System.IDisposable> arabirimini uygulasa da, örneğin <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> yöntemini açıkça çağırmadığını unutmayın. C# Veya Visual Basic Derleyicisi `using` bildirimiyle karşılaştığında, açıkça bir `try/finally` bloğunu içeren aşağıdaki koda denk olan ara DILI (IL) yayar.  
  
[!code-csharp[Conceptual.Disposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using3.cs#3)]
[!code-vb[Conceptual.Disposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using3.vb#3)]  
  
C# `using` deyimi, iç içe `using` deyimlerine dahili olarak eşdeğer olan tek bir deyimde birden fazla kaynak elde etmenizi sağlar. Aşağıdaki örnek iki farklı dosyanın içeriğini okumak için iki <xref:System.IO.StreamReader> nesnesi oluşturur.  
  
[!code-csharp[Conceptual.Disposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using4.cs#4)]

## <a name="tryfinally-block"></a>Try/finally bloğu

Bir `using` bildiriminde `try/finally` bloğunu sarmalama yerine, `try/finally` bloğunu doğrudan uygulamayı seçebilirsiniz. Bu sizin kişisel kodlama stiliniz olabilir veya bunu aşağıdaki nedenlerden biri dolayısıyla yapmak isteyebilirsiniz:  
  
- `try` bloğunda oluşan tüm özel durumları işlemek üzere bir `catch` bloğu eklemek için. Aksi takdirde, bir `try/catch` bloğu yoksa, `using` bloğunda oluşturulan özel durumlar gibi `using` ifadesiyle oluşturulan özel durumlar da işlenmez.  
  
- Kapsamı, içinde bildirildiği bloğa yerel olmayan <xref:System.IDisposable> uygulayan bir nesne oluşturmak için.  
  
Aşağıdaki örnek, bir önceki örneğe benzerdir, ancak bir <xref:System.IO.StreamReader> nesnesinin örneğini oluşturmak, kullanmak ve atmak ve <xref:System.IO.StreamReader> Oluşturucusu ve <xref:System.IO.StreamReader.ReadToEnd%2A> yöntemi tarafından oluşturulan tüm özel durumları işlemek için `try/catch/finally` bir blok kullanması dışında. `finally` bloğundaki kodun, <xref:System.IDisposable.Dispose%2A> yöntemini çağırmadan önce <xref:System.IDisposable> uygulayan nesnenin `null` olmadığını kontrol ettiğini unutmayın. Bunun yapılmaması, çalışma zamanında <xref:System.NullReferenceException> özel durumuyla sonuçlanabilir.  
  
[!code-csharp[Conceptual.Disposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using5.cs#6)]
[!code-vb[Conceptual.Disposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using5.vb#6)]  
  
Programlama diliniz bir `using` ifadesini desteklemediğinden, ancak <xref:System.IDisposable.Dispose%2A> yöntemine doğrudan çağrılara izin veren bir `try/finally` bloğunu uygulamayı tercih etmeniz veya uygulamanız gerekiyorsa, bu temel kalıbı izleyebilirsiniz.
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilmeyen Kaynakları Temizleme](../../../docs/standard/garbage-collection/unmanaged.md)
- [using deyimleri (C# başvuru)](../../csharp/language-reference/keywords/using-statement.md)
- [Using deyimleri (Visual Basic)](../../visual-basic/language-reference/statements/using-statement.md)
