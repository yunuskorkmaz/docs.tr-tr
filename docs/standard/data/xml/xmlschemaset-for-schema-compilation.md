---
title: Şema derleme için XmlSchemaSet
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 55c4b175-3170-4071-9d60-dd5a42f79b54
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c24fe637514ba773cecc7824de276b1707a4e90c
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46288078"
---
# <a name="xmlschemaset-for-schema-compilation"></a>Şema derleme için XmlSchemaSet
Açıklar <xref:System.Xml.Schema.XmlSchemaSet>, burada XML Şeması Tanım Dili (XSD) şemaları depolanabilir ve doğrulanmış bir önbellek.  
  
## <a name="the-xmlschemaset-class"></a>XmlSchemaSet sınıfı  
 <xref:System.Xml.Schema.XmlSchemaSet> Burada XML Şeması Tanım Dili (XSD) şemaları depolanabilir ve doğrulanmış bir önbellektir.  
  
 İçinde <xref:System.Xml?displayProperty=nameWithType> sürüm 1.0, XML şemaları yüklü içine bir <xref:System.Xml.Schema.XmlSchemaCollection> şemaların sınıf kitaplığı olarak. İçinde <xref:System.Xml?displayProperty=nameWithType> sürüm 2.0 <xref:System.Xml.XmlValidatingReader> ve <xref:System.Xml.Schema.XmlSchemaCollection> sınıfları eskidir ve almıştır <xref:System.Xml.XmlReader.Create%2A> yöntemleri ve <xref:System.Xml.Schema.XmlSchemaSet> sırasıyla sınıfı.  
  
 <xref:System.Xml.Schema.XmlSchemaSet> Birkaç standartlara uyumluluk, performans ve eski Microsoft XML verileri azaltılmış (XDR) şema biçimi gibi sorunları düzeltmek için sunulmuştur.  
  
 Bir karşılaştırması aşağıdadır <xref:System.Xml.Schema.XmlSchemaCollection> sınıfı ve <xref:System.Xml.Schema.XmlSchemaSet> sınıfı.  
  
|XmlSchemaCollection|XmlSchemaSet|  
|-------------------------|------------------|  
|Microsoft XDR ve W3C XML şemalarını destekler.|Yalnızca W3C XML şemaları destekler.|  
|Şema derlenen olduğunda <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> yöntemi çağrılır.|Şemaları olmayan zaman derlenmiş <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemi çağrılır. Bu, bir performans geliştirmesi sırasında Şema Kitaplığı oluşturulmasını sağlar.|  
|"Şema Adaları." neden olabilir bir bireysel derlenmiş sürüm her şeması oluşturur Sonuç olarak, tüm içerir ve içeri aktarmalar yalnızca o şema içindeki belirlenir.|Bir "şemaları Ayarla" tek bir mantıksal şema derlenen şemalar oluşturur. Kümeye eklenen bir şema içinde alınan şemalar doğrudan kümesine kendilerini eklenir. Başka bir deyişle, tüm şemalara tüm türleri kullanılabilir.|  
|Belirli bir hedef ad alanı için yalnızca bir şema koleksiyonunda mevcut olabilir.|Birden çok şema aynı hedef ad alanı için hiçbir tür çakışmalar var olduğu sürece eklenebilir.|  
  
## <a name="migrating-to-the-xmlschemaset"></a>Geçiş için XmlSchemaSet  
 Aşağıdaki kod örneği yeni geçiş için bir kılavuz sağlar <xref:System.Xml.Schema.XmlSchemaSet> eski sınıftan <xref:System.Xml.Schema.XmlSchemaCollection> sınıfı. Kod örneği, iki sınıf arasındaki aşağıdaki temel farklar gösterilmektedir.  
  
-   Farklı <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> yöntemi <xref:System.Xml.Schema.XmlSchemaCollection> sınıfı çağrılırken, şemalar derlenmiş değil <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemi <xref:System.Xml.Schema.XmlSchemaSet>. <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> Yöntemi <xref:System.Xml.Schema.XmlSchemaSet> örnek kodda açıkça çağrılır.  
  
-   Üzerinden yinelemek için bir <xref:System.Xml.Schema.XmlSchemaSet>, kullanmanız gereken <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özelliği <xref:System.Xml.Schema.XmlSchemaSet>.  
  
 Aşağıdaki kullanılmıyor <xref:System.Xml.Schema.XmlSchemaCollection> kod örneği.  
  
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
  
 Aşağıdaki eşdeğerdir <xref:System.Xml.Schema.XmlSchemaSet> kod örneği.  
  
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
  
