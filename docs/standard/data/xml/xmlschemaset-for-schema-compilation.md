---
title: Şema Derleme için XmlSchemaSet
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 55c4b175-3170-4071-9d60-dd5a42f79b54
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f0e05b09d5ce788b9a3da262d5890a0694b49375
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969026"
---
# <a name="xmlschemaset-for-schema-compilation"></a>Şema Derleme için XmlSchemaSet
<xref:System.Xml.Schema.XmlSchemaSet>XML şeması tanım dili (xsd) şemaları depolanabilecek ve doğrulanabilen bir önbellek tanımlar.  
  
## <a name="the-xmlschemaset-class"></a>XmlSchemaSet sınıfı  
 <xref:System.Xml.Schema.XmlSchemaSet> XML şeması tanım dili (xsd) şemaları depolanabilecek ve doğrulanabilen bir önbelleğidir.  
  
 Sürüm <xref:System.Xml?displayProperty=nameWithType> 1,0 ' de, XML şemaları bir <xref:System.Xml.Schema.XmlSchemaCollection> sınıfa bir şema kitaplığı olarak yüklenmiştir. Sürüm <xref:System.Xml?displayProperty=nameWithType> 2,0 <xref:System.Xml.Schema.XmlSchemaCollection> <xref:System.Xml.XmlReader.Create%2A> ' de, <xref:System.Xml.Schema.XmlSchemaSet> ve sınıfları kullanılmıyor ve sırasıyla Yöntemler ve sınıf ile değiştirilmiştir. <xref:System.Xml.XmlValidatingReader>  
  
 , <xref:System.Xml.Schema.XmlSchemaSet> Standart uyumluluk, performans ve kullanılmayan Microsoft XML verileri azaltılmış (xdr) şema biçimi gibi birçok sorunu gidermeye yönelik olarak sunulmuştur.  
  
 Aşağıda, <xref:System.Xml.Schema.XmlSchemaCollection> sınıfı <xref:System.Xml.Schema.XmlSchemaSet> ve sınıfı arasında bir karşılaştırma bulunur.  
  
|XmlSchemaCollection|XmlSchemaSet|  
|-------------------------|------------------|  
|Microsoft XDR ve W3C XML şemalarını destekler.|Yalnızca W3C XML şemalarını destekler.|  
|Şemaları, <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> yöntemi çağrıldığında derlenir.|<xref:System.Xml.Schema.XmlSchemaSet.Add%2A> Yöntem çağrıldığında şemalar derlenmez. Bu, şema kitaplığının oluşturulması sırasında bir performans geliştirmesi sağlar.|  
|Her şema, "Schema Adaları" ile sonuçlanabileceğinden bağımsız bir derlenmiş sürüm oluşturur. Sonuç olarak, tüm dahil ve içeri aktarmalar yalnızca o şemanın içinde kapsamlandırılır.|Derlenmiş şemalar, şemaların "kümesi" olan tek bir mantıksal şema oluşturur. Kümesine eklenen bir şema içindeki tüm içeri aktarılan şemalar doğrudan kümesine eklenir. Bu, tüm türlerin tüm şemalarda kullanılabildiği anlamına gelir.|  
|Koleksiyonda belirli bir hedef ad alanı için yalnızca bir şema bulunabilir.|Aynı hedef ad alanı için birden çok şema, tür çakışması olmadığı sürece eklenebilir.|  
  
## <a name="migrating-to-the-xmlschemaset"></a>XmlSchemaSet 'e geçiş  
 Aşağıdaki kod örneği, eski <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaCollection> sınıftan yeni sınıfa geçiş yapmak için bir kılavuz sağlar. Kod örneği, iki sınıf arasındaki aşağıdaki önemli farklılıkları gösterir.  
  
- Sınıfının yönteminden farklı olarak <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> ,, <xref:System.Xml.Schema.XmlSchemaSet>yöntemi çağrılırken şemalar derlenmez. <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> <xref:System.Xml.Schema.XmlSchemaCollection> <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> Yöntemi<xref:System.Xml.Schema.XmlSchemaSet> , örnek kodda açıkça çağırılır.  
  
- Bir <xref:System.Xml.Schema.XmlSchemaSet>üzerinde yinelemek için, öğesinin <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> <xref:System.Xml.Schema.XmlSchemaSet>özelliğini kullanmanız gerekir.  
  
 Eski <xref:System.Xml.Schema.XmlSchemaCollection> kod örneği aşağıda verilmiştir.  
  
