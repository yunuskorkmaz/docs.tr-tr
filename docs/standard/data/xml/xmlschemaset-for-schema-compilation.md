---
title: Şema Derleme için XmlSchemaSet
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 55c4b175-3170-4071-9d60-dd5a42f79b54
ms.openlocfilehash: 55347de81c65b7390584415dd29044f4ca4ba02a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709822"
---
# <a name="xmlschemaset-for-schema-compilation"></a>Şema Derleme için XmlSchemaSet
XML şeması tanım dili (XSD) şemaları depolanabilecek ve doğrulanabilen bir önbellek <xref:System.Xml.Schema.XmlSchemaSet>açıklar.  
  
## <a name="the-xmlschemaset-class"></a>XmlSchemaSet sınıfı  
 <xref:System.Xml.Schema.XmlSchemaSet>, XML şeması tanım dili (XSD) şemaları depolanabilecek ve doğrulanabilen bir önbelleğidir.  
  
 <xref:System.Xml?displayProperty=nameWithType> sürüm 1,0 ' de, XML şemaları bir şema kitaplığı olarak bir <xref:System.Xml.Schema.XmlSchemaCollection> sınıfına yüklenmiştir. <xref:System.Xml?displayProperty=nameWithType> sürüm 2,0 ' de, <xref:System.Xml.XmlValidatingReader> ve <xref:System.Xml.Schema.XmlSchemaCollection> sınıfları kullanımdan kaldırılmıştır ve sırasıyla <xref:System.Xml.XmlReader.Create%2A> yöntemlerle ve <xref:System.Xml.Schema.XmlSchemaSet> sınıfıyla değiştirilmiştir.  
  
 <xref:System.Xml.Schema.XmlSchemaSet>, standart uyumluluk, performans ve kullanılmayan Microsoft XML-verileri azaltılmış (XDR) şema biçimi gibi birçok sorunu gidermeye yönelik olarak sunulmuştur.  
  
 <xref:System.Xml.Schema.XmlSchemaCollection> sınıfı ve <xref:System.Xml.Schema.XmlSchemaSet> sınıfı arasında bir karşılaştırma aşağıda verilmiştir.  
  
|XmlSchemaCollection|XmlSchemaSet|  
|-------------------------|------------------|  
|Microsoft XDR ve W3C XML şemalarını destekler.|Yalnızca W3C XML şemalarını destekler.|  
|<xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> yöntemi çağrıldığında şemalar derlenir.|<xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemi çağrıldığında şemalar derlenmez. Bu, şema kitaplığının oluşturulması sırasında bir performans geliştirmesi sağlar.|  
|Her şema, "Schema Adaları" ile sonuçlanabileceğinden bağımsız bir derlenmiş sürüm oluşturur. Sonuç olarak, tüm dahil ve içeri aktarmalar yalnızca o şemanın içinde kapsamlandırılır.|Derlenmiş şemalar, şemaların "kümesi" olan tek bir mantıksal şema oluşturur. Kümesine eklenen bir şema içindeki tüm içeri aktarılan şemalar doğrudan kümesine eklenir. Bu, tüm türlerin tüm şemalarda kullanılabildiği anlamına gelir.|  
|Koleksiyonda belirli bir hedef ad alanı için yalnızca bir şema bulunabilir.|Aynı hedef ad alanı için birden çok şema, tür çakışması olmadığı sürece eklenebilir.|  
  
## <a name="migrating-to-the-xmlschemaset"></a>XmlSchemaSet 'e geçiş  
 Aşağıdaki kod örneği, eski <xref:System.Xml.Schema.XmlSchemaCollection> sınıfından yeni <xref:System.Xml.Schema.XmlSchemaSet> sınıfına geçiş yapmak için bir kılavuz sağlar. Kod örneği, iki sınıf arasındaki aşağıdaki önemli farklılıkları gösterir.  
  
- <xref:System.Xml.Schema.XmlSchemaCollection> sınıfının <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> yönteminin aksine, şemalar <xref:System.Xml.Schema.XmlSchemaSet><xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemi çağrılırken derlenmez. <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> yöntemi, örnek kodda açıkça çağırılır.  
  
