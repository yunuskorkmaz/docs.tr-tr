---
title: 'Nasıl yapılır: Özel Durumları Yakalamak için Try-Catch Bloğu Kullanma'
ms.date: 02/06/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- exceptions, try/catch blocks
- try blocks
- try/catch blocks
- catch blocks
ms.assetid: a3ce6dfd-1f64-471b-8ad8-8cfaf406275d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5183a854ee2b7462ecc27786a5fc0697565194c0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61970865"
---
# <a name="how-to-use-the-trycatch-block-to-catch-exceptions"></a>Özel durumları yakalamak için try/catch bloğu kullanma

Yükseltme veya bir özel durum herhangi bir kod deyim koyun bir `try` blok ve özel durum ya da bir veya daha fazla özel durumları işlemek için kullanılan bir yerde ifadeleri `catch` aşağıdaki blokları `try` blok. Her `catch` blok özel durum türü içerir ve bu özel durum türü işlemek için gereken ek ifadeleri içerebilir.

Aşağıdaki örnekte, bir <xref:System.IO.StreamReader> adlı bir dosya açılır *data.txt* ve dosyasından bir satır alır. Kod herhangi üç özel durum fırlatabilir beri yerleştirilir bir `try` blok. Üç `catch` bloğu özel durumları yakalamak ve bunları konsola sonuçları görüntüleyerek işlemek.

[!code-csharp[CatchException#3](~/samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception2.cs#3)]
[!code-vb[CatchException#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception2.vb#3)]  

Ortak dil çalışma zamanı (CLR) tarafından işlenmemiş özel durumları yakalayan `catch` engeller. Bir özel durum CLR tarafından yakalandı, aşağıdaki sonuçlardan birini CLR yapılandırmanıza bağlı olarak oluşabilir:

- A **hata ayıklama** iletişim kutusu görüntülenir.
- Program yürütme durdurur ve özel durum bilgilerini içeren bir iletişim kutusu görüntülenir.
- Bir hata yazdırır [standart hata çıkış akışına](xref:System.Console.Error).

> [!NOTE]
> Çoğu kod gibi bazı özel durumlar ve özel durum oluşturabilecek <xref:System.OutOfMemoryException>, CLR tarafından herhangi bir anda atılabilir. Uygulamalar, bu özel durumlar için gerekli değildir, ancak başkaları tarafından kullanılacak kitaplıkları yazarken olasılığını unutmayın. Kod ne zaman öneriler için bir `try` engellemek için bkz: [özel durumlar için en iyi yöntemler](best-practices-for-exceptions.md).

## <a name="see-also"></a>Ayrıca bkz.

[Özel Durumlar](index.md)  
[. NET'te g/ç hataları işleme](../io/handling-io-errors.md)
