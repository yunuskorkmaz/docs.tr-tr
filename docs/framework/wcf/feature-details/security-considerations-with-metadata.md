---
title: Meta Veriler Hakkında Güvenlik Konuları
ms.date: 03/30/2017
ms.assetid: e78ef8ab-4f63-4656-ab93-b1deab2666d5
ms.openlocfilehash: c41ebf5c39e74932a4bade610c4e236b28444327
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601029"
---
# <a name="security-considerations-with-metadata"></a>Meta Veriler Hakkında Güvenlik Konuları
Windows Communication Foundation (WCF) ' de meta veri özelliklerini kullanırken, hizmet meta verilerinin yayımlanması, alınması ve kullanılması için güvenlik etkilerine göz önünde bulundurun.  
  
## <a name="when-to-publish-metadata"></a>Meta verilerin ne zaman yayımlanacağı  
 WCF Hizmetleri varsayılan olarak meta verileri yayımlamaz. Bir WCF hizmeti için meta verileri yayımlamak için, hizmetinize meta veri uç noktaları ekleyerek meta veri yayımlamayı açıkça etkinleştirmeniz gerekir (bkz. [Yayımlama meta verileri](publishing-metadata.md)). Meta veri yayımlamanın devre dışı bırakılması, hizmetinizin saldırı yüzeyini azaltır ve istemeyerek bilgilerin açığa çıkması riskini düşürür. Tüm hizmetlerin meta verileri yayımlaması gerekir. Meta verileri yayımlamanız gerekmez, kapalı bırakmayı göz önünde bulundurun. [ServiceModel meta veri yardımcı programı aracını (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)kullanarak doğrudan hizmet derlemelerinden meta veri ve istemci kodu oluşturmaya devam edebilirsiniz. Meta verileri dışarı aktarmak için Svcutil. exe kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: meta verileri derlenmiş hizmet kodundan dışarı aktarmak Için Svcutil. exe kullanma](how-to-use-svcutil-exe-to-export-metadata-from-compiled-service-code.md).  
  
## <a name="publishing-metadata-using-a-secure-binding"></a>Güvenli bağlama kullanarak meta verileri yayımlama  
 WCF 'nin sağladığı varsayılan meta veri bağlamaları güvenli değildir ve meta verilere anonim erişime izin verir. Bir WCF hizmetinin yayımladığı hizmet meta verileri, hizmet hakkında ayrıntılı bir açıklama içerir ve isteyerek veya istemeden gizli bilgiler içerebilir. Örneğin, hizmet meta verileri, genel olarak yayınlanmak üzere tasarlanmamış altyapı işlemleri hakkında bilgi içerebilir. Hizmet meta verilerini yetkisiz erişime karşı korumak için, meta veri uç noktanız için güvenli bağlama kullanabilirsiniz. Meta veri uç noktaları, meta verileri güvenli hale getirmek için Güvenli Yuva Katmanı (SSL) kullanan HTTP/GET isteklerine yanıt verir. Daha fazla bilgi için bkz. [nasıl yapılır: güvenli meta veri uç noktaları](how-to-secure-metadata-endpoints.md).  
  
 Meta veri uç noktalarınızın güvenliğini sağlamak, istek vericiler için izinsiz veya sızdırma riski olmadan hizmet meta verilerini güvenli bir şekilde almak için bir yol sağlar.  
  
## <a name="using-only-trusted-metadata"></a>Yalnızca güvenilir meta verileri kullanma  
 Hizmeti çağırmak için gereken çalışma zamanı bileşenlerini otomatik olarak oluşturmak için hizmet meta verilerini kullanabilirsiniz. Ayrıca, bir istemcinin bir hizmeti çağırmak için kullandığı bağlamayı dinamik olarak güncellemek üzere bir istemci uygulaması geliştirmek için veya çalışma zamanında meta verileri tasarım zamanında kullanabilirsiniz.  
  
 Hizmet meta verileri, güvenli olmayan bir şekilde alındığında üzerinde değişiklik yapılabilir veya sızmış olabilir. Değiştirilen meta veriler, istemcinizi kötü amaçlı bir hizmete yönlendirebilir, güvenliği aşılmış güvenlik ayarlarını içerebilir veya kötü amaçlı XML yapıları içerebilir. Meta veri belgeleri büyük olabilir ve sıklıkla dosya sistemine kaydedilir. İzinsiz ve yanıltmaya karşı korumak için, kullanılabilir bir hizmet meta verileri istemek üzere güvenli bağlama kullanın.  
  
