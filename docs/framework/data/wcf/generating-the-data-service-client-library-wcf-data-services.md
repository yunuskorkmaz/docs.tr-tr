---
title: "Veri Hizmeti istemci kitaplığı (WCF Veri Hizmetleri) oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- client applications, WCF Data Services
- WCF Data Services, client library
- Add Service Reference dialog box
ms.assetid: 314077c1-ac10-47e1-bed4-940b5462359d
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 72b75451d69e107b78152b301027f902ff77a25d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="generating-the-data-service-client-library-wcf-data-services"></a><span data-ttu-id="05cb6-102">Veri Hizmeti istemci kitaplığı (WCF Veri Hizmetleri) oluşturma</span><span class="sxs-lookup"><span data-stu-id="05cb6-102">Generating the Data Service Client Library (WCF Data Services)</span></span>
<span data-ttu-id="05cb6-103">Arabirimini uygulayan bir veri hizmeti [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] tarafından sunulan veri modeli açıklayan bir hizmeti meta veri belgesi döndürebilir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akış.</span><span class="sxs-lookup"><span data-stu-id="05cb6-103">A data service that implements the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] can return a service metadata document that describes the data model exposed by the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed.</span></span> <span data-ttu-id="05cb6-104">Daha fazla bilgi için bkz: [OData: hizmeti meta veri belgesi](http://go.microsoft.com/fwlink/?LinkId=186070).</span><span class="sxs-lookup"><span data-stu-id="05cb6-104">For more information, see [OData: Service Metadata Document](http://go.microsoft.com/fwlink/?LinkId=186070).</span></span> <span data-ttu-id="05cb6-105">Kullanabileceğiniz **hizmet Başvurusu Ekle** iletişim için bir başvuru eklemek için Visual Studio'da bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-hizmet tabanlı.</span><span class="sxs-lookup"><span data-stu-id="05cb6-105">You can use the **Add Service Reference** dialog in Visual Studio to add a reference to an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-based service.</span></span> <span data-ttu-id="05cb6-106">Kullandığınızda, bu aracı tarafından döndürülen meta veriler için bir başvuru eklemek için bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] istemci projede akış, aşağıdaki eylemleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="05cb6-106">When you use this tool to add a reference to the metadata returned by an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed in a client project, it performs the following actions:</span></span>  
  
-   <span data-ttu-id="05cb6-107">Veri hizmetinden veri hizmeti meta veri belgesi ister ve döndürülen meta veri yorumlar.</span><span class="sxs-lookup"><span data-stu-id="05cb6-107">Requests the service metadata document from the data service and interprets the returned metadata.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="05cb6-108">Döndürülen meta veri istemci projesinde bir .edmx dosyası olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="05cb6-108">The returned metadata is stored in the client project as an .edmx file.</span></span> <span data-ttu-id="05cb6-109">Entity Framework tarafından kullanılan bir .edmx dosyasının biçimlendirmek aynı olmadığı için varlık veri modeli Tasarımcısı'nı kullanarak bu .edmx dosyasının açılamaz.</span><span class="sxs-lookup"><span data-stu-id="05cb6-109">This .edmx file cannot be opened by using the Entity Data Model designer because it does not have the same format an .edmx file used by the Entity Framework.</span></span> <span data-ttu-id="05cb6-110">Bu meta veri dosyası, herhangi bir metin düzenleyicisi veya XML düzenleyicisi kullanarak görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05cb6-110">You can view this metadata file by using the XML editor or any text editor.</span></span> <span data-ttu-id="05cb6-111">Daha fazla bilgi için bkz: [ \[MC EDMX\]: Varlık veri modeli için Veri Hizmetleri paketleme biçimi](http://go.microsoft.com/fwlink/?LinkID=178833) belirtimi</span><span class="sxs-lookup"><span data-stu-id="05cb6-111">For more information, see the [\[MC-EDMX\]: Entity Data Model for Data Services Packaging Format](http://go.microsoft.com/fwlink/?LinkID=178833) specification</span></span>  
  
-   <span data-ttu-id="05cb6-112">Hizmet bir gösterimini devralan bir varlık kapsayıcı sınıfı olarak oluşturur <xref:System.Data.Services.Client.DataServiceContext>.</span><span class="sxs-lookup"><span data-stu-id="05cb6-112">Generates a representation of the service as an entity container class that inherits from <xref:System.Data.Services.Client.DataServiceContext>.</span></span> <span data-ttu-id="05cb6-113">Bu oluşturulan varlık kapsayıcı sınıfı varlık veri modeli araçları varlık kapsayıcıya benzer.</span><span class="sxs-lookup"><span data-stu-id="05cb6-113">This generated entity container class resembles the entity container that the Entity Data Model tools generate.</span></span> <span data-ttu-id="05cb6-114">Daha fazla bilgi için bkz: [nesne Hizmetleri'ne Genel Bakış (Entity Framework)](http://msdn.microsoft.com/library/43014cf9-c9cb-4538-bfbb-197820b60038).</span><span class="sxs-lookup"><span data-stu-id="05cb6-114">For more information, see [Object Services Overview (Entity Framework)](http://msdn.microsoft.com/library/43014cf9-c9cb-4538-bfbb-197820b60038).</span></span>  
  
-   <span data-ttu-id="05cb6-115">Hizmet meta verilerde bulduğu veri modeli türleri için veri sınıfları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="05cb6-115">Generates data classes for the data model types that it discovers in the service metadata.</span></span>  
  
-   <span data-ttu-id="05cb6-116">Bir başvuru ekler `System.Data.Services.Client` projeye derleme.</span><span class="sxs-lookup"><span data-stu-id="05cb6-116">Adds a reference to the `System.Data.Services.Client` assembly to the project.</span></span>  
  
 <span data-ttu-id="05cb6-117">Daha fazla bilgi için bkz: [nasıl yapılır: bir veri hizmet Başvurusu Ekle](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="05cb6-117">For more information, see [How to: Add a Data Service Reference](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="05cb6-118">İstemci veri hizmeti sınıflarını kullanarak da oluşturulabilir [DataSvcUtil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) aracı komut isteminde.</span><span class="sxs-lookup"><span data-stu-id="05cb6-118">The client data service classes can also be generated by using the [DataSvcUtil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) tool at the command prompt.</span></span> <span data-ttu-id="05cb6-119">Daha fazla bilgi için bkz: [nasıl yapılır: el ile oluşturmak istemci veri hizmeti sınıfları](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="05cb6-119">For more information, see [How to: Manually Generate Client Data Service Classes](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md).</span></span>  
  
## <a name="client-data-type-mapping"></a><span data-ttu-id="05cb6-120">İstemci veri türü eşlemesi</span><span class="sxs-lookup"><span data-stu-id="05cb6-120">Client Data Type Mapping</span></span>  
 <span data-ttu-id="05cb6-121">Kullandığınızda **hizmet Başvurusu Ekle** Visual Studio'da iletişim kutusu veya `DataSvcUtil.exe` temel alan istemci veri sınıfları oluşturmak için aracı bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akış, ilkel türler .NET Framework Veri türlerin eşlendiği aşağıdaki gibi veri modeli:</span><span class="sxs-lookup"><span data-stu-id="05cb6-121">When you use the **Add Service Reference** dialog in Visual Studio or the `DataSvcUtil.exe` tool to generate client data classes that are based on an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed, the .NET Framework data types are mapped to the primitive types from the data model as follows:</span></span>  
  
|<span data-ttu-id="05cb6-122">Veri modeli türü</span><span class="sxs-lookup"><span data-stu-id="05cb6-122">Data model type</span></span>|<span data-ttu-id="05cb6-123">.NET framework veri türü</span><span class="sxs-lookup"><span data-stu-id="05cb6-123">.NET Framework data type</span></span>|  
|---------------------|------------------------------|  
|`Edm.Binary`|<span data-ttu-id="05cb6-124"><xref:System.Byte>`[]`</span><span class="sxs-lookup"><span data-stu-id="05cb6-124"><xref:System.Byte> `[]`</span></span>|  
|`Edm.Boolean`|<xref:System.Boolean>|  
|`Edm.Byte`|<xref:System.Byte>|  
|`Edm.DateTime`|<xref:System.DateTime>|  
|`Edm.Decimal`|<xref:System.Decimal>|  
|`Edm.Double`|<xref:System.Double>|  
|`Edm.Guid`|<xref:System.Guid>|  
|`Edm.Int16`|<xref:System.Int16>|  
|`Edm.Int32`|<xref:System.Int32>|  
|`Edm.Int64`|<xref:System.Int64>|  
|`Edm.SByte`|<xref:System.SByte>|  
|`Edm.Single`|<xref:System.Single>|  
|`Edm.String`|<xref:System.String>|  
  
 <span data-ttu-id="05cb6-125">Daha fazla bilgi için bkz: [OData: Basit veri türleri](http://go.microsoft.com/fwlink/?LinkId=186072).</span><span class="sxs-lookup"><span data-stu-id="05cb6-125">For more information, see [OData: Primitive Data Types](http://go.microsoft.com/fwlink/?LinkId=186072).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05cb6-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="05cb6-126">See Also</span></span>  
 [<span data-ttu-id="05cb6-127">WCF Veri Hizmetleri İstemci Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="05cb6-127">WCF Data Services Client Library</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 [<span data-ttu-id="05cb6-128">Hızlı başlangıç</span><span class="sxs-lookup"><span data-stu-id="05cb6-128">Quickstart</span></span>](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)
