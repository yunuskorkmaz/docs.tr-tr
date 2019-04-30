---
title: Hizmet Çerçevesi
ms.date: 03/30/2017
ms.assetid: 75f60b87-f80e-4377-ba7c-8e6becaa2b28
ms.openlocfilehash: 859e718a56ab63c8e012e1851c0730f53cb707be
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61780763"
---
# <a name="service-framework"></a>Hizmet Çerçevesi
Bu konu hizmet çerçevesi verileri tarafından oluşturulan tüm özel durumları listeler.  
  
## <a name="exception-list"></a>Özel durum listesi  
  
|Kaynak kodu|Kaynak dizesi|  
|-------------------|---------------------|  
|ABindingInstanceHasAlreadyBeenAssociatedTo1|Bir binding örneği, belirtilen Tekdüzen Kaynak Tanımlayıcısı dinlemek için zaten ilişkilendirilmiş. İki uç nokta aynı ListenUniform kaynak göstergesi paylaşmak istiyorsanız, bunlar aynı bağlama nesne örneğini de paylaşmanız gerekir. Çakışan iki uç nokta yapılandırma dosyasında veya AddServiceEndpoint() ve yapılandırma AddServiceEndpoint() çağrılarındaki belirtildi.|  
|AChannelServiceEndpointIsNull0|Bir kanal ya da hizmet uç noktası null olur.|  
|AChannelServiceEndpointSContractSNameIsNull0|Bir Channel/Service uç noktası sözleşme adı null veya boş.|  
|AChannelServiceEndpointSContractSNamespace0|Bir Channel/Service uç noktası sözleşme ad alanı null olur.|  
|BaseAddressCannotHaveFragment|Temel adres bir Tekdüzen Kaynak Tanımlayıcısı parçası bulunduramaz.|  
|BaseAddressCannotHaveQuery|Temel adres bir Tekdüzen Kaynak Tanımlayıcısı sorgu dizesi içeremez.|  
|BaseAddressCannotHaveUserInfo|Bir temel adres bir Tekdüzen Kaynak Tanımlayıcısı kullanıcı bilgileri bölümü bulunduramaz.|  
|BaseAddressDuplicateScheme|Bu koleksiyon zaten belirtilen düzenine sahip bir adres içeriyor. Yalnızca bir adres, bu koleksiyonda her düzen için izin verilir.|  
|BaseAddressMustBeAbsolute|Yalnızca bir mutlak Tekdüzen Kaynak Tanımlayıcısı bir temel adres olarak kullanılabilir.|  
|BindingDoesnTSupportAnyChannelTypes1|Belirtilen bağlama, herhangi bir kanal türü oluşturmayı desteklemiyor. Özel bir bağlamaya ait bağlama öğelerini yanlış Yığılmış ya da yanlış sırada. Bir taşıma altındaki yığını için gereklidir. Bağlama öğeleri için önerilen sırası şöyledir: TransactionFlow, ReliableSession, Security, CompositeDuplex, OneWay, StreamSecurity, MessageEncoding, taşıma.|  
|BindingDoesnTSupportDuplexButContractRequires1|Anlaşma için Duplex gerekiyor. Belirtilen bağlama bunu desteklemiyor ya da bunu destekleyecek biçimde düzgün yapılandırılmamış.|  
|BindingDoesnTSupportOneWayButContractRequires1|Anlaşma için OneWay gerekiyor. Belirtilen bağlama bunu desteklemiyor ya da bunu destekleyecek biçimde düzgün yapılandırılmamış.|  
|BindingDoesnTSupportRequestReplyButContract1|Anlaşma için Request/Reply gerekiyor. Belirtilen bağlama bunu desteklemiyor ya da bunu destekleyecek biçimde düzgün yapılandırılmamış.|  
|BindingDoesnTSupportSessionButContractRequires1|Anlaşma için Session gerekiyor.  Belirtilen bağlama bunu desteklemiyor ya da bunu destekleyecek biçimde düzgün yapılandırılmamış.|  
|BindingDoesnTSupportTwoWayButContractRequires1|Sözleşme gerekiyor çift yönlü (istek-yanıt ya da çift yönlü). Belirtilen bağlama bunu desteklemiyor ya da bunu destekleyecek biçimde düzgün yapılandırılmamış.|  
|BindingRequirementsAttributeDisallowsQueuedDelivery1|DeliveryRequirementsAttribute QueuedDelivery izin vermez. Belirtilen sözleşme ile uç nokta için bağlama da destekler.|  
|BindingRequirementsAttributeRequiresQueuedDelivery1|DeliveryRequirementsAttribute QueuedDelivery gerektirir. Belirtilen sözleşme ile uç nokta için bağlama bunu desteklemiyor ya da onu desteklemek için düzgün yapılandırılmamış.|  
|channelDoesNotHaveADuplexSession0|Geçerli kanal çıkış oturumunu kapatmayı desteklemez. Bu kanal, ISessionChannel uygulamıyor\<Iduplexsession >.|  
|ClientRuntimeRequiresFormatter0|SerializeRequest ve DeserializeReply değerlerinin her ikisi de olmadığından belirtilen ClientOperation bir biçimlendirici gerektirir false.|  
|CommunicationObjectAborted1|Durmuş olduğu için belirtilen iletişim nesnesi iletişim için kullanılamaz.|  
|CommunicationObjectAbortedStack2|Durmuş olduğu için belirtilen iletişim nesnesi iletişim için kullanılamaz: {1}|  
|CommunicationObjectBaseClassMethodNotCalled|Belirtilen iletişim nesnesi sanal işlevi geçersiz kılınmış {1} ancak temel sınıfta tanımlanan sürümü çağırmıyor.|  
|ContractIsNotSelfConsistentItHasOneOrMore2|Belirtilen sözleşme, bir veya daha fazla IsTerminating ya da IsInitiating olmayan sahiptir. SessionMode özelliği SessionMode.Required için yok. IsInitiating ve IsTerminating öznitelikleri yalnızca bir oturum bağlamında kullanılabilir.|  
|CouldnTCreateChannelForChannelType2|Belirtilen kanal türü istendi, ancak belirtilen bağlama bunu desteklemiyor ya da bunu destekleyecek biçimde düzgün yapılandırılmamış.|  
|DispatchRuntimeRequiresFormatter0|DeserializeRequest ve SerializeReply değerlerinin her ikisi de olmadığından belirtilen DispatchOperation bir biçimlendirici gerektirir false.|  
|EndMethodsCannotBeDecoratedWithOperationContractAttribute|IAsyncResult tasarım deseni kullanılırken, End metodu OperationContractAttribute ile kullanılamaz. Yalnızca ilgili Begin metodu OperationContractAttribute ile kullanılabilir. Bu özniteliğin yöntem Begin-End çiftine uygular.|  
|EndpointListenerRequirementsCannotBeMetBy3|Sözleşme bu belirtilen kanal türlerinden biri için destek gerektirdiğinden ChannelDispatcher gereksinimleri belirtilen bağlama için IChannelListener tarafından karşılanamıyor. Ancak, bağlama yalnızca belirtilen kanal türlerini destekler.|  
|EndpointsMustHaveAValidBinding0|Uç noktaları, geçerli bir bağlaması olması gerekir.|  
|InvalidOrUnrecognizedAction|İleti belirtilen eylemi geçersiz olduğu için işlenen veya tanınmıyor.|  
|MultipleMebesInParameters|BindingContext BindingParameters içinde birden fazla MessageEncodingBindingElement bulundu. CustomBinding içinde birden çok birkaç MessageEncodingBindingElements bulunması sahip olamaz. Biri bu öğeleri hariç tümünü kaldırın.|  
|MultipleStreamUpgradeProvidersInParameters|BindingContext BindingParameters içinde birden çok IStreamUpgradeProviderElement bulundu. CustomBinding içinde birden çok IStreamUpgradeProviderElement sahip olamaz. Biri bu öğeleri hariç tümünü kaldırın.|  
|NoChannelBuilderAvailable|Bağlama, bir TransportBindingElement öğesine sahip olmadığı için kanal fabrikası ya da bir kanal dinleyicisi oluşturmak için kullanılamaz. Her bağlamanın, TransportBindingElement öğesinden türetilen en az bir bağlama öğesi bulunmalıdır.|  
|NotAllBindingElementsBuilt|Bazı bağlama öğeleri bu bağlama, kanal fabrikası ve kanal dinleyicisi oluşturulurken kullanılmadı. Bağlama öğelerinin sıralı doğru değil. Bağlama öğeleri için önerilen sırası şöyledir: TransactionFlow, ReliableSession, Security, CompositeDuplex, OneWay, StreamSecurity, MessageEncoding, taşıma.  TransportBindingElement en sonda olması gerektiğine dikkat edin. Belirtilen bağlama öğeleri oluşturulmadı değil.|  
|RuntimeRequiresInvoker0|Dağıtma işlemi, bir Invoker gerektirir.|  
|ServiceHasZeroAppEndpoints|Belirtilen hizmet uygulaması (altyapı olmayan) uç nokta vardır. Bu, uygulamanız için herhangi bir yapılandırma dosyası bulunamadığından veya hizmet adı ile eşleşen hiçbir hizmet öğesi yapılandırma dosyasında bulunamadığından ya da hizmet öğesinde tanımlanan uç nokta nedeniyle olabilir.|  
|SFxActionMismatch|Yazılı ileti bir eylem uyumsuzluğu nedeniyle oluşturulamıyor. Belirtilen eylem ancak karşılaştı başka bekleniyor|  
|SFxAnonymousTypeNotSupported|Belirtilen iletisinde belirtilen bölümü RPC'yle dışarı veya türü anonim olduğundan kodlanmış.|  
|SFxBadMetadataLocationNoAppropriateBaseAddress|ServiceMetadataBehavior yapılandırma bölümü yapılandırmada serviceMetadata bölümündeki ExternalMetadataLocation özelliği veya externalMetadataLocation özniteliğiyle kullanarak sağlanan URL bir göreli URL şuydu ve çözmek kullanılacak temel adresi yok .|  
|SFxBadMetadataMustBePolicy|Bir ilke adını ve belirtilen ad alanı olan bir XmlElement sağlamanız gerekir. Bu XmlElement, adını ve belirtilen ad alanı vardır.|  
|SFxBodyObjectTypeCannotBeInherited|Belirtilen tür, RPC stili gövdesi nesne olarak kullanılacak nesne dışında herhangi bir sınıftan devralınamaz.|  
|SFxBodyObjectTypeCannotBeInterface|Belirtilen tür için gövde nesnesi RPC stili desteklenmiyor belirtilen arabirim uygular.|  
|SFxCallbackBehaviorAttributeOnlyOnDuplex|CallbackBehaviorAttribute, yalnızca çift yönlü sözleşme ile bir uç noktada bir davranışı çalıştırılabilir. Belirtilen sözleşme çift yönlü değildir ve herhangi bir geri çağırma işlemi içerir.|  
|SFxCallbackRequestReplyInOrder1|Geçerli iletinin işlenmesi tamamlanana kadar bu işlemi yanıt alınamıyor. Düzen dışı ileti işleme izin vermek istiyorsanız, Reentrant ConcurrencyMode veya çoklu belirtilen belirtin.|  
|SfxCallbackTypeCannotBeNull|Belirtilen sözleşme anlaşmasının DuplexChannelFactory ile kullanılabilmesi sözleşme geçerli bir geri çağırma anlaşması belirtmeniz gerekir. Anlaşmanızda bir geri çağırma anlaşması varsa, DuplexChannelFactory yerine ChannelFactory kullanın.|  
|SFxCannotGetMetadataFromLocation|MetadataExchangeClient, yalnızca HTTP ve HTTPS MetadataLocations meta veri alabilir. Belirtilen meta verileri alınamıyor.|  
|SFxCannotHttpGetMetadataFromAddress|MetadataExchangeClient, yalnızca meta veriler HTTP veya HTTPS adreslerinden MetadataExchangeClientMode HttpGet kullanırken alabilir. Belirtilen meta verileri alınamıyor.|  
|SFxCannotImportAsParameters_Bare|Belirtilen işlemi RPC ya da belge kaydırmalı olduğundan ileti anlaşması oluşturuluyor.|  
|SFxCannotImportAsParameters_DifferentWrapperName|Varsayılan değer belirtilen iletisinin sarmalayıcı adı eşleşmediğinden ileti anlaşması oluşturuluyor.|  
|SFxCannotImportAsParameters_DifferentWrapperNs|Belirtilen iletisinin sarmalayıcı ad alanı varsayılan değer eşleşmediğinden ileti anlaşması oluşturuluyor.|  
|SFxCannotImportAsParameters_ElementIsNotNillable|Belirtilen ad alanından belirtilen öğe adı sıfırlanabilir olarak işaretlenmediğinden çünkü bir ileti anlaşması oluşturuluyor.|  
|SFxCannotImportAsParameters_HeadersAreUnsupported|Belirtilen iletiyi üstbilgileri olduğundan ileti anlaşması oluşturuluyor.|  
|SFxCannotImportAsParameters_Message|Belirtilen işlem yazılmamış bir Message bağımsız değişkeni ya da dönüş türü sahip olduğu bir ileti anlaşması oluşturuluyor.|  
|SFxCannotImportAsParameters_MessageHasProtectionLevel|Belirtilen iletisi koruma gerektirdiğinden ileti anlaşması oluşturuluyor.|  
|SFxCannotImportAsParameters_NamespaceMismatch|Belirtilen ileti bölümü ad alanı varsayılan değer eşleşmediğinden ileti anlaşması oluşturuluyor.|  
|SFxCannotRequireBothSessionAndDatagram3|Belirtilen sözleşme SessionMode.NotAllowed ve belirtilen sözleşme SessionMode.Required belirtir. Sessionmode'u değerlerden birini değiştirin veya farklı bir adres veya ListenURI, her uç nokta için belirtin.|  
|SFxCannotSetExtensionsByIndex|Bu koleksiyon ayarını uzantıları dizine göre desteklemez. InsertItem ya da removeItem yöntemleri kullanın.|  
|SFxChannelDispatcherDifferentHost0|ChannelDispatcher şu anda sağlanan ServiceHost bağlı değil.|  
|SFxChannelDispatcherMultipleHost0|ChannelDispatcher için birden fazla ServiceHost eklenemez.|  
|SFxChannelDispatcherNoHost0|Bir ServiceHost öğesine bağlı olmadığından, ChannelDispatcher açılamıyor.|  
|SfxChannelFactoryDisposed|ChannelFactory zaten atıldı gibi bu ChannelFactory açılamıyor. ChannelFactory yeniden kullanmadan önce oluşturun.|  
|SFxChannelFactoryNoBinding|Hiçbir bağlama kendi uç noktası ile ilişkili ayarlanmadığından, ChannelFactory açılamıyor. Oluşturucu veya uç nokta özelliği ile bir bağlama belirtin.|  
|SFxChannelTerminated0|IsTerminating zaten bu kanalda sonlandırmak kanal bağlantısı neden çağrılmış olarak işaretlenen bir işlem. Daha fazla işlem yok, bu kanalda çağrılabilir. İletişimi devam etmek için kanal yeniden oluşturun.|  
|SFxCloseTimedOut1|Belirtilen ServiceHost kapatma işlemi durduruldu. Bir istemcinin oturumdaki kanalı gereken sürede kapatmak başarısız oldu çünkü bu olabilir. Bu işlem için izin verilen süreyi uzun bir zaman aşımının parçası olabilir.|  
|SfxCloseTimedOutWaitingForDispatchToComplete|Kapatma işlemi hizmet dağıtımının tamamlanması beklenirken zaman aşımına uğradı.|  
|SFxCodeGenIsNotAssignableFrom|Belirtilen değer atanamaz.|  
|SFxConfigChannelConfigurationNotFound|Belirtilen ada ve ServiceModel istemci yapılandırma bölümünde sözleşme ile Bitiş öğesi bulunamadı.|  
|SFxConflictingGlobalElement|Belirtilen ad alanında belirtilen ada sahip en üst düzey Genişletilebilir Biçimlendirme Dili öğesi belirtilen türde başvuramaz. Bunu zaten farklı bir türe başvuruyor. Farklı işlem adı veya MessageBodyAttribute ileti ya da message bölümleri için farklı bir ad belirtmek için kullanın.|  
|SFxContractHasZeroInitiatingOperations|Bir sözleşme en az bir IsInitiating olmalıdır = true işlemi.|  
|SFxContractHasZeroOperations|Bir sözleşme en az bir işlem olmalıdır.|  
|SFxContractInheritanceRequiresInterfaces|Belirtilen türdeki hizmet sınıfı bir ServiceContract tanımlar hem de belirtilen türünden bir ServiceContract devralır. Anlaşma devralma yalnızca arabirim türleri arasında kullanılabilir. Bir sınıf ServiceContractAttribute ile işaretlenmişse, hiyerarşide ServiceContractAttribute ile tek tür olmalıdır.  ServiceContractAttribute belirtilen türün uyguladığı ayrı bir arabirimi belirtilen tür üzerinde taşıyın.|  
|SFxCreateDuplexChannel1|Belirtilen sözleşme geri çağırma anlaşması yok veya herhangi bir işlem tanımlamıyor. Bu, çift yönlü bir anlaşma değilse, DuplexChannelFactory yerine ChannelFactory kullanın.|  
|SFxCreateDuplexChannelNoCallback|Bu CreateChannel aşırı yükü, DuplexChannelFactory öğesinin bu örneğinde çağrılamıyor. DuplexChannelFactory bir InstanceContext ile başlatılmadı. Bir InstanceContext alan CreateChannel aşırı yüklemesini çağırın.|  
|SFxCreateDuplexChannelNoCallback1|Bu CreateChannel aşırı yükü, DuplexChannelFactory öğesinin bu örneğinde çağrılamıyor. DuplexChannelFactory bir Type ile başlatıldığından ve geçerli InstanceContext sağlandı. Bir InstanceContext alan CreateChannel aşırı yüklemesini çağırın.|  
|SFxCreateDuplexChannelNoCallbackUserObject|Bu CreateChannel aşırı yükü, DuplexChannelFactory öğesinin bu örneğinde çağrılamıyor. DuplexChannelFactory öğesine sağlanan InstanceContext geçerli bir UserObject içermiyor.|  
|SFxCreateNonDuplexChannel1|Belirtilen sözleşme ChannelFactory desteklemez. ChannelFactory bir geri çağırma anlaşması bir veya daha fazla operations tanımlar. DuplexChannelFactory yerine ChannelFactory kullanın.|  
|SFxCustomBindingNeedsTransport1|Belirtilen anlaşmasına sahip ServiceEndpoint üstündeki CustomBinding içinde bir TransportBindingElement öğesine sahip değil. Her bağlamanın, TransportBindingElement öğesinden türetilen en az bir bağlama öğesi bulunmalıdır.|  
|SFxCustomBindingWithoutTransport|Düzen, bir TransportBindingElement öğesine sahip olmadığından bu özel bağlama için hesaplanamıyor. Her bağlamanın, TransportBindingElement öğesinden türetilen en az bir bağlama öğesi bulunmalıdır.|  
|SFxDataContractSerializerDoesNotSupportBareArray|DataContractSerializer belirtilen öğede belirtilen koleksiyonu desteklemiyor.|  
|SFxDictionaryIsEmpty|Sözlüğü boş olduğundan işlem gerçekleştirilemiyor.|  
|SFxDocEncodedNotSupported|Belirtilen yansıtılırken bir hata oluştu. Belge kodlu desteklenmiyor. Değişmez değer veya 'Style' RPC 'Use' değiştirin.|  
|SFxDuplicateInitiatingActionAtSameVia|Bu hizmet, belirtilen adreste dinleme yapan birden fazla uç nokta vardır. Uç noktalar aynı belirtilen başlatma eylemi paylaşın. Dağıtıcı ileti işleme için doğru uç noktaya belirlemek mümkün olmayacağından bırakılan iletiler bu eylemle.|  
|SFXEndpointBehaviorUsedOnWrongSide|Belirtilen IEndpointBehavior sunucusunda kullanılamaz. Bu davranış yalnızca istemcilere geçerli.|  
|SFxEndpointNoMatchingScheme|Uç noktası için belirtilen şema ile belirtilen bağlama eşleşen taban adresi bulunamıyor. Kayıtlı bir temel adres düzenleri belirtilir.|  
|SFxErrorCreatingMtomReader|İletim en iyi duruma getirme mekanizması ileti için bir okuyucu oluşturulurken bir hata oluştu.|  
|SFxErrorDeserializingFault|Sunucu bir geçersiz Basit Nesne erişim protokolü hatası döndürdü. Daha fazla ayrıntı için InnerException öğesine bakın.|  
|SFxErrorDeserializingHeader|Belirtilen iletisindeki üst biri seri durumdan çıkarılırken bir hata oluştu. Daha fazla ayrıntı için InnerException öğesine bakın.|  
|SFxErrorReflectingOnMethod3|Belirtilen özniteliğin üzerinde belirtilen yöntemi belirtilen türdeki yüklenirken bir hata oluştu.  Daha fazla ayrıntı için InnerException öğesine bakın.|  
|SFxErrorReflectingOnParameter4|Belirtilen özniteliğin belirtilen parametresinde belirtilen yöntemi belirtilen türdeki yüklenirken bir hata oluştu. Daha fazla ayrıntı için InnerException öğesine bakın.|  
|SFxErrorReflectingOnType2|Belirtilen özniteliğin belirtilen tür yüklenirken bir hata oluştu.  Daha fazla ayrıntı için InnerException öğesine bakın.|  
|SFxErrorSerializingBody|Belirtilen ileti gövdesi serileştirilirken bir hata oluştu. Daha fazla ayrıntı için InnerException öğesine bakın.|  
|SFxErrorSerializingHeader|Belirtilen iletisindeki üst biri serileştirilirken bir hata oluştu. Daha fazla ayrıntı için InnerException öğesine bakın.|  
|SFxExpectedIMethodCallMessage|İç Hata. İletinin geçerli bir IMethodCallMessage olması gerekir.|  
|SFxExportMustHaveType|Geçerli bir CLR türü olmadığı için belirtilen işlem belirtilen bölümün dışarı aktarılamaz.|  
|SFxHeaderNotUnderstood|İleti işlenmedi. Belirtilen ad alanından belirtilen üst bilgisi bu ileti alıcısı tarafından anlaşılmadı. Bu hata tipik biçimde bu iletiyi gönderenin alıcının işleyemeyeceği bir iletişim protokolü etkinleştirdiğini gösterir. İstemcinin bağlama yapılandırmasını hizmet bağlamasıyla tutarlı olduğundan emin olun.|  
|SFxHeadersAreNotSupportedInEncoded|Belirtilen iletiyi uzak yordam çağrısı kodlanmış stili kullanılacak üstbilgileri olmaması gerekir.|  
|SFxInconsistentWsdlOperationStyleInMessageParts|Belirtilen işlemindeki iletinin tüm bölümlerinde ya da bir türü veya bir öğe içermelidir.|  
|SFxInconsistentWsdlOperationStyleInOperationMessages|Belirtilen işlem iletileri içinden gösterilen belirtilen stili, bağlamalar kullanılarak belirtilen belirtilen beklenen stiliyle eşleşmiyor.|  
|SFxInvalidCallbackIAsyncResult|IAsyncResult sağlanmadı ya da yanlış türde.|  
|SFxInvalidMessageBody|OperationFormatter, geçersiz bir iletiyle karşılaşıldı. Belirtilen ada ve ad alanı ile 'Element' düğüm türü bekleniyordu. Belirtilen ada ve ad alanı ile belirtilen düğüm türü bulundu.|  
|SFxInvalidMessageBodyEmptyMessage|OperationFormatter, message boş olduğundan herhangi bir bilgi iletisi kaldırılamıyor.|  
|SFxInvalidMessageBodyErrorDeserializingParameter|Belirtilen parametre seri durumdan çıkarılmaya çalışılırken bir hata oluştu. Daha fazla bilgi için InnerException öğesine bakın.|  
|SFxInvalidMessageBodyErrorSerializingParameter|Belirtilen parametresi serileştirilmeye çalışılırken bir hata oluştu. InnerException iletisi belirtildi.  Daha fazla ayrıntı için InnerException öğesine bakın.|  
|SFxInvalidMessageBodyUnexpectedNode|Belirtilen beklenmeyen düğüm parametreleri seri kaldırma sırasında belirtilen ad alanından karşılaşıldı.|  
|SFxInvalidMessageContractSignature|Belirtilen işlem, bir parametre ya da MessageContractAttribute ile işaretlenmiş bir dönüş türü vardır. İstek iletisini göstermek için bir ileti anlaşması kullanarak, işlemi MessageContractAttribute ile işaretlenmiş bir tek parametresi olması gerekir. Yanıt iletisini temsil eden bir ileti anlaşması kullanarak, işlemin döndürdüğü değerin MessageContractAttribute ile işaretlenmiş bir tür olmalıdır. İşlem, herhangi bir 'out' veya 'ref' olamaz. parametreler.|  
|SFxInvalidReplyAction|İşlemi giden yanıt iletisi için belirtilen eylemi olsa da, bu işlemin anlaşması ReplyAction başka bir belirtir. Message içinde belirtilen Action değerinin ReplyAction eşleşmesi gerekir ya da işlem anlaşması ReplyAction belirtmelisiniz ='* '.|  
|SFxInvalidRequestAction|İşlemi giden istek iletisi için belirtilen eylemi olsa da, bu işlemin anlaşması başka bir RequestAction belirtir. Message içinde belirtilen Action değerinin RequestAction eşleşmesi gerekir ya da işlem anlaşması RequestAction belirtmelisiniz ='* '.|  
|SFxInvalidStaticOverloadCalledForDuplexChannelFactory1|Anlaşması bir geri çağırma anlaşması tanımladığından statik CreateChannel metodu belirlenen söyleşmesi kullanılamaz. Statik CreateChannel aşırı yüklemelerinden DuplexChannelFactory kullanın\<TChannel >.|  
|SFxInvalidStreamInRequest|Bir akış olabilmesi istekte için belirtilen işlem, işlemin, türü Stream olan bir tek parametresi olması gerekir.|  
|SFxInvalidStreamInResponse|Bir akış olabilmesi için belirtilen işlem yanıta için işlemi tek bir out parametresinin veya dönüş değeri, türü Stream olan gerekir.|  
|SFxInvalidStreamInTypedMessage|Akışları ileti anlaşması programlama modeli ile kullanmak için belirtilen tür, türü Stream olan tek bir MessageBody üyesi olmalıdır.|  
|SFxInvalidUseOfPrimitiveOperationFormatter|PrimitiveOperationFormatter bir parametre veya dönüş desteklemediği türü.|  
|SFxMessageContractBaseTypeNotValid|Belirtilen tür bir MessageContract tanımlıyor ve türeyen bir belirtilen türden bir MessageContract tanımlamıyor. Belirtilen devralma hiyerarşisindeki tüm nesneler bir MessageContract tanımlamanız gerekir.|  
|SFxMethodNotSupported1|Bu nesne üzerinde belirtilen yöntemi desteklenmiyor. Bu, metodun OperationContractAttribute ile işaretlenmemiş olması ya da arabirim türünün ServiceContractAttribute ile işaretlenmemiş oluşabilir.|  
|SFxMethodNotSupportedByType2|Belirtilen ServiceHost uygulama türü, belirtilen hizmet sözleşmesi uygulamıyor.|  
|SFxMethodNotSupportedOnCallback1|Belirtilen geri çağırma yöntemi desteklenmiyor. Bu metodu OperationContractAttribute ile işaretlenmemiş olması ya da arabirimi türünün ServiceContractAttribute CallbackContract hedefinin değilse oluşabilir.|  
|SFxMismatchedOperationParent|Yalnızca kendi ana DispatchRuntime ya da ClientRuntime sırasıyla bir DispatchOperation ya da ClientOperation eklenebilir.|  
|SFxNameCannotBeEmpty|Name özelliği boş bir dize olamaz.|  
|SfxNoTypeSpecifiedForParameter|CLR türünün belirtilmemesi, işlemin oluşturulmasını engeller parametresi için belirtildi.|  
|SFxOperationBehaviorAttributeOnlyOnServiceClass|OperationBehaviorAttribute yalnızca hizmet sınıfıyla gidebilirsiniz. ServiceContract arabirimde sokulamaz. Belirtilen türü belirtilen yöntem bunu ihlal ediyor.|  
|SFxOperationContractOnNonServiceContract|Belirtilen metodu OperationContractAttribute ile işaretlenmiş, ancak kapsayan belirtilen türü ServiceContractAttribute ile işaretlenmemiş. OperationContractAttribute, yalnızca ServiceContractAttribute türündeki metotlarda ya da bunların CallbackContract türlerinde kullanılabilir.|  
|SFxParameterCountMismatch|Sağlanan bağımsız değişken sayısı ve beklenen bağımsız değişken sayısı arasında bir uyuşmazlık oluştu. Özellikle, beklenen bağımsız değişken belirtilen sayıda öğeyi sahipken belirtilen sayıda öğeyi belirtilen bağımsız değişken vardır.|  
|SFxPartNameMustBeUniqueInRpc|Belirtilen ileti bölümü adı uzak yordam çağrısı message öğesinde benzersiz değil.|  
|SFxReplyActionMismatch3|Belirtilen işlemle belirtilen eylem için bir yanıt iletisi alındı. Ancak, belirtilen eylem istemci kodunuz gerektirir.|  
|SFxRequestReplyNone|"None" hedeflenen bir WS-Addressing ReplyTo ya da FaultTo üst bilgisiyle bir ileti alındı adresi. Bu değerler, istek-yanıt işlemlerinde geçerli değildir. Tek yönlü işlem kullanmak ya da "None" ReplyTo ya da FaultTo değerlerini desteklemeniz gereken ManualAddressing özelliğini etkinleştirin.|  
|SFxRequestTimedOut1|Bu istek işlemi, belirtilen yapılandırılan süre içinde bir yanıt almadı. İzin verilen süreyi uzun bir zaman aşımının parçası olabilir. Bu, hizmetin işlemi hala işlemesi veya hizmetin bir yanıt iletisi gönderemedi olduğundan olabilir.|  
|SFxRequestTimedOut2|Belirtilen konuma gönderilen isteği işlemi, belirtilen yapılandırılan süre içinde bir yanıt almadı. İzin verilen süreyi uzun bir zaman aşımının parçası olabilir. Bu, hizmetin işlemi hala işlemesi veya hizmetin bir yanıt iletisi gönderemedi olduğundan olabilir.|  
|SFxSchemaDoesNotContainType|Belirtilen hedef ad alanına sahip şema, belirtilen ada sahip bir türü içermiyor.|  
|SfxServiceContractAttributeNotFound|Belirtilen sözleşme türü ServiceContractAttribute ile değil. Geçerli bir sözleşme tanımlamak için belirtilen türü ServiceContractAttribute ile ilişkilendirilmesi gerekir. Tür ya da sözleşme arabirimi veya bir hizmet sınıfı olabilir.|  
|SFxServiceContractGeneratorConfigRequired|GenerateServiceEndpoint yöntemini kullanarak yapılandırma bilgilerini üretmek için geçerli bir yapılandırma nesnesi ile ServiceContractGenerator örnek başlatılmalıdır.|  
|SFxServiceHostBaseCannotAddEndpointAfterOpen|ServiceHost şu durumlardan birinde olduğunda uç noktaları eklenemiyor:<br /><br /> -Açıldı<br />-Hatalı<br />-Sona erdi<br />-Kapalı|  
|SFxServiceHostBaseCannotAddEndpointWithoutDescription|Description özelliği başlatılmadan önce uç noktaları eklenemiyor.|  
|SFxServiceMetadataBehaviorNoHttpBaseAddress|ServiceMetadataBehavior özelliği true HttpGetUrl özelliği ile ayarlanır de göreli adresidir ancak HTTP temel adresi yok. Bir HTTP temel adresi sağlayın ya da HttpGetUrl mutlak bir adres olarak ayarlayın.|  
|SFxServiceMetadataBehaviorNoHttpsBaseAddress|ServiceMetadataBehavior özelliği true HttpsGetUrl özelliği ile ayarlanır de göreli adresidir ancak HTTPS taban adresi yok. HTTPS temel adres sağlamak ya da HttpsGetUrl mutlak bir adres olarak ayarlayın.|  
|SFxServiceMetadataBehaviorUrlMustBeHttpOrRelative|Davranış Url, göreli Tekdüzen Kaynak Tanımlayıcısı veya belirtilen şemasına sahip bir mutlak Tekdüzen kaynak tanımlayıcısı olmalıdır. Belirtilen Url, belirtilen şemasına sahip bir mutlak Tekdüzen kaynak tanımlayıcısıdır.|  
|SFxStreamRequestMessageClosed|Bu akışı içeren ileti kapatıldı. İstek akışlarına, hizmet işlemi dönüşünden sonra erişilemez.|  
|SFxStreamResponseMessageClosed|Bu akışı içeren ileti kapatıldı.|  
|SFxTerminateRequestProcessingException|İşlem hattındaki bir uzantı bu iletiyi işlemeyi çıkmalısınız.|  
|SFxTerminatingOperationAlreadyCalled1|IsTerminating işlemi çağrıldığından, bu kanal daha fazla ileti gönderilemiyor.|  
|SFxThrottleLimitMustBeGreaterThanZero0|Kısıtlama sınırı, sıfırdan büyük olmalıdır. Kısıtlama sınırı devre dışı bırakmak için Int32.MaxValue değeri ayarlayın.|  
|SFxTypedOrUntypedMessageCannotBeMixedWithVoidInRpc|İşlemi hiç parametre yok ya da bir void dönüş değerine sahip RPC kodlamalı stil kullanırken, ileti anlaşması türleri ya da System.ServiceModel.Channels.Message türü kullanılamaz. Bir parametre olarak bir boş ileti anlaşması türü ekleyin veya belirtilen işlem için dönüş türü.|  
|SFxUserCodeThrewException|Belirtilen kullanıcı işlemi, kullanıcı kodunda işlenmemiş bir özel durum oluşturdu. Bu yinelenen bir sorun ise, belirtilen yöntemin uygulanmasında bir hata gösterebilir.|  
|SfxUseTypedMessageForCustomAttributes|Ek öznitelikler gerektiğinden işlem parametresi için belirtilen parametre eşlenemez.|  
|SFxVersionMismatchInOperationContextAndMessage2|Giden üst bilgiler OperationContext.Current'içindeki MessageVersion işlenen ileti üst bilgi sürümüyle eşleşmediğinden iletiye eklenemiyor|  
|SFxWellKnownNonSingleton0|Alan bir hizmet örneği ServiceHost oluşturucuları birini kullanmak için hizmetin InstanceContextMode InstanceContextMode öğesi için ayarlanması gerekir. Bu, ServiceBehaviorAttribute kullanılarak yapılandırılabilir. Aksi takdirde, bir tür bağımsız değişkeni almayan ServiceHost oluşturucular kullanın.|  
|SFxWrapperTypeHasMultipleNamespaces|Birden çok ad olduğundan, belirtilen iletisi için sarmalayıcı türü bir veri anlaşması türü yansıtılamaz. XmlSerializer'ı kullanın.|  
|UriMustBeAbsolute|URI mutlak olmalı.|
