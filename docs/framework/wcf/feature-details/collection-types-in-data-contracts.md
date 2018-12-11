---
title: Veri Sözleşmelerinde Koleksiyon Türleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- collection types [WCF], data contracts
- data contracts [WCF], collection types
- collection types [WCF]
ms.assetid: 9b45b28e-0a82-4ea3-8c33-ec0094aff9d5
ms.openlocfilehash: 0399c89e926611b076072e6475c52bf31ae83637
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53155190"
---
# <a name="collection-types-in-data-contracts"></a>Veri Sözleşmelerinde Koleksiyon Türleri
A *koleksiyon* , belirli bir türdeki öğelerin listesidir. İçinde [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], böyle listeleri diziler veya çeşitli diğer türleri kullanarak temsil edilebilen (genel liste, genel <xref:System.ComponentModel.BindingList%601>, <xref:System.Collections.Specialized.StringCollection>, veya <xref:System.Collections.ArrayList>). Örneğin, bir koleksiyon için belirli bir müşteri adresleri listesi tutabilir. Bu koleksiyonlara adlı *liste koleksiyonları*kendi gerçek türü ne olursa olsun.  
  
 Koleksiyonun özel bir formu temsil eden bir öğe ("anahtarını") ve başka bir ("value") arasında bir ilişki var. İçinde [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], bunlar gibi türlerine göre gösterilir <xref:System.Collections.Hashtable> ve genel bir sözlük. Örneğin, bir ilişki koleksiyonu yıllarındaki nüfusu ("value") bir şehir ("anahtarı") eşlenebilir. Bu koleksiyonlara adlı *sözlük koleksiyon*kendi gerçek türü ne olursa olsun.  
  
 Koleksiyonlar, özel olarak değerlendirilmesi veri sözleşme modelinde alırsınız.  
  
 Türleri uygulayan <xref:System.Collections.IEnumerable> arabirimi, diziler ve genel koleksiyonlar gibi koleksiyon olarak tanınıyor. Bu uygulayan türleri <xref:System.Collections.IDictionary> veya genel <xref:System.Collections.Generic.IDictionary%602> arabirimleri sözlük koleksiyon; diğer tüm liste koleksiyonlarıdır.  
  
 Koleksiyon türleri'adında bir yöntem olması gibi ek gereksinimleri `Add` ve varsayılan bir oluşturucu aşağıdaki bölümlerde ayrıntılı olarak ele alınmıştır. Bu koleksiyon türleri hem seri durumdan ve sağlar. Bazı koleksiyonlar doğrudan, genel gibi desteklenmeyen, yani <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> (hiçbir varsayılan oluşturucu olduğundan). Ancak, bu kısıtlamalar atlanarak hakkında daha fazla bilgi için bu konunun ilerleyen bölümlerindeki "Kullanarak koleksiyon arabirim türleri ve salt okunur koleksiyonları" bölümüne bakın.  
  
 Koleksiyonları'nda yer alan tür veri anlaşması türleri veya aksi halde seri hale getirilebilir olması gerekir. Daha fazla bilgi için [veri sözleşme seri hale getirici tarafından desteklenen türleri](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md).  
  
 Nedir ve ne geçerli bir koleksiyon olarak kabul edilmez yanı sıra koleksiyonlar nasıl serileştirilir hakkında daha fazla bilgi için bu konunun "Gelişmiş toplama kuralları" bölümünde serileştirmek Koleksiyonlar hakkında bilgi.  
  
