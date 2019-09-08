---
title: Istemci uygulamasında bir veri hizmeti kullanma (WCF Veri Hizmetleri)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, getting started
ms.assetid: 90872d0c-e989-4490-b3e9-54afb10d33d4
ms.openlocfilehash: 050c1a67a367a6dd5175c535fe89fb0010ae8cbc
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790287"
---
# <a name="using-a-data-service-in-a-client-application-wcf-data-services"></a>Istemci uygulamasında bir veri hizmeti kullanma (WCF Veri Hizmetleri)
Bir Web tarayıcısına URI sağlayarak bir [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] akışı kullanıma sunan bir hizmete erişebilirsiniz. URI, bir kaynağın adresini sağlar ve isteğin gösterdiği temel verilere erişmek veya değiştirmek için bu adreslere gönderilen istek iletileri gönderilir. Tarayıcı bir http get komutu yayınlar ve istenen kaynağı bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akış olarak döndürür. Daha fazla bilgi için bkz. [bir Web tarayıcısından hizmete erişme](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).  
  
 Bir Web tarayıcısı, bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] hizmetin beklenen verileri döndürdüğü test etmek için yararlı olsa da, veri oluşturma, güncelleştirme ve silme işlemleri için genellikle uygulama kodu veya betik dilleri tarafından erişilen üretim hizmetleri [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] bir Web sayfasında. Bu konu, bir istemci uygulamasından akışlara erişme [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] hakkında genel bakış sağlar.  
  
## <a name="accessing-and-changing-data-using-rest-semantics"></a>REST semantiğini kullanarak verilere erişme ve verileri değiştirme  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]akışları kullanan [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akışlar ve uygulamalar [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] sunan hizmetler arasında birlikte çalışabilirlik garantisi sağlanmasına yardımcı olur. Uygulamalar, belirli bir http eyleminin istek [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]iletilerini ve eylemin gerçekleştirilmesi gereken bir varlık kaynağını adresleyen bir URI ile bir tabanlı hizmette verilere erişir ve bu verileri değiştirebilir. Varlık verileri sağlanmalı, iletinin gövdesinde özel olarak kodlanmış bir yük olarak sağlanır.  
  
### <a name="http-actions"></a>HTTP eylemleri  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)], çözümlenmiş kaynağın gösterdiği varlık verilerinde oluşturma, okuma, güncelleştirme ve silme işlemlerini gerçekleştirmek için aşağıdaki HTTP eylemlerini destekler:  
  
- **Http get** -bir tarayıcıdan bir kaynağa erişildiğinde bu varsayılan eylemdir. İstek iletisinde yük sağlanmadı ve istenen verileri içeren bir yük ile yanıt metodu döndürülür.  
  
- **Http post** -yeni varlık verilerini sağlanan kaynağa ekler. Eklenecek veriler istek iletisi yükünde sağlanır. Yanıt iletisinin yükü, yeni oluşturulan varlığa ilişkin verileri içerir. Bu, tüm otomatik oluşturulan anahtar değerlerini içerir. Üst bilgi ayrıca yeni varlık kaynağına adresleyen URI 'yi içerir.  
  
- **Http Delete** -belirtilen kaynağın temsil ettiği varlık verilerini siler. İstek veya yanıt iletilerinde yük yok.  
  
- **Http put** -istenen kaynaktaki mevcut varlık verilerini istek iletisi yükünde sağlanan yeni verilerle değiştirir.  
  
