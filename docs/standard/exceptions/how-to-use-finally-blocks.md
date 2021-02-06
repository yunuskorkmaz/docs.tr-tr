---
description: 'Daha fazla bilgi edinin: finally bloklarını kullanma'
title: 'Nasıl yapılır: Finally Bloklarını Kullanma'
ms.date: 03/30/2017
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
ms.openlocfilehash: 0c296e5cba8e3f4f50005a6178886a116f6e7bac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99629610"
---
# <a name="how-to-use-finally-blocks"></a>Finally bloklarını kullanma

Bir özel durum oluştuğunda, yürütme duraklar ve denetim uygun özel durum işleyicisine verilir. Bu genellikle, yürütülmesi beklenen kod satırlarının atlanacağı anlamına gelir. Bir dosya kapatma gibi bazı kaynak temizleme işlemleri, özel durum oluşturulması durumunda bile yapılmalıdır. Bunu yapmak için bir `finally` bloğu kullanabilirsiniz. Bir `finally` blok, bir özel durumun oluşturulup oluşturulmayacağını ne olursa olsun her zaman yürütülür.

Aşağıdaki kod örneği `try` / `catch` bir bloğu yakalamak için kullanır <xref:System.ArgumentOutOfRangeException> . `Main`Yöntemi iki dizi oluşturur ve diğerini kopyalamaya çalışır. Eylem bir oluşturur <xref:System.ArgumentOutOfRangeException> ve hata konsola yazılır. `finally`Blok, kopyalama eyleminin sonucu ne olursa olsun yürütülür.

[!code-cpp[CodeTryCatchFinallyExample#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CPP/source2.cpp#3)]
[!code-csharp[CodeTryCatchFinallyExample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CS/source2.cs#3)]
[!code-vb[CodeTryCatchFinallyExample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeTryCatchFinallyExample/VB/source2.vb#3)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Özel durumlar](index.md)