## <a name="using-safe-techniques-for-processing-metadata"></a>Meta verileri Işlemek için güvenli teknikler kullanma  
 Hizmet meta verileri genellikle WS-MetadataExchange (MEX) gibi standartlaştırılmış protokoller kullanılarak ağ üzerinden bir hizmetten alınır. Birçok meta veri biçimi, ek meta verilere işaret eden bir başvuru mekanizmalarına sahiptir. <xref:System.ServiceModel.Description.MetadataExchangeClient>Tür, Web Hizmetleri Açıklama Dili (wsdl) belgeleri, XML şeması ve MEX belgelerinde sizin için başvuruları otomatik olarak işler. <xref:System.ServiceModel.Description.MetadataSet>Alınan meta verilerden oluşturulan nesnenin boyutu, <xref:System.ServiceModel.Description.MetadataExchangeClient.MaximumResolvedReferences%2A> kullanılan örneğin değeri ile doğrudan orantılıdır <xref:System.ServiceModel.Description.MetadataExchangeClient> ve `MaxReceivedMessageSize` Bu örnek tarafından kullanılan bağlamanın değeridir <xref:System.ServiceModel.Description.MetadataExchangeClient> . Bu kotaları, senaryonuzun dikte edildiği şekilde uygun değerlere ayarlayın.  
  
 WCF 'de, hizmet meta verileri XML olarak işlenir. XML belgeleri işlenirken, uygulamalar kendilerini kötü amaçlı XML yapılarına karşı korumalıdır. <xref:System.Xml.XmlDictionaryReader>XML 'yi işlerken uygun kotalarla birlikte kullanın ve ayrıca <xref:System.Xml.XmlTextReader.DtdProcessing%2A> özelliğini olarak ayarlayın <xref:System.Xml.DtdProcessing.Prohibit> .  
  
 WCF 'deki meta veri sistemi genişletilebilir ve meta veri uzantıları uygulama yapılandırma dosyanıza kaydedilebilir (bkz. [meta veri sistemini genişletme](../extending/extending-the-metadata-system.md)). Meta veri uzantıları rastgele kod çalıştırabilir, bu nedenle uygulama yapılandırma dosyanızı uygun erişim denetim listeleriyle (ACL 'Ler) korumanız ve yalnızca güvenilir meta veri uzantısı uygulamalarını kaydetmeniz gerekir.  
  
## <a name="validating-generated-clients"></a>Oluşturulan Istemciler doğrulanıyor  
 Güvenilir olmayan bir kaynaktan alınan meta verilerden istemci kodu oluştururken, oluşturulan istemcinin istemci uygulamalarınızın güvenlik ilkelerine uygun olduğundan emin olmak için oluşturulan istemci kodunu doğrulayın. İstemci bağlamalarınızdaki ayarları denetlemek veya araçlar tarafından oluşturulan kodu görsel olarak incelemek için doğrulama davranışını kullanabilirsiniz. Davranışları doğrulayan bir istemcinin nasıl uygulanacağı hakkında bir örnek için bkz. [Istemci doğrulaması](../samples/client-validation.md).  
  
## <a name="protecting-application-configuration-files"></a>Uygulama yapılandırma dosyalarını koruma  
 Bir hizmetin uygulama yapılandırma dosyası, meta verilerin nasıl ve ne şekilde yayımlanmakta olduğunu denetleyebilir. Bir saldırganın bu ayarları değiştirememesini sağlamak için uygulama yapılandırma dosyasını uygun erişim denetim listeleriyle (ACL 'Ler) korumak iyi bir fikirdir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Meta Veri Uç Noktalarını Güvenli Hale Getirme](how-to-secure-metadata-endpoints.md)
- [Güvenlik](security.md)
