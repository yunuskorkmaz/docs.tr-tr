---
title: 'Nasıl yapılır: Enterprise Uç Noktalarını Kilitleme'
ms.date: 03/30/2017
ms.assetid: 1b7eaab7-da60-4cf7-9d6a-ec02709cf75d
ms.openlocfilehash: 032b69c1fae38576b0374b329f1ab6fe90e2b1a0
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44184395"
---
# <a name="how-to-lock-down-endpoints-in-the-enterprise"></a>Nasıl yapılır: Enterprise Uç Noktalarını Kilitleme
Büyük kuruluşlar genellikle uygulamaları kuruluş güvenlik ilkelerine uygun olarak geliştirilen gerektirir. Aşağıdaki konuda geliştirme ve bilgisayarlarda yüklü tüm Windows Communication Foundation (WCF) istemci uygulamaları doğrulamak için kullanılan bir istemci uç noktası Doğrulayıcı yüklemek nasıl ele alınmaktadır.  
  
 Bu uç nokta davranışı istemciye eklendiğinden bu durumda, bir istemci Doğrulayıcı doğrulayıcıdır [ \<commonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) machine.config dosyasının bir bölümünde. WCF istemci uygulamaları için yalnızca ortak uç nokta davranışları yükler ve yalnızca hizmet uygulamaları için ortak bir hizmet davranışı yükler. Hizmet uygulamaları için aynı bu Doğrulayıcı yüklemek için bir hizmet davranışını Doğrulayıcı olmalıdır. Daha fazla bilgi için [ \<commonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) bölümü.  
  
> [!IMPORTANT]
>  Hizmet veya uç nokta davranışları işaretlenmemiş ile <xref:System.Security.AllowPartiallyTrustedCallersAttribute> eklenen özniteliği (APTCA) [ \<commonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) kısmi güvende uygulama çalışırken, bir yapılandırma dosyası bölümünü çalıştırmak değil Bu durumda ortam ve hiçbir özel durum oluşturulur. Doğrulayıcıların gibi ortak davranışları çalışmasını zorunlu kılmak için aşağıdakilerden birini yapmanız gerekir:  
>   
>  --Ortak davranışınızı işaretlemek <xref:System.Security.AllowPartiallyTrustedCallersAttribute> kısmi güven bir uygulama dağıtıldığında çalıştırabileceği şekilde onlara özniteliği. Bir kayıt defteri girişi bilgisayarda APTCA işaretli derlemeler çalışmasını önlemek için ayarlanabilir dikkat edin...  
>   
>  --Uygulama tam olarak güvenilen bir uygulama kullanıcılar, uygulamayı bir kısmi güven ortamında çalıştırmak için kod erişimi güvenlik ayarlarını değiştiremez dağıtılırsa emin olun. Bunu yapmak, özel Doğrulayıcı çalışmaz ve hiçbir özel durum. Bunu sağlamak bir yol için bkz. `levelfinal` seçeneği kullanılarak [kod erişimi güvenliği ilke Aracı (Caspol.exe)](https://go.microsoft.com/fwlink/?LinkId=248222).  
>   
>  Daha fazla bilgi için [kısmi güven en iyi uygulamaları](../../../../docs/framework/wcf/feature-details/partial-trust-best-practices.md) ve [desteklenen dağıtım senaryoları](../../../../docs/framework/wcf/feature-details/supported-deployment-scenarios.md).  
  
### <a name="to-create-the-endpoint-validator"></a>Uç nokta Doğrulayıcısı oluşturmak için  
  
1.  Oluşturma bir <xref:System.ServiceModel.Description.IEndpointBehavior> istenen doğrulama adımları ile <xref:System.ServiceModel.Description.IEndpointBehavior.Validate%2A> yöntemi. Aşağıdaki kod örneği sağlar. ( `InternetClientValidatorBehavior` Alınır [güvenlik doğrulaması](../../../../docs/framework/wcf/samples/security-validation.md) örnek.)  
  
     [!code-csharp[LockdownValidation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/internetclientvalidatorbehavior.cs#2)]  
  
2.  Yeni Oluştur <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> 1. adımda oluşturulan uç nokta Doğrulayıcı kaydeder. Aşağıdaki kod örneği bunu gösterir. (Bu örnek için özgün kod [güvenlik doğrulaması](../../../../docs/framework/wcf/samples/security-validation.md) örnek.)  
  
     [!code-csharp[LockdownValidation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/internetclientvalidatorelement.cs#3)]  
  
3.  Derlenmiş bütünleştirilmiş kodu, tanımlayıcı ad ile imzalandığından emin olun. Ayrıntılar için bkz [tanımlayıcı ad Aracı (SN. EXE)](https://go.microsoft.com/fwlink/?LinkId=248217) ve dil derleyici komutları.  
  
### <a name="to-install-the-validator-into-the-target-computer"></a>Doğrulayıcı hedef bilgisayara yüklemek için  
  
1.  Uygun mekanizmayı kullanarak uç nokta Doğrulayıcı yükleyin. Kuruluş, bu Grup İlkesi ve Systems Management Server (SMS) kullanıyor.  
  
2.  Genel derleme önbellek kullanarak kesin adlandırılmış derlemeyi yüklemek [Gacutil.exe (Genel Derleme Önbelleği Aracı)](https://msdn.microsoft.com/library/ex0ss12c\(v=vs.110\).aspx).  
  
3.  Kullanım <xref:System.Configuration?displayProperty=nameWithType> ad alanı türleri için:  
  
    1.  Uzantısına ekleme [ \<behaviorExtensions >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviorextensions.md) tam olarak nitelenmiş tür adını kullanarak bölüm ve öğe kilitleyin.  
  
         [!code-csharp[LockdownValidation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#5)]  
  
    2.  Davranış öğesine ekleyin `EndpointBehaviors` özelliği [ \<commonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) bölüm ve öğe kilitleyin. (Doğrulayıcı hizmetini yüklemek için Doğrulayıcı olmalıdır bir <xref:System.ServiceModel.Description.IServiceBehavior> ve eklenen `ServiceBehaviors` özellik.) Aşağıdaki kod örneği uygun yapılandırmaya sonrasında adımları gösterir bir. ve b, tanımlayıcı adı olan tek özel durum.  
  
         [!code-csharp[LockdownValidation#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#6)]  
  
    3.  Machine.config dosyasına kaydedin. Aşağıdaki kod örneği, adım 3'te tüm görevleri gerçekleştirir ancak değiştirilen machine.config dosyasının yerel bir kopyasını kaydeder.  
  
         [!code-csharp[LockdownValidation#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#7)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, ortak davranışını machine.config dosyasına ekleyin ve diske bir kopyasını kaydetmek gösterilmektedir. `InternetClientValidatorBehavior` Alınır [güvenlik doğrulaması](../../../../docs/framework/wcf/samples/security-validation.md) örnek.  
  
 [!code-csharp[LockdownValidation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#1)]  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Yapılandırma dosyası öğelerini şifreleme isteyebilirsiniz. Daha fazla bilgi için Ayrıca bakınız bölümüne bakın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yapılandırma dosyası öğeleri DPAPI kullanılarak şifreleme](https://go.microsoft.com/fwlink/?LinkId=94954)  
 [Yapılandırma dosyası öğeleri RSA kullanarak şifreleme](https://go.microsoft.com/fwlink/?LinkId=94955)
