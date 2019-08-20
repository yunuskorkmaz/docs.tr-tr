---
title: Koleksiyon başlatıcısı ile bir sözlük başlatma- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 12/20/2018
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
ms.openlocfilehash: 22f80365b974df66999ac68f7bc2a9ffa7d445a5
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596807"
---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a>Koleksiyon başlatıcısı ile bir sözlük başlatma (C# Programlama Kılavuzu)

Bir <xref:System.Collections.Generic.Dictionary%602> anahtar/değer çiftleri koleksiyonu içerir. <xref:System.Collections.Generic.Dictionary%602.Add*> Yöntemi, biri anahtar ve diğeri değer için olmak üzere iki parametre alır. Ya da `Add` yöntemi birden çok <xref:System.Collections.Generic.Dictionary%602>parametre alan herhangi bir koleksiyonu başlatmanın bir yolu, aşağıdaki örnekte gösterildiği gibi her bir parametre kümesini küme ayraçları içine allemektir. Diğer bir seçenek de aşağıdaki örnekte gösterilen bir dizin başlatıcısı kullanmaktır.

## <a name="example"></a>Örnek

Aşağıdaki kod örneğinde,, <xref:System.Collections.Generic.Dictionary%602> türünde `StudentName`örneklerle başlatılır.  İlk başlatma `Add` yöntemi iki bağımsız değişkenle birlikte kullanır. Derleyici, her `Add` `int` anahtar ve `StudentName` değer çiftlerinin her biri için bir çağrı oluşturur. İkincisi, `Dictionary` sınıfının ortak bir okuma/yazma Indexer yöntemini kullanır:

[!code-csharp[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToDictionaryInitializer.cs#HowToDictionaryInitializer)]  

İlk bildirimde koleksiyonun her bir öğesinde iki ayraç çiftini aklınızda edin. En içteki ayraç, `StudentName`için nesne başlatıcısını kapsar ve en dıştaki küme ayraçları `students` <xref:System.Collections.Generic.Dictionary%602>öğesine eklenecek anahtar/değer çifti için başlatıcıyı kapsar. Son olarak, sözlük için tüm koleksiyon başlatıcısı küme ayraçları içine alınmıştır. İkinci başlatmada atamanın sol tarafı anahtardır ve sağ tarafta ise, için `StudentName`bir nesne Başlatıcısı kullanılarak değer bulunur.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Nesne ve Koleksiyon Başlatıcıları](./object-and-collection-initializers.md)
