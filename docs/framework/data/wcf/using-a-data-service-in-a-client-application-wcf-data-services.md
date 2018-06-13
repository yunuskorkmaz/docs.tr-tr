---
title: Veri Hizmeti istemci uygulamasında (WCF Veri Hizmetleri) kullanma
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, getting started
ms.assetid: 90872d0c-e989-4490-b3e9-54afb10d33d4
ms.openlocfilehash: b25489de9a64ba4f1938e4d52c1cc677a218495b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365299"
---
# <a name="using-a-data-service-in-a-client-application-wcf-data-services"></a>Veri Hizmeti istemci uygulamasında (WCF Veri Hizmetleri) kullanma
Kullanıma sunan bir hizmet erişebileceğiniz bir [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] bir URI ile bir Web tarayıcısı sağlayarak akış. Bir kaynak adres URI sağlar ve istek iletilerini erişmek veya kaynak temsil eden temel alınan veri değiştirmek için bu adrese gönderilir. Tarayıcı bir HTTP GET komutu verdiğinde ve istenen kaynak olarak döndüren bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akış. Daha fazla bilgi için bkz: [bir Web tarayıcısından hizmete erişim](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).  
  
 Bir Web tarayıcısı, test etmek için yararlı olabilir ancak bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] hizmeti döndürür beklenen verileri, üretim [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] de oluşturmanıza olanak sağlayan hizmetlerinin güncelleştirmek ve verileri sil genellikle uygulama kodu tarafından erişilen veya dil komut dosyası oluşturma bir Web sayfasında. Bu konuda nasıl erişileceği genel bakış sağlar [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akışları istemci uygulamasından.  
  
## <a name="accessing-and-changing-data-using-rest-semantics"></a>Verilere erişme ve REST özelliklerini kullanarak verileri değiştirme  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] yardımcı garanti kullanıma hizmetleri arasında birlikte çalışabilirlik [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akışları ve kullanan uygulamaları [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akışları. Uygulamaları erişme ve verileri değiştirme bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-istek iletilerini belirli bir HTTP eylemi ve hangi eylemini gerçekleştirilmelidir bir varlık kaynak adresleri bir URI ile göndererek hizmet tabanlı. Varlık veri sağlanmalıdır, özellikle kodlanmış yükü ileti gövdesi olarak sağlanır.  
  
### <a name="http-actions"></a>HTTP Eylemler  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] destekler gerçekleştirmek için aşağıdaki HTTP eylemleri oluşturma, okuma, güncelleştirme ve silme işlemleri adresli kaynak temsil eden varlık veriler üzerinde:  
  
-   **HTTP GET** -kaynak bir tarayıcıdan erişildiğinde bu varsayılan değerdir. Yükü yok istek iletisinde sağlanan ve istenen verileri içeren bir yükü yanıt yöntemiyle döndürülür.  
  
-   **HTTP POST** -sağlanan kaynak yeni varlık verilerini ekler. Eklenecek verileri istek iletisi yükünde sağlanır. Yanıt iletisi yükü, yeni oluşturulan varlık için veri içerir. Bu, herhangi bir otomatik olarak oluşturulur anahtar değeri içerir. Üstbilgi, yeni varlık kaynak adresleri URI de içerir.  
  
-   **HTTP DELETE** -belirtilen kaynak temsil eden varlık verilerini siler. Bir yük isteği veya Yanıtı iletilerinde mevcut değil.  
  
-   **HTTP PUT** - istenen kaynak varlık veri istek iletisi yükünde sağlanan yeni verilerle varolan değiştirir.  
  
-   **HTTP birleştirme** - yalnızca varlık veri değişikliğini için veri kaynağında bir ekleme ve ardından bir silme yürütürken verimsiz nedeniyle [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] yeni bir HTTP birleştirme eylem tanıtır. İstek iletisi yükü adresli varlık kaynakta değiştirilmelidir özelliklerini içerir. HTTP birleştirme HTTP belirtiminde tanımlanmadığından, aracılığıyla olmayan bir HTTP birleştirme isteği yönlendirmek için ek işleme gerektirebilir[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kullanan sunucuları.  
  
 Daha fazla bilgi için bkz: [OData: işlemleri](http://go.microsoft.com/fwlink/?LinkId=185792).  
  
### <a name="payload-formats"></a>Yükü biçimleri  
 Bir HTTP PUT, HTTP POST ve HTTP birleştirme isteği için bir istek iletisi yükü veri hizmetine gönderdiğiniz varlık verilerini içerir. Yükü içeriğini ileti veri biçimi bağlıdır. Ayrıca Sil dışındaki tüm eylemler HTTP yanıtlarını böyle bir yükü içerir. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] erişmek ve veri hizmeti ile değiştirme şu yükü biçimlerini destekler:  
  
-   **Atom** -tarafından tanımlanan bir XML tabanlı ileti başka bir deyişle kodlama [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Atom yayımlama Web akışları, pod yayınları, Wiki için HTTP üzerinden veri değişimi etkinleştirmek üzere Protokolü (AtomPub) ve XML tabanlı Internet işlevine bir uzantısı olarak. Daha fazla bilgi için bkz: [OData: Atom biçimi](http://go.microsoft.com/fwlink/?LinkId=185794).  
  
-   **JSON** -JavaScript nesne gösterimi (JSON) olan bir JavaScript programlama dili alt üzerinde dayalı basit veri değişim biçimi. Daha fazla bilgi için bkz: [OData: JSON biçimine](http://go.microsoft.com/fwlink/?LinkId=185795).  
  
 İleti biçimi yükün HTTP istek iletisinin başlığında istendi. Daha fazla bilgi için bkz: [OData: işlemleri](http://go.microsoft.com/fwlink/?LinkID=185792).  
  
## <a name="accessing-and-changing-data-using-client-libraries"></a>Verilere erişme ve istemci kitaplıkları kullanarak verileri değiştirme  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] daha kolayca kullanmalarını sağlayan istemci kitaplıklarını içerir bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] .NET Framework ve Silverlight tabanlı istemci uygulamalardan akış. Bu kitaplıklar, HTTP ileti gönderme ve alma basitleştirir. Bunlar ayrıca varlık verilerini temsil eden CLR nesneleri içine ileti yükü çevir. İstemci kitaplıkları iki çekirdek sınıfları özellik <xref:System.Data.Services.Client.DataServiceContext> ve <xref:System.Data.Services.Client.DataServiceQuery%601>. Bu sınıfları, veri hizmeti sorgulamak ve CLR nesneler olarak döndürülen varlığı verilerle çalışmak etkinleştirin. Daha fazla bilgi için bkz: [WCF Veri Hizmetleri İstemci Kitaplığı](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md) ve [WCF Veri Hizmetleri (Silverlight)](http://msdn.microsoft.com/library/c0cd9f4b-1372-48e4-9935-c8421239da30).  
  
 Kullanabileceğiniz **hizmet Başvurusu Ekle** veri hizmeti için bir başvuru eklemek için Visual Studio'da iletişim kutusu. Bu araç başvurulan veri hizmetinden veri hizmeti meta veri isteklerini ve oluşturur <xref:System.Data.Services.Client.DataServiceContext> , veri hizmeti temsil eden yanı sıra varlıkları temsil istemci veri hizmeti sınıfları oluşturur. Daha fazla bilgi için bkz: [veri hizmeti istemci kitaplığı oluşturma](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md).  
  
 Programlama kitaplığı kullanmak için kullanabileceğiniz bir [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] diğer tür istemci uygulamaların akışı. Daha fazla bilgi için bkz: [OData SDK](http://go.microsoft.com/fwlink/?LinkId=185796).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Hizmeti Kaynaklarına Erişme](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)  
 [Hızlı başlangıç](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)
