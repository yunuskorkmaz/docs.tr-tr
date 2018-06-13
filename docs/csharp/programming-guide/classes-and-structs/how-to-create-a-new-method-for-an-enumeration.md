---
title: 'Nasıl yapılır: Numaralandırma için Yeni bir Yöntem Oluşturma (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
ms.openlocfilehash: 8de44cbddf26af45245709d0e28d2d157256ce59
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33313039"
---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a><span data-ttu-id="559d3-102">Nasıl yapılır: Numaralandırma için Yeni bir Yöntem Oluşturma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="559d3-102">How to: Create a New Method for an Enumeration (C# Programming Guide)</span></span>
<span data-ttu-id="559d3-103">Belirli numaralandırma türü için özel işlevsellik eklemek için genişletme yöntemleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="559d3-103">You can use extension methods to add functionality specific to a particular enum type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="559d3-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="559d3-104">Example</span></span>  
 <span data-ttu-id="559d3-105">Aşağıdaki örnekte, `Grades` numaralandırma öğrencinin bir sınıfta alabilirsiniz olası harf dereceleri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="559d3-105">In the following example, the `Grades` enumeration represents the possible letter grades that a student may receive in a class.</span></span> <span data-ttu-id="559d3-106">Adlı bir genişletme yöntemi `Passing` eklenen `Grades` türü artık her örneği bilir"veya değil, geçirme düzeyde temsil edip etmediğini böylece" yazın.</span><span class="sxs-lookup"><span data-stu-id="559d3-106">An extension method named `Passing` is added to the `Grades` type so that each instance of that type now "knows" whether it represents a passing grade or not.</span></span>  
  
 [!code-csharp[csProgGuideExtensionMethods#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-create-a-new-method-for-an-enumeration_1.cs)]  
  
 <span data-ttu-id="559d3-107">Unutmayın `Extensions` sınıfı ayrıca dinamik olarak güncelleştirilen bir statik değişken içerir ve uzantı yönteminin dönüş değeri bu değişkenin geçerli değeri yansıtır.</span><span class="sxs-lookup"><span data-stu-id="559d3-107">Note that the `Extensions` class also contains a static variable that is updated dynamically and that the return value of the extension method reflects the current value of that variable.</span></span> <span data-ttu-id="559d3-108">Bu arka planda tanımlı doğrudan statik sınıf üzerinde genişletme yöntemleri çağrılır, gösterir.</span><span class="sxs-lookup"><span data-stu-id="559d3-108">This demonstrates that, behind the scenes, extension methods are invoked directly on the static class in which they are defined.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="559d3-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="559d3-109">Compiling the Code</span></span>  
 <span data-ttu-id="559d3-110">Bu kodu çalıştırmak için kopyalayın ve Visual Studio'da oluşturulan bir Visual C# konsol uygulaması projesi yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="559d3-110">To run this code, copy and paste it into a Visual C# console application project that has been created in Visual Studio.</span></span> <span data-ttu-id="559d3-111">Varsayılan olarak, bu proje 3.5 sürümünü hedefler [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], ve System.Core.dll bir başvuru içeriyor ve bir `using` System.Linq yönergesi.</span><span class="sxs-lookup"><span data-stu-id="559d3-111">By default, this project targets version 3.5 of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], and it has a reference to System.Core.dll and a `using` directive for System.Linq.</span></span> <span data-ttu-id="559d3-112">Bir veya daha fazla bu gereksinimleri projeden eksikse, bunları el ile ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="559d3-112">If one or more of these requirements are missing from the project, you can add them manually.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="559d3-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="559d3-113">See Also</span></span>  
 [<span data-ttu-id="559d3-114">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="559d3-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="559d3-115">Genişletme Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="559d3-115">Extension Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
