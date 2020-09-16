---
title: XML serileştirme ayrıntıları
description: Serileştirme bir nesneyi, taşınan bir forma dönüştürür. Bu makalede, XML serileştirme ve XmlSerializer sınıfına bir genel bakış sunulmaktadır.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XML serialization, about XML serialization
- ICollection interface, serializing
- XmlSerializer class, serializing
- serialization, about serialization
- DataSet class, serializing
- XML Schema, serializing
ms.assetid: 8c63200d-db63-4a03-a93d-21641623df62
ms.openlocfilehash: 334cb3fe40c310189018d924aef552ecd87e9a65
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90535416"
---
# <a name="xml-serialization"></a>XML serileştirme

Serileştirme, bir nesneyi, kolayca taşınacak bir forma dönüştürme işlemidir. Örneğin, bir nesneyi seri hale getirebilirsiniz ve bir istemci ile sunucu arasında HTTP kullanarak Internet üzerinden aktarabilirsiniz. Diğer uçta, seri durumdan çıkarma nesneyi akıştan yeniden oluşturur.

 XML serileştirme, bir nesnenin yalnızca ortak alanlarını ve özellik değerlerini bir XML akışına seri hale getirir. XML serileştirme türü bilgilerini içermez. Örneğin, **kitaplık** ad alanında bulunan bir **kitap** nesneniz varsa, bunun seri durumdan çıkarılma, aynı türde bir nesneye sahip değildir.

