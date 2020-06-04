---
title: Tür birden fazla 'System.Collections.Generic.IEnumerable(Of T)' örneği uyguladığından '<typename>' türü üzerindeki 'For Each' belirsiz
ms.date: 07/20/2015
f1_keywords:
- vbc32096
- bc32096
helpviewer_keywords:
- BC32096
ms.assetid: ed20d09c-913f-482e-89f8-c0a596c3ec24
ms.openlocfilehash: 153a2640d66f48660f21339aaf0ecc8eaa10f51f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402972"
---
# <a name="for-each-on-type-typename-is-ambiguous-because-the-type-implements-multiple-instantiations-of-systemcollectionsgenericienumerableof-t"></a>Tür birden fazla 'System.Collections.Generic.IEnumerable(Of T)' örneği uyguladığından '\<typename>' türü üzerindeki 'For Each' belirsiz
Bir `For Each` ifade, birden fazla metodu olan bir yineleyici değişkenini belirtir <xref:System.Collections.IEnumerable.GetEnumerator%2A> .  
  
 Yineleyici değişkeni, <xref:System.Collections.IEnumerable?displayProperty=nameWithType> <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> `Collections` .NET Framework ad uzaylarından birinde veya arabirimini uygulayan bir türde olmalıdır. Bir sınıfın, her oluşturma için farklı bir tür bağımsız değişkeni kullanılarak birden fazla oluşturulmuş genel arabirim uygulaması mümkündür. Bunu yapan bir sınıf Yineleyici değişkeni için kullanılırsa, bu değişkenin birden fazla <xref:System.Collections.IEnumerable.GetEnumerator%2A> yöntemi vardır. Böyle bir durumda Visual Basic hangi yöntemin çağrılacağını seçemezsiniz.  
  
 **Hata kimliği:** BC32096  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Yineleyici değişken türünü kullanmak istediğiniz yöntemi tanımlayan arabirime dönüştürmek için [DirectCast İşleci](../operators/directcast-operator.md) veya [TryCast işlecini](../operators/trycast-operator.md) kullanın <xref:System.Collections.IEnumerable.GetEnumerator%2A> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [For Each...Next Deyimi](../statements/for-each-next-statement.md)
- [Arabirimler](../../programming-guide/language-features/interfaces/index.md)
