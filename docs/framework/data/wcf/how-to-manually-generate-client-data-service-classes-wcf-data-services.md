---
title: 'Nasıl yapılır: Istemci veri hizmeti sınıflarını el ile oluştur (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, client library
ms.assetid: b98cb1d6-956a-4e50-add6-67e4f2587346
ms.openlocfilehash: 2a827e4909b18d9cca74fc20a2d83d2730ea0cd9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952291"
---
# <a name="how-to-manually-generate-client-data-service-classes-wcf-data-services"></a><span data-ttu-id="64bf4-102">Nasıl yapılır: Istemci veri hizmeti sınıflarını el ile oluştur (WCF Veri Hizmetleri)</span><span class="sxs-lookup"><span data-stu-id="64bf4-102">How to: Manually Generate Client Data Service Classes (WCF Data Services)</span></span>
<span data-ttu-id="64bf4-103">WCF Veri Hizmetleri, Visual Studio projesindeki bir veri hizmetine bir başvuru eklemek için **hizmet başvurusu Ekle** iletişim kutusunu kullandığınızda istemci veri hizmeti sınıflarını otomatik olarak oluşturmanıza olanak tanımak üzere Visual Studio ile tümleşir.</span><span class="sxs-lookup"><span data-stu-id="64bf4-103">WCF Data Services integrates with Visual Studio to enable you to automatically generate client data service classes when you use the **Add Service Reference** dialog box to add a reference to a data service in a Visual Studio project.</span></span> <span data-ttu-id="64bf4-104">Daha fazla bilgi için [nasıl yapılır: Veri hizmeti başvurusu](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)ekleyin.</span><span class="sxs-lookup"><span data-stu-id="64bf4-104">For more information, see [How to: Add a Data Service Reference](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).</span></span> <span data-ttu-id="64bf4-105">Ayrıca, `DataSvcUtil.exe`kod oluşturma aracını kullanarak aynı istemci veri hizmeti sınıflarını el ile oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="64bf4-105">You can also manually generate the same client data service classes by using the code-generation tool, `DataSvcUtil.exe`.</span></span> <span data-ttu-id="64bf4-106">WCF Veri Hizmetleri ile birlikte bulunan bu araç, veri hizmeti tanımından .NET Framework sınıfları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="64bf4-106">This tool, which is included with WCF Data Services, generates .NET Framework classes from the data service definition.</span></span> <span data-ttu-id="64bf4-107">Ayrıca, kavramsal model (. csdl) dosyasından ve Visual Studio projesindeki bir Entity Framework modeli temsil eden. edmx dosyasından veri hizmeti sınıfları oluşturmak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="64bf4-107">It can also be used to generate data service classes from the conceptual model (.csdl) file and from the .edmx file that represents an Entity Framework model in a Visual Studio project.</span></span>

 <span data-ttu-id="64bf4-108">Bu konudaki örnek, Northwind örnek veri hizmeti temel alınarak istemci veri hizmeti sınıfları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="64bf4-108">The example in this topic creates client data service classes based on the Northwind sample data service.</span></span> <span data-ttu-id="64bf4-109">Bu hizmet, [WCF veri hizmetleri hızlı](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)başlangıcı 'nı tamamladığınızda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="64bf4-109">This service is created when you complete the [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span> <span data-ttu-id="64bf4-110">Bu konudaki bazı örneklerde, Northwind modeli için kavramsal model dosyası gereklidir.</span><span class="sxs-lookup"><span data-stu-id="64bf4-110">Some examples in this topic require the conceptual model file for the Northwind model.</span></span> <span data-ttu-id="64bf4-111">Daha fazla bilgi için [nasıl yapılır: Modeli ve eşleme dosyalarını](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)oluşturmak Için EdmGen. exe ' yi kullanın.</span><span class="sxs-lookup"><span data-stu-id="64bf4-111">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span> <span data-ttu-id="64bf4-112">Bu konudaki bazı örnekler, Northwind modeli için. edmx dosyasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="64bf4-112">Some examples in this topic require the .edmx file for the Northwind model.</span></span> <span data-ttu-id="64bf4-113">Daha fazla bilgi için bkz [. edmx dosyasına genel bakış](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="64bf4-113">For more information, see [.edmx File Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)).</span></span>

### <a name="to-generate-c-classes-that-support-data-binding"></a><span data-ttu-id="64bf4-114">Veri bağlamayı C# destekleyen sınıflar oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="64bf4-114">To generate C# classes that support data binding</span></span>

- <span data-ttu-id="64bf4-115">Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="64bf4-115">At the command prompt, execute the following command without line breaks:</span></span>

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:CSharp /out:Northwind.cs /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    > <span data-ttu-id="64bf4-116">Verilen değeri, Northwind örnek veri hizmeti örneğinizin `/uri:` URI 'siyle parametreye değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="64bf4-116">You must replace the value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>

