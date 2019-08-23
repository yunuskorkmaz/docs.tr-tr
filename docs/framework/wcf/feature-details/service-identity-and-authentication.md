---
title: Kimlik Doğrulama ile Hizmet Kimliği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- authentication [WCF], specifying the identity of a service
ms.assetid: a4c8f52c-5b30-45c4-a545-63244aba82be
ms.openlocfilehash: f9ed2a7c284588a0fb481d41dca61e663fd090b1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969242"
---
# <a name="service-identity-and-authentication"></a>Kimlik Doğrulama ile Hizmet Kimliği
Hizmetin *uç nokta kimliği* , hizmet Web Hizmetleri Açıklama DILI (wsdl) tarafından oluşturulan bir değerdir. Bu değer, herhangi bir istemciye yayılan, hizmetin kimliğini doğrulamak için kullanılır. İstemci bir uç noktaya iletişim başlattıktan ve hizmet istemcinin kimliğini doğruladıktan sonra, uç nokta kimlik değerini, uç nokta kimlik doğrulama işleminin döndürdüğü gerçek değer ile karşılaştırır. Eşleşiyorlarsa, istemci beklenen hizmet uç noktasıyla iletişim kurduysa emin olur. Bu, bir istemcinin kötü amaçlı bir hizmet tarafından barındırılan bir uç noktaya yeniden yönlendirilmesini önlemek yoluyla *kimlik avına* karşı koruma olarak çalışır.  
  
 Kimlik ayarını gösteren örnek bir uygulama için bkz. [hizmet kimliği örneği](../../../../docs/framework/wcf/samples/service-identity-sample.md). Uç noktalar ve uç nokta adresleri hakkında daha fazla bilgi için bkz. [adresler](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md).  
  
> [!NOTE]
> Kimlik doğrulaması için NT LanMan (NTLM) kullandığınızda, NTLM altında istemci sunucunun kimliğini doğrulayamadığından hizmet kimliği denetlenmez. Bilgisayarlar bir Windows çalışma grubunun parçası olduğunda veya Kerberos kimlik doğrulamasını desteklemeyen eski bir Windows sürümü çalıştırıldığında NTLM kullanılır.  
  
 İstemci, üzerinden bir hizmete ileti göndermek için güvenli bir kanal başlattığında, Windows Communication Foundation (WCF) altyapısı hizmetin kimliğini doğrular ve yalnızca hizmet kimliği uç noktada belirtilen kimlikle eşleşiyorsa iletiyi gönderir istemcinin kullandığı adres.  
  
 Kimlik işleme aşağıdaki aşamalardan oluşur:  
  
- Tasarım zamanında, istemci geliştiricisi uç noktanın meta verilerindeki hizmetin kimliğini (WSDL aracılığıyla gösterilir) belirler.  
  
