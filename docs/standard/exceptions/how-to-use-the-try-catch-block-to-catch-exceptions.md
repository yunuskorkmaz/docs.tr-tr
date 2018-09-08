---
title: 'Nasıl yapılır: özel durumları yakalamak için Try-Catch bloğu kullanma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 852df5cb3eeea2ee5fa44ddce2f97e9c4f8d8b5a
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44185210"
---
# <a name="how-to-use-the-trycatch-block-to-catch-exceptions"></a>Özel durumları yakalamak için try/catch bloğu kullanma

Özel durum oluşturma olasılığı olan kod bölümlerini yerleştirileceği bir `try` özel durumları işleyen bloğu ve yerde kodu bir `catch` blok. `catch` Bloğudur bir dizi deyim anahtar sözcüğü ile başlayan `catch`ve ardından bir özel durum türünü ve bir eylem gerçekleştirilebilir.

Aşağıdaki kod örneğinde bir `try` / `catch` olası bir özel durum yakalamak için blok. `Main` Yöntemi içeren bir `try` ile engelleyecek bir <xref:System.IO.StreamReader> adlı bir veri dosyası açılır deyimi `data.txt` ve dosyanın bir dize yazar. Aşağıdaki `try` bloğu bir `catch` oluşur herhangi bir özel durumu yakalar blok `try` blok.

 [!code-cpp[CatchException#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception2.cpp#3)]
 [!code-csharp[CatchException#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception2.cs#3)]
 [!code-vb[CatchException#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception2.vb#3)]  

Ortak dil çalışma zamanı bir catch bloğu tarafından yakalandı özel durumu yakalar. Çalışma zamanının nasıl yapılandırdığına bağlı olarak hata ayıklama iletişim kutusu görüntülenirse, program yürütme durdurur ve özel durum bilgilerini içeren bir iletişim kutusu görünür veya bir hata stderr biçiminde yazdırılır.

> [!NOTE] 
> Hemen hemen her kod satırının bir özel durum, özellikle ortak dil çalışma zamanı tarafından kendisi gibi attığı özel durumları oluşabilir <xref:System.OutOfMemoryException>. Uygulamaların çoğu bu özel durumlar gerekmez, ancak, başkaları tarafından kullanılacak kitaplıkları yazarken bu olasılığını bilmeniz gerekir. Öneriler ne zaman bir Try bloğu içinde kod için bkz: [özel durumlar için en iyi yöntemler](best-practices-for-exceptions.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Durumlar](index.md)
