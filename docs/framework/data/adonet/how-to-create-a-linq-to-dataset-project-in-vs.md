---
title: "Nasıl yapılır: Visual Studio'da bir LINQ to DataSet projesi oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 49ba6cb0-cdd2-4571-aeaa-25bf0f40e9b3
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 3add191250a10d1d6016263ada0ba53fc8082717
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-create-a-linq-to-dataset-project-in-visual-studio"></a><span data-ttu-id="69751-102">Nasıl yapılır: Visual Studio'da bir LINQ to DataSet projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="69751-102">How to: Create a LINQ to DataSet Project In Visual Studio</span></span>
<span data-ttu-id="69751-103">Farklı türde [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] projeleri gerektiren belirli içeri aktarılan ad alanları (Visual Basic) veya `using` yönergeleri (C#) ve başvuruları.</span><span class="sxs-lookup"><span data-stu-id="69751-103">The different types of [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] projects require certain imported namespaces (Visual Basic) or `using` directives (C#) and references.</span></span> <span data-ttu-id="69751-104">En düşük gereksinim System.Core.dll başvurusudur ve `using` için yönerge <xref:System.Linq>.</span><span class="sxs-lookup"><span data-stu-id="69751-104">The minimum requirement is a reference to System.Core.dll and a `using` directive for <xref:System.Linq>.</span></span> <span data-ttu-id="69751-105">Yeni bir oluşturursanız, varsayılan olarak, bunlar sağlanan [!INCLUDE[csharp_orcas_long](../../../../includes/csharp-orcas-long-md.md)] projesi.</span><span class="sxs-lookup"><span data-stu-id="69751-105">By default, these are supplied if you create a new [!INCLUDE[csharp_orcas_long](../../../../includes/csharp-orcas-long-md.md)] project.</span></span> [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]<span data-ttu-id="69751-106">Ayrıca bir başvuru System.Data.dll ve System.Data.DataSetExtensions.dll gerektirir ve bir `Imports` (Visual Basic) veya `using` yönergesi (C#).</span><span class="sxs-lookup"><span data-stu-id="69751-106"> also requires a reference to System.Data.dll and System.Data.DataSetExtensions.dll and an `Imports` (Visual Basic) or `using` (C#) directive.</span></span>  
  
 <span data-ttu-id="69751-107">Bir proje Visual Studio'nun önceki bir sürümünden yükseltme yapıyorsanız, bu LINQ ile ilgili başvuruları el ile sağlamanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="69751-107">If you are upgrading a project from an earlier version of Visual Studio, you might have to supply these LINQ-related references manually.</span></span> <span data-ttu-id="69751-108">.NET Framework sürüm 3.5 hedeflemek için projeyi el ile ayarlamanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="69751-108">You might also have to manually set the project to target the .NET Framework version 3.5.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="69751-109">Bir komut isteminden oluşturuluyorsa, el ile LINQ ile ilgili DLL'leri başvurmalıdır `drive` **:**\Program Files\Reference Assemblies\Microsoft\Framework\v3.5.</span><span class="sxs-lookup"><span data-stu-id="69751-109">If you are building from a command prompt, you must manually reference the LINQ-related DLLs in `drive`**:**\Program Files\Reference Assemblies\Microsoft\Framework\v3.5.</span></span>  
  
### <a name="to-target-the-net-framework-35"></a><span data-ttu-id="69751-110">Hedef .NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="69751-110">To target the .NET Framework 3.5</span></span>  
  
1.  <span data-ttu-id="69751-111">İçinde [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)], yeni bir Visual Basic veya C# projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="69751-111">In [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)], create a new Visual Basic or C# project.</span></span> <span data-ttu-id="69751-112">Alternatif olarak, Visual Studio 2005'te oluşturulmuş bir Visual Basic veya C# projesini açın ve dönüştürün yönergeleri izleyerek bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] projesi.</span><span class="sxs-lookup"><span data-stu-id="69751-112">Alternatively, you can open a Visual Basic or C# project that was created in Visual Studio 2005 and follow the prompts to convert it to a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] project.</span></span>  
  
2.  <span data-ttu-id="69751-113">Bir C# projesi için tıklatın **proje** menüsüne ve ardından **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="69751-113">For a C# project, click the **Project** menu, and then click **Properties**.</span></span>  
  
    1.  <span data-ttu-id="69751-114">İçinde **uygulama** özellik sayfası, select .NET Framework 3.5 **hedef Framework** aşağı açılan liste.</span><span class="sxs-lookup"><span data-stu-id="69751-114">In the **Application** property page, select .NET Framework 3.5 in the **Target Framework** drop-down list.</span></span>  
  
3.  <span data-ttu-id="69751-115">Visual Basic proje için tıklatın **proje** menüsüne ve ardından **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="69751-115">For a Visual Basic project, click the **Project** menu, and then click **Properties**.</span></span>  
  
    1.  <span data-ttu-id="69751-116">İçinde **derleme** özellik sayfası, tıklatın **Gelişmiş derleme seçenekleri** ve .NET Framework 3. 5'ın ardından **hedef Framework'ü (tüm yapılandırmaları)** aşağı açılan liste.</span><span class="sxs-lookup"><span data-stu-id="69751-116">In the **Compile** property page, click **Advanced Compile Options** and then select .NET Framework 3.5 in the **Target Framework (all configurations)** drop-down list.</span></span>  
  
