---
title: Meta Veriler Hakkında Güvenlik Konuları
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e78ef8ab-4f63-4656-ab93-b1deab2666d5
caps.latest.revision: 10
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: d033a3e22def60c5d82191fd7fcc93bd67f4548b
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="security-considerations-with-metadata"></a>Meta Veriler Hakkında Güvenlik Konuları
Meta verileri kullanarak ne zaman özellikleri [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]yayımlama güvenlik etkilerini göz önünde bulundurmanız, alma ve kullanarak hizmet meta verileri.  
  
## <a name="when-to-publish-metadata"></a>Ne zaman meta verileri yayımlama  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmetleri meta verileri varsayılan olarak yayımlamayın. Meta verilerini yayımlamak için bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] açıkça etkinleştirmelisiniz meta veri yayımlama hizmetinize meta veri uç noktalarını ekleyerek hizmet (bkz [meta veri yayımlama](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)). Meta veri yayımlama devre dışı bırakarak, hizmetiniz için saldırı yüzeyini azaltan ve istemeyerek bilgi ifşaatı riskini azaltır. Tüm hizmetler meta veri yayımlamanız gerekir. Meta veri yayımlama yoksa, devre dışı bırakarak göz önünde bulundurun. Doğrudan kullanarak, hizmet derlemelerden meta verileri ve istemci kodu hala oluşturabilirsiniz Not [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)] bkz: meta verileri dışarı aktarmak için svcutil.exe kullanma [nasıl yapılır: derlenmiş hizmet kodundan dışarı meta verilerine kullanım Svcutil.exe](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-export-metadata-from-compiled-service-code.md).  
  
## <a name="publishing-metadata-using-a-secure-binding"></a>Güvenli bağlama kullanarak meta verileri yayımlama  
 Varsayılan meta veri bağlamaları, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] değil güvenli ve meta verileri anonim erişime izin sağlar. Hizmet meta verileri, bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet yayımlar hizmeti hakkında ayrıntılı bir açıklama içerir ve kasıtlı veya kasıtsız olarak hassas bilgiler içerebilir. Örneğin, hizmeti meta verileri genel olarak yayınlamak için amaçlanmamış altyapı işlemleri hakkında bilgi içerebilir. Hizmet meta verileri yetkisiz erişimden korumak için güvenli bağlama, meta veri uç noktası için kullanabilirsiniz. Meta veri uç noktalarını Güvenli Yuva Katmanı (SSL) meta verileri güvenli hale getirmek için kullanabileceğiniz HTTP/GET isteklerine yanıt. Daha fazla bilgi için bkz: [nasıl yapılır: meta veri uç noktalarını güvenli](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md).  
  
 Meta veri uç noktalarını güvenli hale getirme sahiplerini güvenli bir şekilde müdahale veya yanıltma riski olmadan hizmeti meta verilerini almak için bir yol sağlar.  
  
## <a name="using-only-trusted-metadata"></a>Yalnızca güvenilir meta verileri kullanma  
 Hizmet meta verilerini hizmetini çağırmak için gereken çalışma zamanı bileşenlerini otomatik olarak oluşturmak için kullanabilirsiniz. Meta verileri tasarım zamanında bir istemci uygulaması geliştirmek için de kullanabilirsiniz veya dinamik olarak bağlama güncelleştirmek için çalışma zamanında bir istemci bir hizmetini çağırmak için kullanır.  
  
 Hizmet meta verilerini değiştirilmiş veya güvenli bir şekilde alınırken sahte. Değiştirilen meta verileri istemci kötü amaçlı bir hizmete yönlendirmek, güvenliği aşılan güvenlik ayarlarını içeren veya kötü amaçlı XML yapıları içeren. Meta veri belgelerini dosya sistemine hangi sıklıkla kaydedileceğini ve daha büyük olabilir. İzinsiz ve yanıltmaya karşı korumak için güvenli bağlama biri kullanılabilir olduğunda hizmet meta verilerini istemek için kullanın.  
  
## <a name="using-safe-techniques-for-processing-metadata"></a>Meta verileri işlemek için güvenli teknikleri kullanarak  
 Hizmet meta verilerini standartlaştırılmış protokolleri gibi WS-MetadataExchange (MEX) kullanarak ağ üzerinden bir hizmetinden sık alınır. Çok sayıda meta veri biçimleri için ek meta veri işaret eden mekanizmalar başvuran içerir. <xref:System.ServiceModel.Description.MetadataExchangeClient> Türü otomatik olarak işler başvuruları sizin için Web Hizmetleri Açıklama Dili (WSDL) belgeleri, XML şeması ve MEX belgeleri. Boyutunu <xref:System.ServiceModel.Description.MetadataSet> alınan meta verileri oluşturulan nesnedir doğrudan orantılı <xref:System.ServiceModel.Description.MetadataExchangeClient.MaximumResolvedReferences%2A> değerini <xref:System.ServiceModel.Description.MetadataExchangeClient> kullanılan örnek ve `MaxReceivedMessageSize` tarafından kullanılan bağlama için değer <xref:System.ServiceModel.Description.MetadataExchangeClient> örneği. Bu kotalar senaryonuz tarafından dikte gibi uygun değerlere ayarlayın.  
  
 İçinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], hizmet meta verilerini bir XML olarak işlenir. XML belgeleri işlerken uygulamaları kendilerini kötü amaçlı XML yapıları karşı korumanız gerekir. Kullanım `XmlDictionaryReader` ile XML dosyası işlenirken kotaları uygun ve ayrıca <xref:System.Xml.XmlTextReader.DtdProcessing%2A> özelliğine `Prohibit`.  
  
 Meta veri sistemde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] genişletilebilir ve meta veri uzantılarını, uygulama yapılandırma dosyasında kayıtlı (bakın [meta veri sistemini genişletme](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)). Meta veri uzantıları rastgele kod çalıştırabilir, korumanız gerekir böylece uygulama yapılandırma dosyanızı uygun erişim denetimi ile listeleri (ACL'ler) ve yalnızca güvenilen meta veri uzantısı uygulamaları kaydedin.  
  
## <a name="validating-generated-clients"></a>Oluşturulan istemcileri doğrulanıyor  
 Güvenilir olmayan bir kaynaktan alınan meta veriler istemci kodu oluşturma sırasında oluşturulan istemci istemci uygulamaları güvenlik ilkelerinizi uymasını sağlamak için oluşturulan istemci kodunu doğrulayın. Bağlama, istemci ayarlarını kontrol edin veya araçları tarafından oluşturulan kod görsel olarak inceleyin için bir doğrulama davranışı kullanabilirsiniz. Davranışları doğrulayan bir istemci uygulama örneği için bkz: [istemci doğrulama](../../../../docs/framework/wcf/samples/client-validation.md).  
  
## <a name="protecting-application-configuration-files"></a>Uygulama yapılandırma dosyaları koruma  
 Bir hizmetin uygulama yapılandırma dosyasını kontrol edebilir nasıl ve meta verileri yayımlanır. Uygun erişim denetim listeleriyle (ACL) bir saldırgan bu ayarları değiştiremezsiniz emin olmak için uygulama yapılandırma dosyasını korumak için iyi bir fikirdir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Meta Veri Uç Noktalarını Güvenli Hale Getirme](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md)  
 [Güvenlik](../../../../docs/framework/wcf/feature-details/security.md)
