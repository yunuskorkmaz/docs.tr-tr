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
<xref:System.Xml.Schema.XmlSchemaSet>XML şeması tanım DILI (xsd) şemaları depolanabilecek ve doğrulanabilen bir önbellek tanımlar.  
  
## <a name="the-xmlschemaset-class"></a>XmlSchemaSet sınıfı  
 <xref:System.Xml.Schema.XmlSchemaSet> XML şeması tanım DILI (xsd) şemaları depolanabilecek ve doğrulanabilen bir önbelleğidir.  
  
 Sürüm <xref:System.Xml?displayProperty=nameWithType> 1,0 ' de, XML şemaları bir <xref:System.Xml.Schema.XmlSchemaCollection> sınıfa bir şema kitaplığı olarak yüklenmiştir. Sürüm <xref:System.Xml?displayProperty=nameWithType> 2,0 ' de, <xref:System.Xml.XmlValidatingReader> ve <xref:System.Xml.Schema.XmlSchemaCollection> sınıfları kullanılmıyor ve sırasıyla <xref:System.Xml.XmlReader.Create%2A> Yöntemler ve <xref:System.Xml.Schema.XmlSchemaSet> sınıf ile değiştirilmiştir.  
  
 , <xref:System.Xml.Schema.XmlSchemaSet> Standart uyumluluk, performans ve kullanılmayan Microsoft XML verileri AZALTıLMıŞ (xdr) şema biçimi gibi birçok sorunu gidermeye yönelik olarak sunulmuştur.  
  
 Aşağıda, <xref:System.Xml.Schema.XmlSchemaCollection> sınıfı ve <xref:System.Xml.Schema.XmlSchemaSet> sınıfı arasında bir karşılaştırma bulunur.  
  
|XmlSchemaCollection|XmlSchemaSet|  
|-------------------------|------------------|  
|Microsoft XDR ve W3C XML şemalarını destekler.|Yalnızca W3C XML şemalarını destekler.|  
|Şemaları, <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> yöntemi çağrıldığında derlenir.|<xref:System.Xml.Schema.XmlSchemaSet.Add%2A> Yöntem çağrıldığında şemalar derlenmez. Bu, şema kitaplığının oluşturulması sırasında bir performans geliştirmesi sağlar.|  
|Her şema, "Schema Adaları" ile sonuçlanabileceğinden bağımsız bir derlenmiş sürüm oluşturur. Sonuç olarak, tüm dahil ve içeri aktarmalar yalnızca o şemanın içinde kapsamlandırılır.|Derlenmiş şemalar, şemaların "kümesi" olan tek bir mantıksal şema oluşturur. Kümesine eklenen bir şema içindeki tüm içeri aktarılan şemalar doğrudan kümesine eklenir. Bu, tüm türlerin tüm şemalarda kullanılabildiği anlamına gelir.|  
|Koleksiyonda belirli bir hedef ad alanı için yalnızca bir şema bulunabilir.|Aynı hedef ad alanı için birden çok şema, tür çakışması olmadığı sürece eklenebilir.|  
  
## <a name="migrating-to-the-xmlschemaset"></a>XmlSchemaSet 'e geçiş  
 Aşağıdaki kod örneği, eski <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaCollection> sınıftan yeni sınıfa geçiş yapmak için bir kılavuz sağlar. Kod örneği, iki sınıf arasındaki aşağıdaki önemli farklılıkları gösterir.  
  
- <xref:System.Xml.Schema.XmlSchemaCollection> Sınıfının <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> yönteminden farklı olarak,, <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> <xref:System.Xml.Schema.XmlSchemaSet>yöntemi çağrılırken şemalar derlenmez. <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> Yöntemi <xref:System.Xml.Schema.XmlSchemaSet> , örnek kodda açıkça çağırılır.  
  
