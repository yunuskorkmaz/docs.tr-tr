---
title: Istemci uygulamasında bir veri hizmeti kullanma (WCF Veri Hizmetleri)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, getting started
ms.assetid: 90872d0c-e989-4490-b3e9-54afb10d33d4
ms.openlocfilehash: 49e5ad2e6ae3dc50a0f48fcc3df2f7ec49ed7f88
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544407"
---
# <a name="using-a-data-service-in-a-client-application-wcf-data-services"></a>Istemci uygulamasında bir veri hizmeti kullanma (WCF Veri Hizmetleri)
Bir Web tarayıcısına URI sağlayarak açık veri Protokolü (OData) akışı sunan bir hizmete erişebilirsiniz. URI, bir kaynağın adresini sağlar ve isteğin gösterdiği temel verilere erişmek veya değiştirmek için bu adreslere gönderilen istek iletileri gönderilir. Tarayıcı bir HTTP GET komutu yayınlar ve istenen kaynağı OData akışı olarak döndürür. Daha fazla bilgi için bkz. [bir Web tarayıcısından hizmete erişme](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).  
  
 Bir OData hizmetinin beklenen verileri döndürdüğü test için bir Web tarayıcısı yararlı olsa da, bir Web sayfasındaki uygulama kodu veya komut dosyası dilleri tarafından da oluşturmanız, güncelleştirmeniz ve silmeniz sağlayan üretim OData Hizmetleri de genellikle erişilebilir. Bu konu, bir istemci uygulamasından OData akışlarına erişme hakkında genel bakış sağlar.  
  
## <a name="accessing-and-changing-data-using-rest-semantics"></a>REST semantiğini kullanarak verilere erişme ve verileri değiştirme  
 OData, OData akışlarını kullanan hizmetler ve OData akışlarını kullanan uygulamalar arasında birlikte çalışabilirlik sağlanmasına yardımcı olur. Uygulamalar, belirli bir HTTP eyleminin istek iletilerini ve eylemin gerçekleştirilmesi gereken bir varlık kaynağını adresleyen bir URI ile bir OData tabanlı hizmette verilere erişir ve verileri değiştirebilir. Varlık verileri sağlanmalı, iletinin gövdesinde özel olarak kodlanmış bir yük olarak sağlanır.  
  
### <a name="http-actions"></a>HTTP eylemleri  
 OData, belirtilen kaynağın gösterdiği varlık verilerinde oluşturma, okuma, güncelleştirme ve silme işlemlerini gerçekleştirmek için aşağıdaki HTTP eylemlerini destekler:  
  
- **Http get** -bir tarayıcıdan bir kaynağa erişildiğinde bu varsayılan eylemdir. İstek iletisinde yük sağlanmadı ve istenen verileri içeren bir yük ile yanıt metodu döndürülür.  
  
- **Http post** -yeni varlık verilerini sağlanan kaynağa ekler. Eklenecek veriler istek iletisi yükünde sağlanır. Yanıt iletisinin yükü, yeni oluşturulan varlığa ilişkin verileri içerir. Bu, tüm otomatik oluşturulan anahtar değerlerini içerir. Üst bilgi ayrıca yeni varlık kaynağına adresleyen URI 'yi içerir.  
  
- **Http Delete** -belirtilen kaynağın temsil ettiği varlık verilerini siler. İstek veya yanıt iletilerinde yük yok.  
  
- **Http put** -istenen kaynaktaki mevcut varlık verilerini istek iletisi yükünde sağlanan yeni verilerle değiştirir.  
  