```vb  
Dim schemaCollection As XmlSchemaCollection = New XmlSchemaCollection()  
schemaCollection.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd")  
schemaCollection.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
  
Dim schema As XmlSchema  
  
For Each schema in schemaCollection  
  
   Console.WriteLine(schema.TargetNamespace)  
  
Next  
```  
  
```csharp  
XmlSchemaCollection schemaCollection = new XmlSchemaCollection();  
schemaCollection.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd");  
schemaCollection.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
  
foreach(XmlSchema schema in schemaCollection)  
{  
   Console.WriteLine(schema.TargetNamespace);  
}  
```  
  
 Aşağıda eşdeğer <xref:System.Xml.Schema.XmlSchemaSet> kod örneği verilmiştir.  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd")  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
schemaSet.Compile()  
  
Dim schema As XmlSchema  
  
For Each schema in schemaSet.Schemas()  
  
   Console.WriteLine(schema.TargetNamespace)  
  
Next  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd");  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
schemaSet.Compile();  
  
foreach(XmlSchema schema in schemaSet.Schemas())  
{  
   Console.WriteLine(schema.TargetNamespace);  
}  
```  
  
## <a name="adding-and-retrieving-schemas"></a>Şemaları ekleme ve alma  
 Şemaları, <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> öğesininyöntemi<xref:System.Xml.Schema.XmlSchemaSet>kullanılarak öğesine eklenir. Bir şema bir <xref:System.Xml.Schema.XmlSchemaSet>öğesine eklendiğinde, hedef ad alanı URI 'si ile ilişkilendirilir. Hedef ad alanı URI 'si <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metodun bir parametresi olarak belirtilebilir ya da hiçbir hedef ad alanı belirtilmemişse <xref:System.Xml.Schema.XmlSchemaSet> , şemada tanımlanan hedef ad alanını kullanır.  
  
 Şemaları, <xref:System.Xml.Schema.XmlSchemaSet> öğesinin<xref:System.Xml.Schema.XmlSchemaSet>özelliğini kullanarak bir <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> öğesinden alınır. Öğesinin özelliği içinde yeralan<xref:System.Xml.Schema.XmlSchema> nesneler üzerinde yineleme yapmanızı sağlar.<xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> Özelliği, veya içinde <xref:System.Xml.Schema.XmlSchema> <xref:System.Xml.Schema.XmlSchemaSet>içerilen tüm nesneleri döndürür veya hedef ad alanı parametresi verildiğinde, hedef ad alanına ait tüm <xref:System.Xml.Schema.XmlSchema> nesneleri döndürür. <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> Hedef ad alanı parametresi olarak belirtilmişse <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> , özelliği ad alanı olmayan tüm şemaları döndürür. `null`  
  
 Aşağıdaki örnek, `http://www.contoso.com/books` ad alanındaki `books.xsd` şemayı öğesine <xref:System.Xml.Schema.XmlSchemaSet>ekler `http://www.contoso.com/books` , <xref:System.Xml.Schema.XmlSchemaSet> öğesinden<xref:System.Console>ad alanına ait olan tüm şemaları alır ve ardından bu şemaları öğesine yazar.  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet  
schemaSet.Add("http://www.contoso.com/books", "books.xsd")  
  
Dim schema As XmlSchema  
  
For Each schema In schemaSet.Schemas("http://www.contoso.com/books")  
  
   schema.Write(Console.Out)  
  
Next  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/books", "books.xsd");  
  
