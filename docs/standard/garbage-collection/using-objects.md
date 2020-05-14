---
title: IDisposable uygulayan nesneleri kullanma
ms.date: 05/13/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dispose method
- try/finally block
- garbage collection, encapsulating resources
ms.assetid: 81b2cdb5-c91a-4a31-9c83-eadc52da5cf0
ms.openlocfilehash: d0d55a9253fee1ffcfd5c10714a1118883f6c4ce
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396967"
---
# <a name="using-objects-that-implement-idisposable"></a>IDisposable uygulayan nesneleri kullanma

Ortak dil çalışma zamanının atık toplayıcısı, yönetilen nesneler tarafından kullanılan belleği geri kazanır, ancak yönetilmeyen kaynakları kullanan türler, <xref:System.IDisposable> Bu yönetilmeyen kaynakların gerektirdiği kaynakların geri kazanılabileceği şekilde arabirimini uygular. Uygulayan bir nesneyi kullanmayı bitirdiğinizde <xref:System.IDisposable> nesnenin uygulamasını çağırmanız gerekir <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> . Bunu iki yoldan biriyle yapabilirsiniz:

- C# `using` ifadesiyle ( `Using` Visual Basic).
- Bir blok uygulayarak `try/finally` ve içinde öğesini çağırarak <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> `finally` .

## <a name="the-using-statement"></a>Using deyimi

C# [ `using` ve içindeki deyimindeki ifade](../../csharp/language-reference/keywords/using-statement.md) , [ `Using` ](../../visual-basic/language-reference/statements/using-statement.md) bir nesneyi temizlemek için yazmanız gereken kodu basitleştirir Visual Basic. `using`Deyimi bir veya daha fazla kaynak edinir, belirttiğiniz deyimleri yürütür ve nesneyi otomatik olarak atar. Ancak, `using` ifade yalnızca oluşturuldukları yöntemin kapsamı içinde kullanılan nesneler için yararlıdır.

Aşağıdaki örnek, `using` bir nesnesi oluşturmak ve serbest bırakmak için ifadesini kullanır <xref:System.IO.StreamReader?displayProperty=nameWithType> .

[!code-csharp[Conceptual.Disposable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using1.cs#1)]
[!code-vb[Conceptual.Disposable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using1.vb#1)]

Sınıfı, <xref:System.IO.StreamReader> <xref:System.IDisposable> yönetilmeyen bir kaynak kullandığını belirten arabirimini uygular; ancak, örnek yöntemi açıkça çağırmaz <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> . C# veya Visual Basic Derleyicisi `using` ifadesiyle karşılaştığında, açıkça bir blok içeren aşağıdaki koda denk olan ara dili (IL) yayar `try/finally` .

[!code-csharp[Conceptual.Disposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using3.cs#3)]
[!code-vb[Conceptual.Disposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using3.vb#3)]

C# `using` deyimi Ayrıca, iç içe geçmiş deyimlere dahili olarak eşdeğer olan tek bir deyimde birden fazla kaynak almanızı sağlar `using` . Aşağıdaki örnek <xref:System.IO.StreamReader> iki farklı dosyanın içeriğini okumak için iki nesne örneği oluşturur.

[!code-csharp[Conceptual.Disposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using4.cs#4)]

## <a name="tryfinally-block"></a>Try/finally bloğu

Bir deyime bir blok sarmalama yerine `try/finally` `using` , `try/finally` bloğu doğrudan uygulamayı seçebilirsiniz. Kişisel kodlama stiliniz olabilir veya bunu aşağıdaki nedenlerden biri için yapmak isteyebilirsiniz:

- `catch`Blokta oluşan özel durumları işlemek üzere bir blok eklemek için `try` . Aksi takdirde, bildiriminde oluşturulan özel durumlar `using` işlenmemiş değildir.

- <xref:System.IDisposable>Kapsamı, içinde bildirildiği bloğa yerel olmayan uygulayan bir nesne örneğini oluşturmak için.

Aşağıdaki örnek, `try/catch/finally` bir nesnenin örneğini oluşturma, kullanma ve atma, <xref:System.IO.StreamReader> <xref:System.IO.StreamReader> Oluşturucu ve yöntemi tarafından oluşturulan özel durumları işlemek için bir blok kullanması dışında, önceki örneğe benzer <xref:System.IO.StreamReader.ReadToEnd%2A> . Bloktaki kod, `finally` uygulayan nesnenin <xref:System.IDisposable> `null` yöntemini çağırmadan önce olmadığını denetler <xref:System.IDisposable.Dispose%2A> . Bunun başarısız olması, <xref:System.NullReferenceException> çalışma zamanında bir özel durum oluşmasına neden olabilir.

[!code-csharp[Conceptual.Disposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using5.cs#6)]
[!code-vb[Conceptual.Disposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using5.vb#6)]

`try/finally`Programlama diliniz bir ifadeyi desteklemediğinden, `using` ancak yönteme doğrudan çağrı yapmasına izin vereceğinden, bir blok uygulamayı uygulamayı veya uygulamayı tercih etmeniz gerekiyorsa, bu temel kalıbı izleyebilirsiniz <xref:System.IDisposable.Dispose%2A> .

## <a name="idisposable-instance-members"></a>IDisposable örnek üyeleri

Bir sınıf bir <xref:System.IDisposable> uygulama, bir alan veya özellik olan bir örnek üye olarak tutuyorsa, sınıf da uygulamalıdır <xref:System.IDisposable> . Daha fazla bilgi için bkz. [Cascade Dispose uygulama](implementing-dispose.md#cascade-dispose-calls).

## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilmeyen kaynakları Temizleme](../../../docs/standard/garbage-collection/unmanaged.md)
- [using Deyimi (C# Başvurusu)](../../csharp/language-reference/keywords/using-statement.md)
- [Using Deyimi (Visual Basic)](../../visual-basic/language-reference/statements/using-statement.md)
