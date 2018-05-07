---
title: 'Nasıl yapılır: Temsilcileri Birleştirme (Çok Noktaya Yayın Temsilcileri)(C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: e1214a4d281dbcb9d8186770b68510d3d9a4b15f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-combine-delegates-multicast-delegatesc-programming-guide"></a>Nasıl yapılır: Temsilcileri Birleştirme (Çok Noktaya Yayın Temsilcileri)(C# Programlama Kılavuzu)
Bu örnek çok noktaya yayın temsilcileri oluşturulacağını gösterir. Kullanışlı bir özelliği [temsilci](../../../csharp/language-reference/keywords/delegate.md) nesnedir kullanarak birden çok nesne bir temsilci örneğine atanabilir `+` işleci. Çok noktaya yayın temsilci atanan temsilcileri listesini içerir. Çok noktaya yayın temsilci çağrıldığında, sırayla listesinde temsilcileri çağırır. Yalnızca aynı türdeki temsilciler birleştirilebilir.  
  
 `-` İşleci, çok noktaya yayın bir temsilciyi bileşen temsilciyi kaldırmak için kullanılabilir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideDelegates#11](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-combine-delegates-multicast-delegates_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.MulticastDelegate>  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Olaylar](../../../csharp/programming-guide/events/index.md)
