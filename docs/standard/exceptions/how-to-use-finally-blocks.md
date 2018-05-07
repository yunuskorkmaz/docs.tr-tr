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
ms.openlocfilehash: dff1083256e24a35b7238ee5e8af6cb5743bc0ea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-finally-blocks"></a>Finally bloklarını kullanma

Özel durum oluştuğunda yürütme durur ve denetim için uygun özel durum işleyici verilir. Bu, genellikle yürütülecek beklediğiniz kod satırlarını atladığını anlamına gelir. Bir dosyayı kapatma gibi bazı kaynak temizleme bir özel durum olsa bile yapılmalıdır. Bunu yapmak için kullanabileceğiniz bir `finally` bloğu. A `finally` bloğu her zaman yürütür, bir özel durum ne olursa olsun.

Aşağıdaki kod örneğinde bir `try` / `catch` catch bloğu bir <xref:System.ArgumentOutOfRangeException>. `Main` Yöntemi dizilerinin oluşturur ve diğerine kopyalamak çalışır. Eylem oluşturan bir <xref:System.ArgumentOutOfRangeException> ve hata konsoluna yazılır. `finally` Blok kopyalama eylemin sonucunu bağımsız olarak yürütür.

[!code-cpp[CodeTryCatchFinallyExample#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CPP/source2.cpp#3)]
[!code-csharp[CodeTryCatchFinallyExample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CS/source2.cs#3)]
[!code-vb[CodeTryCatchFinallyExample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeTryCatchFinallyExample/VB/source2.vb#3)]  

## <a name="see-also"></a>Ayrıca Bkz.  
[Özel Durumlar](index.md)   
