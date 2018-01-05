---
title: "Seri Hale Getirme ve Seri Durumdan Çıkarma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 3d71814c-bda7-424b-85b7-15084ff9377a
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a73fa30f1ebae805abd6f3e7e397d005d5b7130d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="serialization-and-deserialization"></a>Seri Hale Getirme ve Seri Durumdan Çıkarma
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]Yeni bir seri hale getirme altyapısı içeren <xref:System.Runtime.Serialization.DataContractSerializer>. <xref:System.Runtime.Serialization.DataContractSerializer> Arasında çevirir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] nesneleri ve her iki yönde XML. Bu konu, seri hale getirici nasıl çalıştığını açıklar.  
  
 Serileştirilirken [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] nesneleri seri hale getirici anlar serileştirme programlama modelleri, yeni dahil olmak üzere çeşitli *veri sözleşmesi* modeli. Desteklenen türlerinin tam listesi için bkz: [veri sözleşmesi seri hale getirici tarafından desteklenen türleri](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md). Veri sözleşmeleri giriş için bkz: [kullanarak veri sözleşmeleri](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
 XML çıkarılırken seri hale getirici kullanan <xref:System.Xml.XmlReader> ve <xref:System.Xml.XmlWriter> sınıfları. Ayrıca destekler <xref:System.Xml.XmlDictionaryReader> ve <xref:System.Xml.XmlDictionaryWriter> üretmek etkinleştirmek üzere sınıfları XML gibi bazı durumlarda, iyileştirilmiş kullanırken [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ikili XML biçimi.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Ayrıca bir yardımcı serileştirici içerir <xref:System.Runtime.Serialization.NetDataContractSerializer>. <xref:System.Runtime.Serialization.NetDataContractSerializer> Benzer <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> ve <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> serileştiricileri ayrıca yayar çünkü [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] adları serileştirilmiş veriler bir parçası olarak yazın. Seri hale getirme ve seri durumdan çıkarmak uçları aynı türlerini paylaşılan olduğunda kullanılır. Hem <xref:System.Runtime.Serialization.DataContractSerializer> ve <xref:System.Runtime.Serialization.NetDataContractSerializer> ortak bir taban sınıftan türetilen <xref:System.Runtime.Serialization.XmlObjectSerializer>.  
  
> [!WARNING]
>  <xref:System.Runtime.Serialization.DataContractSerializer> 20 XML varlıkları olarak aşağıda onaltılık bir değerle denetim karakterleri içeren bir dize serileştirir. Bu tür veriler bir WCF hizmetine gönderirken bu olmayan WCF istemcisi ile ilgili bir sorun neden olabilir.  
  
## <a name="creating-a-datacontractserializer-instance"></a>DataContractSerializer örneği oluşturma  
 Örneği oluşturma <xref:System.Runtime.Serialization.DataContractSerializer> önemli bir adımdır. Yapım sonra ayarlardan herhangi birini değiştiremezsiniz.  
  
### <a name="specifying-the-root-type"></a>Kök türünü belirtme  
 *Kök türü* hangisinin örnekleri serileştirilecek veya serisi türüdür. <xref:System.Runtime.Serialization.DataContractSerializer> Birçok Oluşturucusu aşırı yüklemeye sahip, ancak, en azından kullanarak kök türü sağlanmalıdır `type` parametresi.  
  
 Başka bir türüne seri (veya seri durumdan çıkarmak için) belirli bir kök türü kullanılamaz için oluşturulan bir seri hale getirici türü kök türden türetilmiş sürece. Aşağıdaki örnekte, iki sınıf gösterir.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#1)]
 [!code-vb[c_StandaloneDataContractSerializer#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#1)]  
  
 Bu kod örneğini oluşturur `DataContractSerializer` yalnızca serileştirmek veya seri durumdan örnekleri için kullanılabilir `Person` sınıfı.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#2)]
 [!code-vb[c_StandaloneDataContractSerializer#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#2)]  
  
### <a name="specifying-known-types"></a>Bilinen türlerini belirtme  
 Çok biçimlilik kullanarak zaten işlenmiyor serileştirilen türleri söz konusu ise, <xref:System.Runtime.Serialization.KnownTypeAttribute> özniteliği veya başka bir mekanizma, olası bilinen türlerinin bir listesini gerekir bayraklarıdır seri hale getirici'nın oluşturucuya kullanarak `knownTypes` parametresi. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]bilinen türlerini, bkz: [veri sözleşmesi bilinen türleri](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
 Aşağıdaki örnek, bir sınıfı gösterir `LibraryPatron`, belirli bir türde bir koleksiyonu içeren `LibraryItem`. İkinci sınıfı tanımlayan `LibraryItem` türü. Üçüncü ve dördüncü sınıfları (`Book` ve `Newspaper`) devralınmalıdır `LibraryItem` sınıfı.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#3)]  
 [!code-vb[c_StandaloneDataContractSerializer#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#3)]  
  
 Aşağıdaki kodu kullanarak seri hale getirici örneğini oluşturur `knownTypes` parametresi.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#4)]
 [!code-vb[c_StandaloneDataContractSerializer#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#4)]  
  
### <a name="specifying-the-default-root-name-and-namespace"></a>Varsayılan kök adı ve Namespace belirtme  
 Bir nesne seri, normalde, varsayılan adı ve en dıştaki XML öğesinin ad alanı, ad alanı ve veri sözleşme adına göre belirlenir. Tüm iç öğelerinin adlarını veri üyesi adlarından belirlenir ve kendi ad alanı veri sözleşmenin ad alanıdır. Aşağıdaki örnek kümeleri `Name` ve `Namespace` değerleri Yapıcılardaki <xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> sınıfları.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#5)]
 [!code-vb[c_StandaloneDataContractSerializer#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#5)]  
  
 Örneğini serileştirmek `Person` sınıfı XML aşağıdakine benzer üretir.  
  
```xml  
<PersonContract xmlns="http://schemas.contoso.com">  
  <AddressMember>  
    <StreetMember>123 Main Street</StreetMember>  
   </AddressMember>  
</PersonContract>  
```  
  
 Ancak, varsayılan adı ve kök öğesinin ad alanı değerlerini geçirerek özelleştirebileceğiniz `rootName` ve `rootNamespace` parametreleri <xref:System.Runtime.Serialization.DataContractSerializer> Oluşturucusu. Unutmayın `rootNamespace` veri üyelerine karşılık içerilen öğelerin ad etkilemez. Yalnızca en dıştaki öğesinin ad alanı etkiler.  
  
 Bu değerleri dizeler veya örnekleri geçirilen <xref:System.Xml.XmlDictionaryString> ikili XML biçimi kullanarak kendi iyileştirme için izin veren sınıfı.  
  
### <a name="setting-the-maximum-objects-quota"></a>En büyük nesneleri kotası ayarlama  
 Bazı `DataContractSerializer` Oluşturucusu aşırı yüklü bir `maxItemsInObjectGraph` parametresi. Bu parametre, seri hale getirici serileştiren veya tek bir seri durumdan çıkarır nesne sayısını belirler <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> yöntem çağrısı. (Yöntemi her zaman bir kök nesnesi okur, ancak bu nesne veri üyeleri başka nesneler olabilir. Bu nesneler diğer nesneleri vb.) 65536 varsayılandır. Seri hale getirme veya diziler seri durumdan çıkarılırken, her dizi girişi ayrı bir nesne sayar unutmayın. Ayrıca, bazı nesneler büyük bellek gösterimi olabilir ve bu nedenle bu kota tek başına bir hizmet reddi saldırısına önlemek yeterli olmayabilir unutmayın. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Veriler için güvenlik konuları](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md). Varsayılan değerin dışında bu kotayı artırmak gerekiyorsa, bunu gönderen (seri hale getirme) ve hem için verileri okurken ve yazarken uygulandığından (seri durumdan) kenara alma üzerinde yapmak önemlidir.  
  
### <a name="round-trips"></a>Gidiş dönüş  
 A *gidiş dönüş* bir nesne seri durumdan ve tek bir işlemde yeniden seri oluşur. Bu nedenle, XML'den bir nesne örneği ve geri için yeniden bir XML akışı gidiyor.  
  
 Bazı `DataContractSerializer` Oluşturucusu aşırı yüklü bir `ignoreExtensionDataObject` ayarlamak için parametre `false` varsayılan olarak. Implements veri sözleşmesi sürece bu varsayılan modda veri gidiş dönüş üzerinde bir veri sözleşmesi bir eski sürümü ve geri aracılığıyla daha yeni bir sürümünde kaybı olmadan daha yeni sürümüne gönderilebilir <xref:System.Runtime.Serialization.IExtensibleDataObject> arabirimi. Örneğin, 1. sürümü varsayalım `Person` veri sözleşmesi içeren `Name` ve `PhoneNumber` veri üyeleri ve sürüm 2 ekler bir `Nickname` üye. Varsa `IExtensibleDataObject` bilgi sürüm 1, sürüm 2 gönderirken uygulanır `Nickname` veriler depolanır ve verileri yeniden serileştirildiğinde yeniden yayılan; bu nedenle, hiçbir veri gidiş dönüş kaybolur. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][İleri uyumlu veri sözleşmeleri](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md) ve [veri sözleşmesi sürümü oluşturma](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md).  
  
#### <a name="security-and-schema-validity-concerns-with-round-trips"></a>Güvenlik ve gidiş dönüş ile şema geçerlilik sorunları  
 Gidiş dönüş güvenlik etkileri olabilir. Örneğin, seri durumdan ve büyük miktarlarda yabancı veri depolamak bir güvenlik riski olabilir. Özellikle dijital imzalar verilmemişse doğrulamak için hiçbir şekilde olduğunu bu verileri yeniden yayma ilgili güvenlik sorunları olabilir. Önceki senaryoda sürüm 1 endpoint örneğin oturum bir `Nickname` değeri kötü amaçlı veriler içerir. Son olarak, olabilir şema geçerlilik sorunları: bir uç nokta her zaman kesinlikle belirtilen sözleşmesi ve hiçbir ek değerler için eklenecek veri yayma isteyebilirsiniz. Önceki örnekte, yalnızca yayar sürüm 1 uç noktanın sözleşme diyor `Name` ve `PhoneNumber`ve şema doğrulaması kullanılıyorsa, ek yayma `Nickname` değeri doğrulama başarısız olmasına neden olur.  
  
#### <a name="enabling-and-disabling-round-trips"></a>Etkinleştirme ve gidiş dönüş devre dışı bırakma  
 Gidiş dönüş devre dışı bırakmak için uygulamayan <xref:System.Runtime.Serialization.IExtensibleDataObject> arabirimi. Türleri üzerinde hiçbir denetimi varsa ayarlamak `ignoreExtensionDataObject` parametresi `true` aynı sonucu elde etmek için.  
  
### <a name="object-graph-preservation"></a>Nesne grafiği koruma  
 Normalde, aşağıdaki kod olduğu gibi nesne kimliğine ilişkin seri hale getirici ilgilenmez.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#6)]
 [!code-vb[c_StandaloneDataContractSerializer#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#6)]  
  
 Aşağıdaki kod bir satın alma siparişi oluşturur.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#7)]
 [!code-vb[c_StandaloneDataContractSerializer#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#7)]  
  
 Dikkat `billTo` ve `shipTo` alanları aynı nesne örneğini ayarlayın. Ancak, oluşturulan XML çoğaltılan bilgiler çoğaltan ve aşağıdaki XML'e benzer.  
  
```xml  
<PurchaseOrder>  
  <billTo><street>123 Main St.</street></billTo>  
  <shipTo><street>123 Main St.</street></shipTo>  
</PurchaseOrder>  
```  
  
 Ancak, bu yaklaşım istenmeyen aşağıdaki özelliklere sahiptir:  
  
-   Performans. Veri çoğaltma verimli değildir.  
  
-   Döngüsel başvuru. Çoğaltma tarafından seri hale getirme nesnelerini kendileri için diğer nesnelerde bile başvurursanız sonsuz bir döngüde sonuçlanır. (Seri hale getirici oluşturur bir <xref:System.Runtime.Serialization.SerializationException> aşması durumunda.)  
  
-   Semantiği. Bazen aynı nesneye değil de iki aynı nesne iki başvuru olan olgu korumak önemlidir.  
  
 Bu nedenleri, bazı `DataContractSerializer` Oluşturucusu aşırı yüklü bir `preserveObjectReferences` parametresi (varsayılan `false`). Bu parametre ayarlandığında `true`, özel bir yöntem kodlama nesnesinin başvuruyor, hangi yalnızca [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bilir, kullanılır. Ayarlandığında `true`, XML kodu örneği şimdi aşağıdakine benzer.  
  
```xml  
<PurchaseOrder ser:id="1">  
  <billTo ser:id="2"><street ser:id="3">123 Main St.</street></billTo>  
  <shipTo ser:ref="2"/>  
</PurchaseOrder>  
```  
  
 "Ser" ad alanı standart seri hale getirme ad alanına başvuruyor http://schemas.microsoft.com/2003/10/Serialization/. Her veri parçası yalnızca bir kez serileştirilmiş ve bir kimlik numarası verilen ve zaten serileştirilmiş veriler için bir başvuru sonucu sonraki kullanır.  
  
> [!IMPORTANT]
>  Veri sözleşmesi "id" ve "ref" öznitelikleri varsa `XMLElement`, ardından "ref" özniteliği dikkate alınır ve "id" özniteliği yok sayılır.  
  
 Bu mod sınırlamaları anlamak önemlidir:  
  
-   XML `DataContractSerializer` ile üretir `preserveObjectReferences` kümesine `true` diğer teknolojilerle birlikte çalışabilir değildir ve yalnızca bir başkası tarafından erişilebilen `DataContractSerializer` örneği de `preserveObjectReferences` kümesine `true`.  
  
-   Bu özellik için meta veriler (şema) desteği yoktur. Üretilen şema bu durum yalnızca geçerli olduğunda `preserveObjectReferences` ayarlanır `false`.  
  
-   Bu özellik seri hale getirme ve seri durumdan çıkarma işleminin daha yavaş çalışmasına neden olabilir. Veri çoğaltılacak gerekmese de, fazladan nesne karşılaştırmaları bu modda gerçekleştirilmesi gerekir.  
  
> [!CAUTION]
>  Zaman `preserveObjectReferences` modu etkin olduğunda, ayarlamak özellikle önemlidir `maxItemsInObjectGraph` doğru kota değeri. Diziler, bu modda işlenir yöntemi nedeniyle, yalnızca sınırlı büyük bellek tüketimine küçük bir kötü amaçlı iletisini oluşturmak bir saldırgan daha kolay `maxItemsInObjectGraph` kota.  
  
### <a name="specifying-a-data-contract-surrogate"></a>Bir veri sözleşmesi yedek belirtme  
 Bazı `DataContractSerializer` Oluşturucusu aşırı yüklü bir `dataContractSurrogate` olarak ayarlanmış olabilir parametresi `null`. Belirtmek için kullanın Aksi halde, bir *veri sözleşmesi yedek*, uygulayan bir tür olduğu <xref:System.Runtime.Serialization.IDataContractSurrogate> arabirimi. Ardından, serileştirme özelleştirmek ve işlem seri durumundan çıkarma için arabirimi kullanabilirsiniz. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Veri sözleşmesi yedekleri](../../../../docs/framework/wcf/extending/data-contract-surrogates.md).  
  
## <a name="serialization"></a>Serileştirme  
 Aşağıdaki bilgiler devraldığı herhangi bir sınıf geçerlidir <xref:System.Runtime.Serialization.XmlObjectSerializer>dahil <xref:System.Runtime.Serialization.DataContractSerializer> ve <xref:System.Runtime.Serialization.NetDataContractSerializer> sınıfları.  
  
### <a name="simple-serialization"></a>Basit seri hale getirme  
 Bir nesneyi serileştirme en temel yolu için geçirmektir <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObject%2A> yöntemi. Her biri yazma için üç aşırı bir <xref:System.IO.Stream>, bir <xref:System.Xml.XmlWriter>, veya bir <xref:System.Xml.XmlDictionaryWriter>. İle <xref:System.IO.Stream> aşırı yüklemesi, çıktı, XML UTF-8 kodlaması. İle <xref:System.Xml.XmlDictionaryWriter> aşırı yüklemesi, seri hale getirici için ikili XML çıktısını iyileştirir.  
  
 Kullanırken <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObject%2A> yöntemi, seri hale getirici varsayılan adı ve ad alanı için sarmalayıcı öğesi kullanır ve (önceki "Belirterek varsayılan kök adı ve Namespace" bölümüne bakın) içeriği ile birlikte yazar.  
  
 Aşağıdaki örnek, yazma ile gösterir bir <xref:System.Xml.XmlDictionaryWriter>.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#8)]
 [!code-vb[c_StandaloneDataContractSerializer#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#8)]  
  
 Bu, aşağıdakine benzer XML oluşturur.  
  
```xml  
<Person>  
  <Name>Jay Hamlin</Name>  
  <Address>123 Main St.</Address>  
</Person>  
```  
  
### <a name="step-by-step-serialization"></a>Adım adım seri hale getirme  
 Kullanım <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteStartObject%2A>, <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObjectContent%2A>, ve <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteEndObject%2A> bir end öğesinin yazma yöntemleri nesne içeriğini yazmak ve kapsayıcı öğe sırasıyla kapatın.  
  
> [!NOTE]
>  Var olan hiçbir <xref:System.IO.Stream> aşırı dolayı bu yöntemleri.  
  
 Bu adım adım serileştirme iki ortak kullanımı vardır. Bir içeriği öznitelikleri gibi eklemektir veya arasında yorumları `WriteStartObject` ve `WriteObjectContent`, aşağıdaki örnekte gösterildiği gibi.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#9)]
 [!code-vb[c_StandaloneDataContractSerializer#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#9)]  
  
 Bu, aşağıdakine benzer XML oluşturur.  
  
```xml  
<Person serializedBy="myCode">  
  <Name>Jay Hamlin</Name>  
  <Address>123 Main St.</Address>  
</Person>  
```  
  
 Başka bir yaygın kullanım kullanarak kaçınmaktır <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteStartObject%2A> ve <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteEndObject%2A> tamamen ve kendi özel kapsayıcı öğe yazma (veya bir sarmalayıcı tamamen yazma bile atlamak için), aşağıdaki kodda gösterildiği gibi.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#10)]
 [!code-vb[c_StandaloneDataContractSerializer#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#10)]  
  
 Bu, aşağıdakine benzer XML oluşturur.  
  
```xml  
<MyCustomWrapper>  
  <Name>Jay Hamlin</Name>  
  <Address>123 Main St.</Address>  
</MyCustomWrapper>  
```  
  
> [!NOTE]
>  Adım adım serileştirme kullanarak şema geçersiz XML neden olabilir.  
  
## <a name="deserialization"></a>Seri durumdan çıkarma  
 Aşağıdaki bilgiler devraldığı herhangi bir sınıf geçerlidir <xref:System.Runtime.Serialization.XmlObjectSerializer>dahil <xref:System.Runtime.Serialization.DataContractSerializer> ve <xref:System.Runtime.Serialization.NetDataContractSerializer> sınıfları.  
  
 Nesne seri durumdan en temel yolu birini çağırmaktır <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> yöntemi aşırı. Her biri ile okumak için üç aşırı bir <xref:System.Xml.XmlDictionaryReader>, bir `XmlReader`, veya bir `Stream`. Unutmayın `Stream` aşırı oluşturur bir metinsel <xref:System.Xml.XmlDictionaryReader> tarafından hiçbir kota korumalı değil ve güvenilir veri salt okunur olarak kullanılmalıdır.  
  
 Ayrıca nesne `ReadObject` yöntemi döndürür gerekir uygun türe dönüştürülür.  
  
 Aşağıdaki kod örneğini oluşturur <xref:System.Runtime.Serialization.DataContractSerializer> ve bir <xref:System.Xml.XmlDictionaryReader>, ardından çıkarır bir `Person` örneği.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#11)]
 [!code-vb[c_StandaloneDataContractSerializer#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#11)]  
  
 Çağırmadan önce <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> yöntemi, XML okuyucusu sarmalayıcı öğede veya kapsayıcı öğe önündeki içeriği olmayan bir düğüm üzerindeki yerleştir. Bunu çağırarak yapmak <xref:System.Xml.XmlReader.Read%2A> yöntemi <xref:System.Xml.XmlReader> veya kendi türetme ve test <xref:System.Xml.XmlReader.NodeType%2A>aşağıdaki kodda gösterildiği gibi.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#12)]
 [!code-vb[c_StandaloneDataContractSerializer#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#12)]  
  
 Okuyucu için teslim etmeden önce bu sarmalayıcı öğesi özniteliklerini okuyabilir Not `ReadObject`.  
  
 Basit birini kullanırken `ReadObject` aşırı yüklemeleri, seri durumdan çıkarıcının arar sarmalayıcı öğede ad alanı ve varsayılan adı ("Belirterek varsayılan kök adı ve Namespace" kısmına bakın) ve bilinmeyen bulursa, bir özel durum oluşturur öğesi. Önceki örnekte `<Person>` sarmalayıcı öğesi bekleniyordu. <xref:System.Runtime.Serialization.XmlObjectSerializer.IsStartObject%2A> Yöntemi okuyucu beklendiği gibi adlı bir öğe üzerinde konumlandırılır doğrulamak için çağrılır.  
  
 Bu sarmalayıcı öğe adı denetimi devre dışı bırakmak için bir yolu yoktur; Bazı aşırı `ReadObject` yöntemi ele Boole parametresi `verifyObjectName`, ayarlanmış `true` varsayılan olarak. Ayarlandığında `false`, sarmalayıcı öğesinin ad alanı ve ad yoksayıldı. Bu, daha önce açıklanan adım adım seri hale getirme mekanizmasını kullanarak yazıldı XML okumak için kullanışlıdır.  
  
## <a name="using-the-netdatacontractserializer"></a>NetDataContractSerializer kullanma  
 Arasındaki birincil fark `DataContractSerializer` ve <xref:System.Runtime.Serialization.NetDataContractSerializer> olan `DataContractSerializer` veri sözleşmesi adları kullanır, ancak `NetDataContractSerializer` tam çıkarır [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] serileştirilmiş XML derleme ve tür adları. Başka bir deyişle, tam aynı türleri seri hale getirme ve seri durumdan çıkarma uç noktaları arasında paylaşılan gerekir. Bu bilinen türleri mekanizması ile gerekli olmadığı anlamına gelir `NetDataContractSerializer` seri durumdan çıkarılacak tam türleri her zaman bildiği.  
  
 Ancak, bazı sorunlar oluşabilir:  
  
-   Güvenlik. Seri durumdan çıkarılmakta XML dosyasında bulunan herhangi bir tür yüklenir. Bu kötü amaçlı türleri yüklenmesini zorlamak için yararlanılabilir. Kullanarak `NetDataContractSerializer` yalnızca veri'nin yapılması güvenilmeyen bir *seri hale getirme Bağlayıcısı* kullanılır (kullanarak <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder%2A> özelliği veya oluşturucusu parametresi). Cilt yalnızca güvenli türler yüklenmesine izin verir. Bağlayıcı mekanizmasıdır türlerini birine aynı <xref:System.Runtime.Serialization> ad alanı kullanın.  
  
-   Sürüm oluşturma. Tam tür ve derleme adları XML'de ciddi bir şekilde kullanarak nasıl türleri sürümlü olabilir kısıtlar. Aşağıdaki değiştirilemez: adları, ad alanları, derleme adları ve derleme sürümlerini yazın. Ayarı <xref:System.Runtime.Serialization.NetDataContractSerializer.AssemblyFormat%2A> özelliği veya oluşturucusu parametresi <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle.Simple> varsayılan değeri yerine <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle.Full> derleme sürüm değişiklikleri ancak genel parametre türleri için izin verir.  
  
-   Birlikte çalışabilirlik. Çünkü [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] türü ve derleme adları dahil edildiği XML, platformlar dışında [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] elde edilen verilere erişemez.  
  
-   Performans. Derleme ve türünü yazma önemli ölçüde artırır sonuç XML boyutunu adları.  
  
 Bu ikili veya tarafından kullanılan SOAP serileştirme için benzer bir mekanizmadır [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] remoting (özellikle <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> ve <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>).  
  
 Kullanarak `NetDataContractSerializer` kullanmaya benzer `DataContractSerializer`, aşağıdaki farklarla birlikte:  
  
-   Oluşturucular, kök türünü belirtmek gerektirmez. Aynı örneği ile herhangi bir türü serileştirebilen `NetDataContractSerializer`.  
  
-   Oluşturucular bilinen türlerinin bir listesini kabul etmez. Bilinen türler mekanizması tür adları XML'de serileştirilir ise gerekli değildir.  
  
-   Oluşturucular bir veri sözleşmesi yedek kabul etmez. Bunun yerine, kabul bir <xref:System.Runtime.Serialization.ISurrogateSelector> adlı bir parametreye `surrogateSelector` (hangi eşlendiğini <xref:System.Runtime.Serialization.NetDataContractSerializer.SurrogateSelector%2A> özelliği). Eski yedek mekanizması budur.  
  
-   Oluşturucular adlı bir parametre kabul `assemblyFormat` , <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle> eşlenen <xref:System.Runtime.Serialization.NetDataContractSerializer.AssemblyFormat%2A> özelliği. Daha önce açıklandığı gibi bu seri hale getirici sürüm oluşturma yeteneklerini geliştirmek için kullanılabilir. Bu aynıdır <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle> mekanizması ikili veya SOAP seri hale getirme.  
  
-   Oluşturucular kabul bir <xref:System.Runtime.Serialization.StreamingContext> adlı bir parametreye `context` eşlenen <xref:System.Runtime.Serialization.NetDataContractSerializer.Context%2A> özelliği. Bu bilgi serileştirilen türleriyle geçirmek için kullanabilirsiniz. Bu kullanım olarak aynıdır <xref:System.Runtime.Serialization.StreamingContext> diğer kullanılan mekanizma <xref:System.Runtime.Serialization> sınıfları.  
  
-   <xref:System.Runtime.Serialization.NetDataContractSerializer.Serialize%2A> Ve <xref:System.Runtime.Serialization.NetDataContractSerializer.Deserialize%2A> yöntemleridir için diğer adlar <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObject%2A> ve <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> yöntemleri. Bu ikili veya SOAP seri hale getirme ile daha tutarlı bir programlama modeli sağlamak için mevcut.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Bu özellikler bkz [ikili seri hale getirme](../../../../docs/standard/serialization/binary-serialization.md).  
  
 XML biçimleri `NetDataContractSerializer` ve `DataContractSerializer` kullanım normalde uyumlu değil. Diğer bir deyişle, bu serileştiricileri biri ile seri hale getirmek ve diğer seri durumdan çalışılıyor desteklenen bir senaryo değil.  
  
 Ayrıca, unutmayın `NetDataContractSerializer` tam çıkış değil [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] nesne grafikteki her düğüm için tür ve derleme adı. Bu bilgileri yalnızca belirsiz olduğu çıkarır. Diğer bir deyişle, kök nesne düzeyinde ve tüm biçimli durumlarda çıkarır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Runtime.Serialization.NetDataContractSerializer>  
 <xref:System.Runtime.Serialization.XmlObjectSerializer>  
 [İkili Serileştirme](../../../../docs/standard/serialization/binary-serialization.md)  
 [Veri Anlaşması Seri Hale Getirici Tarafından Desteklenen Türler](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)
