---
title: Bir koleksiyon başharfi ile sözlük başlatma - C# Programlama Kılavuzu
ms.date: 12/20/2018
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
ms.openlocfilehash: 1e6e7fac9dd49ad1943ac9046bd9e4932c383257
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75741360"
---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a>Bir koleksiyon başharfi (C# Programlama Kılavuzu) ile sözlük başlatma

A, <xref:System.Collections.Generic.Dictionary%602> anahtar/değer çiftleri koleksiyonunu içerir. Yöntemi <xref:System.Collections.Generic.Dictionary%602.Add%2A> iki parametre, bir anahtar ve değer için bir alır. Bir veya <xref:System.Collections.Generic.Dictionary%602> `Add` yöntem birden çok parametre alan herhangi bir koleksiyonu başlatmanın bir yolu, aşağıdaki örnekte gösterildiği gibi her parametre kümesini ayraçlara bünyesine katıyor. Başka bir seçenek de aşağıdaki örnekte gösterilen bir dizin baş harflerini kullanmaktır.

## <a name="example"></a>Örnek

Aşağıdaki kod örneğinde, <xref:System.Collections.Generic.Dictionary%602> a türü `StudentName`örnekleri ile başharfe  İlk başlatma yöntemini `Add` iki bağımsız değişkenle kullanır. Derleyici, anahtar ve `Add` `StudentName` değer çiftlerinin her biri için bir çağrı oluşturur. `int` İkinci `Dictionary` sınıfın ortak okuma / yazma dizinleyici yöntemi kullanır:

[!code-csharp[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToDictionaryInitializer.cs#HowToDictionaryInitializer)]  

İlk bildirimde koleksiyonun her öğesindeki iki çift ayraç çiftine dikkat edin. En içteki parantezler `StudentName`nesne baş harflerini içine, en dıştaki parantezler `students` <xref:System.Collections.Generic.Dictionary%602>ise . Son olarak, sözlük için tüm toplama başharfleri parantez içinde kapalıdır. İkinci başharfte, atamanın sol tarafı anahtar, sağ tarafı ise değerdir, nesne başharfi kullanır. `StudentName`

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Nesne ve Koleksiyon Başlatıcıları](./object-and-collection-initializers.md)
