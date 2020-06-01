---
title: My Namespace-C# programlama kılavuzunu kullanma
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, My namespace access
ms.assetid: e7152414-0ea5-4c8e-bf02-c8d5bbe45ff4
ms.openlocfilehash: 268543980ba891b0b30f393ee8982f2863ba9a71
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241948"
---
# <a name="how-to-use-the-my-namespace-c-programming-guide"></a><span data-ttu-id="d8859-102">My ad alanım 'ı kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="d8859-102">How to use the My namespace (C# Programming Guide)</span></span>

<span data-ttu-id="d8859-103"><xref:Microsoft.VisualBasic.MyServices>Ad alanı ( `My` Visual Basic), bir dizi .net sınıfına kolay ve sezgisel erişim sağlar ve bu sayede bilgisayar, uygulama, ayarlar, kaynaklar vb. ile etkileşime geçmek için kod yazmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="d8859-103">The <xref:Microsoft.VisualBasic.MyServices> namespace (`My` in Visual Basic) provides easy and intuitive access to a number of .NET classes, enabling you to write code that interacts with the computer, application, settings, resources, and so on.</span></span> <span data-ttu-id="d8859-104">Başlangıçta Visual Basic ile kullanım için tasarlanmış olsa da, `MyServices` ad alanı C# uygulamalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d8859-104">Although originally designed for use with Visual Basic, the `MyServices` namespace can be used in C# applications.</span></span>  
  
 <span data-ttu-id="d8859-105">Visual Basic ad alanını kullanma hakkında daha fazla bilgi için `MyServices` , bkz. [ile geliştirme](../../../visual-basic/developing-apps/development-with-my/index.md).</span><span class="sxs-lookup"><span data-stu-id="d8859-105">For more information about using the `MyServices` namespace from Visual Basic, see [Development with My](../../../visual-basic/developing-apps/development-with-my/index.md).</span></span>  
  
## <a name="add-a-reference"></a><span data-ttu-id="d8859-106">Başvuru ekleme</span><span class="sxs-lookup"><span data-stu-id="d8859-106">Add a reference</span></span>

 <span data-ttu-id="d8859-107">`MyServices`Çözümünüzde sınıfları kullanabilmeniz için, Visual Basic kitaplığına bir başvuru eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d8859-107">Before you can use the `MyServices` classes in your solution, you must add a reference to the Visual Basic library.</span></span>  
  
### <a name="add-a-reference-to-the-visual-basic-library"></a><span data-ttu-id="d8859-108">Visual Basic kitaplığına bir başvuru ekleme</span><span class="sxs-lookup"><span data-stu-id="d8859-108">Add a reference to the Visual Basic library</span></span>  
  
1. <span data-ttu-id="d8859-109">**Çözüm Gezgini**, **Başvurular** düğümüne sağ tıklayın ve **Başvuru Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="d8859-109">In **Solution Explorer**, right-click the **References** node, and select **Add Reference**.</span></span>  
  
2. <span data-ttu-id="d8859-110">**Başvurular** iletişim kutusu göründüğünde, listeyi aşağı kaydırın ve Microsoft. VisualBasic. dll ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="d8859-110">When the **References** dialog box appears, scroll down the list, and select Microsoft.VisualBasic.dll.</span></span>  
  
     <span data-ttu-id="d8859-111">Programınızın başlangıcında bölümüne aşağıdaki satırı da eklemek isteyebilirsiniz `using` .</span><span class="sxs-lookup"><span data-stu-id="d8859-111">You might also want to include the following line in the `using` section at the start of your program.</span></span>  
  
     [!code-csharp[csProgGuideNamespaces#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#18)]  
  
## <a name="example"></a><span data-ttu-id="d8859-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="d8859-112">Example</span></span>  
 <span data-ttu-id="d8859-113">Bu örnek, ad alanında bulunan çeşitli statik yöntemleri çağırır `MyServices` .</span><span class="sxs-lookup"><span data-stu-id="d8859-113">This example calls various static methods contained in the `MyServices` namespace.</span></span> <span data-ttu-id="d8859-114">Bu kodun derlenmesi için projeye Microsoft. VisualBasic. DLL başvurusunun eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="d8859-114">For this code to compile, a reference to Microsoft.VisualBasic.DLL must be added to the project.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#19)]  
  
 <span data-ttu-id="d8859-115">`MyServices`Ad alanındaki sınıfların hepsi bir C# uygulamasından çağrılabilir: Örneğin, <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> sınıfı uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="d8859-115">Not all the classes in the `MyServices` namespace can be called from a C# application: for example, the <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> class is not compatible.</span></span> <span data-ttu-id="d8859-116">Bu durumda, ' ın bir parçası olan statik yöntemler <xref:Microsoft.VisualBasic.FileIO.FileSystem> bunun yerine VisualBasic. dll içinde de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d8859-116">In this particular case, the static methods that are part of <xref:Microsoft.VisualBasic.FileIO.FileSystem>, which are also contained in VisualBasic.dll, can be used instead.</span></span> <span data-ttu-id="d8859-117">Örneğin, bir dizini yinelemek için bu yöntemin nasıl kullanılacağı aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="d8859-117">For example, here is how to use one such method to duplicate a directory:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#20)]  
  
## <a name="see-also"></a><span data-ttu-id="d8859-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8859-118">See also</span></span>

- [<span data-ttu-id="d8859-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="d8859-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="d8859-120">Ad alanları</span><span class="sxs-lookup"><span data-stu-id="d8859-120">Namespaces</span></span>](./index.md)
- [<span data-ttu-id="d8859-121">Ad alanlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="d8859-121">Using Namespaces</span></span>](./using-namespaces.md)
