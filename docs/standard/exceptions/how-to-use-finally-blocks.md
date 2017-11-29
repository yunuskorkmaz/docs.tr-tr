---
title: "Nasıl yapılır: Finally Bloklarını Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b303582a62f211091b1ebee0e88cf380da8b03d9
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/21/2017
---
# <a name="how-to-use-finally-blocks"></a>Finally bloklarını kullanma

Özel durum oluştuğunda yürütme durur ve denetim için uygun özel durum işleyici verilir. Bu, genellikle yürütülecek beklediğiniz kod satırlarını atladığını anlamına gelir. Bir dosyayı kapatma gibi bazı kaynak temizleme bir özel durum olsa bile yapılmalıdır. Bunu yapmak için kullanabileceğiniz bir `finally` bloğu. A `finally` bloğu her zaman yürütür, bir özel durum ne olursa olsun.

Aşağıdaki kod örneğinde bir `try` / `catch` catch bloğu bir <xref:System.ArgumentOutOfRangeException>. `Main` Yöntemi dizilerinin oluşturur ve diğerine kopyalamak çalışır. Eylem oluşturan bir <xref:System.ArgumentOutOfRangeException> ve hata konsoluna yazılır. `finally` Blok kopyalama eylemin sonucunu bağımsız olarak yürütür.

[!code-cpp[CodeTryCatchFinallyExample#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CPP/source2.cpp#3)]
[!code-csharp[CodeTryCatchFinallyExample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CS/source2.cs#3)]
[!code-vb[CodeTryCatchFinallyExample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeTryCatchFinallyExample/VB/source2.vb#3)]  

## <a name="see-also"></a>Ayrıca Bkz.  
[Özel durumlar](index.md)   
