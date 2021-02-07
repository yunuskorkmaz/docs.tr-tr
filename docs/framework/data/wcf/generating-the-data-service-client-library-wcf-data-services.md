---
description: 'Hakkında daha fazla bilgi edinin: veri hizmeti Istemci kitaplığı oluşturma (WCF Veri Hizmetleri)'
title: Veri hizmeti Istemci kitaplığı oluşturuluyor (WCF Veri Hizmetleri)
ms.date: 03/30/2017
helpviewer_keywords:
- client applications, WCF Data Services
- WCF Data Services, client library
- Add Service Reference dialog box
ms.assetid: 314077c1-ac10-47e1-bed4-940b5462359d
ms.openlocfilehash: 3bac2459044ff910c8085ff56e60d9da6e0ba877
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99765938"
---
# <a name="generating-the-data-service-client-library-wcf-data-services"></a>Veri hizmeti Istemci kitaplığı oluşturuluyor (WCF Veri Hizmetleri)

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

Açık Veri Protokolü 'Nü (OData) uygulayan bir veri hizmeti, OData akışı tarafından sunulan veri modelini açıklayan bir hizmet meta verileri belgesi döndürebilir. Daha fazla bilgi için [OData: genel bakış](https://www.odata.org/documentation/odata-version-2-0/overview/) makalesindeki hizmet meta verileri belgesi bölümüne bakın. OData tabanlı bir hizmete başvuru eklemek için Visual Studio 'daki **hizmet başvurusu Ekle** iletişim kutusunu kullanabilirsiniz. İstemci projesindeki bir OData akışı tarafından döndürülen meta verilere başvuru eklemek için bu aracı kullandığınızda, aşağıdaki eylemleri gerçekleştirir:  
  
- Veri hizmetinden hizmet meta veri belgesini ister ve döndürülen meta verileri yorumlar.  
  
    > [!NOTE]
    > Döndürülen meta veriler, istemci projesinde bir. edmx dosyası olarak depolanır. Bu. edmx dosyası, Entity Framework tarafından kullanılan bir. edmx dosyası biçiminde olmadığından Varlık Veri Modeli Tasarımcısı kullanılarak açılamaz. XML düzenleyicisini veya herhangi bir metin düzenleyicisini kullanarak bu meta veri dosyasını görüntüleyebilirsiniz. Daha fazla bilgi için bkz. [ \[ mc-EDMX \] : varlık veri modeli Data Services paketleme biçimi için](/openspecs/windows_protocols/mc-edmx/5dff5e25-56a1-408b-9d44-bff6634c7d16).
  
- Hizmetinden devralan bir varlık kapsayıcı sınıfı olarak hizmetin temsilini oluşturur <xref:System.Data.Services.Client.DataServiceContext> . Oluşturulan bu varlık kapsayıcı sınıfı, Varlık Veri Modeli araçlarının oluşturduğu varlık kapsayıcısına benzer. Daha fazla bilgi için bkz. [nesne hizmetlerine genel bakış (Entity Framework)](/previous-versions/bb386871(v=vs.100)).  
  
- Hizmet meta verilerinde bulduğu veri modeli türleri için veri sınıfları oluşturur.  
  
- Projeye derlemeye bir başvuru ekler `System.Data.Services.Client` .  
  
 Daha fazla bilgi için bkz. [nasıl yapılır: veri hizmeti başvurusu ekleme](how-to-add-a-data-service-reference-wcf-data-services.md).  
  
 İstemci veri hizmeti sınıfları, komut isteminde [DataSvcUtil.exe](wcf-data-service-client-utility-datasvcutil-exe.md) Aracı kullanılarak da oluşturulabilir. Daha fazla bilgi için bkz. [nasıl yapılır: El Ile Istemci veri hizmeti sınıfları oluşturma](how-to-manually-generate-client-data-service-classes-wcf-data-services.md).  
  
## <a name="client-data-type-mapping"></a>İstemci veri türü eşleme  

 Visual Studio 'da **hizmet başvurusu Ekle** iletişim kutusunu veya `DataSvcUtil.exe` bir OData akışını temel alan istemci veri sınıfları oluşturmak için aracı kullandığınızda, .NET Framework veri türleri, veri modelindeki temel türlere aşağıdaki gibi eşlenir:  
  
|Veri modeli türü|.NET Framework veri türü|  
|---------------------|------------------------------|  
|`Edm.Binary`|<xref:System.Byte> `[]`|  
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
  
 Daha fazla bilgi için [OData: genel bakış](https://www.odata.org/documentation/odata-version-2-0/overview/) makalesindeki temel veri türleri bölümüne bakın.
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri İstemci Kitaplığı](wcf-data-services-client-library.md)
- [Hızlı Başlangıç](quickstart-wcf-data-services.md)
