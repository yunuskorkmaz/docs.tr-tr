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
ms.openlocfilehash: 5a9218d394b76e897f4263708a10f1bc895ad4e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708472"
---
# <a name="how-to-use-the-trycatch-block-to-catch-exceptions"></a>Özel durumları yakalamak için try/catch bloğu nasıl kullanılır?

Bir `try` blokta özel durum yükseltebilecek veya atabilecek kod deyimlerini yerleştirin ve özel durum `catch` veya özel `try` durumları işlemek için kullanılan deyimleri bloğun altındaki bir veya daha fazla bloka yerleştirin. Her `catch` blok özel durum türünü içerir ve bu özel durum türünü işlemek için gereken ek deyimler içerebilir.

Aşağıdaki örnekte, <xref:System.IO.StreamReader> *data.txt* adlı bir dosya açılır ve dosyadan bir satır alır. Kod üç özel durumdan herhangi birini atabileceğinden, `try` bir blota yerleştirilir. Üç `catch` blok özel durumları yakalar ve sonuçları konsola göstererek bunları işler.

[!code-csharp[CatchException#3](~/samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception2.cs#3)]
[!code-vb[CatchException#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception2.vb#3)]

Ortak Dil Çalışma Süresi (CLR), bloklar `catch` tarafından işlenmemiş özel durumları yakalar. CLR tarafından bir özel durum yakalanırsa, CLR yapılandırmanıza bağlı olarak aşağıdaki sonuçlardan biri oluşabilir:

- Hata **Ayıklama** iletişim kutusu görüntülenir.
- Program yürütmeyi durdurur ve özel durum bilgilerini içeren bir iletişim kutusu görüntülenir.
- Standart [hata çıktı akışına](xref:System.Console.Error)bir hata yazdırır.

> [!NOTE]
> Çoğu kod bir özel durum atabilir <xref:System.OutOfMemoryException>ve clr kendisi tarafından herhangi bir zamanda atılabilir gibi bazı özel durumlar. Bu özel durumlarla başa çıkmak için uygulamalar aranmazken, kitaplıkyazarken başkaları tarafından kullanılma olasılığına dikkat edin. Bir `try` blokta kod ayarlamanın ne zaman ayarlanacaklarına ilişkin öneriler [için, Özel Durumlar için En İyi Uygulamalar'a](best-practices-for-exceptions.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Özel durumlar](index.md)
- [.NET'teki G/Ç hatalarını işleme](../io/handling-io-errors.md)
