---
title: Kimlik Doğrulama ile Hizmet Kimliği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- authentication [WCF], specifying the identity of a service
ms.assetid: a4c8f52c-5b30-45c4-a545-63244aba82be
ms.openlocfilehash: def49bc4264f2cae8e17d5f00ff12ad41674da2d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54540617"
---
# <a name="service-identity-and-authentication"></a>Kimlik Doğrulama ile Hizmet Kimliği
Bir hizmetin *uç noktası kimlik*oluşturulan Web Hizmetleri Açıklama Dili (WSDL) hizmetinden bir değerdir. Herhangi bir istemciye yayılır. Bu değer, hizmet kimlik doğrulaması için kullanılır. İstemci bir uç nokta için bir iletişim başlatır ve hizmeti kendisi için istemci kimlik doğrulaması sonra istemci uç noktası kimlik değeri uç nokta kimlik doğrulama işlemi döndürdü gerçek değerle karşılaştırır. Eşleşiyorlarsa istemci beklenen hizmet uç noktası başvurduğunu sağlanmıştır. Bu olarak karşı koruma işlev *kimlik avı* bir istemcinin kötü amaçlı bir hizmeti tarafından barındırılan bir uç noktaya yönlendirilmesini engelleyerek.  
  
 Kimlik ayarı gösteren örnek bir uygulama için bkz. [hizmet kimliği örneği](../../../../docs/framework/wcf/samples/service-identity-sample.md). Uç noktaları ve uç nokta adresleri hakkında daha fazla bilgi için bkz: [adresleri](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md).  
  
> [!NOTE]
>  NT LanMan (NTLM) kimlik doğrulaması için kullandığınızda, istemci NTLM altında sunucunun kimliğini doğrulayamıyor olduğundan hizmet kimliği işaretlenmemiştir. NTLM, bilgisayarların bir Windows çalışma grubunun parçası olduğunda veya Kerberos kimlik doğrulaması desteği olmayan Windows daha eski bir sürümünü çalıştırırken kullanılır.  
  
 İstemci için bir hizmet üzerinde bir ileti göndermek için güvenli bir kanal başlattığında Windows Communication Foundation (WCF) altyapısı hizmeti kimlik doğrulaması ve hizmet kimliği uç noktasında belirtilen kimlikle eşleşmesi durumunda, yalnızca ileti gönderir istemci adres kullanır.  
  
 Kimlik işleme aşağıdaki aşamalardan oluşur:  
  
-   Tasarım zamanında istemci geliştiricisinin hizmetin kimliğini (WSDL kullanıma sunulan) uç noktanın meta verilerden belirler.  
  
-   Çalışma zamanında, istemci uygulama hizmetine herhangi bir ileti göndermeden önce hizmetin güvenlik kimlik bilgileri taleplerini denetler.  
  
 İstemcide işleme kimliği, istemci kimlik doğrulaması hizmetine benzer. İstemcinin kimlik doğrulamasından kadar güvenli bir hizmetin kod çalıştırılmaz. Benzer şekilde, istemci hangi önceden hizmet meta verilerinden bilinen üzerinde hizmet kimlik bilgilerini doğrulanmadıkça hizmete ileti tabanlı göndermez.  
  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A> Özelliği <xref:System.ServiceModel.EndpointAddress> sınıfı, istemci tarafından adlı hizmetin kimliğini temsil eder. Hizmet yayımlar <xref:System.ServiceModel.EndpointAddress.Identity%2A> meta. Bir istemci geliştiricisinin çalıştığında [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) karşı hizmet uç noktası, oluşturulan yapılandırma hizmetin değerini içeren <xref:System.ServiceModel.EndpointAddress.Identity%2A> özelliği. WCF altyapıyı (güvenlik ile yapılandırılmışsa), hizmet belirtilen kimlik sahip olduğunu doğrular.  
  
> [!IMPORTANT]
>  Meta veri, beklenen hizmet kimliğini içeriyor, bu nedenle, hizmet meta verileri güvenli araçlarla, örneğin, hizmet için bir HTTPS uç noktası oluşturarak ortaya önerilir. Daha fazla bilgi için [nasıl yapılır: Meta veri uç noktalarını güvenli](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md).  
  
## <a name="identity-types"></a>Kimlik türleri  
 Hizmet kimlikleri altı tür sağlar. İçinde bulunan bir öğeye karşılık gelen her bir kimlik türü `<identity>` yapılandırma öğesi. Kullanılan türü, senaryo ve hizmetin güvenlik gereksinimlerine bağlıdır. Aşağıdaki tabloda her bir kimlik türü açıklar.  
  