- Bir <xref:System.Xml.Schema.XmlSchemaSet>üzerinde yinelemek için, öğesinin <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özelliğini kullanmanız gerekir. <xref:System.Xml.Schema.XmlSchemaSet>  
  
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
 Şemaları, <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> <xref:System.Xml.Schema.XmlSchemaSet>öğesinin yöntemi kullanılarak öğesine eklenir. Bir şema bir <xref:System.Xml.Schema.XmlSchemaSet>öğesine eklendiğinde, hedef ad alanı URI 'si ile ilişkilendirilir. Hedef ad alanı URI 'SI <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metodun bir parametresi olarak belirtilebilir ya da hiçbir hedef ad alanı belirtilmemişse, şemada tanımlanan hedef ad alanını <xref:System.Xml.Schema.XmlSchemaSet> kullanır.  
  
 Şemaları, <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> <xref:System.Xml.Schema.XmlSchemaSet>öğesinin özelliğini kullanarak bir öğesinden alınır. Öğesinin <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özelliği içinde yer <xref:System.Xml.Schema.XmlSchemaSet> alan <xref:System.Xml.Schema.XmlSchema> nesneler üzerinde yineleme yapmanızı sağlar <xref:System.Xml.Schema.XmlSchemaSet>. <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> Özelliği, veya içinde <xref:System.Xml.Schema.XmlSchemaSet>içerilen tüm <xref:System.Xml.Schema.XmlSchema> nesneleri döndürür veya hedef ad alanı parametresi verildiğinde, hedef ad alanına ait tüm <xref:System.Xml.Schema.XmlSchema> nesneleri döndürür. `null` Hedef ad alanı parametresi olarak belirtilmişse, <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özelliği ad alanı olmayan tüm şemaları döndürür.  
  
 Aşağıdaki örnek, `books.xsd` `http://www.contoso.com/books` <xref:System.Xml.Schema.XmlSchemaSet>ad alanındaki şemayı öğesine ekler, öğesinden `http://www.contoso.com/books` <xref:System.Xml.Schema.XmlSchemaSet>ad alanına ait olan tüm şemaları alır ve ardından bu şemaları öğesine yazar. <xref:System.Console>  
  
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
  
 Bir <xref:System.Xml.Schema.XmlSchemaSet> nesneden şemaları ekleme ve alma hakkında daha fazla bilgi için, bkz. <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemi ve <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özellik başvurusu belgeleri.  
  
## <a name="compiling-schemas"></a>Şemaları derleme  
 İçindeki <xref:System.Xml.Schema.XmlSchemaSet> şemalar, <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> <xref:System.Xml.Schema.XmlSchemaSet>yöntemi tarafından bir mantıksal şemaya derlenir.  
  
> [!NOTE]
> Eski <xref:System.Xml.Schema.XmlSchemaCollection> sınıftan farklı olarak, <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntem çağrıldığında şemalar derlenmez.  
  
 <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> Yöntem başarıyla yürütülüyorsa öğesinin <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> <xref:System.Xml.Schema.XmlSchemaSet> özelliği olarak `true`ayarlanır.  
  
> [!NOTE]
> İçinde <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> şemalar düzenlenirse Özellik etkilenmez <xref:System.Xml.Schema.XmlSchemaSet>. İçindeki <xref:System.Xml.Schema.XmlSchemaSet> tek tek şemaların güncelleştirmeleri izlenmez. Sonuç <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> `true` olarak, içinde <xref:System.Xml.Schema.XmlSchemaSet> bulunan şemalardan biri, ' den eklenen veya kaldırılan hiçbir şema olmadığı sürece değiştirilmiş olabilir. <xref:System.Xml.Schema.XmlSchemaSet>  
  
 Aşağıdaki örnek `books.xsd` dosyasını öğesine ekler <xref:System.Xml.Schema.XmlSchemaSet> ve sonra <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> yöntemini çağırır.  
  
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
  
 İçindeki <xref:System.Xml.Schema.XmlSchemaSet>şemaları derleme hakkında daha fazla bilgi için bkz. <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> Yöntem başvurusu belgeleri.  
  
## <a name="reprocessing-schemas"></a>Şemaları yeniden işleme  
 Bir <xref:System.Xml.Schema.XmlSchemaSet> şemanın ' de yeniden işlenmesi, <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemi <xref:System.Xml.Schema.XmlSchemaSet> çağrıldığında bir şemada gerçekleştirilen tüm ön işleme adımlarını gerçekleştirir. <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> Yöntemine yapılan çağrı başarılı olursa öğesinin <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> <xref:System.Xml.Schema.XmlSchemaSet> özelliği olarak `false`ayarlanır.  
  
 <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> Yöntemi, derleme gerçekleştirildikten sonra <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet> içindeki bir şema değiştirildiğinde kullanılmalıdır.  
  
 Aşağıdaki örnek, <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> yöntemi kullanılarak öğesine eklenen bir şemanın yeniden işlenmesini gösterir. <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> <xref:System.Xml.Schema.XmlSchemaSet> Yöntemi kullanılarak derlendikten ve öğesine eklenen şema değiştirilirse, içindeki bir şema değiştirilse bile özelliği olarak `true` <xref:System.Xml.Schema.XmlSchemaSet> ayarlanır. <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> Yöntemi <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> çağırmak yöntemi tarafından gerçekleştirilen tüm ön işleme gerçekleştirir ve <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> özelliğini olarak `false`ayarlar.  
  
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
  
 Bir şemayı bir <xref:System.Xml.Schema.XmlSchemaSet>içinde yeniden işleme hakkında daha fazla bilgi için bkz. <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> Yöntem başvurusu belgeleri.  
  
