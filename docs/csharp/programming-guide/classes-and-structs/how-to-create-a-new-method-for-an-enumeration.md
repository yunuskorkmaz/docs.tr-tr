---
title: Numaralandırma için yeni bir yöntem oluşturma- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
ms.openlocfilehash: 02af55c851392ce5dde4c83fd32d18b927950a3f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73971026"
---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a><span data-ttu-id="0c035-102">Numaralandırma için yeni bir yöntem oluşturma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="0c035-102">How to create a new method for an enumeration (C# Programming Guide)</span></span>
<span data-ttu-id="0c035-103">Belirli bir numaralandırma türüne özgü işlevselliği eklemek için uzantı yöntemlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0c035-103">You can use extension methods to add functionality specific to a particular enum type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c035-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="0c035-104">Example</span></span>  
 <span data-ttu-id="0c035-105">Aşağıdaki örnekte `Grades` numaralandırması, bir öğrencinin bir sınıfta alabileceği olası harf çalışmalarını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0c035-105">In the following example, the `Grades` enumeration represents the possible letter grades that a student may receive in a class.</span></span> <span data-ttu-id="0c035-106">`Passing` adlı bir genişletme yöntemi `Grades` türüne eklenir, böylece bu türün her örneği, bir geçen sınıfı temsil edip etmediğini "bilir".</span><span class="sxs-lookup"><span data-stu-id="0c035-106">An extension method named `Passing` is added to the `Grades` type so that each instance of that type now "knows" whether it represents a passing grade or not.</span></span>  
  
 [!code-csharp[csProgGuideExtensionMethods#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#2)]  
  
 <span data-ttu-id="0c035-107">`Extensions` sınıfının ayrıca dinamik olarak güncellenen bir statik değişken içerdiğini ve Genişletme yönteminin dönüş değerinin o değişkenin geçerli değerini yansıttığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0c035-107">Note that the `Extensions` class also contains a static variable that is updated dynamically and that the return value of the extension method reflects the current value of that variable.</span></span> <span data-ttu-id="0c035-108">Bu, arka planda uzantı yöntemlerinin tanımlandıkları statik sınıfta doğrudan çağrılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0c035-108">This demonstrates that, behind the scenes, extension methods are invoked directly on the static class in which they are defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c035-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0c035-109">See also</span></span>

- [<span data-ttu-id="0c035-110">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0c035-110">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="0c035-111">Genişletme Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="0c035-111">Extension Methods</span></span>](./extension-methods.md)