### <a name="to-generate-visual-basic-classes-that-support-data-binding"></a><span data-ttu-id="64bf4-117">Veri bağlamayı destekleyen Visual Basic sınıfları oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="64bf4-117">To generate Visual Basic classes that support data binding</span></span>

- <span data-ttu-id="64bf4-118">Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="64bf4-118">At the command prompt, execute the following command without line breaks:</span></span>

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    > <span data-ttu-id="64bf4-119">Sağlanan değeri, Northwind örnek veri hizmeti `/uri:` örneğinizin URI 'siyle parametreye değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="64bf4-119">You must replace value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>

### <a name="to-generate-c-classes-based-on-the-service-uri"></a><span data-ttu-id="64bf4-120">Hizmet URI C# 'sini temel alan sınıflar oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="64bf4-120">To generate C# classes based on the service URI</span></span>

- <span data-ttu-id="64bf4-121">Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="64bf4-121">At the command prompt, execute the following command without line breaks:</span></span>

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /language:CSharp /out:northwind.cs /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    > <span data-ttu-id="64bf4-122">Verilen değeri, Northwind örnek veri hizmeti örneğinizin `/uri:` URI 'siyle parametreye değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="64bf4-122">You must replace the value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>

### <a name="to-generate-visual-basic-classes-based-on-the-service-uri"></a><span data-ttu-id="64bf4-123">Hizmet URI 'sini temel alan Visual Basic sınıfları oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="64bf4-123">To generate Visual Basic classes based on the service URI</span></span>

- <span data-ttu-id="64bf4-124">Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="64bf4-124">At the command prompt, execute the following command without line breaks:</span></span>

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    > <span data-ttu-id="64bf4-125">Sağlanan değeri, Northwind örnek veri hizmeti `/uri:` örneğinizin URI 'siyle parametreye değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="64bf4-125">You must replace value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>

### <a name="to-generate-c-classes-based-on-the-conceptual-model-file-csdl"></a><span data-ttu-id="64bf4-126">Kavramsal model C# DOSYASıNA (csdl) göre sınıflar oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="64bf4-126">To generate C# classes based on the conceptual model file (CSDL)</span></span>

- <span data-ttu-id="64bf4-127">Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="64bf4-127">At the command prompt, execute the following command without line breaks:</span></span>

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.csdl /out:Northwind.cs
    ```

### <a name="to-generate-visual-basic-classes-based-on-the-conceptual-model-file-csdl"></a><span data-ttu-id="64bf4-128">Kavramsal model dosyasına (CSDL) göre Visual Basic sınıfları oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="64bf4-128">To generate Visual Basic classes based on the conceptual model file (CSDL)</span></span>

- <span data-ttu-id="64bf4-129">Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="64bf4-129">At the command prompt, execute the following command without line breaks:</span></span>

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.csdl /out:Northwind.vb
    ```

### <a name="to-generate-c-classes-based-on-the-edmx-file"></a><span data-ttu-id="64bf4-130">. Edmx C# dosyasını temel alan sınıflar oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="64bf4-130">To generate C# classes based on the .edmx file</span></span>

- <span data-ttu-id="64bf4-131">Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="64bf4-131">At the command prompt, execute the following command without line breaks:</span></span>

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.edmx /out:c:\northwind.cs
    ```

### <a name="to-generate-visual-basic-classes-based-on-the-edmx-file"></a><span data-ttu-id="64bf4-132">. Edmx dosyasına göre Visual Basic sınıfları oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="64bf4-132">To generate Visual Basic classes based on the .edmx file</span></span>

- <span data-ttu-id="64bf4-133">Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="64bf4-133">At the command prompt, execute the following command without line breaks:</span></span>

    ```
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.edmx /out:c:\northwind.vb
    ```

## <a name="see-also"></a><span data-ttu-id="64bf4-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64bf4-134">See also</span></span>

- [<span data-ttu-id="64bf4-135">Veri Hizmeti İstemci Kitaplığı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="64bf4-135">Generating the Data Service Client Library</span></span>](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)
- [<span data-ttu-id="64bf4-136">Nasıl yapılır: Veri hizmeti başvurusu ekleme</span><span class="sxs-lookup"><span data-stu-id="64bf4-136">How to: Add a Data Service Reference</span></span>](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)
- [<span data-ttu-id="64bf4-137">WCF Veri Hizmeti İstemci Yardımcı Programı (DataSvcUtil.exe)</span><span class="sxs-lookup"><span data-stu-id="64bf4-137">WCF Data Service Client Utility (DataSvcUtil.exe)</span></span>](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md)
