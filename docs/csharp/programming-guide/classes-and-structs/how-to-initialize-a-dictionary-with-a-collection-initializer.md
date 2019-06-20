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
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a><span data-ttu-id="81646-102">Nasıl (C# programlama Kılavuzu) koleksiyon Başlatıcısı ile bir sözlük başlatma</span><span class="sxs-lookup"><span data-stu-id="81646-102">How to initialize a dictionary with a collection initializer (C# Programming Guide)</span></span>

<span data-ttu-id="81646-103">A <xref:System.Collections.Generic.Dictionary%602> anahtar/değer çiftleri koleksiyonu içerir.</span><span class="sxs-lookup"><span data-stu-id="81646-103">A <xref:System.Collections.Generic.Dictionary%602> contains a collection of key/value pairs.</span></span> <span data-ttu-id="81646-104">Kendi <xref:System.Collections.Generic.Dictionary%602.Add*> yöntemi biri anahtar ve değer için bir tane olmak üzere iki parametre alır.</span><span class="sxs-lookup"><span data-stu-id="81646-104">Its <xref:System.Collections.Generic.Dictionary%602.Add*> method takes two parameters, one for the key and one for the value.</span></span> <span data-ttu-id="81646-105">Başlatmak için tek yönlü bir <xref:System.Collections.Generic.Dictionary%602>, ya da herhangi bir koleksiyon olan `Add` yöntemi birden çok parametre alır, aşağıdaki örnekte gösterildiği gibi her parametre kümesi küme ayraçları içine çevrelemektir.</span><span class="sxs-lookup"><span data-stu-id="81646-105">One way to initialize a <xref:System.Collections.Generic.Dictionary%602>, or any collection whose `Add` method takes multiple parameters, is to enclose each set of parameters in braces as shown in the following example.</span></span> <span data-ttu-id="81646-106">Başka bir seçenek de aşağıdaki örnekte gösterildiği bir dizin Başlatıcı kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="81646-106">Another option is to use an index initializer, also shown in the following example.</span></span>

## <a name="example"></a><span data-ttu-id="81646-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="81646-107">Example</span></span>

<span data-ttu-id="81646-108">Aşağıdaki kod örneğinde, bir <xref:System.Collections.Generic.Dictionary%602> türünün bir örneğini ile başlatılmış `StudentName`.</span><span class="sxs-lookup"><span data-stu-id="81646-108">In the following code example, a <xref:System.Collections.Generic.Dictionary%602> is initialized with instances of type `StudentName`.</span></span>  <span data-ttu-id="81646-109">İlk başlatma kullanır `Add` yöntemi iki bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="81646-109">The first initialization uses the `Add` method with two arguments.</span></span> <span data-ttu-id="81646-110">Derleyici bir çağrı oluşturur `Add` her çiftleri `int` anahtarları ve `StudentName` değerleri.</span><span class="sxs-lookup"><span data-stu-id="81646-110">The compiler generates a call to `Add` for each of the pairs of `int` keys and `StudentName` values.</span></span> <span data-ttu-id="81646-111">İkinci kullandığı ortak okuma / dizin oluşturucu yönteminin yazma `Dictionary` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="81646-111">The second uses a public read / write indexer method of the `Dictionary` class:</span></span>

[!code-csharp[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToDictionaryInitializer.cs#HowToDictionaryInitializer)]  

<span data-ttu-id="81646-112">Küme ayraçları içine ilk bildirimi koleksiyonda her öğeye iki çiftleri unutmayın.</span><span class="sxs-lookup"><span data-stu-id="81646-112">Note the two pairs of braces in each element of the collection in the first declaration.</span></span> <span data-ttu-id="81646-113">Nesne Başlatıcısı için en içteki ayraç içine `StudentName`, ve en dıştaki ayraç içine eklenecek anahtar/değer çifti için Başlatıcı `students` <xref:System.Collections.Generic.Dictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="81646-113">The innermost braces enclose the object initializer for the `StudentName`, and the outermost braces enclose the initializer for the key/value pair that will be added to the `students` <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="81646-114">Son olarak, tüm koleksiyon Başlatıcısı sözlüğü için parantez içine alınır.</span><span class="sxs-lookup"><span data-stu-id="81646-114">Finally, the whole collection initializer for the dictionary is enclosed in braces.</span></span> <span data-ttu-id="81646-115">İkinci ise başlatma sırasında atamanın sol tarafında anahtar ve sağ tarafındaki nesne Başlatıcı kullanarak değer, `StudentName`.</span><span class="sxs-lookup"><span data-stu-id="81646-115">In the second initialization, the left side of the assignment is the key and the right side is the value, using an object initializer for `StudentName`.</span></span>

## <a name="see-also"></a><span data-ttu-id="81646-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="81646-116">See also</span></span>

- [<span data-ttu-id="81646-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="81646-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="81646-118">Nesne ve Koleksiyon Başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="81646-118">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