## <a name="checking-for-a-schema"></a>Şema denetleniyor  
 Bir şemanın içinde içerildiğini denetlemek <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> <xref:System.Xml.Schema.XmlSchemaSet> için ' ın metodunu kullanabilirsiniz. <xref:System.Xml.Schema.XmlSchemaSet> Yöntemi <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> , denetlenecek bir hedef ad alanı ya da <xref:System.Xml.Schema.XmlSchema> nesne alır. Her iki durumda da, <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> şema içinde `true` içerilse, yöntemi döndürür <xref:System.Xml.Schema.XmlSchemaSet>. Aksi takdirde, döndürür `false`.  
  
 Bir şemayı denetleme hakkında daha fazla bilgi için bkz. <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> Yöntem başvurusu belgeleri.  
  
## <a name="removing-schemas"></a>Şemaları kaldırma  
 <xref:System.Xml.Schema.XmlSchemaSet> Şemaları, <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> <xref:System.Xml.Schema.XmlSchemaSet>ve <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> yöntemleri kullanılarak bir öğesinden kaldırılır. <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> Yöntemi belirtilen şemayı öğesinden kaldırır <xref:System.Xml.Schema.XmlSchemaSet>, ancak <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> yöntem belirtilen şemayı ve içeri aktardığı tüm şemaları kaldırır <xref:System.Xml.Schema.XmlSchemaSet>.  
  
 Aşağıdaki örnek, bir <xref:System.Xml.Schema.XmlSchemaSet>öğesine birden çok şema eklemeyi ve sonra şemadan birini <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> ve içeri aktardığı tüm şemaları kaldırmak için yöntemini kullanmayı gösterir.  
  
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
  
 İçindeki şemaları kaldırma hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaSet>, <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> ve <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> yöntemleri başvuru belgelerine bakın.  
  
## <a name="schema-resolution-and-xsimport"></a>Şema çözünürlüğü ve xs: import  
 Aşağıdaki örneklerde, içinde verilen <xref:System.Xml.Schema.XmlSchemaSet> bir ad alanı için birden çok şema olduğunda şemaları içeri aktarma davranışı açıklanır <xref:System.Xml.Schema.XmlSchemaSet>.  
  
 Örneğin, `http://www.contoso.com` ad alanı için <xref:System.Xml.Schema.XmlSchemaSet> birden çok şema içeren bir düşünün. Aşağıdaki `xs:import` yönergeyle bir şema öğesine eklenmiştir <xref:System.Xml.Schema.XmlSchemaSet>.  
  
```xml  
<xs:import namespace="http://www.contoso.com" schemaLocation="http://www.contoso.com/schema.xsd" />  
```  
  
 URL 'den yükleyerek <xref:System.Xml.Schema.XmlSchemaSet> `http://www.contoso.com` ad alanı için bir şemayı içeri aktarmaya çalışır. `http://www.contoso.com/schema.xsd` İçindeki `http://www.contoso.com` ad alanı için başka bir şema belgesi olsa da, yalnızca şema belgesinde belirtilen şema bildirimi ve türleri içeri aktarma şemasında kullanılabilir <xref:System.Xml.Schema.XmlSchemaSet>. `schema.xsd` Dosya `http://www.contoso.com/schema.xsd` URL 'de bulunamıyorsa, `http://www.contoso.com` ad alanı için bir şema içeri aktarma şemasına içeri aktarılmaz.  
  
## <a name="validating-xml-documents"></a>XML belgelerini doğrulama  
 XML belgeleri, içindeki şemalara karşı doğrulanabilir <xref:System.Xml.Schema.XmlSchemaSet>. <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.XmlReaderSettings.Schemas%2A> Bir <xref:System.Xml.XmlReaderSettings> nesnenin özelliğine bir şema ekleyerek veya bir <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.XmlReaderSettings.Schemas%2A> <xref:System.Xml.XmlReaderSettings> nesnenin özelliğine bir nesne ekleyerek bir XML belgesini doğrularsınız. Daha <xref:System.Xml.XmlReaderSettings> sonra nesnesi, <xref:System.Xml.XmlReader.Create%2A> <xref:System.Xml.XmlReader> sınıfının YÖNTEMI tarafından bir <xref:System.Xml.XmlReader> nesne oluşturmak ve XML belgesini doğrulamak için kullanılır.  
  
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
