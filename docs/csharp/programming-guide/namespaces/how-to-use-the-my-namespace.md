---
title: My Namespace-C# programlama kılavuzunu kullanma
description: "' My ' ad alanını bizimle öğrenin. ' My ' ad alanı, bir dizi .NET sınıfına kolay ve sezgisel erişim sağlar."
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, My namespace access
ms.assetid: e7152414-0ea5-4c8e-bf02-c8d5bbe45ff4
ms.openlocfilehash: 5310b911cc0abf0e82c4dc8efd45eb45ffb94c9d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176233"
---
# <a name="how-to-use-the-my-namespace-c-programming-guide"></a><span data-ttu-id="ae4b6-104">My ad alanım 'ı kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="ae4b6-104">How to use the My namespace (C# Programming Guide)</span></span>

<span data-ttu-id="ae4b6-105"><xref:Microsoft.VisualBasic.MyServices>Ad alanı ( `My` Visual Basic), bir dizi .net sınıfına kolay ve sezgisel erişim sağlar ve bu sayede bilgisayar, uygulama, ayarlar, kaynaklar vb. ile etkileşime geçmek için kod yazmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="ae4b6-105">The <xref:Microsoft.VisualBasic.MyServices> namespace (`My` in Visual Basic) provides easy and intuitive access to a number of .NET classes, enabling you to write code that interacts with the computer, application, settings, resources, and so on.</span></span> <span data-ttu-id="ae4b6-106">Başlangıçta Visual Basic ile kullanım için tasarlanmış olsa da, `MyServices` ad alanı C# uygulamalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ae4b6-106">Although originally designed for use with Visual Basic, the `MyServices` namespace can be used in C# applications.</span></span>  
  
 <span data-ttu-id="ae4b6-107">Visual Basic ad alanını kullanma hakkında daha fazla bilgi için `MyServices` , bkz. [ile geliştirme](../../../visual-basic/developing-apps/development-with-my/index.md).</span><span class="sxs-lookup"><span data-stu-id="ae4b6-107">For more information about using the `MyServices` namespace from Visual Basic, see [Development with My](../../../visual-basic/developing-apps/development-with-my/index.md).</span></span>  
  
## <a name="add-a-reference"></a><span data-ttu-id="ae4b6-108">Başvuru ekleme</span><span class="sxs-lookup"><span data-stu-id="ae4b6-108">Add a reference</span></span>

 <span data-ttu-id="ae4b6-109">`MyServices`Çözümünüzde sınıfları kullanabilmeniz için, Visual Basic kitaplığına bir başvuru eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ae4b6-109">Before you can use the `MyServices` classes in your solution, you must add a reference to the Visual Basic library.</span></span>  
  
### <a name="add-a-reference-to-the-visual-basic-library"></a><span data-ttu-id="ae4b6-110">Visual Basic kitaplığına bir başvuru ekleme</span><span class="sxs-lookup"><span data-stu-id="ae4b6-110">Add a reference to the Visual Basic library</span></span>  
  
1. <span data-ttu-id="ae4b6-111">**Çözüm Gezgini**, **Başvurular** düğümüne sağ tıklayın ve **Başvuru Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="ae4b6-111">In **Solution Explorer**, right-click the **References** node, and select **Add Reference**.</span></span>  
  
2. <span data-ttu-id="ae4b6-112">**Başvurular** iletişim kutusu göründüğünde, listeyi aşağı kaydırın ve Microsoft.VisualBasic.dll ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="ae4b6-112">When the **References** dialog box appears, scroll down the list, and select Microsoft.VisualBasic.dll.</span></span>  
  
     <span data-ttu-id="ae4b6-113">Programınızın başlangıcında bölümüne aşağıdaki satırı da eklemek isteyebilirsiniz `using` .</span><span class="sxs-lookup"><span data-stu-id="ae4b6-113">You might also want to include the following line in the `using` section at the start of your program.</span></span>  
  
     [!code-csharp[csProgGuideNamespaces#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#18)]  
  
## <a name="example"></a><span data-ttu-id="ae4b6-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="ae4b6-114">Example</span></span>  

 <span data-ttu-id="ae4b6-115">Bu örnek, ad alanında bulunan çeşitli statik yöntemleri çağırır `MyServices` .</span><span class="sxs-lookup"><span data-stu-id="ae4b6-115">This example calls various static methods contained in the `MyServices` namespace.</span></span> <span data-ttu-id="ae4b6-116">Bu kodun derlenmesi için, projeye Microsoft.VisualBasic.DLL bir başvuru eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="ae4b6-116">For this code to compile, a reference to Microsoft.VisualBasic.DLL must be added to the project.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#19)]  
  
 <span data-ttu-id="ae4b6-117">`MyServices`Ad alanındaki sınıfların hepsi bir C# uygulamasından çağrılabilir: Örneğin, <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> sınıfı uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="ae4b6-117">Not all the classes in the `MyServices` namespace can be called from a C# application: for example, the <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> class is not compatible.</span></span> <span data-ttu-id="ae4b6-118">Bu durumda, öğesinin parçası olan statik yöntemler <xref:Microsoft.VisualBasic.FileIO.FileSystem> bunun yerine VisualBasic.dll de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ae4b6-118">In this particular case, the static methods that are part of <xref:Microsoft.VisualBasic.FileIO.FileSystem>, which are also contained in VisualBasic.dll, can be used instead.</span></span> <span data-ttu-id="ae4b6-119">Örneğin, bir dizini yinelemek için bu yöntemin nasıl kullanılacağı aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="ae4b6-119">For example, here is how to use one such method to duplicate a directory:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#20)]  
  
## <a name="see-also"></a><span data-ttu-id="ae4b6-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae4b6-120">See also</span></span>

- [<span data-ttu-id="ae4b6-121">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ae4b6-121">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ae4b6-122">Ad alanları</span><span class="sxs-lookup"><span data-stu-id="ae4b6-122">Namespaces</span></span>](./index.md)
- [<span data-ttu-id="ae4b6-123">Ad alanlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="ae4b6-123">Using Namespaces</span></span>](./using-namespaces.md)
