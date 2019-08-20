---
title: 'Nasıl yapılır: Temsilcileri birleştirme (çok noktaya yayın temsilcileri C# )-Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: d9430021e6a9b438822f1a6dc201f64adf4fdb0f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590670"
---
# <a name="how-to-combine-delegates-multicast-delegatesc-programming-guide"></a>Nasıl yapılır: Temsilcileri Birleştirme (Çok Noktaya Yayın Temsilcileri)(C# Programlama Kılavuzu)
Bu örnek, çok noktaya yayın temsilcileri oluşturmayı gösterir. [Temsilci](../../language-reference/keywords/delegate.md) nesnelerinin yararlı bir özelliği, `+` işleç kullanılarak bir temsilci örneğine birden çok nesne atanabilmesini sağlar. Çok noktaya yayın temsilcisi, atanan temsilcilerin bir listesini içerir. Çok noktaya yayın temsilcisi çağrıldığında, listedeki temsilcileri sırayla çağırır. Yalnızca aynı türde temsilciler birleştirilebilir.  
  
 `-` İşleci bir çok noktaya yayın temsilcisinden bir bileşen temsilcisini kaldırmak için kullanılabilir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideDelegates#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#11)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.MulticastDelegate>
- [C# Programlama Kılavuzu](../index.md)
- [Olaylar](../events/index.md)