## <a name="adding-and-retrieving-schemas"></a>Ekleme ve şemaları alma  
 Şemaları eklenir bir <xref:System.Xml.Schema.XmlSchemaSet> kullanarak <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemi <xref:System.Xml.Schema.XmlSchemaSet>. İçin bir şema eklendiğinde bir <xref:System.Xml.Schema.XmlSchemaSet>, bir hedef ad alanı URI ile ilişkilidir. Hedef ad alanı URI ya da belirtilebilir bir parametre olarak <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemi veya hiçbir hedef ad alanı belirtilmiş olup olmadığını <xref:System.Xml.Schema.XmlSchemaSet> şemasında tanımlanan hedef ad alanını kullanır.  
  
 Şemaları öğesinden alınan bir <xref:System.Xml.Schema.XmlSchemaSet> kullanarak <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özelliği <xref:System.Xml.Schema.XmlSchemaSet>. <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> Özelliği <xref:System.Xml.Schema.XmlSchemaSet> gezinilen sağlar <xref:System.Xml.Schema.XmlSchema> bulunan nesneleri <xref:System.Xml.Schema.XmlSchemaSet>. <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> Özellik ya da döndürür tüm <xref:System.Xml.Schema.XmlSchema> bulunan nesneleri <xref:System.Xml.Schema.XmlSchemaSet>, ya da bir hedef ad alanı parametresi, tüm döndürür <xref:System.Xml.Schema.XmlSchema> hedef ad alanına ait nesneleri. Varsa `null` hedef ad alanı parametre olarak belirtilen <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özelliği ad alanı olmayan tüm şemalar döndürür.  
  
 Aşağıdaki örnek ekler `books.xsd` şemasında `http://www.contoso.com/books` ad alanına bir <xref:System.Xml.Schema.XmlSchemaSet>, ait tüm şemaları alır `http://www.contoso.com/books` ad alanından <xref:System.Xml.Schema.XmlSchemaSet>ve ardından bu şemaya Yazar <xref:System.Console>.  
  
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
  
 Ekleme ve şemalardan alma hakkında daha fazla bilgi için bir <xref:System.Xml.Schema.XmlSchemaSet> nesne, bkz: <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemi ve <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özellik başvuru belgeleri.  
  
## <a name="compiling-schemas"></a>Şemaları derlenirken  
 Şemalarda bir <xref:System.Xml.Schema.XmlSchemaSet> mantıksal bir şema tarafından derlenmiş <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> yöntemi <xref:System.Xml.Schema.XmlSchemaSet>.  
  
> [!NOTE]
>  Eski aksine <xref:System.Xml.Schema.XmlSchemaCollection> sınıfı şemaları olmayan zaman derlenmiş <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemi çağrılır.  
  
 Varsa <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> yöntemini yürütür başarıyla <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> özelliği <xref:System.Xml.Schema.XmlSchemaSet> ayarlanır `true`.  
  
> [!NOTE]
>  <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> Şemaları düzenlediyseniz özelliği etkilenmez while <xref:System.Xml.Schema.XmlSchemaSet>. Güncelleştirmeleri tek tek şemalarda <xref:System.Xml.Schema.XmlSchemaSet> değil izlenir. Sonuç olarak, <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> özelliği `true` şemalardan birine bulunan olsa bile <xref:System.Xml.Schema.XmlSchemaSet> şema eklendi veya kaldırıldı sürece, değiştirilmiş <xref:System.Xml.Schema.XmlSchemaSet>.  
  
 Aşağıdaki örnek ekler `books.xsd` dosyasını <xref:System.Xml.Schema.XmlSchemaSet> ve <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> yöntemi.  
  
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
  
 Şemalarda derleme hakkında daha fazla bilgi için bir <xref:System.Xml.Schema.XmlSchemaSet>, bkz: <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> yöntemi başvuru belgeleri.  
  
## <a name="reprocessing-schemas"></a>Şemaları yeniden işleniyor  
 Şemada yeniden işlemeyerek bir <xref:System.Xml.Schema.XmlSchemaSet> bir şema üzerinde gerçekleştirilen tüm ön işleme adımları gerçekleştirir, <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemi <xref:System.Xml.Schema.XmlSchemaSet> çağrılır. Çağrı <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> yöntemdir başarılı <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> özelliği <xref:System.Xml.Schema.XmlSchemaSet> ayarlanır `false`.  
  
 <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> Yöntemi kullanılmalıdır şemada <xref:System.Xml.Schema.XmlSchemaSet> sonra değiştirilmiş <xref:System.Xml.Schema.XmlSchemaSet> derleme gerçekleştirdi.  
  
 Aşağıdaki örnekte, eklenen bir şema yeniden işlemeyerek gösterilmektedir <xref:System.Xml.Schema.XmlSchemaSet> kullanarak <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> yöntemi. Sonra <xref:System.Xml.Schema.XmlSchemaSet> kullanılarak derlenmiş <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> yöntemi ve eklenen şemayı <xref:System.Xml.Schema.XmlSchemaSet> değiştirildiğinde <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> özelliği `true` şemada olsa bile <xref:System.Xml.Schema.XmlSchemaSet> değiştirildi. Çağırma <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> yöntemi gerçekleştirdiği tüm gerçekleştirdiği ön işleme <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemi ve kümelerini <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> özelliğini `false`.  
  
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
  
 Şemada yeniden işlemeyerek hakkında daha fazla bilgi için bir <xref:System.Xml.Schema.XmlSchemaSet>, bkz: <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> yöntemi başvuru belgeleri.  
  
