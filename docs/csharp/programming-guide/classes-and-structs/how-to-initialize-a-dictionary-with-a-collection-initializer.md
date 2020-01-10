---
title: Koleksiyon başlatıcısı ile bir sözlük başlatma- C# Programlama Kılavuzu
ms.date: 12/20/2018
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
ms.openlocfilehash: 1e6e7fac9dd49ad1943ac9046bd9e4932c383257
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75741360"
---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a>Koleksiyon başlatıcısı ile bir sözlük başlatma (C# Programlama Kılavuzu)

<xref:System.Collections.Generic.Dictionary%602>, anahtar/değer çiftleri koleksiyonu içerir. <xref:System.Collections.Generic.Dictionary%602.Add%2A> yöntemi, biri anahtar ve diğeri değer için olmak üzere iki parametre alır. <xref:System.Collections.Generic.Dictionary%602>başlatmanın bir yolu veya `Add` yöntemi birden çok parametre alan herhangi bir koleksiyon, aşağıdaki örnekte gösterildiği gibi her parametre kümesini küme ayraçları içine allemektir. Diğer bir seçenek de aşağıdaki örnekte gösterilen bir dizin başlatıcısı kullanmaktır.

## <a name="example"></a>Örnek

Aşağıdaki kod örneğinde, bir <xref:System.Collections.Generic.Dictionary%602> `StudentName`türündeki örneklerle başlatılır.  İlk başlatma `Add` yöntemini iki bağımsız değişkenle kullanır. Derleyici, `int` anahtarların ve `StudentName` değerlerinin her bir çiftinin `Add` için bir çağrı oluşturur. İkincisi `Dictionary` sınıfının genel okuma/yazma Indexer yöntemini kullanır:

[!code-csharp[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToDictionaryInitializer.cs#HowToDictionaryInitializer)]  

İlk bildirimde koleksiyonun her bir öğesinde iki ayraç çiftini aklınızda edin. En içteki ayraç, `StudentName`için nesne başlatıcısını kapsar ve en dıştaki ayraç, `students` <xref:System.Collections.Generic.Dictionary%602>eklenecek anahtar/değer çifti için başlatıcıyı kapsar. Son olarak, sözlük için tüm koleksiyon başlatıcısı küme ayraçları içine alınmıştır. İkinci başlatmada, atamanın sol tarafı anahtardır ve sağ tarafta ise `StudentName`için bir nesne Başlatıcısı kullanılarak değer bulunur.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Nesne ve Koleksiyon Başlatıcıları](./object-and-collection-initializers.md)