foreach (XmlSchema schema in schemaSet.Schemas("http://www.contoso.com/books"))  
{  
   schema.Write(Console.Out);  
}  
```  
  
 Bir <xref:System.Xml.Schema.XmlSchemaSet> nesneden şemaları ekleme ve alma hakkında daha fazla bilgi için, <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> bkz. yöntemi ve <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özellik başvurusu belgeleri.  
  
## <a name="compiling-schemas"></a>Şemaları derleme  
 İçindeki <xref:System.Xml.Schema.XmlSchemaSet> şemalar <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> ,<xref:System.Xml.Schema.XmlSchemaSet>yöntemi tarafından bir mantıksal şemaya derlenir.  
  
> [!NOTE]
> Eski <xref:System.Xml.Schema.XmlSchemaCollection> sınıftan farklı olarak, <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntem çağrıldığında şemalar derlenmez.  
  
 Yöntem başarıyla <xref:System.Xml.Schema.XmlSchemaSet> yürütülüyorsa öğesinin `true`özelliği olarak ayarlanır. <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A>  
  
> [!NOTE]
> İçinde şemalar düzenlenirse <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> Özellik etkilenmez <xref:System.Xml.Schema.XmlSchemaSet>. İçindeki <xref:System.Xml.Schema.XmlSchemaSet> tek tek şemaların güncelleştirmeleri izlenmez. Sonuç <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> <xref:System.Xml.Schema.XmlSchemaSet>olarak, içinde<xref:System.Xml.Schema.XmlSchemaSet> bulunan şemalardan biri, ' den eklenen veya kaldırılan hiçbir şema olmadığı sürece değiştirilmiş olabilir. `true`  
  
 Aşağıdaki örnek `books.xsd` dosyasını <xref:System.Xml.Schema.XmlSchemaSet> öğesine ekler ve sonra <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> yöntemini çağırır.  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
schemaSet.Add("http://www.contoso.com/books", "books.xsd")  
schemaSet.Compile()  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/books", "books.xsd");  
schemaSet.Compile();  
```  
  
 İçindeki <xref:System.Xml.Schema.XmlSchemaSet>şemaları derleme hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> bkz. Yöntem başvurusu belgeleri.  
  
## <a name="reprocessing-schemas"></a>Şemaları yeniden işleme  
 Bir <xref:System.Xml.Schema.XmlSchemaSet> şemanın ' de yeniden işlenmesi, <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemi <xref:System.Xml.Schema.XmlSchemaSet> çağrıldığında bir şemada gerçekleştirilen tüm ön işleme adımlarını gerçekleştirir. <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> Yöntemine yapılan çağrı başarılı <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> olursa öğesinin <xref:System.Xml.Schema.XmlSchemaSet> özelliği olarak `false`ayarlanır.  
  
 Yöntemi, derleme gerçekleştirildikten sonra <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet> içindeki bir şema değiştirildiğinde kullanılmalıdır. <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A>  
  
 Aşağıdaki örnek, <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> yöntemi kullanılarak öğesine eklenen bir şemanın yeniden işlenmesini gösterir. <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> <xref:System.Xml.Schema.XmlSchemaSet> `true` Yöntemi kullanılarak derlendikten ve öğesine eklenen şema değiştirilirse, içindeki bir şema değiştirilse bile özelliği olarak ayarlanır. <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> Yöntemi çağırmak <xref:System.Xml.Schema.XmlSchemaSet.Add%2A>yöntemitarafından gerçekleştirilen tüm ön işleme gerçekleştirir ve `false` özelliğiniolarakayarlar.<xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A>  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
Dim schema As XmlSchema = schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
schemaSet.Compile()  
  
Dim element As XmlSchemaElement = New XmlSchemaElement()  
schema.Items.Add(element)  
element.Name = "book"  
element.SchemaTypeName = New XmlQualifiedName("string", "http://www.w3.org/2001/XMLSchema")  
  
schemaSet.Reprocess(schema)  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
XmlSchema schema = schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
schemaSet.Compile();  
  
XmlSchemaElement element = new XmlSchemaElement();  
schema.Items.Add(element);  
element.Name = "book";  
element.SchemaTypeName = new XmlQualifiedName("string", "http://www.w3.org/2001/XMLSchema");  
  
