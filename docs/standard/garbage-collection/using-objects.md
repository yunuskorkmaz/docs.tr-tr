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
ms.openlocfilehash: 7c586c725a385029db80763ba13915be79c6cd7e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33576330"
---
# <a name="using-objects-that-implement-idisposable"></a>IDisposable uygulayan nesneler kullanma

Ortak dil çalışma zamanı 's atık toplayıcı yönetilen nesneler tarafından kullanılan bellek kaldırsa ancak yönetilmeyen kaynakları kullanmak türleri uygulayan <xref:System.IDisposable> geri kazanılacak bu yönetilmeyen kaynaklar için ayrılan bellek izin vermek için arabirim. Arabirimini uygulayan bir nesneye kullanarak tamamladığınızda <xref:System.IDisposable>, nesnenin çağırmalıdır <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> uygulaması. Bunu iki yoldan biriyle yapabilirsiniz:  
  
* C# ile `using` deyimi veya Visual Basic `Using` deyimi.  
  
* Uygulama tarafından bir `try/finally` bloğu.  

## <a name="the-using-statement"></a>Using deyimi

`using` Deyimi C# ve `Using` Visual Basic'de deyimini oluşturun ve nesneyi temizlemek amacıyla yazmalısınız kod basitleştirin. `using` Deyimi bir veya daha fazla kaynak alır, belirtin ve otomatik olarak nesnesinin siler deyimleri yürütür. Ancak, `using` deyimi, bunlar oluşturulan yöntemi kapsamında kullanılan nesneler için yararlıdır.  
  
Aşağıdaki örnek kullanır `using` oluşturmak ve yayın için deyimi bir <xref:System.IO.StreamReader?displayProperty=nameWithType> nesnesi.  
  
[!code-csharp[Conceptual.Disposable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using1.cs#1)]
[!code-vb[Conceptual.Disposable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using1.vb#1)]  
  
Ancak unutmayın <xref:System.IO.StreamReader> uygulayan sınıf <xref:System.IDisposable> gösteren bir yönetilmeyen kaynak kullanır, örneğin açıkça çağırın değil arabirimi <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> yöntemi. C# veya Visual Basic derleyici karşılaştığında `using` deyimi, açıkça içeren aşağıdaki kodu eşdeğerdir Ara dile (IL) yayar bir `try/finally` bloğu.  
  
[!code-csharp[Conceptual.Disposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using3.cs#3)]
[!code-vb[Conceptual.Disposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using3.vb#3)]  
  
C# `using` deyimi de sağlar, iç içe geçmiş dahili olarak eşdeğer olan tek bir deyimde birden çok kaynaklarında edinmeye `using` deyimleri. Aşağıdaki örnekte iki başlatır <xref:System.IO.StreamReader> nesneleri iki farklı dosyaların içeriğini okumak için.  
  
[!code-csharp[Conceptual.Disposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using4.cs#4)]

## <a name="tryfinally-block"></a>Try/finally bloğu

Kaydırma yerine bir `try/finally` engelleyin bir `using` deyimi, aktarmızı uygulamak `try/finally` doğrudan engelleyin. Bu sizin kişisel kodlama stiliniz olabilir veya bunu aşağıdaki nedenlerden biri dolayısıyla yapmak isteyebilirsiniz:  
  
* Eklenecek bir `catch` oluşturulan tüm özel durumları işlemek için blok `try` bloğu. Aksi takdirde, tarafından oluşturulan özel durumlar `using` içinde oluşturulan tüm özel durumları olarak deyimi işlenmemiş, `using` bloke bir `try/catch` blok mevcut değil.  
  
* Uygulayan bir nesne örneği oluşturmak için <xref:System.IDisposable> , kapsam içinde beyan blok yerel değil.  
  
Kullandığı aşağıdaki örnek önceki örneğe benzerdir bir `try/catch/finally` örneği, kullanın ve elden blok bir <xref:System.IO.StreamReader> nesnesi ve tarafından oluşturulan tüm özel durumları işlemek için <xref:System.IO.StreamReader> oluşturucusu ve kendi <xref:System.IO.StreamReader.ReadToEnd%2A> yöntemi. Unutmayın kodda `finally` blok denetler nesne uygulayan <xref:System.IDisposable> değil `null` çağırmadan önce <xref:System.IDisposable.Dispose%2A> yöntemi. Bunu yapmak için hata sonuçlanabilir bir <xref:System.NullReferenceException> çalışma zamanında özel durum.  
  
[!code-csharp[Conceptual.Disposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using5.cs#6)]
[!code-vb[Conceptual.Disposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using5.vb#6)]  
  
Uygulanacak seçerseniz veya uygulamalıdır temel bu deseni takip edebilirsiniz bir `try/finally` programlama dilinizi desteklemediğinden bloğunu bir `using` deyimi doğrudan çağrıları izin vermez ancak <xref:System.IDisposable.Dispose%2A> yöntemi. 
  
## <a name="see-also"></a>Ayrıca bkz.

[Yönetilmeyen kaynakları temizleme](../../../docs/standard/garbage-collection/unmanaged.md)   
[using deyimi (C# Başvurusu)](~/docs/csharp/language-reference/keywords/using-statement.md)   
[Using deyimi (Visual Basic)](~/docs/visual-basic/language-reference/statements/using-statement.md)
