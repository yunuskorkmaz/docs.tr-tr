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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 213ab53c68a37ac0ba5f337a1d6fc32bfe6f8989
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43883686"
---
# <a name="how-to-use-finally-blocks"></a>Finally bloklarını kullanma

Bir özel durum oluştuğunda yürütmeyi durdurur ve denetim uygun bir özel durum işleyicisine verilir. Bu, genellikle yürütülecek beklediğiniz kod satırlarını atladığını anlamına gelir. Bir dosyayı kapatma gibi bazı kaynak temizleme bir özel durum olsa bile yapılmalıdır. Bunu yapmak için kullanabileceğiniz bir `finally` blok. A `finally` her zaman bloğun, bir özel durum ne olursa olsun.

Aşağıdaki kod örneğinde bir `try` / `catch` catch bloğu bir <xref:System.ArgumentOutOfRangeException>. `Main` Yöntemi iki diziler oluşturur ve diğerine kopyalamak çalışır. Eylem üretir bir <xref:System.ArgumentOutOfRangeException> ve hata konsoluna yazılır. `finally` Blok kopyalama eylem sonucunu bağımsız olarak yürütür.

[!code-cpp[CodeTryCatchFinallyExample#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CPP/source2.cpp#3)]
[!code-csharp[CodeTryCatchFinallyExample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CS/source2.cs#3)]
[!code-vb[CodeTryCatchFinallyExample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeTryCatchFinallyExample/VB/source2.vb#3)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Durumlar](index.md)
