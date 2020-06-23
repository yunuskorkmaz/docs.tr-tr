---
title: Seri Hale Getirme ve Seri Durumdan Çıkarma
description: Her iki yönde de .NET Framework nesneleri ve XML arasında çeviren WCF serileştirme altyapısı hakkında bilgi edinin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3d71814c-bda7-424b-85b7-15084ff9377a
ms.openlocfilehash: 3927c17a2548a094a63ffd95ff8a3701403de281
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244913"
---
# <a name="serialization-and-deserialization"></a>Seri Hale Getirme ve Seri Durumdan Çıkarma
Windows Communication Foundation (WCF) yeni bir serileştirme altyapısı içerir, <xref:System.Runtime.Serialization.DataContractSerializer> . <xref:System.Runtime.Serialization.DataContractSerializer>.NET Framework nesneleri ve XML arasında her iki yönde çevirir. Bu konuda, serileştiricinin nasıl çalıştığı açıklanmaktadır.  
  
 .NET Framework nesneleri serileştirilirken, serileştirici, yeni *veri sözleşmesi* modeli de dahil olmak üzere çeşitli serileştirme programlama modellerini anlamıştır. Desteklenen türlerin tam listesi için bkz. [veri sözleşmesi serileştiricisi tarafından desteklenen türler](types-supported-by-the-data-contract-serializer.md). Veri sözleşmelerine giriş için bkz. [Veri Sözleşmelerini Kullanma](using-data-contracts.md).  
  
 XML serisi kaldırılırken, serileştirici <xref:System.Xml.XmlReader> ve sınıflarını kullanır <xref:System.Xml.XmlWriter> . Ayrıca, <xref:System.Xml.XmlDictionaryReader> <xref:System.Xml.XmlDictionaryWriter> WCF ikili xml biçimi kullanılırken olduğu gibi bazı durumlarda iyileştirilmiş XML üretmesine olanak tanımak için ve sınıflarını destekler.  
  
 WCF Ayrıca bir yardımcı seri hale getirici içerir <xref:System.Runtime.Serialization.NetDataContractSerializer> . , <xref:System.Runtime.Serialization.NetDataContractSerializer> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> Ve <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> serileştiricilerle benzerdir çünkü Ayrıca, seri hale getirilmiş verilerin bir parçası olarak .NET Framework tür adları da yayar. Aynı türler serileştirilmede paylaşıldığında ve seri durumdan çıkarma bittikten sonra kullanılır. Hem hem de, <xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Runtime.Serialization.NetDataContractSerializer> ortak bir temel sınıftan türet, <xref:System.Runtime.Serialization.XmlObjectSerializer> .  
  
> [!WARNING]
> , <xref:System.Runtime.Serialization.DataContractSerializer> Denetim karakterlerini içeren DIZELERI xml varlıkları olarak 20 ' nin altında olan onaltılık bir değerle seri hale getirir. Bu, bir WCF hizmetine bu tür veriler gönderilirken WCF olmayan bir istemciyle ilgili soruna neden olabilir.  
  
## <a name="creating-a-datacontractserializer-instance"></a>DataContractSerializer örneği oluşturma  
 Öğesinin bir örneğini oluşturmak <xref:System.Runtime.Serialization.DataContractSerializer> önemli bir adımdır. Oluşturma işleminden sonra ayarları değiştiremezsiniz.  
  
