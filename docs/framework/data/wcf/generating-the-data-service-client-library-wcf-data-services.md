---
title: Veri hizmeti Istemci kitaplığı oluşturuluyor (WCF Veri Hizmetleri)
ms.date: 03/30/2017
helpviewer_keywords:
- client applications, WCF Data Services
- WCF Data Services, client library
- Add Service Reference dialog box
ms.assetid: 314077c1-ac10-47e1-bed4-940b5462359d
ms.openlocfilehash: 14ea550715c1b224945137f123eed3b53e56cead
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918647"
---
# <a name="generating-the-data-service-client-library-wcf-data-services"></a>Veri hizmeti Istemci kitaplığı oluşturuluyor (WCF Veri Hizmetleri)
Öğesini uygulayan [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] bir veri hizmeti, [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akışın açığa çıkarılan veri modelini açıklayan bir hizmet meta verileri belgesi döndürebilir. Daha fazla bilgi için bkz [. OData: Hizmet meta verileri](https://go.microsoft.com/fwlink/?LinkId=186070)belgesi. Visual Studio 'daki **hizmet başvurusu Ekle** iletişim kutusunu kullanarak tabanlı bir hizmete başvuru [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]ekleyebilirsiniz. Bu aracı, bir istemci projesinde bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akış tarafından döndürülen meta verilere başvuru eklemek için kullandığınızda, aşağıdaki eylemleri gerçekleştirir:  
  
- Veri hizmetinden hizmet meta veri belgesini ister ve döndürülen meta verileri yorumlar.  
  
    > [!NOTE]
    > Döndürülen meta veriler, istemci projesinde bir. edmx dosyası olarak depolanır. Bu. edmx dosyası, Entity Framework tarafından kullanılan bir. edmx dosyası biçiminde olmadığından Varlık Veri Modeli Tasarımcısı kullanılarak açılamaz. XML düzenleyicisini veya herhangi bir metin düzenleyicisini kullanarak bu meta veri dosyasını görüntüleyebilirsiniz. Daha fazla bilgi için bkz [ \[. mc-edmx\]: Veri Hizmetleri paketleme biçimi](https://go.microsoft.com/fwlink/?LinkID=178833) belirtimi için varlık veri modeli  
  
- Hizmetinden devralan <xref:System.Data.Services.Client.DataServiceContext>bir varlık kapsayıcı sınıfı olarak hizmetin temsilini oluşturur. Oluşturulan bu varlık kapsayıcı sınıfı, Varlık Veri Modeli araçlarının oluşturduğu varlık kapsayıcısına benzer. Daha fazla bilgi için bkz. [nesne hizmetlerine genel bakış (Entity Framework)](https://docs.microsoft.com/previous-versions/bb386871(v=vs.100)).  
  
- Hizmet meta verilerinde bulduğu veri modeli türleri için veri sınıfları oluşturur.  
  
- Projeye `System.Data.Services.Client` derlemeye bir başvuru ekler.  
  
 Daha fazla bilgi için [nasıl yapılır: Veri hizmeti başvurusu](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)ekleyin.  
  
 İstemci veri hizmeti sınıfları, komut isteminde [DataSvcUtil. exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) Aracı kullanılarak da oluşturulabilir. Daha fazla bilgi için [nasıl yapılır: Istemci veri hizmeti sınıflarını](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md)el ile oluşturun.  
  
## <a name="client-data-type-mapping"></a>İstemci veri türü eşleme  
 Visual Studio 'da **hizmet başvurusu Ekle** iletişim kutusunu veya `DataSvcUtil.exe` bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akışı temel alan istemci veri sınıfları oluşturmak için aracı kullandığınızda, .NET Framework veri türleri veri modelinden aşağıdaki gibi temel türler ile eşleştirilir:  
  
|Veri modeli türü|.NET Framework veri türü|  
|---------------------|------------------------------|  
|`Edm.Binary`|<xref:System.Byte>`[]`|  
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
  
 Daha fazla bilgi için bkz [. OData: İlkel veri türleri](https://go.microsoft.com/fwlink/?LinkId=186072).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri İstemci Kitaplığı](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
- [Hızlı başlangıç](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)
