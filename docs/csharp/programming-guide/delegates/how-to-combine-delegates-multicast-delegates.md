---
title: 'Nasıl yapılır: temsilcileri birleştirme (çok noktaya yayın temsilcileri C# )-Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: d7098bb5518b92b407f905ddabbfafdcb77536bf
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423344"
---
# <a name="how-to-combine-delegates-multicast-delegatesc-programming-guide"></a>Nasıl yapılır: Temsilcileri Birleştirme (Çok Noktaya Yayın Temsilcileri)(C# Programlama Kılavuzu)
Bu örnek, çok noktaya yayın temsilcileri oluşturmayı gösterir. [Temsilci](../../language-reference/builtin-types/reference-types.md) nesnelerinin yararlı bir özelliği, `+` işleci kullanılarak bir temsilci örneğine birden çok nesne atanabilmesini sağlar. Çok noktaya yayın temsilcisi, atanan temsilcilerin bir listesini içerir. Çok noktaya yayın temsilcisi çağrıldığında, listedeki temsilcileri sırayla çağırır. Yalnızca aynı türde temsilciler birleştirilebilir.  
  
 `-` işleci bir çok noktaya yayın temsilcisinden bir bileşen temsilcisini kaldırmak için kullanılabilir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideDelegates#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#11)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.MulticastDelegate>
- [C# Programlama Kılavuzu](../index.md)
- [Olaylar](../events/index.md)
