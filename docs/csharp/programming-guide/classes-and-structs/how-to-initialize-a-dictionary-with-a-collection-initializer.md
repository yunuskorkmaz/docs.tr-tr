---
title: Koleksiyon başlatıcısı ile bir sözlük başlatma-C# Programlama Kılavuzu
description: Add yöntemini veya bir dizin başlatıcısı kullanarak C# ' de bir sözlüğü nasıl başlatacağınızı öğrenin. Bu örnekte her iki seçenek de gösterilmektedir.
ms.date: 12/20/2018
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
ms.openlocfilehash: 2f33240b02785c5c886a1ebebb8984d29c9f7795
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865053"
---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a>Koleksiyon başlatıcısı ile bir sözlük başlatma (C# Programlama Kılavuzu)

Bir <xref:System.Collections.Generic.Dictionary%602> anahtar/değer çiftleri koleksiyonu içerir. <xref:System.Collections.Generic.Dictionary%602.Add%2A>Yöntemi, biri anahtar ve diğeri değer için olmak üzere iki parametre alır. <xref:System.Collections.Generic.Dictionary%602>Ya da yöntemi birden çok parametre alan herhangi bir koleksiyonu başlatmanın bir yolu `Add` , aşağıdaki örnekte gösterildiği gibi her bir parametre kümesini küme ayraçları içine allemektir. Diğer bir seçenek de aşağıdaki örnekte gösterilen bir dizin başlatıcısı kullanmaktır.

## <a name="example"></a>Örnek

Aşağıdaki kod örneğinde,, <xref:System.Collections.Generic.Dictionary%602> türünde örneklerle başlatılır `StudentName` .  İlk başlatma `Add` yöntemi iki bağımsız değişkenle birlikte kullanır. Derleyici, `Add` her `int` anahtar ve değer çiftlerinin her biri için bir çağrı oluşturur `StudentName` . İkincisi, sınıfının ortak bir okuma/yazma Indexer yöntemini kullanır `Dictionary` :

[!code-csharp[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToDictionaryInitializer.cs#HowToDictionaryInitializer)]  

İlk bildirimde koleksiyonun her bir öğesinde iki ayraç çiftini aklınızda edin. En içteki ayraç, için nesne başlatıcısını kapsar `StudentName` ve en dıştaki küme ayraçları öğesine eklenecek anahtar/değer çifti için başlatıcıyı kapsar `students` <xref:System.Collections.Generic.Dictionary%602> . Son olarak, sözlük için tüm koleksiyon başlatıcısı küme ayraçları içine alınmıştır. İkinci başlatmada atamanın sol tarafı anahtardır ve sağ tarafta ise, için bir nesne Başlatıcısı kullanılarak değer bulunur `StudentName` .

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Nesne ve Koleksiyon Başlatıcıları](./object-and-collection-initializers.md)
