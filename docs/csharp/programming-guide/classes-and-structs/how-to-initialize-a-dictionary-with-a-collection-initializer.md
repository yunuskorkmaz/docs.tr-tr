---
title: Koleksiyon başlatıcısı ile bir sözlük başlatma-C# Programlama Kılavuzu
description: Add yöntemini veya bir dizin başlatıcısı kullanarak C# ' de bir sözlüğü nasıl başlatacağınızı öğrenin. Bu örnekte her iki seçenek de gösterilmektedir.
ms.date: 12/20/2018
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.topic: how-to
ms.custom: contperfq2
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
ms.openlocfilehash: 667b39076f01ab59eb64cf31d7c1dbb921500135
ms.sourcegitcommit: 30e9e11dfd90112b8eec6406186ba3533f21eba1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2020
ms.locfileid: "95099354"
---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a><span data-ttu-id="9b935-104">Koleksiyon başlatıcısı ile bir sözlük başlatma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="9b935-104">How to initialize a dictionary with a collection initializer (C# Programming Guide)</span></span>

<span data-ttu-id="9b935-105">Bir <xref:System.Collections.Generic.Dictionary%602> anahtar/değer çiftleri koleksiyonu içerir.</span><span class="sxs-lookup"><span data-stu-id="9b935-105">A <xref:System.Collections.Generic.Dictionary%602> contains a collection of key/value pairs.</span></span> <span data-ttu-id="9b935-106"><xref:System.Collections.Generic.Dictionary%602.Add%2A>Yöntemi, biri anahtar ve diğeri değer için olmak üzere iki parametre alır.</span><span class="sxs-lookup"><span data-stu-id="9b935-106">Its <xref:System.Collections.Generic.Dictionary%602.Add%2A> method takes two parameters, one for the key and one for the value.</span></span> <span data-ttu-id="9b935-107"><xref:System.Collections.Generic.Dictionary%602>Ya da yöntemi birden çok parametre alan herhangi bir koleksiyonu başlatmanın bir yolu `Add` , aşağıdaki örnekte gösterildiği gibi her bir parametre kümesini küme ayraçları içine allemektir.</span><span class="sxs-lookup"><span data-stu-id="9b935-107">One way to initialize a <xref:System.Collections.Generic.Dictionary%602>, or any collection whose `Add` method takes multiple parameters, is to enclose each set of parameters in braces as shown in the following example.</span></span> <span data-ttu-id="9b935-108">Diğer bir seçenek de aşağıdaki örnekte gösterilen bir dizin başlatıcısı kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="9b935-108">Another option is to use an index initializer, also shown in the following example.</span></span>

## <a name="example"></a><span data-ttu-id="9b935-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="9b935-109">Example</span></span>

<span data-ttu-id="9b935-110">Aşağıdaki kod örneğinde,, <xref:System.Collections.Generic.Dictionary%602> türünde örneklerle başlatılır `StudentName` .</span><span class="sxs-lookup"><span data-stu-id="9b935-110">In the following code example, a <xref:System.Collections.Generic.Dictionary%602> is initialized with instances of type `StudentName`.</span></span>  <span data-ttu-id="9b935-111">İlk başlatma `Add` yöntemi iki bağımsız değişkenle birlikte kullanır.</span><span class="sxs-lookup"><span data-stu-id="9b935-111">The first initialization uses the `Add` method with two arguments.</span></span> <span data-ttu-id="9b935-112">Derleyici, `Add` her `int` anahtar ve değer çiftlerinin her biri için bir çağrı oluşturur `StudentName` .</span><span class="sxs-lookup"><span data-stu-id="9b935-112">The compiler generates a call to `Add` for each of the pairs of `int` keys and `StudentName` values.</span></span> <span data-ttu-id="9b935-113">İkincisi, sınıfının ortak bir okuma/yazma Indexer yöntemini kullanır `Dictionary` :</span><span class="sxs-lookup"><span data-stu-id="9b935-113">The second uses a public read / write indexer method of the `Dictionary` class:</span></span>

[!code-csharp[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToDictionaryInitializer.cs#HowToDictionaryInitializer)]  

<span data-ttu-id="9b935-114">İlk bildirimde koleksiyonun her bir öğesinde iki ayraç çiftini aklınızda edin.</span><span class="sxs-lookup"><span data-stu-id="9b935-114">Note the two pairs of braces in each element of the collection in the first declaration.</span></span> <span data-ttu-id="9b935-115">En içteki ayraç, için nesne başlatıcısını kapsar `StudentName` ve en dıştaki küme ayraçları öğesine eklenecek anahtar/değer çifti için başlatıcıyı kapsar `students` <xref:System.Collections.Generic.Dictionary%602> .</span><span class="sxs-lookup"><span data-stu-id="9b935-115">The innermost braces enclose the object initializer for the `StudentName`, and the outermost braces enclose the initializer for the key/value pair that will be added to the `students` <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="9b935-116">Son olarak, sözlük için tüm koleksiyon başlatıcısı küme ayraçları içine alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="9b935-116">Finally, the whole collection initializer for the dictionary is enclosed in braces.</span></span> <span data-ttu-id="9b935-117">İkinci başlatmada atamanın sol tarafı anahtardır ve sağ tarafta ise, için bir nesne Başlatıcısı kullanılarak değer bulunur `StudentName` .</span><span class="sxs-lookup"><span data-stu-id="9b935-117">In the second initialization, the left side of the assignment is the key and the right side is the value, using an object initializer for `StudentName`.</span></span>

## <a name="see-also"></a><span data-ttu-id="9b935-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9b935-118">See also</span></span>

- [<span data-ttu-id="9b935-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="9b935-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9b935-120">Nesne ve Koleksiyon Başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="9b935-120">Object and Collection Initializers</span></span>](./object-and-collection-initializers.md)