- Bir <xref:System.Xml.Schema.XmlSchemaSet>üzerinden yinelemek için <xref:System.Xml.Schema.XmlSchemaSet><xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özelliğini kullanmanız gerekir.  
  
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
 Şemalar, <xref:System.Xml.Schema.XmlSchemaSet><xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemi kullanılarak bir <xref:System.Xml.Schema.XmlSchemaSet> eklenir. Bir şema bir <xref:System.Xml.Schema.XmlSchemaSet>eklendiğinde, hedef ad alanı URI 'SI ile ilişkilendirilir. Hedef ad alanı URI 'SI <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemi için bir parametre olarak belirtilebilir veya hiçbir hedef ad alanı belirtilmemişse, <xref:System.Xml.Schema.XmlSchemaSet> şemada tanımlanan hedef ad alanını kullanır.  
  
 Şemalar, <xref:System.Xml.Schema.XmlSchemaSet><xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özelliğini kullanarak bir <xref:System.Xml.Schema.XmlSchemaSet> alınır. <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özelliği, <xref:System.Xml.Schema.XmlSchemaSet>bulunan <xref:System.Xml.Schema.XmlSchema> nesneleri üzerinde yineleme yapmanızı sağlar. <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özelliği, <xref:System.Xml.Schema.XmlSchemaSet>içerilen tüm <xref:System.Xml.Schema.XmlSchema> nesneleri döndürür veya hedef ad alanı parametresi verildiğinde, hedef ad alanına ait tüm <xref:System.Xml.Schema.XmlSchema> nesnelerini döndürür. `null` hedef ad alanı parametresi olarak belirtilmişse, <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özelliği ad alanı olmayan tüm şemaları döndürür.  
  
 Aşağıdaki örnek, `http://www.contoso.com/books` ad alanındaki `books.xsd` şemasını bir <xref:System.Xml.Schema.XmlSchemaSet>ekler, <xref:System.Xml.Schema.XmlSchemaSet>`http://www.contoso.com/books` ad alanına ait olan tüm şemaları alır ve ardından bu şemaları <xref:System.Console>yazar.  
  
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
  
 <xref:System.Xml.Schema.XmlSchemaSet> nesnesinden şemaları ekleme ve alma hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemine ve <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özellik başvurusu belgelerine bakın.  
  
## <a name="compiling-schemas"></a>Şemaları derleme  
 Bir <xref:System.Xml.Schema.XmlSchemaSet> şemaları, <xref:System.Xml.Schema.XmlSchemaSet><xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> yöntemi tarafından bir mantıksal şemaya derlenir.  
  
> [!NOTE]
> Eski <xref:System.Xml.Schema.XmlSchemaCollection> sınıfından farklı olarak, <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemi çağrıldığında şemalar derlenmez.  
  
 <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> yöntemi başarıyla yürütülüyorsa, <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> özelliği `true`olarak ayarlanır.  
  
> [!NOTE]
> <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> özelliği, şemalar <xref:System.Xml.Schema.XmlSchemaSet>sırada düzenleniyorsa etkilenmez. <xref:System.Xml.Schema.XmlSchemaSet> tek tek şemaların güncelleştirmeleri izlenmez. Sonuç olarak, <xref:System.Xml.Schema.XmlSchemaSet>hiçbir şema eklenmemiş veya kaldırılmadığı sürece, <xref:System.Xml.Schema.XmlSchemaSet> bulunan şemalardan biri değiştirilmiş olsa bile <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> özelliği `true` olabilir.  
  
 Aşağıdaki örnek `books.xsd` dosyasını <xref:System.Xml.Schema.XmlSchemaSet> ekler ve sonra <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> yöntemini çağırır.  
  
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
  
 <xref:System.Xml.Schema.XmlSchemaSet>şemaları derleme hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> yöntemi başvuru belgelerine bakın.  
  
## <a name="reprocessing-schemas"></a>Şemaları yeniden işleme  
 Bir <xref:System.Xml.Schema.XmlSchemaSet> şemayı yeniden işlemek, <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemi çağrıldığında bir şemada gerçekleştirilen tüm ön işleme adımlarını gerçekleştirir. <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> yöntemine yapılan çağrı başarılı olursa <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> özelliği `false`olarak ayarlanır.  
  
 <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> yöntemi, <xref:System.Xml.Schema.XmlSchemaSet> derlemeyi gerçekleştirdikten sonra <xref:System.Xml.Schema.XmlSchemaSet> bir şema değiştirildiğinde kullanılmalıdır.  
  
 Aşağıdaki örnek, <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> yöntemi kullanılarak <xref:System.Xml.Schema.XmlSchemaSet> eklenen bir şemanın yeniden işlenmesini gösterir. <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> yöntemi kullanılarak derlendikten ve <xref:System.Xml.Schema.XmlSchemaSet> eklenen şema değiştirilirse, `true` bir şema değiştirilse bile <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> özelliği <xref:System.Xml.Schema.XmlSchemaSet> olarak ayarlanır. <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> yöntemini çağırmak, <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemi tarafından gerçekleştirilen tüm ön işleme gerçekleştirir ve <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> özelliğini `false`olarak ayarlar.  
  
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
  
 Bir <xref:System.Xml.Schema.XmlSchemaSet>şemayı yeniden işleme hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> yöntemi başvuru belgelerine bakın.  
  