> [!NOTE]
> XML serileştirme yöntemleri, Dizinleyicileri, özel alanları veya salt okunur özelliklerini (dışında salt okunur koleksiyonlar) dönüştürmez. Bir nesnenin tüm alanları ve özellikleri serileştirmek için ve ortak ve özel, kullanın <xref:System.Runtime.Serialization.DataContractSerializer> XML serileştirme yerine.

 XML serileştirme içindeki merkezi sınıf sınıftır <xref:System.Xml.Serialization.XmlSerializer> ve bu sınıftaki en önemli Yöntemler **serileştirme** ve **seri durumdan çıkarma** yöntemleridir. <xref:System.Xml.Serialization.XmlSerializer> C# dosyaları oluşturur ve bunları bu serileştirme gerçekleştirmek için .dll dosyalarıyla derler. .NET Framework 2,0 ' de, [XML serileştiricisi oluşturma aracı (Sgen.exe)](xml-serializer-generator-tool-sgen-exe.md) , uygulamanızla birlikte dağıtılacak ve başlangıç performansını iyileştirecek şekilde bu serileştirme derlemelerini oluşturmak için tasarlanmıştır. **XmlSerializer** tarafından oluşturulan xml akışı, world WIDE Web KONSORSIYUMU (W3C) [XML şeması tanım dili (xsd) 1,0 önerisi](https://www.w3.org/TR/xslt)ile uyumludur. Ayrıca, oluşturulan veri türleri başlıklı belge ile uyumludur "XML şema bölüm 2: veri türleri."

 Nesnelerinizin verileri, diziler, alanlar, özellikler, ilkel türler, diziler ve hatta katıştırılmış XML gibi programlama dili yapılarını **XmlElement** veya **XmlAttribute** nesneleri biçiminde kullanarak açıklanır. Kendi sınıflarınızı oluşturma, özniteliklerle açıklama eklenmiş veya XML şema tanımı aracını kullanarak mevcut bir XML şemasına göre sınıfları oluşturma seçeneğiniz vardır.

 XML şemanız varsa, şemaya kesin olarak yazılan ve özniteliklerle açıklanan bir sınıf kümesi oluşturmak için XML şema tanımı aracını çalıştırabilirsiniz. Bu tür bir sınıfının bir örneğini serileştirilmiş olduğunda, oluşturulan XML için XML Şeması uyar. Bu tür bir sınıf ile programlayabileceğiniz sağlanan kolay yönetilebilen nesne modeli olan sırasında oluşturulan XML XML şemaya uygun olduğunu garanti. Bu, bir XML akışı ayrıştırmak ve yazmak için **XmlReader** ve **XmlWriter** sınıfları gibi .NET Framework diğer sınıfların kullanılmasına bir alternatiftir. Daha fazla bilgi için bkz. [XML belgeleri ve verileri](../data/xml/index.md). Bu sınıflar herhangi bir XML akışını ayrıştırabilmeniz için izin verir. Buna karşılık, XML akışının bilinen bir XML şemasına uyması beklendiğinde **XmlSerializer** 'ı kullanın.

 Öznitelikler, XML akışının XML ad alanını, öğe adını, öznitelik adını ve benzerlerini ayarlamanıza olanak tanıyan **XmlSerializer** sınıfı tarafından oluşturulan XML akışını denetler. Bu öznitelikler ve XML serileştirmesini denetleme hakkında daha fazla bilgi için bkz. [öznitelikleri kullanarak XML serileştirmesini denetleme](controlling-xml-serialization-using-attributes.md). Oluşturulan XML 'yi denetlemek için kullanılan özniteliklerin bir tablosu için bkz. [XML serileştirme denetleyen öznitelikler](attributes-that-control-xml-serialization.md).

 **XmlSerializer** sınıfı bir nesneyi daha sonra serileştirmez ve KODLANMıŞ BIR SOAP XML akışı oluşturabilir. Oluşturulan XML "Basit Nesne Erişim Protokolü (SOAP) 1.1." başlıklı bölümüne World Wide Web Consortium belgesinin 5 uyar Bu işlem hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir NESNEYI SOAP kodlu XML akışı olarak serileştirme](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md). Oluşturulan XML 'yi denetleyen özniteliklerin bir tablosu için bkz. [KODLANMıŞ SOAP serileştirmesini denetleyen öznitelikler](attributes-that-control-encoded-soap-serialization.md).

 **XmlSerializer** sınıfı, tarafından oluşturulan ve XML Web Hizmetleri 'NE geçirilen SOAP iletilerini oluşturur. SOAP iletilerini denetlemek için sınıflar, dönüş değerleri, parametreler ve bir XML Web hizmeti dosyasında (. asmx) bulunan alanlara öznitelikler uygulayabilirsiniz. XML Web hizmeti değişmez değer veya kodlanmış SOAP stilini kullanabilmesi için, "XML serileştirmesini denetleyen öznitelikler" ve "kodlanmış SOAP serileştirmesini denetleyen öznitelikler" bölümünde listelenen öznitelikleri kullanabilirsiniz. XML Web hizmeti tarafından oluşturulan XML 'yi denetlemek için öznitelikleri kullanma hakkında daha fazla bilgi için bkz. xml [Web Hizmetleri Ile XML serileştirme](xml-serialization-with-xml-web-services.md). SOAP ve XML Web Hizmetleri hakkında daha fazla bilgi için bkz. [SOAP Ileti biçimlendirmesini özelleştirme](/previous-versions/dotnet/netframework-4.0/dkwy2d72(v=vs.100)).

## <a name="security-considerations-for-xmlserializer-applications"></a>XmlSerializer uygulamalar için güvenlik hususları

**XmlSerializer**'ı kullanan bir uygulama oluştururken, aşağıdaki öğeleri ve bunların etkilerini unutmayın:

