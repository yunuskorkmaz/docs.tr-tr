---
title: Veri hizmeti Istemci kitaplığı oluşturuluyor (WCF Veri Hizmetleri)
ms.date: 03/30/2017
helpviewer_keywords:
- client applications, WCF Data Services
- WCF Data Services, client library
- Add Service Reference dialog box
ms.assetid: 314077c1-ac10-47e1-bed4-940b5462359d
ms.openlocfilehash: f73ea93fe76f31c81935dbfb29183c247e41d8cd
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975280"
---
# <a name="generating-the-data-service-client-library-wcf-data-services"></a><span data-ttu-id="244a4-102">Veri hizmeti Istemci kitaplığı oluşturuluyor (WCF Veri Hizmetleri)</span><span class="sxs-lookup"><span data-stu-id="244a4-102">Generating the Data Service Client Library (WCF Data Services)</span></span>
<span data-ttu-id="244a4-103">Açık Veri Protokolü 'Nü (OData) uygulayan bir veri hizmeti, OData akışı tarafından sunulan veri modelini açıklayan bir hizmet meta verileri belgesi döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="244a4-103">A data service that implements the Open Data Protocol (OData) can return a service metadata document that describes the data model exposed by the OData feed.</span></span> <span data-ttu-id="244a4-104">Daha fazla bilgi için bkz. [OData: hizmet meta verileri belgesi](https://go.microsoft.com/fwlink/?LinkId=186070).</span><span class="sxs-lookup"><span data-stu-id="244a4-104">For more information, see [OData: Service Metadata Document](https://go.microsoft.com/fwlink/?LinkId=186070).</span></span> <span data-ttu-id="244a4-105">OData tabanlı bir hizmete başvuru eklemek için Visual Studio 'daki **hizmet başvurusu Ekle** iletişim kutusunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="244a4-105">You can use the **Add Service Reference** dialog in Visual Studio to add a reference to an OData-based service.</span></span> <span data-ttu-id="244a4-106">İstemci projesindeki bir OData akışı tarafından döndürülen meta verilere başvuru eklemek için bu aracı kullandığınızda, aşağıdaki eylemleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="244a4-106">When you use this tool to add a reference to the metadata returned by an OData feed in a client project, it performs the following actions:</span></span>  
  
