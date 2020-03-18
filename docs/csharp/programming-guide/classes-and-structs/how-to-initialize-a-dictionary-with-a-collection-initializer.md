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
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a><span data-ttu-id="0ba1b-102">Bir koleksiyon başharfi (C# Programlama Kılavuzu) ile sözlük başlatma</span><span class="sxs-lookup"><span data-stu-id="0ba1b-102">How to initialize a dictionary with a collection initializer (C# Programming Guide)</span></span>

<span data-ttu-id="0ba1b-103">A, <xref:System.Collections.Generic.Dictionary%602> anahtar/değer çiftleri koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="0ba1b-103">A <xref:System.Collections.Generic.Dictionary%602> contains a collection of key/value pairs.</span></span> <span data-ttu-id="0ba1b-104">Yöntemi <xref:System.Collections.Generic.Dictionary%602.Add%2A> iki parametre, bir anahtar ve değer için bir alır.</span><span class="sxs-lookup"><span data-stu-id="0ba1b-104">Its <xref:System.Collections.Generic.Dictionary%602.Add%2A> method takes two parameters, one for the key and one for the value.</span></span> <span data-ttu-id="0ba1b-105">Bir veya <xref:System.Collections.Generic.Dictionary%602> `Add` yöntem birden çok parametre alan herhangi bir koleksiyonu başlatmanın bir yolu, aşağıdaki örnekte gösterildiği gibi her parametre kümesini ayraçlara bünyesine katıyor.</span><span class="sxs-lookup"><span data-stu-id="0ba1b-105">One way to initialize a <xref:System.Collections.Generic.Dictionary%602>, or any collection whose `Add` method takes multiple parameters, is to enclose each set of parameters in braces as shown in the following example.</span></span> <span data-ttu-id="0ba1b-106">Başka bir seçenek de aşağıdaki örnekte gösterilen bir dizin baş harflerini kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="0ba1b-106">Another option is to use an index initializer, also shown in the following example.</span></span>

## <a name="example"></a><span data-ttu-id="0ba1b-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="0ba1b-107">Example</span></span>

<span data-ttu-id="0ba1b-108">Aşağıdaki kod örneğinde, <xref:System.Collections.Generic.Dictionary%602> a türü `StudentName`örnekleri ile başharfe</span><span class="sxs-lookup"><span data-stu-id="0ba1b-108">In the following code example, a <xref:System.Collections.Generic.Dictionary%602> is initialized with instances of type `StudentName`.</span></span>  <span data-ttu-id="0ba1b-109">İlk başlatma yöntemini `Add` iki bağımsız değişkenle kullanır.</span><span class="sxs-lookup"><span data-stu-id="0ba1b-109">The first initialization uses the `Add` method with two arguments.</span></span> <span data-ttu-id="0ba1b-110">Derleyici, anahtar ve `Add` `StudentName` değer çiftlerinin her biri için bir çağrı oluşturur. `int`</span><span class="sxs-lookup"><span data-stu-id="0ba1b-110">The compiler generates a call to `Add` for each of the pairs of `int` keys and `StudentName` values.</span></span> <span data-ttu-id="0ba1b-111">İkinci `Dictionary` sınıfın ortak okuma / yazma dizinleyici yöntemi kullanır:</span><span class="sxs-lookup"><span data-stu-id="0ba1b-111">The second uses a public read / write indexer method of the `Dictionary` class:</span></span>

[!code-csharp[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToDictionaryInitializer.cs#HowToDictionaryInitializer)]  

<span data-ttu-id="0ba1b-112">İlk bildirimde koleksiyonun her öğesindeki iki çift ayraç çiftine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="0ba1b-112">Note the two pairs of braces in each element of the collection in the first declaration.</span></span> <span data-ttu-id="0ba1b-113">En içteki parantezler `StudentName`nesne baş harflerini içine, en dıştaki parantezler `students` <xref:System.Collections.Generic.Dictionary%602>ise .</span><span class="sxs-lookup"><span data-stu-id="0ba1b-113">The innermost braces enclose the object initializer for the `StudentName`, and the outermost braces enclose the initializer for the key/value pair that will be added to the `students` <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="0ba1b-114">Son olarak, sözlük için tüm toplama başharfleri parantez içinde kapalıdır.</span><span class="sxs-lookup"><span data-stu-id="0ba1b-114">Finally, the whole collection initializer for the dictionary is enclosed in braces.</span></span> <span data-ttu-id="0ba1b-115">İkinci başharfte, atamanın sol tarafı anahtar, sağ tarafı ise değerdir, nesne başharfi kullanır. `StudentName`</span><span class="sxs-lookup"><span data-stu-id="0ba1b-115">In the second initialization, the left side of the assignment is the key and the right side is the value, using an object initializer for `StudentName`.</span></span>

## <a name="see-also"></a><span data-ttu-id="0ba1b-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ba1b-116">See also</span></span>

- [<span data-ttu-id="0ba1b-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0ba1b-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="0ba1b-118">Nesne ve Koleksiyon Başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="0ba1b-118">Object and Collection Initializers</span></span>](./object-and-collection-initializers.md)