## <a name="interchangeable-collections"></a>Birbirinin yerine koleksiyonları  
 Aynı türdeki tüm liste koleksiyonları aynı verilere sahip olduğu kabul edilir anlaşması (kullanarak özelleştirilir sürece <xref:System.Runtime.Serialization.CollectionDataContractAttribute> özniteliği, bu konunun ilerleyen kısımlarında açıklandığı gibi). Bu nedenle, örneğin, aşağıdaki veri sözleşmeleri eşdeğerdir.  
  
 [!code-csharp[c_collection_types_in_data_contracts#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#0)]
 [!code-vb[c_collection_types_in_data_contracts#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#0)]  
  
 XML şu kod gibi her iki veri sözleşmeleri sonuçlanır.  
  
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
  
 Koleksiyon interchangeability kullanmanızı, örneğin, sunucu üzerindeki performans için iyileştirilmiş bir koleksiyon türü ve kullanıcı arabirimi bileşenlerine istemcide bağlanması için tasarlanmış bir koleksiyon türü sağlar.  
  
 Benzer şekilde liste koleksiyonları, aynı anahtar ve değer türlerine sahip tüm sözlük koleksiyon aynı verilere sahip olduğu kabul edilir anlaşması (tarafından özelleştirmediyseniz <xref:System.Runtime.Serialization.CollectionDataContractAttribute> özniteliği).  
  
 Yalnızca veri anlaşması türü koleksiyonu denklik ilgili olarak çok önemlidir, .NET türleri değil. Diğer bir deyişle, type1 ve Type2 eşdeğeri veri sözleşmeleri varsa Type1 koleksiyonunu Type2 koleksiyonu için eşdeğer olarak değerlendirilir.  
  
 Genel olmayan koleksiyon kabul edilir aynı veri türünde genel koleksiyonlar anlaşmaya `Object`. (Örneğin, için veri sözleşmeleri <xref:System.Collections.ArrayList> ve genel <xref:System.Collections.Generic.List%601> , `Object` aynıdır.)  
  
## <a name="using-collection-interface-types-and-read-only-collections"></a>Koleksiyon arabirim türleri ve salt okunur koleksiyonları kullanma  
 Koleksiyon arabirim türleri (<xref:System.Collections.IEnumerable>, <xref:System.Collections.IDictionary>genel <xref:System.Collections.Generic.IDictionary%602>, veya arabirimleri bu arabirimden türetilmiş) koleksiyon veri sözleşmeleri, gerçek koleksiyon türleri için koleksiyon veri sözleşmeleri eşdeğer sahip olarak kabul edilir. Bu nedenle, bir koleksiyon arabirim türü olarak serileştirilmekte olan türün bildirmek mümkündür ve bir gerçek koleksiyon türü kullanmışsınız gibi sonuçları aynı olan. Örneğin, aşağıdaki veri sözleşmeleri eşdeğerdir.  
  
 [!code-csharp[c_collection_types_in_data_contracts#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#1)]
 [!code-vb[c_collection_types_in_data_contracts#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#1)]  
  
 Bildirilen türü bir arabirim olduğunda serileştirme sırasında kullanılan gerçek örnek türü arabirimi uygulayan herhangi bir tür olabilir. Daha önce bahsedilen kısıtlamaları (varsayılan bir oluşturucuya sahip ve bir `Add` yöntemi) geçerli değildir. Örneğin, genel örneğine Customer2 içinde adresleri ayarlayabilirsiniz <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> doğrudan veri üyesi bildiremezsiniz olsa bile, adresi, genel tür <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>.  
  
 Seri durumundan çıkarma sırasında bildirilen türü bir arabirim, bildirilen arabirimi uygulayan bir tür serileştirme motoruna seçer ve tür örneği. Bilinen türleri mekanizması (açıklanan [veri sözleşme bilinen türleri](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)) hiçbir etkisi burada; türü seçimi WCF içinde yerleşik olarak bulunur.  
  
## <a name="customizing-collection-types"></a>Koleksiyon türlerini özelleştirme  
 Koleksiyon türleri kullanarak özelleştirebileceğiniz <xref:System.Runtime.Serialization.CollectionDataContractAttribute> özniteliği birden çok kullanımı vardır.  
  
 Genellikle bu öznitelik, mümkün olduğunda uygulanmasını önlemek için önerilir, böylece bu özelleştirme koleksiyon türlerini anladığınızda koleksiyonu interchangeability, unutmayın. Bu sorun hakkında daha fazla bilgi için "Gelişmiş toplama kuralları" bölümünde bu konunun ilerleyen bölümlerinde bkz.  
  
### <a name="collection-data-contract-naming"></a>Koleksiyon veri anlaşması adlandırma  
 Koleksiyon türleri adlandırma kuralları bölümünde anlatıldığı gibi normal veri anlaşması türleri adlandırma benzerdir [veri sözleşmesi adları](../../../../docs/framework/wcf/feature-details/data-contract-names.md), ancak bazı önemli farklar vardır:  
  
-   <xref:System.Runtime.Serialization.CollectionDataContractAttribute> Öznitelik adı yerine özelleştirmek için kullanılan <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği. <xref:System.Runtime.Serialization.CollectionDataContractAttribute> Da özniteliğine sahip `Name` ve `Namespace` özellikleri.  
  
-   Zaman <xref:System.Runtime.Serialization.CollectionDataContractAttribute> öznitelik uygulanmadı, adları ve ad alanları koleksiyon içinde yer alan türlerinin varsayılan adını ve koleksiyon türleri için ad alanı bağlıdır. Bunlar, koleksiyon türünün ad alanını ve ad etkilenmez. Örneğin, aşağıdaki türleri bakın.  
  
    ```csharp  
    public CustomerList1 : Collection<string> {}  
    public StringList1 : Collection<string> {}  
    ```  
  
 Her iki türü veri anlaşması adına "ArrayOfstring" ve değil "CustomerList1" veya "StringList1" dir. Başka bir deyişle, herhangi bir kök düzeyinde bu tür serileştirme XML aşağıdaki koda benzer verir.  
  
```xml  
<ArrayOfstring>  
    <string>...</string>  
    <string>...</string>  
    <string>...</string>  
    ...  
</ArrayOfstring>  
```  
  
 Bu adlandırma kuralı temsil eden bir dize listesi özelleştirilmemiş türü aynı veri anlaşması ve XML gösterimi olduğundan emin olmak için seçilmiştir. Bu koleksiyon interchangeability mümkün kılar. Bu örnekte, CustomerList1 ve StringList1 tamamen birbirinin yerine kullanılabilir.  
  
 Ancak, <xref:System.Runtime.Serialization.CollectionDataContractAttribute> özniteliği uygulanır, hiçbir özellik özniteliği ayarlanmış olsa bile, koleksiyon özelleştirilmiş koleksiyon veri anlaşması olur. Koleksiyon verisi ad alanı ve ad sözleşme ardından koleksiyon türüne kendisini bağlıdır. Örneğin, şu tür bakın.  
  
 [!code-csharp[c_collection_types_in_data_contracts#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#2)]
 [!code-vb[c_collection_types_in_data_contracts#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#2)]  
  
 Serileştirilmiş olduğunda, elde edilen XML aşağıdakine benzer.  
  
```xml  
<CustomerList2>  
    <string>...</string>  
    <string>...</string>  
    <string>...</string>  
    ...  
</CustomerList2>  
```  
  
 Bu artık özelleştirilmemiş türleri XML gösterimi denk olduğuna dikkat edin.  
  
-   Kullanabileceğiniz `Name` ve `Namespace` daha da özellikleri özelleştirmek adlandırma. Aşağıdaki sınıf konusuna bakın.  
  
     [!code-csharp[c_collection_types_in_data_contracts#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#3)]
     [!code-vb[c_collection_types_in_data_contracts#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#3)]  
  
 Elde edilen XML aşağıdakine benzer.  
  
```xml  
<cust_list>  
    <string>...</string>  
    <string>...</string>  
    <string>...</string>  
    ...  
</cust_list>  
```  
  
 Daha fazla bilgi için bu konunun ilerleyen bölümlerindeki "Gelişmiş toplama kuralları" bölümüne bakın.  
  
### <a name="customizing-the-repeating-element-name-in-list-collections"></a>Yinelenen öğe adı liste koleksiyonları özelleştirme  
 Liste koleksiyonları yinelenen girişler içeriyor. Normalde, her yinelenen giriş koleksiyonda yer alan türü veri anlaşması adına göre adlı bir öğe olarak temsil edilir.  
  
 İçinde `CustomerList` örnekler, yer alan koleksiyon dizeleri. Yinelenen öğe bulunamadı "dize" dize ilkel tür için veri anlaşması adına olduğundan "\<dizesi >".  
  
 Ancak, <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> özelliği <xref:System.Runtime.Serialization.CollectionDataContractAttribute> özniteliği, bu yinelenen öğe adı özelleştirilebilir. Örneğin, şu tür bakın.  
  
 [!code-csharp[c_collection_types_in_data_contracts#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#4)]
 [!code-vb[c_collection_types_in_data_contracts#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#4)]  
  
 Elde edilen XML aşağıdakine benzer.  
  
```xml  
<CustomerList4>  
    <customer>...</customer>  
    <customer>...</customer>  
    <customer>...</customer>  
    ...  
</CustomerList4>  
```  
  
 Yinelenen öğe ad alanı her zaman kullanılarak özelleştirilebilir koleksiyon veri anlaşması ad alanı ile aynı olduğu `Namespace` özelliği, daha önce açıklandığı gibi.  
  
### <a name="customizing-dictionary-collections"></a>Sözlük koleksiyonları özelleştirme  
 Sözlük topluluklarıdır temelde, her giriş değeri tarafından izlenen bir anahtar bulunduğu girişlerinin listeler. Yalnızca normal listeleriyle karşılık gelen öğe adı yinelenen öğeye kullanarak değiştirebileceğiniz gibi <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> özelliği.  
  
 Ayrıca, anahtarı ve değeri kullanarak temsil eden öğe adlarını değiştirebilirsiniz <xref:System.Runtime.Serialization.CollectionDataContractAttribute.KeyName%2A> ve <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ValueName%2A> özellikleri. Bu öğeler için ad, koleksiyon veri anlaşması ad alanı ile aynıdır.  
  
 Örneğin, şu tür bakın.  
  
 [!code-csharp[c_collection_types_in_data_contracts#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#5)]
 [!code-vb[c_collection_types_in_data_contracts#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#5)]  
  
 Serileştirilmiş olduğunda, elde edilen XML aşağıdakine benzer.  
  
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
  
 Sözlük Koleksiyonlar hakkında daha fazla bilgi için "Gelişmiş toplama kuralları" bölümünde bu konunun ilerleyen bölümlerinde bkz.  
  
## <a name="collections-and-known-types"></a>Koleksiyonlar ve bilinen türler  
 Diğer koleksiyonları veya koleksiyon arabirimleri yerine polymorphically kullanıldığında bilinen türler koleksiyon türleri eklemek gerekmez. Örneğin, bir veri üyesi türünün bildirirseniz <xref:System.Collections.IEnumerable> örneği göndermek için <xref:System.Collections.ArrayList>, eklemek gerekmez <xref:System.Collections.ArrayList> bilinen türleri için.  
  
 Koleksiyonları polymorphically yerine olmayan koleksiyon türlerini kullandığınızda, bilinen türleri için eklenmelidir. Örneğin, bir veri üyesi türünün bildirirseniz `Object` örneği göndermek için <xref:System.Collections.ArrayList>, ekleme <xref:System.Collections.ArrayList> bilinen türleri için.  
  
 Bu, herhangi bir eşdeğer koleksiyon polymorphically serileştirmek izin vermez. Örneğin, eklediğinizde <xref:System.Collections.ArrayList> önceki örnekte bilinen türler listesine bu atamanıza izin vermez `Array of Object` eşdeğeri veri sözleşme sahip olsa da, sınıf. Bu seri hale getirme için koleksiyon olmayan türleri üzerinde normal bilinen türleri davranışından farklı değildir, ancak koleksiyonları söz konusu olduğunda denk olarak koleksiyonlar için çok yaygın olmadığından anlamak özellikle önemlidir.  
  
 Serileştirme sırasında belirli veri anlaşması için verilen tüm kapsamda yalnızca bir türü bilinen ve eşdeğer koleksiyonlar tüm aynı veri sözleşmeleri sahip. Önceki örnekte, her ikisi de ekleyemezsiniz, yani <xref:System.Collections.ArrayList> ve `Array of Object` aynı kapsamda bilinen türleri için. Yeniden eşit olmayan koleksiyon türleri bilinen türler davranışı budur ancak koleksiyonlar için anlamak özellikle önemlidir.  
  
 Bilinen türler de koleksiyonlar içeriği için gerekli olabilir. Örneğin, bir <xref:System.Collections.ArrayList> gerçekten örneklerini içerir `Type1` ve `Type2`, bu iki türü bilinen türler için eklenmelidir.  
  
 Aşağıdaki örnek, koleksiyonlar ve bilinen türleri kullanarak doğru şekilde oluşturulmuş nesne grafik gösterir. Gerçek bir uygulamada aşağıdaki veri üyelerini olarak tanımlayın normalde çünkü örnek biraz, contrived `Object`ve bu nedenle herhangi bir bilinen türü/çok biçimlilik sorun yoktur.  
  
 [!code-csharp[c_collection_types_in_data_contracts#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#6)]
 [!code-vb[c_collection_types_in_data_contracts#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#6)]  
  
 Bildirilen türü bir koleksiyon türü ise asıl gönderildiği türü bağımsız olarak seri durumundan çıkarma işleminde bildirilen türü başlatılır. Bildirilen türü bir koleksiyon arabirimi ise, bir tür ile bilinen türler için hiçbir haklısın örneği seri durumdan çıkarıcı seçer.  
  
 Ayrıca seri durumundan çıkarma işleminde bildirilen türü bir koleksiyon türü değil, ancak bir koleksiyon türü gönderiliyor, eşleşen bir koleksiyon türü bilinen türler listesinden çekilir. Koleksiyon arabirim türü seri durumdan çıkarma üzerinde bilinen türler listesine eklemek mümkündür. Bu durumda, seri durumundan çıkarma altyapısı örneği için bir tür yeniden seçer.  
  
## <a name="collections-and-the-netdatacontractserializer-class"></a>Koleksiyonlar ve NetDataContractSerializer sınıfı  
 Zaman <xref:System.Runtime.Serialization.NetDataContractSerializer> sınıfı, kullanımda olmayan özelleştirilmiş koleksiyon türleri (olmadan <xref:System.Runtime.Serialization.CollectionDataContractAttribute> özniteliği) olan değil diziler kaybı, özel anlamları.  
  
 Özelleştirilmiş olmayan koleksiyon türleri ile işaretlenmiş <xref:System.SerializableAttribute> özniteliği hala seri hale getirilemiyor tarafından <xref:System.Runtime.Serialization.NetDataContractSerializer> göre sınıf <xref:System.SerializableAttribute> özniteliği veya <xref:System.Runtime.Serialization.ISerializable> arabirim kuralları.  
  
 Özelleştirilmiş koleksiyon türleri, koleksiyon arabirimleri ve dizi koleksiyon olarak işlendiği hala bile <xref:System.Runtime.Serialization.NetDataContractSerializer> sınıfı kullanılıyor.  
  
## <a name="collections-and-schema"></a>Koleksiyonlar ve şema  
 Tüm eşdeğer koleksiyonları aynı gösterimi XML Şeması Tanım Dili (XSD) şemasında sahiptir. Bu nedenle, normalde aynı koleksiyon türü oluşturulan istemci kodu bir sunucuda almıyor. Örneğin, sunucu ile genel bir veri anlaşması kullanabilir <xref:System.Collections.Generic.List%601> tam sayı veri üyesinin, ancak oluşturulan istemci kodu aynı veri üye dizisi olabilir.  
  
 Sözlük koleksiyon sözlükleri olduklarını belirten bir WCF özel şema ek açıklamalarını ile işaretlenmiş; Aksi takdirde, bunlar bir anahtar ve değer girişleri basit listelerden ayırt edilemiyor. Veri sözleşmesi şema koleksiyonları nasıl temsil edildiğini bir tam açıklaması için bkz: [veri sözleşmesi şema başvurusu](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).  
  
 Varsayılan olarak, içeri aktarılan kod özelleştirilmemiş koleksiyonlar için türleri oluşturulmaz. Veri üyeleri liste koleksiyon türleri dizileri olarak içeri aktarılır ve sözlük koleksiyon türleri veri üyelerinin genel bir sözlük içeri aktarılır.  
  
 Ancak, özelleştirilmiş koleksiyonlar için farklı türler, işaretlenmiş oluşturulan <xref:System.Runtime.Serialization.CollectionDataContractAttribute> özniteliği. (Varsayılan ad alanı, adı, yinelenen öğe adı veya anahtar/değer kullanmayan bir şema özelleştirilmiş koleksiyon türü olan öğe adları.) Bu tür genel türetilen boş türleridir <xref:System.Collections.Generic.List%601> liste türleri ve sözlük türleri için genel bir sözlük.  
  
 Örneğin, aşağıdaki türleri sunucuda olabilir.  
  
 [!code-csharp[c_collection_types_in_data_contracts#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#7)]
 [!code-vb[c_collection_types_in_data_contracts#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#7)]  
  
 Ne zaman şemasını dışarı ve içeri aktarılan geri yeniden oluşturulan istemci kodu aşağıdakine benzer (kolay okunması için özellikleri yerine alanları gösterilir).  
  
 [!code-csharp[c_collection_types_in_data_contracts#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#8)]
 [!code-vb[c_collection_types_in_data_contracts#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#8)]  
  
 Oluşturulan kodda olanları varsayılandan farklı türler kullanmak isteyebilirsiniz. Örneğin, genel kullanmak isteyebilirsiniz <xref:System.ComponentModel.BindingList%601> veri üyeleriniz bunları bağlamak için kullanıcı arabirimi bileşenleri daha kolay hale getirmek için normal diziler yerine.  
  
 Oluşturmak için koleksiyon türlerini seçmek için kullanmak istediğiniz koleksiyon türlerinin bir listesini geçirmek <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A> özelliği <xref:System.Runtime.Serialization.ImportOptions> şema içeri aktarılırken nesne. Bu tür adında *koleksiyon türleri başvurulan*.  
  
 Genel türler başvurulur, ya da tamamen açık genel türler veya tamamen kapalı genel türler olmalıdır.  
  
> [!NOTE]
>  Svcutil.exe aracını kullanırken, bu başvuruyu kullanarak gerçekleştirilebilir **/collectionType** komut satırı anahtarı (kısa form: **/ct**). Bütünleştirilmiş kod kullanarak başvuru yapılan koleksiyon türlerinin de belirtmeniz gerekir aklınızda bulundurun **/reference** geçiş (kısa form: **/r**). Tür genelse, geriye tırnak ve genel parametre sayısı tarafından izlenmesi gerekir. Geriye tırnak (\`) olduğundan tek tırnak (') karakteri ile karıştırılmamalıdır. Kullanarak birden çok başvuru yapılan koleksiyon türlerinin belirtebilirsiniz **/collectionType** birden çok kez geçin.  
  
 Örneğin, genel içeri aktarılacak tüm listeleri neden <xref:System.Collections.Generic.List%601>.  
  
```console  
svcutil.exe MyService.wsdl MyServiceSchema.xsd /r:C:\full_path_to_system_dll\System.dll /ct:System.Collections.Generic.List`1  
```  
  
 Bu başvuru yapılan koleksiyon türlerinin listesi herhangi bir koleksiyonu içeri aktarma sırasında taranır ve en iyi eşleşen koleksiyon, bir veri üye türü (özelleştirilmemiş koleksiyonları için) veya (için özelleştirilmiş koleksiyonlar) türetilmesi için bir temel tür olarak bulunması durumunda kullanılır. Listeleri listeleriyle eşleştirilir sırada sözlükleri yalnızca sözlükleri karşı eşleştirilir.  
  
 Örneğin, genel eklerseniz <xref:System.ComponentModel.BindingList%601> ve <xref:System.Collections.Hashtable> için başvuru yapılan türlerin listesinde, önceki örnekte oluşturulan istemci kodunu aşağıdakine benzer.  
  
 [!code-csharp[c_collection_types_in_data_contracts#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#9)]
 [!code-vb[c_collection_types_in_data_contracts#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#9)]  
  
 Koleksiyon arabirim türleri, başvuru yapılan koleksiyon türlerinin bir parçası olarak belirtebilirsiniz, ancak geçersiz bir koleksiyon türleri belirtemezsiniz (Hayır ettiklerinizi gibi `Add` yöntemi veya Genel oluşturucu).  
  
 Kapalı genel en iyi eşleşme olarak değerlendirilir. (Genel olmayan türler kapalı genel türler için eşdeğer olarak değerlendirilir `Object`). Örneğin, genel türleri <xref:System.Collections.Generic.List%601> , <xref:System.DateTime>genel <xref:System.ComponentModel.BindingList%601> (açık genel), ve <xref:System.Collections.ArrayList> olan aşağıdaki başvuru yapılan koleksiyon türlerinin oluşturulur.  
  
 [!code-csharp[c_collection_types_in_data_contracts#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#10)]
 [!code-vb[c_collection_types_in_data_contracts#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#10)]  
  
 Liste koleksiyonları için yalnızca aşağıdaki tabloda durumlarda desteklenir.  
  
|Başvurulan tür|Başvurulan tür tarafından uygulanan arabirimi|Örnek|Tür kabul edilir:|  
|---------------------|----------------------------------------------|-------------|----------------------|  
|Genel olmayan ya da kapalı genel (parametre herhangi sayısı)|Genel olmayan|`MyType : IList`<br /><br /> veya<br /><br /> `MyType<T> : IList`<br /><br /> Burada T = `int`|Genel, kapalı `Object` (örneğin, `IList<object>`)|  
|Genel olmayan ya da kapalı genel (herhangi bir sayıda mutlaka koleksiyon türü eşleşmeyen)|Genel kapalı|`MyType : IList<string>`<br /><br /> veya<br /><br /> `MyType<T> : IList<string>` Burada T =`int`|Kapalı genel (örneğin, `IList<string>`)|  
|Genel parametreleri herhangi bir sayıda ile kapalı|Açık genel tür parametreleri herhangi birini kullanarak|`MyType<T,U,V> : IList<U>`<br /><br /> Burada T =`int`, U =`string`, V =`bool`|Kapalı genel (örneğin, `IList<string>`)|  
|Açık genel bir parametreye sahip|Açık genel tür parametresini kullanma|`MyType<T> : IList<T>`, T Aç|Açık genel (örneğin, `IList<T>`)|  
  
 Bir türü birden fazla liste koleksiyon arabirim uygularsa aşağıdaki kısıtlamalar uygulanır:  
  
-   Türü genel uyguluyorsa <xref:System.Collections.Generic.IEnumerable%601> (veya türetilmiş arabirimleri) türü birden çok kez farklı türleri için geçerli bir başvuru yapılan koleksiyon türü olarak kabul edilmez ve göz ardı edilir. Bazı uygulamalar geçersiz veya açık genel türler kullanmak olsa bile bu geçerlidir. Örneğin, genel uygulayan bir tür <xref:System.Collections.Generic.IEnumerable%601> , `int` ve genel <xref:System.Collections.Generic.IEnumerable%601> T hiçbir zaman başvurulan bir koleksiyonu olarak kullanılacak `int` veya türünde bağımsız olarak başka herhangi bir tür bir `Add` kabul yöntemi `int` veya `Add` T ya da her ikisi de, bir parametreyi kabul eden yöntemi yazın.  
  
-   Türü bir genel koleksiyon arabirimi uyguluyorsa yanı <xref:System.Collections.IList>, kapalı genel tür genel koleksiyon arabirim olmadığı sürece türü hiçbir zaman bir başvuru yapılan koleksiyon türü olarak kullanılan <xref:System.Object>.  
  
 Aşağıdaki tabloda yalnızca durumlarda sözlük koleksiyonlar için desteklenir.  
  
|Başvurulan tür|Başvurulan tür tarafından uygulanan arabirimi|Örnek|Tür olarak kabul|  
|---------------------|----------------------------------------------|-------------|---------------------|  
|Genel olmayan ya da kapalı genel (parametre herhangi sayısı)|<xref:System.Collections.IDictionary>|`MyType : IDictionary`<br /><br /> veya<br /><br /> `MyType<T> : IDictionary` Burada T =`int`|Genel kapalı `IDictionary<object,object>`|  
|Kapalı genel (parametre herhangi sayısı)|<xref:System.Collections.Generic.IDictionary%602>, kapalı|`MyType<T> : IDictionary<string, bool>` Burada T =`int`|Kapalı genel (örneğin, `IDIctionary<string,bool>`)|  
|Kapalı genel (parametre herhangi sayısı)|Genel <xref:System.Collections.Generic.IDictionary%602>, anahtar veya değer birini kapalı, diğer açıksa ve türün parametrelerden birini kullanır|`MyType<T,U,V> : IDictionary<string,V>` Burada T =`int`, U =`float`, V =`bool`<br /><br /> veya<br /><br /> `MyType<Z> : IDictionary<Z,bool>` Burada Z =`string`|Kapalı genel (örneğin, `IDictionary<string,bool>`)|  
|Kapalı genel (parametre herhangi sayısı)|Genel <xref:System.Collections.Generic.IDictionary%602>, hem anahtar hem de değer açık ve her türün parametrelerden birini kullanır|`MyType<T,U,V> : IDictionary<V,U>` Burada T =`int`, U =`bool`, V =`string`|Kapalı genel (örneğin, `IDictionary<string,bool>`)|  
|Açık genel (iki parametre)|Genel <xref:System.Collections.Generic.IDictionary%602>açın, genel tür parametrelerinin her ikisi göründükleri sırayla kullanır|`MyType<K,V> : IDictionary<K,V>`, K ve V hem de açın|Açık genel (örneğin, `IDictionary<K,V>`)|  
  
 Türü hem de uyguluyorsa <xref:System.Collections.IDictionary> ve genel <xref:System.Collections.Generic.IDictionary%602>, yalnızca genel <xref:System.Collections.Generic.IDictionary%602> olarak kabul edilir.  
  
 Kısmi genel türler başvuran desteklenmiyor.  
  
 Yinelenenlere izin verilmiyor, örneğin, her iki genel eklenemiyor <xref:System.Collections.Generic.List%601> , `Integer` ve genel koleksiyonu `Integer` için <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A>, çünkü bu, hangi tamsayı listesi olduğunda kullanılacak bulunması belirlemek mümkün kılar şemada. Yinelenen sorun ortaya koyan şemada bir tür varsa yinelenenleri algılanır. İçeri aktarılan şema tamsayı listesi içermiyorsa, örneğin, bu iki genel için izin <xref:System.Collections.Generic.List%601> , `Integer` ve genel koleksiyonu `Integer` içinde <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A>, ancak diğerinden hiçbir etkisi olmaz.  
  
## <a name="advanced-collection-rules"></a>Gelişmiş toplama kuralları  
  
### <a name="serializing-collections"></a>Seri hale getirilmesi  
 Toplama kuralları için serileştirme listesi verilmiştir:  
  
-   Koleksiyon türleri (koleksiyonlar, koleksiyonların sahip) birleştirme izin verilir. Basit diziler koleksiyonların koleksiyon olarak kabul edilir. Çok boyutlu diziler desteklenmez.  
  
-   Bayt dizileri ve diziler <xref:System.Xml.XmlNode> değil koleksiyonları temel olarak kabul edilir özel dizi türleri. Her bayt için ayrı bir öğe yerine Base64 kodlamalı veri öbeğinin içeren tek bir XML öğesi sonuçlarında bayt dizisi seri hale getiriliyor. Hakkında daha fazla bilgi için bir dizi <xref:System.Xml.XmlNode> olduğu kabul edilir, bkz: [XML ve ADO.NET türleri veri anlaşmalarında](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md). Elbette, bu özel türleri kendilerini koleksiyonlarında katılabilir: bir dizi içeren her veri Base64 ile kodlanmış bir Öbek ile birden çok XML öğeleri sonuçlarında bayt dizisi.  
  
-   Varsa <xref:System.Runtime.Serialization.DataContractAttribute> öznitelik, bir koleksiyon türüne uygulanır, türü bir koleksiyon olarak değil, normal veri anlaşması türü olarak kabul edilir.  
  
-   Bir koleksiyon türü uyguluyorsa <xref:System.Xml.Serialization.IXmlSerializable> arabirimi, aşağıdaki kurallar geçerlidir, belirli bir türe `myType:IList<string>, IXmlSerializable`:  
  
    -   Bildirilen tür ise `IList<string>`, türü bir liste olarak serileştirilmiş.  
  
    -   Bildirilen tür ise `myType`, olarak serileştirilmiş `IXmlSerializable`.  
  
    -   Bildirilen tür ise `IXmlSerializable`, olarak serileştirilmiş `IXmlSerializable`, ancak yalnızca `myType` bilinen türleri listesi.  
  
-   Koleksiyonlar, serileştirilen ve aşağıdaki tabloda gösterilen yöntemleri kullanılarak seri durumdan.  
  
|Koleksiyon türü uygular|Yöntemleri seri hale getirme üzerinde çağrılır|Yöntemleri seri durumundan çıkarma üzerinde çağrılır|  
|--------------------------------|-----------------------------------------|-------------------------------------------|  
|Genel <xref:System.Collections.Generic.IDictionary%602>|`get_Keys`, `get_Values`|Genel ekleme|  
|<xref:System.Collections.IDictionary>|`get_Keys`, `get_Values`|`Add`|  
|Genel <xref:System.Collections.Generic.IList%601>|Genel <xref:System.Collections.Generic.IList%601> dizin oluşturucu|Genel ekleme|  
|Genel <xref:System.Collections.Generic.ICollection%601>|Numaralandırıcı|Genel ekleme|  
|<xref:System.Collections.IList>|<xref:System.Collections.IList> Dizin Oluşturucu|`Add`|  
|Genel <xref:System.Collections.Generic.IEnumerable%601>|`GetEnumerator`|Statik olmayan bir yöntem `Add` , veya temel türlerinden biri (genel parametre türü) uygun türde bir parametre alır. Bu tür bir yöntem bir koleksiyon türü hem seri hale getirme ve seri durumundan çıkarma sırasında bir koleksiyon olarak değerlendirilecek seri hale getirici için mevcut olması gerekir.|  
|<xref:System.Collections.IEnumerable> (ve bu nedenle <xref:System.Collections.ICollection>, ondan türetilen)|`GetEnumerator`|Statik olmayan bir yöntem `Add` türünden bir parametre almayan `Object`. Bu tür bir yöntem bir koleksiyon türü hem seri hale getirme ve seri durumundan çıkarma sırasında bir koleksiyon olarak değerlendirilecek seri hale getirici için mevcut olması gerekir.|  
  
 Yukarıdaki tabloda azalan öncelik koleksiyon arabirimleri listeler. Bir tür hem de uygular, örneğin, yani <xref:System.Collections.IList> ve genel <xref:System.Collections.Generic.IEnumerable%601>, koleksiyon serileştirilmiş ve ayarına göre seri durumdan <xref:System.Collections.IList> kuralları:  
  
-   Seri durumundan çıkarma sırasında tüm koleksiyonlar ilk türünün bir örneği mevcut bir koleksiyon türü hem seri hale getirme ve seri durumundan çıkarma sırasında bir koleksiyon olarak değerlendirilecek seri hale getirici için varsayılan oluşturucu çağırarak oluşturarak seri.  
  
-   Aynı genel koleksiyon arabirimi birden çok kez uygulanması durumunda (örneğin, bir tür iki genel uyguluyorsa <xref:System.Collections.Generic.ICollection%601> , `Integer` ve genel <xref:System.Collections.Generic.ICollection%601> , <xref:System.String>) ve daha yüksek önceliğe arabirim bulundu, koleksiyonu Geçerli bir koleksiyon kabul değil.  
  
-   Koleksiyon türleri olabilir <xref:System.SerializableAttribute> özniteliği uygulanmış ve uygulayabilirsiniz <xref:System.Runtime.Serialization.ISerializable> arabirimi. Bunların her ikisi de göz ardı edilir. Ancak, türü tam koleksiyon türü gereksinimlerini karşılamıyor, (örneğin, `Add` yöntemi eksik), türü bir koleksiyon türü olarak kabul edilmez ve bu nedenle <xref:System.SerializableAttribute> özniteliği ve <xref:System.Runtime.Serialization.ISerializable> arabirimi belirlemek üzere kullanılır türü seri hale getirilebilir.  
  
-   Uygulama <xref:System.Runtime.Serialization.CollectionDataContractAttribute> özniteliğini kaldırır özelleştirmek için bir koleksiyona <xref:System.SerializableAttribute> önceki geri dönüş mekanizması. Bunun yerine, özelleştirilmiş bir koleksiyon değil karşılayan koleksiyon gereksinimleri çalışamazsa mu bir <xref:System.Runtime.Serialization.InvalidDataContractException> özel durumu oluşturulur. Özel durum dizesi genellikle neden verilen tür geçerli bir koleksiyon olarak kabul edilmez açıklayan bilgiler içerir (hiçbir `Add` yöntemi, hiçbir varsayılan oluşturucu vb.), genellikle uygulamak yararlı olacak şekilde <xref:System.Runtime.Serialization.CollectionDataContractAttribute> hata ayıklama amacıyla özniteliği.  
  
### <a name="collection-naming"></a>Koleksiyon adlandırma  
 Koleksiyon adlandırma kurallarının bir listesi verilmiştir:  
  
-   İlkel türler, içeren liste koleksiyon veri sözleşmeleri yanı sıra, tüm sözlük koleksiyon veri anlaşmaları için varsayılan ad alanı `http://schemas.microsoft.com/2003/10/Serialization/Arrays` Namespace kullanarak geçersiz kılınmadığı sürece. Yerleşik XSD türleri için eşleme türleri olarak `char`, `Timespan`, ve `Guid` türler, ilkel bu amaç için değerlendirilir.  
  
-   Basit olmayan türler, Namespace kullanılarak kılınmadığı sürece içeren koleksiyon türleri için varsayılan ad alanı koleksiyonda yer alan türü veri anlaşması ad ile aynıdır.  
  
-   Varsayılan liste koleksiyon veri sözleşmeleri, adını kullanarak geçersiz kılınmadığı sürece koleksiyonda yer alan türü veri anlaşması adına sahip "ArrayOf" birleştirilmiş dizeyi adıdır. Örneğin, genel liste, tamsayılar için veri anlaşması adına "ArrayOfint" dir. Veri anlaşması adına akılda tutulması `Object` "anyType" olduğundan, genel olmayan listelerin veri anlaşması adına ister <xref:System.Collections.ArrayList> "ArrayOfanyType" olduğu.  
  
 Sözlük koleksiyon verisi için varsayılan adı sözleşmeler, kullanarak geçersiz kılınmadığı sürece `Name`, "ArrayOfKeyValueOf" birleştirilmiş değer türü veri anlaşması adından önce gelen anahtar türü veri anlaşması adına sahip bir dize. Örneğin, veri anlaşması adına bir sözlük genel dize ve tamsayı olan "ArrayOfKeyValueOfstringint". Ayrıca, bir anahtar veya değer türleri ilkel türler emin değilseniz, bir ad alanı karma anahtar ve değer türlerinin veri anlaşması ad alanı adına eklenir. Ad alanı karmaları hakkında daha fazla bilgi için bkz: [veri sözleşmesi adları](../../../../docs/framework/wcf/feature-details/data-contract-names.md).  
  
 Her sözlük koleksiyon veri anlaşması bir sözlük girişi temsil eden yardımcı veri sözleşme var. Adı "ArrayOf" ön eki hariç sözlük veri anlaşması ile aynıdır ve kendi ad alanı sözlük veri anlaşması ile aynıdır. Örneğin, "ArrayOfKeyValueOfstringint" sözlük veri anlaşması için bir sözlük girişi "KeyValueofstringint" veri anlaşması temsil eder. Bu veri sözleşme adını kullanarak özelleştirebileceğiniz `ItemName` sonraki bölümde açıklandığı gibi özellik.  
  
 Genel tür adlandırma kuralları bölümünde anlatıldığı gibi [veri sözleşmesi adları](../../../../docs/framework/wcf/feature-details/data-contract-names.md)olan koleksiyon türlerine; tam olarak uygulamak, genel tür parametreleri belirtmek için küme ayraçlarının içinde adı kullanabilirsiniz. Ancak, küme ayraçları içine numaraları genel parametreler ve koleksiyonda bulunan türleri bakın.  
  
## <a name="collection-customization"></a>Koleksiyon özelleştirme  
 Aşağıdaki kullanır <xref:System.Runtime.Serialization.CollectionDataContractAttribute> özniteliği yasaklanmış olduğuna ve sonucunda bir <xref:System.Runtime.Serialization.InvalidDataContractException> özel durum:  
  
-   Uygulama <xref:System.Runtime.Serialization.DataContractAttribute> bir türün özniteliği <xref:System.Runtime.Serialization.CollectionDataContractAttribute> özniteliği uygulandı, veya türetilmiş türlerini birine.  
  
-   Uygulama <xref:System.Runtime.Serialization.CollectionDataContractAttribute> uygulayan bir tür özniteliği <xref:System.Xml.Serialization.IXmlSerializable> arabirimi.  
  
-   Uygulama <xref:System.Runtime.Serialization.CollectionDataContractAttribute> özniteliği için bir koleksiyon olmayan tür.  
  
-   Ayarlama girişimi <xref:System.Runtime.Serialization.CollectionDataContractAttribute.KeyName%2A> veya <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ValueName%2A> üzerinde bir <xref:System.Runtime.Serialization.CollectionDataContractAttribute> özniteliği bir sözlük olmayan türe uygulandı.  
  
### <a name="polymorphism-rules"></a>Çok biçimlilik kuralları  
 Daha önceden belirtildiği, koleksiyonları kullanarak özelleştirme <xref:System.Runtime.Serialization.CollectionDataContractAttribute> özniteliği ile koleksiyon interchangeability engelleyebilir. İki özelleştirilmiş koleksiyon türleri yalnızca kendi adı, ad alanı, öğe adı, aynı zamanda anahtar ve değer adlarını (bunların sözlük koleksiyon olması halinde) eşleşiyorsa eşdeğer kabul edilebilir.  
  
 Özelleştirmeler nedeniyle, başka bir yere beklenen yanlışlıkla kullanımı bir koleksiyon veri anlaşması için mümkündür. Bu kaçınılmalıdır. Aşağıdaki türleri bakın.  
  
 [!code-csharp[c_collection_types_in_data_contracts#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#11)]
 [!code-vb[c_collection_types_in_data_contracts#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#11)]  
  
 Bu durumda, bir örneğinde `Marks1` atanabilir `testMarks`. Ancak, `Marks2` veri sözleşmesinin eşdeğer kabul edilmediğinden kullanılmamalıdır `IList<int>` veri anlaşması. Veri anlaşması adına "Marks2" değil "ArrayOfint" ise ve yinelenen öğe adı: "\<işaretleyin >" ve "\<int >".  
  
 Aşağıdaki tabloda kurallar koleksiyonları polimorfik atama için geçerlidir.  
  
|Bildirilen tür|Özelleştirilmiş bir koleksiyonu atama|Özelleştirilmiş bir koleksiyonu atama|  
|-------------------|--------------------------------------------|---------------------------------------|  
|Nesne|Sözleşme adı seri hale getirilir.|Sözleşme adı seri hale getirilir.<br /><br /> Özelleştirme kullanılır.|  
|Koleksiyon arabirimi|Sözleşme adı serileştirilmemiş.|Sözleşme adı serileştirilmemiş.<br /><br /> Özelleştirme used.* değil|  
|Koleksiyon olmayan özelleştirilmiş|Sözleşme adı serileştirilmemiş.|Sözleşme adı seri hale getirilir.<br /><br /> Özelleştirme used.* *|  
|Özelleştirilmiş koleksiyonu|Sözleşme adı seri hale getirilir. Özelleştirme used.* * değil|Sözleşme adı seri hale getirilir.<br /><br /> Atanan türü özelleştirme used.* *|  
  
 * İle <xref:System.Runtime.Serialization.NetDataContractSerializer> sınıfı özelleştirme bu durumda kullanılır. <xref:System.Runtime.Serialization.NetDataContractSerializer> Sınıfı da serileştiren gerçek tür adı bu durumda, bu nedenle beklendiği gibi çalıştığını seri durumdan çıkarma.  
  
 ** Bu gibi durumlarda, şema geçersiz durumda neden ve bu nedenle kaçınılmalıdır.  
  
 Sözleşme adı burada serileştirildiği durumlarda atanan koleksiyon türü bilinen türler listesinde olmalıdır. Bunun tersi de geçerlidir: Burada adı seri durumda türü bilinen türler listesine ekleyerek gerekli değildir.  
  
 Türetilmiş bir tür dizisi, bir dizi temel türüne atanabilir. Bu durumda, türetilmiş bir tür için sözleşme adı yinelenen her öğe için seri hale getirilir. Örneğin, bir tür ederse `Book` türünden türetilen `LibraryItem`, bir dizi atayabilirsiniz `Book` dizisi olarak `LibraryItem`. Bu, diğer koleksiyon türlerine uygulanmaz. Örneğin, atanamaz bir `Generic List of Book` için bir `Generic List of LibraryItem`. Ancak, atamak için bir `Generic List of LibraryItem` içeren `Book` örnekleri. Dizi ve dizi olmayan durum `Book` bilinen türleri listesinde olmalıdır.  
  
## <a name="collections-and-object-reference-preservation"></a>Koleksiyonlar ve nesne başvuru korunması  
 Seri hale getirici işlevleri, burada, nesne başvuruları korur modunda nesne başvuru korunması koleksiyonlar için de geçerlidir. Özellikle, nesne kimliği, tüm koleksiyonlar ve koleksiyonları'nda yer alan tek tek öğeleri korunur. Sözlük için hem de anahtar/değer çifti nesneleri ve ayrı anahtar ve değer nesneleri için nesne kimliğini korunur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.Serialization.CollectionDataContractAttribute>
