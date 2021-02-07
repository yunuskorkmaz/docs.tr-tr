---
description: 'Hakkında daha fazla bilgi edinin: veri anlaşması temsilciler'
title: Veri Sözleşmesi Yedekleri
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts [WCF], surrogates
ms.assetid: 8c31134c-46c5-4ed7-94af-bab0ac0dfce5
ms.openlocfilehash: 335e7f64868177d00c747e29c463808f3eff3056
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99685809"
---
# <a name="data-contract-surrogates"></a>Veri Sözleşmesi Yedekleri

Veri anlaşması *yedeği* , veri anlaşması modeli üzerine inşa olan gelişmiş bir özelliktir. Bu özellik, kullanıcıların bir türün serileştirilme, seri durumdan çıkarılan veya yansıtılma göre meta verileri değiştirmek istedikleri durumlarda tür özelleştirmesi ve değiştirme için kullanılmak üzere tasarlanmıştır. Bir vekil 'in kullanılabileceği bazı senaryolar tür için bir veri anlaşması belirtilmediğinde, alanlar ve Özellikler öznitelik ile işaretlenmez <xref:System.Runtime.Serialization.DataMemberAttribute> veya kullanıcılar dinamik olarak şema çeşitlemeleri oluşturmak istiyor.  
  
 Serileştirme ve seri durumdan çıkarma, <xref:System.Runtime.Serialization.DataContractSerializer> .NET Framework, XML gibi uygun bir biçime dönüştürmek için kullanılırken veri sözleşmesi yedeği ile gerçekleştirilir. Veri sözleşmesi yedek, XML şema belgeleri (XSD) gibi meta veri gösterimleri üretilirken türler için aktarılmış meta verileri değiştirmek için de kullanılabilir. İçeri aktarma işleminden sonra kod meta verilerden oluşturulur ve yedek bu durumda, oluşturulan kodu özelleştirmek için kullanılabilir.  
  
