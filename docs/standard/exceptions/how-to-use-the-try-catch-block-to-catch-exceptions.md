---
title: 'Nasıl yapılır: Özel Durumları Yakalamak için Try-Catch Bloğu Kullanma'
description: Özel durum tetiklemeli veya oluşturabilen deyimler içermesi için try bloğunu kullanın. Bir veya daha fazla catch bloklarında özel durumları işlemek için deyimler koyun.
ms.date: 02/06/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- exceptions, try/catch blocks
- try blocks
- try/catch blocks
- catch blocks
ms.assetid: a3ce6dfd-1f64-471b-8ad8-8cfaf406275d
ms.openlocfilehash: cfe5b2b304cdb9efe7f0d91059fe1c279b4fa2dd
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828016"
---
# <a name="how-to-use-the-trycatch-block-to-catch-exceptions"></a>Özel durumları yakalamak için try/catch bloğunu kullanma

Bir blok içinde özel durum oluşturabilen veya oluşturabilen herhangi bir kod deyimini yerleştirin `try` ve bir veya daha fazla blok altındaki bir veya daha fazla blok içindeki özel durumu veya özel durumları işlemek için kullanılan deyimleri yerleştirebilirsiniz `catch` `try` . Her `catch` bir blok özel durum türünü içerir ve bu özel durum türünü işlemek için gereken ek deyimler içerebilir.

Aşağıdaki örnekte, <xref:System.IO.StreamReader> *data.txt* adlı bir dosya açılır ve dosyadan bir satır alır. Kod üç özel durum oluşturmasından dolayı bir blok içine yerleştirilir `try` . Üç `catch` blok özel durumları yakalar ve sonuçları konsola görüntüleyerek işler.

[!code-csharp[CatchException#3](~/samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception2.cs#3)]
[!code-vb[CatchException#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception2.vb#3)]

Ortak dil çalışma zamanı (CLR), bloklar tarafından işlenmeyen özel durumları yakalar `catch` . CLR tarafından bir özel durum yakalanmışsa, CLR yapılandırmanıza bağlı olarak aşağıdaki sonuçlardan biri ortaya çıkabilir:

- **Hata ayıklama** iletişim kutusu görüntülenir.
- Program yürütmeyi durduruyor ve özel durum bilgileri içeren bir iletişim kutusu görünür.
- Bir hata [Standart hata çıkış akışına](xref:System.Console.Error)yazdırılır.

> [!NOTE]
> Çoğu kod bir özel durum oluşturabilir ve gibi bazı özel durumlar <xref:System.OutOfMemoryException> herhangi bir zamanda CLR tarafından oluşturulabilir. Uygulamalar bu özel durumlarla uğraşmak zorunda olmasa da, diğer kullanıcılar tarafından kullanılacak kitaplıkları yazma olasılıklarının farkında olun. Bir bloktaki kodun ne zaman ayarlanacağı hakkında öneriler için `try` bkz. [özel durumlar Için en iyi uygulamalar](best-practices-for-exceptions.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Özel durumlar](index.md)
- [.NET 'te g/ç hatalarını işleme](../io/handling-io-errors.md)
