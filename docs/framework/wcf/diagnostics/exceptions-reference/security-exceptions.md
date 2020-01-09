---
title: Güvenlik Özel Durumları
ms.date: 03/30/2017
ms.assetid: 76d5e5cd-e4f4-404f-9a5a-ec3522494ad8
ms.openlocfilehash: e96c317862867b9e461eb2d13dce6ede5b30cf13
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75348238"
---
# <a name="security-exceptions"></a>Güvenlik özel durumları

Bu konu, tüm güvenlik özel durumlarını listeler.

## <a name="exception-list"></a>Özel durum listesi

|Kaynak kodu|Kaynak dizesi|
|-------------------|---------------------|
|AnonymousLogonsAreNotAllowed|Hizmet, anonim olarak oturum açmaya izin vermez.|
|Attaastonecontractoperationrequestrequiresprotectionlevelnotsupportedbybinding|İstek iletisinin korunması gerekir. Bu, belirtilen sözleşmenin bir işlemi için gereklidir. Korumanın belirtilen bağlama tarafından sağlanması gerekir.|
|AtLeastOneContractOperationResponseRequiresProtectionLevelNotSupportedByBinding|Yanıt iletisinin korunması gerekir. Bu, belirtilen sözleşmenin bir işlemi için gereklidir. Korumanın belirtilen bağlama tarafından sağlanması gerekir.|
|Atmostoneprimarysignatureınreceivesecurityheader|Güvenlik üstbilgisinde yalnızca bir birincil imzaya izin verilir.|
|BadContextTokenFaultReason|Güvenlik bağlamı belirtecinin geçerlilik aşımına uğradı veya geçersiz. İleti işlenmedi.|
|BadEncryptionState|EncryptedData veya EncryptedKey, bu işlem için geçersiz bir durumda.|
|BasicHttpMessageSecurityRequiresCertificate|BasicHttp bağlaması, güvenli iletiler için BasicHttpBinding. Security. Message. ClientCredentialType 'ın BasicHttpMessageCredentialType. Certificate kimlik bilgisi türüne eşit olmasını gerektirir. Kullanıcı adı kimlik bilgileri için Transport veya TransportWithMessageCredential güvenliği ' ni seçin.|
|Basictokencannotbewrittenwithoutencryptıon|Temel belirteç şifrelenmeden yazılamaz.|
|Bindingdrnotsupportprotectionforrst|Belirtilen sözleşme için belirtilen bağlama SecureConversation ile yapılandırılmış, ancak kimlik doğrulama modu istek/yanıt tabanlı bütünlüğü ve anlaşma için gereken gizliliği sağlayamıyor.|
|Bindingınotsupportwindowsıdenityforımpersonation|Belirtilen sözleşme işlemi otomatik kimliğe bürünme için Windows kimliği gerektirir. Çağrıyı temsil eden bir Windows kimliği belirtilen sözleşme için belirtilen bağlama tarafından sağlanmadı.|
|Cachednegotiationstatequotareatiz|Belirtilen kapasiteye ulaşıldığından hizmet, anlaşma durumunu önbelleğe alamaz. İsteği yeniden deneyin.|
|Önbellekeşitlenmiş|Öğe eklenemiyor. En büyük önbellek boyutu belirtilir.|
|CannotDetermineSPNBasedOnAddress|İstemci, SspiNegotiation/Kerberos amacıyla belirtilen hedef adresteki kimliğe göre hizmet asıl adını belirleyemiyor. Hedef adres kimliği, bir UPN kimliği (acmedomain\\\gamze) veya SPN kimliği (konak/bobs-Machine gibi) olmalıdır.|
|CannotFindCert|Belirtilen arama ölçütleri kullanılarak X. 509.952 sertifikası bulunamıyor: StoreName, StoreLocation, FindType, FindValue.|
|CannotFindCertForTarget|Belirtilen hedef için belirtilen arama ölçütleri kullanılarak X. 509.952 sertifikası bulunamıyor: StoreName, StoreLocation, FindType, FindValue.|
|CannotFindCorrelationStateForApplyingSecurity|Yanıtlayanın yanıt vermesi için güvenlik uygulama bağıntı durumu bulunamıyor.|
|CannotFindNegotiationState|Belirtilen bağlam için anlaşma durumu bulunamıyor.|
|CannotFindSecuritySession|Belirtilen KIMLIĞE sahip güvenlik oturumu bulunamıyor.|
|CannotImportProtectionLevelForContract|Bir işlemi içeri aktarma ilkesi belirtilen sözleşmeye yönelik bağlamayı içeri aktaramazsınız. Bağlama için koruma gereksinimleri, anlaşma için önceden içeri aktarılmış bir bağlama ile uyumlu değildir. Bağlamayı yeniden yapılandırmanız gerekir.|
|CannotImportSupportingTokensForOperationWithoutRequestAction|Güvenlik ilkesi içeri aktarılamadı. Güvenlik ilkesi, işlem kapsamında destekleyici belirteç gereksinimlerini içerir. Sözleşme açıklaması, bu işlemle ilişkili istek iletisi için eylemi belirtmiyor.|
|Cannotısuersttokentype|Belirteç veya belirtilen tür yapılamıyor.|
|Cannotobcontainer ıssuedtokenkeysize|Verilen belirtecin anahtar boyutu belirlenemiyor.|
|CannotPerformImpersonationOnUsernameToken|İstemci belirtecini kullanarak kimliğe bürünme mümkün değildir. Belirtilen sözleşme için belirtilen bağlama, kayıtlı bir üyelik sağlayıcısıyla istemci kimlik doğrulaması için Kullanıcı adı güvenlik belirtecini kullanır. İstemci için farklı türde bir güvenlik belirteci kullanın.|
|CannotPerformS4UImpersonationOnPlatform|Belirtilen sözleşme için belirtilen bağlama yalnızca Windows Server 2003 ve Windows 'un daha yeni bir sürümünde kimliğe bürünme özelliğini destekliyor. İptal özellikli güvenli konuşma ile SspiNegotiated kimlik doğrulaması ve bağlamayı kullanın.|
|Cannotreadkeyıdentifier|Belirtilen ad alanı ile belirtilen öğeden KeyIdentifier okunamıyor.|
|CannotReadToken|Belirtilen bir ValueType ile, belirtilen öğeden, BinarySecretSecurityToken için belirtilen ad alanına belirteç okunamıyor. Bu öğenin geçerli olması bekleniyorsa, güvenliğin belirtilen ad, ad alanı ve değer türü ile belirteçleri kullanması için yapılandırıldığından emin olun.|
|CertificateUnsupportedForHttpTransportCredentialOnly|Sertifika tabanlı istemci kimlik doğrulaması, TransportCredentialOnly güvenlik modunda desteklenmez. Taşıma güvenliği modunu seçin.|
|ClaimTypeCannotBeEmpty|ClaimType boş bir dize olamaz.|
|Clientcertificatenotsaðlanan|İstemci sertifikası sağlanmadı. Sertifika ClientCredentials veya ServiceCredentials üzerinde ayarlanabilir.|
|ClientCredentialTypeMustBeSpecifiedForMixedMode|ClientCredentialType. None, TransportWithMessageCredential güvenlik modu için geçerli değil. Bir kimlik bilgisi türü belirtin veya farklı bir güvenlik modu kullanın.|
|ConfigurationSchemaInsuffientForSecurityBindingElementInstance|Yapılandırma şeması, aşağıdaki güvenlik bağlama öğesinin standart dışı yapılandırmasını anlatmak için yetersiz:|
|DerivedKeyTokenGenerationAndLengthTooHigh|Türetilmiş anahtarın belirtilen oluşturma ve uzunluğu, izin verilen en yüksek uzaklıktan büyük bir anahtar türetme uzaklığıyla sonuçlanır.|
|Dnsıdentitycheckfailedforıncomingmessage|Kimlik denetimi gelen iletide başarısız oldu. Uzak uç noktanın beklenen etki alanı adı sistemi (DNS) kimliği belirtildi. Uzak uç nokta, belirtilen etki alanı adı sistemi (DNS) talebini sağladı. Bu yasal bir uzak uç nokta ise, kanal proxy 'si oluştururken EndpointAddress öğesinin Identity özelliği olarak etki alanı adı sistem kimliğini belirterek sorunu çözebilirsiniz.|
|Dnsıdentitycheckfailedforoutgoingmessage|Kimlik denetimi, giden ileti için başarısız oldu. Uzak uç nokta, belirtilen etki alanı adı sistem kimliğine sahip olmalıdır. Uzak uç nokta, etki alanı adı sistemi (DNS) talebini sağladı. Bu yasal bir uzak uç nokta ise, kanal proxy 'si oluştururken DNS kimliğini EndpointAddress öğesinin Identity özelliği olarak açıkça belirterek sorunu çözebilirsiniz.|
|Duplicateıdınmessagetobedoğrulandı|Belirtilen KIMLIK doğrulama için sağlanan iletide iki kez oluştu.|
|EmptyBase64Attribute|Gerekli Base-64 öznitelik adı ve ad alanı için boş bir değer bulundu.|
|ExportOfBindingWithAsymmetricAndTransportSecurityNotSupported|Güvenlik ilkesi dışarı aktarılamadı. Bağlama hem bir AsymmetricSecurityBindingElement hem de güvenli bir aktarım bağlama öğesi içerir. Böyle bir bağlama için ilke dışarı aktarma desteklenmiyor.|
|ExportOfBindingWithSymmetricAndTransportSecurityNotSupported|Güvenlik ilkesi dışarı aktarılamadı. Bağlama hem SymmetricSecurityBindingElement hem de güvenli bir aktarım bağlama öğesi içerir. Böyle bir bağlama için ilke dışarı aktarma desteklenmiyor.|
|ExportOfBindingWithTransportSecurityBindingElementAndNoTransportSecurityNotSupported|Güvenlik ilkesi dışarı aktarılamadı. Bağlama bir TransportSecurityBindingElement içeriyor, ancak ITransportTokenAssertionProvider uygulayan bir aktarım bağlama öğesi yok. Böyle bir bağlama için ilke dışarı aktarma desteklenmiyor. Bağlamadaki taşıma bağlama öğesinin ITransportTokenAssertionProvider arabirimini uyguladığından emin olun.|
|Buluna bulunan Çoğulcert|Belirtilen arama ölçütleri kullanılarak birden çok X. 509.952 sertifikası bulundu: StoreName, StoreLocation, FindType, FindValue. Daha belirli bir bulma değeri sağlayın.|
|Buluna bulunan Çoğulcertsfortarget|Belirtilen hedef için belirtilen arama ölçütleri kullanılarak birden çok X. 509.440 sertifikası bulundu: StoreName, StoreLocation, FindType, FindValue. Daha belirli bir bulma değeri sağlayın.|
|HeaderDecryptionNotSupportedInWsSecurityJan2004|SecurityVersion. WSSecurityJan2004, üst bilgi şifre çözmeyi desteklemez. Tam iletiyi şifrelemek için SecurityVersion. WsSecurityXXX2005 ve üstünü kullanın veya aktarım güvenliği kullanın.|
|Identitycheckfailedforıncomingmessage|Kimlik denetimi gelen iletide başarısız oldu. Hedef uç nokta için beklenen kimlik belirtildi.|
|Identitycheckfailedforoutgoingmessage|Kimlik denetimi giden iletide başarısız oldu. Hedef uç nokta için beklenen kimlik belirtildi.|
|IncorrectSpnOrUpnSpecified|Güvenlik desteği sağlayıcısı arabirimi (SSPI) kimlik doğrulaması başarısız oldu. Sunucu belirtilen kimliğe sahip bir hesapta çalışmıyor olabilir. Sunucu bir hizmet hesabında çalışıyorsa (örneğin, ağ hizmeti), hesabın ServicePrincipalName öğesini sunucu için EndpointAddress öğesinde kimlik olarak belirtin. Sunucu bir kullanıcı hesabında çalışıyorsa, hesabın UserPrincipalName değerini sunucu için EndpointAddress öğesinde kimlik olarak belirtin.|
|Invalidattributeınsignedheader|Belirtilen imzalı üst bilgi belirtilen özniteliği içeriyor. Beklenen öznitelik belirtildi.|
|Invalidcloseresponseaction|Belirtilen geçersiz eylemle bir güvenlik oturumu kapatma yanıtı alındı.|
|Invalidqname|QName geçersiz.|
|Invalidrenewresponseaction|Belirtilen geçersiz eylemle bir güvenlik oturumu yenileme yanıtı alındı.|
|InvalidSspiNegotiation|Güvenlik desteği sağlayıcısı arabirimi anlaşması başarısız oldu.|
|IssuerBindingNotPresentInTokenRequirement|Güvenlik belirteci Yöneticisi, güvenli konuşmayı açıklayan belirteç gereksiniminde önyükleme güvenlik bağlama öğesinin belirtilmesini gerektirir. Belirteç gereksinimi aşağıdaki şekilde belirtilmiştir.|
|Keylengthmustbemultipleofsekiz|Belirtilen anahtar uzunluğu simetrik anahtarlar için 8 ' in katı değil.|
|Lsaauthoritynotgörüşülen|İç SSL hatası (Ayrıntılar için Win32 durum koduna bakın). Anahtar değişimi yeteneğine sahip olup olmadığını öğrenmek için sunucu sertifikasını kontrol edin.|
|MaximumPolicyRedirectionsExceeded|Özyinelemeli ilke getirme sınırına ulaşıldı. Federasyon Hizmeti zincirinde bir döngü olup olmadığını kontrol edin.|
|Messagepartspecificationmustbesabit|İleti bölümü belirtiminin ayarlanmadan önce sabit hale getirilmeli.|
|Missingcustomcercertificate Atevalidator|X509CertificateValidationMode. Custom, Customcercertificate Atevalidator gerektirir. Customcercertificate Atevalidator özelliğini belirtin.|
|MissingCustomUserNamePasswordValidator|UserNamePasswordValidationMode. Custom, CustomUserNamePasswordValidator gerektirir. CustomUserNamePasswordValidator özelliğini belirtin.|
|MissingMembershipProvider|UserNamePasswordValidationMode. MembershipProvider, MembershipProvider gerektirir. MembershipProvider özelliğini belirtin.|
|Nobinarynesayfaysend|Diğer tarafa hiçbir ikili anlaşma gönderilmedi.|
|Noencryptionpartsbelirtti|Belirtilen eyleme sahip iletiler için şifreleme iletisi bölümü belirtilmedi.|
|Nokeyınfoınencrypteditemtofinddecryptingtoken|Şifre çözme belirtecini bulmak için şifrelenen öğede KeyInfo değeri bulunamadı.|
|NonceLengthTooShort|Belirtilen nonce çok kısa. Gerekli en düşük nonce uzunluğu 4 bayttır.|
|Nooutgoingendpointaddressavailablefordoıngidentitycheck|Gönderilecek bir iletideki kimliği denetlemek için hiçbir giden EndpointAddress yok.|
|Nooutgoingendpointaddressavailablefordoıngidentitycheckonreply|Alınan bir yanıttaki kimliği denetlemek için hiçbir giden EndpointAddress yok.|
|NoPartsOfMessageMatchedPartsToSign|Verilen ileti bölümü belirtimiyle eşleşen iletinin bir kısmı olmadığından imza oluşturulmadı.|
|NoPrincipalSpecifiedInAuthorizationContext|Yetkilendirme bağlamında hiçbir özel asıl belirtilmedi.|
|NoSignatureAvailableInSecurityHeaderToDoReplayDetection|Yeniden yürütme algılaması için nonce sağlamak üzere güvenlik üstbilgisinde imza yok.|
|Nosignaturepartsbelirtti|Belirtilen eyleme sahip iletiler için imza iletisi bölümü belirtilmedi.|
|NoSigningTokenAvailableToDoIncomingIdentityCheck|Gelen kimlik denetimi yapmak için imzalama belirteci yok.|
|NoTimestampAvailableInSecurityHeaderToDoReplayDetection|Güvenlik üstbilgisinde yeniden yürütme algılaması yapacak zaman damgası yok.|
|NoTransportTokenAssertionProvided|Güvenlik ilkesi uzmanı başarısız oldu. Belirtilen tür için belirtilen taşıma belirteci onayı, SP: TransportBinding güvenlik ilkesi onayını dahil etmek için bir taşıma belirteci onayı oluşturmadı.|
|OnlyOneOfEncryptedKeyOrSymmetricBindingCanBeSelected|Simetrik güvenlik protokolü, simetrik bir belirteç sağlayıcısıyla, simetrik bir belirteç kimlik doğrulayıcısı veya asimetrik belirteç sağlayıcısıyla yapılandırılabilir. Her ikisiyle de yapılandırılamaz.|
|OperationCannotBeDoneOnReceiverSideSecurityHeaders|Bu işlem, alıcı güvenlik üst bilgilerinde yapılamaz.|
|OperationDoesNotAllowImpersonation|Belirtilen ad ve ad alanı ile sözleşmeye ait olan belirtilen hizmet işlemi, kimliğe bürünmeye izin vermiyor.|
|PolicyRequiresConfidentialityWithoutIntegrity|Belirtilen eylem için ileti güvenlik ilkesi, bütünlük olmadan gizliliği gerektirir. Bütünlük olmadan gizlilik desteklenmez.|
|Primarysignatureısrequiredtobeşifrelendi|Birincil imza şifrelenmelidir.|
|PropertySettingErrorOnProtocolFactory|Belirtilen güvenlik protokolü fabrikasında gerekli olan özellik ayarlı değil veya geçersiz bir değere sahip.|
|Protocolfactory, Dnotcreateprotocol|Protokol fabrikası bir protokol oluşturamıyor.|
|PublicKeyNotRSA|Ortak anahtar bir RSA anahtarı değil.|
|Requiredmessagepartnotşifrelenmiştir|Belirtilen gerekli ileti bölümü şifrelenmedi.|
|RequiredMessagePartNotEncryptedNs|Belirtilen gerekli ileti bölümü şifrelenmedi.|
|RequiredMessagePartNotSigned|Belirtilen gerekli ileti bölümü imzalanmadı.|
|RequiredMessagePartNotSignedNs|Belirtilen gerekli ileti bölümü imzalanmadı.|
|RequiredSecurityHeaderElementNotSigned|Belirtilen KIMLIĞE sahip belirtilen güvenlik üst bilgisi öğesi imzalı olmalıdır.|
|Requiredsecuritytokennotşifrelenmiştir|Belirtilen ek moduna sahip belirtilen ' güvenlik belirteci şifrelenmelidir.|
|RequiredSecurityTokenNotSigned|Belirtilen ek moduna sahip belirtilen güvenlik belirteci imzalı olmalıdır.|
|RequiredSignatureMissing yok|İmza, güvenlik üstbilgisinde olmalıdır.|
|Talep Suonzı ıemode|Belirtilen ad alanıyla belirtilen bağlama, tanımlama bilgisi güvenlik bağlamı belirteçleri verecek şekilde yapılandırılmış. COM+ Tümleştirme Hizmetleri, tanımlama bilgisi güvenlik bağlamı belirteçlerini desteklemez.|
|RevertingPrivilegeFailed|Geri alma işlemi belirtilen özel durumla başarısız oldu.|
|Rstradoğrulayıcısının Catoryanlýþ|RequestSecurityTokenResponse CombinedHash yanlış.|
|Secure, bir uyarı Notallowedfaultreason|Bağlama tarafından güvenli konuşma iptaline izin verilmiyor.|
|Securesestiondriverversionyok Notsupportsession|Yapılandırılmış SecureConversation sürümü oturumları desteklemiyor. WSSecureConversationFeb2005 veya üstünü kullanın.|
|Securesestionrequiredbyreliableoturumu|Güvenli konuşma olmadan güvenilir bir oturum kurulamıyor. Güvenli konuşmayı etkinleştirin.|
|SecurityAuditFailToLoadDll|Belirtilen dinamik bağlantı kitaplığı (dll) yüklenemedi.|
|SecurityAuditNotSupportedOnChannelFactory|SecurityAuditBehavior, kanal fabrikası üzerinde desteklenmez.|
|SecurityAuditPlatformNotSupported|Denetim iletilerinin güvenlik günlüğüne yazılması, geçerli platform tarafından desteklenmez. Denetim iletilerini uygulama günlüğüne yazmanız gerekir.|
|SecurityBindingElementCannotBeExpressedInConfig|Uç nokta için bir güvenlik ilkesi içeri aktarıldı. Güvenlik ilkesi, bir Windows Communication Foundation yapılandırmasında gösterilemeyecek gereksinimleri içerir. Oluşturulan yapılandırma dosyasında gerekli olan SecurityBindingElement parametreleri hakkında bir açıklama bulun. Kodla doğru bağlama öğesini oluşturun. Yapılandırma dosyasındaki bağlama yapılandırması güvenli değil.|
|SecurityBindingSupportsOneWayOnly|Belirtilen sözleşme için belirtilen bağlamanın SecurityBinding 'i yalnızca OneWay işlemini destekliyor.|
|SecurityContextDoesNotAllowImpersonation|Kimliğe bürünme işlemi, belirtilen eyleme sahip istek iletisinden alınan Ultıtereceiver rolü için SecurityContext bir Windows kimliğiyle eşlenmediğinden başlatılamıyor.|
|SecurityListenerClosing|Bu, kapatıldığı için yeni güvenli konuşmaları kabul etmiyor.|
|SecurityListenerClosingFaultReason|Sunucu, kapatıldığı için şu anda yeni güvenli konuşmaları kabul etmiyor. Lütfen daha sonra yeniden deneyin.|
|SecurityProtocolFactoryShouldBeSetBeforeThisOperation|Güvenlik protokolü fabrikası, bu işlem gerçekleştirilmeden önce ayarlanmalıdır.|
|SecuritySessionAbortedFaultReason|Güvenlik oturumu sonlandırıldı. Bu, oturumda çok uzun süredir hiçbir iletinin alınamadığı için olabilir.|
|SecuritySessionKeyIsStale|Uygulama iletilerinin güvenliğini sağlamak için oturum anahtarı yenilenmelidir.|
|Securitysessionlimitulaşıldı|Güvenlik oturumu oluşturulamıyor. Daha sonra yeniden deneyin.|
|SecuritySessionNotPending|Belirtilen KIMLIĞE sahip bir güvenlik oturumu beklemede değil.|
|Securitytokenparametershasincompatibleary ıonmode|Belirtilen bağlama, belirtilen uyumsuz güvenlik belirteci ekleme moduna sahip bir güvenlik belirteci parametresiyle yapılandırılmış. Alternatif bir güvenlik belirteci ekleme modu belirtin.|
|Securityversionınotsupportencryptedkeybinding|Belirtilen sözleşme için belirtilen bağlama, EncryptedKeys 'e eklenmemiş başvuruları desteklemeyen uyumsuz bir güvenlik sürümü ile yapılandırıldı. Bağlama için güvenlik sürümü olarak belirtilen değeri veya daha üstünü kullanın.|
|Securityversionyok Notsupportsignatureconfirmation|Belirtilen SecurityVersion imza onayını desteklemiyor. Daha sonraki bir SecurityVersion kullanın.|
|SecurityVersionDoesNotSupportThumbprintX509KeyIdentifierClause|Belirtilen sözleşme için belirtilen bağlama, sertifikanın parmak izi değerini kullanarak X. 509.440 belirteçlerine dış başvuruları desteklemeyen bir güvenlik sürümü ile yapılandırılmış. Bağlama için güvenlik sürümü olarak belirtilen değeri veya daha üstünü kullanın.|
|SenderSideSupportingTokensMustSpecifySecurityTokenParameters|Her ileti için destekleme belirteçleriyle birlikte güvenlik belirteci parametrelerinin belirtilmesi gerekir.|
|Servercertificatenotsaðlanan|Alıcı sertifikasını sağlamadı. Bu sertifika TLS protokolü tarafından gerektirilir. Her iki tarafın da sertifikalarına erişimi olmalıdır.|
|SignatureConfirmationNotSupported|Yapılandırılmış SecurityVersion imza onayını desteklemiyor. WSSecurityXXX2005 veya üstünü kullanın.|
|SignatureConfirmationRequiresRequestReply|Protokol fabrikası, imza onayı sunmak için Istek/yanıt güvenliğini desteklemelidir.|
|Tabeturenotexlanted|Bu ileti için bir imza beklenmiyor.|
|SigningTokenHasNoKeys|Belirtilen imzalama belirtecinin anahtarı yok. Güvenlik belirteci, şifreleme işlemleri gerçekleştirmesini gerektiren bir bağlamda kullanılır, ancak belirteç şifreleme anahtarları içermez. Belirteç türü şifreleme işlemlerini desteklemiyor ya da belirli belirteç örneği şifreleme anahtarları içermiyor. Şifreli olarak devre dışı bırakılmış belirteç türlerini (örneğin, UserNameSecurityToken) şifreleme işlemleri gerektiren bir bağlamda belirtilmemiş olduğundan emin olmak için yapılandırmanızı denetleyin (örneğin, bir onaylama destekleme belirteci).|
|SpnegoImpersonationLevelCannotBeSetToNone|Güvenlik desteği sağlayıcısı arabirimi, ' none ' kimliğe bürünme düzeyini desteklemiyor. Tanımlama, kimliğe bürünme veya temsil düzeyini belirtin.|
|SslClientCertMustHavePrivateKey|Belirtilen sertifika özel bir anahtara sahip olmalıdır. İşlem, özel anahtar için erişim haklarına sahip olmalıdır.|
|SslServerCertMustDoKeyExchange|Belirtilen sertifika, anahtar değişim yeteneğine sahip bir özel anahtara sahip olmalıdır. İşlem, özel anahtar için erişim haklarına sahip olmalıdır.|
|StandardsManagerCannotWriteObject|Belirteç seri hale getirici belirtilen nesneyi seri hale getirilemez.  Bu özel bir tür ise özel bir serileştirici sağlamanız gerekir.|
|Timestamphascreationaheadofsüre sonu|Oluşturulma zamanı sona erme zamanından daha büyük veya ona eşit olduğundan, güvenlik zaman damgası geçersiz.|
|Timestamphascreationtimeınfuture|Oluşturma süresi gelecekte olduğundan, güvenlik zaman damgası geçersiz. Geçerli saat belirtildi ve izin verilen saat sapması belirtildi.|
|Timestamphasexpıryıtimeınpast|Sona erme saati geçmişte olduğundan, güvenlik zaman damgası eskimiş. Geçerli saat belirtildi ve izin verilen saat sapması belirtildi.|
|Timestamp, Createdtoolongönce|Oluşturma saati geçmişte çok geride olduğundan güvenlik zaman damgası eskimiş. Geçerli zaman, en fazla zaman damgası ömrü ve izin verilen saat sapması belirtildi.|
|TokenProviderCannotGetTokensForTarget|Belirteç sağlayıcı belirtilen hedef için belirteçleri alamıyor.|
|Toomanyıssuedsecuritytokenparameters|Federe güvenlik zincirinin bir bacağı birden çok IssuedSecurityTokenParameters içerir. Bilgi kartı sistemi her bir baya için yalnızca bir IssuedSecurityTokenParameters destekler.|
|TransportDoesNotProtectMessage|Belirtilen sözleşme için belirtilen bağlama, aktarım düzeyi bütünlüğü ve gizliliği gerektiren bir kimlik doğrulama modu ile yapılandırılmış. Ancak aktarım, bütünlük ve gizlilik sağlayamaz.|
|TrustApr2004DoesNotSupportCertainIssuedTokens|WSTrustApr2004, X. 509.440 sertifikaları veya EncryptedKeys vermeyi desteklemez. WsTrustFeb2005 veya üstünü kullanın.|
|Trustdriverversionyok Notsupportsession|Yapılandırılan güven sürümü oturumları desteklemez. WSTrustFeb2005 veya üstünü kullanın.|
|Unabletocreateiccryptotofromtokenforsignaturedoğrulaması|İmza doğrulaması için belirtilen belirteçten bir ıcryptoınterface oluşturulamıyor.|
|UnableToCreateSymmetricAlgorithmFromToken|Belirteçten belirtilen simetrik algoritma oluşturulamıyor.|
|UnableToDeriveKeyFromKeyInfoClause|Belirtilen KeyInfo yan tümcesi, türetmede kullanılabilecek bir simetrik anahtar içermeyen belirtilen belirtece çözümlendi.|
|UnableToFindTokenAuthenticator|Belirtilen belirteç türü için bir belirteç kimlik doğrulayıcısı bulunamıyor. Bu türün belirteçleri geçerli güvenlik ayarlarına göre kabul edilemez.|
|Unabletoloadcertificateıdentity|Yapılandırmada belirtilen X. 509.952 sertifika kimliği yüklenemiyor.|
|UnexpectedEmptyElementExpectingClaim|Belirtilen ad alanındaki belirtilen öğe boş ve geçerli bir kimlik talebi belirtmiyor.|
|UnknownEncodingInBinarySecurityToken|İkili güvenlik belirteci okunurken Tanınmayan kodlama oluştu.|
|Unsecuredmessagefaultalındı|Diğer taraftan güvenli olmayan veya yanlış bir şekilde güvenli bir hata alındı. Hata kodu ve ayrıntı için iç FaultException bölümüne bakın.|
|UnsupportedPasswordType|Belirtilen Kullanıcı adı belirteci, desteklenmeyen bir parola türüne sahip.|
|Unsupportedsecurekonuşma Tionbootstrapprotectionrequirements|Güvenlik ilkesi içeri aktarılamıyor. Güvenli konuşma önyükleme bağlamasının koruma gereksinimleri desteklenmez. Güvenli konuşma önyüklemesi için koruma gereksinimleri hem isteğin hem de yanıtın imzalanmasını ve şifrelenmesini gerektirmelidir.|
|UnsupportedSecurityPolicyAssertion|Belirtilen güvenlik ilkesi içeri aktarma sırasında desteklenmeyen bir güvenlik ilkesi onayı algılandı.|
