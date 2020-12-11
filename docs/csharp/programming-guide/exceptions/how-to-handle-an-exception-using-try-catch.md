---
title: Try-catch-C# programlama kılavuzunu kullanarak özel durum işleme
description: Try-catch bloğu kullanarak bir özel durumu nasıl işleyeceğinizi öğrenin. Bir kod örneğine bakın ve kullanılabilir ek kaynakları görüntüleyin.
ms.date: 12/09/2020
helpviewer_keywords:
- exception handling [C#], try/catch blocks
- exceptions [C#], try/catch blocks
- try/catch blocks [C#]
ms.assetid: ca8e3773-980e-4767-8633-7408540e9818
ms.openlocfilehash: b6368660dbe037123f5bb6ce52502d4a94fcfc3a
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97110526"
---
# <a name="how-to-handle-an-exception-using-trycatch-c-programming-guide"></a>Try/catch kullanarak özel durum işleme (C# Programlama Kılavuzu)

[Try-catch](../../language-reference/keywords/try-catch.md) bloğunun amacı, çalışma kodu tarafından oluşturulan bir özel durumu yakalamak ve işleymelidir. Bazı özel durumlar bir `catch` blokta işlenebilir ve sorunu yeniden oluşturulan özel durum olmadan çözüldü; ancak, daha sık yapabileceğiniz tek şey uygun özel durumun oluşturulmuş olduğundan emin olabilir.

## <a name="example"></a>Örnek

Bu örnekte, <xref:System.IndexOutOfRangeException> en uygun özel durum değildir: <xref:System.ArgumentOutOfRangeException> hata, `index` çağıran tarafından geçirilen bağımsız değişkenin neden olduğu için yöntem için daha anlamlı hale gelir.

:::code language="csharp" source="snippets/exceptions/ExampleTryCatch.cs" id="ExampleTryCatch":::

## <a name="comments"></a>Yorumlar

Özel duruma neden olan kod `try` bloğa alınmıştır. Bir `catch` ifade, gerçekleşirse, işleme hemen sonra eklenir `IndexOutOfRangeException` . `catch`Bloğu öğesini işler `IndexOutOfRangeException` ve bunun yerine daha uygun `ArgumentOutOfRangeException` özel durumu oluşturur. Çağıranı mümkün olduğunca fazla bilgi sağlamak için, özgün özel durumu yeni özel durum olarak belirtmeyi göz önünde bulundurun <xref:System.Exception.InnerException%2A> . <xref:System.Exception.InnerException%2A>Özelliği [salt okunurdur](../../properties.md#read-only), bunu yeni özel durumun oluşturucusunda atamanız gerekir.
