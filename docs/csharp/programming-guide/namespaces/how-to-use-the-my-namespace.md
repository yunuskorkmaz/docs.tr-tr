---
title: "Nasıl yapılır: Ad Alanım'ı Kullanma (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: C# language, My namespace access
ms.assetid: e7152414-0ea5-4c8e-bf02-c8d5bbe45ff4
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f3564c594a5fbb9bd05a956e5c12bbb173d2db51
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-the-my-namespace-c-programming-guide"></a><span data-ttu-id="70b3d-102">Nasıl yapılır: Ad Alanım'ı Kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="70b3d-102">How to: Use the My Namespace (C# Programming Guide)</span></span>
<span data-ttu-id="70b3d-103"><xref:Microsoft.VisualBasic.MyServices> Ad alanı (`My` Visual Basic'te) .NET Framework sınıfları, bilgisayar, uygulama, ayarları, kaynaklar vb. ile etkileşime giren kod yazmayı sağlayan bir dizi kolay ve sezgisel erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="70b3d-103">The <xref:Microsoft.VisualBasic.MyServices> namespace (`My` in Visual Basic) provides easy and intuitive access to a number of .NET Framework classes, enabling you to write code that interacts with the computer, application, settings, resources, and so on.</span></span> <span data-ttu-id="70b3d-104">İlk olarak Visual Basic ile kullanılmak üzere tasarlanmış olsa da `MyServices` ad alanı, C# uygulamalarda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="70b3d-104">Although originally designed for use with Visual Basic, the `MyServices` namespace can be used in C# applications.</span></span>  
  
 <span data-ttu-id="70b3d-105">Kullanma hakkında daha fazla bilgi için `MyServices` ad alanı Visual Basic'teki bkz [ile geliştirme My](../../../visual-basic/developing-apps/development-with-my/index.md).</span><span class="sxs-lookup"><span data-stu-id="70b3d-105">For more information about using the `MyServices` namespace from Visual Basic, see [Development with My](../../../visual-basic/developing-apps/development-with-my/index.md).</span></span>  
  
## <a name="adding-a-reference"></a><span data-ttu-id="70b3d-106">Başvuru ekleme</span><span class="sxs-lookup"><span data-stu-id="70b3d-106">Adding a Reference</span></span>  
 <span data-ttu-id="70b3d-107">Kullanmadan önce `MyServices` sınıfları çözümünüzde, Visual Basic kitaplığına bir başvuru eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="70b3d-107">Before you can use the `MyServices` classes in your solution, you must add a reference to the Visual Basic library.</span></span>  
  
#### <a name="to-add-a-reference-to-the-visual-basic-library"></a><span data-ttu-id="70b3d-108">Visual Basic kitaplığına bir başvuru eklemek için</span><span class="sxs-lookup"><span data-stu-id="70b3d-108">To add a reference to the Visual Basic library</span></span>  
  
1.  <span data-ttu-id="70b3d-109">İçinde **Çözüm Gezgini**, sağ tıklatın **başvuruları** düğümü ve select **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="70b3d-109">In **Solution Explorer**, right-click the **References** node, and select **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="70b3d-110">Zaman **başvuruları** iletişim kutusu görüntülenirse, listede aşağı kaydırın ve Microsoft.VisualBasic.dll içinde seçin.</span><span class="sxs-lookup"><span data-stu-id="70b3d-110">When the **References** dialog box appears, scroll down the list, and select Microsoft.VisualBasic.dll.</span></span>  
  
     <span data-ttu-id="70b3d-111">Aşağıdaki satırda eklemek isteyebilirsiniz `using` programınızı başlangıcında bölümü.</span><span class="sxs-lookup"><span data-stu-id="70b3d-111">You might also want to include the following line in the `using` section at the start of your program.</span></span>  
  
     [!code-csharp[csProgGuideNamespaces#18](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-my-namespace_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="70b3d-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="70b3d-112">Example</span></span>  
 <span data-ttu-id="70b3d-113">Bu örnekte yer alan çeşitli statik yöntemlerini çağıran `MyServices` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="70b3d-113">This example calls various static methods contained in the `MyServices` namespace.</span></span> <span data-ttu-id="70b3d-114">Bu kodu derlemek bir başvuru Microsoft.VisualBasic.dll içinde projeye eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="70b3d-114">For this code to compile, a reference to Microsoft.VisualBasic.DLL must be added to the project.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#19](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-my-namespace_2.cs)]  
  
 <span data-ttu-id="70b3d-115">Tüm sınıflarda `MyServices` ad alanı bir C# uygulamasından çağrılabilir: Örneğin, <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> sınıfı uyumlu değil.</span><span class="sxs-lookup"><span data-stu-id="70b3d-115">Not all the classes in the `MyServices` namespace can be called from a C# application: for example, the <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> class is not compatible.</span></span> <span data-ttu-id="70b3d-116">Bu örnekte, statik yöntemler, parçası olan <xref:Microsoft.VisualBasic.FileIO.FileSystem>, hangi de VisualBasic.dll içinde bulunan kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="70b3d-116">In this particular case, the static methods that are part of <xref:Microsoft.VisualBasic.FileIO.FileSystem>, which are also contained in VisualBasic.dll, can be used instead.</span></span> <span data-ttu-id="70b3d-117">Örneğin, şöyle bir dizini çoğaltmak için bu tür bir yöntem kullanın:</span><span class="sxs-lookup"><span data-stu-id="70b3d-117">For example, here is how to use one such method to duplicate a directory:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#20](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-my-namespace_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="70b3d-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="70b3d-118">See Also</span></span>  
 [<span data-ttu-id="70b3d-119">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="70b3d-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="70b3d-120">Ad alanları</span><span class="sxs-lookup"><span data-stu-id="70b3d-120">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)  
 [<span data-ttu-id="70b3d-121">Ad alanlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="70b3d-121">Using Namespaces</span></span>](../../../csharp/programming-guide/namespaces/using-namespaces.md)