- **XmlSerializer** , C# (. cs) dosyaları oluşturur ve bunları temp ortam değişkeni tarafından adlandırılan dizinde. dll dosyalarına derler; serileştirme bu DLL 'Ler ile oluşur.

  > [!NOTE]
  > Bu seri hale getirme derlemeler önceden oluşturulur ve SGen.exe aracını kullanarak oturum açmış. Bu, bir Web Hizmetleri sunucusu çalışmıyor. Diğer bir deyişle, yalnızca istemci kullanımı için ve el ile serileştirme içindir.

  Kod ve DLL'leri oluşturma ve derleme sırasındaki kötü amaçlı bir işleme etkilenir. Microsoft Windows NT 4.0 veya sonraki sürümü çalıştıran bir bilgisayara kullanırken, TEMP dizinini paylaşmak iki veya daha fazla kullanıcı için olası olabilir. İki hesabın farklı güvenlik ayrıcalıklarına sahip olması ve yüksek ayrıcalıklı hesabın **XmlSerializer**kullanarak bir uygulama ÇALıŞTıRMASı durumunda geçici dizin paylaşımı tehlikelidir. Bu durumda, bir kullanıcı derlenmiş olup .cs veya .dll dosya değiştirerek bilgisayarın güvenlik ihlal. Bu sorunu gidermek için her zaman her bilgisayar hesabında kendi profili sahip olduğundan emin olun. Varsayılan olarak, her hesap için farklı bir dizin TEMP ortam değişkeni gösteriyor.

