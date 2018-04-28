---
title: "Nasıl yapılır: Visual Basic'den COM Nesnelerine Başvuru Yapma"
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- COM interop [Visual Basic], referencing COM objects
- referencing objects, COM objects from Visual Basic
- objects [Visual Basic], referencing
- COM objects, referencing
- interop assemblies
ms.assetid: 9c518fb4-27d9-4112-9e6a-5a7d0210af6f
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0f6f7b4887e2cfba65da7a7a890b78c3d6a8508f
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-reference-com-objects-from-visual-basic"></a><span data-ttu-id="56c52-102">Nasıl yapılır: Visual Basic'den COM Nesnelerine Başvuru Yapma</span><span class="sxs-lookup"><span data-stu-id="56c52-102">How to: Reference COM Objects from Visual Basic</span></span>
<span data-ttu-id="56c52-103">Visual Basic'te tür kitaplıklarının COM nesneleri başvuruları ekleme birlikte çalışabilirlik bütünleştirilmiş oluşturulması için COM kitaplığı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="56c52-103">In Visual Basic, adding references to COM objects that have type libraries requires the creation of an interop assembly for the COM library.</span></span> <span data-ttu-id="56c52-104">COM Nesne üyeleri için başvurular birlikte çalışma derlemesine yönlendirilir ve gerçek COM nesneye iletilir.</span><span class="sxs-lookup"><span data-stu-id="56c52-104">References to the members of the COM object are routed to the interop assembly and then forwarded to the actual COM object.</span></span> <span data-ttu-id="56c52-105">COM nesnesi yanıtlarının birlikte çalışma derlemesine yönlendirilir ve iletilir, [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="56c52-105">Responses from the COM object are routed to the interop assembly and forwarded to your [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] application.</span></span>  
  
 <span data-ttu-id="56c52-106">Bir .NET derlemesi COM nesnesinin tür bilgilerini katıştırma ile birlikte çalışma bütünleştirilmiş kullanmadan bir COM nesnesi başvuruda bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="56c52-106">You can reference a COM object without using an interop assembly by embedding the type information for the COM object in a .NET assembly.</span></span> <span data-ttu-id="56c52-107">Tür bilgileri katıştırmak için `Embed Interop Types` özelliğine `True` COM Nesne başvurusunu için.</span><span class="sxs-lookup"><span data-stu-id="56c52-107">To embed type information, set the `Embed Interop Types` property to `True` for the reference to the COM object.</span></span> <span data-ttu-id="56c52-108">Komut satırı derleyicisini kullanarak derlediğiniz kullanırsanız `/link` COM kitaplığı başvurusu için seçeneği.</span><span class="sxs-lookup"><span data-stu-id="56c52-108">If you are compiling by using the command-line compiler, use the `/link` option to reference the COM library.</span></span> <span data-ttu-id="56c52-109">Daha fazla bilgi için bkz: [/Link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md).</span><span class="sxs-lookup"><span data-stu-id="56c52-109">For more information, see [/link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md).</span></span>  
  
 <span data-ttu-id="56c52-110">Tümleşik geliştirme ortamı (IDE) bir tür kitaplığı için bir başvuru eklediğinizde, Visual Basic birlikte çalışma derlemeleri otomatik olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="56c52-110">Visual Basic automatically creates interop assemblies when you add a reference to a type library from the integrated development environment (IDE).</span></span> <span data-ttu-id="56c52-111">Komut satırından çalışırken, el ile birlikte çalışma derlemeleri oluşturma için Tlbimp yardımcı programını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56c52-111">When working from the command line, you can use the Tlbimp utility to manually create interop assemblies.</span></span>  
  
### <a name="to-add-references-to-com-objects"></a><span data-ttu-id="56c52-112">COM nesneleri eklemek için</span><span class="sxs-lookup"><span data-stu-id="56c52-112">To add references to COM objects</span></span>  
  
1.  <span data-ttu-id="56c52-113">Üzerinde **proje** menüsünde seçin **Başvuru Ekle** ve ardından **COM** iletişim kutusundaki sekmesi.</span><span class="sxs-lookup"><span data-stu-id="56c52-113">On the **Project** menu, choose **Add Reference** and then click the **COM** tab in the dialog box.</span></span>  
  
2.  <span data-ttu-id="56c52-114">COM nesneleri listesinden kullanmak istediğiniz bileşeni seçin.</span><span class="sxs-lookup"><span data-stu-id="56c52-114">Select the component you want to use from the list of COM objects.</span></span>  
  
