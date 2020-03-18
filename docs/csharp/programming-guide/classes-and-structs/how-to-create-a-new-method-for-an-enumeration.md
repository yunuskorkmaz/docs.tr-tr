---
title: Numaralandırma için yeni bir yöntem nasıl oluşturulur - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
ms.openlocfilehash: 0d8e562342239c8ac3c53e05086ede9c234d0b63
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705658"
---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a><span data-ttu-id="fb601-102">Numaralandırma için yeni bir yöntem nasıl oluşturulur (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="fb601-102">How to create a new method for an enumeration (C# Programming Guide)</span></span>
<span data-ttu-id="fb601-103">Belirli bir enum türüne özgü işlevsellik eklemek için uzantı yöntemlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fb601-103">You can use extension methods to add functionality specific to a particular enum type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb601-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="fb601-104">Example</span></span>  
 <span data-ttu-id="fb601-105">Aşağıdaki örnekte, `Grades` numaralandırma, bir öğrencinin bir sınıfta alabileceği olası harf notlarını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fb601-105">In the following example, the `Grades` enumeration represents the possible letter grades that a student may receive in a class.</span></span> <span data-ttu-id="fb601-106">Bu türdeki `Passing` her örneğin `Grades` artık bir geçer notu temsil edip etmediğini "bilmesi" için türe adlandırılmış bir uzantı yöntemi eklenir.</span><span class="sxs-lookup"><span data-stu-id="fb601-106">An extension method named `Passing` is added to the `Grades` type so that each instance of that type now "knows" whether it represents a passing grade or not.</span></span>  
  
 [!code-csharp[csProgGuideExtensionMethods#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#2)]  
  
 <span data-ttu-id="fb601-107">`Extensions` Sınıfın dinamik olarak güncelleştirilen statik bir değişken de içerdiğini ve uzantı yönteminin dönüş değerinin bu değişkenin geçerli değerini yansıttığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="fb601-107">Note that the `Extensions` class also contains a static variable that is updated dynamically and that the return value of the extension method reflects the current value of that variable.</span></span> <span data-ttu-id="fb601-108">Bu, arka planda, uzantı yöntemlerinin doğrudan tanımlandığı statik sınıfa çağrıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fb601-108">This demonstrates that, behind the scenes, extension methods are invoked directly on the static class in which they are defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb601-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fb601-109">See also</span></span>

- [<span data-ttu-id="fb601-110">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="fb601-110">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="fb601-111">Genişletme Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="fb601-111">Extension Methods</span></span>](./extension-methods.md)
