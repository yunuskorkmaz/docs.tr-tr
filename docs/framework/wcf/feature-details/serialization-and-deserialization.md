---
title: Seri Hale Getirme ve Seri Durumdan Çıkarma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3d71814c-bda7-424b-85b7-15084ff9377a
ms.openlocfilehash: 085186eae034314437d5a0c1fe90e6cdf6902c5e
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045847"
---
# <a name="serialization-and-deserialization"></a>Seri Hale Getirme ve Seri Durumdan Çıkarma
Windows Communication Foundation (WCF) yeni bir serileştirme altyapısı içerir, <xref:System.Runtime.Serialization.DataContractSerializer>. .NET Framework nesneleri ve XML arasında her iki yönde çevirir.<xref:System.Runtime.Serialization.DataContractSerializer> Bu konuda, serileştiricinin nasıl çalıştığı açıklanmaktadır.  
  
 .NET Framework nesneleri serileştirilirken, serileştirici, yeni *veri sözleşmesi* modeli de dahil olmak üzere çeşitli serileştirme programlama modellerini anlamıştır. Desteklenen türlerin tam listesi için bkz. [veri sözleşmesi serileştiricisi tarafından desteklenen türler](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md). Veri sözleşmelerine giriş için bkz. [Veri Sözleşmelerini Kullanma](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
 XML serisi kaldırılırken, serileştirici <xref:System.Xml.XmlReader> ve <xref:System.Xml.XmlWriter> sınıflarını kullanır. Ayrıca, <xref:System.Xml.XmlDictionaryReader> WCF ikili XML <xref:System.Xml.XmlDictionaryWriter> biçimi kullanılırken olduğu gibi bazı durumlarda iyileştirilmiş XML üretmesine olanak tanımak için ve sınıflarını destekler.  
  
 WCF Ayrıca bir yardımcı seri hale getirici <xref:System.Runtime.Serialization.NetDataContractSerializer>içerir. <xref:System.Runtime.Serialization.NetDataContractSerializer> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> , Ve<xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> serileştiricilerle benzerdir çünkü Ayrıca, seri hale getirilmiş verilerin bir parçası olarak .NET Framework tür adları da yayar. Aynı türler serileştirilmede paylaşıldığında ve seri durumdan çıkarma bittikten sonra kullanılır. Hem hem de ,<xref:System.Runtime.Serialization.XmlObjectSerializer>ortak bir temel sınıftan türet,.<xref:System.Runtime.Serialization.NetDataContractSerializer> <xref:System.Runtime.Serialization.DataContractSerializer>  
  
> [!WARNING]
> , <xref:System.Runtime.Serialization.DataContractSerializer> Denetim karakterlerini içeren dizeleri xml varlıkları olarak 20 ' nin altında olan onaltılık bir değerle seri hale getirir. Bu, bir WCF hizmetine bu tür veriler gönderilirken WCF olmayan bir istemciyle ilgili soruna neden olabilir.  
  
## <a name="creating-a-datacontractserializer-instance"></a>DataContractSerializer örneği oluşturma  
 Öğesinin <xref:System.Runtime.Serialization.DataContractSerializer> bir örneğini oluşturmak önemli bir adımdır. Oluşturma işleminden sonra ayarları değiştiremezsiniz.  
  
### <a name="specifying-the-root-type"></a>Kök türünü belirtme  
 *Kök türü* , örnekleri seri hale getirilen veya seri durumdan çıkarılan türüdür. Birçok Oluşturucu aşırı yüküne `type` sahiptir,ancakenazından,parametresikullanılarakbirköktürüsağlanmalıdır.<xref:System.Runtime.Serialization.DataContractSerializer>  
  
 Belirli bir kök türü için oluşturulan serileştirici, tür kök türünden türetilmediği takdirde, başka bir türü seri hale getirmek (veya serisini kaldırmak) için kullanılamaz. Aşağıdaki örnekte iki sınıf gösterilmektedir.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#1)]
 [!code-vb[c_StandaloneDataContractSerializer#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#1)]  
  
 Bu kod, `DataContractSerializer` yalnızca `Person` sınıfının örneklerini seri hale getirmek veya seri durumdan çıkarmak için kullanılabilen bir örneğini oluşturur.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#2)]
 [!code-vb[c_StandaloneDataContractSerializer#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#2)]  
  
### <a name="specifying-known-types"></a>Bilinen türleri belirtme  
 Bir çok biçimlilik, seri hale getirilen veya başka bir mekanizmayla işlenmemiş <xref:System.Runtime.Serialization.KnownTypeAttribute> olan türlere dahilse, olası bilinen türlerin bir listesi `knownTypes` parametresi kullanılarak seri hale getirici oluşturucusuna geçirilmelidir. Bilinen türler hakkında daha fazla bilgi için bkz. [veri sözleşmesi bilinen türler](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
 Aşağıdaki örnek, belirli bir türünün `LibraryPatron` `LibraryItem`bir koleksiyonunu içeren sınıfını gösterir,. İkinci sınıf `LibraryItem` türü tanımlar. Üçüncü ve dört Sınıf (`Book` ve `Newspaper`) `LibraryItem` sınıfından devralınır.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#3)]  
 [!code-vb[c_StandaloneDataContractSerializer#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#3)]  
  
 Aşağıdaki kod, `knownTypes` parametresini kullanarak seri hale getirici örneğini oluşturur.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#4)]
 [!code-vb[c_StandaloneDataContractSerializer#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#4)]  
  
### <a name="specifying-the-default-root-name-and-namespace"></a>Varsayılan kök adı ve ad alanını belirtme  
 Normalde, bir nesne serileştirildiğinde, en dıştaki XML öğesinin varsayılan adı ve ad alanı veri sözleşmesinin adı ve ad alanına göre belirlenir. Tüm iç öğelerin adları, veri üyesi adlarından belirlenir ve ad alanı veri sözleşmesinin ad alanıdır. Aşağıdaki örnek, `Name` <xref:System.Runtime.Serialization.DataContractAttribute> ve `Namespace` sınıflarının<xref:System.Runtime.Serialization.DataMemberAttribute> oluşturucularında ve değerlerini ayarlar.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#5)]
 [!code-vb[c_StandaloneDataContractSerializer#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#5)]  
  
 `Person` Sınıfının bir örneğini seri hale getirmek aşağıdakine benzer bir XML üretir.  
  
```xml  
<PersonContract xmlns="http://schemas.contoso.com">  
  <AddressMember>  
    <StreetMember>123 Main Street</StreetMember>  
   </AddressMember>  
</PersonContract>  
```  
  
 Ancak, `rootName` ve `rootNamespace` parametrelerinin <xref:System.Runtime.Serialization.DataContractSerializer> değerlerini oluşturucuya geçirerek kök öğenin varsayılan adını ve ad alanını özelleştirebilirsiniz. Öğesinin, `rootNamespace` veri üyelerine karşılık gelen içerilen öğelerin ad alanını etkilemediğini unutmayın. Yalnızca en dıştaki öğenin ad alanını etkiler.  
  
 Bu değerler, ikili xml biçimi kullanılarak en iyi duruma getirilmesini <xref:System.Xml.XmlDictionaryString> sağlamak için sınıfın dizeleri veya örnekleri olarak geçirilebilir.  
  
### <a name="setting-the-maximum-objects-quota"></a>En fazla nesne kotasını ayarlama  
 Bazı `DataContractSerializer` Oluşturucu aşırı yüklemeleri bir `maxItemsInObjectGraph` parametreye sahip. Bu parametre, seri hale getirici tarafından seri hale getirilen veya seri hale getirilen en fazla nesne sayısını, <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> tek bir yöntem çağrısında belirler. (Yöntem her zaman bir kök nesneyi okur, ancak bu nesnenin veri üyelerinde başka nesneleri olabilir. Bu nesneler başka nesneler içerebilir ve bu şekilde devam eder.) Varsayılan değer 65536 ' dir. Dizileri serileştirmek veya seri durumdan çıkarma sırasında her dizi girişinin ayrı bir nesne olarak sayımlarını unutmayın. Ayrıca, bazı nesnelerin büyük bir bellek temsili olabileceğini ve bu kotanın tek başına hizmet reddi saldırısını engellemek için yeterli olamayacağını unutmayın. Daha fazla bilgi için bkz. [veriler Için güvenlik konuları](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md). Bu kotayı varsayılan değerin ötesinde artırmanız gerekiyorsa, bunu hem gönderme (serileştirme) hem de alma (serisini kaldırma) tarafında yapmak önemlidir çünkü her ikisi de verileri okurken ve yazarken geçerlidir.  
  
### <a name="round-trips"></a>Gidiş dönüşler  
 Bir nesne seri durumdan çıkarılmışsa ve bir işlemde yeniden serileştirildiğinde *gidiş dönüş* oluşur. Bu nedenle, XML 'den bir nesne örneğine gider ve bir XML akışına geri döner.  
  
 Bazı `DataContractSerializer` Oluşturucu aşırı yüklemeleri, `ignoreExtensionDataObject` varsayılan olarak olarak `false` ayarlanmış bir parametreye sahiptir. Bu varsayılan modda, veri sözleşmesi <xref:System.Runtime.Serialization.IExtensibleDataObject> Arabirimi uyguladığı sürece veriler, daha eski bir sürüm aracılığıyla bir veri sözleşmesinin daha yeni bir sürümüne, kayıp olmadan daha yeni sürüme geri gönderilebilir. Örneğin, `Person` veri sözleşmesinin sürüm 1 ' i `Name` ve `PhoneNumber` veri üyelerini içerdiğini varsayın ve sürüm 2 bir `Nickname` üye ekler. Uygulanmışsa, sürüm 2 ' den sürüm 1 `Nickname` ' e bilgi gönderirken veriler depolanır ve sonra veriler tekrar serileştirildiğinde yeniden oluşturulur; bu nedenle, gidiş yolculuğuna hiçbir veri kaybolmaz. `IExtensibleDataObject` Daha fazla bilgi için bkz. [Ileri uyumlu veri sözleşmeleri](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md) ve [veri sözleşmesi sürümü oluşturma](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md).  
  
#### <a name="security-and-schema-validity-concerns-with-round-trips"></a>Güvenlik ve şema geçerliliği gidiş dönüşlerle Ilgilidir  
 Gidiş dönüşlerin güvenliği olumsuz etkileyebilir. Örneğin, büyük miktarlarda gereksiz verileri seri durumdan çıkarmak ve depolamak bir güvenlik riski oluşturabilir. Özellikle dijital imzalar dahil edilmişse, bu verileri doğrulamak için bir yol olmadığı konusunda güvenlik sorunları olabilir. Örneğin, önceki senaryoda sürüm 1 uç noktası kötü amaçlı veriler içeren bir `Nickname` değeri imzalamada olabilir. Son olarak, şema geçerliliği sorunları olabilir: bir uç nokta, belirtilen sözleşmeye tamamen bağlı olan ve ek değer içermeyen verileri her zaman göstermek isteyebilir. Önceki örnekte, sürüm 1 uç noktasının sözleşmesi yalnızca `Name` ve `PhoneNumber`olduğunu söyler ve şema doğrulamasının kullanılıyorsa, ek `Nickname` değerin yaymasının başarısız olmasına neden olur.  
  
#### <a name="enabling-and-disabling-round-trips"></a>Gidiş dönüşleri etkinleştirme ve devre dışı bırakma  
 Gidiş dönüşlerin devre dışı bırakmak için <xref:System.Runtime.Serialization.IExtensibleDataObject> arabirimi uygulamayın. Türler üzerinde denetiminiz yoksa, `ignoreExtensionDataObject` parametresini aynı etkiyi elde etmek için olarak `true` ayarlayın.  
  
### <a name="object-graph-preservation"></a>Nesne grafiği koruması  
 Normal olarak, seri hale getirici aşağıdaki kodda olduğu gibi nesne kimliğiyle ilgilenmez.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#6)]
 [!code-vb[c_StandaloneDataContractSerializer#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#6)]  
  
 Aşağıdaki kod bir satınalma siparişi oluşturur.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#7)]
 [!code-vb[c_StandaloneDataContractSerializer#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#7)]  
  
 `billTo` Ve`shipTo` alanlarının aynı nesne örneğine ayarlandığına dikkat edin. Ancak oluşturulan XML, bilgilerin yinelenenleri yinelemeyor ve aşağıdaki XML 'e benzer şekilde görünür.  
  
```xml  
<PurchaseOrder>  
  <billTo><street>123 Main St.</street></billTo>  
  <shipTo><street>123 Main St.</street></shipTo>  
</PurchaseOrder>  
```  
  
 Ancak, bu yaklaşım, istenmeyen olabilecek aşağıdaki özelliklere sahiptir:  
  
- Mının. Verilerin çoğaltılması verimsiz.  
  
- Döngüsel başvurular. Nesneler, diğer nesneler aracılığıyla bile kendilerine başvursa, çoğaltma tarafından serileştirilmesi sonsuz bir döngüye neden olur. (Bu durumda serileştirici <xref:System.Runtime.Serialization.SerializationException> bir oluşturur.)  
  
- İçeriyor. Bazen iki başvuruyu aynı nesneye ait olan ve iki özdeş nesne için değil, bu olguyu korumak önemlidir.  
  
 Bu nedenlerden dolayı, bazı `DataContractSerializer` Oluşturucu aşırı yüklemeleri bir `preserveObjectReferences` parametreye sahiptir (varsayılan olarak `false`). Bu parametre olarak `true`ayarlandığında, yalnızca WCF 'nin anladığı nesne başvurularını kodlamaya yönelik özel bir yöntem kullanılır. Olarak `true`ayarlandığında, XML kodu örneği şimdi aşağıdakine benzer.  
  
```xml  
<PurchaseOrder ser:id="1">  
  <billTo ser:id="2"><street ser:id="3">123 Main St.</street></billTo>  
  <shipTo ser:ref="2"/>  
</PurchaseOrder>  
```  
  
 "Ser" ad alanı, `http://schemas.microsoft.com/2003/10/Serialization/`standart serileştirme ad alanını ifade eder. Her veri parçası yalnızca bir kez serileştirilir ve KIMLIK numarası verilir ve sonraki kullanımlar, zaten serileştirilmiş veriler için bir başvuruya neden olur.  
  
> [!IMPORTANT]
> Veri sözleşmesinde `XMLElement`hem "kimlik" hem de "ref" öznitelikleri varsa, "ref" özniteliği kabul edilir ve "id" özniteliği yok sayılır.  
  
 Bu modun sınırlamalarını anlamak önemlidir:  
  
- Tarafından `DataContractSerializer` `DataContractSerializer` `true` `preserveObjectReferences` ayarlandığı XML, diğer teknolojilerle birlikte kullanılamaz ve yalnızca başka bir örnek tarafından, olarak ayarlanmış olarak erişilebilir. `true` `preserveObjectReferences`  
  
- Bu özellik için meta veri (şema) desteği yok. Oluşturulan şema yalnızca `preserveObjectReferences` , olarak `false`ayarlandığında geçerlidir.  
  
- Bu özellik serileştirme ve seri durumdan çıkarma işleminin daha yavaş çalışmasına neden olabilir. Verilerin çoğaltılması gerekmese de, bu modda ek nesne karşılaştırmalarının gerçekleştirilmesi gerekir.  
  
> [!CAUTION]
> Mod etkinleştirildiğinde, özellikle doğru kotanın `maxItemsInObjectGraph` değeri ayarlamanız önemlidir. `preserveObjectReferences` Dizilerin bu modda işlenme yöntemi nedeniyle, bir saldırganın büyük bellek tüketimine yalnızca `maxItemsInObjectGraph` kotayla sınırlı olan küçük bir kötü amaçlı ileti oluşturmasıyla kolay bir durum oluşturur.  
  
### <a name="specifying-a-data-contract-surrogate"></a>Veri anlaşması yedeği belirtme  
 Bazı `DataContractSerializer` Oluşturucu aşırı yüklemeleri, `dataContractSurrogate` olarak `null`ayarlanmış olabilecek bir parametreye sahiptir. Aksi takdirde, <xref:System.Runtime.Serialization.IDataContractSurrogate> arabirimini uygulayan bir tür olan bir *veri anlaşması yedeği*belirtmek için bunu kullanabilirsiniz. Daha sonra, serileştirme ve seri kaldırma işlemini özelleştirmek için arabirimini kullanabilirsiniz. Daha fazla bilgi için bkz. [veri sözleşmesi yedeklerin kapıları](../../../../docs/framework/wcf/extending/data-contract-surrogates.md).  
  
## <a name="serialization"></a>Serileştirme  
 Aşağıdaki bilgiler, <xref:System.Runtime.Serialization.XmlObjectSerializer> <xref:System.Runtime.Serialization.DataContractSerializer> ve <xref:System.Runtime.Serialization.NetDataContractSerializer> sınıfları dahil, öğesinden devralan tüm sınıflar için geçerlidir.  
  
### <a name="simple-serialization"></a>Basit serileştirme  
 Bir nesneyi seri hale getirmenin en temel yolu <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObject%2A> yöntemine geçirmektir. Her biri, bir veya <xref:System.IO.Stream> <xref:System.Xml.XmlDictionaryWriter>' a <xref:System.Xml.XmlWriter>yazmak için üç aşırı yükleme vardır. <xref:System.IO.Stream> Aşırı yüklemede, çıktı UTF-8 kodlamasında XML 'dir. <xref:System.Xml.XmlDictionaryWriter> Aşırı yükleme ile serileştirici, ikili XML için çıkışını en iyi duruma getirir.  
  
 <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObject%2A> Yöntemi kullanılırken, serileştirici sarmalayıcı öğesi için varsayılan ad ve ad alanını kullanır ve içeriği (varsayılan kök adı ve ad alanını belirtme "bölümüne bakın).  
  
 Aşağıdaki örnek, ile <xref:System.Xml.XmlDictionaryWriter>yazmayı gösterir.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#8)]
 [!code-vb[c_StandaloneDataContractSerializer#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#8)]  
  
 Bu, aşağıdakine benzer bir XML üretir.  
  
```xml  
<Person>  
  <Name>Jay Hamlin</Name>  
  <Address>123 Main St.</Address>  
</Person>  
```  
  
### <a name="step-by-step-serialization"></a>Adım adım serileştirme  
 Son öğesini yazmak <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObjectContent%2A>, nesne <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteEndObject%2A> içeriğini yazmak ve sarmalayıcı öğesini sırasıyla kapatmak için ,,veyöntemlerinikullanın.<xref:System.Runtime.Serialization.XmlObjectSerializer.WriteStartObject%2A>  
  
> [!NOTE]
> Bu yöntemlerin aşırı <xref:System.IO.Stream> yüklemesi yoktur.  
  
 Bu adım adım serileştirme iki ortak kullanımı vardır. Bunlardan biri, aşağıdaki örnekte gösterildiği gibi, ve `WriteStartObject` `WriteObjectContent`arasında öznitelikler veya açıklamalar gibi içerikler eklemedir.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#9)]
 [!code-vb[c_StandaloneDataContractSerializer#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#9)]  
  
 Bu, aşağıdakine benzer bir XML üretir.  
  
```xml  
<Person serializedBy="myCode">  
  <Name>Jay Hamlin</Name>  
  <Address>123 Main St.</Address>  
</Person>  
```  
  
 Aşağıdaki kodda gösterildiği gibi, başka bir <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteStartObject%2A> yaygın <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteEndObject%2A> kullanım, ve tamamen kullanmaktan ve kendi özel sarmalayıcı öğesini yazmak (ya da sarmalayıcı yazmanın tamamen atlanmak).  
  
 [!code-csharp[c_StandaloneDataContractSerializer#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#10)]
 [!code-vb[c_StandaloneDataContractSerializer#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#10)]  
  
 Bu, aşağıdakine benzer bir XML üretir.  
  
```xml  
<MyCustomWrapper>  
  <Name>Jay Hamlin</Name>  
  <Address>123 Main St.</Address>  
</MyCustomWrapper>  
```  
  
> [!NOTE]
> Adım adım serileştirme kullanma, şemaya geçersiz XML ile sonuçlanabilir.  
  
## <a name="deserialization"></a>Seri  
 Aşağıdaki bilgiler, <xref:System.Runtime.Serialization.XmlObjectSerializer> <xref:System.Runtime.Serialization.DataContractSerializer> ve <xref:System.Runtime.Serialization.NetDataContractSerializer> sınıfları dahil, öğesinden devralan tüm sınıflar için geçerlidir.  
  
 Bir nesneyi seri durumdan çıkarmak için en temel yol, <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> yöntem aşırı yüklerinden birini çağırmanız olur. Her biri, bir veya <xref:System.Xml.XmlDictionaryReader> `Stream`bir ile `XmlReader`okumak için üç aşırı yükleme vardır. Aşırı yüklemenin hiçbir kota tarafından korunmayan bir <xref:System.Xml.XmlDictionaryReader> metin oluşturduğunu ve yalnızca güvenilen verileri okumak için kullanılması gerektiğini unutmayın. `Stream`  
  
 Ayrıca, `ReadObject` yöntemin döndürdüğü nesnenin uygun türe dönüştürülmesi gerektiğini unutmayın.  
  
 Aşağıdaki kod, <xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Xml.XmlDictionaryReader>ve ' ın bir örneğini oluşturur, sonra bir `Person` örneği serileştirir.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#11)]
 [!code-vb[c_StandaloneDataContractSerializer#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#11)]  
  
 <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> Yöntemini çağırmadan önce sarmalayıcı öğesine veya sarmalayıcı öğesinden önce gelen içerik olmayan bir düğüme XML okuyucuyu konumlandırın. Bunu, <xref:System.Xml.XmlReader.Read%2A> <xref:System.Xml.XmlReader> veya türetmesininyönteminiçağırarakveöğesiniaşağıdakikoddagösterildiğigibitestederekyapabilirsiniz.<xref:System.Xml.XmlReader.NodeType%2A>  
  
 [!code-csharp[c_StandaloneDataContractSerializer#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#12)]
 [!code-vb[c_StandaloneDataContractSerializer#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#12)]  
  
 Okuyucuyu öğesine `ReadObject`teslim etmeden önce bu sarmalayıcı öğesinde öznitelikleri okuyabileceğinizi unutmayın.  
  
 Basit `ReadObject` aşırı yüklerden birini kullanırken, seri hale getirici sarmalayıcı öğesinde varsayılan adı ve ad alanını arar ("varsayılan kök adı ve ad alanını belirtme" başlığına bakın) ve bilinmeyen bulursa bir özel durum oluşturur dosyalarında. Önceki örnekte `<Person>` sarmalayıcı öğesi beklenmektedir. <xref:System.Runtime.Serialization.XmlObjectSerializer.IsStartObject%2A> Yöntemi, okuyucunun beklenen olarak adlandırılan bir öğede konumlandığını doğrulamak için çağrılır.  
  
 Bu sarmalayıcı öğe adı denetimini devre dışı bırakmak için bir yol vardır; `ReadObject` metodun bazı aşırı yüklemeleri, varsayılan olarak olarak `true` ayarlanan `verifyObjectName`Boolean parametresini alır. Olarak `false`ayarlandığında, sarmalayıcı öğesinin adı ve ad alanı yok sayılır. Bu, daha önce açıklanan adım adım serileştirme mekanizması kullanılarak yazılmış XML 'yi okumak için yararlıdır.  
  
## <a name="using-the-netdatacontractserializer"></a>NetDataContractSerializer kullanma  
 Ve arasındaki birincil fark, `NetDataContractSerializer` veri anlaşması adlarını kullanır,ancakçıktılartam.NETFrameworkderlemeveserileştirilmişXMLiçindetüradlarıdır.`DataContractSerializer` <xref:System.Runtime.Serialization.NetDataContractSerializer> `DataContractSerializer` Bu, tam olarak aynı türlerin serileştirme ve seri kaldırma uç noktaları arasında paylaşılması gerektiği anlamına gelir. Bu, seri durumdan çıkarılacak kesin türler her zaman bilindiğinden, `NetDataContractSerializer` bilinen türler mekanizmasının ile gerekmediği anlamına gelir.  
  
 Bununla birlikte, çeşitli sorunlar meydana gelebilir:  
  
- Güven. Seri durumdan çıkarılan XML 'de bulunan herhangi bir tür yüklenir. Kötü amaçlı türlerin yüklenmesine zorlamak için bu açıktan yararlanılabilir. ' Nin güvenilmeyen verilerle kullanılması yalnızca bir *serileştirme Bağlayıcısı* <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder%2A> kullanılıyorsa (özellik veya Oluşturucu parametresi kullanılarak) yapılmalıdır. `NetDataContractSerializer` Bağlayıcı yalnızca güvenli türlerin yüklenmesine izin verir. Ciltçi mekanizması, <xref:System.Runtime.Serialization> ad alanı kullanan bir tür ile aynıdır.  
  
- Sürümü. XML 'de tam tür ve derleme adlarının kullanılması, türlerin nasıl sürümlendirilemez olduğunu önemli ölçüde kısıtlar. Aşağıdakiler değiştirilemez: tür adları, ad alanları, derleme adları ve derleme sürümleri. Özellik veya Oluşturucu parametresinin varsayılan değeri <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle.Full> yerine <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle.Simple> olarak ayarlanması, derleme sürümü değişikliklerine izin verir, ancak genel parametre türleri için kullanılamaz. <xref:System.Runtime.Serialization.NetDataContractSerializer.AssemblyFormat%2A>  
  
- Liğin. .NET Framework türü ve derleme adları XML 'ye eklendiğinden, .NET Framework dışındaki platformlar elde edilen verilere erişemez.  
  
- Mının. Tür ve derleme adlarının yazılması, sonuçta elde edilen XML 'in boyutunu önemli ölçüde artırır.  
  
 Bu mekanizma, .NET Framework uzaktan iletişim tarafından kullanılan ikili veya soap serileştirmesine benzer (özellikle <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> , <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>ve).  
  
 `DataContractSerializer`' Ninkullanımı,aşağıdaki`NetDataContractSerializer` farklılıklarla ile benzerdir:  
  
- Oluşturucular için bir kök türü belirtmeniz gerekmez. Aynı örneği `NetDataContractSerializer`ile herhangi bir türü seri hale getirebilirsiniz.  
  
- Oluşturucular bilinen türlerin bir listesini kabul etmez. Tür adları XML içine serileştirildiğinde bilinen türler mekanizması gereksizdir.  
  
- Oluşturucular, bir veri sözleşmesi yedeği kabul etmez. Bunun yerine, adlı <xref:System.Runtime.Serialization.ISurrogateSelector> `surrogateSelector` bir parametresini kabul ederler <xref:System.Runtime.Serialization.NetDataContractSerializer.SurrogateSelector%2A> (özelliği ile eşlenir). Bu, eski bir vekil mekanizmasıdır.  
  
- Oluşturucular, `assemblyFormat` özelliği<xref:System.Runtime.Serialization.NetDataContractSerializer.AssemblyFormat%2A> ile eşleşen bir parametresini <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle> kabul eder. Daha önce anlatıldığı gibi, bu, serileştiricinin sürüm oluşturma yeteneklerini geliştirmek için kullanılabilir. Bu, ikili veya SOAP <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle> serileştirme içindeki mekanizmaya eşdeğerdir.  
  
- Oluşturucular, <xref:System.Runtime.Serialization.StreamingContext> özelliği<xref:System.Runtime.Serialization.NetDataContractSerializer.Context%2A> ile eşleşen adlı `context` bir parametre kabul eder. Bunu, serileştirilmiş olan türlere bilgi geçirmek için kullanabilirsiniz. Bu kullanım, diğer <xref:System.Runtime.Serialization.StreamingContext> <xref:System.Runtime.Serialization> sınıflarda kullanılan mekanizmaya benzer.  
  
- Ve yöntemleri, <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObject%2A> ve yöntemleri<xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> için diğer adlardır. <xref:System.Runtime.Serialization.NetDataContractSerializer.Serialize%2A> <xref:System.Runtime.Serialization.NetDataContractSerializer.Deserialize%2A> Bunlar, ikili veya SOAP serileştirmesi ile daha tutarlı bir programlama modeli sağlamak için mevcuttur.  
  
 Bu özellikler hakkında daha fazla bilgi için bkz. [Ikili serileştirme](../../../standard/serialization/binary-serialization.md).  
  
 `NetDataContractSerializer` Ve kullananXMLbiçimlerinormaldeuyumludeğildir.`DataContractSerializer` Diğer bir deyişle, bu serileştiricilerin biriyle Serileştirmeye çalışılması ve diğeri ile seri durumdan çıkarma desteklenen bir senaryo değildir.  
  
 Ayrıca, nesnesinin, `NetDataContractSerializer` nesne grafiğindeki her bir düğüm için tam .NET Framework türü ve derleme adını çıkmadığını unutmayın. Bu bilgiler yalnızca belirsiz olduğunda çıktı verir. Yani, kök nesne düzeyinde ve çok biçimli durumlar için çıkış yapılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.NetDataContractSerializer>
- <xref:System.Runtime.Serialization.XmlObjectSerializer>
- [İkili Serileştirme](../../../standard/serialization/binary-serialization.md)
- [Veri Anlaşması Seri Hale Getirici Tarafından Desteklenen Türler](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)
