---
title: "Giriş XML serileştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 13afeecc979cab9719ffa063f78ff91c866262d3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="introducing-xml-serialization"></a>Giriş XML serileştirme
Seri hale getirme taşımalarına taşınan bir forma bir nesne dönüştürme işlemidir. Örneğin, bir nesneyi serileştirme ve bir istemci ve sunucu arasında HTTP kullanarak Internet üzerinden aktarım. Diğer tarafta akıştan nesne seri durumdan çıkarma yeniden yapılandırır.  
  
 XML serileştirme yalnızca genel alanlar ve nesnenin özellik değerlerini bir XML akışa serileştirir. XML serileştirme türü bilgilerini içermez. Örneğin, bir **defteri** var. nesne **Kitaplığı** ad alanı, aynı türde bir nesnenin seri durumda garantisi yoktur.  
  
> [!NOTE]
>  XML serileştirme yöntemleri, Dizinleyicileri, özel alanları veya salt okunur özelliklerini (dışında salt okunur koleksiyonlar) dönüştürmez. Bir nesnenin tüm alanları ve özellikleri serileştirmek için ve ortak ve özel, kullanın <xref:System.Runtime.Serialization.DataContractSerializer> XML serileştirme yerine.  
  
 XML serileştirme, merkezi bir sınıftır <xref:System.Xml.Serialization.XmlSerializer> sınıfı ve bu sınıfın en önemli yöntemlere **serileştirme** ve **Deserialize** yöntemleri. <xref:System.Xml.Serialization.XmlSerializer> C# dosyaları oluşturur ve bunları bu serileştirme gerçekleştirmek için .dll dosyalarıyla derler. .NET Framework 2. 0'da, [XML seri hale getirici Oluşturma Aracı (Sgen.exe)](../../../docs/standard/serialization/xml-serializer-generator-tool-sgen-exe.md) önceden uygulamanız ile dağıtılması ve başlangıç performansı artırmak için bu serileştirme derlemelerini oluşturmak üzere tasarlanmıştır. Tarafından oluşturulan XML akışı **XmlSerializer** World Wide Web Konsorsiyumu (www.w3.org) XML Şeması Tanım Dili (XSD) 1.0 ile uyumlu öneri. Ayrıca, oluşturulan veri türleri başlıklı belge ile uyumludur "XML şema bölüm 2: veri türleri."  
  
 Nesnelerinizi verilerde biçiminde sınıfları, alanları, özellikleri, ilkel türler, dizileri ve hatta katıştırılmış XML gibi programlama dil yapıları kullanarak açıklanan **XmlElement** veya **XmlAttribute**nesneleri. Özniteliklerle, açıklama, kendi sınıflarınızı oluşturma seçeneğiniz vardır veya varolan bir XML şemasını temel alan sınıfları oluşturmak için XML şema tanımı aracını kullanarak.  
  
 Bir XML şeması varsa, XML şema tanımı aracı kesinlikle şemaya yazılan ve öznitelikleri ile Açıklama sınıfları kümesi üretmek için çalıştırabilirsiniz. Bu tür bir sınıfının bir örneğini serileştirilmiş olduğunda, oluşturulan XML için XML Şeması uyar. Bu tür bir sınıf ile programlayabileceğiniz sağlanan kolay yönetilebilen nesne modeli olan sırasında oluşturulan XML XML şemaya uygun olduğunu garanti. Bu diğer sınıflar .NET Framework'teki gibi bir alternatifidir **XmlReader** ve **XmlWriter** ayrıştırma ve bir XML akışı yazmak için sınıfları. Daha fazla bilgi için bkz: [XML belgeler ve veriler](../../../docs/standard/data/xml/index.md). Bu sınıfların herhangi XML akışı ayrıştırma olanak sağlar. Buna karşılık, kullanın **XmlSerializer** zaman XML akışı beklenmektedir bilinen bir XML Şeması uymak için.  
  
 Öznitelikleri tarafından oluşturulan XML akışı kontrol **XmlSerializer** XML ad alanı, öğe adı, öznitelik adı ve XML akışı, belirli bir benzeri ayarlamanıza olanak sağlayan sınıf. Bu öznitelikler ve bunların nasıl XML serileştirme kontrol hakkında daha fazla bilgi için bkz: [XML serileştirme kullanarak özniteliklerini denetleme](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md). Oluşturulan XML denetlemek için kullanılan özniteliklerle tablo için bkz: [öznitelikleri, Denetim XML serileştirme](../../../docs/standard/serialization/attributes-that-control-xml-serialization.md).  
  
 **XmlSerializer** sınıfı, başka bir nesneyi serileştirme ve kodlanmış bir SOAP XML Akışı Oluştur. Oluşturulan XML "Basit Nesne Erişim Protokolü (SOAP) 1.1." başlıklı bölümüne World Wide Web Consortium belgesinin 5 uyar Bu işlem hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir SOAP-Encoded XML akışı olarak bir nesneyi serileştirme](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md). Oluşturulan XML denetim öznitelikleri tablo için bkz: [öznitelikleri, Denetim kodlanmış SOAP seri hale getirme](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).  
  
 **XmlSerializer** sınıfı tarafından oluşturulan ve XML Web Hizmetleri için geçirilen SOAP iletileri oluşturur. SOAP iletilerine denetlemek için sınıflar, dönüş değerleri, parametreler ve XML Web hizmeti dosyasında (.asmx) bulunan alanları öznitelikleri uygulayabilirsiniz. XML Web Hizmetleri da değişmez değer veya kodlanmış SOAP stili kullanabileceğinizden "Öznitelikleri, Denetim XML serileştirme" ve "Öznitelikleri, Denetim kodlanmış SOAP seri hale getirme" listelenen her iki öznitelik kullanabilirsiniz. XML Web hizmeti tarafından oluşturulan XML denetlemek için öznitelikleri kullanma hakkında daha fazla bilgi için bkz: [XML serileştirme XML Web Hizmetleri ile](../../../docs/standard/serialization/xml-serialization-with-xml-web-services.md). SOAP ve XML Web Hizmetleri hakkında daha fazla bilgi için bkz: [özelleştirme SOAP iletilerine](https://msdn.microsoft.com/en-us/subscriptions/index/dkwy2d72\(v=vs.71\).aspx).  
  
## <a name="security-considerations-for-xmlserializer-applications"></a>XmlSerializer uygulamalar için güvenlik hususları  
 Bir uygulama oluşturma kullandığında **XmlSerializer**, aşağıdaki öğeleri ve bunların etkileri bilincinde olmanız gerekir:  
  
-   **XmlSerializer** C# oluşturur (.cs) dosyaları ve bunları TEMP ortam değişkeni tarafından adlandırılan dizin .dll dosyaları içine derler; seri hale getirme ile bu DLL'ler oluşur.  
  
    > [!NOTE]
    >  Bu seri hale getirme derlemeler önceden oluşturulur ve SGen.exe aracını kullanarak oturum açmış. Bu, bir Web Hizmetleri sunucusu çalışmıyor. Diğer bir deyişle, yalnızca istemci kullanımı için ve el ile serileştirme içindir.  
  
     Kod ve DLL'leri oluşturma ve derleme sırasındaki kötü amaçlı bir işleme etkilenir. Microsoft Windows NT 4.0 veya sonraki sürümü çalıştıran bir bilgisayara kullanırken, TEMP dizinini paylaşmak iki veya daha fazla kullanıcı için olası olabilir. TEMP dizini paylaşımı tehlikeli iki hesap farklı güvenlik ayrıcalıkları varsa ve daha yüksek ayrıcalıklı hesap kullanarak bir uygulama çalıştıran **XmlSerializer**. Bu durumda, bir kullanıcı derlenmiş olup .cs veya .dll dosya değiştirerek bilgisayarın güvenlik ihlal. Bu sorunu gidermek için her zaman her bilgisayar hesabında kendi profili sahip olduğundan emin olun. Varsayılan olarak, her hesap için farklı bir dizin TEMP ortam değişkeni gösteriyor.  
  
-   Kötü niyetli bir kullanıcının bir Web sunucusu (bir hizmet reddi saldırısına), sürekli bir XML veri akışı gönderiyorsa ardından **XmlSerializer** bilgisayar kaynakları azalıyor kadar veri işlemeye devam eder.  
  
     Internet Information Services (IIS) çalıştıran bir bilgisayara kullandığınız ve uygulamanızı IIS içinde çalışıyorsa bu tür bir saldırıya ortadan kaldırıldı. IIS (varsayılan 4 KB'tır) kümesi miktardan daha uzun akışlarını işlemiyor bir ağ geçidi özellikleri. IIS kullanmaz ve ile çıkarır bir uygulama oluşturursanız **XmlSerializer**, bir hizmet reddi saldırısına engeller benzer bir ağ geçidi uygulaması gerekir.  
  
-   **XmlSerializer** verileri serileştirir ve kendisine verilen herhangi bir tür kullanarak herhangi bir kod çalıştırır.  
  
     Kötü amaçlı bir nesne bir iş parçacığı sayısını gösterir iki yolu vardır. Kötü amaçlı kod çalıştırabilir ya da kötü amaçlı kod tarafından oluşturulan C# dosyasına ekleyebilir **XmlSerializer**. Kötü amaçlı nesnesini yıkıcı bir yordamı çalıştırmayı denediğinde ilk durumda kod erişim güvenliği, herhangi bir zarar gerçekleştirilen gelen önlemeye yardımcı olur. İkinci durumda, kötü amaçlı nesnesini şekilde kod tarafından oluşturulan C# dosyasına yerleştirir, teorik olasılığı vardır **XmlSerializer**. Bu sorunu tamamen incelenmesi ve böyle bir saldırının tahmin edilemez olarak değerlendirilir, ancak hiçbir zaman verileri bilinmeyen ve güvenilir olmayan bir tür ile seri hale getirme önlemleri.  
  
-   Serileştirilmiş hassas verileri açık olabilir.  
  
     Sonra **XmlSerializer**verileri seri hale getirilmiş bir XML dosyası veya diğer veri deposu depolanabilir. Data store diğer işlemler için kullanılabilir veya bir intranet veya Internet üzerinde görünür, veriler çalınması ve kötü amaçlı olarak kullanılan. Örneğin, bir uygulama oluşturursanız, siparişler serileştiren kredi kartı numaraları dahil, veri yüksek oranda duyarlıdır. Bunu önlemek için her zaman için veri deposu korumak ve özel olarak saklamak için adımları izleyin.  
  
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
  
 Daha fazla seri hale getirme örnekleri için bkz: [XML serileştirme örnekler](../../../docs/standard/serialization/examples-of-xml-serialization.md).  
  
## <a name="items-that-can-be-serialized"></a>Seri hale öğeleri  
 Aşağıdaki öğeler kullanarak seri hale **XmLSerializer** sınıfı:  
  
-   Ortak okuma/yazma özellikleri ve ortak sınıfların alanları.  
  
-   Sınıfları uygulayan **ICollection** veya **IEnumerable**.  
  
    > [!NOTE]
    >  Yalnızca koleksiyonları serileştirilmiş, ortak değil Özellikleri ' dir.  
  
-   **XmlElement** nesneleri.  
  
-   **XmlNode** nesneleri.  
  
-   **Veri kümesi** nesneleri.  
  
 Seri hale getirme veya nesneleri seri kaldırma hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir nesneyi serileştirme](../../../docs/standard/serialization/how-to-serialize-an-object.md) ve [nasıl yapılır: bir nesne seri durumdan](../../../docs/standard/serialization/how-to-deserialize-an-object.md).  
  
## <a name="advantages-of-using-xml-serialization"></a>XML Serialization kullanarak avantajları  
 **XmlSerializer**sınıfı sağlar, tam ve esnek denetim XML olarak bir nesneyi serileştirme olduğunda. XML Web Hizmetleri oluşturuyorsanız, sınıflar ve üyeleri XML çıktısı belirli bir şemaya uymasını sağlamak için serileştirme denetim öznitelikleri uygulayabilirsiniz.  
  
 Örneğin, **XmlSerializer** sağlar:  
  
-   Bir alan veya özellik bir öznitelik veya bir öğe kodlanması gereken olup olmadığını belirtin.  
  
-   Kullanmak için bir XML ad alanı belirtin.  
  
-   Bir alan veya özellik adı uygunsuz ise bir öğe veya öznitelik adını belirtin.  
  
 XML serileştirme başka bir avantajı, oluşturulan XML akışı belirli bir şemasıyla uyumlu olduğu sürece, geliştirmek, uygulamaların hiç bir kısıtlama sahip olabilir. Books tanımlamak için kullanılan bir şema düşünün. Bir başlık özelliklerini, yazarın, yayımcı ve ISBN öğe sayısı. Örneğin, bir kitap düzeni veya books envanterini olarak istediğiniz herhangi bir şekilde XML verileri işleyen bir uygulama geliştirebilirsiniz. Her iki durumda da, XML akışı belirtilen XML Şeması Tanım Dili (XSD) şemasıyla uyumlu tek gereksinimdir.  
  
## <a name="xml-serialization-considerations"></a>XML serileştirme konuları  
 Kullanırken aşağıdaki düşünülmesi gereken **XmlSerializer** sınıfı:  
  
-   Sgen.exe aracı açıkça en iyi performans için serileştirme derlemelerini oluşturmak üzere tasarlanmıştır.  
  
-   Serileştirilmiş veriler, yalnızca verileri kendisi ve sınıflarınızı yapısını içerir. Türü kimlik ve derleme bilgiler dahil değildir.  
  
-   Yalnızca genel özelliklerini ve alanları seri hale getirilebilir. Özellikler ortak erişimciler olmalıdır (almanıza ve ayarlamanıza yöntemleri). Genel olmayan verileri seri gerekir, kullanın <xref:System.Runtime.Serialization.DataContractSerializer> sınıfının XML serileştirme değil.  
  
-   Bir sınıf tarafından serileştirilmesi için varsayılan bir oluşturucu olmalıdır **XmlSerializer**.  
  
-   Yöntemleri seri hale getirilemiyor.  
  
-   **XmlSerializer** uygulayan sınıflar işleyebilir **IEnumerable** veya **ICollection** farklı bunlar belirli gereksinimleri gibi karşılaması durumunda.  
  
     Uygulayan bir sınıf **IEnumerable** ortak bir uygulamalıdır **Ekle** yönteminin tek bir parametre alan. **Ekle** yöntemin parametresi tutarlı olmalıdır (çok biçimli) döndürülen tür ile **IEnumerator.Current** döndürülen özelliği **GetEnumerator** yöntem.  
  
     Uygulayan bir sınıf **ICollection** ek olarak **IEnumerable** (gibi **CollectionBase'den**) bir ortak olmalıdır **öğesi** dizini bir tamsayı ve sürer (C# bir dizinleyici) özelliği, ortak bir olmalıdır **sayısı** türündeki özelliği **tamsayı**. Geçirilen parametre **Ekle** yöntemi döndürüldüğü aynı türde olmalıdır **öğesi** özelliği ya da bu tür tabanları biri.  
  
     İçin uygulayan sınıflar **ICollection**, serileştirilmesi için değerleri alınır dizinli gelen **öğesi** özelliği yerine çağırarak **GetEnumerator**. Ayrıca, ortak alanlar ve özellikler, başka bir koleksiyon sınıfına döndüren ortak alanlar dışında seri duruma (uygulayan bir **ICollection**). Bir örnek için bkz: [XML serileştirme örnekler](../../../docs/standard/serialization/examples-of-xml-serialization.md).  
  
## <a name="xsd-data-type-mapping"></a>XSD veri türü eşlemesi  
 "XML Şeması bölümü 2: veri türleri" başlıklı World Wide Web Consortium (www.w3.org) belge bir XML şeması tanım dili (XSD) şemasında izin verilen basit veri türlerini belirtir. Bunların çoğu için (örneğin, **int** ve **ondalık**), .NET Framework'teki karşılık gelen bir veri türü yok. Ancak, bazı XML veri türleri karşılık gelen bir veri türü .NET Framework gerekmez (örneğin, **NMTOKEN** veri türü). XML şema tanımı Aracı'nı kullanırsanız, bu gibi durumlarda ([XML şema tanımı aracını (XSD.exe'nin)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)) şemadan sınıfları oluşturmak için uygun bir öznitelik türü dizesi üyesi için uygulanır ve kendi **veritürü** özelliği, XML veri türü adına ayarlanır. Örneğin, bir şema XML veri türüyle "MyToken" adlı bir öğe içeriyorsa **NMTOKEN**, oluşturulan sınıf, aşağıdaki örnekte gösterildiği gibi bir üye içeriyor olabilir.  
  
```vb  
<XmlElement(DataType:="NMTOKEN")> _  
Public MyToken As String  
```  
  
```csharp  
[XmlElement(DataType = "NMTOKEN")]  
public string MyToken;  
```  
  
 Benzer şekilde, bir özel XML Şeması (XSD) için uyması gereken bir sınıf oluşturuyorsanız, uygun özniteliğini uygulayın ve gerekir ayarlamak kendi **DataType** özelliği istenen XML veri türü adı.  
  
 Tür eşlemeleri tam bir listesi için bkz: **DataType** özelliği aşağıdaki öznitelik sınıflarından herhangi biriyle için:  
  
-   <xref:System.Xml.Serialization.SoapAttributeAttribute>  
  
-   <xref:System.Xml.Serialization.SoapElementAttribute>  
  
-   <xref:System.Xml.Serialization.XmlArrayItemAttribute>  
  
-   <xref:System.Xml.Serialization.XmlAttributeAttribute>  
  
-   <xref:System.Xml.Serialization.XmlElementAttribute>  
  
-   <xref:System.Xml.Serialization.XmlRootAttribute>  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.Serialization.XmlSerializer>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.IO.FileStream>  
 [XML ve SOAP seri hale getirme](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
 [İkili seri hale getirme](../../../docs/standard/serialization/binary-serialization.md)  
 [Seri hale getirme](../../../docs/standard/serialization/index.md)  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [XML serileştirme örnekleri](../../../docs/standard/serialization/examples-of-xml-serialization.md)  
 [Nasıl yapılır: bir nesneyi serileştirme](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 [Nasıl yapılır: bir nesne seri durumdan](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
