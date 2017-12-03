---
title: "Veri Sözleşmesi Yedekleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: data contracts [WCF], surrogates
ms.assetid: 8c31134c-46c5-4ed7-94af-bab0ac0dfce5
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b8d353b50cf9439a9741199a52ca650e02e4d49f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="data-contract-surrogates"></a>Veri Sözleşmesi Yedekleri
Veri sözleşmesi *yedek* veri sözleşmesi modeli yerleşik Gelişmiş bir özelliktir. Bu özellik türü özelleştirme ve kullanıcılar nasıl bir türü seri durumdan çıkarılmış veya meta veri içine tahmini serileştirilir değiştirmek istediğiniz durumlarda değiştirme için kullanılmak üzere tasarlanmıştır. Burada bir yedek kullanılabilir bazı senaryolar türü, alanları ve özellikleri ile işaretlenmemiş için bir veri sözleşmesi belirtilmemiş olduğunda <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliği ya da kullanıcılar şema Çeşitlemeler dinamik olarak oluşturmak istediğiniz.  
  
 Seri hale getirme ve seri durumdan çıkarma başarılır ile veri sözleşmesi yedek kullanırken <xref:System.Runtime.Serialization.DataContractSerializer> .NET Framework'XML gibi uygun bir biçime dönüştürmek için. Veri sözleşmesi yedek meta veri Beyanları XML Şeması belgeleri (XSD) gibi üretirken türleri için dışa aktarılan meta verilerini değiştirmek için de kullanılabilir. İçe aktarma, üzerine kod meta verilerinden oluşturulur ve yedek bu durumda da oluşturulan kod özelleştirmek için kullanılabilir.  
  
