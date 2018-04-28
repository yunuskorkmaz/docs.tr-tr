---
title: Kimlik Doğrulama ile Hizmet Kimliği
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- authentication [WCF], specifying the identity of a service
ms.assetid: a4c8f52c-5b30-45c4-a545-63244aba82be
caps.latest.revision: 32
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a0229ce5c6b7081ae493af22b0daeee444736783
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="service-identity-and-authentication"></a>Kimlik Doğrulama ile Hizmet Kimliği
Bir hizmetin *uç noktası kimlik*hizmeti Web Hizmetleri Açıklama Dili (WSDL) oluşturulan bir değerdir. Herhangi bir istemciye yayılan, bu değer, hizmetin kimliğini doğrulamak için kullanılır. İstemci iletişimi için bir bitiş noktasına başlatır ve hizmeti kendisi için istemci kimlik doğrulaması sonra istemci uç noktası kimlik doğrulama işlemi döndürdü gerçek değer uç noktası kimlik değerle karşılaştırır. Eşleşirlerse, istemci beklenen hizmet uç noktası başvurduğunu emin olur. Bu karşı bir koruma görür *kimlik avı* kötü amaçlı bir hizmet tarafından barındırılan bir uç nokta yönlendiren bir istemci engelleyerek.  
  
 Kimlik ayarı gösteren örnek bir uygulama için bkz: [hizmet kimliği örneği](../../../../docs/framework/wcf/samples/service-identity-sample.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)] uç noktaları ve uç nokta adresleri bkz [adresleri](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md).  
  
> [!NOTE]
>  NT LanMan (NTLM) kimlik doğrulaması için kullandığınızda, NTLM altında istemci sunucu kimlik doğrulaması yapamadı olduğundan, hizmet kimliği işaretlenmemiştir. NTLM Windows Çalışma Grubu'nun bir parçası olduğunda, bilgisayarları veya Kerberos kimlik doğrulamasını desteklemez Windows daha eski bir sürümü çalıştıran olduğunda kullanılır.  
  
 İstemci bir hizmete onun üzerinden ileti göndermek için güvenli bir kanal başlattığında [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Altyapısı hizmeti kimlik doğrulaması ve istemcinin kullandığı uç noktası adresi belirtilen kimlik hizmet kimliği eşleşiyorsa, yalnızca ileti gönderir.  
  
 Kimlik işleme aşağıdaki aşamalardan oluşur:  
  
-   Tasarım zamanında istemci Geliştirici hizmetin kimliğini (WSDL kullanıma sunulur) uç noktanın meta verilerden belirler.  
  
-   Çalışma zamanında, hizmete iletileri göndermeden önce hizmetin güvenlik kimlik bilgileri taleplerini istemci uygulaması denetler.  
  
 İstemci üzerinde işlem kimliği, istemci kimlik doğrulama hizmetine benzerdir. İstemci kimlik doğrulaması kadar güvenli bir hizmet kodu yürütmez. Benzer şekilde, istemci ne önceden hizmetin meta verilerini bilinen üzerinde hizmetin kimlik doğrulaması kadar hizmete ileti tabanlı göndermez.  
  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A> Özelliği <xref:System.ServiceModel.EndpointAddress> sınıfı, istemci tarafından adlı hizmeti kimliğini temsil eder. Hizmet yayımlar <xref:System.ServiceModel.EndpointAddress.Identity%2A> meta verilerinde. İstemci Geliştirici çalıştığında [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) Hizmeti uç noktası karşı üretilen yapılandırma hizmetin değerini içeren <xref:System.ServiceModel.EndpointAddress.Identity%2A> özelliği. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] (Güvenliği ile yapılandırılmışsa) altyapısı hizmeti belirtilen kimlik sahip olduğunu doğrular.  
  
> [!IMPORTANT]
>  Meta veri hizmeti beklenen kimliğini içerdiğinden, hizmeti meta verileri güvenli araçlarla, örneğin, hizmet için bir HTTPS uç noktası oluşturarak ortaya önerilir. Daha fazla bilgi için bkz: [nasıl yapılır: meta veri uç noktalarını güvenli](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md).  
  
## <a name="identity-types"></a>Kimlik türleri  
 Bir hizmeti kimlikleri altı tür sağlayabilir. İçinde bulunan bir öğeye karşılık gelen her kimlik türü `<identity>` yapılandırma öğesinde. Kullanılan türü senaryo ve hizmetin güvenlik gereksinimlerine bağlıdır. Aşağıdaki tabloda, her kimlik türü açıklanmaktadır.  
  
