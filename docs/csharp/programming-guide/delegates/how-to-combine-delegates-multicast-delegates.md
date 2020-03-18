---
title: Nasıl temsilcileri (Multicast Delegates) birleştirmek için - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: 7b5b9ba5c9bf70983fac9f869836b4c8c5449eca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705385"
---
# <a name="how-to-combine-delegates-multicast-delegates-c-programming-guide"></a>Temsilcileri birleştirme (Çok Noktaya Yayın Temsilcileri) (C# Programlama Kılavuzu)
Bu örnek, çok noktaya yayın temsilcilerinin nasıl oluşturulurunu gösterir. [Temsilci](../../language-reference/builtin-types/reference-types.md) nesnelerin kullanışlı bir özelliği, `+` işleç kullanılarak bir temsilci örneğine birden çok nesne atanabilir olmasıdır. Çok noktaya yayın temsilcisi, atanan temsilcilerin listesini içerir. Çok noktaya yayın temsilcisi çağrıldığında, listedeki delegeleri sırayla çağırır. Yalnızca aynı türden temsilciler birleştirilebilir.  
  
 İşleç, `-` bir bileşen temsilcisini çok noktaya yayın temsilcisinden kaldırmak için kullanılabilir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideDelegates#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#11)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.MulticastDelegate>
- [C# Programlama Kılavuzu](../index.md)
- [Olaylar](../events/index.md)
