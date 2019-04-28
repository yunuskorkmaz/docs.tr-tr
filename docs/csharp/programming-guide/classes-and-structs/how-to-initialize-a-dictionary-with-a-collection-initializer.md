---
title: -Koleksiyon Başlatıcısı ile bir sözlük başlatma nasıl C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 12/20/2018
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
ms.openlocfilehash: acd426b7652705ff395df9a81cde8ef549af0e31
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646403"
---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a>Nasıl (C# programlama Kılavuzu) koleksiyon Başlatıcısı ile bir sözlük başlatma

A <xref:System.Collections.Generic.Dictionary%602> anahtar/değer çiftleri koleksiyonu içerir. Kendi <xref:System.Collections.Generic.Dictionary%602.Add*> yöntemi biri anahtar ve değer için bir tane olmak üzere iki parametre alır. Başlatmak için tek yönlü bir <xref:System.Collections.Generic.Dictionary%602>, ya da herhangi bir koleksiyon olan `Add` yöntemi birden çok parametre alır, aşağıdaki örnekte gösterildiği gibi her parametre kümesi küme ayraçları içine çevrelemektir. Başka bir seçenek de aşağıdaki örnekte gösterildiği bir dizin Başlatıcı kullanmaktır.

## <a name="example"></a>Örnek

Aşağıdaki kod örneğinde, bir <xref:System.Collections.Generic.Dictionary%602> türünün bir örneğini ile başlatılmış `StudentName`.  İlk başlatma kullanır `Add` yöntemi iki bağımsız değişken. Derleyici bir çağrı oluşturur `Add` her çiftleri `int` anahtarları ve `StudentName` değerleri. İkinci kullandığı ortak okuma / dizin oluşturucu yönteminin yazma `Dictionary` sınıfı:

[!code-csharp-interactive[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToDictionaryInitializer.cs#HowToDictionaryInitializer)]  

Küme ayraçları içine ilk bildirimi koleksiyonda her öğeye iki çiftleri unutmayın. Nesne Başlatıcısı için en içteki ayraç içine `StudentName`, ve en dıştaki ayraç içine eklenecek anahtar/değer çifti için Başlatıcı `students` <xref:System.Collections.Generic.Dictionary%602>. Son olarak, tüm koleksiyon Başlatıcısı sözlüğü için parantez içine alınır. İkinci ise başlatma sırasında atamanın sol tarafında anahtar ve sağ tarafındaki nesne Başlatıcı kullanarak değer, `StudentName`.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Nesne ve Koleksiyon Başlatıcıları](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