- **Http birleştirme** -bir DELETE ' ın yürütüldüğü ve ardından veri kaynağındaki bir INSERT tarafından yalnızca varlık verilerini değiştirmek Için, OData yenı bır http birleştirme eylemi sunmuştur. İstek iletisinin yükü, belirtilen varlık kaynağında değiştirilmesi gereken özellikleri içerir. Http belirtimi http belirtiminde tanımlanmadığı için, bir HTTP BIRLEŞTIRME isteğini OData ile uyumlu olmayan sunucular aracılığıyla yönlendirmek için ek işleme gerekebilir.  
  
 Daha fazla bilgi için bkz. [OData: Operations](https://www.odata.org/documentation/odata-version-2-0/operations/).
  
### <a name="payload-formats"></a>Yük biçimleri  
 Bir HTTP PUT, HTTP POST veya HTTP MERGE isteği için, bir istek iletisinin yükü veri hizmetine göndereceğiniz varlık verilerini içerir. Yükün içeriği iletinin veri biçimine bağlıdır. SILME dışındaki tüm eylemlere yönelik HTTP yanıtları de böyle bir yük içerir. OData, hizmete erişmek ve verileri değiştirmek için aşağıdaki yük biçimlerini destekler:  
  
- **Atom** -Web akışları, Pod yayınları, WIKSıS ve XML tabanlı Internet IŞLEVSELLIĞI için http üzerinden veri değişimi sağlamak üzere OData tarafından Atom yayımlama Protokolü (AtomPub) uzantısı olarak tanımlanan XML tabanlı bir ileti kodlaması. Daha fazla bilgi için bkz. [OData: Atom biçimi](https://www.odata.org/documentation/odata-version-2-0/atom-format/).
  
- **JSON** -JAVASCRIPT nesne GÖSTERIMI (JSON), JavaScript programlama dilinin bir alt kümesini temel alan hafif bir veri değişim biçimidir. Daha fazla bilgi için bkz. [OData: JSON biçimi](https://www.odata.org/documentation/odata-version-2-0/json-format/).
  
 Yükün ileti biçimi HTTP istek iletisi üstbilgisinde istendi. Daha fazla bilgi için bkz. [OData: Operations](https://www.odata.org/documentation/odata-version-2-0/operations/).
  
## <a name="accessing-and-changing-data-using-client-libraries"></a>Istemci kitaplıklarını kullanarak verilere erişme ve verileri değiştirme  
 WCF Veri Hizmetleri, .NET Framework ve Silverlight tabanlı istemci uygulamalarından bir OData akışını daha kolay bir şekilde kullanmanıza olanak tanıyan istemci kitaplıklarını içerir. Bu kitaplıklar HTTP iletileri göndermeyi ve almayı basitleştirir. Ayrıca, ileti yükünü varlık verilerini temsil eden CLR nesnelerine çevirirler. İstemci kitaplıkları iki çekirdek sınıfı <xref:System.Data.Services.Client.DataServiceContext> ve <xref:System.Data.Services.Client.DataServiceQuery%601> . Bu sınıflar bir veri hizmetini sorgulamanızı ve ardından döndürülen varlık verileriyle CLR nesneleri olarak çalışmanızı sağlar. Daha fazla bilgi için bkz. [WCF veri Hizmetleri Istemci kitaplığı](wcf-data-services-client-library.md) ve [WCF veri Hizmetleri (Silverlight)](/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc838234(v=vs.95)).  
  
 Bir veri hizmetine başvuru eklemek için Visual Studio 'daki **hizmet başvurusu Ekle** iletişim kutusunu kullanabilirsiniz. Bu araç, başvurulan bir veri hizmetinden hizmet meta verilerini ister ve <xref:System.Data.Services.Client.DataServiceContext> bir veri hizmetini temsil eden öğesini oluşturur, ayrıca varlıkları temsil eden istemci veri hizmeti sınıflarını oluşturur. Daha fazla bilgi için bkz. [veri hizmeti Istemci kitaplığı oluşturma](generating-the-data-service-client-library-wcf-data-services.md).  
  
 Diğer istemci uygulamalarında bir OData akışını tüketmek için kullanabileceğiniz programlama kitaplıkları mevcuttur. OData SDK hakkında daha fazla bilgi için bkz. [OData SDK-örnek kodu](https://www.odata.org/ecosystem/#sdk).
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Hizmeti Kaynaklarına Erişme](accessing-data-service-resources-wcf-data-services.md)
- [Hızlı Başlangıç](quickstart-wcf-data-services.md)
