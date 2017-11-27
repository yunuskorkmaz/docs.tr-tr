---
title: "Nasıl yapılır: Visual Basic'den COM Nesnelerine Başvuru Yapma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- COM interop [Visual Basic], referencing COM objects
- referencing objects, COM objects from Visual Basic
- objects [Visual Basic], referencing
- COM objects, referencing
- interop assemblies
ms.assetid: 9c518fb4-27d9-4112-9e6a-5a7d0210af6f
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 694bd74e2b5ae374269accd845fe9178958bf56c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-reference-com-objects-from-visual-basic"></a><span data-ttu-id="b6d3b-102">Nasıl yapılır: Visual Basic'den COM Nesnelerine Başvuru Yapma</span><span class="sxs-lookup"><span data-stu-id="b6d3b-102">How to: Reference COM Objects from Visual Basic</span></span>
<span data-ttu-id="b6d3b-103">İçinde [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], tür kitaplıklarının COM nesneleri başvuruları ekleme birlikte çalışma derlemesi oluşturma için COM kitaplığı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b6d3b-103">In [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], adding references to COM objects that have type libraries requires the creation of an interop assembly for the COM library.</span></span> <span data-ttu-id="b6d3b-104">COM Nesne üyeleri için başvurular birlikte çalışma derlemesine yönlendirilir ve gerçek COM nesneye iletilir.</span><span class="sxs-lookup"><span data-stu-id="b6d3b-104">References to the members of the COM object are routed to the interop assembly and then forwarded to the actual COM object.</span></span> <span data-ttu-id="b6d3b-105">COM nesnesi yanıtlarının birlikte çalışma derlemesine yönlendirilir ve iletilir, [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="b6d3b-105">Responses from the COM object are routed to the interop assembly and forwarded to your [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] application.</span></span>  
  
 <span data-ttu-id="b6d3b-106">Bir .NET derlemesi COM nesnesinin tür bilgilerini katıştırma ile birlikte çalışma bütünleştirilmiş kullanmadan bir COM nesnesi başvuruda bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="b6d3b-106">You can reference a COM object without using an interop assembly by embedding the type information for the COM object in a .NET assembly.</span></span> <span data-ttu-id="b6d3b-107">Tür bilgileri katıştırmak için `Embed Interop Types` özelliğine `True` COM Nesne başvurusunu için.</span><span class="sxs-lookup"><span data-stu-id="b6d3b-107">To embed type information, set the `Embed Interop Types` property to `True` for the reference to the COM object.</span></span> <span data-ttu-id="b6d3b-108">Komut satırı derleyicisini kullanarak derlediğiniz kullanırsanız `/link` COM kitaplığı başvurusu için seçeneği.</span><span class="sxs-lookup"><span data-stu-id="b6d3b-108">If you are compiling by using the command-line compiler, use the `/link` option to reference the COM library.</span></span> <span data-ttu-id="b6d3b-109">Daha fazla bilgi için bkz: [/Link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md).</span><span class="sxs-lookup"><span data-stu-id="b6d3b-109">For more information, see [/link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md).</span></span>  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="b6d3b-110">tümleşik geliştirme ortamı (IDE) bir tür kitaplığı için bir başvuru eklediğinizde birlikte çalışma derlemeleri otomatik olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b6d3b-110"> automatically creates interop assemblies when you add a reference to a type library from the integrated development environment (IDE).</span></span> <span data-ttu-id="b6d3b-111">Komut satırından çalışırken, el ile birlikte çalışma derlemeleri oluşturma için Tlbimp yardımcı programını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6d3b-111">When working from the command line, you can use the Tlbimp utility to manually create interop assemblies.</span></span>  
  
### <a name="to-add-references-to-com-objects"></a><span data-ttu-id="b6d3b-112">COM nesneleri eklemek için</span><span class="sxs-lookup"><span data-stu-id="b6d3b-112">To add references to COM objects</span></span>  
  
1.  <span data-ttu-id="b6d3b-113">Üzerinde **proje** menüsünde seçin **Başvuru Ekle** ve ardından **COM** iletişim kutusundaki sekmesi.</span><span class="sxs-lookup"><span data-stu-id="b6d3b-113">On the **Project** menu, choose **Add Reference** and then click the **COM** tab in the dialog box.</span></span>  
  
2.  <span data-ttu-id="b6d3b-114">COM nesneleri listesinden kullanmak istediğiniz bileşeni seçin.</span><span class="sxs-lookup"><span data-stu-id="b6d3b-114">Select the component you want to use from the list of COM objects.</span></span>  
  
