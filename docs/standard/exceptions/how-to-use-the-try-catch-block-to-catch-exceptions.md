---
title: "Nasıl yapılır: özel durumları yakalamak için Try-Catch bloğu kullanın"
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
- try blocks
- try/catch blocks
- catch blocks
ms.assetid: a3ce6dfd-1f64-471b-8ad8-8cfaf406275d
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5a72a21085c37bed4d84518810f69a013d515189
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/21/2017
---
# <a name="how-to-use-the-trycatch-block-to-catch-exceptions"></a>Özel durumları yakalamak için try/catch bloğu kullanma

Özel durumlar oluşturma kodun bölümlerini yerleştirin bir `try` özel durumları işleme bloğu ve Yerleştir kod bir `catch` bloğu. `catch` Bloğu bir dizi anahtar sözcüğüyle başlayan deyimi `catch`, bir özel durum türünü ve bir eylem yapılması ardından.

Aşağıdaki kod örneğinde bir `try` / `catch` olası Özel catch bloğu. `Main` Yöntemini içeren bir `try` ile engelleme bir <xref:System.IO.StreamReader> veri dosyasını açar deyimi adlı `data.txt` ve dosyasından bir dize yazar. Aşağıdaki `try` bloğu bir `catch` oluşur özel durumları yakalar blok `try` bloğu.

 [!code-cpp[CatchException#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception2.cpp#3)]
 [!code-csharp[CatchException#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception2.cs#3)]
 [!code-vb[CatchException#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception2.vb#3)]  

Ortak dil çalışma zamanı catch bloğu tarafından yakalandı özel durumları yakalar. Çalışma zamanı nasıl yapılandırıldığına bağlı olarak hata ayıklama iletişim kutusu görüntülenirse, programın yürütülmesi durdurulur ve özel durum bilgilerini içeren bir iletişim kutusu görünür veya STDERR'e bir hata yazdırılır.

> [!NOTE] 
> Neredeyse her kod satırının bir özel durum, özellikle ortak dil çalışma zamanı tarafından kendisine gibi oluşturulan özel durumlara neden olabilir <xref:System.OutOfMemoryException>. Uygulamaların çoğu bu durumlarla başa gerekmez, ancak, başkaları tarafından kullanılacak kitaplıkları yazılırken bu olasılığını dikkat etmeniz gerekir. Öneriler zaman ayarlamak bir Try bloğunda kod için bkz: [özel durumlar için en iyi uygulamaları](best-practices-for-exceptions.md).

## <a name="see-also"></a>Ayrıca Bkz.  
[Özel durumlar](index.md)
