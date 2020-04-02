---
title: XML serileştirmeayrıntıları
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
ms.openlocfilehash: d644e80cbf5ac17fca4df039d915c847a1936217
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588448"
---
# <a name="xml-serialization"></a>XML serileştirme

Serileştirme, bir nesneyi kolayca taşınabilen bir forma dönüştürme işlemidir. Örneğin, bir nesneyi seri hale getirebilir ve istemci ve sunucu arasında HTTP kullanarak internet üzerinden taşıyabilirsiniz. Diğer tarafta, deserialization nesneyi akıştan yeniden yapıdadır.

 XML serileştirme, yalnızca bir nesnenin ortak alanlarını ve özellik değerlerini xml akışına serileştirir. XML serileştirme türü bilgilerini içermez. Örneğin, **Kitaplık** ad alanında bulunan bir **Kitap** nesneniz varsa, aynı türdeki bir nesneye deserialized olduğunu garanti yoktur.

> [!NOTE]
> XML serileştirme yöntemleri, Dizinleyicileri, özel alanları veya salt okunur özelliklerini (dışında salt okunur koleksiyonlar) dönüştürmez. Bir nesnenin tüm alanları ve özellikleri serileştirmek için ve ortak ve özel, kullanın <xref:System.Runtime.Serialization.DataContractSerializer> XML serileştirme yerine.

 XML serileştirmede merkezi sınıf <xref:System.Xml.Serialization.XmlSerializer> sınıftır ve bu sınıftaki en önemli yöntemler **Serialize** ve **Deserialize** yöntemleridir. <xref:System.Xml.Serialization.XmlSerializer> C# dosyaları oluşturur ve bunları bu serileştirme gerçekleştirmek için .dll dosyalarıyla derler. .NET Framework 2.0'da, [XML Serializer Generator Tool (Sgen.exe),](xml-serializer-generator-tool-sgen-exe.md) uygulamanızla birlikte dağıtılmak ve başlangıç performansını artırmak üzere bu serileştirme derlemelerini önceden oluşturmak üzere tasarlanmıştır. **XmlSerializer** tarafından oluşturulan XML akışı World Wide Web Konsorsiyumu (W3C) [XML Şema tanım dili (XSD) 1.0 önerisi](https://www.w3.org/TR/xslt)ile uyumludur. Ayrıca, oluşturulan veri türleri başlıklı belge ile uyumludur "XML şema bölüm 2: veri türleri."

 Nesnelerinizdeki veriler, sınıflar, alanlar, özellikler, ilkel türler, diziler ve hatta **XmlElement** veya **XmlAttribute** nesneleri şeklinde katıştırılmış XML gibi programlama dili yapıları kullanılarak tanımlanır. Özniteliklerle açıklamalı kendi sınıflarınızı oluşturma veya varolan bir XML Şeması'na dayalı sınıfları oluşturmak için XML Şema Tanımı aracını kullanma seçeneğiniz vardır.

 Bir XML Şemasınız varsa, şemaya güçlü bir şekilde yazılan ve özniteliklerle açıklamalı bir sınıf kümesi oluşturmak için XML Şema Tanımı aracını çalıştırabilirsiniz. Bu tür bir sınıfının bir örneğini serileştirilmiş olduğunda, oluşturulan XML için XML Şeması uyar. Bu tür bir sınıf ile programlayabileceğiniz sağlanan kolay yönetilebilen nesne modeli olan sırasında oluşturulan XML XML şemaya uygun olduğunu garanti. Bu, **XmlReader** ve **XmlWriter** sınıfları gibi .NET Framework'deki diğer sınıfları ayrıştırmak ve xml akışı yazmak için kullanmaya alternatiftir. Daha fazla bilgi için [Bkz. XML Belgeler ve Veriler.](../../../docs/standard/data/xml/index.md) Bu sınıflar herhangi bir XML akışını ayrıştırmak için izin verir. Buna karşılık, XML akışı bilinen bir XML Şemasına uyması beklenirken **XmlSerializer'ı** kullanın.

 Öznitelikler, XML sınıfı tarafından oluşturulan **XML** akışını denetleyerek XML ad alanını, öğe adını, öznitelik adını ve benzeri, XML akışını ayarlamanızı sağlar. Bu öznitelikler ve XML serileştirmeyi nasıl denetledikleri hakkında daha fazla bilgi için, [Bkz. XML Serileştirmeyi Denetleme Öznitelikleri.](controlling-xml-serialization-using-attributes.md) Oluşturulan XML'i denetlemek için kullanılan bu özniteliklerin bir tablosu için, [XML Serileştirmeyi Denetleyen Özniteliklere](attributes-that-control-xml-serialization.md)bakın.

 **XmlSerializer** sınıfı bir nesneyi daha da seri hale getirebilir ve kodlanmış soap XML akışı oluşturabilir. Oluşturulan XML "Basit Nesne Erişim Protokolü (SOAP) 1.1." başlıklı bölümüne World Wide Web Consortium belgesinin 5 uyar Bu işlem hakkında daha fazla bilgi için [bkz: Bir Nesneyi SOAP Kodlu XML Akışı Olarak Serihale.](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md) Oluşturulan XML'i denetleyen özniteliklerin tablosu için [bkz.](attributes-that-control-encoded-soap-serialization.md)

 **XmlSerializer** sınıfı, XML Web hizmetleri tarafından oluşturulan ve xml Web hizmetlerine aktarılan SOAP iletilerini oluşturur. SOAP iletilerini denetlemek için, bir XML Web hizmet dosyasında (.asmx) bulunan sınıflara, döndürme değerlerine, parametrelere ve alanlara öznitelikleri uygulayabilirsiniz. Bir XML Web hizmeti gerçek veya kodlanmış SOAP stilini kullanabileceğinden, "XML Serileştirmeyi Kontrol Eden Öznitelikler" ve "Kodlanmış SOAP Serialization'ı Kontrol Eden Öznitelikler" dizilerinde listelenen öznitelikleri kullanabilirsiniz. Bir XML Web hizmeti tarafından oluşturulan XML'i denetlemek için öznitelikleri kullanma hakkında daha fazla bilgi için Bkz. [XML Web Hizmetleri ile XML Serileştirme.](xml-serialization-with-xml-web-services.md) SOAP ve XML Web hizmetleri hakkında daha fazla bilgi için [SOAP İleti Biçimlendirmeyi Özelleştirme'ye](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dkwy2d72(v=vs.100))bakın.

