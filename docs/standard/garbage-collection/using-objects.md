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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160292"
---
# <a name="using-objects-that-implement-idisposable"></a>IDisposable uygulayan nesneleri kullanma

Ortak dil runtime'ın çöp toplayıcısı yönetilen nesneler tarafından kullanılan belleği geri alır, ancak yönetilmeyen kaynakları kullanan türler, bu yönetilmeyen kaynaklara ayrılan belleğin geri alınmasına izin vermek için <xref:System.IDisposable> arabirimi uygular. Uygulayan bir nesneyi kullanmayı <xref:System.IDisposable>bitirdiğinizde, nesnenin <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> uygulamasını aramalısınız. Bunu iki yoldan biriyle yapabilirsiniz:  
  
- C# `using` deyimi veya Visual `Using` Basic deyimi ile.  
  
- Bir `try/finally` blok uygulayarak.  

## <a name="the-using-statement"></a>Using deyimi

C# `using` ifadesi ve `Using` Visual Basic'teki deyim, bir nesne oluşturmak ve temizlemek için yazmanız gereken kodu basitleştirir. İfade `using` bir veya daha fazla kaynak elde eder, belirttiğiniz ifadeleri yürütür ve nesneyi otomatik olarak ortadan yıkar. Ancak, `using` deyim yalnızca oluşturuldukları yöntem kapsamında kullanılan nesneler için yararlıdır.  
  
Aşağıdaki örnek, `using` bir <xref:System.IO.StreamReader?displayProperty=nameWithType> nesne oluşturmak ve serbest bırakmak için deyimi kullanır.  
  
[!code-csharp[Conceptual.Disposable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using1.cs#1)]
[!code-vb[Conceptual.Disposable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using1.vb#1)]  
  
<xref:System.IO.StreamReader> Sınıf, yönetilmeyen bir <xref:System.IDisposable> kaynak kullandığını gösteren arabirimi uygulasa da, örnek yöntemi açıkça <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> çağırmaz. C# veya Visual Basic derleyicisi ifadeyle `using` karşılaştığında, açıkça bir `try/finally` blok içeren aşağıdaki koda eşdeğer ara dil (IL) yayır.  
  
[!code-csharp[Conceptual.Disposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using3.cs#3)]
[!code-vb[Conceptual.Disposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using3.vb#3)]  
  
C# `using` deyimi, iç içe kullanılan `using` ifadelere eşdeğer olan tek bir deyimde birden çok kaynak elde etmenizi de sağlar. Aşağıdaki örnek, iki farklı <xref:System.IO.StreamReader> dosyanın içeriğini okumak için iki nesneyi anında okur.  
  
[!code-csharp[Conceptual.Disposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using4.cs#4)]

## <a name="tryfinally-block"></a>Try/finally bloğu

Bir `try/finally` `using` bloğu bir deyimde sarmalamak yerine, `try/finally` bloğu doğrudan uygulamayı seçebilirsiniz. Bu sizin kişisel kodlama stiliniz olabilir veya bunu aşağıdaki nedenlerden biri dolayısıyla yapmak isteyebilirsiniz:  
  
- Blokta `catch` atılan özel durumları işlemek için `try` bir blok eklemek için. Aksi takdirde, `using` bir `using` `try/catch` blok yoksa blok içinde atılan tüm özel durumlar gibi ekstre tarafından atılan tüm özel durumlar işlenmez.  
  
- Kapsamı yerel olmayan bir nesneyi, <xref:System.IDisposable> içinde beyan edildiği blok için anında uygulamak için.  
  
Aşağıdaki `try/catch/finally` örnek, bir <xref:System.IO.StreamReader> nesneyi anlık olarak kullanmak, kullanmak ve elden çıkarmak ve <xref:System.IO.StreamReader> oluşturucu ve <xref:System.IO.StreamReader.ReadToEnd%2A> yöntemi tarafından atılan özel durumları işlemek için bir blok kullanması dışında önceki örneğe benzer. Bloktaki kodun, `finally` uygulayan <xref:System.IDisposable> nesnenin `null` <xref:System.IDisposable.Dispose%2A> yöntemi aramadan önce olmadığını denetlediğine dikkat edin. Bunun yapılmaması, çalışma <xref:System.NullReferenceException> zamanında bir özel durumla sonuçlanabilir.  
  
[!code-csharp[Conceptual.Disposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using5.cs#6)]
[!code-vb[Conceptual.Disposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using5.vb#6)]  
  
Programlama diliniz bir `try/finally` `using` deyimi desteklemediği, ancak <xref:System.IDisposable.Dispose%2A> yönteme doğrudan çağrılara izin verdiği için, bir engelleme uygulamayı veya uygulamanız gerekiyorsa bu temel deseni izleyebilirsiniz.
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilmeyen Kaynakları Temizleme](../../../docs/standard/garbage-collection/unmanaged.md)
- [using Deyimi (C# Başvurusu)](../../csharp/language-reference/keywords/using-statement.md)
- [Using Deyimi (Visual Basic)](../../visual-basic/language-reference/statements/using-statement.md)
