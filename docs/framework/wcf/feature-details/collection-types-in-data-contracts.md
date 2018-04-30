---
title: Veri Sözleşmelerinde Koleksiyon Türleri
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- collection types [WCF], data contracts
- data contracts [WCF], collection types
- collection types [WCF]
ms.assetid: 9b45b28e-0a82-4ea3-8c33-ec0094aff9d5
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c771d78c5e78feabcfe883934ed7ea3589c938d2
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="collection-types-in-data-contracts"></a>Veri Sözleşmelerinde Koleksiyon Türleri
A *koleksiyonu* belirli bir türdeki öğeleri listesini içerir. İçinde [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], böyle listeleri dizileri veya diğer türleri çeşitli kullanarak temsil edilebilir (genel listesi, genel <xref:System.ComponentModel.BindingList%601>, <xref:System.Collections.Specialized.StringCollection>, veya <xref:System.Collections.ArrayList>). Örneğin, bir koleksiyon için belirli bir müşteri adresleri listesi tutabilir. Bu koleksiyon adı verilen *listesinde koleksiyonları*kendi gerçek türü ne olursa olsun.  
  
 Özel bir form koleksiyonu bir öğe ("anahtarı") ve başka bir ("değeri") arasındaki bir ilişkiyi temsil eden bulunmaktadır. İçinde [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], bunlar türlerine göre aşağıdaki gibi gösterilir <xref:System.Collections.Hashtable> ve genel bir sözlük. Örneğin, bir ilişki koleksiyonu Şehir ("anahtarı"), popülasyon ("değeri") eşleyebilir. Bu koleksiyon adı verilen *sözlük koleksiyonları*kendi gerçek türü ne olursa olsun.  
  
 Koleksiyonları veri sözleşmesi modelinde özel işleme alırsınız.  
  
 Türleri uygulayan <xref:System.Collections.IEnumerable> arabirimi dizileri ve genel koleksiyonlar dahil olmak üzere, koleksiyon olarak tanınmıyor. Bu, bu uygulama türleri <xref:System.Collections.IDictionary> veya genel <xref:System.Collections.Generic.IDictionary%602> arabirimleri sözlük koleksiyonları; diğerleri listesine koleksiyonlarıdır.  
  
 Koleksiyon türleri'adlı bir yöntemi olması gibi ek gereksinimleri `Add` ve varsayılan bir oluşturucu, aşağıdaki bölümlerde ayrıntılı olarak ele alınmıştır. Bu koleksiyon türleri hem seri durumdan ve sağlar. Bazı koleksiyonlar doğrudan, gibi genel desteklenmediğini yani <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> (varsayılan oluşturucu yok olduğundan). Ancak, bu kısıtlamalar atlamak hakkında daha fazla bilgi için bu konunun devamındaki "Kullanarak koleksiyon arabirimi türleri ve salt okunur koleksiyonları" bölümüne bakın.  
  
 Koleksiyonlarda yer alan türleri veri sözleşme türleri veya aksi halde seri hale getirilebilir. Daha fazla bilgi için bkz: [veri sözleşmesi seri hale getirici tarafından desteklenen türleri](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md).  
  
 Nedir ve ne geçerli bir koleksiyon olarak kabul edilmez hakkında yanı sıra koleksiyonlar nasıl serileştirilmiş hakkında daha fazla bilgi için bu konunun "Gelişmiş toplama kuralları" bölümünde biçimlendiricisi koleksiyonları hakkında bilgi bakın.  
  
