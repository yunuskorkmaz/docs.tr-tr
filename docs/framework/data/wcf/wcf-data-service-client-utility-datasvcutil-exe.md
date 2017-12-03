---
title: "WCF veri hizmeti istemci yardımcı programı (DataSvcUtil.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, generating client data classes
- WCF Data Services, client library
- WCF Data Services, consuming
ms.assetid: 9d0af606-929b-4c03-b307-3ef5f705afce
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 21189ffd5fc8b113cc746fd855bd5c325aad78c6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="wcf-data-service-client-utility-datasvcutilexe"></a><span data-ttu-id="b332c-102">WCF veri hizmeti istemci yardımcı programı (DataSvcUtil.exe)</span><span class="sxs-lookup"><span data-stu-id="b332c-102">WCF Data Service Client Utility (DataSvcUtil.exe)</span></span>
<span data-ttu-id="b332c-103">DataSvcUtil.exe tarafından sağlanan bir komut satırı aracıdır [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] , tüketir bir [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] akış ve veri hizmeti .NET Framework istemci uygulamasından erişmek için gerekli istemci veri hizmeti sınıfları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b332c-103">DataSvcUtil.exe is a command-line tool provided by [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] that consumes an [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed and generates the client data service classes that are needed to access a data service from a .NET Framework client application.</span></span> <span data-ttu-id="b332c-104">Bu yardımcı programı, aşağıdaki meta veri kaynakları kullanarak veri sınıfları oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b332c-104">This utility can generate data classes by using the following metadata sources:</span></span>  
  
