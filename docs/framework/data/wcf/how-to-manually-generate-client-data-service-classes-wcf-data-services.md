---
title: "Nasıl yapılır: istemci verileri hizmet sınıfları (WCF Veri Hizmetleri) el ile oluştur"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, client library
ms.assetid: b98cb1d6-956a-4e50-add6-67e4f2587346
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f72f898b2a80d7d88a74deabe013e2eecc298bdd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-manually-generate-client-data-service-classes-wcf-data-services"></a><span data-ttu-id="e0041-102">Nasıl yapılır: istemci verileri hizmet sınıfları (WCF Veri Hizmetleri) el ile oluştur</span><span class="sxs-lookup"><span data-stu-id="e0041-102">How to: Manually Generate Client Data Service Classes (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="e0041-103">İstemci veri hizmeti sınıfları kullandığınızda otomatik olarak oluşturmak üzere etkinleştirmek için Visual Studio ile tümleşir **hizmet Başvurusu Ekle** bir başvuru veri hizmeti için bir Visual Studio projesi eklemek için iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="e0041-103"> integrates with Visual Studio to enable you to automatically generate client data service classes when you use the **Add Service Reference** dialog box to add a reference to a data service in a Visual Studio project.</span></span> <span data-ttu-id="e0041-104">Daha fazla bilgi için bkz: [nasıl yapılır: bir veri hizmet Başvurusu Ekle](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="e0041-104">For more information, see [How to: Add a Data Service Reference](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).</span></span> <span data-ttu-id="e0041-105">Kod oluşturma aracı kullanarak el ile de aynı istemci veri hizmeti sınıfları oluşturabilirsiniz `DataSvcUtil.exe`.</span><span class="sxs-lookup"><span data-stu-id="e0041-105">You can also manually generate the same client data service classes by using the code-generation tool, `DataSvcUtil.exe`.</span></span> <span data-ttu-id="e0041-106">Bu araç ile birlikte [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], .NET Framework sınıfları veri hizmeti tanımı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e0041-106">This tool, which is included with [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], generates .NET Framework classes from the data service definition.</span></span> <span data-ttu-id="e0041-107">Ayrıca, kavramsal model (.csdl) dosyası ve bir Visual Studio projesi Entity Framework modelinde temsil eden .edmx dosyasının'ndan veri hizmeti sınıfları oluşturmak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e0041-107">It can also be used to generate data service classes from the conceptual model (.csdl) file and from the .edmx file that represents an Entity Framework model in a Visual Studio project.</span></span>  
  
 <span data-ttu-id="e0041-108">Bu konudaki örnek Northwind örnek veri hizmetini temel alan istemci veri hizmeti sınıfları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e0041-108">The example in this topic creates client data service classes based on the Northwind sample data service.</span></span> <span data-ttu-id="e0041-109">Bu hizmeti tamamladığınızda oluşturulan [WCF Veri Hizmetleri quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="e0041-109">This service is created when you complete the [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span> <span data-ttu-id="e0041-110">Bu konudaki bazı örnekler Northwind modeli için kavramsal model dosyası gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e0041-110">Some examples in this topic require the conceptual model file for the Northwind model.</span></span> <span data-ttu-id="e0041-111">Daha fazla bilgi için bkz: [nasıl yapılır: dosya eşleme ve Model oluşturmak için kullanım EdmGen.exe](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="e0041-111">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span> <span data-ttu-id="e0041-112">Bu konudaki bazı örnekler için Northwind modeli .edmx dosyasının gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e0041-112">Some examples in this topic require the .edmx file for the Northwind model.</span></span> <span data-ttu-id="e0041-113">Daha fazla bilgi için bkz: [.edmx dosyasının genel bakış](http://msdn.microsoft.com/en-us/f4c8e7ce-1db6-417e-9759-15f8b55155d4).</span><span class="sxs-lookup"><span data-stu-id="e0041-113">For more information, see [.edmx File Overview](http://msdn.microsoft.com/en-us/f4c8e7ce-1db6-417e-9759-15f8b55155d4).</span></span>  
  
### <a name="to-generate-c-classes-that-support-data-binding"></a><span data-ttu-id="e0041-114">Veri bağlamayı destekleyen C# sınıfları oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e0041-114">To generate C# classes that support data binding</span></span>  
  
-   <span data-ttu-id="e0041-115">Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="e0041-115">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:CSharp /out:Northwind.cs /uri:http://localhost:12345/Northwind.svc  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="e0041-116">İçin sağlanan değer değiştirmelisiniz `/uri:` Northwind örnek veri hizmeti örneğiniz URI'sini parametresiyle.</span><span class="sxs-lookup"><span data-stu-id="e0041-116">You must replace the value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>  
  
### <a name="to-generate-visual-basic-classes-that-support-data-binding"></a><span data-ttu-id="e0041-117">Veri bağlamayı destekleyen Visual Basic sınıfları oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e0041-117">To generate Visual Basic classes that support data binding</span></span>  
  
-   <span data-ttu-id="e0041-118">Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="e0041-118">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="e0041-119">İçin sağlanan değer değiştirmelisiniz `/uri:` Northwind örnek veri hizmeti örneğiniz URI'sini parametresiyle.</span><span class="sxs-lookup"><span data-stu-id="e0041-119">You must replace value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>  
  
### <a name="to-generate-c-classes-based-on-the-service-uri"></a><span data-ttu-id="e0041-120">Hizmet URI'si temel C# sınıfları oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e0041-120">To generate C# classes based on the service URI</span></span>  
  
-   <span data-ttu-id="e0041-121">Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="e0041-121">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /language:CSharp /out:northwind.cs /uri:http://localhost:12345/Northwind.svc  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="e0041-122">İçin sağlanan değer değiştirmelisiniz `/uri:` Northwind örnek veri hizmeti örneğiniz URI'sini parametresiyle.</span><span class="sxs-lookup"><span data-stu-id="e0041-122">You must replace the value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>  
  
### <a name="to-generate-visual-basic-classes-based-on-the-service-uri"></a><span data-ttu-id="e0041-123">Visual Basic sınıfları URI hizmetini temel alan oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e0041-123">To generate Visual Basic classes based on the service URI</span></span>  
  
-   <span data-ttu-id="e0041-124">Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="e0041-124">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="e0041-125">İçin sağlanan değer değiştirmelisiniz `/uri:` Northwind örnek veri hizmeti örneğiniz URI'sini parametresiyle.</span><span class="sxs-lookup"><span data-stu-id="e0041-125">You must replace value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>  
  
### <a name="to-generate-c-classes-based-on-the-conceptual-model-file-csdl"></a><span data-ttu-id="e0041-126">Kavramsal model dosyasını (CSDL) temel alan C# sınıfları oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e0041-126">To generate C# classes based on the conceptual model file (CSDL)</span></span>  
  
-   <span data-ttu-id="e0041-127">Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="e0041-127">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.csdl /out:Northwind.cs  
    ```  
  
### <a name="to-generate-visual-basic-classes-based-on-the-conceptual-model-file-csdl"></a><span data-ttu-id="e0041-128">Visual Basic sınıfları kavramsal model dosyasını (CSDL) temel alan oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e0041-128">To generate Visual Basic classes based on the conceptual model file (CSDL)</span></span>  
  
-   <span data-ttu-id="e0041-129">Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="e0041-129">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.csdl /out:Northwind.vb  
    ```  
  
### <a name="to-generate-c-classes-based-on-the-edmx-file"></a><span data-ttu-id="e0041-130">.Edmx dosyasını temel alarak C# sınıfları oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e0041-130">To generate C# classes based on the .edmx file</span></span>  
  
-   <span data-ttu-id="e0041-131">Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="e0041-131">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.edmx /out:c:\northwind.cs   
    ```  
  
### <a name="to-generate-visual-basic-classes-based-on-the-edmx-file"></a><span data-ttu-id="e0041-132">Visual Basic sınıfları .edmx dosyasını temel alan oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e0041-132">To generate Visual Basic classes based on the .edmx file</span></span>  
  
-   <span data-ttu-id="e0041-133">Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="e0041-133">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.edmx /out:c:\northwind.vb   
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e0041-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e0041-134">See Also</span></span>  
 [<span data-ttu-id="e0041-135">Veri Hizmeti İstemci Kitaplığı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e0041-135">Generating the Data Service Client Library</span></span>](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)  
 [<span data-ttu-id="e0041-136">Nasıl yapılır: Veri Hizmeti Başvurusu Ekleme</span><span class="sxs-lookup"><span data-stu-id="e0041-136">How to: Add a Data Service Reference</span></span>](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)  
 [<span data-ttu-id="e0041-137">WCF Veri Hizmeti İstemci Yardımcı Programı (DataSvcUtil.exe)</span><span class="sxs-lookup"><span data-stu-id="e0041-137">WCF Data Service Client Utility (DataSvcUtil.exe)</span></span>](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md)