3.  <span data-ttu-id="b6d3b-115">Birlikte çalışma derlemesi erişimi kolaylaştırmak için add bir `Imports` sınıfı veya COM nesnesi içinde kullanacağınız modülü üstüne deyimi.</span><span class="sxs-lookup"><span data-stu-id="b6d3b-115">To simplify access to the interop assembly, add an `Imports` statement to the top of the class or module in which you will use the COM object.</span></span> <span data-ttu-id="b6d3b-116">Örneğin, aşağıdaki kod örneğinde ad alır `INKEDLib` başvurulan nesneler için `Microsoft InkEdit Control 1.0` kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="b6d3b-116">For example, the following code example imports the namespace `INKEDLib` for objects referenced in the `Microsoft InkEdit Control 1.0` library.</span></span>  
  
     [!code-vb[VbVbalrInterop#40](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/how-to-reference-com-objects_1.vb)]  
  
### <a name="to-create-an-interop-assembly-using-tlbimp"></a><span data-ttu-id="b6d3b-117">Birlikte çalışma bütünleştirilmiş Tlbimp kullanarak oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="b6d3b-117">To create an interop assembly using Tlbimp</span></span>  
  
1.  <span data-ttu-id="b6d3b-118">Bunu zaten arama yolu parçası olmayan ve, şu anda bulunduğu dizinde olmayan Tlbimp konumunu arama yoluna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b6d3b-118">Add the location of Tlbimp to the search path, if it is not already part of the search path and you are not currently in the directory where it is located.</span></span>  
  
2.  <span data-ttu-id="b6d3b-119">Çağrı, bir komut isteminden aşağıdaki bilgileri sağlayarak Tlbimp:</span><span class="sxs-lookup"><span data-stu-id="b6d3b-119">Call Tlbimp from a command prompt, providing the following information:</span></span>  
  
    -   <span data-ttu-id="b6d3b-120">Ad ve tür kitaplığı içeren dll Dosyasının konumu</span><span class="sxs-lookup"><span data-stu-id="b6d3b-120">Name and location of the DLL that contains the type library</span></span>  
  
    -   <span data-ttu-id="b6d3b-121">Ad ve konum bilgileri nereye yerleştirileceğini ad alanı</span><span class="sxs-lookup"><span data-stu-id="b6d3b-121">Name and location of the namespace where the information should be placed</span></span>  
  
    -   <span data-ttu-id="b6d3b-122">Ad ve konum hedef birlikte çalışma derlemesinin</span><span class="sxs-lookup"><span data-stu-id="b6d3b-122">Name and location of the target interop assembly</span></span>  
  
     <span data-ttu-id="b6d3b-123">Aşağıdaki kod bir örnek sağlar:</span><span class="sxs-lookup"><span data-stu-id="b6d3b-123">The following code provides an example:</span></span>  
  
    ```  
    Tlbimp test3.dll /out:NameSpace1 /out:Interop1.dll  
    ```  
  
     <span data-ttu-id="b6d3b-124">Kayıtsız COM nesneleri için bile tür kitaplıkları için birlikte çalışma derlemeleri oluşturma için Tlbimp kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6d3b-124">You can use Tlbimp to create interop assemblies for type libraries, even for unregistered COM objects.</span></span> <span data-ttu-id="b6d3b-125">Ancak, birlikte çalışma derlemeleri tarafından başvurulan COM nesneleri düzgün kullanılacak oldukları bilgisayarda kayıtlı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b6d3b-125">However, the COM objects referred to by interop assemblies must be properly registered on the computer where they are to be used.</span></span> <span data-ttu-id="b6d3b-126">Bir COM nesnesi ile Windows işletim sisteminde Regsvr32 yardımcı programını kullanarak kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6d3b-126">You can register a COM object by using the Regsvr32 utility included with the Windows operating system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6d3b-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b6d3b-127">See Also</span></span>  
 [<span data-ttu-id="b6d3b-128">COM birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="b6d3b-128">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)  
 [<span data-ttu-id="b6d3b-129">Tlbimp.exe (tür kitaplığı içeri Aktarıcı)</span><span class="sxs-lookup"><span data-stu-id="b6d3b-129">Tlbimp.exe (Type Library Importer)</span></span>](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382)  
 [<span data-ttu-id="b6d3b-130">Tlbexp.exe (tür kitaplığı dışarı Aktarıcı)</span><span class="sxs-lookup"><span data-stu-id="b6d3b-130">Tlbexp.exe (Type Library Exporter)</span></span>](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d)  
 [<span data-ttu-id="b6d3b-131">İzlenecek yol: COM nesnelerinde kalıtım uygulama</span><span class="sxs-lookup"><span data-stu-id="b6d3b-131">Walkthrough: Implementing Inheritance with COM Objects</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 [<span data-ttu-id="b6d3b-132">Birlikte çalışabilirlik sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="b6d3b-132">Troubleshooting Interoperability</span></span>](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)  
 [<span data-ttu-id="b6d3b-133">Imports deyimi (.NET Namespace ve türü)</span><span class="sxs-lookup"><span data-stu-id="b6d3b-133">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
