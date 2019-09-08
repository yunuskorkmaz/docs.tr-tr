---
title: Veri hizmeti Istemci kitaplığı oluşturuluyor (WCF Veri Hizmetleri)
ms.date: 03/30/2017
helpviewer_keywords:
- client applications, WCF Data Services
- WCF Data Services, client library
- Add Service Reference dialog box
ms.assetid: 314077c1-ac10-47e1-bed4-940b5462359d
ms.openlocfilehash: d53f2d209d6fb0a6f3cadb96245338060ece87db
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780294"
---
# <a name="generating-the-data-service-client-library-wcf-data-services"></a><span data-ttu-id="957fa-102">Veri hizmeti Istemci kitaplığı oluşturuluyor (WCF Veri Hizmetleri)</span><span class="sxs-lookup"><span data-stu-id="957fa-102">Generating the Data Service Client Library (WCF Data Services)</span></span>
<span data-ttu-id="957fa-103">Öğesini uygulayan [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] bir veri hizmeti, [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akışın açığa çıkarılan veri modelini açıklayan bir hizmet meta verileri belgesi döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="957fa-103">A data service that implements the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] can return a service metadata document that describes the data model exposed by the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed.</span></span> <span data-ttu-id="957fa-104">Daha fazla bilgi için bkz [. OData: Hizmet meta verileri](https://go.microsoft.com/fwlink/?LinkId=186070)belgesi.</span><span class="sxs-lookup"><span data-stu-id="957fa-104">For more information, see [OData: Service Metadata Document](https://go.microsoft.com/fwlink/?LinkId=186070).</span></span> <span data-ttu-id="957fa-105">Visual Studio 'daki **hizmet başvurusu Ekle** iletişim kutusunu kullanarak tabanlı bir hizmete başvuru [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="957fa-105">You can use the **Add Service Reference** dialog in Visual Studio to add a reference to an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-based service.</span></span> <span data-ttu-id="957fa-106">Bu aracı, bir istemci projesinde bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akış tarafından döndürülen meta verilere başvuru eklemek için kullandığınızda, aşağıdaki eylemleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="957fa-106">When you use this tool to add a reference to the metadata returned by an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed in a client project, it performs the following actions:</span></span>  
  
- <span data-ttu-id="957fa-107">Veri hizmetinden hizmet meta veri belgesini ister ve döndürülen meta verileri yorumlar.</span><span class="sxs-lookup"><span data-stu-id="957fa-107">Requests the service metadata document from the data service and interprets the returned metadata.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="957fa-108">Döndürülen meta veriler, istemci projesinde bir. edmx dosyası olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="957fa-108">The returned metadata is stored in the client project as an .edmx file.</span></span> <span data-ttu-id="957fa-109">Bu. edmx dosyası, Entity Framework tarafından kullanılan bir. edmx dosyası biçiminde olmadığından Varlık Veri Modeli Tasarımcısı kullanılarak açılamaz.</span><span class="sxs-lookup"><span data-stu-id="957fa-109">This .edmx file cannot be opened by using the Entity Data Model designer because it does not have the same format an .edmx file used by the Entity Framework.</span></span> <span data-ttu-id="957fa-110">XML düzenleyicisini veya herhangi bir metin düzenleyicisini kullanarak bu meta veri dosyasını görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="957fa-110">You can view this metadata file by using the XML editor or any text editor.</span></span> <span data-ttu-id="957fa-111">Daha fazla bilgi için bkz [ \[. mc-edmx\]: Veri Hizmetleri paketleme biçimi](https://go.microsoft.com/fwlink/?LinkID=178833) belirtimi için varlık veri modeli</span><span class="sxs-lookup"><span data-stu-id="957fa-111">For more information, see the [\[MC-EDMX\]: Entity Data Model for Data Services Packaging Format](https://go.microsoft.com/fwlink/?LinkID=178833) specification</span></span>  
  
- <span data-ttu-id="957fa-112">Hizmetinden devralan <xref:System.Data.Services.Client.DataServiceContext>bir varlık kapsayıcı sınıfı olarak hizmetin temsilini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="957fa-112">Generates a representation of the service as an entity container class that inherits from <xref:System.Data.Services.Client.DataServiceContext>.</span></span> <span data-ttu-id="957fa-113">Oluşturulan bu varlık kapsayıcı sınıfı, Varlık Veri Modeli araçlarının oluşturduğu varlık kapsayıcısına benzer.</span><span class="sxs-lookup"><span data-stu-id="957fa-113">This generated entity container class resembles the entity container that the Entity Data Model tools generate.</span></span> <span data-ttu-id="957fa-114">Daha fazla bilgi için bkz. [nesne hizmetlerine genel bakış (Entity Framework)](https://docs.microsoft.com/previous-versions/bb386871(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="957fa-114">For more information, see [Object Services Overview (Entity Framework)](https://docs.microsoft.com/previous-versions/bb386871(v=vs.100)).</span></span>  
  
- <span data-ttu-id="957fa-115">Hizmet meta verilerinde bulduğu veri modeli türleri için veri sınıfları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="957fa-115">Generates data classes for the data model types that it discovers in the service metadata.</span></span>  
  
- <span data-ttu-id="957fa-116">Projeye `System.Data.Services.Client` derlemeye bir başvuru ekler.</span><span class="sxs-lookup"><span data-stu-id="957fa-116">Adds a reference to the `System.Data.Services.Client` assembly to the project.</span></span>  
  
 <span data-ttu-id="957fa-117">Daha fazla bilgi için [nasıl yapılır: Veri hizmeti başvurusu](how-to-add-a-data-service-reference-wcf-data-services.md)ekleyin.</span><span class="sxs-lookup"><span data-stu-id="957fa-117">For more information, see [How to: Add a Data Service Reference](how-to-add-a-data-service-reference-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="957fa-118">İstemci veri hizmeti sınıfları, komut isteminde [DataSvcUtil. exe](wcf-data-service-client-utility-datasvcutil-exe.md) Aracı kullanılarak da oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="957fa-118">The client data service classes can also be generated by using the [DataSvcUtil.exe](wcf-data-service-client-utility-datasvcutil-exe.md) tool at the command prompt.</span></span> <span data-ttu-id="957fa-119">Daha fazla bilgi için [nasıl yapılır: Istemci veri hizmeti sınıflarını](how-to-manually-generate-client-data-service-classes-wcf-data-services.md)el ile oluşturun.</span><span class="sxs-lookup"><span data-stu-id="957fa-119">For more information, see [How to: Manually Generate Client Data Service Classes](how-to-manually-generate-client-data-service-classes-wcf-data-services.md).</span></span>  
  
## <a name="client-data-type-mapping"></a><span data-ttu-id="957fa-120">İstemci veri türü eşleme</span><span class="sxs-lookup"><span data-stu-id="957fa-120">Client Data Type Mapping</span></span>  
 <span data-ttu-id="957fa-121">Visual Studio 'da **hizmet başvurusu Ekle** iletişim kutusunu veya `DataSvcUtil.exe` bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akışı temel alan istemci veri sınıfları oluşturmak için aracı kullandığınızda, .NET Framework veri türleri veri modelinden aşağıdaki gibi temel türler ile eşleştirilir:</span><span class="sxs-lookup"><span data-stu-id="957fa-121">When you use the **Add Service Reference** dialog in Visual Studio or the `DataSvcUtil.exe` tool to generate client data classes that are based on an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed, the .NET Framework data types are mapped to the primitive types from the data model as follows:</span></span>  
  
|<span data-ttu-id="957fa-122">Veri modeli türü</span><span class="sxs-lookup"><span data-stu-id="957fa-122">Data model type</span></span>|<span data-ttu-id="957fa-123">.NET Framework veri türü</span><span class="sxs-lookup"><span data-stu-id="957fa-123">.NET Framework data type</span></span>|  
|---------------------|------------------------------|  
|`Edm.Binary`|<span data-ttu-id="957fa-124"><xref:System.Byte>`[]`</span><span class="sxs-lookup"><span data-stu-id="957fa-124"><xref:System.Byte> `[]`</span></span>|  
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
  
 <span data-ttu-id="957fa-125">Daha fazla bilgi için bkz [. OData: İlkel veri türleri](https://go.microsoft.com/fwlink/?LinkId=186072).</span><span class="sxs-lookup"><span data-stu-id="957fa-125">For more information, see [OData: Primitive Data Types](https://go.microsoft.com/fwlink/?LinkId=186072).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="957fa-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="957fa-126">See also</span></span>

- [<span data-ttu-id="957fa-127">WCF Veri Hizmetleri İstemci Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="957fa-127">WCF Data Services Client Library</span></span>](wcf-data-services-client-library.md)
- [<span data-ttu-id="957fa-128">Hızlı başlangıç</span><span class="sxs-lookup"><span data-stu-id="957fa-128">Quickstart</span></span>](quickstart-wcf-data-services.md)