schemaSet.Reprocess(schema);  
```  
  
 Bir şemayı bir <xref:System.Xml.Schema.XmlSchemaSet>içinde yeniden işleme hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> bkz. Yöntem başvurusu belgeleri.  
  
## <a name="checking-for-a-schema"></a>Şema denetleniyor  
 Bir <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> şemanıniçinde<xref:System.Xml.Schema.XmlSchemaSet> içerildiğini denetlemek için ' ın metodunu kullanabilirsiniz. <xref:System.Xml.Schema.XmlSchemaSet> Yöntemi <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> , denetlenecek bir hedef ad alanı <xref:System.Xml.Schema.XmlSchema> ya da nesne alır. Her iki durumda <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> da <xref:System.Xml.Schema.XmlSchemaSet>, şema içinde `true` içerilse, yöntemi döndürür; Aksi takdirde, döndürür `false`.  
  
 Bir şemayı denetleme hakkında daha fazla bilgi için bkz <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> . Yöntem başvurusu belgeleri.  
  
## <a name="removing-schemas"></a>Şemaları kaldırma  
 <xref:System.Xml.Schema.XmlSchemaSet> Şemaları, <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> veyöntemleri<xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> kullanılarak bir öğesindenkaldırılır.<xref:System.Xml.Schema.XmlSchemaSet> Yöntemi belirtilen şemayı <xref:System.Xml.Schema.XmlSchemaSet>öğesinden kaldırır, ancak <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> yöntem belirtilen şemayı <xref:System.Xml.Schema.XmlSchemaSet>ve içeri aktardığı tüm şemaları kaldırır. <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A>  
  
 Aşağıdaki örnek, bir <xref:System.Xml.Schema.XmlSchemaSet>öğesine birden çok şema eklemeyi ve sonra şemadan birini ve içeri aktardığı tüm şemaları kaldırmak için <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> yöntemini kullanmayı gösterir.  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd")  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
schemaSet.Add("http://www.contoso.com/music", "http://www.contoso.com/music.xsd")  
  
Dim schema As XmlSchema  
  
For Each schema In schemaSet.Schemas()  
  
   If schema.TargetNamespace = "http://www.contoso.com/music" Then  
      schemaSet.RemoveRecursive(schema)  
   End If  
  
Next  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd");  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
schemaSet.Add("http://www.contoso.com/music", "http://www.contoso.com/music.xsd");  
  
foreach (XmlSchema schema in schemaSet.Schemas())  
{  
   if (schema.TargetNamespace == "http://www.contoso.com/music")  
   {  
      schemaSet.RemoveRecursive(schema);  
   }  
}  
```  
  
 İçindeki <xref:System.Xml.Schema.XmlSchemaSet>şemaları kaldırma hakkında daha fazla bilgi için, <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> ve <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> yöntemleri başvuru belgelerine bakın.  
  
## <a name="schema-resolution-and-xsimport"></a>Şema çözünürlüğü ve xs: import  
 Aşağıdaki örneklerde, <xref:System.Xml.Schema.XmlSchemaSet>içinde verilen <xref:System.Xml.Schema.XmlSchemaSet> bir ad alanı için birden çok şema olduğunda şemaları içeri aktarma davranışı açıklanır.  
  
 Örneğin, `http://www.contoso.com` ad alanı için <xref:System.Xml.Schema.XmlSchemaSet> birden çok şema içeren bir düşünün. Aşağıdaki `xs:import` yönergeyle bir şema <xref:System.Xml.Schema.XmlSchemaSet>öğesine eklenmiştir.  
  
```xml  
<xs:import namespace="http://www.contoso.com" schemaLocation="http://www.contoso.com/schema.xsd" />  
```  
  
 URL'den`http://www.contoso.com/schema.xsd` yükleyerek `http://www.contoso.com` ad alanı için bir şemayı içeri aktarmaya çalışır.<xref:System.Xml.Schema.XmlSchemaSet> İçindeki ad`http://www.contoso.com` alanı için başka bir şema belgesi olsa da, yalnızca şema belgesinde belirtilen şema bildirimi ve türleri içeri aktarma şemasında kullanılabilir. <xref:System.Xml.Schema.XmlSchemaSet> Dosya URL 'de bulunamıyorsa`http://www.contoso.com` , ad alanı için bir şema içeri aktarma şemasına içeri aktarılmaz. `http://www.contoso.com/schema.xsd` `schema.xsd`  
  
## <a name="validating-xml-documents"></a>XML belgelerini doğrulama  
 XML belgeleri, içindeki <xref:System.Xml.Schema.XmlSchemaSet>şemalara karşı doğrulanabilir. Bir <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.XmlReaderSettings.Schemas%2A> nesneninözelliğinebirşema<xref:System.Xml.Schema.XmlSchemaSet> ekleyerek veya bir nesnenin<xref:System.Xml.XmlReaderSettings> özelliğine bir nesne ekleyerek bir XML belgesini doğrularsınız. <xref:System.Xml.XmlReaderSettings.Schemas%2A> <xref:System.Xml.XmlReaderSettings> Daha sonra <xref:System.Xml.XmlReader.Create%2A> <xref:System.Xml.XmlReader> nesnesi, sınıfının yöntemi tarafından bir <xref:System.Xml.XmlReader> nesne oluşturmak ve XML belgesini doğrulamak için kullanılır. <xref:System.Xml.XmlReaderSettings>  
  
 XML belgelerinin bir <xref:System.Xml.Schema.XmlSchemaSet>kullanarak doğrulanması hakkında daha fazla bilgi için bkz. [XmlSchemaSet ile XML şeması (xsd) doğrulaması](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Schema.XmlSchemaSet.Add%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A>
- [Şema önbelleği olarak XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [XmlSchemaSet ile XML Şeması (XSD) Doğrulaması](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md)
