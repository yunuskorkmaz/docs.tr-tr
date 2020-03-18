---
title: 'Nasıl yapılır: Finally Bloklarını Kullanma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, try/catch blocks
- exceptions, finally blocks
- try/catch blocks
- finally blocks
- ArgumentOutOfRangeException class
ms.assetid: 4b9c0137-04af-4468-91d1-b9014df8ddd2
ms.openlocfilehash: 44fbb53437c4c8f19a424227a167e2e268b77057
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708838"
---
# <a name="how-to-use-finally-blocks"></a>Son blokları nasıl kullanılır

Bir özel durum oluştuğunda, yürütme durur ve denetim uygun özel durum işleyicisine verilir. Bu genellikle yürütülmesini beklediğiniz kod satırlarının atlanır anlamına gelir. Bir dosyayı kapatma gibi bazı kaynak temizleme, bir özel durum atılsa bile yapılması gerekir. Bunu yapmak için bir `finally` blok kullanabilirsiniz. Bir `finally` özel durum atılıp atılmadığına bakılmaksızın, bir blok her zaman yürütür.

Aşağıdaki kod örneği `try` / `catch` bir <xref:System.ArgumentOutOfRangeException>. Yöntem `Main` iki dizi oluşturur ve birini diğerine kopyalamaya çalışır. Eylem bir oluşturur <xref:System.ArgumentOutOfRangeException> ve hata konsola yazılır. Blok, `finally` kopyalama eyleminin sonucuna bakılmaksızın yürütülür.

[!code-cpp[CodeTryCatchFinallyExample#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CPP/source2.cpp#3)]
[!code-csharp[CodeTryCatchFinallyExample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CS/source2.cs#3)]
[!code-vb[CodeTryCatchFinallyExample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeTryCatchFinallyExample/VB/source2.vb#3)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Özel durumlar](index.md)
