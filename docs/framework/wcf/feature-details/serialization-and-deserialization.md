---
title: Seri Hale Getirme ve Seri Durumdan Çıkarma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3d71814c-bda7-424b-85b7-15084ff9377a
ms.openlocfilehash: cf68834c5612ed51fb3e6c0ed18667cbc13482bc
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64586213"
---
# <a name="serialization-and-deserialization"></a>Seri Hale Getirme ve Seri Durumdan Çıkarma
Windows Communication Foundation (WCF) içeren yeni bir serileştirme motoruna <xref:System.Runtime.Serialization.DataContractSerializer>. <xref:System.Runtime.Serialization.DataContractSerializer> Arasında çevirir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] nesneleri ve her iki yönde de XML. Bu konu, seri hale getirici nasıl çalıştığını açıklar.  
  
 Serileştirilirken [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] nesneleri seri hale getirici anlayan serileştirme programlama modellerini, yeni dahil olmak üzere çeşitli *veri anlaşması* modeli. Desteklenen türler tam bir listesi için bkz. [veri sözleşme seri hale getirici tarafından desteklenen türleri](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md). Veri sözleşmeleri giriş için bkz: [kullanarak veri sözleşmeleri](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
 XML seri durumdan çıkarılırken zaman serileştiriciyi kullanır <xref:System.Xml.XmlReader> ve <xref:System.Xml.XmlWriter> sınıfları. Ayrıca destekler <xref:System.Xml.XmlDictionaryReader> ve <xref:System.Xml.XmlDictionaryWriter> sınıfları üretmek etkinleştirmek için en iyi duruma getirilmiş XML biçimi ne zaman WCF ikili XML kullanılarak gibi bazı durumlarda.  
  
 WCF özel seri hale getirici, ayrıca içerir <xref:System.Runtime.Serialization.NetDataContractSerializer>. <xref:System.Runtime.Serialization.NetDataContractSerializer> Benzer <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> ve <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> seri hale getiricileri genişletme de verir çünkü [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] adları serileştirilmiş veriler bir parçası olarak yazın. Aynı türler seri hale getirme ve seri durumdan çıkarılırken uçları paylaşıldığında kullanılır. Hem <xref:System.Runtime.Serialization.DataContractSerializer> ve <xref:System.Runtime.Serialization.NetDataContractSerializer> ortak temel sınıfından türetilir <xref:System.Runtime.Serialization.XmlObjectSerializer>.  
  
> [!WARNING]
>  <xref:System.Runtime.Serialization.DataContractSerializer> XML varlıklar olarak 20 aşağıda bir onaltılık değer ile denetim karakterlerini içeren bir dize serileştirir. Bu tür veriler için bir WCF Hizmeti gönderirken bu olmayan WCF istemcisi ile ilgili bir sorun neden olabilir.  
  
## <a name="creating-a-datacontractserializer-instance"></a>DataContractSerializer örneği oluşturma  
 Örneği oluşturmak <xref:System.Runtime.Serialization.DataContractSerializer> önemli bir adımdır. Yapı sonra ayarlardan herhangi birini değiştiremezsiniz.  
  
### <a name="specifying-the-root-type"></a>Kök türü belirtme  
 *Kök türü* hangi örnek serileştirilecek veya seri durumdan türü. <xref:System.Runtime.Serialization.DataContractSerializer> Birçok oluşturucu aşırı yüklemeleri vardır ancak kullanarak, en az bir kök türü sağlanmalı `type` parametresi.  
  
 Belirli bir kök türü başka bir tür (serileştirmek veya seri durumdan çıkarmak için) kullanılamaz için oluşturulan bir serileştirici tür kök türünden türetilmiş sürece. Aşağıdaki örnek, iki sınıf gösterir.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#1)]
 [!code-vb[c_StandaloneDataContractSerializer#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#1)]  
  
 Bu kod örneği oluşturur `DataContractSerializer` yalnızca serileştirmek veya seri durumdan örnekleri için kullanılabilir `Person` sınıfı.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#2)]
 [!code-vb[c_StandaloneDataContractSerializer#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#2)]  
  
### <a name="specifying-known-types"></a>Bilinen türleri belirtme  
 Çok biçimlilik kullanarak zaten işlenmiyor serileştirilmekte olan türler dahil edilmişse <xref:System.Runtime.Serialization.KnownTypeAttribute> özniteliği veya başka bir mekanizma, olası bilinen türlerinin bir listesini geçirilmelidir oluşturucuya seri hale getirici'nın kullanarak `knownTypes` parametresi. Bilinen türler hakkında daha fazla bilgi için bkz: [veri sözleşme bilinen türleri](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
 Aşağıdaki örnek, bir sınıfı gösterir `LibraryPatron`, belirli bir türdeki bir koleksiyon içeren `LibraryItem`. İkinci sınıfı tanımlar `LibraryItem` türü. Üçüncü ve dördüncü sınıfları (`Book` ve `Newspaper`) devralınacak `LibraryItem` sınıfı.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#3)]  
 [!code-vb[c_StandaloneDataContractSerializer#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#3)]  
  
 Aşağıdaki kodu kullanarak seri hale getirici örneği oluşturur `knownTypes` parametresi.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#4)]
 [!code-vb[c_StandaloneDataContractSerializer#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#4)]  
  
### <a name="specifying-the-default-root-name-and-namespace"></a>Namespace ve varsayılan kök adı belirtme  
 Bir nesne seri olduğunda, normalde, en dıştaki XML öğesinin ad alanı ve varsayılan adını ad alanı ve veri anlaşması adına göre belirlenir. Tüm iç öğelerin adlarını veri üye adlarından belirlenir ve kendi ad alanı, veri contract ad alanı. Aşağıdaki örnek kümeleri `Name` ve `Namespace` oluşturucuları değerleri <xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> sınıfları.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#5)]
 [!code-vb[c_StandaloneDataContractSerializer#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#5)]  
  
 Bir örneğini serileştirmek `Person` sınıfı oluşturur XML aşağıdakine benzer.  
  
```xml  
<PersonContract xmlns="http://schemas.contoso.com">  
  <AddressMember>  
    <StreetMember>123 Main Street</StreetMember>  
   </AddressMember>  
</PersonContract>  
```  
  
 Ancak, kök öğe ad alanı ve varsayılan adı değerlerini geçirerek özelleştirebileceğiniz `rootName` ve `rootNamespace` parametreleri <xref:System.Runtime.Serialization.DataContractSerializer> Oluşturucusu. Unutmayın `rootNamespace` ad alanı, veri üyelerine karşılık gelen içerilen öğelerin etkilemez. Bu, yalnızca en dıştaki öğenin ad alanı etkiler.  
  
 Bu değerleri dizeler veya örnekleri geçirilebilir <xref:System.Xml.XmlDictionaryString> ikili XML biçimini kullanarak kendi iyileştirme için izin veren sınıfı.  
  
### <a name="setting-the-maximum-objects-quota"></a>En büyük nesneleri kota ayarlama  
 Bazı `DataContractSerializer` oluşturucu aşırı yüklemeleri sahip bir `maxItemsInObjectGraph` parametresi. Bu parametre, nesne seri hale getirici serileştiren veya tek bir'seri durumdan çıkarır maksimum sayısını belirler. <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> yöntem çağrısı. (Yöntem her zaman bir kök nesnesinin okur, ancak bu nesne veri üyelerini başka nesneler olabilir. Bu nesneler diğer nesnelerin vardır ve benzeri.) 65536 varsayılandır. Her dizi girişi serileştirmek veya diziler seri durumdan çıkarılırken zaman ayrı bir nesne sayar unutmayın. Ayrıca, bazı nesneler, büyük bellek gösterimi olabilir ve bu nedenle bu kotayı tek başına bir hizmet reddi saldırısı önlemek için yeterli olmayabilir unutmayın. Daha fazla bilgi için [veriler için güvenlik konuları](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md). Varsayılan değer dışında bu kotayı artırmak gerekiyorsa, bunu gönderen (seri hale getirme) ve hem için verileri okurken ve yazarken geçerlidir (seri durumdan çıkarılırken) yüz aldınız yapmak önemlidir.  
  
### <a name="round-trips"></a>Gidiş dönüş  
 A *gidiş dönüş* bir nesne seri durumdan ve tek bir işlemde yeniden serileştirilmiş olduğunda gerçekleşir. Bu nedenle, XML'den bir nesne örneği ve arka yeniden bir XML akışa gider.  
  
 Bazı `DataContractSerializer` oluşturucu aşırı yüklemeleri sahip bir `ignoreExtensionDataObject` ayarlanır parametresini `false` varsayılan olarak. Veri anlaşması uyguladığı sürece bu varsayılan modda veri gidiş dönüş bir veri anlaşması bir eski sürümü ve arka aracılığıyla daha yeni sürümünden sürüme kaybı olmadan gönderilebilir <xref:System.Runtime.Serialization.IExtensibleDataObject> arabirimi. Örneğin, 1. sürümünü varsayalım `Person` veri sözleşmesi içeriyor `Name` ve `PhoneNumber` veri üyeleri ve sürüm 2 ekler bir `Nickname` üyesi. Varsa `IExtensibleDataObject` uygulanır, sürüm 2 ' sürüm 1'i bilgi gönderirken `Nickname` verilerin depolandığı ve verilere tekrar serileştirilmiş olduğunda yeniden yayılan; bu nedenle, hiçbir veri gidiş dönüş içinde kaybolur. Daha fazla bilgi için [İleri uyumlu veri sözleşmeleri](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md) ve [veri sözleşmesi sürümü oluşturma](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md).  
  
#### <a name="security-and-schema-validity-concerns-with-round-trips"></a>Güvenlik ve şema geçerlilik Kaygılarıyla gidiş dönüş  
 Gidiş dönüş güvenlikle ilgili etkileri olabilir. Örneğin, büyük miktarda yabancı veri depolamak ve seri durumdan çıkarılırken bir güvenlik riski olabilir. Güvenlikle ilgili olduğunu doğrulamak için bir yolu yoktur özellikle dijital imzalar söz konusuysa bu verileri yeniden yayma hakkında olabilir. Örneğin, önceki senaryoda sürüm 1 uç noktası imzalama bir `Nickname` kötü amaçlı veri içeren bir değer. Son olarak, olabilir şema geçerlilik kaygıları: bir uç nokta her zaman kesin olarak belirtilen sözleşmesi ve hiçbir ek değerleri için uyar veri yayma isteyebilirsiniz. Önceki örnekte, yalnızca yaydığı sürüm 1 uç noktasının contract diyor `Name` ve `PhoneNumber`ve şema doğrulaması kullanılması durumunda ek yayma `Nickname` değeri doğrulama başarısız olmasına neden olur.  
  
#### <a name="enabling-and-disabling-round-trips"></a>Gidiş dönüş devre dışı bırakma ve etkinleştirme  
 Gidiş dönüş devre dışı bırakmak için uygulamayın <xref:System.Runtime.Serialization.IExtensibleDataObject> arabirimi. Türleri üzerinde denetiminiz yoktur verilirse `ignoreExtensionDataObject` parametresi `true` aynı etkiyi elde etmek için.  
  
### <a name="object-graph-preservation"></a>Nesne grafiği korunması  
 Normalde, seri hale getirici hakkında aşağıdaki kodda gösterildiği gibi nesne kimliği ilgilenmez.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#6)]
 [!code-vb[c_StandaloneDataContractSerializer#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#6)]  
  
 Aşağıdaki kod, bir sipariş oluşturur.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#7)]
 [!code-vb[c_StandaloneDataContractSerializer#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#7)]  
  
 Dikkat `billTo` ve `shipTo` alanları aynı nesne örneğine ayarlanır. Ancak, oluşturulan XML yinelenen bilgiler ve aşağıdaki XML'e benzer.  
  
```xml  
<PurchaseOrder>  
  <billTo><street>123 Main St.</street></billTo>  
  <shipTo><street>123 Main St.</street></shipTo>  
</PurchaseOrder>  
```  
  
 Ancak, bu yaklaşım, istenmeyen aşağıdaki özelliklere sahiptir:  
  
- Performans. Verilerin çoğaltılması verimli değildir.  
  
- Döngüsel başvuru. Çoğaltma tarafından seri hale getirme, nesneler kendileri için diğer nesneler arasında bile başvuruyorsa, sonsuz bir döngüde sonuçlanır. (Seri hale getirici oluşturur bir <xref:System.Runtime.Serialization.SerializationException> böyle bir durumda.)  
  
- Semantik. Bazen iki başvurunun aynı nesneye ve iki özdeş nesneler için olan olgu korumak önemlidir.  
  
 Bu nedenleri, bazı `DataContractSerializer` oluşturucu aşırı yüklemeleri sahip bir `preserveObjectReferences` parametre (varsayılandır `false`). Bu parametre ayarlandığında `true`, yalnızca WCF anlayan, nesne başvuruları kodlama özel bir yöntem kullanılır. Ayarlandığında `true`, XML kodu örneği şimdi aşağıdakine benzer.  
  
```xml  
<PurchaseOrder ser:id="1">  
  <billTo ser:id="2"><street ser:id="3">123 Main St.</street></billTo>  
  <shipTo ser:ref="2"/>  
</PurchaseOrder>  
```  
  
 "Hi" ad alanı standart serileştirme ad alanına başvuruyor `http://schemas.microsoft.com/2003/10/Serialization/`. Her veri parçası yalnızca bir kez serileştirilmiş ve verilen kimlik numarasını ve yapılan bir başvuru zaten serileştirilmiş veriler sonraki sonucu kullanır.  
  
> [!IMPORTANT]
>  Hem "id" ve "başvuru" öznitelikleri içinde veri anlaşması varsa `XMLElement`, ardından "başvuru" özniteliği dikkate alınır ve "id" özniteliğinin göz ardı edilir.  
  
 Bu mod sınırlamaları anlamak önemlidir:  
  
- XML `DataContractSerializer` ile üretir `preserveObjectReferences` kümesine `true` diğer teknolojilerle birlikte çalışabilen değildir ve yalnızca bir başkası tarafından erişilebilen `DataContractSerializer` örneği de `preserveObjectReferences` kümesine `true`.  
  
- Bu özellik için meta veri (şema) desteği yoktur. Üretilen şema yalnızca durum için geçerli olduğunda `preserveObjectReferences` ayarlanır `false`.  
  
- Bu özellik serileştirme ve seri durumundan çıkarma işleminin daha yavaş çalışmasına neden olabilir. Verilerin çoğaltılması gerekmez. ancak, bu modda ek nesne karşılaştırma gerçekleştirilmesi gerekir.  
  
> [!CAUTION]
>  Zaman `preserveObjectReferences` modu etkin olduğunda, ayarlamak özellikle önemlidir `maxItemsInObjectGraph` doğru kota değeri. Diziler, bu modda işlenir yöntemi nedeniyle yalnızca sınırlı yüksek bellek tüketimine küçük bir kötü amaçlı iletisini oluşturmak bir saldırganın kolaydır `maxItemsInObjectGraph` kota.  
  
### <a name="specifying-a-data-contract-surrogate"></a>Bir veri anlaşması vekil belirtme  
 Bazı `DataContractSerializer` oluşturucu aşırı yüklemeleri sahip bir `dataContractSurrogate` için ayarlanabilir parametresini `null`. Belirtmek için kullanın Aksi halde, bir *veri sözleşme vekil*, uygulayan bir tür olduğu <xref:System.Runtime.Serialization.IDataContractSurrogate> arabirimi. Ardından, seri hale getirme özelleştirmek ve işlem seri durumdan çıkarma için arabirimi kullanabilirsiniz. Daha fazla bilgi için [veri anlaşması yedekleri](../../../../docs/framework/wcf/extending/data-contract-surrogates.md).  
  
## <a name="serialization"></a>Serileştirme  
 Devralınan herhangi bir sınıf aşağıdaki bilgileri uygulandığı <xref:System.Runtime.Serialization.XmlObjectSerializer>de dahil olmak üzere <xref:System.Runtime.Serialization.DataContractSerializer> ve <xref:System.Runtime.Serialization.NetDataContractSerializer> sınıfları.  
  
### <a name="simple-serialization"></a>Basit bir seri hale getirme  
 Bir nesneyi serileştirmek için en temel geçirilecek yoludur <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObject%2A> yöntemi. Üç aşırı yükleme, her biri için yazma için bir <xref:System.IO.Stream>e <xref:System.Xml.XmlWriter>, veya bir <xref:System.Xml.XmlDictionaryWriter>. İle <xref:System.IO.Stream> aşırı yükleme, çıktı olan XML UTF-8 kodlaması. İle <xref:System.Xml.XmlDictionaryWriter> aşırı yükleme, seri hale getirici için ikili XML çıktısını iyileştirir.  
  
 Kullanırken <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObject%2A> yöntemi, seri hale getirici için sarmalayıcı öğe ad alanı ve varsayılan adını kullanır ve içeriği (önceki "Belirten varsayılan kök adı ve Namespace" bölümüne bakın) yanı sıra yazıyor.  
  
 Aşağıdaki örnek, yazma ile gösterir. bir <xref:System.Xml.XmlDictionaryWriter>.  
  
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
 Kullanım <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteStartObject%2A>, <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObjectContent%2A>, ve <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteEndObject%2A> bitiş öğesi yazmak için yöntemleri nesne içeriğini yazmak ve sarmalayıcı öğe sırasıyla kapatın.  
  
> [!NOTE]
>  Var olan hiçbir <xref:System.IO.Stream> bu yöntemler aşırı yüklemeleri.  
  
 Bu adım adım serileştirme iki yaygın kullanımı vardır. Bir içeriği gibi öznitelikleri eklemek için veya arasında yorumları `WriteStartObject` ve `WriteObjectContent`, aşağıdaki örnekte gösterildiği gibi.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#9)]
 [!code-vb[c_StandaloneDataContractSerializer#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#9)]  
  
 Bu, aşağıdakine benzer XML oluşturur.  
  
```xml  
<Person serializedBy="myCode">  
  <Name>Jay Hamlin</Name>  
  <Address>123 Main St.</Address>  
</Person>  
```  
  
 Kullanmaktan kaçınmak için bir diğer yaygın kullanımı olan <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteStartObject%2A> ve <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteEndObject%2A> tamamen ve kendi özel bir sarmalayıcı öğe yazma (veya bir sarmalayıcı tamamen yazma bile atlamak için), aşağıdaki kodda gösterildiği gibi.  
  
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
>  Adım adım serileştirme kullanarak XML şema geçersiz neden olabilir.  
  
## <a name="deserialization"></a>Seri durumundan çıkarma  
 Devralınan herhangi bir sınıf aşağıdaki bilgileri uygulandığı <xref:System.Runtime.Serialization.XmlObjectSerializer>de dahil olmak üzere <xref:System.Runtime.Serialization.DataContractSerializer> ve <xref:System.Runtime.Serialization.NetDataContractSerializer> sınıfları.  
  
 Bir nesneyi seri durumdan çıkarılacak en temel yolu birini çağırmaktır <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> yöntemi aşırı yüklemeleri. Üç aşırı yükleme, her biri ile okumak için bir <xref:System.Xml.XmlDictionaryReader>e `XmlReader`, veya bir `Stream`. Unutmayın `Stream` aşırı oluşturur bir metinsel <xref:System.Xml.XmlDictionaryReader> herhangi bir kota tarafından korunmayan ve güvenilir veri salt okunur olarak kullanılmalıdır.  
  
 Ayrıca nesne `ReadObject` yöntemi döndürür gerekir uygun türüne dönüştürülür.  
  
 Aşağıdaki kod örneği oluşturur <xref:System.Runtime.Serialization.DataContractSerializer> ve <xref:System.Xml.XmlDictionaryReader>, sonra da seri durumdan çıkarır bir `Person` örneği.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#11)]
 [!code-vb[c_StandaloneDataContractSerializer#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#11)]  
  
 Çağırmadan önce <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> yöntemi, XML okuyucusu sarmalayıcı öğe veya sarmalayıcı öğe önündeki içeriği olmayan düğüm getirin. Bunu çağırarak yapmak <xref:System.Xml.XmlReader.Read%2A> yöntemi <xref:System.Xml.XmlReader> veya kendi türetme ve test <xref:System.Xml.XmlReader.NodeType%2A>aşağıdaki kodda gösterildiği gibi.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#12)]
 [!code-vb[c_StandaloneDataContractSerializer#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#12)]  
  
 Bu sarmalayıcı öğe özniteliklerinde Okuyucu için teslim etmeden önce okuyabilirsiniz Not `ReadObject`.  
  
 Basit birini kullanırken `ReadObject` aşırı yüklemeler, seri durumdan çıkarıcı arar sarmalayıcı öğe üzerinde ad alanı ve varsayılan adı ("Belirten varsayılan kök adı ve Namespace" kısmına bakın) ve bilinmeyen bulursa, bir özel durum oluşturur. öğe. Önceki örnekte `<Person>` sarmalayıcı öğe bekleniyor. <xref:System.Runtime.Serialization.XmlObjectSerializer.IsStartObject%2A> Yöntemi okuyucu beklendiği gibi adlı bir öğe üzerinde konumlandırıldı doğrulamak için çağrılır.  
  
 Bu sarmalayıcı öğe adı denetimi devre dışı bırakmak için bir yolu yoktur; Bazı aşırı yüklemeleri `ReadObject` yöntemi ele Boole parametresi `verifyObjectName`, Hosted `true` varsayılan olarak. Ayarlandığında `false`, sarmalayıcı öğe ad alanı ve ad yok sayılır. Bu, daha önce açıklanan adım adım serileştirme mekanizması kullanılarak yazılmıştır XML okumak için kullanışlıdır.  
  
## <a name="using-the-netdatacontractserializer"></a>NetDataContractSerializer kullanma  
 Arasındaki birincil fark `DataContractSerializer` ve <xref:System.Runtime.Serialization.NetDataContractSerializer> olan `DataContractSerializer` veri sözleşmesi adları kullanır `NetDataContractSerializer` tam çıkarır [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] serileştirilmiş XML derlemesi ve tür adları. Bu, tam aynı türlerini serileştirme ve seri durumundan çıkarma uç noktaları arasında paylaşılması gerektiği anlamına gelir. Bu bilinen türler mekanizması ile gerekli olmadığı anlamına gelir `NetDataContractSerializer` seri durumdan için tam türlerinden her zaman bildiği.  
  
 Ancak, bazı sorunlar oluşabilir:  
  
- Güvenlik. Seri durumdan çıkarılmakta olan XML içinde bulunan herhangi bir tür yüklenir. Bu, kötü amaçlı türleri yüklenmesini zorlamak için yararlanılabilir. Kullanarak `NetDataContractSerializer` yalnızca veri yapılmalıdır güvenilmeyen bir *serileştirme Bağlayıcısı* kullanılır (kullanarak <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder%2A> özelliği veya Oluşturucu parametresi). Bağlayıcı yalnızca güvenli türler yüklenmesine izin verir. Türler bir bağlayıcı mekanizması aynıdır <xref:System.Runtime.Serialization> ad alanı kullanın.  
  
- Sürüm oluşturma. Tam tür ve derleme adları XML'de ciddi bir şekilde kullanarak nasıl türleri tutulan olabileceğini kısıtlar. Aşağıdakiler değiştirilemez: ad, ad alanları, derleme adları ve derleme sürümlerini yazın. Ayarı <xref:System.Runtime.Serialization.NetDataContractSerializer.AssemblyFormat%2A> özellik ya da Oluşturucu parametresini <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle.Simple> varsayılan değeri yerine <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle.Full> derleme sürüm değişikliklerini, ancak genel parametre türleri sağlar.  
  
- Birlikte çalışabilirlik. Çünkü [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] tür ve derleme adları dahil edilir XML'de platformları dışında [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] elde edilen verilere erişemez.  
  
- Performans. Tür ve derleme yazma önemli ölçüde artar elde edilen XML boyutu adları.  
  
 Bu mekanizma, ikili veya SOAP serileştirme tarafından kullanılan benzer [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] uzaktan iletişim (özellikle <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> ve <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>).  
  
 Kullanarak `NetDataContractSerializer` kullanmaya benzer `DataContractSerializer`, aşağıdaki farklarla birlikte:  
  
- Oluşturucu bir kök türü belirtmenizi gerektirmez. ' In aynı örneğine sahip herhangi bir türün serileştirip serileştiremeyeceğini `NetDataContractSerializer`.  
  
- Oluşturucular bilinen türlerinin bir listesini kabul etmez. Tür adları XML olarak serileştirilme şeklini, gereksiz bilinen türler mekanizmadır.  
  
- Oluşturucular, bir veri anlaşması vekil kabul etmeyin. Bunun yerine, kabul bir <xref:System.Runtime.Serialization.ISurrogateSelector> adlı parametreyi `surrogateSelector` (eşlenir <xref:System.Runtime.Serialization.NetDataContractSerializer.SurrogateSelector%2A> özelliği). Eski vekil mekanizması budur.  
  
- Oluşturucular adlı bir parametreyi kabul `assemblyFormat` , <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle> eşlenen <xref:System.Runtime.Serialization.NetDataContractSerializer.AssemblyFormat%2A> özelliği. Daha önce açıklandığı gibi bu seri hale getirici sürüm yeteneklerini geliştirmek için kullanılabilir. Bu aynı <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle> ikili veya SOAP serileştirme mekanizması.  
  
- Kabul oluşturucular bir <xref:System.Runtime.Serialization.StreamingContext> adlı parametreyi `context` eşlenen <xref:System.Runtime.Serialization.NetDataContractSerializer.Context%2A> özelliği. Serileştirilmekte olan tür olarak bilgi geçirmek için kullanabilirsiniz. Bu kullanım olarak aynıdır <xref:System.Runtime.Serialization.StreamingContext> diğer kullanılan mekanizma <xref:System.Runtime.Serialization> sınıfları.  
  
- <xref:System.Runtime.Serialization.NetDataContractSerializer.Serialize%2A> Ve <xref:System.Runtime.Serialization.NetDataContractSerializer.Deserialize%2A> yöntemleri adlarıdır <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObject%2A> ve <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> yöntemleri. Bunlar, ikili veya SOAP serileştirme ile daha tutarlı bir programlama modeli sağlamak için mevcut.  
  
 Bu özellikler hakkında daha fazla bilgi için bkz. [ikili serileştirme](../../../../docs/standard/serialization/binary-serialization.md).  
  
 XML, biçimleri `NetDataContractSerializer` ve `DataContractSerializer` kullanmak normalde uyumlu değildir. Diğer bir deyişle, bu seri hale getiricileri genişletme biri ile seri hale getirmek ve diğer seri durumdan çalışılıyor desteklenen bir senaryo değildir.  
  
 Ayrıca, `NetDataContractSerializer` tam çıktısının [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Nesne grafiği her düğüm için tür ve derleme adı. Bu, yalnızca belirsiz olduğu için bu bilgileri çıkarır. Diğer bir deyişle, kök nesne düzeyinde ve çok biçimli herhangi bir servis talebi için çıkarır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.NetDataContractSerializer>
- <xref:System.Runtime.Serialization.XmlObjectSerializer>
- [İkili Serileştirme](../../../../docs/standard/serialization/binary-serialization.md)
- [Veri Anlaşması Seri Hale Getirici Tarafından Desteklenen Türler](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)
