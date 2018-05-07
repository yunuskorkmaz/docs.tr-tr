---
title: Hizmet Çerçevesi
ms.date: 03/30/2017
ms.assetid: 75f60b87-f80e-4377-ba7c-8e6becaa2b28
ms.openlocfilehash: 859e718a56ab63c8e012e1851c0730f53cb707be
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="service-framework"></a>Hizmet Çerçevesi
Bu konu hizmet çerçevesi verileri tarafından oluşturulan tüm özel durumları listeler.  
  
## <a name="exception-list"></a>Özel durum listesi  
  
|Kaynak kodu|Kaynak dizesi|  
|-------------------|---------------------|  
|ABindingInstanceHasAlreadyBeenAssociatedTo1|Bir bağlama örneği, belirtilen Tekdüzen Kaynak Tanımlayıcısı dinlemek için zaten ilişkilendirilmiş. İki uç nokta aynı ListenUniform kaynak göstergesi paylaşmak istiyorsanız da aynı bağlama nesnesi örneğini paylaşması gerekir. İki çakışan uç nokta AddServiceEndpoint() çağrılarında bir yapılandırma dosyası ya da AddServiceEndpoint() ve yapılandırma birleşimi belirtilmiş.|  
|AChannelServiceEndpointIsNull0|Bir kanal ya da hizmet uç noktası null şeklindedir.|  
|AChannelServiceEndpointSContractSNameIsNull0|Bir kanal/hizmet uç noktası sözleşme adı null veya boş olamaz.|  
|AChannelServiceEndpointSContractSNamespace0|Bir kanal/hizmet uç noktası sözleşmesi ad null şeklindedir.|  
|BaseAddressCannotHaveFragment|Temel adres Tekdüzen Kaynak Tanımlayıcısı parça içeremez.|  
|BaseAddressCannotHaveQuery|Temel adres Tekdüzen Kaynak Tanımlayıcısı sorgu dizesi içeremez.|  
|BaseAddressCannotHaveUserInfo|Temel adres Tekdüzen Kaynak Tanımlayıcısı kullanıcı bilgileri bölümüne içeremez.|  
|BaseAddressDuplicateScheme|Bu koleksiyon zaten belirtilen düzenine sahip bir adres içeriyor. Yalnızca tek bir adres, bu koleksiyondaki her şeması için izin verilir.|  
|BaseAddressMustBeAbsolute|Yalnızca bir mutlak Tekdüzen Kaynak Tanımlayıcısı taban adresi olarak kullanılabilir.|  
|BindingDoesnTSupportAnyChannelTypes1|Belirtilen bağlama herhangi bir kanal türü oluşturmayı desteklemiyor. Özel bağlama bağlama öğeleri yanlış Yığılmış veya yanlış sırada. Bir taşıma altındaki yığını için gereklidir. Bağlama öğeleri için önerilen sıra: TransactionFlow, ReliableSession, güvenlik, CompositeDuplex, OneWay, StreamSecurity, MessageEncoding, taşıma.|  
|BindingDoesnTSupportDuplexButContractRequires1|Çift yönlü sözleşme gerektirir. Belirtilen bağlama bunu desteklemiyorsa veya desteklemek için düzgün yapılandırılmamış.|  
|BindingDoesnTSupportOneWayButContractRequires1|Sözleşme OneWay gerektirir. Belirtilen bağlama bunu desteklemiyorsa veya desteklemek için düzgün yapılandırılmamış.|  
|BindingDoesnTSupportRequestReplyButContract1|Sözleşme istek/yanıt gerektirir. Belirtilen bağlama bunu desteklemiyorsa veya desteklemek için düzgün yapılandırılmamış.|  
|BindingDoesnTSupportSessionButContractRequires1|Sözleşme oturum gerektirir.  Belirtilen bağlama bunu desteklemiyorsa veya desteklemek için düzgün yapılandırılmamış.|  
|BindingDoesnTSupportTwoWayButContractRequires1|Sözleşme gerektiren iki yönlü (istek-yanıt ya da çift yönlü). Belirtilen bağlama bunu desteklemiyorsa veya desteklemek için düzgün yapılandırılmamış.|  
|BindingRequirementsAttributeDisallowsQueuedDelivery1|DeliveryRequirementsAttribute QueuedDelivery izin vermiyor. Belirtilen sözleşmesi olan bitiş noktası için bağlama bunu destekler.|  
|BindingRequirementsAttributeRequiresQueuedDelivery1|DeliveryRequirementsAttribute QueuedDelivery gerektirir. Belirtilen sözleşmesi olan bitiş noktası için bağlama bunu desteklemiyorsa veya desteklemek için düzgün yapılandırılmamış.|  
|channelDoesNotHaveADuplexSession0|Geçerli kanal çıktı oturumunu kapatmayı desteklemez. Bu kanal ISessionChannel uygulamıyor\<IDuplexSession >.|  
|ClientRuntimeRequiresFormatter0|SerializeRequest ve DeserializeReply değerlerinin her ikisini de olmadığından belirtilen ClientOperation bir biçimlendirici gerektirir false.|  
|CommunicationObjectAborted1|Durmuş olduğu için belirtilen iletişim nesnesi iletişimi için kullanılamaz.|  
|CommunicationObjectAbortedStack2|Durmuş olduğu için belirtilen iletişim nesnesi iletişimi için kullanılamaz: {1}|  
|CommunicationObjectBaseClassMethodNotCalled|Belirtilen iletişim nesnesi sanal işlevi geçersiz kılınmış {1} ancak taban sınıf içinde tanımlanan sürümü çağırmaz.|  
|ContractIsNotSelfConsistentItHasOneOrMore2|Belirtilen sözleşme bir veya daha fazla IsTerminating ya da IsInitiating olmayan işlemler vardır. SessionMode.Required için ayarlanan SessionMode özelliği yok. IsInitiating ve IsTerminating öznitelikleri yalnızca oturum bağlamında kullanılabilir.|  
|CouldnTCreateChannelForChannelType2|Belirtilen kanal türü istendi, ancak belirtilen bağlama bunu desteklemiyorsa veya desteklemek için düzgün yapılandırılmamış.|  
|DispatchRuntimeRequiresFormatter0|DeserializeRequest ve SerializeReply değerlerinin her ikisini de olmadığından belirtilen DispatchOperation bir biçimlendirici gerektirir false.|  
|EndMethodsCannotBeDecoratedWithOperationContractAttribute|End yöntemi OperationContractAttribute ile IAsyncResult tasarım deseni kullanılırken kullanılamaz. Yalnızca ilgili Begin yöntemi OperationContractAttribute ile kullanılabilir. Bu öznitelik yöntemleri Begin-End çifti için geçerlidir.|  
|EndpointListenerRequirementsCannotBeMetBy3|Sözleşme bu belirtilen kanal türlerinden biri için destek gerektirdiğinden IChannelListener öğesini belirtilen bağlama tarafından ChannelDispatcher gereksinimlerin karşılanması olamaz. Ancak bağlama yalnızca bu belirtilen kanal türlerini destekler.|  
|EndpointsMustHaveAValidBinding0|Uç noktaları geçerli bir bağlaması olması gerekir.|  
|InvalidOrUnrecognizedAction|İleti belirtilen eylemi geçersiz olduğu için işlenen veya tanınmıyor.|  
|MultipleMebesInParameters|BindingContext BindingParameters içinde birden fazla MessageEncodingBindingElement bulundu. CustomBinding birden çok MessageEncodingBindingElements sahip olamaz. Tüm bu öğeleri kaldırın.|  
|MultipleStreamUpgradeProvidersInParameters|Birden fazla IStreamUpgradeProviderElement BindingContext BindingParameters içinde bulunamadı. CustomBinding birden fazla IStreamUpgradeProviderElements sahip olamaz. Tüm bu öğeleri kaldırın.|  
|NoChannelBuilderAvailable|Bağlama, bir TransportBindingElement olmadığı için bir kanal fabrikası veya kanal dinleyicisi oluşturmak için kullanılamaz. Her bağlama TransportBindingElement öğesinden alınan en az bir bağlama öğesi olması gerekir.|  
|NotAllBindingElementsBuilt|Bu bağlama bağlama öğeleri bazıları, kanal fabrikası ve kanal dinleyicisi oluştururken kullanılmadı. Bağlama öğeleri doğru sıralanmaz. Bağlama öğeleri için önerilen sıra: TransactionFlow, ReliableSession, güvenlik, CompositeDuplex, OneWay, StreamSecurity, MessageEncoding, taşıma.  TransportBindingElement son olması gerektiğini unutmayın. Belirtilen bağlama öğeleri yerleşik değil.|  
|RuntimeRequiresInvoker0|Gönderme işlemi çağırıcısı gerektirir.|  
|ServiceHasZeroAppEndpoints|Belirtilen hizmet hiçbir uygulama (altyapı olmayan) uç noktası vardır. Bu, uygulamanız için herhangi bir yapılandırma dosyası bulunamadığından veya hizmet adı ile eşleşen hiçbir hizmet öğesi yapılandırma dosyasında bulunamadı veya uç nokta yok hizmet öğesinde tanımlanan nedeniyle olabilir.|  
|SFxActionMismatch|Bir eylem uyuşmazlığı nedeniyle yazılı bir ileti oluşturulamıyor. Belirtilen eylem ancak karşılaştı başka bekleniyor|  
|SFxAnonymousTypeNotSupported|Belirtilen iletiyi belirtilen bölümünde RPC ile dışarı veya türü anonim olduğundan kodlanmış.|  
|SFxBadMetadataLocationNoAppropriateBaseAddress|Yapılandırma bölümü serviceMetadata bölümünde ExternalMetadataLocation özelliği veya özniteliğiyle kullanarak ServiceMetadataBehavior için sağlanan URL göreli bir URL şuydu ve hangi çözümlemek temel adres yok .|  
|SFxBadMetadataMustBePolicy|Belirtilen ad alanına ve ada sahip XmlElement ilke sağlamanız gerekir. Bu XmlElement belirtilen ad alanına ve ada sahip.|  
|SFxBodyObjectTypeCannotBeInherited|Belirtilen tür RPC stilinde gövde nesnesi olarak kullanılmak üzere nesne dışındaki herhangi bir sınıftan devralınan olamaz.|  
|SFxBodyObjectTypeCannotBeInterface|Belirtilen tür, RPC stilinde gövde nesne için desteklenmeyen belirtilen arabirimini uygular.|  
|SFxCallbackBehaviorAttributeOnlyOnDuplex|Çift yönlü sözleşme ile bir uç noktada CallbackBehaviorAttribute yalnızca bir davranış olarak çalıştırılabilir. Belirtilen sözleşme çift yönlü değil ve hiçbir geri çağırma işlemleri içerir.|  
|SFxCallbackRequestReplyInOrder1|Geçerli ileti işleme tamamlanana kadar bu işlemi yanıt alınamıyor. Düzen dışı ileti işleme izin vermek istiyorsanız, desteklemeyeceğini ConcurrencyMode ya da çoklu belirtilen belirtin.|  
|SfxCallbackTypeCannotBeNull|Belirtilen sözleşme DuplexChannelFactory ile kullanabilmek için sözleşme geçerli geri arama sözleşmesi belirtmeniz gerekir. Sizin bir geri arama sözleşmesi varsa, bu ChannelFactory yerine DuplexChannelFactory kullanın.|  
|SFxCannotGetMetadataFromLocation|MetadataExchangeClient, yalnızca HTTP ve HTTPS MetadataLocations meta veri alabilir. Belirtilen meta veri alınamıyor.|  
|SFxCannotHttpGetMetadataFromAddress|MetadataExchangeClient yalnızca meta veri HTTP veya HTTPS adreslerinden MetadataExchangeClientMode HttpGet kullanırken alabilir. Belirtilen meta veri alınamıyor.|  
|SFxCannotImportAsParameters_Bare|Belirtilen işlem RPC ne Sarmalanan belge olduğundan ileti sözleşmesi oluşturuluyor.|  
|SFxCannotImportAsParameters_DifferentWrapperName|Belirtilen iletiyi sarmalayıcı adını varsayılan değer eşleşmediğinden ileti sözleşmesi oluşturuluyor.|  
|SFxCannotImportAsParameters_DifferentWrapperNs|Belirtilen iletiyi sarmalayıcı ad alanı varsayılan değer eşleşmediğinden ileti sözleşmesi oluşturuluyor.|  
|SFxCannotImportAsParameters_ElementIsNotNillable|Belirtilen öğe adını belirtilen ad alanından olarak işaretlenmediğinden olduğundan ileti sözleşmesi oluşturuluyor.|  
|SFxCannotImportAsParameters_HeadersAreUnsupported|Belirtilen iletiyi üstbilgileri olduğundan ileti sözleşmesi oluşturuluyor.|  
|SFxCannotImportAsParameters_Message|Belirtilen işlem türü belirsiz bir ileti bağımsız değişken veya dönüş türü olduğundan ileti sözleşmesi oluşturuluyor.|  
|SFxCannotImportAsParameters_MessageHasProtectionLevel|Belirtilen iletiyi koruması gerektirdiğinden, ileti sözleşmesi oluşturuluyor.|  
|SFxCannotImportAsParameters_NamespaceMismatch|Belirtilen ileti bölümü ad alanı varsayılan değer eşleşmediğinden ileti sözleşmesi oluşturuluyor.|  
|SFxCannotRequireBothSessionAndDatagram3|Belirtilen sözleşme SessionMode.NotAllowed ve belirtilen sözleşme SessionMode.Required belirtir. SessionMode değerlerden birini değiştirin veya farklı bir adres veya ListenURI, her uç noktası için belirleyin.|  
|SFxCannotSetExtensionsByIndex|Bu koleksiyon ayarını uzantıları dizini tarafından desteklemez. InsertItem ya da removeItem yöntemlerini kullanın.|  
|SFxChannelDispatcherDifferentHost0|Olmadığından şu anda sağlanan ServiceHost öğesine bağlı değil.|  
|SFxChannelDispatcherMultipleHost0|Birden fazla ServiceHost olmadığından eklenemiyor.|  
|SFxChannelDispatcherNoHost0|ServiceHost öğesine eklenmediğinden olmadığından açılamaz.|  
|SfxChannelFactoryDisposed|ChannelFactory zaten atıldı gibi bu ChannelFactory açılamıyor. ChannelFactory yeniden kullanmadan önce oluşturun.|  
|SFxChannelFactoryNoBinding|Hiçbir bağlama, bitiş noktası ile ilişkilendirilmiş olduğundan ChannelFactory açılamıyor. Oluşturucusu veya uç nokta özelliği ile bir bağlama belirtin.|  
|SFxChannelTerminated0|IsTerminating zaten bu kanalda sonlandırmak kanal bağlantısı neden çağrılmış olarak işaretlenen bir işlem. Daha fazla işlem yok, bu kanalda çağrılabilir. Kanal iletişime devam etmek için yeniden oluşturun.|  
|SFxCloseTimedOut1|Belirtilen sonra ServiceHost kapatma işlemi durduruldu. Bir istemci bir süre sonuyla kanal gereken süre içinde kapatamadı olmasından kaynaklanabilir. Bu işlem için izin verilen süreyi daha uzun bir süre parçası olabilir.|  
|SfxCloseTimedOutWaitingForDispatchToComplete|İşlem kapatma Hizmet dağıtımının tamamlanması beklenirken zaman aşımına uğradı.|  
|SFxCodeGenIsNotAssignableFrom|Belirtilen değer atanamaz.|  
|SFxConfigChannelConfigurationNotFound|Belirtilen ad ve ServiceModel istemci yapılandırması bölümünde sözleşme bitiş noktası öğesi bulunamıyor.|  
|SFxConflictingGlobalElement|Belirtilen ad alanında belirtilen ada sahip en üst düzey genişletilebilir biçimleme dili öğesi belirtilen tür başvuramaz. Zaten farklı bir tür başvuruda bulunuyor. Farklı işlem adı veya MessageBodyAttribute ileti veya ileti bölümleri için farklı bir ad belirtmek için kullanın.|  
|SFxContractHasZeroInitiatingOperations|Bir sözleşme en az bir IsInitiating olmalıdır = true işlemi.|  
|SFxContractHasZeroOperations|Bir sözleşme en az bir işlem olması gerekir.|  
|SFxContractInheritanceRequiresInterfaces|Belirtilen türdeki hizmet sınıfı, bir ServiceContract tanımlar ve belirtilen türden ServiceContract devralır. Sözleşme devralma yalnızca arabirim türleri arasında kullanılabilir. Bir sınıf ServiceContractAttribute ile işaretlenmişse ServiceContractAttribute hiyerarşisiyle yalnızca türünde olmalıdır.  ServiceContractAttribute belirtilen türü üzerinde belirtilen tür uygulayan ayrı bir arabirimi taşıyın.|  
|SFxCreateDuplexChannel1|Belirtilen sözleşmenin geri çağırma sözleşme yok ya da herhangi bir işlem tanımlamıyor. Çift yönlü sözleşme değilse ChannelFactory yerine DuplexChannelFactory kullanın.|  
|SFxCreateDuplexChannelNoCallback|Bu CreateChannel öğesinin bu örneğinde çağrılamaz. DuplexChannelFactory ile bir InstanceContext başlatılmadı. Bir InstanceContext alan CreateChannel aşırı yüklemesini çağırın.|  
|SFxCreateDuplexChannelNoCallback1|Bu CreateChannel öğesinin bu örneğinde çağrılamaz. DuplexChannelFactory Type ile başlatıldığından ve geçerli InstanceContext sağlandı. Bir InstanceContext alan CreateChannel aşırı yüklemesini çağırın.|  
|SFxCreateDuplexChannelNoCallbackUserObject|Bu CreateChannel öğesinin bu örneğinde çağrılamaz. DuplexChannelFactory öğesine sağlanan InstanceContext geçerli bir UserObject içermiyor.|  
|SFxCreateNonDuplexChannel1|ChannelFactory belirtilen sözleşme desteklemez. Bir veya daha fazla işlem bir geri çağırma sözleşmeyle ChannelFactory tanımlar. DuplexChannelFactory yerine ChannelFactory kullanın.|  
|SFxCustomBindingNeedsTransport1|Belirtilen sözleşme ServiceEndpoint CustomBinding bir TransportBindingElement yok. Her bağlama TransportBindingElement öğesinden alınan en az bir bağlama öğesi olması gerekir.|  
|SFxCustomBindingWithoutTransport|Bir TransportBindingElement olmadığı için bu özel bağlama için düzeni hesaplanamıyor. Her bağlama TransportBindingElement öğesinden alınan en az bir bağlama öğesi olması gerekir.|  
|SFxDataContractSerializerDoesNotSupportBareArray|DataContractSerializer belirtilen öğede belirtilen koleksiyon desteklemez.|  
|SFxDictionaryIsEmpty|Sözlük boş olduğundan işlem gerçekleştirilemiyor.|  
|SFxDocEncodedNotSupported|Belirtilen yansıtılırken bir hata oluştu. Belge kodlu desteklenmiyor. 'Use' sabit değer veya 'Style' RPC değiştirin.|  
|SFxDuplicateInitiatingActionAtSameVia|Bu hizmet belirtilen dinleme birden fazla uç noktası vardır. Uç noktalar aynı belirtilen başlatma eylemi paylaşır. Dağıtıcı iletiyi işlemek için doğru uç nokta belirlemek mümkün olmayacağından bu eylem iletileriyle bırakılan.|  
|SFXEndpointBehaviorUsedOnWrongSide|Belirtilen IEndpointBehavior sunucu üzerinde kullanılamaz. Bu davranış yalnızca istemciler için geçerlidir.|  
|SFxEndpointNoMatchingScheme|Belirtilen şema uç noktası için belirtilen bağlama ile eşleşen taban adresi bulunamıyor. Kayıtlı taban adresi düzenleri belirtilir.|  
|SFxErrorCreatingMtomReader|İletim en iyi duruma getirme mekanizmasını ileti için bir okuyucu oluşturulurken bir hata oluştu.|  
|SFxErrorDeserializingFault|Sunucu bir geçersiz Basit Nesne erişim protokolü hatası döndürdü. Ayrıntılar için InnerException'a bakın.|  
|SFxErrorDeserializingHeader|Belirtilen iletiyi üstbilgilerinde birini kaldırılırken bir hata oluştu. Daha fazla ayrıntı için lütfen InnerException'a bakın.|  
|SFxErrorReflectingOnMethod3|Belirtilen türdeki belirtilen yöntem belirtilen öznitelikte yüklenirken bir hata oluştu.  Ayrıntılar için InnerException'a bakın.|  
|SFxErrorReflectingOnParameter4|Belirtilen türdeki belirtilen yönteminin belirtilen parametresi belirtilen öznitelikte yüklenirken bir hata oluştu. Ayrıntılar için InnerException'a bakın.|  
|SFxErrorReflectingOnType2|Belirtilen türü üzerinde belirtilen öznitelik yüklenirken bir hata oluştu.  Ayrıntılar için InnerException'a bakın.|  
|SFxErrorSerializingBody|Belirtilen ileti gövdesi seri hale getirilirken bir hata oluştu. Ayrıntılar için InnerException'a bakın.|  
|SFxErrorSerializingHeader|Belirtilen iletiyi üstbilgilerinde birini seri hale getirilirken bir hata oluştu. Ayrıntılar için InnerException'a bakın.|  
|SFxExpectedIMethodCallMessage|İç Hata. İletinin geçerli bir IMethodCallMessage olmalıdır.|  
|SFxExportMustHaveType|Geçerli bir CLR türü olmadığı için belirtilen işlem belirtilen bölümünde verilemez.|  
|SFxHeaderNotUnderstood|İleti işlenmedi. Belirtilen ad alanı belirtilen başlığından bu ileti alıcı tarafından anlaşılmadı. Bu hata genellikle, bu iletiyi gönderenin alıcının işleyemeyeceği bir iletişim protokolü etkinleştirilmiş gösterir. İstemcinin bağlama yapılandırmasını hizmet bağlamasıyla tutarlı olduğundan emin olun.|  
|SFxHeadersAreNotSupportedInEncoded|Belirtilen iletiyi uzak yordam çağrısı kodlanmış stilinde kullanılmak üzere üstbilgi olmaması gerekir.|  
|SFxInconsistentWsdlOperationStyleInMessageParts|Belirtilen işlem iletisinde tüm parçalarını ya da bir tür ya da bir öğe içermesi gerekir.|  
|SFxInconsistentWsdlOperationStyleInOperationMessages|Belirtilen işlem iletilerden çıkarımı yapılan belirtilen stili bağlamalar kullanılarak belirtilen belirtilen beklenen stili eşleşmiyor.|  
|SFxInvalidCallbackIAsyncResult|IAsyncResult sağlanmaz veya yanlış türde.|  
|SFxInvalidMessageBody|OperationFormatter geçersiz bir iletiyle karşılaşıldı. Belirtilen ada ve ad alanı 'Element' düğüm türü bekleniyordu. Belirtilen düğüm türü belirtilen adı ve ad alanı bulunamadı.|  
|SFxInvalidMessageBodyEmptyMessage|İleti boş olduğundan OperationFormatter herhangi bir bilgi iletisi seri durumdan çıkarılamıyor.|  
|SFxInvalidMessageBodyErrorDeserializingParameter|Belirtilen parametre seri durumdan çalışılırken bir hata oluştu. Daha fazla bilgi için bkz. InnerException.|  
|SFxInvalidMessageBodyErrorSerializingParameter|Belirtilen parametre seri çalışılırken bir hata oluştu. InnerException ileti belirtildi.  Ayrıntılar için InnerException'a bakın.|  
|SFxInvalidMessageBodyUnexpectedNode|Belirtilen beklenmeyen düğüm parametreleri seri kaldırma sırasında belirtilen ad alanından karşılaştı.|  
|SFxInvalidMessageContractSignature|Belirtilen işlem, bir parametre veya MessageContractAttribute ile işaretlenmiş bir dönüş türüne sahip. Bir istek iletisi temsil etmek için bir ileti sözleşmesi kullanırken işlemi MessageContractAttribute ile işaretlenmiş tek bir parametre olması gerekir. Yanıt iletisini temsil etmek için bir ileti sözleşmesi kullanırken, işlemin dönüş değeri MessageContractAttribute ile işaretlenmiş bir türü olmalıdır. İşlemi, 'out' veya 'ref' olamaz parametreleri.|  
|SFxInvalidReplyAction|Giden yanıt iletisi işlemi için belirtilen eyleme sahip, ancak bu işlem için anlaşma başka bir ReplyAction belirtir. İletide belirtilen eylemi sözleşmesindeki ReplyAction eşleşmesi gerekir ya da işlemi sözleşme ReplyAction belirtmelisiniz ='* '.|  
|SFxInvalidRequestAction|Giden istek iletisi işlemi için belirtilen eyleme sahip, ancak bu işlem için anlaşma başka bir RequestAction belirtir. İletide belirtilen eylemi sözleşmesindeki RequestAction eşleşmesi gerekir ya da işlemi sözleşme RequestAction belirtmelisiniz ='* '.|  
|SFxInvalidStaticOverloadCalledForDuplexChannelFactory1|Bu sözleşme bir geri arama sözleşmesi tanımladığından statik CreateChannel yöntemi belirtilen sözleşme ile kullanılamaz. Statik CreateChannel aşırı birini DuplexChannelFactory kullanın\<TChannel >.|  
|SFxInvalidStreamInRequest|Bir akış olabilmesi istek için belirtilen işlem, işlem akış türü olan tek bir parametre olması gerekir.|  
|SFxInvalidStreamInResponse|İçin yanıt olarak bir akış olabilmesi için belirtilen işlem işlemi tek bir çıkış parametresi veya akış türü olan bir değer döndürmesi gerekir.|  
|SFxInvalidStreamInTypedMessage|Akışlar ileti programlama modeli Sözleşmesi ile kullanmak için belirtilen tür akış türü olan tek bir MessageBody üye olması gerekir.|  
|SFxInvalidUseOfPrimitiveOperationFormatter|PrimitiveOperationFormatter bir parametre verildi veya desteği olmayan türü döndürür.|  
|SFxMessageContractBaseTypeNotValid|Belirtilen tür ve bir MessageContract tanımlamıyor belirtilen bir türünden türetilen bir MessageContract tanımlar. Tüm nesneleri belirtilen devralma hiyerarşisinde bir MessageContract tanımlamanız gerekir.|  
|SFxMethodNotSupported1|Belirtilen yöntem, bu nesne üzerinde desteklenmiyor. Bu yöntemin OperationContractAttribute ile işaretlenmemiş olması veya arabirim türü ServiceContractAttribute ile işaretlenmemiş yoksa oluşabilir.|  
|SFxMethodNotSupportedByType2|Belirtilen ServiceHost uygulama türü, belirtilen hizmet sözleşmesini uygulamıyor.|  
|SFxMethodNotSupportedOnCallback1|Belirtilen geri çağırma yöntemi desteklenmiyor. Bu yöntem ile OperationContractAttribute işaretlenmemiş olması veya onun arabirim türü ServiceContractAttribute CallbackContract hedef değilse gerçekleşebilir.|  
|SFxMismatchedOperationParent|Yalnızca kendi üst DispatchRuntime ya da ClientRuntime sırasıyla DispatchOperation veya ClientOperation eklenebilir.|  
|SFxNameCannotBeEmpty|Name özelliği boş bir dize olamaz.|  
|SfxNoTypeSpecifiedForParameter|İşlemi oluşturulmasını engeller parametresi için hiçbir CLR türü belirtildi.|  
|SFxOperationBehaviorAttributeOnlyOnServiceClass|OperationBehaviorAttribute yalnızca hizmet sınıfıyla gidebilirsiniz. ServiceContract arabirimde konumuna geçiremezsiniz. Belirtilen türü üzerinde belirtilen yöntemi bunu ihlal ediyor.|  
|SFxOperationContractOnNonServiceContract|Belirtilen yöntem OperationContractAttribute ile işaretlenmiş, ancak kapsayan belirtilen türle ServiceContractAttribute ile işaretlenmemiş. OperationContractAttribute yalnızca ServiceContractAttribute türlerindeki yöntemlere veya bunların CallbackContract türlerinde kullanılabilir.|  
|SFxParameterCountMismatch|Sağlanan bağımsız değişken sayısı beklenen bağımsız değişken sayısı arasında uyumsuzluğa oluştu. Özellikle, beklenen bağımsız değişkeni belirtilen sayıda öğeyi sahipken belirtilen bağımsız değişken belirtilen sayıda öğeyi sahiptir.|  
|SFxPartNameMustBeUniqueInRpc|Belirtilen ileti parçası adı bir uzak yordam çağrısı iletide benzersiz değil.|  
|SFxReplyActionMismatch3|Belirtilen eylemi olan belirtilen işlem için bir yanıt iletisi alındı. Ancak, istemci kodunuzun belirtilen eylem gerektirir.|  
|SFxRequestReplyNone|Bir ileti "None" hedeflenen bir üstbilgiyle WS adresleme ReplyTo ya da FaultTo alındı adresi. Bu değerleri istek-yanıt işlemleri için geçerli değildir. Tek yönlü bir işlem kullanın veya "Hiçbiri" ReplyTo ya da FaultTo değerlerini desteklemeniz gerekiyorsa ManualAddressing işlevini etkinleştirin.|  
|SFxRequestTimedOut1|Bu istek işlemi, belirtilen yapılandırılan süre içinde bir yanıt almadı. İzin verilen süreyi daha uzun bir süre parçası olabilir. Bu hizmet işlemi hala işlemesi veya hizmet bir yanıt iletisi gönderemedi nedeniyle olabilir.|  
|SFxRequestTimedOut2|Belirtilen konuma gönderilen istek işlemi, belirtilen yapılandırılan süre içinde bir yanıt almadı. İzin verilen süreyi daha uzun bir süre parçası olabilir. Bu hizmet işlemi hala işlemesi veya hizmet bir yanıt iletisi gönderemedi nedeniyle olabilir.|  
|SFxSchemaDoesNotContainType|Belirtilen hedef ad alanına sahip şema belirtilen ada sahip bir türü içermiyor.|  
|SfxServiceContractAttributeNotFound|Belirtilen sözleşme türü ServiceContractAttribute ile değil. Geçerli bir sözleşme tanımlamak için belirtilen tür ServiceContractAttribute ile ilişkilendirilmesi gerekir. Türü, bir sözleşme arabirimi ya da hizmet sınıfı ya da olabilir.|  
|SFxServiceContractGeneratorConfigRequired|Yapılandırma bilgileri GenerateServiceEndpoint yöntemini kullanarak oluşturmak için ServiceContractGenerator örneğinin geçerli bir yapılandırma nesnesi ile başlatılması gerekir.|  
|SFxServiceHostBaseCannotAddEndpointAfterOpen|ServiceHost şu durumlardan birinde olduğunda uç noktaları eklenemiyor:<br /><br /> -Açılan<br />-Hatalı<br />-Sonlandırıldı<br />-Kapalı|  
|SFxServiceHostBaseCannotAddEndpointWithoutDescription|Description özelliği başlatılmadan önce uç noktaları eklenemiyor.|  
|SFxServiceMetadataBehaviorNoHttpBaseAddress|ServiceMetadataBehavior özelliği olarak true ve HttpGetUrl özelliği için ayarlanmış de göreli adresidir, ancak hiçbir HTTP temel adresi yok. Bir HTTP temel adresi sağlayın ya da HttpGetUrl mutlak bir adres olarak ayarlayın.|  
|SFxServiceMetadataBehaviorNoHttpsBaseAddress|ServiceMetadataBehavior özelliği olarak true ve HttpsGetUrl özelliği için ayarlanmış de göreli bir adresi ancak HTTPS temel adres yoktur. Bir HTTPS temel adresi sağlayın ya da HttpsGetUrl mutlak bir adres olarak ayarlayın.|  
|SFxServiceMetadataBehaviorUrlMustBeHttpOrRelative|Davranış Url göreli Tekdüzen Kaynak Tanımlayıcısı veya bir mutlak Tekdüzen Kaynak Tanımlayıcısı belirtilen düzenine sahip olmalıdır. Belirtilen Url belirtilen düzenine sahip bir mutlak Tekdüzen kaynak tanımlayıcısıdır.|  
|SFxStreamRequestMessageClosed|Bu akış içeren ileti kapatıldı. Hizmet işlemini döndükten sonra isteği akışları erişilemiyor.|  
|SFxStreamResponseMessageClosed|Bu akış içeren ileti kapatıldı.|  
|SFxTerminateRequestProcessingException|Uzantı işlem hattında, bu iletiyi işlemeyi çıkmanız gerekir.|  
|SFxTerminatingOperationAlreadyCalled1|IsTerminating işlemi çağrıldı çünkü bu kanal daha fazla ileti gönderilemiyor.|  
|SFxThrottleLimitMustBeGreaterThanZero0|Kısıtlama sınırı sıfırdan büyük olmalıdır. Kısıtlama sınırı devre dışı bırakmak için Int32.MaxValue değerini ayarlayın.|  
|SFxTypedOrUntypedMessageCannotBeMixedWithVoidInRpc|İşlemi hiç parametre yok veya geçersiz bir dönüş değeri varsa ileti sözleşme türlerini ya da System.ServiceModel.Channels.Message türü, RPC kodlu stili kullanıldığında, kullanılamaz. Boş ileti sözleşme türü parametre olarak ekleyin veya belirtilen işlem için dönüş türü.|  
|SFxUserCodeThrewException|Belirtilen kullanıcı işlemi içinde kullanıcı kodu işlenmeyen bir özel durum oluşturdu. Bu yinelenen bir sorunsa, belirtilen yöntemin kullanımı bir hata gösterebilir.|  
|SfxUseTypedMessageForCustomAttributes|Ek öznitelikler gerektirdiğinden işlem parametresi için belirtilen parametre eşlenemez.|  
|SFxVersionMismatchInOperationContextAndMessage2|Giden üstbilgiler OperationContext.Current içindeki MessageVersion işlenen ileti üst bilgi sürümüyle eşleşmediğinden iletiye eklenemiyor|  
|SFxWellKnownNonSingleton0|Hizmet örneği alan ServiceHost oluşturucuları birini kullanmak için hizmet InstanceContextMode InstanceContextMode öğesi için ayarlanmalıdır. Bu, ServiceBehaviorAttribute kullanılarak yapılandırılabilir. Aksi takdirde, tür bağımsız değişkeni ele ServiceHost oluşturucuları kullanın.|  
|SFxWrapperTypeHasMultipleNamespaces|Birden çok ad alanına sahip olduğundan belirtilen ileti için sarmalayıcı türü bir veri sözleşmesi türü olarak öngörülen olamaz. XmlSerializer kullanın.|  
|UriMustBeAbsolute|URI mutlak olması gerekir.|
