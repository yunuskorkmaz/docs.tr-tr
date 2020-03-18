---
title: Benim ad alanım nasıl kullanılır - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, My namespace access
ms.assetid: e7152414-0ea5-4c8e-bf02-c8d5bbe45ff4
ms.openlocfilehash: 063b46a32ced859c6c86e40c4a6b9870c3decd24
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75700425"
---
# <a name="how-to-use-the-my-namespace-c-programming-guide"></a><span data-ttu-id="f2fe6-102">Ad alanım (C# Programlama Kılavuzu) nasıl kullanılır?</span><span class="sxs-lookup"><span data-stu-id="f2fe6-102">How to use the My namespace (C# Programming Guide)</span></span>
<span data-ttu-id="f2fe6-103"><xref:Microsoft.VisualBasic.MyServices> Ad alanı`My` (Visual Basic'te), bilgisayar, uygulama, ayarlar, kaynaklar vb. ile etkileşimedebilen kod lar yazmanızı sağlayan bir dizi .NET Framework sınıfına kolay ve sezgisel erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="f2fe6-103">The <xref:Microsoft.VisualBasic.MyServices> namespace (`My` in Visual Basic) provides easy and intuitive access to a number of .NET Framework classes, enabling you to write code that interacts with the computer, application, settings, resources, and so on.</span></span> <span data-ttu-id="f2fe6-104">Başlangıçta Visual Basic ile kullanılmak üzere `MyServices` tasarlanmış olsa da, ad alanı C# uygulamalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f2fe6-104">Although originally designed for use with Visual Basic, the `MyServices` namespace can be used in C# applications.</span></span>  
  
 <span data-ttu-id="f2fe6-105">Visual Basic'teki `MyServices` ad alanını kullanma hakkında daha fazla bilgi [için, Bkz.](../../../visual-basic/developing-apps/development-with-my/index.md)</span><span class="sxs-lookup"><span data-stu-id="f2fe6-105">For more information about using the `MyServices` namespace from Visual Basic, see [Development with My](../../../visual-basic/developing-apps/development-with-my/index.md).</span></span>  
  
## <a name="adding-a-reference"></a><span data-ttu-id="f2fe6-106">Referans Ekleme</span><span class="sxs-lookup"><span data-stu-id="f2fe6-106">Adding a Reference</span></span>  
 <span data-ttu-id="f2fe6-107">Çözümdeki `MyServices` sınıfları kullanabilmek için Önce Visual Basic kitaplığına bir başvuru eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f2fe6-107">Before you can use the `MyServices` classes in your solution, you must add a reference to the Visual Basic library.</span></span>  
  
#### <a name="to-add-a-reference-to-the-visual-basic-library"></a><span data-ttu-id="f2fe6-108">Visual Basic kitaplığına başvuru eklemek için</span><span class="sxs-lookup"><span data-stu-id="f2fe6-108">To add a reference to the Visual Basic library</span></span>  
  
1. <span data-ttu-id="f2fe6-109">**Çözüm Gezgini'nde,** **Başvurular** düğümüne sağ tıklayın ve **Başvuru Ekle'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="f2fe6-109">In **Solution Explorer**, right-click the **References** node, and select **Add Reference**.</span></span>  
  
2. <span data-ttu-id="f2fe6-110">**Başvurular** iletişim kutusu göründüğünde, listeyi aşağı kaydırın ve Microsoft.VisualBasic.dll'yi seçin.</span><span class="sxs-lookup"><span data-stu-id="f2fe6-110">When the **References** dialog box appears, scroll down the list, and select Microsoft.VisualBasic.dll.</span></span>  
  
     <span data-ttu-id="f2fe6-111">Ayrıca, programın başındaki `using` bölüme aşağıdaki satırı eklemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2fe6-111">You might also want to include the following line in the `using` section at the start of your program.</span></span>  
  
     [!code-csharp[csProgGuideNamespaces#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#18)]  
  
## <a name="example"></a><span data-ttu-id="f2fe6-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="f2fe6-112">Example</span></span>  
 <span data-ttu-id="f2fe6-113">Bu örnek, `MyServices` ad alanında bulunan çeşitli statik yöntemleri çağırır.</span><span class="sxs-lookup"><span data-stu-id="f2fe6-113">This example calls various static methods contained in the `MyServices` namespace.</span></span> <span data-ttu-id="f2fe6-114">Bu kodun derlemesi için projeye Microsoft.VisualBasic.DLL'ye bir başvuru eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="f2fe6-114">For this code to compile, a reference to Microsoft.VisualBasic.DLL must be added to the project.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#19)]  
  
 <span data-ttu-id="f2fe6-115">`MyServices` Ad alanındaki tüm sınıflar C# uygulamasından çağrılabilir: örneğin, <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> sınıf uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="f2fe6-115">Not all the classes in the `MyServices` namespace can be called from a C# application: for example, the <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> class is not compatible.</span></span> <span data-ttu-id="f2fe6-116">Bu özel durumda, visualBasic.dll'de de bulunan statik yöntemler <xref:Microsoft.VisualBasic.FileIO.FileSystem>kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f2fe6-116">In this particular case, the static methods that are part of <xref:Microsoft.VisualBasic.FileIO.FileSystem>, which are also contained in VisualBasic.dll, can be used instead.</span></span> <span data-ttu-id="f2fe6-117">Örneğin, bir dizini çoğaltmak için böyle bir yöntemin nasıl kullanılacağı aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="f2fe6-117">For example, here is how to use one such method to duplicate a directory:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#20)]  
  
## <a name="see-also"></a><span data-ttu-id="f2fe6-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2fe6-118">See also</span></span>

- [<span data-ttu-id="f2fe6-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f2fe6-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="f2fe6-120">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="f2fe6-120">Namespaces</span></span>](./index.md)
- [<span data-ttu-id="f2fe6-121">Ad Alanlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="f2fe6-121">Using Namespaces</span></span>](./using-namespaces.md)