- **Http birleştirme** -yalnızca varlık verilerini [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] değiştirmek için veri kaynağındaki bir INSERT tarafından izlenen bir delete tarafından izlenen verimsizlikleri 'in yeni bir http birleştirme eylemi tanıtıldığı için. İstek iletisinin yükü, belirtilen varlık kaynağında değiştirilmesi gereken özellikleri içerir. Http belirtimi http belirtiminde tanımlanmadığı için, bir http birleştirme isteğini[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kullanmayan sunucular aracılığıyla yönlendirmek için ek işlem gerektirebilir.  
  
 Daha fazla bilgi için bkz [. OData: İşlemler](https://go.microsoft.com/fwlink/?LinkId=185792).  
  
### <a name="payload-formats"></a>Yük biçimleri  
 Bir HTTP PUT, HTTP POST veya HTTP MERGE isteği için, bir istek iletisinin yükü veri hizmetine göndereceğiniz varlık verilerini içerir. Yükün içeriği iletinin veri biçimine bağlıdır. SILME dışındaki tüm eylemlere yönelik HTTP yanıtları de böyle bir yük içerir. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]hizmeti ile erişmek ve verileri değiştirmek için aşağıdaki yük biçimlerini destekler:  
  
- **Atom** -Web akışları, Pod yayınları, wiksıs ve [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] XML tabanlı Internet işlevselliği için http üzerinden veri değişimi etkinleştirmek üzere Atom yayımlama Protokolü 'nün (AtomPub) uzantısı olarak tanımlanan XML tabanlı bir ileti kodlaması. Daha fazla bilgi için bkz [. OData: Atom biçimi](https://go.microsoft.com/fwlink/?LinkId=185794).  
  
- **JSON** -JAVASCRIPT nesne GÖSTERIMI (JSON), JavaScript programlama dilinin bir alt kümesini temel alan hafif bir veri değişim biçimidir. Daha fazla bilgi için bkz [. OData: JSON biçimi](https://go.microsoft.com/fwlink/?LinkId=185795).  
  
 Yükün ileti biçimi HTTP istek iletisi üstbilgisinde istendi. Daha fazla bilgi için bkz [. OData: İşlemler](https://go.microsoft.com/fwlink/?LinkID=185792).  
  
## <a name="accessing-and-changing-data-using-client-libraries"></a>Istemci kitaplıklarını kullanarak verilere erişme ve verileri değiştirme  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].NET Framework ve Silverlight tabanlı istemci uygulamalarından bir akışı daha kolay bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] şekilde kullanmanıza olanak tanıyan istemci kitaplıklarını içerir. Bu kitaplıklar HTTP iletileri göndermeyi ve almayı basitleştirir. Ayrıca, ileti yükünü varlık verilerini temsil eden CLR nesnelerine çevirirler. İstemci kitaplıkları iki çekirdek sınıfı <xref:System.Data.Services.Client.DataServiceContext> ve. <xref:System.Data.Services.Client.DataServiceQuery%601> Bu sınıflar bir veri hizmetini sorgulamanızı ve ardından döndürülen varlık verileriyle CLR nesneleri olarak çalışmanızı sağlar. Daha fazla bilgi için bkz. [WCF veri Hizmetleri Istemci kitaplığı](wcf-data-services-client-library.md) ve [WCF veri Hizmetleri (Silverlight)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc838234(v=vs.95)).  
  
 Bir veri hizmetine başvuru eklemek için Visual Studio 'daki **hizmet başvurusu Ekle** iletişim kutusunu kullanabilirsiniz. Bu araç, başvurulan bir veri hizmetinden hizmet meta verilerini ister ve bir veri <xref:System.Data.Services.Client.DataServiceContext> hizmetini temsil eden öğesini oluşturur, ayrıca varlıkları temsil eden istemci veri hizmeti sınıflarını oluşturur. Daha fazla bilgi için bkz. [veri hizmeti Istemci kitaplığı oluşturma](generating-the-data-service-client-library-wcf-data-services.md).  
  
 Başka türdeki istemci uygulamalarında bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akışı tüketmek için kullanabileceğiniz programlama kitaplıkları mevcuttur. Daha fazla bilgi için bkz. [OData SDK](https://go.microsoft.com/fwlink/?LinkId=185796).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Hizmeti Kaynaklarına Erişme](accessing-data-service-resources-wcf-data-services.md)
- [Hızlı başlangıç](quickstart-wcf-data-services.md)
