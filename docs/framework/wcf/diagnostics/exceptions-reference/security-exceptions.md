---
title: Güvenlik Özel Durumları
ms.date: 03/30/2017
ms.assetid: 76d5e5cd-e4f4-404f-9a5a-ec3522494ad8
ms.openlocfilehash: c1eeca9111837b9833de54ecafbc981d1c2b6343
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61780867"
---
# <a name="security-exceptions"></a>Güvenlik Özel Durumları
Bu konu, tüm güvenlik özel durumları listeler.  
  
## <a name="exception-list"></a>Özel durum listesi  
  
|Kaynak kodu|Kaynak dizesi|  
|-------------------|---------------------|  
|AnonymousLogonsAreNotAllowed|Hizmet anonim olarak oturum açmanıza izin vermiyor.|  
|AtLeastOneContractOperationRequestRequiresProtectionLevelNotSupportedByBinding|İstek iletisi korunması gerekir. Bu, belirtilen sözleşmenin bir işlem tarafından gereklidir. Belirtilen bağlama tarafından koruma sağlanması gerekir.|  
|AtLeastOneContractOperationResponseRequiresProtectionLevelNotSupportedByBinding|Yanıt iletisi korunması gerekir. Bu, belirtilen sözleşmenin bir işlem tarafından gereklidir. Belirtilen bağlama tarafından koruma sağlanması gerekir.|  
|AtMostOnePrimarySignatureInReceiveSecurityHeader|Yalnızca bir birincil bir imza, bir güvenlik üstbilgisinde izin verilir.|  
|BadContextTokenFaultReason|Güvenlik bağlam belirtecinin süresi doldu veya geçerli değil. İleti işlenmedi.|  
|BadEncryptionState|EncryptedData veya EncryptedKey, bu işlem için geçersiz bir durumda olduğundan.|  
|BasicHttpMessageSecurityRequiresCertificate|BasicHttp bağlaması BasicHttpBinding.Security.Message.ClientCredentialType güvenli iletiler için BasicHttpBinding.Security.Message.ClientCredentialType öğesinin BasicHttpMessageCredentialType.Certificate kimlik bilgisi türüne eşdeğer olmasını gerektirir. UserName kimlik bilgileri için Transport ya da TransportWithMessageCredential güvenliğini seçin.|  
|BasicTokenCannotBeWrittenWithoutEncryption|Temel belirteç şifreleme olmadan yazılamaz.|  
|BindingDoesNotSupportProtectionForRst|Belirtilen sözleşme için belirtilen bağlama SecureConversation ile yapılandırılmış, ancak kimlik doğrulama modu, istek/yanıt tabanlı bütünlüğü ve gizlilik için anlaşma gerekli sağlamak mümkün değildir.|  
|BindingDoesNotSupportWindowsIdenityForImpersonation|Belirtilen sözleşme işlemi otomatik kimliğe bürünme için Windows kimlik gerektirir. Belirtilen sözleşme için belirtilen bağlama tarafından çağıran temsil eden bir Windows Kimliği sağlanmadı.|  
|CachedNegotiationStateQuotaReached|Belirtilen kapasitesini erişildiğinden anlaşma durumu önbellek hizmeti olamaz. İsteği yeniden deneyin.|  
|CacheQuotaReached|Öğe eklenemez. Belirtilen en yüksek önbellek boyutu.|  
|CannotDetermineSPNBasedOnAddress|İstemci, SspiNegotiation/Kerberos amacıyla belirtilen hedef adresini kimliğini hizmet asıl adı temel belirlenemiyor. Hedef adres varlığı, bir UPN varlığı olmalıdır (ayse gibi\\\alice) ya da SPN varlığı (konak/ebrunun-makinesi).|  
|CannotFindCert|Belirtilen arama ölçütleri kullanılarak X.509 sertifikası bulunamıyor: StoreName, StoreLocation, FindType, FindValue'i tıklatın.|  
|CannotFindCertForTarget|Belirtilen arama ölçütleri kullanılarak X.509 sertifikası bulunamıyor: FindValue belirtilen hedefi için StoreName, StoreLocation, FindType.|  
|CannotFindCorrelationStateForApplyingSecurity|Yanıtlayıcı yanıt vermek için güvenlik uygulamak için bağıntı durumu bulunamıyor.|  
|CannotFindNegotiationState|Belirtilen bağlamı anlaşması durumu bulunamıyor.|  
|CannotFindSecuritySession|Belirtilen kimliğe sahip güvenlik oturumu bulunamıyor|  
|CannotImportProtectionLevelForContract|Bir işlem içeri aktarma İlkesi, belirtilen sözleşme için bir bağlama alamıyor. Bağlamanın koruma gereksinimleri için sözleşme zaten içeri aktarılmış bir bağlama ile uyumlu değildir. Bağlamayı yeniden yapılandırmalısınız.|  
|CannotImportSupportingTokensForOperationWithoutRequestAction|Güvenlik İlkesi içeri aktarılamadı. Güvenlik İlkesi destekleme belirteci gereksinimleri işlem kapsamında içerir. Anlaşma açıklaması, bu işlemle ilişkilendirilen istek iletisi eylemini belirtmiyor.|  
|CannotIssueRstTokenType|Belirteç ya da belirtilen türü veremez.|  
|CannotObtainIssuedTokenKeySize|Verilen belirteç anahtar boyutunu belirlenemiyor.|  
|CannotPerformImpersonationOnUsernameToken|İstemci belirteci kullanarak kimliğe bürünme mümkün değildir. Belirtilen sözleşme için belirtilen bağlama kullanıcı adı güvenlik belirteci istemci kimlik doğrulaması için kayıtlı bir üyelik sağlayıcısı kullanır. Farklı türde bir güvenlik belirteci istemcisini kullanabilirsiniz.|  
|CannotPerformS4UImpersonationOnPlatform|Belirtilen sözleşme yalnızca kimliğe bürünme özelliğini destekler. belirtilen bağlama [!INCLUDE[ws2003](../../../../../includes/ws2003-md.md)] ve daha yeni Windows sürümü. SspiNegotiated kimlik doğrulaması ve bağlama ile Secure Conversation etkin iptal ile kullanın.|  
|CannotReadKeyIdentifier|Belirtilen ad alanı ile belirtilen öğesinden KeyIdentifier okunamıyor.|  
|CannotReadToken|Belirteç, belirtilen bir ValueType sahip BinarySecretSecurityToken için belirtilen ad alanı ile belirtilen öğesinden okunamıyor. Bu öğe bekleniyorsa geçerli olması için güvenlik belirteçleri adı ile kullanmak üzere yapılandırılmış olduğundan emin olun, belirtilen ad ve değer türü.|  
|CertificateUnsupportedForHttpTransportCredentialOnly|İstemci sertifika tabanlı kimlik doğrulaması, TransportCredentialOnly güvenlik modunda desteklenmiyor. Transport güvenlik modunu seçin.|  
|ClaimTypeCannotBeEmpty|ClaimType boş bir dize olamaz.|  
|ClientCertificateNotProvided|İstemci sertifikası sağlanmadı. Sertifika ClientCredentials ya da ServiceCredentials üstünde ayarlanabilir.|  
|ClientCredentialTypeMustBeSpecifiedForMixedMode|ClientCredentialType.None, TransportWithMessageCredential güvenlik modu için geçerli değil. Kimlik bilgisi türü belirtin veya farklı bir güvenlik modu kullanın.|  
|ConfigurationSchemaInsuffientForSecurityBindingElementInstance|Yapılandırma Şeması aşağıdaki güvenlik bağlama öğesinin standart dışı yapılandırmasını açıklamak için yeterli değil:|  
|DerivedKeyTokenGenerationAndLengthTooHigh|Türetilmiş anahtarın sonucu oluşturma ve uzunluğu izin verilen en büyük uzaklık bir anahtar türetme uzaklığı belirtilen.|  
|DnsIdentityCheckFailedForIncomingMessage|Kimlik denetimi gelen iletide başarısız oldu. Uzak uç noktanın beklenen etki alanı adı sistemi (DNS) kimliği belirtildi. Uzak uç nokta, belirtilen etki alanı adı sistemi (DNS) talebini sağladı. Bu yasal bir uzak uç noktaysa, kanal proxy'si oluştururken EndpointAddress Identity özelliği etki alanı adı Sistem kimliğini belirterek sorunu düzeltebilirsiniz.|  
|DnsIdentityCheckFailedForOutgoingMessage|Dışına çıkmasını ileti kimlik denetimi başarısız oldu. Uzak uç nokta belirtilen etki alanı adı sistemi kimliği olan. Uzak uç nokta, etki alanı adı sistemi (DNS) talebini sağladı. Bu yasal bir uzak uç noktaysa, açıkça DNS kimliğini EndpointAddress Identity özelliği kanal proxy'si oluştururken belirterek sorunu düzeltebilirsiniz.|  
|DuplicateIdInMessageToBeVerified|Belirtilen kimlik doğrulama için sağlanan ileti iki kez oluştu.|  
|EmptyBase64Attribute|Ad alanı ve gerekli base-64 özniteliği adı için boş bir değer bulundu.|  
|ExportOfBindingWithAsymmetricAndTransportSecurityNotSupported|Güvenlik İlkesi dışarı aktarılamadı. Bağlama, hem AsymmetricSecurityBindingElement hem de güvenli aktarım bağlama öğesi içeriyor. Böyle bir bağlamanın dışarı desteklenmiyor.|  
|ExportOfBindingWithSymmetricAndTransportSecurityNotSupported|Güvenlik İlkesi dışarı aktarılamadı. Bağlama, SymmetricSecurityBindingElement hem de güvenli aktarım bağlama öğesi içeriyor. Böyle bir bağlamanın dışarı desteklenmiyor.|  
|ExportOfBindingWithTransportSecurityBindingElementAndNoTransportSecurityNotSupported|Güvenlik İlkesi dışarı aktarılamadı. Bağlama, bir TransportSecurityBindingElement ancak Itransporttokenassertionprovider uygulayan aktarım bağlama öğesi içeriyor. Böyle bir bağlamanın dışarı desteklenmiyor. Bağlamadaki aktarım bağlama öğesinin Itransporttokenassertionprovider arabirimini uygulayan emin olun.|  
|FoundMultipleCerts|Belirtilen arama ölçütleri kullanılarak birden çok X.509 sertifikası bulundu: StoreName, StoreLocation, FindType, FindValue'i tıklatın. Daha fazla belirli bir arama değeri sağlayın.|  
|FoundMultipleCertsForTarget|Belirtilen arama ölçütleri kullanılarak birden çok X.509 sertifikası bulundu: FindValue belirtilen hedefi için StoreName, StoreLocation, FindType. Daha fazla belirli bir arama değeri sağlayın.|  
|HeaderDecryptionNotSupportedInWsSecurityJan2004|SecurityVersion.WSSecurityJan2004 üstbilgi şifre desteklemiyor. SecurityVersion.WsSecurityXXX2005 kullanın ve yukarıdaki veya tam iletiyi şifrelemek için Aktarım güvenliği kullanın.|  
|IdentityCheckFailedForIncomingMessage|Kimlik denetimi gelen iletide başarısız oldu. Hedef uç nokta için beklenen kimliği belirtildi.|  
|IdentityCheckFailedForOutgoingMessage|Kimlik denetimi giden iletide başarısız oldu. Hedef uç nokta için beklenen kimliği belirtildi.|  
|IncorrectSpnOrUpnSpecified|Güvenlik Desteği Sağlayıcısı Arabirimi (SSPI) kimlik doğrulaması başarısız oldu. Sunucu belirtilen kimliğe sahip bir hesap içinde çalışmıyor olabilir. Sunucu (örneğin ağ hizmeti) hizmet hesabı altında çalışıyorsa hesabın ServicePrincipalName EndpointAddress sunucusu için kimlik olarak belirtin. Sunucunun bir kullanıcı hesabı olarak çalışıyorsa, hesabın UserPrincipalName EndpointAddress sunucusu için kimlik olarak belirtin.|  
|InvalidAttributeInSignedHeader|Belirtilen imzalı üstbilgi belirtilen öznitelik içeriyor. Beklenen özniteliği belirtildi.|  
|InvalidCloseResponseAction|Belirtilen geçersiz eylem güvenlik oturumu kapat bir yanıt alındı.|  
|InvalidQName|QName geçersiz.|  
|InvalidRenewResponseAction|Bir güvenlik oturumu yanıt yenileme ile belirtilen geçersiz eylem alındı.|  
|InvalidSspiNegotiation|Güvenlik Desteği Sağlayıcısı Arabirimi anlaşması başarısız oldu.|  
|IssuerBindingNotPresentInTokenRequirement|Güvenlik belirteci yöneticisi, önyükleme güvenliği bağlama öğesini güvenli konuşma açıklayan belirteç gereksinimi belirtilmesini gerektirir. Belirteç gereksinimi gibi belirtilir.|  
|KeyLengthMustBeMultipleOfEight|Belirtilen anahtar uzunluğu simetrik anahtarlar için 8'in katı değil.|  
|LsaAuthorityNotContacted|İç SSL hatası (Ayrıntılar için Win32 durum koduna bakın). Sunucu sertifikasının anahtar değişimi özelliğine sahip olup olmadığını belirlemek için denetleyin.|  
|MaximumPolicyRedirectionsExceeded|Yinelemeli ilke alma sınırına ulaşıldı. Hizmet zincirinde bir döngü olup olmadığını belirlemek için bu seçeneği işaretleyin.|  
|MessagePartSpecificationMustBeImmutable|İleti bölümü belirtimi ayarlamadan önce sabit olarak yapılmalıdır.|  
|MissingCustomCertificateValidator|X509CertificateValidationMode.Custom CustomCertificateValidator gerektirir. CustomCertificateValidator özelliğini belirtin.|  
|MissingCustomUserNamePasswordValidator|UserNamePasswordValidationMode.Custom CustomUserNamePasswordValidator gerektirir. CustomUserNamePasswordValidator özelliğini belirtin.|  
|MissingMembershipProvider|UserNamePasswordValidationMode.MembershipProvider MembershipProvider gerektirir. MembershipProvider özelliğini belirtin.|  
|NoBinaryNegoToSend|Herhangi bir ikili anlaşma tarafa gönderildi.|  
|NoEncryptionPartsSpecified|Belirtilen eyleme sahip iletiler için hiçbir şifreleme ileti parçasının belirtildi.|  
|NoKeyInfoInEncryptedItemToFindDecryptingToken|KeyInfo değeri bulmak için şifrelenmiş öğesinde bulunamadı belirteç.|  
|NonceLengthTooShort|Belirtilen nonce çok kısa. Gereken en küçük nonce uzunluğu 4 bayttır.|  
|NoOutgoingEndpointAddressAvailableForDoingIdentityCheck|Herhangi bir EndpointAddress gönderilecek bir iletinin kimliğini denetlemek kullanılabilir.|  
|NoOutgoingEndpointAddressAvailableForDoingIdentityCheckOnReply|Herhangi bir EndpointAddress alınan yanıt kimliğini denetlemek kullanılabilir.|  
|NoPartsOfMessageMatchedPartsToSign|Sağlanan ileti bölümü belirtimi hiçbir bölümü iletinin uymadığı için imzasına oluşturuldu.|  
|NoPrincipalSpecifiedInAuthorizationContext|Hiçbir özel kural yetkilendirme bağlamında belirtilir.|  
|NoSignatureAvailableInSecurityHeaderToDoReplayDetection|Yeniden yürütme algılaması için nonce sağlamak için güvenlik üst bilgisindeki imzasına kullanılabilir.|  
|NoSignaturePartsSpecified|İmza ileti bölümü yok, belirtilen eylem içeren iletilere yönelik belirtildi.|  
|NoSigningTokenAvailableToDoIncomingIdentityCheck|Hiçbir imzalama belirtecinin, gelen bir kimlik denetimi yapmak kullanılabilir.|  
|NoTimestampAvailableInSecurityHeaderToDoReplayDetection|Hiçbir zaman damgası yeniden yürütme algılaması için güvenlik üstbilgisinde kullanılabilir.|  
|NoTransportTokenAssertionProvided|Güvenlik ilkesi uzmanı başarısız oldu. Belirtilen türün sağlanan aktarım belirteci onaylaması, SP: TransportBinding güvenlik ilkesi onayını kapsayan bir aktarım belirteci onayı oluşturmadınız.|  
|OnlyOneOfEncryptedKeyOrSymmetricBindingCanBeSelected|Simetrik güvenlik protokolü ya da simetrik bir belirteç sağlayıcısını ve simetrik bir belirteç kimlik doğrulayıcısı veya asimetrik bir belirteç sağlayıcısı ile yapılandırılabilir. Her ikisi de yapılandırılamaz.|  
|OperationCannotBeDoneOnReceiverSideSecurityHeaders|Alıcı güvenlik üst bilgilere bu işlem gerçekleştirilemez.|  
|OperationDoesNotAllowImpersonation|Söyleşmesi, belirtilen ad ve ad alanı ait belirtilen hizmet işlemi, kimliğe bürünme izin vermez.|  
|PolicyRequiresConfidentialityWithoutIntegrity|Belirtilen eylem için ileti güvenlik ilkesi tutarlılık dışında güvenilirlik gerektirir. Tutarlılık dışındaki güvenilirlik desteklenmiyor.|  
|PrimarySignatureIsRequiredToBeEncrypted|Birincil bir imza şifrelenmelidir.|  
|PropertySettingErrorOnProtocolFactory|Belirtilen güvenlik protokolü fabrikasında gerekli özelliği ayarlı değil veya geçersiz bir değere sahip.|  
|ProtocolFactoryCouldNotCreateProtocol|Protokol fabrikası, bir protokol oluşturamıyor.|  
|PublicKeyNotRSA|Ortak anahtarı bir RSA anahtarı değil.|  
|RequiredMessagePartNotEncrypted|Belirtilen gerekli ileti parçası şifrelenmez.|  
|RequiredMessagePartNotEncryptedNs|Belirtilen gerekli ileti parçası şifrelenmez.|  
|RequiredMessagePartNotSigned|Belirtilen gerekli ileti parçası imzalandı değil.|  
|RequiredMessagePartNotSignedNs|Belirtilen gerekli ileti parçası imzalandı değil.|  
|RequiredSecurityHeaderElementNotSigned|Belirtilen kimliğe sahip belirtilen güvenlik header öğesi oturum açmanız gerekir.|  
|RequiredSecurityTokenNotEncrypted|Belirtilen ' güvenlik belirteci belirtilen ek modu ile yeniden şifrelenir.|  
|RequiredSecurityTokenNotSigned|Belirtilen eki moduyla belirtilen güvenlik belirteci oturum açmanız gerekir.|  
|RequiredSignatureMissing|İmza güvenlik üst bilgisinde olmalıdır.|  
|RequireNonCookieMode|Belirtilen ad alanı ile belirtilen bağlama, tanımlama bilgisinin güvenlik bağlamı belirteçlerini vermek için yapılandırılır. COM + tümleştirme hizmetleri, tanımlama bilgisinin güvenlik bağlamı belirteçleri desteklemez.|  
|RevertingPrivilegeFailed|Geri alma işlemi belirtilen özel durumla başarısız oldu.|  
|RSTRAuthenticatorIncorrect|RequestSecurityTokenResponse CombinedHash doğru değil.|  
|SecureConversationCancelNotAllowedFaultReason|Güvenli konuşma iptal bağlama tarafından izin verilmiyor.|  
|SecureConversationDriverVersionDoesNotSupportSession|Yapılandırılan SecureConversation sürümü, oturumları desteklemez. WSSecureConversationFeb2005 kullanın veya üzeri.|  
|SecureConversationRequiredByReliableSession|Güvenli konuşma olmadan güvenilir bir oturum kurulamıyor. Güvenli konuşmayı etkinleştirin.|  
|SecurityAuditFailToLoadDll|Belirtilen dinamik bağlantı kitaplığı (dll) yüklenemedi.|  
|SecurityAuditNotSupportedOnChannelFactory|SecurityAuditBehavior kanal fabrikası üzerinde desteklenmiyor.|  
|SecurityAuditPlatformNotSupported|Güvenlik günlüğü denetim iletileri yazma geçerli platform tarafından desteklenmiyor. Uygulama günlüğüne denetleme iletileri yazmanız gerekir.|  
|SecurityBindingElementCannotBeExpressedInConfig|Uç nokta için bir güvenlik ilkesi içeri aktarıldı. Güvenlik İlkesi, bir Windows Communication Foundation yapılandırmasında temsil edilemeyen gereksinimler içermektedir. Oluşturulan yapılandırma dosyasında gereken SecurityBindingElement parametreleri hakkında bir açıklama arayın. Doğru bağlama öğesi, kod ile oluşturun. Yapılandırma dosyasındaki bağlama yapılandırması güvenli değil.|  
|SecurityBindingSupportsOneWayOnly|Belirtilen sözleşme için belirtilen bağlama için SecurityBinding yalnızca tek yönlü işlemi destekler.|  
|SecurityContextDoesNotAllowImpersonation|Kimliğe bürünme için bir Windows kimliği için belirtilen eylemi olan istek iletisi UltimateReceiver rolünden SecurityContext eşlenmemiş başlatılamıyor.|  
|SecurityListenerClosing|Dinleyici kapanmakta olduğundan yeni bir güvenli konuşma kabul etmiyor.|  
|SecurityListenerClosingFaultReason|Sunucu şu anda yeni bir güvenli konuşma kabul kapanmakta olduğundan. Lütfen daha sonra yeniden deneyin.|  
|SecurityProtocolFactoryShouldBeSetBeforeThisOperation|Bu işlem gerçekleştirilmeden önce güvenlik protokolü fabrikasında ayarlamanız gerekir.|  
|SecuritySessionAbortedFaultReason|Güvenlik oturumu sonlandırıldı. Oturum çok uzun hiçbir ileti alınmadı çünkü bu olabilir.|  
|SecuritySessionKeyIsStale|Uygulama iletilerini koruyabilmesi için oturum anahtarı yenilenmesi gerekir.|  
|SecuritySessionLimitReached|Bir güvenlik oturumu oluşturulamıyor. Daha sonra yeniden deneyin.|  
|SecuritySessionNotPending|Belirtilen kimliğe sahip hiçbir güvenlik oturumu beklemede.|  
|SecurityTokenParametersHasIncompatibleInclusionMode|Belirtilen bağlama, belirtilen uyumsuz güvenlik belirteci ekleme modu olan bir güvenlik belirteci parametresi ile yapılandırılır. Bir alternatif güvenlik belirteci ekleme modunu belirtin.|  
|SecurityVersionDoesNotSupportEncryptedKeyBinding|Belirtilen sözleşme için belirtilen bağlama eklenmemiş başvuruları da EncryptedKey öğelerini vermeyi desteklemiyor bir güvenlik sürümü ile yapılandırılmış. Belirtilen değeri kullanın veya daha yüksek güvenlik sürüm bağlama olarak.|  
|SecurityVersionDoesNotSupportSignatureConfirmation|Belirtilen SecurityVersion, imza onayını desteklemiyor. Bir sonraki SecurityVersion kullanın.|  
|SecurityVersionDoesNotSupportThumbprintX509KeyIdentifierClause|Belirtilen sözleşme için belirtilen bağlama, sertifikanın parmak izi değerini kullanarak X.509 belirteçleri dış başvuruları desteklemiyor bir güvenlik sürümü ile yapılandırılır. Belirtilen değeri kullanın veya daha yüksek güvenlik sürüm bağlama olarak.|  
|SenderSideSupportingTokensMustSpecifySecurityTokenParameters|Her ileti için destek belirteçleri ile güvenliği belirteç parametrelerinin belirtilmesi gerekir.|  
|ServerCertificateNotProvided|Alıcı sertifikasını sağlamadı. Bu sertifika TLS protokolünün gereklidir. Her iki taraf, sertifikalarını erişiminiz olması gerekir.|  
|SignatureConfirmationNotSupported|Yapılandırılan SecurityVersion, imza onayını desteklemiyor. WSSecurityXXX2005 kullanın veya üzeri.|  
|SignatureConfirmationRequiresRequestReply|Protokol fabrikası, imza onayını sunmak için Request/Reply güvenlik desteklemesi gerekir.|  
|SignatureNotExpected|İmza için bu iletiye beklenmiyor.|  
|SigningTokenHasNoKeys|Belirtilen imzalama belirtecinin anahtarı yok. Güvenlik belirteci şifreleme işlemleri gerçekleştirmesi için gerekli bir bağlamda kullanılır, ancak herhangi bir şifreleme anahtarı belirteç de yer alır. Belirteç türü şifreleme işlemlerini desteklemiyor olabilir ya da belirli belirteç örnekleri şifreleme anahtarları bulundurmuyor olabilir. Onay, belirteç türleri (örneğin UserNameSecurityToken) şifreleme yoluyla devre dışı emin olmak için yapılandırma değildir (örneğin, bir onaylama destekleme belirteci) şifreleme işlemleri gerektiren bir bağlamda belirtilmiş.|  
|SpnegoImpersonationLevelCannotBeSetToNone|Güvenlik Desteği Sağlayıcısı Arabirimi kimliğe bürünme düzeyi 'None' desteklemez. Kimliği, kimliğe bürünme veya temsilci düzeyini belirtin.|  
|SslClientCertMustHavePrivateKey|Belirtilen sertifika bir özel anahtara sahip olmalıdır. İşlem, özel anahtar için erişim haklarına sahip olmalıdır.|  
|SslServerCertMustDoKeyExchange|Belirtilen sertifika anahtar değişim yeteneğine sahip bir özel anahtarı olmalıdır. İşlem, özel anahtar için erişim haklarına sahip olmalıdır.|  
|StandardsManagerCannotWriteObject|Belirteç serializer özelliği, belirtilen nesne serileştirilemiyor.  Bu özel bir tür ise, özel bir serileştirici sağlamalısınız.|  
|TimeStampHasCreationAheadOfExpiry|Oluşturulma zamanı, geçerlilik sonu zamanına eşit veya daha büyük olduğundan, güvenlik zaman damgası geçersiz.|  
|TimeStampHasCreationTimeInFuture|Oluşturulma zamanı gelecekte olduğundan, güvenlik zaman damgası geçersiz. Geçerli saat belirtildi ve izin verilen saat sapması belirtilir.|  
|TimeStampHasExpiryTimeInPast|Sona erme zamanı geçmişte olduğundan, güvenlik zaman damgası eskimiş. Geçerli saat belirtildi ve izin verilen saat sapması belirtilir.|  
|TimeStampWasCreatedTooLongAgo|Oluşturulma zamanı geçmişte geride çok uzun olduğundan, güvenlik zaman damgası eskimiş. Geçerli zamanı, maksimum zaman damgası ömrü ve izin verilen saat sapması belirtilir.|  
|TokenProviderCannotGetTokensForTarget|Belirteç sağlayıcısı, belirteç için belirtilen hedef alınamıyor.|  
|TooManyIssuedSecurityTokenParameters|Birleşik güvenliği zincirinin bir oluşturan birden çok IssuedSecurityTokenParameters içerir. Infocard sistemi, her oluşturan için yalnızca bir IssuedSecurityTokenParameters destekler.|  
|TransportDoesNotProtectMessage|Belirtilen sözleşme için belirtilen bağlama aktarım düzeyi bütünlüğü ve gizliliği gerektiren bir kimlik doğrulama modu ile yapılandırılır. Ancak taşıma bütünlüğü ve gizliliği sağlayamaz.|  
|TrustApr2004DoesNotSupportCertainIssuedTokens|WSTrustApr2004 X.509 sertifikalarıyla ya da EncryptedKey öğelerini vermeyi desteklemez. WsTrustFeb2005 kullanın veya üzeri.|  
|TrustDriverVersionDoesNotSupportSession|Yapılandırılan Trust sürümü, oturumları desteklemez. WSTrustFeb2005 kullanın veya üzeri.|  
|UnableToCreateICryptoFromTokenForSignatureVerification|Belirtilen belirteç imza doğrulaması için bir ICrypto arabirimi oluşturamazsınız.|  
|UnableToCreateSymmetricAlgorithmFromToken|Belirtilen Simetrik algoritma belirteçten oluşturulamıyor.|  
|UnableToDeriveKeyFromKeyInfoClause|Türetme için kullanılan simetrik anahtar içermiyor belirtilen belirteç çözümlendi belirtilen KeyInfo.|  
|UnableToFindTokenAuthenticator|Belirtilen belirteç türü için bir belirteç kimlik doğrulayıcısı bulunamıyor. Bu tür belirteçler göre geçerli güvenlik ayarlarını kabul edilemez.|  
|UnableToLoadCertificateIdentity|Yapılandırmada belirtilen X.509 sertifika kimlik yüklenemiyor.|  
|UnexpectedEmptyElementExpectingClaim|Belirtilen öğe belirtilen ad alanından boş ve geçerli bir kimlik talebi belirtmiyor.|  
|UnknownEncodingInBinarySecurityToken|İkili güvenlik belirteci okunurken tanınmayan kodlama oluştu.|  
|UnsecuredMessageFaultReceived|Diğer taraftan, güvenli olmayan veya yanlış güvenli bir hata alındı. İç FaultException hata kodu ve ayrıntı için bkz.|  
|UnsupportedPasswordType|Belirtilen kullanıcı adı belirteci, desteklenmeyen bir parola türüne sahip.|  
|UnsupportedSecureConversationBootstrapProtectionRequirements|Güvenlik İlkesi içeri aktarılamıyor. Güvenli konuşma başlatma bağlaması koruma gereksinimleri desteklenmiyor. Güvenli konuşma başlatma bağlaması koruma gereksinimleri, hem isteğin hem de yanıtın imzalanmış ve şifrelenmiş olmasını gerektirir.|  
|UnsupportedSecurityPolicyAssertion|Belirtilen güvenlik ilkesi içeri aktarma sırasında bir desteklenmeyen güvenlik ilkesi eklemesi algılandı.|
