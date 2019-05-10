---
title: 'Nasıl yapılır: İstemci veri hizmeti sınıfları (WCF Veri Hizmetleri) el ile oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, client library
ms.assetid: b98cb1d6-956a-4e50-add6-67e4f2587346
ms.openlocfilehash: 86cf9a622f244fd6ea13113310eb05f65da1463f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645607"
---
# <a name="how-to-manually-generate-client-data-service-classes-wcf-data-services"></a><span data-ttu-id="e013e-102">Nasıl yapılır: İstemci veri hizmeti sınıfları (WCF Veri Hizmetleri) el ile oluşturma</span><span class="sxs-lookup"><span data-stu-id="e013e-102">How to: Manually Generate Client Data Service Classes (WCF Data Services)</span></span>
<span data-ttu-id="e013e-103">WCF veri hizmetleri sağlamak kullandığınızda istemci veri hizmeti sınıfları otomatik olarak oluşturmak Visual Studio ile tümleştirilir **hizmet Başvurusu Ekle** bir Visual Studio projenize bir veri hizmetine başvuru eklemek için iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="e013e-103">WCF Data Services integrates with Visual Studio to enable you to automatically generate client data service classes when you use the **Add Service Reference** dialog box to add a reference to a data service in a Visual Studio project.</span></span> <span data-ttu-id="e013e-104">Daha fazla bilgi için [nasıl yapılır: Bir veri hizmeti başvurusu ekleme](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="e013e-104">For more information, see [How to: Add a Data Service Reference](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).</span></span> <span data-ttu-id="e013e-105">Kod oluşturma aracı kullanılarak el ile de aynı istemci veri hizmeti sınıfları oluşturabilirsiniz `DataSvcUtil.exe`.</span><span class="sxs-lookup"><span data-stu-id="e013e-105">You can also manually generate the same client data service classes by using the code-generation tool, `DataSvcUtil.exe`.</span></span> <span data-ttu-id="e013e-106">WCF Veri Hizmetleri ile birlikte, bu aracı, veri hizmeti tanımından .NET Framework sınıfları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e013e-106">This tool, which is included with WCF Data Services, generates .NET Framework classes from the data service definition.</span></span> <span data-ttu-id="e013e-107">Veri Hizmeti sınıfları kavramsal model (.csdl) dosyası ve bir Visual Studio projesinde bir Entity Framework modelini temsil eden .edmx dosyası üretmek için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e013e-107">It can also be used to generate data service classes from the conceptual model (.csdl) file and from the .edmx file that represents an Entity Framework model in a Visual Studio project.</span></span>

 <span data-ttu-id="e013e-108">Bu konudaki örnek Northwind örnek veri hizmetini temel alan istemci veri hizmeti sınıfları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e013e-108">The example in this topic creates client data service classes based on the Northwind sample data service.</span></span> <span data-ttu-id="e013e-109">Bu hizmet, tamamladığınızda oluşturulur [WCF Veri Hizmetleri Hızlı Başlangıç](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="e013e-109">This service is created when you complete the [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span> <span data-ttu-id="e013e-110">Bu konudaki örnekler için Northwind modeli kavramsal model dosyası gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e013e-110">Some examples in this topic require the conceptual model file for the Northwind model.</span></span> <span data-ttu-id="e013e-111">Daha fazla bilgi için [nasıl yapılır: Model ve eşleme dosyalarını üretmek için Edmgen.exe'yi kullanın](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="e013e-111">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span> <span data-ttu-id="e013e-112">Bu konudaki örnekler için Northwind modeli .edmx dosyası gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e013e-112">Some examples in this topic require the .edmx file for the Northwind model.</span></span> <span data-ttu-id="e013e-113">Daha fazla bilgi için [.edmx dosyasını genel bakış](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="e013e-113">For more information, see [.edmx File Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)).</span></span>

### <a name="to-generate-c-classes-that-support-data-binding"></a><span data-ttu-id="e013e-114">Veri bağlamayı destekleyen C# sınıfları oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e013e-114">To generate C# classes that support data binding</span></span>

- <span data-ttu-id="e013e-115">Komut isteminde satır sonları olmadan aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="e013e-115">At the command prompt, execute the following command without line breaks:</span></span>

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:CSharp /out:Northwind.cs /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    >  <span data-ttu-id="e013e-116">İçin sağlanan değer değiştirmelisiniz `/uri:` Northwind örnek veri hizmeti örneğinizi URI parametresiyle.</span><span class="sxs-lookup"><span data-stu-id="e013e-116">You must replace the value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>

### <a name="to-generate-visual-basic-classes-that-support-data-binding"></a><span data-ttu-id="e013e-117">Veri bağlamayı destekleyen Visual Basic sınıfları oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e013e-117">To generate Visual Basic classes that support data binding</span></span>

- <span data-ttu-id="e013e-118">Komut isteminde satır sonları olmadan aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="e013e-118">At the command prompt, execute the following command without line breaks:</span></span>

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    >  <span data-ttu-id="e013e-119">Sağlanan değer değiştirmelisiniz `/uri:` Northwind örnek veri hizmeti örneğinizi URI parametresiyle.</span><span class="sxs-lookup"><span data-stu-id="e013e-119">You must replace value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>

### <a name="to-generate-c-classes-based-on-the-service-uri"></a><span data-ttu-id="e013e-120">Hizmet URI'si temel C# sınıfları oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e013e-120">To generate C# classes based on the service URI</span></span>

- <span data-ttu-id="e013e-121">Komut isteminde satır sonları olmadan aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="e013e-121">At the command prompt, execute the following command without line breaks:</span></span>

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /language:CSharp /out:northwind.cs /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    >  <span data-ttu-id="e013e-122">İçin sağlanan değer değiştirmelisiniz `/uri:` Northwind örnek veri hizmeti örneğinizi URI parametresiyle.</span><span class="sxs-lookup"><span data-stu-id="e013e-122">You must replace the value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>

### <a name="to-generate-visual-basic-classes-based-on-the-service-uri"></a><span data-ttu-id="e013e-123">Visual Basic sınıf tabanlı hizmet URI'si oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e013e-123">To generate Visual Basic classes based on the service URI</span></span>

- <span data-ttu-id="e013e-124">Komut isteminde satır sonları olmadan aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="e013e-124">At the command prompt, execute the following command without line breaks:</span></span>

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    >  <span data-ttu-id="e013e-125">Sağlanan değer değiştirmelisiniz `/uri:` Northwind örnek veri hizmeti örneğinizi URI parametresiyle.</span><span class="sxs-lookup"><span data-stu-id="e013e-125">You must replace value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>

### <a name="to-generate-c-classes-based-on-the-conceptual-model-file-csdl"></a><span data-ttu-id="e013e-126">Kavramsal model dosyasını (CSDL) temel alan C# sınıfları oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e013e-126">To generate C# classes based on the conceptual model file (CSDL)</span></span>

- <span data-ttu-id="e013e-127">Komut isteminde satır sonları olmadan aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="e013e-127">At the command prompt, execute the following command without line breaks:</span></span>

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.csdl /out:Northwind.cs
    ```

### <a name="to-generate-visual-basic-classes-based-on-the-conceptual-model-file-csdl"></a><span data-ttu-id="e013e-128">Kavramsal model dosyasını (CSDL) temel alan Visual Basic sınıflar oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e013e-128">To generate Visual Basic classes based on the conceptual model file (CSDL)</span></span>

- <span data-ttu-id="e013e-129">Komut isteminde satır sonları olmadan aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="e013e-129">At the command prompt, execute the following command without line breaks:</span></span>

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.csdl /out:Northwind.vb
    ```

### <a name="to-generate-c-classes-based-on-the-edmx-file"></a><span data-ttu-id="e013e-130">.Edmx dosyasını temel alan C# sınıfları oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e013e-130">To generate C# classes based on the .edmx file</span></span>

- <span data-ttu-id="e013e-131">Komut isteminde satır sonları olmadan aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="e013e-131">At the command prompt, execute the following command without line breaks:</span></span>

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.edmx /out:c:\northwind.cs
    ```

### <a name="to-generate-visual-basic-classes-based-on-the-edmx-file"></a><span data-ttu-id="e013e-132">.Edmx dosyasını temel alan Visual Basic sınıflar oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e013e-132">To generate Visual Basic classes based on the .edmx file</span></span>

- <span data-ttu-id="e013e-133">Komut isteminde satır sonları olmadan aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="e013e-133">At the command prompt, execute the following command without line breaks:</span></span>

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.edmx /out:c:\northwind.vb
    ```

## <a name="see-also"></a><span data-ttu-id="e013e-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e013e-134">See also</span></span>

- [<span data-ttu-id="e013e-135">Veri Hizmeti İstemci Kitaplığı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e013e-135">Generating the Data Service Client Library</span></span>](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)
- [<span data-ttu-id="e013e-136">Nasıl yapılır: Bir veri hizmeti başvurusu ekleme</span><span class="sxs-lookup"><span data-stu-id="e013e-136">How to: Add a Data Service Reference</span></span>](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)
- [<span data-ttu-id="e013e-137">WCF Veri Hizmeti İstemci Yardımcı Programı (DataSvcUtil.exe)</span><span class="sxs-lookup"><span data-stu-id="e013e-137">WCF Data Service Client Utility (DataSvcUtil.exe)</span></span>](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md)