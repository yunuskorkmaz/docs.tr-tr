---
title: 'Nasıl yapılır: Kullanım My Namespace - C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, My namespace access
ms.assetid: e7152414-0ea5-4c8e-bf02-c8d5bbe45ff4
ms.openlocfilehash: 9621f6a01ef4e30bf34b97df3d2c3033e9b62a23
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59316030"
---
# <a name="how-to-use-the-my-namespace-c-programming-guide"></a><span data-ttu-id="57e55-102">Nasıl yapılır: Kullanım My Namespace (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="57e55-102">How to: Use the My Namespace (C# Programming Guide)</span></span>
<span data-ttu-id="57e55-103"><xref:Microsoft.VisualBasic.MyServices> Ad alanı (`My` Visual Basic'te) .NET Framework sınıfları, bilgisayar, uygulama, ayarları, kaynakları ve benzeri ile etkileşime giren bir kod yazmanızı sağlayan bir dizi kolay ve sezgisel erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="57e55-103">The <xref:Microsoft.VisualBasic.MyServices> namespace (`My` in Visual Basic) provides easy and intuitive access to a number of .NET Framework classes, enabling you to write code that interacts with the computer, application, settings, resources, and so on.</span></span> <span data-ttu-id="57e55-104">İlk olarak, Visual Basic ile kullanılmak üzere tasarlanmış olsa da `MyServices` ad alanı, C# uygulamalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="57e55-104">Although originally designed for use with Visual Basic, the `MyServices` namespace can be used in C# applications.</span></span>  
  
 <span data-ttu-id="57e55-105">Kullanma hakkında daha fazla bilgi için `MyServices` ad alanı Visual Basic'teki bkz [ile geliştirme My](../../../visual-basic/developing-apps/development-with-my/index.md).</span><span class="sxs-lookup"><span data-stu-id="57e55-105">For more information about using the `MyServices` namespace from Visual Basic, see [Development with My](../../../visual-basic/developing-apps/development-with-my/index.md).</span></span>  
  
## <a name="adding-a-reference"></a><span data-ttu-id="57e55-106">Başvuru ekleme</span><span class="sxs-lookup"><span data-stu-id="57e55-106">Adding a Reference</span></span>  
 <span data-ttu-id="57e55-107">Kullanmadan önce `MyServices` sınıfları çözümünüzde, Visual Basic kitaplığına bir başvuru eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="57e55-107">Before you can use the `MyServices` classes in your solution, you must add a reference to the Visual Basic library.</span></span>  
  
#### <a name="to-add-a-reference-to-the-visual-basic-library"></a><span data-ttu-id="57e55-108">Visual Basic kitaplığına bir başvuru eklemek için</span><span class="sxs-lookup"><span data-stu-id="57e55-108">To add a reference to the Visual Basic library</span></span>  
  
1. <span data-ttu-id="57e55-109">İçinde **Çözüm Gezgini**, sağ **başvuruları** düğüm ve select **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="57e55-109">In **Solution Explorer**, right-click the **References** node, and select **Add Reference**.</span></span>  
  
2. <span data-ttu-id="57e55-110">Zaman **başvuruları** iletişim kutusu görüntülenirse, listede aşağıda kaydırarak ve Microsoft.VisualBasic.dll'ı seçin.</span><span class="sxs-lookup"><span data-stu-id="57e55-110">When the **References** dialog box appears, scroll down the list, and select Microsoft.VisualBasic.dll.</span></span>  
  
     <span data-ttu-id="57e55-111">Aşağıdaki satırda eklemek isteyebilirsiniz `using` , program başlangıcında bölümü.</span><span class="sxs-lookup"><span data-stu-id="57e55-111">You might also want to include the following line in the `using` section at the start of your program.</span></span>  
  
     [!code-csharp[csProgGuideNamespaces#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#18)]  
  
## <a name="example"></a><span data-ttu-id="57e55-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="57e55-112">Example</span></span>  
 <span data-ttu-id="57e55-113">Bu örnekte yer alan çeşitli statik yöntemler çağırır `MyServices` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="57e55-113">This example calls various static methods contained in the `MyServices` namespace.</span></span> <span data-ttu-id="57e55-114">Bu kodu derlemek projeye bir başvuru Microsoft.VisualBasic.DLL eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="57e55-114">For this code to compile, a reference to Microsoft.VisualBasic.DLL must be added to the project.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#19)]  
  
 <span data-ttu-id="57e55-115">Tüm sınıfları `MyServices` ad alanı, bir C# uygulamasından çağrılabilir: Örneğin, <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> sınıfı uyumlu değil.</span><span class="sxs-lookup"><span data-stu-id="57e55-115">Not all the classes in the `MyServices` namespace can be called from a C# application: for example, the <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> class is not compatible.</span></span> <span data-ttu-id="57e55-116">Bu durumda, statik yöntemler parçası olan <xref:Microsoft.VisualBasic.FileIO.FileSystem>, hangi ayrıca VisualBasic.dll içinde bulunan kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="57e55-116">In this particular case, the static methods that are part of <xref:Microsoft.VisualBasic.FileIO.FileSystem>, which are also contained in VisualBasic.dll, can be used instead.</span></span> <span data-ttu-id="57e55-117">Örneğin, şöyle bir dizini çoğaltmak için bu tür bir yöntem kullanmak:</span><span class="sxs-lookup"><span data-stu-id="57e55-117">For example, here is how to use one such method to duplicate a directory:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#20)]  
  
## <a name="see-also"></a><span data-ttu-id="57e55-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="57e55-118">See also</span></span>

- [<span data-ttu-id="57e55-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="57e55-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="57e55-120">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="57e55-120">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)
- [<span data-ttu-id="57e55-121">Ad Alanlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="57e55-121">Using Namespaces</span></span>](../../../csharp/programming-guide/namespaces/using-namespaces.md)