## <a name="security-considerations-for-xmlserializer-applications"></a>XmlSerializer uygulamalar için güvenlik hususları

**XmlSerializer**kullanan bir uygulama oluştururken, aşağıdaki öğeleri ve bunların etkileri farkında olun:

- **XmlSerializer** C# (.cs) dosyalarını oluşturur ve temp ortamı değişkeni tarafından adlandırılan dizindeki .dll dosyalarına derler; serileştirme bu DLs ile oluşur.

  > [!NOTE]
  > Bu seri hale getirme derlemeler önceden oluşturulur ve SGen.exe aracını kullanarak oturum açmış. Bu, bir Web Hizmetleri sunucusu çalışmıyor. Diğer bir deyişle, yalnızca istemci kullanımı için ve el ile serileştirme içindir.

  Kod ve DLL'leri oluşturma ve derleme sırasındaki kötü amaçlı bir işleme etkilenir. Microsoft Windows NT 4.0 veya sonraki sürümü çalıştıran bir bilgisayara kullanırken, TEMP dizinini paylaşmak iki veya daha fazla kullanıcı için olası olabilir. İki hesap farklı güvenlik ayrıcalıklarına sahipse ve daha yüksek ayrıcalıklı hesap **XmlSerializer**kullanarak bir uygulama çalıştırıyorsa TEMP dizinini paylaşmak tehlikelidir. Bu durumda, bir kullanıcı derlenmiş olup .cs veya .dll dosya değiştirerek bilgisayarın güvenlik ihlal. Bu sorunu gidermek için her zaman her bilgisayar hesabında kendi profili sahip olduğundan emin olun. Varsayılan olarak, her hesap için farklı bir dizin TEMP ortam değişkeni gösteriyor.