|Kimlik türü|Açıklama|Tipik bir senaryo|  
|-------------------|-----------------|----------------------|  
|Etki Alanı Adı Sistemi (DNS)|Bu öğe, X.509 sertifikaları veya Windows hesapları kullanın. Bu kimlik bilgisi bu öğesinde belirtilen değere belirtilen DNS adı ile karşılaştırır.|Bir DNS denetimi ile DNS sertifikaları kullanmanıza olanak tanır veya konu adları. Sertifika konu adı ve aynı DNS ile yeniden, kimlik denetimi hala geçerli olur. Bir sertifika yeniden, yeni bir RSA anahtarı alır ancak aynı DNS veya konu adı korur. Başka bir deyişle, istemciler kendi hizmet kimlik bilgilerini güncelleştirmek gerekmez.|  
|Sertifika. Varsayılan zaman `ClientCredentialType` sertifikayı ayarlayın.|Bu öğe, istemci ile karşılaştırılacak bir Base64 ile kodlanmış X.509 Sertifika değerini belirtir.<br /><br /> Kullanırken bu öğe ayrıca bir [!INCLUDE[infocard](../../../../includes/infocard-md.md)] hizmet kimlik doğrulaması için bir kimlik bilgisi olarak.|Bu öğe, tek bir sertifika parmak izi değerini temel kimlik doğrulaması kısıtlar. Parmak izi değerleri benzersiz olduğu için bu katı kimlik doğrulamasını etkinleştirir. Bu, bir uyarı ile birlikte gelir: Sertifika ile aynı konu adı belirtecin yeniden, ayrıca yeni bir parmak izi sahiptir. Bu nedenle, istemciler yeni parmak izini bilinen sürece hizmet doğrulayabiliyor değildir. Bir sertifikanın parmak izi bulma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Bir sertifikanın parmak izini alma](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).|  
|Sertifika başvurusu|Daha önce açıklanan sertifikası seçeneğini aynıdır. Ancak, bu öğe, bir sertifika adını belirtin ve sertifika alınacağı konum depolamak sağlar.|Daha önce açıklanan sertifika senaryosu ile aynıdır.<br /><br /> Sertifika depolama konumu değiştirebilirsiniz avantajdır.|  
|RSA|Bu öğe, istemci ile Karşılaştırılacak RSA anahtar değeri belirtir. Bu sertifika seçeneği benzer ancak sertifikanın parmak izi kullanmak yerine, sertifikanın RSA anahtarı yerine kullanılır.|RSA onay, özellikle RSA anahtarıyla dayalı tek bir sertifika kimlik doğrulaması sınırlamanıza olanak sağlar. Bu, belirli bir RSA anahtarı RSA anahtar değeri değişirse, mevcut istemciler artık çalışır hizmetini çoğaltamaz katı kimlik doğrulaması sağlar.|  
|Kullanıcı asıl adı (UPN). Varsayılan zaman `ClientCredentialType` ayarlanır ve Windows hizmet işlemi sistem hesaplarından birisini altında çalışmıyor.|Bu öğe hizmetinin altında çalışmakta olduğu UPN belirtir. Kerberos protokolü ve kimlik bölümüne bakın [kimlik doğrulaması için bir hizmetin kimliğini geçersiz kılma](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md).|Bu hizmet, belirli bir Windows kullanıcı hesabı altında çalıştığından sağlar. Kullanıcı hesabı, geçerli oturum açmış kullanıcı veya belirli bir kullanıcı hesabı altında çalışan bir hizmet olabilir.<br /><br /> Hizmeti Active Directory ortamında etki alanı hesabı altında çalışıyorsa bu ayar Windows Kerberos güvenlik yararlanır.|  
|Hizmet asıl adı (SPN). Varsayılan zaman `ClientCredentialType` ayarlanır Windows ve hizmeti için işlem bir sistem hesabı altında çalışıyor — LocalService, LocalSystem veya NetworkService.|Bu öğe hizmet hesabı ile ilişkili SPN belirtir. Kerberos protokolü ve kimlik bölümüne bakın [kimlik doğrulaması için bir hizmetin kimliğini geçersiz kılma](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md).|Bu, SPN ve SPN ile ilişkili belirli Windows hesabının hizmetinizi tanımlamak sağlar.<br /><br /> Hizmetin kullanıcı hesabı için bir makine hesabı ilişkilendirmek için Setspn.exe Aracı'nı kullanabilirsiniz.<br /><br /> Bu ayar Active Directory ortamında etki alanının bir üyesi Windows hizmet ve bilgisayar ile ilişkili bir SPN ada sahip bir etki alanı hesabı altında ya da bir sistem hesabı altında çalışıyorsa, güvenlik Kerberos yararlanır.|  
  
