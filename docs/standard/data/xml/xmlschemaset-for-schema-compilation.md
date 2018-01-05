---
title: "Şema derleme için XmlSchemaSet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 55c4b175-3170-4071-9d60-dd5a42f79b54
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a834fe8764744f5b2dd41de1f4fe1479059b87bb
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="xmlschemaset-for-schema-compilation"></a>Şema derleme için XmlSchemaSet
Açıklar <xref:System.Xml.Schema.XmlSchemaSet>, bir önbellek burada XML Şeması Tanım Dili (XSD) şemaları depolanabilir ve doğrulandı.  
  
## <a name="the-xmlschemaset-class"></a>XmlSchemaSet sınıfı  
 <xref:System.Xml.Schema.XmlSchemaSet> Burada XML Şeması Tanım Dili (XSD) şemaları depolanabilir ve doğrulanmış bir önbelleğidir.  
  
 İçinde <xref:System.Xml?displayProperty=nameWithType> XML şemaları sürüm 1.0, yüklenen içine bir <xref:System.Xml.Schema.XmlSchemaCollection> şemaların kitaplık olarak sınıfı. İçinde <xref:System.Xml?displayProperty=nameWithType> sürüm 2.0, <xref:System.Xml.XmlValidatingReader> ve <xref:System.Xml.Schema.XmlSchemaCollection> sınıfları eskidir ve almıştır <xref:System.Xml.XmlReader.Create%2A> yöntemleri ve <xref:System.Xml.Schema.XmlSchemaSet> sırasıyla sınıfı.  
  
 <xref:System.Xml.Schema.XmlSchemaSet> Birkaç standartları uyumluluğu, performans ve Microsoft XML verileri azaltılmış (XDR) şema biçimi geçersiz dahil olmak üzere sorunları düzeltmek için sunulmuştur.  
  
 Arasında bir karşılaştırma aşağıdadır <xref:System.Xml.Schema.XmlSchemaCollection> sınıfı ve <xref:System.Xml.Schema.XmlSchemaSet> sınıfı.  
  
|XmlSchemaCollection|XmlSchemaSet|  
|-------------------------|------------------|  
|Microsoft XDR ve W3C XML şemalarını destekler.|Yalnızca W3C XML şemaları destekler.|  
|Şemalar derlenen zaman <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> yöntemi çağrılır.|Şemalar olmayan zaman derlenmiş <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemi çağrılır. Bu şema kitaplığı oluşturulması sırasında performans geliştirmesi sağlar.|  
|"İçinde şema Adaları." sonuçlanabilir tek tek bir derlenmiş sürüm her şema oluşturur Sonuç olarak, tüm içerir ve içeri aktarmalar içinde yalnızca o şeması kapsamına eklenir.|Derlenmiş şema bir "şemaları ayarlama" tek bir mantıksal şema oluşturun. Kümeye eklenen tüm içeri aktarılan bir şema şemalarında kümesine kendilerini doğrudan eklenir. Başka bir deyişle, tüm şemaları tüm türleri kullanılabilir.|  
|Belirli hedef ad alanı için yalnızca bir şema koleksiyonunda var olabilir.|Aynı hedef ad alanı için birden çok şema türü çakışmalar var olduğu sürece eklenebilir.|  
  
## <a name="migrating-to-the-xmlschemaset"></a>XmlSchemaSet geçirme  
 Aşağıdaki kod örneğinde yeni geçiş için bir kılavuz sağlar <xref:System.Xml.Schema.XmlSchemaSet> eski sınıfından <xref:System.Xml.Schema.XmlSchemaCollection> sınıfı. Kod örneği iki sınıf arasında aşağıdaki temel farklılıkları gösterir.  
  
-   Farklı <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> yöntemi <xref:System.Xml.Schema.XmlSchemaCollection> sınıfı, şemalar değil çağrılırken derlenmiş <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemi <xref:System.Xml.Schema.XmlSchemaSet>. <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> Yöntemi <xref:System.Xml.Schema.XmlSchemaSet> örnek kodda açık olarak adlandırılır.  
  