4.  <span data-ttu-id="69751-117">Üzerinde **proje** menüsünde tıklatın **Başvuru Ekle**, tıklatın **.NET** sekmesinde, aşağı kaydırarak **System.Core**, tıklatın ve ardından tıklatın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="69751-117">On the **Project** menu, click **Add Reference**, click the **.NET** tab, scroll down to **System.Core**, click it, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="69751-118">Ekleme bir `using` yönergesi veya içeri aktarılan ad alanı için <xref:System.Linq> kaynak kodu dosyasının veya projesi.</span><span class="sxs-lookup"><span data-stu-id="69751-118">Add a `using` directive or imported namespace for <xref:System.Linq> to your source code file or project.</span></span>  
  
     <span data-ttu-id="69751-119">Daha fazla bilgi için bkz: [using yönergesi](~/docs/csharp/language-reference/keywords/using-directive.md) veya [nasıl yapılır: içeri aktarılan ad alanları (Visual Basic) ekleyip](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="69751-119">For more information, see [using Directive](~/docs/csharp/language-reference/keywords/using-directive.md) or [How to: Add or Remove Imported Namespaces (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span></span>  
  
### <a name="to-enable-linq-to-dataset-functionality"></a><span data-ttu-id="69751-120">LINQ DataSet işlevselliğini etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="69751-120">To enable LINQ to DataSet functionality</span></span>  
  
1.  <span data-ttu-id="69751-121">Gerekirse, System.Core.dll başvuru eklemek için bu konunun önceki adımları ve `using` System.Linq için yönerge veya içeri aktarılan ad alanı.</span><span class="sxs-lookup"><span data-stu-id="69751-121">If necessary, follow the steps earlier in this topic to add a reference to System.Core.dll and a `using` directive or imported namespace for System.Linq.</span></span>  
  
2.  <span data-ttu-id="69751-122">C# veya Visual Basic tıklatın **proje** menüsüne ve ardından **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="69751-122">In C# or Visual Basic, click the **Project** menu, and then click **Add Reference**.</span></span>  
  
3.  <span data-ttu-id="69751-123">İçinde **Başvuru Ekle** iletişim kutusu, tıklatın **.NET** üstte değilse sekmesinde.</span><span class="sxs-lookup"><span data-stu-id="69751-123">In the **Add Reference** dialog box, click the **.NET** tab if it is not on top.</span></span> <span data-ttu-id="69751-124">Ekranı aşağı kaydırarak **System.Data** ve **System.Data.DataSetExtensions** ve bunlar üzerinde'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="69751-124">Scroll down to **System.Data** and **System.Data.DataSetExtensions** and click on them.</span></span> <span data-ttu-id="69751-125">Tıklatın **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="69751-125">Click the **OK** button.</span></span>  
  
4.  <span data-ttu-id="69751-126">Ekleme bir `using` yönergesi veya içeri aktarılan ad alanı için <xref:System.Data> kaynak kodu dosyasının veya projesi.</span><span class="sxs-lookup"><span data-stu-id="69751-126">Add a `using` directive or imported namespace for <xref:System.Data> to your source code file or project.</span></span> <span data-ttu-id="69751-127">Daha fazla bilgi için bkz: [using yönergesi](~/docs/csharp/language-reference/keywords/using-directive.md) veya [nasıl yapılır: içeri aktarılan ad alanları (Visual Basic) ekleyip](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="69751-127">For more information, see [using Directive](~/docs/csharp/language-reference/keywords/using-directive.md) or [How to: Add or Remove Imported Namespaces (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span></span>  
  
5.  <span data-ttu-id="69751-128">System.Data.DataSetExtensions.dll başvuru Dataset işlevselliğini LINQ ekleyin.</span><span class="sxs-lookup"><span data-stu-id="69751-128">Add a reference to System.Data.DataSetExtensions.dll for LINQ to Dataset functionality.</span></span> <span data-ttu-id="69751-129">Zaten yoksa, System.Data.dll bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="69751-129">Add a reference to System.Data.dll if it does not already exist.</span></span>  
  
6.  <span data-ttu-id="69751-130">İsteğe bağlı olarak ekleyin bir `using` yönergesi veya içeri aktarılan ad alanı için `System.Data.Common` veya `System.Data.SqlClient`veritabanına nasıl bağlanacağınızı bağlı olarak.</span><span class="sxs-lookup"><span data-stu-id="69751-130">Optionally, add a `using` directive or imported namespace for `System.Data.Common` or `System.Data.SqlClient`, depending on how you connect to the database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69751-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="69751-131">See Also</span></span>  
 [<span data-ttu-id="69751-132">Başlarken</span><span class="sxs-lookup"><span data-stu-id="69751-132">Getting Started</span></span>](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)  
 [<span data-ttu-id="69751-133">LINQ Kullanmaya Başlama</span><span class="sxs-lookup"><span data-stu-id="69751-133">Getting Started with LINQ</span></span>](http://msdn.microsoft.com/en-us/6cc9af04-950a-4cc3-83d4-2aeb4abe4de9)