|Kimlik türü|Açıklama|Tipik senaryo|  
|-------------------|-----------------|----------------------|  
|Etki Alanı Adı Sistemi (DNS)|Bu öğe X.509 sertifikalarını veya Windows hesapları kullanın. Bu öğe belirtilen değere sahip kimlik bilgisi belirtilen DNS adı karşılaştırır.|DNS ile sertifikalar kullanmak üzere DNS onay sağlar ya da konu adları. Sertifika konu adı ve aynı DNS ile yeniden, kimlik denetimi hala geçerli olur. Bir sertifika yeniden olduğunda yeni bir RSA anahtarı alır ancak aynı DNS veya konu adı korur. Başka bir deyişle, istemciler kendi kimlik bilgilerini hizmeti hakkında güncelleştirmek gerekmez.|  
|Sertifika. Varsayılan zaman `ClientCredentialType` sertifikayı ayarlayın.|Bu öğe istemcisi ile Karşılaştırılacak Base64 ile kodlanmış X.509 Sertifika değer belirtir.<br /><br /> Kullanırken bu öğe ayrıca bir [!INCLUDE[infocard](../../../../includes/infocard-md.md)] hizmetinde kimlik doğrulaması için bir kimlik bilgisi olarak.|Bu öğe tek bir sertifika parmak izi değerini tabanlı kimlik doğrulaması kısıtlar. Parmak izi değerleri benzersiz olduğundan bu katı kimlik doğrulamasını etkinleştirir. Bu bir uyarısıyla birlikte gelir: sertifika ile aynı konu adı yeniden varsa, yeni bir parmak izi ayrıca içerir. Bu nedenle, istemciler yeni parmak izini bilinen sürece hizmet doğrulamak mümkün değildir. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] bkz: bir sertifikanın parmak izi bulma, [nasıl yapılır: bir sertifikanın parmak izini alma](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).|  
|Sertifika başvurusu|Daha önce açıklanan sertifika seçeneği aynıdır. Ancak, bu öğe, bir sertifika adını belirtin ve sertifika alınacağı konum depolamak sağlar.|Daha önce açıklanan sertifika senaryo ile aynıdır.<br /><br /> Sertifika deposu konumu değiştirebilir avantajdır.|  
|RSA|Bu öğe istemcisi ile karşılaştırmak için bir RSA anahtarı değeri belirtir. Bu sertifika seçeneğine benzer ancak sertifikanın parmak izi kullanmak yerine, sertifikanın RSA anahtarı yerine kullanılır.|RSA onay, özellikle kendi RSA anahtarı temel tek bir sertifika kimlik doğrulaması sınırlamanıza olanak sağlar. Bu, belirli bir RSA anahtarı RSA anahtar değeri değişirse, artık mevcut istemcileriyle çalışır hizmetini ödün verme pahasına daha sıkı kimlik doğrulaması sağlar.|  
|Kullanıcı asıl adı (UPN). Varsayılan zaman `ClientCredentialType` ayarlanır Windows ve hizmet işlemi sistem hesaplarından birini altında çalışmıyor.|Bu öğe hizmetinin altında çalışmakta olduğu UPN belirtir. Kerberos protokolü ve kimlik bölümüne bakın [kimlik doğrulaması için bir hizmetin kimliğini geçersiz kılma](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md).|Bu hizmetin belirli bir Windows kullanıcı hesabı altında çalışıyor sağlar. Kullanıcı hesabı, geçerli oturum açmış kullanıcı veya belirli bir kullanıcı hesabı altında çalışan hizmet olabilir.<br /><br /> Hizmeti Active Directory ortamında etki alanı hesabı altında çalışıyorsa, bu ayar Windows Kerberos güvenlik yararlanır.|  
|Hizmet asıl adı (SPN). Varsayılan zaman `ClientCredentialType` ayarlanır Windows ve hizmet için işlem sistem hesaplarından birini altında çalışan — Yerelhizmet, LocalSystem veya NetworkService.|Bu öğe hizmet hesabıyla ilişkilendirilmiş SPN belirtir. Kerberos protokolü ve kimlik bölümüne bakın [kimlik doğrulaması için bir hizmetin kimliğini geçersiz kılma](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md).|Bu, SPN ve SPN ile ilişkili özel bir Windows hesabı Hizmeti'ni tanımlamak sağlar.<br /><br /> Hizmetin kullanıcı hesabı için bir makine hesabı ilişkilendirilecek Setspn.exe aracını kullanabilirsiniz.<br /><br /> Bu ayar, Windows hizmet Sistem hesaplarından birini altında veya ve bilgisayar ile ilişkili bir SPN ada sahip bir etki alanı hesabı altında çalışıyorsa, güvenliği, Kerberos Active Directory ortamında etki alanının üyesi yararlanır.|  
  
