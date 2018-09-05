---
title: 'İzlenecek Yol: Genişletilebilir Uygulama Oluşturma'
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5d2aaeaffaf3abbe1e8efcdb57d40e6ae60f89b5
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43552341"
---
# <a name="walkthrough-creating-an-extensible-application"></a><span data-ttu-id="87283-102">İzlenecek Yol: Genişletilebilir Uygulama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="87283-102">Walkthrough: Creating an Extensible Application</span></span>
<span data-ttu-id="87283-103">Bu izlenecek yol basit hesap makinesi işlevlerini gerçekleştiren bir eklenti için bir işlem hattı oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="87283-103">This walkthrough describes how to create a pipeline for an add-in that performs simple calculator functions.</span></span> <span data-ttu-id="87283-104">Gerçek dünya senaryoları göstermemiz gerekmez; Bunun yerine, bir işlem hattı ve nasıl bir eklenti için bir ana bilgisayar hizmetleri sağlayabilir temel işlevlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="87283-104">It does not demonstrate a real-world scenario; rather, it demonstrates the basic functionality of a pipeline and how an add-in can provide services for a host.</span></span>  
  
 <span data-ttu-id="87283-105">Bu izlenecek yol aşağıdaki görevleri açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="87283-105">This walkthrough describes the following tasks:</span></span>  
  
-   <span data-ttu-id="87283-106">Visual Studio çözümü oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="87283-106">Creating a Visual Studio solution.</span></span>  
  
-   <span data-ttu-id="87283-107">İşlem hattı dizin yapısı oluşturma.</span><span class="sxs-lookup"><span data-stu-id="87283-107">Creating the pipeline directory structure.</span></span>  
  
-   <span data-ttu-id="87283-108">Sözleşme ve görünümler oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="87283-108">Creating the contract and views.</span></span>  
  
-   <span data-ttu-id="87283-109">Ekle tarafı bağdaştırıcısı oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="87283-109">Creating the add-in-side adapter.</span></span>  
  
-   <span data-ttu-id="87283-110">Konak tarafı bağdaştırıcısı oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="87283-110">Creating the host-side adapter.</span></span>  
  
-   <span data-ttu-id="87283-111">Ana bilgisayarı oluşturma.</span><span class="sxs-lookup"><span data-stu-id="87283-111">Creating the host.</span></span>  
  
-   <span data-ttu-id="87283-112">Eklenti oluşturma.</span><span class="sxs-lookup"><span data-stu-id="87283-112">Creating the add-in.</span></span>  
  
-   <span data-ttu-id="87283-113">İşlem hattı dağıtılıyor.</span><span class="sxs-lookup"><span data-stu-id="87283-113">Deploying the pipeline.</span></span>  
  
