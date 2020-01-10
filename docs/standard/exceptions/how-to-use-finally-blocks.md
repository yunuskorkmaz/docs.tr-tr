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
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708838"
---
# <a name="how-to-use-finally-blocks"></a>Finally bloklarını kullanma

Bir özel durum oluştuğunda, yürütme duraklar ve denetim uygun özel durum işleyicisine verilir. Bu genellikle, yürütülmesi beklenen kod satırlarının atlanacağı anlamına gelir. Bir dosya kapatma gibi bazı kaynak temizleme işlemleri, özel durum oluşturulması durumunda bile yapılmalıdır. Bunu yapmak için bir `finally` bloğu kullanabilirsiniz. Bir özel durumun oluşturulup oluşturulmayacağını ne olursa olsun `finally` bloğu her zaman yürütülür.

Aşağıdaki kod örneği bir <xref:System.ArgumentOutOfRangeException>yakalamak için bir `try`/`catch` bloğu kullanır. `Main` yöntemi iki dizi oluşturur ve diğerini kopyalamaya çalışır. Eylem bir <xref:System.ArgumentOutOfRangeException> oluşturur ve hata konsola yazılır. `finally` bloğu kopyalama eyleminin sonucu ne olursa olsun yürütülür.

[!code-cpp[CodeTryCatchFinallyExample#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CPP/source2.cpp#3)]
[!code-csharp[CodeTryCatchFinallyExample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CS/source2.cs#3)]
[!code-vb[CodeTryCatchFinallyExample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeTryCatchFinallyExample/VB/source2.vb#3)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Durumlar](index.md)