## <a name="how-the-surrogate-works"></a>Vekil nasıl kullanılır?  

 Bir vekil, bir tür ("orijinal" tür) diğer bir türe ("yedeklerin Gated" türü) eşleyerek işe yarar. Aşağıdaki örnek orijinal türünü `Inventory` ve yeni bir yedek `InventorySurrogated` türünü gösterir. `Inventory`Tür serileştirilebilir değil, ancak `InventorySurrogated` tür:  
  
 [!code-csharp[C_IDataContractSurrogate#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#1)]  
  
 Bu sınıf için bir veri sözleşmesi tanımlanmadığı için, sınıfı bir veri sözleşmesine sahip bir yedek sınıfa dönüştürün. Yedeklerin Gated class aşağıdaki örnekte gösterilmiştir:  
  
 [!code-csharp[C_IDataContractSurrogate#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#2)]  
  
## <a name="implementing-the-idatacontractsurrogate"></a>Idatacontractvekil uygulama  

 Veri sözleşmesi yedek öğesini kullanmak için <xref:System.Runtime.Serialization.IDataContractSurrogate> arabirimini uygulayın.  
  
 Aşağıda, <xref:System.Runtime.Serialization.IDataContractSurrogate> olası bir uygulamayla ilgili her bir yönteme genel bakış verilmiştir.  
  
### <a name="getdatacontracttype"></a>GetDataContractType  

 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A>Yöntemi bir türü diğerine eşler. Serileştirme, seri durumdan çıkarma, içeri aktarma ve dışarı aktarma için bu yöntem gereklidir.  
  
 İlk görev, diğer türlere hangi türlerin eşlenildiğini tanımlar. Örneğin:  
  
 [!code-csharp[C_IDataContractSurrogate#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#3)]  
  
- Serileştirme sırasında, bu yöntem tarafından döndürülen eşleme daha sonra yöntemi çağırarak orijinal örneği bir yedeklerin geçitli örneğine dönüştürmek için kullanılır <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> .  
  
- Seri durumdan çıkarma sırasında, bu yöntem tarafından döndürülen eşleme, seri hale getirici tarafından, yedek türünün bir örneğinde seri durumdan çıkarmak için kullanılır. Daha sonra <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%2A> , yedekleri bulunan örneği orijinal türün bir örneğine dönüştürmeyi çağırır.  
  
- Dışarı aktarma sırasında, bu yöntem tarafından döndürülen vekil türü, meta verileri oluşturmak için kullanılacak veri sözleşmesini almak üzere yansıtılır.  
  
- İçeri aktarma işleminde, başlangıç türü, destek gibi amaçlarla kullanılacak veri sözleşmesini almak için yansıtılan bir vekil türüne değiştirilir.  
  
 <xref:System.Type>Parametresi seri hale getirilen, seri durumdan çıkarılan, içeri aktarılan veya aktarılan nesnenin türüdür. <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A>Yedek türü işlemezse yöntemin giriş türünü döndürmesi gerekir. Aksi takdirde, uygun yedeklerin geçitli türünü döndürün. Birden fazla yedek tür varsa, bu yöntemde çok sayıda eşleme tanımlanabilir.  
  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A>Yöntemi, veya gibi yerleşik veri anlaşması temelleri için çağrılmaz <xref:System.Int32> <xref:System.String> . Diziler, Kullanıcı tanımlı türler ve diğer veri yapıları gibi diğer türler için, bu yöntem her bir tür için çağrılır.  
  
 Önceki örnekte, yöntemi parametrenin ve karşılaştırılabilir olup olmadığını denetler `type` `Inventory` . Öyleyse, yöntemi ile eşlenir `InventorySurrogated` . Bir serileştirme, seri kaldırma, içeri aktarma şeması veya dışa aktarma şeması çağrıldığında, türler arasındaki eşlemeyi belirlemekte bu işlev ilk olarak çağırılır.  
  
### <a name="getobjecttoserialize-method"></a>GetObjectToSerialize yöntemi  

 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A>Yöntemi, özgün tür örneğini yedeklerin geçişli tür örneğine dönüştürür. Serileştirme için yöntemi gerekir.  
  
 Bir sonraki adım, yöntemi uygulayarak fiziksel verilerin özgün örnekten vekil 'e eşlenme şeklini tanımlamaktır <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> . Örneğin:  
  
 [!code-csharp[C_IDataContractSurrogate#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#4)]  
  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A>Yöntemi bir nesne serileştirildiğinde çağrılır. Bu yöntem, verileri özgün türünden yedeklerin geçişli tür alanlarına aktarır. Alanlar doğrudan vekil alanlarla eşleştirilebilir veya orijinal verilerin düzenlemeleri vekil içinde depolanabilir. Bazı olası kullanımlar şunlardır: alanları doğrudan eşleme, yedekleri geçitli alanlarda depolanacak veriler üzerinde işlem yapma veya orijinal türün XML 'sini, yedekleri geçitli alanda depolama.  
  
 `targetType`Parametresi, üyenin belirtilen türüne başvurur. Bu parametre, yöntemi tarafından döndürülen yedeklerin kapılı türüdür <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> . Seri hale getirici, döndürülen nesnenin bu türe atanabilir olmasını zorunlu kılmaz. `obj`Parametresi, seri hale getirilecek nesnedir ve gerekirse, bu nesnenin vekil değerine dönüştürülür. Bu yöntem, bir yedeklerin, nesneyi işlemezse giriş nesnesini döndürmelidir. Aksi takdirde, yeni yedek nesne döndürülür. Nesne null ise vekil çağrılmaz. Farklı örnekler için çok sayıda vekil eşleme bu yöntem içinde tanımlanabilir.  
  
 Bir oluştururken <xref:System.Runtime.Serialization.DataContractSerializer> , bunu nesne başvurularını koruyacak şekilde bildirebilirsiniz. (Daha fazla bilgi için bkz. [serileştirme ve serisini kaldırma](../feature-details/serialization-and-deserialization.md).) Bu, `preserveObjectReferences` oluşturucusunun içindeki parametresi olarak ayarlanarak yapılır `true` . Bu durumda, sonraki tüm serileştirmeler yalnızca akışa başvuru yazdığından, bir nesne için yedek yalnızca bir kez çağırılır. `preserveObjectReferences`Olarak ayarlanırsa `false` , bir örnek ile karşılaşıldığında, yedek çağırılır.  
  
 Seri hale getirilmiş Örneğin türü, belirtilen türden farklıysa, örneğin, örneğin `xsi:type` diğer uçta seri durumdan çıkarılmaya izin vermek için tür bilgileri akışa yazılır. Bu işlem, nesnenin yedeklerin yapılıp yapılmayacağını belirtir.  
  
 Yukarıdaki örnek, örneğin verisini `Inventory` öğesine dönüştürür `InventorySurrogated` . Nesnenin türünü denetler ve yedeklerin kapılı türe dönüştürmek için gerekli düzenlemeleri gerçekleştirir. Bu durumda, `Inventory` sınıfının alanları doğrudan `InventorySurrogated` sınıf alanlarına kopyalanır.  
  
### <a name="getdeserializedobject-method"></a>GetDeserializedObject yöntemi  

 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%2A>Yöntemi, yedeklerin kapılı tür örneğini orijinal tür örneğine dönüştürür. Seri durumdan çıkarma için gereklidir.  
  
 Sonraki görev, fiziksel verilerin vekil örnekten orijinale nasıl eşleştirilecektir. Örneğin:  
  
 [!code-csharp[C_IDataContractSurrogate#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#5)]  
  
 Bu yöntem yalnızca bir nesnenin serisini kaldırma işlemi sırasında çağrılır. Yedek türden seri durumundan çıkarma için, özgün türüne geri doğru veri eşleme sağlar. Yönteme benzer şekilde `GetObjectToSerialize` , bazı olası kullanımlar alan verilerini doğrudan değiş tokuş etmek, veriler üzerinde işlemler gerçekleştirmek ve XML verilerini depolamak olabilir. Seri durumdan çıkarma sırasında, veri dönüştürmesinde yapılan düzenlemeler nedeniyle her zaman özgün verilerden tam veri değerlerini elde edebilirsiniz.  
  
 `targetType`Parametresi, üyenin belirtilen türüne başvurur. Bu parametre, yöntemi tarafından döndürülen yedeklerin kapılı türüdür `GetDataContractType` . `obj`Parametresi, serisi kaldırılan nesneye başvurur. Nesne, bir yedek ise özgün türüne dönüştürülebilir. Bu yöntem, yedek nesneyi işlemezse giriş nesnesini döndürür. Aksi takdirde, seri durumdan çıkarılan nesne, dönüştürme işlemi tamamlandıktan sonra döndürülür. Birden fazla yedek tür varsa, her bir türü ve dönüşümünü belirterek, her biri için, vekil 'ten birincil türe veri dönüştürme sağlayabilirsiniz.  
  
 Bir nesne döndürüldüğünde, iç nesne tabloları bu vekil tarafından döndürülen nesneyle güncelleştirilir. Bir örneğe yapılan sonraki başvurular, nesne tablolarından yedeklerin geçitli örneğini elde eder.  
  
 Önceki örnek, türü nesneleri `InventorySurrogated` ilk türe geri dönüştürür `Inventory` . Bu durumda, veriler doğrudan `InventorySurrogated` içindeki karşılık gelen alanlara geri aktarılır `Inventory` . Veri düzenlemeleri bulunmadığından, her üye alanı serileştirme öncesindeki değerlerle aynı değerleri içerecektir.  
  
### <a name="getcustomdatatoexport-method"></a>GetCustomDataToExport yöntemi  

 Bir şemayı dışarı aktarırken <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%2A> Yöntem isteğe bağlıdır. Bu, diğer verileri veya ipuçlarını, dışarıya aktarılmış şemaya eklemek için kullanılır. Ek veriler üye düzeyinde veya tür düzeyinde eklenebilir. Örneğin:  
  
 [!code-csharp[C_IDataContractSurrogate#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#6)]  
  
 Bu Yöntem (iki aşırı yükleme ile), ek bilgilerin üye veya tür düzeyinde meta verilere eklenmesine olanak sunar. Bir üyenin genel mi yoksa özel mi olduğunu ve şemanın dışa ve içeri aktarılması boyunca korunacak açıklamaları eklemek mümkündür. Bu tür bilgiler bu yöntem olmadan kaybedilir. Bu yöntem üye veya türlerin eklenmesine veya silinmesine neden olmaz, bunun yerine bu düzeylerin her birindeki şemalara daha fazla veri ekler.  
  
 Yöntemi aşırı yüklendi ve bir `Type` ( `clrtype` parametre) ya da <xref:System.Reflection.MemberInfo> ( `memberInfo` parametre) alabilir. İkinci parametre her zaman bir `Type` ( `dataContractType` parametre). Bu yöntem, her üye için ve yedeklerin Gated Type türü için çağrılır `dataContractType` .  
  
 Bu aşırı yüklemelerin her biri ya da `null` serileştirilebilir bir nesne döndürmelidir. Null olmayan bir nesne, bir ek açıklama olarak, verilecek şemaya seri hale getirilebilir. `Type`Aşırı yüklemede, şemaya aktarılmış her tür, parametre olarak yedeklerin geçitli türü ile birlikte ilk parametrede bu yönteme gönderilir `dataContractType` . `MemberInfo`Aşırı yükleme için, şemaya aktarılmış her üye, bilgilerini `memberInfo` ikinci parametrede yedeklerin geçitli türü olan parametre olarak gönderir.  
  
#### <a name="getcustomdatatoexport-method-type-type"></a>GetCustomDataToExport yöntemi (tür, tür)  

 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%28System.Type%2CSystem.Type%29?displayProperty=nameWithType>Yöntemi, her tür tanımı için şema dışarı aktarma sırasında çağrılır. Yöntemi, dışarı aktarırken şema içindeki türlere bilgi ekler. Tanımlanan her tür, şemaya eklenmesi gereken herhangi bir ek veri olup olmadığını öğrenmek için bu yönteme gönderilir.  
  
#### <a name="getcustomdatatoexport-method-memberinfo-type"></a>GetCustomDataToExport yöntemi (MemberInfo, tür)  

 Dışarı <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%28System.Reflection.MemberInfo%2CSystem.Type%29?displayProperty=nameWithType> aktarılmış türlerindeki her üye için dışarı aktarma sırasında çağrılır. Bu işlev, dışa aktarma sırasında şemaya dahil edilecek Üyeler için herhangi bir yorumu özelleştirmenizi sağlar. Sınıf içindeki her üyeye ait bilgiler, şemaya eklemek gerekip gerekmediğini denetlemek için bu yönteme gönderilir.  
  
 Yukarıdaki örnek, `dataContractType` her bir vekil üye için ' i arar. Ardından, her bir alan için uygun erişim değiştiricisini döndürür. Bu özelleştirme olmadan, erişim değiştiricileri için varsayılan değer geneldir. Bu nedenle, tüm Üyeler gerçek erişim kısıtlamalarının ne olduğuna bakılmaksızın, dışarıya aktarılmış şema kullanılarak oluşturulan kodda ortak olarak tanımlanır. Bu uygulamayı kullanmadığında, üye `numpens` , özel olarak tanımlansa bile, bu uygulamada ortak olur. Bu yöntemin kullanımı ile, verdiğiniz şemada erişim değiştiricisi özel olarak oluşturulabilir.  
  
### <a name="getreferencedtypeonimport-method"></a>GetReferencedTypeOnImport yöntemi  

 Bu yöntem, <xref:System.Type> asıl öğesinin türünü özgün türe eşler. Bu yöntem, şema içe aktarılması işlemini için isteğe bağlıdır.  
  
 Bir şemayı içeri aktaran ve kendisi için kod üreten bir yedek oluştururken, bir sonraki görev, bir yedek örneğin türünü özgün türüne tanımlamaktır.  
  
 Oluşturulan kodun var olan bir kullanıcı türüne başvurması gerekiyorsa bu, yöntemi uygulayarak yapılır <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%2A> .  
  
 Bir şemayı içeri aktarırken, bu yöntem her tür bildirimi için, yedekleri geçitli veri sözleşmesini bir türle eşlemek için çağrılır. Dize parametreleri `typeName` ve `typeNamespace` yedeklerin geçişli türünün adını ve ad alanını tanımlar. İçin dönüş değeri, <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%2A> Yeni bir türün oluşturulması gerekip gerekmediğini belirlemekte kullanılır. Bu yöntem, geçerli bir tür ya da null döndürmelidir. Geçerli türler için döndürülen tür, oluşturulan kodda başvurulan bir tür olarak kullanılacaktır. Null döndürülürse, hiçbir türe başvurulmayacak ve yeni bir tür oluşturulmalıdır. Birden fazla yedekli kapı varsa, her bir yedek türü için eşlemeyi ilk türüne geri almak mümkündür.  
  
 `customData`Parametresi, ilk olarak öğesinden döndürülen nesnedir <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%2A> . Bu `customData` , yedek yazarları kod oluşturmak için içeri aktarma sırasında kullanılacak meta verilere ek veri/İpucu eklemek istediğinizde kullanılır.  
  
### <a name="processimportedtype-method"></a>ProcessImportedType yöntemi  

 <xref:System.Runtime.Serialization.IDataContractSurrogate.ProcessImportedType%2A>Yöntemi, şema içe aktarılması işlemini oluşturulan herhangi bir türü özelleştirir. Bu yöntem isteğe bağlıdır.  
  
 Bir şemayı içeri aktarırken, bu yöntem tüm içeri aktarılan tür ve derleme bilgilerinin özelleştirilme için izin verir. Örneğin:  
  
 [!code-csharp[C_IDataContractSurrogate#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#7)]  
  
 İçeri aktarma sırasında, oluşturulan her tür için bu yöntem çağrılır. Belirtilen ' i değiştirin <xref:System.CodeDom.CodeTypeDeclaration> veya değiştirin <xref:System.CodeDom.CodeCompileUnit> . Bu, adının, üyelerin, özniteliklerin ve diğer diğer özelliklerinin değiştirilmesini içerir `CodeTypeDeclaration` . Öğesini işleyerek, `CodeCompileUnit` yönergeleri, ad alanlarını, başvurulan derlemeleri ve diğer birkaç yönü değiştirmek mümkündür.  
  
 `CodeTypeDeclaration`Parametresi, kod Dom türü bildirimini içerir. `CodeCompileUnit`Parametresi, kodu işlemeye yönelik değişikliğe izin verir.  `null`Tür bildiriminde sonuçlar atılmak üzere döndürülüyor. Buna karşılık, bir döndürürken `CodeTypeDeclaration` , değişiklikler korunur.  
  
 Meta veri dışa aktarma sırasında özel veriler eklenirse, kullanılabilmesi için içeri aktarma sırasında kullanıcıya sağlanması gerekir. Bu özel veriler, programlama modeli ipuçlarına veya diğer açıklamalara yönelik olarak kullanılabilir. Her `CodeTypeDeclaration` ve <xref:System.CodeDom.CodeTypeMember> örnek, özelliği olarak özel verileri içerir ve <xref:System.CodeDom.CodeObject.UserData%2A> `IDataContractSurrogate` türüne atayın.  
  
 Yukarıdaki örnekte, içeri aktarılan şemada bazı değişiklikler gerçekleştirilir. Kod, bir yedek kullanarak özgün türün özel üyelerini korur. Bir şemayı içeri aktarırken varsayılan erişim değiştiricisi `public` . Bu nedenle, bu örnekte olduğu gibi, yedek şemanın tüm üyeleri değiştirilmediği sürece ortak olur. Dışarı aktarma sırasında özel veriler, hangi üyelerin özel olduğu hakkında meta verilere eklenir. Örnek, özel verileri arar, erişim değiştiricisinin özel olup olmadığını denetler ve ardından özniteliklerini ayarlayarak uygun üyeyi özel olarak değiştirir. Bu özelleştirme olmadan, `numpens` üye özel yerine ortak olarak tanımlanır.  
  
### <a name="getknowncustomdatatypes-method"></a>GetKnownCustomDataTypes yöntemi  

 Bu yöntem şemadan tanımlanan özel veri türlerini alır. Yöntemi, şema içe aktarılması işlemini için isteğe bağlıdır.  
  
 Yöntemi, şema dışa aktarma ve içeri aktarma başlangıcında çağrılır. Yöntemi, aktarılan veya içeri aktarılan şemada kullanılan özel veri türlerini döndürür. Yöntemi <xref:System.Collections.ObjectModel.Collection%601> `customDataTypes` , bir tür koleksiyonu olan bir (parametresi) geçirilir. Yöntemi bu koleksiyona ek bilinen türler eklemeli. Bilinen özel veri türleri, kullanarak özel verilerin serileştirilmesi ve serisini kaldırma özelliğini etkinleştirmek için gereklidir <xref:System.Runtime.Serialization.DataContractSerializer> . Daha fazla bilgi için bkz. [veri sözleşmesi bilinen türleri](../feature-details/data-contract-known-types.md).  
  
## <a name="implementing-a-surrogate"></a>Yedek uygulama  

 WCF 'de veri sözleşme yedeği kullanmak için birkaç özel yordamı izlemeniz gerekir.  
  
### <a name="to-use-a-surrogate-for-serialization-and-deserialization"></a>Serileştirme ve seri durumdan çıkarma için bir yedek kullanmak için  

 <xref:System.Runtime.Serialization.DataContractSerializer>Vekil ile verilerin serileştirilmesi ve serisini kaldırma işlemini gerçekleştirmek için kullanın. , <xref:System.Runtime.Serialization.DataContractSerializer> Tarafından oluşturulur <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> . Yedek de belirtilmelidir.  
  
##### <a name="to-implement-serialization-and-deserialization"></a>Serileştirme ve seri durumdan çıkarma uygulamak için  
  
1. Hizmetiniz için bir örneği oluşturun <xref:System.ServiceModel.ServiceHost> . Tüm yönergeler için bkz. [Temel WCF programlama](../basic-wcf-programming.md).  
  
2. <xref:System.ServiceModel.Description.ServiceEndpoint>Belirtilen hizmet ana bilgisayarının her biri için, konumunu bulun <xref:System.ServiceModel.Description.OperationDescription> .  
  
3. Öğesinin bir örneğinin bulunduğunu öğrenmek için işlem davranışlarıyla arama yapın <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> .  
  
4. Bir <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> bulunursa, <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.DataContractSurrogate%2A> özelliğini yeni bir yedek örneğine ayarlayın. Hayır <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> bulunamazsa, yeni bir örnek oluşturun ve yeni davranışın üyesini, yeni bir örnek <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.DataContractSurrogate%2A> örneğine ayarlayın.  
  
5. Son olarak, aşağıdaki örnekte gösterildiği gibi, bu yeni davranışı geçerli işlem davranışlarına ekleyin:  
  
     [!code-csharp[C_IDataContractSurrogate#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#8)]  
  
### <a name="to-use-a-surrogate-for-metadata-import"></a>Meta verilerin Içeri aktarılması için bir yedek kullanmak için  

 İstemci tarafı kodu oluşturmak için WSDL ve XSD gibi meta verileri içeri aktarırken, XSD şemasından kod oluşturmaktan sorumlu bileşene eklenmelidir <xref:System.Runtime.Serialization.XsdDataContractImporter> . Bunu yapmak için, <xref:System.ServiceModel.Description.WsdlImporter> meta verileri içeri aktarmak için kullanılan ' ı doğrudan değiştirin.  
  
##### <a name="to-implement-a-surrogate-for-metadata-importation"></a>Meta veri içe aktarılması işlemini için bir yedek uygulamak için  
  
1. Sınıfını kullanarak meta verileri içeri aktarın <xref:System.ServiceModel.Description.WsdlImporter> .  
  
2. <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A>Bir nesnenin tanımlanıp tanımlanmadığını denetlemek için yöntemini kullanın <xref:System.Runtime.Serialization.XsdDataContractImporter> .  
  
3. <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A>Yöntemi döndürürse `false` , yeni bir oluşturun <xref:System.Runtime.Serialization.XsdDataContractImporter> ve <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> özelliğini sınıfının yeni bir örneği olarak ayarlayın <xref:System.Runtime.Serialization.ImportOptions> . Aksi takdirde, yönteminin parametresi tarafından döndürülen içe aktarıcı 'yı kullanın `out` <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> .  
  
4. Tanımlı değilse, <xref:System.Runtime.Serialization.XsdDataContractImporter> <xref:System.Runtime.Serialization.ImportOptions> özelliğini sınıfının yeni bir örneği olacak şekilde ayarlayın <xref:System.Runtime.Serialization.ImportOptions> .  
  
5. <xref:System.Runtime.Serialization.ImportOptions.DataContractSurrogate%2A>Öğesinin özelliğinin özelliğini, <xref:System.Runtime.Serialization.ImportOptions> <xref:System.Runtime.Serialization.XsdDataContractImporter> Yeni bir yedek örneğine ayarlayın.  
  
6. <xref:System.Runtime.Serialization.XsdDataContractImporter>Öğesinin özelliği tarafından döndürülen koleksiyona ekleyin <xref:System.ServiceModel.Description.MetadataExporter.State%2A> <xref:System.ServiceModel.Description.WsdlImporter> ( <xref:System.ServiceModel.Description.MetadataExporter> sınıfından devralınmış.)  
  
7. <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A> <xref:System.ServiceModel.Description.WsdlImporter> Şema içindeki tüm veri sözleşmelerini içeri aktarmak için yöntemini kullanın. Son adım sırasında kod, vekil içine çağırarak yüklenen şemalardan oluşturulur.  
  
     [!code-csharp[C_IDataContractSurrogate#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#9)]  
  
### <a name="to-use-a-surrogate-for-metadata-export"></a>Meta verileri dışarı aktarma için bir yedek kullanmak için  

 Varsayılan olarak, bir hizmet için WCF 'den meta veriler dışarı aktarılırken hem WSDL hem de XSD şemasının oluşturulması gerekir. Vekil, veri anlaşması türleri için XSD şeması oluşturmaktan sorumlu bileşene eklenmelidir <xref:System.Runtime.Serialization.XsdDataContractExporter> . Bunu yapmak için, öğesini değiştirmek için uygulayan bir davranış kullanın <xref:System.ServiceModel.Description.IWsdlExportExtension> ya da <xref:System.ServiceModel.Description.WsdlExporter> <xref:System.ServiceModel.Description.WsdlExporter> meta verileri dışarı aktarmak için kullanılan ' ı doğrudan değiştirin.  
  
##### <a name="to-use-a-surrogate-for-metadata-export"></a>Meta verileri dışarı aktarma için bir yedek kullanmak için  
  
1. Yeni bir oluşturun <xref:System.ServiceModel.Description.WsdlExporter> veya `wsdlExporter` yöntemine geçirilen parametreyi kullanın <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A> .  
  
2. <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A>Tanımlanmış olup olmadığını denetlemek için işlevini kullanın <xref:System.Runtime.Serialization.XsdDataContractExporter> .  
  
3. <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A>Öğesini döndürürse, `false` <xref:System.Runtime.Serialization.XsdDataContractExporter> öğesinden oluşturulan xml şemaları ile yeni bir oluşturun <xref:System.ServiceModel.Description.WsdlExporter> ve öğesinin özelliği tarafından döndürülen koleksiyona ekleyin <xref:System.ServiceModel.Description.MetadataExporter.State%2A> <xref:System.ServiceModel.Description.WsdlExporter> . Aksi takdirde, yönteminin parametresi tarafından döndürülen Dışarı Aktarıcı 'yı kullanın `out` <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> .  
  
4. Tanımlı değilse, <xref:System.Runtime.Serialization.XsdDataContractExporter> <xref:System.Runtime.Serialization.ExportOptions> <xref:System.Runtime.Serialization.XsdDataContractExporter.Options%2A> özelliğini sınıfının yeni bir örneğine ayarlayın <xref:System.Runtime.Serialization.ExportOptions> .  
  
5. <xref:System.Runtime.Serialization.ExportOptions.DataContractSurrogate%2A>Öğesinin özelliğinin özelliğini, <xref:System.Runtime.Serialization.ExportOptions> <xref:System.Runtime.Serialization.XsdDataContractExporter> Yeni bir yedek örneğine ayarlayın. Meta verilerin dışarı aktarılması için sonraki adımlarda herhangi bir değişiklik yapılması gerekmez.  
  
     [!code-csharp[C_IDataContractSurrogate#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#10)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.IDataContractSurrogate>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.Runtime.Serialization.ImportOptions>
- <xref:System.Runtime.Serialization.ExportOptions>
- [Veri Sözleşmelerini Kullanma](../feature-details/using-data-contracts.md)
