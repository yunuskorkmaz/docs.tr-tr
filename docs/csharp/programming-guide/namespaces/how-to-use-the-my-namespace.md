---
title: 'Nasıl yapılır: My Namespace- C# Programming kılavuzunu kullanın'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, My namespace access
ms.assetid: e7152414-0ea5-4c8e-bf02-c8d5bbe45ff4
ms.openlocfilehash: ff00a60d92ec6abbeb257abec76ed2812867f651
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588870"
---
# <a name="how-to-use-the-my-namespace-c-programming-guide"></a><span data-ttu-id="a89e6-102">Nasıl yapılır: My Namespace (C# Programlama Kılavuzu) kullanın</span><span class="sxs-lookup"><span data-stu-id="a89e6-102">How to: Use the My Namespace (C# Programming Guide)</span></span>
<span data-ttu-id="a89e6-103">Ad alanı (`My` Visual Basic), bir dizi .NET Framework sınıfa kolay ve sezgisel erişim sağlar ve bu sayede bilgisayar, uygulama, ayarlar, kaynaklar vb. ile etkileşimde bulunan bir kod yazmanıza olanak tanır. <xref:Microsoft.VisualBasic.MyServices></span><span class="sxs-lookup"><span data-stu-id="a89e6-103">The <xref:Microsoft.VisualBasic.MyServices> namespace (`My` in Visual Basic) provides easy and intuitive access to a number of .NET Framework classes, enabling you to write code that interacts with the computer, application, settings, resources, and so on.</span></span> <span data-ttu-id="a89e6-104">Başlangıçta Visual Basic ile kullanım için tasarlanmış olsa da, `MyServices` ad alanı C# uygulamalarda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a89e6-104">Although originally designed for use with Visual Basic, the `MyServices` namespace can be used in C# applications.</span></span>  
  
 <span data-ttu-id="a89e6-105">Visual Basic `MyServices` ad alanını kullanma hakkında daha fazla bilgi için, bkz. [ile geliştirme](../../../visual-basic/developing-apps/development-with-my/index.md).</span><span class="sxs-lookup"><span data-stu-id="a89e6-105">For more information about using the `MyServices` namespace from Visual Basic, see [Development with My](../../../visual-basic/developing-apps/development-with-my/index.md).</span></span>  
  
## <a name="adding-a-reference"></a><span data-ttu-id="a89e6-106">Başvuru ekleme</span><span class="sxs-lookup"><span data-stu-id="a89e6-106">Adding a Reference</span></span>  
 <span data-ttu-id="a89e6-107">Çözümünüzde `MyServices` sınıfları kullanabilmeniz için, Visual Basic kitaplığına bir başvuru eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a89e6-107">Before you can use the `MyServices` classes in your solution, you must add a reference to the Visual Basic library.</span></span>  
  
#### <a name="to-add-a-reference-to-the-visual-basic-library"></a><span data-ttu-id="a89e6-108">Visual Basic kitaplığına bir başvuru eklemek için</span><span class="sxs-lookup"><span data-stu-id="a89e6-108">To add a reference to the Visual Basic library</span></span>  
  
1. <span data-ttu-id="a89e6-109">**Çözüm Gezgini**, **Başvurular** düğümüne sağ tıklayın ve **Başvuru Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="a89e6-109">In **Solution Explorer**, right-click the **References** node, and select **Add Reference**.</span></span>  
  
2. <span data-ttu-id="a89e6-110">**Başvurular** iletişim kutusu göründüğünde, listeyi aşağı kaydırın ve Microsoft. VisualBasic. dll ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="a89e6-110">When the **References** dialog box appears, scroll down the list, and select Microsoft.VisualBasic.dll.</span></span>  
  
     <span data-ttu-id="a89e6-111">Programınızın başlangıcında `using` bölümüne aşağıdaki satırı da eklemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a89e6-111">You might also want to include the following line in the `using` section at the start of your program.</span></span>  
  
     [!code-csharp[csProgGuideNamespaces#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#18)]  
  
## <a name="example"></a><span data-ttu-id="a89e6-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="a89e6-112">Example</span></span>  
 <span data-ttu-id="a89e6-113">Bu örnek, `MyServices` ad alanında bulunan çeşitli statik yöntemleri çağırır.</span><span class="sxs-lookup"><span data-stu-id="a89e6-113">This example calls various static methods contained in the `MyServices` namespace.</span></span> <span data-ttu-id="a89e6-114">Bu kodun derlenmesi için projeye Microsoft. VisualBasic. DLL başvurusunun eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="a89e6-114">For this code to compile, a reference to Microsoft.VisualBasic.DLL must be added to the project.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#19)]  
  
 <span data-ttu-id="a89e6-115">`MyServices` Ad alanındaki sınıfların tümü bir C# uygulamadan çağrılabilir: Örneğin, <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> sınıfı uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="a89e6-115">Not all the classes in the `MyServices` namespace can be called from a C# application: for example, the <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> class is not compatible.</span></span> <span data-ttu-id="a89e6-116">Bu durumda, ' ın bir <xref:Microsoft.VisualBasic.FileIO.FileSystem>parçası olan statik yöntemler bunun yerine VisualBasic. dll içinde de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a89e6-116">In this particular case, the static methods that are part of <xref:Microsoft.VisualBasic.FileIO.FileSystem>, which are also contained in VisualBasic.dll, can be used instead.</span></span> <span data-ttu-id="a89e6-117">Örneğin, bir dizini yinelemek için bu yöntemin nasıl kullanılacağı aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="a89e6-117">For example, here is how to use one such method to duplicate a directory:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#20)]  
  
## <a name="see-also"></a><span data-ttu-id="a89e6-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a89e6-118">See also</span></span>

- [<span data-ttu-id="a89e6-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a89e6-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="a89e6-120">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="a89e6-120">Namespaces</span></span>](./index.md)
- [<span data-ttu-id="a89e6-121">Ad Alanlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="a89e6-121">Using Namespaces</span></span>](./using-namespaces.md)
