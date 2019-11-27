---
title: Erken ve Geç Bağlama
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
ms.openlocfilehash: bd70d8642c18e9bc2baba8128ec908c88e0477ce
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345179"
---
# <a name="early-and-late-binding-visual-basic"></a><span data-ttu-id="ae21f-102">Erken ve Geç Bağlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae21f-102">Early and Late Binding (Visual Basic)</span></span>
<span data-ttu-id="ae21f-103">Visual Basic derleyici, nesne değişkenine bir nesne atandığında `binding` adlı bir işlem gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="ae21f-103">The Visual Basic compiler performs a process called `binding` when an object is assigned to an object variable.</span></span> <span data-ttu-id="ae21f-104">Bir nesne, belirli bir nesne türü olarak belirtilen bir değişkene atandığında *erken bağlanır* .</span><span class="sxs-lookup"><span data-stu-id="ae21f-104">An object is *early bound* when it is assigned to a variable declared to be of a specific object type.</span></span> <span data-ttu-id="ae21f-105">Erken bağlantılı nesneler, derleyicinin bellek ayırmasını ve uygulama yürütmeden önce diğer iyileştirmeler gerçekleştirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="ae21f-105">Early bound objects allow the compiler to allocate memory and perform other optimizations before an application executes.</span></span> <span data-ttu-id="ae21f-106">Örneğin, aşağıdaki kod parçası <xref:System.IO.FileStream>türünde olması için bir değişken bildirir:</span><span class="sxs-lookup"><span data-stu-id="ae21f-106">For example, the following code fragment declares a variable to be of type <xref:System.IO.FileStream>:</span></span>  
  
 [!code-vb[VbVbalrOOP#90](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#90)]  
  
 <span data-ttu-id="ae21f-107"><xref:System.IO.FileStream> belirli bir nesne türü olduğundan, `FS` atanan örnek erken bağlanır.</span><span class="sxs-lookup"><span data-stu-id="ae21f-107">Because <xref:System.IO.FileStream> is a specific object type, the instance assigned to `FS` is early bound.</span></span>  
  
 <span data-ttu-id="ae21f-108">Buna karşılık, bir nesne, `Object`türünde olduğu belirtilen bir değişkene atandığında *geç bağlanır* .</span><span class="sxs-lookup"><span data-stu-id="ae21f-108">By contrast, an object is *late bound* when it is assigned to a variable declared to be of type `Object`.</span></span> <span data-ttu-id="ae21f-109">Bu türdeki nesneler herhangi bir nesneye başvuruları tutabilir, ancak erken bağlantılı nesnelerin avantajlarından birçoğuna sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="ae21f-109">Objects of this type can hold references to any object, but lack many of the advantages of early-bound objects.</span></span> <span data-ttu-id="ae21f-110">Örneğin, aşağıdaki kod parçası `CreateObject` işlevi tarafından döndürülen bir nesneyi tutacak bir nesne değişkeni bildirir:</span><span class="sxs-lookup"><span data-stu-id="ae21f-110">For example, the following code fragment declares an object variable to hold an object returned by the `CreateObject` function:</span></span>  
  
 [!code-vb[VbVbalrOOP#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/LateBinding.vb#91)]  
  
## <a name="advantages-of-early-binding"></a><span data-ttu-id="ae21f-111">Erken bağlamanın avantajları</span><span class="sxs-lookup"><span data-stu-id="ae21f-111">Advantages of Early Binding</span></span>  
 <span data-ttu-id="ae21f-112">Derleyicinin daha verimli uygulamalar sunan önemli iyileştirmeler yapmasına izin verdiklerinden, mümkün olduğunda erken bağlanan nesneleri kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ae21f-112">You should use early-bound objects whenever possible, because they allow the compiler to make important optimizations that yield more efficient applications.</span></span> <span data-ttu-id="ae21f-113">Erken bağlantılı nesneler, geç bağlantılı nesnelerden önemli ölçüde daha hızlıdır ve tam olarak hangi tür nesnelerin kullanıldığını belirterek kodunuzun okunmasını ve bakımını daha kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="ae21f-113">Early-bound objects are significantly faster than late-bound objects and make your code easier to read and maintain by stating exactly what kind of objects are being used.</span></span> <span data-ttu-id="ae21f-114">Erken bağlamanın bir diğer avantajı da, Visual Studio tümleşik geliştirme ortamı (IDE), sizin düzenlediğiniz sırada çalıştığınız nesne türünü tam olarak belirleyebildiğinden, otomatik kod tamamlama ve dinamik yardım gibi faydalı özellikleri mümkün hale getirmenizi sağlar. kodudur.</span><span class="sxs-lookup"><span data-stu-id="ae21f-114">Another advantage to early binding is that it enables useful features such as automatic code completion and Dynamic Help because the Visual Studio integrated development environment (IDE) can determine exactly what type of object you are working with as you edit the code.</span></span> <span data-ttu-id="ae21f-115">Erken bağlama, bir program derlendiğinde derleyicinin hata raporlenmesini sağladığından, çalışma zamanı hatalarının sayısını ve önem derecesini azaltır.</span><span class="sxs-lookup"><span data-stu-id="ae21f-115">Early binding reduces the number and severity of run-time errors because it allows the compiler to report errors when a program is compiled.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ae21f-116">Geç bağlama yalnızca `Public`olarak belirtilen tür üyelerine erişmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ae21f-116">Late binding can only be used to access type members that are declared as `Public`.</span></span> <span data-ttu-id="ae21f-117">`Friend` veya `Protected Friend` olarak belirtilen üyelere erişim bir çalışma zamanı hatasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="ae21f-117">Accessing members declared as `Friend` or `Protected Friend` results in a run-time error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae21f-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae21f-118">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>
- [<span data-ttu-id="ae21f-119">Nesne Ömrü: Nesneleri Oluşturma ve Yok Etme</span><span class="sxs-lookup"><span data-stu-id="ae21f-119">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [<span data-ttu-id="ae21f-120">Object Veri Türü</span><span class="sxs-lookup"><span data-stu-id="ae21f-120">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