- Çalışma zamanında istemci uygulaması, hizmete herhangi bir ileti göndermeden önce hizmetin güvenlik kimlik bilgileri taleplerini kontrol eder.  
  
 İstemci üzerindeki kimlik işleme, hizmette istemci kimlik doğrulamasına benzer. Güvenli bir hizmet, istemci kimlik bilgilerinin kimliği doğrulanana kadar kodu çalıştırmaz. Benzer şekilde, istemci, hizmet kimlik bilgilerinin kimliği, hizmetin meta verilerinden öncelikli olarak bilinene kadar hizmetine ileti göndermez.  
  
 <xref:System.ServiceModel.EndpointAddress> Sınıfının özelliği, istemci tarafından çağrılan hizmetin kimliğini temsil eder. <xref:System.ServiceModel.EndpointAddress.Identity%2A> Hizmeti meta verilerinde yayımlar <xref:System.ServiceModel.EndpointAddress.Identity%2A> . İstemci geliştiricisi, hizmet uç noktasında [ServiceModel meta veri yardımcı programı aracı 'nı (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) çalıştırdığında, oluşturulan yapılandırma hizmetin <xref:System.ServiceModel.EndpointAddress.Identity%2A> özelliğinin değerini içerir. WCF altyapısı (güvenlikle yapılandırıldıysa), hizmetin belirtilen kimliğe sahip olduğunu doğrular.  
  
> [!IMPORTANT]
> Meta veriler hizmetin beklenen kimliğini içerir, bu nedenle hizmet meta verilerini güvenli yollarla kullanıma sunabilmeniz önerilir, örneğin, hizmet için bir HTTPS uç noktası oluşturarak. Daha fazla bilgi için [nasıl yapılır: Güvenli meta veri](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md)uç noktaları.  
  
## <a name="identity-types"></a>Kimlik türleri  
 Bir hizmet, altı tür kimlik sağlayabilir. Her kimlik türü, `<identity>` yapılandırmada öğesinin içinde yer alan bir öğeye karşılık gelir. Kullanılan tür senaryoya ve hizmetin güvenlik gereksinimlerine bağlıdır. Aşağıdaki tabloda her kimlik türü açıklanmaktadır.  
  
|Kimlik türü|Açıklama|Tipik senaryo|  
|-------------------|-----------------|----------------------|  
|Etki Alanı Adı Sistemi (DNS)|Bu öğeyi X. 509.440 sertifikaları veya Windows hesaplarıyla kullanın. Kimlik bilgilerinde belirtilen DNS adını bu öğede belirtilen değerle karşılaştırır.|DNS denetimi, sertifikaları DNS veya konu adlarıyla kullanmanıza olanak sağlar. Bir sertifika aynı DNS veya konu adıyla yeniden kullanılıyorsa, kimlik denetimi hala geçerli olur. Bir sertifika yeniden yayımlandığında, yeni bir RSA anahtarı alır, ancak aynı DNS veya konu adını korur. Bu, istemcilerin hizmet hakkındaki kimlik bilgilerini güncelleştirmesi gerekmediği anlamına gelir.|  
|Sertifika. Varsayılan `ClientCredentialType` olarak, sertifika olarak ayarlanır.|Bu öğe, istemcisiyle karşılaştırmak için Base64 kodlamalı bir X. 509.440 sertifika değeri belirtir.<br /><br /> Ayrıca, hizmet kimliğini doğrulamak için bir CardSpace kimlik bilgisi olarak kullanılırken bu öğeyi kullanın.|Bu öğe, kimlik doğrulamasını parmak izi değerine göre tek bir sertifikayla kısıtlar. Bu, parmak izi değerleri benzersiz olduğundan daha sıkı kimlik doğrulama imkanı sunar. Bu bir desteklenmediği uyarısıyla ile birlikte gelir: Sertifika aynı konu adıyla yeniden bırakılırsa, yeni bir parmak Izi de vardır. Bu nedenle, yeni parmak izi tanınmadığı takdirde istemciler hizmeti doğrulayamayabilir. Bir sertifikanın parmak izini bulma hakkında daha fazla bilgi için bkz [. nasıl yapılır: Bir sertifikanın](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)parmak izini alın.|  
|Sertifika başvurusu|Daha önce açıklanan sertifika seçeneğiyle aynı. Ancak, bu öğe, sertifikanın alınacağı bir sertifika adı ve depolama konumu belirtmenize olanak sağlar.|Daha önce açıklanan sertifika senaryosuna benzer.<br /><br /> Avantaj, sertifika depolama konumunun değişebilir.|  
|RSA|Bu öğe, istemcisiyle Karşılaştırılacak bir RSA anahtar değeri belirtir. Bu, sertifika seçeneğine benzer, ancak sertifikanın parmak izini kullanmak yerine sertifikanın RSA anahtarı kullanılır.|Bir RSA denetimi, kimlik doğrulamasını, RSA anahtarına bağlı olarak tek bir sertifika ile kısıtlamanıza olanak sağlar. Bu, hizmet masrafına belirli bir RSA anahtarının daha sıkı şekilde doğrulanmasını sağladığından, RSA anahtar değeri değişirse artık mevcut istemcilerle birlikte çalışmaz.|  
|Kullanıcı asıl adı (UPN). Varsayılan değer Windows olarak `ClientCredentialType` ayarlandığında ve hizmet işlemi sistem hesaplarından biri altında çalışmadığı zaman varsayılandır.|Bu öğe, hizmetin altında çalıştığı UPN 'yi belirtir. [Kimlik doğrulaması için bir hizmetin kimliğini geçersiz kılan](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md)Kerberos protokolü ve kimlik bölümüne bakın.|Bu, hizmetin belirli bir Windows Kullanıcı hesabı altında çalıştığından emin olmanızı sağlar. Kullanıcı hesabı, geçerli oturum açmış kullanıcı veya belirli bir kullanıcı hesabı altında çalışan hizmet olabilir.<br /><br /> Bu ayar, hizmet Active Directory ortamında bir etki alanı hesabı altında çalışıyorsa Windows Kerberos güvenliğinin avantajlarından yararlanır.|  
|Hizmet asıl adı (SPN). Varsayılan değer Windows olarak `ClientCredentialType` ayarlandığında ve hizmet işlemi sistem hesaplarından biri (LocalService, LocalSystem veya NetworkService) altında çalışıyorsa varsayılandır.|Bu öğe, hizmetin hesabıyla ilişkili SPN 'YI belirtir. [Kimlik doğrulaması için bir hizmetin kimliğini geçersiz kılan](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md)Kerberos protokolü ve kimlik bölümüne bakın.|Bu, SPN 'nin ve SPN ile ilişkili belirli Windows hesabının hizmeti belirlemesine de sağlar.<br /><br /> Setspn. exe aracını kullanarak hizmetin Kullanıcı hesabı için bir makine hesabını ilişkilendirebilirsiniz.<br /><br /> Bu ayar, hizmet sistem hesaplarından biri altında veya bununla ilişkili bir SPN adına sahip bir etki alanı hesabı altında çalışıyorsa ve bilgisayar Active Directory ortamındaki bir etki alanının üyesiyse Windows Kerberos güvenliğinin avantajlarından yararlanır.|  
  
## <a name="specifying-identity-at-the-service"></a>Hizmette kimlik belirtme  
 Genellikle, bir hizmetin kimliğini ayarlamanız gerekmez, çünkü bir istemci kimlik bilgisi türü seçimi, hizmet meta verilerinde sunulan kimlik türünü belirler. Hizmet kimliğini geçersiz kılma veya belirtme hakkında daha fazla bilgi için bkz. [kimlik doğrulaması için bir hizmetin kimliğini geçersiz kılma](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md).  
  
## <a name="using-the-identity-element-in-configuration"></a>\<Yapılandırmada kimlik > öğesi kullanma  
 Daha önce gösterilen `Certificate,` bağlamadaki istemci kimlik bilgisi türünü değiştirirseniz oluşturulan wsdl, kimlik değeri için aşağıdaki kodda gösterildiği gibi Base64 serileştirilmiş X. 509.440 sertifikası içerir. Bu, Windows dışındaki tüm istemci kimlik bilgisi türleri için varsayılandır.  

 Yapılandırma içindeki `<identity>` öğeyi kullanarak veya koddaki kimliği ayarlayarak, varsayılan hizmet kimliğinin değerini değiştirebilir veya kimliğin türünü değiştirebilirsiniz. Aşağıdaki yapılandırma kodu, bir etki alanı adı sistemi (DNS) kimliğini değeriyle `contoso.com`ayarlar.  

## <a name="setting-identity-programmatically"></a>Kimliği programlı olarak ayarlama  
 WCF tarafından otomatik olarak belirlediği için hizmetiniz bir kimlik belirtmek zorunda değildir. Ancak, WCF, gerekirse bir uç nokta üzerinde kimlik belirtmenize olanak tanır. Aşağıdaki kod, belirli bir DNS kimliğine sahip yeni bir hizmet uç noktası ekler.  
  
 [!code-csharp[C_Identity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_identity/cs/source.cs#5)]
 [!code-vb[C_Identity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_identity/vb/source.vb#5)]  
  
## <a name="specifying-identity-at-the-client"></a>Istemcide kimlik belirtme  
 Tasarım zamanında, istemci geliştiricisi istemci yapılandırması oluşturmak için genellikle [ServiceModel meta veri yardımcı programı aracını (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) kullanır. Oluşturulan yapılandırma dosyası (istemci tarafından kullanılmak üzere tasarlanmıştır) sunucunun kimliğini içerir. Örneğin, aşağıdaki kod, önceki örnekte gösterildiği gibi bir DNS kimliğini belirten bir hizmetten oluşturulmuştur. İstemcinin uç nokta kimliği değerinin, hizmetin ile eşleştiğini unutmayın. Bu durumda, istemci hizmetin Windows (Kerberos) kimlik bilgilerini aldığında değerin olmasını `contoso.com`bekler.  

 Windows yerine hizmet, istemci kimlik bilgileri türü olarak bir sertifika belirtiyorsa, sertifikanın DNS özelliğinin değeri `contoso.com`olması beklenir. (Veya DNS özelliği ise `null`, sertifikanın konu adı `contoso.com`olmalıdır.)  
  
#### <a name="using-a-specific-value-for-identity"></a>Kimlik için belirli bir değer kullanma  
 Aşağıdaki istemci yapılandırma dosyasında hizmetin kimliğinin belirli bir değer olması beklenildiği gösterilmektedir. Aşağıdaki örnekte, istemci iki uç nokta ile iletişim kurabilir. Birincisi bir sertifika parmak iziyle ve ikincisi bir sertifika RSA anahtarıyla tanımlanır. Diğer bir deyişle, yalnızca ortak anahtar/özel anahtar çifti içeren, ancak güvenilen bir yetkili tarafından verilmemiş bir sertifikadır.  

## <a name="identity-checking-at-run-time"></a>Çalışma zamanında kimlik denetimi  
 Tasarım zamanında, bir istemci geliştiricisi sunucunun meta verilerini kullanarak kimliğini belirler. Çalışma zamanında, kimlik denetimi, hizmette herhangi bir uç nokta çağrılmadan önce gerçekleştirilir.  
  
 Kimlik değeri meta veriler tarafından belirtilen kimlik doğrulaması türüne bağlıdır; diğer bir deyişle, hizmet için kullanılan kimlik bilgilerinin türü.  
  
 Kanal, kimlik doğrulaması için X. 509.440 sertifikaları ile ileti veya aktarım düzeyi Güvenli Yuva Katmanı (SSL) kullanarak kimlik doğrulaması yapacak şekilde yapılandırıldıysa, aşağıdaki kimlik değerleri geçerlidir:  
  
- BKZ. WCF, SSL el sıkışması sırasında sağlanmış sertifikanın, istemcideki DNS kimliğinde belirtilen değere `CommonName` eşit bir DNS veya (CN) özniteliği içerdiğinden emin olmanızı sağlar. Bu denetimlerin, sunucu sertifikasının geçerliliğini belirlemeye ek olarak yapıldığını unutmayın. Varsayılan olarak, WCF, sunucu sertifikasının güvenilen bir kök yetkili tarafından verildiğini doğrular.  
  
- Sertifika. SSL el sıkışması sırasında, WCF, uzak uç noktanın kimlik içinde belirtilen tam sertifika değerini sağladığından emin olmanızı sağlar.  
  
- Sertifika başvurusu. Sertifikayla aynı.  
  
- RSA. SSL el sıkışması sırasında, WCF, uzak uç noktanın kimlik içinde belirtilen tam RSA anahtarını sağladığından emin olmanızı sağlar.  
  
 Hizmet kimlik doğrulaması için bir Windows kimlik bilgisi ile ileti veya aktarım düzeyi SSL kullanarak kimlik doğrulaması gerçekleştiriyorsa ve kimlik bilgisini görüşür, aşağıdaki kimlik değerleri geçerlidir:  
  
- BKZ. Bu anlaşma, DNS adının denetlenebilmesi için hizmetin SPN 'sini geçirir. SPN, formundadır `host/<dns name>`.  
  
- SPN. Örneğin, `host/myservice`açık bir Service SPN döndürülür.  
  
- 'LE. Hizmet hesabının UPN 'si. UPN, formundadır `username`. @ `domain` Örneğin, hizmet bir kullanıcı hesabında çalışırken, bu `username@contoso.com`olabilir.  
  
 Kimliği programlı olarak belirtme ( <xref:System.ServiceModel.EndpointAddress.Identity%2A> özelliği kullanılarak) isteğe bağlıdır. Kimlik belirtilmemişse ve istemci kimlik bilgisi türü Windows ise, varsayılan olarak SPN, "Host/" değişmez değeri ön eki olan hizmet uç noktası adresinin konak adı bölümüne ayarlanmıştır. Kimlik belirtilmezse ve istemci kimlik bilgisi türü bir sertifikadır, varsayılan olarak olur `Certificate`. Bu hem ileti hem de aktarım düzeyi güvenlik için geçerlidir.  
  
## <a name="identity-and-custom-bindings"></a>Kimlik ve özel bağlamalar  
 Bir hizmetin kimliği kullanılan bağlama türüne bağlı olduğundan, özel bağlama oluştururken uygun bir kimliğin sunulduğundan emin olun. Örneğin, aşağıdaki kod örneğinde, sunulan kimlik güvenlik türüyle uyumlu değildir, çünkü güvenli konuşma önyükleme bağlamasının kimliği, uç noktasındaki bağlamanın kimliğiyle eşleşmez. Güvenli konuşma bağlaması DNS kimliğini ayarlar, ancak <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement> UPN veya SPN kimliğini ayarlar.  
  
 [!code-csharp[C_Identity#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_identity/cs/source.cs#8)]
 [!code-vb[C_Identity#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_identity/vb/source.vb#8)]  
  
 Özel bir bağlama için bağlama öğelerinin doğru bir şekilde nasıl yığılabilecek hakkında daha fazla bilgi için bkz. [Kullanıcı Tanımlı Bağlamalar Oluşturma](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md). İle <xref:System.ServiceModel.Channels.SecurityBindingElement>özel bir bağlama oluşturma hakkında daha fazla bilgi için bkz [. nasıl yapılır: Belirtilen kimlik doğrulama modu](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)için bir SecurityBindingElement oluşturun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Nasıl yapılır: Belirtilen kimlik doğrulama modu için bir SecurityBindingElement oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
- [Nasıl yapılır: Özel bir Istemci Kimliği Doğrulayıcısı oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md)
- [Kimlik Bilgisi Türü Seçme](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)
- [Sertifikalarla Çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [ServiceModel Meta Veri Yardımcı Programı Aracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Kullanıcı Tanımlı Bağlamalar Oluşturma](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)
- [Nasıl yapılır: Bir sertifikanın parmak Izini alma](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
