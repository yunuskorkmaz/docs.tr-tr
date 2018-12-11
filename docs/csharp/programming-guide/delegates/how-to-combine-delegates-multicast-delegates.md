---
title: 'Nasıl Yapılır: Temsilcileri (çok noktaya yayın temsilcileri) birleştirme- C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: d835f9b22fef550d6e73cbd620a283bd71e393ec
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237798"
---
# <a name="how-to-combine-delegates-multicast-delegatesc-programming-guide"></a>Nasıl Yapılır: (Çok noktaya yayın temsilcileri) temsilcileri birleştirme (C# Programlama Kılavuzu)
Bu örnek, çok noktaya yayın temsilcileri oluşturma işlemini gösterir. Kullanışlı bir özelliği [temsilci](../../../csharp/language-reference/keywords/delegate.md) nesneleri, kullanarak birden çok nesne için bir temsilci örneği atanabilir `+` işleci. Çok noktaya yayın temsilci atanmış temsilcileri listesini içerir. Çok noktaya yayın temsilci çağrıldığında listesinde sırada, temsilciler çağırır. Yalnızca aynı türdeki temsilciler birleştirilebilir.  
  
 `-` İşleci, bir bileşen temsilci bir çok noktaya yayın temsilciyi kaldırmak için kullanılabilir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideDelegates#11](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-combine-delegates-multicast-delegates_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- <xref:System.MulticastDelegate>  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Olaylar](../../../csharp/programming-guide/events/index.md)
