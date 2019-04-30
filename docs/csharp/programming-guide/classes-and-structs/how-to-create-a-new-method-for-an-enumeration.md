---
title: 'Nasıl yapılır: -Numaralandırma için yeni bir yöntem oluşturma C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
ms.openlocfilehash: ebd0433efda43c65ea6d9494a8ec25e8263f5b43
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646507"
---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a><span data-ttu-id="100fc-102">Nasıl yapılır: Numaralandırma için yeni bir yöntem oluşturma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="100fc-102">How to: Create a New Method for an Enumeration (C# Programming Guide)</span></span>
<span data-ttu-id="100fc-103">Belirli numaralandırma türüne özgü işlevsellik eklemek için genişletme yöntemleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="100fc-103">You can use extension methods to add functionality specific to a particular enum type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="100fc-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="100fc-104">Example</span></span>  
 <span data-ttu-id="100fc-105">Aşağıdaki örnekte, `Grades` numaralandırması bir öğrenci bir sınıfta alabileceğiniz olası harf dereceleri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="100fc-105">In the following example, the `Grades` enumeration represents the possible letter grades that a student may receive in a class.</span></span> <span data-ttu-id="100fc-106">Adlı bir genişletme yöntemi `Passing` eklenir `Grades` artık o türün her örneğinin "ya da değil, geçirme sınıf temsil edip etmediğini bilebilmesi" yazın.</span><span class="sxs-lookup"><span data-stu-id="100fc-106">An extension method named `Passing` is added to the `Grades` type so that each instance of that type now "knows" whether it represents a passing grade or not.</span></span>  
  
 [!code-csharp[csProgGuideExtensionMethods#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#2)]  
  
 <span data-ttu-id="100fc-107">Unutmayın `Extensions` sınıfı ayrıca dinamik olarak güncelleştirilen bir statik değişken içerir ve dönüş değeri genişletme yöntemi bu değişkenin geçerli değeri yansıtır.</span><span class="sxs-lookup"><span data-stu-id="100fc-107">Note that the `Extensions` class also contains a static variable that is updated dynamically and that the return value of the extension method reflects the current value of that variable.</span></span> <span data-ttu-id="100fc-108">Bu, arka planda, bunlar tanımlanır doğrudan statik sınıf üzerinde genişletme yöntemleri çağrılır, gösterir.</span><span class="sxs-lookup"><span data-stu-id="100fc-108">This demonstrates that, behind the scenes, extension methods are invoked directly on the static class in which they are defined.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="100fc-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="100fc-109">Compiling the Code</span></span>  
 <span data-ttu-id="100fc-110">Bu kodu çalıştırmak için kopyalayın ve Visual Studio'da oluşturulan bir Visual C# konsol uygulaması projesi yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="100fc-110">To run this code, copy and paste it into a Visual C# console application project that has been created in Visual Studio.</span></span> <span data-ttu-id="100fc-111">Varsayılan olarak, bu proje 3.5 sürümünü hedefleyen [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], ve bir System.Core.dll başvurusu vardır ve bir `using` System.Linq yönergesi.</span><span class="sxs-lookup"><span data-stu-id="100fc-111">By default, this project targets version 3.5 of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], and it has a reference to System.Core.dll and a `using` directive for System.Linq.</span></span> <span data-ttu-id="100fc-112">Projeden bir veya daha fazla bu gereksinimleri eksikse, bunları el ile ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="100fc-112">If one or more of these requirements are missing from the project, you can add them manually.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="100fc-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="100fc-113">See also</span></span>

- [<span data-ttu-id="100fc-114">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="100fc-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="100fc-115">Genişletme Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="100fc-115">Extension Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
