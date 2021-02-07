---
description: 'Daha fazla bilgi edinin: Service Framework'
title: Hizmet Çerçevesi
ms.date: 03/30/2017
ms.assetid: 75f60b87-f80e-4377-ba7c-8e6becaa2b28
ms.openlocfilehash: aa53a6c0740c292c1f34920edabdb81f7c5a13ab
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99686147"
---
# <a name="service-framework"></a>Hizmet Çerçevesi

Bu konu, Service Framework verileri tarafından oluşturulan tüm özel durumları listeler.  
  
## <a name="exception-list"></a>Özel durum listesi  
  
|Kaynak kodu|Kaynak dizesi|  
|-------------------|---------------------|  
|ABindingInstanceHasAlreadyBeenAssociatedTo1|Belirtilen Tekdüzen Kaynak tanımlayıcısını dinlemek için bir bağlama örneği zaten ilişkilendirilmiş. İki uç nokta aynı ListenUniform kaynak göstergesini paylaşmak isterseniz aynı bağlama nesnesi örneğini de paylaşmalıdır. İki çakışan uç nokta AddServiceEndpoint () çağrılarında, bir yapılandırma dosyasında ya da AddServiceEndpoint () ve yapılandırmanın bir birleşimi olarak belirtilmiştir.|  
|AChannelServiceEndpointIsNull0|Bir kanal veya hizmet uç noktası null.|  
|AChannelServiceEndpointSContractSNameIsNull0|Bir Channel/Service uç noktası sözleşme adı null veya boş.|  
|AChannelServiceEndpointSContractSNamespace0|Bir Channel/Service Endpoint Contract ad alanı null.|  
|BaseAddressCannotHaveFragment|Temel adres bir Tekdüzen Kaynak tanımlayıcı parçası içeremez.|  
|BaseAddressCannotHaveQuery|Temel adres Tekdüzen Kaynak tanımlayıcısı sorgu dizesi içeremez.|  
|Baseaddresscannothaveuserınfo|Temel adres bir Tekdüzen Kaynak tanımlayıcısı Kullanıcı bilgileri bölümü içeremez.|  
|BaseAddressDuplicateScheme|Bu koleksiyon zaten belirtilen düzene sahip bir adres içeriyor. Bu koleksiyondaki her bir şema için yalnızca bir adrese izin verilir.|  
|BaseAddressMustBeAbsolute|Yalnızca mutlak bir Tekdüzen Kaynak tanımlayıcısı, temel adres olarak kullanılabilir.|  
|BindingDoesnTSupportAnyChannelTypes1|Belirtilen bağlama herhangi bir kanal türü oluşturmayı desteklemiyor. Özel bağlamadaki bağlama öğeleri yanlış bir şekilde veya yanlış sırada. Yığın için en altta bir aktarım gereklidir. Bağlama öğeleri için önerilen sıra: TransactionFlow, ReliableSession, Security, Compositedupleks, OneWay, StreamSecurity, MessageEncoding, Transport.|  
|BindingDoesnTSupportDuplexButContractRequires1|Sözleşme için çift yönlü olmalıdır. Belirtilen bağlama bunu desteklemiyor ya da bunu destekleyecek biçimde yapılandırılmamış.|  
|BindingDoesnTSupportOneWayButContractRequires1|Sözleşme için OneWay gerekir. Belirtilen bağlama bunu desteklemiyor ya da bunu destekleyecek biçimde yapılandırılmamış.|  
|BindingDoesnTSupportRequestReplyButContract1|Sözleşme Istek/yanıt gerektiriyor. Belirtilen bağlama bunu desteklemiyor ya da bunu destekleyecek biçimde yapılandırılmamış.|  
|BindingDoesnTSupportSessionButContractRequires1|Sözleşme için oturum gerekiyor.  Belirtilen bağlama bunu desteklemiyor ya da bunu destekleyecek biçimde yapılandırılmamış.|  
|BindingDoesnTSupportTwoWayButContractRequires1|Sözleşme Two-Way gerektiriyor (istek-yanıt veya çift yönlü). Belirtilen bağlama bunu desteklemiyor ya da bunu destekleyecek biçimde yapılandırılmamış.|  
|BindingRequirementsAttributeDisallowsQueuedDelivery1|DeliveryRequirementsAttribute, QueuedDelivery 'e izin vermez. Uç noktanın belirtilen sözleşmeye sahip bağlaması bunu destekler.|  
|BindingRequirementsAttributeRequiresQueuedDelivery1|DeliveryRequirementsAttribute, QueuedDelivery gerektirir. Uç noktanın belirtilen sözleşmeye sahip bağlaması bunu desteklemiyor ya da bunu destekleyecek biçimde yapılandırılmamış.|  
|channelDoesNotHaveADuplexSession0|Geçerli kanal, çıkış oturumunun kapanışını desteklemiyor. Bu kanal ISessionChannel 'ı uygulamıyor \<IDuplexSession> .|  
|ClientRuntimeRequiresFormatter0|SerializeRequest ve DeserializeReply değerlerinin her ikisi de yanlış olmadığından, belirtilen Clienentoperation bir biçimlendirici gerektiriyor.|  
|CommunicationObjectAborted1|Belirtilen iletişim nesnesi, durdurulduğu için iletişim için kullanılamaz.|  
|CommunicationObjectAbortedStack2|Belirtilen iletişim nesnesi, durdurulduğu için iletişim için kullanılamaz: {1}|  
|Communicationobjectbaseclassmethodnotçağırılır|Belirtilen iletişim nesnesi sanal işlevi geçersiz kıldı, {1} ancak temel sınıfta tanımlanan sürümü çağırmıyor.|  
|ContractIsNotSelfConsistentItHasOneOrMore2|Belirtilen sözleşmede bir veya daha fazla IsInitiating veya ıısating olmayan işlem vardır. SessionMode özelliği SessionMode. Required olarak ayarlanamaz. IsInitiating ve ısterating öznitelikleri yalnızca bir oturum bağlamında kullanılabilir.|  
|CouldnTCreateChannelForChannelType2|Belirtilen kanal türü istendi, ancak belirtilen bağlama bunu desteklemiyor ya da bunu destekleyecek biçimde yapılandırılmamış.|  
|DispatchRuntimeRequiresFormatter0|DeserializeRequest ve SerializeReply değerlerinin her ikisi de yanlış olmadığından belirtilen DispatchOperation bir biçimlendirici gerektiriyor.|  
|EndMethodsCannotBeDecoratedWithOperationContractAttribute|IAsyncResult tasarım deseninin kullanıldığı sırada End metodu OperationContractAttribute ile kullanılamaz. OperationContractAttribute ile yalnızca ilgili Begin yöntemi kullanılabilir. Bu öznitelik Begin-End metot çiftine uygulanır.|  
|EndpointListenerRequirementsCannotBeMetBy3|Sözleşme belirtilen bu kanal türlerinden biri için destek gerektirdiğinden, ChannelDispatcher gereksinimleri belirtilen bağlama için IChannelListener tarafından karşılanamıyor. Ancak bağlama yalnızca belirtilen kanal türlerini destekler.|  
|EndpointsMustHaveAValidBinding0|Uç noktaların geçerli bir bağlaması olmalıdır.|  
|Invalidorunrecognizedadction|Belirtilen eylem geçersiz veya tanınmayan olduğundan ileti işlenemiyor.|  
|Multiplemebesınparameters|BindingContext 'in BindingParameters öğesinde birden fazla yalnızca bulundu. CustomBinding birden çok MessageEncodingBindingElements olamaz. Bu öğelerden biri hariç tümünü kaldırın.|  
|MultipleStreamUpgradeProvidersInParameters|BindingContext 'in BindingParameters öğesinde birden fazla ıstreamupgrade Providerelement bulundu. CustomBinding birden fazla ımımupgradeproviderelements içeremez. Bu öğelerden biri hariç tümünü kaldırın.|  
|NoChannelBuilderAvailable|Bağlama, bir TransportBindingElement içermediğinden kanal fabrikası veya kanal dinleyicisi oluşturmak için kullanılamaz. Her bağlamanın, TransportBindingElement öğesinden türeyen en az bir Binding öğesi olmalıdır.|  
|NotAllBindingElementsBuilt|Bu bağlamadaki bağlama öğelerinden bazıları kanal fabrikası ve kanal dinleyicisi oluşturulurken kullanılmadı. Bağlama öğeleri doğru şekilde sıralanmaz. Bağlama öğeleri için önerilen sıra: TransactionFlow, ReliableSession, Security, Compositedupleks, OneWay, StreamSecurity, MessageEncoding, Transport.  TransportBindingElement öğesinin en son olması gerektiğini unutmayın. Belirtilen bağlama öğeleri oluşturulmadı.|  
|RuntimeRequiresInvoker0|Dağıtım işlemi bir Invoker gerektirir.|  
|Servicehassıfırlama Appendpoints|Belirtilen hizmette hiçbir uygulama (altyapı olmayan) uç noktası yok. Bunun nedeni, uygulamanız için bir yapılandırma dosyası bulunamamış olması veya hizmet öğesinde hizmet adıyla eşleşen hiçbir hiçbir uç nokta bulunamadığı için olabilir.|  
|Sfxactionuyuşmazlığıdır|Bir eylem uyumsuzluğu nedeniyle yazılı bir ileti oluşturulamıyor. Belirtilen eylem bekleniyor ancak başka bir sorunla karşılaşıldı|  
|SFxAnonymousTypeNotSupported|Belirtilen iletideki belirtilen bölüm, türü anonim olduğu için RPC ile verilemez veya kodlanamaz.|  
|Sfxbadmetadatalocationnouygunluğunu Atebaseaddress|Bu URL, ExternalMetadataLocation özelliği veya yapılandırma bölümünün serviceMetadata bölümünde yer aldığı externalMetadataLocation özniteliği kullanılarak ServiceMetadataBehavior ile ilişkili bir URL idi ve bu, çözülecek temel bir adres yok.|  
|SFxBadMetadataMustBePolicy|Belirtilen ad alanına ve ada sahip bir ilke XmlElement sağlanmalıdır. Bu XmlElement, belirtilen ad alanına ve ada sahip.|  
|SFxBodyObjectTypeCannotBeInherited|Belirtilen tür, RPC stilindeki gövde nesnesi olarak kullanılacak nesne dışında herhangi bir sınıftan devralınabilir.|  
|SFxBodyObjectTypeCannotBeInterface|Belirtilen tür, RPC stilindeki gövde nesnesi için desteklenmeyen belirtilen arabirimini uyguluyor.|  
|SFxCallbackBehaviorAttributeOnlyOnDuplex|CallbackBehaviorAttribute, yalnızca bir çift yönlü sözleşmeyle bir uç noktada davranış olarak çalıştırılabilir. Belirtilen sözleşme çift yönlü değil ve geri çağırma işlemi içermiyor.|  
|SFxCallbackRequestReplyInOrder1|Geçerli Ileti işleme tamamlanana kadar bu işlemden yanıt alınamıyor. Sıra dışı ileti işlemeye izin vermek istiyorsanız, belirtilen bir veya birden çok alan için ConcurrencyMode belirtin.|  
|SfxCallbackTypeCannotBeNull|Belirtilen sözleşmeyi DuplexChannelFactory ile kullanmak için, sözleşmenin geçerli bir geri çağırma anlaşması belirtmesi gerekir. Sözleşmeniz için bir geri çağırma sözleşmesi varsa, DuplexChannelFactory yerine ChannelFactory kullanın.|  
|SFxCannotGetMetadataFromLocation|MetadataExchangeClient yalnızca HTTP ve HTTPS Metadataloterlerden meta verileri alabilir. Belirtilen meta verileri alamıyor.|  
|SFxCannotHttpGetMetadataFromAddress|MetadataExchangeClient, MetadataExchangeClientMode HttpGet kullanılırken yalnızca HTTP veya HTTPS adreslerinden meta verileri alabilir. Belirtilen meta verileri alamıyor.|  
|SFxCannotImportAsParameters_Bare|Belirtilen işlem ne RPC ne de belge sarmalandığından, ileti anlaşması oluşturuluyor.|  
|SFxCannotImportAsParameters_DifferentWrapperName|Belirtilen iletinin sarmalayıcı adı varsayılan değerle eşleşmediğinden ileti anlaşması oluşturuluyor.|  
|SFxCannotImportAsParameters_DifferentWrapperNs|Belirtilen iletinin sarmalayıcı ad alanı varsayılan değerle eşleşmediğinden ileti anlaşması oluşturuluyor.|  
|SFxCannotImportAsParameters_ElementIsNotNillable|Belirtilen ad alanındaki belirtilen öğe adı boş bırakılabilir olarak işaretlenmediğinden bir ileti sözleşmesi oluşturuluyor.|  
|SFxCannotImportAsParameters_HeadersAreUnsupported|Belirtilen iletinin üst bilgileri olduğundan ileti anlaşması oluşturuluyor.|  
|SFxCannotImportAsParameters_Message|Belirtilen işlem bağımsız değişken veya dönüş türü olarak türsüz bir Ileti içerdiğinden, bir ileti sözleşmesi oluşturuluyor.|  
|SFxCannotImportAsParameters_MessageHasProtectionLevel|Belirtilen ileti koruma gerektirdiğinden ileti anlaşması oluşturuluyor.|  
|SFxCannotImportAsParameters_NamespaceMismatch|Belirtilen ileti bölümü ad alanı varsayılan değerle eşleşmediğinden ileti anlaşması oluşturuluyor.|  
|SFxCannotRequireBothSessionAndDatagram3|Belirtilen sözleşme SessionMode. NotAllowed belirtiyor ve belirtilen sözleşme SessionMode. Required belirtiyor. SessionMode değerlerinden birini değiştirin veya her bitiş noktası için farklı bir adres veya ListenURI belirtin.|  
|Sfxcannotse/2 Sionsbyındex|Bu koleksiyon, uzantıları dizine göre ayarlamayı desteklemiyor. InsertItem veya RemoveItem yöntemlerini kullanın.|  
|SFxChannelDispatcherDifferentHost0|ChannelDispatcher Şu anda sağlanmış olan ServiceHost öğesine bağlı değil.|  
|SFxChannelDispatcherMultipleHost0|ChannelDispatcher birden fazla ServiceHost 'a eklenemez.|  
|SFxChannelDispatcherNoHost0|ChannelDispatcher bir ServiceHost öğesine eklenmediğinden açılamıyor.|  
|Sfxchannelfactoryatıldı|ChannelFactory zaten atılmış olduğundan bu ChannelFactory açılamıyor. ChannelFactory öğesini kullanmadan önce oluşturun.|  
|SFxChannelFactoryNoBinding|Bir bağlama, uç noktasıyla ilişkili olmadığından ChannelFactory açılamıyor. Oluşturucuya veya Endpoint özelliğine sahip bir bağlama belirtin.|  
|SFxChannelTerminated0|Isterating olarak işaretlenen bir işlem bu kanalda zaten çağrıldı, kanal bağlantısının sonlandırılmasına neden oldu. Bu kanalda başka işlem çağrılamaz. İletişime devam etmek için kanalı yeniden oluşturun.|  
|SFxCloseTimedOut1|ServiceHost kapatma işlemi, belirtilen tarihten sonra durdu. Bunun nedeni, bir istemcinin gereken süre içinde oturumsuz bir kanalı kapatması başarısız olabilir. Bu işlem için izin verilen süre, daha uzun bir zaman aşımının parçası olabilir.|  
|SfxCloseTimedOutWaitingForDispatchToComplete|Hizmet dağıtımının tamamlanması beklenirken kapatma işlemi zaman aşımına uğradı.|  
|SFxCodeGenIsNotAssignableFrom|Belirtilen atanamıyor.|  
|SFxConfigChannelConfigurationNotFound|ServiceModel istemci yapılandırması bölümünde belirtilen ad ve sözleşmeye sahip uç nokta öğesi bulunamıyor.|  
|SFxConflictingGlobalElement|Belirtilen ad alanında belirtilen ada sahip en üst düzey genişletilebilir biçimlendirme dili öğesi belirtilen türe başvuramaz. Zaten farklı bir türe başvuruyor. İleti veya ileti parçaları için farklı bir ad belirtmek üzere farklı bir işlem adı veya MessageBodyAttribute kullanın.|  
|Sfxcontracthassıfırlaması ınitiatingoperations|Bir sözleşmede en az bir IsInitiating = true işlemi olmalıdır.|  
|Sfxcontracthassıfırlaması Işlemleri|Bir sözleşmede en az bir işlem olmalıdır.|  
|Sfxcontractınheritancerequiresınterfaces|Belirtilen türdeki hizmet sınıfı bir ServiceContract tanımlıyor ve belirtilen türden bir ServiceContract devralıyor. Sözleşme devralma yalnızca arabirim türleri arasında kullanılabilir. Bir sınıf ServiceContractAttribute ile işaretlenmişse, hiyerarşide ServiceContractAttribute ile tek tür olmalıdır.  Belirtilen türdeki ServiceContractAttribute öğesini belirtilen türün uyguladığı ayrı bir arabirime taşıyın.|  
|SFxCreateDuplexChannel1|Belirtilen sözleşmenin geri çağırma anlaşması yok ya da herhangi bir işlem tanımlamıyor. Bu bir çift yönlü sözleşme değilse, DuplexChannelFactory yerine ChannelFactory kullanın.|  
|SFxCreateDuplexChannelNoCallback|Bu CreateChannel aşırı yükü, DuplexChannelFactory öğesinin bu örneğinde çağrılamaz. DuplexChannelFactory bir InstanceContext ile başlatılmadı. Bir InstanceContext alan CreateChannel aşırı yüklemesini çağırın.|  
|SFxCreateDuplexChannelNoCallback1|Bu CreateChannel aşırı yükü, DuplexChannelFactory öğesinin bu örneğinde çağrılamaz. DuplexChannelFactory bir türle başlatılmış ve geçerli bir InstanceContext sağlanmadı. Bir InstanceContext alan CreateChannel aşırı yüklemesini çağırın.|  
|SFxCreateDuplexChannelNoCallbackUserObject|Bu CreateChannel aşırı yükü, DuplexChannelFactory öğesinin bu örneğinde çağrılamaz. DuplexChannelFactory öğesine belirtilen InstanceContext geçerli bir UserObject içermiyor.|  
|SFxCreateNonDuplexChannel1|ChannelFactory belirtilen sözleşmeyi desteklemiyor. ChannelFactory bir veya daha fazla işlem içeren bir geri çağırma anlaşması tanımlar. ChannelFactory yerine DuplexChannelFactory kullanın.|  
|SFxCustomBindingNeedsTransport1|Belirtilen sözleşmeye sahip olan ServiceEndpoint üzerinde CustomBinding bir TransportBindingElement öğesine sahip değil. Her bağlamanın, TransportBindingElement öğesinden türeyen en az bir Binding öğesi olmalıdır.|  
|SFxCustomBindingWithoutTransport|Bu özel bağlama bir TransportBindingElement öğesine sahip olmadığından, şema bu özel bağlama için hesaplanamıyor. Her bağlamanın, TransportBindingElement öğesinden türeyen en az bir Binding öğesi olmalıdır.|  
|Sfxdatacontractserializerynotsupportbarearray|DataContractSerializer, belirtilen öğede belirtilen koleksiyonu desteklemiyor.|  
|SFxDictionaryIsEmpty|Sözlük boş olduğundan işlem gerçekleştirilemiyor.|  
|SFxDocEncodedNotSupported|Belirtilen yansıtılırken hata oluştu. Document-Encoded desteklenmez. ' Use ' değerini literal veya ' Style ' olarak RPC 'ye değiştirin.|  
|SFxDuplicateInitiatingActionAtSameVia|Bu hizmette, belirtilen sayıda dinleme yapan birden fazla uç nokta vardır. Uç noktalar, belirtilen başlatma eylemini paylaşır. Dağıtıcı iletiyi işlemeye yönelik doğru uç noktayı belirleyemediği için bu eyleme sahip iletiler bırakılır.|  
|SFXEndpointBehaviorUsedOnWrongSide|Belirtilen IEndpointBehavior sunucuda kullanılamıyor. Bu davranış yalnızca istemciler için geçerli olabilir.|  
|SFxEndpointNoMatchingScheme|Belirtilen bağlamaya sahip uç nokta için belirtilen şemayla eşleşen temel adres bulunamıyor. Kayıtlı temel adres düzenleri belirtildi.|  
|SFxErrorCreatingMtomReader|İleti iletimi iyileştirme mekanizması iletisi için bir okuyucu oluşturulurken hata oluştu.|  
|SFxErrorDeserializingFault|Sunucu geçersiz bir basit nesne erişim Protokolü hatası döndürdü. Daha fazla ayrıntı için InnerException öğesine bakın.|  
|SFxErrorDeserializingHeader|Belirtilen iletideki üst bilgilerden birinin serisi kaldırılırken bir hata oluştu. Daha fazla ayrıntı için lütfen InnerException öğesine bakın.|  
|SFxErrorReflectingOnMethod3|Belirtilen bir türdeki belirtilen metoda belirtilen öznitelik yüklenirken bir hata oluştu.  Daha fazla ayrıntı için InnerException öğesine bakın.|  
|SFxErrorReflectingOnParameter4|Belirtilen türdeki belirtilen metodun belirtilen parametresine belirtilen öznitelik yüklenirken bir hata oluştu. Daha fazla ayrıntı için InnerException öğesine bakın.|  
|SFxErrorReflectingOnType2|Belirtilen tür üzerine belirtilen öznitelik yüklenirken bir hata oluştu.  Daha fazla ayrıntı için InnerException öğesine bakın.|  
|SFxErrorSerializingBody|Belirtilen iletinin gövdesi serileştirilirken bir hata oluştu. Daha fazla ayrıntı için InnerException öğesine bakın.|  
|SFxErrorSerializingHeader|Belirtilen iletideki üst bilgilerden biri serileştirilirken bir hata oluştu. Daha fazla ayrıntı için InnerException öğesine bakın.|  
|SFxExpectedIMethodCallMessage|İç Hata. İleti geçerli bir IMethodCallMessage olmalıdır.|  
|SFxExportMustHaveType|Belirtilen işlemdeki belirtilen bölüm geçerli bir CLR türüne sahip olmadığından verilemiyor.|  
|SFxHeaderNotUnderstood|İleti işlenmedi. Belirtilen ad alanındaki belirtilen üst bilgi, bu iletinin alıcısı tarafından anlaşılmadı. Bu hata genellikle bu iletinin göndericisinin alıcının işleyemeyeceği bir iletişim protokolünü etkinleştirdiğini gösterir. İstemci bağlamasının yapılandırmasının hizmetin bağlamasıyla tutarlı olduğundan emin olun.|  
|SFxHeadersAreNotSupportedInEncoded|Belirtilen ileti, uzak yordam çağrısı kodlanmış stilinde kullanılacak üst bilgilere sahip olmamalıdır.|  
|Sfxıntattentwsdloperationstyleınmessageparts|Belirtilen işlemdeki iletinin tüm bölümlerinin bir tür ya da öğe içermesi gerekir.|  
|Sfxıntattentwsdloperationstyleınoperationmessages|Belirtilen işlemdeki iletilerden çıkarılan belirtilen stil, bağlamalar kullanılarak belirtilen beklenen stille eşleşmiyor.|  
|Sfxınvalidcallbackiasyncresult|IAsyncResult sağlanmadı ya da yanlış türde.|  
|Sfxınvalidmessagebody|OperationFormatter geçersiz bir ileti gövdesiyle karşılaştı. Belirtilen ad ve ad alanına sahip ' element ' düğüm türü bekleniyordu. Belirtilen ad ve ad alanına sahip belirtilen düğüm türü bulundu.|  
|Sfxınvalidmessagebodyemptymessage|İleti boş olduğu için OperationFormatter, iletideki bilgilerin serisini kaldıramıyor.|  
|Sfxınvalidmessagebodyerrordeserializingparameter|Belirtilen parametrenin serisi kaldırılmaya çalışılırken bir hata oluştu. Daha fazla bilgi için InnerException öğesine bakın.|  
|Sfxınvalidmessagebodyerrorserializingparameter|Belirtilen parametre Serileştirmeye çalışılırken bir hata oluştu. InnerException iletisi belirtildi.  Daha fazla ayrıntı için InnerException öğesine bakın.|  
|SFxInvalidMessageBodyUnexpectedNode|Parametrelerin serisi kaldırılırken belirtilen ad alanından belirtilen beklenmeyen düğüm ile karşılaşıldı.|  
|Sfxınvalidmessagecontractsignature|Belirtilen işlem, MessageContractAttribute ile işaretlenmiş bir parametre ya da dönüş türü içeriyor. Bir istek iletisini temsil eden bir ileti sözleşmesi kullanırken, işlem MessageContractAttribute ile işaretlenmiş tek bir parametreye sahip olmalıdır. Yanıt iletisini temsil eden bir ileti sözleşmesi kullanırken, işlemin dönüş değeri MessageContractAttribute ile işaretlenmiş bir tür olmalıdır. İşlem ' Out ' veya ' ref ' parametrelerine sahip olamaz.|  
|SFxInvalidReplyAction|İşlemin giden yanıt iletisi belirtilen eyleme sahip, ancak bu işlem için sözleşme başka bir ReplyAction belirtiyor. İletide belirtilen eylem, sözleşmesindeki ReplyAction eşleşmelidir veya işlem sözleşmesi ReplyAction = ' * ' belirtmelidir.|  
|Sfxınvalidrequestaction|İşlem için giden istek iletisi belirtilen eyleme sahip, ancak bu işlem için sözleşme başka bir Istek öğesine ait anlaşma belirtiyor. İletide belirtilen eylem, sözleşmede RequestAction ile eşleşmelidir veya işlem sözleşmesinin RequestAction = ' * ' belirtmesi gerekir.|  
|SFxInvalidStaticOverloadCalledForDuplexChannelFactory1|Bu sözleşme bir geri çağırma sözleşmesi tanımladığından, statik CreateChannel yöntemi belirtilen sözleşmeyle birlikte kullanılamaz. DuplexChannelFactory üzerinde statik CreateChannel aşırı yüklemelerinin birini kullanın \<TChannel> .|  
|Sfxınvalidstreaminrequest|Belirtilen işlemdeki isteğin bir akış olması için işlem, türü Stream olan bir tek parametreye sahip olmalıdır.|  
|Sfxınvalidstreaminresponse|Belirtilen işlemdeki yanıtın bir akış olması için işlemin, türü Stream olan bir tek parametre veya dönüş değeri olması gerekir.|  
|Sfxınvalidstreamintypedmessage|Akışları Ileti sözleşmesi programlama modeliyle kullanmak için, belirtilen türün türü Stream olan tek bir MessageBody üyesine sahip olması gerekir.|  
|Sfxınvaliduseofprimitiveoperationformatter|PrimitiveOperationFormatter öğesine desteklemediği bir parametre veya dönüş türü verdi.|  
|SFxMessageContractBaseTypeNotValid|Belirtilen tür bir MessageContract tanımlar ve bir MessageContract tanımlamayan belirtilen bir türden türetilir. Belirtilen devralma hiyerarşisindeki tüm nesneler bir MessageContract tanımlamalıdır.|  
|SFxMethodNotSupported1|Belirtilen yöntem bu nesnede desteklenmiyor. Bu durum, yöntemin OperationContractAttribute ile işaretlenmemiş olması ya da arabirim türünün ServiceContractAttribute ile işaretlenmemiş olması durumunda gerçekleşebilir.|  
|SFxMethodNotSupportedByType2|Belirtilen ServiceHost uygulama türü belirtilen hizmet sözleşmesini uygulamıyor.|  
|SFxMethodNotSupportedOnCallback1|Belirtilen geri çağırma yöntemi desteklenmiyor. Bu durum, yöntemin OperationContractAttribute ile işaretlenmemiş olması ya da arabirim türünün ServiceContractAttribute CallbackContract öğesinin hedefi olmaması olabilir.|  
|SFxMismatchedOperationParent|Bir DispatchOperation veya Clienentoperation, sırasıyla yalnızca kendi üst DispatchRuntime veya ClientRuntime eklenebilir.|  
|SFxNameCannotBeEmpty|Name özelliği boş bir dize olamaz.|  
|SfxNoTypeSpecifiedForParameter|Parametresi için CLR türü belirtilmedi, bu işlem oluşturulmasını engelliyor.|  
|SFxOperationBehaviorAttributeOnlyOnServiceClass|OperationBehaviorAttribute yalnızca hizmet sınıfına gidebilir. ServiceContract arabirimine konulamıyor. Belirtilen türdeki belirtilen yöntem bunu ihlal ediyor.|  
|SFxOperationContractOnNonServiceContract|Belirtilen metot OperationContractAttribute ile işaretlenmiş, ancak kapsayan belirtilen tür ServiceContractAttribute ile işaretlenmemiş. OperationContractAttribute, yalnızca ServiceContractAttribute türlerindeki yöntemlerde veya CallbackContract türlerinde kullanılabilir.|  
|Sfxparametercountuyuşmazlığıdır|Sağlanan bağımsız değişken sayısı ile beklenen bağımsız değişkenlerin sayısı arasında bir uyuşmazlık oluştu. Özellikle, belirtilen bağımsız değişken belirtilen sayıda öğe içeriyor, ancak beklenen bağımsız değişken belirtilen sayıda öğe içeriyor.|  
|Sfxpartnamemustbeuniqueınrpc|Belirtilen ileti bölümü adı, uzak yordam çağrısı iletisinde benzersiz değil.|  
|SFxReplyActionMismatch3|Belirtilen işlem için belirtilen eyleme sahip bir yanıt iletisi alındı. Ancak, istemci kodunuz belirtilen eylemi gerektirir.|  
|SFxRequestReplyNone|"None" adresine hedeflenmiş WS-Addressing ReplyTo veya FaultTo üstbilgisiyle bir ileti alındı. Bu değerler, istek-yanıt işlemleri için geçerli değildir. "None" öğesinin ReplyTo veya FaultTo değerlerini desteklemesi gerekiyorsa tek yönlü bir işlem kullanın veya ManualAddressing Işlevini etkinleştirin.|  
|SFxRequestTimedOut1|Bu istek işlemi belirtilen yapılandırılan süre içinde bir yanıt almadı. İzin verilen süre, daha uzun bir zaman aşımının parçası olabilir. Bunun nedeni hizmetin işlemi hala işlemesi veya hizmetin bir yanıt iletisi gönderemediği olabilir.|  
|SFxRequestTimedOut2|Belirtilen konuma gönderilen istek işlemi belirtilen yapılandırılan süre içinde yanıt almadı. İzin verilen süre, daha uzun bir zaman aşımının parçası olabilir. Bunun nedeni hizmetin işlemi hala işlemesi veya hizmetin bir yanıt iletisi gönderemediği olabilir.|  
|Sfxschema, Notcontaintype|Belirtilen hedef ad alanına sahip şema, belirtilen ada sahip bir tür içermiyor.|  
|SfxServiceContractAttributeNotFound|Belirtilen sözleşme türüne ServiceContractAttribute ile öznitelik yok. Geçerli bir sözleşme tanımlamak için, belirtilen türün ServiceContractAttribute ile ilişkilendirilmesi gerekir. Tür bir sözleşme arabirimi ya da bir hizmet sınıfı olabilir.|  
|SFxServiceContractGeneratorConfigRequired|GenerateServiceEndpoint metodunu kullanarak yapılandırma bilgilerini oluşturmak için, ServiceContractGenerator örneği geçerli bir yapılandırma nesnesiyle başlatılmalıdır.|  
|SFxServiceHostBaseCannotAddEndpointAfterOpen|Uç noktalar, ServiceHost aşağıdaki durumlardan birinde olduktan sonra eklenemez:<br /><br /> -Açıldı<br />-Hata verdi<br />-Sona erdirildi<br />-Kapalı|  
|SFxServiceHostBaseCannotAddEndpointWithoutDescription|Bitiş noktaları, açıklama özelliği başlatılmadan eklenemiyor.|  
|SFxServiceMetadataBehaviorNoHttpBaseAddress|ServiceMetadataBehavior HttpGetEnabled özelliği true olarak ayarlanır ve HttpGetUrl özelliği göreli bir adrestir, ancak HTTP temel adresi yoktur. Bir HTTP temel adresi sağlayın ya da HttpGetUrl öğesini mutlak bir adres olarak ayarlayın.|  
|SFxServiceMetadataBehaviorNoHttpsBaseAddress|ServiceMetadataBehavior HttpsGetEnabled özelliği true olarak ayarlanır ve HttpsGetUrl özelliği göreli bir adrestir, ancak HTTPS temel adresi yoktur. Bir HTTPS temel adresi sağlayın ya da HttpsGetUrl öğesini mutlak bir adres olarak ayarlayın.|  
|SFxServiceMetadataBehaviorUrlMustBeHttpOrRelative|Davranış URL 'Si, göreli bir Tekdüzen Kaynak tanımlayıcısı veya belirtilen şemayla mutlak bir Tekdüzen Kaynak tanımlayıcısı olmalıdır. Belirtilen URL, belirtilen düzene sahip mutlak bir Tekdüzen kaynak tanımlayıcısıdır.|  
|SFxStreamRequestMessageClosed|Bu akışı içeren ileti kapatıldı. Hizmet işlemi geri döndüğünde istek akışlarına erişilemez.|  
|SFxStreamResponseMessageClosed|Bu akışı içeren ileti kapatıldı.|  
|Sfxsonlandıraterequestprocessingexception|İşlem ardışık düzeninde bir uzantının bu iletiyi işlemesini sonlandırmalıdır.|  
|SFxTerminatingOperationAlreadyCalled1|Bu kanal, ısterating işlemi çağrıldığından daha fazla ileti gönderemiyor.|  
|SFxThrottleLimitMustBeGreaterThanZero0|Kısıtlama sınırı sıfırdan büyük olmalıdır. Kısıtlama sınırını devre dışı bırakmak için değeri Int32. MaxValue olarak ayarlayın.|  
|Sfxtypedoruntypedmessagecannotbemixedwithkaçındinrpc|RPC kodlu stili kullanırken, işlem parametre yoksa veya void dönüş değerine sahipse ileti sözleşmesi türleri veya System. ServiceModel. Channels. Message türü kullanılamaz. Belirtilen işleme bir parametre veya dönüş türü olarak boş bir ileti sözleşme türü ekleyin.|  
|SFxUserCodeThrewException|Belirtilen kullanıcı işlemi kullanıcı kodunda işlenmemiş bir özel durum oluşturdu. Bu yinelenen bir sorun ise, belirtilen metodun uygulamasında bir hata olduğunu gösteriyor olabilir.|  
|SfxUseTypedMessageForCustomAttributes|Belirtilen parametre ek öznitelikler gerektirdiğinden, işlem parametresine eşlenemez.|  
|SFxVersionMismatchInOperationContextAndMessage2|OperationContext. Current içindeki MessageVersion işlenen iletinin üstbilgi sürümüyle eşleşmediğinden, giden üst bilgiler iletiye eklenemiyor|  
|SFxWellKnownNonSingleton0|Hizmet örneği alan ServiceHost oluşturucularından birini kullanmak için, hizmetin InstanceContextMode değerinin InstanceContextMode. single olarak ayarlanması gerekir. Bu, ServiceBehaviorAttribute kullanılarak yapılandırılabilir. Aksi takdirde, bir tür bağımsız değişkeni alan ServiceHost oluşturucularını kullanın.|  
|SFxWrapperTypeHasMultipleNamespaces|Birden çok ad alanı olduğundan, belirtilen ileti için sarmalayıcı türü bir veri anlaşması türü olarak yansıtılmıyor. XmlSerializer 'ı kullanın.|  
|UriMustBeAbsolute|URI mutlak olmalıdır.|
