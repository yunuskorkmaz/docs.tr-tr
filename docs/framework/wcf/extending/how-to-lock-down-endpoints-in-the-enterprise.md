---
title: 'Nasıl yapılır: Enterprise Uç Noktalarını Kilitleme'
ms.date: 03/30/2017
ms.assetid: 1b7eaab7-da60-4cf7-9d6a-ec02709cf75d
ms.openlocfilehash: 68a7b80a01d9b1a8c5243331e63a1b82996e8ee6
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558153"
---
# <a name="how-to-lock-down-endpoints-in-the-enterprise"></a>Nasıl yapılır: Enterprise Uç Noktalarını Kilitleme

Büyük kuruluşlar genellikle uygulamaların kurumsal güvenlik ilkeleriyle uyumlu olarak geliştirilmesini gerektirir. Aşağıdaki konuda, bilgisayarlarda yüklü olan tüm Windows Communication Foundation (WCF) istemci uygulamalarını doğrulamak için kullanılabilecek bir istemci uç noktası doğrulayıcısı geliştirme ve yükleme açıklanmaktadır.

Bu durumda, bu uç nokta davranışı machine.config dosyasındaki istemci bölümüne eklendiğinden, Doğrulayıcı bir istemci doğrulayıcısı olur [\<commonBehaviors>](../../configure-apps/file-schema/wcf/commonbehaviors.md) . WCF, ortak uç nokta davranışlarını yalnızca istemci uygulamaları için yükler ve yalnızca hizmet uygulamaları için ortak hizmet davranışlarını yükler. Bu hizmet uygulamalarına yönelik aynı Doğrulayıcı 'yı yüklemek için doğrulayıcının bir hizmet davranışı olması gerekir. Daha fazla bilgi için bölümüne bakın [\<commonBehaviors>](../../configure-apps/file-schema/wcf/commonbehaviors.md) .

> [!IMPORTANT]
> <xref:System.Security.AllowPartiallyTrustedCallersAttribute>Bir yapılandırma dosyasının bölümüne eklenen öznitelik (APTCA) ile işaretlenmemiş hizmet veya uç nokta davranışları, [\<commonBehaviors>](../../configure-apps/file-schema/wcf/commonbehaviors.md) Uygulama kısmi güven ortamında çalıştırıldığında ve bu gerçekleştiğinde hiçbir özel durum oluşturulmaz. Doğrulayıcılar gibi yaygın davranışları çalıştırmaya zorlamak için şunlardan birini yapmanız gerekir:
>
> - <xref:System.Security.AllowPartiallyTrustedCallersAttribute>Kısmi güven uygulaması olarak dağıtıldığında çalışabilmesi için ortak davranışınızı özniteliğiyle işaretleyin. APTCA tarafından işaretlenmiş derlemelerin çalıştırılmasını engellemek için bilgisayarda bir kayıt defteri girişi ayarlanmayacağınızı unutmayın.
>
> - Uygulamanın, uygulamayı kısmi güven ortamında çalıştırmak için kod erişimi güvenlik ayarlarını değiştiremediği tam güvenilir bir uygulama olarak dağıtıldığından emin olun. Bunu yapabilmeleri durumunda özel Doğrulayıcı çalışmaz ve hiçbir özel durum oluşturulmaz. Bunu sağlamanın bir yolu için, `levelfinal` [kod erişimi güvenlik ilkesi aracını kullanma (Caspol.exe)](../../tools/caspol-exe-code-access-security-policy-tool.md)seçeneğine bakın.
>
> Daha fazla bilgi için bkz. [kısmi güvenin En Iyi uygulamaları](../feature-details/partial-trust-best-practices.md) ve [Desteklenen Dağıtım senaryoları](../feature-details/supported-deployment-scenarios.md).

### <a name="to-create-the-endpoint-validator"></a>Uç nokta doğrulayıcısı oluşturmak için

