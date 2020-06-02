---
title: Şema Derleme için XmlSchemaSet
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 55c4b175-3170-4071-9d60-dd5a42f79b54
ms.openlocfilehash: 44850755c41b212e88e0b90dd3b016f96a0af96d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290233"
---
# <a name="xmlschemaset-for-schema-compilation"></a>Şema Derleme için XmlSchemaSet
<xref:System.Xml.Schema.XmlSchemaSet>XML şeması tanım dili (xsd) şemaları depolanabilecek ve doğrulanabilen bir önbellek tanımlar.  
  
## <a name="the-xmlschemaset-class"></a>XmlSchemaSet sınıfı  
 <xref:System.Xml.Schema.XmlSchemaSet>XML şeması tanım dili (xsd) şemaları depolanabilecek ve doğrulanabilen bir önbelleğidir.  
  
 <xref:System.Xml?displayProperty=nameWithType>Sürüm 1,0 ' de, XML şemaları bir <xref:System.Xml.Schema.XmlSchemaCollection> sınıfa bir şema kitaplığı olarak yüklenmiştir. <xref:System.Xml?displayProperty=nameWithType>Sürüm 2,0 ' de, <xref:System.Xml.XmlValidatingReader> ve <xref:System.Xml.Schema.XmlSchemaCollection> sınıfları kullanılmıyor ve <xref:System.Xml.XmlReader.Create%2A> sırasıyla Yöntemler ve sınıf ile değiştirilmiştir <xref:System.Xml.Schema.XmlSchemaSet> .  
  
 , <xref:System.Xml.Schema.XmlSchemaSet> Standart uyumluluk, performans ve kullanılmayan MICROSOFT XML verileri azaltılmış (xdr) şema biçimi gibi birçok sorunu gidermeye yönelik olarak sunulmuştur.  
  
 Aşağıda, sınıfı ve sınıfı arasında bir karşılaştırma bulunur <xref:System.Xml.Schema.XmlSchemaCollection> <xref:System.Xml.Schema.XmlSchemaSet> .  
  
|XmlSchemaCollection|XmlSchemaSet|  
|-------------------------|------------------|  
|Microsoft XDR ve W3C XML şemalarını destekler.|Yalnızca W3C XML şemalarını destekler.|  
|Şemaları, <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> yöntemi çağrıldığında derlenir.|Yöntem çağrıldığında şemalar derlenmez <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> . Bu, şema kitaplığının oluşturulması sırasında bir performans geliştirmesi sağlar.|  
|Her şema, "Schema Adaları" ile sonuçlanabileceğinden bağımsız bir derlenmiş sürüm oluşturur. Sonuç olarak, tüm dahil ve içeri aktarmalar yalnızca o şemanın içinde kapsamlandırılır.|Derlenmiş şemalar, şemaların "kümesi" olan tek bir mantıksal şema oluşturur. Kümesine eklenen bir şema içindeki tüm içeri aktarılan şemalar doğrudan kümesine eklenir. Bu, tüm türlerin tüm şemalarda kullanılabildiği anlamına gelir.|  
|Koleksiyonda belirli bir hedef ad alanı için yalnızca bir şema bulunabilir.|Aynı hedef ad alanı için birden çok şema, tür çakışması olmadığı sürece eklenebilir.|  
  
## <a name="migrating-to-the-xmlschemaset"></a>XmlSchemaSet 'e geçiş  
 Aşağıdaki kod örneği, eski sınıftan yeni sınıfa geçiş yapmak için bir kılavuz sağlar <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaCollection> . Kod örneği, iki sınıf arasındaki aşağıdaki önemli farklılıkları gösterir.  
  
- <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A>Sınıfının yönteminden farklı olarak, <xref:System.Xml.Schema.XmlSchemaCollection> , yöntemi çağrılırken şemalar derlenmez <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> <xref:System.Xml.Schema.XmlSchemaSet> . <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A>Yöntemi, <xref:System.Xml.Schema.XmlSchemaSet> örnek kodda açıkça çağırılır.  
  