3.  <span data-ttu-id="56c52-115">Birlikte çalışma derlemesi erişimi kolaylaştırmak için add bir `Imports` sınıfı veya COM nesnesi içinde kullanacağınız modülü üstüne deyimi.</span><span class="sxs-lookup"><span data-stu-id="56c52-115">To simplify access to the interop assembly, add an `Imports` statement to the top of the class or module in which you will use the COM object.</span></span> <span data-ttu-id="56c52-116">Örneğin, aşağıdaki kod örneğinde ad alır `INKEDLib` başvurulan nesneler için `Microsoft InkEdit Control 1.0` kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="56c52-116">For example, the following code example imports the namespace `INKEDLib` for objects referenced in the `Microsoft InkEdit Control 1.0` library.</span></span>  
  
     [!code-vb[VbVbalrInterop#40](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/how-to-reference-com-objects_1.vb)]  
  
### <a name="to-create-an-interop-assembly-using-tlbimp"></a><span data-ttu-id="56c52-117">Birlikte çalışma bütünleştirilmiş Tlbimp kullanarak oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="56c52-117">To create an interop assembly using Tlbimp</span></span>  
  
1.  <span data-ttu-id="56c52-118">Bunu zaten arama yolu parçası olmayan ve, şu anda bulunduğu dizinde olmayan Tlbimp konumunu arama yoluna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="56c52-118">Add the location of Tlbimp to the search path, if it is not already part of the search path and you are not currently in the directory where it is located.</span></span>  
  
2.  <span data-ttu-id="56c52-119">Çağrı, bir komut isteminden aşağıdaki bilgileri sağlayarak Tlbimp:</span><span class="sxs-lookup"><span data-stu-id="56c52-119">Call Tlbimp from a command prompt, providing the following information:</span></span>  
  
    -   <span data-ttu-id="56c52-120">Ad ve tür kitaplığı içeren dll Dosyasının konumu</span><span class="sxs-lookup"><span data-stu-id="56c52-120">Name and location of the DLL that contains the type library</span></span>  
  
    -   <span data-ttu-id="56c52-121">Ad ve konum bilgileri nereye yerleştirileceğini ad alanı</span><span class="sxs-lookup"><span data-stu-id="56c52-121">Name and location of the namespace where the information should be placed</span></span>  
  
    -   <span data-ttu-id="56c52-122">Ad ve konum hedef birlikte çalışma derlemesinin</span><span class="sxs-lookup"><span data-stu-id="56c52-122">Name and location of the target interop assembly</span></span>  
  
     <span data-ttu-id="56c52-123">Aşağıdaki kod bir örnek sağlar:</span><span class="sxs-lookup"><span data-stu-id="56c52-123">The following code provides an example:</span></span>  
  
    ```  
    Tlbimp test3.dll /out:NameSpace1 /out:Interop1.dll  
    ```  
  
     <span data-ttu-id="56c52-124">Kayıtsız COM nesneleri için bile tür kitaplıkları için birlikte çalışma derlemeleri oluşturma için Tlbimp kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56c52-124">You can use Tlbimp to create interop assemblies for type libraries, even for unregistered COM objects.</span></span> <span data-ttu-id="56c52-125">Ancak, birlikte çalışma derlemeleri tarafından başvurulan COM nesneleri düzgün kullanılacak oldukları bilgisayarda kayıtlı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="56c52-125">However, the COM objects referred to by interop assemblies must be properly registered on the computer where they are to be used.</span></span> <span data-ttu-id="56c52-126">Bir COM nesnesi ile Windows işletim sisteminde Regsvr32 yardımcı programını kullanarak kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56c52-126">You can register a COM object by using the Regsvr32 utility included with the Windows operating system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56c52-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="56c52-127">See Also</span></span>  
 [<span data-ttu-id="56c52-128">COM Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="56c52-128">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)  
 [<span data-ttu-id="56c52-129">Tlbimp.exe (Tür Kitaplığı İçeri Aktarıcı)</span><span class="sxs-lookup"><span data-stu-id="56c52-129">Tlbimp.exe (Type Library Importer)</span></span>](../../../framework/tools/tlbimp-exe-type-library-importer.md)  
 [<span data-ttu-id="56c52-130">Tlbexp.exe (Tür Kitaplığı Dışarı Aktarıcı)</span><span class="sxs-lookup"><span data-stu-id="56c52-130">Tlbexp.exe (Type Library Exporter)</span></span>](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d)  
 [<span data-ttu-id="56c52-131">İzlenecek yol: COM Nesnelerinde Kalıtım Uygulama</span><span class="sxs-lookup"><span data-stu-id="56c52-131">Walkthrough: Implementing Inheritance with COM Objects</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 [<span data-ttu-id="56c52-132">Birlikte Çalışabilirlik İle İlgili Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="56c52-132">Troubleshooting Interoperability</span></span>](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)  
 [<span data-ttu-id="56c52-133">Imports Deyimi (.NET Ad Alanı ve Türü)</span><span class="sxs-lookup"><span data-stu-id="56c52-133">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