- <span data-ttu-id="244a4-107">Veri hizmetinden hizmet meta veri belgesini ister ve döndürülen meta verileri yorumlar.</span><span class="sxs-lookup"><span data-stu-id="244a4-107">Requests the service metadata document from the data service and interprets the returned metadata.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="244a4-108">Döndürülen meta veriler, istemci projesinde bir. edmx dosyası olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="244a4-108">The returned metadata is stored in the client project as an .edmx file.</span></span> <span data-ttu-id="244a4-109">Bu. edmx dosyası, Entity Framework tarafından kullanılan bir. edmx dosyası biçiminde olmadığından Varlık Veri Modeli Tasarımcısı kullanılarak açılamaz.</span><span class="sxs-lookup"><span data-stu-id="244a4-109">This .edmx file cannot be opened by using the Entity Data Model designer because it does not have the same format an .edmx file used by the Entity Framework.</span></span> <span data-ttu-id="244a4-110">XML düzenleyicisini veya herhangi bir metin düzenleyicisini kullanarak bu meta veri dosyasını görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="244a4-110">You can view this metadata file by using the XML editor or any text editor.</span></span> <span data-ttu-id="244a4-111">Daha fazla bilgi için bkz [.\[mc-EDMX\]: varlık veri modeli veri Hizmetleri paketleme biçimi](https://go.microsoft.com/fwlink/?LinkID=178833) belirtimi</span><span class="sxs-lookup"><span data-stu-id="244a4-111">For more information, see the [\[MC-EDMX\]: Entity Data Model for Data Services Packaging Format](https://go.microsoft.com/fwlink/?LinkID=178833) specification</span></span>  
  
- <span data-ttu-id="244a4-112"><xref:System.Data.Services.Client.DataServiceContext>devralan bir varlık kapsayıcı sınıfı olarak hizmetin temsilini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="244a4-112">Generates a representation of the service as an entity container class that inherits from <xref:System.Data.Services.Client.DataServiceContext>.</span></span> <span data-ttu-id="244a4-113">Oluşturulan bu varlık kapsayıcı sınıfı, Varlık Veri Modeli araçlarının oluşturduğu varlık kapsayıcısına benzer.</span><span class="sxs-lookup"><span data-stu-id="244a4-113">This generated entity container class resembles the entity container that the Entity Data Model tools generate.</span></span> <span data-ttu-id="244a4-114">Daha fazla bilgi için bkz. [nesne hizmetlerine genel bakış (Entity Framework)](https://docs.microsoft.com/previous-versions/bb386871(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="244a4-114">For more information, see [Object Services Overview (Entity Framework)](https://docs.microsoft.com/previous-versions/bb386871(v=vs.100)).</span></span>  
  
- <span data-ttu-id="244a4-115">Hizmet meta verilerinde bulduğu veri modeli türleri için veri sınıfları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="244a4-115">Generates data classes for the data model types that it discovers in the service metadata.</span></span>  
  
- <span data-ttu-id="244a4-116">Projeye `System.Data.Services.Client` derlemesine bir başvuru ekler.</span><span class="sxs-lookup"><span data-stu-id="244a4-116">Adds a reference to the `System.Data.Services.Client` assembly to the project.</span></span>  
  
 <span data-ttu-id="244a4-117">Daha fazla bilgi için bkz. [nasıl yapılır: veri hizmeti başvurusu ekleme](how-to-add-a-data-service-reference-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="244a4-117">For more information, see [How to: Add a Data Service Reference](how-to-add-a-data-service-reference-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="244a4-118">İstemci veri hizmeti sınıfları, komut isteminde [DataSvcUtil. exe](wcf-data-service-client-utility-datasvcutil-exe.md) Aracı kullanılarak da oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="244a4-118">The client data service classes can also be generated by using the [DataSvcUtil.exe](wcf-data-service-client-utility-datasvcutil-exe.md) tool at the command prompt.</span></span> <span data-ttu-id="244a4-119">Daha fazla bilgi için bkz. [nasıl yapılır: El Ile Istemci veri hizmeti sınıfları oluşturma](how-to-manually-generate-client-data-service-classes-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="244a4-119">For more information, see [How to: Manually Generate Client Data Service Classes](how-to-manually-generate-client-data-service-classes-wcf-data-services.md).</span></span>  
  
## <a name="client-data-type-mapping"></a><span data-ttu-id="244a4-120">İstemci veri türü eşleme</span><span class="sxs-lookup"><span data-stu-id="244a4-120">Client Data Type Mapping</span></span>  
 <span data-ttu-id="244a4-121">Bir OData akışına dayalı istemci veri sınıfları oluşturmak için Visual Studio 'daki **hizmet başvurusu Ekle** iletişim kutusunu veya `DataSvcUtil.exe` aracını kullandığınızda, .NET Framework veri türleri veri modelinden temel alınan türlere aşağıdaki gibi eşlenir:</span><span class="sxs-lookup"><span data-stu-id="244a4-121">When you use the **Add Service Reference** dialog in Visual Studio or the `DataSvcUtil.exe` tool to generate client data classes that are based on an OData feed, the .NET Framework data types are mapped to the primitive types from the data model as follows:</span></span>  
  
|<span data-ttu-id="244a4-122">Veri modeli türü</span><span class="sxs-lookup"><span data-stu-id="244a4-122">Data model type</span></span>|<span data-ttu-id="244a4-123">.NET Framework veri türü</span><span class="sxs-lookup"><span data-stu-id="244a4-123">.NET Framework data type</span></span>|  
|---------------------|------------------------------|  
|`Edm.Binary`|<span data-ttu-id="244a4-124"><xref:System.Byte>`[]`</span><span class="sxs-lookup"><span data-stu-id="244a4-124"><xref:System.Byte> `[]`</span></span>|  
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
  
 <span data-ttu-id="244a4-125">Daha fazla bilgi için bkz. [OData: Ilkel veri türleri](https://go.microsoft.com/fwlink/?LinkId=186072).</span><span class="sxs-lookup"><span data-stu-id="244a4-125">For more information, see [OData: Primitive Data Types](https://go.microsoft.com/fwlink/?LinkId=186072).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="244a4-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="244a4-126">See also</span></span>

- [<span data-ttu-id="244a4-127">WCF Veri Hizmetleri İstemci Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="244a4-127">WCF Data Services Client Library</span></span>](wcf-data-services-client-library.md)
- [<span data-ttu-id="244a4-128">Hızlı başlangıç</span><span class="sxs-lookup"><span data-stu-id="244a4-128">Quickstart</span></span>](quickstart-wcf-data-services.md)
