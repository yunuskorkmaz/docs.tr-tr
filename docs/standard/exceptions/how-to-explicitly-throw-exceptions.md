---
title: "Nasıl yapılır: Açıkça Özel Durumlar Oluşturma"
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
helpviewer_keywords:
- exceptions, try/catch blocks
- FileNotFoundException class
- try/catch blocks
- exceptions, throwing
- implicitly throwing exceptions
ms.assetid: 72bdd157-caa9-4478-9ee3-cb4500b84528
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 02576db4b9920a367ac3111f2c2c49989ea45149
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-explicitly-throw-exceptions"></a>Nasıl açıkça özel durumlar oluşturma

Kullanarak bir özel durum açıkça atabilirsiniz `throw` deyimi. Kullanarak yeniden yakalanan bir özel durum da atabilirsiniz `throw` deyimi. Hata ayıklama sırasında daha fazla bilgi sağlamak üzere yeniden atılmış bir özel durum bilgileri eklemek için uygulama kodlama iyi olur.

Aşağıdaki kod örneğinde bir `try` / `catch` olası catch bloğu <xref:System.IO.FileNotFoundException>. Aşağıdaki `try` bloğu bir `catch` yakalar blok <xref:System.IO.FileNotFoundException> ve veri dosyası bulunamazsa, bir ileti konsola yazar. Sonraki deyim `throw` yeni bir oluşturur deyimi <xref:System.IO.FileNotFoundException> ve metin bilgileri özel durumu ekler.

[!code-csharp[Exception.Throwing#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Exception.Throwing/CS/throw.cs#1)]
[!code-vb[Exception.Throwing#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Exception.Throwing/VB/throw.vb#1)]  

## <a name="see-also"></a>Ayrıca Bkz.  
[Özel Durumlar](index.md)
