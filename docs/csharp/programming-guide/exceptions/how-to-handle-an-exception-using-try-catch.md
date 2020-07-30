---
title: Try-catch-C# programlama kılavuzunu kullanarak özel durum işleme
description: Try-catch bloğu kullanarak bir özel durumu nasıl işleyeceğinizi öğrenin. Bir kod örneğine bakın ve kullanılabilir ek kaynakları görüntüleyin.
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], try/catch blocks
- exceptions [C#], try/catch blocks
- try/catch blocks [C#]
ms.assetid: ca8e3773-980e-4767-8633-7408540e9818
ms.openlocfilehash: 357aebe042bc5b6e761b3c1bad258021441de22c
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302002"
---
# <a name="how-to-handle-an-exception-using-trycatch-c-programming-guide"></a>Try/catch kullanarak özel durum işleme (C# Programlama Kılavuzu)
[Try-catch](../../language-reference/keywords/try-catch.md) bloğunun amacı, çalışma kodu tarafından oluşturulan bir özel durumu yakalamak ve işleymelidir. Bazı özel durumlar bir `catch` blokta işlenebilir ve sorun yeniden oluşturulan özel durum olmadan çözüldü; ancak, genellikle yapabileceğiniz tek şey uygun özel durumun atılmasından emin olabilir.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, <xref:System.IndexOutOfRangeException> en uygun özel durum değildir: hata, <xref:System.ArgumentOutOfRangeException> `index` çağıran tarafından geçirilen bağımsız değişkenin nedeni olduğundan yöntem için daha anlamlı hale gelir.  
  
 [!code-csharp[csProgGuideExceptions#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#5)]  
  
## <a name="comments"></a>Yorumlar  
 Özel duruma neden olan kod `try` bloğa alınmıştır. Bir `catch` ifade, gerçekleşirse, işleme hemen sonra eklenir `IndexOutOfRangeException` . `catch`Bloğu öğesini işler `IndexOutOfRangeException` ve bunun yerine daha uygun `ArgumentOutOfRangeException` özel durumu oluşturur. Çağıranı mümkün olduğunca fazla bilgi sağlamak için, özgün özel durumu yeni özel durum olarak belirtmeyi göz önünde bulundurun <xref:System.Exception.InnerException%2A> . <xref:System.Exception.InnerException%2A>Özelliği [salt okunurdur](../../properties.md#read-only), bunu yeni özel durumun oluşturucusunda atamanız gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Özel durumlar ve özel durum Işleme](./index.md)
- [Özel Durum İşleme](./exception-handling.md)
