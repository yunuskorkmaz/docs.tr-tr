---
title: Güvenlik Özel Durumları
ms.date: 03/30/2017
ms.assetid: 76d5e5cd-e4f4-404f-9a5a-ec3522494ad8
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 057d01ba918a41df0bdf2acc30c9bb35777ebc27
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474889"
---
# <a name="security-exceptions"></a>Güvenlik Özel Durumları
Bu konu, tüm güvenlik özel durumları listeler.  
  
## <a name="exception-list"></a>Özel durum listesi  
  
|Kaynak kodu|Kaynak dizesi|  
|-------------------|---------------------|  
|AnonymousLogonsAreNotAllowed|Hizmet anonim olarak oturum açmanıza izin vermiyor.|  
|AtLeastOneContractOperationRequestRequiresProtectionLevelNotSupportedByBinding|İstek iletisi korunması gerekir. Bu, belirtilen sözleşme bir işlem tarafından gereklidir. Koruma belirtilen bağlama tarafından sağlanmalıdır.|  
|AtLeastOneContractOperationResponseRequiresProtectionLevelNotSupportedByBinding|Yanıt iletisi korunması gerekir. Bu, belirtilen sözleşme bir işlem tarafından gereklidir. Koruma belirtilen bağlama tarafından sağlanmalıdır.|  
|AtMostOnePrimarySignatureInReceiveSecurityHeader|Yalnızca bir birincil imza güvenlik üstbilgisinde izin verilir.|  
|BadContextTokenFaultReason|Güvenlik kapsamı belirtecinin süresi doldu veya geçerli değil. İleti işlenmedi.|  
|BadEncryptionState|EncryptedData veya EncryptedKey bu işlem için geçersiz bir durumda değil.|  
|BasicHttpMessageSecurityRequiresCertificate|BasicHttp bağlama BasicHttpBinding.Security.Message.ClientCredentialType BasicHttpMessageCredentialType.Certificate kimlik bilgisi türü güvenli iletiler için eşit olmalıdır. Taşıma ya da TransportWithMessageCredential güvenlik için kullanıcı adı kimlik bilgilerini seçin.|  
|BasicTokenCannotBeWrittenWithoutEncryption|Temel belirteç şifreleme olmadan yazılamaz.|  
|BindingDoesNotSupportProtectionForRst|Belirtilen sözleşme için belirtilen bağlama SecureConversation ile yapılandırılmış, ancak kimlik doğrulama modu istek/yanıt tabanlı bütünlüğü ve gizliliği anlaşması için gerekli sağlamak mümkün değil.|  
|BindingDoesNotSupportWindowsIdenityForImpersonation|Belirtilen sözleşme işlemi otomatik kimliğe bürünme için Windows kimlik gerektirir. Belirtilen sözleşme için belirtilen bağlama tarafından çağıran temsil eden bir Windows Kimliği sağlanmadı.|  
|CachedNegotiationStateQuotaReached|Belirtilen kapasitesine ulaşıldı gibi hizmet anlaşma durumunu önbelleğe alamıyor. İsteği yeniden deneyin.|  
|CacheQuotaReached|Öğe eklenemez. Belirtilen en büyük önbellek boyutu.|  
|CannotDetermineSPNBasedOnAddress|İstemci, hizmet asıl adı belirtilen hedef adres SspiNegotiation/Kerberos amacıyla kimliğini temel alarak belirleyemiyor. Hedef adres varlığı UPN kimlik olmalıdır (acmedomain gibi\\\alice) ya da SPN kimliği (örneğin, ana bilgisayar/bobs-makine).|  
|CannotFindCert|Belirtilen arama ölçütleri kullanarak X.509 sertifikası bulunamıyor: StoreName, StoreLocation, FindType, FindValue.|  
|CannotFindCertForTarget|Belirtilen arama ölçütleri kullanarak X.509 sertifikası bulunamıyor: StoreName, StoreLocation, FindType, belirtilen hedef için FindValue.|  
|CannotFindCorrelationStateForApplyingSecurity|Bağıntı durumu Yanıtlayıcı yanıtlamak için güvenlik uygulamak için bulunamıyor.|  
|CannotFindNegotiationState|Anlaşma durumu için belirtilen bağlamı bulunamıyor.|  
|CannotFindSecuritySession|Belirtilen kimliğe sahip güvenlik oturumu bulunamıyor.|  
|CannotImportProtectionLevelForContract|Bir işlem içeri aktarmak için ilke belirtilen sözleşme için bir bağlama alınamıyor. Bağlama için koruma gereksinimlerini sözleşme için aktarılmış bir bağlama ile uyumlu değildir. Bağlama yeniden yapılandırmanız gerekir.|  
|CannotImportSupportingTokensForOperationWithoutRequestAction|Güvenlik İlkesi alma başarısız oldu. Güvenlik İlkesi işlemi kapsamında belirteci gereksinimleri destek içerir. Sözleşme açıklaması bu işlemle ilişkili istek iletisi için eylem belirtmiyor.|  
|CannotIssueRstTokenType|Belirteç ya da belirtilen türü veremez.|  
|CannotObtainIssuedTokenKeySize|Verilen belirteç anahtar boyutu saptanamaz.|  
|CannotPerformImpersonationOnUsernameToken|İstemci belirteci kullanarak kimliğe bürünme mümkün değildir. Belirtilen sözleşme için belirtilen bağlama kullanıcı adı güvenlik belirteci istemci kimlik doğrulaması için kayıtlı bir üyelik sağlayıcısı kullanır. Farklı türde bir güvenlik belirteci istemcisini kullanabilirsiniz.|  
|CannotPerformS4UImpersonationOnPlatform|Yalnızca belirtilen sözleşmenin kimliğe bürünme desteklediği için belirtilen bağlama [!INCLUDE[ws2003](../../../../../includes/ws2003-md.md)] ve daha yeni Windows sürümü. Güvenli Konuşmayla SspiNegotiated kimlik doğrulaması ve bağlama etkin iptalini kullanın.|  
|CannotReadKeyIdentifier|KeyIdentifier belirtilen öğe belirtilen ad ile gelen okuyamaz.|  
|CannotReadToken|Belirtecin belirtilen ValueType ile BinarySecretSecurityToken için belirtilen ad ile belirtilen öğeden okunamıyor. Bu öğe bekleniyorsa geçerli olması için güvenlik belirteçleri adı ile kullanmak üzere yapılandırılmış olduğundan emin olun, belirtilen ad ve değer türü.|  
|CertificateUnsupportedForHttpTransportCredentialOnly|İstemci sertifikası tabanlı kimlik doğrulaması TransportCredentialOnly güvenlik modunda desteklenmiyor. Aktarım güvenlik modu seçin.|  
|ClaimTypeCannotBeEmpty|ClaimType boş bir dize olamaz.|  
|ClientCertificateNotProvided|İstemci sertifikası sağlanmadı. Sertifika ClientCredentials ya da ServiceCredentials ayarlayabilirsiniz.|  
|ClientCredentialTypeMustBeSpecifiedForMixedMode|ClientCredentialType.None TransportWithMessageCredential güvenlik modu için geçerli değil. Bir kimlik bilgisi türü belirtin veya farklı bir güvenlik modu kullanın.|  
|ConfigurationSchemaInsuffientForSecurityBindingElementInstance|Yapılandırma Şeması aşağıdaki güvenlik bağlama öğesi standart olmayan yapılandırmasını tanımlamak için yeterli değil:|  
|DerivedKeyTokenGenerationAndLengthTooHigh|Türetilen anahtarın oluşturma ve uzunluğu sonucu izin verilen en fazla uzaklığında daha büyük bir anahtar türetme uzaklığı belirtilen.|  
|DnsIdentityCheckFailedForIncomingMessage|Gelen ileti kimlik denetimi başarısız oldu. Uzak uç nokta beklenen etki alanı adı sistemi (DNS) kimliği belirtildi. Belirtilen etki alanı adı sistemi (DNS) talep uzak uç nokta sağlanır. Bu yasal uzak uç nokta ise, kanal proxy oluşturulurken EndpointAddress kimlik özelliği olarak etki alanı adı sistemi kimlik belirterek sorunu düzeltebilirsiniz.|  
|DnsIdentityCheckFailedForOutgoingMessage|Kimlik denetimi çıkmasını ileti için başarısız oldu. Belirtilen etki alanı adı sistemi kimlik uzak uç nokta beklendiğinden. Etki alanı adı sistemi (DNS) talep uzak uç nokta sağlanır. Bu yasal uzak uç nokta ise, açıkça DNS kimlik EndpointAddress kimlik özelliği olarak kanal proxy oluşturulurken belirterek sorunu düzeltebilirsiniz.|  
|DuplicateIdInMessageToBeVerified|Belirtilen kimlik doğrulama için sağlanan iki kez olan iletide oluştu.|  
|EmptyBase64Attribute|Boş bir değer gerekli base-64 öznitelik adı ve ad alanı için bulunamadı.|  
|ExportOfBindingWithAsymmetricAndTransportSecurityNotSupported|Güvenlik İlkesi verme başarısız oldu. Bağlama, hem AsymmetricSecurityBindingElement hem de güvenli aktarım bağlama öğesi içeriyor. Bu tür bir bağlama için ilke verme desteklenmez.|  
|ExportOfBindingWithSymmetricAndTransportSecurityNotSupported|Güvenlik İlkesi verme başarısız oldu. Bağlama, hem SymmetricSecurityBindingElement hem de güvenli aktarım bağlama öğesi içeriyor. Bu tür bir bağlama için ilke verme desteklenmez.|  
|ExportOfBindingWithTransportSecurityBindingElementAndNoTransportSecurityNotSupported|Güvenlik İlkesi verme başarısız oldu. Bağlama, bir TransportSecurityBindingElement ancak ITransportTokenAssertionProvider uygulayan herhangi bir aktarım bağlama öğe içeriyor. Bu tür bir bağlama için ilke verme desteklenmez. Bağlama aktarım bağlama öğesinde ITransportTokenAssertionProvider arabirimini uygulayan emin olun.|  
|FoundMultipleCerts|Belirtilen arama ölçütleri kullanarak birden çok X.509 Sertifika bulundu: StoreName, StoreLocation, FindType, FindValue. Daha fazla belirli bir bulma değeri sağlayın.|  
|FoundMultipleCertsForTarget|Belirtilen arama ölçütleri kullanarak birden çok X.509 Sertifika bulundu: StoreName, StoreLocation, FindType, belirtilen hedef için FindValue. Daha fazla belirli bir bulma değeri sağlayın.|  
|HeaderDecryptionNotSupportedInWsSecurityJan2004|SecurityVersion.WSSecurityJan2004 üstbilgi şifre desteklemez. SecurityVersion.WsSecurityXXX2005 kullanın ve yukarıdaki veya tam iletiyi şifrelemek için Aktarım güvenliği'ni kullanın.|  
|IdentityCheckFailedForIncomingMessage|Gelen ileti kimlik denetimi başarısız oldu. Hedef uç nokta için beklenen kimliği belirtildi.|  
|IdentityCheckFailedForOutgoingMessage|Giden ileti kimlik denetimi başarısız oldu. Hedef uç nokta için beklenen kimliği belirtildi.|  
|IncorrectSpnOrUpnSpecified|Güvenlik Desteği Sağlayıcısı Arabirimi (SSPI) kimlik doğrulaması başarısız oldu. Sunucu belirtilen kimliğe sahip bir hesap çalışmıyor olabilir. Sunucu hizmeti hesabı (örneğin ağ hizmeti) çalıştırıyorsa hesabın ServicePrincipalName EndpointAddress sunucusu için kimlik olarak belirtin. Sunucunun bir kullanıcı hesabında çalışıyorsa, hesabın UserPrincipalName EndpointAddress sunucusu için kimlik olarak belirtin.|  
|InvalidAttributeInSignedHeader|Belirtilen imzalı üstbilgi belirtilen öznitelik içeriyor. Beklenen özniteliği belirtildi.|  
|InvalidCloseResponseAction|Belirtilen geçersiz eylemiyle güvenlik oturumu kapat bir yanıt alındı.|  
|InvalidQName|QName geçersiz.|  
|InvalidRenewResponseAction|Bir güvenlik oturumu yenileme yanıtı belirtilen geçersiz eylemiyle alındı.|  
|InvalidSspiNegotiation|Güvenlik Desteği Sağlayıcısı Arabirimi anlaşması başarısız oldu.|  
|IssuerBindingNotPresentInTokenRequirement|Güvenlik belirteci yöneticisi önyükleme güvenliği bağlama öğesi güvenli Konuşmayla açıklayan belirteç gereksinimi belirtilmesini gerektirir. Belirteç gereksinimi gibi belirtilir.|  
|KeyLengthMustBeMultipleOfEight|Belirtilen anahtar uzunluğu simetrik anahtarlar için 8 katı değil.|  
|LsaAuthorityNotContacted|İç SSL hatası (Ayrıntılar için Win32 durum koduna bakın). Anahtar değişimi yeteneğine sahip olup olmadığını belirlemek için sunucu sertifikasının denetleyin.|  
|MaximumPolicyRedirectionsExceeded|Yinelemeli ilke alma sınırı aşıldı. Federasyon Hizmeti zincirinde döngü olup olmadığını belirlemek için denetleyin.|  
|MessagePartSpecificationMustBeImmutable|İleti bölümü belirtme ayarlamadan önce sabitlenmelidir.|  
|MissingCustomCertificateValidator|X509CertificateValidationMode.Custom CustomCertificateValidator gerektirir. CustomCertificateValidator özelliğini belirtin.|  
|MissingCustomUserNamePasswordValidator|UserNamePasswordValidationMode.Custom CustomUserNamePasswordValidator gerektirir. CustomUserNamePasswordValidator özelliğini belirtin.|  
|MissingMembershipProvider|UserNamePasswordValidationMode.MembershipProvider MembershipProvider gerektirir. MembershipProvider özelliğini belirtin.|  
|NoBinaryNegoToSend|Herhangi bir ikili anlaşma diğer tarafa gönderildi.|  
|NoEncryptionPartsSpecified|Belirtilen eyleme sahip iletiler için herhangi bir şifreleme iletisi bölümü belirtilmedi.|  
|NoKeyInfoInEncryptedItemToFindDecryptingToken|KeyInfo değeri bulmak için şifrelenen öğede bulunamadı belirteci.|  
|NonceLengthTooShort|Belirtilen nonce çok kısa. Gereken en düşük nonce uzunluğu 4 bayttır.|  
|NoOutgoingEndpointAddressAvailableForDoingIdentityCheck|Herhangi bir EndpointAddress gönderilmek üzere bir ileti kimliğini denetlemek kullanılabilir.|  
|NoOutgoingEndpointAddressAvailableForDoingIdentityCheckOnReply|Herhangi bir EndpointAddress alınan yanıt kimliğini denetlemek kullanılabilir.|  
|NoPartsOfMessageMatchedPartsToSign|Sağlanan ileti bölümü belirtimi hiçbir bölümü iletinin uymadığı için hiçbir imza oluşturulmadı.|  
|NoPrincipalSpecifiedInAuthorizationContext|Hiçbir özel kural yetkilendirme bağlamında belirtilir.|  
|NoSignatureAvailableInSecurityHeaderToDoReplayDetection|Herhangi bir imza güvenlik üstbilgisinde yeniden yürütme algılaması için nonce sağlamak için kullanılabilir.|  
|NoSignaturePartsSpecified|Hiç imza ileti bölümü belirtilen eyleme sahip iletiler için belirtildi.|  
|NoSigningTokenAvailableToDoIncomingIdentityCheck|İmzalama belirteci yok gelen kimlik denetimi yapmak kullanılabilir.|  
|NoTimestampAvailableInSecurityHeaderToDoReplayDetection|Hiçbir zaman damgası yeniden yürütme algılaması için güvenlik üstbilgisinde kullanılabilir.|  
|NoTransportTokenAssertionProvided|Güvenlik ilkesi uzmanı başarısız oldu. Belirtilen türdeki sağlanan taşıma belirteci onayı TransportBinding güvenlik ilkesi eklemek için bir taşıma belirteci onayı oluşturmadı.|  
|OnlyOneOfEncryptedKeyOrSymmetricBindingCanBeSelected|Simetrik güvenlik protokolü ya da bir simetrik belirteç sağlayıcısı ve simetrik belirteç kimlik doğrulayıcı veya asimetrik bir belirteç sağlayıcısı ile yapılandırılabilir. Her ikisi de yapılandırılamaz.|  
|OperationCannotBeDoneOnReceiverSideSecurityHeaders|Bu işlem alıcı güvenlik üstbilgilerinde yapılamaz.|  
|OperationDoesNotAllowImpersonation|Belirtilen ada ve ad sözleşmeyle ait belirtilen hizmet işlemi, kimliğe bürünme izin vermiyor.|  
|PolicyRequiresConfidentialityWithoutIntegrity|Belirtilen eylem için ileti güvenlik ilkesi tutarlılık dışında güvenilirlik gerektirir. Gizliliği bütünlüğü olmadan desteklenmiyor.|  
|PrimarySignatureIsRequiredToBeEncrypted|Birincil imza şifrelenmelidir.|  
|PropertySettingErrorOnProtocolFactory|Belirtilen güvenlik protokolü fabrikası gerekli özelliği ayarlı değil veya geçersiz bir değere sahip.|  
|ProtocolFactoryCouldNotCreateProtocol|Protokol fabrikası bir protokol oluşturamıyor.|  
|PublicKeyNotRSA|Ortak anahtar bir RSA anahtarı değil.|  
|RequiredMessagePartNotEncrypted|Belirtilen gerekli ileti bölümü şifrelenmez.|  
|RequiredMessagePartNotEncryptedNs|Belirtilen gerekli ileti bölümü şifrelenmez.|  
|RequiredMessagePartNotSigned|Belirtilen gerekli ileti bölümü imzalanmamış.|  
|RequiredMessagePartNotSignedNs|Belirtilen gerekli ileti bölümü imzalanmamış.|  
|RequiredSecurityHeaderElementNotSigned|Belirtilen kimliğe sahip belirtilen güvenlik üstbilgi öğesi imzalanması gerekir.|  
|RequiredSecurityTokenNotEncrypted|Belirtilen ' belirtilen ek moduna sahip güvenlik belirteci yeniden şifrelenir.|  
|RequiredSecurityTokenNotSigned|Belirtilen ek moduna sahip belirtilen güvenlik belirteci imzalanması gerekir.|  
|RequiredSignatureMissing|İmza güvenlik üstbilgisinde olması gerekir.|  
|RequireNonCookieMode|Belirtilen bağlama belirtilen ad ile tanımlama bilgisi güvenlik kapsamı belirteçleri vermek üzere yapılandırılır. COM + tümleştirme hizmetleri tanımlama bilgisi güvenlik kapsamı belirteçlerini desteklemez.|  
|RevertingPrivilegeFailed|Geri alma işlemi belirtilen özel durumla başarısız oldu.|  
|RSTRAuthenticatorIncorrect|RequestSecurityTokenResponse CombinedHash doğru değil.|  
|SecureConversationCancelNotAllowedFaultReason|Bağlama tarafından güvenli konuşma iptaline izin verilmiyor.|  
|SecureConversationDriverVersionDoesNotSupportSession|Yapılandırılan SecureConversation sürümü oturumları desteklemiyor. WSSecureConversationFeb2005 kullanın veya üstü.|  
|SecureConversationRequiredByReliableSession|Güvenli Konuşmayla olmadan güvenilir bir oturum kurulamıyor. Güvenli Konuşmayla etkinleştirin.|  
|SecurityAuditFailToLoadDll|Belirtilen dinamik bağlantı kitaplığı (dll) yüklenemedi.|  
|SecurityAuditNotSupportedOnChannelFactory|SecurityAuditBehavior kanal fabrikası üzerinde desteklenmiyor.|  
|SecurityAuditPlatformNotSupported|Denetim iletileri güvenlik günlüğüne yazma geçerli platformu tarafından desteklenmiyor. Denetim iletileri uygulama günlüğüne yazmanız gerekir.|  
|SecurityBindingElementCannotBeExpressedInConfig|Bir güvenlik ilkesi için uç noktaya alınmadı. Güvenlik İlkesi, bir Windows Communication Foundation yapılandırmasında gösterilemez gereksinimlerini içerir. Oluşturulan yapılandırma dosyasında gerekli SecurityBindingElement parametreleri hakkında bir yorum arayın. Doğru bağlama öğesi koduyla oluşturun. Yapılandırma dosyasında bulunan bağlama yapılandırması güvenli değil.|  
|SecurityBindingSupportsOneWayOnly|Belirtilen sözleşme için belirtilen bağlama SecurityBinding yalnızca OneWay işlemi destekler.|  
|SecurityContextDoesNotAllowImpersonation|Belirtilen eylemi olan istek iletisi UltimateReceiver rolü için SecurityContext bir Windows kimliğine eşlenmediğinden, kimliğe bürünme başlatılamıyor.|  
|SecurityListenerClosing|Kapanmakta olduğundan dinleyici yeni güvenli konuşmaları kabul etmiyor.|  
|SecurityListenerClosingFaultReason|Sunucu yeni güvenli konuşmaları şu anda kabul etmiyor kapanmakta olduğundan. Lütfen daha sonra yeniden deneyin.|  
|SecurityProtocolFactoryShouldBeSetBeforeThisOperation|Bu işlem gerçekleştirilmeden önce güvenlik protokolü fabrikası ayarlamanız gerekir.|  
|SecuritySessionAbortedFaultReason|Güvenlik oturumu sona erdirildi. Bu ileti çok uzun süre oturum alınan nedeniyle olabilir.|  
|SecuritySessionKeyIsStale|Uygulama iletilerini koruyabilmesi için oturum anahtarını yenilenmesi gerekir.|  
|SecuritySessionLimitReached|Bir güvenlik oturumu oluşturulamıyor. Daha sonra yeniden deneyin.|  
|SecuritySessionNotPending|Belirtilen kimliğe sahip hiçbir güvenlik oturumu beklemede.|  
|SecurityTokenParametersHasIncompatibleInclusionMode|Belirtilen bağlama belirtilen uyumsuz güvenlik belirteci ekleme modu olan bir güvenlik belirteci parametresiyle yapılandırılır. Bir alternatif güvenlik belirteci ekleme modu belirtin.|  
|SecurityVersionDoesNotSupportEncryptedKeyBinding|Belirtilen sözleşme için belirtilen bağlama da EncryptedKey öğelerini vermeyi eklenmemiş başvurular desteklemeyen bir uyumsuz güvenlik sürümü yapılandırıldı. Belirtilen değeri kullanır veya bağlama için güvenlik sürüm olarak daha yüksek.|  
|SecurityVersionDoesNotSupportSignatureConfirmation|Belirtilen SecurityVersion imza onayı desteklemez. Daha yeni bir SecurityVersion kullanın.|  
|SecurityVersionDoesNotSupportThumbprintX509KeyIdentifierClause|Belirtilen sözleşme için belirtilen bağlama sertifikanın parmak izi değerini kullanarak X.509 belirteçleri dış başvuruları desteklemiyor security sürüm ile yapılandırılır. Belirtilen değeri kullanır veya bağlama için güvenlik sürüm olarak daha yüksek.|  
|SenderSideSupportingTokensMustSpecifySecurityTokenParameters|Her ileti için destek belirteçleri ile güvenlik belirteci parametreleri belirtilmelidir.|  
|ServerCertificateNotProvided|Alıcı sertifikasını sağlamadı. Bu sertifika TLS protokolü tarafından gereklidir. Her iki taraf sertifikalarını erişiminiz olması gerekir.|  
|SignatureConfirmationNotSupported|Yapılandırılan SecurityVersion imza onayı desteklemez. WSSecurityXXX2005 kullanın veya üstü.|  
|SignatureConfirmationRequiresRequestReply|Protokol fabrikası imza onayı sunmak için istek/yanıt güvenlik desteklemesi gerekir.|  
|SignatureNotExpected|İmza için bu iletiyi beklenmiyor.|  
|SigningTokenHasNoKeys|Belirtilen imzalama belirteci anahtarı yok. Güvenlik belirteci şifreleme işlemlerini gerçekleştirmek için gerekli bir bağlamda kullanılır, ancak belirteç herhangi bir şifreleme anahtarı içerir. Belirteç türü şifreleme işlemlerini desteklemiyor ya da belirli belirteç örnekleri şifreleme anahtarları içermiyor. Onay, yapılandırma emin olmak için şifreleme açısından belirteç türleri (örneğin, UserNameSecurityToken) devre dışı değildir, şifreleme işlemlerini (örneğin, bir onaylama destekleme belirteci) gerektiren bir bağlamda belirtilmiş.|  
|SpnegoImpersonationLevelCannotBeSetToNone|Güvenlik Desteği Sağlayıcısı Arabirimi kimliğe bürünme düzeyi 'None' desteklemez. Kimlik, kimliğe bürünme veya temsilci düzeyini belirtin.|  
|SslClientCertMustHavePrivateKey|Belirtilen sertifika özel anahtarı olması gerekir. İşlem, özel anahtar için erişim haklarına sahip olmalıdır.|  
|SslServerCertMustDoKeyExchange|Belirtilen sertifika anahtar değişim yeteneğine sahip bir özel anahtarı olması gerekir. İşlem, özel anahtar için erişim haklarına sahip olmalıdır.|  
|StandardsManagerCannotWriteObject|Belirteci seri hale getirici, belirtilen nesne seri hale getirilemiyor.  Bu özel bir tür ise özel bir seri hale getirici sağlamanız gerekir.|  
|TimeStampHasCreationAheadOfExpiry|Oluşturulma zamanı kendi sona erme zamanı eşit veya daha büyük olduğu için güvenlik damgasının geçersiz.|  
|TimeStampHasCreationTimeInFuture|Oluşturulma zamanı gelecekte olduğu için güvenlik damgasının geçersiz. Geçerli saat belirtilir ve izin verilen saat eğriltme belirtilir.|  
|TimeStampHasExpiryTimeInPast|Süre sonu zamanı geçmişte güvenlik zaman damgası eski olduğundan. Geçerli saat belirtilir ve izin verilen saat eğriltme belirtilir.|  
|TimeStampWasCreatedTooLongAgo|Oluşturulma zamanı çok kadar geri geçmişte güvenlik zaman damgası eski olduğundan. Geçerli saati, maksimum zaman damgası yaşam süresi ve izin verilen saat eğriltme belirtilir.|  
|TokenProviderCannotGetTokensForTarget|Belirteç sağlayıcı için belirtilen hedef belirteçleri alınamıyor.|  
|TooManyIssuedSecurityTokenParameters|Federasyon güvenlik zincirinin bir bacağı birden çok IssuedSecurityTokenParameters içerir. Infocard sistemi, her Bacak için yalnızca bir IssuedSecurityTokenParameters destekler.|  
|TransportDoesNotProtectMessage|Belirtilen bağlama belirtilen sözleşme için aktarım düzeyi bütünlüğü ve gizliliği gerektiren bir kimlik doğrulama modu ile yapılandırılır. Ancak taşıma bütünlüğü ve gizliliği sağlayamaz.|  
|TrustApr2004DoesNotSupportCertainIssuedTokens|WSTrustApr2004 X.509 sertifikalarını ya da EncryptedKey öğelerini vermeyi desteklemez. WsTrustFeb2005 kullanın veya üstü.|  
|TrustDriverVersionDoesNotSupportSession|Yapılandırılan güven sürümü oturumları desteklemiyor. WSTrustFeb2005 kullanın veya üstü.|  
|UnableToCreateICryptoFromTokenForSignatureVerification|Belirtilen belirteç imza doğrulaması için bir ICrypto arabirimi oluşturamazsınız.|  
|UnableToCreateSymmetricAlgorithmFromToken|Belirtilen Simetrik algoritma belirteçten oluşturulamıyor.|  
|UnableToDeriveKeyFromKeyInfoClause|Türetme için kullanılan simetrik anahtar içermiyor belirtilen belirtecine çözümlendi belirtilen KeyInfo.|  
|UnableToFindTokenAuthenticator|Belirtilen belirteç türü için bir belirteç kimlik doğrulayıcısı bulunamıyor. Bu tür belirteçler göre geçerli güvenlik ayarları kabul edilemez.|  
|UnableToLoadCertificateIdentity|Yapılandırmada belirtilen X.509 sertifikası kimliği yüklenemiyor.|  
|UnexpectedEmptyElementExpectingClaim|Belirtilen öğe belirtilen ad boş ve geçerli bir kimlik talebi belirtmiyor.|  
|UnknownEncodingInBinarySecurityToken|Tanınmayan kodlama ikili güvenlik belirteci okunurken oluştu.|  
|UnsecuredMessageFaultReceived|Diğer taraftan korunmayan ya da yanlış güvenli hatası alındı. Hata kodu ve ayrıntı için iç FaultException bakın.|  
|UnsupportedPasswordType|Belirtilen kullanıcı adı belirteci desteklenmeyen bir parola türüne sahip.|  
|UnsupportedSecureConversationBootstrapProtectionRequirements|Güvenlik İlkesi içeri aktarılamıyor. Güvenli konuşma başlatma bağlaması koruma gereksinimleri desteklenmez. Güvenli Konuşmayla önyükleme koruma gereksinimlerini istek ve yanıt İmzalanabilir ve şifrelenebilir gerektirir.|  
|UnsupportedSecurityPolicyAssertion|Desteklenmeyen güvenlik ilkesini onaylama işlemi sırasında belirtilen güvenlik ilkesi alma algılandı.|