- Kötü amaçlı bir Kullanıcı bir Web sunucusuna (hizmet reddi saldırısı) sürekli bir XML verisi akışı gönderirse, bilgisayar kaynakları azalana kadar **XmlSerializer** verileri işlemeye devam eder.

  Internet Information Services (IIS) çalıştıran bir bilgisayara kullandığınız ve uygulamanızı IIS içinde çalışıyorsa bu tür bir saldırıya ortadan kaldırıldı. IIS, küme miktarından daha uzun akışları işlemez (varsayılan 4 KB 'tır). IIS kullanmayan ve **XmlSerializer**ile seri hale getirilen bir uygulama oluşturursanız, hizmet reddi saldırısını engelleyen benzer bir geçit uygulamanız gerekir.

- **XmlSerializer** verileri seri hale getirir ve kendisine verilen herhangi bir türü kullanarak herhangi bir kodu çalıştırır.

  Kötü amaçlı bir nesne bir iş parçacığı sayısını gösterir iki yolu vardır. Kötü amaçlı kod çalıştırabilir veya **XmlSerializer**tarafından oluşturulan C# dosyasına kötü amaçlı kod ekleyebilir. İlk durumda, kötü amaçlı bir nesne bozucu bir yordam çalıştırmaya çalışırsa, kod erişim güvenliği, herhangi bir hasar yapılmasını önlemeye yardımcı olur. İkinci durumda, kötü niyetli bir nesnenin **XmlSerializer**tarafından oluşturulan C# dosyasına bir kod eklemesine olanak tanıyan bir teorik olabilir. Bu sorun kapsamlı bir şekilde incelendi ve bu tür bir saldırı nadiren düşünülse de, verileri bilinmeyen ve güvenilmeyen bir türle asla serileştirmez.

- Serileştirilmiş hassas verileri açık olabilir.

  **XmlSerializer** verileri serileştirdikten sonra bir XML dosyası veya başka bir veri deposu olarak depolanabilir. Veri depetiniz diğer işlemlere kullanılabilirse veya bir intranette ya da Internet üzerinde görülebilir durumdaysa, veriler çalınıp kötü amaçlı olarak kullanılabilir. Örneğin, bir uygulama oluşturursanız, siparişler serileştiren kredi kartı numaraları dahil, veri yüksek oranda duyarlıdır. Bunu önlemek için her zaman için veri deposu korumak ve özel olarak saklamak için adımları izleyin.

## <a name="serialization-of-a-simple-class"></a>Basit bir sınıfın seri hale getirme

Aşağıdaki kod örneğinde, ortak bir alanla temel bir sınıfı gösterir.

```vb
Public Class OrderForm
    Public OrderDate As DateTime
End Class
```

```csharp
public class OrderForm
{
    public DateTime OrderDate;
}
```

Bu sınıfın örneğini serileştirilmiş olduğunda, aşağıdakine benzer.

```xml
<OrderForm>
    <OrderDate>12/12/01</OrderDate>
</OrderForm>
```

Serileştirme hakkında daha fazla örnek için bkz. [XML serileştirme örnekleri](examples-of-xml-serialization.md).

## <a name="items-that-can-be-serialized"></a>Seri hale öğeleri

Aşağıdaki öğeler **XmlSerializer** sınıfı kullanılarak seri hale getirilebilir:

- Ortak okuma/yazma özellikleri ve ortak sınıfların alanları.

- **ICollection** veya **IEnumerable**uygulayan sınıflar.

  > [!NOTE]
  > Yalnızca koleksiyonları serileştirilmiş, ortak değil Özellikleri ' dir.

- **XmlElement** nesneleri.

- **XMLNode** nesneleri.

- **Veri kümesi** nesneleri.

 Nesneleri serileştirmek veya seri durumdan çıkarma hakkında daha fazla bilgi için bkz. [nasıl yapılır: serileştirme bir nesne](how-to-serialize-an-object.md) ve [nasıl yapılır: bir nesnenin serisini kaldırma](how-to-deserialize-an-object.md).

## <a name="advantages-of-using-xml-serialization"></a>XML Serialization kullanarak avantajları

**XmlSerializer** sınıfı, BIR nesneyi XML olarak serileştirçalışırken size tüm ve esnek denetim sağlar. Bir XML Web hizmeti oluşturuyorsanız, XML çıkışının belirli bir şemaya uygun olmasını sağlamak için, sınıfları ve üyeleri serileştirme ' i denetleyen öznitelikler uygulayabilirsiniz.

Örneğin, **XmlSerializer** şunları yapmanızı sağlar:

- Bir alanın veya özelliğin öznitelik veya bir öğe olarak kodlanıp kodlanmayacağını belirtin.

- Kullanmak için bir XML ad alanı belirtin.

- Bir alan veya özellik adı uygun değilse, bir öğenin veya özniteliğin adını belirtin.

XML serileştirmenin bir diğer avantajı, oluşturulan uygulamalar üzerinde herhangi bir kısıtlama olmadığı sürece, üretilen XML akışı belirli bir şemaya uygun değildir. Books tanımlamak için kullanılan bir şema düşünün. Bir başlık özelliklerini, yazarın, yayımcı ve ISBN öğe sayısı. Örneğin, bir kitap düzeni veya books envanterini olarak istediğiniz herhangi bir şekilde XML verileri işleyen bir uygulama geliştirebilirsiniz. Her iki durumda da, XML akışının belirtilen XML şeması tanım dili (XSD) şemasına uygun olması yeterlidir.

## <a name="xml-serialization-considerations"></a>XML serileştirme konuları

**XmlSerializer** sınıfı kullanılırken aşağıdakiler göz önünde bulundurulmalıdır:

- Sgen.exe aracı açıkça en iyi performans için serileştirme derlemelerini oluşturmak üzere tasarlanmıştır.

- Serileştirilmiş veriler yalnızca verilerin kendisini ve sınıflarınızın yapısını içerir. Türü kimlik ve derleme bilgiler dahil değildir.

- Yalnızca genel özelliklerini ve alanları seri hale getirilebilir. Özellikler ortak erişimciler olmalıdır (almanıza ve ayarlamanıza yöntemleri). Genel olmayan verileri seri gerekir, kullanın <xref:System.Runtime.Serialization.DataContractSerializer> sınıfının XML serileştirme değil.

- Bir sınıf **XmlSerializer**tarafından seri hale getirilecek parametresiz bir oluşturucuya sahip olmalıdır.

- Yöntemleri seri hale getirilemiyor.

- **XmlSerializer** , bazı gereksinimleri karşılıyorsa **IEnumerable** veya **ICollection** uygulayan sınıfları aşağıdaki gibi işleyebilir.

  **IEnumerable** uygulayan bir sınıf, tek bir parametre alan ortak bir **Add** yöntemi gerçekleştirmelidir. **Add** yönteminin parametresi, **GetEnumerator** yönteminden döndürülen **IEnumerator. Current** özelliğinden döndürülen türle tutarlı (Polimorfik) olmalıdır.

  **IEnumerable** ( **CollectionBase**gibi) ek olarak **ICollection** uygulayan bir sınıf, bir tamsayı alan ortak bir **öğe** dizinli özelliğine (C# ' deki bir Dizin Oluşturucu) sahip olmalıdır ve **tamsayı**türünde bir ortak **Count** özelliği olmalıdır. **Add** yöntemine geçirilen parametre, **öğe** özelliğinden döndürülen aynı türde veya bu tür tabanlarından biri olmalıdır.

  **ICollection**uygulayan sınıflar için, seri hale getirilecek değerler **GetEnumerator**çağrısı yerine dizinli **Item** özelliğinden alınır. Ayrıca, genel alanlar ve özellikler, başka bir koleksiyon sınıfını ( **ICollection**uygulayan bir tane) döndüren ortak alanlar dışında serileştirilmez. Örnek için bkz. [XML serileştirme örnekleri](examples-of-xml-serialization.md).

## <a name="xsd-data-type-mapping"></a>XSD veri türü eşlemesi

[XML şeması Bölüm 2: veri türleri](https://www.w3.org/TR/xmlschema-2/) başlıklı W3C belgesi, bir XML şeması tanım DILI (xsd) şemasında izin verilen basit veri türlerini belirtir. Bunlardan birçoğu (örneğin, **int** ve **decimal**) için .NET Framework karşılık gelen bir veri türü vardır. Ancak, bazı XML veri türleri .NET Framework karşılık gelen bir veri türüne sahip değildir (örneğin, **NMTOKEN** veri türü). Bu gibi durumlarda, bir şemadan sınıflar oluşturmak için XML şema tanımı aracını ([XML şema tanımı Aracı (Xsd.exe)](xml-schema-definition-tool-xsd-exe.md)) kullanırsanız, String türünde bir üyeye uygun bir öznitelik uygulanır ve **DataType** özelliği XML veri türü adına ayarlanır. Örneğin, bir şema XML veri türü **NMTOKEN**olan "mytoken" adlı bir öğe içeriyorsa, oluşturulan sınıf aşağıdaki örnekte gösterildiği gibi bir üye içerebilir.

```vb
<XmlElement(DataType:="NMTOKEN")> _
Public MyToken As String
```

```csharp
[XmlElement(DataType = "NMTOKEN")]
public string MyToken;
```

Benzer şekilde, belirli bir XML şeması (XSD) ile uyumlu olması gereken bir sınıf oluşturuyorsanız, uygun özniteliği uygulamanız ve **DataType** ÖZELLIĞINI istenen XML veri türü adı olarak ayarlamanız gerekir.

Tür eşlemelerinin tüm listesi için aşağıdaki öznitelik sınıflarının herhangi biri için **DataType** özelliğine bakın:

- <xref:System.Xml.Serialization.SoapAttributeAttribute>

- <xref:System.Xml.Serialization.SoapElementAttribute>

- <xref:System.Xml.Serialization.XmlArrayItemAttribute>

- <xref:System.Xml.Serialization.XmlAttributeAttribute>

- <xref:System.Xml.Serialization.XmlElementAttribute>

- <xref:System.Xml.Serialization.XmlRootAttribute>

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Serialization.XmlSerializer>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.IO.FileStream>
- [XML ve SOAP serileştirme](xml-and-soap-serialization.md)
- [İkili serileştirme](binary-serialization.md)
- [Serileştirme](index.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [XML Serileştirme Örnekleri](examples-of-xml-serialization.md)
- [Nasıl yapılır: Nesne Serileştirme](how-to-serialize-an-object.md)
- [Nasıl yapılır: Nesneyi Seri Durumdan Çıkarma](how-to-deserialize-an-object.md)