-   <span data-ttu-id="b332c-105">Veri Hizmeti URI kökü.</span><span class="sxs-lookup"><span data-stu-id="b332c-105">The root URI of a data service.</span></span> <span data-ttu-id="b332c-106">Yardımcı programı veri hizmeti tarafından sunulan veri modeli açıklayan hizmeti meta veri belgesi ister.</span><span class="sxs-lookup"><span data-stu-id="b332c-106">The utility requests the service metadata document, which describes the data model exposed by the data service.</span></span> <span data-ttu-id="b332c-107">Daha fazla bilgi için bkz: [OData: hizmeti meta veri belgesi](http://go.microsoft.com/fwlink/?LinkId=186070).</span><span class="sxs-lookup"><span data-stu-id="b332c-107">For more information, see [OData: Service Metadata Document](http://go.microsoft.com/fwlink/?LinkId=186070).</span></span>  
  
-   <span data-ttu-id="b332c-108">Kavramsal şema tanım dili (CSDL) kullanılarak tanımlandığı şekilde tanımlanmış bir veri modeli dosyası (.csdl) [ \[MC CSDL\]: kavramsal şema tanım dosyası biçimi](http://go.microsoft.com/fwlink/?LinkID=159072) belirtimi.</span><span class="sxs-lookup"><span data-stu-id="b332c-108">A data model file (.csdl) defined by using the conceptual schema definition language (CSDL), as defined in the [\[MC-CSDL\]: Conceptual Schema Definition File Format](http://go.microsoft.com/fwlink/?LinkID=159072) specification.</span></span>  
  
-   <span data-ttu-id="b332c-109">Entity Framework ile sağlanan varlık veri modeli araçları kullanılarak oluşturulan bir .edmx dosyasının.</span><span class="sxs-lookup"><span data-stu-id="b332c-109">An .edmx file created by using the Entity Data Model tools that are provided with the Entity Framework.</span></span> <span data-ttu-id="b332c-110">Daha fazla bilgi için bkz: [ \[MC EDMX\]: Varlık veri modeli için Veri Hizmetleri paketleme biçimi](http://go.microsoft.com/fwlink/?LinkID=178833) belirtimi.</span><span class="sxs-lookup"><span data-stu-id="b332c-110">For more information, see the [\[MC-EDMX\]: Entity Data Model for Data Services Packaging Format](http://go.microsoft.com/fwlink/?LinkID=178833) specification.</span></span>  
  
 <span data-ttu-id="b332c-111">Daha fazla bilgi için bkz: [nasıl yapılır: el ile oluşturmak istemci veri hizmeti sınıfları](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="b332c-111">For more information, see [How to: Manually Generate Client Data Service Classes](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="b332c-112">DataSvcUtil.exe aracına [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dizin.</span><span class="sxs-lookup"><span data-stu-id="b332c-112">The DataSvcUtil.exe tool is installed in the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] directory.</span></span> <span data-ttu-id="b332c-113">Çoğu durumda bu C:\Windows\Microsoft.NET\Framework\v4.0 içinde bulunan.</span><span class="sxs-lookup"><span data-stu-id="b332c-113">In many cases, this is located in C:\Windows\Microsoft.NET\Framework\v4.0,.</span></span> <span data-ttu-id="b332c-114">64 bit sistemler için bu C:\Windows\Microsoft.NET\Framework64\v4.0 içinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="b332c-114">For 64-bit systems, this is located in C:\Windows\Microsoft.NET\Framework64\v4.0.</span></span> <span data-ttu-id="b332c-115">Visual Studio komut isteminden DataSvcUtil.exe aracı da erişebilirsiniz (tıklatın **Başlat**, işaret **tüm programlar**, işaret **Microsoft Visual Studio 2010**, işaret **Visual Studio Araçları**ve ardından **Visual Studio 2010 Komut İstemi**).</span><span class="sxs-lookup"><span data-stu-id="b332c-115">You can also access the DataSvcUtil.exe tool from the Visual Studio command prompt (Click **Start**, point to **All Programs**, point to **Microsoft Visual Studio 2010**, point to **Visual Studio Tools**, and then click **Visual Studio 2010 Command Prompt**).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b332c-116">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b332c-116">Syntax</span></span>  
  
```  
datasvcutil /out:file [/in:file | /uri:serviceuri] [/dataservicecollection] [/language:devlang] [/nologo] [/version:ver] [/help]  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b332c-117">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b332c-117">Parameters</span></span>  
  
|<span data-ttu-id="b332c-118">Seçenek</span><span class="sxs-lookup"><span data-stu-id="b332c-118">Option</span></span>|<span data-ttu-id="b332c-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b332c-119">Description</span></span>|  
|------------|-----------------|  
|`/dataservicecollection`|<span data-ttu-id="b332c-120">Denetimlere nesneleri bağlamak için gereken kod ayrıca oluşturulan belirtir.</span><span class="sxs-lookup"><span data-stu-id="b332c-120">Specifies that the code required to bind objects to controls is also generated.</span></span>|  
|`/help`<br /><br /> <span data-ttu-id="b332c-121">veya</span><span class="sxs-lookup"><span data-stu-id="b332c-121">-or-</span></span><br /><br /> `/?`|<span data-ttu-id="b332c-122">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="b332c-122">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="b332c-123">`/in:` *\<dosyası >*</span><span class="sxs-lookup"><span data-stu-id="b332c-123">`/in:` *\<file>*</span></span>|<span data-ttu-id="b332c-124">.Csdl veya .edmx dosyasının veya dosyanın bulunduğu dizini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b332c-124">Specifies the .csdl or .edmx file or a directory where the file is located.</span></span>|  
|<span data-ttu-id="b332c-125">`/language:`[VB &#124; CSharp]</span><span class="sxs-lookup"><span data-stu-id="b332c-125">`/language:`[VB&#124;CSharp]</span></span>|<span data-ttu-id="b332c-126">Oluşturulan kaynak kodu dosyaları dilini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b332c-126">Specifies the language for the generated source code files.</span></span> <span data-ttu-id="b332c-127">C# dil Varsayılanları.</span><span class="sxs-lookup"><span data-stu-id="b332c-127">The language defaults to C#.</span></span>|  
|`/nologo`|<span data-ttu-id="b332c-128">Telif Hakkı görüntüleme iletiden gizler.</span><span class="sxs-lookup"><span data-stu-id="b332c-128">Suppresses the copyright message from displaying.</span></span>|  
|<span data-ttu-id="b332c-129">`/out:` *\<dosyası >*</span><span class="sxs-lookup"><span data-stu-id="b332c-129">`/out:` *\<file>*</span></span>|<span data-ttu-id="b332c-130">Oluşturulan istemci veri hizmeti sınıfları içeren kaynak kodu dosyasının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b332c-130">Specifies the name of the source code file that contains the generated client data service classes.</span></span>|  
|<span data-ttu-id="b332c-131">`/uri:` *\<dize >*</span><span class="sxs-lookup"><span data-stu-id="b332c-131">`/uri:` *\<string>*</span></span>|<span data-ttu-id="b332c-132">URI'sini [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akış.</span><span class="sxs-lookup"><span data-stu-id="b332c-132">The URI of the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed.</span></span>|  
|<span data-ttu-id="b332c-133">`/version:`[1.0&#124;2.0]</span><span class="sxs-lookup"><span data-stu-id="b332c-133">`/version:`[1.0&#124;2.0]</span></span>|<span data-ttu-id="b332c-134">En yüksek kabul edilen sürümünü belirtir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b332c-134">Specifies the highest accepted version of [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].</span></span> <span data-ttu-id="b332c-135">Sürüm göre belirlenir `DataServiceVersion` döndürülen veri hizmeti meta verilerde DataService öğesinin özniteliği.</span><span class="sxs-lookup"><span data-stu-id="b332c-135">The version is determined based on the `DataServiceVersion` attribute of the DataService element in the returned data service metadata.</span></span> <span data-ttu-id="b332c-136">Daha fazla bilgi için bkz: [veri hizmeti sürüm](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="b332c-136">For more information, see [Data Service Versioning](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md).</span></span> <span data-ttu-id="b332c-137">Belirttiğinizde `/dataservicecollection` parametresini de belirtmeniz gerekir `/version:2.0` veri bağlamasını etkinleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="b332c-137">When you specify the `/dataservicecollection` parameter, you must also specify `/version:2.0` to enable data binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b332c-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b332c-138">See Also</span></span>  
 [<span data-ttu-id="b332c-139">Veri Hizmeti istemci kitaplığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="b332c-139">Generating the Data Service Client Library</span></span>](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)  
 [<span data-ttu-id="b332c-140">Nasıl yapılır: bir veri hizmet Başvurusu Ekle</span><span class="sxs-lookup"><span data-stu-id="b332c-140">How to: Add a Data Service Reference</span></span>](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)
