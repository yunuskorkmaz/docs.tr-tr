---
title: "Erken ve Geç Bağlama (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- early binding [Visual Basic]
- objects [Visual Basic], late-bound
- objects [Visual Basic], early-bound
- objects [Visual Basic], late bound
- early binding [Visual Basic], Visual Basic compiler
- binding [Visual Basic], late and early
- objects [Visual Basic], early bound
- Visual Basic compiler, early and late binding
- late binding [Visual Basic]
- late binding [Visual Basic], Visual Basic compiler
ms.assetid: d6ff7f1e-b94f-4205-ab8d-5cfa91758724
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: aceffe59fb6043b3089621b9a3f95b0425f9a522
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="early-and-late-binding-visual-basic"></a><span data-ttu-id="e2066-102">Erken ve Geç Bağlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e2066-102">Early and Late Binding (Visual Basic)</span></span>
<span data-ttu-id="e2066-103">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Derleyici adlı bir işlem gerçekleştirir `binding` bir nesne bir nesne değişkenine atanan zaman.</span><span class="sxs-lookup"><span data-stu-id="e2066-103">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler performs a process called `binding` when an object is assigned to an object variable.</span></span> <span data-ttu-id="e2066-104">Bir nesne *erken bağlama* bildirilen belirli nesne türünde olması için ne zaman bir değişkene atanır.</span><span class="sxs-lookup"><span data-stu-id="e2066-104">An object is *early bound* when it is assigned to a variable declared to be of a specific object type.</span></span> <span data-ttu-id="e2066-105">Erken bağlama nesnelerine bellek ayırabilir ve bir uygulama yürütülmeden önce diğer en iyi duruma getirme gerçekleştirmek derleyici izin verin.</span><span class="sxs-lookup"><span data-stu-id="e2066-105">Early bound objects allow the compiler to allocate memory and perform other optimizations before an application executes.</span></span> <span data-ttu-id="e2066-106">Örneğin, aşağıdaki kod parçası türünde olması için bir değişken bildirir <xref:System.IO.FileStream>:</span><span class="sxs-lookup"><span data-stu-id="e2066-106">For example, the following code fragment declares a variable to be of type <xref:System.IO.FileStream>:</span></span>  
  
 [!code-vb[VbVbalrOOP#90](../../../../visual-basic/misc/codesnippet/VisualBasic/early-and-late-binding_1.vb)]  
  
 <span data-ttu-id="e2066-107">Çünkü <xref:System.IO.FileStream> belirli nesne türü, atanan örnek `FS` erken bağlama.</span><span class="sxs-lookup"><span data-stu-id="e2066-107">Because <xref:System.IO.FileStream> is a specific object type, the instance assigned to `FS` is early bound.</span></span>  
  
 <span data-ttu-id="e2066-108">Bunun aksine, bir nesnedir *geç bağlama* ne zaman bir değişkene atanır bildirilen türünde olmasını `Object`.</span><span class="sxs-lookup"><span data-stu-id="e2066-108">By contrast, an object is *late bound* when it is assigned to a variable declared to be of type `Object`.</span></span> <span data-ttu-id="e2066-109">Bu tür nesneler herhangi bir nesne başvuruları tutmak ancak erken bağlama nesneleri avantajları çoğunu eksik.</span><span class="sxs-lookup"><span data-stu-id="e2066-109">Objects of this type can hold references to any object, but lack many of the advantages of early-bound objects.</span></span> <span data-ttu-id="e2066-110">Örneğin, aşağıdaki kod parçası tarafından döndürülen nesne tutmak için bir nesne değişkeni bildirir `CreateObject` işlevi:</span><span class="sxs-lookup"><span data-stu-id="e2066-110">For example, the following code fragment declares an object variable to hold an object returned by the `CreateObject` function:</span></span>  
  
 [!code-vb[VbVbalrOOP#91](../../../../visual-basic/misc/codesnippet/VisualBasic/early-and-late-binding_2.vb)]  
  
## <a name="advantages-of-early-binding"></a><span data-ttu-id="e2066-111">Erken bağlama avantajları</span><span class="sxs-lookup"><span data-stu-id="e2066-111">Advantages of Early Binding</span></span>  
 <span data-ttu-id="e2066-112">Daha verimli uygulamaları verim önemli iyileştirmeler yapmak için derleyici izin verdiğinden, mümkün olduğunda, erken bağlama nesneleri kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e2066-112">You should use early-bound objects whenever possible, because they allow the compiler to make important optimizations that yield more efficient applications.</span></span> <span data-ttu-id="e2066-113">Erken bağlama nesneleri geç bağlama nesneleri önemli ölçüde daha hızlıdır ve kodunuzu okuyun ve tam olarak ne tür bir nesneleri kullanıldığından belirterek sürdürmek daha kolay hale.</span><span class="sxs-lookup"><span data-stu-id="e2066-113">Early-bound objects are significantly faster than late-bound objects and make your code easier to read and maintain by stating exactly what kind of objects are being used.</span></span> <span data-ttu-id="e2066-114">Erken bağlama başka bir avantajı olduğundan, otomatik kod tamamlama ve dinamik Yardım gibi kullanışlı özellikler olanak tanıdığı olduğu [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] tümleşik geliştirme ortamı (IDE) düzenleme gibi tam olarak hangi nesne türünü çalıştığınız belirleyebilir kod.</span><span class="sxs-lookup"><span data-stu-id="e2066-114">Another advantage to early binding is that it enables useful features such as automatic code completion and Dynamic Help because the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] integrated development environment (IDE) can determine exactly what type of object you are working with as you edit the code.</span></span> <span data-ttu-id="e2066-115">Bir program derlendiğinde derleyici hatalarını raporlamak izin verdiği için erken bağlama sayısı ve önem derecesi çalışma zamanı hataları azaltır.</span><span class="sxs-lookup"><span data-stu-id="e2066-115">Early binding reduces the number and severity of run-time errors because it allows the compiler to report errors when a program is compiled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e2066-116">Geç bağlama yalnızca kullanılabilir olarak bildirilen tür üyeleri erişmek için `Public`.</span><span class="sxs-lookup"><span data-stu-id="e2066-116">Late binding can only be used to access type members that are declared as `Public`.</span></span> <span data-ttu-id="e2066-117">Üyelere erişme bildirilen `Friend` veya `Protected Friend` bir çalışma zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="e2066-117">Accessing members declared as `Friend` or `Protected Friend` results in a run-time error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2066-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e2066-118">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>  
 [<span data-ttu-id="e2066-119">Nesne ömrü: Nesneleri oluşturma ve yok etme</span><span class="sxs-lookup"><span data-stu-id="e2066-119">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)  
 [<span data-ttu-id="e2066-120">Nesne veri türü</span><span class="sxs-lookup"><span data-stu-id="e2066-120">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
