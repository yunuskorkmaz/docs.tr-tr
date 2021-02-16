---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Visual Basic COM nesnelerine başvurma'
title: "Nasıl yapılır: Visual Basic'den COM Nesnelerine Başvuru Yapma"
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop [Visual Basic], referencing COM objects
- referencing objects, COM objects from Visual Basic
- objects [Visual Basic], referencing
- COM objects, referencing
- interop assemblies
ms.assetid: 9c518fb4-27d9-4112-9e6a-5a7d0210af6f
ms.openlocfilehash: f0c08e5be9144bdefc3fe0b4609bad2421889d52
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100477573"
---
# <a name="how-to-reference-com-objects-from-visual-basic"></a><span data-ttu-id="d9cc2-103">Nasıl yapılır: Visual Basic'den COM Nesnelerine Başvuru Yapma</span><span class="sxs-lookup"><span data-stu-id="d9cc2-103">How to: Reference COM Objects from Visual Basic</span></span>

<span data-ttu-id="d9cc2-104">Visual Basic, tür kitaplıklarının bulunduğu COM nesnelerine başvurular eklemek için COM kitaplığı için birlikte çalışma derlemesinin oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d9cc2-104">In Visual Basic, adding references to COM objects that have type libraries requires the creation of an interop assembly for the COM library.</span></span> <span data-ttu-id="d9cc2-105">COM nesnesinin üyelerine yapılan başvurular birlikte çalışma derlemesine yönlendirilir ve ardından gerçek COM nesnesine iletilir.</span><span class="sxs-lookup"><span data-stu-id="d9cc2-105">References to the members of the COM object are routed to the interop assembly and then forwarded to the actual COM object.</span></span> <span data-ttu-id="d9cc2-106">COM nesnesinden gelen yanıtlar birlikte çalışma derlemesine yönlendirilir ve .NET Framework uygulamanıza iletilir.</span><span class="sxs-lookup"><span data-stu-id="d9cc2-106">Responses from the COM object are routed to the interop assembly and forwarded to your .NET Framework application.</span></span>  
  
 <span data-ttu-id="d9cc2-107">Bir .NET derlemesine COM nesnesinin tür bilgilerini gömerek derleme kullanmadan bir COM nesnesine başvurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d9cc2-107">You can reference a COM object without using an interop assembly by embedding the type information for the COM object in a .NET assembly.</span></span> <span data-ttu-id="d9cc2-108">Tür bilgilerini eklemek için `Embed Interop Types` ÖZELLIĞI `True` com nesnesine başvuru için olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d9cc2-108">To embed type information, set the `Embed Interop Types` property to `True` for the reference to the COM object.</span></span> <span data-ttu-id="d9cc2-109">Komut satırı derleyicisini kullanarak derlerken, `/link` com kitaplığına başvurmak için seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d9cc2-109">If you are compiling by using the command-line compiler, use the `/link` option to reference the COM library.</span></span> <span data-ttu-id="d9cc2-110">Daha fazla bilgi için bkz. [-Link (Visual Basic)](../../reference/command-line-compiler/link.md).</span><span class="sxs-lookup"><span data-stu-id="d9cc2-110">For more information, see [-link (Visual Basic)](../../reference/command-line-compiler/link.md).</span></span>  
  
 <span data-ttu-id="d9cc2-111">Visual Basic, tümleşik geliştirme ortamından (IDE) bir tür kitaplığına bir başvuru eklediğinizde otomatik olarak birlikte çalışma derlemeleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d9cc2-111">Visual Basic automatically creates interop assemblies when you add a reference to a type library from the integrated development environment (IDE).</span></span> <span data-ttu-id="d9cc2-112">Komut satırından çalışırken, Tlbimp yardımcı programını kullanarak birlikte çalışma derlemelerini el ile oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d9cc2-112">When working from the command line, you can use the Tlbimp utility to manually create interop assemblies.</span></span>  
  
### <a name="to-add-references-to-com-objects"></a><span data-ttu-id="d9cc2-113">COM nesnelerine başvuru eklemek için</span><span class="sxs-lookup"><span data-stu-id="d9cc2-113">To add references to COM objects</span></span>  
  
1. <span data-ttu-id="d9cc2-114">**Proje** menüsünde, **Başvuru Ekle** ' yi seçin ve ardından iletişim kutusunda **com** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d9cc2-114">On the **Project** menu, choose **Add Reference** and then click the **COM** tab in the dialog box.</span></span>  
  
2. <span data-ttu-id="d9cc2-115">COM nesneleri listesinden kullanmak istediğiniz bileşeni seçin.</span><span class="sxs-lookup"><span data-stu-id="d9cc2-115">Select the component you want to use from the list of COM objects.</span></span>  
  
