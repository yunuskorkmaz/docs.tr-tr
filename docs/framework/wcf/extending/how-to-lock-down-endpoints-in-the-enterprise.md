---
title: 'Nasıl yapılır: Enterprise Uç Noktalarını Kilitleme'
ms.date: 03/30/2017
ms.assetid: 1b7eaab7-da60-4cf7-9d6a-ec02709cf75d
ms.openlocfilehash: d2a0299dd67e6efe3e3d9e6bae81265d4ad314ee
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040288"
---
# <a name="how-to-lock-down-endpoints-in-the-enterprise"></a>Nasıl yapılır: Enterprise Uç Noktalarını Kilitleme

Büyük kuruluşlar genellikle uygulamaların kurumsal güvenlik ilkeleriyle uyumlu olarak geliştirilmesini gerektirir. Aşağıdaki konuda, bilgisayarlarda yüklü olan tüm Windows Communication Foundation (WCF) istemci uygulamalarını doğrulamak için kullanılabilecek bir istemci uç noktası doğrulayıcısı geliştirme ve yükleme açıklanmaktadır.

Bu durumda, bu uç nokta davranışı Machine. config dosyasındaki istemci [ \<commonbehavior >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) bölümüne eklendiğinden, Doğrulayıcı bir istemci doğrulayıcısı olur. WCF, ortak uç nokta davranışlarını yalnızca istemci uygulamaları için yükler ve yalnızca hizmet uygulamaları için ortak hizmet davranışlarını yükler. Bu hizmet uygulamalarına yönelik aynı Doğrulayıcı 'yı yüklemek için doğrulayıcının bir hizmet davranışı olması gerekir. Daha fazla bilgi için, [ \<commondavranışlar >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) bölümüne bakın.

