---
title: IdentityModel Özel Durumları
ms.date: 03/30/2017
ms.assetid: 4ef34497-8ff5-4621-b773-7731cc721231
ms.openlocfilehash: ee0b5537a415e1ea53c653ae8e8485e94cc713fd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474876"
---
# <a name="identitymodel-exceptions"></a>IdentityModel Özel Durumları
Bu konuda IdentityModel tarafından oluşturulan tüm özel durumlar listelenir.  
  
## <a name="exception-list"></a>Özel durum listesi  
  
|Kaynak kodu|Geçerli dize|  
|-------------------|--------------------|  
|ValueMustBeOf2Types|Bu bağımsız değişkenin değeri bu iki türlerinden biri olması gerekir.|  
|SAMLSubjectNameIdentifierRequiresNameValue|Bir SamlNameIdentifier için belirtilen 'Name' null veya uzunluğu 0 olamaz.|  
|TraceCodeIssuanceTokenProviderEndSecurityNegotiation|IssuanceTokenProvider güvenlik anlaşması tamamlandı.|  
|TraceCodeSecurityNewServerSessionKeyIssued|Yeni güvenlik oturumu anahtarı sunucu tarafından yayınlandı.|  
|SAMLAttributeMissingNameAttributeOnRead|Okunan SamlAttribute için 'Name' eksik veya 0 uzunluğu.|  
|UnknownICryptoType|ICrypto uygulaması desteklenmiyor.|  
|TraceCodeSecurityTokenProviderClosed|Güvenlik belirteci sağlayıcısı kapatıldı.|  
|SAMLUnableToLoadAdvice|Yüklenemedi \<saml:advice > öğesi.|  
|SAMLAuthenticationStatementMissingAuthenticationMethodOnRead|Bir SamlAuthenticationStatement ya da uzunluk 0 okunan 'AuthenticationMethod' özniteliği.|  
|UnsupportedTransformAlgorithm|Desteklenmeyen dönüştürme veya Standartlaştırma algoritması.|  
|SAMLAudienceRestrictionShouldHaveOneAudience|Bir SamlAudienceRestrictionCondition en az bir izleyici (URI) içermelidir.|  
|SAMLEvidenceShouldHaveOneAssertion|SamlEvidence en az bir SamlAssertion kimliği veya reference başvurmalıdır.|  
|SAMLAudienceRestrictionInvalidAudienceValueOnRead|Okunan SamlAudienceRestrictionCondition 'İzleyici' öğesinde bir değer eksik.|  
|X509ChainBuildFail|Belirli X.509 Sertifika zinciri oluşturma başarısız oldu. Kullanılan sertifikanın doğrulanamıyor bir güven zinciri var. Sertifikayı değiştirin ya da certificateValidationMode değerini değiştirin.|  
|XDCannotFindValueInDictionaryString|Belirli bir değerin kimliği sözlük dizesinde bulunamadı.|  
|TraceCodeImportSecurityChannelBindingEntry|Güvenlik ImportChannelBinding başlatılıyor.|  
|PrivateKeyExchangeNotSupported|Özel anahtarı KeySpec öğesinin exchange desteklemez.|  
|TokenProviderUnableToGetToken|Özel Belirteç sağlayıcı güvenlik belirteci sağlayamadı.|  
|SAMLEntityCannotBeNullOrEmpty|Belirli bir SamlAssertion varlık null veya boş olamaz.|  
|SAMLAssertionRequireOneStatement|SamlAssertion en az bir ifade gerektirir. Oluşturmakta olduğunuz SamlAssertion en az bir SamlStatement eklediğinizden emin olun.|  
|AESInvalidInputBlockSize|Giriş boyutu belirli baytın katlarından biri olması gerekir.|  
|AESCryptAcquireContextFailed|CSP bağlamı alınamadı.|  
|SAMLAssertionRequireOneStatementOnRead|Okunan SamlAssertion herhangi SamlStatement içermiyordu. SamlAssertion en az bir SamlStatement içermesi gerekir.|  
|TraceCodeSecuritySessionClosedFaultReceived|İstemci güvenlik oturumu sunucudan bir oturum kapalı hatası aldı.|  
|TraceCodeIssuanceTokenProviderRedirectApplied|IssuanceTokenProvider bir yeniden yönlendirme üstbilgisi uygulanır.|  
|TraceCodeSecuritySessionClosedFaultSendFailure|Bir güvenlik oturumu gönderme hatası istemciye kapatıldığında bir hata oluştu.|  
|ValueMustBeZero|Bu bağımsız değişkenin değeri 0 olmalıdır.|  
|SAMLUnableToResolveSignatureKey|SecurityKeyIdentifier SamlAssertion imzada bulunan çözümlenemiyor. Belirli vericisi SamlAssertion imzası doğrulanamıyor.|  
|X509IsNotInTrustedStore|Belirli bir X.509 Sertifika güvenilir kişiler deposunda değil.|  
|SAMLElementNotRecognized|Belirli öğesi desteklenmiyor.|  
|SAMLAuthorizationDecisionStatementMissingResourceAttributeOnRead|'Resource' özniteliği okunan özniteliği eksik ya da 0 uzunluğunda.|  
|SamlTokenMissingSignature|SamlAssertion imzalı değil. SamlAssertions SigningCredentials ayarlayarak imzalanabilir.|  
|ExpectedElementMissing|Belirli bir ad alanı ile beklenen öğesi eksik.|  
|NoKeyIdentifierClauseFound|Belirli türdeki hiçbir yan tümcesi içinde SecurityKeyIdentifier bulundu.|  
|MissingPrivateKey|X.509 sertifikasının özel anahtarı yok.|  
|UnexpectedEOFFromReader|Beklenmeyen EOF XML okuyucudan.|  
|UnsupportedKeyDerivationAlgorithm|Özel anahtar elde etme algoritması desteklenmiyor.|  
|TokenDoesNotSupportKeyIdentifierClauseCreation|Özel belirteç özel anahtarı tanımlayıcısı yan tümcesi oluşturmayı desteklemiyor.|  
|LastMessageNumberExceeded|Sıra numarası protokolü ihlal algılandı.|  
|SymmetricKeyLengthTooShort|Belirtilen simetrik anahtar uzunluğu çok kısa.|  
|SAMLAuthorityBindingMissingAuthorityKindOnRead|Bir 'AuthorityKind' saptandı okundu SamlAuthorityBinding olması, eksik veya 0 uzunluğu.  Bu duruma izin verilmez.|  
|XmlTokenBufferIsEmpty|XmlTokenBuffer boştur.|  
|InvalidXmlQualifiedName|Bir Xml tam adı bekleniyordu, ancak geçersiz bir ad bulunamadı.|  
|SAMLAuthorityKindMissingName|SamlAuthorityBinding 'AuthorityKind' temsil eden XmlQualifiedName null ya da 0 uzunluğunda olamaz.|  
|AESCryptEncryptFailed|Belirli verileri şifrelemek başarısız oldu.|  
|AuthorizationContextCreated|Özel kimliği ile kimlik doğrulama bağlamını oluşturulur.|  
|SamlSerializerUnableToReadSecurityKeyIdentifier|SamlSerializer SecurityKeyIdentifier okuma özellikli bir SecurityTokenSerializer içermiyor. Özel bir SecurityKeyIdentifier kullanıyorsanız, özel bir SecurityTokenSerializer sağlamanız gerekir.|  
|TraceCodeIssuanceTokenProviderServiceTokenCacheFull|IssuanceTokenProvider hizmet belirteç önbelleğini azalır.|  
|TraceCodeSecurityTokenProviderOpened|Güvenlik belirteci sağlayıcısı açıldı.|  
|PublicKeyNotRSA|Ortak anahtar bir RSA anahtarı değil.|  
|InvalidReaderState|Özel durumu için sağlanan giriş okuyucu geçerli değil.|  
|UnableToResolveReferenceUriForSignature|Özet işlem için özel URI imzada çözümlenemiyor.|  
|EmptyBase64Attribute|Boş bir değer gerekli base64 öznitelik adı ve ad alanı için bulunamadı.|  
|SAMLSubjectRequiresConfirmationMethodWhenConfirmationDataOrKeyInfoIsSpecified|Onay verileri veya KeyInfo belirtildiğinde SAML SubjectConfirmation onay yöntemi gerektirir.|  
|SAMLAudienceRestrictionShouldHaveOneAudienceOnRead|Okunan SamlAudienceRestrictionCondition en az bir 'İzleyici' değeri içermelidir. Hiçbiri bulunamadı.|  
|TokenProviderUnableToRenewToken|Özel Belirteç sağlayıcı güvenlik belirtecini yenileyemedi.|  
|AESIVLengthNotSupported|Belirli BITS IV desteklenmiyor. Yalnızca 128 bit IV desteklenir.|  
|SAMLAuthorityBindingMissingAuthorityKind|Bir SamlAuthorityBinding 'AuthorityKind' içermelidir null değil.|  
|TraceCodeSecuritySessionDemuxFailure|Gelen ileti var olan bir güvenlik oturumunun parçası değil.|  
|TokenRenewalNotSupported|Özel Belirteç sağlayıcı belirteç yenilemeyi desteklemez.|  
|AtLeastOneReferenceRequired|En az bir başvuru imza gereklidir.|  
|SAMLSignatureAlreadyRead|İmza zaten SAML onayı okuyun.|  
|AlgorithmAndPrivateKeyMisMatch|Belirtilen algoritma ve özel anahtar eşleşmiyor.|  
|EmptyTransformChainNotSupported|Boş dönüştürme zinciri desteklenmez.|  
|SspiWrapperEncryptDecryptAssert1|SSPIWrapper::EncryptDecryptHelper&#124;' uzaklığı ' aralık dışında.|  
|SspiWrapperEncryptDecryptAssert2|SSPIWrapper::EncryptDecryptHelper&#124;' boyutudur ' aralık dışında. SecurityTokenManagerCannotCreateAuthenticatorForRequirement = güvenlik belirteci yöneticisi, bir belirteç kimlik doğrulayıcısı belirli gereksinimi oluşturamıyor.|  
|UnableToCreateKeyedHashAlgorithm|Belirli imza algoritması için belirli değerinden bir KeyedHashAlgorithm oluşturulamıyor.|  
|SAMLUnableToLoadAssertion|\<Saml:assertion > öğesi yüklenemedi.|  
|X509FindValueMismatchMulti|Belirli X509FindType 2 değerlerden biri için değişken findValue türü gerektirir. Bağımsız değişken findValue başka bir türde değil.|  
|TraceCodeSecurityIdentityDeterminationSuccess|Kimlik için bir EndpointAddress belirlendi.|  
|UndefinedUseOfPrefixAtElement|Konumundaki öğe kullanılan belirli ön tanımlı ad alanı yok.|  
|TraceCodeSecuritySessionResponderOperationFailure|Güvenlik oturumu işlemi sunucuda başarısız oldu.|  
|CannotFindCert|Arama ölçütleri kullanarak X.509 sertifikası bulunamıyor: StoreName, StoreLocation, FindType, FindValue.|  
|X509InvalidUsageTime|Belirli bir X.509 sertifikası kullanım saat geçersiz. Kullanım süresi nın gerekli NotBefore ve NotAfter saatini arasında kalan değil.|  
|TraceCodeSecurityIdentityDeterminationFailure|Kimlik için bir EndpointAddress belirlenemiyor.|  
|AsyncObjectAlreadyEnded|End yöntemi bu zaman uyumsuz sonuç nesnesinde zaten çağrıldı.|  
|ExternalDictionaryDoesNotContainAllRequiredStrings|Dış sözlük tüm gerekli dizeleri tanımlarında içermiyor. Spesifik dize uzak sözlükte kullanılamıyor.|  
|TraceCodeSecuritySessionKeyRenewalFaultReceived|İstemci güvenlik oturumu sunucudan bir anahtar yenileme hatası aldı.|  
|SAMLActionNameRequired|SamlAction temsil eden dize uzunluğu 0 olamaz.|  
|SignatureVerificationFailed|İmza doğrulaması başarısız oldu.|  
|TraceCodeSecurityContextTokenCacheFull|SecurityContextSecurityToken önbelleği dolu.|  
|SAMLAssertionMissingMajorVersionAttributeOnRead|Okunan SamlAssertion MajorVersion eksik veya 0 uzunluğu.|  
|SamlAttributeClaimRightShouldBePossessProperty|Bu SamlAttribute Oluşturucu talep hakkı değerinin isteğinin System.IdentityModel.Claims.Rights.PossessProperty sahip olmasını gerektirir.|  
|AuthorizationPolicyEvaluated|Belirli kimlikli ilke değerlendirilir.|  
|SAMLUnableToLoadCondtions|\<Saml:conditions > öğesi yüklenemedi.|  
|AESKeyLengthNotSupported|Belirli bit anahtar desteklenmiyor. Yalnızca 128, 192 ve 256 bit anahtar desteklenir.|  
|UserNameCannotBeEmpty|Kullanıcı adı boş olamaz.|  
|AlgorithmAndPublicKeyMisMatch|Belirtilen algoritma ve ortak anahtar eşleşmiyor.|  
|SAMLUnableToLoadCondtion|\<Saml:conditions > öğesi yüklenemedi.|  
|SamlAssertionMissingSigningCredentials|SigningCredentials SamlAssertion üstünde ayarlanmamış. SamlAssertions imzalı, Lütfen geçerli bir SigningCredentials devam etmek için SamlAssertion ayarlayın.|  
|SspiPayloadNotEncrypted|İkili veriler SSPI güvenlik bağlamı ile şifrelenmedi.|  
|SAMLAuthorizationDecisionShouldHaveOneActionOnRead|Okunan özniteliği herhangi SamlAction içermiyor.|  
|TraceCodeSecurityBindingSecureOutgoingMessageFailure|Güvenlik protokolü giden iletiyi koruyamazsınız.|  
|UndefinedUseOfPrefixAtAttribute|Belirli özniteliğinde kullanılan belirli ön tanımlı ad alanı yok.|  
|NoInputIsSetForCanonicalization|Herhangi bir giriş Kurallaştırılan çıktı yazmak için ayarlanır.|  
|TraceCodeSecurityPendingServerSessionAdded|Bekleyen bir güvenlik oturumu sunucuya eklenir.|  
|AsyncCallbackException|Bir AsyncCallback özel durum oluşturdu.|  
|PrivateKeyNotRSA|Özel anahtar bir RSA anahtarı değil.|  
|TraceCodeSecurityClientSessionKeyRenewed|İstemci güvenlik oturumu oturum anahtarını yeniledi.|  
|SAMLAuthorizationDecisionStatementMissingDecisionAttributeOnRead|'Karar' okunan özniteliği eksik ya da 0 uzunluğunda.|  
|SAMLAttributeNameAttributeRequired|SamlAttribute için belirtilen 'Name' null veya uzunluğu 0 olamaz.|  
|SamlSerializerRequiresExternalSerializers|SamlSerializer belirtecinde SecurityKeyIdentifier serileştirmek bir SecurityTokenSerializer gerektirir.|  
|UnableToResolveKeyReference|Belirteç çözümleyicisi belirli güvenlik anahtarı başvurusunu çözümleyemiyor.|  
|UnsupportedKeyWrapAlgorithm|Özel anahtar sarma algoritması desteklenmiyor.|  
|SAMLAssertionMissingIssuerAttributeOnRead|Okunan SamlAssertion 'vericisi' eksik veya 0 uzunluğu.|  
|TraceCodeIssuanceTokenProviderUsingCachedToken|IssuanceTokenProvider önbelleğe alınan hizmet belirteci kullanılır.|  
|AESCryptGetKeyParamFailed|Özel anahtar parametre alınamadı.|  
|InvalidNamespaceForEmptyPrefix|Ad alanı boş önek için geçersiz.|  
|AESCipherModeNotSupported|Özel şifreleme modu desteklenmiyor. Yalnızca CBC desteklenir.|  
|ArgumentCannotBeEmptyString|Bağımsız değişkeni boş olmayan bir dize olmalıdır.|  
|SAMLAssertionMissingMinorVersionAttributeOnRead|Okunan SamlAssertion MinorVersion eksik veya 0 uzunluğu.|  
|SpecifiedStringNotAvailableInDictionary|Belirtilen dize geçerli sözlükte bir giriş değil.|  
|KerberosApReqInvalidOrOutOfMemory|AP-REQ geçersiz veya sistem yeterli belleğe sahip değil.|  
|FailLogonUser|LogonUser belirtilen kullanıcı için başarısız oldu. Kullanıcının geçerli bir Windows hesabı olduğundan emin olun.|  
|ValueMustBeNonNegative|Bu bağımsız değişkenin değeri negatif olmalıdır.|  
|X509ValidationFail|Belirtilen X.509 sertifika doğrulaması başarısız oldu.|  
|TraceCodeSecuritySessionRequestorOperationSuccess|Güvenlik oturumu işlemi istemcide başarıyla tamamlandı.|  
|SAMLActionNameRequiredOnRead|SamlAction için okunan dizesi eksik veya 0 uzunluğu.|  
|KerberosMultilegsNotSupported|Kimlik UPN belirtilir. Bir kullanıcı hesabı altında çalışan bir hizmete kimlik doğrulaması, Kerberos çok bacak desteklenmeyen olduğu gerektirir.|  
|SAMLAssertionIdRequired|SamlAssertion için 'onaylama 'kimliği null veya boş olamaz.|  
|InvalidOperationForWriterState|Belirtilen işlem belirtilen XmlWriter durumu geçersiz.|  
|CannotValidateSecurityTokenType|Belirtilen güvenlik belirteci kimlik doğrulayıcı belirtilen türde bir belirteç doğrulanamıyor.|  
|X509FindValueMismatch|Belirtilen X509FindType belirtilen değeri olması için bağımsız değişken findValue türü gerektirir. Bağımsız değişken findValue başka bir türde değil.|  
|TraceCodeSecurityClientSessionCloseSent|İletiyi Kapat istemci güvenlik oturumu tarafından gönderildi.|  
|SuiteDoesNotAcceptAlgorithm|Belirtilen algoritma belirtilen işlem için belirtilen algoritma paketi tarafından kabul edilmedi|  
|TraceCodeSecuritySessionRequestorOperationFailure|İstemci güvenlik oturumu işlemi başarısız oldu.|  
|SAMLUnableToLoadStatement|SamlStatement yüklenemedi.|  
|InnerReaderMustBeAtElement|İç okuyucu konumundaki öğe olmalıdır.|  
|UnableToCreateTokenReference|Bir güvenlik belirteci başvurusu oluşturulamıyor.|  
|TraceCodeSecurityBindingIncomingMessageVerified|Güvenlik protokolü gelen iletiyi doğruladı.|  
|ObjectIsReadOnly|Nesne salt okunurdur.|  
|TraceCodeSecurityClientSessionPreviousKeyDiscarded|İstemci güvenlik oturumu önceki oturum anahtarı atıldı.|  
|SAMLTokenTimeInvalid|SamlToken olan değil zaman geçerli. Belirteç dışında etkili ve sona erme saati geçerli saattir.|  
|TraceCodeSecurityIdentityVerificationSuccess|Kimlik doğrulama başarılı oldu.|  
|SigningTokenHasNoKeys|Belirtilen imzalama belirteci anahtarı yok.|  
|TraceCodeSecurityIdentityVerificationFailure|Kimlik doğrulaması başarısız oldu.|  
|AESCryptImportKeyFailed|Anahtar malzemesi alma başarısız oldu.|  
|FailInitializeSecurityContext|InitializeSecurityContent başarısız oldu. Hizmet asıl adının doğru olduğundan emin olun.|  
|TraceCodeStreamSecurityUpgradeAccepted|Akış güvenlik yükseltmesi başarıyla kabul edildi.|  
|SAMLAuthorityBindingRequiresLocation|SamlAuthorityBinding üstünde belirtilen 'Konum' özniteliği null ya da 0 uzunluğunda olamaz.|  
|PublicKeyNotDSA|Ortak anahtar bir DSA anahtarı değil.|  
|ImpersonationLevelNotSupported|Kerberos kullanarak kimlik doğrulama modları belirtilen kimliğe bürünme düzeyini desteklemez. Geçerli bir kimlik veya kimliğe bürünme düzeyini belirtin.|  
|RequiredTargetNotSigned|Belirtilen kimliğe sahip öğe imzalanması gerekiyor, ancak değildi.|  
|SAMLAuthenticationStatementMissingAuthenticationInstanceOnRead|Bir SamlAuthenticationStatement ya da uzunluk 0 okunan 'AuthenticationInstant' özniteliği.|  
|SAMLEvidenceShouldHaveOneAssertionOnRead|Okunan SamlEvidence bir başvuru veya katıştırılmış bir SamlAssertion içermiyordu.|  
|LengthOfArrayToConvertMustGreaterThanZero|Dizi uzunluğu, bir tamsayıya dönüştürmek için 0'dan büyük olmalıdır.|  
|InvalidAsyncResult|Geçersiz AsyncResult.|  
|TraceCodeIssuanceTokenProviderRemovedCachedToken|IssuanceTokenProvider süresi dolan hizmet belirteci kaldırıldı.|  
|IncorrectUserNameFormat|Kullanıcı adı geçersiz bir biçimdedir. Kullanıcı adı biçimi biçiminde olmalıdır "kullanıcı adı ' veya ' etki alanı\\\username'.|  
|TraceCodeExportSecurityChannelBindingEntry|Güvenlik ExportChannelBinding başlatılıyor.|  
|UnsupportedInputTypeForTransform|Belirtilen giriş türü dönüştürme için desteklenmiyor.|  
|CannotFindDocumentRoot|Belge kökü bulunamıyor.|  
|XmlBufferQuotaExceeded|XML içeriği arabellek gerekli boyutu ara bellek kotasını aştı.|  
|TraceCodeSecuritySessionClosedResponseSendFailure|İstemciye bir güvenlik oturumu kapat yanıtı gönderilirken bir hata oluştu.|  
|UnableToResolveReferenceInSamlSignature|Onaylama kimliği ile SAML imzada belirtilen başvurusu çözümlenemiyor.|  
|SAMLSubjectRequiresNameIdentifierOrConfirmationMethod|Bir SamlSubject 'NameIdentifier' veya 'ConfirmationMethod' belirtilmesini gerektirir. Her ikisi de eksik.|  
|SAMLAttributeMissingNamespaceAttributeOnRead|'Namespace' Okunan SamlAttribute eksik ya da 0 uzunluğunda.|  
|SAMLSubjectConfirmationClauseMissingConfirmationMethodOnRead|Okunan SamlSubjectConfirmation 'ConfirmationMethod' bulunamıyor.|  
|SecurityTokenRequirementHasInvalidTypeForProperty|Belirtilen özellik için beklenmeyen bir tür belirteç gereksinimi vardır. Beklenen özellik türü başka bir değerdir.|  
|TraceCodeNegotiationTokenProviderAttached|NegotiationTokenProvider eklendi.|  
|TraceCodeSpnegoClientNegotiationCompleted|SpnegoTokenProvider SSPI anlaşmasını tamamladı.|  
|SAMLUnableToLoadUnknownElement|Seçili SamlSerializer bu öğeyi seri durumdan alamıyor. Lütfen özel öğeleri seri durumdan çıkarılacak özel bir SamlSerializer kaydettirin.|  
|CreateSequenceRefused|Oluşturma sırası isteği RM Destination tarafından reddedildi.|  
|TraceCodeSecuritySessionRedirectApplied|İstemci güvenlik oturumu yeniden yönlendirildi.|  
|SecurityTokenRequirementDoesNotContainProperty|Belirteç gereksinimi belirtilen özellik içermiyor.|  
|SAMLAttributeValueCannotBeNull|SamlAttribute içinde bulunan attributeValues öğelerinden biri null değeri bulundu. Listeleri SamlAttribute oluştururken null olduğundan emin olun.|  
|ValueMustBeGreaterThanZero|Bu bağımsız değişkenin değeri 0'dan büyük olmalıdır.|  
|TraceCodeNegotiationAuthenticatorAttached|NegotiationTokenAuthenticator eklendi.|  
|ValueMustBePositive||  
|SAMLAuthorizationDecisionShouldHaveOneAction|Bir SamlAuthorizationDecisionStatement en az bir SamlAction olması gerekir.|  
|TraceCodeSecurityTokenAuthenticatorClosed|Güvenlik belirteci kimlik doğrulayıcı kapatıldı.|  
|TraceCodeSecurityAuditWrittenSuccess|Güvenlik Denetim günlüğü başarıyla yazıldı.|  
|PrivateKeyNotDSA|Özel anahtar bir DSA anahtarı değil.|  
|MessageNumberRollover|Bu sırası için en büyük sıra sayısı aşıldı.|  
|AESPaddingModeNotSupported|Belirtilen doldurma modu desteklenmiyor. Yalnızca PKCS7 ve ISO10126 desteklenir.|  
|SAMLSubjectRequiresNameIdentifierOrConfirmationMethodOnRead|Gerekli 'NameIdentifier' ve 'ConfirmationMethod' öğeleri okunan SamlSubject için bulunamadı.|  
|TraceCodeSecurityAuditWrittenFailure|Güvenlik Denetim günlüğüne yazılırken bir hata oluştu.|  
|UnsupportedCryptoAlgorithm|Belirtilen şifreleme algoritması bu bağlamda desteklenmiyor.|  
|SigningTokenHasNoKeysSupportingTheAlgorithmSuite|İmzalama belirtecin belirtilen algoritma paketini destekleyen anahtarı yok.|  
|SAMLNameIdentifierMissingIdentifierValueOnRead|Okunan SamlNameIdentifier 'Tanımlayıcısı' dizesi eksik.|  
|SAMLSubjectStatementRequiresSubject|SAML konu deyimi bir SAML konu belirtilmesini gerektirir.|  
|TraceCodeSslClientCertMissing|Gerekli bir sertifika sağlamak uzak SSL istemcisi başarısız oldu.|  
|SAMLTokenVersionNotSupported|Belirtilen ana sürüm ve alt sürümü desteklenmez.|  
|TraceCodeConfigurationIsReadOnly|Yapılandırma salt okunurdur.|  
|TraceCodeSecuritySessionRenewFaultSendFailure|Bir yenileme hatası güvenlik oturum anahtarının istemciye gönderirken bir hata oluştu.|  
|TraceCodeSecurityInactiveSessionFaulted|Etkin olmayan güvenlik oturumu sunucu tarafından alındı.|  
|SAMLUnableToLoadAttribute|SamlAttribute yüklenemedi.|  
|Psha1KeyLengthInvalid|Belirtilen PSHA1 anahtar uzunluğu geçersiz.|  
|KeyIdentifierCannotCreateKey|Bu SecurityKeyIdentifier bir anahtar oluşturmak herhangi bir koşul yok.|  
|X509IsInUntrustedStore|Belirtilen X.509 sertifikası bir Güvenilmeyen sertifika deposunda olduğunu.|  
|UnexpectedXmlChildNode|Belirtilen XML alt düğümü belirtilen türündeki belirtilen öğe için beklenmeyen bir durumdur.|  
|TokenDoesNotMeetKeySizeRequirements|Belirtilen belirteç tarafından belirtilen algoritma paketi için anahtar boyutu gereksinimleri karşılanmadı.|  
|TraceCodeSecuritySessionRequestorStartOperation|İstemcide güvenlik oturumu işlemi başlatıldı.|  
|InvalidHexString|Onaltılık dize biçimi geçersiz.|  
|SamlAttributeClaimResourceShouldBeAString|Bu SamlAttribute Oluşturucu talep kaynak türü 'string' olmasını gerektirir.|  
|SamlSigningTokenNotFound|SamlAssertion imzalandı ancak SamlAssertion imzalı belirteç bulunamıyor. SecurityTokenResolver SamlAssertion imzalı belirteç içerdiğinden emin olun.|  
|TraceCodeSecuritySpnToSidMappingFailure|ServicePrincipalName bir SecurityIdentifier eşlenemedi.|  
|UnableToCreateSignatureFormatterFromAsymmetricCrypto|Belirtilen algoritma için imza biçimlendirici belirtilen asimetrik şifreleme oluşturulamıyor.|  
|TraceCodeSecurityServerSessionClosedFaultSent|Sunucu güvenlik oturumu istemciye bir oturum kapalı hatası gönderdi.|  
|UnableToFindPrefix|Belirtilen öğede belirtilen görünür şekilde kullanılan öneki için önek bulunamıyor|  
|TraceCodeSecurityTokenAuthenticatorOpened|Güvenlik belirteci kimlik doğrulayıcı açıldı.|  
|RequiredAttributeMissing|Belirtilen özniteliğin belirtilen öğede gereklidir.|  
|LocalIdCannotBeEmpty|LocalId boş olamaz. Bir geçerli 'yerel kimlik' belirtin.|  
|ValueMustBeInRange|Bu bağımsız değişkenin değeri belirtilen aralıkta olmalıdır.|  
|TraceCodeIssuanceTokenProviderBeginSecurityNegotiation|IssuanceTokenProvider yeni bir güvenlik anlaşması başlatıldı.|  
|InvalidNtMapping|Belirtilen X.509 sertifikası için bir Windows hesabı eşlenemez. UPN konu alternatif adı gereklidir.|  
|AESCryptSetKeyParamFailed|Belirtilen anahtar parametresini ayarlama başarısız oldu.|  
|TraceCodeSecuritySessionClosedResponseReceived|İstemci güvenlik oturumu sunucudan kapalı bir yanıt aldı.|  
|UnableToCreateSignatureDeformatterFromAsymmetricCrypto|Belirtilen algoritma için imza biçim kaldırıcısı belirtilen asimetrik şifreleme oluşturulamıyor.|  
|TraceCodeIdentityModelAsyncCallbackThrewException|Zaman uyumsuz geri çağırma özel durum oluşturdu.|  
|LengthMustBeGreaterThanZero|Bu bağımsız değişkenin uzunluğu 0'dan büyük olmalıdır.|  
|FoundMultipleCerts|Belirtilen arama ölçütleri kullanarak birden çok X.509 Sertifika bulundu: StoreName, StoreLocation, FindType, FindValue. Daha fazla belirli bir bulma değeri sağlayın.|  
|AtLeastOneTransformRequired|Dönüşümler öğesi en az bir dönüşüm içermelidir.|  
|SAMLTokenNotSerialized|SamlAssertion XML seri hale getirilemedi. Lütfen ayrıntılar için iç özel duruma bakın.|  
|TraceCodeSecurityBindingOutgoingMessageSecured|Güvenlik protokolü giden iletiyi güvenli.|  
|KeyIdentifierClauseDoesNotSupportKeyCreation|Bu SecurityKeyIdentifierClause, anahtar oluşturmayı desteklemiyor.|  
|UnableToResolveTokenReference|Belirteç çözümleyicisi belirtilen belirteç başvurusu çözümleyemiyor.|  
|UnsupportedEncryptionAlgorithm|Belirtilen şifreleme algoritması desteklenmiyor.|  
|SamlSerializerUnableToWriteSecurityKeyIdentifier|SamlSerializer verilen SecurityKeyIdentifier seri hale getirme uyumlu bir SecurityTokenSerializer içermiyor. Özel bir SecurityKeyIdentifier kullanıyorsanız, özel bir SecurityTokenSerializer sağlamanız gerekir.|  
|SAMLAttributeShouldHaveOneValue|Öznitelik değeri bulunamadı. SamlAttribute özniteliği en az bir öznitelik değeri olmalıdır.|  
|TraceCodeSecurityBindingVerifyIncomingMessageFailure|Güvenlik protokolü gelen iletiyi doğrulayamıyor.|  
|SamlSigningTokenMissing|SamlSecurityTokenAuthenticator öğesine geçirilen SamlAssertion imzalama belirteci içermiyor.|  
|NoPrivateKeyAvailable|Özel anahtar yok.|  
|ValueMustBeOne|Bu bağımsız değişkenin değeri 1 olmalıdır.|  
|TraceCodeSecurityPendingServerSessionRemoved|Bekleyen bir güvenlik oturumu sunucu tarafından etkin hale getirildi.|  
|TraceCodeImportSecurityChannelBindingExit|Güvenlik ImportChannelBinding tamamlandı.|  
|X509CertStoreLocationNotValid|StoreLocation, LocalMachine veya Currentuser'a olması gerekir.|  
|SettingdMayBeModifiedOnlyWhenTheWriterIsInStartState|Yazıcı ayarları, yalnızca yazıcı başlangıç durumda olduğunda değiştirilebilir.|  
|ArgumentInvalidCertificate|Sertifika geçersiz.|  
|DigestVerificationFailedForReference|Özet, belirtilen başvurusu doğrulanamadı.|  
|SAMLAuthorityBindingRequiresBinding|SamlAuthorityBinding üstünde belirtilen 'Binding' özniteliği null ya da 0 uzunluğunda olamaz.|  
|AESInsufficientOutputBuffer|Çıkış arabelleği belirtilen bayttan büyük olmalıdır.|  
|SAMLAuthorityBindingMissingBindingOnRead|'Binding' özniteliği Okunan SamlAuthorityBinding eksik ya da 0 uzunluğunda.|  
|SAMLAuthorityBindingInvalidAuthorityKind|Okunan SamlAuthorityBinding geçersiz bir AuthorityKind değerine sahiptir. AuthorityKind biçimlerinin QName olmalıdır.|  
|ProvidedNetworkCredentialsForKerberosHasInvalidUserName|Kerberos Token için sağlanan NetworkCredentials geçerli bir kullanıcı adı yok.|  
|SSPIPackageNotSupported|Belirtilen SSPI paketi desteklenmiyor.|  
|TokenCancellationNotSupported|Belirtilen belirteç sağlayıcı belirteci iptal desteklemez.|  
|UnboundPrefixInQName|İlişkisiz bir ön eki içinde belirtilen tam adı kullanılır.|  
|SAMLAuthorizationDecisionResourceRequired|'Özniteliği için belirtilen'resource ' null veya uzunluğu 0 olamaz.|  
|TraceCodeSecurityNegotiationProcessingFailure|Hizmet güvenliği anlaşma işleme hatası.|  
|SAMLAssertionIssuerRequired|'SamlAssertion için belirtilen dağıtımcı' null veya boş olamaz.|  
|UnableToCreateHashAlgorithmFromAsymmetricCrypto|Belirtilen algoritma için bir HashAlgorithm belirtilen asimetrik şifreleme oluşturulamıyor.|  
|SamlUnableToExtractSubjectKey|SamlSubject bulundu SecurityKeyIdentifier bir SecurityToken çözümlenemiyor. SecurityTokenResolver SecurityKeyIdentifier çözümler SecurityToken içermesi gerekir.|  
|ChildNodeTypeMissing|Belirtilen XML öğesi belirtilen türde bir alt yok.|  
|TraceCodeSecurityPendingServerSessionClosed|Bekleyen güvenlik oturumu sunucu tarafından kapatıldı.|  
|TraceCodeSecuritySessionCloseResponseSent|Sunucu güvenlik oturumu istemciye Kapat bir yanıt gönderdi.|  
|TraceCodeSecurityIdentityHostNameNormalizationFailure|Bir uç nokta adresi ana bilgisayar adı kısmı normalleştirilmiş olamaz.|  
|FailAcceptSecurityContext|AcceptSecurityContext başarısız oldu.|  
|EmptyXmlElementError|Belirtilen öğe boş olamaz.|  
|PrefixNotDefinedForNamespace|Belirtilen ad alanı için bir önek bu bağlamda tanımlı değil ve bildirilemez.|  
|SAMLAuthorizationDecisionHasMoreThanOneEvidence|Okunan özniteliği birden fazla kanıt saptandı. Bu duruma izin verilmez.|  
|SamlTokenAuthenticatorCanOnlyProcessSamlTokens|SamlSecurityTokenAuthenticator yalnızca SamlSecurityToken öğelerini işleyebilir. Belirtilen SecurityTokenType alındı.|  
|SAMLAttributeStatementMissingAttributeOnRead|Okunan SamlAttributeStatement herhangi bir 'SamlAttribute' öğesi içermiyor. Bu duruma izin verilmez.|  
|CouldNotFindNamespaceForPrefix|Ad alanı için belirtilen önek arayın olamaz.|  
|TraceCodeExportSecurityChannelBindingExit|Tamamlanmış Güvenlik ExportChannelBinding.|  
|AESCryptDecryptFailed|Belirtilen verilerin şifresi çözülemedi.|  
|SAMLAttributeNamespaceAttributeRequired|'SamlAttribute için belirtilen Namespace' null veya uzunluğu 0 olamaz.|  
|TraceCodeSpnegoServiceNegotiationCompleted|SpnegoTokenAuthenticator SSPI anlaşmasını tamamladı.|  
|TraceCodeSecurityServerSessionRenewalFaultSent|Sunucu güvenlik oturumu istemciye bir anahtar yenileme hatası gönderdi.|  
|AlgorithmMismatchForTransform|Dönüştürme algoritmasında bir uyuşmazlığı oluştu.|  
|UserNameAuthenticationFailed|Belirtilen mekanizmasını kullanarak bir kullanıcı adı/parola kimlik doğrulaması başarısız oldu. Kullanıcının kimliği.|  
|SamlInvalidSigningToken|SamlAssertion göre Protokolü doğrulanmadı bir belirteç ile imzalanmış. X.509 sertifikaları kullanıyorsanız, doğrulama semantiği inceleyin.|  
|TraceCodeSecurityServerSessionKeyUpdated|Güvenlik oturumu anahtarı sunucu tarafından güncelleştirildi.|  
|TraceCodeSecurityServerSessionCloseReceived|Sunucu güvenlik oturumu istemciden Kapat bir ileti aldı.|  
|SAMLAuthenticationStatementMissingSubject|SamlAuthenticationStatement gerekli SamlSubjectStatement öğesi eksik.|  
|UnexpectedEndOfFile|Beklenmeyen dosya sonu.|  
|UnsupportedAlgorithmForCryptoOperation|Belirtilen algoritma belirtilen işlem için desteklenmiyor.|  
|XmlLangAttributeMissing|Gereken XML: lang özniteliği eksik.|  
|TraceCodeSecurityImpersonationSuccess|Güvenlik kimliğine bürünme işlemi sunucuda başarılı oldu.|  
|SAMLAuthorityBindingMissingLocationOnRead|Okunan SamlAuthorityBinding eksik ya da uzunluğu 0 'Konum' özniteliği.|  
|SAMLAttributeStatementMissingSubjectOnRead|SamlAttributeStatement için 'SamlSubject' öğesi eksik.|  
|SAMLAuthorizationDecisionStatementMissingSubjectOnRead|Okunan SamlAuthorizationDecisionStatement 'SamlSubject' öğesi eksik.|  
|SAMLBadSchema|SamlAssertion okunurken şeması ile uyumlu olmadığı için bu belirtilen öğe bulunamadı.|  
|SAMLAssertionIDIsInvalid|Belirtilen 'onaylama kimliği' SamlAssertion için bir harf veya '_' ile başlamalıdır.|  
|TraceCodeSecurityActiveServerSessionRemoved|Etkin bir güvenlik oturumu sunucu tarafından kaldırıldı.|  
|UnableToCreateKeyedHashAlgorithmFromSymmetricCrypto|Belirtilen algoritma için bir keyedHashAlgorithm belirtilen simetrik şifreleme oluşturulamıyor.|  
|SAMLAuthenticationStatementMissingAuthenticationMethod|'Bir SamlAuthenticationStatement için belirtilen AuthenticationMethod' null veya uzunluğu 0 olamaz.|  
|TraceCodeSecurityImpersonationFailure|Güvenlik kimliğine bürünme işlemi sunucuda başarısız oldu.|  
|Varsayılan|(Varsayılan)|  
|UnsupportedNodeTypeInReader|Belirtilen ada sahip belirtilen düğüm türü desteklenmiyor.|