### <a name="specifying-the-root-type"></a>Kök türünü belirtme  
 *Kök türü* , örnekleri seri hale getirilen veya seri durumdan çıkarılan türüdür. <xref:System.Runtime.Serialization.DataContractSerializer>Birçok Oluşturucu aşırı yüküne sahiptir, ancak en azından, parametresi kullanılarak bir kök türü sağlanmalıdır `type` .  
  
 Belirli bir kök türü için oluşturulan serileştirici, tür kök türünden türetilmediği takdirde, başka bir türü seri hale getirmek (veya serisini kaldırmak) için kullanılamaz. Aşağıdaki örnekte iki sınıf gösterilmektedir.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#1)]
 [!code-vb[c_StandaloneDataContractSerializer#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#1)]  
  
 Bu kod, `DataContractSerializer` yalnızca sınıfının örneklerini seri hale getirmek veya seri durumdan çıkarmak için kullanılabilen bir örneğini oluşturur `Person` .  
  
 [!code-csharp[c_StandaloneDataContractSerializer#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#2)]
 [!code-vb[c_StandaloneDataContractSerializer#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#2)]  
  
### <a name="specifying-known-types"></a>Bilinen türleri belirtme  
 Bir çok biçimlilik, seri hale getirilen <xref:System.Runtime.Serialization.KnownTypeAttribute> veya başka bir mekanizmayla işlenmemiş olan türlere dahilse, olası bilinen türlerin bir listesi parametresi kullanılarak seri hale getirici oluşturucusuna geçirilmelidir `knownTypes` . Bilinen türler hakkında daha fazla bilgi için bkz. [veri sözleşmesi bilinen türler](data-contract-known-types.md).  
  
 Aşağıdaki örnek, belirli bir türünün bir `LibraryPatron` koleksiyonunu içeren sınıfını gösterir, `LibraryItem` . İkinci sınıf `LibraryItem` türü tanımlar. Üçüncü ve dört Sınıf ( `Book` ve `Newspaper` ) `LibraryItem` sınıfından devralınır.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#3)]  
 [!code-vb[c_StandaloneDataContractSerializer#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#3)]  
  
 Aşağıdaki kod, parametresini kullanarak seri hale getirici örneğini oluşturur `knownTypes` .  
  
 [!code-csharp[c_StandaloneDataContractSerializer#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#4)]
 [!code-vb[c_StandaloneDataContractSerializer#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#4)]  
  
### <a name="specifying-the-default-root-name-and-namespace"></a>Varsayılan kök adı ve ad alanını belirtme  
 Normalde, bir nesne serileştirildiğinde, en dıştaki XML öğesinin varsayılan adı ve ad alanı veri sözleşmesinin adı ve ad alanına göre belirlenir. Tüm iç öğelerin adları, veri üyesi adlarından belirlenir ve ad alanı veri sözleşmesinin ad alanıdır. Aşağıdaki örnek, `Name` `Namespace` ve sınıflarının oluşturucularında ve değerlerini ayarlar <xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.Runtime.Serialization.DataMemberAttribute> .  
  
 [!code-csharp[c_StandaloneDataContractSerializer#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#5)]
 [!code-vb[c_StandaloneDataContractSerializer#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#5)]  
  
 Sınıfının bir örneğini seri hale `Person` getirmek aşağıdakine benzer BIR XML üretir.  
  
```xml  
<PersonContract xmlns="http://schemas.contoso.com">  
  <AddressMember>  
    <StreetMember>123 Main Street</StreetMember>  
   </AddressMember>  
</PersonContract>  
```  
  
 Ancak, ve parametrelerinin değerlerini oluşturucuya geçirerek kök öğenin varsayılan adını ve ad alanını özelleştirebilirsiniz `rootName` `rootNamespace` <xref:System.Runtime.Serialization.DataContractSerializer> . `rootNamespace`Öğesinin, veri üyelerine karşılık gelen içerilen öğelerin ad alanını etkilemediğini unutmayın. Yalnızca en dıştaki öğenin ad alanını etkiler.  
  
 Bu değerler <xref:System.Xml.XmlDictionaryString> , IKILI XML biçimi kullanılarak en iyi duruma getirilmesini sağlamak için sınıfın dizeleri veya örnekleri olarak geçirilebilir.  
  
### <a name="setting-the-maximum-objects-quota"></a>En fazla nesne kotasını ayarlama  
 Bazı `DataContractSerializer` Oluşturucu aşırı yüklemeleri bir `maxItemsInObjectGraph` parametreye sahip. Bu parametre, seri hale getirici tarafından seri hale getirilen veya seri hale getirilen en fazla nesne sayısını, tek bir <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> Yöntem çağrısında belirler. (Yöntem her zaman bir kök nesneyi okur, ancak bu nesnenin veri üyelerinde başka nesneleri olabilir. Bu nesneler başka nesneler içerebilir ve bu şekilde devam eder.) Varsayılan değer 65536 ' dir. Dizileri serileştirmek veya seri durumdan çıkarma sırasında her dizi girişinin ayrı bir nesne olarak sayımlarını unutmayın. Ayrıca, bazı nesnelerin büyük bir bellek temsili olabileceğini ve bu kotanın tek başına hizmet reddi saldırısını engellemek için yeterli olamayacağını unutmayın. Daha fazla bilgi için bkz. [veriler Için güvenlik konuları](security-considerations-for-data.md). Bu kotayı varsayılan değerin ötesinde artırmanız gerekiyorsa, bunu hem gönderme (serileştirme) hem de alma (serisini kaldırma) tarafında yapmak önemlidir çünkü her ikisi de verileri okurken ve yazarken geçerlidir.  
  
### <a name="round-trips"></a>Gidiş dönüşler  
 Bir nesne seri durumdan çıkarılmışsa ve bir işlemde yeniden serileştirildiğinde *gidiş dönüş* oluşur. Bu nedenle, XML 'den bir nesne örneğine gider ve bir XML akışına geri döner.  
  
 Bazı `DataContractSerializer` Oluşturucu aşırı yüklemeleri `ignoreExtensionDataObject` , varsayılan olarak olarak ayarlanmış bir parametreye sahiptir `false` . Bu varsayılan modda, veri sözleşmesi arabirimi uyguladığı sürece veriler, daha eski bir sürüm aracılığıyla bir veri sözleşmesinin daha yeni bir sürümüne, kayıp olmadan daha yeni sürüme geri gönderilebilir <xref:System.Runtime.Serialization.IExtensibleDataObject> . Örneğin, veri sözleşmesinin sürüm 1 ' i `Person` `Name` ve veri üyelerini içerdiğini varsayın `PhoneNumber` ve sürüm 2 bir `Nickname` üye ekler. `IExtensibleDataObject`Uygulanmışsa, sürüm 2 ' den sürüm 1 ' e bilgi gönderirken `Nickname` veriler depolanır ve sonra veriler tekrar serileştirildiğinde yeniden oluşturulur; bu nedenle, gidiş yolculuğuna hiçbir veri kaybolmaz. Daha fazla bilgi için bkz. [Ileri uyumlu veri sözleşmeleri](forward-compatible-data-contracts.md) ve [veri sözleşmesi sürümü oluşturma](data-contract-versioning.md).  
  
#### <a name="security-and-schema-validity-concerns-with-round-trips"></a>Güvenlik ve şema geçerliliği gidiş dönüşlerle Ilgilidir  
 Gidiş dönüşlerin güvenliği olumsuz etkileyebilir. Örneğin, büyük miktarlarda gereksiz verileri seri durumdan çıkarmak ve depolamak bir güvenlik riski oluşturabilir. Özellikle dijital imzalar dahil edilmişse, bu verileri doğrulamak için bir yol olmadığı konusunda güvenlik sorunları olabilir. Örneğin, önceki senaryoda sürüm 1 uç noktası `Nickname` kötü amaçlı veriler içeren bir değeri imzalamada olabilir. Son olarak, şema geçerliliği sorunları olabilir: bir uç nokta, belirtilen sözleşmeye tamamen bağlı olan ve ek değer içermeyen verileri her zaman göstermek isteyebilir. Önceki örnekte, sürüm 1 uç noktasının sözleşmesi yalnızca ve olduğunu söyler `Name` `PhoneNumber` ve şema doğrulamasının kullanılıyorsa, ek değerin yaymasının `Nickname` başarısız olmasına neden olur.  
  
#### <a name="enabling-and-disabling-round-trips"></a>Gidiş dönüşleri etkinleştirme ve devre dışı bırakma  
 Gidiş dönüşlerin devre dışı bırakmak için <xref:System.Runtime.Serialization.IExtensibleDataObject> arabirimi uygulamayın. Türler üzerinde denetiminiz yoksa, `ignoreExtensionDataObject` parametresini `true` aynı etkiyi elde etmek için olarak ayarlayın.  
  
### <a name="object-graph-preservation"></a>Nesne grafiği koruması  
 Normal olarak, seri hale getirici aşağıdaki kodda olduğu gibi nesne kimliğiyle ilgilenmez.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#6)]
 [!code-vb[c_StandaloneDataContractSerializer#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#6)]  
  
 Aşağıdaki kod bir satınalma siparişi oluşturur.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#7)]
 [!code-vb[c_StandaloneDataContractSerializer#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#7)]  
  
 `billTo`Ve `shipTo` alanlarının aynı nesne örneğine ayarlandığına dikkat edin. Ancak oluşturulan XML, bilgilerin yinelenenleri yinelemeyor ve aşağıdaki XML 'e benzer şekilde görünür.  
  
```xml  
<PurchaseOrder>  
  <billTo><street>123 Main St.</street></billTo>  
  <shipTo><street>123 Main St.</street></shipTo>  
</PurchaseOrder>  
```  
  
 Ancak, bu yaklaşım, istenmeyen olabilecek aşağıdaki özelliklere sahiptir:  
  
- Performans. Verilerin çoğaltılması verimsiz.  
  
- Döngüsel başvurular. Nesneler, diğer nesneler aracılığıyla bile kendilerine başvursa, çoğaltma tarafından serileştirilmesi sonsuz bir döngüye neden olur. (Bu durumda serileştirici bir oluşturur <xref:System.Runtime.Serialization.SerializationException> .)  
  
- İçeriyor. Bazen iki başvuruyu aynı nesneye ait olan ve iki özdeş nesne için değil, bu olguyu korumak önemlidir.  
  
 Bu nedenlerden dolayı, bazı `DataContractSerializer` Oluşturucu aşırı yüklemeleri bir `preserveObjectReferences` parametreye sahiptir (varsayılan olarak `false` ). Bu parametre olarak ayarlandığında `true` , yalnızca WCF 'nin anladığı nesne başvurularını kodlamaya yönelik özel bir yöntem kullanılır. Olarak ayarlandığında `true` , XML kodu örneği şimdi aşağıdakine benzer.  
  
```xml  
<PurchaseOrder ser:id="1">  
  <billTo ser:id="2"><street ser:id="3">123 Main St.</street></billTo>  
  <shipTo ser:ref="2"/>  
</PurchaseOrder>  
```  
  
 "Ser" ad alanı, standart serileştirme ad alanını ifade eder `http://schemas.microsoft.com/2003/10/Serialization/` . Her veri parçası yalnızca bir kez serileştirilir ve KIMLIK numarası verilir ve sonraki kullanımlar, zaten serileştirilmiş veriler için bir başvuruya neden olur.  
  
> [!IMPORTANT]
> Veri sözleşmesinde hem "kimlik" hem de "ref" öznitelikleri varsa `XMLElement` , "ref" özniteliği kabul edilir ve "id" özniteliği yok sayılır.  
  
 Bu modun sınırlamalarını anlamak önemlidir:  
  
- `DataContractSerializer`Tarafından AYARLANDıĞı XML, `preserveObjectReferences` `true` diğer teknolojilerle birlikte kullanılamaz ve yalnızca başka bir örnek tarafından `DataContractSerializer` , `preserveObjectReferences` olarak ayarlanmış olarak erişilebilir `true` .  
  
- Bu özellik için meta veri (şema) desteği yok. Oluşturulan şema yalnızca, `preserveObjectReferences` olarak ayarlandığında geçerlidir `false` .  
  
- Bu özellik serileştirme ve seri durumdan çıkarma işleminin daha yavaş çalışmasına neden olabilir. Verilerin çoğaltılması gerekmese de, bu modda ek nesne karşılaştırmalarının gerçekleştirilmesi gerekir.  
  
> [!CAUTION]
> `preserveObjectReferences`Mod etkinleştirildiğinde, özellikle `maxItemsInObjectGraph` doğru kotanın değeri ayarlamanız önemlidir. Dizilerin bu modda işlenme yöntemi nedeniyle, bir saldırganın büyük bellek tüketimine yalnızca kotayla sınırlı olan küçük bir kötü amaçlı ileti oluşturmasıyla kolay bir durum oluşturur `maxItemsInObjectGraph` .  
  
### <a name="specifying-a-data-contract-surrogate"></a>Veri anlaşması yedeği belirtme  
 Bazı `DataContractSerializer` Oluşturucu aşırı yüklemeleri `dataContractSurrogate` , olarak ayarlanmış olabilecek bir parametreye sahiptir `null` . Aksi takdirde, arabirimini uygulayan bir tür olan bir *veri anlaşması yedeği*belirtmek için bunu kullanabilirsiniz <xref:System.Runtime.Serialization.IDataContractSurrogate> . Daha sonra, serileştirme ve seri kaldırma işlemini özelleştirmek için arabirimini kullanabilirsiniz. Daha fazla bilgi için bkz. [veri sözleşmesi yedeklerin kapıları](../extending/data-contract-surrogates.md).  
  
## <a name="serialization"></a>Serileştirme  
 Aşağıdaki bilgiler, <xref:System.Runtime.Serialization.XmlObjectSerializer> ve sınıfları dahil, öğesinden devralan tüm sınıflar için geçerlidir <xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Runtime.Serialization.NetDataContractSerializer> .  
  
### <a name="simple-serialization"></a>Basit serileştirme  
 Bir nesneyi seri hale getirmenin en temel yolu yöntemine geçirmektir <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObject%2A> . Her biri, bir veya ' a yazmak için üç aşırı yükleme vardır <xref:System.IO.Stream> <xref:System.Xml.XmlWriter> <xref:System.Xml.XmlDictionaryWriter> . <xref:System.IO.Stream>Aşırı yüklemede, ÇıKTı UTF-8 KODLAMASıNDA XML 'dir. <xref:System.Xml.XmlDictionaryWriter>Aşırı yükleme ile serileştirici, IKILI XML için çıkışını en iyi duruma getirir.  
  
 <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObject%2A>Yöntemi kullanılırken, serileştirici sarmalayıcı öğesi için varsayılan ad ve ad alanını kullanır ve içeriği (varsayılan kök adı ve ad alanını belirtme "bölümüne bakın).  
  
 Aşağıdaki örnek, ile yazmayı gösterir <xref:System.Xml.XmlDictionaryWriter> .  
  
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
 <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteStartObject%2A> <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObjectContent%2A> <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteEndObject%2A> Son öğesini yazmak, nesne içeriğini yazmak ve sarmalayıcı öğesini sırasıyla kapatmak için,, ve yöntemlerini kullanın.  
  
> [!NOTE]
> <xref:System.IO.Stream>Bu yöntemlerin aşırı yüklemesi yoktur.  
  
 Bu adım adım serileştirme iki ortak kullanımı vardır. Bunlardan biri `WriteStartObject` `WriteObjectContent` , aşağıdaki örnekte gösterildiği gibi, ve arasında öznitelikler veya açıklamalar gibi içerikler eklemedir.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#9)]
 [!code-vb[c_StandaloneDataContractSerializer#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#9)]  
  
 Bu, aşağıdakine benzer bir XML üretir.  
  
```xml  
<Person serializedBy="myCode">  
  <Name>Jay Hamlin</Name>  
  <Address>123 Main St.</Address>  
</Person>  
```  
  
 Aşağıdaki kodda gösterildiği gibi, başka bir yaygın kullanım <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteStartObject%2A> <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteEndObject%2A> , ve tamamen kullanmaktan ve kendi özel sarmalayıcı öğesini yazmak (ya da sarmalayıcı yazmanın tamamen atlanmak).  
  
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
 Aşağıdaki bilgiler, <xref:System.Runtime.Serialization.XmlObjectSerializer> ve sınıfları dahil, öğesinden devralan tüm sınıflar için geçerlidir <xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Runtime.Serialization.NetDataContractSerializer> .  
  
 Bir nesneyi seri durumdan çıkarmak için en temel yol, yöntem aşırı yüklerinden birini çağırmanız olur <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> . Her biri, bir veya bir ile okumak için üç aşırı yükleme vardır <xref:System.Xml.XmlDictionaryReader> `XmlReader` `Stream` . `Stream`Aşırı yüklemenin <xref:System.Xml.XmlDictionaryReader> hiçbir kota tarafından korunmayan bir metin oluşturduğunu ve yalnızca güvenilen verileri okumak için kullanılması gerektiğini unutmayın.  
  
 Ayrıca, `ReadObject` yöntemin döndürdüğü nesnenin uygun türe dönüştürülmesi gerektiğini unutmayın.  
  
 Aşağıdaki kod, ve ' ın bir örneğini oluşturur <xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Xml.XmlDictionaryReader> , sonra bir örneği serileştirir `Person` .  
  
 [!code-csharp[c_StandaloneDataContractSerializer#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#11)]
 [!code-vb[c_StandaloneDataContractSerializer#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#11)]  
  
 Yöntemini çağırmadan önce <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> sarmalayıcı öğesine veya sarmalayıcı öğesinden önce gelen içerik olmayan bir DÜĞÜME XML okuyucuyu konumlandırın. Bunu, <xref:System.Xml.XmlReader.Read%2A> <xref:System.Xml.XmlReader> veya türetmesinin yöntemini çağırarak ve <xref:System.Xml.XmlReader.NodeType%2A> öğesini aşağıdaki kodda gösterildiği gibi test ederek yapabilirsiniz.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#12)]
 [!code-vb[c_StandaloneDataContractSerializer#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#12)]  
  
 Okuyucuyu öğesine teslim etmeden önce bu sarmalayıcı öğesinde öznitelikleri okuyabileceğinizi unutmayın `ReadObject` .  
  
 Basit aşırı yüklerden birini kullanırken `ReadObject` , seri hale getirici sarmalayıcı öğesinde varsayılan adı ve ad alanını arar ("varsayılan kök adı ve ad alanını belirtme" kısmına bakın) ve bilinmeyen bir öğe bulursa bir özel durum oluşturur. Önceki örnekte `<Person>` sarmalayıcı öğesi beklenmektedir. <xref:System.Runtime.Serialization.XmlObjectSerializer.IsStartObject%2A>Yöntemi, okuyucunun beklenen olarak adlandırılan bir öğede konumlandığını doğrulamak için çağrılır.  
  
 Bu sarmalayıcı öğe adı denetimini devre dışı bırakmak için bir yol vardır; metodun bazı aşırı yüklemeleri `ReadObject` `verifyObjectName` , varsayılan olarak olarak ayarlanan Boolean parametresini alır `true` . Olarak ayarlandığında `false` , sarmalayıcı öğesinin adı ve ad alanı yok sayılır. Bu, daha önce açıklanan adım adım serileştirme mekanizması kullanılarak yazılmış XML 'yi okumak için yararlıdır.  
  
## <a name="using-the-netdatacontractserializer"></a>NetDataContractSerializer kullanma  
 Ve arasındaki birincil fark, `DataContractSerializer` <xref:System.Runtime.Serialization.NetDataContractSerializer> `DataContractSerializer` veri anlaşması adlarını kullanır, ancak `NetDataContractSerializer` çıktılar tam .NET Framework derleme ve serileştirilmiş XML içinde tür adlarıdır. Bu, tam olarak aynı türlerin serileştirme ve seri kaldırma uç noktaları arasında paylaşılması gerektiği anlamına gelir. Bu, `NetDataContractSerializer` seri durumdan çıkarılacak kesin türler her zaman bilindiğinden, bilinen türler mekanizmasının ile gerekmediği anlamına gelir.  
  
 Bununla birlikte, çeşitli sorunlar meydana gelebilir:  
  
- Güvenlik'i seçin. Seri durumdan çıkarılan XML 'de bulunan herhangi bir tür yüklenir. Kötü amaçlı türlerin yüklenmesine zorlamak için bu açıktan yararlanılabilir. ' Nin `NetDataContractSerializer` Güvenilmeyen verilerle kullanılması yalnızca bir *serileştirme Bağlayıcısı* kullanılıyorsa ( <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder%2A> özellik veya Oluşturucu parametresi kullanılarak) yapılmalıdır. Bağlayıcı yalnızca güvenli türlerin yüklenmesine izin verir. Ciltçi mekanizması, ad alanı kullanan bir tür ile aynıdır <xref:System.Runtime.Serialization> .  
  
- Sürümü. XML 'de tam tür ve derleme adlarının kullanılması, türlerin nasıl sürümlendirilemez olduğunu önemli ölçüde kısıtlar. Aşağıdakiler değiştirilemez: tür adları, ad alanları, derleme adları ve derleme sürümleri. <xref:System.Runtime.Serialization.NetDataContractSerializer.AssemblyFormat%2A>Özellik veya Oluşturucu parametresinin <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle.Simple> varsayılan değeri yerine olarak ayarlanması <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle.Full> , derleme sürümü değişikliklerine izin verir, ancak genel parametre türleri için kullanılamaz.  
  
- Birlikte çalışabilirlik. .NET Framework türü ve derleme adları XML 'ye eklendiğinden, .NET Framework dışındaki platformlar elde edilen verilere erişemez.  
  
- Performans. Tür ve derleme adlarının yazılması, sonuçta elde edilen XML 'in boyutunu önemli ölçüde artırır.  
  
 Bu mekanizma, .NET Framework uzaktan iletişim tarafından kullanılan ikili veya SOAP serileştirmesine benzer (özellikle, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> ve <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> ).  
  
 `NetDataContractSerializer`' Nin kullanımı, `DataContractSerializer` aşağıdaki farklılıklarla ile benzerdir:  
  
- Oluşturucular için bir kök türü belirtmeniz gerekmez. Aynı örneği ile herhangi bir türü seri hale getirebilirsiniz `NetDataContractSerializer` .  
  
- Oluşturucular bilinen türlerin bir listesini kabul etmez. Tür adları XML içine serileştirildiğinde bilinen türler mekanizması gereksizdir.  
  
- Oluşturucular, bir veri sözleşmesi yedeği kabul etmez. Bunun yerine, adlı bir <xref:System.Runtime.Serialization.ISurrogateSelector> parametresini kabul ederler `surrogateSelector` (özelliği ile eşlenir <xref:System.Runtime.Serialization.NetDataContractSerializer.SurrogateSelector%2A> ). Bu, eski bir vekil mekanizmasıdır.  
  
- Oluşturucular, özelliği ile eşleşen bir parametresini kabul eder `assemblyFormat` <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle> <xref:System.Runtime.Serialization.NetDataContractSerializer.AssemblyFormat%2A> . Daha önce anlatıldığı gibi, bu, serileştiricinin sürüm oluşturma yeteneklerini geliştirmek için kullanılabilir. Bu, <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle> ikili veya SOAP serileştirme içindeki mekanizmaya eşdeğerdir.  
  
- Oluşturucular, <xref:System.Runtime.Serialization.StreamingContext> özelliği ile eşleşen adlı bir parametre kabul eder `context` <xref:System.Runtime.Serialization.NetDataContractSerializer.Context%2A> . Bunu, serileştirilmiş olan türlere bilgi geçirmek için kullanabilirsiniz. Bu kullanım, <xref:System.Runtime.Serialization.StreamingContext> diğer sınıflarda kullanılan mekanizmaya benzer <xref:System.Runtime.Serialization> .  
  
- Ve yöntemleri, <xref:System.Runtime.Serialization.NetDataContractSerializer.Serialize%2A> <xref:System.Runtime.Serialization.NetDataContractSerializer.Deserialize%2A> ve yöntemleri için diğer adlardır <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObject%2A> <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> . Bunlar, ikili veya SOAP serileştirmesi ile daha tutarlı bir programlama modeli sağlamak için mevcuttur.  
  
 Bu özellikler hakkında daha fazla bilgi için bkz. [Ikili serileştirme](../../../standard/serialization/binary-serialization.md).  
  
 `NetDataContractSerializer`Ve kullanan XML biçimleri `DataContractSerializer` normalde uyumlu değildir. Diğer bir deyişle, bu serileştiricilerin biriyle Serileştirmeye çalışılması ve diğeri ile seri durumdan çıkarma desteklenen bir senaryo değildir.  
  
 Ayrıca, `NetDataContractSerializer` nesnesinin, nesne grafiğindeki her bir düğüm için tam .NET Framework türü ve derleme adını çıkmadığını unutmayın. Bu bilgiler yalnızca belirsiz olduğunda çıktı verir. Yani, kök nesne düzeyinde ve çok biçimli durumlar için çıkış yapılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.NetDataContractSerializer>
- <xref:System.Runtime.Serialization.XmlObjectSerializer>
- [İkili serileştirme](../../../standard/serialization/binary-serialization.md)
- [Veri Sözleşmesi Seri Hale Getirici Tarafından Desteklenen Türler](types-supported-by-the-data-contract-serializer.md)