-   <span data-ttu-id="87283-114">Ana bilgisayar uygulaması çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="87283-114">Running the host application.</span></span>  
  
 <span data-ttu-id="87283-115">Bu işlem hattı yalnızca serializable türler geçirir (<xref:System.Double> ve <xref:System.String>), konak ile eklenti arasındaki.</span><span class="sxs-lookup"><span data-stu-id="87283-115">This pipeline passes only serializable types (<xref:System.Double> and <xref:System.String>), between the host and the add-in.</span></span> <span data-ttu-id="87283-116">Karmaşık veri türlerini koleksiyonlarının nasıl gösteren bir örnek için bkz: [izlenecek yol: koleksiyonları konaklar arasında geçirme ve eklentileri](https://msdn.microsoft.com/library/b532c604-548e-4fab-b11c-377257dd0ee5).</span><span class="sxs-lookup"><span data-stu-id="87283-116">For an example that shows how to pass collections of complex data types, see [Walkthrough: Passing Collections Between Hosts and Add-Ins](https://msdn.microsoft.com/library/b532c604-548e-4fab-b11c-377257dd0ee5).</span></span>  
  
 <span data-ttu-id="87283-117">Bu işlem hattı için anlaşma dört aritmetik işlemler bir nesne modelini tanımlar: ekleme, çıkarma, çarpma ve bölme.</span><span class="sxs-lookup"><span data-stu-id="87283-117">The contract for this pipeline defines an object model of four arithmetic operations: add, subtract, multiply, and divide.</span></span> <span data-ttu-id="87283-118">Ana bilgisayar 2 + 2 gibi hesaplanacak Denklem eklenti sağlar ve eklenti konağa sonuç döndürür.</span><span class="sxs-lookup"><span data-stu-id="87283-118">The host provides the add-in with an equation to calculate, such as 2 + 2, and the add-in returns the result to the host.</span></span>  
  
 <span data-ttu-id="87283-119">Sürüm 2 hesaplayıcı eklentisinin daha hesaplama olanaklar sağlar ve sürüm oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="87283-119">Version 2 of the calculator add-in provides more calculating possibilities and demonstrates versioning.</span></span> <span data-ttu-id="87283-120">İçinde açıklanan [izlenecek yol: ana bilgisayar değişikliklerinizi olarak geriye dönük uyumluluk etkinleştirme](https://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848).</span><span class="sxs-lookup"><span data-stu-id="87283-120">It is described in [Walkthrough: Enabling Backward Compatibility as Your Host Changes](https://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="87283-121">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="87283-121">Prerequisites</span></span>  
 <span data-ttu-id="87283-122">Bu izlenecek yolu tamamlamak için aşağıdakiler gerekir:</span><span class="sxs-lookup"><span data-stu-id="87283-122">You need the following to complete this walkthrough:</span></span>  
  
-   <span data-ttu-id="87283-123">Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="87283-123">Visual Studio.</span></span>  
  
## <a name="creating-a-visual-studio-solution"></a><span data-ttu-id="87283-124">Visual Studio çözümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="87283-124">Creating a Visual Studio Solution</span></span>  
 <span data-ttu-id="87283-125">Bir çözümü Visual Studio'da projeler, ardışık düzeni segmentlerini içerecek şekilde kullanın.</span><span class="sxs-lookup"><span data-stu-id="87283-125">Use a solution in Visual Studio to contain the projects of your pipeline segments.</span></span>  
  
#### <a name="to-create-the-pipeline-solution"></a><span data-ttu-id="87283-126">İşlem hattı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="87283-126">To create the pipeline solution</span></span>  
  
1.  <span data-ttu-id="87283-127">Visual Studio'da adlı yeni bir proje oluşturun `Calc1Contract`.</span><span class="sxs-lookup"><span data-stu-id="87283-127">In Visual Studio, create a new project named `Calc1Contract`.</span></span> <span data-ttu-id="87283-128">Bu temel **sınıf kitaplığı** şablonu.</span><span class="sxs-lookup"><span data-stu-id="87283-128">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="87283-129">Çözüm adı `CalculatorV1`.</span><span class="sxs-lookup"><span data-stu-id="87283-129">Name the solution `CalculatorV1`.</span></span>  
  
## <a name="creating-the-pipeline-directory-structure"></a><span data-ttu-id="87283-130">İşlem hattı dizin yapısı oluşturma</span><span class="sxs-lookup"><span data-stu-id="87283-130">Creating the Pipeline Directory Structure</span></span>  
 <span data-ttu-id="87283-131">Eklenti modeli, işlem hattı segment derlemeleri belirtilen dizin yapısında yerleştirilmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="87283-131">The add-in model requires the pipeline segment assemblies to be placed in a specified directory structure.</span></span> <span data-ttu-id="87283-132">İşlem hattı yapısı hakkında daha fazla bilgi için bkz. [ardışık düzen geliştirme gereksinimleri](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span><span class="sxs-lookup"><span data-stu-id="87283-132">For more information about the pipeline structure, see [Pipeline Development Requirements](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span></span>  
  
#### <a name="to-create-the-pipeline-directory-structure"></a><span data-ttu-id="87283-133">İşlem hattı dizin yapısı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="87283-133">To create the pipeline directory structure</span></span>  
  
1.  <span data-ttu-id="87283-134">Bir uygulama klasörü herhangi bir yere bilgisayarınızda oluşturun.</span><span class="sxs-lookup"><span data-stu-id="87283-134">Create an application folder anywhere on your computer.</span></span>  
  
2.  <span data-ttu-id="87283-135">Bu klasörde aşağıdaki yapısını oluşturun:</span><span class="sxs-lookup"><span data-stu-id="87283-135">In that folder, create the following structure:</span></span>  
  
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
  
     <span data-ttu-id="87283-136">İşlem hattı klasör yapısını uygulama klasörünüzde koymak gerekli değildir; Ayrıca, yalnızca kolaylık sağlamak için burada yapılır.</span><span class="sxs-lookup"><span data-stu-id="87283-136">It is not necessary to put the pipeline folder structure in your application folder; it is done here only for convenience.</span></span> <span data-ttu-id="87283-137">Uygun adımda, işlem hattı klasör yapısının farklı bir konumda ise, kod değiştirme gözden geçirme açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="87283-137">At the appropriate step, the walkthrough explains how to change the code if the pipeline folder structure is in a different location.</span></span> <span data-ttu-id="87283-138">İşlem hattı dizin gereksinimleri bkz [ardışık düzen geliştirme gereksinimleri](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span><span class="sxs-lookup"><span data-stu-id="87283-138">See the discussion of pipeline directory requirements in [Pipeline Development Requirements](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="87283-139">`CalcV2` Klasör, bu izlenecek yolda kullanılamıyor; bunun için bir yer tutucu [izlenecek yol: ana bilgisayar değişikliklerinizi olarak geriye dönük uyumluluk etkinleştirme](https://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848).</span><span class="sxs-lookup"><span data-stu-id="87283-139">The `CalcV2` folder is not used in this walkthrough; it is a placeholder for [Walkthrough: Enabling Backward Compatibility as Your Host Changes](https://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848).</span></span>  
  
## <a name="creating-the-contract-and-views"></a><span data-ttu-id="87283-140">Sözleşme ve görünümler oluşturma</span><span class="sxs-lookup"><span data-stu-id="87283-140">Creating the Contract and Views</span></span>  
 <span data-ttu-id="87283-141">Bu işlem hattı sözleşme kesimin tanımlar `ICalc1Contract` dört yöntemi tanımlayan arabirim: `add`, `subtract`, `multiply`, ve `divide`.</span><span class="sxs-lookup"><span data-stu-id="87283-141">The contract segment for this pipeline defines the `ICalc1Contract` interface, which defines four methods: `add`, `subtract`, `multiply`, and `divide`.</span></span>  
  
#### <a name="to-create-the-contract"></a><span data-ttu-id="87283-142">Sözleşme oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="87283-142">To create the contract</span></span>  
  
1.  <span data-ttu-id="87283-143">Visual Studio çözümünde adlı `CalculatorV1`açın `Calc1Contract` proje.</span><span class="sxs-lookup"><span data-stu-id="87283-143">In the Visual Studio solution named `CalculatorV1`, open the `Calc1Contract` project.</span></span>  
  
2.  <span data-ttu-id="87283-144">İçinde **Çözüm Gezgini**, aşağıdaki derlemelere başvurular ekleyin `Calc1Contract` proje:</span><span class="sxs-lookup"><span data-stu-id="87283-144">In **Solution Explorer**, add references to the following assemblies to the `Calc1Contract` project:</span></span>  
  
     <span data-ttu-id="87283-145">System.AddIn.Contract.dll</span><span class="sxs-lookup"><span data-stu-id="87283-145">System.AddIn.Contract.dll</span></span>  
  
     <span data-ttu-id="87283-146">System.AddIn.dll</span><span class="sxs-lookup"><span data-stu-id="87283-146">System.AddIn.dll</span></span>  
  
3.  <span data-ttu-id="87283-147">İçinde **Çözüm Gezgini**, yeni eklenen varsayılan sınıfı hariç **sınıf kitaplığı** projeleri.</span><span class="sxs-lookup"><span data-stu-id="87283-147">In **Solution Explorer**, exclude the default class that is added to new **Class Library** projects.</span></span>  
  
4.  <span data-ttu-id="87283-148">İçinde **Çözüm Gezgini**, projeye yeni bir öğe eklemek kullanarak **arabirimi** şablonu.</span><span class="sxs-lookup"><span data-stu-id="87283-148">In **Solution Explorer**, add a new item to the project, using the **Interface** template.</span></span> <span data-ttu-id="87283-149">İçinde **Yeni Öğe Ekle** iletişim kutusunda adı arabirim `ICalc1Contract`.</span><span class="sxs-lookup"><span data-stu-id="87283-149">In the **Add New Item** dialog box, name the interface `ICalc1Contract`.</span></span>  
  
5.  <span data-ttu-id="87283-150">Arabirimi dosyasında, ad alanı başvurularını ekleyin <xref:System.AddIn.Contract> ve <xref:System.AddIn.Pipeline>.</span><span class="sxs-lookup"><span data-stu-id="87283-150">In the interface file, add namespace references to <xref:System.AddIn.Contract> and <xref:System.AddIn.Pipeline>.</span></span>  
  
6.  <span data-ttu-id="87283-151">Bu sözleşme parçasını tamamlamak için aşağıdaki kodu kullanın.</span><span class="sxs-lookup"><span data-stu-id="87283-151">Use the following code to complete this contract segment.</span></span> <span data-ttu-id="87283-152">Bu arabirim olmalıdır Not <xref:System.AddIn.Pipeline.AddInContractAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="87283-152">Note that this interface must have the <xref:System.AddIn.Pipeline.AddInContractAttribute> attribute.</span></span>  
  
     [!code-csharp[AddInP1Contract#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1Contract/cs/ICalc1Contract.cs#1)]
     [!code-vb[AddInP1Contract#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1Contract/vb/ICalc1Contract.vb#1)]  
  
7.  <span data-ttu-id="87283-153">İsteğe bağlı olarak, Visual Studio çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="87283-153">Optionally, build the Visual Studio solution.</span></span> <span data-ttu-id="87283-154">Çözüm, son yordamı, ancak her yordam, her proje olmasını sağlar, sonra onu oluşturmak düzeltene kadar çalıştırılamaz.</span><span class="sxs-lookup"><span data-stu-id="87283-154">The solution cannot be run until the final procedure, but building it after each procedure ensures that each project is correct.</span></span>  
  
 <span data-ttu-id="87283-155">Eklenti görünümü ve ana görünümünde eklenti genellikle aynı kodu, özellikle ilk sürümüne sahip bir eklenti içinde aynı anda kolayca görünümler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87283-155">Because the add-in view and the host view of the add-in usually have the same code, especially in the first version of an add-in, you can easily create the views at the same time.</span></span> <span data-ttu-id="87283-156">Bunların değişiklik gösterdiği bir faktör: eklenti görünümü gerektirir <xref:System.AddIn.Pipeline.AddInBaseAttribute> eklentisinin ana görünümünde herhangi bir özniteliği ihtiyacı olmasa da, öznitelik.</span><span class="sxs-lookup"><span data-stu-id="87283-156">They differ by only one factor: the add-in view requires the <xref:System.AddIn.Pipeline.AddInBaseAttribute> attribute, while the host view of the add-in does not require any attributes.</span></span>  
  
#### <a name="to-create-the-add-in-view"></a><span data-ttu-id="87283-157">Eklenti görünümü oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="87283-157">To create the add-in view</span></span>  
  
1.  <span data-ttu-id="87283-158">Adlı yeni bir proje ekleyin `Calc1AddInView` için `CalculatorV1` çözüm.</span><span class="sxs-lookup"><span data-stu-id="87283-158">Add a new project named `Calc1AddInView` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="87283-159">Bu temel **sınıf kitaplığı** şablonu.</span><span class="sxs-lookup"><span data-stu-id="87283-159">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="87283-160">İçinde **Çözüm Gezgini**, System.AddIn.dll için bir başvuru ekleyin `Calc1AddInView` proje.</span><span class="sxs-lookup"><span data-stu-id="87283-160">In **Solution Explorer**, add a reference to System.AddIn.dll to the `Calc1AddInView` project.</span></span>  
  
3.  <span data-ttu-id="87283-161">İçinde **Çözüm Gezgini**, yeni eklenen varsayılan sınıfı hariç **sınıf kitaplığı** projeleri ve proje için yeni bir öğe eklemek kullanarak **arabirimi** şablonu.</span><span class="sxs-lookup"><span data-stu-id="87283-161">In **Solution Explorer**, exclude the default class that is added to new **Class Library** projects, and add a new item to the project, using the **Interface** template.</span></span> <span data-ttu-id="87283-162">İçinde **Yeni Öğe Ekle** iletişim kutusunda adı arabirim `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="87283-162">In the **Add New Item** dialog box, name the interface `ICalculator`.</span></span>  
  
4.  <span data-ttu-id="87283-163">Ad alanı başvuru arabirimi dosyasına ekleyin <xref:System.AddIn.Pipeline>.</span><span class="sxs-lookup"><span data-stu-id="87283-163">In the interface file, add a namespace reference to <xref:System.AddIn.Pipeline>.</span></span>  
  
5.  <span data-ttu-id="87283-164">Bu eklenti görünümü tamamlamak için aşağıdaki kodu kullanın.</span><span class="sxs-lookup"><span data-stu-id="87283-164">Use the following code to complete this add-in view.</span></span> <span data-ttu-id="87283-165">Bu arabirim olmalıdır Not <xref:System.AddIn.Pipeline.AddInBaseAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="87283-165">Note that this interface must have the <xref:System.AddIn.Pipeline.AddInBaseAttribute> attribute.</span></span>  
  
     [!code-csharp[AddInP1AddInViews#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInViews/cs/Calc1AddInView.cs#1)]
     [!code-vb[AddInP1AddInViews#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInViews/vb/Calc1AddInView.vb#1)]  
  
6.  <span data-ttu-id="87283-166">İsteğe bağlı olarak, Visual Studio çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="87283-166">Optionally, build the Visual Studio solution.</span></span>  
  
#### <a name="to-create-the-host-view-of-the-add-in"></a><span data-ttu-id="87283-167">Eklentinin ana bilgisayar görünümü oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="87283-167">To create the host view of the add-in</span></span>  
  
1.  <span data-ttu-id="87283-168">Adlı yeni bir proje ekleyin `Calc1HVA` için `CalculatorV1` çözüm.</span><span class="sxs-lookup"><span data-stu-id="87283-168">Add a new project named `Calc1HVA` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="87283-169">Bu temel **sınıf kitaplığı** şablonu.</span><span class="sxs-lookup"><span data-stu-id="87283-169">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="87283-170">İçinde **Çözüm Gezgini**, yeni eklenen varsayılan sınıfı hariç **sınıf kitaplığı** projeleri ve proje için yeni bir öğe eklemek kullanarak **arabirimi** şablonu.</span><span class="sxs-lookup"><span data-stu-id="87283-170">In **Solution Explorer**, exclude the default class that is added to new **Class Library** projects, and add a new item to the project, using the **Interface** template.</span></span> <span data-ttu-id="87283-171">İçinde **Yeni Öğe Ekle** iletişim kutusunda adı arabirim `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="87283-171">In the **Add New Item** dialog box, name the interface `ICalculator`.</span></span>  
  
3.  <span data-ttu-id="87283-172">Arabirimi dosyasında, eklentinin ana görünümünde tamamlamak için aşağıdaki kodu kullanın.</span><span class="sxs-lookup"><span data-stu-id="87283-172">In the interface file, use the following code to complete the host view of the add-in.</span></span>  
  
     [!code-csharp[AddInP1HVA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1HVA/cs/calc1hva.cs#1)]
     [!code-vb[AddInP1HVA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1HVA/vb/Calc1HVA.vb#1)]  
  
4.  <span data-ttu-id="87283-173">İsteğe bağlı olarak, Visual Studio çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="87283-173">Optionally, build the Visual Studio solution.</span></span>  
  
## <a name="creating-the-add-in-side-adapter"></a><span data-ttu-id="87283-174">Ekleme tarafı bağdaştırıcısı oluşturma</span><span class="sxs-lookup"><span data-stu-id="87283-174">Creating the Add-in-side Adapter</span></span>  
 <span data-ttu-id="87283-175">Bu ekleme tarafı bağdaştırıcısı bir görünüm ve sözleşme bağdaştırıcısı oluşur.</span><span class="sxs-lookup"><span data-stu-id="87283-175">This add-in-side adapter consists of one view-to-contract adapter.</span></span> <span data-ttu-id="87283-176">Bu işlem Hattı Kesim türleri eklenti görünümünden Anlaşmadaki dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="87283-176">This pipeline segment converts the types from the add-in view to the contract.</span></span>  
  
 <span data-ttu-id="87283-177">Bu işlem hattı eklenti konağa bir hizmet sağlar ve türleri eklentisi konağa akış.</span><span class="sxs-lookup"><span data-stu-id="87283-177">In this pipeline, the add-in provides a service to the host, and the types flow from the add-in to the host.</span></span> <span data-ttu-id="87283-178">Eklentinin ana bilgisayardan tür akış olduğundan, bu işlem hattı eklenti tarafındaki bir sözleşme ve görünüm bağdaştırıcısı dahil gerekmez.</span><span class="sxs-lookup"><span data-stu-id="87283-178">Because no types flow from the host to the add-in, you do not have to include a contract-to-view adapter on the add-in side of this pipeline.</span></span>  
  
#### <a name="to-create-the-add-in-side-adapter"></a><span data-ttu-id="87283-179">Ekle tarafı bağdaştırıcısı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="87283-179">To create the add-in-side adapter</span></span>  
  
1.  <span data-ttu-id="87283-180">Adlı yeni bir proje ekleyin `Calc1AddInSideAdapter` için `CalculatorV1` çözüm.</span><span class="sxs-lookup"><span data-stu-id="87283-180">Add a new project named `Calc1AddInSideAdapter` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="87283-181">Bu temel **sınıf kitaplığı** şablonu.</span><span class="sxs-lookup"><span data-stu-id="87283-181">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="87283-182">İçinde **Çözüm Gezgini**, aşağıdaki derlemelere başvurular ekleyin `Calc1AddInSideAdapter` proje:</span><span class="sxs-lookup"><span data-stu-id="87283-182">In **Solution Explorer**, add references to the following assemblies to the `Calc1AddInSideAdapter` project:</span></span>  
  
     <span data-ttu-id="87283-183">System.AddIn.dll</span><span class="sxs-lookup"><span data-stu-id="87283-183">System.AddIn.dll</span></span>  
  
     <span data-ttu-id="87283-184">System.AddIn.Contract.dll</span><span class="sxs-lookup"><span data-stu-id="87283-184">System.AddIn.Contract.dll</span></span>  
  
3.  <span data-ttu-id="87283-185">Bitişik ardışık düzeni segmentlerini projelerde proje başvuruları ekleyin:</span><span class="sxs-lookup"><span data-stu-id="87283-185">Add project references to the projects for the adjacent pipeline segments:</span></span>  
  
     `Calc1AddInView`  
  
     `Calc1Contract`  
  
4.  <span data-ttu-id="87283-186">Her bir proje başvurusu seçin ve **özellikleri** ayarlamak **Yereli Kopyala** için **False**.</span><span class="sxs-lookup"><span data-stu-id="87283-186">Select each project reference, and in **Properties** set **Copy Local** to **False**.</span></span> <span data-ttu-id="87283-187">Visual Basic'teki **başvuruları** sekmesinde **proje özellikleri** ayarlanacak **Yereli Kopyala** için **False** iki proje başvuruları için.</span><span class="sxs-lookup"><span data-stu-id="87283-187">In Visual Basic, use the **References** tab of **Project Properties** to set **Copy Local** to **False** for the two project references.</span></span>  
  
5.  <span data-ttu-id="87283-188">Projenin varsayılan sınıfı Yeniden Adlandır `CalculatorViewToContractAddInSideAdapter`.</span><span class="sxs-lookup"><span data-stu-id="87283-188">Rename the project's default class `CalculatorViewToContractAddInSideAdapter`.</span></span>  
  
6.  <span data-ttu-id="87283-189">Sınıf dosyasında ad alanı başvurularını ekleyin <xref:System.AddIn.Pipeline>.</span><span class="sxs-lookup"><span data-stu-id="87283-189">In the class file, add namespace references to <xref:System.AddIn.Pipeline>.</span></span>  
  
7.  <span data-ttu-id="87283-190">Sınıf dosyasında bitişik parçaları için ad alanı başvurularını ekleyin: `CalcAddInViews` ve `CalculatorContracts`.</span><span class="sxs-lookup"><span data-stu-id="87283-190">In the class file, add namespace references for the adjacent segments: `CalcAddInViews` and `CalculatorContracts`.</span></span> <span data-ttu-id="87283-191">(Visual Basic'te bu ad alanı başvurularını olan `Calc1AddInView.CalcAddInViews` ve `Calc1Contract.CalculatorContracts`sürece, Visual Basic projelerinde varsayılan ad alanlarını devre dışı bırakmış.)</span><span class="sxs-lookup"><span data-stu-id="87283-191">(In Visual Basic, these namespace references are `Calc1AddInView.CalcAddInViews` and `Calc1Contract.CalculatorContracts`, unless you have turned off the default namespaces in your Visual Basic projects.)</span></span>  
  
8.  <span data-ttu-id="87283-192">Uygulama <xref:System.AddIn.Pipeline.AddInAdapterAttribute> özniteliğini `CalculatorViewToContractAddInSideAdapter` sınıfı Ekle tarafı bağdaştırıcısı olarak tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="87283-192">Apply the <xref:System.AddIn.Pipeline.AddInAdapterAttribute> attribute to the `CalculatorViewToContractAddInSideAdapter` class, to identify it as the add-in-side adapter.</span></span>  
  
9. <span data-ttu-id="87283-193">Olun `CalculatorViewToContractAddInSideAdapter` sınıfı <xref:System.AddIn.Pipeline.ContractBase>, varsayılan bir uygulama sağlayan <xref:System.AddIn.Contract.IContract> arabirim ve işlem hattının anlaşma arabirimi uygulayan `ICalc1Contract`.</span><span class="sxs-lookup"><span data-stu-id="87283-193">Make the `CalculatorViewToContractAddInSideAdapter` class inherit <xref:System.AddIn.Pipeline.ContractBase>, which provides a default implementation of the <xref:System.AddIn.Contract.IContract> interface, and implement the contract interface for the pipeline, `ICalc1Contract`.</span></span>  
  
10. <span data-ttu-id="87283-194">Kabul eden bir Genel oluşturucu ekleyin bir `ICalculator`, özel bir alanda önbelleğe alır ve temel sınıf oluşturucusunu çağırır.</span><span class="sxs-lookup"><span data-stu-id="87283-194">Add a public constructor that accepts an `ICalculator`, caches it in a private field, and calls the base class constructor.</span></span>  
  
11. <span data-ttu-id="87283-195">Üyeleri uygulamak için `ICalc1Contract`, karşılık gelen üyelerini çağırarak yeterlidir `ICalculator` örneği oluşturucuya geçirilir ve sonuçlar döndürür.</span><span class="sxs-lookup"><span data-stu-id="87283-195">To implement the members of `ICalc1Contract`, simply call the corresponding members of the `ICalculator` instance that is passed to the constructor, and return the results.</span></span> <span data-ttu-id="87283-196">Bu görünüm uyum sağlayan (`ICalculator`) sözleşmeye (`ICalc1Contract`).</span><span class="sxs-lookup"><span data-stu-id="87283-196">This adapts the view (`ICalculator`) to the contract (`ICalc1Contract`).</span></span>  
  
     <span data-ttu-id="87283-197">Aşağıdaki kod, tamamlanan ekleme tarafı bağdaştırıcısı gösterir.</span><span class="sxs-lookup"><span data-stu-id="87283-197">The following code shows the completed add-in-side adapter.</span></span>  
  
     [!code-csharp[AddInP1AddInSideAdapters#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInSideAdapters/cs/Calc1ViewToContractAddInSideAdapter.cs#1)]
     [!code-vb[AddInP1AddInSideAdapters#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInSideAdapters/vb/Calc1ViewToContractAddInSideAdapter.vb#1)]  
  
12. <span data-ttu-id="87283-198">İsteğe bağlı olarak, Visual Studio çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="87283-198">Optionally, build the Visual Studio solution.</span></span>  
  
## <a name="creating-the-host-side-adapter"></a><span data-ttu-id="87283-199">Konak tarafı bağdaştırıcısı oluşturma</span><span class="sxs-lookup"><span data-stu-id="87283-199">Creating the Host-side Adapter</span></span>  
 <span data-ttu-id="87283-200">Bu konak tarafı bağdaştırıcı bir sözleşme ve görünüm bağdaştırıcısı oluşur.</span><span class="sxs-lookup"><span data-stu-id="87283-200">This host-side adapter consists of one contract-to-view adapter.</span></span> <span data-ttu-id="87283-201">Bu kesimin eklentisinin ana görünümünde Anlaşmadaki uyum sağlar.</span><span class="sxs-lookup"><span data-stu-id="87283-201">This segment adapts the contract to the host view of the add-in.</span></span>  
  
 <span data-ttu-id="87283-202">Bu işlem hattı, eklenti hizmet ana bilgisayarı ve türleri flow'a eklenti konağa sağlar.</span><span class="sxs-lookup"><span data-stu-id="87283-202">In this pipeline, the add-in provides a service to the host and the types flow from the add-in to the host.</span></span> <span data-ttu-id="87283-203">Eklentinin ana bilgisayardan tür akış olduğundan, bir görünüm ve sözleşme bağdaştırıcısı dahil gerekmez.</span><span class="sxs-lookup"><span data-stu-id="87283-203">Because no types flow from the host to the add-in, you do not have to include a view-to-contract adapter.</span></span>  
  
 <span data-ttu-id="87283-204">Ömür Yönetimi uygulamak için kullanmak bir <xref:System.AddIn.Pipeline.ContractHandle> Anlaşmadaki bir ömrü belirteci eklemek için nesne.</span><span class="sxs-lookup"><span data-stu-id="87283-204">To implement lifetime management, use a <xref:System.AddIn.Pipeline.ContractHandle> object to attach a lifetime token to the contract.</span></span> <span data-ttu-id="87283-205">Sırayla çalışması ömür yönetimi için bu tutamacı başvuru tutmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="87283-205">You must keep a reference to this handle in order for lifetime management to work.</span></span> <span data-ttu-id="87283-206">Artık kullanılmayan ve çöp toplama için kullanılabilir hale getirmek eklenti sistem nesneleri atmak çünkü belirteç uygulandıktan sonra ek programlama gereklidir.</span><span class="sxs-lookup"><span data-stu-id="87283-206">After the token is applied, no additional programming is required because the add-in system can dispose of objects when they are no longer being used and make them available for garbage collection.</span></span> <span data-ttu-id="87283-207">Daha fazla bilgi için [ömür Yönetimi](https://msdn.microsoft.com/library/57a9c87e-394c-4fef-89f2-aa4223a2aeb5).</span><span class="sxs-lookup"><span data-stu-id="87283-207">For more information, see [Lifetime Management](https://msdn.microsoft.com/library/57a9c87e-394c-4fef-89f2-aa4223a2aeb5).</span></span>  
  
#### <a name="to-create-the-host-side-adapter"></a><span data-ttu-id="87283-208">Konak tarafı bağdaştırıcısı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="87283-208">To create the host-side adapter</span></span>  
  
1.  <span data-ttu-id="87283-209">Adlı yeni bir proje ekleyin `Calc1HostSideAdapter` için `CalculatorV1` çözüm.</span><span class="sxs-lookup"><span data-stu-id="87283-209">Add a new project named `Calc1HostSideAdapter` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="87283-210">Bu temel **sınıf kitaplığı** şablonu.</span><span class="sxs-lookup"><span data-stu-id="87283-210">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="87283-211">İçinde **Çözüm Gezgini**, aşağıdaki derlemelere başvurular ekleyin `Calc1HostSideAdapter` proje:</span><span class="sxs-lookup"><span data-stu-id="87283-211">In **Solution Explorer**, add references to the following assemblies to the `Calc1HostSideAdapter` project:</span></span>  
  
     <span data-ttu-id="87283-212">System.AddIn.dll</span><span class="sxs-lookup"><span data-stu-id="87283-212">System.AddIn.dll</span></span>  
  
     <span data-ttu-id="87283-213">System.AddIn.Contract.dll</span><span class="sxs-lookup"><span data-stu-id="87283-213">System.AddIn.Contract.dll</span></span>  
  
3.  <span data-ttu-id="87283-214">Bitişik parçaları için proje proje başvurular ekleyin:</span><span class="sxs-lookup"><span data-stu-id="87283-214">Add project references to the projects for the adjacent segments:</span></span>  
  
     `Calc1Contract`  
  
     `Calc1HVA`  
  
4.  <span data-ttu-id="87283-215">Her bir proje başvurusu seçin ve **özellikleri** ayarlamak **Yereli Kopyala** için **False**.</span><span class="sxs-lookup"><span data-stu-id="87283-215">Select each project reference, and in **Properties** set **Copy Local** to **False**.</span></span> <span data-ttu-id="87283-216">Visual Basic'teki **başvuruları** sekmesinde **proje özellikleri** ayarlanacak **Yereli Kopyala** için **False** iki proje başvuruları için.</span><span class="sxs-lookup"><span data-stu-id="87283-216">In Visual Basic, use the **References** tab of **Project Properties** to set **Copy Local** to **False** for the two project references.</span></span>  
  
5.  <span data-ttu-id="87283-217">Projenin varsayılan sınıfı Yeniden Adlandır `CalculatorContractToViewHostSideAdapter`.</span><span class="sxs-lookup"><span data-stu-id="87283-217">Rename the project's default class `CalculatorContractToViewHostSideAdapter`.</span></span>  
  
6.  <span data-ttu-id="87283-218">Sınıf dosyasında ad alanı başvurularını ekleyin <xref:System.AddIn.Pipeline>.</span><span class="sxs-lookup"><span data-stu-id="87283-218">In the class file, add namespace references to <xref:System.AddIn.Pipeline>.</span></span>  
  
7.  <span data-ttu-id="87283-219">Sınıf dosyasında bitişik parçaları için ad alanı başvurularını ekleyin: `CalcHVAs` ve `CalculatorContracts`.</span><span class="sxs-lookup"><span data-stu-id="87283-219">In the class file, add namespace references for the adjacent segments: `CalcHVAs` and `CalculatorContracts`.</span></span> <span data-ttu-id="87283-220">(Visual Basic'te bu ad alanı başvurularını olan `Calc1HVA.CalcHVAs` ve `Calc1Contract.CalculatorContracts`sürece, Visual Basic projelerinde varsayılan ad alanlarını devre dışı bırakmış.)</span><span class="sxs-lookup"><span data-stu-id="87283-220">(In Visual Basic, these namespace references are `Calc1HVA.CalcHVAs` and `Calc1Contract.CalculatorContracts`, unless you have turned off the default namespaces in your Visual Basic projects.)</span></span>  
  
8.  <span data-ttu-id="87283-221">Uygulama <xref:System.AddIn.Pipeline.HostAdapterAttribute> özniteliğini `CalculatorContractToViewHostSideAdapter` konak tarafı bağdaştırıcısı kesim olarak tanımlamak için sınıfı.</span><span class="sxs-lookup"><span data-stu-id="87283-221">Apply the <xref:System.AddIn.Pipeline.HostAdapterAttribute> attribute to the `CalculatorContractToViewHostSideAdapter` class, to identify it as the host-side adapter segment.</span></span>  
  
9. <span data-ttu-id="87283-222">Olun `CalculatorContractToViewHostSideAdapter` sınıf uygulama ana görünümünde eklentisinin temsil eden arabirim: `Calc1HVAs.ICalculator` (`Calc1HVA.CalcHVAs.ICalculator` Visual Basic'te).</span><span class="sxs-lookup"><span data-stu-id="87283-222">Make the `CalculatorContractToViewHostSideAdapter` class implement the interface that represents the host view of the add-in: `Calc1HVAs.ICalculator` (`Calc1HVA.CalcHVAs.ICalculator` in Visual Basic).</span></span>  
  
10. <span data-ttu-id="87283-223">İşlem hattı sözleşme türü kabul eden bir Genel oluşturucu ekleyin `ICalc1Contract`.</span><span class="sxs-lookup"><span data-stu-id="87283-223">Add a public constructor that accepts the pipeline contract type, `ICalc1Contract`.</span></span> <span data-ttu-id="87283-224">Oluşturucu sözleşmesine başvuru önbellek gerekir.</span><span class="sxs-lookup"><span data-stu-id="87283-224">The constructor must cache the reference to the contract.</span></span> <span data-ttu-id="87283-225">Bu ayrıca oluşturabilir ve yeni bir önbellek <xref:System.AddIn.Pipeline.ContractHandle> ömrünü yönetmek için sözleşmeyi için.</span><span class="sxs-lookup"><span data-stu-id="87283-225">It must also create and cache a new <xref:System.AddIn.Pipeline.ContractHandle> for the contract, to manage the lifetime of the add-in.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="87283-226"><xref:System.AddIn.Pipeline.ContractHandle> Ömür yönetimi için kritik öneme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="87283-226">The <xref:System.AddIn.Pipeline.ContractHandle> is critical to lifetime management.</span></span> <span data-ttu-id="87283-227">Başvuru tutmak başarısız olursa <xref:System.AddIn.Pipeline.ContractHandle> nesne, çöp toplama, geri ve işlem hattı, programınızın beklemediğinden kapanır.</span><span class="sxs-lookup"><span data-stu-id="87283-227">If you fail to keep a reference to the <xref:System.AddIn.Pipeline.ContractHandle> object, garbage collection will reclaim it, and the pipeline will shut down when your program does not expect it.</span></span> <span data-ttu-id="87283-228">Bu gibi tanılama zor olan hatalara yol <xref:System.AppDomainUnloadedException>.</span><span class="sxs-lookup"><span data-stu-id="87283-228">This can lead to errors that are difficult to diagnose, such as <xref:System.AppDomainUnloadedException>.</span></span> <span data-ttu-id="87283-229">Bu durum bir hata olduğunu tespit etmek ömrü Yönetimi kod bir yolu olmasını kapatma bir işlem hattı, yaşamında normal bir aşamayı ifade eder.</span><span class="sxs-lookup"><span data-stu-id="87283-229">Shutdown is a normal stage in the life of a pipeline, so there is no way for the lifetime management code to detect that this condition is an error.</span></span>  
  
11. <span data-ttu-id="87283-230">Üyeleri uygulamak için `ICalculator`, karşılık gelen üyelerini çağırarak yeterlidir `ICalc1Contract` örneği oluşturucuya geçirilir ve sonuçlar döndürür.</span><span class="sxs-lookup"><span data-stu-id="87283-230">To implement the members of `ICalculator`, simply call the corresponding members of the `ICalc1Contract` instance that is passed to the constructor, and return the results.</span></span> <span data-ttu-id="87283-231">Bu sözleşme uyum sağlayan (`ICalc1Contract`) görünümüne (`ICalculator`).</span><span class="sxs-lookup"><span data-stu-id="87283-231">This adapts the contract (`ICalc1Contract`) to the view (`ICalculator`).</span></span>  
  
     <span data-ttu-id="87283-232">Aşağıdaki kod, tamamlanan konak tarafı bağdaştırıcısı gösterir.</span><span class="sxs-lookup"><span data-stu-id="87283-232">The following code shows the completed host-side adapter.</span></span>  
  
     [!code-csharp[AddInP1HostSideAdapters#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1HostSideAdapters/cs/Calc1ContractToViewHostSideAdapter.cs#1)]
     [!code-vb[AddInP1HostSideAdapters#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1HostSideAdapters/vb/Calc1ContractToViewHostSideAdapter.vb#1)]  
  
12. <span data-ttu-id="87283-233">İsteğe bağlı olarak, Visual Studio çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="87283-233">Optionally, build the Visual Studio solution.</span></span>  
  
## <a name="creating-the-host"></a><span data-ttu-id="87283-234">Konağı oluşturma</span><span class="sxs-lookup"><span data-stu-id="87283-234">Creating the Host</span></span>  
 <span data-ttu-id="87283-235">Bir ana bilgisayar uygulaması ile eklenti eklentisinin ana görünümünde aracılığıyla etkileşim kurar.</span><span class="sxs-lookup"><span data-stu-id="87283-235">A host application interacts with the add-in through the host view of the add-in.</span></span> <span data-ttu-id="87283-236">Tarafından sağlanan eklentisi bulma ve etkinleştirme yöntemlerini kullanan <xref:System.AddIn.Hosting.AddInStore> ve <xref:System.AddIn.Hosting.AddInToken> sınıflar aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="87283-236">It uses add-in discovery and activation methods provided by the <xref:System.AddIn.Hosting.AddInStore> and <xref:System.AddIn.Hosting.AddInToken> classes to do the following:</span></span>  
  
-   <span data-ttu-id="87283-237">İşlem hattı ve eklenti bilgileri önbelleğini güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="87283-237">Update the cache of pipeline and add-in information.</span></span>  
  
-   <span data-ttu-id="87283-238">Ana görünüm türünün, eklentiler bulma `ICalculator`, belirtilen işlem hattı kök dizininin altındaki.</span><span class="sxs-lookup"><span data-stu-id="87283-238">Find add-ins of the host view type, `ICalculator`, under the specified pipeline root directory.</span></span>  
  
-   <span data-ttu-id="87283-239">Hangi kullanmak için eklenti belirtmek için kullanıcıdan.</span><span class="sxs-lookup"><span data-stu-id="87283-239">Prompt the user to specify which add-in to use.</span></span>  
  
-   <span data-ttu-id="87283-240">Seçili eklenti belirtilen güvenlik güven düzeyine sahip yeni bir uygulama etki alanında etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="87283-240">Activate the selected add-in in a new application domain with a specified security trust level.</span></span>  
  
-   <span data-ttu-id="87283-241">Özel çalıştırma `RunCalculator` yöntemi eklentinin ana görünümünde eklentisinin belirtildiği gibi yöntemleri çağırır.</span><span class="sxs-lookup"><span data-stu-id="87283-241">Run the custom `RunCalculator` method, which calls the add-in's methods as specified by the host view of the add-in.</span></span>  
  
#### <a name="to-create-the-host"></a><span data-ttu-id="87283-242">Ana bilgisayar oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="87283-242">To create the host</span></span>  
  
1.  <span data-ttu-id="87283-243">Adlı yeni bir proje ekleyin `Calc1Host` için `CalculatorV1` çözüm.</span><span class="sxs-lookup"><span data-stu-id="87283-243">Add a new project named `Calc1Host` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="87283-244">Bu temel **konsol uygulaması** şablonu.</span><span class="sxs-lookup"><span data-stu-id="87283-244">Base it on the **Console Application** template.</span></span>  
  
2.  <span data-ttu-id="87283-245">İçinde **Çözüm Gezgini**, System.AddIn.dll derlemeye bir başvuru ekleyin `Calc1Host` proje.</span><span class="sxs-lookup"><span data-stu-id="87283-245">In **Solution Explorer**, add a reference to the System.AddIn.dll assembly to the `Calc1Host` project.</span></span>  
  
3.  <span data-ttu-id="87283-246">Bir proje başvurusu Ekle `Calc1HVA` proje.</span><span class="sxs-lookup"><span data-stu-id="87283-246">Add a project reference to the `Calc1HVA` project.</span></span> <span data-ttu-id="87283-247">Proje başvurusu seçin ve **özellikleri** ayarlamak **Yereli Kopyala** için **False**.</span><span class="sxs-lookup"><span data-stu-id="87283-247">Select the project reference, and in **Properties** set **Copy Local** to **False**.</span></span> <span data-ttu-id="87283-248">Visual Basic'teki **başvuruları** sekmesinde **proje özellikleri** ayarlanacak **Yereli Kopyala** için **False**.</span><span class="sxs-lookup"><span data-stu-id="87283-248">In Visual Basic, use the **References** tab of **Project Properties** to set **Copy Local** to **False**.</span></span>  
  
4.  <span data-ttu-id="87283-249">Sınıf dosyasını (Visual Basic'te Modülü) Yeniden Adlandır `MathHost1`.</span><span class="sxs-lookup"><span data-stu-id="87283-249">Rename the class file (module in Visual Basic) `MathHost1`.</span></span>  
  
5.  <span data-ttu-id="87283-250">Visual Basic'teki **uygulama** sekmesinde **proje özellikleri** ayarlamak için iletişim kutusunun **Başlangıç nesnesi** için **Sub Main**.</span><span class="sxs-lookup"><span data-stu-id="87283-250">In Visual Basic, use the **Application** tab of the **Project Properties** dialog box to set **Startup object** to **Sub Main**.</span></span>  
  
6.  <span data-ttu-id="87283-251">Bir ad alanı başvuru sınıfı veya Modülü dosyasında ekleyin <xref:System.AddIn.Hosting>.</span><span class="sxs-lookup"><span data-stu-id="87283-251">In the class or module file, add a namespace reference to <xref:System.AddIn.Hosting>.</span></span>  
  
7.  <span data-ttu-id="87283-252">Eklentinin ana bilgisayar görünümü için bir ad alanı başvuru sınıfı veya modülü dosyasına ekleyin: `CalcHVAs`.</span><span class="sxs-lookup"><span data-stu-id="87283-252">In the class or module file, add a namespace reference for the host view of the add-in: `CalcHVAs`.</span></span> <span data-ttu-id="87283-253">(Visual Basic'te bu ad alanı başvurudur `Calc1HVA.CalcHVAs`sürece, Visual Basic projelerinde varsayılan ad alanlarını devre dışı bırakmış.)</span><span class="sxs-lookup"><span data-stu-id="87283-253">(In Visual Basic, this namespace reference is `Calc1HVA.CalcHVAs`, unless you have turned off the default namespaces in your Visual Basic projects.)</span></span>  
  
8.  <span data-ttu-id="87283-254">İçinde **Çözüm Gezgini**, çözümü seçin ve **proje** menüsünde **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="87283-254">In **Solution Explorer**, select the solution and from the **Project** menu choose **Properties**.</span></span> <span data-ttu-id="87283-255">İçinde **çözüm özellik sayfaları** iletişim kutusu, kümesi **tek başlangıç projesi** bu ana bilgisayar uygulaması proje olacak.</span><span class="sxs-lookup"><span data-stu-id="87283-255">In the **Solution Property Pages** dialog box, set the **Single Startup Project** to be this host application project.</span></span>  
  
9. <span data-ttu-id="87283-256">Sınıf veya modül dosyasında kullanmak <xref:System.AddIn.Hosting.AddInStore.Update%2A?displayProperty=nameWithType> önbelleği güncelleştirmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="87283-256">In the class or module file, use the <xref:System.AddIn.Hosting.AddInStore.Update%2A?displayProperty=nameWithType> method to update the cache.</span></span> <span data-ttu-id="87283-257">Kullanma <xref:System.AddIn.Hosting.AddInStore.FindAddIn%2A?displayProperty=nameWithType> belirteçleri koleksiyonu almak ve kullanmak için yöntem <xref:System.AddIn.Hosting.AddInToken.Activate%2A?displayProperty=nameWithType> bir eklentiyi etkinleştirmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="87283-257">Use the <xref:System.AddIn.Hosting.AddInStore.FindAddIn%2A?displayProperty=nameWithType> method to get a collection of tokens, and use the <xref:System.AddIn.Hosting.AddInToken.Activate%2A?displayProperty=nameWithType> method to activate an add-in.</span></span>  
  
     <span data-ttu-id="87283-258">Aşağıdaki kod, tamamlanan Ana bilgisayar uygulaması gösterir.</span><span class="sxs-lookup"><span data-stu-id="87283-258">The following code shows the completed host application.</span></span>  
  
     [!code-csharp[AddInP1Host#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1Host/cs/MathHost1.cs#1)]
     [!code-vb[AddInP1Host#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1Host/vb/MathHost1.vb#1)]  
  
    > [!NOTE]
    >  <span data-ttu-id="87283-259">Bu kod, işlem hattı klasör yapısını uygulama klasöründe bulunduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="87283-259">This code assumes that the pipeline folder structure is located in the application folder.</span></span> <span data-ttu-id="87283-260">Başka bir yerde bulunan ayarlar kod satırının tıklarsanız `addInRoot` değişken değişkeni içeren işlem hattı dizin yapınızı yolu.</span><span class="sxs-lookup"><span data-stu-id="87283-260">If you located it elsewhere, change the line of code that sets the `addInRoot` variable, so that the variable contains the path to your pipeline directory structure.</span></span>  
  
     <span data-ttu-id="87283-261">Kod bir `ChooseCalculator` belirteçlerin listesi ve eklenti seçmek için kullanıcıdan istemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="87283-261">The code uses a `ChooseCalculator` method to list the tokens and to prompt the user to choose an add-in.</span></span> <span data-ttu-id="87283-262">`RunCalculator` Yöntemi basit matematik ifadeler için kullanıcıdan, kullanarak ifadeleri ayrıştırma `Parser` sınıfı ve sonuçları döndüren eklenti tarafından görüntüler.</span><span class="sxs-lookup"><span data-stu-id="87283-262">The `RunCalculator` method prompts the user for simple math expressions, parses the expressions using the `Parser` class, and displays the results returned by the add-in.</span></span>  
  
10. <span data-ttu-id="87283-263">İsteğe bağlı olarak, Visual Studio çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="87283-263">Optionally, build the Visual Studio solution.</span></span>  
  
## <a name="creating-the-add-in"></a><span data-ttu-id="87283-264">Eklentiyi oluşturma</span><span class="sxs-lookup"><span data-stu-id="87283-264">Creating the Add-In</span></span>  
 <span data-ttu-id="87283-265">Bir eklenti eklenti görünümü tarafından belirtilen yöntemleri uygular.</span><span class="sxs-lookup"><span data-stu-id="87283-265">An add-in implements the methods specified by the add-in view.</span></span> <span data-ttu-id="87283-266">Bu eklenti uygulayan `Add`, `Subtract`, `Multiply`, ve `Divide` işlemler ve ana bilgisayar sonuçları döndürür.</span><span class="sxs-lookup"><span data-stu-id="87283-266">This add-in implements the `Add`, `Subtract`, `Multiply`, and `Divide` operations and returns the results to the host.</span></span>  
  
#### <a name="to-create-the-add-in"></a><span data-ttu-id="87283-267">Eklenti oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="87283-267">To create the add-in</span></span>  
  
1.  <span data-ttu-id="87283-268">Adlı yeni bir proje ekleyin `AddInCalcV1` için `CalculatorV1` çözüm.</span><span class="sxs-lookup"><span data-stu-id="87283-268">Add a new project named `AddInCalcV1` to the `CalculatorV1` solution.</span></span> <span data-ttu-id="87283-269">Bu temel **sınıf kitaplığı** şablonu.</span><span class="sxs-lookup"><span data-stu-id="87283-269">Base it on the **Class Library** template.</span></span>  
  
2.  <span data-ttu-id="87283-270">İçinde **Çözüm Gezgini**, projeye System.AddIn.dll derlemesine bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="87283-270">In **Solution Explorer**, add a reference to the System.AddIn.dll assembly to the project.</span></span>  
  
3.  <span data-ttu-id="87283-271">Bir proje başvurusu Ekle `Calc1AddInView` proje.</span><span class="sxs-lookup"><span data-stu-id="87283-271">Add a project reference to the `Calc1AddInView` project.</span></span> <span data-ttu-id="87283-272">Proje başvurusu seçin ve **özellikleri**ayarlayın **Yereli Kopyala** için **False**.</span><span class="sxs-lookup"><span data-stu-id="87283-272">Select the project reference, and in **Properties**, set **Copy Local** to **False**.</span></span> <span data-ttu-id="87283-273">Visual Basic'teki **başvuruları** sekmesinde **proje özellikleri** ayarlanacak **Yereli Kopyala** için **False** proje başvurusu için.</span><span class="sxs-lookup"><span data-stu-id="87283-273">In Visual Basic, use the **References** tab of **Project Properties** to set **Copy Local** to **False** for the project reference.</span></span>  
  
4.  <span data-ttu-id="87283-274">Sınıfı yeniden adlandırmak `AddInCalcV1`.</span><span class="sxs-lookup"><span data-stu-id="87283-274">Rename the class `AddInCalcV1`.</span></span>  
  
5.  <span data-ttu-id="87283-275">Sınıf dosyasında, bir ad alanı referansı eklemek <xref:System.AddIn> ve eklenti görünümü segment: `CalcAddInViews` (`Calc1AddInView.CalcAddInViews` Visual Basic'te).</span><span class="sxs-lookup"><span data-stu-id="87283-275">In the class file, add a namespace reference to <xref:System.AddIn> and the add-in view segment: `CalcAddInViews` (`Calc1AddInView.CalcAddInViews` in Visual Basic).</span></span>  
  
6.  <span data-ttu-id="87283-276">Uygulama <xref:System.AddIn.AddInAttribute> özniteliğini `AddInCalcV1` sınıf bir eklenti olarak tanımlamak için sınıfı.</span><span class="sxs-lookup"><span data-stu-id="87283-276">Apply the <xref:System.AddIn.AddInAttribute> attribute to the `AddInCalcV1` class, to identify the class as an add-in.</span></span>  
  
7.  <span data-ttu-id="87283-277">Olun `AddInCalcV1` sınıf uygulama eklenti görünümü temsil eden arabirim: `CalcAddInViews.ICalculator` (`Calc1AddInView.CalcAddInViews.ICalculator` Visual Basic'te).</span><span class="sxs-lookup"><span data-stu-id="87283-277">Make the `AddInCalcV1` class implement the interface that represents the add-in view: `CalcAddInViews.ICalculator` (`Calc1AddInView.CalcAddInViews.ICalculator` in Visual Basic).</span></span>  
  
8.  <span data-ttu-id="87283-278">Üyeleri uygulamak `ICalculator` uygun hesaplamaların sonuçlarını döndürerek.</span><span class="sxs-lookup"><span data-stu-id="87283-278">Implement the members of `ICalculator` by returning the results of the appropriate calculations.</span></span>  
  
     <span data-ttu-id="87283-279">Aşağıdaki kod, tamamlanan eklentisi gösterir.</span><span class="sxs-lookup"><span data-stu-id="87283-279">The following code shows the completed add-in.</span></span>  
  
     [!code-csharp[AddInP1AddInCalcV1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInCalcV1/cs/AddInCalcV1.cs#1)]
     [!code-vb[AddInP1AddInCalcV1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInCalcV1/vb/AddInCalcV1.vb#1)]  
  
9. <span data-ttu-id="87283-280">İsteğe bağlı olarak, Visual Studio çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="87283-280">Optionally, build the Visual Studio solution.</span></span>  
  
## <a name="deploying-the-pipeline"></a><span data-ttu-id="87283-281">İşlem hattı dağıtma</span><span class="sxs-lookup"><span data-stu-id="87283-281">Deploying the Pipeline</span></span>  
 <span data-ttu-id="87283-282">Derleme ve eklenti parçaları için gerekli işlem hattı dizin yapısını dağıtmak artık hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="87283-282">You are now ready to build and deploy the add-in segments to the required pipeline directory structure.</span></span>  
  
#### <a name="to-deploy-the-segments-to-the-pipeline"></a><span data-ttu-id="87283-283">Segment işlem hattına dağıtmak için</span><span class="sxs-lookup"><span data-stu-id="87283-283">To deploy the segments to the pipeline</span></span>  
  
1.  <span data-ttu-id="87283-284">Çözümdeki her proje için kullanmak **derleme** sekmesinde **proje özellikleri** ( **derleme** Visual Basic sekmesini) değerini ayarlamak için **çıkış yolu**  ( **yapı çıkış yolu** Visual Basic'te).</span><span class="sxs-lookup"><span data-stu-id="87283-284">For each project in the solution, use the **Build** tab of **Project Properties** (the **Compile** tab in Visual Basic) to set the value of the **Output path** (the **Build output path** in Visual Basic).</span></span> <span data-ttu-id="87283-285">Uygulama klasörünüzdeki adlı `MyApp`, örneğin, projelerinizi aşağıdaki klasörler halinde oluşturmayı tercih:</span><span class="sxs-lookup"><span data-stu-id="87283-285">If you named your application folder `MyApp`, for example, your projects would build into the following folders:</span></span>  
  
    |<span data-ttu-id="87283-286">Proje</span><span class="sxs-lookup"><span data-stu-id="87283-286">Project</span></span>|<span data-ttu-id="87283-287">Yol</span><span class="sxs-lookup"><span data-stu-id="87283-287">Path</span></span>|  
    |-------------|----------|  
    |<span data-ttu-id="87283-288">AddInCalcV1</span><span class="sxs-lookup"><span data-stu-id="87283-288">AddInCalcV1</span></span>|<span data-ttu-id="87283-289">MyApp\Pipeline\AddIns\CalcV1</span><span class="sxs-lookup"><span data-stu-id="87283-289">MyApp\Pipeline\AddIns\CalcV1</span></span>|  
    |<span data-ttu-id="87283-290">Calc1AddInSideAdapter</span><span class="sxs-lookup"><span data-stu-id="87283-290">Calc1AddInSideAdapter</span></span>|<span data-ttu-id="87283-291">MyApp\Pipeline\AddInSideAdapters</span><span class="sxs-lookup"><span data-stu-id="87283-291">MyApp\Pipeline\AddInSideAdapters</span></span>|  
    |<span data-ttu-id="87283-292">Calc1AddInView</span><span class="sxs-lookup"><span data-stu-id="87283-292">Calc1AddInView</span></span>|<span data-ttu-id="87283-293">MyApp\Pipeline\AddInViews</span><span class="sxs-lookup"><span data-stu-id="87283-293">MyApp\Pipeline\AddInViews</span></span>|  
    |<span data-ttu-id="87283-294">Calc1Contract</span><span class="sxs-lookup"><span data-stu-id="87283-294">Calc1Contract</span></span>|<span data-ttu-id="87283-295">MyApp\Pipeline\Contracts</span><span class="sxs-lookup"><span data-stu-id="87283-295">MyApp\Pipeline\Contracts</span></span>|  
    |<span data-ttu-id="87283-296">Calc1Host</span><span class="sxs-lookup"><span data-stu-id="87283-296">Calc1Host</span></span>|<span data-ttu-id="87283-297">Uygulamam</span><span class="sxs-lookup"><span data-stu-id="87283-297">MyApp</span></span>|  
    |<span data-ttu-id="87283-298">Calc1HostSideAdapter</span><span class="sxs-lookup"><span data-stu-id="87283-298">Calc1HostSideAdapter</span></span>|<span data-ttu-id="87283-299">MyApp\Pipeline\HostSideAdapters</span><span class="sxs-lookup"><span data-stu-id="87283-299">MyApp\Pipeline\HostSideAdapters</span></span>|  
    |<span data-ttu-id="87283-300">Calc1HVA</span><span class="sxs-lookup"><span data-stu-id="87283-300">Calc1HVA</span></span>|<span data-ttu-id="87283-301">Uygulamam</span><span class="sxs-lookup"><span data-stu-id="87283-301">MyApp</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="87283-302">İşlem hattı klasör yapınız, uygulama klasörünüzdeki dışındaki bir konuma koymak karar verirseniz buna göre tabloda gösterilen yolları değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="87283-302">If you decided to put your pipeline folder structure in a location other than your application folder, you must modify the paths shown in the table accordingly.</span></span> <span data-ttu-id="87283-303">İşlem hattı dizin gereksinimleri bkz [ardışık düzen geliştirme gereksinimleri](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span><span class="sxs-lookup"><span data-stu-id="87283-303">See the discussion of pipeline directory requirements in [Pipeline Development Requirements](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span></span>  
  
2.  <span data-ttu-id="87283-304">Visual Studio çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="87283-304">Build the Visual Studio solution.</span></span>  
  
3.  <span data-ttu-id="87283-305">Derlemeler için doğru dizinleri kopyalanan ve hiçbir ek derlemeler kopyalarını yanlış klasörlerinde yüklenen emin olmak için uygulama ve işlem hattı dizinleri denetleyin.</span><span class="sxs-lookup"><span data-stu-id="87283-305">Check the application and pipeline directories to ensure that the assemblies were copied to the correct directories and that no extra copies of assemblies were installed in the wrong folders.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="87283-306">Değişmedi, **Yereli Kopyala** için **False** için `Calc1AddInView` proje başvurusu `AddInCalcV1` proje, yükleyici bağlamı sorunları engeller eklenti bulunan öğesinden.</span><span class="sxs-lookup"><span data-stu-id="87283-306">If you did not change **Copy Local** to **False** for the `Calc1AddInView` project reference in the `AddInCalcV1` project, loader context problems will prevent the add-in from being located.</span></span>  
  
     <span data-ttu-id="87283-307">İşlem hattına dağıtma hakkında daha fazla bilgi için bkz: [ardışık düzen geliştirme gereksinimleri](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span><span class="sxs-lookup"><span data-stu-id="87283-307">For information about deploying to the pipeline, see [Pipeline Development Requirements](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).</span></span>  
  
## <a name="running-the-host-application"></a><span data-ttu-id="87283-308">Konak uygulama çalıştırma</span><span class="sxs-lookup"><span data-stu-id="87283-308">Running the Host Application</span></span>  
 <span data-ttu-id="87283-309">Konak çalıştırın ve eklentisi ile etkileşim kurmak artık hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="87283-309">You are now ready to run the host and interact with the add-in.</span></span>  
  
#### <a name="to-run-the-host-application"></a><span data-ttu-id="87283-310">Ana bilgisayar uygulamasını çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="87283-310">To run the host application</span></span>  
  
1.  <span data-ttu-id="87283-311">Komut isteminde, uygulama dizinine gidin ve ana bilgisayar uygulaması çalıştırın `Calc1Host.exe`.</span><span class="sxs-lookup"><span data-stu-id="87283-311">At the command prompt, go to the application directory and run the host application, `Calc1Host.exe`.</span></span>  
  
2.  <span data-ttu-id="87283-312">Konak, tüm kullanılabilir eklentiler türüne bulur ve eklenti seçmenizi ister.</span><span class="sxs-lookup"><span data-stu-id="87283-312">The host finds all available add-ins of its type and prompts you to select an add-in.</span></span> <span data-ttu-id="87283-313">Girin **1** için yalnızca eklenti.</span><span class="sxs-lookup"><span data-stu-id="87283-313">Enter **1** for the only available add-in.</span></span>  
  
3.  <span data-ttu-id="87283-314">Hesap makinesi için bir eşitlik girin; örn **2 + 2**.</span><span class="sxs-lookup"><span data-stu-id="87283-314">Enter an equation for the calculator, such as **2 + 2**.</span></span> <span data-ttu-id="87283-315">Sayılar ve işleci arasında boşluk olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="87283-315">There must be spaces between the numbers and the operator.</span></span>  
  
4.  <span data-ttu-id="87283-316">Tür **çıkmak** basın **Enter** uygulamayı kapatmak için anahtar.</span><span class="sxs-lookup"><span data-stu-id="87283-316">Type **exit** and press the **Enter** key to close the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87283-317">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="87283-317">See Also</span></span>  
 [<span data-ttu-id="87283-318">İzlenecek yol: Ana bilgisayarınız değiştiğinde geriye dönük uyumluluğu etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="87283-318">Walkthrough: Enabling Backward Compatibility as Your Host Changes</span></span>](https://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848)  
 [<span data-ttu-id="87283-319">İzlenecek yol: Ana bilgisayarlar ve eklentiler arasında geçirme koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="87283-319">Walkthrough: Passing Collections Between Hosts and Add-Ins</span></span>](https://msdn.microsoft.com/library/b532c604-548e-4fab-b11c-377257dd0ee5)  
 [<span data-ttu-id="87283-320">Ardışık Düzen geliştirme gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="87283-320">Pipeline Development Requirements</span></span>](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5)  
 [<span data-ttu-id="87283-321">Sözleşmeler, görünümler ve bağdaştırıcılar</span><span class="sxs-lookup"><span data-stu-id="87283-321">Contracts, Views, and Adapters</span></span>](https://msdn.microsoft.com/library/a6460173-9507-4b87-8c07-d4ee245d715c)  
 [<span data-ttu-id="87283-322">İşlem Hattı Geliştirme</span><span class="sxs-lookup"><span data-stu-id="87283-322">Pipeline Development</span></span>](../../../docs/framework/add-ins/pipeline-development.md)