- Bir üzerinde yinelemek için, <xref:System.Xml.Schema.XmlSchemaSet> öğesinin özelliğini kullanmanız gerekir <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> <xref:System.Xml.Schema.XmlSchemaSet> .  
  
 Eski kod örneği aşağıda verilmiştir <xref:System.Xml.Schema.XmlSchemaCollection> .  
  
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
 Şemaları <xref:System.Xml.Schema.XmlSchemaSet> , öğesinin yöntemi kullanılarak öğesine eklenir <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> <xref:System.Xml.Schema.XmlSchemaSet> . Bir şema bir öğesine eklendiğinde <xref:System.Xml.Schema.XmlSchemaSet> , hedef ad alanı URI 'si ile ilişkilendirilir. Hedef ad alanı URI 'SI metodun bir parametresi olarak belirtilebilir <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> ya da hiçbir hedef ad alanı belirtilmemişse, <xref:System.Xml.Schema.XmlSchemaSet> şemada tanımlanan hedef ad alanını kullanır.  
  
 Şemaları <xref:System.Xml.Schema.XmlSchemaSet> , öğesinin özelliğini kullanarak bir öğesinden alınır <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> <xref:System.Xml.Schema.XmlSchemaSet> . <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>Öğesinin özelliği <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchema> içinde yer alan nesneler üzerinde yineleme yapmanızı sağlar <xref:System.Xml.Schema.XmlSchemaSet> . <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>Özelliği, <xref:System.Xml.Schema.XmlSchema> veya içinde içerilen tüm nesneleri döndürür <xref:System.Xml.Schema.XmlSchemaSet> veya hedef ad alanı parametresi verildiğinde, <xref:System.Xml.Schema.XmlSchema> hedef ad alanına ait tüm nesneleri döndürür. `null`Hedef ad alanı parametresi olarak belirtilmişse, <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özelliği ad alanı olmayan tüm şemaları döndürür.  
  
 Aşağıdaki örnek, `books.xsd` `http://www.contoso.com/books` ad alanındaki şemayı öğesine ekler <xref:System.Xml.Schema.XmlSchemaSet> , öğesinden ad alanına ait olan tüm şemaları alır `http://www.contoso.com/books` <xref:System.Xml.Schema.XmlSchemaSet> ve ardından bu şemaları öğesine yazar <xref:System.Console> .  
  
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
  
 Bir nesneden şemaları ekleme ve alma hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaSet> , bkz <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> . yöntemi ve <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özellik başvurusu belgeleri.  
  
## <a name="compiling-schemas"></a>Şemaları derleme  
 İçindeki şemalar <xref:System.Xml.Schema.XmlSchemaSet> , yöntemi tarafından bir mantıksal şemaya derlenir <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> <xref:System.Xml.Schema.XmlSchemaSet> .  
  
> [!NOTE]
> Eski sınıftan farklı olarak <xref:System.Xml.Schema.XmlSchemaCollection> , yöntem çağrıldığında şemalar derlenmez <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> .  
  
 <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A>Yöntem başarıyla yürütülüyorsa <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> öğesinin özelliği <xref:System.Xml.Schema.XmlSchemaSet> olarak ayarlanır `true` .  
  
> [!NOTE]
> <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A>İçinde şemalar düzenlenirse Özellik etkilenmez <xref:System.Xml.Schema.XmlSchemaSet> . İçindeki tek tek şemaların güncelleştirmeleri <xref:System.Xml.Schema.XmlSchemaSet> izlenmez. Sonuç olarak, <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> `true` içinde bulunan şemalardan biri, <xref:System.Xml.Schema.XmlSchemaSet> ' den eklenen veya kaldırılan hiçbir şema olmadığı sürece değiştirilmiş olabilir <xref:System.Xml.Schema.XmlSchemaSet> .  
  
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
  
 İçindeki şemaları derleme hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaSet> bkz <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> . Yöntem başvurusu belgeleri.  
  
## <a name="reprocessing-schemas"></a>Şemaları yeniden işleme  
 Bir şemanın ' de yeniden işlenmesi, <xref:System.Xml.Schema.XmlSchemaSet> yöntemi çağrıldığında bir şemada gerçekleştirilen tüm ön işleme adımlarını gerçekleştirir <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> <xref:System.Xml.Schema.XmlSchemaSet> . Yöntemine yapılan çağrı başarılı olursa <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> öğesinin özelliği <xref:System.Xml.Schema.XmlSchemaSet> olarak ayarlanır `false` .  
  
 <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A>Yöntemi, <xref:System.Xml.Schema.XmlSchemaSet> derleme gerçekleştirildikten sonra içindeki bir şema değiştirildiğinde kullanılmalıdır <xref:System.Xml.Schema.XmlSchemaSet> .  
  
 Aşağıdaki örnek, yöntemi kullanılarak öğesine eklenen bir şemanın yeniden işlenmesini gösterir <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> . <xref:System.Xml.Schema.XmlSchemaSet>Yöntemi kullanılarak derlendikten <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> ve öğesine eklenen şema <xref:System.Xml.Schema.XmlSchemaSet> değiştirilirse, <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> `true` içindeki bir şema değiştirilse bile özelliği olarak ayarlanır <xref:System.Xml.Schema.XmlSchemaSet> . Yöntemi çağırmak <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> yöntemi tarafından gerçekleştirilen tüm ön işleme gerçekleştirir <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> ve <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> özelliğini olarak ayarlar `false` .  
  
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
  
 Bir şemayı bir içinde yeniden işleme hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaSet> bkz <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> . Yöntem başvurusu belgeleri.  
  
