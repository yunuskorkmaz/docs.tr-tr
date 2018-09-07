---
title: XML şema tanımı Aracı (XSD.exe'nin)
ms.date: 03/30/2017
ms.assetid: a6e6e65c-347f-4494-9457-653bf29baac2
ms.openlocfilehash: a3a16e92dab6994de6bfa99c248ff0b13658e22d
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44079753"
---
# <a name="xml-schema-definition-tool-xsdexe"></a>XML şema tanımı Aracı (XSD.exe'nin)
XML şema tanımı (XSD.exe'nin) aracı XDR, XML ve XSD dosyalarından veya bir çalışma zamanı derleme sınıflarda XML Şeması veya ortak dil çalışma zamanı sınıflar oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
xsd file.xdr [/outputdir:directory][/parameters:file.xml]  
xsd file.xml [/outputdir:directory] [/parameters:file.xml]  
xsd file.xsd {/classes | /dataset} [/element:element]   
             [/enableLinqDataSet] [/language:language]   
                          [/namespace:namespace] [/outputdir:directory] [URI:uri]   
                          [/parameters:file.xml]  
xsd {file.dll | file.exe} [/outputdir:directory] [/type:typename [...]][/parameters:file.xml]  
```  
  
## <a name="argument"></a>Bağımsız Değişken  
  
|Bağımsız Değişken|Açıklama|  
|--------------|-----------------|  
|*file.extension*|Dönüştürülecek giriş dosyasını belirtir. Extensionas şunlardan birini belirtmelidir: .xdr, .xml, .xsd, .dll veya .exe.<br /><br /> XDR şema dosyası (.xdr uzantısı) belirtirseniz, xsd.exe'nin bir XSD şemasına XDR şeması dönüştürür. Çıkış dosyası XDR şeması, ancak .xsd uzantısı ile aynı ada sahip.<br /><br /> Bir XML dosyası (.xml uzantısı) belirtirseniz, xsd.exe'nin veri dosyasındaki bir şema öğesinin ve bir XSD şeması üretir. Çıkış dosyası XML dosyası olarak, ancak .xsd uzantısı ile aynı ada sahip.<br /><br /> Bir XML şema dosyası (.xsd uzantısı) belirtirseniz, xsd.exe'nin için XML Şeması karşılık gelen çalışma zamanı nesneler için kaynak kodu oluşturur.<br /><br /> Bir çalışma zamanı derleme dosyası (.exe veya .dll uzantısı) belirtirseniz, xsd.exe'nin şemaları bir veya daha fazla türleri için bu derlemede oluşturur. Kullanabilirsiniz `/type` şemaları oluşturulacak türlerini belirtmek için seçeneği. Çıkış şemaları schema0.xsd, schema1.xsd vb. adlandırılır. Yalnızca belirli türlerini kullanarak bir ad belirtmezseniz XSD.exe'nin üretir birden çok şema `XMLRoot` özel öznitelik.|  
  
## <a name="general-options"></a>Genel seçenekleri  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/h**[**elp**]|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|**/o**[**utputdir**] **: *** dizini*|Çıktı dosyaları dizinini belirtir. Bu bağımsız değişken yalnızca bir kez görünebilir. Geçerli dizin varsayılandır.|  
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|**/P [parametreleri]:** *file.xml*|Çeşitli işlem modları için seçenekler belirtilen .xml dosyasından okuyun. Kısa form ' / p:'. Daha fazla bilgi için aşağıdaki Açıklamalar bölümüne bakın.|  
  
## <a name="xsd-file-options"></a>XSD dosyası seçenekleri  
 .Xsd dosyaları için aşağıdaki seçeneklerden birini belirtmelisiniz.  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/c**[**sınıfları**]|Belirtilen şemaya karşılık gelen sınıflar oluşturur. XML veri nesnesine okumak için kullanın `System.Xml.Serialization.XmlSerializer.Deserializer` yöntemi.|  
|**/d**[**ataset**]|Türetilen bir sınıf oluşturur <xref:System.Data.DataSet> belirtilen şemaya karşılık gelir. Türetilen sınıfın XML verileri okumak için kullanın `System.Data.DataSet.ReadXml` yöntemi.|  
  
 .Xsd dosyaları için aşağıdaki seçeneklerden birini belirleyebilirsiniz.  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/e**[**uygu**] **: *** öğesi*|Öğe için kod oluşturmak için şema belirtir. Varsayılan olarak tüm öğeler yazılmalıdır. Bu bağımsız değişken birden çok kez belirtebilirsiniz.|  
|**/enableDataBinding**|Uygular <xref:System.ComponentModel.INotifyPropertyChanged> veri bağlama etkinleştirmek için oluşturulan tüm türleri arabirimi. Kısa form `/edb`.|  
|**/enableLinqDataSet**|(Kısa form: `/eld`.) Oluşturulan veri kümesi LINQ to DataSet kullanarak karşı sorgulanabilir belirtir. Bu seçenek /dataset seçeneği de belirtildiğinde kullanılır. Daha fazla bilgi için [LINQ to DataSet genel bakış](../../../docs/framework/data/adonet/linq-to-dataset-overview.md) ve [yazılan veri kümelerini sorgulama](../../../docs/framework/data/adonet/querying-typed-datasets.md). LINQ kullanma hakkında genel bilgi için bkz. [LINQ (dil ile tümleşik sorgu)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d).|  
|**/f**[**lanları**]|Alanları özellikleri yerine oluşturur. Varsayılan olarak, özellikleri üretilir.|  
|**/l**[**dil**] **: *** dil*|Kullanmak için programlama dilini belirtir. Aralarından seçim `CS` (C varsayılan değer olan #), `VB` (Visual Basic) `JS` (JScript) veya `VJS` (Visual J#). Ayrıca bir sınıf uygulamak için tam bir ad belirtin<xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>|  
|**/n**[**amespace**] **: *** ad alanı*|Oluşturulan türleri için çalışma zamanı ad alanını belirtir. Varsayılan ad alanı `Schemas`.|  
|**/nologo**|Başlık göstermez.|  
|**/ ORDER**|Tüm parçacık üyeleri açık sipariş tanımlayıcılarını oluşturur.|  
|**/o [ut]:** *directoryName*|Dosyalarında yerleştirmek için çıktı dizini belirtir. Geçerli dizin varsayılandır.|  
|**/u**[**RI**] **: *** URI'si*|Öğeler için URI için kod oluşturmak için şema belirtir. Bu URI varsa, ile belirtilen tüm öğelere uygulanır `/element` seçeneği.|  
  
## <a name="dll-and-exe-file-options"></a>DLL ve EXE dosya seçenekleri  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/t**[**türü**] **: *** typename*|Şema için oluşturulacak tür adını belirtir. Birden çok tür bağımsız değişkeni belirtebilirsiniz. Varsa *typename* bir ad alanı belirtilen türle tüm türleri derlemesinde XSD.exe'nin eşleşme belirtmiyor. Varsa *typename* türü eşleşen bir ad alanı, yalnızca belirtir. Varsa *typename* bir yıldız işareti karakter ile sona erer (\*), aracı eşleştirir önceki dizesi ile başlayan tüm türleri \*. Unutursanız, `/type` seçeneği XSD.exe'nin derlemesinde tüm türler için şemalar oluşturur.|  
  
## <a name="remarks"></a>Açıklamalar  
 Aşağıdaki tablo operasyonları XSD.exe'nin gerçekleştireceğini gösterir.  
  
 XDR XSD için  
 Bir XML şeması bir XML veri azaltılmış şema dosyasından oluşturur. XDR erken bir XML tabanlı şema biçimidir.  
  
 XML için XSD  
 Bir XML Şeması XML dosyasından oluşturur.  
  
 Veri kümesi için XSD  
 Ortak dil çalışma zamanı oluşturur <xref:System.Data.DataSet> bir XSD şema dosyasından sınıfları. Oluşturulan sınıflar için normal XML verileri zengin nesne modeli sağlar.  
  
 XSD sınıflar için  
 Bir XSD şema dosyasından çalışma zamanı sınıflar oluşturur. Oluşturulan sınıflar birlikte kullanılabilecek <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> okuma ve yazma şema izleyen XML kodu.  
  
 XSD için sınıflar  
 Bir XML şeması bir türü veya türleri bir çalışma zamanı derleme dosyası oluşturur. Oluşturulan şema tarafından kullanılan XML biçiminde tanımlar `System.Xml.Serialization.XmlSerializer`.  
  
 XSD.exe'nin yalnızca World Wide Web Konsorsiyumu (W3C) tarafından önerilen XML şema tanımı (XSD) dil izleyin XML şemaları yönetmenize olanak sağlar. XML şema tanımı teklif veya XML standart hakkında daha fazla bilgi için bkz. http://w3.org.  
  
## <a name="setting-options-with-an-xml-file"></a>Bir XML dosyası ile seçenekleri ayarlama  
 Kullanarak `/parameters` anahtarı, çeşitli seçenekler ayarlar tek bir XML dosyası belirtebilirsiniz. Nasıl XSD.exe'nin aracını kullanarak ayarlayabilirsiniz seçenekler bağlıdır. Seçenekler şunlardır şemaları oluşturmak, kod dosyaları oluşturmak veya dahil kod dosyaları oluşturmak `DataSet` özellikleri. Örneğin, ayarlayabilirsiniz `<assembly\>` öğesi için bir yürütülebilir (.exe) veya bir şema oluşturulurken türü kitaplık (.dll) dosyası, ancak bir kod dosyası değil oluşturulurken adı. Aşağıdaki XML nasıl kullanılacağı gösterilmiştir `<generateSchemas\>` belirtilen yürütülebilir öğe:  
  
```xml  
<!-- This is in a file named GenerateSchemas.xml. -->  
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>  
<generateSchemas>  
   <assembly>ConsoleApplication1.exe</assembly>  
</generateSchemas>  
</xsd>  
```  
  
 Önceki XML GenerateSchemas.xml adlı bir dosyaya içeriyorsa, ardından kullanmak `/parameters` komut istemine aşağıdakileri yazıp ENTER tuşuna basarak geçin:  
  
 `xsd /p:GenerateSchemas.xml`  
  
 Diğer yandan, derlemede bulunan tek bir tür için bir şema oluşturuyorsanız, aşağıdaki XML kullanabilirsiniz:  
  
```xml  
<!-- This is in a file named GenerateSchemaFromType.xml. -->  
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>  
<generateSchemas>  
   <type>IDItems</type>  
</generateSchemas>  
</xsd>  
```  
  
 Ancak, önceki kodu kullanmak için da komut isteminde derlemenin adı sağlamanız gerekir. (Pek fazla XML dosyası GenerateSchemaFromType.xml adlı) bir komut istemine şunu yazın:  
  
 `xsd /p:GenerateSchemaFromType.xml ConsoleApplication1.exe`  
  
 İçin aşağıdaki seçeneklerden birini belirtmelisiniz `\<generateSchemas>` öğesi.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|\<Derleme >|Şema oluşturmak için bir derleme belirtir.|  
|\<türü >|Bir türü için bir şema oluşturmak için bir derleme bulundu belirtir.|  
|\<xml>|Bir XML dosyası için bir şema oluşturmak için belirtir.|  
|\<xdr>|İçin bir şema oluşturmak için bir XDR dosyasını belirtir.|  
  
 Bir kod dosyası oluşturmak için kullanılan `<generateClasses\>` öğesi. Aşağıdaki örnek, bir kod dosyası oluşturur. Oluşturulan dosyanın ad alanı ve programlama dili ayarlamanızı izin iki öznitelik de gösterilir unutmayın.  
  
```xml  
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>  
<generateClasses language='VB' namespace='Microsoft.Serialization.Examples'/>  
</xsd>  
<!-- You must supply an .xsd file when typing in the command line.-->  
<!-- For example: xsd /p:genClasses mySchema.xsd -->  
```  
  
 Seçenekleri için Ayarla `\<generateClasses>` öğesi şunlar.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|\<öğesi >|Bir öğe için kod oluşturmak üzere .xsd dosyasını belirtir.|  
|\<schemaImporterExtensions >|Türetilen bir türü belirtiyor. <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> sınıfı.|  
|\<Şema >|Kodunu oluşturmak için bir XML şema dosyası belirtir.  Birden çok XML Şeması dosya birden fazla belirtilebilir \<şema > öğeleri.|  
  
 Aşağıdaki tablo ile kullanılabilen öznitelikleri gösterir `<generateClasses\>` öğesi.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|dil|Kullanmak için programlama dilini belirtir. Aralarından seçim `CS` (C#, varsayılan), `VB` (Visual Basic) `JS` (JScript) veya `VJS` (Visual J#). Ayrıca uygulayan bir sınıf için tam bir ad belirtin <xref:System.CodeDom.Compiler.CodeDomProvider>.|  
|ad alanı|Oluşturulan kodun ad alanını belirtir. Ad alanı CLR standartları (örneğin, boşluk veya ters eğik çizgi karakterleri) uyması gerekir.|  
|seçenekler|Aşağıdaki değerlerden biri: `none`, `properties` (ortak alanları yerine özellikleri oluşturur), `order`, veya `enableDataBinding` (bkz `/order` ve `/enableDataBinding` XSD dosyası seçenekleri kısmına anahtarları.|  
  
 De denetleyebilirsiniz nasıl `DataSet` kod kullanarak oluşturulur `<generateDataSets\>` öğesi. Aşağıdaki XML belirten oluşturulan codeuses `DataSet` yapıları (gibi <xref:System.Data.DataTable> sınıfı) bir belirtilen öğe için Visual Basic kodunu oluşturmak için. Oluşturulan veri kümesi yapıları LINQ sorguları destekler.  
  
 `<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>`  
  
 `<generateDataSet language='VB' namespace='Microsoft.Serialization.Examples' enableLinqDataSet='true'>`  
  
 `</generateDataSet>`  
  
 `</xsd>`  
  
 Seçenekleri için Ayarla `<generateDataSet\>` öğesi şunlar.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|\<Şema >|Kodunu oluşturmak için bir XML şeması dosyasını belirtir. Birden çok XML Şeması dosya birden fazla belirtilebilir \<şema > öğeleri.|  
  
 Aşağıdaki tabloda kullanılabilir öznitelikleri gösterir `<generateDataSet\>` öğesi.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|enableLinqDataSet|Oluşturulan veri kümesi LINQ to DataSet kullanarak karşı sorgulanabilir belirtir. Varsayılan değer false'tur.|  
|dil|Kullanmak için programlama dilini belirtir. Aralarından seçim `CS` (C#, varsayılan), `VB` (Visual Basic) `JS` (JScript) veya `VJS` (Visual J#). Ayrıca uygulayan bir sınıf için tam bir ad belirtin <xref:System.CodeDom.Compiler.CodeDomProvider>.|  
|ad alanı|Oluşturulan kodun ad alanını belirtir. Ad alanı CLR standartları (örneğin, boşluk veya ters eğik çizgi karakterleri) uyması gerekir.|  
  
 En üst düzey ayarladığınız öznitelikleri vardır `<xsd\>` öğesi. Herhangi bir alt öğelerinin bu seçenekler kullanılabilir (`<generateSchemas\>`, `<generateClasses\>` veya `<generateDataSet\>`). Aşağıdaki XML kodu "MyOutputDirectory" adlı Çıktı dizininde "IDItems" adlı bir öğe için kod oluşturur.  
  
```xml  
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/' output='MyOutputDirectory'>  
<generateClasses>  
<element>IDItems</element>  
</generateClasses>  
</xsd>  
```  
  
 Aşağıdaki tablo ile kullanılabilen öznitelikleri gösterir `\<xsd>` öğesi.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|çıktı|Oluşturulan şema veya kod dosyanın yerleştirileceği bir dizinin adı.|  
|nologo|Başlık göstermez. Ayarlanan `true` veya `false`.|  
|Yardım|Araç için komut sözdizimini ve seçenekleri görüntüler. Ayarlanan `true` veya `false`.|  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki komutu bir XML şema oluşturur `myFile.xdr` ve geçerli dizine kaydeder.  
  
```  
xsd myFile.xdr   
```  
  
 Aşağıdaki komutu bir XML şema oluşturur `myFile.xml` ve belirtilen dizine kaydeder.  
  
```  
xsd myFile.xml /outputdir:myOutputDir  
```  
  
 Aşağıdaki komutu olarak kaydeder ve C# dili belirtilen şemada karşılık gelen bir veri kümesi oluşturur `XSDSchemaFile.cs` geçerli dizin.  
  
```  
xsd /dataset /language:CS XSDSchemaFile.xsd  
```  
  
 Aşağıdaki komutu tüm türleri için XML şemaları derlemesinde oluşturur `myAssembly.dll` ve bunları olarak kaydeder `schema0.xsd` geçerli dizin.  
  
```  
xsd myAssembly.dll    
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.DataSet>  
- <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>  
- [Araçlar](../../../docs/framework/tools/index.md)      
- [Komut İstemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md)  
- [LINQ to DataSet Genel Bakış](../../../docs/framework/data/adonet/linq-to-dataset-overview.md)  
- [Türü Belirtilmiş DataSet’leri Sorgulama](../../../docs/framework/data/adonet/querying-typed-datasets.md)  
- [LINQ (dil ile tümleşik sorgu)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)
