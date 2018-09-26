---
title: Meta Veriler Hakkında Güvenlik Konuları
ms.date: 03/30/2017
ms.assetid: e78ef8ab-4f63-4656-ab93-b1deab2666d5
author: BrucePerlerMS
ms.openlocfilehash: 1469e5b48fbbdcbb289e4ca3147145688e1669f4
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47082422"
---
# <a name="security-considerations-with-metadata"></a>Meta Veriler Hakkında Güvenlik Konuları
Meta veri özelliklerini Windows Communication Foundation (WCF) kullanırken, yayımlama, alma ve hizmet meta verileri kullanarak güvenlikle ilgili etkileri göz önünde bulundurun.  
  
## <a name="when-to-publish-metadata"></a>Ne zaman meta verileri yayımlama  
 WCF hizmetleri varsayılan meta veri yayımlamayın. Bir WCF hizmeti için meta verilerinin açıkça meta veri yayımlama hizmetinize meta veri uç noktalarını ekleyerek etkinleştirmeniz gerekir (bkz [meta veri yayımlama](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)). Meta veri yayımlamayı devre dışı bırakarak, hizmetiniz için saldırı yüzeyini azaltan ve istenmeyen bilgi ifşaatı riskini azaltır. Tüm hizmetler meta verilerini yayımlamanız gerekir. Meta veri yayımlamayı yoksa, devre dışı bırakarak göz önünde bulundurun. Doğrudan kullanarak, hizmet derlemelerden meta verileri ve istemci kodu hala oluşturabilirsiniz Not [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Meta verileri dışarı aktarmak için Svcutil.exe kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: derlenmiş hizmet kodundan dışarı meta verilerine kullanın Svcutil.exe](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-export-metadata-from-compiled-service-code.md).  
  
## <a name="publishing-metadata-using-a-secure-binding"></a>Güvenli bir bağlama kullanarak meta verileri yayımlama  
 Güvenli olmayan WCF sağlayan varsayılan meta veri bağlantılarını ve bunların meta verileri anonim erişime izin verin. Bir WCF Hizmeti yayımlayan hizmet meta verileri, hizmet hakkında ayrıntılı bir açıklama içerir ve kasıtlı veya kasıtsız olarak hassas bilgiler içerebilir. Örneğin, hizmet meta verileri herkese açık şekilde yayınlamak için hedeflememektedir altyapı işlemleri hakkında bilgi içeriyor olabilir. Hizmet meta verileri yetkisiz erişimden korumak için güvenli bir bağlama meta veri uç noktanız için kullanabilirsiniz. Meta veri uç noktalarını Güvenli Yuva Katmanı (SSL) meta verileri güvenli hale getirmek için kullanabileceğiniz HTTP/GET isteklerine yanıt. Daha fazla bilgi için [nasıl yapılır: meta veri uç noktalarını güvenli hale getirme](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md).  
  
 Meta veri uç noktalarını güvenli hale getirme isteyenlere hizmet meta verilerinin değiştirilmesine veya yanıltma riski olmadan güvenli bir şekilde almak bir yol sağlar.  
  
## <a name="using-only-trusted-metadata"></a>Yalnızca güvenilen meta verileri kullanma  
 Hizmet meta verileri, bir hizmeti çağırmak için gereken çalışma zamanı bileşenlerini otomatik olarak oluşturmak için kullanabilirsiniz. Meta veri tasarım zamanında bir istemci uygulaması geliştirmek için kullanabilirsiniz veya dinamik olarak bağlama güncelleştirmek için çalışma zamanında istemci bir hizmeti çağırmak için kullanır.  
  
 Hizmet meta verileri kurcalanmadığından veya güvenli bir şekilde alınırken sahte. Değiştirilen meta verileri kötü amaçlı bir hizmette istemci yeniden yönlendirme, güvenliği aşılmış güvenlik ayarlarını içerir veya kötü amaçlı XML yapıları içerir. Meta veri belgelerini dosya sistemine hangi sıklıkla kaydedileceğini ve daha büyük olabilir. Kurcalama ve yanıltmaya karşı korumaya yönelik bir kullanılabilir olduğunda hizmet meta verileri istemek için güvenli bir bağlama kullanın.  
  
## <a name="using-safe-techniques-for-processing-metadata"></a>Meta verileri işlemek için güvenli teknikleri kullanarak  
 Hizmet meta verileri, WS-MetadataExchange (MEX) gibi standart protokolleri kullanarak ağ üzerinden bir hizmet sık alınır. Çok sayıda meta veri biçimleri mekanizmaları işaret eden ek meta verileri için başvuru içerir. <xref:System.ServiceModel.Description.MetadataExchangeClient> Türü otomatik olarak işler başvurular sizin için Web Hizmetleri Açıklama Dili (WSDL) belgeleri, XML şema ve MEX belgeleri. Boyutu <xref:System.ServiceModel.Description.MetadataSet> alınan meta verilerinden oluşturulan nesne doğru orantılı <xref:System.ServiceModel.Description.MetadataExchangeClient.MaximumResolvedReferences%2A> değerini <xref:System.ServiceModel.Description.MetadataExchangeClient> kullanılır örneği ve `MaxReceivedMessageSize` tarafından kullanılan bir bağlama için değer <xref:System.ServiceModel.Description.MetadataExchangeClient> örneği. Bu kotalar senaryonuza göre belirlenen uygun değerlere ayarlayın.  
  
 WCF'de, hizmet meta verileri XML olarak işlenir. XML belgeleri işlerken uygulamalar kendilerini kötü amaçlı XML yapıları karşı korumanız gerekir. Kullanım `XmlDictionaryReader` ile XML işlenirken uygun kotaları ve ayrıca <xref:System.Xml.XmlTextReader.DtdProcessing%2A> özelliğini `Prohibit`.  
  
 Wcf'de meta veri sistemini Genişletilebilir olduğundan ve meta verileri uzantıları, uygulama yapılandırma dosyasında kayıtlı (bakın [meta veri sistemini genişletme](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)). Meta veri uzantıları rastgele kod çalıştırabilir, korumanız gerekir, uygulama yapılandırma dosyası ile ilgili erişim denetim listeleri (ACL'ler) ve yalnızca güvenilen meta veri uzantısı uygulamaları kaydetme.  
  
## <a name="validating-generated-clients"></a>Oluşturulan istemciler doğrulanıyor  
 Güvenilmeyen bir kaynaktan alınan meta veriler istemci kodu oluşturuluyor, oluşturulan istemciyi istemci uygulamalar güvenlik ilkelerinize uygun olduğunu emin olmak için oluşturulan istemci kodu doğrulayın. Bağlama, istemcide ayarlarını kontrol edin veya araçları tarafından oluşturulan kodda görsel olarak inceleyin, doğrulama davranışını kullanabilirsiniz. Davranışlar doğrulayan bir istemci uygulama bir örnek için bkz [istemci doğrulama](../../../../docs/framework/wcf/samples/client-validation.md).  
  
## <a name="protecting-application-configuration-files"></a>Uygulama yapılandırma dosyaları koruma  
 Bir hizmetin uygulama yapılandırma dosyasını denetleyebilirsiniz nasıl ve meta verileri yayımlanır. Uygun erişim denetim listeleriyle (ACL) bir saldırganın bu ayarları değiştiremezsiniz emin olmak için uygulama yapılandırma dosyasına korumak için iyi bir fikirdir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Meta Veri Uç Noktalarını Güvenli Hale Getirme](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md)  
 [Güvenlik](../../../../docs/framework/wcf/feature-details/security.md)
