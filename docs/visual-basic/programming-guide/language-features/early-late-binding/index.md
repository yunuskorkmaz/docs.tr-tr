---
title: Erken ve Geç Bağlama (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 20eb96d0d9f81ec9dfa359edf63a60f72a45aa01
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973231"
---
# <a name="early-and-late-binding-visual-basic"></a><span data-ttu-id="c74a2-102">Erken ve Geç Bağlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c74a2-102">Early and Late Binding (Visual Basic)</span></span>
<span data-ttu-id="c74a2-103">Visual Basic Derleyicisi adlı bir işlem gerçekleştirir `binding` bir nesne bir nesne değişkenine atanan zaman.</span><span class="sxs-lookup"><span data-stu-id="c74a2-103">The Visual Basic compiler performs a process called `binding` when an object is assigned to an object variable.</span></span> <span data-ttu-id="c74a2-104">Bir nesnenin *erken bağlama* onu bir değişkene atandığında bildirilen belirli nesne türünde olması.</span><span class="sxs-lookup"><span data-stu-id="c74a2-104">An object is *early bound* when it is assigned to a variable declared to be of a specific object type.</span></span> <span data-ttu-id="c74a2-105">Erken bağlama nesnelerine derleyicinin bellek ayırma ve uygulama yürütülmeden önce diğer iyileştirmeler gerçekleştirmek izin verin.</span><span class="sxs-lookup"><span data-stu-id="c74a2-105">Early bound objects allow the compiler to allocate memory and perform other optimizations before an application executes.</span></span> <span data-ttu-id="c74a2-106">Örneğin, aşağıdaki kod parçası, türünde bir değişkeni bildirir <xref:System.IO.FileStream>:</span><span class="sxs-lookup"><span data-stu-id="c74a2-106">For example, the following code fragment declares a variable to be of type <xref:System.IO.FileStream>:</span></span>  
  
 [!code-vb[VbVbalrOOP#90](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#90)]  
  
 <span data-ttu-id="c74a2-107">Çünkü <xref:System.IO.FileStream> bir belirli nesne türü, atanan örnek `FS` erken bağlama.</span><span class="sxs-lookup"><span data-stu-id="c74a2-107">Because <xref:System.IO.FileStream> is a specific object type, the instance assigned to `FS` is early bound.</span></span>  
  
 <span data-ttu-id="c74a2-108">Bunun aksine, bir nesnedir *geç bağlama* onu bir değişkene atandığında bildirilen türü olmasını `Object`.</span><span class="sxs-lookup"><span data-stu-id="c74a2-108">By contrast, an object is *late bound* when it is assigned to a variable declared to be of type `Object`.</span></span> <span data-ttu-id="c74a2-109">Bu tür nesnelerin herhangi bir nesne başvuruları tutmak ancak çok erken bağlanan nesneleri avantajları eksik.</span><span class="sxs-lookup"><span data-stu-id="c74a2-109">Objects of this type can hold references to any object, but lack many of the advantages of early-bound objects.</span></span> <span data-ttu-id="c74a2-110">Örneğin, aşağıdaki kod parçası tarafından döndürülen bir nesnesini tutacak bir nesne değişkeni bildirir `CreateObject` işlevi:</span><span class="sxs-lookup"><span data-stu-id="c74a2-110">For example, the following code fragment declares an object variable to hold an object returned by the `CreateObject` function:</span></span>  
  
 [!code-vb[VbVbalrOOP#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/LateBinding.vb#91)]  
  
## <a name="advantages-of-early-binding"></a><span data-ttu-id="c74a2-111">Erken bağlama avantajları</span><span class="sxs-lookup"><span data-stu-id="c74a2-111">Advantages of Early Binding</span></span>  
 <span data-ttu-id="c74a2-112">Bunlar daha verimli uygulamalar yield önemli iyileştirmeler yapmak için derleyici izin verdiğinden, mümkün olduğunca erken bağlanan nesneleri kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c74a2-112">You should use early-bound objects whenever possible, because they allow the compiler to make important optimizations that yield more efficient applications.</span></span> <span data-ttu-id="c74a2-113">Erken bağlı nesneler geç bağlama nesnelerini önemli ölçüde daha hızlı ve kodunuzu okunması ve düzenlenmesi hangi türdeki nesneleri tam olarak kullanıldığı belirterek daha kolay hale getirmek.</span><span class="sxs-lookup"><span data-stu-id="c74a2-113">Early-bound objects are significantly faster than late-bound objects and make your code easier to read and maintain by stating exactly what kind of objects are being used.</span></span> <span data-ttu-id="c74a2-114">Visual Studio tümleşik geliştirme ortamı (IDE) düzenleme gibi tam olarak hangi tür nesnenin çalıştığınız belirlemek için otomatik kod tamamlama ve dinamik Yardım gibi yararlı özellikleri sağlayan erken bağlama başka bir avantajı, kodu.</span><span class="sxs-lookup"><span data-stu-id="c74a2-114">Another advantage to early binding is that it enables useful features such as automatic code completion and Dynamic Help because the Visual Studio integrated development environment (IDE) can determine exactly what type of object you are working with as you edit the code.</span></span> <span data-ttu-id="c74a2-115">Bir program derlendiğinde derleyici hatalarını raporlamak için izin verdiği için erken bağlama sayısını ve çalışma zamanı hataları azaltır.</span><span class="sxs-lookup"><span data-stu-id="c74a2-115">Early binding reduces the number and severity of run-time errors because it allows the compiler to report errors when a program is compiled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c74a2-116">Geç bağlama yalnızca olarak bildirilen tür üyelerine erişmek için kullanılabilir `Public`.</span><span class="sxs-lookup"><span data-stu-id="c74a2-116">Late binding can only be used to access type members that are declared as `Public`.</span></span> <span data-ttu-id="c74a2-117">Olarak bildirilen üyelere erişme `Friend` veya `Protected Friend` bir çalışma zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="c74a2-117">Accessing members declared as `Friend` or `Protected Friend` results in a run-time error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c74a2-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c74a2-118">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>
- [<span data-ttu-id="c74a2-119">Nesne ömrü: Nesnelerin nasıl oluşturulduğunu ve yok</span><span class="sxs-lookup"><span data-stu-id="c74a2-119">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [<span data-ttu-id="c74a2-120">Object Veri Türü</span><span class="sxs-lookup"><span data-stu-id="c74a2-120">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
