---
title: Veri Sözleşmesi Yedekleri
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts [WCF], surrogates
ms.assetid: 8c31134c-46c5-4ed7-94af-bab0ac0dfce5
ms.openlocfilehash: cc0772cbb35f7c149af7eac04239d7349fa79f27
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797205"
---
# <a name="data-contract-surrogates"></a>Veri Sözleşmesi Yedekleri
Veri anlaşması *yedeği* , veri anlaşması modeli üzerine inşa olan gelişmiş bir özelliktir. Bu özellik, kullanıcıların bir türün serileştirilme, seri durumdan çıkarılan veya yansıtılma göre meta verileri değiştirmek istedikleri durumlarda tür özelleştirmesi ve değiştirme için kullanılmak üzere tasarlanmıştır. Bir vekil 'in kullanılabileceği bazı senaryolar tür için bir veri anlaşması belirtilmediğinde, alanlar ve Özellikler <xref:System.Runtime.Serialization.DataMemberAttribute> öznitelik ile işaretlenmez veya kullanıcılar dinamik olarak şema çeşitlemeleri oluşturmak istiyor.  
  
 Serileştirme ve seri durumdan çıkarma, .NET Framework, XML gibi uygun bir <xref:System.Runtime.Serialization.DataContractSerializer> biçime dönüştürmek için kullanılırken veri sözleşmesi yedeği ile gerçekleştirilir. Veri sözleşmesi yedek, XML şema belgeleri (XSD) gibi meta veri gösterimleri üretilirken türler için aktarılmış meta verileri değiştirmek için de kullanılabilir. İçeri aktarma işleminden sonra kod meta verilerden oluşturulur ve yedek bu durumda, oluşturulan kodu özelleştirmek için kullanılabilir.  
  