- Kötü niyetli bir kullanıcı bir Web sunucusuna sürekli xml veri akışı gönderirse (hizmet reddi saldırısı), bilgisayar kaynakları azalana kadar **XmlSerializer** verileri işlemeye devam edin.

  Internet Information Services (IIS) çalıştıran bir bilgisayara kullandığınız ve uygulamanızı IIS içinde çalışıyorsa bu tür bir saldırıya ortadan kaldırıldı. IIS, akışları belirli bir miktardan daha uzun işlemeyen bir kapı sunar (varsayılan değer 4 KB'dir). IIS kullanmayan ve **XmlSerializer**ile deserialize bir uygulama oluşturursanız, hizmet reddi saldırısını engelleyen benzer bir kapı uygulamanız gerekir.

- **XmlSerializer** verileri serileştirir ve verilen herhangi bir türü kullanarak herhangi bir kodu çalıştırır.

  Kötü amaçlı bir nesne bir iş parçacığı sayısını gösterir iki yolu vardır. Kötü amaçlı kod çalıştırabilir veya **XmlSerializer**tarafından oluşturulan C# dosyasına kötü amaçlı kod enjekte edebilir. İlk durumda, kötü amaçlı bir nesne yıkıcı bir yordam çalıştırmaya çalışırsa, kod erişim güvenliği herhangi bir hasarın yapılmasını önlemeye yardımcı olur. İkinci durumda, kötü amaçlı bir nesnenin **XmlSerializer**tarafından oluşturulan C# dosyasına bir şekilde kod enjekte edebileceği teorik bir olasılık vardır. Bu sorun ayrıntılı olarak incelenmiş olsa da ve böyle bir saldırı olası kabul edilmiştir, bilinmeyen ve güvenilmeyen türü ile veri seri asla önlem almalıdır.

- Serileştirilmiş hassas verileri açık olabilir.

  **XmlSerializer** serileştirilmiş veri sonra, bir XML dosyası veya diğer veri deposu olarak saklanabilir. Veri deponuz başka işlemler için kullanılabilirse veya bir intranet veya Internet'te görünüyorsa, veriler çalınabilir ve kötü amaçlı olarak kullanılabilir. Örneğin, bir uygulama oluşturursanız, siparişler serileştiren kredi kartı numaraları dahil, veri yüksek oranda duyarlıdır. Bunu önlemek için her zaman için veri deposu korumak ve özel olarak saklamak için adımları izleyin.

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

Serileştirmenin diğer örnekleri için Bkz. [XML Serileştirme örnekleri.](examples-of-xml-serialization.md)

## <a name="items-that-can-be-serialized"></a>Seri hale öğeleri

Aşağıdaki öğeler **XmLSerializer** sınıfı kullanılarak seri hale getirilebilir:

- Ortak okuma/yazma özellikleri ve ortak sınıfların alanları.

- **ICollection** veya **ImEnumerable**uygulayan sınıflar.

  > [!NOTE]
  > Yalnızca koleksiyonları serileştirilmiş, ortak değil Özellikleri ' dir.

- **XmlElement** nesneleri.

- **XmlNode** nesneleri.

- **DataSet** nesneleri.

 Nesneleri serileştirme veya deserializing hakkında daha fazla bilgi için [bkz: Nesneyi Serihale](how-to-serialize-an-object.md) ve [Nasıl İşle: Nesneyi Deserialize Etme](how-to-deserialize-an-object.md).

## <a name="advantages-of-using-xml-serialization"></a>XML Serialization kullanarak avantajları

**XmlSerializer** sınıfı, bir nesneyi XML olarak serihale ettiğinizde tam ve esnek denetim sağlar. Bir XML Web hizmeti oluşturuyorsanız, XML çıkışının belirli bir şemaya uygun olduğundan emin olmak için sınıflara ve üyelere serileştirmeyi denetleyen öznitelikleri uygulayabilirsiniz.

Örneğin, **XmlSerializer** şunları yapmanızı sağlar:

- Bir alanın veya özelliğin öznitelik veya öğe olarak kodlanıp kodlanmayacağını belirtin.

- Kullanmak için bir XML ad alanı belirtin.

- Bir alan veya özellik adı uygun değilse, bir öğenin adını veya özniteliğini belirtin.

XML serileştirmenin bir diğer avantajı da, oluşturulan XML akışı belirli bir şemaya uygun olduğu sürece, geliştirdiğiniz uygulamalarüzerinde herhangi bir kısıtlama olmamasıdır. Books tanımlamak için kullanılan bir şema düşünün. Bir başlık özelliklerini, yazarın, yayımcı ve ISBN öğe sayısı. Örneğin, bir kitap düzeni veya books envanterini olarak istediğiniz herhangi bir şekilde XML verileri işleyen bir uygulama geliştirebilirsiniz. Her iki durumda da, tek gereksinim XML akışının belirtilen XML Şema tanım dili (XSD) şemasına uygun olmasıdır.

## <a name="xml-serialization-considerations"></a>XML serileştirme konuları

**XmlSerializer** sınıfı kullanırken aşağıdakiler göz önünde bulundurulmalıdır:

- Sgen.exe aracı açıkça en iyi performans için serileştirme derlemelerini oluşturmak üzere tasarlanmıştır.

- Serileştirilmiş veriler yalnızca verilerin kendisini ve sınıflarınızın yapısını içerir. Türü kimlik ve derleme bilgiler dahil değildir.

- Yalnızca genel özelliklerini ve alanları seri hale getirilebilir. Özellikler ortak erişimciler olmalıdır (almanıza ve ayarlamanıza yöntemleri). Genel olmayan verileri seri gerekir, kullanın <xref:System.Runtime.Serialization.DataContractSerializer> sınıfının XML serileştirme değil.

- Bir sınıfın **XmlSerializer**tarafından serihale getirilebilmek için parametresiz bir oluşturucusu olmalıdır.

- Yöntemleri seri hale getirilemiyor.

- **XmlSerializer,** aşağıdaki gibi, belirli gereksinimleri karşılıyorsa, **IEnumerable** veya **ICollection'ı** farklı şekilde uygulayan sınıfları işleyebilir.

  **Tümevarım'ı** uygulayan bir sınıfın, tek bir parametre alan ortak bir **Ekle** yöntemini uygulaması gerekir. **Add** yönteminin parametresi, **IEnumerator.Current** özelliği **GetEnumerator** yönteminden döndürülen türle tutarlı (polimorfik) olmalıdır.

  **IEnumerable** 'a **(CollectionBase**gibi) ek olarak **ICollection** uygulayan bir sınıfın, bir tamsayı alan ortak **Öğe** dizineli özelliği (C#'da bir dizinleyici) olması ve tür **tamsayı**ortak **Sayısı** özelliğine sahip olması gerekir. **Ekle** metoduna geçirilen parametre, **Öğe** özelliğinden döndürülen türle veya bu türdeki tabanlardan biri olmalıdır.

  **ICollection**uygulayan sınıflar için, seri hale getirilecek değerler **GetEnumerator'u**aramak yerine dizine eklenmiş **Öğe** özelliğinden alınır. Ayrıca, başka bir koleksiyon sınıfı döndüren ortak alanlar **(ICollection**uygulayan lar) dışında, ortak alanlar ve özellikler serileştirilmez. Örneğin, [Bkz. XML Serileştirme Örnekleri.](examples-of-xml-serialization.md)