-   Üzerinden yineleme yapmak için bir <xref:System.Xml.Schema.XmlSchemaSet>, kullanmalısınız <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özelliği <xref:System.Xml.Schema.XmlSchemaSet>.  
  
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
 Şemalar eklenir bir <xref:System.Xml.Schema.XmlSchemaSet> kullanarak <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemi <xref:System.Xml.Schema.XmlSchemaSet>. İçin bir şema eklendiğinde bir <xref:System.Xml.Schema.XmlSchemaSet>, hedef ad alanı URI ile ilişkilidir. URI ya da belirtilebilir parametre olarak hedef ad alanı <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemi veya hiçbir hedef ad alanı belirtilmiş olup olmadığını <xref:System.Xml.Schema.XmlSchemaSet> şemada tanımlanan hedef ad alanı kullanır.  
  
 Öğesinden alınan şemaları bir <xref:System.Xml.Schema.XmlSchemaSet> kullanarak <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özelliği <xref:System.Xml.Schema.XmlSchemaSet>. <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> Özelliği <xref:System.Xml.Schema.XmlSchemaSet> üzerinden yineleme sayesinde <xref:System.Xml.Schema.XmlSchema> içinde yer alan nesneler <xref:System.Xml.Schema.XmlSchemaSet>. <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> Özelliği ya da döndürür tüm <xref:System.Xml.Schema.XmlSchema> içinde yer alan nesneler <xref:System.Xml.Schema.XmlSchemaSet>, veya hedef ad alanı parametre, tüm döndürür <xref:System.Xml.Schema.XmlSchema> hedef ad alanına ait nesneleri. Varsa `null` hedef ad alanı parametre olarak belirtilen <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özelliği, bir ad alanı olmayan tüm şemalarını döndürür.  
  
 Aşağıdaki örnek, `books.xsd` şemada `http://www.contoso.com/books` ad alanına bir <xref:System.Xml.Schema.XmlSchemaSet>, ait tüm şemaları alır `http://www.contoso.com/books` ad alanından <xref:System.Xml.Schema.XmlSchemaSet>ve ardından bu şemaya Yazar <xref:System.Console>.  
  
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
  
 Ekleme ve gelen şemaları alma hakkında daha fazla bilgi için bir <xref:System.Xml.Schema.XmlSchemaSet> nesne için bkz: <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemi ve <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> özelliği başvuru belgeleri.  
  
## <a name="compiling-schemas"></a>Şema derleme  
 Şemalarda bir <xref:System.Xml.Schema.XmlSchemaSet> tarafından bir mantıksal şema içine derlenmiş <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> yöntemi <xref:System.Xml.Schema.XmlSchemaSet>.  
  
> [!NOTE]
>  Artık kullanılmayan aksine <xref:System.Xml.Schema.XmlSchemaCollection> sınıfı, şemalar olmayan zaman derlenmiş <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemi çağrılır.  
  
 Varsa <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> yöntemini yürütür başarıyla <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> özelliği <xref:System.Xml.Schema.XmlSchemaSet> ayarlanır `true`.  
  
> [!NOTE]
>  <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> Özelliği şemaları düzenlediyseniz etkilenmez while içinde <xref:System.Xml.Schema.XmlSchemaSet>. Güncelleştirmeleri tek tek şemalardan <xref:System.Xml.Schema.XmlSchemaSet> değil izlenir. Sonuç olarak, <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> özelliği `true` şemalardan birine yer alan olsa bile <xref:System.Xml.Schema.XmlSchemaSet> şema eklendi veya korumadan kaldırıldı sürece, değiştirilmiş <xref:System.Xml.Schema.XmlSchemaSet>.  
  
 Aşağıdaki örnek, `books.xsd` dosya <xref:System.Xml.Schema.XmlSchemaSet> ve çağırır <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> yöntemi.  
  
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
  
## <a name="reprocessing-schemas"></a>Yeniden işlemenin şemaları  
 Şemada yeniden işlemenin bir <xref:System.Xml.Schema.XmlSchemaSet> şemayı gerçekleştirilen tüm önişlem adımları gerçekleştirir, <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemi <xref:System.Xml.Schema.XmlSchemaSet> olarak adlandırılır. Varsa çağrısı <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> yöntemdir başarılı <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> özelliği <xref:System.Xml.Schema.XmlSchemaSet> ayarlanır `false`.  
  
 <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> Yöntemi şemada zaman kullanılmalıdır <xref:System.Xml.Schema.XmlSchemaSet> sonra değiştirilen <xref:System.Xml.Schema.XmlSchemaSet> derleme gerçekleştirdi.  
  
 Aşağıdaki örnekte, eklenen bir şema yeniden işlemeyerek gösterilmektedir <xref:System.Xml.Schema.XmlSchemaSet> kullanarak <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> yöntemi. Sonra <xref:System.Xml.Schema.XmlSchemaSet> derlenip <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> yöntemi ve eklenen şema <xref:System.Xml.Schema.XmlSchemaSet> değiştirildiğinde <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> özelliği ayarlanmış `true` dahi şemada <xref:System.Xml.Schema.XmlSchemaSet> değiştirildi. Çağırma <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> yöntemi gerçekleştirir tüm tarafından gerçekleştirilen ön işleme <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> yöntemi ve kümelerini <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> özelliğine `false`.  
  
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
  
 Şemada yeniden işleme hakkında daha fazla bilgi için bir <xref:System.Xml.Schema.XmlSchemaSet>, bkz: <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> yöntemi başvuru belgeleri.  
  
