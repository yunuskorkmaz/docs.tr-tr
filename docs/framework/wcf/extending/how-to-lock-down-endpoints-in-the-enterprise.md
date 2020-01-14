---
title: 'Nasıl yapılır: Enterprise Uç Noktalarını Kilitleme'
ms.date: 03/30/2017
ms.assetid: 1b7eaab7-da60-4cf7-9d6a-ec02709cf75d
ms.openlocfilehash: 35b9a1dbebce48823799689a581033d0483c3984
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937675"
---
# <a name="how-to-lock-down-endpoints-in-the-enterprise"></a>Nasıl yapılır: Enterprise Uç Noktalarını Kilitleme

Büyük kuruluşlar genellikle uygulamaların kurumsal güvenlik ilkeleriyle uyumlu olarak geliştirilmesini gerektirir. Aşağıdaki konuda, bilgisayarlarda yüklü olan tüm Windows Communication Foundation (WCF) istemci uygulamalarını doğrulamak için kullanılabilecek bir istemci uç noktası doğrulayıcısı geliştirme ve yükleme açıklanmaktadır.

Bu durumda, bu uç nokta davranışı Machine. config dosyasındaki Client [\<commonbehavior >](../../configure-apps/file-schema/wcf/commonbehaviors.md) bölümüne eklendiğinden, Doğrulayıcı bir istemci doğrulayıcısı olur. WCF, ortak uç nokta davranışlarını yalnızca istemci uygulamaları için yükler ve yalnızca hizmet uygulamaları için ortak hizmet davranışlarını yükler. Bu hizmet uygulamalarına yönelik aynı Doğrulayıcı 'yı yüklemek için doğrulayıcının bir hizmet davranışı olması gerekir. Daha fazla bilgi için [\<Commondavranışlar >](../../configure-apps/file-schema/wcf/commonbehaviors.md) bölümüne bakın.

