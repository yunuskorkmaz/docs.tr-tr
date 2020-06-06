---
title: XML şema tanımı Aracı (XSD.exe'nin)
description: XML serileştirici Oluşturucusu, belirtilen derlemedeki türler için bir XML serileştirme derlemesi oluşturur ve bu da XmlSerializer 'ın başlangıç performansını geliştirir.
ms.date: 03/30/2017
ms.assetid: a6e6e65c-347f-4494-9457-653bf29baac2
ms.openlocfilehash: 0275ecfebd427feb104013024654d4a0bc98748a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "84288985"
---
# <a name="xml-schema-definition-tool-xsdexe"></a>XML şema tanımı Aracı (XSD.exe'nin)

XML şema tanımı (XSD.exe'nin) aracı XDR, XML ve XSD dosyalarından veya bir çalışma zamanı derleme sınıflarda XML Şeması veya ortak dil çalışma zamanı sınıflar oluşturur.

XML şema tanımı Aracı (xsd. exe) genellikle şu yolda bulunabilir: \
_C: \\ Program Files (x86) \\ Microsoft SDK 'ları \\ Windows \\ {Version} \\ bin \\ Netfx {Version} araçları\\_

## <a name="syntax"></a>Sözdizimi

Aracı komut satırından çalıştırın.

```console
xsd file.xdr [-outputdir:directory][/parameters:file.xml]
xsd file.xml [-outputdir:directory] [/parameters:file.xml]
xsd file.xsd {/classes | /dataset} [/element:element]
             [/enableLinqDataSet] [/language:language]
                          [/namespace:namespace] [-outputdir:directory] [URI:uri]
                          [/parameters:file.xml]
xsd {file.dll | file.exe} [-outputdir:directory] [/type:typename [...]][/parameters:file.xml]
```
  
> [!TIP]
> .NET Framework araçlarının düzgün çalışması için,, `Path` `Include` ve `Lib` ortam değişkenlerinizi doğru şekilde ayarlamanız gerekir. \V2.0\Bin dizininde bulunan SDKVars. bat dosyasını çalıştırarak bu ortam değişkenlerini ayarlayın \<SDK> . Her komut kabuğu'nu SDKVars.bat yürütülmelidir.

## <a name="argument"></a>Bağımsız Değişken

|Bağımsız Değişken|Açıklama|
|--------------|-----------------|
|*dosya. Extension*|Dönüştürülecek giriş dosyasını belirtir. Uzantıyı aşağıdakilerden biri olarak belirtmeniz gerekir:. xdr,. xml,. xsd,. dll veya. exe.<br /><br /> XDR şema dosyası (.xdr uzantısı) belirtirseniz, xsd.exe'nin bir XSD şemasına XDR şeması dönüştürür. Çıkış dosyası XDR şeması, ancak .xsd uzantısı ile aynı ada sahip.<br /><br /> Bir XML dosyası (.xml uzantısı) belirtirseniz, xsd.exe'nin veri dosyasındaki bir şema öğesinin ve bir XSD şeması üretir. Çıkış dosyası XML dosyası olarak, ancak .xsd uzantısı ile aynı ada sahip.<br /><br /> Bir XML şema dosyası (.xsd uzantısı) belirtirseniz, xsd.exe'nin için XML Şeması karşılık gelen çalışma zamanı nesneler için kaynak kodu oluşturur.<br /><br /> Bir çalışma zamanı derleme dosyası (.exe veya .dll uzantısı) belirtirseniz, xsd.exe'nin şemaları bir veya daha fazla türleri için bu derlemede oluşturur. Kullanabilirsiniz `/type` şemaları oluşturulacak türlerini belirtmek için seçeneği. Çıkış şemaları schema0.xsd, schema1.xsd vb. adlandırılır. Yalnızca verilen türler özel özniteliği kullanarak bir ad alanı belirtse xsd. exe birden çok şema oluşturur `XMLRoot` .|

## <a name="general-options"></a>Genel seçenekleri

|Seçenek|Açıklama|
|------------|-----------------|
|**/h \[ ELP\]**|Araç için komut sözdizimini ve seçenekleri görüntüler.|
|**/o \[ utputdir \] :**_Dizin_|Çıktı dosyaları dizinini belirtir. Bu bağımsız değişken yalnızca bir kez görünebilir. Geçerli dizin varsayılandır.|
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|
|**/p \[ arameters \] :**_File. xml_|Çeşitli işlem modları için seçenekler belirtilen .xml dosyasından okuyun. Kısa biçim `/p:` . Daha fazla bilgi için, [açıklamalar](#remarks) bölümüne bakın.|

## <a name="xsd-file-options"></a>XSD dosyası seçenekleri
 .Xsd dosyaları için aşağıdaki seçeneklerden birini belirtmelisiniz.

|Seçenek|Açıklama|
|------------|-----------------|
|**/c \[ lasses\]**|Belirtilen şemaya karşılık gelen sınıflar oluşturur. XML verilerini nesnesine okumak için <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A?displayProperty=nameWithType> yöntemini kullanın.|
|**/d \[ atakümesi\]**|Türetilen bir sınıf oluşturur <xref:System.Data.DataSet> belirtilen şemaya karşılık gelir. XML verilerini türetilmiş sınıfa okumak için <xref:System.Data.DataSet.ReadXml%2A?displayProperty=nameWithType> yöntemini kullanın.|

 .Xsd dosyaları için aşağıdaki seçeneklerden birini belirleyebilirsiniz.

|Seçenek|Açıklama|
|------------|-----------------|
|**/e \[ lement \] :**_öğesi_|Öğe için kod oluşturmak için şema belirtir. Varsayılan olarak tüm öğeler yazılmalıdır. Bu bağımsız değişken birden çok kez belirtebilirsiniz.|
|**/enableDataBinding**|Uygular <xref:System.ComponentModel.INotifyPropertyChanged> veri bağlama etkinleştirmek için oluşturulan tüm türleri arabirimi. Kısa biçim `/edb` .|
|**/enableLinqDataSet**|(Kısa biçim: `/eld` .) Oluşturulan veri kümesinin LINQ to DataSet kullanılarak sorgulanabilecek olduğunu belirtir. Bu seçenek /dataset seçeneği de belirtildiğinde kullanılır. Daha fazla bilgi için bkz. [LINQ to DataSet genel bakış](../../framework/data/adonet/linq-to-dataset-overview.md) ve [yazılan veri kümelerini sorgulama](../../framework/data/adonet/querying-typed-datasets.md). LINQ kullanma hakkında genel bilgi için bkz. [dil Ile tümleşik sorgu (LINQ)-C#](../../csharp/programming-guide/concepts/linq/index.md) veya [dil ile TÜMLEŞIK sorgu (lınq)-Visual Basic](../../visual-basic/programming-guide/concepts/linq/index.md).|
|**/f \[ ields\]**|Alanları özellikleri yerine oluşturur. Varsayılan olarak, özellikleri üretilir.|
|**/l \[ dili \] :**_dil_|Kullanmak için programlama dilini belirtir. Aralarından seçim `CS` (C varsayılan değer olan #), `VB` (Visual Basic) `JS` (JScript) veya `VJS` (Visual J#). Ayrıca bir sınıf uygulamak için tam bir ad belirtin<xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>|
|**/n \[ amespace \] :**_Namespace_|Oluşturulan türleri için çalışma zamanı ad alanını belirtir. Varsayılan ad alanı `Schemas`.|
|**/nologo**|Başlık göstermez.|
|**/Order**|Tüm parçacık üyeleri açık sipariş tanımlayıcılarını oluşturur.|
|**/o \[ \] :**_DirectoryName_|Dosyalarında yerleştirmek için çıktı dizini belirtir. Geçerli dizin varsayılandır.|
|**/u \[ Ri \] :**_URI_|Öğeler için URI için kod oluşturmak için şema belirtir. Bu URI varsa, ile belirtilen tüm öğelere uygulanır `/element` seçeneği.|

## <a name="dll-and-exe-file-options"></a>DLL ve EXE dosya seçenekleri

|Seçenek|Açıklama|
|------------|-----------------|
|**/t \[ türü \] :**_TypeName_|Şema için oluşturulacak tür adını belirtir. Birden çok tür bağımsız değişkeni belirtebilirsiniz. *TypeName* bir ad alanı belirtmezse, xsd. exe, belirtilen türe sahip derlemedeki tüm türlerle eşleşir. *TypeName* bir ad alanı belirtiyorsa, yalnızca bu tür eşleştirilir. *TypeName* bir yıldız karakteriyle () sonlanıyorsa, \* araç, önceki dizeyle başlayan tüm türlerle eşleşir \* . Unutursanız, `/type` seçeneği XSD.exe'nin derlemesinde tüm türler için şemalar oluşturur.|

## <a name="remarks"></a>Açıklamalar

Aşağıdaki tablo operasyonları XSD.exe'nin gerçekleştireceğini gösterir.

| | |
|------------|-----------------|
|XDR XSD için|Bir XML şeması bir XML veri azaltılmış şema dosyasından oluşturur. XDR erken bir XML tabanlı şema biçimidir.|
|XML için XSD|Bir XML Şeması XML dosyasından oluşturur.|
|Veri kümesi için XSD|Ortak dil çalışma zamanı oluşturur <xref:System.Data.DataSet> bir XSD şema dosyasından sınıfları. Oluşturulan sınıflar için normal XML verileri zengin nesne modeli sağlar.|
|XSD sınıflar için|Bir XSD şema dosyasından çalışma zamanı sınıflar oluşturur. Oluşturulan sınıflar birlikte kullanılabilecek <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> okuma ve yazma şema izleyen XML kodu.|
|XSD için sınıflar| Bir XML şeması bir türü veya türleri bir çalışma zamanı derleme dosyası oluşturur. Oluşturulan şema, tarafından kullanılan XML biçimini tanımlar <xref:System.Xml.Serialization.XmlSerializer> .|

 XSD.exe'nin yalnızca World Wide Web Konsorsiyumu (W3C) tarafından önerilen XML şema tanımı (XSD) dil izleyin XML şemaları yönetmenize olanak sağlar. XML şema tanımı teklifi veya XML standardı hakkında daha fazla bilgi için bkz <https://w3.org> ..

## <a name="setting-options-with-an-xml-file"></a>Bir XML dosyası ile seçenekleri ayarlama

`/parameters`Anahtarını kullanarak, çeşitli seçenekleri ayarlayan tek BIR XML dosyası belirtebilirsiniz. Nasıl XSD.exe'nin aracını kullanarak ayarlayabilirsiniz seçenekler bağlıdır. Seçenekler şunlardır şemaları oluşturmak, kod dosyaları oluşturmak veya dahil kod dosyaları oluşturmak `DataSet` özellikleri. Örneğin, ayarlayabilirsiniz `<assembly>` öğesi için bir yürütülebilir (.exe) veya bir şema oluşturulurken türü kitaplık (.dll) dosyası, ancak bir kod dosyası değil oluşturulurken adı. Aşağıdaki XML nasıl kullanılacağı gösterilmiştir `<generateSchemas>` belirtilen yürütülebilir öğe:

```xml
<!-- This is in a file named GenerateSchemas.xml. -->
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>
<generateSchemas>
   <assembly>ConsoleApplication1.exe</assembly>
</generateSchemas>
</xsd>
```

Önceki XML, GenerateSchemas. xml adlı bir dosyada yer alıyorsa, `/parameters` komut istemine aşağıdakileri yazıp **ENTER**tuşuna basarak anahtarı kullanın:

```console
 xsd /p:GenerateSchemas.xml
```

Diğer yandan, derlemede bulunan tek bir tür için bir şema oluşturuyorsanız, aşağıdaki XML kullanabilirsiniz:

```xml
<!-- This is in a file named GenerateSchemaFromType.xml. -->
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>
<generateSchemas>
   <type>IDItems</type>
</generateSchemas>
</xsd>
```

Ancak, önceki kodu kullanmak için da komut isteminde derlemenin adı sağlamanız gerekir. Komut istemine aşağıdaki komutu girin (XML dosyası, GenerateSchemaFromType. xml olarak adlandırılır):

```console
xsd /p:GenerateSchemaFromType.xml ConsoleApplication1.exe
```

İçin aşağıdaki seçeneklerden birini belirtmelisiniz `<generateSchemas>` öğesi.

|Öğe|Açıklama|
|-------------|-----------------|
|\<assembly>|Şema oluşturmak için bir derleme belirtir.|
|\<type>|Bir türü için bir şema oluşturmak için bir derleme bulundu belirtir.|
|\<xml>|Bir XML dosyası için bir şema oluşturmak için belirtir.|
|\<xdr>|İçin bir şema oluşturmak için bir XDR dosyasını belirtir.|

Bir kod dosyası oluşturmak için kullanılan `<generateClasses>` öğesi. Aşağıdaki örnek, bir kod dosyası oluşturur. Oluşturulan dosyanın programlama dilini ve ad alanını ayarlamanıza olanak tanıyan iki özniteliğin de gösterildiğini unutmayın.

```xml
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>
<generateClasses language='VB' namespace='Microsoft.Serialization.Examples'/>
</xsd>
<!-- You must supply an .xsd file when typing in the command line.-->
<!-- For example: xsd /p:genClasses mySchema.xsd -->
```

 Seçenekleri için Ayarla `<generateClasses>` öğesi şunlar.

|Öğe|Açıklama|
|-------------|-----------------|
|\<element>|Bir öğe için kod oluşturmak üzere .xsd dosyasını belirtir.|
|\<schemaImporterExtensions>|Türetilen bir türü belirtiyor. <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> sınıfı.|
|\<schema>|Kodunu oluşturmak için bir XML şema dosyası belirtir. Birden çok öğe kullanılarak birden fazla XML şema dosyası belirtilebilir \<schema> .|

Aşağıdaki tabloda öğesi ile de kullanılabilecek öznitelikler gösterilmektedir `<generateClasses>` .

|Öznitelik|Açıklama|
|---------------|-----------------|
|language|Kullanmak için programlama dilini belirtir. Aralarından seçim `CS` (C#, varsayılan), `VB` (Visual Basic) `JS` (JScript) veya `VJS` (Visual J#). Ayrıca uygulayan bir sınıf için tam bir ad belirtin <xref:System.CodeDom.Compiler.CodeDomProvider>.|
|ad alanı|Oluşturulan kodun ad alanını belirtir. Ad alanı CLR standartları (örneğin, boşluk veya ters eğik çizgi karakterleri) uyması gerekir.|
|seçenekler|Aşağıdaki değerlerden biri: `none` , `properties` (ortak alanlar yerine Özellikler oluşturur), `order` veya `enableDataBinding` ( `/order` `/enableDataBinding` önceki xsd dosya seçenekleri bölümündeki ve anahtarlarına bakın.|

 Ayrıca `DataSet` , öğesinin öğesini kullanarak kodun nasıl oluşturulduğunu da denetleyebilirsiniz `<generateDataSet>` . Aşağıdaki XML, `DataSet` <xref:System.Data.DataTable> belirtilen bir öğe için Visual Basic kodu oluşturmak üzere oluşturulan kodun yapıları (sınıf gibi) kullandığını belirtir. Oluşturulan veri kümesi yapıları LINQ sorgularını destekleyecektir.

 ```xml
 <xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>
     <generateDataSet language='VB' namespace='Microsoft.Serialization.Examples' enableLinqDataSet='true'>
     </generateDataSet>
 </xsd>
```

Seçenekleri için Ayarla `<generateDataSet>` öğesi şunlar.

|Öğe|Açıklama|
|-------------|-----------------|
|\<schema>|Kodunu oluşturmak için bir XML şeması dosyasını belirtir. Birden çok öğe kullanılarak birden fazla XML şema dosyası belirtilebilir \<schema> .|

 Aşağıdaki tabloda öğesiyle birlikte kullanılabilecek öznitelikler gösterilmektedir `<generateDataSet>` .

|Öznitelik|Açıklama|
|---------------|-----------------|
|enableLinqDataSet|Oluşturulan veri kümesi LINQ to DataSet kullanarak karşı sorgulanabilir belirtir. Varsayılan değer false'tur.|
|language|Kullanmak için programlama dilini belirtir. Aralarından seçim `CS` (C#, varsayılan), `VB` (Visual Basic) `JS` (JScript) veya `VJS` (Visual J#). Ayrıca uygulayan bir sınıf için tam bir ad belirtin <xref:System.CodeDom.Compiler.CodeDomProvider>.|
|ad alanı|Oluşturulan kodun ad alanını belirtir. Ad alanı CLR standartları (örneğin, boşluk veya ters eğik çizgi karakterleri) uyması gerekir.|

 En üst düzey öğede ayarlayabileceğiniz öznitelikler vardır `<xsd>` . Herhangi bir alt öğelerinin bu seçenekler kullanılabilir (`<generateSchemas>`, `<generateClasses>` veya `<generateDataSet>`). Aşağıdaki XML kodu "MyOutputDirectory" adlı Çıktı dizininde "IDItems" adlı bir öğe için kod oluşturur.

```xml
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/' output='MyOutputDirectory'>
<generateClasses>
    <element>IDItems</element>
</generateClasses>
</xsd>
```

Aşağıdaki tabloda öğesi ile de kullanılabilecek öznitelikler gösterilmektedir `<xsd>` .

|Öznitelik|Açıklama|
|---------------|-----------------|
|çıkış|Oluşturulan şema veya kod dosyanın yerleştirileceği bir dizinin adı.|
|nologo|Başlık göstermez. Ayarlanan `true` veya `false`.|
|Yardım|Araç için komut sözdizimini ve seçenekleri görüntüler. Ayarlanan `true` veya `false`.|

## <a name="examples"></a>Örnekler
 Aşağıdaki komutu bir XML şema oluşturur `myFile.xdr` ve geçerli dizine kaydeder.

```console
xsd myFile.xdr
```

Aşağıdaki komutu bir XML şema oluşturur `myFile.xml` ve belirtilen dizine kaydeder.

```console
xsd myFile.xml /outputdir:myOutputDir
```

Aşağıdaki komutu olarak kaydeder ve C# dili belirtilen şemada karşılık gelen bir veri kümesi oluşturur `XSDSchemaFile.cs` geçerli dizin.

```console
xsd /dataset /language:CS XSDSchemaFile.xsd
```

Aşağıdaki komutu tüm türleri için XML şemaları derlemesinde oluşturur `myAssembly.dll` ve bunları olarak kaydeder `schema0.xsd` geçerli dizin.

```console
xsd myAssembly.dll
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.DataSet>
- <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
- [Araçlar](../../framework/tools/index.md)
- [Komut Istemleri](../../framework/tools/developer-command-prompt-for-vs.md)
- [LINQ to DataSet Genel Bakış](../../framework/data/adonet/linq-to-dataset-overview.md)
- [Türü Belirtilmiş DataSet’leri Sorgulama](../../framework/data/adonet/querying-typed-datasets.md)
- [LINQ (dil ile tümleşik sorgu) (C#)](../../csharp/programming-guide/concepts/linq/index.md)
- [LINQ (dil ile tümleşik sorgu) (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/index.md)
