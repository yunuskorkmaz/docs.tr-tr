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
# <a name="generating-the-data-service-client-library-wcf-data-services"></a>Veri Hizmeti istemci kitaplığı (WCF Veri Hizmetleri) oluşturma
Arabirimini uygulayan bir veri hizmeti [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] tarafından sunulan veri modeli açıklayan bir hizmeti meta veri belgesi döndürebilir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akış. Daha fazla bilgi için bkz: [OData: hizmeti meta veri belgesi](http://go.microsoft.com/fwlink/?LinkId=186070). Kullanabileceğiniz **hizmet Başvurusu Ekle** iletişim için bir başvuru eklemek için Visual Studio'da bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-hizmet tabanlı. Kullandığınızda, bu aracı tarafından döndürülen meta veriler için bir başvuru eklemek için bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] istemci projede akış, aşağıdaki eylemleri gerçekleştirir:  
  
-   Veri hizmetinden veri hizmeti meta veri belgesi ister ve döndürülen meta veri yorumlar.  
  
    > [!NOTE]
    >  Döndürülen meta veri istemci projesinde bir .edmx dosyası olarak depolanır. Entity Framework tarafından kullanılan bir .edmx dosyasının biçimlendirmek aynı olmadığı için varlık veri modeli Tasarımcısı'nı kullanarak bu .edmx dosyasının açılamaz. Bu meta veri dosyası, herhangi bir metin düzenleyicisi veya XML düzenleyicisi kullanarak görüntüleyebilirsiniz. Daha fazla bilgi için bkz: [ \[MC EDMX\]: Varlık veri modeli için Veri Hizmetleri paketleme biçimi](http://go.microsoft.com/fwlink/?LinkID=178833) belirtimi  
  
-   Hizmet bir gösterimini devralan bir varlık kapsayıcı sınıfı olarak oluşturur <xref:System.Data.Services.Client.DataServiceContext>. Bu oluşturulan varlık kapsayıcı sınıfı varlık veri modeli araçları varlık kapsayıcıya benzer. Daha fazla bilgi için bkz: [nesne Hizmetleri'ne Genel Bakış (Entity Framework)](http://msdn.microsoft.com/library/43014cf9-c9cb-4538-bfbb-197820b60038).  
  
-   Hizmet meta verilerde bulduğu veri modeli türleri için veri sınıfları oluşturur.  
  
-   Bir başvuru ekler `System.Data.Services.Client` projeye derleme.  
  
 Daha fazla bilgi için bkz: [nasıl yapılır: bir veri hizmet Başvurusu Ekle](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).  
  
 İstemci veri hizmeti sınıflarını kullanarak da oluşturulabilir [DataSvcUtil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) aracı komut isteminde. Daha fazla bilgi için bkz: [nasıl yapılır: el ile oluşturmak istemci veri hizmeti sınıfları](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md).  
  
## <a name="client-data-type-mapping"></a>İstemci veri türü eşlemesi  
 Kullandığınızda **hizmet Başvurusu Ekle** Visual Studio'da iletişim kutusu veya `DataSvcUtil.exe` temel alan istemci veri sınıfları oluşturmak için aracı bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akış, ilkel türler .NET Framework Veri türlerin eşlendiği aşağıdaki gibi veri modeli:  
  
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
  
 Daha fazla bilgi için bkz: [OData: Basit veri türleri](http://go.microsoft.com/fwlink/?LinkId=186072).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Veri Hizmetleri İstemci Kitaplığı](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 [Hızlı başlangıç](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)