## <a name="specifying-identity-at-the-service"></a>Hizmet kimlik belirtme  
 Genellikle, istemci kimlik bilgisi türü seçiminde kimlik hizmeti metaveri türünü belirler. çünkü bir hizmette kimlik ayarlamak gerekmez. Hizmet kimliği belirtin veya geçersiz kılma hakkında daha fazla bilgi için bkz. [kimlik doğrulaması için bir hizmetin kimliğini geçersiz kılma](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md).  
  
## <a name="using-the-identity-element-in-configuration"></a>Kullanarak \<kimlik > yapılandırma öğesi  
 Daha önce gösterilen bağlamasında istemci kimlik bilgileri türünü değiştirirseniz `Certificate,` oluşturulan WSDL seri hale getirilmiş bir Base64 içeriyorsa aşağıdaki kodda gösterildiği gibi kimlik değeri için X.509 sertifikası. Windows dışındaki tüm istemci kimlik bilgisi türleri için varsayılan değer budur.  
  
  
  
 Varsayılan hizmet kimliği değerini değiştirin ya da kullanarak kimlik türünü değiştirme `<identity>` öğesi yapılandırma veya kod kimliği ayarlama. Bir etki alanı adı sistemi (DNS) kimlik değerine sahip aşağıdaki yapılandırma kodunu ayarlar `contoso.com`.  
  
  
  
