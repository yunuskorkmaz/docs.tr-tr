---
title: "İzlenecek Yol: Genişletilebilir Uygulama Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- views [.NET Framework], add-in pipeline
- host-side adapters for add-ins [.NET Framework]
- add-in pipeline [.NET Framework], creating
- add-in-side adapter [.NET Framework]
- contracts for add-in pipelines [.NET Framework]
ms.assetid: 694a33c5-a040-450d-aed5-ac49fc88ce61
caps.latest.revision: "32"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5cee99346d19c632739bcc6540c43f1a35217a2f
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-creating-an-extensible-application"></a><span data-ttu-id="1b0fe-102">İzlenecek Yol: Genişletilebilir Uygulama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1b0fe-102">Walkthrough: Creating an Extensible Application</span></span>
<span data-ttu-id="1b0fe-103">Bu kılavuz, basit hesaplayıcı işlevler gerçekleştirdiği bir eklenti için bir işlem hattı oluşturma açıklar.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-103">This walkthrough describes how to create a pipeline for an add-in that performs simple calculator functions.</span></span> <span data-ttu-id="1b0fe-104">Gerçek dünya senaryoları gösterilmemiştir; Bunun yerine, bir ardışık düzen ve nasıl bir eklenti için hizmetleri bir konak sağlayabilir temel işlevselliğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-104">It does not demonstrate a real-world scenario; rather, it demonstrates the basic functionality of a pipeline and how an add-in can provide services for a host.</span></span>  
  
 <span data-ttu-id="1b0fe-105">Bu kılavuz aşağıdaki görevler açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="1b0fe-105">This walkthrough describes the following tasks:</span></span>  
  
-   <span data-ttu-id="1b0fe-106">Visual Studio çözümü oluşturma.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-106">Creating a Visual Studio solution.</span></span>  
  
-   <span data-ttu-id="1b0fe-107">Ardışık Düzen dizin yapısı oluşturma.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-107">Creating the pipeline directory structure.</span></span>  
  
-   <span data-ttu-id="1b0fe-108">Sözleşme ve görünümler oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-108">Creating the contract and views.</span></span>  
  
-   <span data-ttu-id="1b0fe-109">Ekle tarafı bağdaştırıcısı oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-109">Creating the add-in-side adapter.</span></span>  
  
-   <span data-ttu-id="1b0fe-110">Konak tarafındaki bağdaştırıcı oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-110">Creating the host-side adapter.</span></span>  
  
-   <span data-ttu-id="1b0fe-111">Ana bilgisayar oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-111">Creating the host.</span></span>  
  
-   <span data-ttu-id="1b0fe-112">Eklentisi oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-112">Creating the add-in.</span></span>  
  
-   <span data-ttu-id="1b0fe-113">Ardışık Düzen dağıtma.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-113">Deploying the pipeline.</span></span>  
  
-   <span data-ttu-id="1b0fe-114">Ana bilgisayar uygulaması çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-114">Running the host application.</span></span>  
  
 <span data-ttu-id="1b0fe-115">Bu ardışık seri hale getirilebilir türler yalnızca geçirir (<xref:System.Double> ve <xref:System.String>), konak ve eklenti arasında.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-115">This pipeline passes only serializable types (<xref:System.Double> and <xref:System.String>), between the host and the add-in.</span></span> <span data-ttu-id="1b0fe-116">Karmaşık veri türlerinin koleksiyonları geçirmek nasıl oluşturulduğunu gösteren örnek için bkz: [izlenecek yol: konaklar arasında geçirme koleksiyonları ve eklentiler](http://msdn.microsoft.com/library/b532c604-548e-4fab-b11c-377257dd0ee5).</span><span class="sxs-lookup"><span data-stu-id="1b0fe-116">For an example that shows how to pass collections of complex data types, see [Walkthrough: Passing Collections Between Hosts and Add-Ins](http://msdn.microsoft.com/library/b532c604-548e-4fab-b11c-377257dd0ee5).</span></span>  
  
 <span data-ttu-id="1b0fe-117">Bu ardışık düzen sözleşme dört aritmetik işlemler bir nesne modelini tanımlar: ekleme, çıkarma, çarpma ve bölme.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-117">The contract for this pipeline defines an object model of four arithmetic operations: add, subtract, multiply, and divide.</span></span> <span data-ttu-id="1b0fe-118">Eklenti konağa sonucunu döndürür ve ana bilgisayar 2 + 2 gibi hesaplamakta bir eşitlik eklenti sağlar.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-118">The host provides the add-in with an equation to calculate, such as 2 + 2, and the add-in returns the result to the host.</span></span>  
  
 <span data-ttu-id="1b0fe-119">Sürüm 2 hesaplayıcı eklentisi fazla hesaplama olasılıkları sağlar ve sürüm oluşturma gösterir.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-119">Version 2 of the calculator add-in provides more calculating possibilities and demonstrates versioning.</span></span> <span data-ttu-id="1b0fe-120">Bölümünde açıklanan [izlenecek yol: ana bilgisayar değişikliklerinizi olarak geriye dönük uyumluluk etkinleştirme](http://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848).</span><span class="sxs-lookup"><span data-stu-id="1b0fe-120">It is described in [Walkthrough: Enabling Backward Compatibility as Your Host Changes](http://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="1b0fe-121">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="1b0fe-121">Prerequisites</span></span>  
 <span data-ttu-id="1b0fe-122">Bu izlenecek yolu tamamlamak için aşağıdakiler gerekir:</span><span class="sxs-lookup"><span data-stu-id="1b0fe-122">You need the following to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]<span data-ttu-id="1b0fe-123">.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-123">.</span></span>  
  
## <a name="creating-a-visual-studio-solution"></a><span data-ttu-id="1b0fe-124">Visual Studio çözümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="1b0fe-124">Creating a Visual Studio Solution</span></span>  
 <span data-ttu-id="1b0fe-125">Bir çözümde kullanmak [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] ardışık düzen segmentlerinizi projeleri içerecek biçimde.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-125">Use a solution in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] to contain the projects of your pipeline segments.</span></span>  
  
#### <a name="to-create-the-pipeline-solution"></a><span data-ttu-id="1b0fe-126">Ardışık Düzen çözüm oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="1b0fe-126">To create the pipeline solution</span></span>  
  
1.  <span data-ttu-id="1b0fe-127">İçinde [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], adlı yeni bir proje oluşturma `Calc1Contract`.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-127">In [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], create a new project named `Calc1Contract`.</span></span> <span data-ttu-id="1b0fe-128">İçin temel **sınıf kitaplığı** şablonu.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-128">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="1b0fe-129">Çözüm adı `CalculatorV1`.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-129">Name the solution `CalculatorV1`.</span></span>  
  
## <a name="creating-the-pipeline-directory-structure"></a><span data-ttu-id="1b0fe-130">Ardışık Düzen dizin yapısı oluşturma</span><span class="sxs-lookup"><span data-stu-id="1b0fe-130">Creating the Pipeline Directory Structure</span></span>  
 <span data-ttu-id="1b0fe-131">Eklenti modeli belirtilen dizin yapısında yerleştirilecek ardışık düzen segment derlemeler gerektirir.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-131">The add-in model requires the pipeline segment assemblies to be placed in a specified directory structure.</span></span> <span data-ttu-id="1b0fe-132">Ardışık Düzen yapısı hakkında daha fazla bilgi için bkz: [ardışık düzen geliştirme gereksinimleri](http://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span><span class="sxs-lookup"><span data-stu-id="1b0fe-132">For more information about the pipeline structure, see [Pipeline Development Requirements](http://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span></span>  
  
#### <a name="to-create-the-pipeline-directory-structure"></a><span data-ttu-id="1b0fe-133">Ardışık Düzen dizin yapısını oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="1b0fe-133">To create the pipeline directory structure</span></span>  
  