3. <span data-ttu-id="d9cc2-116">Birlikte çalışma derlemesine erişimi basitleştirmek için, `Imports` com nesnesini kullanacağınız sınıfın veya modülün üst kısmına bir ifade ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d9cc2-116">To simplify access to the interop assembly, add an `Imports` statement to the top of the class or module in which you will use the COM object.</span></span> <span data-ttu-id="d9cc2-117">Örneğin, aşağıdaki kod örneği, `INKEDLib` kitaplıkta başvurulan nesneler için ad alanını içeri aktarır `Microsoft InkEdit Control 1.0` .</span><span class="sxs-lookup"><span data-stu-id="d9cc2-117">For example, the following code example imports the namespace `INKEDLib` for objects referenced in the `Microsoft InkEdit Control 1.0` library.</span></span>  
  
     [!code-vb[VbVbalrInterop#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#40)]  
  
### <a name="to-create-an-interop-assembly-using-tlbimp"></a><span data-ttu-id="d9cc2-118">Tlbimp kullanarak birlikte çalışma derlemesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d9cc2-118">To create an interop assembly using Tlbimp</span></span>  
  
1. <span data-ttu-id="d9cc2-119">Tlbimp 'nin konumunu, zaten arama yolunun bir parçası değilse ve şu anda bulunduğu dizinde değilseniz arama yoluna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d9cc2-119">Add the location of Tlbimp to the search path, if it is not already part of the search path and you are not currently in the directory where it is located.</span></span>  
  
2. <span data-ttu-id="d9cc2-120">Aşağıdaki bilgileri sağlayarak bir komut isteminden Tlbimp 'i çağırın:</span><span class="sxs-lookup"><span data-stu-id="d9cc2-120">Call Tlbimp from a command prompt, providing the following information:</span></span>  
  
    - <span data-ttu-id="d9cc2-121">Tür kitaplığını içeren DLL 'nin adı ve konumu</span><span class="sxs-lookup"><span data-stu-id="d9cc2-121">Name and location of the DLL that contains the type library</span></span>  
  
    - <span data-ttu-id="d9cc2-122">Bilgilerin yerleştirilmesi gereken ad alanının adı ve konumu</span><span class="sxs-lookup"><span data-stu-id="d9cc2-122">Name and location of the namespace where the information should be placed</span></span>  
  
    - <span data-ttu-id="d9cc2-123">Hedef birlikte çalışma derlemesinin adı ve konumu</span><span class="sxs-lookup"><span data-stu-id="d9cc2-123">Name and location of the target interop assembly</span></span>  
  
     <span data-ttu-id="d9cc2-124">Aşağıdaki kod bir örnek sağlar:</span><span class="sxs-lookup"><span data-stu-id="d9cc2-124">The following code provides an example:</span></span>  
  
    ```console  
    Tlbimp test3.dll /out:NameSpace1 /out:Interop1.dll  
    ```  
  
     <span data-ttu-id="d9cc2-125">Kayıtsız COM nesneleri için bile tür kitaplıkları için birlikte çalışma derlemeleri oluşturmak üzere Tlbimp kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d9cc2-125">You can use Tlbimp to create interop assemblies for type libraries, even for unregistered COM objects.</span></span> <span data-ttu-id="d9cc2-126">Bununla birlikte, birlikte çalışma derlemelerinin başvurduğu COM nesneleri, kullanıldığı bilgisayarda düzgün şekilde kaydedilmelidir.</span><span class="sxs-lookup"><span data-stu-id="d9cc2-126">However, the COM objects referred to by interop assemblies must be properly registered on the computer where they are to be used.</span></span> <span data-ttu-id="d9cc2-127">Windows işletim sistemine dahil edilen regsvr32 yardımcı programını kullanarak bir COM nesnesini kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d9cc2-127">You can register a COM object by using the Regsvr32 utility included with the Windows operating system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9cc2-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9cc2-128">See also</span></span>

- [<span data-ttu-id="d9cc2-129">COM birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="d9cc2-129">COM Interop</span></span>](index.md)
- [<span data-ttu-id="d9cc2-130">Tlbimp.exe (tür kitaplığı Içeri Aktarıcı)</span><span class="sxs-lookup"><span data-stu-id="d9cc2-130">Tlbimp.exe (Type Library Importer)</span></span>](../../../framework/tools/tlbimp-exe-type-library-importer.md)
- [<span data-ttu-id="d9cc2-131">Tlbexp.exe (tür kitaplığı verme programı)</span><span class="sxs-lookup"><span data-stu-id="d9cc2-131">Tlbexp.exe (Type Library Exporter)</span></span>](../../../framework/tools/tlbexp-exe-type-library-exporter.md)
- [<span data-ttu-id="d9cc2-132">İzlenecek yol: COM Nesnelerinde Kalıtım Uygulama</span><span class="sxs-lookup"><span data-stu-id="d9cc2-132">Walkthrough: Implementing Inheritance with COM Objects</span></span>](walkthrough-implementing-inheritance-with-com-objects.md)
- [<span data-ttu-id="d9cc2-133">Birlikte Çalışabilirlik İle İlgili Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="d9cc2-133">Troubleshooting Interoperability</span></span>](troubleshooting-interoperability.md)
- [<span data-ttu-id="d9cc2-134">Imports Deyimi (.NET Ad Alanı ve Türü)</span><span class="sxs-lookup"><span data-stu-id="d9cc2-134">Imports Statement (.NET Namespace and Type)</span></span>](../../language-reference/statements/imports-statement-net-namespace-and-type.md)