## <a name="interchangeable-collections"></a>Birbirinin yerine koleksiyonları  
 Tüm liste koleksiyonları aynı türde aynı verilere sahip düşünülür Sözleşme (kullanarak özelleştirilen sürece <xref:System.Runtime.Serialization.CollectionDataContractAttribute> özniteliği, bu konunun ilerleyen bölümlerinde açıklandığı gibi). Bu nedenle, örneğin, aşağıdaki veri sözleşmeleri eşdeğerdir.  
  
 [!code-csharp[c_collection_types_in_data_contracts#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#0)]
 [!code-vb[c_collection_types_in_data_contracts#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#0)]  
  
 Her iki veri sözleşmeleri XML aşağıdaki kodu benzer sonuçlanır.  
  
```xml  
<PurchaseOrder>  
    <customerName>...</customerName>  
    <items>  
        <Item>...</Item>  
        <Item>...</Item>  
        <Item>...</Item>  
        ...  
    </items>  
    <comments>  
        <string>...</string>  
        <string>...</string>  
        <string>...</string>  
        ...  
    </comments>  
</PurchaseOrder>  
```  
  
 Koleksiyon interchangeability kullanmanızı, örneğin, sunucudaki performansı en iyi hale getirilmiş bir koleksiyon türü ve kullanıcı arabirimi bileşenlerini istemcide bağlanması için tasarlanmış bir koleksiyon türü sağlar.  
  
 Benzer şekilde listesi koleksiyonları, aynı anahtar ve değer türleri olan tüm sözlük koleksiyonları aynı verilere sahip kabul edilir Sözleşme (tarafından özelleştirmediyseniz <xref:System.Runtime.Serialization.CollectionDataContractAttribute> özniteliği).  
  
 Yalnızca veri sözleşmesi türü koleksiyonu eşdeğer ilgili olarak çok önemlidir, .NET türleri değil. Diğer bir deyişle, type1 ve Type2 eşdeğer veri sözleşmeleri varsa Type1 koleksiyonu Type2 koleksiyona eşdeğer olarak değerlendirilir.  
  
 Genel olmayan koleksiyonları aynı verileri olarak kabul edilir sözleşme genel koleksiyonlar türü olarak `Object`. (Örneğin, için veri sözleşmeleri <xref:System.Collections.ArrayList> ve genel <xref:System.Collections.Generic.List%601> , `Object` aynıdır.)  
  
## <a name="using-collection-interface-types-and-read-only-collections"></a>Koleksiyon arabirimi türleri ve salt okunur koleksiyonları kullanma  
 Koleksiyon arabirimi türleri (<xref:System.Collections.IEnumerable>, <xref:System.Collections.IDictionary>genel <xref:System.Collections.Generic.IDictionary%602>, veya arabirimleri türetilmiş bu arabirimlerinden) koleksiyonu veri sözleşmeleri, gerçek koleksiyon türleri için koleksiyon veri sözleşmeleri eşdeğer sahip olarak kabul edilir. Bu nedenle, koleksiyon arabirimi türü olarak serileştirilen türünü bildirmesine mümkündür ve gerçek koleksiyon türü kullanılan sanki sonuçları aynıdır. Örneğin, aşağıdaki veri sözleşmeleri eşdeğerdir.  
  
 [!code-csharp[c_collection_types_in_data_contracts#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#1)]
 [!code-vb[c_collection_types_in_data_contracts#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#1)]  
  
 Bildirilen türü bir arabirim olduğunda seri hale getirme sırasında kullanılan gerçek örneği türü arabirimi uygulayan herhangi bir türü olabilir. Kısıtlamaları daha önce ele alınan (varsayılan bir oluşturucu sahip ve bir `Add` yöntemi) geçerli değildir. Örneğin, genel bir örneğine Customer2 içinde adresleri ayarlayabilirsiniz <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> doğrudan veri üyesi bildiremezsiniz olsa bile, adresini genel yazın <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>.  
  
 Arabirim türü olduğunda, serileştirme motoruna bildirilen arabirimini uygulayan bir türünü seçer ve türü örneği seri durumdan çıkarma sırasında. Bilinen türleri mekanizması (açıklanan [veri sözleşmesi bilinen türleri](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)) etkisizdir içinde türü seçimi burada; yerleşik [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="customizing-collection-types"></a>Koleksiyon türleri özelleştirme  
 Koleksiyon türleri kullanarak özelleştirebileceğiniz <xref:System.Runtime.Serialization.CollectionDataContractAttribute> birkaç kullanımı vardır özniteliği.  
  
 Genellikle bu öznitelik mümkün olduğunca uygulanmasını önlemek için önerilir, özelleştirme koleksiyon türleri güvenlik ihlalleri koleksiyonu interchangeability, unutmayın. Bu sorun hakkında daha fazla bilgi için bu konunun devamındaki "Toplama kuralları Gelişmiş" bölümüne bakın.  
  
### <a name="collection-data-contract-naming"></a>Koleksiyon veri sözleşmesi adlandırma  
 Koleksiyon türleri adlandırma kuralları bölümünde açıklandığı gibi normal veri sözleşme türleri, adlandırma benzerdir [veri sözleşmesi adları](../../../../docs/framework/wcf/feature-details/data-contract-names.md), önemli bazı farklar olsa da:  
  
-   <xref:System.Runtime.Serialization.CollectionDataContractAttribute> Yerine adını özelleştirmek için kullanılan öznitelik <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği. <xref:System.Runtime.Serialization.CollectionDataContractAttribute> Özniteliği de sahip `Name` ve `Namespace` özellikleri.  
  
-   Zaman <xref:System.Runtime.Serialization.CollectionDataContractAttribute> özniteliği uygulanmamış, varsayılan adı ve koleksiyon türleri için ad alanı adları ve ad alanları koleksiyonundaki türlerinin bağlıdır. Bunlar, koleksiyon türünün ad alanını ve ad etkilenmez. Örneğin, aşağıdaki türlerden bakın.  
  
    ```  
    public CustomerList1 : Collection<string> {}  
    public StringList1 : Collection<string> {}  
    ```  
  
 Her iki tür veri sözleşme adına "ArrayOfstring" ve değil "CustomerList1" veya "StringList1" dir. Bu, herhangi bir kök düzeyinde bu tür serileştirme XML aşağıdaki kodu benzer oluşturduğunda anlamına gelir.  
  
```xml  
<ArrayOfstring>  
    <string>...</string>  
    <string>...</string>  
    <string>...</string>  
    ...  
</ArrayOfstring>  
```  
  
 Bu adlandırma kuralı dizelerinin listesini gösteren özelleştirilmiş olmayan türü XML gösterimi ve aynı veri sözleşmesi olduğundan emin olmak için seçildi. Bu koleksiyon interchangeability mümkün kılar. Bu örnekte, CustomerList1 ve StringList1 tamamen birbirinin yerine kullanılabilir.  
  
 Ancak, ne zaman <xref:System.Runtime.Serialization.CollectionDataContractAttribute> özniteliği uygulanır, hiçbir özellik özniteliği ayarlanmış olsa bile, koleksiyon özelleştirilmiş koleksiyon veri sözleşmesi olur. Ad ve ad alanı koleksiyonu veri sözleşme ardından koleksiyon türü kendisi bağlıdır. Örneğin, aşağıdaki tür bakın.  
  
 [!code-csharp[c_collection_types_in_data_contracts#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#2)]
 [!code-vb[c_collection_types_in_data_contracts#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#2)]  
  
 Seri hale getirilmiş sonuç XML aşağıdakine benzer tutulduğunda.  
  
```xml  
<CustomerList2>  
    <string>...</string>  
    <string>...</string>  
    <string>...</string>  
    ...  
</CustomerList2>  
```  
  
 Bu artık özelleştirilmiş olmayan türleri XML gösterimini eşdeğer olduğuna dikkat edin.  
  
-   Kullanabileceğiniz `Name` ve `Namespace` daha da fazla özelliklerini özelleştirme adlandırma. Aşağıdaki sınıf bakın.  
  
     [!code-csharp[c_collection_types_in_data_contracts#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#3)]
     [!code-vb[c_collection_types_in_data_contracts#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#3)]  
  
 Sonuçta elde edilen XML aşağıdakine benzer.  
  
```xml  
<cust_list>  
    <string>...</string>  
    <string>...</string>  
    <string>...</string>  
    ...  
</cust_list>  
```  
  
 Daha fazla bilgi için bu konunun devamındaki "Toplama kuralları Gelişmiş" bölümüne bakın.  
  
### <a name="customizing-the-repeating-element-name-in-list-collections"></a>Yinelenen öğe adı listesi koleksiyonlarda özelleştirme  
 Liste koleksiyonları yinelenen girişler içerir. Normalde, her yinelenen giriş derlemesinde türü veri sözleşme adına göre adlı bir öğe olarak temsil edilir.  
  
 İçinde `CustomerList` örnekler, içerdiği koleksiyonları dizeleri. Yinelenen öğe şekilde dize ilkel tür için veri sözleşme adı "dize" olan "\<dize >".  
  
 Ancak, kullanarak <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> özellikte <xref:System.Runtime.Serialization.CollectionDataContractAttribute> özniteliği, bu yinelenen öğe adı özelleştirilebilir. Örneğin, aşağıdaki tür bakın.  
  
 [!code-csharp[c_collection_types_in_data_contracts#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#4)]
 [!code-vb[c_collection_types_in_data_contracts#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#4)]  
  
 Sonuçta elde edilen XML aşağıdakine benzer.  
  
```xml  
<CustomerList4>  
    <customer>...</customer>  
    <customer>...</customer>  
    <customer>...</customer>  
    ...  
</CustomerList4>  
```  
  
 Yinelenen öğe ad alanı her zaman kullanılarak özelleştirilebilir koleksiyon veri sözleşmesi ad alanı ile aynı olan `Namespace` özelliği, daha önce açıklandığı gibi.  
  
### <a name="customizing-dictionary-collections"></a>Sözlük koleksiyonları özelleştirme  
 Sözlük koleksiyonlarıdır temelde her girişin bir değer tarafından izlenen bir anahtar bulunduğu girişlerinin listeler. Yalnızca normal listeleriyle karşılık gelen öğe adı için yinelenen öğe kullanarak değiştirebileceğiniz gibi <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> özelliği.  
  
 Ayrıca, anahtarı ve değeri kullanarak temsil eden öğe adları değiştirebilirsiniz <xref:System.Runtime.Serialization.CollectionDataContractAttribute.KeyName%2A> ve <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ValueName%2A> özellikleri. Ad alanları bu öğeler için koleksiyon veri sözleşmesi ad alanı ile aynı olur.  
  
 Örneğin, aşağıdaki tür bakın.  
  
 [!code-csharp[c_collection_types_in_data_contracts#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#5)]
 [!code-vb[c_collection_types_in_data_contracts#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#5)]  
  
 Seri hale getirilmiş sonuç XML aşağıdakine benzer tutulduğunda.  
  
```xml  
<CountriesOrRegionsWithCapitals>  
    <entry>  
        <countryorregion>USA</countryorregion>  
        <capital>Washington</capital>  
    </entry>  
    <entry>  
        <countryorregion>France</countryorregion>  
        <capital>Paris</capital>  
    </entry>  
    ...  
</CountriesOrRegionsWithCapitals>  
```  
  
 Sözlük Koleksiyonlar hakkında daha fazla bilgi için bu konunun devamındaki "Toplama kuralları Gelişmiş" bölümüne bakın.  
  
## <a name="collections-and-known-types"></a>Koleksiyonlar ve bilinen türler  
 Diğer koleksiyonları veya koleksiyon arabirimleri yerine polymorphically kullanıldığında bilinen türleri koleksiyon türleri eklemeniz gerekmez. Örneğin, bir veri üyesi türü bildirirseniz <xref:System.Collections.IEnumerable> ve örneği göndermek için kullanmak <xref:System.Collections.ArrayList>, eklemek gerekmez <xref:System.Collections.ArrayList> bilinen türleri için.  
  
 Koleksiyon olmayan türleri yerine polymorphically koleksiyonları kullandığınızda, bilinen türleri eklenmelidir. Örneğin, bir veri üyesi türü bildirirseniz `Object` ve örneği göndermek için kullanmak <xref:System.Collections.ArrayList>, ekleme <xref:System.Collections.ArrayList> bilinen türleri için.  
  
 Bu, herhangi bir eşdeğer koleksiyonu polymorphically serileştirmek izin vermiyor. Örneğin, eklerseniz <xref:System.Collections.ArrayList> önceki örnekte bilinen türleri listesine bu atamanıza izin vermez `Array of Object` eşdeğer veri sözleşmesi olmasına rağmen sınıf. Bu seri hale getirme koleksiyon olmayan türleri için normal bilinen türleri davranışı öğesinden farklı değildir, ancak eşdeğer olarak koleksiyonlar için yaygın olduğu için söz konusu olduğunda koleksiyonları anlamak özellikle önemlidir.  
  
 Seri hale getirme sırasında verilen veri sözleşmesi için verilen tüm kapsam içinde yalnızca bir türü bilinen ve aynı veri sözleşmeleri sahip tüm eşdeğer koleksiyonların. Önceki örnekte, her ikisi de ekleyemezsiniz, yani <xref:System.Collections.ArrayList> ve `Array of Object` aynı kapsamda bilinen türleri için. Yeniden, bu koleksiyon olmayan türleri için bilinen türler davranışı eşdeğer olan, ancak koleksiyonlar için anlamak özellikle önemlidir.  
  
 Bilinen türler de koleksiyonları içeriği için gerekli olabilir. Örneğin, bir <xref:System.Collections.ArrayList> gerçekten örneklerini içeren `Type1` ve `Type2`, bu iki türü için bilinen türler eklenmelidir.  
  
 Aşağıdaki örnek, koleksiyonlar ve bilinen türleri kullanarak doğru şekilde oluşturulmuş bir grafiğinin gösterir. Gerçek bir uygulamada, aşağıdaki veri üye olarak tanımlarsınız normalde çünkü örnek biraz, contrived `Object`ve bu nedenle herhangi bir bilinen türü/çok biçimlilik sorun yoktur.  
  
 [!code-csharp[c_collection_types_in_data_contracts#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#6)]
 [!code-vb[c_collection_types_in_data_contracts#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#6)]  
  
 Bildirilen bir koleksiyon türü ise seri durumundan çıkarma işleminde gerçekten gönderilip gönderilmediğini türü ne olursa olsun türü örneği. Bildirilen koleksiyonu arabirimi ise, bilinen türler için hiçbir şekilde ile örneğinin oluşturulması için bir türü seri durumdan çıkarıcının seçer.  
  
 Ayrıca seri durumundan çıkarma işleminde türü koleksiyon türü değil, ancak bir koleksiyon türü gönderilen, eşleşen bir koleksiyon türü bilinen türleri listesi dışında çekilir. Koleksiyon arabirimi türleri seri durumdan çıkarma işleminde bilinen türleri listesine eklemek mümkündür. Bu durumda, seri durumdan çıkarma altyapısı yeniden örneğinin oluşturulması için türünü seçer.  
  
## <a name="collections-and-the-netdatacontractserializer-class"></a>Koleksiyonlar ve NetDataContractSerializer sınıfı  
 Zaman <xref:System.Runtime.Serialization.NetDataContractSerializer> sınıfı kullanılıyor, özelleştirilmiş koleksiyon türleri (olmadan <xref:System.Runtime.Serialization.CollectionDataContractAttribute> özniteliği) olan değil diziler kaybeder, kendi özel bir anlamı.  
  
 İle işaretli olmayan özelleştirilmiş koleksiyon türleri <xref:System.SerializableAttribute> özniteliği hala hale getirilebilir tarafından <xref:System.Runtime.Serialization.NetDataContractSerializer> göre sınıf <xref:System.SerializableAttribute> özniteliği veya <xref:System.Runtime.Serialization.ISerializable> arabirim kuralları.  
  
 Özelleştirilmiş koleksiyon türleri, koleksiyon arabirimleri ve diziler hala kabul edilir koleksiyon olarak ayarlansa bile <xref:System.Runtime.Serialization.NetDataContractSerializer> sınıfı kullanılıyor.  
  
## <a name="collections-and-schema"></a>Koleksiyonlar ve şema  
 Tüm eşdeğer koleksiyonları aynı gösterimi XML Şeması Tanım Dili (XSD) şemasında sahiptir. Bu nedenle, normalde aynı koleksiyon türü oluşturulan istemci kodu sunucuda olarak aldığınız değil. Örneğin, bir veri sözleşmesi ile genel sunucu kullanabilir <xref:System.Collections.Generic.List%601> tamsayı veri üyesi, ancak oluşturulan istemci kodu aynı veri üyesi dizisi duruma gelebilir.  
  
 Sözlük koleksiyonları ile işaretlenmiş bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-belirtmek belirli Şeması ek açıklama sözlükler oldukları; Aksi halde, bir anahtar ve değer girişleri basit listelerinden ayırt. Veri sözleşmesi şema içinde koleksiyonları nasıl temsil edildiğini bir tam açıklama için bkz: [veri sözleşmesi şema başvurusu](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).  
  
 Varsayılan olarak, özelleştirilmiş olmayan koleksiyonları içeri aktarılan kodda türleri oluşturulmaz. Veri üyeleri liste koleksiyon türleri dizileri olarak içe aktarılır ve sözlük koleksiyon türleri veri üyeleri genel bir sözlük aktarılır.  
  
 Ancak, özelleştirilmiş koleksiyonlar için ayrı türleri, işaretlenmiş oluşturulan <xref:System.Runtime.Serialization.CollectionDataContractAttribute> özniteliği. (Varsayılan ad alanı adı, yinelenen öğe adı veya anahtar/değer kullanmayan şemada özelleştirilmiş koleksiyon türü biridir öğe adları.) Bu tür genel türetilen boş türleridir <xref:System.Collections.Generic.List%601> liste türleri ve sözlük türleri için genel bir sözlük.  
  
 Örneğin, aşağıdaki türlerden sunucuda olabilir.  
  
 [!code-csharp[c_collection_types_in_data_contracts#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#7)]
 [!code-vb[c_collection_types_in_data_contracts#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#7)]  
  
 Ne zaman şemayı dışarı ve içeri aktarılan geri yeniden oluşturulan istemci kodu aşağıdakine benzer (Okuma Kolaylığı için özellikleri yerine alanları gösterilir).  
  
 [!code-csharp[c_collection_types_in_data_contracts#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#8)]
 [!code-vb[c_collection_types_in_data_contracts#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#8)]  
  
 Oluşturulan kod olanları varsayılandan farklı kullanmak isteyebilirsiniz. Örneğin, genel kullanmak isteyebilirsiniz <xref:System.ComponentModel.BindingList%601> normal diziler için kullanıcı arabirimi bileşenlerini bağlamak kolaylaştırmak, veri üyeleri için yerine.  
  
 İçine kullanmak istediğiniz koleksiyon türleri listesini oluşturmak için koleksiyon türleri seçin geçmesini <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A> özelliği <xref:System.Runtime.Serialization.ImportOptions> şema içe aktarma sırasında nesne. Bu tür adlı *koleksiyon türleri başvurulan*.  
  
 Genel türler başvurulan olduğunda ya da tam olarak açık genel türler veya genel türler tamamen kapalı olmaları gerekir.  
  
> [!NOTE]
>  Svcutil.exe aracını kullanırken, bu başvuru kullanılarak gerçekleştirilebilir **/collectionType** komut satırı anahtarını (kısa form: **/ct**). Derleme kullanarak başvurulan koleksiyon türleri için de belirtmeniz gerekir göz önünde bulundurmanız **/reference** geçiş (kısa form: **/r**). Tür genel ise, geri teklif ve genel parametre sayısı tarafından izlenmesi gerekir. Geri (') tek tırnak işareti (') karakteri ile karıştırılmamalıdır tekliftir. Kullanarak birden çok başvurulan koleksiyon türleri belirtebilirsiniz **/collectionType** birden çok kez geçin.  
  
 Örneğin, genel içeri aktarılacak tüm listeleri neden <xref:System.Collections.Generic.List%601>.  
  
```  
svcutil.exe MyService.wsdl MyServiceSchema.xsd /r:C:\full_path_to_system_dll\System.dll /ct:System.Collections.Generic.List`1  
```  
  
 Başvurulan koleksiyon türleri bu listesi herhangi bir koleksiyonu içeri aktarırken taranır ve en iyi eşleşen koleksiyon, bir veri türü (özelleştirilmiş olmayan koleksiyonları için) veya (özelleştirilmiş koleksiyonları için) türetilen bir taban türü olarak bulunması durumunda kullanılır. Listeleri listeleri karşı eşleştirilir sırada sözlükler yalnızca sözlükler karşı eşleştirilir.  
  
 Örneğin, genel eklerseniz <xref:System.ComponentModel.BindingList%601> ve <xref:System.Collections.Hashtable> başvurulan türleri listesi için önceki örnekte oluşturulan istemci kodunu aşağıdakine benzer.  
  
 [!code-csharp[c_collection_types_in_data_contracts#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#9)]
 [!code-vb[c_collection_types_in_data_contracts#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#9)]  
  
 Koleksiyon arabirimi türleri, başvurulan koleksiyon türleri bir parçası olarak belirtebilirsiniz, ancak geçersiz koleksiyon türleri belirtilemez (olanları hiçbir gibi `Add` yöntemi veya ortak oluşturucu).  
  
 Kapalı bir genel en iyi eşleşme olarak değerlendirilir. (Olmayan genel türleri olarak kabul edilir kapalı genel türler için eşdeğer `Object`). Örneğin, genel türleri <xref:System.Collections.Generic.List%601> , <xref:System.DateTime>genel <xref:System.ComponentModel.BindingList%601> (açık genel), ve <xref:System.Collections.ArrayList> olan aşağıdaki başvurulan koleksiyon türleri oluşturulur.  
  
 [!code-csharp[c_collection_types_in_data_contracts#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#10)]
 [!code-vb[c_collection_types_in_data_contracts#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#10)]  
  
 Liste koleksiyonlar için aşağıdaki tabloda yalnızca durumlarda desteklenir.  
  
|Başvurulan türü|Başvurulan türü tarafından uygulanan arabirimi|Örnek|Tür kabul edilir:|  
|---------------------|----------------------------------------------|-------------|----------------------|  
|Genel olmayan ya da kapalı genel (parametreleri herhangi sayısı)|Non-genel|`MyType : IList`<br /><br /> veya<br /><br /> `MyType<T> : IList`<br /><br /> Burada T = `int`|Genel olarak kapalı `Object` (örneğin, `IList<object>`)|  
|Genel olmayan ya da kapalı genel (mutlaka koleksiyon türü ile eşleşmiyor parametre herhangi sayısı)|Genel kapalı|`MyType : IList<string>`<br /><br /> veya<br /><br /> `MyType<T> : IList<string>` Burada T =`int`|Kapalı genel (örneğin, `IList<string>`)|  
|Herhangi bir sayıda parametreyle genel kapalı|Açık genel tür parametreleri herhangi birini kullanarak|`MyType<T,U,V> : IList<U>`<br /><br /> Burada T =`int`, U =`string`, V =`bool`|Kapalı genel (örneğin, `IList<string>`)|  
|Açık genel bir parametre ile|Açık genel tür parametresi kullanılarak|`MyType<T> : IList<T>`, T, açık|Açık genel (örneğin, `IList<T>`)|  
  
 Bir türü birden fazla liste koleksiyonu arabirimini uygulayan durumunda aşağıdaki kısıtlamalar geçerlidir:  
  
-   Genel tür uyguluyorsa <xref:System.Collections.Generic.IEnumerable%601> (veya türetilmiş arabirimlerinden) türü birden çok kez farklı türleri için geçerli başvurulan koleksiyon türü olarak kabul edilmez ve yok sayılır. Bazı uygulamaları geçersiz veya açık genel türler kullanın olsa bile bu geçerlidir. Örneğin, genel uygulayan bir tür <xref:System.Collections.Generic.IEnumerable%601> , `int` ve genel <xref:System.Collections.Generic.IEnumerable%601> T hiçbir zaman başvurulan koleksiyonu olarak kullanılacak `int` veya türü olup bağımsız olarak herhangi bir türü, bir `Add` kabul yöntemi `int` veya bir `Add` T ya da her ikisini de parametre olarak kabul yöntemi yazın.  
  
-   Türü bir genel koleksiyon arabirimi uyguluyorsa yanı <xref:System.Collections.IList>, genel koleksiyon arabirim türünün kapalı bir genel olmadıkça türü hiçbir zaman başvurulan koleksiyon türü olarak kullanılan <xref:System.Object>.  
  
 Sözlük koleksiyonlar için aşağıdaki tabloda yalnızca durumlarda desteklenir.  
  
|Başvurulan türü|Başvurulan türü tarafından uygulanan arabirimi|Örnek|Kabul türü|  
|---------------------|----------------------------------------------|-------------|---------------------|  
|Genel olmayan ya da kapalı genel (parametreleri herhangi sayısı)|<xref:System.Collections.IDictionary>|`MyType : IDictionary`<br /><br /> veya<br /><br /> `MyType<T> : IDictionary` Burada T =`int`|Genel kapalı `IDictionary<object,object>`|  
|Kapalı genel (parametreleri herhangi sayısı)|<xref:System.Collections.Generic.IDictionary%602>, kapalı|`MyType<T> : IDictionary<string, bool>` Burada T =`int`|Kapalı genel (örneğin, `IDIctionary<string,bool>`)|  
|Kapalı genel (parametreleri herhangi sayısı)|Genel <xref:System.Collections.Generic.IDictionary%602>, bir anahtar veya değer kapalı, diğer açık olduğundan ve tür parametrelerden birini kullanır|`MyType<T,U,V> : IDictionary<string,V>` Burada T =`int`, U =`float`, V =`bool`<br /><br /> veya<br /><br /> `MyType<Z> : IDictionary<Z,bool>` Burada Z =`string`|Kapalı genel (örneğin, `IDictionary<string,bool>`)|  
|Kapalı genel (parametreleri herhangi sayısı)|Genel <xref:System.Collections.Generic.IDictionary%602>, anahtar ve değer açık ve her tür parametrelerden birini kullanır|`MyType<T,U,V> : IDictionary<V,U>` Burada T =`int`, U =`bool`, V =`string`|Kapalı genel (örneğin, `IDictionary<string,bool>`)|  
|Açık genel (iki parametre)|Genel <xref:System.Collections.Generic.IDictionary%602>, açın, her iki tür genel parametreler göründükleri sırada kullanır|`MyType<K,V> : IDictionary<K,V>`, K ve V hem açın|Açık genel (örneğin, `IDictionary<K,V>`)|  
  
 Türü hem de uyguluyorsa <xref:System.Collections.IDictionary> ve genel <xref:System.Collections.Generic.IDictionary%602>, yalnızca genel <xref:System.Collections.Generic.IDictionary%602> olarak kabul edilir.  
  
 Kısmi genel türlerine başvurma desteklenmiyor.  
  
 Çoğaltmaları izin verilmez, örneğin, her iki genel ekleyemezsiniz <xref:System.Collections.Generic.List%601> , `Integer` ve genel koleksiyonunu `Integer` için <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A>, bu hangi tamsayı listesi yapılırken kullanılacak bulunması belirlemek mümkün kılar şemada. Yalnızca yinelenen sorun gösteren şemada bir türü varsa yinelenenleri algılanır. Alınan şema tamsayılar listesi içermiyorsa, örneğin, bu iki genel sağlamak için izin <xref:System.Collections.Generic.List%601> , `Integer` ve genel koleksiyonunu `Integer` içinde <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A>, ancak, herhangi bir etkisi olmaz.  
  
## <a name="advanced-collection-rules"></a>Gelişmiş toplama kuralları  
  
### <a name="serializing-collections"></a>Seri hale getirilmesi  
 Serileştirme için toplama kuralları listesi verilmiştir:  
  
-   Koleksiyon türleri (koleksiyonların koleksiyon sahip) birleştirerek izin verilir. Basit diziler koleksiyonların koleksiyon olarak kabul edilir. Çok boyutlu diziler desteklenmiyor.  
  
-   Bayt ve dizilerin dizilerini <xref:System.Xml.XmlNode> değil koleksiyonları temel olarak davranılır özel dizi türleridir. Her bayt için ayrı bir öğe yerine Base64 olarak kodlanmış veri yığınını içeren tek bir XML öğesi sonuçlarında bayt dizisi seri hale getirme. Hakkında daha fazla bilgi için bir dizi <xref:System.Xml.XmlNode> olduğu kabul edilir, bkz: [XML ve ADO.NET türleri veri sözleşmelerinde](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md). Elbette, bu özel türleri kendilerini koleksiyonlarda katılabilir: bir dizi içeren her veri Base64 ile kodlanmış bir Öbek ile birden çok XML öğeleri sonuçlarında bayt dizisi.  
  
-   Varsa <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği bir koleksiyon türü uygulanır, türü normal veri sözleşmesi türü, bir koleksiyon olarak değil olarak kabul edilir.  
  
-   Koleksiyon türü uyguluyorsa <xref:System.Xml.Serialization.IXmlSerializable> arabirimi, aşağıdaki kurallar geçerlidir, verilen bir türdeki `myType:IList<string>, IXmlSerializable`:  
  
    -   Bildirilen türü ise `IList<string>`, türü bir liste olarak seri.  
  
    -   Bildirilen türü ise `myType`, olarak serileştirilmiş `IXmlSerializable`.  
  
    -   Bildirilen türü ise `IXmlSerializable`, olarak serileştirilmiş `IXmlSerializable`, ancak yalnızca eklerseniz `myType` bilinen türleri listesi.  
  
-   Koleksiyonlar, serileştirilen ve aşağıdaki tabloda gösterilen yöntem kullanılarak seri durumdan.  
  
|Koleksiyon türü uygular|Yöntem serileştirme üzerinde çağrılır|Seri durumundan çıkarma işleminde adlı yöntemleri|  
|--------------------------------|-----------------------------------------|-------------------------------------------|  
|Genel <xref:System.Collections.Generic.IDictionary%602>|`get_Keys`, `get_Values`|Genel ekleme|  
|<xref:System.Collections.IDictionary>|`get_Keys`, `get_Values`|`Add`|  
|Genel <xref:System.Collections.Generic.IList%601>|Genel <xref:System.Collections.Generic.IList%601> dizin oluşturucu|Genel ekleme|  
|Genel <xref:System.Collections.Generic.ICollection%601>|Numaralandırıcı|Genel ekleme|  
|<xref:System.Collections.IList>|<xref:System.Collections.IList> Dizin Oluşturucu|`Add`|  
|Genel <xref:System.Collections.Generic.IEnumerable%601>|`GetEnumerator`|Statik olmayan yöntemi `Add` (genel parametre türü) veya temel türlerinden biri uygun türde bir parametre alır. Bu tür bir yöntem bir koleksiyon türü seri hale getirme ve seri durumdan çıkarma sırasında bir koleksiyon olarak işlemek seri hale getirici için mevcut olması gerekir.|  
|<xref:System.Collections.IEnumerable> (ve bu nedenle <xref:System.Collections.ICollection>, ondan türetilen)|`GetEnumerator`|Statik olmayan yöntemi `Add` türünde bir parametre alan `Object`. Bu tür bir yöntem bir koleksiyon türü seri hale getirme ve seri durumdan çıkarma sırasında bir koleksiyon olarak işlemek seri hale getirici için mevcut olması gerekir.|  
  
 Önceki tabloda azalan sırada öncelik koleksiyon arabirimleri listeler. Bir türü hem de uyguluyorsa, örneğin, yani <xref:System.Collections.IList> ve genel <xref:System.Collections.Generic.IEnumerable%601>, koleksiyon serileştirilmiş ve göre seri <xref:System.Collections.IList> kuralları:  
  
-   Seri durumdan çıkarma sırasında tüm koleksiyonlar ilk türünün bir örneği için bir koleksiyon türü seri hale getirme ve seri durumdan çıkarma sırasında bir koleksiyon olarak işlemek seri hale getirici mevcut olmalıdır varsayılan oluşturucu çağırarak oluşturarak serisi.  
  
-   Aynı genel koleksiyon arabirimi birden çok kez uygulanmışsa (örneğin, bir tür hem genel uyguluyorsa <xref:System.Collections.Generic.ICollection%601> , `Integer` ve genel <xref:System.Collections.Generic.ICollection%601> , <xref:System.String>) ve daha yüksek önceliği arabirim bulundu, koleksiyonu Geçerli bir koleksiyon olarak kabul değil.  
  
-   Koleksiyon türleri olabilir <xref:System.SerializableAttribute> özniteliği uygulanmış ve uygulayabilirsiniz <xref:System.Runtime.Serialization.ISerializable> arabirimi. Bunların her ikisi de göz ardı edilir. Ancak, türü tam olarak koleksiyon türü gereksinimlerini karşılamıyor varsa (örneğin, `Add` yöntemi eksik), türü bir koleksiyon türü olarak kabul edilmez ve bu nedenle <xref:System.SerializableAttribute> özniteliği ve <xref:System.Runtime.Serialization.ISerializable> arabirimi belirlemek için kullanılır türü seri hale getirilebilir.  
  
-   Uygulama <xref:System.Runtime.Serialization.CollectionDataContractAttribute> özniteliği kaldırır özelleştirmek için bir koleksiyona <xref:System.SerializableAttribute> geri dönüş mekanizması önceki. Bunun yerine, özelleştirilmiş bir koleksiyon değil karşılayan koleksiyonu gereksinimleri çalışamazsa mu bir <xref:System.Runtime.Serialization.InvalidDataContractException> özel durumu oluşur. Özel durum dizesi genellikle neden belirli bir türde geçerli bir koleksiyon olarak kabul edilmez açıklayan bilgi içerir (hiçbir `Add` yöntemi, varsayılan oluşturucu yok vb.), genellikle uygulamak yararlı olacak şekilde <xref:System.Runtime.Serialization.CollectionDataContractAttribute> hata ayıklama amacıyla özniteliği.  
  
### <a name="collection-naming"></a>Koleksiyon adlandırma  
 Koleksiyon adlandırma kurallarının bir listesi verilmiştir:  
  
-   İlkel türler içeren liste koleksiyonu veri sözleşmeleri yanı sıra, tüm sözlük koleksiyonu veri sözleşmeleri için varsayılan ad alanı http://schemas.microsoft.com/2003/10/Serialization/Arrays Namespace kullanılarak geçersiz kılınmadığı sürece. Yerleşik XSD türlerine eşlenir türleri yanı `char`, `Timespan`, ve `Guid` türleri, bu amaçla temelleri değerlendirilir.  
  
-   Namespace, kullanarak kılınmadığı sürece, olmayan ilkel türler içeren koleksiyon türleri için varsayılan ad alanını veri sözleşmesi türünün ad alanını derlemesinde ile aynıdır.  
  
-   Liste koleksiyonu veri sözleşmeleri için varsayılan adı adını kullanarak geçersiz kılınmadığı sürece derlemesinde türü veri sözleşme adı "ArrayOf" birlikte dizedir. Örneğin, veri sözleşmesi genel olarak tamsayılar listesi "ArrayOfint" adıdır. Adını veri sözleşmesi göz önünde bulundurmanız `Object` genel olmayan listeleri veri sözleşmesi adını ister "anyType" olduğundan <xref:System.Collections.ArrayList> "ArrayOfanyType" değil.  
  
 Sözlük koleksiyonu veriler için varsayılan ad sözleşmeler, kullanarak geçersiz kılınmadığı sürece `Name`, "ArrayOfKeyValueOf" birleştirilmiş değer türü veri sözleşmesi adını yazarak ve ardından anahtar türü veri sözleşme adı dizesi. Örneğin, veri sözleşmesi adı bir dize genel bir sözlük ve tamsayı olan "ArrayOfKeyValueOfstringint". Ayrıca, anahtar veya değer türleri ilkel türler emin değilseniz, anahtar ve değer türleri veri sözleşmesi ad alanları bir ad alanı karma ada eklenir. Ad alanı karmaları hakkında daha fazla bilgi için bkz: [veri sözleşmesi adları](../../../../docs/framework/wcf/feature-details/data-contract-names.md).  
  
 Her sözlük koleksiyon veri sözleşmesi sözlükteki bir girişini temsil eden bir yardımcı veri sözleşmesi sahiptir. Adı "ArrayOf" öneki dışında sözlük veri sözleşmesi ile aynıdır ve kendi ad sözlük veri sözleşmesi ile aynıdır. Örneğin, "ArrayOfKeyValueOfstringint" sözlük veri sözleşmesi için bir giriş sözlükteki "KeyValueofstringint" veri sözleşmesi temsil eder. Bu veri sözleşmesi adını kullanarak özelleştirebileceğiniz `ItemName` sonraki bölümde açıklandığı gibi özelliği.  
  
 Genel tür adlandırma kuralları bölümünde açıklandığı gibi [veri sözleşmesi adları](../../../../docs/framework/wcf/feature-details/data-contract-names.md)olan koleksiyon türleri için; tam olarak uygulamak, ad içinde süslü ayraçlar genel tür parametreleri belirtmek için kullanabilirsiniz. Ancak, küme ayraçları içinde numaraları genel parametreler ve koleksiyonundaki türleri bakın.  
  
## <a name="collection-customization"></a>Koleksiyon özelleştirme  
 Aşağıdaki kullanır <xref:System.Runtime.Serialization.CollectionDataContractAttribute> özniteliği yasaklanmış olduğuna ve neden bir <xref:System.Runtime.Serialization.InvalidDataContractException> özel durum:  
  
-   Uygulama <xref:System.Runtime.Serialization.DataContractAttribute> bir türün özniteliği <xref:System.Runtime.Serialization.CollectionDataContractAttribute> özniteliği uygulanan, veya türetilmiş türlerinden biri için açıldı.  
  
-   Uygulama <xref:System.Runtime.Serialization.CollectionDataContractAttribute> özniteliği uygulayan bir tür <xref:System.Xml.Serialization.IXmlSerializable> arabirimi.  
  
-   Uygulama <xref:System.Runtime.Serialization.CollectionDataContractAttribute> özniteliği bir koleksiyon olmayan tür.  
  
-   Ayarlama girişimi <xref:System.Runtime.Serialization.CollectionDataContractAttribute.KeyName%2A> veya <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ValueName%2A> üzerinde bir <xref:System.Runtime.Serialization.CollectionDataContractAttribute> özniteliği için bir sözlük olmayan türü uygulanmıştır.  
  
### <a name="polymorphism-rules"></a>Çok biçimlilik kuralları  
 Daha önce belirtildiği, koleksiyonlar kullanarak özelleştirme <xref:System.Runtime.Serialization.CollectionDataContractAttribute> öznitelik koleksiyonu interchangeability ile engel. İki özelleştirilmiş koleksiyon türleri yalnızca kendi ad, ad alanı, öğe adı yanı sıra (bunlar sözlük koleksiyonları varsa) anahtar ve değer adlarını eşleşiyorsa eşdeğer kabul edilebilir.  
  
 Özelleştirmeler nedeniyle, başka bir beklenirken yanlışlıkla kullanımı bir koleksiyon veri sözleşmesi için mümkündür. Bu kaçınılmalıdır. Aşağıdaki türleri bölümüne bakın.  
  
 [!code-csharp[c_collection_types_in_data_contracts#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#11)]
 [!code-vb[c_collection_types_in_data_contracts#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#11)]  
  
 Bu durumda örneğindeki `Marks1` atanabilir `testMarks`. Ancak, `Marks2` veri sözleşmesi eşdeğer olarak kabul edilmez çünkü kullanılmamalıdır `IList<int>` veri sözleşme. Veri sözleşmesi adı "Marks2" değil "ArrayOfint" ise ve yinelenen öğe adı "\<işaretlemek >" ve "\<int >".  
  
 Aşağıdaki tabloda kurallar koleksiyonları biçimli atama için geçerlidir.  
  
|Bildirilen türü|Özelleştirilmiş olmayan bir toplama atama|Özelleştirilmiş bir koleksiyon atama|  
|-------------------|--------------------------------------------|---------------------------------------|  
|Nesne|Sözleşme adı serileştirilir.|Sözleşme adı serileştirilir.<br /><br /> Özelleştirme kullanılır.|  
|Koleksiyon arabirimi|Sözleşme adı serileştirilmemiş.|Sözleşme adı serileştirilmemiş.<br /><br /> Özelleştirme used.* değil|  
|Koleksiyon olmayan özelleştirilmiş|Sözleşme adı serileştirilmemiş.|Sözleşme adı serileştirilir.<br /><br /> Özelleştirme used.* * bulunur|  
|Özelleştirilmiş koleksiyonu|Sözleşme adı serileştirilir. Özelleştirme used.* * değil|Sözleşme adı serileştirilir.<br /><br /> Atanan türü özelleştirme used.* * bulunur|  
  
 * İle <xref:System.Runtime.Serialization.NetDataContractSerializer> sınıfı, özelleştirme, bu durumda kullanılır. <xref:System.Runtime.Serialization.NetDataContractSerializer> Sınıfı ayrıca serileştiren gerçek tür adı bu durumda, bu nedenle beklendiği gibi çalıştığını seri durumundan çıkarma.  
  
 ** Bu gibi durumlarda şema geçersiz durumlarda neden ve bu nedenle kaçınılmalıdır.  
  
 Sözleşme adı burada seri durumda atanan koleksiyon türü bilinen türleri listesinde olmalıdır. Bunun tersi de geçerlidir: Burada adı sıralanmış değildir durumlarda türü bilinen türleri listesine ekleme gerekli değildir.  
  
 Bir dizi türetilmiş bir tür için bir taban türü dizisi atanabilir. Bu durumda, türetilmiş bir tür sözleşme adı yinelenen her öğe için serileştirilir. Örneğin, bir tür değilse `Book` türünden `LibraryItem`, bir dizi atayabilirsiniz `Book` dizisi olarak `LibraryItem`. Bu diğer koleksiyon türleri için geçerli değildir. Örneğin, atayamazsınız bir `Generic List of Book` için bir `Generic List of LibraryItem`. Ancak, atamak için bir `Generic List of LibraryItem` içeren `Book` örnekleri. Dizi ve dizi olmayan durumda `Book` bilinen türleri listesinde olmalıdır.  
  
## <a name="collections-and-object-reference-preservation"></a>Koleksiyonlar ve nesne başvurusu koruma  
 Seri hale getirici işlevleri, burada nesne başvuruları korur modunda nesne başvurusu korunması koleksiyonlar için de geçerlidir. Özellikle, nesne kimliği, tüm koleksiyonlar ve koleksiyonlarında bulunan bireysel öğeleri korunur. Sözlük için nesne kimliği hem de anahtar/değer çifti nesneleri ve ayrı anahtar ve değer nesneleri korunur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.Serialization.CollectionDataContractAttribute>
