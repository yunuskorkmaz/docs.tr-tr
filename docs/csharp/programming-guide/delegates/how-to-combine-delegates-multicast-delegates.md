---
title: Temsilcileri birleştirme (çok noktaya yayın temsilcileri)- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: 7b5b9ba5c9bf70983fac9f869836b4c8c5449eca
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705385"
---
# <a name="how-to-combine-delegates-multicast-delegates-c-programming-guide"></a>Temsilcileri birleştirme (Çok Noktaya Yayın Temsilcileri) (C# Programlama Kılavuzu)
Bu örnek, çok noktaya yayın temsilcileri oluşturmayı gösterir. [Temsilci](../../language-reference/builtin-types/reference-types.md) nesnelerinin yararlı bir özelliği, `+` işleci kullanılarak bir temsilci örneğine birden çok nesne atanabilmesini sağlar. Çok noktaya yayın temsilcisi, atanan temsilcilerin bir listesini içerir. Çok noktaya yayın temsilcisi çağrıldığında, listedeki temsilcileri sırayla çağırır. Yalnızca aynı türde temsilciler birleştirilebilir.  
  
 `-` işleci bir çok noktaya yayın temsilcisinden bir bileşen temsilcisini kaldırmak için kullanılabilir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideDelegates#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#11)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.MulticastDelegate>
- [C# Programlama Kılavuzu](../index.md)
- [Olaylar](../events/index.md)
