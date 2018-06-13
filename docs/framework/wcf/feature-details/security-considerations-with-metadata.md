---
title: Meta Veriler Hakkında Güvenlik Konuları
ms.date: 03/30/2017
ms.assetid: e78ef8ab-4f63-4656-ab93-b1deab2666d5
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: b8028b27e721e19a5fc01887e4095218d0e14436
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498549"
---
# <a name="security-considerations-with-metadata"></a>Meta Veriler Hakkında Güvenlik Konuları
Meta veri özelliklerini Windows Communication Foundation (WCF) kullanırken, yayımlama, alınmasını ve hizmeti meta verileri kullanarak güvenlik etkilerini göz önünde bulundurun.  
  
## <a name="when-to-publish-metadata"></a>Ne zaman meta verileri yayımlama  
 WCF hizmetleri meta verileri varsayılan olarak yayımlamayın. Bir WCF Hizmeti meta verilerini yayımlamak için açıkça meta veri yayımlama hizmetinize meta veri uç noktalarını ekleyerek etkinleştirmeniz gerekir (bkz [meta veri yayımlama](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)). Meta veri yayımlama devre dışı bırakarak, hizmetiniz için saldırı yüzeyini azaltan ve istemeyerek bilgi ifşaatı riskini azaltır. Tüm hizmetler meta veri yayımlamanız gerekir. Meta veri yayımlama yoksa, devre dışı bırakarak göz önünde bulundurun. Doğrudan kullanarak, hizmet derlemelerden meta verileri ve istemci kodu hala oluşturabilirsiniz Not [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Meta veri dışarı aktarmak için Svcutil.exe kullanma hakkında daha fazla bilgi için bkz: [nasıl yapılır: derlenmiş hizmet kodundan dışarı meta verilerine kullanım Svcutil.exe](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-export-metadata-from-compiled-service-code.md).  
  
## <a name="publishing-metadata-using-a-secure-binding"></a>Güvenli bağlama kullanarak meta verileri yayımlama  
 Güvenli olmayan WCF sağlar varsayılan meta veri bağlama ve bunların meta verileri anonim erişime izin verin. Bir WCF Hizmeti yayımlar hizmeti meta veri hizmeti hakkında ayrıntılı bir açıklama içerir ve kasıtlı veya kasıtsız olarak hassas bilgiler içerebilir. Örneğin, hizmeti meta verileri genel olarak yayınlamak için amaçlanmamış altyapı işlemleri hakkında bilgi içerebilir. Hizmet meta verileri yetkisiz erişimden korumak için güvenli bağlama, meta veri uç noktası için kullanabilirsiniz. Meta veri uç noktalarını Güvenli Yuva Katmanı (SSL) meta verileri güvenli hale getirmek için kullanabileceğiniz HTTP/GET isteklerine yanıt. Daha fazla bilgi için bkz: [nasıl yapılır: meta veri uç noktalarını güvenli](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md).  
  
 Meta veri uç noktalarını güvenli hale getirme sahiplerini güvenli bir şekilde müdahale veya yanıltma riski olmadan hizmeti meta verilerini almak için bir yol sağlar.  
  
## <a name="using-only-trusted-metadata"></a>Yalnızca güvenilir meta verileri kullanma  
 Hizmet meta verilerini hizmetini çağırmak için gereken çalışma zamanı bileşenlerini otomatik olarak oluşturmak için kullanabilirsiniz. Meta verileri tasarım zamanında bir istemci uygulaması geliştirmek için de kullanabilirsiniz veya dinamik olarak bağlama güncelleştirmek için çalışma zamanında bir istemci bir hizmetini çağırmak için kullanır.  
  
 Hizmet meta verilerini değiştirilmiş veya güvenli bir şekilde alınırken sahte. Değiştirilen meta verileri istemci kötü amaçlı bir hizmete yönlendirmek, güvenliği aşılan güvenlik ayarlarını içeren veya kötü amaçlı XML yapıları içeren. Meta veri belgelerini dosya sistemine hangi sıklıkla kaydedileceğini ve daha büyük olabilir. İzinsiz ve yanıltmaya karşı korumak için güvenli bağlama biri kullanılabilir olduğunda hizmet meta verilerini istemek için kullanın.  
  
## <a name="using-safe-techniques-for-processing-metadata"></a>Meta verileri işlemek için güvenli teknikleri kullanarak  
 Hizmet meta verilerini standartlaştırılmış protokolleri gibi WS-MetadataExchange (MEX) kullanarak ağ üzerinden bir hizmetinden sık alınır. Çok sayıda meta veri biçimleri için ek meta veri işaret eden mekanizmalar başvuran içerir. <xref:System.ServiceModel.Description.MetadataExchangeClient> Türü otomatik olarak işler başvuruları sizin için Web Hizmetleri Açıklama Dili (WSDL) belgeleri, XML şeması ve MEX belgeleri. Boyutunu <xref:System.ServiceModel.Description.MetadataSet> alınan meta verileri oluşturulan nesnedir doğrudan orantılı <xref:System.ServiceModel.Description.MetadataExchangeClient.MaximumResolvedReferences%2A> değerini <xref:System.ServiceModel.Description.MetadataExchangeClient> kullanılan örnek ve `MaxReceivedMessageSize` tarafından kullanılan bağlama için değer <xref:System.ServiceModel.Description.MetadataExchangeClient> örneği. Bu kotalar senaryonuz tarafından dikte gibi uygun değerlere ayarlayın.  
  
 WCF'de, hizmeti meta verileri XML olarak işlenir. XML belgeleri işlerken uygulamaları kendilerini kötü amaçlı XML yapıları karşı korumanız gerekir. Kullanım `XmlDictionaryReader` ile XML dosyası işlenirken kotaları uygun ve ayrıca <xref:System.Xml.XmlTextReader.DtdProcessing%2A> özelliğine `Prohibit`.  
  
 WCF Meta veri sistemde genişletilebilirdir ve meta veri uzantılarını, uygulama yapılandırma dosyasında kaydedilebilir (bkz [meta veri sistemini genişletme](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)). Meta veri uzantıları rastgele kod çalıştırabilir, korumanız gerekir böylece uygulama yapılandırma dosyanızı uygun erişim denetimi ile listeleri (ACL'ler) ve yalnızca güvenilen meta veri uzantısı uygulamaları kaydedin.  
  
## <a name="validating-generated-clients"></a>Oluşturulan istemcileri doğrulanıyor  
 Güvenilir olmayan bir kaynaktan alınan meta veriler istemci kodu oluşturma sırasında oluşturulan istemci istemci uygulamaları güvenlik ilkelerinizi uymasını sağlamak için oluşturulan istemci kodunu doğrulayın. Bağlama, istemci ayarlarını kontrol edin veya araçları tarafından oluşturulan kod görsel olarak inceleyin için bir doğrulama davranışı kullanabilirsiniz. Davranışları doğrulayan bir istemci uygulama örneği için bkz: [istemci doğrulama](../../../../docs/framework/wcf/samples/client-validation.md).  
  
## <a name="protecting-application-configuration-files"></a>Uygulama yapılandırma dosyaları koruma  
 Bir hizmetin uygulama yapılandırma dosyasını kontrol edebilir nasıl ve meta verileri yayımlanır. Uygun erişim denetim listeleriyle (ACL) bir saldırgan bu ayarları değiştiremezsiniz emin olmak için uygulama yapılandırma dosyasını korumak için iyi bir fikirdir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Meta Veri Uç Noktalarını Güvenli Hale Getirme](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md)  
 [Güvenlik](../../../../docs/framework/wcf/feature-details/security.md)
