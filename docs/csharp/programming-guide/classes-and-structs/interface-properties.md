---
title: Arabirim Özellikleri (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
ms.openlocfilehash: bfa03c7ebe82f3f6a03666d908a5fa9d4e386172
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33325415"
---
# <a name="interface-properties-c-programming-guide"></a><span data-ttu-id="10946-102">Arabirim Özellikleri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="10946-102">Interface Properties (C# Programming Guide)</span></span>
<span data-ttu-id="10946-103">Özellikler bildirilebilir bir [arabirimi](../../../csharp/language-reference/keywords/interface.md).</span><span class="sxs-lookup"><span data-stu-id="10946-103">Properties can be declared on an [interface](../../../csharp/language-reference/keywords/interface.md).</span></span> <span data-ttu-id="10946-104">Arabirim dizin oluşturucu erişimci örneği verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="10946-104">The following is an example of an interface indexer accessor:</span></span>  
  
 [!code-csharp[csProgGuideProperties#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_1.cs)]  
  
 <span data-ttu-id="10946-105">Bir arabirim özelliği erişimcisi gövde yok.</span><span class="sxs-lookup"><span data-stu-id="10946-105">The accessor of an interface property does not have a body.</span></span> <span data-ttu-id="10946-106">Bu nedenle, özelliğin okuma-yazma, salt okunur veya sadece yazılabilir olup olmadığını belirtmek için erişimciler amacı budur.</span><span class="sxs-lookup"><span data-stu-id="10946-106">Thus, the purpose of the accessors is to indicate whether the property is read-write, read-only, or write-only.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10946-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="10946-107">Example</span></span>  
 <span data-ttu-id="10946-108">Bu örnekte, arabirim `IEmployee` bir okuma-yazma özelliği var. `Name`ve salt okunur bir özellik `Counter`.</span><span class="sxs-lookup"><span data-stu-id="10946-108">In this example, the interface `IEmployee` has a read-write property, `Name`, and a read-only property, `Counter`.</span></span> <span data-ttu-id="10946-109">Sınıf `Employee` uygulayan `IEmployee` arabirim ve bu iki özellik kullanır.</span><span class="sxs-lookup"><span data-stu-id="10946-109">The class `Employee` implements the `IEmployee` interface and uses these two properties.</span></span> <span data-ttu-id="10946-110">Programın adını yeni bir çalışan ve çalışanların geçerli sayısını okur ve çalışan adını ve hesaplanan çalışan numarasını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="10946-110">The program reads the name of a new employee and the current number of employees and displays the employee name and the computed employee number.</span></span>  
  
 <span data-ttu-id="10946-111">Üye bildirilmedi arabirimi başvuran özelliği tam adını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="10946-111">You could use the fully qualified name of the property, which references the interface in which the member is declared.</span></span> <span data-ttu-id="10946-112">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="10946-112">For example:</span></span>  
  
 [!code-csharp[csProgGuideProperties#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_2.cs)]  
  
 <span data-ttu-id="10946-113">Bu adlı [açık arabirim uygulaması](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md).</span><span class="sxs-lookup"><span data-stu-id="10946-113">This is called [Explicit Interface Implementation](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md).</span></span> <span data-ttu-id="10946-114">Örneğin, varsa sınıfı `Employee` iki arabirimler uygulama `ICitizen` ve `IEmployee` ve her iki arabirimde `Name` özelliği, açık arabirim üye uygulaması gerekli olacak.</span><span class="sxs-lookup"><span data-stu-id="10946-114">For example, if the class `Employee` is implementing two interfaces `ICitizen` and `IEmployee` and both interfaces have the `Name` property, the explicit interface member implementation will be necessary.</span></span> <span data-ttu-id="10946-115">Diğer bir deyişle, aşağıdaki özellik bildirimi:</span><span class="sxs-lookup"><span data-stu-id="10946-115">That is, the following property declaration:</span></span>  
  
 [!code-csharp[csProgGuideProperties#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_2.cs)]  
  
 <span data-ttu-id="10946-116">uygulayan `Name` özellikte `IEmployee` arabirimi, aşağıdaki bildirimi sırasında:</span><span class="sxs-lookup"><span data-stu-id="10946-116">implements the `Name` property on the `IEmployee` interface, while the following declaration:</span></span>  
  
 [!code-csharp[csProgGuideProperties#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_3.cs)]  
  
 <span data-ttu-id="10946-117">uygulayan `Name` özellikte `ICitizen` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="10946-117">implements the `Name` property on the `ICitizen` interface.</span></span>  
  
 [!code-csharp[csProgGuideProperties#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_4.cs)]  
  
  **`210 Hazem Abolrous`**    
## <a name="sample-output"></a><span data-ttu-id="10946-118">Örnek Çıktı</span><span class="sxs-lookup"><span data-stu-id="10946-118">Sample Output</span></span>  
 `Enter number of employees: 210`  
  
 `Enter the name of the new employee: Hazem Abolrous`  
  
 `The employee information:`  
  
 `Employee number: 211`  
  
 `Employee name: Hazem Abolrous`  
  
## <a name="see-also"></a><span data-ttu-id="10946-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="10946-119">See Also</span></span>  
 [<span data-ttu-id="10946-120">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="10946-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="10946-121">Özellikler</span><span class="sxs-lookup"><span data-stu-id="10946-121">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [<span data-ttu-id="10946-122">Özellikleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="10946-122">Using Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
 [<span data-ttu-id="10946-123">Özellikler ve Dizin Oluşturucular Arasında Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="10946-123">Comparison Between Properties and Indexers</span></span>](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)  
 [<span data-ttu-id="10946-124">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="10946-124">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)  
 [<span data-ttu-id="10946-125">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="10946-125">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)
