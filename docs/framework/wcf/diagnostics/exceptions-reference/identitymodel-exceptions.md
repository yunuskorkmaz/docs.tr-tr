---
title: IdentityModel Özel Durumları
ms.date: 03/30/2017
ms.assetid: 4ef34497-8ff5-4621-b773-7731cc721231
ms.openlocfilehash: ee0b5537a415e1ea53c653ae8e8485e94cc713fd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61998523"
---
# <a name="identitymodel-exceptions"></a>IdentityModel Özel Durumları
Bu konu IdentityModel tarafından oluşturulan tüm özel durumları listeler.  
  
## <a name="exception-list"></a>Özel durum listesi  
  
|Kaynak kodu|Geçerli bir dize|  
|-------------------|--------------------|  
|ValueMustBeOf2Types|Bu bağımsız değişkenin değeri bu iki tür olmalıdır.|  
|SAMLSubjectNameIdentifierRequiresNameValue|SamlNameIdentifier için belirtilen 'Name', null ya da 0 uzunluğunda olamaz.|  
|TraceCodeIssuanceTokenProviderEndSecurityNegotiation|Güvenlik görüşmeleri IssuanceTokenProvider tamamlandı.|  
|TraceCodeSecurityNewServerSessionKeyIssued|Yeni güvenlik oturumu anahtarı, sunucu tarafından yayınlandı.|  
|SAMLAttributeMissingNameAttributeOnRead|'Name' için Okunan SamlAttribute eksik ya da 0 uzunluğunda.|  
|UnknownICryptoType|ICrypto uygulaması desteklenmiyor.|  
|TraceCodeSecurityTokenProviderClosed|Güvenlik belirteci sağlayıcı kapatıldı.|  
|SAMLUnableToLoadAdvice|Yüklenemedi \<SAML: advice > öğesi.|  
|SAMLAuthenticationStatementMissingAuthenticationMethodOnRead|Bir SamlAuthenticationStatement ya da 0 uzunluğunda okunan 'AuthenticationMethod' özniteliği.|  
|UnsupportedTransformAlgorithm|Desteklenmeyen dönüştürme ya da kurallaştırma algoritması.|  
|SAMLAudienceRestrictionShouldHaveOneAudience|Bir SamlAudienceRestrictionCondition en az bir hedef kitleye (URI) içermelidir.|  
|SAMLEvidenceShouldHaveOneAssertion|En az bir SamlAssertion kimliği veya başvuru SamlEvidence başvurmalıdır.|  
|SAMLAudienceRestrictionInvalidAudienceValueOnRead|Okunan SamlAudienceRestrictionCondition 'Audience' öğesine bir değer eksik.|  
|X509ChainBuildFail|Özel X.509 Sertifika zinciri oluşturma başarısız oldu. Kullanılan sertifika doğrulanamayan bir güven zincirine sahip. Sertifikayı değiştirin veya Certificatevalidationmode'u değiştirin.|  
|XDCannotFindValueInDictionaryString|Belirli bir değerin kimlik sözlük dizesinde bulunamadı.|  
|TraceCodeImportSecurityChannelBindingEntry|Güvenlik ImportChannelBinding başlatılıyor.|  
|PrivateKeyExchangeNotSupported|Özel anahtarı KeySpec öğesinin exchange desteklemez.|  
|TokenProviderUnableToGetToken|Belirli belirteç sağlayıcısı bir güvenlik belirteci sağlayamadı.|  
|SAMLEntityCannotBeNullOrEmpty|Belirli SamlAssertion varlığı null veya boş olamaz.|  
|SAMLAssertionRequireOneStatement|Bir SamlAssertion en az bir deyim gerektirir. Oluşturmakta olduğunuz SamlAssertion en az bir SamlStatement eklediğinizden emin olun.|  
|AESInvalidInputBlockSize|Giriş boyutu belirli baytın katlarından biri olmalıdır.|  
|AESCryptAcquireContextFailed|CSP bağlamı alınamadı.|  
|SAMLAssertionRequireOneStatementOnRead|Okunan SamlAssertion herhangi bir SamlStatement içermiyordu. Bir SamlAssertion en az bir SamlStatement içermelidir.|  
|TraceCodeSecuritySessionClosedFaultReceived|İstemci güvenlik oturumu sunucudan oturum kapalı hatası alındı.|  
|TraceCodeIssuanceTokenProviderRedirectApplied|Bir yeniden yönlendirme üstbilgisi IssuanceTokenProvider uygulanır.|  
|TraceCodeSecuritySessionClosedFaultSendFailure|İstemciye hata kapalı bir güvenlik oturumu göndermeye çalışırken bir hata oluştu.|  
|ValueMustBeZero|Bu bağımsız değişkenin değeri 0 olmalıdır.|  
|SAMLUnableToResolveSignatureKey|SamlAssertion imzasında bulunan SecurityKeyIdentifier bulunan çözmek yüklenemiyor. Belirli bir sertifika veren için SamlAssertion imzası doğrulanamıyor.|  
|X509IsNotInTrustedStore|Özel X.509 sertifikası güvenilir kişiler deposunda değil.|  
|SAMLElementNotRecognized|Belirli bir öğe desteklenmiyor.|  
|SAMLAuthorizationDecisionStatementMissingResourceAttributeOnRead|'Resource' özniteliği okunan özniteliği eksik ya da 0 uzunluğunda.|  
|SamlTokenMissingSignature|SamlAssertion imzalanmamış. SamlAssertion öğeleri signingcredential değerleri ayarlanarak imzalanabilir.|  
|ExpectedElementMissing|Belirli ad alanıyla beklenen öğesi eksik.|  
|NoKeyIdentifierClauseFound|Belirli türünde yan tümce SecurityKeyIdentifier içinde bulunamadı.|  
|MissingPrivateKey|X.509 Sertifika özel anahtarı yok.|  
|UnexpectedEOFFromReader|XML okuyucusundan beklenmeyen dosya sonu.|  
|UnsupportedKeyDerivationAlgorithm|Belirli bir anahtar türetme algoritması desteklenmiyor.|  
|TokenDoesNotSupportKeyIdentifierClauseCreation|Özel belirteç özel anahtarı tanımlayıcısı yan tümcesi oluşturulmasını desteklemiyor.|  
|LastMessageNumberExceeded|Sıra numarası protokolü ihlali algılandı.|  
|SymmetricKeyLengthTooShort|Belirtilen simetrik anahtarın uzunluğu çok kısa.|  
|SAMLAuthorityBindingMissingAuthorityKindOnRead|Bir 'AuthorityKind' saptandı salt okunur olan SamlAuthorityBinding, eksik ya da 0 uzunluğunda.  Buna izin verilmez.|  
|XmlTokenBufferIsEmpty|XmlTokenBuffer boştur.|  
|InvalidXmlQualifiedName|Bir Xml tam adı bekleniyordu, ancak geçersiz bir ad bulunamadı.|  
|SAMLAuthorityKindMissingName|SamlAuthorityBinding 'AuthorityKind' temsil eden XmlQualifiedName null ya da 0 uzunluğunda olamaz.|  
|AESCryptEncryptFailed|Belirli verileri şifrelemek başarısız oldu.|  
|AuthorizationContextCreated|Yetkilendirme bağlamında belirli kimliği ile oluşturulur.|  
|SamlSerializerUnableToReadSecurityKeyIdentifier|SamlSerializer, SecurityKeyIdentifier okuma özellikli bir SecurityTokenSerializer içermiyor. Özel bir SecurityKeyIdentifier kullanıyorsanız, özel bir SecurityTokenSerializer sağlamalısınız.|  
|TraceCodeIssuanceTokenProviderServiceTokenCacheFull|Hizmet belirteç önbelleği IssuanceTokenProvider azaltıldı.|  
|TraceCodeSecurityTokenProviderOpened|Güvenlik belirteci sağlayıcı açıldı.|  
|PublicKeyNotRSA|Ortak anahtarı bir RSA anahtarı değil.|  
|InvalidReaderState|Belirli bir durum için sağlanan giriş okuyucu geçersiz.|  
|UnableToResolveReferenceUriForSignature|Özet işlem için özel URI imzasında çözmek yüklenemiyor.|  
|EmptyBase64Attribute|Ad alanı ve gerekli base64 öznitelik adı için boş bir değer bulundu.|  
|SAMLSubjectRequiresConfirmationMethodWhenConfirmationDataOrKeyInfoIsSpecified|Onay verileri veya KeyInfo belirtildiğinde SAML SubjectConfirmation onay yöntemini gerektirir.|  
|SAMLAudienceRestrictionShouldHaveOneAudienceOnRead|Okunan SamlAudienceRestrictionCondition 'Audience' en az bir değer içermelidir. Hiçbiri bulunamadı.|  
|TokenProviderUnableToRenewToken|Belirli belirteç sağlayıcısı güvenlik belirtecini yenileyemedi.|  
|AESIVLengthNotSupported|Belirli BITS IV desteklenmiyor. Yalnızca 128 bit IV desteklenir.|  
|SAMLAuthorityBindingMissingAuthorityKind|Bir SamlAuthorityBinding 'AuthorityKind' içermelidir. null değil.|  
|TraceCodeSecuritySessionDemuxFailure|Gelen ileti, var olan bir güvenlik oturumunun parçası değil.|  
|TokenRenewalNotSupported|Belirli belirteç sağlayıcısı, belirteç yenilemeyi desteklemiyor.|  
|AtLeastOneReferenceRequired|Bir imzada en az bir başvuru gereklidir.|  
|SAMLSignatureAlreadyRead|İmza zaten SAML onaylaması okunur.|  
|AlgorithmAndPrivateKeyMisMatch|Belirtilen algoritma ve özel anahtarı eşleşmiyor.|  
|EmptyTransformChainNotSupported|Boş dönüştürme zinciri desteklenmiyor.|  
|SspiWrapperEncryptDecryptAssert1|SSPIWrapper::EncryptDecryptHelper&#124;'offset' olan aralık dışında.|  
|SspiWrapperEncryptDecryptAssert2|SSPIWrapper::EncryptDecryptHelper&#124;' boyutudur ' aralık dışında. SecurityTokenManagerCannotCreateAuthenticatorForRequirement = güvenlik belirteci yöneticisi, belirli bir gereksinim için bir belirteç kimlik doğrulayıcısı oluşturamıyor.|  
|UnableToCreateKeyedHashAlgorithm|Belirli bir imza algoritması belirli değerinden bir KeyedHashAlgorithm oluşturulamadı.|  
|SAMLUnableToLoadAssertion|\<SAML: assertion > öğesi yüklenemedi.|  
|X509FindValueMismatchMulti|Belirli X509FindType türü bağımsız değişkeni findValue 2 değerlerden biri olmasını gerektirir. Bağımsız değişken findValue başka bir türüdür.|  
|TraceCodeSecurityIdentityDeterminationSuccess|Kimlik için bir EndpointAddress belirlendi.|  
|UndefinedUseOfPrefixAtElement|Öğe kullanılan belirli ön tanımlı ad alanı yok.|  
|TraceCodeSecuritySessionResponderOperationFailure|Güvenlik oturumu işlem sunucusunda başarısız oldu.|  
|CannotFindCert|Arama ölçütleri kullanılarak X.509 sertifikası bulunamıyor: StoreName, StoreLocation, FindType, FindValue'i tıklatın.|  
|X509InvalidUsageTime|Belirli bir X.509 sertifikası kullanım süresi geçerli değil. Kullanım süresi NotBefore zamanı ile NotAfter zamanı arasında düşmüyor.|  
|TraceCodeSecurityIdentityDeterminationFailure|Kimlik için bir EndpointAddress belirlenemiyor.|  
|AsyncObjectAlreadyEnded|End yöntemi, bu zaman uyumsuz sonuç nesnesi üzerinde zaten çağrıldı.|  
|ExternalDictionaryDoesNotContainAllRequiredStrings|Dış sözlüğü tanımlar için gerekli tüm dizeleri içermiyor. Spesifik dize, uzak sözlükte kullanılamaz.|  
|TraceCodeSecuritySessionKeyRenewalFaultReceived|İstemci güvenlik oturumu sunucudan bir anahtar yenileme hatası alındı.|  
|SAMLActionNameRequired|SamlAction temsil eden dize null ya da 0 uzunluğunda olamaz.|  
|SignatureVerificationFailed|İmza doğrulaması başarısız oldu.|  
|TraceCodeSecurityContextTokenCacheFull|SecurityContextSecurityToken önbellek dolu.|  
|SAMLAssertionMissingMajorVersionAttributeOnRead|Okunan SamlAssertion için MajorVersion eksik ya da 0 uzunluğunda.|  
|SamlAttributeClaimRightShouldBePossessProperty|Bu SamlAttribute Oluşturucu talep sağındaki değer isteğinin System.IdentityModel.Claims.Rights.PossessProperty sahip olmasını gerektirir.|  
|AuthorizationPolicyEvaluated|Belirli kimliğine sahip ilke değerlendirilir.|  
|SAMLUnableToLoadCondtions|\<SAML: Conditions > öğesi yüklenemedi.|  
|AESKeyLengthNotSupported|Belirli bir bit anahtar desteklenmiyor. Yalnızca 128, 192 ve 256 bit anahtar desteklenir.|  
|UserNameCannotBeEmpty|Kullanıcı adı boş olamaz.|  
|AlgorithmAndPublicKeyMisMatch|Belirtilen algoritma ve ortak anahtarı eşleşmiyor.|  
|SAMLUnableToLoadCondtion|\<SAML: Conditions > öğesi yüklenemedi.|  
|SamlAssertionMissingSigningCredentials|Samlassertion'da SigningCredentials ayarlanmamış. SamlAssertions oturum açın, Lütfen geçerli bir SigningCredentials devam etmek için Samlassertion'da ayarlayın.|  
|SspiPayloadNotEncrypted|İkili verileri SSPI güvenlik bağlamı ile şifrelenmemiş.|  
|SAMLAuthorizationDecisionShouldHaveOneActionOnRead|Tüm SamlAction okunan özniteliği içermiyor.|  
|TraceCodeSecurityBindingSecureOutgoingMessageFailure|Giden ileti güvenlik protokolü koruyamazsınız.|  
|UndefinedUseOfPrefixAtAttribute|Belirli özellik kullanılan belirli ön tanımlı ad alanı yok.|  
|NoInputIsSetForCanonicalization|Herhangi bir giriş Kurallaştırılan çıktı yazmak için ayarlanır.|  
|TraceCodeSecurityPendingServerSessionAdded|Bekleyen bir güvenlik oturumu sunucuya eklendi.|  
|AsyncCallbackException|Bir AsyncCallback bir özel durum oluşturdu.|  
|PrivateKeyNotRSA|Özel anahtarı bir RSA anahtarı değil.|  
|TraceCodeSecurityClientSessionKeyRenewed|İstemci güvenlik oturumu oturum anahtarı yenilendi.|  
|SAMLAuthorizationDecisionStatementMissingDecisionAttributeOnRead|'Kararı' okunan özniteliği eksik ya da 0 uzunluğunda.|  
|SAMLAttributeNameAttributeRequired|SamlAttribute için belirtilen 'Name', null ya da 0 uzunluğunda olamaz.|  
|SamlSerializerRequiresExternalSerializers|SamlSerializer belirteç içinde bulunan SecurityKeyIdentifier öğesini serileştirmek bir SecurityTokenSerializer öğesine gereksinim duyar.|  
|UnableToResolveKeyReference|Belirteç çözümleyici belirli güvenlik anahtarı başvurusunu çözümleyemiyor.|  
|UnsupportedKeyWrapAlgorithm|Belirli bir anahtarı kaydırma algoritması desteklenmiyor.|  
|SAMLAssertionMissingIssuerAttributeOnRead|Okunan SamlAssertion için 'Issuer' eksik ya da 0 uzunluğunda.|  
|TraceCodeIssuanceTokenProviderUsingCachedToken|IssuanceTokenProvider önbelleğe alınan hizmet belirteci kullanılır.|  
|AESCryptGetKeyParamFailed|Özel anahtar parametresi alınamadı.|  
|InvalidNamespaceForEmptyPrefix|Boş önek için ad alanı geçersiz.|  
|AESCipherModeNotSupported|Belirli bir şifreleme modu desteklenmiyor. Yalnızca CBC desteklenir.|  
|ArgumentCannotBeEmptyString|Bağımsız değişkeni boş olmayan bir dize olmalıdır.|  
|SAMLAssertionMissingMinorVersionAttributeOnRead|Okunan SamlAssertion için MinorVersion eksik ya da 0 uzunluğunda.|  
|SpecifiedStringNotAvailableInDictionary|Belirtilen dize geçerli sözlükte bir giriş değil.|  
|KerberosApReqInvalidOrOutOfMemory|AP-REQ geçersiz olduğundan veya sistem, yeterli belleğe sahip değil.|  
|FailLogonUser|LogonUser belirtilen kullanıcı için başarısız oldu. Kullanıcının geçerli bir Windows hesabı olduğundan emin olun.|  
|ValueMustBeNonNegative|Bu bağımsız değişkenin değeri negatif olmayan olmalıdır.|  
|X509ValidationFail|Belirtilen X.509 Sertifika doğrulama başarısız oldu.|  
|TraceCodeSecuritySessionRequestorOperationSuccess|Güvenlik oturumu işlem istemcide başarıyla tamamlandı.|  
|SAMLActionNameRequiredOnRead|SamlAction için okunabilir dize eksik ya da 0 uzunluğunda.|  
|KerberosMultilegsNotSupported|Kimlik, UPN belirtilir. Bir kullanıcı hesabı altında çalışan bir hizmete kimlik doğrulaması, Kerberos çok bacak desteklenmeyen olduğu gerektirir.|  
|SAMLAssertionIdRequired|'In 'Assertionıd'si bir SamlAssertion null veya boş olamaz.|  
|InvalidOperationForWriterState|Belirtilen işlem belirtilen XmlWriter durumu geçersiz.|  
|CannotValidateSecurityTokenType|Belirtilen bir güvenlik belirteci kimlik doğrulayıcı, belirtilen türde bir belirteç doğrulanamıyor.|  
|X509FindValueMismatch|Belirtilen X509FindType türü bağımsız değişkeni findValue belirtilen bir değer olmasını gerektirir. Bağımsız değişken findValue başka bir türüdür.|  
|TraceCodeSecurityClientSessionCloseSent|Bir iletiyi kapat tarafından istemci güvenlik oturumu gönderildi.|  
|SuiteDoesNotAcceptAlgorithm|Belirtilen algoritma belirtilen işlem için belirtilen algoritma paketi tarafından kabul edilmiyor|  
|TraceCodeSecuritySessionRequestorOperationFailure|İstemci güvenlik oturumu işlemi başarısız oldu.|  
|SAMLUnableToLoadStatement|Bir SamlStatement yüklenemedi.|  
|InnerReaderMustBeAtElement|İç okuyucu öğe olmalıdır.|  
|UnableToCreateTokenReference|Güvenlik belirteci başvurusu oluşturulamıyor.|  
|TraceCodeSecurityBindingIncomingMessageVerified|Gelen ileti güvenlik protokolü doğrulandı.|  
|ObjectIsReadOnly|Nesne salt okunur.|  
|TraceCodeSecurityClientSessionPreviousKeyDiscarded|İstemci güvenlik oturumu önceki oturum anahtarının atıldı.|  
|SAMLTokenTimeInvalid|SamlToken zaman geçerli. Belirteç dışında etkili ve sona erme saati geçerli zamandır.|  
|TraceCodeSecurityIdentityVerificationSuccess|Kimlik doğrulama başarılı oldu.|  
|SigningTokenHasNoKeys|Belirtilen imzalama belirtecinin anahtarı yok.|  
|TraceCodeSecurityIdentityVerificationFailure|Kimlik doğrulaması başarısız oldu.|  
|AESCryptImportKeyFailed|Anahtar malzemesi içeri aktarılamadı.|  
|FailInitializeSecurityContext|InitializeSecurityContent başarısız oldu. Hizmet asıl adının doğru olduğundan emin olun.|  
|TraceCodeStreamSecurityUpgradeAccepted|Akış güvenlik yükseltmesi başarıyla kabul edildi.|  
|SAMLAuthorityBindingRequiresLocation|SamlAuthorityBinding üzerinde belirtilen 'Konum' özniteliği null ya da 0 uzunluğunda olamaz.|  
|PublicKeyNotDSA|Ortak anahtarı, DSA anahtarı değil.|  
|ImpersonationLevelNotSupported|Kerberos kullanarak kimlik doğrulama modları, belirtilen kimliğe bürünme düzeyini desteklemez. Geçerli tanımlama veya kimliğe bürünme düzeyini belirtin.|  
|RequiredTargetNotSigned|Belirtilen kimliğe sahip bir öğe imzalanması için gereklidir ancak değildi.|  
|SAMLAuthenticationStatementMissingAuthenticationInstanceOnRead|Bir SamlAuthenticationStatement ya da 0 uzunluğunda okunan 'AuthenticationInstant' özniteliği.|  
|SAMLEvidenceShouldHaveOneAssertionOnRead|Okunan SamlEvidence, başvuru veya katıştırılmış bir SamlAssertion içermiyordu.|  
|LengthOfArrayToConvertMustGreaterThanZero|Bir tamsayıya dönüştürmek için dizinin uzunluğu 0'dan büyük olmalıdır.|  
|InvalidAsyncResult|Neplatný výsledek AsyncResult|  
|TraceCodeIssuanceTokenProviderRemovedCachedToken|Süresi dolan hizmet belirteci IssuanceTokenProvider kaldırıldı.|  
|IncorrectUserNameFormat|Kullanıcı adı geçersiz bir biçimdedir. Kullanıcı adı biçimi biçiminde olmalıdır "kullanıcıadı ' veya ' etki alanı\\\username'.|  
|TraceCodeExportSecurityChannelBindingEntry|Starting Security ExportChannelBinding.|  
|UnsupportedInputTypeForTransform|Belirtilen giriş türü dönüştürme için desteklenmiyor.|  
|CannotFindDocumentRoot|Belgenin kök bulunamıyor.|  
|XmlBufferQuotaExceeded|XML içeriğini ara belleğe almak için gereken boyut, ara bellek kotasını aştı.|  
|TraceCodeSecuritySessionClosedResponseSendFailure|İstemciye bir güvenlik oturumu kapat yanıtı gönderilirken bir hata oluştu.|  
|UnableToResolveReferenceInSamlSignature|SAML imza onaylama kimliği ile belirtilen başvurusunda çözmek yüklenemiyor.|  
|SAMLSubjectRequiresNameIdentifierOrConfirmationMethod|Bir SamlSubject 'NameIdentifier' veya 'ConfirmationMethod' belirtilmesini gerektirir. Her ikisi de eksik.|  
|SAMLAttributeMissingNamespaceAttributeOnRead|'Namespace' Okunan SamlAttribute eksik ya da 0 uzunluğunda.|  
|SAMLSubjectConfirmationClauseMissingConfirmationMethodOnRead|Okunan SamlSubjectConfirmation 'ConfirmationMethod' bulunamıyor.|  
|SecurityTokenRequirementHasInvalidTypeForProperty|Belirteç gereksinimi, belirtilen özellik için beklenmeyen bir türde. Beklenen özellik türü başka bir değerdir.|  
|TraceCodeNegotiationTokenProviderAttached|NegotiationTokenProvider eklendi.|  
|TraceCodeSpnegoClientNegotiationCompleted|SSPI anlaşması SpnegoTokenProvider tamamlandı.|  
|SAMLUnableToLoadUnknownElement|Seçili SamlSerializer, bu öğeyi seri durumdan çıkaramıyor. Lütfen özel öğeleri seri durumdan çıkarmak için özel bir SamlSerializer kaydettirin.|  
|CreateSequenceRefused|Oluşturma sırası isteği RM hedef tarafından reddedildi.|  
|TraceCodeSecuritySessionRedirectApplied|İstemci güvenlik oturumu yönlendirildi.|  
|SecurityTokenRequirementDoesNotContainProperty|Belirteç gereksinimi, belirtilen özellik içermiyor.|  
|SAMLAttributeValueCannotBeNull|SamlAttribute içinde bulunan attributeValues öğelerinden biri null değeri bulundu. Listeleri SamlAttribute oluşturulurken null olmadığından emin olun.|  
|ValueMustBeGreaterThanZero|Bu bağımsız değişkenin değeri 0'dan büyük olmalıdır.|  
|TraceCodeNegotiationAuthenticatorAttached|NegotiationTokenAuthenticator eklendi.|  
|ValueMustBePositive||  
|SAMLAuthorizationDecisionShouldHaveOneAction|Bir SamlAuthorizationDecisionStatement en az bir SamlAction olması gerekir.|  
|TraceCodeSecurityTokenAuthenticatorClosed|Güvenlik belirteci kimlik doğrulayıcı kapatıldı.|  
|TraceCodeSecurityAuditWrittenSuccess|Güvenlik Denetim günlüğü başarıyla yazıldı.|  
|PrivateKeyNotDSA|Özel anahtar, DSA anahtarı değil.|  
|MessageNumberRollover|Bu dizi için en büyük sıra sayısı aşıldı.|  
|AESPaddingModeNotSupported|Belirtilen doldurma modu desteklenmiyor. Yalnızca PKCS7 ve ISO10126 desteklenir.|  
|SAMLSubjectRequiresNameIdentifierOrConfirmationMethodOnRead|Gerekli 'NameIdentifier' ve 'ConfirmationMethod' öğeleri okunan SamlSubject için bulunamadı.|  
|TraceCodeSecurityAuditWrittenFailure|Güvenlik Denetim günlüğüne yazılırken bir hata oluştu.|  
|UnsupportedCryptoAlgorithm|Belirtilen şifreleme algoritması bu bağlamda desteklenmiyor.|  
|SigningTokenHasNoKeysSupportingTheAlgorithmSuite|İmzalama belirtecinin belirtilen algoritma paketini destekleyen anahtarı yok.|  
|SAMLNameIdentifierMissingIdentifierValueOnRead|Okunan SamlNameIdentifier 'Identifier' dizesi eksik.|  
|SAMLSubjectStatementRequiresSubject|SAML konu deyimi bir SAML konu belirtilmesini gerektirir.|  
|TraceCodeSslClientCertMissing|Gerekli bir sertifika sağlamak uzak SSL istemcisi başarısız oldu.|  
|SAMLTokenVersionNotSupported|Belirtilen ana sürüm ve alt sürümü desteklenmez.|  
|TraceCodeConfigurationIsReadOnly|Yapılandırma, salt okunur.|  
|TraceCodeSecuritySessionRenewFaultSendFailure|Yenileme hatası güvenlik oturum anahtarının istemciye gönderilirken bir hata oluştu.|  
|TraceCodeSecurityInactiveSessionFaulted|Etkin olmayan güvenlik oturumu sunucu tarafından sonlandırıldı.|  
|SAMLUnableToLoadAttribute|SamlAttribute yüklenemedi.|  
|Psha1KeyLengthInvalid|Belirtilen PSHA1 anahtar uzunluğu geçersiz.|  
|KeyIdentifierCannotCreateKey|Bu SecurityKeyIdentifier, anahtar oluşturabilecek bir yan tümceye sahip değil.|  
|X509IsInUntrustedStore|Belirtilen X.509 sertifikası bir Güvenilmeyen sertifika deposunda olduğunu.|  
|UnexpectedXmlChildNode|Belirtilen öğe için belirtilen türün belirtilen XML alt düğümü beklenmiyor.|  
|TokenDoesNotMeetKeySizeRequirements|Belirtilen belirteç tarafından belirtilen algoritma paketini anahtar boyutu gereksinimleri karşılanmadı.|  
|TraceCodeSecuritySessionRequestorStartOperation|İstemcide güvenlik oturumu işlemi başlatıldı.|  
|InvalidHexString|Geçersiz onaltılık dize biçimi.|  
|SamlAttributeClaimResourceShouldBeAString|Bu SamlAttribute Oluşturucu ait kaynak talebi, 'string' türünde olmasını gerektirir.|  
|SamlSigningTokenNotFound|SamlAssertion imzalandı ancak SamlAssertion imzalandı belirteç bulunamıyor. SecurityTokenResolver SamlAssertion'ı imzalayan belirteci içerdiğinden emin olun.|  
|TraceCodeSecuritySpnToSidMappingFailure|ServicePrincipalName için bir SecurityIdentifier eşlenemedi.|  
|UnableToCreateSignatureFormatterFromAsymmetricCrypto|Belirtilen asimetrik şifreleme imzası biçimlendirici belirtilen algoritma için oluşturulamıyor.|  
|TraceCodeSecurityServerSessionClosedFaultSent|Sunucu güvenlik oturumu oturum kapalı hatası istemciye gönderilebilir.|  
|UnableToFindPrefix|Belirtilen öğede belirtilen görünüşte kullanılan öneki önek bulmak yüklenemiyor.|  
|TraceCodeSecurityTokenAuthenticatorOpened|Güvenlik belirteci kimlik doğrulayıcı açıldı.|  
|RequiredAttributeMissing|Belirtilen öğede belirtilen özniteliği gereklidir.|  
|LocalIdCannotBeEmpty|LocalId boş olamaz. Geçerli bir 'localId' belirtin.|  
|ValueMustBeInRange|Bu bağımsız değişkenin değeri belirtilen aralıkta olmalıdır.|  
|TraceCodeIssuanceTokenProviderBeginSecurityNegotiation|Yeni bir güvenlik anlaşması IssuanceTokenProvider başlatıldı.|  
|InvalidNtMapping|Belirtilen X.509 sertifikası için bir Windows hesabı eşlenemez. UPN konu alternatif adı gereklidir.|  
|AESCryptSetKeyParamFailed|Belirtilen anahtar parametresi ayarlanamadı.|  
|TraceCodeSecuritySessionClosedResponseReceived|İstemci güvenlik oturumu kapalı bir yanıt aldı.|  
|UnableToCreateSignatureDeformatterFromAsymmetricCrypto|Belirtilen algoritma için bir imza biçim kaldırıcısı belirtilen asimetrik şifreleme oluşturulamıyor.|  
|TraceCodeIdentityModelAsyncCallbackThrewException|Zaman uyumsuz bir geri çağırma bir özel durum oluşturdu.|  
|LengthMustBeGreaterThanZero|Bu bağımsız değişkenin uzunluğu 0'dan büyük olmalıdır.|  
|FoundMultipleCerts|Belirtilen arama ölçütleri kullanılarak birden çok X.509 sertifikası bulundu: StoreName, StoreLocation, FindType, FindValue'i tıklatın. Daha fazla belirli bir arama değeri sağlayın.|  
|AtLeastOneTransformRequired|Dönüşümler öğesi en az bir dönüştürme içermelidir.|  
|SAMLTokenNotSerialized|SamlAssertion, XML'ye serileştirilemedi. Lütfen ayrıntılar için iç özel duruma bakın.|  
|TraceCodeSecurityBindingOutgoingMessageSecured|Giden ileti güvenlik protokolü güvenli.|  
|KeyIdentifierClauseDoesNotSupportKeyCreation|Bu SecurityKeyIdentifierClause anahtar oluşturmayı desteklemiyor.|  
|UnableToResolveTokenReference|Belirteç çözümleyici belirtilen belirteç başvurusunu çözümleyemiyor.|  
|UnsupportedEncryptionAlgorithm|Belirtilen şifreleme algoritması desteklenmiyor.|  
|SamlSerializerUnableToWriteSecurityKeyIdentifier|SamlSerializer verilen SecurityKeyIdentifier seri hale getirme özelliğine sahip bir SecurityTokenSerializer içermiyor. Özel bir SecurityKeyIdentifier kullanıyorsanız, özel bir SecurityTokenSerializer sağlamalısınız.|  
|SAMLAttributeShouldHaveOneValue|Öznitelik değeri bulunamadı. En az bir öznitelik değeri bir SamlAttribute özniteliği olmalıdır.|  
|TraceCodeSecurityBindingVerifyIncomingMessageFailure|Güvenlik protokolü, gelen ileti doğrulanamıyor.|  
|SamlSigningTokenMissing|SamlAssertion SamlSecurityTokenAuthenticator öğesine geçirilen imzalama belirtecinin içermiyor.|  
|NoPrivateKeyAvailable|Özel anahtar kullanılabilir.|  
|ValueMustBeOne|Bu bağımsız değişkenin değeri 1 olmalıdır.|  
|TraceCodeSecurityPendingServerSessionRemoved|Bekleyen bir güvenlik oturumu sunucu tarafından etkin olarak yapıldı.|  
|TraceCodeImportSecurityChannelBindingExit|Güvenlik ImportChannelBinding tamamlandı.|  
|X509CertStoreLocationNotValid|StoreLocation LocalMachine ya da CurrentUser olmalıdır.|  
|SettingdMayBeModifiedOnlyWhenTheWriterIsInStartState|Yazıcı ayarları, yalnızca yazıcı başlangıç durumda olduğunda değiştirilebilir.|  
|ArgumentInvalidCertificate|Sertifika geçersiz.|  
|DigestVerificationFailedForReference|Özet için belirtilen başvurusu doğrulanamadı.|  
|SAMLAuthorityBindingRequiresBinding|SamlAuthorityBinding üzerinde belirtilen 'Binding' özniteliği null ya da 0 uzunluğunda olamaz.|  
|AESInsufficientOutputBuffer|Çıkış arabelleği belirtilen bayttan büyük olmalıdır.|  
|SAMLAuthorityBindingMissingBindingOnRead|'Binding' özniteliği Okunan SamlAuthorityBinding eksik ya da 0 uzunluğunda.|  
|SAMLAuthorityBindingInvalidAuthorityKind|Okunan SamlAuthorityBinding geçersiz bir AuthorityKind değerine sahiptir. Biçim AuthorityKind bir QName olmalıdır.|  
|ProvidedNetworkCredentialsForKerberosHasInvalidUserName|Kerberos belirteci için sağlanan NetworkCredentials geçerli bir kullanıcı adı yok.|  
|SSPIPackageNotSupported|Belirtilen SSPI paketi desteklenmiyor.|  
|TokenCancellationNotSupported|Belirtilen belirteç sağlayıcısı, belirteç iptal etmeyi desteklemiyor.|  
|UnboundPrefixInQName|İlişkisiz bir ön eki içinde belirtilen tam adı kullanılır.|  
|SAMLAuthorizationDecisionResourceRequired|'Özniteliği için belirtilen kaynak', null ya da 0 uzunluğunda olamaz.|  
|TraceCodeSecurityNegotiationProcessingFailure|Hizmet güvenliği anlaşması işleme hatası.|  
|SAMLAssertionIssuerRequired|SamlAssertion için belirtilen 'Issuer' null veya boş olamaz.|  
|UnableToCreateHashAlgorithmFromAsymmetricCrypto|Belirtilen algoritma için bir HashAlgorithm belirtilen asimetrik şifreleme oluşturulamıyor.|  
|SamlUnableToExtractSubjectKey|İçin bir SecurityToken SamlSubject içinde bulunan SecurityKeyIdentifier çözümlenemedi. SecurityTokenResolver SecurityKeyIdentifier çözümler bir SecurityToken içermelidir.|  
|ChildNodeTypeMissing|Belirtilen XML öğesi bir alt öğesinin belirtilen türe sahip değil.|  
|TraceCodeSecurityPendingServerSessionClosed|Bekleyen güvenlik oturumu sunucu tarafından kapatıldı.|  
|TraceCodeSecuritySessionCloseResponseSent|Sunucu güvenlik oturumu kapat istemciye yanıt gönderdi.|  
|TraceCodeSecurityIdentityHostNameNormalizationFailure|Bir uç nokta adresi ana bilgisayar adı kısmı normalleştirilmiş olamaz.|  
|FailAcceptSecurityContext|AcceptSecurityContext başarısız oldu.|  
|EmptyXmlElementError|Belirtilen öğe boş olamaz.|  
|PrefixNotDefinedForNamespace|Belirtilen ad alanı için bir önek, bu bağlamda tanımlı değil ve bildirilemez.|  
|SAMLAuthorizationDecisionHasMoreThanOneEvidence|Okunan özniteliği birden fazla kanıt saptandı. Buna izin verilmez.|  
|SamlTokenAuthenticatorCanOnlyProcessSamlTokens|SamlSecurityTokenAuthenticator SamlSecurityToken öğelerini yalnızca işleyebilir. Belirtilen SecurityTokenType alındı.|  
|SAMLAttributeStatementMissingAttributeOnRead|Okunan SamlAttributeStatement herhangi bir 'SamlAttribute' öğesi içermiyor. Buna izin verilmez.|  
|CouldNotFindNamespaceForPrefix|Belirtilen önek için ad alanı arama yapamazsınız.|  
|TraceCodeExportSecurityChannelBindingExit|Finished Security ExportChannelBinding.|  
|AESCryptDecryptFailed|Belirtilen verilerin şifresi çözülemedi.|  
|SAMLAttributeNamespaceAttributeRequired|'SamlAttribute için belirtilen Namespace', null ya da 0 uzunluğunda olamaz.|  
|TraceCodeSpnegoServiceNegotiationCompleted|SSPI anlaşması SpnegoTokenAuthenticator tamamlandı.|  
|TraceCodeSecurityServerSessionRenewalFaultSent|Sunucu güvenlik oturumu anahtar yenileme hatası istemciye gönderilebilir.|  
|AlgorithmMismatchForTransform|Dönüştürme algoritması üzerinde bir uyuşmazlığı oluştu.|  
|UserNameAuthenticationFailed|Belirtilen mekanizmayı kullanarak bir kullanıcı adı/parola kimlik doğrulaması başarısız oldu. Kullanıcının kimliği.|  
|SamlInvalidSigningToken|SamlAssertion göre Protokolü doğrulanmadı bir belirteç ile imzalanmış. X.509 sertifikaları kullanıyorsanız, doğrulama ifadelerinizi inceleyin.|  
|TraceCodeSecurityServerSessionKeyUpdated|Güvenlik oturum anahtarı, sunucu tarafından güncelleştirildi.|  
|TraceCodeSecurityServerSessionCloseReceived|Sunucu güvenlik oturumu istemciden Kapat bir ileti alındı.|  
|SAMLAuthenticationStatementMissingSubject|SamlAuthenticationStatement gerekli SamlSubjectStatement öğesi eksik.|  
|UnexpectedEndOfFile|Beklenmeyen dosya sonu.|  
|UnsupportedAlgorithmForCryptoOperation|Belirtilen algoritma belirtilen işlem için desteklenmiyor.|  
|XmlLangAttributeMissing|Gerekli XML: lang özniteliği eksik.|  
|TraceCodeSecurityImpersonationSuccess|Güvenlik kimliğe bürünme sunucuda başarılı oldu.|  
|SAMLAuthorityBindingMissingLocationOnRead|'Konum' özniteliği Okunan SamlAuthorityBinding eksik ya da 0 uzunluğunda.|  
|SAMLAttributeStatementMissingSubjectOnRead|SamlAttributeStatement 'SamlSubject' öğesi eksik.|  
|SAMLAuthorizationDecisionStatementMissingSubjectOnRead|Okunan SamlAuthorizationDecisionStatement 'SamlSubject' öğesi eksik.|  
|SAMLBadSchema|SamlAssertion okunurken şemasıyla uyumlu olmadığı için bu belirtilen öğe bulundu.|  
|SAMLAssertionIDIsInvalid|Belirtilen'ın 'Assertionıd'si bir SamlAssertion, bir harf veya '_' ile başlamalıdır.|  
|TraceCodeSecurityActiveServerSessionRemoved|Etkin bir güvenlik oturumu sunucu tarafından kaldırıldı.|  
|UnableToCreateKeyedHashAlgorithmFromSymmetricCrypto|Belirtilen algoritma için bir keyedHashAlgorithm belirtilen simetrik şifreleme oluşturulamıyor.|  
|SAMLAuthenticationStatementMissingAuthenticationMethod|'AuthenticationMethod SamlAuthenticationStatement için belirtilen', null ya da 0 uzunluğunda olamaz.|  
|TraceCodeSecurityImpersonationFailure|Güvenlik kimliğe bürünme sunucuda başarısız oldu.|  
|Varsayılan|(Varsayılan)|  
|UnsupportedNodeTypeInReader|Belirtilen ada sahip belirtilen düğümün türü desteklenmiyor.|