## <a name="checking-for-a-schema"></a>Şema denetleniyor  
 Bir <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> <xref:System.Xml.Schema.XmlSchemaSet> şemanın içinde içerildiğini denetlemek için ' ın metodunu kullanabilirsiniz <xref:System.Xml.Schema.XmlSchemaSet> . <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A>Yöntemi, denetlenecek bir hedef ad alanı ya da <xref:System.Xml.Schema.XmlSchema> nesne alır. Her iki durumda da, <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> `true` şema içinde içerilse, yöntemi döndürür <xref:System.Xml.Schema.XmlSchemaSet> ; Aksi takdirde, döndürür `false` .  
  
 Bir şemayı denetleme hakkında daha fazla bilgi için bkz <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> . Yöntem başvurusu belgeleri.  
  
## <a name="removing-schemas"></a>Şemaları kaldırma  
 Şemaları <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> , ve yöntemleri kullanılarak bir öğesinden kaldırılır <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> <xref:System.Xml.Schema.XmlSchemaSet> . Yöntemi belirtilen şemayı <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> öğesinden kaldırır <xref:System.Xml.Schema.XmlSchemaSet> , ancak <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> Yöntem belirtilen şemayı ve içeri aktardığı tüm şemaları kaldırır <xref:System.Xml.Schema.XmlSchemaSet> .  
  
 Aşağıdaki örnek, bir öğesine birden çok şema eklemeyi <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> ve sonra şemadan birini ve içeri aktardığı tüm şemaları kaldırmak için yöntemini kullanmayı gösterir.  
  
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
  
 İçindeki şemaları kaldırma hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaSet> , <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> ve <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> yöntemleri başvuru belgelerine bakın.  
  
## <a name="schema-resolution-and-xsimport"></a>Şema çözünürlüğü ve xs: import  
 Aşağıdaki örneklerde, <xref:System.Xml.Schema.XmlSchemaSet> içinde verilen bir ad alanı için birden çok şema olduğunda şemaları içeri aktarma davranışı açıklanır <xref:System.Xml.Schema.XmlSchemaSet> .  
  
 Örneğin, <xref:System.Xml.Schema.XmlSchemaSet> ad alanı için birden çok şema içeren bir düşünün `http://www.contoso.com` . Aşağıdaki yönergeyle bir şema `xs:import` öğesine eklenmiştir <xref:System.Xml.Schema.XmlSchemaSet> .  
  
```xml  
<xs:import namespace="http://www.contoso.com" schemaLocation="http://www.contoso.com/schema.xsd" />  
```  
  
 <xref:System.Xml.Schema.XmlSchemaSet> `http://www.contoso.com` URL 'den yükleyerek ad alanı için bir şemayı içeri aktarmaya çalışır `http://www.contoso.com/schema.xsd` . İçindeki ad alanı için başka bir şema belgesi olsa da, yalnızca şema belgesinde belirtilen şema bildirimi ve türleri içeri aktarma şemasında kullanılabilir `http://www.contoso.com` <xref:System.Xml.Schema.XmlSchemaSet> . `schema.xsd`Dosya URL 'de bulunamıyorsa `http://www.contoso.com/schema.xsd` , ad alanı için bir şema `http://www.contoso.com` içeri aktarma şemasına içeri aktarılmaz.  
  
## <a name="validating-xml-documents"></a>XML belgelerini doğrulama  
 XML belgeleri, içindeki şemalara karşı doğrulanabilir <xref:System.Xml.Schema.XmlSchemaSet> . Bir nesnenin özelliğine bir şema ekleyerek <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.XmlReaderSettings.Schemas%2A> <xref:System.Xml.XmlReaderSettings> veya bir <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.XmlReaderSettings.Schemas%2A> nesnenin ÖZELLIĞINE bir <xref:System.Xml.XmlReaderSettings> nesne ekleyerek bir XML belgesini doğrularsınız. <xref:System.Xml.XmlReaderSettings>Daha sonra nesnesi, <xref:System.Xml.XmlReader.Create%2A> sınıfının yöntemi tarafından <xref:System.Xml.XmlReader> bir <xref:System.Xml.XmlReader> nesne oluşturmak ve XML belgesini doğrulamak için kullanılır.  
  
 XML belgelerinin bir kullanarak doğrulanması hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaSet> bkz. [XmlSchemaSet Ile xml ŞEMASı (xsd) doğrulaması](xml-schema-xsd-validation-with-xmlschemaset.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Schema.XmlSchemaSet.Add%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A>
- [Şema önbelleği olarak XmlSchemaSet](xmlschemaset-for-schema-compilation.md)
- [XmlSchemaSet ile XML Şeması (XSD) Doğrulaması](xml-schema-xsd-validation-with-xmlschemaset.md)