## <a name="checking-for-a-schema"></a>İçin bir şema denetleniyor  
 Kullanabileceğiniz <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> yöntemi <xref:System.Xml.Schema.XmlSchemaSet> bir şema içinde dahil olup olmadığını denetlemek için bir <xref:System.Xml.Schema.XmlSchemaSet>. <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> Yöntemi alır ya da bir hedef ad alanı veya bir <xref:System.Xml.Schema.XmlSchema> denetlenecek nesne. Her iki durumda da <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> yöntemi döndürür `true` şema içinde yer alıyorsa <xref:System.Xml.Schema.XmlSchemaSet>; Aksi halde döndürür `false`.  
  
 İçin bir şema denetleme hakkında daha fazla bilgi için bkz. <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> yöntemi başvuru belgeleri.  
  
## <a name="removing-schemas"></a>Şemaları kaldırılıyor  
 Şemaları kaldırılma bir <xref:System.Xml.Schema.XmlSchemaSet> kullanarak <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> ve <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> yöntemlerinin <xref:System.Xml.Schema.XmlSchemaSet>. <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> Yöntemi, belirtilen şemasından kaldırır <xref:System.Xml.Schema.XmlSchemaSet>, ancak <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> yöntemi, belirtilen şemaya ve bunu içe aktaran tüm şemalar kaldırır <xref:System.Xml.Schema.XmlSchemaSet>.  
  
 Ekleme için birden çok şema, aşağıdaki örnekte gösterilmiştir bir <xref:System.Xml.Schema.XmlSchemaSet>, ardından kullanarak <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> şemalardan birine ve bunu içe aktaran tüm şemalar kaldırmak için yöntemi.  
  
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
  
 Şemalardan kaldırma hakkında daha fazla bilgi için bir <xref:System.Xml.Schema.XmlSchemaSet>, bkz: <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> ve <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> yöntemleri başvuru belgeleri.  
  
## <a name="schema-resolution-and-xsimport"></a>Şema çözümleme ve xs:import  
 Aşağıdaki örnekler açıklar <xref:System.Xml.Schema.XmlSchemaSet> şemaları içeri aktarma için belirtilen bir ad alanı için birden çok şema mevcut olduğunda davranışı bir <xref:System.Xml.Schema.XmlSchemaSet>.  
  
 Örneğin, bir <xref:System.Xml.Schema.XmlSchemaSet> için birden çok şema içeren `http://www.contoso.com` ad alanı. Aşağıdaki şema `xs:import` yönergesi eklenir <xref:System.Xml.Schema.XmlSchemaSet>.  
  
```xml  
<xs:import namespace="http://www.contoso.com" schemaLocation="http://www.contoso.com/schema.xsd" />  
```  
  
 <xref:System.Xml.Schema.XmlSchemaSet> İçeri aktarmak için bir şema dener `http://www.contoso.com` ondan yükleme tarafından ad alanı `http://www.contoso.com/schema.xsd` URL'si. Diğer şeması belgeleri için olsa bile şema belgesi içinde bildirilen türleri ve şema bildirim alma şemada yalnızca kullanılabilir `http://www.contoso.com` ad alanında <xref:System.Xml.Schema.XmlSchemaSet>. Varsa `schema.xsd` dosya konumu olamaz `http://www.contoso.com/schema.xsd` URL için şema `http://www.contoso.com` ad alanı alma şemasına aktarılır.  
  
## <a name="validating-xml-documents"></a>XML belgeleri doğrulanıyor  
 XML belgeleri doğrulanmış şemalarda karşı bir <xref:System.Xml.Schema.XmlSchemaSet>. Bir şema ekleyerek bir XML belgesi doğrulama <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.XmlReaderSettings.Schemas%2A> özelliği bir <xref:System.Xml.XmlReaderSettings> nesne veya ekleyerek bir <xref:System.Xml.Schema.XmlSchemaSet> için <xref:System.Xml.XmlReaderSettings.Schemas%2A> özelliği bir <xref:System.Xml.XmlReaderSettings> nesne. <xref:System.Xml.XmlReaderSettings> Nesne tarafından kullanılan ardından <xref:System.Xml.XmlReader.Create%2A> yöntemi <xref:System.Xml.XmlReader> sınıfı oluşturmak için bir <xref:System.Xml.XmlReader> nesnesi ve bir XML belgesi doğrulama.  
  
 XML doğrulama hakkında daha fazla bilgi için belgeler kullanan bir <xref:System.Xml.Schema.XmlSchemaSet>, bkz: [XmlSchemaSet ile XML Şeması (XSD) doğrulaması](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md).  
  
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
