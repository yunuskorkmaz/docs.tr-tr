---
title: IDisposable uygulayan nesneler kullanma
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
ms.openlocfilehash: 70955d496f5cf9e3bf44b9bc03a054d1c96efe98
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44260025"
---
# <a name="using-objects-that-implement-idisposable"></a>IDisposable uygulayan nesneler kullanma

Ortak dil çalışma zamanının atık toplayıcı yönetilen nesneler tarafından kullanılan belleği geri kazanır, ancak yönetilmeyen kaynakları kullanan türler <xref:System.IDisposable> kazanılacak bu yönetilmeyen kaynakların tahsis edilen bellek izin vermek için arabirim. Bitirdiğinizde uygulayan bir nesne kullanarak <xref:System.IDisposable>, nesnenin çağırmalıdır <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> uygulaması. Bunu iki yoldan biriyle yapabilirsiniz:  
  
* C# ile `using` deyimi veya Visual Basic `Using` deyimi.  
  
* Uygulayarak bir `try/finally` blok.  

## <a name="the-using-statement"></a>Using deyimi

`using` C# deyimi ve `Using` Visual Basic'de deyimini oluşturmak ve bir nesneyi temizlemek için yazmanız gereken kodu basitleştirin. `using` Deyimi bir veya daha fazla kaynağı alır, belirtin ve nesnenin otomatik olarak atar deyimleri yürütür. Ancak, `using` deyimi, bunlar oluşturulan yöntem kapsamında kullanılan nesneler için kullanışlıdır.  
  
Aşağıdaki örnekte `using` oluşturmak ve serbest bırakmak için deyimi bir <xref:System.IO.StreamReader?displayProperty=nameWithType> nesne.  
  
[!code-csharp[Conceptual.Disposable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using1.cs#1)]
[!code-vb[Conceptual.Disposable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using1.vb#1)]  
  
Ancak dikkat <xref:System.IO.StreamReader> sınıfının Implements <xref:System.IDisposable> gösteren yönetilmeyen bir kaynağı kullanır, örneğin açıkça çağırmak değil arabirimi <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> yöntemi. C# veya Visual Basic derleyici karşılaştığında `using` deyimi, açıkça içeren aşağıdaki koda denk olan ara dil (IL) yayar bir `try/finally` blok.  
  
[!code-csharp[Conceptual.Disposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using3.cs#3)]
[!code-vb[Conceptual.Disposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using3.vb#3)]  
  
C# `using` deyimi de sayesinde iç içe geçmiş dahili olarak denk olan tek bir deyimde birden çok kaynak elde `using` deyimleri. Aşağıdaki örnek iki başlatır <xref:System.IO.StreamReader> nesneleri iki farklı dosyanın içeriğini okumak için.  
  
[!code-csharp[Conceptual.Disposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using4.cs#4)]

## <a name="tryfinally-block"></a>Try/finally bloğu

Kaydırmak yerine bir `try/finally` engelleyin bir `using` deyimi, seçebilirsiniz `try/finally` doğrudan engelleyin. Bu sizin kişisel kodlama stiliniz olabilir veya bunu aşağıdaki nedenlerden biri dolayısıyla yapmak isteyebilirsiniz:  
  
* Eklenecek bir `catch` oluşturulan özel durumları işlemek için blok `try` blok. Aksi takdirde, tarafından oluşturulan özel durumlar `using` içinde oluşturulan özel durumlar olarak deyimi işlenmemiş, `using` bloke bir `try/catch` blok mevcut değil.  
  
* Uygulayan bir nesne örneği <xref:System.IDisposable> kapsamı içinde beyan blokta yerel değil.  
  
Bunu kullanması hariç, aşağıdaki örnek önceki örneğe benzer bir `try/catch/finally` elden oluşturmak ve kullanmak için blok bir <xref:System.IO.StreamReader> nesnesi ve tarafından oluşturulan özel durumları işlemek için <xref:System.IO.StreamReader> oluşturucusu ve <xref:System.IO.StreamReader.ReadToEnd%2A> yöntemi. Unutmayın kodda `finally` blok denetler uygulayan nesnenin <xref:System.IDisposable> değil `null` çağırmadan önce <xref:System.IDisposable.Dispose%2A> yöntemi. Bunun yapılmaması sonuçlanabilir bir <xref:System.NullReferenceException> çalışma zamanında özel durum.  
  
[!code-csharp[Conceptual.Disposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using5.cs#6)]
[!code-vb[Conceptual.Disposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using5.vb#6)]  
  
Uygulamak seçin ya da uygulamalıdır bu temel modeli izleyebilirsiniz bir `try/finally` block programlama diliniz desteklemediğinden bir `using` deyimi doğrudan çağrıları izin vermez ancak <xref:System.IDisposable.Dispose%2A> yöntemi. 
  
## <a name="see-also"></a>Ayrıca bkz.

* [Yönetilmeyen Kaynakları Temizleme](../../../docs/standard/garbage-collection/unmanaged.md)   
* [using deyimi (C# Başvurusu)](~/docs/csharp/language-reference/keywords/using-statement.md)   
* [Using deyimi (Visual Basic)](~/docs/visual-basic/language-reference/statements/using-statement.md)
