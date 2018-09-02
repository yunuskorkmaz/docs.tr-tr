---
title: Veri Hizmeti istemci Kitaplığı'nı (WCF Veri Hizmetleri) oluşturma
ms.date: 03/30/2017
helpviewer_keywords:
- client applications, WCF Data Services
- WCF Data Services, client library
- Add Service Reference dialog box
ms.assetid: 314077c1-ac10-47e1-bed4-940b5462359d
ms.openlocfilehash: 170f9714f3cfbf2350423f28316d665d427fd56e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43389380"
---
# <a name="generating-the-data-service-client-library-wcf-data-services"></a>Veri Hizmeti istemci Kitaplığı'nı (WCF Veri Hizmetleri) oluşturma
Uygulayan bir veri hizmeti [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] tarafından kullanıma sunulan veri modeli açıklayan bir hizmeti meta veri belgesi döndürebilir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akış. Daha fazla bilgi için [OData: hizmet meta verileri belgesi](https://go.microsoft.com/fwlink/?LinkId=186070). Kullanabileceğiniz **hizmet Başvurusu Ekle** iletişim için bir başvuru eklemek için Visual Studio'da bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-hizmet tabanlı. Tarafından döndürülen meta veriler için bir başvuru eklemek için bu aracı kullanırken bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] istemci projesinde akışı, aşağıdaki eylemleri gerçekleştirir:  
  
-   Hizmet meta verileri belgesi veri hizmetinden ister ve döndürülen meta verilere yorumlar.  
  
    > [!NOTE]
    >  Döndürülen meta verilere istemci projesinde bir .edmx dosyası olarak depolanır. Entity Framework tarafından kullanılan bir .edmx dosyası biçim aynı olmadığı için varlık veri modeli Tasarımcısı'nı kullanarak bu .edmx dosyası açılamıyor. Bu meta veri dosyası, herhangi bir metin düzenleyicisi veya XML düzenleyicisi kullanarak görüntüleyebilirsiniz. Daha fazla bilgi için [ \[MC EDMX\]: Varlık veri modeli için veri hizmetlerini paketleme biçimini](https://go.microsoft.com/fwlink/?LinkID=178833) belirtimi  
  
-   Hizmet bir temsili olarak devraldığı bir varlık kapsayıcı sınıfı oluşturur <xref:System.Data.Services.Client.DataServiceContext>. Bu oluşturulan varlık kapsayıcı sınıfı, varlık veri modeli araçları oluşturan varlık kapsayıcısı benzer. Daha fazla bilgi için [nesne hizmetlerine genel bakış (Entity Framework)](https://msdn.microsoft.com/library/43014cf9-c9cb-4538-bfbb-197820b60038).  
  
-   Veri sınıfları bulduğu veri modeli türleri için hizmet meta verileri içinde oluşturur.  
  
-   Bir başvuru ekler `System.Data.Services.Client` projeyi derlemeye.  
  
 Daha fazla bilgi için [nasıl yapılır: bir veri hizmeti başvurusu ekleme](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).  
  
 İstemci veri hizmeti sınıfları kullanarak da oluşturulabilir [DataSvcUtil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) aracı komut isteminde. Daha fazla bilgi için [nasıl yapılır: el ile oluşturmak istemci veri hizmeti sınıfları](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md).  
  
## <a name="client-data-type-mapping"></a>İstemci veri türü eşlemesi  
 Kullanırken **hizmet Başvurusu Ekle** Visual Studio'da iletişim kutusu veya `DataSvcUtil.exe` aracını temel alan istemci veri sınıfları oluşturmak için bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akışı, ilkel türleri .NET Framework veri türlerinin eşlenir aşağıdaki gibi veri modeli:  
  
|Veri modeli türü|.NET framework veri türü|  
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
  
 Daha fazla bilgi için [OData: ilkel veri türleri](https://go.microsoft.com/fwlink/?LinkId=186072).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Veri Hizmetleri İstemci Kitaplığı](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 [Hızlı başlangıç](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)