## <a name="how-the-surrogate-works"></a>Vekil nasıl kullanılır?  
 Bir vekil, bir tür ("orijinal" tür) diğer bir türe ("yedeklerin Gated" türü) eşleyerek işe yarar. Aşağıdaki örnek orijinal türünü `Inventory` ve yeni bir yedek `InventorySurrogated` türünü gösterir. Tür serileştirilebilir değil, `InventorySurrogated` ancak tür: `Inventory`  
  
 [!code-csharp[C_IDataContractSurrogate#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#1)]  
  
 Bu sınıf için bir veri sözleşmesi tanımlanmadığı için, sınıfı bir veri sözleşmesine sahip bir yedek sınıfa dönüştürün. Yedeklerin Gated class aşağıdaki örnekte gösterilmiştir:  
  
 [!code-csharp[C_IDataContractSurrogate#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#2)]  
  
## <a name="implementing-the-idatacontractsurrogate"></a>Idatacontractvekil uygulama  
 Veri sözleşmesi yedek öğesini kullanmak için <xref:System.Runtime.Serialization.IDataContractSurrogate> arabirimini uygulayın.  
  
 Aşağıda, olası bir uygulamayla <xref:System.Runtime.Serialization.IDataContractSurrogate> ilgili her bir yönteme genel bakış verilmiştir.  
  
### <a name="getdatacontracttype"></a>GetDataContractType  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> Yöntemi bir türü diğerine eşler. Serileştirme, seri durumdan çıkarma, içeri aktarma ve dışarı aktarma için bu yöntem gereklidir.  
  
 İlk görev, diğer türlere hangi türlerin eşlenildiğini tanımlar. Örneğin:  
  
 [!code-csharp[C_IDataContractSurrogate#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#3)]  
  
- Serileştirme sırasında, bu yöntem tarafından döndürülen eşleme daha sonra <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> yöntemi çağırarak orijinal örneği bir yedeklerin geçitli örneğine dönüştürmek için kullanılır.  
  
- Seri durumdan çıkarma sırasında, bu yöntem tarafından döndürülen eşleme, seri hale getirici tarafından, yedek türünün bir örneğinde seri durumdan çıkarmak için kullanılır. Daha sonra, <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%2A> yedekleri bulunan örneği orijinal türün bir örneğine dönüştürmeyi çağırır.  
  
- Dışarı aktarma sırasında, bu yöntem tarafından döndürülen vekil türü, meta verileri oluşturmak için kullanılacak veri sözleşmesini almak üzere yansıtılır.  
  
- İçeri aktarma işleminde, başlangıç türü, destek gibi amaçlarla kullanılacak veri sözleşmesini almak için yansıtılan bir vekil türüne değiştirilir.  
  
 <xref:System.Type> Parametresi seri hale getirilen, seri durumdan çıkarılan, içeri aktarılan veya aktarılan nesnenin türüdür. Yedek türü işlemezse yöntemin giriş türünü döndürmesi gerekir. <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> Aksi takdirde, uygun yedeklerin geçitli türünü döndürün. Birden fazla yedek tür varsa, bu yöntemde çok sayıda eşleme tanımlanabilir.  
  
 Yöntemi, <xref:System.Int32> veya<xref:System.String>gibi yerleşik veri anlaşması temelleri için çağrılmaz. <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> Diziler, Kullanıcı tanımlı türler ve diğer veri yapıları gibi diğer türler için, bu yöntem her bir tür için çağrılır.  
  
 Önceki örnekte, yöntemi `type` parametrenin ve `Inventory` karşılaştırılabilir olup olmadığını denetler. Öyleyse, yöntemi ile `InventorySurrogated`eşlenir. Bir serileştirme, seri kaldırma, içeri aktarma şeması veya dışa aktarma şeması çağrıldığında, türler arasındaki eşlemeyi belirlemekte bu işlev ilk olarak çağırılır.  
  
### <a name="getobjecttoserialize-method"></a>GetObjectToSerialize yöntemi  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> Yöntemi, özgün tür örneğini yedeklerin geçişli tür örneğine dönüştürür. Serileştirme için yöntemi gerekir.  
  
 Bir sonraki adım, <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> yöntemi uygulayarak fiziksel verilerin özgün örnekten vekil 'e eşlenme şeklini tanımlamaktır. Örneğin:  
  
 [!code-csharp[C_IDataContractSurrogate#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#4)]  
  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> Yöntemi bir nesne serileştirildiğinde çağrılır. Bu yöntem, verileri özgün türünden yedeklerin geçişli tür alanlarına aktarır. Alanlar doğrudan vekil alanlarla eşleştirilebilir veya orijinal verilerin düzenlemeleri vekil içinde depolanabilir. Bazı olası kullanımlar şunlardır: alanları doğrudan eşleme, yedekleri geçitli alanlarda depolanacak veriler üzerinde işlem yapma veya orijinal türün XML 'sini, yedekleri geçitli alanda depolama.  
  
 `targetType` Parametresi, üyenin belirtilen türüne başvurur. Bu parametre, <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> yöntemi tarafından döndürülen yedeklerin kapılı türüdür. Seri hale getirici, döndürülen nesnenin bu türe atanabilir olmasını zorunlu kılmaz. `obj` Parametresi, seri hale getirilecek nesnedir ve gerekirse, bu nesnenin vekil değerine dönüştürülür. Bu yöntem, bir yedeklerin, nesneyi işlemezse giriş nesnesini döndürmelidir. Aksi takdirde, yeni yedek nesne döndürülür. Nesne null ise vekil çağrılmaz. Farklı örnekler için çok sayıda vekil eşleme bu yöntem içinde tanımlanabilir.  
  
 Bir <xref:System.Runtime.Serialization.DataContractSerializer>oluştururken, bunu nesne başvurularını koruyacak şekilde bildirebilirsiniz. (Daha fazla bilgi için bkz. [serileştirme ve serisini kaldırma](../feature-details/serialization-and-deserialization.md).) Bu, oluşturucusunun içindeki `preserveObjectReferences` parametresi olarak `true`ayarlanarak yapılır. Bu durumda, sonraki tüm serileştirmeler yalnızca akışa başvuru yazdığından, bir nesne için yedek yalnızca bir kez çağırılır. `preserveObjectReferences` Olarak`false`ayarlanırsa, bir örnek ile karşılaşıldığında, yedek çağırılır.  
  
 Seri hale getirilmiş Örneğin türü, belirtilen türden farklıysa, örneğin, `xsi:type` örneğin diğer uçta seri durumdan çıkarılmaya izin vermek için tür bilgileri akışa yazılır. Bu işlem, nesnenin yedeklerin yapılıp yapılmayacağını belirtir.  
  
 Yukarıdaki örnek, örneğin verisini `Inventory` öğesine `InventorySurrogated`dönüştürür. Nesnenin türünü denetler ve yedeklerin kapılı türe dönüştürmek için gerekli düzenlemeleri gerçekleştirir. Bu durumda, `Inventory` sınıfının alanları doğrudan `InventorySurrogated` sınıf alanlarına kopyalanır.  
  
### <a name="getdeserializedobject-method"></a>GetDeserializedObject yöntemi  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%2A> Yöntemi, yedeklerin kapılı tür örneğini orijinal tür örneğine dönüştürür. Seri durumdan çıkarma için gereklidir.  
  
 Sonraki görev, fiziksel verilerin vekil örnekten orijinale nasıl eşleştirilecektir. Örneğin:  
  
 [!code-csharp[C_IDataContractSurrogate#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#5)]  
  
 Bu yöntem yalnızca bir nesnenin serisini kaldırma işlemi sırasında çağrılır. Yedek türden seri durumundan çıkarma için, özgün türüne geri doğru veri eşleme sağlar. `GetObjectToSerialize` Yönteme benzer şekilde, bazı olası kullanımlar alan verilerini doğrudan değiş tokuş etmek, veriler üzerinde işlemler gerçekleştirmek ve XML verilerini depolamak olabilir. Seri durumdan çıkarma sırasında, veri dönüştürmesinde yapılan düzenlemeler nedeniyle her zaman özgün verilerden tam veri değerlerini elde edebilirsiniz.  
  
 `targetType` Parametresi, üyenin belirtilen türüne başvurur. Bu parametre, `GetDataContractType` yöntemi tarafından döndürülen yedeklerin kapılı türüdür. `obj` Parametresi, serisi kaldırılan nesneye başvurur. Nesne, bir yedek ise özgün türüne dönüştürülebilir. Bu yöntem, yedek nesneyi işlemezse giriş nesnesini döndürür. Aksi takdirde, seri durumdan çıkarılan nesne, dönüştürme işlemi tamamlandıktan sonra döndürülür. Birden fazla yedek tür varsa, her bir türü ve dönüşümünü belirterek, her biri için, vekil 'ten birincil türe veri dönüştürme sağlayabilirsiniz.  
  
 Bir nesne döndürüldüğünde, iç nesne tabloları bu vekil tarafından döndürülen nesneyle güncelleştirilir. Bir örneğe yapılan sonraki başvurular, nesne tablolarından yedeklerin geçitli örneğini elde eder.  
  
 Önceki örnek, türü `InventorySurrogated` nesneleri ilk türe `Inventory`geri dönüştürür. Bu durumda, veriler doğrudan içindeki `InventorySurrogated` `Inventory`karşılık gelen alanlara geri aktarılır. Veri düzenlemeleri bulunmadığından, her üye alanı serileştirme öncesindeki değerlerle aynı değerleri içerecektir.  
  
### <a name="getcustomdatatoexport-method"></a>GetCustomDataToExport yöntemi  
 Bir şemayı <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%2A> dışarı aktarırken Yöntem isteğe bağlıdır. Bu, diğer verileri veya ipuçlarını, dışarıya aktarılmış şemaya eklemek için kullanılır. Ek veriler üye düzeyinde veya tür düzeyinde eklenebilir. Örneğin:  
  
 [!code-csharp[C_IDataContractSurrogate#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#6)]  
  
 Bu Yöntem (iki aşırı yükleme ile), ek bilgilerin üye veya tür düzeyinde meta verilere eklenmesine olanak sunar. Bir üyenin genel mi yoksa özel mi olduğunu ve şemanın dışa ve içeri aktarılması boyunca korunacak açıklamaları eklemek mümkündür. Bu tür bilgiler bu yöntem olmadan kaybedilir. Bu yöntem üye veya türlerin eklenmesine veya silinmesine neden olmaz, bunun yerine bu düzeylerin her birindeki şemalara daha fazla veri ekler.  
  
 Yöntemi aşırı yüklendi ve `Type` bir (`clrtype` parametre) ya <xref:System.Reflection.MemberInfo> da (`memberInfo` parametre) alabilir. İkinci parametre her zaman bir `Type` (`dataContractType` parametre). Bu yöntem, her üye için ve yedeklerin Gated `dataContractType` Type türü için çağrılır.  
  
 Bu aşırı yüklemelerin her biri ya da `null` serileştirilebilir bir nesne döndürmelidir. Null olmayan bir nesne, bir ek açıklama olarak, verilecek şemaya seri hale getirilebilir. Aşırı yüklemede, şemaya aktarılmış her tür, `dataContractType` parametre olarak yedeklerin geçitli türü ile birlikte ilk parametrede bu yönteme gönderilir. `Type` Aşırı yükleme için, şemaya aktarılmış her üye, bilgilerini ikinci parametrede yedeklerin geçitli türü olan `memberInfo` parametre olarak gönderir. `MemberInfo`  
  
#### <a name="getcustomdatatoexport-method-type-type"></a>GetCustomDataToExport yöntemi (tür, tür)  
 Yöntemi <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%28System.Type%2CSystem.Type%29?displayProperty=nameWithType> , her tür tanımı için şema dışarı aktarma sırasında çağrılır. Yöntemi, dışarı aktarırken şema içindeki türlere bilgi ekler. Tanımlanan her tür, şemaya eklenmesi gereken herhangi bir ek veri olup olmadığını öğrenmek için bu yönteme gönderilir.  
  
#### <a name="getcustomdatatoexport-method-memberinfo-type"></a>GetCustomDataToExport yöntemi (MemberInfo, tür)  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%28System.Reflection.MemberInfo%2CSystem.Type%29?displayProperty=nameWithType> Dışarı aktarılmış türlerindeki her üye için dışarı aktarma sırasında çağrılır. Bu işlev, dışa aktarma sırasında şemaya dahil edilecek Üyeler için herhangi bir yorumu özelleştirmenizi sağlar. Sınıf içindeki her üyeye ait bilgiler, şemaya eklemek gerekip gerekmediğini denetlemek için bu yönteme gönderilir.  
  
 Yukarıdaki örnek, `dataContractType` her bir vekil üye için ' i arar. Ardından, her bir alan için uygun erişim değiştiricisini döndürür. Bu özelleştirme olmadan, erişim değiştiricileri için varsayılan değer geneldir. Bu nedenle, tüm Üyeler gerçek erişim kısıtlamalarının ne olduğuna bakılmaksızın, dışarıya aktarılmış şema kullanılarak oluşturulan kodda ortak olarak tanımlanır. Bu uygulamayı kullanmadığında, üye `numpens` , özel olarak tanımlansa bile, bu uygulamada ortak olur. Bu yöntemin kullanımı ile, verdiğiniz şemada erişim değiştiricisi özel olarak oluşturulabilir.  
  
### <a name="getreferencedtypeonimport-method"></a>GetReferencedTypeOnImport yöntemi  
 Bu yöntem, asıl <xref:System.Type> öğesinin türünü özgün türe eşler. Bu yöntem, şema içe aktarılması işlemini için isteğe bağlıdır.  
  
 Bir şemayı içeri aktaran ve kendisi için kod üreten bir yedek oluştururken, bir sonraki görev, bir yedek örneğin türünü özgün türüne tanımlamaktır.  
  
 Oluşturulan kodun var olan bir kullanıcı türüne başvurması gerekiyorsa bu, <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%2A> yöntemi uygulayarak yapılır.  
  
 Bir şemayı içeri aktarırken, bu yöntem her tür bildirimi için, yedekleri geçitli veri sözleşmesini bir türle eşlemek için çağrılır. Dize parametreleri `typeName` ve `typeNamespace` yedeklerin geçişli türünün adını ve ad alanını tanımlar. İçin <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%2A> dönüş değeri, yeni bir türün oluşturulması gerekip gerekmediğini belirlemekte kullanılır. Bu yöntem, geçerli bir tür ya da null döndürmelidir. Geçerli türler için döndürülen tür, oluşturulan kodda başvurulan bir tür olarak kullanılacaktır. Null döndürülürse, hiçbir türe başvurulmayacak ve yeni bir tür oluşturulmalıdır. Birden fazla yedekli kapı varsa, her bir yedek türü için eşlemeyi ilk türüne geri almak mümkündür.  
  
 Parametresi, ilk olarak öğesinden <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%2A>döndürülen nesnedir. `customData` Bu `customData` , yedek yazarları kod oluşturmak için içeri aktarma sırasında kullanılacak meta verilere ek veri/İpucu eklemek istediğinizde kullanılır.  
  
### <a name="processimportedtype-method"></a>ProcessImportedType yöntemi  
 Yöntemi <xref:System.Runtime.Serialization.IDataContractSurrogate.ProcessImportedType%2A> , şema içe aktarılması işlemini oluşturulan herhangi bir türü özelleştirir. Bu yöntem isteğe bağlıdır.  
  
 Bir şemayı içeri aktarırken, bu yöntem tüm içeri aktarılan tür ve derleme bilgilerinin özelleştirilme için izin verir. Örneğin:  
  
 [!code-csharp[C_IDataContractSurrogate#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#7)]  
  
 İçeri aktarma sırasında, oluşturulan her tür için bu yöntem çağrılır. Belirtilen <xref:System.CodeDom.CodeTypeDeclaration> ' i değiştirin veya <xref:System.CodeDom.CodeCompileUnit>değiştirin. Bu, adının, üyelerin, özniteliklerin ve diğer diğer özelliklerinin `CodeTypeDeclaration`değiştirilmesini içerir. `CodeCompileUnit`Öğesini işleyerek, yönergeleri, ad alanlarını, başvurulan derlemeleri ve diğer birkaç yönü değiştirmek mümkündür.  
  
 `CodeTypeDeclaration` Parametresi, kod Dom türü bildirimini içerir. Parametresi `CodeCompileUnit` , kodu işlemeye yönelik değişikliğe izin verir.  Tür `null` bildiriminde sonuçlar atılmak üzere döndürülüyor. Buna karşılık, bir `CodeTypeDeclaration`döndürürken, değişiklikler korunur.  
  
 Meta veri dışa aktarma sırasında özel veriler eklenirse, kullanılabilmesi için içeri aktarma sırasında kullanıcıya sağlanması gerekir. Bu özel veriler, programlama modeli ipuçlarına veya diğer açıklamalara yönelik olarak kullanılabilir. Her `CodeTypeDeclaration` ve <xref:System.CodeDom.CodeTypeMember> örnek, <xref:System.CodeDom.CodeObject.UserData%2A> özelliği olarak özel verileri içerir ve `IDataContractSurrogate` türüne atayın.  
  
 Yukarıdaki örnekte, içeri aktarılan şemada bazı değişiklikler gerçekleştirilir. Kod, bir yedek kullanarak özgün türün özel üyelerini korur. Bir şemayı `public`içeri aktarırken varsayılan erişim değiştiricisi. Bu nedenle, bu örnekte olduğu gibi, yedek şemanın tüm üyeleri değiştirilmediği sürece ortak olur. Dışarı aktarma sırasında özel veriler, hangi üyelerin özel olduğu hakkında meta verilere eklenir. Örnek, özel verileri arar, erişim değiştiricisinin özel olup olmadığını denetler ve ardından özniteliklerini ayarlayarak uygun üyeyi özel olarak değiştirir. Bu özelleştirme olmadan, `numpens` üye özel yerine ortak olarak tanımlanır.  
  
### <a name="getknowncustomdatatypes-method"></a>GetKnownCustomDataTypes yöntemi  
 Bu yöntem şemadan tanımlanan özel veri türlerini alır. Yöntemi, şema içe aktarılması işlemini için isteğe bağlıdır.  
  
 Yöntemi, şema dışa aktarma ve içeri aktarma başlangıcında çağrılır. Yöntemi, aktarılan veya içeri aktarılan şemada kullanılan özel veri türlerini döndürür. Yöntemi, bir tür koleksiyonu <xref:System.Collections.ObjectModel.Collection%601> olan bir `customDataTypes` (parametresi) geçirilir. Yöntemi bu koleksiyona ek bilinen türler eklemeli. Bilinen özel veri türleri, <xref:System.Runtime.Serialization.DataContractSerializer>kullanarak özel verilerin serileştirilmesi ve serisini kaldırma özelliğini etkinleştirmek için gereklidir. Daha fazla bilgi için bkz. [veri sözleşmesi bilinen türleri](../feature-details/data-contract-known-types.md).  
  
## <a name="implementing-a-surrogate"></a>Yedek uygulama  
 WCF 'de veri sözleşme yedeği kullanmak için birkaç özel yordamı izlemeniz gerekir.  
  
### <a name="to-use-a-surrogate-for-serialization-and-deserialization"></a>Serileştirme ve seri durumdan çıkarma için bir yedek kullanmak için  
 Vekil ile verilerin serileştirilmesi ve serisini kaldırma işlemini gerçekleştirmek içinkullanın.<xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Runtime.Serialization.DataContractSerializer> , Tarafından<xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>oluşturulur. Yedek de belirtilmelidir.  
  
##### <a name="to-implement-serialization-and-deserialization"></a>Serileştirme ve seri durumdan çıkarma uygulamak için  
  
1. Hizmetiniz <xref:System.ServiceModel.ServiceHost> için bir örneği oluşturun. Tüm yönergeler için bkz. [Temel WCF programlama](../basic-wcf-programming.md).  
  
2. Belirtilen hizmet <xref:System.ServiceModel.Description.ServiceEndpoint> ana bilgisayarının her biri için, konumunu <xref:System.ServiceModel.Description.OperationDescription>bulun.  
  
3. Öğesinin <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> bir örneğinin bulunduğunu öğrenmek için işlem davranışlarıyla arama yapın.  
  
4. Bir <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> bulunursa, <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.DataContractSurrogate%2A> özelliğini yeni bir yedek örneğine ayarlayın. Hayır <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> bulunamazsa, yeni bir örnek oluşturun ve yeni davranışın <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.DataContractSurrogate%2A> üyesini, yeni bir örnek örneğine ayarlayın.  
  
5. Son olarak, aşağıdaki örnekte gösterildiği gibi, bu yeni davranışı geçerli işlem davranışlarına ekleyin:  
  
     [!code-csharp[C_IDataContractSurrogate#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#8)]  
  
### <a name="to-use-a-surrogate-for-metadata-import"></a>Meta verilerin Içeri aktarılması için bir yedek kullanmak için  
 İstemci tarafı kodu oluşturmak için WSDL ve XSD gibi meta verileri içeri aktarırken, XSD şemasından <xref:System.Runtime.Serialization.XsdDataContractImporter>kod oluşturmaktan sorumlu bileşene eklenmelidir. Bunu yapmak için, meta verileri içeri <xref:System.ServiceModel.Description.WsdlImporter> aktarmak için kullanılan ' ı doğrudan değiştirin.  
  
##### <a name="to-implement-a-surrogate-for-metadata-importation"></a>Meta veri içe aktarılması işlemini için bir yedek uygulamak için  
  
1. <xref:System.ServiceModel.Description.WsdlImporter> Sınıfını kullanarak meta verileri içeri aktarın.  
  
2. Bir nesnenin<xref:System.Runtime.Serialization.XsdDataContractImporter> tanımlanıp tanımlanmadığını denetlemek için yönteminikullanın.<xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A>  
  
3. <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> Yöntemi döndürürse `false`, yeni <xref:System.Runtime.Serialization.XsdDataContractImporter> <xref:System.Runtime.Serialization.ImportOptions> bir oluşturun ve <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> özelliğini sınıfının yeni bir örneği olarak ayarlayın. Aksi takdirde, `out` <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> yönteminin parametresi tarafından döndürülen içe aktarıcı 'yı kullanın.  
  
4. Tanımlı değilse, özelliğini <xref:System.Runtime.Serialization.ImportOptions> sınıfının yeni bir örneği olacak şekilde ayarlayın. <xref:System.Runtime.Serialization.XsdDataContractImporter> <xref:System.Runtime.Serialization.ImportOptions>  
  
5. <xref:System.Runtime.Serialization.ImportOptions> Öğesinin <xref:System.Runtime.Serialization.ImportOptions.DataContractSurrogate%2A> özelliğininözelliğini,yeni<xref:System.Runtime.Serialization.XsdDataContractImporter> bir yedek örneğine ayarlayın.  
  
6. Öğesinin özelliği tarafından döndürülen <xref:System.ServiceModel.Description.MetadataExporter> koleksiyona ekleyin (sınıfından devralınmış.) <xref:System.ServiceModel.Description.WsdlImporter> <xref:System.Runtime.Serialization.XsdDataContractImporter> <xref:System.ServiceModel.Description.MetadataExporter.State%2A>  
  
7. Şema içindeki tüm veri sözleşmelerini <xref:System.ServiceModel.Description.WsdlImporter> içeri aktarmak için yönteminikullanın.<xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A> Son adım sırasında kod, vekil içine çağırarak yüklenen şemalardan oluşturulur.  
  
     [!code-csharp[C_IDataContractSurrogate#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#9)]  
  
### <a name="to-use-a-surrogate-for-metadata-export"></a>Meta verileri dışarı aktarma için bir yedek kullanmak için  
 Varsayılan olarak, bir hizmet için WCF 'den meta veriler dışarı aktarılırken hem WSDL hem de XSD şemasının oluşturulması gerekir. Vekil, veri anlaşması türleri <xref:System.Runtime.Serialization.XsdDataContractExporter>için xsd şeması oluşturmaktan sorumlu bileşene eklenmelidir. Bunu yapmak için, <xref:System.ServiceModel.Description.IWsdlExportExtension> <xref:System.ServiceModel.Description.WsdlExporter>öğesini değiştirmek için uygulayan bir davranış kullanın ya da meta verileri dışarı aktarmak için kullanılan'ıdoğrudandeğiştirin.<xref:System.ServiceModel.Description.WsdlExporter>  
  
##### <a name="to-use-a-surrogate-for-metadata-export"></a>Meta verileri dışarı aktarma için bir yedek kullanmak için  
  
1. Yeni <xref:System.ServiceModel.Description.WsdlExporter> bir oluşturun veya <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A> yöntemine geçirilen `wsdlExporter` parametreyi kullanın.  
  
2. Tanımlanmış olup olmadığını denetlemek için <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A>işlevinikullanın <xref:System.Runtime.Serialization.XsdDataContractExporter> .  
  
3. <xref:System.Runtime.Serialization.XsdDataContractExporter> <xref:System.ServiceModel.Description.WsdlExporter> <xref:System.ServiceModel.Description.MetadataExporter.State%2A> Öğesini döndürürse ,`false`öğesinden oluşturulan xml şemaları ile yeni bir oluşturun ve öğesinin özelliği tarafından döndürülen koleksiyona ekleyin. <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> <xref:System.ServiceModel.Description.WsdlExporter> Aksi takdirde, `out` <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> yönteminin parametresi tarafından döndürülen Dışarı Aktarıcı 'yı kullanın.  
  
4. Tanımlı değilse <xref:System.Runtime.Serialization.ExportOptions> , özelliğinisınıfınınyenibirörneğineayarlayın.<xref:System.Runtime.Serialization.XsdDataContractExporter.Options%2A> <xref:System.Runtime.Serialization.XsdDataContractExporter> <xref:System.Runtime.Serialization.ExportOptions>  
  
5. <xref:System.Runtime.Serialization.ExportOptions> Öğesinin <xref:System.Runtime.Serialization.ExportOptions.DataContractSurrogate%2A> özelliğininözelliğini,yeni<xref:System.Runtime.Serialization.XsdDataContractExporter> bir yedek örneğine ayarlayın. Meta verilerin dışarı aktarılması için sonraki adımlarda herhangi bir değişiklik yapılması gerekmez.  
  
     [!code-csharp[C_IDataContractSurrogate#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#10)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.IDataContractSurrogate>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.Runtime.Serialization.ImportOptions>
- <xref:System.Runtime.Serialization.ExportOptions>
- [Veri Anlaşmalarını Kullanma](../feature-details/using-data-contracts.md)