## <a name="checking-for-a-schema"></a>Şema denetleniyor  
 Bir şemanın bir <xref:System.Xml.Schema.XmlSchemaSet>dahil olup olmadığını denetlemek için <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> yöntemini kullanabilirsiniz. <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> yöntemi, denetlenecek bir hedef ad alanı ya da bir <xref:System.Xml.Schema.XmlSchema> nesnesi alır. Her iki durumda da, şema <xref:System.Xml.Schema.XmlSchemaSet>içindeyse <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> yöntemi `true` döndürür; Aksi takdirde, `false`döndürür.  
  
 Bir şemayı denetleme hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> yöntemi başvuru belgelerine bakın.  
  
## <a name="removing-schemas"></a>Şemaları kaldırma  
 Şemalar, <xref:System.Xml.Schema.XmlSchemaSet><xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> ve <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> yöntemleri kullanılarak bir <xref:System.Xml.Schema.XmlSchemaSet> kaldırılır. <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> yöntemi, belirtilen şemayı <xref:System.Xml.Schema.XmlSchemaSet>kaldırır, ancak <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> yöntemi belirtilen şemayı ve <xref:System.Xml.Schema.XmlSchemaSet>içeri aktardığı tüm şemaları kaldırır.  
  
 Aşağıdaki örnek, bir <xref:System.Xml.Schema.XmlSchemaSet>birden çok şema eklemeyi, sonra şemalardan birini ve içeri aktardığı tüm şemaları kaldırmak için <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> yöntemini kullanmayı gösterir.  
  
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
  
 <xref:System.Xml.Schema.XmlSchemaSet>şemaları kaldırma hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> ve <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> yöntemleri başvuru belgelerine bakın.  
  
## <a name="schema-resolution-and-xsimport"></a>Şema çözünürlüğü ve xs: import  
 Aşağıdaki örneklerde, bir <xref:System.Xml.Schema.XmlSchemaSet>verilen bir ad alanı için birden çok şema varsa şemaları içeri aktarmaya yönelik <xref:System.Xml.Schema.XmlSchemaSet> davranışı açıklanır.  
  
 Örneğin, `http://www.contoso.com` ad alanı için birden çok şema içeren bir <xref:System.Xml.Schema.XmlSchemaSet> düşünün. Aşağıdaki `xs:import` yönergesine sahip bir şema <xref:System.Xml.Schema.XmlSchemaSet>eklenmiş.  
  
```xml  
<xs:import namespace="http://www.contoso.com" schemaLocation="http://www.contoso.com/schema.xsd" />  
```  
  
 <xref:System.Xml.Schema.XmlSchemaSet>, `http://www.contoso.com/schema.xsd` URL 'sinden yükleyerek `http://www.contoso.com` ad alanı için bir şemayı içeri aktarmaya çalışır. <xref:System.Xml.Schema.XmlSchemaSet>`http://www.contoso.com` ad alanı için başka bir şema belgesi olsa da, yalnızca şema belgesinde belirtilen şema bildirimi ve türleri içeri aktarma şemasında kullanılabilir. `schema.xsd` dosyası `http://www.contoso.com/schema.xsd` URL 'sinde bulunamıyorsa, `http://www.contoso.com` ad alanı için bir şema içeri aktarma şemasına içeri aktarılmaz.  
  
## <a name="validating-xml-documents"></a>XML belgelerini doğrulama  
 XML belgeleri, bir <xref:System.Xml.Schema.XmlSchemaSet>şemalara karşı doğrulanabilir. Bir <xref:System.Xml.XmlReaderSettings> nesnesinin <xref:System.Xml.Schema.XmlSchemaSet><xref:System.Xml.XmlReaderSettings.Schemas%2A> özelliğine bir şema ekleyerek veya bir <xref:System.Xml.XmlReaderSettings.Schemas%2A> nesnesinin <xref:System.Xml.XmlReaderSettings> özelliğine bir <xref:System.Xml.Schema.XmlSchemaSet> ekleyerek bir XML belgesini doğrularsınız. <xref:System.Xml.XmlReaderSettings> nesnesi daha sonra bir <xref:System.Xml.XmlReader> nesnesi oluşturmak ve XML belgesini doğrulamak için <xref:System.Xml.XmlReader> sınıfının <xref:System.Xml.XmlReader.Create%2A> yöntemi tarafından kullanılır.  
  
 <xref:System.Xml.Schema.XmlSchemaSet>kullanarak XML belgelerinin doğrulanması hakkında daha fazla bilgi için, bkz. [XmlSchemaSet Ile xml şeması (xsd) doğrulaması](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md).  
  
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
