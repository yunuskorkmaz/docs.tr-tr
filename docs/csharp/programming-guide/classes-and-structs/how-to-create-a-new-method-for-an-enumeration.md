---
title: Numaralandırma için yeni bir yöntem oluşturma-C# Programlama Kılavuzu
description: C# ' deki bir numaralandırmaya işlevsellik eklemek için uzantı yöntemlerini nasıl kullanacağınızı öğrenin. Bu örnek, notlar adlı bir numaralandırma için geçirme adlı bir genişletme yöntemi gösterir.
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
ms.openlocfilehash: 2714b29d64e18250f0fe379aee1c09c242d3f63f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91174270"
---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a><span data-ttu-id="52c9a-104">Numaralandırma için yeni bir yöntem oluşturma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="52c9a-104">How to create a new method for an enumeration (C# Programming Guide)</span></span>

<span data-ttu-id="52c9a-105">Belirli bir numaralandırma türüne özgü işlevselliği eklemek için uzantı yöntemlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="52c9a-105">You can use extension methods to add functionality specific to a particular enum type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52c9a-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="52c9a-106">Example</span></span>  

 <span data-ttu-id="52c9a-107">Aşağıdaki örnekte, `Grades` sabit listesi bir öğrencinin bir sınıfta alabileceği olası harf çalışmalarını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="52c9a-107">In the following example, the `Grades` enumeration represents the possible letter grades that a student may receive in a class.</span></span> <span data-ttu-id="52c9a-108">Adlandırılmış bir genişletme yöntemi `Passing` türüne eklenir, `Grades` böylece bu türün her örneği, bir geçen sınıfı temsil edip etmediğini "bilir".</span><span class="sxs-lookup"><span data-stu-id="52c9a-108">An extension method named `Passing` is added to the `Grades` type so that each instance of that type now "knows" whether it represents a passing grade or not.</span></span>  
  
 [!code-csharp[csProgGuideExtensionMethods#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#2)]  
  
 <span data-ttu-id="52c9a-109">`Extensions`Sınıfının ayrıca dinamik olarak güncellenen bir statik değişken içerdiğini ve Genişletme yönteminin dönüş değerinin o değişkenin geçerli değerini yansıttığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="52c9a-109">Note that the `Extensions` class also contains a static variable that is updated dynamically and that the return value of the extension method reflects the current value of that variable.</span></span> <span data-ttu-id="52c9a-110">Bu, arka planda uzantı yöntemlerinin tanımlandıkları statik sınıfta doğrudan çağrılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="52c9a-110">This demonstrates that, behind the scenes, extension methods are invoked directly on the static class in which they are defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52c9a-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="52c9a-111">See also</span></span>

- [<span data-ttu-id="52c9a-112">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="52c9a-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="52c9a-113">Uzantı yöntemleri</span><span class="sxs-lookup"><span data-stu-id="52c9a-113">Extension Methods</span></span>](./extension-methods.md)
