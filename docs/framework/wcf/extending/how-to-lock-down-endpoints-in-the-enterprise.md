---
title: "Nasıl yapılır: Enterprise Uç Noktalarını Kilitleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b7eaab7-da60-4cf7-9d6a-ec02709cf75d
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4c580316415a1186bbdee518e201fb4c88419a72
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-lock-down-endpoints-in-the-enterprise"></a>Nasıl yapılır: Enterprise Uç Noktalarını Kilitleme
Büyük ölçekli işletmeler genellikle Kurumsal güvenlik ilkeleriyle uyumlu uygulamalar geliştirilir gerektirir. Aşağıdaki konu geliştirmek ve tüm doğrulamak için kullanılan bir istemci uç nokta Doğrulayıcı yüklemek nasıl ele [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] istemci uygulamaları bilgisayarlarda yüklü.  
  
 Bu uç noktası davranışı istemciye eklendiği bu durumda, bir istemci Doğrulayıcı doğrulayıcıdır [ \<commonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) machine.config dosyasının bölümünde. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]yalnızca istemci uygulamaları için ortak uç nokta davranışları yükler ve yalnızca hizmet uygulamaları için ortak hizmet davranışları yükler. Hizmet uygulamaları için aynı bu Doğrulayıcı yüklemek için Doğrulayıcı hizmet davranışı olması gerekir. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][ \<commonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) bölümü.  
  
> [!IMPORTANT]
>  Hizmet veya uç nokta davranışları işaretlenmemiş ile <xref:System.Security.AllowPartiallyTrustedCallersAttribute> eklenir (APTCA) özniteliği [ \<commonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) uygulama kısmi güvende çalıştığında, bir yapılandırma dosyası bölümünü çalıştırmak değil ortam ve hiçbir özel durum oluşur böyle bir durumda. Doğrulayıcıları gibi ortak davranışları çalışan zorlamak için aşağıdakilerden birini yapmanız gerekir:  
>   
>  --Ortak davranışı ile işaretle <xref:System.Security.AllowPartiallyTrustedCallersAttribute> kısmi güven bir uygulama olarak dağıtıldığında çalışabilmesi özniteliği. Bir kayıt defteri girdisi bilgisayarda APTCA işaretlenmiş derlemeleri çalışmasını engellemek için ayarlanabilir Not...  
>   
>  --Uygulama kullanıcılar uygulamayı kısmi güven bir ortamda çalıştırmak için kod erişimi güvenlik ayarlarını değiştiremez tam güvenilir bir uygulama olarak dağıtılırsa emin olun. Bunu yapmak, özel Doğrulayıcı çalışmaz ve hiçbir özel durum oluşur. Bunu sağlamanın bir yolu için bkz: `levelfinal` seçeneği kullanılarak [kod erişimi güvenlik ilkesi aracını (Caspol.exe)](http://go.microsoft.com/fwlink/?LinkId=248222).  
>   
>  Daha fazla bilgi için bkz: [kısmi güven en iyi yöntemler](../../../../docs/framework/wcf/feature-details/partial-trust-best-practices.md) ve [desteklenen dağıtım senaryoları](../../../../docs/framework/wcf/feature-details/supported-deployment-scenarios.md).  
  
### <a name="to-create-the-endpoint-validator"></a>Uç nokta Doğrulayıcısı oluşturmak için  
  
1.  Oluşturma bir <xref:System.ServiceModel.Description.IEndpointBehavior> istenen doğrulama adımları <xref:System.ServiceModel.Description.IEndpointBehavior.Validate%2A> yöntemi. Aşağıdaki kod bir örnek sağlar. ( `InternetClientValidatorBehavior` Alınırlar [güvenlik doğrulaması](../../../../docs/framework/wcf/samples/security-validation.md) örnek.)  
  
     [!code-csharp[LockdownValidation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/internetclientvalidatorbehavior.cs#2)]  
  
2.  Yeni Oluştur <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> 1. adımda oluşturduğunuz uç nokta Doğrulayıcı kaydeder. Aşağıdaki kod örneğinde bu gösterir. (Bu örnek için özgün kod [güvenlik doğrulaması](../../../../docs/framework/wcf/samples/security-validation.md) örnek.)  
  
     [!code-csharp[LockdownValidation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/internetclientvalidatorelement.cs#3)]  
  
3.  Derlenmiş bütünleştirilmiş kod tanımlayıcı bir ad ile imzalandığından emin olun. Ayrıntılar için bkz [tanımlayıcı ad Aracı (SN. EXE)](http://go.microsoft.com/fwlink/?LinkId=248217) ve dilinizi derleyici komutları.  
  
### <a name="to-install-the-validator-into-the-target-computer"></a>Doğrulayıcı hedef bilgisayara yüklemek için  
  
1.  Uygun mekanizmayı kullanarak uç nokta Doğrulayıcı yükleyin. Bir kuruluşta bu Grup İlkesi ve Systems Management Server (SMS) kullanılarak.  
  
2.  Kesin olarak adlandırılmamış derleme genel derleme önbelleği kullanılarak içine yüklemek [Gacutil.exe (Genel Derleme Önbelleği Aracı)](http://msdn.microsoft.com/library/ex0ss12c\(v=vs.110\).aspx).  
  
3.  Kullanım <xref:System.Configuration?displayProperty=nameWithType> ad alanı türleri için:  
  
    1.  Uzantısına ekleme [ \<behaviorExtensions >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviorextensions.md) tam olarak nitelenmiş tür adını kullanarak bölümünde ve öğe kilitleyin.  
  
         [!code-csharp[LockdownValidation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#5)]  
  
    2.  Davranış öğesine eklemek `EndpointBehaviors` özelliği [ \<commonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) bölümünde ve öğeyi kilitle. (Doğrulayıcı hizmetini yüklemek için Doğrulayıcı olmalıdır bir <xref:System.ServiceModel.Description.IServiceBehavior> ve eklenen `ServiceBehaviors` özelliğini.) Aşağıdaki kod örneğinde uygun yapılandırma adımları sonra gösterir bir. ve güçlü bir ad olduğundan tek özel durum ile b.  
  
         [!code-csharp[LockdownValidation#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#6)]  
  
    3.  Machine.config dosyasının kaydedin. Aşağıdaki kod örneğinde, adım 3'teki tüm görevleri gerçekleştirir ancak değiştirilmiş machine.config dosyasının yerel bir kopyasını kaydeder.  
  
         [!code-csharp[LockdownValidation#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#7)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, bir ortak davranışı machine.config dosyaya ekleyin ve bir kopyasını kaydetmek için disk gösterilmektedir. `InternetClientValidatorBehavior` Alınırlar [güvenlik doğrulaması](../../../../docs/framework/wcf/samples/security-validation.md) örnek.  
  
 [!code-csharp[LockdownValidation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#1)]  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Yapılandırma dosyası öğelerini şifreleme isteyebilirsiniz. Daha fazla bilgi için Ayrıca bakınız bölümüne bakın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DPAPI kullanarak şifreleme yapılandırma dosyası öğeleri](http://go.microsoft.com/fwlink/?LinkId=94954)  
 [RSA kullanarak şifreleme yapılandırma dosyası öğeleri](http://go.microsoft.com/fwlink/?LinkId=94955)
