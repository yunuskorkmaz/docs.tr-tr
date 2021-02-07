---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: El Ile Istemci veri hizmeti sınıfları oluşturma (WCF Veri Hizmetleri)'
title: 'Nasıl yapılır: Istemci veri hizmeti sınıflarını El Ile oluşturma (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, client library
ms.assetid: b98cb1d6-956a-4e50-add6-67e4f2587346
ms.openlocfilehash: 6fe878e1177055540a29fb84252eddaa4d97e536
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99765210"
---
# <a name="how-to-manually-generate-client-data-service-classes-wcf-data-services"></a><span data-ttu-id="6962a-103">Nasıl yapılır: Istemci veri hizmeti sınıflarını El Ile oluşturma (WCF Veri Hizmetleri)</span><span class="sxs-lookup"><span data-stu-id="6962a-103">How to: Manually Generate Client Data Service Classes (WCF Data Services)</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="6962a-104">WCF Veri Hizmetleri, Visual Studio projesindeki bir veri hizmetine bir başvuru eklemek için **hizmet başvurusu Ekle** iletişim kutusunu kullandığınızda istemci veri hizmeti sınıflarını otomatik olarak oluşturmanıza olanak tanımak üzere Visual Studio ile tümleşir.</span><span class="sxs-lookup"><span data-stu-id="6962a-104">WCF Data Services integrates with Visual Studio to enable you to automatically generate client data service classes when you use the **Add Service Reference** dialog box to add a reference to a data service in a Visual Studio project.</span></span> <span data-ttu-id="6962a-105">Daha fazla bilgi için bkz. [nasıl yapılır: veri hizmeti başvurusu ekleme](how-to-add-a-data-service-reference-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="6962a-105">For more information, see [How to: Add a Data Service Reference](how-to-add-a-data-service-reference-wcf-data-services.md).</span></span> <span data-ttu-id="6962a-106">Ayrıca, kod oluşturma aracını kullanarak aynı istemci veri hizmeti sınıflarını el ile oluşturabilirsiniz `DataSvcUtil.exe` .</span><span class="sxs-lookup"><span data-stu-id="6962a-106">You can also manually generate the same client data service classes by using the code-generation tool, `DataSvcUtil.exe`.</span></span> <span data-ttu-id="6962a-107">WCF Veri Hizmetleri ile birlikte bulunan bu araç, veri hizmeti tanımından .NET Framework sınıfları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6962a-107">This tool, which is included with WCF Data Services, generates .NET Framework classes from the data service definition.</span></span> <span data-ttu-id="6962a-108">Ayrıca, kavramsal model (. csdl) dosyasından ve Visual Studio projesindeki bir Entity Framework modeli temsil eden. edmx dosyasından veri hizmeti sınıfları oluşturmak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6962a-108">It can also be used to generate data service classes from the conceptual model (.csdl) file and from the .edmx file that represents an Entity Framework model in a Visual Studio project.</span></span>

 <span data-ttu-id="6962a-109">Bu konudaki örnek, Northwind örnek veri hizmeti temel alınarak istemci veri hizmeti sınıfları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6962a-109">The example in this topic creates client data service classes based on the Northwind sample data service.</span></span> <span data-ttu-id="6962a-110">Bu hizmet, [WCF veri hizmetleri hızlı](quickstart-wcf-data-services.md)başlangıcı 'nı tamamladığınızda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6962a-110">This service is created when you complete the [WCF Data Services quickstart](quickstart-wcf-data-services.md).</span></span> <span data-ttu-id="6962a-111">Bu konudaki bazı örneklerde, Northwind modeli için kavramsal model dosyası gereklidir.</span><span class="sxs-lookup"><span data-stu-id="6962a-111">Some examples in this topic require the conceptual model file for the Northwind model.</span></span> <span data-ttu-id="6962a-112">Daha fazla bilgi için bkz. [nasıl yapılır: model ve eşleme dosyalarını oluşturmak için EdmGen.exe kullanma](../adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="6962a-112">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span> <span data-ttu-id="6962a-113">Bu konudaki bazı örnekler, Northwind modeli için. edmx dosyasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="6962a-113">Some examples in this topic require the .edmx file for the Northwind model.</span></span> <span data-ttu-id="6962a-114">Daha fazla bilgi için bkz [.. edmx dosyasına genel bakış](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="6962a-114">For more information, see [.edmx File Overview](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)).</span></span>

### <a name="to-generate-c-classes-that-support-data-binding"></a><span data-ttu-id="6962a-115">Veri bağlamayı destekleyen C# sınıfları oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="6962a-115">To generate C# classes that support data binding</span></span>

- <span data-ttu-id="6962a-116">Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="6962a-116">At the command prompt, execute the following command without line breaks:</span></span>

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:CSharp /out:Northwind.cs /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    > <span data-ttu-id="6962a-117">Verilen değeri, `/uri:` Northwind örnek veri hizmeti ÖRNEĞINIZIN URI 'siyle parametreye değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="6962a-117">You must replace the value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>

### <a name="to-generate-visual-basic-classes-that-support-data-binding"></a><span data-ttu-id="6962a-118">Veri bağlamayı destekleyen Visual Basic sınıfları oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="6962a-118">To generate Visual Basic classes that support data binding</span></span>

- <span data-ttu-id="6962a-119">Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="6962a-119">At the command prompt, execute the following command without line breaks:</span></span>

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    > <span data-ttu-id="6962a-120">Sağlanan değeri, `/uri:` Northwind örnek veri hizmeti ÖRNEĞINIZIN URI 'siyle parametreye değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="6962a-120">You must replace value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>

### <a name="to-generate-c-classes-based-on-the-service-uri"></a><span data-ttu-id="6962a-121">Hizmet URI 'sini temel alan C# sınıfları oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="6962a-121">To generate C# classes based on the service URI</span></span>

- <span data-ttu-id="6962a-122">Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="6962a-122">At the command prompt, execute the following command without line breaks:</span></span>

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /language:CSharp /out:northwind.cs /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    > <span data-ttu-id="6962a-123">Verilen değeri, `/uri:` Northwind örnek veri hizmeti ÖRNEĞINIZIN URI 'siyle parametreye değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="6962a-123">You must replace the value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>

### <a name="to-generate-visual-basic-classes-based-on-the-service-uri"></a><span data-ttu-id="6962a-124">Hizmet URI 'sini temel alan Visual Basic sınıfları oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="6962a-124">To generate Visual Basic classes based on the service URI</span></span>

- <span data-ttu-id="6962a-125">Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="6962a-125">At the command prompt, execute the following command without line breaks:</span></span>

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    > <span data-ttu-id="6962a-126">Sağlanan değeri, `/uri:` Northwind örnek veri hizmeti ÖRNEĞINIZIN URI 'siyle parametreye değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="6962a-126">You must replace value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>

### <a name="to-generate-c-classes-based-on-the-conceptual-model-file-csdl"></a><span data-ttu-id="6962a-127">Kavramsal model dosyasına (CSDL) göre C# sınıfları oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="6962a-127">To generate C# classes based on the conceptual model file (CSDL)</span></span>

- <span data-ttu-id="6962a-128">Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="6962a-128">At the command prompt, execute the following command without line breaks:</span></span>

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.csdl /out:Northwind.cs
    ```

### <a name="to-generate-visual-basic-classes-based-on-the-conceptual-model-file-csdl"></a><span data-ttu-id="6962a-129">Kavramsal model dosyasına (CSDL) göre Visual Basic sınıfları oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="6962a-129">To generate Visual Basic classes based on the conceptual model file (CSDL)</span></span>

- <span data-ttu-id="6962a-130">Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="6962a-130">At the command prompt, execute the following command without line breaks:</span></span>

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.csdl /out:Northwind.vb
    ```

### <a name="to-generate-c-classes-based-on-the-edmx-file"></a><span data-ttu-id="6962a-131">. Edmx dosyasını temel alan C# sınıfları oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="6962a-131">To generate C# classes based on the .edmx file</span></span>

- <span data-ttu-id="6962a-132">Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="6962a-132">At the command prompt, execute the following command without line breaks:</span></span>

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.edmx /out:c:\northwind.cs
    ```

### <a name="to-generate-visual-basic-classes-based-on-the-edmx-file"></a><span data-ttu-id="6962a-133">. Edmx dosyasına göre Visual Basic sınıfları oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="6962a-133">To generate Visual Basic classes based on the .edmx file</span></span>

- <span data-ttu-id="6962a-134">Komut isteminde, satır sonları olmadan aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="6962a-134">At the command prompt, execute the following command without line breaks:</span></span>

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.edmx /out:c:\northwind.vb
    ```

## <a name="see-also"></a><span data-ttu-id="6962a-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6962a-135">See also</span></span>

- [<span data-ttu-id="6962a-136">Veri Hizmeti İstemci Kitaplığı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="6962a-136">Generating the Data Service Client Library</span></span>](generating-the-data-service-client-library-wcf-data-services.md)
- [<span data-ttu-id="6962a-137">Nasıl yapılır: Veri Hizmeti Başvurusu Ekleme</span><span class="sxs-lookup"><span data-stu-id="6962a-137">How to: Add a Data Service Reference</span></span>](how-to-add-a-data-service-reference-wcf-data-services.md)
- [<span data-ttu-id="6962a-138">WCF Veri Hizmeti İstemci Yardımcı Programı (DataSvcUtil.exe)</span><span class="sxs-lookup"><span data-stu-id="6962a-138">WCF Data Service Client Utility (DataSvcUtil.exe)</span></span>](wcf-data-service-client-utility-datasvcutil-exe.md)