> [!IMPORTANT]
> Bir yapılandırma dosyasının [\<Commondavranışları >](../../configure-apps/file-schema/wcf/commonbehaviors.md) bölümüne eklenen <xref:System.Security.AllowPartiallyTrustedCallersAttribute> özniteliği (aptca) ile işaretlenmemiş hizmet veya uç nokta davranışları, uygulama kısmi güven ortamında çalıştırıldığında ve bu gerçekleştiğinde hiçbir özel durum oluşturulmaz. Doğrulayıcılar gibi yaygın davranışları çalıştırmaya zorlamak için şunlardan birini yapmanız gerekir:
>
> - Kısmi güven uygulaması olarak dağıtıldığında çalışabilmesi için, <xref:System.Security.AllowPartiallyTrustedCallersAttribute> özniteliğiyle ortak davranışınızı işaretleyin. APTCA tarafından işaretlenmiş derlemelerin çalıştırılmasını engellemek için bilgisayarda bir kayıt defteri girişi ayarlanmayacağınızı unutmayın.
>
> - Uygulamanın, uygulamayı kısmi güven ortamında çalıştırmak için kod erişimi güvenlik ayarlarını değiştiremediği tam güvenilir bir uygulama olarak dağıtıldığından emin olun. Bunu yapabilmeleri durumunda özel Doğrulayıcı çalışmaz ve hiçbir özel durum oluşturulmaz. Bunu sağlamanın bir yolu için, [kod erişimi güvenlik Ilkesi aracı 'nı (Caspol. exe)](../../tools/caspol-exe-code-access-security-policy-tool.md)kullanarak `levelfinal` seçeneğine bakın.
>
> Daha fazla bilgi için bkz. [kısmi güvenin En Iyi uygulamaları](../feature-details/partial-trust-best-practices.md) ve [Desteklenen Dağıtım senaryoları](../feature-details/supported-deployment-scenarios.md).

### <a name="to-create-the-endpoint-validator"></a>Uç nokta doğrulayıcısı oluşturmak için

1. <xref:System.ServiceModel.Description.IEndpointBehavior.Validate%2A> yönteminde istenen Doğrulama adımlarıyla bir <xref:System.ServiceModel.Description.IEndpointBehavior> oluşturun. Aşağıdaki kod bir örnek sağlar. (`InternetClientValidatorBehavior`, [güvenlik doğrulama](../samples/security-validation.md) örneğinden alınır.)

    [!code-csharp[LockdownValidation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/internetclientvalidatorbehavior.cs#2)]

2. Adım 1 ' de oluşturulan uç nokta doğrulayıcısı kaydeden yeni <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> oluşturun. Aşağıdaki kod örneği bunu gösterir. (Bu örnek için özgün kod, [güvenlik doğrulama](../samples/security-validation.md) örneğidir.)

    [!code-csharp[LockdownValidation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/internetclientvalidatorelement.cs#3)]

3. Derlenmiş derlemenin bir tanımlayıcı ad ile imzalandığından emin olun. Ayrıntılar için bkz [. tanımlayıcı ad Aracı (sn. EXE)](../../tools/sn-exe-strong-name-tool.md) ve dilinize yönelik derleyici komutlarını.

### <a name="to-install-the-validator-into-the-target-computer"></a>Doğrulayıcısı hedef bilgisayara yüklemek için

1. Uygun mekanizmayı kullanarak uç nokta doğrulayıcısı 'nı yükler. Bir kuruluşta bu, grup ilkesi ve Systems Management Server (SMS) ile kullanılabilir.

2. [Gacutil. exe](../../tools/gacutil-exe-gac-tool.md)' yi kullanarak, kesin adlı derlemeyi genel bütünleştirilmiş kod önbelleğine yükler (genel bütünleştirilmiş kod önbelleği aracı).

3. <xref:System.Configuration?displayProperty=nameWithType> ad alanı türlerini kullanın:

    1. Uzantıyı tam nitelikli bir tür adı kullanarak [\<behaviorExtensions >](../../configure-apps/file-schema/wcf/behaviorextensions.md) bölümüne ekleyin ve öğeyi kilitleyin.

         [!code-csharp[LockdownValidation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#5)]

    2. Davranış öğesini [\<commonbehavior >](../../configure-apps/file-schema/wcf/commonbehaviors.md) bölümünün `EndpointBehaviors` özelliğine ekleyin ve öğeyi kilitleyin. (Doğrulayıcısı hizmetine yüklemek için, Doğrulayıcı bir <xref:System.ServiceModel.Description.IServiceBehavior> olmalıdır ve `ServiceBehaviors` özelliğine eklenmelidir.) Aşağıdaki kod örneği, adımlarında sonra uygun yapılandırmayı gösterir. ve b., tek istisna dışında, kesin bir ad yok.

        [!code-csharp[LockdownValidation#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#6)]

    3. Machine.config dosyasına kaydedin. Aşağıdaki kod örneği, adım 3 ' teki tüm görevleri gerçekleştirir, ancak değiştirilen Machine. config dosyasının bir kopyasını yerel olarak kaydeder.

        [!code-csharp[LockdownValidation#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#7)]

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, Machine. config dosyasına ortak bir davranışın nasıl ekleneceğini ve bir kopyasını diske kaydetmenizi gösterir. `InternetClientValidatorBehavior`, [güvenlik doğrulama](../samples/security-validation.md) örneğinden alınır.

[!code-csharp[LockdownValidation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#1)]

## <a name="net-framework-security"></a>.NET Framework Güvenliği

Yapılandırma dosyası öğelerini şifrelemek da isteyebilirsiniz. Daha fazla bilgi için Ayrıca bkz. bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [DPAPI kullanarak yapılandırma dosyası öğelerini şifreleme](https://docs.microsoft.com/previous-versions/msp-n-p/ff647398(v=pandp.10))
- [RSA kullanarak yapılandırma dosyası öğelerini şifreleme](https://docs.microsoft.com/previous-versions/msp-n-p/ff650304(v=pandp.10))
