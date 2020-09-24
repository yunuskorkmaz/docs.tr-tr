---
title: 'Nasıl yapılır: Istemci veri hizmeti sınıflarını El Ile oluşturma (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, client library
ms.assetid: b98cb1d6-956a-4e50-add6-67e4f2587346
ms.openlocfilehash: 368f2546652d21be44c0ffb4cc5f279c56beda51
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91165998"
---
# <a name="how-to-manually-generate-client-data-service-classes-wcf-data-services"></a><span data-ttu-id="d3f80-102">Nasıl yapılır: Istemci veri hizmeti sınıflarını El Ile oluşturma (WCF Veri Hizmetleri)</span><span class="sxs-lookup"><span data-stu-id="d3f80-102">How to: Manually Generate Client Data Service Classes (WCF Data Services)</span></span>

<span data-ttu-id="d3f80-103">WCF Veri Hizmetleri, Visual Studio projesindeki bir veri hizmetine bir başvuru eklemek için **hizmet başvurusu Ekle** iletişim kutusunu kullandığınızda istemci veri hizmeti sınıflarını otomatik olarak oluşturmanıza olanak tanımak üzere Visual Studio ile tümleşir.</span><span class="sxs-lookup"><span data-stu-id="d3f80-103">WCF Data Services integrates with Visual Studio to enable you to automatically generate client data service classes when you use the **Add Service Reference** dialog box to add a reference to a data service in a Visual Studio project.</span></span> <span data-ttu-id="d3f80-104">Daha fazla bilgi için bkz. [nasıl yapılır: veri hizmeti başvurusu ekleme](how-to-add-a-data-service-reference-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="d3f80-104">For more information, see [How to: Add a Data Service Reference](how-to-add-a-data-service-reference-wcf-data-services.md).</span></span> <span data-ttu-id="d3f80-105">Ayrıca, kod oluşturma aracını kullanarak aynı istemci veri hizmeti sınıflarını el ile oluşturabilirsiniz `DataSvcUtil.exe` .</span><span class="sxs-lookup"><span data-stu-id="d3f80-105">You can also manually generate the same client data service classes by using the code-generation tool, `DataSvcUtil.exe`.</span></span> <span data-ttu-id="d3f80-106">WCF Veri Hizmetleri ile birlikte bulunan bu araç, veri hizmeti tanımından .NET Framework sınıfları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d3f80-106">This tool, which is included with WCF Data Services, generates .NET Framework classes from the data service definition.</span></span> <span data-ttu-id="d3f80-107">Ayrıca, kavramsal model (. csdl) dosyasından ve Visual Studio projesindeki bir Entity Framework modeli temsil eden. edmx dosyasından veri hizmeti sınıfları oluşturmak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d3f80-107">It can also be used to generate data service classes from the conceptual model (.csdl) file and from the .edmx file that represents an Entity Framework model in a Visual Studio project.</span></span>

 <span data-ttu-id="d3f80-108">Bu konudaki örnek, Northwind örnek veri hizmeti temel alınarak istemci veri hizmeti sınıfları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d3f80-108">The example in this topic creates client data service classes based on the Northwind sample data service.</span></span> <span data-ttu-id="d3f80-109">Bu hizmet, [WCF veri hizmetleri hızlı](quickstart-wcf-data-services.md)başlangıcı 'nı tamamladığınızda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d3f80-109">This service is created when you complete the [WCF Data Services quickstart](quickstart-wcf-data-services.md).</span></span> <span data-ttu-id="d3f80-110">Bu konudaki bazı örneklerde, Northwind modeli için kavramsal model dosyası gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d3f80-110">Some examples in this topic require the conceptual model file for the Northwind model.</span></span> <span data-ttu-id="d3f80-111">Daha fazla bilgi için bkz. [nasıl yapılır: model ve eşleme dosyalarını oluşturmak için EdmGen.exe kullanma](../adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="d3f80-111">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span> <span data-ttu-id="d3f80-112">Bu konudaki bazı örnekler, Northwind modeli için. edmx dosyasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d3f80-112">Some examples in this topic require the .edmx file for the Northwind model.</span></span> <span data-ttu-id="d3f80-113">Daha fazla bilgi için bkz [.. edmx dosyasına genel bakış](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="d3f80-113">For more information, see [.edmx File Overview](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)).</span></span>

### <a name="to-generate-c-classes-that-support-data-binding"></a><span data-ttu-id="d3f80-114">Veri bağlamayı destekleyen C# sınıfları oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d3f80-114">To generate C# classes that support data binding</span></span>

- <span data-ttu-id="d3f80-115">Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="d3f80-115">At the command prompt, execute the following command without line breaks:</span></span>

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:CSharp /out:Northwind.cs /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    > <span data-ttu-id="d3f80-116">Verilen değeri, `/uri:` Northwind örnek veri hizmeti ÖRNEĞINIZIN URI 'siyle parametreye değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="d3f80-116">You must replace the value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>

### <a name="to-generate-visual-basic-classes-that-support-data-binding"></a><span data-ttu-id="d3f80-117">Veri bağlamayı destekleyen Visual Basic sınıfları oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d3f80-117">To generate Visual Basic classes that support data binding</span></span>

- <span data-ttu-id="d3f80-118">Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="d3f80-118">At the command prompt, execute the following command without line breaks:</span></span>

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    > <span data-ttu-id="d3f80-119">Sağlanan değeri, `/uri:` Northwind örnek veri hizmeti ÖRNEĞINIZIN URI 'siyle parametreye değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="d3f80-119">You must replace value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>

### <a name="to-generate-c-classes-based-on-the-service-uri"></a><span data-ttu-id="d3f80-120">Hizmet URI 'sini temel alan C# sınıfları oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d3f80-120">To generate C# classes based on the service URI</span></span>

- <span data-ttu-id="d3f80-121">Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="d3f80-121">At the command prompt, execute the following command without line breaks:</span></span>

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /language:CSharp /out:northwind.cs /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    > <span data-ttu-id="d3f80-122">Verilen değeri, `/uri:` Northwind örnek veri hizmeti ÖRNEĞINIZIN URI 'siyle parametreye değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="d3f80-122">You must replace the value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>

### <a name="to-generate-visual-basic-classes-based-on-the-service-uri"></a><span data-ttu-id="d3f80-123">Hizmet URI 'sini temel alan Visual Basic sınıfları oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d3f80-123">To generate Visual Basic classes based on the service URI</span></span>

- <span data-ttu-id="d3f80-124">Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="d3f80-124">At the command prompt, execute the following command without line breaks:</span></span>

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    > <span data-ttu-id="d3f80-125">Sağlanan değeri, `/uri:` Northwind örnek veri hizmeti ÖRNEĞINIZIN URI 'siyle parametreye değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="d3f80-125">You must replace value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>

### <a name="to-generate-c-classes-based-on-the-conceptual-model-file-csdl"></a><span data-ttu-id="d3f80-126">Kavramsal model dosyasına (CSDL) göre C# sınıfları oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d3f80-126">To generate C# classes based on the conceptual model file (CSDL)</span></span>

- <span data-ttu-id="d3f80-127">Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="d3f80-127">At the command prompt, execute the following command without line breaks:</span></span>

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.csdl /out:Northwind.cs
    ```

### <a name="to-generate-visual-basic-classes-based-on-the-conceptual-model-file-csdl"></a><span data-ttu-id="d3f80-128">Kavramsal model dosyasına (CSDL) göre Visual Basic sınıfları oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d3f80-128">To generate Visual Basic classes based on the conceptual model file (CSDL)</span></span>

- <span data-ttu-id="d3f80-129">Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="d3f80-129">At the command prompt, execute the following command without line breaks:</span></span>

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.csdl /out:Northwind.vb
    ```

### <a name="to-generate-c-classes-based-on-the-edmx-file"></a><span data-ttu-id="d3f80-130">. Edmx dosyasını temel alan C# sınıfları oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d3f80-130">To generate C# classes based on the .edmx file</span></span>

- <span data-ttu-id="d3f80-131">Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="d3f80-131">At the command prompt, execute the following command without line breaks:</span></span>

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.edmx /out:c:\northwind.cs
    ```

### <a name="to-generate-visual-basic-classes-based-on-the-edmx-file"></a><span data-ttu-id="d3f80-132">. Edmx dosyasına göre Visual Basic sınıfları oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d3f80-132">To generate Visual Basic classes based on the .edmx file</span></span>

- <span data-ttu-id="d3f80-133">Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="d3f80-133">At the command prompt, execute the following command without line breaks:</span></span>

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.edmx /out:c:\northwind.vb
    ```

## <a name="see-also"></a><span data-ttu-id="d3f80-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3f80-134">See also</span></span>

- [<span data-ttu-id="d3f80-135">Veri Hizmeti İstemci Kitaplığı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d3f80-135">Generating the Data Service Client Library</span></span>](generating-the-data-service-client-library-wcf-data-services.md)
- [<span data-ttu-id="d3f80-136">Nasıl yapılır: Veri Hizmeti Başvurusu Ekleme</span><span class="sxs-lookup"><span data-stu-id="d3f80-136">How to: Add a Data Service Reference</span></span>](how-to-add-a-data-service-reference-wcf-data-services.md)
- [<span data-ttu-id="d3f80-137">WCF Veri Hizmeti İstemci Yardımcı Programı (DataSvcUtil.exe)</span><span class="sxs-lookup"><span data-stu-id="d3f80-137">WCF Data Service Client Utility (DataSvcUtil.exe)</span></span>](wcf-data-service-client-utility-datasvcutil-exe.md)
