---
title: Bir veri hizmeti istemci uygulaması (WCF Veri Hizmetleri) kullanma
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, getting started
ms.assetid: 90872d0c-e989-4490-b3e9-54afb10d33d4
ms.openlocfilehash: 092f073a138a09fc25b96fbddde5b73992056981
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44087789"
---
# <a name="using-a-data-service-in-a-client-application-wcf-data-services"></a>Bir veri hizmeti istemci uygulaması (WCF Veri Hizmetleri) kullanma
Kullanıma sunan bir hizmet erişebileceğiniz bir [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] bir URI ile bir Web tarayıcısı sağlanarak akış. Bir kaynak adresi URI sağlar ve istek iletilerinin erişmek veya kaynak temsil eden temel alınan verileri değiştirmek için bu adrese gönderilir. Tarayıcı bir HTTP GET komutu çalıştırır ve istenen kaynak olarak döndüren bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akış. Daha fazla bilgi için [bir Web tarayıcısından hizmete erişim](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).  
  
 Bir Web tarayıcısı, test etmek için yararlı olabilir ancak bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] hizmeti döndürür beklenen verileri, üretim [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] ayrıca oluşturmanıza olanak sağlayan Hizmetleri güncelleştirin ve verileri silmek uygulama kodu tarafından genel olarak erişilen veya dil komut dosyası bir Web sayfasında. Bu konu nasıl erişmek genel bir bakış sağlar [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] bir istemci uygulamasından akışları.  
  
## <a name="accessing-and-changing-data-using-rest-semantics"></a>Erişim ve REST semantiği kullanarak verileri değiştirme  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] yardımcı garanti açığa çıkaran hizmetler arasında birlikte çalışabilirlik [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akışları ve kullanan uygulamaları [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akışları. Uygulama erişimi ve verileri değiştirme bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-belirli bir HTTP eylemi ve karşı eyleme gerçekleştirilmelidir bir varlık kaynağı ele alan bir URI ile istek iletiler göndererek hizmet tabanlı. Varlık verilerini sağlanmalıdır, ileti gövdesinde özel olarak kodlanmış bir yükü olarak sağlanır.  
  
### <a name="http-actions"></a>HTTP eylemleri  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] destekler gerçekleştirmek için aşağıdaki HTTP eylemleri oluşturma, okuma, güncelleştirme ve silme işlemleri adresli kaynak temsil eden varlık verileri üzerinde:  
  
-   **HTTP GET** -bir kaynak bir tarayıcıdan erişildiğinde bu varsayılan değerdir. Yükü yok istek iletisinde sağlanır ve istenen veriler içeren bir yükü yanıt yöntemiyle döndürülür.  
  
-   **HTTP POST** -sağlanan kaynak içinde yeni varlık verilerini ekler. İstek iletisinin yükteki eklenecek veri sağlanır. Yanıt iletisinin yükü, yeni oluşturulan varlığın verilerini içerir. Bu, herhangi bir otomatik olarak oluşturulan anahtar değeri içerir. Üst bilgi de ele alan yeni varlık Kaynak URI içeriyor.  
  
-   **HTTP DELETE** -belirtilen kaynak temsil eden varlık verilerini siler. Bir yük istek veya yanıt iletilerindeki mevcut değil.  
  
-   **HTTP PUT** - istenen kaynak varlık veri istek iletisi yükteki sağlanan yeni verilerle mevcut değiştirir.  
  
-   **HTTP birleştirme** - yalnızca varlık verilerini değiştirmek için veri kaynağındaki bir ekleme ardından delete yürütürken verimsizlikleri nedeniyle [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] yeni bir HTTP birleştirme eylemi tanıtır. İstek iletisinin yükü adresli varlık kaynağı değiştirmesi gereken özellikleri içerir. HTTP birleştirme HTTP belirtimini tanımlanmadığından üzerinden olmayan bir HTTP birleştirme isteği yönlendirmek için ek işleme gerektirebilir[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kullanan sunucuları.  
  
 Daha fazla bilgi için [OData: işlem](https://go.microsoft.com/fwlink/?LinkId=185792).  
  
### <a name="payload-formats"></a>Yük biçimleri  
 Bir HTTP PUT, HTTP POST ve HTTP birleştirme isteği için bir istek iletisi yükü, veri hizmetine gönderdiğiniz varlık verilerini içerir. Akıştaki içeriği ileti üzerinde veri biçimi bağlıdır. Böyle bir yükü de silme dışındaki tüm eylemler HTTP yanıtlarını içerir. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] erişim ve veri hizmeti ile değiştirmek için aşağıdaki yük biçimleri destekler:  
  
-   **Atom** -tarafından tanımlanan diğer bir deyişle, XML tabanlı ileti kodlama [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Atom yayımlama Web akışları, pod yayınlarını, Wiki'ler için veri değişimi, HTTP üzerinden etkinleştirmek için protokol (AtomPub) ve XML tabanlı Internet işlevselliği için bir genişletme olarak. Daha fazla bilgi için [OData: Atom biçimi](https://go.microsoft.com/fwlink/?LinkId=185794).  
  
-   **JSON** -JavaScript nesne gösterimi (JSON) olan bir alt kümeyi programlama JavaScript dilinin temel bir basit veri değişim biçimi. Daha fazla bilgi için [OData: JSON biçimine](https://go.microsoft.com/fwlink/?LinkId=185795).  
  
 HTTP isteği iletisi üst bilgisinde yükü ileti biçimi istenir. Daha fazla bilgi için [OData: işlem](https://go.microsoft.com/fwlink/?LinkID=185792).  
  
## <a name="accessing-and-changing-data-using-client-libraries"></a>Erişme ve verileri istemci kitaplığı kullanarak değiştirme  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] daha kolay kullanmayı sağlayan istemci kütüphaneleri içerir bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] .NET Framework ve Silverlight tabanlı istemci uygulamalarından akış. Bu kitaplıklar, HTTP iletileri gönderip basitleştirir. Bunlar ayrıca varlık verilerini temsil eden CLR nesneleri iletisi yüküne çevir. İstemci kitaplıkları iki çekirdek sınıfı özelliği <xref:System.Data.Services.Client.DataServiceContext> ve <xref:System.Data.Services.Client.DataServiceQuery%601>. Bu sınıflar, bir veri hizmetini sorgulama ve CLR nesne olarak döndürülen varlığı verilerle çalışmak etkinleştirin. Daha fazla bilgi için [WCF Veri Hizmetleri İstemci Kitaplığı](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md) ve [WCF Veri Hizmetleri (Silverlight)](https://msdn.microsoft.com/library/c0cd9f4b-1372-48e4-9935-c8421239da30).  
  
 Kullanabileceğiniz **hizmet Başvurusu Ekle** veri hizmetine başvuru eklemek için Visual Studio'da iletişim kutusu. Bu araç, başvurulan veri hizmetinden hizmet meta verileri ister ve oluşturur <xref:System.Data.Services.Client.DataServiceContext> , veri hizmetini temsil eder, aynı zamanda varlıkları temsil eden istemci veri hizmeti sınıfları oluşturur. Daha fazla bilgi için [veri hizmeti istemci kitaplığı oluşturma](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md).  
  
 Programlama kitaplığı kullanmak için kullanabileceğiniz bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] diğer türde istemci uygulamalar akış. Daha fazla bilgi için [OData SDK](https://go.microsoft.com/fwlink/?LinkId=185796).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Hizmeti Kaynaklarına Erişme](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)  
 [Hızlı başlangıç](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)