## <a name="checking-for-a-schema"></a>İçin bir şema denetleniyor  
 Kullanabileceğiniz <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> yöntemi <xref:System.Xml.Schema.XmlSchemaSet> bir şema içinde dahil olup olmadığını denetlemek için bir <xref:System.Xml.Schema.XmlSchemaSet>. <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> Yöntemi alır ya da, bir hedef ad alanı veya bir <xref:System.Xml.Schema.XmlSchema> denetlemek için nesne. Her iki durumda da <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> yöntemi döndürür `true` şema içinde yer alıyorsa <xref:System.Xml.Schema.XmlSchemaSet>; Aksi takdirde döndürdüğü `false`.  
  
 İçin bir şema denetimi hakkında daha fazla bilgi için bkz: <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> yöntemi başvuru belgeleri.  
  
## <a name="removing-schemas"></a>Şemalar kaldırma  
 Şemalar kaldırılma bir <xref:System.Xml.Schema.XmlSchemaSet> kullanarak <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> ve <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> yöntemlerini <xref:System.Xml.Schema.XmlSchemaSet>. <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> Yöntemi, belirtilen şemasından kaldırır <xref:System.Xml.Schema.XmlSchemaSet>, sırada <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> yöntemi, belirtilen şema ve bunu aktarır tüm şemaları kaldırır <xref:System.Xml.Schema.XmlSchemaSet>.  
  
 Aşağıdaki örnekte, birden çok şema ekleme gösterilmektedir bir <xref:System.Xml.Schema.XmlSchemaSet>, ardından kullanarak <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> şemalardan birine ve bunu aktarır tüm şemaları kaldırmak için yöntem.  
  
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
  
 Gelen şemaları kaldırma hakkında daha fazla bilgi için bir <xref:System.Xml.Schema.XmlSchemaSet>, bkz: <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> ve <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> yöntemleri başvuru belgelerini.  
  
## <a name="schema-resolution-and-xsimport"></a>Şema çözümlemesi ve xs:import  
 Aşağıdaki örnekler açıklar <xref:System.Xml.Schema.XmlSchemaSet> şemalarını içeri aktarma için belirli bir ad için birden çok şema mevcut olduğunda davranışı bir <xref:System.Xml.Schema.XmlSchemaSet>.  
  
 Örneğin, göz önünde bulundurun bir <xref:System.Xml.Schema.XmlSchemaSet> için birden çok şema içeren `http://www.contoso.com` ad alanı. Aşağıdaki şema `xs:import` yönergesi eklenir <xref:System.Xml.Schema.XmlSchemaSet>.  
  
```xml  
<xs:import namespace="http://www.contoso.com" schemaLocation="http://www.contoso.com/schema.xsd" />  
```  
  
 <xref:System.Xml.Schema.XmlSchemaSet> İçin bir şema alma girişiminde `http://www.contoso.com` şuradan yükleniyor tarafından ad alanı `http://www.contoso.com/schema.xsd` URL. Diğer şema belgeler için olsa bile şema bildirimi ve şema belgesinde bildirilen türler alma şemada yalnızca kullanılabilir `http://www.contoso.com` ad alanında <xref:System.Xml.Schema.XmlSchemaSet>. Varsa `schema.xsd` dosya adresindedir olamaz `http://www.contoso.com/schema.xsd` URL için şema yok `http://www.contoso.com` ad alanı içeri aktarma şemaya alınır.  
  
## <a name="validating-xml-documents"></a>XML belgeleri doğrulanıyor  
 XML belgeleri doğrulanmış şemalarda karşı bir <xref:System.Xml.Schema.XmlSchemaSet>. Bir şemaya ekleyerek bir XML belgesi doğrulamak <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.XmlReaderSettings.Schemas%2A> özelliği bir <xref:System.Xml.XmlReaderSettings> nesne veya ekleyerek bir <xref:System.Xml.Schema.XmlSchemaSet> için <xref:System.Xml.XmlReaderSettings.Schemas%2A> özelliği bir <xref:System.Xml.XmlReaderSettings> nesnesi. <xref:System.Xml.XmlReaderSettings> Nesnesi tarafından kullanılan sonra <xref:System.Xml.XmlReader.Create%2A> yöntemi <xref:System.Xml.XmlReader> sınıfı oluşturmak için bir <xref:System.Xml.XmlReader> nesne ve XML belgesi doğrulayın.  
  
 XML doğrulama hakkında daha fazla bilgi için belgeleri kullanarak bir <xref:System.Xml.Schema.XmlSchemaSet>, bkz: [XmlSchemaSet ile XML Şeması (XSD) doğrulama](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.Schema.XmlSchemaSet.Add%2A>  
 <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>  
 <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A>  
 <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A>  
 <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A>  
 <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A>  
 <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A>  
 [Bir şema önbelleği olarak XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 [XmlSchemaSet ile XML Şeması (XSD) Doğrulaması](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md)
