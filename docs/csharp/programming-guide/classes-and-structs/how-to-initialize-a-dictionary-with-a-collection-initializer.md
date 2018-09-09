---
title: Nasıl (C# programlama Kılavuzu) koleksiyon Başlatıcısı ile bir sözlük başlatma
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
ms.openlocfilehash: ca2f508e5500cc135b2712362bcfb71778a664c1
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44227343"
---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a><span data-ttu-id="d19f0-102">Nasıl (C# programlama Kılavuzu) koleksiyon Başlatıcısı ile bir sözlük başlatma</span><span class="sxs-lookup"><span data-stu-id="d19f0-102">How to initialize a dictionary with a collection initializer (C# Programming Guide)</span></span>

<span data-ttu-id="d19f0-103">A <xref:System.Collections.Generic.Dictionary%602> anahtar/değer çiftleri koleksiyonu içerir.</span><span class="sxs-lookup"><span data-stu-id="d19f0-103">A <xref:System.Collections.Generic.Dictionary%602> contains a collection of key/value pairs.</span></span> <span data-ttu-id="d19f0-104">Kendi <xref:System.Collections.Generic.Dictionary%602.Add*> yöntemi biri anahtar ve değer için bir tane olmak üzere iki parametre alır.</span><span class="sxs-lookup"><span data-stu-id="d19f0-104">Its <xref:System.Collections.Generic.Dictionary%602.Add*> method takes two parameters, one for the key and one for the value.</span></span> <span data-ttu-id="d19f0-105">Başlatmak için bir <xref:System.Collections.Generic.Dictionary%602>, ya da herhangi bir koleksiyon olan `Add` yöntemi birden çok parametre alır, aşağıdaki örnekte gösterildiği gibi her parametre kümesi ayraçlarının içine alın.</span><span class="sxs-lookup"><span data-stu-id="d19f0-105">To initialize a <xref:System.Collections.Generic.Dictionary%602>, or any collection whose `Add` method takes multiple parameters, enclose each set of parameters in braces as shown in the following example.</span></span>

## <a name="example"></a><span data-ttu-id="d19f0-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="d19f0-106">Example</span></span>

<span data-ttu-id="d19f0-107">Aşağıdaki kod örneğinde, bir <xref:System.Collections.Generic.Dictionary%602> türünün bir örneğini ile başlatılmış `StudentName`.</span><span class="sxs-lookup"><span data-stu-id="d19f0-107">In the following code example, a <xref:System.Collections.Generic.Dictionary%602> is initialized with instances of type `StudentName`.</span></span>  
  
[!code-csharp[csProgGuideLINQ#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-a-dictionary-with-a-collection-initializer_1.cs)]

<span data-ttu-id="d19f0-108">Küme ayraçları içine koleksiyonun her öğesine iki çiftleri unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d19f0-108">Note the two pairs of braces in each element of the collection.</span></span> <span data-ttu-id="d19f0-109">Nesne Başlatıcısı için en içteki ayraç içine `StudentName`, ve en dıştaki ayraç içine eklenecek anahtar/değer çifti için Başlatıcı `students` <xref:System.Collections.Generic.Dictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="d19f0-109">The innermost braces enclose the object initializer for the `StudentName`, and the outermost braces enclose the initializer for the key/value pair that will be added to the `students` <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="d19f0-110">Son olarak, tüm koleksiyon Başlatıcısı sözlüğü için parantez içine alınır.</span><span class="sxs-lookup"><span data-stu-id="d19f0-110">Finally, the whole collection initializer for the dictionary is enclosed in braces.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="d19f0-111">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="d19f0-111">Compiling the code</span></span>

<span data-ttu-id="d19f0-112">Bu kodu çalıştırmak için kopyalayın ve Visual Studio'da oluşturulan bir Visual C# konsol uygulaması projesi sınıfı yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="d19f0-112">To run this code, copy and paste the class into a Visual C# console application project that has been created in Visual Studio.</span></span> <span data-ttu-id="d19f0-113">Varsayılan olarak, bu proje 3.5 sürümünü hedefleyen [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], ve System.Core.dll ve kullanarak bir başvuru olduğundan System.Linq yönergesi.</span><span class="sxs-lookup"><span data-stu-id="d19f0-113">By default, this project targets version 3.5 of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], and it has a reference to System.Core.dll and a using directive for System.Linq.</span></span> <span data-ttu-id="d19f0-114">Projeden bir veya daha fazla bu gereksinimleri eksikse, bunları el ile ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d19f0-114">If one or more of these requirements are missing from the project, you can add them manually.</span></span>

## <a name="see-also"></a><span data-ttu-id="d19f0-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d19f0-115">See also</span></span>

- [<span data-ttu-id="d19f0-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="d19f0-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="d19f0-117">Nesne ve Koleksiyon Başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="d19f0-117">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
