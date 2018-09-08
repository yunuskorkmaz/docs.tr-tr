---
title: XML serileştirmeye giriş
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
ms.openlocfilehash: 805a495790266b34ede030b76fbd83e6f172ceaf
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44206123"
---
# <a name="introducing-xml-serialization"></a>XML serileştirmeye giriş

Seri hale getirme kolayca taşınan bir forma bir nesne dönüştürme işlemidir. Örneğin, bir nesneyi serileştirip ve bir istemci ve sunucu arasında HTTP kullanarak Internet üzerinden aktarım. Diğer tarafta akıştan nesne seri durumundan çıkarma yeniden oluşturur.

 XML serileştirme yalnızca ortak alanları ve nesnenin özellik değerlerini bir XML akışa serileştirir. XML serileştirme türü bilgilerini içermez. Örneğin, bir **kitap** var nesne **Kitaplığı** ad alanı, aynı türde bir nesnede seri olmasını garanti yoktur.

> [!NOTE]
> XML serileştirme yöntemleri, Dizinleyicileri, özel alanları veya salt okunur özelliklerini (dışında salt okunur koleksiyonlar) dönüştürmez. Bir nesnenin tüm alanları ve özellikleri serileştirmek için ve ortak ve özel, kullanın <xref:System.Runtime.Serialization.DataContractSerializer> XML serileştirme yerine.

 XML serileştirme merkezi sınıfta olan <xref:System.Xml.Serialization.XmlSerializer> sınıfı ve bu sınıftaki yöntemleri en önemli **serileştirme** ve **Deserialize** yöntemleri. <xref:System.Xml.Serialization.XmlSerializer> C# dosyaları oluşturur ve bunları bu serileştirme gerçekleştirmek için .dll dosyalarıyla derler. .NET Framework 2.0 [XML serileştiricisi Oluşturma Aracı (Sgen.exe)](xml-serializer-generator-tool-sgen-exe.md) önceden uygulamanızla dağıtılması ve başlangıç performansı artırmak için bu serileştirme derlemeler oluşturmak üzere tasarlanmıştır. XML akışı tarafından oluşturulan **XmlSerializer** World Wide Web Consortium (W3C) ile uyumlu [XML Şeması Tanım Dili (XSD) 1.0 öneri](https://www.w3.org/TR/xslt). Ayrıca, oluşturulan veri türleri başlıklı belge ile uyumludur "XML şema bölüm 2: veri türleri."

 Nesnelerinizi verilerde biçiminde sınıflar, alanları, özellikler, ilkel türler, dizileri ve hatta katıştırılmış XML gibi programlama dili yapıları kullanarak açıklanan **XmlElement** veya **XmlAttribute**nesneleri. Özniteliklerle, ek açıklamalı kendi sınıflar, oluşturma seçeneğiniz vardır veya varolan bir XML şemasını temel alan sınıflar oluşturmak için XML şema tanımı aracını kullanarak.

 Bir XML şeması varsa, kesin türü belirtilmiş şemaya ve özniteliklerle ek açıklama sınıflar kümesini üretmek için XML şema tanımı aracı çalıştırabilirsiniz. Bu tür bir sınıfının bir örneğini serileştirilmiş olduğunda, oluşturulan XML için XML Şeması uyar. Bu tür bir sınıf ile programlayabileceğiniz sağlanan kolay yönetilebilen nesne modeli olan sırasında oluşturulan XML XML şemaya uygun olduğunu garanti. Bu diğer sınıflar .NET Framework gibi bir alternatifidir **XmlReader** ve **XmlWriter** sınıflar, ayrıştırma ve bir XML akışı yazar. Daha fazla bilgi için [XML belgeleri ve verileri](../../../docs/standard/data/xml/index.md). Bu sınıflar, herhangi bir XML akışı ayrıştıramadı olanak tanır. Buna karşılık, kullanın **XmlSerializer** zaman XML akışı beklenir bilinen bir XML şemaya uygun.

 Öznitelikleri ürettiği XML akışı kontrol **XmlSerializer** sınıfı, XML ad alanı, öğe adı, öznitelik adı vb., XML akışının ayarlamanızı izin verme. Bu öznitelikler ve bunların nasıl XML serileştirme kontrol hakkında daha fazla bilgi için bkz: [XML serileştirme kullanarak özniteliklerini denetleme](controlling-xml-serialization-using-attributes.md). Oluşturulan XML denetlemek için kullanılan özniteliklerle tablo için bkz: [öznitelikleri, Denetim XML serileştirme](attributes-that-control-xml-serialization.md).

 **XmlSerializer** sınıfı, başka bir nesneyi serileştirip ve bir kodlanmış SOAP XML akışı oluşturmak. Oluşturulan XML "Basit Nesne Erişim Protokolü (SOAP) 1.1." başlıklı bölümüne World Wide Web Consortium belgesinin 5 uyar Bu işlem hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir SOAP-Encoded XML Stream olarak bir nesneyi serileştirmek](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md). Oluşturulan XML denetleyen öznitelikleri tablo için bkz: [öznitelikleri, Denetim kodlanmış SOAP serileştirme](attributes-that-control-encoded-soap-serialization.md).

 **XmlSerializer** sınıfı tarafından oluşturulan ve XML Web Hizmetleri için geçirilen SOAP iletileri oluşturur. SOAP iletilerini denetlemek için sınıflar, dönüş değerleri, parametreleri ve XML Web hizmeti dosyasında (.asmx) bulunan alanları için öznitelikleri uygulayabilirsiniz. XML Web hizmeti değişmez değer veya kodlanmış SOAP stili kullanabilir olduğundan "Öznitelikleri emin denetim XML serileştirme" ve "Öznitelikleri emin denetim kodlanmış SOAP serileştirme" listelenen her iki öznitelikleri kullanabilirsiniz. Bir XML Web hizmeti tarafından oluşturulan XML denetlemek için öznitelikleri kullanma hakkında daha fazla bilgi için bkz. [XML serileştirme XML Web Hizmetleri ile](xml-serialization-with-xml-web-services.md). SOAP ve XML Web Hizmetleri hakkında daha fazla bilgi için bkz. [SOAP iletilerini özelleştirme](https://msdn.microsoft.com/en-us/subscriptions/index/dkwy2d72\(v=vs.71\).aspx).

## <a name="security-considerations-for-xmlserializer-applications"></a>XmlSerializer uygulamalar için güvenlik hususları

Bir uygulama oluşturma kullandığında **XmlSerializer**, aşağıdaki öğeleri ve bunların etkileri farkında olmalıdır:

- **XmlSerializer** oluşturur C# (.cs) dosyaları ve bunları TEMP ortam değişkeni tarafından adlı dizinindeki .dll dosyaları içine derler; serileştirme ile bu DLL'leri oluşur.

  > [!NOTE]
  > Bu seri hale getirme derlemeler önceden oluşturulur ve SGen.exe aracını kullanarak oturum açmış. Bu, bir Web Hizmetleri sunucusu çalışmıyor. Diğer bir deyişle, yalnızca istemci kullanımı için ve el ile serileştirme içindir.

  Kod ve DLL'leri oluşturma ve derleme sırasındaki kötü amaçlı bir işleme etkilenir. Microsoft Windows NT 4.0 veya sonraki sürümü çalıştıran bir bilgisayara kullanırken, TEMP dizinini paylaşmak iki veya daha fazla kullanıcı için olası olabilir. TEMP dizinini paylaşımı tehlikeli iki hesap farklı güvenlik ayrıcalıkları varsa ve daha yüksek ayrıcalıklı hesabı kullanarak uygulama çalışır **XmlSerializer**. Bu durumda, bir kullanıcı derlenmiş olup .cs veya .dll dosya değiştirerek bilgisayarın güvenlik ihlal. Bu sorunu gidermek için her zaman her bilgisayar hesabında kendi profili sahip olduğundan emin olun. Varsayılan olarak, her hesap için farklı bir dizin TEMP ortam değişkeni gösteriyor.

- Kötü niyetli bir kullanıcı, bir Web sunucusu (hizmet saldırı reddi), sürekli bir XML veri akışı gönderirse, ardından **XmlSerializer** bilgisayar kaynakları düşük çalışana kadar veri işlemeye devam eder.

  Internet Information Services (IIS) çalıştıran bir bilgisayara kullandığınız ve uygulamanızı IIS içinde çalışıyorsa bu tür bir saldırıya ortadan kaldırıldı. IIS akış (varsayılan değer 4 KB'dir) bir kümesi tutarı uzun işlemez bir ağ geçidi özellikleri. IIS kullanmaz ve ile çıkarır bir uygulama oluşturursanız **XmlSerializer**, bir saldırı hizmet reddi engelleyen benzer bir ağ geçidi uygulamalıdır.

- **XmlSerializer** verileri serileştirir ve izin verilen herhangi bir türü kullanarak herhangi bir kod çalıştırır.

  Kötü amaçlı bir nesne bir iş parçacığı sayısını gösterir iki yolu vardır. Bu kötü amaçlı kod tarafından oluşturulan C# dosyasına ekleyebilir veya kötü amaçlı kod çalıştırabilir **XmlSerializer**. Zararlı bir yordamı çalıştırmak kötü amaçlı bir nesne çalışırsa, bu durumda, kod erişim güvenliği, herhangi bir zarar bitti öğesinden önlemeye yardımcı olur. İkinci durumda, kötü amaçlı bir nesne şekilde kod tarafından oluşturulan C# dosyasına yerleştirir, teorik olasılığı yok **XmlSerializer**. Bu sorunu ayrıntılı bir şekilde incelenmesi ve bu tür bir saldırıya olası değerlendirilir olsa da, hiçbir zaman bir bilinmeyen ve güvenilmeyen türü verilerle serileştirmek önlemleri.

- Serileştirilmiş hassas verileri açık olabilir.

  Sonra **XmlSerializer**verileri seri hale getirilmiş bir XML dosyasına veya diğer veri deposu depolanabilir. Veri deponuzun diğer işlemler için kullanılabilir veya Intranet veya Internet üzerinde görülebilir, veri çalındıysa ve kötü amaçlı olarak kullanılır. Örneğin, bir uygulama oluşturursanız, siparişler serileştiren kredi kartı numaraları dahil, veri yüksek oranda duyarlıdır. Bunu önlemek için her zaman için veri deposu korumak ve özel olarak saklamak için adımları izleyin.

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

Serileştirme daha fazla örnek için bkz: [XML serileştirme örnekler](examples-of-xml-serialization.md).

## <a name="items-that-can-be-serialized"></a>Seri hale öğeleri

Aşağıdaki öğeleri kullanılarak seri hale getirilebilir **XmLSerializer** sınıfı:

- Ortak okuma/yazma özellikleri ve ortak sınıfların alanları.

- Uygulayan sınıflar **ICollection** veya **IEnumerable**.

  > [!NOTE]
  > Yalnızca koleksiyonları serileştirilmiş, ortak değil Özellikleri ' dir.

- **XmlElement** nesneleri.

- **XmlNode** nesneleri.

- **Veri kümesi** nesneleri.

 Serileştirmek veya seri kaldırma nesnelerini hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir nesneyi serileştirmek](how-to-serialize-an-object.md) ve [nasıl yapılır: bir nesnenin serisini](how-to-deserialize-an-object.md).

## <a name="advantages-of-using-xml-serialization"></a>XML Serialization kullanarak avantajları

**XmlSerializer**sınıfı size eksiksiz ve esnek denetim XML olarak bir nesne seri olduğunda. XML Web hizmeti oluşturuyorsanız, sınıf ve üyelerine XML çıktısı belirli bir şemaya uygun olduğunu emin olmak için serileştirme denetleyen öznitelikleri uygulayabilirsiniz.

Örneğin, **XmlSerializer** sağlar:

- Bir alan veya özellik bir özniteliği veya bir öğe kodlanması gereken olup olmadığını belirtin.

- Kullanmak için bir XML ad alanı belirtin.

- Bir alan veya özellik adı uygunsuz ise bir öğe veya öznitelik adı belirtin.

Başka bir XML serileştirme avantajlarından üretilir XML akışı belirli bir şemaya uygun sürece, geliştirme, uygulamaları hiçbir kısıtlamaları olmasıdır. Books tanımlamak için kullanılan bir şema düşünün. Bir başlık özelliklerini, yazarın, yayımcı ve ISBN öğe sayısı. Örneğin, bir kitap düzeni veya books envanterini olarak istediğiniz herhangi bir şekilde XML verileri işleyen bir uygulama geliştirebilirsiniz. Her iki durumda da, XML akışı belirtilen XML Şeması Tanım Dili (XSD) şemaya uygun olduğunu tek gereksinim olmasıdır.

## <a name="xml-serialization-considerations"></a>XML serileştirme konuları

Aşağıdakileri kullanarak göz önünde bulundurulması **XmlSerializer** sınıfı:

- Sgen.exe aracı açıkça en iyi performans için serileştirme derlemelerini oluşturmak üzere tasarlanmıştır.

- Serileştirilmiş veriler yalnızca verileri kendisini ve yapısı, sınıfları içerir. Türü kimlik ve derleme bilgiler dahil değildir.

- Yalnızca genel özelliklerini ve alanları seri hale getirilebilir. Özellikler ortak erişimciler olmalıdır (almanıza ve ayarlamanıza yöntemleri). Genel olmayan verileri seri gerekir, kullanın <xref:System.Runtime.Serialization.DataContractSerializer> sınıfının XML serileştirme değil.

- Bir sınıf tarafından serileştirilecek bir varsayılan oluşturucusu olmalıdır **XmlSerializer**.

- Yöntemleri seri hale getirilemiyor.

- **XmlSerializer** uygulayan sınıflar işleyebilir **IEnumerable** veya **ICollection** farklı bunlar belirli gereksinimleri gibi karşılıyorsa.

  Uygulayan bir sınıf **IEnumerable** bir ortak uygulamalıdır **Ekle** tek parametresi alan yöntemi. **Ekle** yöntemin parametresi tutarlı olmalıdır (çok biçimli) öğesinden döndürülen tür **IEnumerator.Current'ın** döndürüldüğü özelliği **GetEnumerator** yöntem.

  Uygulayan bir sınıf **ICollection** ek olarak **IEnumerable** (gibi **CollectionBase'den**) bir ortak olmalıdır **öğesi** dizini bir tamsayı alan özelliği (bir dizin oluşturucu C#) bir ortak olmalıdır **sayısı** türünün özelliği **tamsayı**. Parametre geçirilen **Ekle** yöntemi döndürülen aynı türde olmalıdır **öğesi** özelliği veya bu türün temellerine biri.

  İçin uygulayan sınıflar **ICollection**, serileştirilecek değerleri alınır dizinli öğesinden **öğesi** özelliği yerine çağırarak **GetEnumerator**. Ayrıca, genel alanlar ve özellikler, başka bir koleksiyon sınıfı döndüren ortak alanlar dışında sıralanır değil (uygulayan bir **ICollection**). Bir örnek için bkz. [XML serileştirme örnekler](examples-of-xml-serialization.md).

## <a name="xsd-data-type-mapping"></a>XSD veri türü eşlemesi

Başlıklı W3C belge [XML şema bölümü 2: veri türleri](https://www.w3.org/TR/xmlschema-2/) bir XML Şeması Tanım Dili (XSD) şemasında izin verilen basit veri türlerini belirtir. Bunların çoğu için (örneğin, **int** ve **ondalık**), .NET Framework içinde karşılık gelen bir veri türü yoktur. Ancak, bazı XML veri türleri karşılık gelen bir veri türü .NET Framework yoktur (örneğin, **NMTOKEN** veri türü). XML şema tanımı aracı kullanırsanız, bu gibi durumlarda ([XML şema tanımı Aracı (XSD.exe'nin)](xml-schema-definition-tool-xsd-exe.md)) bir şema sınıfları oluşturmak için uygun bir öznitelik türü dizesi üyesi için uygulanır ve kendi **veritürü** özelliğini XML veri türü adına ayarlayın. Örneğin, bir şema XML veri türüyle "MyToken" adlı bir öğe içeriyorsa **NMTOKEN**, oluşturulan sınıfın, aşağıdaki örnekte gösterildiği gibi bir üye içeriyor olabilir.

```vb
<XmlElement(DataType:="NMTOKEN")> _
Public MyToken As String
```

```csharp
[XmlElement(DataType = "NMTOKEN")]
public string MyToken;
```

Benzer şekilde, bir özel XML Şeması (XSD) için uymalıdır bir sınıf oluşturuyorsanız uygun özniteliğini uygulayın ve gerekir ayarlayın, **DataType** istenen XML verileri için özellik adını yazın.

Türü eşlemeleri tam bir listesi için bkz. **DataType** özelliği için herhangi bir aşağıdaki öznitelik sınıfı:

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
