---
description: 'Hakkında daha fazla bilgi edinin: taşma (Visual Basic Run-Time hata)'
title: Taşma (Visual Basic Çalışma Süresi Hatası)
ms.date: 07/20/2015
f1_keywords:
- vbrERRID_Overflow
ms.assetid: c6a23279-3086-412a-bcff-ff8ed2cb8c6f
ms.openlocfilehash: a01a8916e09f9278dbdf6d594c5ef84d63b04c51
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795462"
---
# <a name="overflow-visual-basic-run-time-error"></a>Taşma (Visual Basic Çalışma Süresi Hatası)

Atama hedefinin sınırlarını aşan bir atamaya çalıştığınızda bir taşma oluşur.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Atamalar, hesaplamalar ve veri türü dönüştürmelerinden oluşan sonuçların, bu tür değer için izin verilen değişkenlerin aralığında gösterilemeyecek kadar büyük olmadığından emin olun ve değeri, gerekirse daha büyük bir değer aralığını tutabilecek bir tür değişkenine atayın.  
  
2. Özelliklerin atamalarının, yaptıkları özelliğin aralığına uygun olduğundan emin olun.  
  
3. Tamsayılar üzerinde zorlanmakta olan hesaplamalarda kullanılan sayıların, tamsayılarla daha büyük sonuçlara sahip olmadığından emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Int32.MaxValue?displayProperty=nameWithType>
- <xref:System.Double.MaxValue?displayProperty=nameWithType>
- [Veri türleri](../data-types/index.md)
- [Hata Türleri](../../programming-guide/language-features/error-types.md)