## <a name="specifying-identity-at-the-service"></a>Hizmetine kimliğini belirtme  
 Genellikle, bir istemci kimlik bilgisi türü seçimi hizmet metaveri kimliği türü belirler olduğu bir hizmette kimlik Ayarla gerekmez. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] geçersiz kılma veya hizmet kimliği belirtin, bkz [kimlik doğrulaması için bir hizmetin kimliğini geçersiz kılma](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md).  
  
## <a name="using-the-identity-element-in-configuration"></a>Kullanarak \<kimliği > yapılandırma öğesi  
 İstemci kimlik bilgisi türü için daha önce gösterilen bağlamadaki değiştirirseniz `Certificate,` oluşturulan WSDL seri hale getirilmiş bir Base64 içeriyorsa aşağıdaki kodda gösterildiği gibi kimlik değeri X.509 sertifikası. Bu Windows dışındaki tüm istemci kimlik bilgisi türü için varsayılan değerdir.  
  
  
  
 Varsayılan hizmet kimliği değerini değiştirin ya da kullanarak kimliği türü değiştirme `<identity>` öğesi yapılandırmasında veya kodda kimliği ayarlayarak. Bir etki alanı adı sistemi (DNS) kimlik değeri olan aşağıdaki yapılandırma kodunu ayarlar `contoso.com`.  
  
  
  