1.  <span data-ttu-id="1b0fe-134">Bir uygulama klasörü herhangi bir yerden bilgisayarınızda oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-134">Create an application folder anywhere on your computer.</span></span>  
  
2.  <span data-ttu-id="1b0fe-135">Bu klasörde aşağıdaki yapısını oluşturun:</span><span class="sxs-lookup"><span data-stu-id="1b0fe-135">In that folder, create the following structure:</span></span>  
  
    ```  
    Pipeline  
      AddIns  
        CalcV1  
        CalcV2  
      AddInSideAdapters  
      AddInViews  
      Contracts  
      HostSideAdapters  
    ```  
  
     <span data-ttu-id="1b0fe-136">Uygulama klasörünüzde ardışık düzen klasör yapısı koymak gerekli değildir; Ayrıca, yalnızca kolaylık sağlamak için burada yapılır.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-136">It is not necessary to put the pipeline folder structure in your application folder; it is done here only for convenience.</span></span> <span data-ttu-id="1b0fe-137">Uygun adımda Kılavuzu ardışık düzen klasör yapısı farklı bir konumda ise kodunu değiştirmek açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-137">At the appropriate step, the walkthrough explains how to change the code if the pipeline folder structure is in a different location.</span></span> <span data-ttu-id="1b0fe-138">Ardışık Düzen directory gereksinimleri hakkında bilgi bkz [ardışık düzen geliştirme gereksinimleri](http://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span><span class="sxs-lookup"><span data-stu-id="1b0fe-138">See the discussion of pipeline directory requirements in [Pipeline Development Requirements](http://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1b0fe-139">`CalcV2` Klasör, bu kılavuzda kullanılmaz; için tutucudur [izlenecek yol: ana bilgisayar değişikliklerinizi olarak geriye dönük uyumluluk etkinleştirme](http://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848).</span><span class="sxs-lookup"><span data-stu-id="1b0fe-139">The `CalcV2` folder is not used in this walkthrough; it is a placeholder for [Walkthrough: Enabling Backward Compatibility as Your Host Changes](http://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848).</span></span>  
  
## <a name="creating-the-contract-and-views"></a><span data-ttu-id="1b0fe-140">Sözleşme ve görünümler oluşturma</span><span class="sxs-lookup"><span data-stu-id="1b0fe-140">Creating the Contract and Views</span></span>  
 <span data-ttu-id="1b0fe-141">Bu ardışık düzen sözleşme kesimini tanımlar `ICalc1Contract` dört yöntemleri tanımlar arabirimi: `add`, `subtract`, `multiply`, ve `divide`.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-141">The contract segment for this pipeline defines the `ICalc1Contract` interface, which defines four methods: `add`, `subtract`, `multiply`, and `divide`.</span></span>  
  
#### <a name="to-create-the-contract"></a><span data-ttu-id="1b0fe-142">Sözleşme oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="1b0fe-142">To create the contract</span></span>  
  
1.  <span data-ttu-id="1b0fe-143">Adlı Visual Studio çözümüne `CalculatorV1`, açık `Calc1Contract` projesi.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-143">In the Visual Studio solution named `CalculatorV1`, open the `Calc1Contract` project.</span></span>  
  
2.  <span data-ttu-id="1b0fe-144">İçinde **Çözüm Gezgini**, aşağıdaki derlemelerine başvurular ekleyin `Calc1Contract` proje:</span><span class="sxs-lookup"><span data-stu-id="1b0fe-144">In **Solution Explorer**, add references to the following assemblies to the `Calc1Contract` project:</span></span>  
  
     <span data-ttu-id="1b0fe-145">System.AddIn.Contract.dll</span><span class="sxs-lookup"><span data-stu-id="1b0fe-145">System.AddIn.Contract.dll</span></span>  
  
     <span data-ttu-id="1b0fe-146">System.AddIn.dll</span><span class="sxs-lookup"><span data-stu-id="1b0fe-146">System.AddIn.dll</span></span>  
  
3.  <span data-ttu-id="1b0fe-147">İçinde **Çözüm Gezgini**, yeni eklenen varsayılan sınıfı hariç **sınıf kitaplığı** projeleri.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-147">In **Solution Explorer**, exclude the default class that is added to new **Class Library** projects.</span></span>  
  
4.  <span data-ttu-id="1b0fe-148">İçinde **Çözüm Gezgini**, projesine yeni öğe eklemek kullanarak **arabirimi** şablonu.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-148">In **Solution Explorer**, add a new item to the project, using the **Interface** template.</span></span> <span data-ttu-id="1b0fe-149">İçinde **Yeni Öğe Ekle** iletişim kutusunda, adı arabirimi `ICalc1Contract`.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-149">In the **Add New Item** dialog box, name the interface `ICalc1Contract`.</span></span>  
  
5.  <span data-ttu-id="1b0fe-150">Arabirim dosyasında ad alanı başvurularını ekleyin <xref:System.AddIn.Contract> ve <xref:System.AddIn.Pipeline>.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-150">In the interface file, add namespace references to <xref:System.AddIn.Contract> and <xref:System.AddIn.Pipeline>.</span></span>  
  
6.  <span data-ttu-id="1b0fe-151">Bu sözleşme segment tamamlamak için aşağıdaki kodu kullanın.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-151">Use the following code to complete this contract segment.</span></span> <span data-ttu-id="1b0fe-152">Bu arabirim olmalıdır Not <xref:System.AddIn.Pipeline.AddInContractAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-152">Note that this interface must have the <xref:System.AddIn.Pipeline.AddInContractAttribute> attribute.</span></span>  
  
     [!code-csharp[AddInP1Contract#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1Contract/cs/ICalc1Contract.cs#1)]
     [!code-vb[AddInP1Contract#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1Contract/vb/ICalc1Contract.vb#1)]  
  
7.  <span data-ttu-id="1b0fe-153">İsteğe bağlı olarak, Visual Studio çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-153">Optionally, build the Visual Studio solution.</span></span> <span data-ttu-id="1b0fe-154">Son yordam, ancak her bir yordam her proje olmasını sağlar sonra derleme düzeltmeden çözüm çalıştırılamaz.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-154">The solution cannot be run until the final procedure, but building it after each procedure ensures that each project is correct.</span></span>  
  
 <span data-ttu-id="1b0fe-155">Eklenti görünümü ve konak görünümünü çünkü eklenti genellikle aynı kodu özellikle ilk sürümüne sahip bir eklenti, aynı anda kolayca görünümler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-155">Because the add-in view and the host view of the add-in usually have the same code, especially in the first version of an add-in, you can easily create the views at the same time.</span></span> <span data-ttu-id="1b0fe-156">Yalnızca bir faktörüyle farklı: eklenti görünümü gerektirir <xref:System.AddIn.Pipeline.AddInBaseAttribute> eklenti konak görünümünü öznitelikleri gerekmese özniteliği.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-156">They differ by only one factor: the add-in view requires the <xref:System.AddIn.Pipeline.AddInBaseAttribute> attribute, while the host view of the add-in does not require any attributes.</span></span>  
  
#### <a name="to-create-the-add-in-view"></a><span data-ttu-id="1b0fe-157">Eklenti görünümü oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="1b0fe-157">To create the add-in view</span></span>  
  
1.  <span data-ttu-id="1b0fe-158">Adlı yeni bir proje eklemek `Calc1AddInView` için `CalculatorV1` çözümü.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-158">Add a new project named `Calc1AddInView` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="1b0fe-159">İçin temel **sınıf kitaplığı** şablonu.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-159">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="1b0fe-160">İçinde **Çözüm Gezgini**, System.AddIn.dll için bir başvuru ekleyin `Calc1AddInView` projesi.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-160">In **Solution Explorer**, add a reference to System.AddIn.dll to the `Calc1AddInView` project.</span></span>  
  
3.  <span data-ttu-id="1b0fe-161">İçinde **Çözüm Gezgini**, yeni eklenen varsayılan sınıfı hariç **sınıf kitaplığı** projeleri ve projesine yeni öğe eklemek kullanarak **arabirimi** şablonu.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-161">In **Solution Explorer**, exclude the default class that is added to new **Class Library** projects, and add a new item to the project, using the **Interface** template.</span></span> <span data-ttu-id="1b0fe-162">İçinde **Yeni Öğe Ekle** iletişim kutusunda, adı arabirimi `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-162">In the **Add New Item** dialog box, name the interface `ICalculator`.</span></span>  
  
4.  <span data-ttu-id="1b0fe-163">Ad alanı referansı arabirimi dosyasına ekleyin <xref:System.AddIn.Pipeline>.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-163">In the interface file, add a namespace reference to <xref:System.AddIn.Pipeline>.</span></span>  
  
5.  <span data-ttu-id="1b0fe-164">Bu eklenti görünümü tamamlamak için aşağıdaki kodu kullanın.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-164">Use the following code to complete this add-in view.</span></span> <span data-ttu-id="1b0fe-165">Bu arabirim olmalıdır Not <xref:System.AddIn.Pipeline.AddInBaseAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-165">Note that this interface must have the <xref:System.AddIn.Pipeline.AddInBaseAttribute> attribute.</span></span>  
  
     [!code-csharp[AddInP1AddInViews#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInViews/cs/Calc1AddInView.cs#1)]
     [!code-vb[AddInP1AddInViews#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInViews/vb/Calc1AddInView.vb#1)]  
  
6.  <span data-ttu-id="1b0fe-166">İsteğe bağlı olarak, Visual Studio çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-166">Optionally, build the Visual Studio solution.</span></span>  
  
#### <a name="to-create-the-host-view-of-the-add-in"></a><span data-ttu-id="1b0fe-167">Eklenti konak görünümünü oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="1b0fe-167">To create the host view of the add-in</span></span>  
  
1.  <span data-ttu-id="1b0fe-168">Adlı yeni bir proje eklemek `Calc1HVA` için `CalculatorV1` çözümü.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-168">Add a new project named `Calc1HVA` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="1b0fe-169">İçin temel **sınıf kitaplığı** şablonu.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-169">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="1b0fe-170">İçinde **Çözüm Gezgini**, yeni eklenen varsayılan sınıfı hariç **sınıf kitaplığı** projeleri ve projesine yeni öğe eklemek kullanarak **arabirimi** şablonu.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-170">In **Solution Explorer**, exclude the default class that is added to new **Class Library** projects, and add a new item to the project, using the **Interface** template.</span></span> <span data-ttu-id="1b0fe-171">İçinde **Yeni Öğe Ekle** iletişim kutusunda, adı arabirimi `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-171">In the **Add New Item** dialog box, name the interface `ICalculator`.</span></span>  
  
3.  <span data-ttu-id="1b0fe-172">Arabirim dosyasında eklenti konak görünümünü tamamlamak için aşağıdaki kodu kullanın.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-172">In the interface file, use the following code to complete the host view of the add-in.</span></span>  
  
     [!code-csharp[AddInP1HVA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1HVA/cs/calc1hva.cs#1)]
     [!code-vb[AddInP1HVA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1HVA/vb/Calc1HVA.vb#1)]  
  
4.  <span data-ttu-id="1b0fe-173">İsteğe bağlı olarak, Visual Studio çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-173">Optionally, build the Visual Studio solution.</span></span>  
  
## <a name="creating-the-add-in-side-adapter"></a><span data-ttu-id="1b0fe-174">Ekleme tarafı bağdaştırıcısı oluşturma</span><span class="sxs-lookup"><span data-stu-id="1b0fe-174">Creating the Add-in-side Adapter</span></span>  
 <span data-ttu-id="1b0fe-175">Bu ekleme tarafı bağdaştırıcı bir görünüm sözleşme bağdaştırıcısı oluşur.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-175">This add-in-side adapter consists of one view-to-contract adapter.</span></span> <span data-ttu-id="1b0fe-176">Bu ardışık düzen segmenti türleri eklenti görünümünden sözleşmesine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-176">This pipeline segment converts the types from the add-in view to the contract.</span></span>  
  
 <span data-ttu-id="1b0fe-177">Bu ardışık düzendeki eklenti ana bilgisayara bir hizmet sunar ve ana bilgisayara akışı eklentiden türünü.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-177">In this pipeline, the add-in provides a service to the host, and the types flow from the add-in to the host.</span></span> <span data-ttu-id="1b0fe-178">Eklenti ana bilgisayardan akışı hiçbir türünü olduğundan, bu ardışık düzen eklenti tarafı sözleşme görünümü bağdaştırıcısında eklemek zorunda değil.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-178">Because no types flow from the host to the add-in, you do not have to include a contract-to-view adapter on the add-in side of this pipeline.</span></span>  
  
#### <a name="to-create-the-add-in-side-adapter"></a><span data-ttu-id="1b0fe-179">Ekle tarafı bağdaştırıcısı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="1b0fe-179">To create the add-in-side adapter</span></span>  
  
1.  <span data-ttu-id="1b0fe-180">Adlı yeni bir proje eklemek `Calc1AddInSideAdapter` için `CalculatorV1` çözümü.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-180">Add a new project named `Calc1AddInSideAdapter` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="1b0fe-181">İçin temel **sınıf kitaplığı** şablonu.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-181">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="1b0fe-182">İçinde **Çözüm Gezgini**, aşağıdaki derlemelerine başvurular ekleyin `Calc1AddInSideAdapter` proje:</span><span class="sxs-lookup"><span data-stu-id="1b0fe-182">In **Solution Explorer**, add references to the following assemblies to the `Calc1AddInSideAdapter` project:</span></span>  
  
     <span data-ttu-id="1b0fe-183">System.AddIn.dll</span><span class="sxs-lookup"><span data-stu-id="1b0fe-183">System.AddIn.dll</span></span>  
  
     <span data-ttu-id="1b0fe-184">System.AddIn.Contract.dll</span><span class="sxs-lookup"><span data-stu-id="1b0fe-184">System.AddIn.Contract.dll</span></span>  
  
3.  <span data-ttu-id="1b0fe-185">Proje başvurularını bitişik ardışık düzen kesimlerin projelerine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1b0fe-185">Add project references to the projects for the adjacent pipeline segments:</span></span>  
  
     `Calc1AddInView`  
  
     `Calc1Contract`  
  
4.  <span data-ttu-id="1b0fe-186">Her proje başvurusu seçin ve **özellikleri** ayarlamak **kopya yerel** için **False**.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-186">Select each project reference, and in **Properties** set **Copy Local** to **False**.</span></span> <span data-ttu-id="1b0fe-187">Visual Basic'teki **başvuruları** sekmesinde **proje özelliklerini** ayarlamak için **kopya yerel** için **False** iki proje başvuruları için.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-187">In Visual Basic, use the **References** tab of **Project Properties** to set **Copy Local** to **False** for the two project references.</span></span>  
  
5.  <span data-ttu-id="1b0fe-188">Projenin varsayılan sınıfı yeniden adlandırma `CalculatorViewToContractAddInSideAdapter`.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-188">Rename the project's default class `CalculatorViewToContractAddInSideAdapter`.</span></span>  
  
6.  <span data-ttu-id="1b0fe-189">Sınıf dosyasında için ad alanı başvurularını ekleyin <xref:System.AddIn.Pipeline>.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-189">In the class file, add namespace references to <xref:System.AddIn.Pipeline>.</span></span>  
  
7.  <span data-ttu-id="1b0fe-190">Sınıf dosyasında bitişik parçaları için ad alanı başvurularını ekleyin: `CalcAddInViews` ve `CalculatorContracts`.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-190">In the class file, add namespace references for the adjacent segments: `CalcAddInViews` and `CalculatorContracts`.</span></span> <span data-ttu-id="1b0fe-191">(Visual Basic'te, bu ad alanı başvurularını olan `Calc1AddInView.CalcAddInViews` ve `Calc1Contract.CalculatorContracts`, Visual Basic projeleri varsayılan ad alanlarını devre dışı bırakmış sürece.)</span><span class="sxs-lookup"><span data-stu-id="1b0fe-191">(In Visual Basic, these namespace references are `Calc1AddInView.CalcAddInViews` and `Calc1Contract.CalculatorContracts`, unless you have turned off the default namespaces in your Visual Basic projects.)</span></span>  
  
8.  <span data-ttu-id="1b0fe-192">Uygulama <xref:System.AddIn.Pipeline.AddInAdapterAttribute> özniteliğini `CalculatorViewToContractAddInSideAdapter` Ekle tarafı bağdaştırıcı olarak belirlemek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-192">Apply the <xref:System.AddIn.Pipeline.AddInAdapterAttribute> attribute to the `CalculatorViewToContractAddInSideAdapter` class, to identify it as the add-in-side adapter.</span></span>  
  
9. <span data-ttu-id="1b0fe-193">Olun `CalculatorViewToContractAddInSideAdapter` sınıfı <xref:System.AddIn.Pipeline.ContractBase>, bir varsayılan uygulaması sağlayan <xref:System.AddIn.Contract.IContract> arabirim ve ardışık düzeni için sözleşme arabirimini uygulayan `ICalc1Contract`.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-193">Make the `CalculatorViewToContractAddInSideAdapter` class inherit <xref:System.AddIn.Pipeline.ContractBase>, which provides a default implementation of the <xref:System.AddIn.Contract.IContract> interface, and implement the contract interface for the pipeline, `ICalc1Contract`.</span></span>  
  
10. <span data-ttu-id="1b0fe-194">Kabul ortak bir oluşturucu ekleyin bir `ICalculator`, özel bir alana önbelleğe alır ve temel sınıf oluşturucu çağırır.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-194">Add a public constructor that accepts an `ICalculator`, caches it in a private field, and calls the base class constructor.</span></span>  
  
11. <span data-ttu-id="1b0fe-195">Üyeleri uygulamak için `ICalc1Contract`, yalnızca ilgili üyeleri çağrı `ICalculator` örneğinin oluşturucuya geçirilen ve sonuçları döndürür.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-195">To implement the members of `ICalc1Contract`, simply call the corresponding members of the `ICalculator` instance that is passed to the constructor, and return the results.</span></span> <span data-ttu-id="1b0fe-196">Bu görünüm uyum (`ICalculator`) sözleşmeye (`ICalc1Contract`).</span><span class="sxs-lookup"><span data-stu-id="1b0fe-196">This adapts the view (`ICalculator`) to the contract (`ICalc1Contract`).</span></span>  
  
     <span data-ttu-id="1b0fe-197">Aşağıdaki kod tamamlanmış eklemek tarafı bağdaştırıcı gösterir.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-197">The following code shows the completed add-in-side adapter.</span></span>  
  
     [!code-csharp[AddInP1AddInSideAdapters#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInSideAdapters/cs/Calc1ViewToContractAddInSideAdapter.cs#1)]
     [!code-vb[AddInP1AddInSideAdapters#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInSideAdapters/vb/Calc1ViewToContractAddInSideAdapter.vb#1)]  
  
12. <span data-ttu-id="1b0fe-198">İsteğe bağlı olarak, Visual Studio çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-198">Optionally, build the Visual Studio solution.</span></span>  
  
## <a name="creating-the-host-side-adapter"></a><span data-ttu-id="1b0fe-199">Konak tarafındaki bağdaştırıcısı oluşturma</span><span class="sxs-lookup"><span data-stu-id="1b0fe-199">Creating the Host-side Adapter</span></span>  
 <span data-ttu-id="1b0fe-200">Bu ana bilgisayar tarafı bağdaştırıcı bir sözleşme görünümü bağdaştırıcısı oluşur.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-200">This host-side adapter consists of one contract-to-view adapter.</span></span> <span data-ttu-id="1b0fe-201">Bu kesimin eklenti konak görünümünü sözleşmesine uyum sağlar.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-201">This segment adapts the contract to the host view of the add-in.</span></span>  
  
 <span data-ttu-id="1b0fe-202">Bu ardışık düzeninde eklenti bir hizmet ana bilgisayarı ve türleri akış bileşeninden Ekle ana bilgisayara sağlar.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-202">In this pipeline, the add-in provides a service to the host and the types flow from the add-in to the host.</span></span> <span data-ttu-id="1b0fe-203">Eklenti ana bilgisayardan akışı hiçbir türünü olduğundan, bir görünüm sözleşme bağdaştırıcısı içeriyor gerekmez.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-203">Because no types flow from the host to the add-in, you do not have to include a view-to-contract adapter.</span></span>  
  
 <span data-ttu-id="1b0fe-204">Ömür Yönetimi uygulamak için kullandığınız bir <xref:System.AddIn.Pipeline.ContractHandle> sözleşmesine ömrü belirteci eklemek için nesne.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-204">To implement lifetime management, use a <xref:System.AddIn.Pipeline.ContractHandle> object to attach a lifetime token to the contract.</span></span> <span data-ttu-id="1b0fe-205">Çalışmak yaşam süresi Management sırayla bu işlemek için bir başvuru tutmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-205">You must keep a reference to this handle in order for lifetime management to work.</span></span> <span data-ttu-id="1b0fe-206">Belirteç uygulandıktan sonra ek bir programlamaya artık kullanılıyor ve atık toplama için kullanılabilmesini eklenti sistemi nesnelerin dispose çünkü gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-206">After the token is applied, no additional programming is required because the add-in system can dispose of objects when they are no longer being used and make them available for garbage collection.</span></span> <span data-ttu-id="1b0fe-207">Daha fazla bilgi için bkz: [yaşam süresi Management](http://msdn.microsoft.com/library/57a9c87e-394c-4fef-89f2-aa4223a2aeb5).</span><span class="sxs-lookup"><span data-stu-id="1b0fe-207">For more information, see [Lifetime Management](http://msdn.microsoft.com/library/57a9c87e-394c-4fef-89f2-aa4223a2aeb5).</span></span>  
  
#### <a name="to-create-the-host-side-adapter"></a><span data-ttu-id="1b0fe-208">Konak tarafındaki bağdaştırıcısı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="1b0fe-208">To create the host-side adapter</span></span>  
  
1.  <span data-ttu-id="1b0fe-209">Adlı yeni bir proje eklemek `Calc1HostSideAdapter` için `CalculatorV1` çözümü.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-209">Add a new project named `Calc1HostSideAdapter` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="1b0fe-210">İçin temel **sınıf kitaplığı** şablonu.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-210">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="1b0fe-211">İçinde **Çözüm Gezgini**, aşağıdaki derlemelerine başvurular ekleyin `Calc1HostSideAdapter` proje:</span><span class="sxs-lookup"><span data-stu-id="1b0fe-211">In **Solution Explorer**, add references to the following assemblies to the `Calc1HostSideAdapter` project:</span></span>  
  
     <span data-ttu-id="1b0fe-212">System.AddIn.dll</span><span class="sxs-lookup"><span data-stu-id="1b0fe-212">System.AddIn.dll</span></span>  
  
     <span data-ttu-id="1b0fe-213">System.AddIn.Contract.dll</span><span class="sxs-lookup"><span data-stu-id="1b0fe-213">System.AddIn.Contract.dll</span></span>  
  
3.  <span data-ttu-id="1b0fe-214">Proje başvurularını bitişik parçaları projelerine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1b0fe-214">Add project references to the projects for the adjacent segments:</span></span>  
  
     `Calc1Contract`  
  
     `Calc1HVA`  
  
4.  <span data-ttu-id="1b0fe-215">Her proje başvurusu seçin ve **özellikleri** ayarlamak **kopya yerel** için **False**.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-215">Select each project reference, and in **Properties** set **Copy Local** to **False**.</span></span> <span data-ttu-id="1b0fe-216">Visual Basic'teki **başvuruları** sekmesinde **proje özelliklerini** ayarlamak için **kopya yerel** için **False** iki proje başvuruları için.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-216">In Visual Basic, use the **References** tab of **Project Properties** to set **Copy Local** to **False** for the two project references.</span></span>  
  
5.  <span data-ttu-id="1b0fe-217">Projenin varsayılan sınıfı yeniden adlandırma `CalculatorContractToViewHostSideAdapter`.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-217">Rename the project's default class `CalculatorContractToViewHostSideAdapter`.</span></span>  
  
6.  <span data-ttu-id="1b0fe-218">Sınıf dosyasında için ad alanı başvurularını ekleyin <xref:System.AddIn.Pipeline>.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-218">In the class file, add namespace references to <xref:System.AddIn.Pipeline>.</span></span>  
  
7.  <span data-ttu-id="1b0fe-219">Sınıf dosyasında bitişik parçaları için ad alanı başvurularını ekleyin: `CalcHVAs` ve `CalculatorContracts`.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-219">In the class file, add namespace references for the adjacent segments: `CalcHVAs` and `CalculatorContracts`.</span></span> <span data-ttu-id="1b0fe-220">(Visual Basic'te, bu ad alanı başvurularını olan `Calc1HVA.CalcHVAs` ve `Calc1Contract.CalculatorContracts`, Visual Basic projeleri varsayılan ad alanlarını devre dışı bırakmış sürece.)</span><span class="sxs-lookup"><span data-stu-id="1b0fe-220">(In Visual Basic, these namespace references are `Calc1HVA.CalcHVAs` and `Calc1Contract.CalculatorContracts`, unless you have turned off the default namespaces in your Visual Basic projects.)</span></span>  
  
8.  <span data-ttu-id="1b0fe-221">Uygulama <xref:System.AddIn.Pipeline.HostAdapterAttribute> özniteliğini `CalculatorContractToViewHostSideAdapter` konak tarafı bağdaştırıcısı kesim olarak belirlemek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-221">Apply the <xref:System.AddIn.Pipeline.HostAdapterAttribute> attribute to the `CalculatorContractToViewHostSideAdapter` class, to identify it as the host-side adapter segment.</span></span>  
  
9. <span data-ttu-id="1b0fe-222">Olun `CalculatorContractToViewHostSideAdapter` sınıf eklenti konak görünümünü temsil eden arabirim uygulama: `Calc1HVAs.ICalculator` (`Calc1HVA.CalcHVAs.ICalculator` Visual Basic'te).</span><span class="sxs-lookup"><span data-stu-id="1b0fe-222">Make the `CalculatorContractToViewHostSideAdapter` class implement the interface that represents the host view of the add-in: `Calc1HVAs.ICalculator` (`Calc1HVA.CalcHVAs.ICalculator` in Visual Basic).</span></span>  
  
10. <span data-ttu-id="1b0fe-223">Ardışık Düzen sözleşme türü kabul eden bir ortak oluşturucu ekleyin `ICalc1Contract`.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-223">Add a public constructor that accepts the pipeline contract type, `ICalc1Contract`.</span></span> <span data-ttu-id="1b0fe-224">Oluşturucusu sözleşme referansı önbelleğe gerekir.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-224">The constructor must cache the reference to the contract.</span></span> <span data-ttu-id="1b0fe-225">Bu ayrıca oluşturabilir ve yeni bir önbellek <xref:System.AddIn.Pipeline.ContractHandle> ömrünü yönetmek için sözleşmesi için.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-225">It must also create and cache a new <xref:System.AddIn.Pipeline.ContractHandle> for the contract, to manage the lifetime of the add-in.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="1b0fe-226"><xref:System.AddIn.Pipeline.ContractHandle> Ömür yönetimi için kritik öneme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-226">The <xref:System.AddIn.Pipeline.ContractHandle> is critical to lifetime management.</span></span> <span data-ttu-id="1b0fe-227">Bir başvuru tutmak başarısız olursa <xref:System.AddIn.Pipeline.ContractHandle> nesne, atık toplama, geri ve ardışık düzen programınızı beklemiyor zaman kapanacak.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-227">If you fail to keep a reference to the <xref:System.AddIn.Pipeline.ContractHandle> object, garbage collection will reclaim it, and the pipeline will shut down when your program does not expect it.</span></span> <span data-ttu-id="1b0fe-228">Bu tanılama, gibi zor olan hatalara yol açabilir <xref:System.AppDomainUnloadedException>.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-228">This can lead to errors that are difficult to diagnose, such as <xref:System.AppDomainUnloadedException>.</span></span> <span data-ttu-id="1b0fe-229">Bu yüzden bu durum bir hata olduğunu tespit etmek üzere yaşam süresi management kod yolu kapatma bir ardışık düzen yaşamında normal bir aşamadır.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-229">Shutdown is a normal stage in the life of a pipeline, so there is no way for the lifetime management code to detect that this condition is an error.</span></span>  
  
11. <span data-ttu-id="1b0fe-230">Üyeleri uygulamak için `ICalculator`, yalnızca ilgili üyeleri çağrı `ICalc1Contract` örneğinin oluşturucuya geçirilen ve sonuçları döndürür.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-230">To implement the members of `ICalculator`, simply call the corresponding members of the `ICalc1Contract` instance that is passed to the constructor, and return the results.</span></span> <span data-ttu-id="1b0fe-231">Bu sözleşme uyum (`ICalc1Contract`) görüntülemek için (`ICalculator`).</span><span class="sxs-lookup"><span data-stu-id="1b0fe-231">This adapts the contract (`ICalc1Contract`) to the view (`ICalculator`).</span></span>  
  
     <span data-ttu-id="1b0fe-232">Aşağıdaki kod tamamlanmış konak tarafı bağdaştırıcısı gösterir.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-232">The following code shows the completed host-side adapter.</span></span>  
  
     [!code-csharp[AddInP1HostSideAdapters#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1HostSideAdapters/cs/Calc1ContractToViewHostSideAdapter.cs#1)]
     [!code-vb[AddInP1HostSideAdapters#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1HostSideAdapters/vb/Calc1ContractToViewHostSideAdapter.vb#1)]  
  
12. <span data-ttu-id="1b0fe-233">İsteğe bağlı olarak, Visual Studio çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-233">Optionally, build the Visual Studio solution.</span></span>  
  
## <a name="creating-the-host"></a><span data-ttu-id="1b0fe-234">Konak oluşturma</span><span class="sxs-lookup"><span data-stu-id="1b0fe-234">Creating the Host</span></span>  
 <span data-ttu-id="1b0fe-235">Bir ana bilgisayar uygulaması eklentisi eklenti konak görünümünü üzerinden ile etkileşim kurar.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-235">A host application interacts with the add-in through the host view of the add-in.</span></span> <span data-ttu-id="1b0fe-236">Tarafından sağlanan eklenti bulma ve etkinleştirme yöntemlerini kullanan <xref:System.AddIn.Hosting.AddInStore> ve <xref:System.AddIn.Hosting.AddInToken> sınıfları aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="1b0fe-236">It uses add-in discovery and activation methods provided by the <xref:System.AddIn.Hosting.AddInStore> and <xref:System.AddIn.Hosting.AddInToken> classes to do the following:</span></span>  
  
-   <span data-ttu-id="1b0fe-237">Ardışık Düzen ve eklenti bilgilerini önbelleğini güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-237">Update the cache of pipeline and add-in information.</span></span>  
  
-   <span data-ttu-id="1b0fe-238">Eklentiler ana görünüm türü bulmak `ICalculator`, belirtilen ardışık düzen kök dizininin altında.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-238">Find add-ins of the host view type, `ICalculator`, under the specified pipeline root directory.</span></span>  
  
-   <span data-ttu-id="1b0fe-239">Hangi kullanmak için eklenti belirtmek için kullanıcıya sor.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-239">Prompt the user to specify which add-in to use.</span></span>  
  
-   <span data-ttu-id="1b0fe-240">Seçili eklenti belirtilen güvenlik güven düzeyine sahip yeni bir uygulama etki alanında etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-240">Activate the selected add-in in a new application domain with a specified security trust level.</span></span>  
  
-   <span data-ttu-id="1b0fe-241">Özel çalıştırmak `RunCalculator` eklentinin eklenti konak görünümünü tarafından belirtilen yöntemlerini çağıran yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-241">Run the custom `RunCalculator` method, which calls the add-in's methods as specified by the host view of the add-in.</span></span>  
  
#### <a name="to-create-the-host"></a><span data-ttu-id="1b0fe-242">Ana bilgisayar oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="1b0fe-242">To create the host</span></span>  
  
1.  <span data-ttu-id="1b0fe-243">Adlı yeni bir proje eklemek `Calc1Host` için `CalculatorV1` çözümü.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-243">Add a new project named `Calc1Host` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="1b0fe-244">İçin temel **konsol uygulaması** şablonu.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-244">Base it on the **Console Application** template.</span></span>  
  
2.  <span data-ttu-id="1b0fe-245">İçinde **Çözüm Gezgini**, System.AddIn.dll derlemesine başvuru ekleyin `Calc1Host` projesi.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-245">In **Solution Explorer**, add a reference to the System.AddIn.dll assembly to the `Calc1Host` project.</span></span>  
  
3.  <span data-ttu-id="1b0fe-246">Proje için bir başvuru ekleyin `Calc1HVA` projesi.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-246">Add a project reference to the `Calc1HVA` project.</span></span> <span data-ttu-id="1b0fe-247">Proje başvurusu seçin ve **özellikleri** ayarlamak **kopya yerel** için **False**.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-247">Select the project reference, and in **Properties** set **Copy Local** to **False**.</span></span> <span data-ttu-id="1b0fe-248">Visual Basic'teki **başvuruları** sekmesinde **proje özelliklerini** ayarlamak için **kopya yerel** için **False**.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-248">In Visual Basic, use the **References** tab of **Project Properties** to set **Copy Local** to **False**.</span></span>  
  
4.  <span data-ttu-id="1b0fe-249">Sınıf dosyası (Visual Basic modülünde) yeniden adlandırma `MathHost1`.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-249">Rename the class file (module in Visual Basic) `MathHost1`.</span></span>  
  
5.  <span data-ttu-id="1b0fe-250">Visual Basic'teki **uygulama** sekmesinde **proje özelliklerini** ayarlamak için iletişim kutusunu **Başlangıç nesnesi** için **Sub Main**.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-250">In Visual Basic, use the **Application** tab of the **Project Properties** dialog box to set **Startup object** to **Sub Main**.</span></span>  
  
6.  <span data-ttu-id="1b0fe-251">Sınıf veya Modülü dosyasında ad alanı için bir başvuru ekleyin <xref:System.AddIn.Hosting>.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-251">In the class or module file, add a namespace reference to <xref:System.AddIn.Hosting>.</span></span>  
  
7.  <span data-ttu-id="1b0fe-252">Sınıf veya Modülü dosyasında eklenti konak görünümünü ad alanı başvurusunu ekleyin: `CalcHVAs`.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-252">In the class or module file, add a namespace reference for the host view of the add-in: `CalcHVAs`.</span></span> <span data-ttu-id="1b0fe-253">(Visual Basic'te, bu ad alanı başvurudur `Calc1HVA.CalcHVAs`, Visual Basic projeleri varsayılan ad alanlarını devre dışı bırakmış sürece.)</span><span class="sxs-lookup"><span data-stu-id="1b0fe-253">(In Visual Basic, this namespace reference is `Calc1HVA.CalcHVAs`, unless you have turned off the default namespaces in your Visual Basic projects.)</span></span>  
  
8.  <span data-ttu-id="1b0fe-254">İçinde **Çözüm Gezgini**, çözümü seçin ve **proje** menüsünü seçin **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-254">In **Solution Explorer**, select the solution and from the **Project** menu choose **Properties**.</span></span> <span data-ttu-id="1b0fe-255">İçinde **çözüm özellik sayfaları** iletişim kutusu, kümesi **tek başlangıç projesi** bu ana bilgisayar uygulaması projesi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-255">In the **Solution Property Pages** dialog box, set the **Single Startup Project** to be this host application project.</span></span>  
  
9. <span data-ttu-id="1b0fe-256">Sınıf veya Modülü dosyasında kullanmak <xref:System.AddIn.Hosting.AddInStore.Update%2A?displayProperty=nameWithType> önbelleğini güncelleştirmeye yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-256">In the class or module file, use the <xref:System.AddIn.Hosting.AddInStore.Update%2A?displayProperty=nameWithType> method to update the cache.</span></span> <span data-ttu-id="1b0fe-257">Kullanmak <xref:System.AddIn.Hosting.AddInStore.FindAddIn%2A?displayProperty=nameWithType> belirteçleri koleksiyonunu alma ve kullanmak için yöntem <xref:System.AddIn.Hosting.AddInToken.Activate%2A?displayProperty=nameWithType> bir eklentiyi etkinleştirmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-257">Use the <xref:System.AddIn.Hosting.AddInStore.FindAddIn%2A?displayProperty=nameWithType> method to get a collection of tokens, and use the <xref:System.AddIn.Hosting.AddInToken.Activate%2A?displayProperty=nameWithType> method to activate an add-in.</span></span>  
  
     <span data-ttu-id="1b0fe-258">Aşağıdaki kod tamamlanmış ana bilgisayar uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-258">The following code shows the completed host application.</span></span>  
  
     [!code-csharp[AddInP1Host#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1Host/cs/MathHost1.cs#1)]
     [!code-vb[AddInP1Host#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1Host/vb/MathHost1.vb#1)]  
  
    > [!NOTE]
    >  <span data-ttu-id="1b0fe-259">Bu kod, ardışık düzen klasör yapısı uygulama klasöründe bulunduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-259">This code assumes that the pipeline folder structure is located in the application folder.</span></span> <span data-ttu-id="1b0fe-260">Başka bir yerde bulunan ayarlar kod satırı tıklarsanız `addInRoot` değişken, böylece değişkeni ardışık düzen directory yapınızı yolunu içerir.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-260">If you located it elsewhere, change the line of code that sets the `addInRoot` variable, so that the variable contains the path to your pipeline directory structure.</span></span>  
  
     <span data-ttu-id="1b0fe-261">Kod kullanan bir `ChooseCalculator` yöntemi belirteçleri listelemek için ve kullanıcıdan bir eklenti seçin.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-261">The code uses a `ChooseCalculator` method to list the tokens and to prompt the user to choose an add-in.</span></span> <span data-ttu-id="1b0fe-262">`RunCalculator` Yöntemi basit aritmetik ifadeler için kullanıcıdan, kullanarak ifadeler ayrıştırır `Parser` sınıfı ve sonuçları döndürdü eklenti tarafından görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-262">The `RunCalculator` method prompts the user for simple math expressions, parses the expressions using the `Parser` class, and displays the results returned by the add-in.</span></span>  
  
10. <span data-ttu-id="1b0fe-263">İsteğe bağlı olarak, Visual Studio çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-263">Optionally, build the Visual Studio solution.</span></span>  
  
## <a name="creating-the-add-in"></a><span data-ttu-id="1b0fe-264">Eklentiyi oluşturma</span><span class="sxs-lookup"><span data-stu-id="1b0fe-264">Creating the Add-In</span></span>  
 <span data-ttu-id="1b0fe-265">Bir eklenti eklenti görünümü tarafından belirtilen yöntemlerini uygular.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-265">An add-in implements the methods specified by the add-in view.</span></span> <span data-ttu-id="1b0fe-266">Bu eklenti uygulayan `Add`, `Subtract`, `Multiply`, ve `Divide` işlemler ve ana bilgisayar için sonuçları döndürür.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-266">This add-in implements the `Add`, `Subtract`, `Multiply`, and `Divide` operations and returns the results to the host.</span></span>  
  
#### <a name="to-create-the-add-in"></a><span data-ttu-id="1b0fe-267">Eklenti oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="1b0fe-267">To create the add-in</span></span>  
  
1.  <span data-ttu-id="1b0fe-268">Adlı yeni bir proje eklemek `AddInCalcV1` için `CalculatorV1` çözümü.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-268">Add a new project named `AddInCalcV1` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="1b0fe-269">İçin temel **sınıf kitaplığı** şablonu.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-269">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="1b0fe-270">İçinde **Çözüm Gezgini**, projeye System.AddIn.dll derlemesine başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-270">In **Solution Explorer**, add a reference to the System.AddIn.dll assembly to the project.</span></span>  
  
3.  <span data-ttu-id="1b0fe-271">Proje için bir başvuru ekleyin `Calc1AddInView` projesi.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-271">Add a project reference to the `Calc1AddInView` project.</span></span> <span data-ttu-id="1b0fe-272">Proje başvurusu seçin ve **özellikleri**ayarlayın **kopya yerel** için **False**.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-272">Select the project reference, and in **Properties**, set **Copy Local** to **False**.</span></span> <span data-ttu-id="1b0fe-273">Visual Basic'teki **başvuruları** sekmesinde **proje özelliklerini** ayarlamak için **kopya yerel** için **False** proje başvurusu için.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-273">In Visual Basic, use the **References** tab of **Project Properties** to set **Copy Local** to **False** for the project reference.</span></span>  
  
4.  <span data-ttu-id="1b0fe-274">Sınıfı yeniden adlandırma `AddInCalcV1`.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-274">Rename the class `AddInCalcV1`.</span></span>  
  
5.  <span data-ttu-id="1b0fe-275">Sınıf dosyasında, ad alanı için bir başvuru ekleyin <xref:System.AddIn> ve eklenti görünümü kesimi: `CalcAddInViews` (`Calc1AddInView.CalcAddInViews` Visual Basic'te).</span><span class="sxs-lookup"><span data-stu-id="1b0fe-275">In the class file, add a namespace reference to <xref:System.AddIn> and the add-in view segment: `CalcAddInViews` (`Calc1AddInView.CalcAddInViews` in Visual Basic).</span></span>  
  
6.  <span data-ttu-id="1b0fe-276">Uygulama <xref:System.AddIn.AddInAttribute> özniteliğini `AddInCalcV1` sınıfı bir eklenti olarak belirlemek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-276">Apply the <xref:System.AddIn.AddInAttribute> attribute to the `AddInCalcV1` class, to identify the class as an add-in.</span></span>  
  
7.  <span data-ttu-id="1b0fe-277">Olun `AddInCalcV1` sınıf eklenti görünümü temsil eden arabirim uygulama: `CalcAddInViews.ICalculator` (`Calc1AddInView.CalcAddInViews.ICalculator` Visual Basic'te).</span><span class="sxs-lookup"><span data-stu-id="1b0fe-277">Make the `AddInCalcV1` class implement the interface that represents the add-in view: `CalcAddInViews.ICalculator` (`Calc1AddInView.CalcAddInViews.ICalculator` in Visual Basic).</span></span>  
  
8.  <span data-ttu-id="1b0fe-278">Üyelerini uygulama `ICalculator` uygun hesaplamaların sonuçlarını döndürerek.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-278">Implement the members of `ICalculator` by returning the results of the appropriate calculations.</span></span>  
  
     <span data-ttu-id="1b0fe-279">Tamamlanan eklentisi aşağıdaki kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-279">The following code shows the completed add-in.</span></span>  
  
     [!code-csharp[AddInP1AddInCalcV1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInCalcV1/cs/AddInCalcV1.cs#1)]
     [!code-vb[AddInP1AddInCalcV1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInCalcV1/vb/AddInCalcV1.vb#1)]  
  
9. <span data-ttu-id="1b0fe-280">İsteğe bağlı olarak, Visual Studio çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-280">Optionally, build the Visual Studio solution.</span></span>  
  
## <a name="deploying-the-pipeline"></a><span data-ttu-id="1b0fe-281">Ardışık Düzen dağıtma</span><span class="sxs-lookup"><span data-stu-id="1b0fe-281">Deploying the Pipeline</span></span>  
 <span data-ttu-id="1b0fe-282">Şimdi oluşturmak ve eklenti parçaları için gerekli ardışık düzen dizin yapısını dağıtmak hazır olursunuz.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-282">You are now ready to build and deploy the add-in segments to the required pipeline directory structure.</span></span>  
  
#### <a name="to-deploy-the-segments-to-the-pipeline"></a><span data-ttu-id="1b0fe-283">Ardışık düzene kesimleri dağıtmak için</span><span class="sxs-lookup"><span data-stu-id="1b0fe-283">To deploy the segments to the pipeline</span></span>  
  
1.  <span data-ttu-id="1b0fe-284">Çözümdeki her proje için kullanmak **yapı** sekmesinde **proje özelliklerini** ( **derleme** sekmesini Visual Basic'te) değerini ayarlamak için **çıkış yolu**  ( **yapı çıkış yolu** Visual Basic'te).</span><span class="sxs-lookup"><span data-stu-id="1b0fe-284">For each project in the solution, use the **Build** tab of **Project Properties** (the **Compile** tab in Visual Basic) to set the value of the **Output path** (the **Build output path** in Visual Basic).</span></span> <span data-ttu-id="1b0fe-285">Uygulama klasörünüzde adlandırırsanız `MyApp`, örneğin, projelerinizi aşağıdaki klasörler halinde oluşturmayı tercih:</span><span class="sxs-lookup"><span data-stu-id="1b0fe-285">If you named your application folder `MyApp`, for example, your projects would build into the following folders:</span></span>  
  
    |<span data-ttu-id="1b0fe-286">Proje</span><span class="sxs-lookup"><span data-stu-id="1b0fe-286">Project</span></span>|<span data-ttu-id="1b0fe-287">Yol</span><span class="sxs-lookup"><span data-stu-id="1b0fe-287">Path</span></span>|  
    |-------------|----------|  
    |<span data-ttu-id="1b0fe-288">AddInCalcV1</span><span class="sxs-lookup"><span data-stu-id="1b0fe-288">AddInCalcV1</span></span>|<span data-ttu-id="1b0fe-289">MyApp\Pipeline\AddIns\CalcV1</span><span class="sxs-lookup"><span data-stu-id="1b0fe-289">MyApp\Pipeline\AddIns\CalcV1</span></span>|  
    |<span data-ttu-id="1b0fe-290">Calc1AddInSideAdapter</span><span class="sxs-lookup"><span data-stu-id="1b0fe-290">Calc1AddInSideAdapter</span></span>|<span data-ttu-id="1b0fe-291">MyApp\Pipeline\AddInSideAdapters</span><span class="sxs-lookup"><span data-stu-id="1b0fe-291">MyApp\Pipeline\AddInSideAdapters</span></span>|  
    |<span data-ttu-id="1b0fe-292">Calc1AddInView</span><span class="sxs-lookup"><span data-stu-id="1b0fe-292">Calc1AddInView</span></span>|<span data-ttu-id="1b0fe-293">MyApp\Pipeline\AddInViews</span><span class="sxs-lookup"><span data-stu-id="1b0fe-293">MyApp\Pipeline\AddInViews</span></span>|  
    |<span data-ttu-id="1b0fe-294">Calc1Contract</span><span class="sxs-lookup"><span data-stu-id="1b0fe-294">Calc1Contract</span></span>|<span data-ttu-id="1b0fe-295">MyApp\Pipeline\Contracts</span><span class="sxs-lookup"><span data-stu-id="1b0fe-295">MyApp\Pipeline\Contracts</span></span>|  
    |<span data-ttu-id="1b0fe-296">Calc1Host</span><span class="sxs-lookup"><span data-stu-id="1b0fe-296">Calc1Host</span></span>|<span data-ttu-id="1b0fe-297">Uygulamam</span><span class="sxs-lookup"><span data-stu-id="1b0fe-297">MyApp</span></span>|  
    |<span data-ttu-id="1b0fe-298">Calc1HostSideAdapter</span><span class="sxs-lookup"><span data-stu-id="1b0fe-298">Calc1HostSideAdapter</span></span>|<span data-ttu-id="1b0fe-299">MyApp\Pipeline\HostSideAdapters</span><span class="sxs-lookup"><span data-stu-id="1b0fe-299">MyApp\Pipeline\HostSideAdapters</span></span>|  
    |<span data-ttu-id="1b0fe-300">Calc1HVA</span><span class="sxs-lookup"><span data-stu-id="1b0fe-300">Calc1HVA</span></span>|<span data-ttu-id="1b0fe-301">Uygulamam</span><span class="sxs-lookup"><span data-stu-id="1b0fe-301">MyApp</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="1b0fe-302">Uygulama klasörü dışında bir konumda ardışık düzen klasör yapısı almaya karar verdiyseniz, buna göre tabloda gösterilen yolları değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-302">If you decided to put your pipeline folder structure in a location other than your application folder, you must modify the paths shown in the table accordingly.</span></span> <span data-ttu-id="1b0fe-303">Ardışık Düzen directory gereksinimleri hakkında bilgi bkz [ardışık düzen geliştirme gereksinimleri](http://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span><span class="sxs-lookup"><span data-stu-id="1b0fe-303">See the discussion of pipeline directory requirements in [Pipeline Development Requirements](http://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span></span>  
  
2.  <span data-ttu-id="1b0fe-304">Visual Studio çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-304">Build the Visual Studio solution.</span></span>  
  
3.  <span data-ttu-id="1b0fe-305">Derlemeler için doğru dizinleri kopyalanan ve derlemeler hiçbir ek kopyalarını yanlış klasörlerde yüklenen emin olmak için uygulama ve ardışık düzen dizinleri denetleyin.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-305">Check the application and pipeline directories to ensure that the assemblies were copied to the correct directories and that no extra copies of assemblies were installed in the wrong folders.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1b0fe-306">Değil değiştirirseniz **kopya yerel** için **False** için `Calc1AddInView` proje başvurusu'nda `AddInCalcV1` projesi, yükleyici bağlamı sorunları engeller eklenti bulunan gelen.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-306">If you did not change **Copy Local** to **False** for the `Calc1AddInView` project reference in the `AddInCalcV1` project, loader context problems will prevent the add-in from being located.</span></span>  
  
     <span data-ttu-id="1b0fe-307">Ardışık düzene dağıtma hakkında daha fazla bilgi için bkz: [ardışık düzen geliştirme gereksinimleri](http://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span><span class="sxs-lookup"><span data-stu-id="1b0fe-307">For information about deploying to the pipeline, see [Pipeline Development Requirements](http://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span></span>  
  
## <a name="running-the-host-application"></a><span data-ttu-id="1b0fe-308">Ana bilgisayar uygulamasını çalıştırma</span><span class="sxs-lookup"><span data-stu-id="1b0fe-308">Running the Host Application</span></span>  
 <span data-ttu-id="1b0fe-309">Şimdi konak çalıştırın ve eklentisi ile etkileşim kurmak hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-309">You are now ready to run the host and interact with the add-in.</span></span>  
  
#### <a name="to-run-the-host-application"></a><span data-ttu-id="1b0fe-310">Ana bilgisayar uygulamasını çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="1b0fe-310">To run the host application</span></span>  
  
1.  <span data-ttu-id="1b0fe-311">Komut isteminde uygulama dizinine gidin ve ana bilgisayar uygulamasını çalıştırmak `Calc1Host.exe`.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-311">At the command prompt, go to the application directory and run the host application, `Calc1Host.exe`.</span></span>  
  
2.  <span data-ttu-id="1b0fe-312">Ana bilgisayar tüm kullanılabilir eklentiler türüne bulur ve bir eklenti seçmenizi ister.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-312">The host finds all available add-ins of its type and prompts you to select an add-in.</span></span> <span data-ttu-id="1b0fe-313">Girin **1** için yalnızca eklentisi.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-313">Enter **1** for the only available add-in.</span></span>  
  
3.  <span data-ttu-id="1b0fe-314">Bir eşitlik için hesaplayıcı, gibi girin **2 + 2**.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-314">Enter an equation for the calculator, such as **2 + 2**.</span></span> <span data-ttu-id="1b0fe-315">Alanları numaraları işleci arasında olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-315">There must be spaces between the numbers and the operator.</span></span>  
  
4.  <span data-ttu-id="1b0fe-316">Tür **çıkmak** ve basın **Enter** uygulamayı kapatmak için anahtar.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-316">Type **exit** and press the **Enter** key to close the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b0fe-317">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1b0fe-317">See Also</span></span>  
 [<span data-ttu-id="1b0fe-318">İzlenecek yol: Ana bilgisayar değişikliklerinizi olarak geriye dönük uyumluluk etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="1b0fe-318">Walkthrough: Enabling Backward Compatibility as Your Host Changes</span></span>](http://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848)  
 [<span data-ttu-id="1b0fe-319">İzlenecek yol: Geçirme koleksiyonları arasında konakları ve eklentiler</span><span class="sxs-lookup"><span data-stu-id="1b0fe-319">Walkthrough: Passing Collections Between Hosts and Add-Ins</span></span>](http://msdn.microsoft.com/library/b532c604-548e-4fab-b11c-377257dd0ee5)  
 [<span data-ttu-id="1b0fe-320">Ardışık Düzen geliştirme gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="1b0fe-320">Pipeline Development Requirements</span></span>](http://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5)  
 [<span data-ttu-id="1b0fe-321">Sözleşmeler, görünümler ve bağdaştırıcıları</span><span class="sxs-lookup"><span data-stu-id="1b0fe-321">Contracts, Views, and Adapters</span></span>](http://msdn.microsoft.com/library/a6460173-9507-4b87-8c07-d4ee245d715c)  
 [<span data-ttu-id="1b0fe-322">İşlem Hattı Geliştirme</span><span class="sxs-lookup"><span data-stu-id="1b0fe-322">Pipeline Development</span></span>](../../../docs/framework/add-ins/pipeline-development.md)