## <a name="setting-identity-programmatically"></a>Kimlik programlı olarak ayarlama  
 WCF formu otomatik olarak belirlediğinden hizmetiniz bir kimlik açıkça belirtmek yok. Ancak, WCF, bir kimlik bir uç nokta belirtmek gerekirse sağlar. Aşağıdaki kod, belirli bir DNS kimliği ile yeni bir hizmet uç noktası ekler.  
  
 [!code-csharp[C_Identity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_identity/cs/source.cs#5)]
 [!code-vb[C_Identity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_identity/vb/source.vb#5)]  
  
## <a name="specifying-identity-at-the-client"></a>İstemci kimliğini belirtme  
 Tasarım zamanında, bir istemci geliştiricisinin genellikle kullanan [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) istemci yapılandırması oluşturmak için. Oluşturulan yapılandırma dosyası (hedeflenen istemci tarafından kullanılmak üzere), sunucunun kimliğini içerir. Örneğin, aşağıdaki kod önceki örnekte gösterildiği gibi bir DNS kimliğini belirten bir hizmetten oluşturulur. İstemci uç noktası kimlik değeri hizmet eşleşmesini unutmayın. Bu durumda, istemci hizmeti için Windows (Kerberos) kimlik bilgilerini aldığında, değerin olmasını bekler `contoso.com`.  
  
  
  
 Windows, yerine hizmeti bir sertifika istemci kimlik bilgileri türünü belirtir ve sertifikanın DNS özelliği değeri olması beklenir, `contoso.com`. (Veya DNS özelliği ise `null`, sertifikanın konu adı olmalıdır `contoso.com`.)  
  
#### <a name="using-a-specific-value-for-identity"></a>Kimlik için belirli bir değer kullanma  
 Aşağıdaki istemci yapılandırma dosyası, hizmetin kimliğini nasıl belirli bir değer olması bekleniyorsa gösterir. Aşağıdaki örnekte, istemci iki uç noktaları ile iletişim kurabilir. Birinci, ikinci bir sertifika parmak izi ile bir sertifika RSA anahtarıyla tanımlanır. Diğer bir deyişle, yalnızca bir genel anahtar/özel içeren bir sertifika anahtar çiftini ancak güvenilir bir yetkili tarafından verilmemiş.  
  
  
  
## <a name="identity-checking-at-run-time"></a>Çalışma zamanında kimlik  
 Tasarım zamanında, bir istemci geliştiricisinin sunucunun kimliği ile meta verilerini belirler. Çalışma zamanında, hizmette uç çağırmadan önce kimlik denetimi gerçekleştirilir.  
  
 Kimlik değeri meta verileri tarafından belirtilen kimlik doğrulaması türü bağlıdır; diğer bir deyişle, hizmet için kullanılan kimlik bilgileri türü.  
  
 Kanal iletisi veya aktarım düzeyinde Güvenli Yuva Katmanı (SSL) X.509 sertifikalarıyla için kimlik doğrulamasını kullanarak kimlik doğrulaması için yapılandırılmışsa, aşağıdaki kimlik değerleri geçerlidir:  
  
-   DNS. WCF sağlar SSL el sıkışması sırasında sağlanan sertifikanın DNS içerdiğini veya `CommonName` (CN) öznitelik istemcisindeki DNS kimliği belirtilen değere eşittir. Sunucu sertifikasının geçerliliğini belirlemek için bu denetimler ayrıca yapıldığını unutmayın. Varsayılan olarak, WCF, sunucu sertifikasının güvenilen kök yetkilisi tarafından verildiğini doğrular.  
  
-   Sertifika. SSL el sıkışması sırasında uzak uç nokta kimliğinde belirtilen tam sertifika değer sağlar, WCF sağlar.  
  
-   Sertifika başvurusu. Sertifika ile aynıdır.  
  
-   RSA. SSL el sıkışması sırasında uzak uç nokta kimliğinde belirtilen RSA anahtarı tam sağlar, WCF sağlar.  
  
 Hizmet, ileti veya aktarım düzeyi SSL kimlik doğrulaması için bir Windows kimlik bilgisi ile kullanarak kimliğini doğrular ve kimlik bilgisi belirleyici, aşağıdaki kimlik değerleri geçerlidir:  
  
-   DNS. DNS adı denetlenebilir böylece anlaşma, sunucunun hizmetin SPN'si geçirir. SPN biçimindedir `host/<dns name>`.  
  
-   SPN. SPN döndürülür, örneğin, bir açık hizmeti `host/myservice`.  
  
-   UPN. Hizmet hesabının UPN'si. UPN formundadır `username` @ `domain`. Örneğin, bir kullanıcı hesabı hizmet çalışırken, olabilir `username@contoso.com`.  
  
 Kimliğini programlı olarak belirtme (kullanarak <xref:System.ServiceModel.EndpointAddress.Identity%2A> özelliği) isteğe bağlıdır. Hiçbir kimlik belirtilmedi ve Windows istemci kimlik bilgisi türüdür, varsayılan bir ana bilgisayar adı ön ekine sahip hizmet uç noktası adresi parçası için ayarlanan değer ile SPN'dir "konak /" değişmez. Hiçbir kimlik belirtilmedi ve istemci kimlik bilgisi türü bir sertifika varsa varsayılan değer `Certificate`. Bu, her iki ileti ve aktarım düzeyi güvenlik için geçerlidir.  
  
## <a name="identity-and-custom-bindings"></a>Kimlik ve özel bağlamalar  
 Bir hizmetin kimliğini kullanılan bağlama türüne bağlı olduğundan, uygun bir kimliği özel bağlama oluştururken maruz kalmamasını sağlamak. Güvenli konuşma başlatma bağlaması için kimliği uç noktasında bağlamaya kimlik eşleşmediğinden Örneğin, aşağıdaki kod örneğinde gösterilen kimlik güvenlik türüyle uyumlu değil. DNS kimlik güvenli konuşma bağlama ayarlar sırada <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement> UPN veya SPN kimliğini ayarlar.  
  
 [!code-csharp[C_Identity#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_identity/cs/source.cs#8)]
 [!code-vb[C_Identity#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_identity/vb/source.vb#8)]  
  
 Yığın bağlama hakkında daha fazla bilgi için öğeler doğru özel bağlama için bkz [Creating User-Defined bağlamaları](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md). Özel bağlama ile oluşturma hakkında daha fazla bilgi için <xref:System.ServiceModel.Channels.SecurityBindingElement>, bkz: [nasıl yapılır: Belirtilen kimlik doğrulama modu için SecurityBindingElement oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Nasıl yapılır: Belirtilen kimlik doğrulama modu için SecurityBindingElement oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
- [Nasıl yapılır: Özel İstemci Kimliği Doğrulayıcı oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md)
- [Kimlik Bilgisi Türü Seçme](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)
- [Sertifikalarla Çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [ServiceModel Meta Veri Yardımcı Programı Aracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Kullanıcı Tanımlı Bağlamalar Oluşturma](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)
- [Nasıl yapılır: Bir sertifikanın parmak izini alma](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
