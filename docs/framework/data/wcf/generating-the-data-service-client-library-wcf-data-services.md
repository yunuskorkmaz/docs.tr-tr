---
title: Veri Hizmeti istemci Kitaplığı'nı (WCF Veri Hizmetleri) oluşturma
ms.date: 03/30/2017
helpviewer_keywords:
- client applications, WCF Data Services
- WCF Data Services, client library
- Add Service Reference dialog box
ms.assetid: 314077c1-ac10-47e1-bed4-940b5462359d
ms.openlocfilehash: 170f9714f3cfbf2350423f28316d665d427fd56e
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43862257"
---
# <a name="generating-the-data-service-client-library-wcf-data-services"></a><span data-ttu-id="e121e-102">Veri Hizmeti istemci Kitaplığı'nı (WCF Veri Hizmetleri) oluşturma</span><span class="sxs-lookup"><span data-stu-id="e121e-102">Generating the Data Service Client Library (WCF Data Services)</span></span>
<span data-ttu-id="e121e-103">Uygulayan bir veri hizmeti [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] tarafından kullanıma sunulan veri modeli açıklayan bir hizmeti meta veri belgesi döndürebilir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akış.</span><span class="sxs-lookup"><span data-stu-id="e121e-103">A data service that implements the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] can return a service metadata document that describes the data model exposed by the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed.</span></span> <span data-ttu-id="e121e-104">Daha fazla bilgi için [OData: hizmet meta verileri belgesi](https://go.microsoft.com/fwlink/?LinkId=186070).</span><span class="sxs-lookup"><span data-stu-id="e121e-104">For more information, see [OData: Service Metadata Document](https://go.microsoft.com/fwlink/?LinkId=186070).</span></span> <span data-ttu-id="e121e-105">Kullanabileceğiniz **hizmet Başvurusu Ekle** iletişim için bir başvuru eklemek için Visual Studio'da bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-hizmet tabanlı.</span><span class="sxs-lookup"><span data-stu-id="e121e-105">You can use the **Add Service Reference** dialog in Visual Studio to add a reference to an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-based service.</span></span> <span data-ttu-id="e121e-106">Tarafından döndürülen meta veriler için bir başvuru eklemek için bu aracı kullanırken bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] istemci projesinde akışı, aşağıdaki eylemleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="e121e-106">When you use this tool to add a reference to the metadata returned by an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed in a client project, it performs the following actions:</span></span>  
  
-   <span data-ttu-id="e121e-107">Hizmet meta verileri belgesi veri hizmetinden ister ve döndürülen meta verilere yorumlar.</span><span class="sxs-lookup"><span data-stu-id="e121e-107">Requests the service metadata document from the data service and interprets the returned metadata.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e121e-108">Döndürülen meta verilere istemci projesinde bir .edmx dosyası olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="e121e-108">The returned metadata is stored in the client project as an .edmx file.</span></span> <span data-ttu-id="e121e-109">Entity Framework tarafından kullanılan bir .edmx dosyası biçim aynı olmadığı için varlık veri modeli Tasarımcısı'nı kullanarak bu .edmx dosyası açılamıyor.</span><span class="sxs-lookup"><span data-stu-id="e121e-109">This .edmx file cannot be opened by using the Entity Data Model designer because it does not have the same format an .edmx file used by the Entity Framework.</span></span> <span data-ttu-id="e121e-110">Bu meta veri dosyası, herhangi bir metin düzenleyicisi veya XML düzenleyicisi kullanarak görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e121e-110">You can view this metadata file by using the XML editor or any text editor.</span></span> <span data-ttu-id="e121e-111">Daha fazla bilgi için [ \[MC EDMX\]: Varlık veri modeli için veri hizmetlerini paketleme biçimini](https://go.microsoft.com/fwlink/?LinkID=178833) belirtimi</span><span class="sxs-lookup"><span data-stu-id="e121e-111">For more information, see the [\[MC-EDMX\]: Entity Data Model for Data Services Packaging Format](https://go.microsoft.com/fwlink/?LinkID=178833) specification</span></span>  
  
-   <span data-ttu-id="e121e-112">Hizmet bir temsili olarak devraldığı bir varlık kapsayıcı sınıfı oluşturur <xref:System.Data.Services.Client.DataServiceContext>.</span><span class="sxs-lookup"><span data-stu-id="e121e-112">Generates a representation of the service as an entity container class that inherits from <xref:System.Data.Services.Client.DataServiceContext>.</span></span> <span data-ttu-id="e121e-113">Bu oluşturulan varlık kapsayıcı sınıfı, varlık veri modeli araçları oluşturan varlık kapsayıcısı benzer.</span><span class="sxs-lookup"><span data-stu-id="e121e-113">This generated entity container class resembles the entity container that the Entity Data Model tools generate.</span></span> <span data-ttu-id="e121e-114">Daha fazla bilgi için [nesne hizmetlerine genel bakış (Entity Framework)](https://msdn.microsoft.com/library/43014cf9-c9cb-4538-bfbb-197820b60038).</span><span class="sxs-lookup"><span data-stu-id="e121e-114">For more information, see [Object Services Overview (Entity Framework)](https://msdn.microsoft.com/library/43014cf9-c9cb-4538-bfbb-197820b60038).</span></span>  
  
-   <span data-ttu-id="e121e-115">Veri sınıfları bulduğu veri modeli türleri için hizmet meta verileri içinde oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e121e-115">Generates data classes for the data model types that it discovers in the service metadata.</span></span>  
  
-   <span data-ttu-id="e121e-116">Bir başvuru ekler `System.Data.Services.Client` projeyi derlemeye.</span><span class="sxs-lookup"><span data-stu-id="e121e-116">Adds a reference to the `System.Data.Services.Client` assembly to the project.</span></span>  
  
 <span data-ttu-id="e121e-117">Daha fazla bilgi için [nasıl yapılır: bir veri hizmeti başvurusu ekleme](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="e121e-117">For more information, see [How to: Add a Data Service Reference](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="e121e-118">İstemci veri hizmeti sınıfları kullanarak da oluşturulabilir [DataSvcUtil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) aracı komut isteminde.</span><span class="sxs-lookup"><span data-stu-id="e121e-118">The client data service classes can also be generated by using the [DataSvcUtil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) tool at the command prompt.</span></span> <span data-ttu-id="e121e-119">Daha fazla bilgi için [nasıl yapılır: el ile oluşturmak istemci veri hizmeti sınıfları](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="e121e-119">For more information, see [How to: Manually Generate Client Data Service Classes](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md).</span></span>  
  
## <a name="client-data-type-mapping"></a><span data-ttu-id="e121e-120">İstemci veri türü eşlemesi</span><span class="sxs-lookup"><span data-stu-id="e121e-120">Client Data Type Mapping</span></span>  
 <span data-ttu-id="e121e-121">Kullanırken **hizmet Başvurusu Ekle** Visual Studio'da iletişim kutusu veya `DataSvcUtil.exe` aracını temel alan istemci veri sınıfları oluşturmak için bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akışı, ilkel türleri .NET Framework veri türlerinin eşlenir aşağıdaki gibi veri modeli:</span><span class="sxs-lookup"><span data-stu-id="e121e-121">When you use the **Add Service Reference** dialog in Visual Studio or the `DataSvcUtil.exe` tool to generate client data classes that are based on an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed, the .NET Framework data types are mapped to the primitive types from the data model as follows:</span></span>  
  
|<span data-ttu-id="e121e-122">Veri modeli türü</span><span class="sxs-lookup"><span data-stu-id="e121e-122">Data model type</span></span>|<span data-ttu-id="e121e-123">.NET framework veri türü</span><span class="sxs-lookup"><span data-stu-id="e121e-123">.NET Framework data type</span></span>|  
|---------------------|------------------------------|  
|`Edm.Binary`|<span data-ttu-id="e121e-124"><xref:System.Byte>`[]`</span><span class="sxs-lookup"><span data-stu-id="e121e-124"><xref:System.Byte> `[]`</span></span>|  
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
  
 <span data-ttu-id="e121e-125">Daha fazla bilgi için [OData: ilkel veri türleri](https://go.microsoft.com/fwlink/?LinkId=186072).</span><span class="sxs-lookup"><span data-stu-id="e121e-125">For more information, see [OData: Primitive Data Types](https://go.microsoft.com/fwlink/?LinkId=186072).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e121e-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e121e-126">See Also</span></span>  
 [<span data-ttu-id="e121e-127">WCF Veri Hizmetleri İstemci Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="e121e-127">WCF Data Services Client Library</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 [<span data-ttu-id="e121e-128">Hızlı başlangıç</span><span class="sxs-lookup"><span data-stu-id="e121e-128">Quickstart</span></span>](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)
