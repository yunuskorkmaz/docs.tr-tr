---
description: 'Daha fazla bilgi edinin: IdentityModel özel durumları'
title: IdentityModel Özel Durumları
ms.date: 03/30/2017
ms.assetid: 4ef34497-8ff5-4621-b773-7731cc721231
ms.openlocfilehash: 902403d5809bd75a3b370e9b435dbefce2e97d3c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99686433"
---
# <a name="identitymodel-exceptions"></a>IdentityModel Özel Durumları

Bu konu, IdentityModel tarafından oluşturulan tüm özel durumları listeler.  
  
## <a name="exception-list"></a>Özel durum listesi  
  
|Kaynak kodu|Geçerli dize|  
|-------------------|--------------------|  
|ValueMustBeOf2Types|Bu bağımsız değişkenin değeri bu iki türden biri olmalıdır.|  
|Samlsubjectnameıdentifierrequiresnamevalue|SamlNameIdentifier için belirtilen ' name ' null ya da 0 uzunluğunda olamaz.|  
|Tracecodeıssuancetokenproviderendsecuritynegotiation|IssuanceTokenProvider güvenlik anlaşmasını tamamladı.|  
|Tracecodesecuritynewserversessionkeyyayınlandı|Sunucu tarafından yeni bir güvenlik oturumu anahtarı verildi.|  
|SAMLAttributeMissingNameAttributeOnRead|Okunan SamlAttribute için ' name ' eksik ya da 0 uzunluğunda.|  
|Unknowniccryptotype|Icryptoto uygulaması desteklenmiyor.|  
|TraceCodeSecurityTokenProviderClosed|Güvenlik belirteci sağlayıcısı kapatıldı.|  
|SAMLUnableToLoadAdvice|\<saml:advice>Öğe yüklenemedi.|  
|SAMLAuthenticationStatementMissingAuthenticationMethodOnRead|Bir Samlauthenticationdeyimin okunduğu ' AuthenticationMethod ' özniteliği eksik ya da 0 uzunluğunda.|  
|UnsupportedTransformAlgorithm|Desteklenmeyen dönüşüm veya kurallı kullanım algoritması.|  
|Samdefdiencerestrictionshouldhaveoneaudience|Bir Samdefdiencerestrictioncondition en az bir Audience (URI) içermelidir.|  
|Samlet Videnceshouldaveoneassertion|SamlEvidence, kimliğe veya başvuruya göre en az bir SamlAssertion öğesine başvurmalıdır.|  
|Samdefdiencerestrictionınvalidaudiencevalueonread|Okunan Samdefdiencerestrictioncondition, ' Audience ' öğesinde bir değer içermiyor.|  
|X509ChainBuildFail|Belirli X. 509.440 sertifika zinciri oluşturulamadı. Kullanılan sertifikanın doğrulanamayan bir güven zinciri vardır. Sertifikayı değiştirin veya certificateValidationMode değerini değiştirin.|  
|Xdcannotfindvalueındictionarystring|Belirtilen değer kimliği, sözlük dizesinde bulunamadı.|  
|TraceCodeImportSecurityChannelBindingEntry|Güvenlik ImportChannelBinding başlatılıyor.|  
|PrivateKeyExchangeNotSupported|Özel anahtar, Exchange KeySpec 'i desteklemiyor.|  
|TokenProviderUnableToGetToken|Özel belirteç sağlayıcı bir güvenlik belirteci sağlayamıyor.|  
|SAMLEntityCannotBeNullOrEmpty|Belirli SamlAssertion varlığı null veya boş olamaz.|  
|SAMLAssertionRequireOneStatement|Bir SamlAssertion en az bir ifade gerektirir. Oluşturmakta olduğunuz SamlAssertion öğesine en az bir Samldeyimin eklendiğinden emin olun.|  
|Aesinvalidınputblocksize|Giriş boyutu, belirli baytların katlarından biri olmalıdır.|  
|AESCryptAcquireContextFailed|CSP bağlamı alınamadı.|  
|SAMLAssertionRequireOneStatementOnRead|Okunan SamlAssertion hiçbir Samldeyimin içermiyordu. SamlAssertion, en az bir Samldeyimin içermelidir.|  
|Tracecodesecuritysessionclosedfaultalındı|İstemci güvenlik oturumu, sunucudan oturum kapalı hatası aldı.|  
|Tracecodeıssuancetokenproviderredirectapphesaplanır|IssuanceTokenProvider bir yeniden yönlendirme üstbilgisi uyguladı.|  
|TraceCodeSecuritySessionClosedFaultSendFailure|İstemciye bir güvenlik oturumu kapalı hatası gönderilirken bir hata oluştu.|  
|ValueMustBeZero|Bu bağımsız değişkenin değeri 0 olmalıdır.|  
|SAMLUnableToResolveSignatureKey|SamlAssertion imzasında bulunan SecurityKeyIdentifier çözümlenemedi. SamlAssertion imzası, belirli bir veren için doğrulanamıyor.|  
|X509IsNotInTrustedStore|Belirli X. 509.440 sertifikası güvenilir kişiler deposunda değil.|  
|Samtalementnottanınmış|Belirli öğe desteklenmiyor.|  
|SAMLAuthorizationDecisionStatementMissingResourceAttributeOnRead|Okunan SamlAuthorizationDecisionStatement 'ın ' Resource ' özniteliği eksik ya da 0 uzunluğunda.|  
|SamlTokenMissingSignature|SamlAssertion imzalanmadı. SamlAssertions, SigningCredentials ayarlanarak imzalanabilir.|  
|ExpectedElementMissing|Belirtilen ad alanı ile beklenen öğe eksik.|  
|Nokeyıdentifierclausefound|SecurityKeyIdentifier içinde belirli türde bir yan tümce bulunamadı.|  
|MissingPrivateKey|Özel anahtar X. 509.440 sertifikasında yok.|  
|UnexpectedEOFFromReader|XML okuyucudan beklenmeyen EOF.|  
|Unsupportedkeytürettionalgorithm|Belirli anahtar türetme algoritması desteklenmiyor.|  
|Tokenyok Notsupportkeyıdentifierclauseoluşturma|Belirli belirteç, belirli anahtar tanımlayıcı yan tümce oluşturmayı desteklemiyor.|  
|LastMessageNumberExceeded|Sıra numarası Protokolü ihlali algılandı.|  
|SymmetricKeyLengthTooShort|Belirtilen simetrik anahtar uzunluğu çok kısa.|  
|SAMLAuthorityBindingMissingAuthorityKindOnRead|Okunan SamlAuthorityBinding, eksik olan veya 0 uzunluğunda bir ' AuthorityKind ' içerdiğini buldu.  Buna izin verilmez.|  
|XmlTokenBufferIsEmpty|XmlTokenBuffer boş.|  
|Invalidxmlqualifiedname|XML nitelenmiş adı bekleniyordu, ancak geçersiz bir ad bulundu.|  
|Samlauthority, missingName|SamlAuthorityBinding içindeki ' AuthorityKind ' öğesini temsil eden XmlQualifiedName null ya da 0 uzunluğunda olamaz.|  
|AESCryptEncryptFailed|Belirli veriler şifrelenemedi.|  
|AuthorizationContextCreated|Belirtilen kimliğe sahip yetkilendirme bağlamı oluşturuldu.|  
|Samlserializerunabletoreadsecuritykeyıdentifier|SamlSerializer, SecurityKeyIdentifier 'ı okuyabilen bir SecurityTokenSerializer içermiyor. Özel bir SecurityKeyIdentifier kullanıyorsanız, özel bir SecurityTokenSerializer sağlamanız gerekir.|  
|Tracecodeıssuancetokenproviderservicetokencachefull|IssuanceTokenProvider hizmet belirteci önbelleğini azalttı.|  
|Tracecodesecuritytokenprovideraçıldı|Güvenlik belirteci sağlayıcısı açıldı.|  
|PublicKeyNotRSA|Ortak anahtar bir RSA anahtarı değil.|  
|Invalidreaderstate|Belirtilen giriş okuyucusu için belirtilen durum geçersiz.|  
|UnableToResolveReferenceUriForSignature|Özet hesaplamak için İmzadaki belirli URI çözümlenemiyor.|  
|EmptyBase64Attribute|Gerekli Base64 özniteliği adı ve ad alanı için boş bir değer bulundu.|  
|SAMLSubjectRequiresConfirmationMethodWhenConfirmationDataOrKeyInfoIsSpecified|SAML SubjectConfirmation, onay verileri veya KeyInfo belirtildiğinde bir onay yöntemi gerektirir.|  
|Samdefdiencerestrictionshouldhaveoneaudienceonread|Okunan Samdefdiencerestrictioncondition, en az bir ' Audience ' değeri içermelidir. Hiçbiri bulunamadı.|  
|TokenProviderUnableToRenewToken|Özel belirteç sağlayıcı güvenlik belirtecini yenileyemedi.|  
|AESIVLengthNotSupported|Belirli bitler IV desteklenmez. Yalnızca 128 bit IV desteklenir.|  
|SAMLAuthorityBindingMissingAuthorityKind|Bir SamlAuthorityBinding null olmayan bir ' AuthorityKind ' içermelidir.|  
|TraceCodeSecuritySessionDemuxFailure|Gelen ileti, var olan bir güvenlik oturumunun parçası değil.|  
|TokenRenewalNotSupported|Belirli belirteç sağlayıcısı belirteç yenilemeyi desteklemiyor.|  
|AtLeastOneReferenceRequired|Bir imzada en az bir başvuru gereklidir.|  
|Samltifturealreadyread|İmza, SAML onaylama işlemi içinde zaten okundu.|  
|AlgorithmAndPrivateKeyMisMatch|Belirtilen algoritma ve özel anahtar eşleşmiyor.|  
|EmptyTransformChainNotSupported|Boş dönüştürme zinciri desteklenmiyor.|  
|SspiWrapperEncryptDecryptAssert1|SSPIWrapper:: EncryptDecryptHelper&#124; ' fark ' Aralık dışında.|  
|SspiWrapperEncryptDecryptAssert2|SSPIWrapper:: EncryptDecryptHelper&#124; ' size ' Aralık dışında. Securitytokenmanagercannotcreateauthenticator Torforrequirement = güvenlik belirteci Yöneticisi, belirli bir gereksinim için bir belirteç kimlik doğrulayıcısı oluşturamıyor.|  
|UnableToCreateKeyedHashAlgorithm|Belirli bir imza algoritması için belirli bir değerden bir KeyedHashAlgorithm oluşturulamıyor.|  
|SAMLUnableToLoadAssertion|\<saml:assertion>Öğe yüklenemedi.|  
|X509FindValueMismatchMulti|Belirli X509FindType, findValue bağımsız değişkeninin türünü 2 değerden biri olmasını gerektirir. FindValue bağımsız değişkeni başka bir türde.|  
|Tracecodesecurityıdentitydeterminationsuccess|Bir EndpointAddress için kimlik belirlendi.|  
|Undefineğitiseofprefixatelement|Öğesinde kullanılan özel önek tanımlanmış bir ad alanı içermiyor.|  
|TraceCodeSecuritySessionResponderOperationFailure|Güvenlik oturumu işlemi sunucuda başarısız oldu.|  
|CannotFindCert|Özel arama ölçütleri kullanılarak X. 509.952 sertifikası bulunamıyor: StoreName, StoreLocation, FindType, FindValue.|  
|X509InvalidUsageTime|Belirli X. 509.440 sertifikası kullanım saati geçersiz. Kullanım süresi gerekli NotBefore saati ile NotAfter saati arasında değil.|  
|Tracecodesecurityıdentitydeterminationfailure|Bir EndpointAddress için kimlik belirlenemiyor.|  
|AsyncObjectAlreadyEnded|End yöntemi bu zaman uyumsuz sonuç nesnesi üzerinde zaten çağrılmış.|  
|Externaldictionarysız Notcontainallrequiredstrings|Dış sözlük tüm gerekli dizeler için tanımlar içermiyor. Belirli dize uzak sözlükte kullanılamıyor.|  
|TraceCodeSecuritySessionKeyRenewalFaultReceived|İstemci güvenlik oturumu, sunucudan bir anahtar yenileme hatası aldı.|  
|SAMLActionNameRequired|SamlAction öğesini temsil eden dize null ya da 0 uzunluğunda olamaz.|  
|Signaturedoğrulamaları Icationfailed|İmza doğrulaması başarısız oldu.|  
|TraceCodeSecurityContextTokenCacheFull|SecurityContextSecurityToken önbelleği dolu.|  
|SAMLAssertionMissingMajorVersionAttributeOnRead|Okunan SamlAssertion için MajorVersion, eksik ya da 0 uzunluğunda.|  
|SamlAttributeClaimRightShouldBePossessProperty|Bu SamlAttribute Oluşturucusu, talebin sağ öğesinin System. IdentityModel. Claim. Rights. PossessProperty değerine sahip olmasını gerektirir.|  
|AuthorizationPolicyEvaluated|Belirli kimliğe sahip ilke değerlendirilir.|  
|SAMLUnableToLoadCondtions<!-- the misspelling here is deliberate. -->|\<saml:conditions>Öğe yüklenemedi.|  
|AESKeyLengthNotSupported|Belirli bit anahtarı desteklenmiyor. Yalnızca 128, 192 ve 256 bit anahtarı desteklenir.|  
|UserNameCannotBeEmpty|Kullanıcı adı boş olamaz.|  
|AlgorithmAndPublicKeyMisMatch|Belirtilen algoritma ve ortak anahtar eşleşmiyor.|  
|SAMLUnableToLoadCondtion<!-- the misspelling here is deliberate. -->|\<saml:conditions>Öğe yüklenemedi.|  
|SamlAssertionMissingSigningCredentials|SigningCredentials, SamlAssertion üzerinde ayarlanmamış. SamlAssertions, lütfen devam etmek için SamlAssertion üzerinde geçerli bir SigningCredentials ayarlayın.|  
|Sspipayloadnotşifrelenmiştir|İkili veriler SSPI güvenlik içeriğiyle şifrelenmedi.|  
|SAMLAuthorizationDecisionShouldHaveOneActionOnRead|Okunan SamlAuthorizationDecisionStatement, herhangi bir SamlAction içermiyor.|  
|TraceCodeSecurityBindingSecureOutgoingMessageFailure|Güvenlik protokolü giden iletiyi güvenli hale alamaz.|  
|UndefinedUseOfPrefixAtAttribute|Belirli öznitelikte kullanılan özel önek tanımlanmış bir ad alanına sahip değil.|  
|Noinputissetforkurallaştırma|Kurallı çıkışı yazmak için ayarlanmış bir giriş yok.|  
|TraceCodeSecurityPendingServerSessionAdded|Sunucuya bekleyen bir güvenlik oturumu eklenir.|  
|AsyncCallbackException|Bir AsyncCallback özel durum oluşturdu.|  
|PrivateKeyNotRSA|Özel anahtar bir RSA anahtarı değil.|  
|Tracecodesecurityclientsessionkeyyeniledi|İstemci güvenlik oturumu, oturum anahtarını yeniledi.|  
|SAMLAuthorizationDecisionStatementMissingDecisionAttributeOnRead|Okunan SamlAuthorizationDecisionStatement için ' karar ' eksik ya da 0 uzunluğunda.|  
|SAMLAttributeNameAttributeRequired|SamlAttribute için belirtilen ' name ' null ya da 0 uzunluğunda olamaz.|  
|Samlserializerrequiresexternalserileştiriciler|SamlSerializer, belirteçte bulunan SecurityKeyIdentifier seri hale getirmek için bir SecurityTokenSerializer gerektirir.|  
|UnableToResolveKeyReference|Belirteç çözümleyici, belirli güvenlik anahtarı başvurusunu çözümleyemiyor.|  
|UnsupportedKeyWrapAlgorithm|Belirli anahtar kaydırması algoritması desteklenmiyor.|  
|SAMLAssertionMissingIssuerAttributeOnRead|Okunan SamlAssertion için ' Issuer ' eksik ya da 0 uzunluğunda.|  
|Tracecodeıssuancetokenproviderusingcachedtoken|IssuanceTokenProvider önbelleğe alınmış hizmet belirtecini kullandı.|  
|AESCryptGetKeyParamFailed|Belirli anahtar parametresi alınamadı.|  
|Invalidnamespaceforemptypredüzeltmesini|Ad alanı boş önek için geçersiz.|  
|Aesciphermonominal Tsupported|Belirli şifreleme modu desteklenmiyor. Yalnızca CBC desteklenir.|  
|ArgumentCannotBeEmptyString|Bağımsız değişken boş olmayan bir dize olmalıdır.|  
|SAMLAssertionMissingMinorVersionAttributeOnRead|Okunan SamlAssertion için MinorVersion değeri eksik ya da 0 uzunluğunda.|  
|SpecifiedStringNotAvailableInDictionary|Belirtilen dize geçerli sözlükte bir giriş değil.|  
|KerberosApReqInvalidOrOutOfMemory|AP-REQ geçersiz veya sistem yeterli belleğe sahip değil.|  
|FailLogonUser|LogonUser, belirtilen kullanıcı için başarısız oldu. Kullanıcının geçerli bir Windows hesabı olduğundan emin olun.|  
|ValueMustBeNonNegative|Bu bağımsız değişkenin değeri negatif olmayan bir değer olmalıdır.|  
|X509ValidationFail|Belirtilen X. 509.440 sertifikası doğrulaması başarısız oldu.|  
|Tracecodesecuritysessionrequestoroperationbaşarılı|Güvenlik oturumu işlemi istemcide başarıyla tamamlandı.|  
|SAMLActionNameRequiredOnRead|SamlAction için okunan dize yok ya da 0 uzunluğunda.|  
|KerberosMultilegsNotSupported|Kimlik, UPN olarak belirtilir. Bir kullanıcı hesabı altında çalışan bir hizmetin kimlik doğrulaması, desteklenmeyen Kerberos çoklu tarafı gerektirir.|  
|SAMLAssertionIdRequired|Bir SamlAssertion için ' AssertionId 'si ' null veya boş olamaz.|  
|InvalidOperationForWriterState|Belirtilen işlem belirtilen XmlWriter durumunda geçersiz.|  
|CannotValidateSecurityTokenType|Belirtilen güvenlik belirteci kimlik doğrulayıcısı belirtilen türün bir belirtecini doğrulayamıyor.|  
|X509FindValueMismatch|Belirtilen X509FindType, findValue bağımsız değişkeninin türünü belirtilen değer olarak gerektiriyor. FindValue bağımsız değişkeni başka bir türde.|  
|TraceCodeSecurityClientSessionCloseSent|İstemci güvenlik oturumu tarafından bir kapatma iletisi gönderildi.|  
|Suitelicnotacceptalgorithd|Belirtilen algoritma paketi tarafından belirtilen işlem için belirtilen algoritma kabul edilmedi|  
|Tracecodesecuritysessionrequestoroperationhatası|İstemci güvenlik oturumu işlemi başarısız oldu.|  
|Samlunabletoloaddeyimin|Bir Samldeyimin yüklemesi başarısız oldu.|  
|Innerreadermusde TElement|İç okuyucu, öğesinde olmalıdır.|  
|UnableToCreateTokenReference|Güvenlik belirteci başvurusu oluşturulamıyor.|  
|Tracecodesecuritybindingıncomingmessagedoğrulandı|Güvenlik protokolü gelen iletiyi doğruladı.|  
|Objectıreadonly|Nesne salt okunurdur.|  
|Tracecodesecurityclientsessionpreviouskeyatılan|İstemci güvenlik oturumu önceki oturum anahtarını iptal etti.|  
|Samltokentimegeçersiz|SamlToken zaman geçerli değil. Geçerli saat, belirtecin etkin ve sona erme saatinin dışındadır.|  
|Tracecodesecurityıdentitydoğrulamaları Icationsuccess|Kimlik doğrulaması başarılı.|  
|SigningTokenHasNoKeys|Belirtilen imzalama belirtecinin anahtarı yok.|  
|Tracecodesecurityıdentitydoğrulamaları Icationfailure|Kimlik doğrulama başarısız oldu.|  
|Aescryptımportkeyfailed|Anahtar malzemesi içe aktarılamadı.|  
|Failınitializesecuritycontext|InitializeSecurityContent başarısız oldu. Hizmet sorumlusu adının doğru olduğundan emin olun.|  
|Tracecodestreamsecurityupgradekabul edildi|Akış güvenlik yükseltmesi başarıyla kabul edildi.|  
|SAMLAuthorityBindingRequiresLocation|SamlAuthorityBinding üzerinde belirtilen ' Location ' özniteliği null ya da 0 uzunluğunda olamaz.|  
|PublicKeyNotDSA|Ortak anahtar bir DSA anahtarı değil.|  
|Impersonationlevelnotsupported|Kerberos kullanan kimlik doğrulama modları belirtilen kimliğe bürünme düzeyini desteklemez. Geçerli bir kimlik veya kimliğe bürünme düzeyi belirtin.|  
|RequiredTargetNotSigned|Belirtilen kimliğe sahip öğe imzalanabilmesi, ancak yoktu.|  
|Samlauthenticationstatementmissingauthenticationınstanceonread|Bir Samlauthenticationdeyimin okunduğu ' AuthenticationInstant ' özniteliği eksik ya da 0 uzunluğunda.|  
|Samlet Videnceshouldaveoneassertiononread|Okunan SamlEvidence, ya da gömülü bir SamlAssertion başvurusu içermiyordu.|  
|LengthOfArrayToConvertMustGreaterThanZero|Tamsayıya dönüştürülecek dizinin uzunluğu 0 ' dan büyük olmalıdır.|  
|Invalidasyncresult|Geçersiz AsyncResult.|  
|Tracecodeıssuancetokenproviderremovedcachedtoken|IssuanceTokenProvider, süre dolma hizmet belirtecini kaldırdı.|  
|IncorrectUserNameFormat|Kullanıcı adı geçersiz bir biçimde. Kullanıcı adı biçimi "Kullanıcı adı" veya ' etki alanı \\ \ KullanıcıAdı ' biçiminde olmalıdır.|  
|TraceCodeExportSecurityChannelBindingEntry|Güvenlik ExportChannelBinding başlatılıyor.|  
|Unsupportedınputtypefortransform|Belirtilen giriş türü dönüştürme için desteklenmiyor.|  
|Cannotfindbelgekökü|Belgenin kökü bulunamıyor.|  
|Xmlbufferquotaaşıldı|XML içeriğini arabelleğe almak için gereken boyut, arabellek kotasını aştı.|  
|TraceCodeSecuritySessionClosedResponseSendFailure|İstemciye bir güvenlik oturumu kapatma yanıtı gönderilirken bir hata oluştu.|  
|Unabletoresolvereferenceınsamlsignature|SAML imzasında, AssertionId 'si ile belirtilen başvuru çözümlenemiyor.|  
|SAMLSubjectRequiresNameIdentifierOrConfirmationMethod|Bir SamlSubject, ' NameIdentifier ' veya ' ConfirmationMethod ' belirtilmesini gerektirir. İkisi de eksikti.|  
|SAMLAttributeMissingNamespaceAttributeOnRead|Okunan SamlAttribute için ' namespace ' eksik ya da 0 uzunluğunda.|  
|SAMLSubjectConfirmationClauseMissingConfirmationMethodOnRead|Okunan SamlSubjectConfirmation üzerinde bir ' ConfirmationMethod ' bulunamadı.|  
|Securitytokenrequirementhasınvalidtypeforproperty|Belirteç gereksiniminin belirtilen özellik için beklenmeyen bir türü vardır. Beklenen özellik türü başka bir değer.|  
|TraceCodeNegotiationTokenProviderAttached|NegotiationTokenProvider eklendi.|  
|TraceCodeSpnegoClientNegotiationCompleted|SpnegoTokenProvider SSPI anlaşması tamamlandı.|  
|SAMLUnableToLoadUnknownElement|Seçili SamlSerializer, bu öğenin serisini kaldıramıyor. Özel öğelerin serisini kaldırmak için lütfen özel bir SamlSerializer kaydettirin.|  
|CreateSequenceRefused|Sıra oluşturma isteği, RM hedefi tarafından reddedildi.|  
|Tracecodesecuritysessionredirectapphesaplanır|İstemci güvenlik oturumu yeniden yönlendirildi.|  
|Securitytokengereksinimyok Notcontainproperty|Belirteç gereksinimi, belirtilen özelliği içermiyor.|  
|SAMLAttributeValueCannotBeNull|SamlAttribute içinde bulunan attributeValues değerlerinden biri null değer olacak şekilde bulundu. SamlAttribute oluşturulurken listelerin null olmadığından emin olun.|  
|ValueMustBeGreaterThanZero|Bu bağımsız değişkenin değeri 0 ' dan büyük olmalıdır.|  
|TraceCodeNegotiationAuthenticatorAttached|NegotiationTokenAuthenticator eklendi.|  
|ValueMustBePositive||  
|SAMLAuthorizationDecisionShouldHaveOneAction|Bir SamlAuthorizationDecisionStatement en az bir SamlAction içermelidir.|  
|Tracecodesecuritytokendoğrulayıcısı Torclosed|Güvenlik belirteci kimlik doğrulayıcısı kapatıldı.|  
|TraceCodeSecurityAuditWrittenSuccess|Güvenlik denetim günlüğü başarıyla yazıldı.|  
|PrivateKeyNotDSA|Özel anahtar bir DSA anahtarı değil.|  
|MessageNumberRollover|Bu sıranın en büyük sıra numarası aşıldı.|  
|Aesdoldurma Ingmonominal Tsupported|Belirtilen doldurma modu desteklenmiyor. Yalnızca PKCS7 ve ISO10126 desteklenir.|  
|SAMLSubjectRequiresNameIdentifierOrConfirmationMethodOnRead|Okunan SamlSubject için gereken ' NameIdentifier ' ve ' ConfirmationMethod ' öğeleri bulunamadı.|  
|TraceCodeSecurityAuditWrittenFailure|Güvenlik denetim günlüğüne yazılırken bir hata oluştu.|  
|UnsupportedCryptoAlgorithm|Belirtilen şifreleme algoritması bu bağlamda desteklenmiyor.|  
|SigningTokenHasNoKeysSupportingTheAlgorithmSuite|İmza belirtecinin, belirtilen algoritma paketini destekleyen bir anahtarı yok.|  
|Samlnameıdentifiermissingidentifiervalueonread|Okunan SamlNameIdentifier için ' Identifier ' dizesi eksik.|  
|SAMLSubjectStatementRequiresSubject|SAML Subject bildiriminde bir SAML konusunun belirtilmesi gerekir.|  
|TraceCodeSslClientCertMissing yok|Uzak SSL istemcisi gerekli bir sertifikayı sağlamadı.|  
|SAMLTokenVersionNotSupported|Belirtilen ana sürüm ve ikincil sürüm desteklenmiyor.|  
|TraceCodeConfigurationIsReadOnly|Yapılandırma salt okunurdur.|  
|TraceCodeSecuritySessionRenewFaultSendFailure|İstemciye güvenlik oturumu anahtarı üzerinde bir yenileme hatası gönderilirken bir hata oluştu.|  
|Tracecodesecurityınactivesessionhata|Etkin olmayan bir güvenlik oturumu sunucu tarafından hata verdi.|  
|SAMLUnableToLoadAttribute|SamlAttribute yüklenemedi.|  
|Psha1KeyLengthInvalid|Belirtilen PSHA1 anahtar uzunluğu geçersiz.|  
|Keyıdentifiercannotcreatekey|Bu SecurityKeyIdentifier, anahtar oluşturabileceğiniz herhangi bir yan tümce içermiyor.|  
|X509IsInUntrustedStore|Belirtilen X. 509.440 sertifikası güvenilmeyen bir sertifika deposunda.|  
|UnexpectedXmlChildNode|Belirtilen öğenin belirtilen XML alt düğümü belirtilen öğe için beklenmiyordu.|  
|Tokenlannotmeeting Keysizerequirements|Belirtilen algoritma paketi için anahtar boyutu gereksinimleri belirtilen belirteç tarafından karşılanmadı.|  
|TraceCodeSecuritySessionRequestorStartOperation|İstemcide bir güvenlik oturumu işlemi başlatıldı.|  
|Invalidhexstring|Geçersiz onaltılı dize biçimi.|  
|Samlattributeclaimresourceshouldkirstring|Bu SamlAttribute Oluşturucu, talep kaynağının ' String ' türünde olmasını gerektirir.|  
|SamlSigningTokenNotFound|SamlAssertion imzalı, ancak SamlAssertion 'ı imzalayan belirteç bulunamıyor. SecurityTokenResolver 'ın SamlAssertion 'yi imzalayan belirteci içerdiğinden emin olun.|  
|TraceCodeSecuritySpnToSidMappingFailure|ServicePrincipalName, bir SecurityIdentifier ile eşlenemedi.|  
|UnableToCreateSignatureFormatterFromAsymmetricCrypto|Belirtilen asimetrik şifre içinden belirtilen algoritma için imza biçimlendiricisi oluşturulamıyor.|  
|TraceCodeSecurityServerSessionClosedFaultSent|Sunucu güvenlik oturumu, istemciye bir oturum kapatma hatası gönderdi.|  
|UnableToFindPrefix|Belirtilen öğede belirtilen ı, kullanılan ön ek için önek bulunamıyor.|  
|Tracecodesecuritytokendoğrukimliği|Güvenlik belirteci kimlik doğrulayıcısı açıldı.|  
|RequiredAttributeMissing yok|Belirtilen öğe üzerinde belirtilen öznitelik gereklidir.|  
|LocalIdCannotBeEmpty|LocalId boş olamaz. Geçerli bir ' LocalId ' belirtin.|  
|ValueMustBeInRange|Bu bağımsız değişkenin değeri, belirtilen Aralık içinde olmalıdır.|  
|Tracecodeıssuancetokenproviderbeginsecuritynegotiation|IssuanceTokenProvider yeni bir güvenlik anlaşması başlattı.|  
|Invalidntmapping|Belirtilen X. 509.440 sertifikası bir Windows hesabıyla eşlenemez. UPN konu diğer adı gereklidir.|  
|AESCryptSetKeyParamFailed|Belirtilen anahtar parametresi ayarlanamadı.|  
|TraceCodeSecuritySessionClosedResponseReceived|İstemci güvenlik oturumu sunucudan kapalı bir yanıt aldı.|  
|UnableToCreateSignatureDeformatterFromAsymmetricCrypto|Belirtilen asimetrik şifre içinden belirtilen algoritma için bir imza yok biçimlendiricisi oluşturulamıyor.|  
|Tracecodeıdentitymodelasynccallbackthrewexception|Zaman uyumsuz bir geri çağırma özel durum oluşturdu.|  
|Lengthmustbegreatermi sıfır|Bu bağımsız değişkenin uzunluğu 0 ' dan büyük olmalıdır.|  
|Buluna bulunan Çoğulcert|Belirtilen arama ölçütleri kullanılarak birden çok X. 509.952 sertifikası bulundu: StoreName, StoreLocation, FindType, FindValue. Daha belirli bir bulma değeri sağlayın.|  
|Attaastonetransformrequired|Transforms öğesi en az bir dönüşüm içermelidir.|  
|Samltokennotserileştirilmiş|SamlAssertion, XML olarak seri hale getirilemedi. Ayrıntılar için lütfen iç özel duruma bakın.|  
|Tracecodesecuritybindingoutgoingmessagegüvenceye al|Güvenlik protokolü giden iletiyi güvenli hale getirdi.|  
|Keyıdentifierclausealnotsupportkeyoluşturma|Bu SecurityKeyIdentifierClause anahtar oluşturmayı desteklemiyor.|  
|UnableToResolveTokenReference|Belirteç çözümleyici, belirtilen belirteç başvurusunu çözümleyemiyor.|  
|UnsupportedEncryptionAlgorithm|Belirtilen şifreleme algoritması desteklenmiyor.|  
|Samlserializerunabletowritesecuritykeyıdentifier|SamlSerializer, verilen SecurityKeyIdentifier 'ı seri hale getirmek özellikli bir SecurityTokenSerializer içermiyor. Özel bir SecurityKeyIdentifier kullanıyorsanız, özel bir SecurityTokenSerializer sağlamanız gerekir.|  
|SAMLAttributeShouldHaveOneValue|Öznitelik değeri bulunamadı. SamlAttribute özniteliği en az bir öznitelik değerine sahip olmalıdır.|  
|Tracecodesecuritybindingdoğrulamaları ıncomingmessagefailure|Güvenlik protokolü gelen iletiyi doğrulayamaz.|  
|SamlSigningTokenMissing|SamlSecurityTokenAuthenticator 'e geçirilen SamlAssertion bir imzalama belirteci içermiyor.|  
|NoPrivateKeyAvailable|Özel anahtar yok.|  
|ValueMustBeOne|Bu bağımsız değişkenin değeri 1 olmalıdır.|  
|TraceCodeSecurityPendingServerSessionRemoved|Bekleyen bir güvenlik oturumu sunucu tarafından etkin yapıldı.|  
|Tracecodeımportsecuritychannelbindingexit|Güvenlik ImportChannelBinding tamamlandı.|  
|X509CertStoreLocationNotValid|StoreLocation, LocalMachine ya da CurrentUser olmalıdır.|  
|SettingdMayBeModifiedOnlyWhenTheWriterIsInStartState|Yazıcı ayarları yalnızca yazıcı başlangıç durumunda olduğunda değiştirilebilir.|  
|ArgumentInvalidCertificate|Sertifika geçersiz.|  
|DigestVerificationFailedForReference|Belirtilen başvuru için Özet doğrulaması başarısız oldu.|  
|SAMLAuthorityBindingRequiresBinding|SamlAuthorityBinding üzerinde belirtilen ' Binding ' özniteliği null ya da 0 uzunluğunda olamaz.|  
|AESInsufficientOutputBuffer|Çıkış arabelleğinin belirtilen bayttan büyük olması gerekir.|  
|SAMLAuthorityBindingMissingBindingOnRead|Okunan SamlAuthorityBinding ' Binding ' özniteliği eksik ya da 0 uzunluğunda.|  
|Samlauthoritybindingınvalidauthoritykind|Okunan SamlAuthorityBinding geçersiz bir AuthorityKind 'e sahip. AuthorityKind biçimi QName olmalıdır.|  
|ProvidedNetworkCredentialsForKerberosHasInvalidUserName|Kerberos belirteci için belirtilen NetworkCredentials geçerli bir kullanıcı adına sahip değil.|  
|SSPIPackageNotSupported|Belirtilen SSPI paketi desteklenmiyor.|  
|TokenCancellationNotSupported|Belirtilen belirteç sağlayıcısı belirteç iptalini desteklemiyor.|  
|UnboundPrefixInQName|Belirtilen nitelenmiş adda ilişkisiz bir ön ek kullanılıyor.|  
|SAMLAuthorizationDecisionResourceRequired|SamlAuthorizationDecisionStatement için belirtilen ' Resource ' değeri null ya da 0 uzunluğunda olamaz.|  
|TraceCodeSecurityNegotiationProcessingFailure|Hizmet güvenliği anlaşması işleme hatası.|  
|SAMLAssertionIssuerRequired|SamlAssertion için belirtilen ' Issuer ' değeri null veya boş olamaz.|  
|UnableToCreateHashAlgorithmFromAsymmetricCrypto|Belirtilen asimetrik şifre içinden belirtilen algoritma için bir HashAlgorithm oluşturulamıyor.|  
|SamlUnableToExtractSubjectKey|SamlSubject 'te bulunan SecurityKeyIdentifier bir SecurityToken olarak çözümlenemiyor. SecurityTokenResolver, SecurityKeyIdentifier 'ın çözümlediği bir SecurityToken içermelidir.|  
|ChildNodeTypeMissing|Belirtilen XML öğesi belirtilen türde bir alt öğeye sahip değil.|  
|TraceCodeSecurityPendingServerSessionClosed|Bekleyen güvenlik oturumu sunucu tarafından kapatıldı.|  
|TraceCodeSecuritySessionCloseResponseSent|Sunucu güvenlik oturumu istemciye bir kapatma yanıtı gönderdi.|  
|Tracecodesecurityıdentityhostsüs Ormalizationfailure|Bir uç nokta adresinin konak adı bölümü normalleştirilemez.|  
|FailAcceptSecurityContext|AcceptSecurityContext başarısız oldu.|  
|Emptyxmtalementerror|Belirtilen öğe boş olamaz.|  
|PrefixNotDefinedForNamespace|Belirtilen ad alanı için bir ön ek, bu bağlamda tanımlı değil ve bildirilemez.|  
|Samlauthorizationdecisionhaste, Onekanıt|Okunan SamlAuthorizationDecisionStatement 'ın birden fazla kanıt içerdiği bulundu. Buna izin verilmez.|  
|SamlTokenAuthenticatorCanOnlyProcessSamlTokens|SamlSecurityTokenAuthenticator yalnızca SamlSecurityToken işlemlerini işleyebilir. Belirtilen SecurityTokenType alındı.|  
|SAMLAttributeStatementMissingAttributeOnRead|Okunan Samlattributedeyim, herhangi bir ' SamlAttribute ' öğesi içermiyor. Buna izin verilmez.|  
|Hayır Dnotfindnamespaceforprefix|Belirtilen önek için ad alanı arama yapılamıyor.|  
|TraceCodeExportSecurityChannelBindingExit|Güvenlik ExportChannelBinding tamamlandı.|  
|AESCryptDecryptFailed|Belirtilen verilerin şifresi çözülemedi.|  
|SAMLAttributeNamespaceAttributeRequired|SamlAttribute için belirtilen ' namespace ' null ya da 0 uzunluğunda olamaz.|  
|TraceCodeSpnegoServiceNegotiationCompleted|SpnegoTokenAuthenticator SSPI anlaşması tamamlandı.|  
|TraceCodeSecurityServerSessionRenewalFaultSent|Sunucu güvenlik oturumu istemciye bir anahtar yenileme hatası gönderdi.|  
|AlgorithmMismatchForTransform|Dönüştürme algoritmasında uyuşmazlık oluştu.|  
|UserNameAuthenticationFailed|Belirtilen mekanizmayı kullanarak bir Kullanıcı adı/parola doğrulaması başarısız oldu. Kullanıcının kimliği doğrulanmadı.|  
|SamlInvalidSigningToken|SamlAssertion, protokole göre doğrulanmamış bir belirteç ile imzalandı. X. 509.440 sertifikaları kullanıyorsanız, doğrulama semantiğini inceleyin.|  
|TraceCodeSecurityServerSessionKeyUpdated|Güvenlik oturumu anahtarı sunucu tarafından güncelleştirildi.|  
|Tracecodesecurityserversessioncloserecıor|Sunucu güvenlik oturumu istemciden bir kapatma iletisi aldı.|  
|SAMLAuthenticationStatementMissingSubject|Samlauthenticationdeyimin gerekli Samlsubjectdeyimin eksik olması.|  
|UnexpectedEndOfFile|Beklenmeyen dosya sonu.|  
|UnsupportedAlgorithmForCryptoOperation|Belirtilen algoritma belirtilen işlem için desteklenmiyor.|  
|XmlLangAttributeMissing yok|Gerekli xml: lang özniteliği eksik.|  
|Tracecodesecurityımpersonationsuccess|Güvenlik kimliğe bürünme sunucuda başarılı oldu.|  
|SAMLAuthorityBindingMissingLocationOnRead|Okunan SamlAuthorityBinding ' Location ' özniteliği eksik ya da 0 uzunluğunda.|  
|SAMLAttributeStatementMissingSubjectOnRead|Samlattributedeyimin ' SamlSubject ' öğesi eksik.|  
|SAMLAuthorizationDecisionStatementMissingSubjectOnRead|Okunan SamlAuthorizationDecisionStatement ' SamlSubject ' öğesi eksik.|  
|SAMLBadSchema|Bir SamlAssertion okunurken belirtilen öğe şemayla uyumlu değil bulundu.|  
|SAMLAssertionIDIsInvalid|Bir SamlAssertion için belirtilen ' AssertionId 'si ' bir harfle veya ' _ ' ile başlamalıdır.|  
|TraceCodeSecurityActiveServerSessionRemoved|Etkin bir güvenlik oturumu sunucu tarafından kaldırıldı.|  
|UnableToCreateKeyedHashAlgorithmFromSymmetricCrypto|Belirtilen simetrik şifre içinden belirtilen algoritma için bir keyedHashAlgorithm oluşturulamıyor.|  
|SAMLAuthenticationStatementMissingAuthenticationMethod|Bir Samlauthenticationdeyimin belirtilen ' AuthenticationMethod ' değeri null ya da 0 uzunluğunda olamaz.|  
|Tracecodesecurityımpersonationfailure|Güvenlik kimliğe bürünme sunucuda başarısız oldu.|  
|Varsayılan|(Varsayılan)|  
|Unsupportednodetypeınreader|Belirtilen ada sahip belirtilen düğüm türü desteklenmiyor.|