## <a name="xsd-data-type-mapping"></a>XSD veri türü eşlemesi

[XML Şema Bölüm 2: Datatypes](https://www.w3.org/TR/xmlschema-2/) başlıklı W3C belge, XML Şema tanım dili (XSD) şemasında izin verilen basit veri türlerini belirtir. Bunların çoğu için (örneğin, **int** ve **ondalık),**.NET Framework'de karşılık gelen bir veri türü vardır. Ancak, bazı XML veri türlerinin .NET Framework'de (örneğin, **NMTOKEN** veri türü) karşılık gelen bir veri türü yoktur. Bu gibi durumlarda, bir şemadan sınıflar oluşturmak için XML Şema Tanım Aracı 'nı[(XML Şema Tanım Aracı (Xsd.exe)](xml-schema-definition-tool-xsd-exe.md)kullanıyorsanız, tür dizesinin bir üyesine uygun bir öznitelik uygulanır ve **DataType** özelliği XML veri türü adına ayarlanır. Örneğin, bir şema XML veri türü **NMTOKEN**ile "MyToken" adlı bir öğe içeriyorsa, oluşturulan sınıf aşağıdaki örnekte gösterildiği gibi bir üye içerebilir.

```vb
<XmlElement(DataType:="NMTOKEN")> _
Public MyToken As String
```

```csharp
[XmlElement(DataType = "NMTOKEN")]
public string MyToken;
```

Benzer şekilde, belirli bir XML Şemasına (XSD) uyması gereken bir sınıf oluşturuyorsanız, uygun özniteliği uygulamalı ve **DataType** özelliğini istenen XML veri türü adına ayarlamanız gerekir.

Tür eşlemelerinin tam listesi için, aşağıdaki öznitelik sınıflarından herhangi biri için **DataType** özelliğine bakın:

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
- [XML ve SOAP Serileştirme](xml-and-soap-serialization.md)
- [İkili Serileştirme](binary-serialization.md)
- [Serileştirme](index.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [XML Serileştirme Örnekleri](examples-of-xml-serialization.md)
- [Nasıl yapılır: Nesne Serileştirme](how-to-serialize-an-object.md)
- [Nasıl yapılır: Nesneyi Seri Durumdan Çıkarma](how-to-deserialize-an-object.md)
