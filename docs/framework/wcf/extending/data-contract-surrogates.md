---
title: Veri Sözleşmesi Yedekleri
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts [WCF], surrogates
ms.assetid: 8c31134c-46c5-4ed7-94af-bab0ac0dfce5
ms.openlocfilehash: b9349291979e76650f07db5e433620554928eb4b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54614643"
---
# <a name="data-contract-surrogates"></a>Veri Sözleşmesi Yedekleri
Veri anlaşması *vekil* veri anlaşması modeli üzerinde oluşturulmuş, Gelişmiş bir özelliktir. Bu özellik türü özelleştirme ve kullanıcılar nasıl bir tür, seri durumdan çıkarılmış veya öngörülen meta verileri içine serileştirilmiş değiştirmek istediğiniz durumlarda değiştirme için kullanılmak üzere tasarlanmıştır. Bir veri anlaşması türü, alanlar ve özellikler ile işaretlenmemiş için belirtilmemiş bazı senaryolar, bir vekil nerede kullanılabilir olduğunda <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliği veya kullanıcılar şema farklılıkları dinamik olarak oluşturmak istediğiniz.  
  
 Serileştirme ve seri durumundan çıkarma elde ile veri sözleşme vekil kullanırken <xref:System.Runtime.Serialization.DataContractSerializer> .NET Framework'ten XML gibi uygun bir biçime dönüştürmek için. Veri sözleşmesi temsilci türleri için XML Şeması belgeleri (XSD) gibi meta veri gösterimleri üretirken dışarı meta verilerini değiştirmek için de kullanılabilir. İçeri aktarma, bağlı kod meta verilerinden oluşturulur ve vekil Bu örnekte oluşturulan kod da özelleştirmek için kullanılabilir.  
  