> [!IMPORTANT]
> Bir yapılandırma dosyasının [ \<commondavranışlar >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) bölümüne eklenen <xref:System.Security.AllowPartiallyTrustedCallersAttribute> öznitelik (aptca) ile işaretlenmemiş hizmet veya uç nokta davranışları, uygulama kısmi güven ortamında çalıştırıldığında ve Hayır olmadığında çalışmaz. Bu gerçekleştiğinde özel durum oluşturulur. Doğrulayıcılar gibi yaygın davranışları çalıştırmaya zorlamak için şunlardan birini yapmanız gerekir:
>
> - Kısmi güven uygulaması olarak dağıtıldığında çalışabilmesi <xref:System.Security.AllowPartiallyTrustedCallersAttribute> için ortak davranışınızı özniteliğiyle işaretleyin. APTCA tarafından işaretlenmiş derlemelerin çalıştırılmasını engellemek için bilgisayarda bir kayıt defteri girişi ayarlanmayacağınızı unutmayın.
>
> - Uygulamanın, uygulamayı kısmi güven ortamında çalıştırmak için kod erişimi güvenlik ayarlarını değiştiremediği tam güvenilir bir uygulama olarak dağıtıldığından emin olun. Bunu yapabilmeleri durumunda özel Doğrulayıcı çalışmaz ve hiçbir özel durum oluşturulmaz. Bunu sağlamanın bir yolu için, `levelfinal` [kod erişimi güvenlik ilkesi aracı 'nı (Caspol. exe)](https://go.microsoft.com/fwlink/?LinkId=248222)kullanma seçeneğine bakın.
>
> Daha fazla bilgi için bkz. [kısmi güvenin En Iyi uygulamaları](../../../../docs/framework/wcf/feature-details/partial-trust-best-practices.md) ve [Desteklenen Dağıtım senaryoları](../../../../docs/framework/wcf/feature-details/supported-deployment-scenarios.md).

### <a name="to-create-the-endpoint-validator"></a>Uç nokta doğrulayıcısı oluşturmak için

1. <xref:System.ServiceModel.Description.IEndpointBehavior.Validate%2A> <xref:System.ServiceModel.Description.IEndpointBehavior> Yönteminde istenen doğrulama adımları ile oluşturun. Aşağıdaki kod bir örnek sağlar. (Güvenlik doğrulama örneğinden alınır.) [](../../../../docs/framework/wcf/samples/security-validation.md) `InternetClientValidatorBehavior`

    [!code-csharp[LockdownValidation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/internetclientvalidatorbehavior.cs#2)]

2. Adım 1 <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> ' de oluşturulan uç nokta doğrulayıcısı kaydeden yeni oluştur. Aşağıdaki kod örneği bunu gösterir. (Bu örnek için özgün kod, [güvenlik doğrulama](../../../../docs/framework/wcf/samples/security-validation.md) örneğidir.)

    [!code-csharp[LockdownValidation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/internetclientvalidatorelement.cs#3)]

3. Derlenmiş derlemenin bir tanımlayıcı ad ile imzalandığından emin olun. Ayrıntılar için bkz [. tanımlayıcı ad Aracı (sn. EXE)](https://go.microsoft.com/fwlink/?LinkId=248217) ve dilinize yönelik derleyici komutlarını.

### <a name="to-install-the-validator-into-the-target-computer"></a>Doğrulayıcısı hedef bilgisayara yüklemek için

1. Uygun mekanizmayı kullanarak uç nokta doğrulayıcısı 'nı yükler. Bir kuruluşta bu, grup ilkesi ve Systems Management Server (SMS) ile kullanılabilir.

2. [Gacutil. exe](../../../../docs/framework/tools/gacutil-exe-gac-tool.md)' yi kullanarak, kesin adlı derlemeyi genel bütünleştirilmiş kod önbelleğine yükler (genel bütünleştirilmiş kod önbelleği aracı).

3. <xref:System.Configuration?displayProperty=nameWithType> Ad alanı türlerini şu şekilde kullanın:

    1. Uzantıyı tam nitelikli bir tür adı kullanarak [ BehaviorExtensions>bölümüneekleyinveöğeyikilitleyin.\<](../../../../docs/framework/configure-apps/file-schema/wcf/behaviorextensions.md)

         [!code-csharp[LockdownValidation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#5)]

    2. Davranış öğesini `EndpointBehaviors` [ \<commonbehavior >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) bölümünün özelliğine ekleyin ve öğesini kilitleyin. (Doğrulayıcısı hizmetine yüklemek için, Doğrulayıcı bir <xref:System.ServiceModel.Description.IServiceBehavior> olmalıdır ve `ServiceBehaviors` özelliğine eklenmelidir.) Aşağıdaki kod örneği, adımlarında sonra uygun yapılandırmayı gösterir. ve b., tek istisna dışında, kesin bir ad yok.

        [!code-csharp[LockdownValidation#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#6)]

    3. Machine.config dosyasına kaydedin. Aşağıdaki kod örneği, adım 3 ' teki tüm görevleri gerçekleştirir, ancak değiştirilen Machine. config dosyasının bir kopyasını yerel olarak kaydeder.

        [!code-csharp[LockdownValidation#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#7)]

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, Machine. config dosyasına ortak bir davranışın nasıl ekleneceğini ve bir kopyasını diske kaydetmenizi gösterir. , `InternetClientValidatorBehavior` [Güvenlik doğrulama](../../../../docs/framework/wcf/samples/security-validation.md) örneğinden alınır.

[!code-csharp[LockdownValidation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#1)]

## <a name="net-framework-security"></a>.NET Framework Güvenliği

Yapılandırma dosyası öğelerini şifrelemek da isteyebilirsiniz. Daha fazla bilgi için Ayrıca bkz. bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [DPAPI kullanarak yapılandırma dosyası öğelerini şifreleme](https://go.microsoft.com/fwlink/?LinkId=94954)
- [RSA kullanarak yapılandırma dosyası öğelerini şifreleme](https://go.microsoft.com/fwlink/?LinkId=94955)
