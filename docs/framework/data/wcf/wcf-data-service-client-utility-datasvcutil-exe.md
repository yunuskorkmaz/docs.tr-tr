---
description: 'Daha fazla bilgi edinin: WCF veri hizmeti Istemci yardımcı programı (DataSvcUtil.exe)'
title: WCF Veri Hizmeti İstemci Yardımcı Programı (DataSvcUtil.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, generating client data classes
- WCF Data Services, client library
- WCF Data Services, consuming
ms.assetid: 9d0af606-929b-4c03-b307-3ef5f705afce
ms.openlocfilehash: 1e232538284072d82eed3f1b9e8d41f2ae950adf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791705"
---
# <a name="wcf-data-service-client-utility-datasvcutilexe"></a><span data-ttu-id="b9327-103">WCF Veri Hizmeti İstemci Yardımcı Programı (DataSvcUtil.exe)</span><span class="sxs-lookup"><span data-stu-id="b9327-103">WCF Data Service Client Utility (DataSvcUtil.exe)</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="b9327-104">DataSvcUtil.exe, bir açık veri Protokolü (OData) akışı tüketen ve bir .NET Framework istemci uygulamasından bir veri hizmetine erişmek için gereken istemci veri hizmeti sınıflarını oluşturan WCF Veri Hizmetleri tarafından sunulan bir komut satırı aracıdır.</span><span class="sxs-lookup"><span data-stu-id="b9327-104">DataSvcUtil.exe is a command-line tool provided by WCF Data Services that consumes an Open Data Protocol (OData) feed and generates the client data service classes that are needed to access a data service from a .NET Framework client application.</span></span> <span data-ttu-id="b9327-105">Bu yardımcı program, aşağıdaki meta veri kaynaklarını kullanarak veri sınıfları oluşturabilir:</span><span class="sxs-lookup"><span data-stu-id="b9327-105">This utility can generate data classes by using the following metadata sources:</span></span>

- <span data-ttu-id="b9327-106">Veri hizmetinin kök URI 'SI.</span><span class="sxs-lookup"><span data-stu-id="b9327-106">The root URI of a data service.</span></span> <span data-ttu-id="b9327-107">Yardımcı programı, veri hizmeti tarafından açığa çıkarılan veri modelini açıklayan hizmet meta verileri belgesini ister.</span><span class="sxs-lookup"><span data-stu-id="b9327-107">The utility requests the service metadata document, which describes the data model exposed by the data service.</span></span> <span data-ttu-id="b9327-108">Daha fazla bilgi için bkz. [AtomPub (RFC5023)](https://tools.ietf.org/html/rfc5023#section-8).</span><span class="sxs-lookup"><span data-stu-id="b9327-108">For more information, see [AtomPub (RFC5023)](https://tools.ietf.org/html/rfc5023#section-8).</span></span>

- <span data-ttu-id="b9327-109">, [ \[ Mc-csdl \] : kavramsal şema tanımı dosya biçimi](/openspecs/windows_protocols/mc-csdl/c03ad8c3-e8b7-4306-af96-a9e52bb3df12) belirtiminde tanımlandığı şekilde kavramsal şema tanım dili (csdl) kullanılarak tanımlanan bir veri modeli dosyası (. csdl).</span><span class="sxs-lookup"><span data-stu-id="b9327-109">A data model file (.csdl) defined by using the conceptual schema definition language (CSDL), as defined in the [\[MC-CSDL\]: Conceptual Schema Definition File Format](/openspecs/windows_protocols/mc-csdl/c03ad8c3-e8b7-4306-af96-a9e52bb3df12) specification.</span></span>

- <span data-ttu-id="b9327-110">Entity Framework ile birlikte sunulan Varlık Veri Modeli araçları kullanılarak oluşturulan bir. edmx dosyası.</span><span class="sxs-lookup"><span data-stu-id="b9327-110">An .edmx file created by using the Entity Data Model tools that are provided with the Entity Framework.</span></span> <span data-ttu-id="b9327-111">Daha fazla bilgi için bkz. [ \[ mc-EDMX \] : varlık veri modeli for Data Services paketleme biçim](/openspecs/windows_protocols/mc-edmx/5dff5e25-56a1-408b-9d44-bff6634c7d16) belirtimi.</span><span class="sxs-lookup"><span data-stu-id="b9327-111">For more information, see the [\[MC-EDMX\]: Entity Data Model for Data Services Packaging Format](/openspecs/windows_protocols/mc-edmx/5dff5e25-56a1-408b-9d44-bff6634c7d16) specification.</span></span>

<span data-ttu-id="b9327-112">Daha fazla bilgi için bkz. [nasıl yapılır: El Ile Istemci veri hizmeti sınıfları oluşturma](how-to-manually-generate-client-data-service-classes-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="b9327-112">For more information, see [How to: Manually Generate Client Data Service Classes](how-to-manually-generate-client-data-service-classes-wcf-data-services.md).</span></span>

<span data-ttu-id="b9327-113">DataSvcUtil.exe aracı .NET Framework dizinine yüklenir.</span><span class="sxs-lookup"><span data-stu-id="b9327-113">The DataSvcUtil.exe tool is installed in the .NET Framework directory.</span></span> <span data-ttu-id="b9327-114">Çoğu durumda bu, *C:\Windows\Microsoft.NET\Framework\v4.0*' de bulunur.</span><span class="sxs-lookup"><span data-stu-id="b9327-114">In many cases, this is located in *C:\Windows\Microsoft.NET\Framework\v4.0*.</span></span> <span data-ttu-id="b9327-115">64 bit sistemler için bu *C:\Windows\Microsoft.NET\Framework64\v4.0* konumunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="b9327-115">For 64-bit systems, this is located in *C:\Windows\Microsoft.NET\Framework64\v4.0*.</span></span> <span data-ttu-id="b9327-116">Visual Studio için Geliştirici Komut İstemi DataSvcUtil.exe aracına da erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b9327-116">You can also access the DataSvcUtil.exe tool from Developer Command Prompt for Visual Studio.</span></span>

## <a name="syntax"></a><span data-ttu-id="b9327-117">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b9327-117">Syntax</span></span>

```console
datasvcutil /out:file [/in:file | /uri:serviceuri] [/dataservicecollection] [/language:devlang] [/nologo] [/version:ver] [/help]
```

## <a name="parameters"></a><span data-ttu-id="b9327-118">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b9327-118">Parameters</span></span>

|<span data-ttu-id="b9327-119">Seçenek</span><span class="sxs-lookup"><span data-stu-id="b9327-119">Option</span></span>|<span data-ttu-id="b9327-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b9327-120">Description</span></span>|
|------------|-----------------|
|`/dataservicecollection`|<span data-ttu-id="b9327-121">Nesneleri denetimlere bağlamak için gereken kodun de oluşturulduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="b9327-121">Specifies that the code required to bind objects to controls is also generated.</span></span>|
|`/help`<br /><br /> <span data-ttu-id="b9327-122">-veya-</span><span class="sxs-lookup"><span data-stu-id="b9327-122">-or-</span></span><br /><br /> `/?`|<span data-ttu-id="b9327-123">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="b9327-123">Displays command syntax and options for the tool.</span></span>|
|<span data-ttu-id="b9327-124">`/in:` *\<file>*</span><span class="sxs-lookup"><span data-stu-id="b9327-124">`/in:` *\<file>*</span></span>|<span data-ttu-id="b9327-125">. Csdl veya. edmx dosyasını ya da dosyanın bulunduğu bir dizini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b9327-125">Specifies the .csdl or .edmx file or a directory where the file is located.</span></span>|
|<span data-ttu-id="b9327-126">`/language:`[VB&#124;CSharp]</span><span class="sxs-lookup"><span data-stu-id="b9327-126">`/language:`[VB&#124;CSharp]</span></span>|<span data-ttu-id="b9327-127">Oluşturulan kaynak kodu dosyalarının dilini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b9327-127">Specifies the language for the generated source code files.</span></span> <span data-ttu-id="b9327-128">Dil varsayılan olarak C# ' dir.</span><span class="sxs-lookup"><span data-stu-id="b9327-128">The language defaults to C#.</span></span>|
|`/nologo`|<span data-ttu-id="b9327-129">Telif hakkı iletisinin görüntülenmesini önler.</span><span class="sxs-lookup"><span data-stu-id="b9327-129">Suppresses the copyright message from displaying.</span></span>|
|<span data-ttu-id="b9327-130">`/out:` *\<file>*</span><span class="sxs-lookup"><span data-stu-id="b9327-130">`/out:` *\<file>*</span></span>|<span data-ttu-id="b9327-131">Oluşturulan istemci veri hizmeti sınıflarını içeren kaynak kodu dosyasının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b9327-131">Specifies the name of the source code file that contains the generated client data service classes.</span></span>|
|<span data-ttu-id="b9327-132">`/uri:` *\<string>*</span><span class="sxs-lookup"><span data-stu-id="b9327-132">`/uri:` *\<string>*</span></span>|<span data-ttu-id="b9327-133">OData akışı URI 'SI.</span><span class="sxs-lookup"><span data-stu-id="b9327-133">The URI of the OData feed.</span></span>|
|<span data-ttu-id="b9327-134">`/version:`[1,0&#124;2,0]</span><span class="sxs-lookup"><span data-stu-id="b9327-134">`/version:`[1.0&#124;2.0]</span></span>|<span data-ttu-id="b9327-135">En yüksek kabul edilen OData sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="b9327-135">Specifies the highest accepted version of OData.</span></span> <span data-ttu-id="b9327-136">Sürüm, `DataServiceVersion` döndürülen veri hizmeti meta verilerindeki DataService öğesinin özniteliğine göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="b9327-136">The version is determined based on the `DataServiceVersion` attribute of the DataService element in the returned data service metadata.</span></span> <span data-ttu-id="b9327-137">Daha fazla bilgi için bkz. [veri hizmeti sürümü oluşturma](data-service-versioning-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="b9327-137">For more information, see [Data Service Versioning](data-service-versioning-wcf-data-services.md).</span></span> <span data-ttu-id="b9327-138">`/dataservicecollection`Parametresini belirttiğinizde `/version:2.0` veri bağlamayı etkinleştirmek için de belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b9327-138">When you specify the `/dataservicecollection` parameter, you must also specify `/version:2.0` to enable data binding.</span></span>|

## <a name="see-also"></a><span data-ttu-id="b9327-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b9327-139">See also</span></span>

- [<span data-ttu-id="b9327-140">Veri Hizmeti İstemci Kitaplığı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b9327-140">Generating the Data Service Client Library</span></span>](generating-the-data-service-client-library-wcf-data-services.md)
- [<span data-ttu-id="b9327-141">Nasıl yapılır: Veri Hizmeti Başvurusu Ekleme</span><span class="sxs-lookup"><span data-stu-id="b9327-141">How to: Add a Data Service Reference</span></span>](how-to-add-a-data-service-reference-wcf-data-services.md)