## <a name="how-the-surrogate-works"></a>Vekil nasıl çalışır?  
 Bir yedek başka bir tür ("surrogated" türü) için eşleme bir türü tarafından ("özgün") çalışır. Aşağıdaki örnek, özgün türü gösterir `Inventory` ve yeni bir yedek `InventorySurrogated` türü. `Inventory` Türü seri hale getirilebilir değil ancak `InventorySurrogated` türü:  
  
 [!code-csharp[C_IDataContractSurrogate#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#1)]  
  
 Bir veri anlaşması için bu sınıfın tanımlı değil çünkü veri sözleşme ile bir vekil sınıfı için sınıf dönüştürün. Surrogated sınıfı aşağıdaki örnekte gösterilmiştir:  
  
 [!code-csharp[C_IDataContractSurrogate#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#2)]  
  
## <a name="implementing-the-idatacontractsurrogate"></a>IDataContractSurrogate uygulama  
 Veri sözleşmesi vekil kullanmak için uygulama <xref:System.Runtime.Serialization.IDataContractSurrogate> arabirimi.  
  
 Her yöntem genel bir bakış aşağıdadır <xref:System.Runtime.Serialization.IDataContractSurrogate> olası bir uygulama.  
  
### <a name="getdatacontracttype"></a>GetDataContractType  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> Yöntemi başka bir tür eşler. Bu yöntem serileştirme, seri durumundan çıkarma, içeri ve dışarı aktarma için gereklidir.  
  
 İlk görev türleri ne olacağını tanımlayan diğer türlerine eşlenir. Örneğin:  
  
 [!code-csharp[C_IDataContractSurrogate#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#3)]  
  
-   Seri hale getirme üzerinde bu yöntem tarafından döndürülen eşleme sonradan surrogated örneği özgün örneğe çağırarak dönüştürmek için kullanılan <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> yöntemi.  
  
-   Seri durumundan çıkarma işleminde, bu yöntem tarafından döndürülen eşleme, temsilci türünün bir örneği seri durumdan çıkarılacak seri hale getirici tarafından kullanılır. Daha sonra çağıran <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%2A> surrogated örneği özgün türün bir örneğine dönüştürülecek.  
  
-   Dışarı aktarma üzerinde bu yöntem tarafından döndürülen vekil türü meta verileri oluşturmak için veri anlaşması almak için yansıtılır.  
  
-   İçeri aktarma işlemi sırasında Başlangıç türü desteğine başvurma gibi amaçlarla kullanmak için veri anlaşması almak için yansıtılan bir temsilci türü değiştirilir.  
  
 <xref:System.Type> Parametredir, seri durumdan çıkarılmış, içeri aktarılan veya dışarı aktarılan serileştirilmekte olan nesnenin türü. <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> Vekil türü işlemez, yöntem giriş türünü döndürmesi gerekir. Aksi takdirde, uygun surrogated türü döndürür. Çok sayıda eşlemeleri, yedek birden fazla varsa, bu yöntemde tanımlanabilir.  
  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> Yönteminin çağrılmaması için yerleşik veri sözleşme temelleri gibi <xref:System.Int32> veya <xref:System.String>. Diziler, kullanıcı tanımlı türler ve diğer veri yapılarını gibi diğer türleri için her türü için bu yöntem çağrılır.  
  
 Önceki örnekte, yöntem denetler `type` parametresi ve `Inventory` benzerdir. Bu nedenle, yöntem için eşleniyorsa `InventorySurrogated`. Her bir seri hale getirme seri durumundan çıkarma, şemayı İçeri Aktar veya dışarı aktarma şeması olarak adlandırılır, bu işlev varsayılan türleri arasındaki eşlemeyi belirlemek için çağrılır.  
  
### <a name="getobjecttoserialize-method"></a>GetObjectToSerialize yöntemi  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> Yöntemi özgün tür örneği yerine temsilci konulduğundan türü örneğine dönüştürür. Yöntemi, seri hale getirme için gereklidir.  
  
 Fiziksel veri eşleştirilir özgün örneğinden için yedek uygulayarak şeklini tanımlamak için sonraki adımdır <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> yöntemi. Örneğin:  
  
 [!code-csharp[C_IDataContractSurrogate#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#4)]  
  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> Yöntemi, bir nesne seri olduğunda çağrılır. Bu yöntem, özgün türünden surrogated türündeki alanlar için veri aktarır. Alanlar doğrudan alanları vekil eşlenebilir veya özgün veri değişikliklerini vekil içinde depolanabilir. Bazı olası kullanımları şunlardır: doğrudan alanlarını eşleme surrogated alanlarında depolanan veriler üzerinde işlem gerçekleştirme ya da özgün türün XML surrogated alanında depolama.  
  
 `targetType` Parametre bildirilen üye türüne başvuruyor. Bu parametre, tarafından döndürülen surrogated türüdür <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> yöntemi. Seri hale getirici, döndürülen nesne bu türüne atanabilir uygulamaz. `obj` Nesneyi serileştirmek için bir parametredir ve gerekirse, yedek için dönüştürülür. Bu yöntem, surrogated nesne işlemez giriş nesnesi döndürmelidir. Aksi takdirde, yeni bir vekil nesne döndürülür. Nesne null ise temsilci çağrılmaz. Çok sayıda vekil eşlemeleri farklı örnekleri için bu yöntem içinde tanımlanabilir.  
  
 Oluştururken bir <xref:System.Runtime.Serialization.DataContractSerializer>, nesne başvuruları korumak için bildirebilirsiniz. (Daha fazla bilgi için [serileştirme ve seri durumundan çıkarma](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).) Bu ayarı gerçekleştirilir `preserveObjectReferences` yapıcısına parametresinde `true`. Bu durumda, tüm sonraki serializations, yalnızca başvuru akışa yazmak olduğundan yedek bir nesne için yalnızca bir kez çağrılır. Varsa `preserveObjectReferences` ayarlanır `false`, sonra bir örneği ile her karşılaşmanızda vekil çağrılır.  
  
 Seri hale getirilmiş örneği türü bildirilen türü farklıysa, tür bilgileri akışa Örneğin, yazılan `xsi:type` diğer uçta seri durumdan örneği izin vermek için. Bu işlem, nesne olmayan ya da yerine temsilci konulduğundan olup olmadığını gerçekleşir.  
  
 Yukarıdaki örnek verileri dönüştürür `Inventory` , örneğine `InventorySurrogated`. Bu nesne türünü denetler ve surrogated türe dönüştürmek için gerekli işlemeleri gerçekleştirir. Bu durumda, alanlarını `Inventory` sınıfı doğrudan kopyalanır üzerinden `InventorySurrogated` sınıfı alanları.  
  
### <a name="getdeserializedobject-method"></a>GetDeserializedObject yöntemi  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%2A> Yöntemi yerine temsilci konulduğundan tür örneği özgün türü örneğine dönüştürür. Seri durumundan çıkarma için gereklidir.  
  
 Sıradaki görev, fiziksel veri özgün vekil örneğinden eşleştirilecek yol tanımlamaktır. Örneğin:  
  
 [!code-csharp[C_IDataContractSurrogate#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#5)]  
  
 Bu yöntem, yalnızca bir nesne seri kaldırma sırasında çağrılır. Temsilci türünden ters veri eşlemesi seri durumundan çıkarma için özgün türünü sağlar. Benzer şekilde `GetObjectToSerialize` yöntemi, bazı olası kullanımı doğrudan alan veri değişimi, veriler üzerinde işlemler gerçekleştirmek ve XML verileri depolamak için olabilir. Seri durumdan çıkarmak olduğunda her zaman tam veri değerleri özgün veri dönüştürme işlemeleri nedeniyle elde değil.  
  
 `targetType` Parametre bildirilen üye türüne başvuruyor. Bu parametre, tarafından döndürülen surrogated türüdür `GetDataContractType` yöntemi. `obj` Parametresi seri durumdan nesneye başvurur. Bunun yerine temsilci konulduğundan, nesne özgün türüne dönüştürülebilir. Bu yöntem, yedek nesne işlemez giriş nesnesi döndürür. Aksi takdirde, dönüştürme tamamlandığında seri durumdan çıkarılmış nesne döndürülür. Vekil birden fazla varsa, veri dönüştürme vekil birincil türü her her tür belirterek ve kendi dönüştürme sağlayabilir.  
  
 Nesneyi döndürürken, iç nesne tabloları bu yedek tarafından döndürülen nesne ile güncelleştirilir. Sonraki tüm başvuruları örneğine surrogated örneği nesne tablolardan elde eder.  
  
 Önceki örnekte türünden nesnelerin dönüştürür `InventorySurrogated` ilk yazmasını `Inventory`. Bu durumda, veriler doğrudan geri aktarılır `InventorySurrogated` , karşılık gelen alanlara `Inventory`. Hiçbir veri değişikliklerini olduğundan, alanların her biri üye serileştirme önce aynı değerleri içerir.  
  
### <a name="getcustomdatatoexport-method"></a>GetCustomDataToExport yöntemi  
 Bir şema verirken <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%2A> yöntemi, isteğe bağlıdır. Dışarı aktarılan şemasına ek verileri veya ipuçları eklemek için kullanılır. Ek veri üyesi düzeyinde veya tür düzeyinde eklenebilir. Örneğin:  
  
 [!code-csharp[C_IDataContractSurrogate#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#6)]  
  
 Bu yöntemle (iki aşırı yükleme) eklenmesi ek meta veri bilgileri, üyenin veya türün düzeyinde ya da sağlar. Genel veya özel ve dışarı aktarma ve içeri aktarma şemasının korunması yorumları üyesi olup olmadığı hakkında ipuçları dahil etmek mümkündür. Bu yöntem gibi bilgiler kaybolacak. Bu yöntem, ekleme veya üyeleri veya türleri silinmesine neden olmaz, ancak ek veri şemaları ya da bu düzeyler, yerine ekler.  
  
 Yöntem aşırı yüklendi ve ya da sürebilir bir `Type` (`clrtype` parametresi) veya <xref:System.Reflection.MemberInfo> (`memberInfo` parametresi). Her zaman ikinci parametresi olan bir `Type` (`dataContractType` parametresi). Her üye ve yerine temsilci konulduğundan türü için bu yöntem çağrılır `dataContractType` türü.  
  
 Bu aşırı yüklemeler birini ya da döndürmelidir `null` veya seri hale getirilebilir bir nesne. Dışarı aktarılan şema içinde ek açıklama olarak bir null olmayan nesne seri hale. İçin `Type` aşırı yükleme, şemaya verilen her bir türü bu yönteme ilk parametrede surrogated türü ile birlikte gönderilir `dataContractType` parametresi. İçin `MemberInfo` aşırı yükleme, şemaya verilen her bir üyesi olarak bilgilerini gönderir `memberInfo` ikinci parametrede surrogated türüne sahip parametre.  
  
#### <a name="getcustomdatatoexport-method-type-type"></a>(Tür, türü) GetCustomDataToExport yöntemi  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%28System.Type%2CSystem.Type%29?displayProperty=nameWithType> Yöntemi, her tür tanımı için şema dışarı aktarma sırasında çağrılır. Yöntem bilgi şeması içindeki türleri verirken ekler. Tanımlanan her tür, şemada eklenmesi gereken herhangi bir ek veriyi olup olmadığını belirlemek için bu yönteme gönderilir.  
  
#### <a name="getcustomdatatoexport-method-memberinfo-type"></a>GetCustomDataToExport yöntemi (MemberInfo, türü)  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%28System.Reflection.MemberInfo%2CSystem.Type%29?displayProperty=nameWithType> Dışarı aktarılan türlerinde her üye için dışarı aktarma sırasında çağrılır. Bu işlev, dışa aktarma sırasında şema eklenecek üyeleri için açıklamalar özelleştirmenizi sağlar. Bilgi sınıf içindeki her üye için herhangi bir ek veriyi şemada eklenmesi gerekip gerekmediğini kontrol etmek için bu yönteme gönderilir.  
  
 Arar yukarıdaki örnekte `dataContractType` vekil her üyesi için. Ardından, her bir alan için uygun erişim değiştiricisi döndürür. Bu özelleştirme, erişim değiştiricileri için varsayılan değer geneldir. Bu nedenle, bunların gerçek erişim kısıtlamaları nelerdir ne olursa olsun dışarı aktarılan şema kullanılarak oluşturulan kodda genel olarak tüm üyelerinin tanımlanması. Bu uygulama, üye kullanılmadığında `numpens` vekil özel olarak tanımlanan olsa da dışarı aktarılan şemada genel olacaktır. Dışarı aktarılan şema, bu yöntem kullanılarak erişim değiştiricisi özel olarak oluşturulabilir.  
  
### <a name="getreferencedtypeonimport-method"></a>GetReferencedTypeOnImport yöntemi  
 Bu yöntem eşler <xref:System.Type> , özgün türü için temsilci. Bu yöntem, şema içeri aktarma için isteğe bağlıdır.  
  
 Bir şema içeri aktarır ve bir yedek oluşturma için kod oluşturur, sonraki görev özgün türü için bir yedek örneği türünü tanımlamaktır.  
  
 Oluşturulan kodun var olan bir kullanıcı türü başvuru yapması gerekiyorsa, bu uygulama tarafından gerçekleştirilir <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%2A> yöntemi.  
  
 Şema içeri aktarırken, her tür bildirimi yerine temsilci konulduğundan veri anlaşması bir türe eşlemek için bu yöntem çağrılır. Dize parametreleri `typeName` ve `typeNamespace` surrogated türün ad alanı ve adını tanımlayın. Dönüş değeri <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%2A> yeni bir tür oluşturulması gerekip gerekmediğini belirlemek için kullanılır. Bu yöntem, geçerli bir tür veya null döndürmelidir. Geçerli türler için döndürülen tür, oluşturulan kodda başvurulan türü olarak kullanılır. Null değeri döndürülürse, hiçbir tür başvurulan ve yeni bir tür oluşturulması gerekir. Birkaç temsilciler varsa, her temsilci türüne geri başlangıç türü için eşleme gerçekleştirmek mümkündür.  
  
 `customData` Parametredir özgün yönteminden döndürülen nesne <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%2A>. Bu `customData` vekil yazarlar ek veri ipuçları içeri aktarma sırasında kodu oluşturmak için kullanılacak meta verilere eklemek istediğinizde kullanılır.  
  
### <a name="processimportedtype-method"></a>ProcessImportedType yöntemi  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.ProcessImportedType%2A> Yöntemi şema içeri aktarma oluşturulan herhangi bir tür özelleştirir. Bu yöntem, isteğe bağlıdır.  
  
 Şema içeri aktarırken, bu yöntem özelleştirilmesi gereken tüm içeri aktarılan türü ve derleme bilgiler sağlar. Örneğin:  
  
 [!code-csharp[C_IDataContractSurrogate#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#7)]  
  
 İçeri aktarma sırasında oluşturulan her tür için bu yöntem çağrılır. Belirtilen değişiklik <xref:System.CodeDom.CodeTypeDeclaration> veya değiştirme <xref:System.CodeDom.CodeCompileUnit>. Bu ad, üyeleri, öznitelikler ve diğer birçok özelliklerini değiştirme içerir `CodeTypeDeclaration`. İşlem tarafından `CodeCompileUnit`, yönergeleri, ad alanları, başvurulan derlemeleri ve diğer birçok yönünü değiştirmek mümkündür.  
  
 `CodeTypeDeclaration` Parametresi ' % s'kod DOM türü bildirimini içerir. `CodeCompileUnit` Kod işlemek için değiştirme parametresi sağlar.  Döndüren `null` atılmadan tür bildiriminde sonuçlanır. Buna karşılık, döndürülürken bir `CodeTypeDeclaration`, değişiklikler korunur.  
  
 Meta veri dışarı aktarma sırasında özel veriler eklenir, böylece kullanılabilmesi için içeri aktarma işlemi sırasında kullanıcıya sağlanması gerekir. Bu özel veri programlama modeli ipuçları veya diğer açıklamaları için kullanılabilir. Her `CodeTypeDeclaration` ve <xref:System.CodeDom.CodeTypeMember> örnek olarak özel veri içeren <xref:System.CodeDom.CodeObject.UserData%2A> başvurusuna özelliği `IDataContractSurrogate` türü.  
  
 Yukarıdaki örnekte alınan şema üzerinde bazı değişiklikler yapar. Kod, bir yedek kullanarak özgün türün özel üyeleri korur. Şema içeri aktarırken varsayılan erişim değiştiricisidir `public`. Bu nedenle, tüm üyeleri vekil şema, bu örnekte olduğu gibi değiştirilmediği sürece herkes tarafından görülebilir. Dışarı aktarma sırasında özel veri üyeleri özel olan ilgili meta verilere eklenir. Örneğin, özel verileri arar, erişim değiştiricisi özeldir ve ardından uygun bir üye öznitelikleri ayarlayarak özel olacak şekilde değiştirir olup olmadığını denetler. Bu özelleştirme olmadan `numpens` üye genel olarak tanımlanmış özel yerine.  
  
### <a name="getknowncustomdatatypes-method"></a>GetKnownCustomDataTypes yöntemi  
 Bu yöntem, şemadan tanımlanan özel veri türlerini alır. Yöntemi, şema içeri aktarma için isteğe bağlıdır.  
  
 Şema dışarı ve içeri aktarma başında yöntemi çağrılır. Şema içe veya dışa kullanılan özel veri türleri yöntemi döndürür. Yönteme bir <xref:System.Collections.ObjectModel.Collection%601> ( `customDataTypes` parametresi), türleri koleksiyonu. Yöntemi, bu koleksiyona ek bilinen türleri eklemeniz gerekir. Bilinen özel veri türleri, serileştirme ve seri durumundan çıkarma özel veri kullanımının etkinleştirmek için gerekli olan <xref:System.Runtime.Serialization.DataContractSerializer>. Daha fazla bilgi için [veri sözleşme bilinen türleri](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
## <a name="implementing-a-surrogate"></a>Bir yedek uygulama  
 Veri sözleşmesi vekil WCF içinde kullanmak için birkaç özel yordamları izlemelisiniz.  
  
### <a name="to-use-a-surrogate-for-serialization-and-deserialization"></a>Serileştirme ve seri durumundan çıkarma için bir yedek kullanmak için  
 Kullanım <xref:System.Runtime.Serialization.DataContractSerializer> serileştirme ve seri durumundan çıkarma veri yedeği ile gerçekleştirmek için. <xref:System.Runtime.Serialization.DataContractSerializer> Tarafından oluşturulan <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>. Vekil de belirtilmelidir.  
  
##### <a name="to-implement-serialization-and-deserialization"></a>Serileştirme ve seri durumundan çıkarma uygulamak için  
  
1.  Bir örneğini oluşturmak <xref:System.ServiceModel.ServiceHost> hizmetiniz için. Eksiksiz yönergeler için bkz: [temel WCF programlama](../../../../docs/framework/wcf/basic-wcf-programming.md).  
  
2.  İçin her <xref:System.ServiceModel.Description.ServiceEndpoint> belirtilen hizmet ana bilgisayarı, bulmak, <xref:System.ServiceModel.Description.OperationDescription>.  
  
3.  Örneği olup olmadığını belirlemek için işlem davranışları aracılığıyla aramayı <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> bulunur.  
  
4.  Varsa bir <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> bulunamadı, ayarla, <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.DataContractSurrogate%2A> vekil yeni bir örneğini özelliğini. Hayır ise <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> bulunamadı, ardından yeni bir örneğini oluşturun ve ayarlayın <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.DataContractSurrogate%2A> yeni davranış için yeni bir örneğini vekil üyesi.  
  
5.  Son olarak, bu yeni davranış için geçerli işlem davranışları, aşağıdaki örnekte gösterildiği gibi ekleyin:  
  
     [!code-csharp[C_IDataContractSurrogate#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#8)]  
  
### <a name="to-use-a-surrogate-for-metadata-import"></a>Bir yedek meta veri alma için kullanılacak  
 İstemci tarafı kod oluşturmak için WSDL ve XSD gibi meta veriler içeri aktarılırken vekil XSD şema, kod oluşturma için sorumlu bileşenine eklenmesi gerekir <xref:System.Runtime.Serialization.XsdDataContractImporter>. Bunu yapmak için doğrudan değiştirme <xref:System.ServiceModel.Description.WsdlImporter> meta verileri almak için kullanılır.  
  
##### <a name="to-implement-a-surrogate-for-metadata-importation"></a>Meta verileri içeri aktarma için bir temsilci uygulamak için  
  
1.  Meta verileri kullanarak içeri aktarma <xref:System.ServiceModel.Description.WsdlImporter> sınıfı.  
  
2.  Kullanım <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> denetlenecek yöntemi olup olmadığını bir <xref:System.Runtime.Serialization.XsdDataContractImporter> tanımlanmış.  
  
3.  Varsa <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> yöntemi döndürür `false`, yeni bir <xref:System.Runtime.Serialization.XsdDataContractImporter> ve kendi <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> özelliğine yeni bir örneğini <xref:System.Runtime.Serialization.ImportOptions> sınıfı. Aksi takdirde içeri Aktarıcı tarafından döndürülen kullanın `out` parametresinin <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> yöntemi.  
  
4.  Varsa <xref:System.Runtime.Serialization.XsdDataContractImporter> hiçbir <xref:System.Runtime.Serialization.ImportOptions> tanımlanan ve ardından yeni bir örneğini özelliğini ayarlayın <xref:System.Runtime.Serialization.ImportOptions> sınıfı.  
  
5.  Ayarlama <xref:System.Runtime.Serialization.ImportOptions.DataContractSurrogate%2A> özelliği <xref:System.Runtime.Serialization.ImportOptions> , <xref:System.Runtime.Serialization.XsdDataContractImporter> vekil yeni bir örneğini için.  
  
6.  Ekleme <xref:System.Runtime.Serialization.XsdDataContractImporter> tarafından döndürülen koleksiyona <xref:System.ServiceModel.Description.MetadataExporter.State%2A> özelliği <xref:System.ServiceModel.Description.WsdlImporter> (devralınan <xref:System.ServiceModel.Description.MetadataExporter> sınıfı.)  
  
7.  Kullanım <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A> yöntemi <xref:System.ServiceModel.Description.WsdlImporter> veri sözleşmeleri şeması içindeki tüm içeri aktarabilirsiniz. Son adımda kod vekil çağırarak yüklenen şemaları oluşturulur.  
  
     [!code-csharp[C_IDataContractSurrogate#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#9)]  
  
### <a name="to-use-a-surrogate-for-metadata-export"></a>Meta veri dışarı aktarma için bir yedek kullanmak için  
 Varsayılan meta veri hizmeti için WCF verilirken, WSDL hem XSD şema oluşturulması gerekir. Yedek oluşturma XSD şeması için veri anlaşması türleri, sorumlu bileşenine eklenmesi gerekir <xref:System.Runtime.Serialization.XsdDataContractExporter>. Bunu yapmak için ya da uygulayan bir davranışı kullanmak <xref:System.ServiceModel.Description.IWsdlExportExtension> değiştirmek için <xref:System.ServiceModel.Description.WsdlExporter>, veya doğrudan değiştirme <xref:System.ServiceModel.Description.WsdlExporter> meta verileri dışarı aktarmak için kullanılır.  
  
##### <a name="to-use-a-surrogate-for-metadata-export"></a>Meta veri dışarı aktarma için bir yedek kullanmak için  
  
1.  Yeni bir <xref:System.ServiceModel.Description.WsdlExporter> veya `wsdlExporter` geçirilen <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A> yöntemi.  
  
2.  Kullanım <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> denetlemek için işlev olup olmadığını bir <xref:System.Runtime.Serialization.XsdDataContractExporter> tanımlanmış.  
  
3.  Varsa <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> döndürür `false`, yeni bir <xref:System.Runtime.Serialization.XsdDataContractExporter> oluşturulan XML şemaları ile <xref:System.ServiceModel.Description.WsdlExporter>ve döndürdüğü koleksiyona ekleyin <xref:System.ServiceModel.Description.MetadataExporter.State%2A> özelliği <xref:System.ServiceModel.Description.WsdlExporter>. Tarafından döndürülen verici kullanmayacak `out` parametresinin <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> yöntemi.  
  
4.  Varsa <xref:System.Runtime.Serialization.XsdDataContractExporter> hiçbir <xref:System.Runtime.Serialization.ExportOptions> tanımlanan sonra ayarlanmış <xref:System.Runtime.Serialization.XsdDataContractExporter.Options%2A> özelliğine yeni bir örneğini <xref:System.Runtime.Serialization.ExportOptions> sınıfı.  
  
5.  Ayarlama <xref:System.Runtime.Serialization.ExportOptions.DataContractSurrogate%2A> özelliği <xref:System.Runtime.Serialization.ExportOptions> , <xref:System.Runtime.Serialization.XsdDataContractExporter> vekil yeni bir örneğini için. Meta verileri dışarı aktarma için sonraki adımlar herhangi bir değişiklik gerektirmez.  
  
     [!code-csharp[C_IDataContractSurrogate#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#10)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.IDataContractSurrogate>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.Runtime.Serialization.ImportOptions>
- <xref:System.Runtime.Serialization.ExportOptions>
- [Veri Anlaşmalarını Kullanma](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
