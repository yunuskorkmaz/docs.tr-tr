---
title: 'Nasıl yapılır: Try-Catch- C# Programming kılavuzunu kullanarak özel durum işleme'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], try/catch blocks
- exceptions [C#], try/catch blocks
- try/catch blocks [C#]
ms.assetid: ca8e3773-980e-4767-8633-7408540e9818
ms.openlocfilehash: 5378de09962055fe7d2e100484ad69662c803e0f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590240"
---
# <a name="how-to-handle-an-exception-using-trycatch-c-programming-guide"></a>Nasıl yapılır: Try/catch kullanarak özel durum işleme (C# Programlama Kılavuzu)
[Try-catch](../../language-reference/keywords/try-catch.md) bloğunun amacı, çalışma kodu tarafından oluşturulan bir özel durumu yakalamak ve işleymelidir. Bazı özel durumlar bir `catch` blokta işlenebilir ve sorun yeniden oluşturulan özel durum olmadan çözüldü; ancak, genellikle yapabileceğiniz tek şey uygun özel durumun atılmasından emin olabilir.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, <xref:System.IndexOutOfRangeException> en uygun özel durum değildir: <xref:System.ArgumentOutOfRangeException> `index` hata, çağıran tarafından geçirilen bağımsız değişkenin nedeni olduğundan yöntem için daha anlamlı hale gelir.  
  
 [!code-csharp[csProgGuideExceptions#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#5)]  
  
## <a name="comments"></a>Açıklamalar  
 Özel duruma neden olan kod `try` bloğa alınmıştır. Bir `catch` ifade, gerçekleşirse, işleme `IndexOutOfRangeException`hemen sonra eklenir. Bloğu öğesini işler ve bunun yerine daha uygun `ArgumentOutOfRangeException` özel durumu oluşturur. `IndexOutOfRangeException` `catch` Çağıranı mümkün olduğunca fazla bilgi sağlamak için, özgün özel durumu yeni özel durum olarak <xref:System.Exception.InnerException%2A> belirtmeyi göz önünde bulundurun. Özelliği ReadOnly olduğundan, bunu yeni özel durumun oluşturucusunda atamanız gerekir. [](../../language-reference/keywords/readonly.md) <xref:System.Exception.InnerException%2A>  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Özel Durumlar ve Özel Durum İşleme](./index.md)
- [Özel Durum İşleme](./exception-handling.md)
