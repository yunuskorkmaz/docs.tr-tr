---
title: "Arabirim Özellikleri (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1da48adf73cccb28d9cff641948db52b40b8c1bb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="interface-properties-c-programming-guide"></a><span data-ttu-id="69b45-102">Arabirim Özellikleri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="69b45-102">Interface Properties (C# Programming Guide)</span></span>
<span data-ttu-id="69b45-103">Özellikler bildirilebilir bir [arabirimi](../../../csharp/language-reference/keywords/interface.md).</span><span class="sxs-lookup"><span data-stu-id="69b45-103">Properties can be declared on an [interface](../../../csharp/language-reference/keywords/interface.md).</span></span> <span data-ttu-id="69b45-104">Arabirim dizin oluşturucu erişimci örneği verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="69b45-104">The following is an example of an interface indexer accessor:</span></span>  
  
 [!code-csharp[csProgGuideProperties#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_1.cs)]  
  
 <span data-ttu-id="69b45-105">Bir arabirim özelliği erişimcisi gövde yok.</span><span class="sxs-lookup"><span data-stu-id="69b45-105">The accessor of an interface property does not have a body.</span></span> <span data-ttu-id="69b45-106">Bu nedenle, özelliğin okuma-yazma, salt okunur veya sadece yazılabilir olup olmadığını belirtmek için erişimciler amacı budur.</span><span class="sxs-lookup"><span data-stu-id="69b45-106">Thus, the purpose of the accessors is to indicate whether the property is read-write, read-only, or write-only.</span></span>  
  
## <a name="example"></a><span data-ttu-id="69b45-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="69b45-107">Example</span></span>  
 <span data-ttu-id="69b45-108">Bu örnekte, arabirim `IEmployee` bir okuma-yazma özelliği var. `Name`ve salt okunur bir özellik `Counter`.</span><span class="sxs-lookup"><span data-stu-id="69b45-108">In this example, the interface `IEmployee` has a read-write property, `Name`, and a read-only property, `Counter`.</span></span> <span data-ttu-id="69b45-109">Sınıf `Employee` uygulayan `IEmployee` arabirim ve bu iki özellik kullanır.</span><span class="sxs-lookup"><span data-stu-id="69b45-109">The class `Employee` implements the `IEmployee` interface and uses these two properties.</span></span> <span data-ttu-id="69b45-110">Programın adını yeni bir çalışan ve çalışanların geçerli sayısını okur ve çalışan adını ve hesaplanan çalışan numarasını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="69b45-110">The program reads the name of a new employee and the current number of employees and displays the employee name and the computed employee number.</span></span>  
  
 <span data-ttu-id="69b45-111">Üye bildirilmedi arabirimi başvuran özelliği tam adını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="69b45-111">You could use the fully qualified name of the property, which references the interface in which the member is declared.</span></span> <span data-ttu-id="69b45-112">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="69b45-112">For example:</span></span>  
  
 [!code-csharp[csProgGuideProperties#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_2.cs)]  
  
 <span data-ttu-id="69b45-113">Bu adlı [açık arabirim uygulaması](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md).</span><span class="sxs-lookup"><span data-stu-id="69b45-113">This is called [Explicit Interface Implementation](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md).</span></span> <span data-ttu-id="69b45-114">Örneğin, varsa sınıfı `Employee` iki arabirimler uygulama `ICitizen` ve `IEmployee` ve her iki arabirimde `Name` özelliği, açık arabirim üye uygulaması gerekli olacak.</span><span class="sxs-lookup"><span data-stu-id="69b45-114">For example, if the class `Employee` is implementing two interfaces `ICitizen` and `IEmployee` and both interfaces have the `Name` property, the explicit interface member implementation will be necessary.</span></span> <span data-ttu-id="69b45-115">Diğer bir deyişle, aşağıdaki özellik bildirimi:</span><span class="sxs-lookup"><span data-stu-id="69b45-115">That is, the following property declaration:</span></span>  
  
 [!code-csharp[csProgGuideProperties#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_2.cs)]  
  
 <span data-ttu-id="69b45-116">uygulayan `Name` özellikte `IEmployee` arabirimi, aşağıdaki bildirimi sırasında:</span><span class="sxs-lookup"><span data-stu-id="69b45-116">implements the `Name` property on the `IEmployee` interface, while the following declaration:</span></span>  
  
 [!code-csharp[csProgGuideProperties#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_3.cs)]  
  
 <span data-ttu-id="69b45-117">uygulayan `Name` özellikte `ICitizen` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="69b45-117">implements the `Name` property on the `ICitizen` interface.</span></span>  
  
 [!code-csharp[csProgGuideProperties#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_4.cs)]  
  
  **`210 Hazem Abolrous`**    
## <a name="sample-output"></a><span data-ttu-id="69b45-118">Örnek Çıktı</span><span class="sxs-lookup"><span data-stu-id="69b45-118">Sample Output</span></span>  
 `Enter number of employees: 210`  
  
 `Enter the name of the new employee: Hazem Abolrous`  
  
 `The employee information:`  
  
 `Employee number: 211`  
  
 `Employee name: Hazem Abolrous`  
  
## <a name="see-also"></a><span data-ttu-id="69b45-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="69b45-119">See Also</span></span>  
 [<span data-ttu-id="69b45-120">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="69b45-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="69b45-121">Özellikleri</span><span class="sxs-lookup"><span data-stu-id="69b45-121">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [<span data-ttu-id="69b45-122">Özellikleri kullanma</span><span class="sxs-lookup"><span data-stu-id="69b45-122">Using Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
 [<span data-ttu-id="69b45-123">Özellikler ve dizin oluşturucular arasında karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="69b45-123">Comparison Between Properties and Indexers</span></span>](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)  
 [<span data-ttu-id="69b45-124">Dizin oluşturucular</span><span class="sxs-lookup"><span data-stu-id="69b45-124">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)  
 [<span data-ttu-id="69b45-125">Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="69b45-125">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)
