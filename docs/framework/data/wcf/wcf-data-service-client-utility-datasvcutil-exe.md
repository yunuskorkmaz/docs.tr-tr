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
ms.workload: dotnet
ms.openlocfilehash: fcbbbe5180acaf943956310d4837a105d8d049d7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="wcf-data-service-client-utility-datasvcutilexe"></a>WCF veri hizmeti istemci yardımcı programı (DataSvcUtil.exe)
DataSvcUtil.exe tarafından sağlanan bir komut satırı aracıdır [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] , tüketir bir [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] akış ve veri hizmeti .NET Framework istemci uygulamasından erişmek için gerekli istemci veri hizmeti sınıfları oluşturur. Bu yardımcı programı, aşağıdaki meta veri kaynakları kullanarak veri sınıfları oluşturabilirsiniz:  
  
-   Veri Hizmeti URI kökü. Yardımcı programı veri hizmeti tarafından sunulan veri modeli açıklayan hizmeti meta veri belgesi ister. Daha fazla bilgi için bkz: [OData: hizmeti meta veri belgesi](http://go.microsoft.com/fwlink/?LinkId=186070).  
  
-   Kavramsal şema tanım dili (CSDL) kullanılarak tanımlandığı şekilde tanımlanmış bir veri modeli dosyası (.csdl) [ \[MC CSDL\]: kavramsal şema tanım dosyası biçimi](http://go.microsoft.com/fwlink/?LinkID=159072) belirtimi.  
  
-   Entity Framework ile sağlanan varlık veri modeli araçları kullanılarak oluşturulan bir .edmx dosyasının. Daha fazla bilgi için bkz: [ \[MC EDMX\]: Varlık veri modeli için Veri Hizmetleri paketleme biçimi](http://go.microsoft.com/fwlink/?LinkID=178833) belirtimi.  
  
 Daha fazla bilgi için bkz: [nasıl yapılır: el ile oluşturmak istemci veri hizmeti sınıfları](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md).  
  
 DataSvcUtil.exe aracına [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dizin. Çoğu durumda bu C:\Windows\Microsoft.NET\Framework\v4.0 içinde bulunan. 64 bit sistemler için bu C:\Windows\Microsoft.NET\Framework64\v4.0 içinde bulunur. Visual Studio komut isteminden DataSvcUtil.exe aracı da erişebilirsiniz (tıklatın **Başlat**, işaret **tüm programlar**, işaret **Microsoft Visual Studio 2010**, işaret **Visual Studio Araçları**ve ardından **Visual Studio 2010 Komut İstemi**).  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
datasvcutil /out:file [/in:file | /uri:serviceuri] [/dataservicecollection] [/language:devlang] [/nologo] [/version:ver] [/help]  
```  
  
#### <a name="parameters"></a>Parametreler  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|`/dataservicecollection`|Denetimlere nesneleri bağlamak için gereken kod ayrıca oluşturulan belirtir.|  
|`/help`<br /><br /> veya<br /><br /> `/?`|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|`/in:` *\<dosyası >*|.Csdl veya .edmx dosyasının veya dosyanın bulunduğu dizini belirtir.|  
|`/language:`[VB &#124; CSharp]|Oluşturulan kaynak kodu dosyaları dilini belirtir. C# dil Varsayılanları.|  
|`/nologo`|Telif Hakkı görüntüleme iletiden gizler.|  
|`/out:` *\<dosyası >*|Oluşturulan istemci veri hizmeti sınıfları içeren kaynak kodu dosyasının adını belirtir.|  
|`/uri:` *\<dize >*|URI'sini [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akış.|  
|`/version:`[1.0&#124;2.0]|En yüksek kabul edilen sürümünü belirtir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]. Sürüm göre belirlenir `DataServiceVersion` döndürülen veri hizmeti meta verilerde DataService öğesinin özniteliği. Daha fazla bilgi için bkz: [veri hizmeti sürüm](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md). Belirttiğinizde `/dataservicecollection` parametresini de belirtmeniz gerekir `/version:2.0` veri bağlamasını etkinleştirmek için.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Hizmeti İstemci Kitaplığı Oluşturma](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)  
 [Nasıl yapılır: Veri Hizmeti Başvurusu Ekleme](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)
