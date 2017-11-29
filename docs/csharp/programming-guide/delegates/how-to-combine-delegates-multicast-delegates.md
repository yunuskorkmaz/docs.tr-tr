---
title: "Nasıl yapılır: Temsilcileri Birleştirme (Çok Noktaya Yayın Temsilcileri)(C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ddb4ecbbf456179e91aa0003c2dc5653f153411f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-combine-delegates-multicast-delegatesc-programming-guide"></a>Nasıl yapılır: Temsilcileri Birleştirme (Çok Noktaya Yayın Temsilcileri)(C# Programlama Kılavuzu)
Bu örnek çok noktaya yayın temsilcileri oluşturulacağını gösterir. Kullanışlı bir özelliği [temsilci](../../../csharp/language-reference/keywords/delegate.md) nesnedir kullanarak birden çok nesne bir temsilci örneğine atanabilir `+` işleci. Çok noktaya yayın temsilci atanan temsilcileri listesini içerir. Çok noktaya yayın temsilci çağrıldığında, sırayla listesinde temsilcileri çağırır. Yalnızca aynı türdeki temsilciler birleştirilebilir.  
  
 `-` İşleci, çok noktaya yayın bir temsilciyi bileşen temsilciyi kaldırmak için kullanılabilir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideDelegates#11](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-combine-delegates-multicast-delegates_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.MulticastDelegate>  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Olayları](../../../csharp/programming-guide/events/index.md)
