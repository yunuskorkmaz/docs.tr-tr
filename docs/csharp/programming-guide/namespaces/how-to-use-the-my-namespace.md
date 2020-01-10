---
title: My Namespace- C# programlama kılavuzunu kullanma
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, My namespace access
ms.assetid: e7152414-0ea5-4c8e-bf02-c8d5bbe45ff4
ms.openlocfilehash: 063b46a32ced859c6c86e40c4a6b9870c3decd24
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75700425"
---
# <a name="how-to-use-the-my-namespace-c-programming-guide"></a><span data-ttu-id="68117-102">My Namespace (C# Programlama Kılavuzu) kullanma</span><span class="sxs-lookup"><span data-stu-id="68117-102">How to use the My namespace (C# Programming Guide)</span></span>
<span data-ttu-id="68117-103"><xref:Microsoft.VisualBasic.MyServices> ad alanı (Visual Basic`My`), bir dizi .NET Framework sınıfına kolay ve sezgisel erişim sağlar ve bu sayede bilgisayar, uygulama, ayarlar, kaynaklar vb. ile etkileşime geçmek için kod yazmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="68117-103">The <xref:Microsoft.VisualBasic.MyServices> namespace (`My` in Visual Basic) provides easy and intuitive access to a number of .NET Framework classes, enabling you to write code that interacts with the computer, application, settings, resources, and so on.</span></span> <span data-ttu-id="68117-104">Başlangıçta Visual Basic ile kullanım için tasarlanmış olsa da, `MyServices` ad alanı C# uygulamalarda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="68117-104">Although originally designed for use with Visual Basic, the `MyServices` namespace can be used in C# applications.</span></span>  
  
 <span data-ttu-id="68117-105">Visual Basic `MyServices` ad alanını kullanma hakkında daha fazla bilgi için, bkz. [Ile geliştirme](../../../visual-basic/developing-apps/development-with-my/index.md).</span><span class="sxs-lookup"><span data-stu-id="68117-105">For more information about using the `MyServices` namespace from Visual Basic, see [Development with My](../../../visual-basic/developing-apps/development-with-my/index.md).</span></span>  
  
## <a name="adding-a-reference"></a><span data-ttu-id="68117-106">Başvuru ekleme</span><span class="sxs-lookup"><span data-stu-id="68117-106">Adding a Reference</span></span>  
 <span data-ttu-id="68117-107">Çözümünüzde `MyServices` sınıfları kullanabilmeniz için, Visual Basic kitaplığına bir başvuru eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="68117-107">Before you can use the `MyServices` classes in your solution, you must add a reference to the Visual Basic library.</span></span>  
  
#### <a name="to-add-a-reference-to-the-visual-basic-library"></a><span data-ttu-id="68117-108">Visual Basic kitaplığına bir başvuru eklemek için</span><span class="sxs-lookup"><span data-stu-id="68117-108">To add a reference to the Visual Basic library</span></span>  
  
1. <span data-ttu-id="68117-109">**Çözüm Gezgini**, **Başvurular** düğümüne sağ tıklayın ve **Başvuru Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="68117-109">In **Solution Explorer**, right-click the **References** node, and select **Add Reference**.</span></span>  
  
2. <span data-ttu-id="68117-110">**Başvurular** iletişim kutusu göründüğünde, listeyi aşağı kaydırın ve Microsoft. VisualBasic. dll ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="68117-110">When the **References** dialog box appears, scroll down the list, and select Microsoft.VisualBasic.dll.</span></span>  
  
     <span data-ttu-id="68117-111">Programınızın başlangıcında `using` bölümüne aşağıdaki satırı da eklemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68117-111">You might also want to include the following line in the `using` section at the start of your program.</span></span>  
  
     [!code-csharp[csProgGuideNamespaces#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#18)]  
  
## <a name="example"></a><span data-ttu-id="68117-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="68117-112">Example</span></span>  
 <span data-ttu-id="68117-113">Bu örnek `MyServices` ad alanında bulunan çeşitli statik yöntemleri çağırır.</span><span class="sxs-lookup"><span data-stu-id="68117-113">This example calls various static methods contained in the `MyServices` namespace.</span></span> <span data-ttu-id="68117-114">Bu kodun derlenmesi için projeye Microsoft. VisualBasic. DLL başvurusunun eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="68117-114">For this code to compile, a reference to Microsoft.VisualBasic.DLL must be added to the project.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#19)]  
  
 <span data-ttu-id="68117-115">`MyServices` ad alanındaki sınıfların tümü bir C# uygulamadan çağrılamaz: örneğin, <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> sınıfı uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="68117-115">Not all the classes in the `MyServices` namespace can be called from a C# application: for example, the <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> class is not compatible.</span></span> <span data-ttu-id="68117-116">Bu durumda, bunun yerine VisualBasic. dll içinde bulunan <xref:Microsoft.VisualBasic.FileIO.FileSystem>parçası olan statik yöntemler de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="68117-116">In this particular case, the static methods that are part of <xref:Microsoft.VisualBasic.FileIO.FileSystem>, which are also contained in VisualBasic.dll, can be used instead.</span></span> <span data-ttu-id="68117-117">Örneğin, bir dizini yinelemek için bu yöntemin nasıl kullanılacağı aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="68117-117">For example, here is how to use one such method to duplicate a directory:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#20)]  
  
## <a name="see-also"></a><span data-ttu-id="68117-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="68117-118">See also</span></span>

- [<span data-ttu-id="68117-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="68117-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="68117-120">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="68117-120">Namespaces</span></span>](./index.md)
- [<span data-ttu-id="68117-121">Ad Alanlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="68117-121">Using Namespaces</span></span>](./using-namespaces.md)
