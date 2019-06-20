---
title: -Koleksiyon Başlatıcısı ile bir sözlük başlatma nasıl C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 12/20/2018
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
ms.openlocfilehash: bab2c4c996f7780cec572d58eb572a90aeea592a
ms.sourcegitcommit: 4c41ec195caf03d98b7900007c3c8e24eba20d34
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/20/2019
ms.locfileid: "67267676"
---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a>Nasıl (C# programlama Kılavuzu) koleksiyon Başlatıcısı ile bir sözlük başlatma

A <xref:System.Collections.Generic.Dictionary%602> anahtar/değer çiftleri koleksiyonu içerir. Kendi <xref:System.Collections.Generic.Dictionary%602.Add*> yöntemi biri anahtar ve değer için bir tane olmak üzere iki parametre alır. Başlatmak için tek yönlü bir <xref:System.Collections.Generic.Dictionary%602>, ya da herhangi bir koleksiyon olan `Add` yöntemi birden çok parametre alır, aşağıdaki örnekte gösterildiği gibi her parametre kümesi küme ayraçları içine çevrelemektir. Başka bir seçenek de aşağıdaki örnekte gösterildiği bir dizin Başlatıcı kullanmaktır.

## <a name="example"></a>Örnek

Aşağıdaki kod örneğinde, bir <xref:System.Collections.Generic.Dictionary%602> türünün bir örneğini ile başlatılmış `StudentName`.  İlk başlatma kullanır `Add` yöntemi iki bağımsız değişken. Derleyici bir çağrı oluşturur `Add` her çiftleri `int` anahtarları ve `StudentName` değerleri. İkinci kullandığı ortak okuma / dizin oluşturucu yönteminin yazma `Dictionary` sınıfı:

[!code-csharp[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToDictionaryInitializer.cs#HowToDictionaryInitializer)]  

Küme ayraçları içine ilk bildirimi koleksiyonda her öğeye iki çiftleri unutmayın. Nesne Başlatıcısı için en içteki ayraç içine `StudentName`, ve en dıştaki ayraç içine eklenecek anahtar/değer çifti için Başlatıcı `students` <xref:System.Collections.Generic.Dictionary%602>. Son olarak, tüm koleksiyon Başlatıcısı sözlüğü için parantez içine alınır. İkinci ise başlatma sırasında atamanın sol tarafında anahtar ve sağ tarafındaki nesne Başlatıcı kullanarak değer, `StudentName`.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Nesne ve Koleksiyon Başlatıcıları](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