## <a name="how-the-surrogate-works"></a>Yedek nasıl çalışır?  
 Bir yedek başka bir tür ("surrogated" türü) için eşleme bir türü ("özgün" türü) çalışır. Aşağıdaki örnek, özgün türünü gösterir `Inventory` ve yeni bir yedek `InventorySurrogated` türü. `Inventory` Türü seri hale getirilebilir değil ancak `InventorySurrogated` türü:  
  
 [!code-csharp[C_IDataContractSurrogate#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#1)]  
  
 Veri sözleşmesi Bu sınıf için tanımlı değil çünkü bir veri sözleşmesi yedek sınıfıyla sınıfı dönüştürülemiyor. Surrogated sınıfı, aşağıdaki örnekte gösterilmiştir:  
  
 [!code-csharp[C_IDataContractSurrogate#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#2)]  
  
## <a name="implementing-the-idatacontractsurrogate"></a>IDataContractSurrogate uygulama  
 Veri sözleşmesi yedek kullanmak için uygulama <xref:System.Runtime.Serialization.IDataContractSurrogate> arabirimi.  
  
 Her yöntem genel bir bakış verilmiştir <xref:System.Runtime.Serialization.IDataContractSurrogate> olası bir uygulama.  
  
### <a name="getdatacontracttype"></a>GetDataContractType  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> Yöntemi başka bir tür eşler. Bu yöntem serileştirme, seri durumdan çıkarma, içeri ve dışarı aktarma için gereklidir.  
  
 İlk görev türleri ne olacağını tanımlayan diğer türlerine eşlenir. Örneğin:  
  
 [!code-csharp[C_IDataContractSurrogate#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#3)]  
  
-   Serileştirme üzerinde bu yöntem tarafından döndürülen eşleme sonradan surrogated örneği özgün örneğe çağırarak dönüştürmek için kullanılır <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> yöntemi.  
  
-   Seri kaldırma işleminde, bu yöntem tarafından döndürülen eşleme yedek türünün bir örneği seri durumdan çıkarılacak seri hale getirici tarafından kullanılır. Daha sonra çağırır <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%2A> surrogated örneği özgün türünün bir örneğine dönüştürülecek.  
  
-   Dışarı aktarma üzerinde meta verileri oluşturmak için kullanılacak veri sözleşmesi almak için bu yöntem tarafından döndürülen yedek türü yansıtılır.  
  
-   İçeri aktarma işlemi sırasında ilk türü desteğine başvurma gibi amaçlarla kullanmak için veri sözleşmesi almak için yansıtılan bir temsilci türü değiştirildi.  
  
 <xref:System.Type> Parametredir, seri durumdan çıkarılmış, içe aktarılan ya da dışarı aktarılan serileştirilmekte olan nesnenin türü. <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> Yedek türü işlemedi varsa, yöntem giriş türü döndürmesi gerekir. Aksi takdirde, uygun surrogated türünü döndürür. Birçok yedek yoksa, bu yöntemi, çok sayıda eşlemeleri tanımlanabilir.  
  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> Yöntemi çağrılmaz için yerleşik veri sözleşmesi temelleri gibi <xref:System.Int32> veya <xref:System.String>. Diziler, kullanıcı tanımlı türler ve diğer veri yapılarını gibi diğer türleri için her tür için bu yöntem çağrılır.  
  
 Önceki örnekte, yöntem denetler `type` parametre ve `Inventory` benzer. Bu nedenle, yöntem kendisine eşleniyorsa `InventorySurrogated`. Bir seri hale getirme olduğunda, seri durumdan çıkarma, içeri aktarma şema veya dışarı aktarma şema olarak adlandırılır, bu işlev varsayılan türleri arasında eşleme belirlemek için çağrılır.  
  
### <a name="getobjecttoserialize-method"></a>GetObjectToSerialize yöntemi  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> Yöntemi özgün türü örneği surrogated türü örneğine dönüştürür. Yöntemi, seri hale getirme için gereklidir.  
  
 Fiziksel veri eşleştirilir özgün örneğinden yedek uygulayarak şekilde tanımlamak için sonraki adımdır <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> yöntemi. Örneğin:  
  
 [!code-csharp[C_IDataContractSurrogate#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#4)]  
  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> Bir nesne serileştirildiğinde yöntemi çağrılır. Bu yöntem, özgün türünden surrogated türünde alanlar için verileri aktarır. Alanları doğrudan alanları vekil eşlenebilir veya özgün veriyi işlemeleri yedek depolanabilir. Bazı olası kullanımları şunlardır: doğrudan alanlarını eşleme, surrogated alanlarında depolanan veriler üzerinde işlemler veya özgün türü XML surrogated alanında saklanması.  
  
 `targetType` Parametresi üyesinin bildirilen bir türe başvurur. Bu parametre, tarafından döndürülen surrogated türüdür <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> yöntemi. Seri hale getirici döndürülen nesne bu türe atanabilir uygulamaz. `obj` Nesneyi serileştirmek için bir parametredir ve gerekirse, yedek dönüştürülür. Bu yöntem, surrogated nesne işlemiyor durumunda giriş nesnesi döndürmesi gerekir. Aksi takdirde, yeni bir yedek nesne döndürülür. Nesne null ise temsilci çağrılmaz. Çok sayıda yedek eşlemeleri farklı örnekleri için bu yöntem içinde tanımlanabilir.  
  
 Oluştururken bir <xref:System.Runtime.Serialization.DataContractSerializer>, nesne başvuruları korumak için söyleyebilirsiniz. ([!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Seri hale getirme ve seri durumdan çıkarma](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).) Bu ayarlayarak yapılır `preserveObjectReferences` kendi oluşturucuya parametresinde `true`. Bu durumda, tüm sonraki serializations başvuru akışa yazmanız yeterlidir beri yedek bir nesne için yalnızca bir kez çağrılır. Varsa `preserveObjectReferences` ayarlanır `false`, sonra bir örneği ile her karşılaşmanızda yedek olarak adlandırılır.  
  
 Seri hale getirilmiş örnek türü bildirilen türünden farklıysa, türü bilgileri akışa, örneğin, yazılır `xsi:type` diğer sonunda seri durumdan çıkarılacak örneği izin vermek için. Bu işlem, nesne veya surrogated gerçekleşir.  
  
 Yukarıdaki örnek verileri dönüştürür `Inventory` , örneğine `InventorySurrogated`. Nesne türünü denetler ve surrogated türüne dönüştürmek için gerekli işlemeleri gerçekleştirir. Bu durumda, alanlarını `Inventory` sınıfı doğrudan kopyalanır üzerinden `InventorySurrogated` sınıf alanları.  
  
### <a name="getdeserializedobject-method"></a>GetDeserializedObject yöntemi  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%2A> Yöntemi surrogated türü örneği özgün türü örneğine dönüştürür. Çıkarma için gereklidir.  
  
 Sonraki görev, fiziksel veri yedek örneğinden asıl eşleneceği yol tanımlamaktır. Örneğin:  
  
 [!code-csharp[C_IDataContractSurrogate#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#5)]  
  
 Bu yöntem yalnızca bir nesne seri kaldırma sırasında çağrılır. Yedek türünden ters veri eşleme seri durumundan çıkarma için özgün türünü sağlar. Benzer şekilde `GetObjectToSerialize` yöntemi, bazı olası kullanımları doğrudan alan veri değişimi, veriler üzerinde işlemler gerçekleştirmek ve XML verilerini depolamak için olabilir. Seri durumdan çıkarılırken, her zaman tam veri değerleri için veri dönüştürme işlemeleri nedeniyle özgün almak değil.  
  
 `targetType` Parametresi üyesinin bildirilen bir türe başvurur. Bu parametre, tarafından döndürülen surrogated türüdür `GetDataContractType` yöntemi. `obj` Parametre seri durumdan nesnesine başvuruyor. Surrogated, nesne özgün türüne dönüştürülebilir. Yedek nesne işlemiyor varsa bu yöntem giriş nesnesi döndürür. Aksi takdirde, dönüştürme tamamlandığında seri durumdan çıkarılmış nesne döndürülür. Yedek birçok varsa, veri dönüştürme yedek birincil türe her her türü belirterek ve onun dönüştürme sağlayabilir.  
  
 Bir nesne döndürülürken iç nesne tablolar bu yedek tarafından döndürülen nesne ile güncelleştirilir. Sonraki tüm başvuruları örneğine surrogated örnek nesne tablolardan elde eder.  
  
 Önceki örnekte türündeki nesneleri dönüştürür `InventorySurrogated` ilk yazmasını `Inventory`. Bu durumda, verileri doğrudan geri aktarılır `InventorySurrogated` karşılık gelen alanlara `Inventory`. Hiçbir veri değişikliklerini olduğundan üye alanlarının her seri hale getirme önce aynı değerleri içerir.  
  
### <a name="getcustomdatatoexport-method"></a>GetCustomDataToExport yöntemi  
 Bir şema verilirken <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%2A> yöntemdir isteğe bağlıdır. Ek veri veya ipuçları dışarı aktarılan şemaya eklemek için kullanılır. Ek veri üye düzeyinde veya türü düzeyinde eklenebilir. Örneğin:  
  
 [!code-csharp[C_IDataContractSurrogate#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#6)]  
  
 Bu yöntemle (iki aşırı) ek bilgileri meta verilerine dahil edilmesi üye veya türü düzeyinde ya da sağlar. Üye ortak veya özel ve dışarı ve içeri aktarma şemasının korunması açıklamaları olup olmadığına dair ipuçları eklemek mümkündür. Bu yöntem gibi bilgiler kaybolacak. Bu yöntem ekleme veya üyeleri veya türleri silinmesine neden olmaz ancak bu düzeyleri birini adresindeki şemaları yerine ek veri ekler.  
  
 Yöntemi aşırı yüklendi ve ya da alabilir bir `Type` (`clrtype` parametresi) veya <xref:System.Reflection.MemberInfo> (`memberInfo` parametresi). İkinci parametre her zaman olduğu bir `Type` (`dataContractType` parametresi). Bu yöntem her üye ve surrogated türü için çağrılır `dataContractType` türü.  
  
 Bu aşırı birini ya da döndürmelidir `null` veya serileştirilebilir bir nesne. Dışarı aktarılan Şeması ek açıklama olarak bir null olmayan nesne seri hale getirilir. İçin `Type` aşırı yüklemesi şemaya dışarı her tür gönderildiği ilk parametre surrogated türü ile birlikte Bu yöntemde `dataContractType` parametresi. İçin `MemberInfo` aşırı yüklemesi şemaya dışarı her üye olarak bilgilerini gönderir `memberInfo` ikinci parametrede surrogated türüne sahip parametre.  
  
#### <a name="getcustomdatatoexport-method-type-type"></a>GetCustomDataToExport yöntemi (tür, tür)  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%28System.Type%2CSystem.Type%29?displayProperty=nameWithType> Yöntemi, her tür tanımı için şema dışa aktarma sırasında çağrılır. Yöntemi bilgi türleri şeması içindeki verilirken ekler. Tanımlanan her tür şemada dahil edilmesi gereken herhangi bir ek veriyi olup olmadığını belirlemek için bu yöntem için gönderilir.  
  
#### <a name="getcustomdatatoexport-method-memberinfo-type"></a>GetCustomDataToExport yöntemi (MemberInfo, türü)  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%28System.Reflection.MemberInfo%2CSystem.Type%29?displayProperty=nameWithType> Verilir türleri her üye dışa aktarma sırasında çağrılır. Bu işlev, dışa aktarma sırasında şema dahil edilecek üyeler için tüm yorumlar özelleştirmenizi sağlar. Bilgi sınıf içindeki her üye için bu yöntem herhangi bir ek veriyi şemada eklenmesi gerekip gerekmediğini denetleyin gönderilir.  
  
 Aramalar Yukarıdaki örnek `dataContractType` yedek her bir üyesi için. Ardından, her bir alan için uygun erişim değiştiricisi döndürür. Erişim değiştiricileri için varsayılan değer bu özelleştirme olmadan geneldir. Bu nedenle, tüm üyeleri bunların gerçek erişim kısıtlamaları nelerdir olsun dışarı aktarılan Şeması kullanılarak oluşturulan kodda ortak olarak tanımlanması. Bu uygulama, üye kullanmadığınızda `numpens` yedek özel olarak tanımlanan olsa da dışarı aktarılan şemada genel olacaktır. Bu yöntemde, dışarı aktarılan şemanın kullanımı ile erişim değiştiricisi özel olarak oluşturulabilir.  
  
### <a name="getreferencedtypeonimport-method"></a>GetReferencedTypeOnImport yöntemi  
 Bu yöntem eşler <xref:System.Type> özgün türü için yedek olarak. Bu yöntem için şema başlangıcından isteğe bağlıdır.  
  
 Bir yedek oluşturmayı bir şema alır ve bunun için kod oluşturur, sonraki görev için özgün türüne bir yedek örneği türünü tanımlamak için değildir.  
  
 Oluşturulan kodun var olan bir kullanıcı türü başvuru gerekiyorsa, bu uygulama tarafından yapılır <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%2A> yöntemi.  
  
 Bir şema içe aktarırken, bu yöntem surrogated veri sözleşmesi bir türüyle eşleştirmek her tür bildirimi için çağrılır. Dize parametreleri `typeName` ve `typeNamespace` surrogated türünün ad alanını ve adını tanımlayın. Dönüş değeri <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%2A> yeni bir tür oluşturulması gerekip gerekmediğini belirlemek için kullanılır. Bu yöntem, geçerli bir tür veya null döndürmesi gerekir. Geçerli türler için oluşturulan kodda başvurulan bir türü olarak döndürülen türü kullanılır. Null değeri döndürülür, tür başvurulacak ve yeni bir tür oluşturulması gerekir. Birkaç temsilciler varsa, her yedek türü başlangıç türü için geri eşlemeyi gerçekleştirmek mümkündür.  
  
 `customData` Parametredir başlangıçta yönteminden döndürülen nesne <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%2A>. Bu `customData` yedek yazarlar ek veri ipuçları kod oluşturmak için içeri aktarma sırasında kullanılacak meta veri eklemek istediğinizde kullanılır.  
  
### <a name="processimportedtype-method"></a>ProcessImportedType yöntemi  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.ProcessImportedType%2A> Yöntemi özelleştirir şema başlangıcından oluşturulan herhangi bir tür. Bu yöntem isteğe bağlıdır.  
  
 Bir şema içe aktarırken, bu yöntem özelleştirilmek üzere tüm içeri aktarılan türü ve derleme bilgilerini sağlar. Örneğin:  
  
 [!code-csharp[C_IDataContractSurrogate#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#7)]  
  
 İçeri aktarma sırasında oluşturulan her tür için bu yöntem çağrılır. Belirtilen değiştirme <xref:System.CodeDom.CodeTypeDeclaration> veya değiştirme <xref:System.CodeDom.CodeCompileUnit>. Bu ad, üyeler, öznitelikler ve diğer birçok özelliklerini değiştirme içerir `CodeTypeDeclaration`. İşlem tarafından `CodeCompileUnit`, yönergeleri, ad alanları, başvurulan derlemeler ve diğer çeşitli yönlerini değiştirmek mümkündür.  
  
 `CodeTypeDeclaration` Parametresi DOM türü bildirimi kodunu içerir. `CodeCompileUnit` Kodu işlemek için değiştirme parametresi sağlar.  Döndürme `null` atılmadan tür bildiriminde neden olur. Buna karşılık, döndürülürken bir `CodeTypeDeclaration`, değişiklikler korunur.  
  
 Özel veri meta verileri dışa aktarma sırasında eklediyseniz, böylece kullanılabilmesi için içeri aktarma sırasında kullanıcıya sağlanması gerekiyor. Bu özel veri programlama modeli ipuçları veya diğer açıklamaları için kullanılabilir. Her `CodeTypeDeclaration` ve <xref:System.CodeDom.CodeTypeMember> örneği içeren özel veri olarak <xref:System.CodeDom.CodeObject.UserData%2A> için cast özelliği `IDataContractSurrogate` türü.  
  
 Yukarıdaki örnekte alınan şema üzerinde bazı değişiklikler gerçekleştirir. Kod, bir yedek kullanarak özgün türün özel üyeleri korur. Bir şema alırken varsayılan erişim değiştiricisi `public`. Bu nedenle, tüm üyeleri yedek şema, bu örnekteki değiştiren sürece ortak olacaktır. Dışa aktarma sırasında özel veriler hakkında üyeleri özel meta verileri eklenir. Örneğin, özel verileri arayan, erişim değiştiricisi özeldir ve özniteliklerini ayarlayarak özel olarak uygun üye değiştirir olup olmadığını denetler. Bu özelleştirme olmadan `numpens` üye genel olarak tanımlanan özel yerine.  
  
### <a name="getknowncustomdatatypes-method"></a>GetKnownCustomDataTypes yöntemi  
 Bu yöntem şemadan tanımlı özel veri türleri alır. Yöntem için şema başlangıcından isteğe bağlıdır.  
  
 Yöntem şema dışarı ve içeri aktarma başında çağrılır. Bu yöntem, dışarı veya içeri aktarılan şemasında kullanılan özel veri türleri döndürür. Yöntemine geçirilen bir <xref:System.Collections.ObjectModel.Collection%601> ( `customDataTypes` parametresi), türleri koleksiyonu. Yöntemi, bu koleksiyona ek bilinen türleri eklemeniz gerekir. Bilinen özel veri türleri seri hale getirme ve seri durumdan çıkarma özel verileri kullanarak etkinleştirmek için gerekli olan <xref:System.Runtime.Serialization.DataContractSerializer>. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Veri sözleşmesi bilinen türler](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
## <a name="implementing-a-surrogate"></a>Bir yedek uygulama  
 Veri sözleşmesi yedek içinde kullanmak için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], birkaç özel yordamları izlemeniz gerekir.  
  
### <a name="to-use-a-surrogate-for-serialization-and-deserialization"></a>Serileştirme ve seri durumundan çıkarma için bir yedek kullanmak için  
 Kullanım <xref:System.Runtime.Serialization.DataContractSerializer> seri hale getirme ve seri durumdan çıkarma veri yedeği ile gerçekleştirmek için. <xref:System.Runtime.Serialization.DataContractSerializer> Tarafından oluşturulan <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>. Yedek de belirtilmesi gerekir.  
  
##### <a name="to-implement-serialization-and-deserialization"></a>Serileştirme ve seri durumdan çıkarma uygulamak için  
  
1.  Bir örneğini oluşturmak <xref:System.ServiceModel.ServiceHost> hizmetiniz için. Tam yönergeler için bkz: [temel WCF programlama](../../../../docs/framework/wcf/basic-wcf-programming.md).  
  
2.  İçin her <xref:System.ServiceModel.Description.ServiceEndpoint> belirtilen hizmet konağının bulmak, <xref:System.ServiceModel.Description.OperationDescription>.  
  
3.  Arama işlemi davranışları örneği olup olmadığı belirlenemiyor aracılığıyla <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> bulunur.  
  
4.  Varsa bir <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> bulundu, ayarlamak kendi <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.DataContractSurrogate%2A> yedek yeni bir örneğini özelliğine. Öyle değilse <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> bulunamadı, ardından yeni bir örneğini oluşturun ve ayarlayın <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.DataContractSurrogate%2A> yedek yeni bir örneğini yeni davranışı üyesi.  
  
5.  Son olarak, bu yeni davranış geçerli işlemi davranışları, aşağıdaki örnekte gösterildiği gibi ekleyin:  
  
     [!code-csharp[C_IDataContractSurrogate#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#8)]  
  
### <a name="to-use-a-surrogate-for-metadata-import"></a>Bir yedek meta veri alma için kullanmak için  
 İstemci tarafı kodlar oluşturmak için WSDL ve XSD gibi meta verileri içe aktarırken, yedek XSD şemadan kodu oluşturmak için sorumlu bileşenine eklenmesi gerekir <xref:System.Runtime.Serialization.XsdDataContractImporter>. Bunu yapmak için doğrudan değiştirmek <xref:System.ServiceModel.Description.WsdlImporter> meta verileri içe aktarmak için kullanılır.  
  
##### <a name="to-implement-a-surrogate-for-metadata-importation"></a>Meta verileri içe aktarılması için bir yedek uygulamak için  
  
1.  Meta verileri kullanarak içe <xref:System.ServiceModel.Description.WsdlImporter> sınıfı.  
  
2.  Kullanım <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> denetlemek için yöntemi olup olmadığını bir <xref:System.Runtime.Serialization.XsdDataContractImporter> tanımlanmış.  
  
3.  Varsa <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> yöntemi döndürür `false`, yeni bir <xref:System.Runtime.Serialization.XsdDataContractImporter> ve kendi <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> yeni bir örneğini özelliğine <xref:System.Runtime.Serialization.ImportOptions> sınıfı. Aksi takdirde tarafından döndürülen içeri Aktarıcı kullanın `out` parametresinin <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> yöntemi.  
  
4.  Varsa <xref:System.Runtime.Serialization.XsdDataContractImporter> hiç <xref:System.Runtime.Serialization.ImportOptions> tanımlanan sonra yeni bir örneğini özelliğini ayarlamak <xref:System.Runtime.Serialization.ImportOptions> sınıfı.  
  
5.  Ayarlama <xref:System.Runtime.Serialization.ImportOptions.DataContractSurrogate%2A> özelliği <xref:System.Runtime.Serialization.ImportOptions> , <xref:System.Runtime.Serialization.XsdDataContractImporter> yedek yeni bir örneğini için.  
  
6.  Ekleme <xref:System.Runtime.Serialization.XsdDataContractImporter> tarafından döndürülen koleksiyonuna <xref:System.ServiceModel.Description.MetadataExporter.State%2A> özelliği <xref:System.ServiceModel.Description.WsdlImporter> (devralınan <xref:System.ServiceModel.Description.MetadataExporter> sınıfı.)  
  
7.  Kullanım <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A> yöntemi <xref:System.ServiceModel.Description.WsdlImporter> tümünü şeması içindeki veri sözleşmeleri almak için. Son adımı sırasında yedek çağırarak yüklenen şemaları kodu oluşturulur.  
  
     [!code-csharp[C_IDataContractSurrogate#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#9)]  
  
### <a name="to-use-a-surrogate-for-metadata-export"></a>Meta veri dışarı aktarma için bir yedek kullanmak için  
 Varsayılan olarak meta verilerini dışa aktarırken, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bir hizmet için WSDL ve XSD şema oluşturulması gerekiyor. Yedek veri sözleşme türleri için oluşturma XSD şema sorumlu bileşenine eklenmesi gerekir <xref:System.Runtime.Serialization.XsdDataContractExporter>. Bunu yapmak için kullanın ya da uygulayan bir davranış <xref:System.ServiceModel.Description.IWsdlExportExtension> değiştirmek için <xref:System.ServiceModel.Description.WsdlExporter>, veya doğrudan değiştirmek <xref:System.ServiceModel.Description.WsdlExporter> meta verilerini dışa aktarmak için kullanılır.  
  
##### <a name="to-use-a-surrogate-for-metadata-export"></a>Meta veri dışarı aktarma için bir yedek kullanmak için  
  
1.  Yeni bir <xref:System.ServiceModel.Description.WsdlExporter> veya `wsdlExporter` parametresi geçirilen <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A> yöntemi.  
  
2.  Kullanım <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> denetlemek için işlevini olup bir <xref:System.Runtime.Serialization.XsdDataContractExporter> tanımlanmış.  
  
3.  Varsa <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> döndürür `false`, yeni bir <xref:System.Runtime.Serialization.XsdDataContractExporter> oluşturulan XML şemaları ile <xref:System.ServiceModel.Description.WsdlExporter>ve tarafından döndürülen koleksiyonuna ekleyin <xref:System.ServiceModel.Description.MetadataExporter.State%2A> özelliği <xref:System.ServiceModel.Description.WsdlExporter>. Aksi takdirde tarafından döndürülen dışarı aktarma kullanın `out` parametresinin <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> yöntemi.  
  
4.  Varsa <xref:System.Runtime.Serialization.XsdDataContractExporter> hiç <xref:System.Runtime.Serialization.ExportOptions> tanımlanan sonra ayarlamak <xref:System.Runtime.Serialization.XsdDataContractExporter.Options%2A> yeni bir örneğini özelliğine <xref:System.Runtime.Serialization.ExportOptions> sınıfı.  
  
5.  Ayarlama <xref:System.Runtime.Serialization.ExportOptions.DataContractSurrogate%2A> özelliği <xref:System.Runtime.Serialization.ExportOptions> , <xref:System.Runtime.Serialization.XsdDataContractExporter> yedek yeni bir örneğini için. Meta verileri dışarı aktarma için sonraki adımları herhangi bir değişiklik gerektirmez.  
  
     [!code-csharp[C_IDataContractSurrogate#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#10)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Runtime.Serialization.IDataContractSurrogate>  
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>  
 <xref:System.Runtime.Serialization.ImportOptions>  
 <xref:System.Runtime.Serialization.ExportOptions>  
 [Veri sözleşmelerini kullanma](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