1. <xref:System.ServiceModel.Description.IEndpointBehavior>Yönteminde istenen doğrulama adımları ile oluşturun <xref:System.ServiceModel.Description.IEndpointBehavior.Validate%2A> . Aşağıdaki kod bir örnek sağlar. ( `InternetClientValidatorBehavior` [Güvenlik doğrulama](../samples/security-validation.md) örneğinden alınır.)

    [!code-csharp[LockdownValidation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/internetclientvalidatorbehavior.cs#2)]

2. <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>Adım 1 ' de oluşturulan uç nokta doğrulayıcısı kaydeden yeni oluştur. Aşağıdaki kod örneği bunu gösterir. (Bu örnek için özgün kod, [güvenlik doğrulama](../samples/security-validation.md) örneğidir.)

    [!code-csharp[LockdownValidation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/internetclientvalidatorelement.cs#3)]

3. Derlenmiş derlemenin bir tanımlayıcı ad ile imzalandığından emin olun. Ayrıntılar için bkz. [tanımlayıcı ad Aracı (SN.EXE)](../../tools/sn-exe-strong-name-tool.md) ve dilinize yönelik derleyici komutları.

### <a name="to-install-the-validator-into-the-target-computer"></a>Doğrulayıcısı hedef bilgisayara yüklemek için

1. Uygun mekanizmayı kullanarak uç nokta doğrulayıcısı 'nı yükler. Bir kuruluşta bu, grup ilkesi ve Systems Management Server (SMS) ile kullanılabilir.

2. [Gacutil.exe (genel bütünleştirilmiş kod önbelleği aracı)](../../tools/gacutil-exe-gac-tool.md)kullanarak, kesin adlı derlemeyi genel bütünleştirilmiş kod önbelleğine yükler.

3. <xref:System.Configuration?displayProperty=nameWithType>Ad alanı türlerini şu şekilde kullanın:

    1. Uzantıyı [\<behaviorExtensions>](../../configure-apps/file-schema/wcf/behaviorextensions.md) tam nitelikli bir tür adı kullanarak bölüme ekleyin ve öğeyi kilitleyin.

         [!code-csharp[LockdownValidation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#5)]

    2. Bölüm özelliğine Behavior öğesini ekleyin `EndpointBehaviors` [\<commonBehaviors>](../../configure-apps/file-schema/wcf/commonbehaviors.md) ve öğesini kilitleyin. (Doğrulayıcısı hizmetine yüklemek için, Doğrulayıcı bir olmalıdır <xref:System.ServiceModel.Description.IServiceBehavior> ve `ServiceBehaviors` özelliğine eklenmelidir.) Aşağıdaki kod örneği, adımlarında sonra uygun yapılandırmayı gösterir. ve b., tek istisna dışında, kesin bir ad yok.

        [!code-csharp[LockdownValidation#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#6)]

    3. machine.config dosyasını kaydedin. Aşağıdaki kod örneği, adım 3 ' teki tüm görevleri gerçekleştirir, ancak değiştirilen machine.config dosyanın bir kopyasını yerel olarak kaydeder.

        [!code-csharp[LockdownValidation#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#7)]

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, machine.config dosyasına ortak bir davranışın nasıl ekleneceğini ve bir kopyasının diske nasıl kaydedileceğini gösterir. , `InternetClientValidatorBehavior` [Güvenlik doğrulama](../samples/security-validation.md) örneğinden alınır.

[!code-csharp[LockdownValidation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#1)]

## <a name="net-framework-security"></a>.NET Framework Güvenliği

Yapılandırma dosyası öğelerini şifrelemek da isteyebilirsiniz. Daha fazla bilgi için Ayrıca bkz. bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [DPAPI kullanarak yapılandırma dosyası öğelerini şifreleme](/previous-versions/msp-n-p/ff647398(v=pandp.10))
- [RSA kullanarak yapılandırma dosyası öğelerini şifreleme](/previous-versions/msp-n-p/ff650304(v=pandp.10))