## <a name="setting-identity-programmatically"></a>Kimlik programlı olarak ayarlama  
 Çünkü, bir kimlik açıkça belirtmek, hizmet yok. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] otomatik olarak belirler. Ancak, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gerekli olursa bir uç nokta üzerinde bir kimlik belirtmenize olanak tanır. Aşağıdaki kod, belirli bir DNS kimlik ile yeni bir hizmet uç noktası ekler.  
  
 [!code-csharp[C_Identity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_identity/cs/source.cs#5)]
 [!code-vb[C_Identity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_identity/vb/source.vb#5)]  
  
## <a name="specifying-identity-at-the-client"></a>İstemci kimliğini belirtme  
 Tasarım zamanında bir istemci geliştirici genellikle kullandığı [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) istemci yapılandırması oluşturmak için. Oluşturulan yapılandırma dosyası (amaçlanan istemci tarafından kullanılmak üzere), sunucunun kimliğini içerir. Örneğin, aşağıdaki kod önceki örnekte gösterildiği gibi bir DNS kimliği belirten bir hizmetinden oluşturulur. İstemcinin uç noktası kimlik değeri hizmet eşleşmesini unutmayın. Bu durumda, istemci hizmeti için Windows (Kerberos) kimlik bilgilerini aldığında, değerin olmasını bekler `contoso.com`.  
  
  
  
 Windows, yerine hizmeti istemcisi kimlik bilgisi türü bir sertifika belirtir, sonra sertifikanın DNS özellik değeri olması bekleniyor, `contoso.com`. (Veya DNS özelliği olan ise `null`, sertifikanın konu adı olmalıdır `contoso.com`.)  
  
#### <a name="using-a-specific-value-for-identity"></a>Belirli bir değere kimliğini kullanma  
 İstemci yapılandırma dosyası, hizmetin kimliğini nasıl belirli bir değer olması bekleniyor gösterir. Aşağıdaki örnekte, istemci iki uç ile iletişim kurabilir. İlk sertifika parmak izi ve ikinci bir sertifika RSA anahtarı ile tanımlanır. Diğer bir deyişle, yalnızca bir ortak anahtar/özel içeren bir sertifika anahtar çifti, ancak güvenilir bir yetkili tarafından verilmemiş.  
  
  
  
## <a name="identity-checking-at-run-time"></a>Çalışma zamanında denetimi kimliği  
 Tasarım zamanında bir istemci Geliştirici meta verilerini aracılığıyla sunucunun kimliğini belirler. Çalışma zamanında, uç nokta hizmetini çağırmadan önce kimlik denetimi gerçekleştirilir.  
  
 Kimlik değerini meta verileri tarafından belirtilen kimlik doğrulama türü bağlıdır; diğer bir deyişle, hizmet için kullanılan kimlik bilgileri türü.  
  
 Kanal, ileti veya aktarım düzeyi Güvenli Yuva Katmanı (SSL) X.509 sertifikalarıyla için kimlik doğrulaması kullanarak kimlik doğrulaması için yapılandırılmışsa, aşağıdaki kimlik değerler geçerlidir:  
  
-   DNS. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] SSL el sıkışması sırasında sağlanan sertifikanın DNS içerdiğini garantiler veya `CommonName` (CN) öznitelik istemci DNS kimliğini belirtilen değere eşit. Sunucu sertifikasının geçerliliğini belirlemek için bu denetimleri ayrıca yapıldığını unutmayın. Varsayılan olarak, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sunucu sertifikasının güvenilen kök yetkilisi tarafından verilen olduğunu doğrular.  
  
-   Sertifika. SSL el sıkışması sırasında [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uzak uç nokta kimlik belirtilen tam sertifika değer sağlar sağlar.  
  
-   Sertifika başvurusu. Sertifika ile aynıdır.  
  
-   RSA. SSL el sıkışması sırasında [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uzak uç nokta kimlik belirtilen RSA anahtarı tam sağlar sağlar.  
  
 Hizmet, ileti veya aktarım düzeyi SSL kimlik doğrulaması için Windows kimlik bilgileri ile kullanarak kimliğini doğrular ve kimlik bilgisi görüşür, aşağıdaki kimlik değerler geçerlidir:  
  
-   DNS. Böylece DNS adı denetlenebilir anlaşma sunucunun hizmetin SPN'si geçirir. SPN biçimindedir `host/<dns name>`.  
  
-   SPN. SPN döndürülür, örneğin, bir açık hizmet `host/myservice`.  
  
-   UPN. Hizmet hesabı UPN. UPN biçimindedir `username` @ `domain`. Örneğin, bir kullanıcı hesabında hizmet çalışırken olabilir `username@contoso.com`.  
  
 Program aracılığıyla kimlik belirtmeyi (kullanarak <xref:System.ServiceModel.EndpointAddress.Identity%2A> özelliği) isteğe bağlıdır. Hiçbir kimlik belirtilir ve Windows istemci kimlik bilgisi türü ise, varsayılan SPN önekine sahip hizmet uç nokta adresi ana bilgisayar adı bölümü için ayarlanan değer olan "konak /" değişmez. Hiçbir kimlik belirtilir ve sertifika istemci kimlik bilgisi türü ise, varsayılan değer `Certificate`. Bu, her iki ileti ve aktarım düzeyi güvenlik için geçerlidir.  
  
## <a name="identity-and-custom-bindings"></a>Kimlik ve özel bağlamalar  
 Bir hizmetin kimliğini kullanılan bağlama türü bağımlı olduğundan, uygun kimlik özel bağlama oluşturma sırasında sunulur emin olun. Kimliği güvenli konuşma başlatma bağlaması için uç bağlama için kimlik eşleşmediği için örneğin, aşağıdaki kod örneğinde, sunulan kimlik güvenlik türüyle uyumlu değil. Güvenli Konuşmayla bağlama DNS kimliğini ayarlar sırada <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement> UPN veya SPN kimliğini ayarlar.  
  
 [!code-csharp[C_Identity#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_identity/cs/source.cs#8)]
 [!code-vb[C_Identity#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_identity/vb/source.vb#8)]  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] bağlama öğeleri özel bağlama için doğru yığın nasıl [Creating User-Defined bağlamaları](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)] özel bağlama ile oluşturma <xref:System.ServiceModel.Channels.SecurityBindingElement>, bkz: [nasıl yapılır: belirtilen kimlik doğrulama modu için SecurityBindingElement oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [Nasıl yapılır: Belirtilen Bir Kimlik Doğrulama Modu için SecurityBindingElement Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)  
 [Nasıl yapılır: Özel İstemci Kimliği Doğrulayıcı Oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md)  
 [Kimlik Bilgisi Türü Seçme](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [Sertifikalarla Çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [ServiceModel Meta Veri Yardımcı Programı Aracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [Kullanıcı Tanımlı Bağlamalar Oluşturma](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)  
 [Nasıl yapılır: Bir Sertifikanın Parmak İzini Alma](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
