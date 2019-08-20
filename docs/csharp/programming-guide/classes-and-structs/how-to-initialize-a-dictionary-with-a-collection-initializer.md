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
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a><span data-ttu-id="79d54-102">Koleksiyon başlatıcısı ile bir sözlük başlatma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="79d54-102">How to initialize a dictionary with a collection initializer (C# Programming Guide)</span></span>

<span data-ttu-id="79d54-103">Bir <xref:System.Collections.Generic.Dictionary%602> anahtar/değer çiftleri koleksiyonu içerir.</span><span class="sxs-lookup"><span data-stu-id="79d54-103">A <xref:System.Collections.Generic.Dictionary%602> contains a collection of key/value pairs.</span></span> <span data-ttu-id="79d54-104"><xref:System.Collections.Generic.Dictionary%602.Add*> Yöntemi, biri anahtar ve diğeri değer için olmak üzere iki parametre alır.</span><span class="sxs-lookup"><span data-stu-id="79d54-104">Its <xref:System.Collections.Generic.Dictionary%602.Add*> method takes two parameters, one for the key and one for the value.</span></span> <span data-ttu-id="79d54-105">Ya da `Add` yöntemi birden çok <xref:System.Collections.Generic.Dictionary%602>parametre alan herhangi bir koleksiyonu başlatmanın bir yolu, aşağıdaki örnekte gösterildiği gibi her bir parametre kümesini küme ayraçları içine allemektir.</span><span class="sxs-lookup"><span data-stu-id="79d54-105">One way to initialize a <xref:System.Collections.Generic.Dictionary%602>, or any collection whose `Add` method takes multiple parameters, is to enclose each set of parameters in braces as shown in the following example.</span></span> <span data-ttu-id="79d54-106">Diğer bir seçenek de aşağıdaki örnekte gösterilen bir dizin başlatıcısı kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="79d54-106">Another option is to use an index initializer, also shown in the following example.</span></span>

## <a name="example"></a><span data-ttu-id="79d54-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="79d54-107">Example</span></span>

<span data-ttu-id="79d54-108">Aşağıdaki kod örneğinde,, <xref:System.Collections.Generic.Dictionary%602> türünde `StudentName`örneklerle başlatılır.</span><span class="sxs-lookup"><span data-stu-id="79d54-108">In the following code example, a <xref:System.Collections.Generic.Dictionary%602> is initialized with instances of type `StudentName`.</span></span>  <span data-ttu-id="79d54-109">İlk başlatma `Add` yöntemi iki bağımsız değişkenle birlikte kullanır.</span><span class="sxs-lookup"><span data-stu-id="79d54-109">The first initialization uses the `Add` method with two arguments.</span></span> <span data-ttu-id="79d54-110">Derleyici, her `Add` `int` anahtar ve `StudentName` değer çiftlerinin her biri için bir çağrı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="79d54-110">The compiler generates a call to `Add` for each of the pairs of `int` keys and `StudentName` values.</span></span> <span data-ttu-id="79d54-111">İkincisi, `Dictionary` sınıfının ortak bir okuma/yazma Indexer yöntemini kullanır:</span><span class="sxs-lookup"><span data-stu-id="79d54-111">The second uses a public read / write indexer method of the `Dictionary` class:</span></span>

[!code-csharp[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToDictionaryInitializer.cs#HowToDictionaryInitializer)]  

<span data-ttu-id="79d54-112">İlk bildirimde koleksiyonun her bir öğesinde iki ayraç çiftini aklınızda edin.</span><span class="sxs-lookup"><span data-stu-id="79d54-112">Note the two pairs of braces in each element of the collection in the first declaration.</span></span> <span data-ttu-id="79d54-113">En içteki ayraç, `StudentName`için nesne başlatıcısını kapsar ve en dıştaki küme ayraçları `students` <xref:System.Collections.Generic.Dictionary%602>öğesine eklenecek anahtar/değer çifti için başlatıcıyı kapsar.</span><span class="sxs-lookup"><span data-stu-id="79d54-113">The innermost braces enclose the object initializer for the `StudentName`, and the outermost braces enclose the initializer for the key/value pair that will be added to the `students` <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="79d54-114">Son olarak, sözlük için tüm koleksiyon başlatıcısı küme ayraçları içine alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="79d54-114">Finally, the whole collection initializer for the dictionary is enclosed in braces.</span></span> <span data-ttu-id="79d54-115">İkinci başlatmada atamanın sol tarafı anahtardır ve sağ tarafta ise, için `StudentName`bir nesne Başlatıcısı kullanılarak değer bulunur.</span><span class="sxs-lookup"><span data-stu-id="79d54-115">In the second initialization, the left side of the assignment is the key and the right side is the value, using an object initializer for `StudentName`.</span></span>

## <a name="see-also"></a><span data-ttu-id="79d54-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="79d54-116">See also</span></span>

- [<span data-ttu-id="79d54-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="79d54-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="79d54-118">Nesne ve Koleksiyon Başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="79d54-118">Object and Collection Initializers</span></span>](./object-and-collection-initializers.md)
