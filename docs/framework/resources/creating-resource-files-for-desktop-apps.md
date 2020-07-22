---
title: .NET uygulamaları için kaynak dosyaları oluşturma
description: .NET uygulamaları için kaynak dosyaları oluşturun. Dize kaynakları, XML veya ikili dosyaları programlama yoluyla veya dize, resim veya nesne verileri içeren XML dosyaları ile metin dosyaları oluşturun.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- resource files, .resources files
- .resources files
- application resources, creating files
- resource files, creating
ms.assetid: 6c5ad891-66a0-4e7a-adcf-f41863ba6d8d
ms.openlocfilehash: 4730a14e499c75176d7ba7c8378626070d5211e9
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865183"
---
# <a name="create-resource-files-for-net-apps"></a>.NET uygulamaları için kaynak dosyaları oluşturma

Uygulamanızda kolayca kullanılabilir hale getirmek için dizeler, görüntüler ve nesneler verileri gibi kaynaklarını ekleyebilirsiniz. .NET Framework, kaynak dosyaları oluşturmak için beş yol sunar:

- Dize kaynaklarını içeren bir metin dosyası oluşturun. Metin dosyasını ikili kaynak (. resources) dosyasına dönüştürmek için [kaynak dosya Oluşturucu (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) kullanabilirsiniz. Daha sonra bir dil derleyicisi kullanarak bir uygulama yürütülebilir dosyasına veya bir uygulama kitaplığına ikili kaynak dosyasını ekleyebilir veya [derleme Bağlayıcısı (Al.exe)](../tools/al-exe-assembly-linker.md)kullanarak bir uydu derlemesine gömebilirsiniz. Daha fazla bilgi için [metin dosyalarındaki kaynaklar](creating-resource-files-for-desktop-apps.md#TextFiles) bölümüne bakın.

- Dize, resim veya nesne verilerini içeren bir XML kaynak (.resx) dosyası oluşturun. . Resx dosyasını ikili bir kaynak dosyasına (. resources) dönüştürmek için [kaynak dosya Oluşturucu (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) kullanabilirsiniz. Daha sonra bir dil derleyicisi kullanarak bir uygulama yürütülebilir dosyasına veya bir uygulama kitaplığına ikili kaynak dosyasını ekleyebilir veya [derleme Bağlayıcısı (Al.exe)](../tools/al-exe-assembly-linker.md)kullanarak bir uydu derlemesine gömebilirsiniz. Daha fazla bilgi için [. resx dosyaları bölümündeki kaynaklar](creating-resource-files-for-desktop-apps.md#ResxFiles) bölümüne bakın.

- <xref:System.Resources> ad alanındaki türleri kullanarak program aracılığıyla bir XML kaynak (.resx) dosyası oluşturun . Bir .resx dosyası oluşturabilir, kaynaklarını numaralandırabilir veya belirli kaynaklarını ada göre alabilirsiniz. Daha fazla bilgi için bkz [.. resx dosyalarıyla programlama yoluyla çalışma](working-with-resx-files-programmatically.md).

- Program aracılığıyla ikili bir kaynak (.resources) dosyası oluşturun. Daha sonra bir dil derleyicisi kullanarak dosyayı bir uygulama yürütülebilir dosyasına veya uygulama kitaplığına katıştırabilir veya [derleme Bağlayıcısı (Al.exe)](../tools/al-exe-assembly-linker.md)kullanarak bir uydu derlemesine gömebilirsiniz. Daha fazla bilgi için bkz [. resources Files bölümündeki Resources](creating-resource-files-for-desktop-apps.md#ResourcesFiles) .

- [Visual Studio 'yu](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) kullanarak bir kaynak dosyası oluşturun ve bu dosyayı projenize ekleyin. Visual Studio, kaynakları eklemenizi, silmenizi ve değiştirmenizi sağlayan bir kaynak düzenleyicisi sağlar. Derleme sırasında, kaynak dosyası otomatik olarak ikili bir .resources dosyasına dönüştürülür ve bir uygulama derlemesine veya uydu derlemesine gömülür. Daha fazla bilgi için bkz. [Visual Studio 'Da kaynak dosyaları](creating-resource-files-for-desktop-apps.md#VSResFiles) bölümü.

<a name="TextFiles"></a>
## <a name="resources-in-text-files"></a>Metin dosyalarındaki kaynaklar

Yalnızca dize kaynaklarını depolamak için metin (. txt veya. restext) dosyalarını kullanabilirsiniz. Dize olmayan kaynaklar için. resx dosyalarını kullanın veya program aracılığıyla oluşturun. Dize kaynaklarını içeren metin dosyaları aşağıdaki biçime sahiptir:

```text
# This is an optional comment.
name = value

; This is another optional comment.
name = value

; The following supports conditional compilation if X is defined.
#ifdef X
name1=value1
name2=value2
#endif

# The following supports conditional compilation if Y is undefined.
#if !Y
name1=value1
name2=value2
#endif
```

 .txt ve .restext dosyalarının kaynak dosya biçimi aynıdır. .restext dosya uzantısı yalnızca metin dosyalarının metin tabanlı kaynak dosyaları olarak hemen tanımlanabilmesi için hizmet verir.

 Dize kaynakları *ad/değer* çiftleri olarak görünür; burada *ad* kaynağı tanımlayan bir dizedir ve *değer* , gibi bir kaynak alımı *yöntemine geçirdiğinizde döndürülen* kaynak dizesidir <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> . *ad* ve *değerin* eşittir işareti (=) ile ayrılması gerekir. Örnek:

```text
FileMenuName=File
EditMenuName=Edit
ViewMenuName=View
HelpMenuName=Help
```

> [!CAUTION]
> Şifreleri, güvenlik açısından duyarlı bilgileri veya özel verileri depolamak için kaynak dosyalarını kullanmayın.

 Boş dizelere (yani değeri <xref:System.String.Empty?displayProperty=nameWithType> olan bir kaynak) metin dosyalarında izin verilir. Örnek:

```text
EmptyString=
```

 .NET Framework 4,5 ve tüm .NET Core sürümlerinde, metin dosyaları `#ifdef` *symbol*... `#endif` ve `#if !` *symbol*... yapılar ile koşullu derlemeyi destekler `#endif` . Ardından, `/define` sembolleri tanımlamak Için [kaynak dosya oluşturucu (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) ile anahtarı kullanabilirsiniz. Her kaynak kendi `#ifdef` *simgesini*gerektiriyor... `#endif` veya `#if !` *symbol*... `#endif` yapı. Bir `#ifdef` ifade ve *sembol* kullanırsanız, ilişkili kaynak. resources dosyasına dahil edilir; Aksi takdirde, dahil değildir. Bir `#if !` ifade kullanırsanız ve *sembol* tanımlı değilse, ilişkili kaynak. resources dosyasına dahil edilir; Aksi takdirde, dahil değildir.

 Yorumlar metin dosyalarında isteğe bağlıdır ve satır başında noktalı virgül (;) veya diyez işareti (#) ile başlanır. Yorumları içeren satırlar dosyanın herhangi bir yerine yerleştirilebilir. Açıklamalar, [kaynak dosya Oluşturucu (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md)kullanılarak oluşturulan derlenmiş bir. resources dosyasına dahil edilmez.

 Metin dosyasındaki tüm boş satırlar beyaz boşluk olarak değerlendirilir ve göz ardı edilir.

 Aşağıdaki örnek `OKButton` ve `CancelButton` adındaki iki dize kaynağını tanımlar.

```text
#Define resources for buttons in the user interface.
OKButton=OK
CancelButton=Cancel
```

 Metin dosyası, *adın*Yinelenen oluşumlarını içeriyorsa, [kaynak dosya Oluşturucu (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) bir uyarı görüntüler ve ikinci adı yoksayar.

 *değer* yeni satır karakterleri içeremez, ancak `\n` Yeni bir satırı göstermek ve `\t` bir sekmeyi göstermek için gibi C dil stili kaçış karakterlerini de kullanabilirsiniz. Ayrıca, bir ters eğik çizgi karakteri (örneğin, " \\ \\ ") ekleyebilirsiniz. Ayrıca, boş bir dizeye izin verilir.

 Küçük endian veya Big-endian bayt düzeninde UTF-8 kodlaması veya UTF-16 kodlaması kullanarak, kaynakları metin dosyası biçiminde kaydedin. Ancak, bir. txt dosyasını. resources dosyasına dönüştüren [kaynak dosyası Oluşturucu (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md), dosyaları varsayılan olarak UTF-8 olarak değerlendirir. Resgen.exe'nin, UTF-16 kullanılarak kodlanmış bir dosyayı tanımasını istiyorsanız, dosyanın başına bir Unicode bayt sırası işareti (U+FEFF) eklemeniz gerekir.

 Bir kaynak dosyasını bir .NET derlemesine metin biçiminde eklemek için, [kaynak dosya Oluşturucu (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md)kullanarak dosyayı ikili bir kaynak (. resources) dosyasına dönüştürmeniz gerekir. Daha sonra bir dil derleyicisi kullanarak. resources dosyasını bir .NET derlemesine katıştırabilir veya [derleme Bağlayıcısı (Al.exe)](../tools/al-exe-assembly-linker.md)kullanarak bir uydu derlemesine gömebilirsiniz.

 Aşağıdaki örnek, basit bir "Hello World" konsol uygulaması için GreetingResources.txt adındaki metin biçimindeki bir kaynak dosyayı kullanır. Metin dosyası iki dizeyi tanımlar `prompt` ve `greeting` kullanıcıdan adını girmesini ve bir selamlama görüntülemesini ister.

```text
# GreetingResources.txt
# A resource file in text format for a "Hello World" application.
#
# Initial prompt to the user.
prompt=Enter your name:
# Format string to display the result.
greeting=Hello, {0}!
```

Metin dosyası, aşağıdaki komut kullanılarak bir .resources dosyasına dönüştürülür:

```console
resgen GreetingResources.txt
```

 Aşağıdaki örnek, kullanıcıya mesajlar göstermek için .resource dosyasını kullanan bir konsol uygulamasının kaynak kodunu gösterir.

 [!code-csharp[Conceptual.Resources.TextFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.textfiles/cs/greeting.cs#1)]
 [!code-vb[Conceptual.Resources.TextFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.textfiles/vb/greeting.vb#1)]

 Eğer Visual Basic kullanıyorsanız ve kaynak kod dosyanız Greeting.vb olarak adlandırılmışsa aşağıdaki komut, gömülü .resources dosyasını içeren yürütülebilir bir dosya oluşturur:

```console
vbc greeting.vb -resource:GreetingResources.resources
```

 Eğer C# kullanıyorsanız ve kaynak kod dosyanız Greeting.cs olarak adlandırılmışsa aşağıdaki komut, gömülü .resources dosyasını içeren yürütülebilir bir dosya oluşturur:

```console
csc greeting.cs -resource:GreetingResources.resources
```

<a name="ResxFiles"></a>
## <a name="resources-in-resx-files"></a>. Resx dosyalarındaki kaynaklar
 Yalnızca dize kaynaklarını depolayabilen metin dosyalarından farklı olarak XML kaynak (.resx) dosyaları; dizeleri, resimler, simgeler ve ses klipleri gibi ikili verileri ve programatik nesneleri depolayabilir. Bir .resx dosyası, kaynak girdilerinin biçimini açıklayan ve verileri ayrıştırmak için kullanılan XML'ye ait sürüm oluşturma bilgilerini belirten standart bir başlık içerir. Kaynak dosya verisi XML başlığını izler. Her bir veri öğesi, bir `data` etiketi içinde bulunan bir isim/değer ikilisinden oluşur. Kendi `name` özniteliği kaynak adını tanımlar ve iç içe `value` etiketi kaynak değerini içerir. Dize verisi için, `value` etiketi dizeyi içerir.

 Örneğin aşağıdaki `data` etiketi, değeri "Adınızı girin:" olan `prompt` adındaki bir dize kaynağını tanımlar.

```xml
<data name="prompt" xml:space="preserve">
  <value>Enter your name:</value>
</data>
```

> [!WARNING]
> Şifreleri, güvenlik açısından duyarlı bilgileri veya özel verileri depolamak için kaynak dosyalarını kullanmayın.

 Kaynak nesnelerinde **veri** etiketi, `type` kaynağın veri türünü gösteren bir özniteliği içerir. İkili verilerden oluşan nesneler için `data` etiketi, aynı zamanda ikili verilerin `mimetype` türünü gösteren bir `base64` özniteliğini içerir.

> [!NOTE]
> Tüm .resx dosyaları, belirli bir tür için ikili verileri oluşturmak ve ayrıştırmak amacıyla bir ikili seri biçimlendirici kullanır. Sonuç olarak, bir nesnenin ikili serileştirme biçimi uyumsuz bir şekilde değişirse bir .resx dosyası geçersiz hale gelebilir.

 Aşağıdaki örnek, bir <xref:System.Int32> kaynağını ve bir eşlem görüntüsünü içeren .resx dosyasının bir bölümünü gösterir.

```xml
<data name="i1" type="System.Int32, mscorlib">
  <value>20</value>
</data>

<data name="flag" type="System.Drawing.Bitmap, System.Drawing,
    Version=1.0.5000.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"
    mimetype="application/x-microsoft.net.object.bytearray.base64">
  <value>
    AAEAAAD/////AQAAAAAAAAAMAgAAADtTeX…
  </value>
</data>
```

> [!IMPORTANT]
> .resx dosyaları, önceden tanımlanmış formatta doğru biçimlendirilmiş XML'lerden oluşması gerektiğinden özellikle .resx dosyaları dizeler haricinde kaynaklar içerdiğinde .resx dosyalarıyla el ile çalışılmasını önermeyiz. Bunun yerine, [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) . resx dosyalarını oluşturmak ve işlemek için saydam bir arabirim sağlar. Daha fazla bilgi için bkz. [Visual Studio 'Da kaynak dosyaları](creating-resource-files-for-desktop-apps.md#VSResFiles) bölümü. .resx dosyalarını aynı zamanda program aracılığıyla oluşturabilir ve değiştirebilirsiniz. Daha fazla bilgi için bkz [.. resx dosyalarıyla programlama yoluyla çalışma](working-with-resx-files-programmatically.md).

<a name="ResourcesFiles"></a>
## <a name="resources-in-resources-files"></a>. Resources dosyalarındaki kaynaklar

İkili bir kaynak (.resources) dosyasını program aracılığıyla doğrudan koddan oluşturmak için <xref:System.Resources.ResourceWriter?displayProperty=nameWithType> sınıfını kullanabilirsiniz. Ayrıca, bir metin dosyasından veya. resx dosyasından bir. resources dosyası oluşturmak için [kaynak dosya Oluşturucu (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) kullanabilirsiniz. .resources dosyası, dize verilerine ek olarak ikili verileri (bayt dizileri) ve nesne verilerini içerebilir. Bir .resources dosyasının program aracılığıyla oluşturulması aşağıdaki adımları gerektirir:

1. Benzersiz bir dosya adı ile bir <xref:System.Resources.ResourceWriter> nesnesi oluşturun. Bunu, bir <xref:System.Resources.ResourceWriter> sınıf yapıcısına bir dosya adı veya bir dosya akışı belirterek gerçekleştirebilirsiniz.

2. Dosyaya eklemek için, adlandırılmış her bir kaynağa ait <xref:System.Resources.ResourceWriter.AddResource%2A?displayProperty=nameWithType> yönteminin aşırı yüklemelerinden birini çağırın. Kaynak bir dize, bir nesne veya bir ikili veri koleksiyonu (bir bayt dizisi) olabilir.

3. Kaynakları dosyaya yazmak ve <xref:System.Resources.ResourceWriter.Close%2A?displayProperty=nameWithType> nesnesini kapatmak için <xref:System.Resources.ResourceWriter> yöntemini çağırın.

> [!NOTE]
> Şifreleri, güvenlik açısından duyarlı bilgileri veya özel verileri depolamak için kaynak dosyalarını kullanmayın.

 Aşağıdaki örnek, altı dizeyi, bir simgeyi ve uygulama tanımlı iki nesneyi (iki `Automobile` nesnesi) depolayan CarResources.resources adındaki bir .resources dosyasını progam aracılığıyla oluşturur. `Automobile`Örnekte tanımlanan ve örneği oluşturulan sınıf, <xref:System.SerializableAttribute> ikili serileştirme biçimlendiricisi tarafından kalıcı hale getirilmesini sağlayan özniteliğiyle etiketlenmiştir.

 [!code-csharp[Conceptual.Resources.Resources#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resources/cs/resources1.cs#1)]
 [!code-vb[Conceptual.Resources.Resources#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resources/vb/resources1.vb#1)]

 . Resources dosyasını oluşturduktan sonra, dil derleyicisinin anahtarını ekleyerek bir çalışma zamanı yürütülebilir dosyasına veya kitaplığına eklenebilir `/resource` veya [derleme bağlayıcısı (Al.exe)](../tools/al-exe-assembly-linker.md)kullanarak bir uydu derlemesine gömebilirsiniz.

<a name="VSResFiles"></a>
## <a name="resource-files-in-visual-studio"></a>Visual Studio 'da kaynak dosyaları

[Visual](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) Studio projenize bir kaynak dosyası eklediğinizde, Visual Studio proje dizininde bir. resx dosyası oluşturur. Visual Studio, dizeler, görüntüler ve ikili nesneleri eklemenizi sağlayan kaynak düzenleyicileri sağlar. Düzenleyiciler yalnızca statik verileri işlemek için tasarlandığından programatik nesneleri depolamak için kullanılamazlar; nesne verilerini bir .resx dosyasına veya bir .resources dosyasına program aracılığıyla yazmanız gerekir. Daha fazla bilgi için bkz [.. resx dosyalarıyla çalışma programlı](working-with-resx-files-programmatically.md) ve [kaynakları. resources dosyaları](creating-resource-files-for-desktop-apps.md#ResourcesFiles) bölümünde.

Yerelleştirilmiş kaynaklar ekliyorsanız, ana kaynak dosyası ile aynı kök dosya adını verin. Ayrıca dosya adında kültürünü de atamanız gerekir. Örneğin, Resources.resx adında bir kaynak dosyası eklerseniz, sırasıyla İngilizce (Amerika Birleşik Devletleri) ve Fransızca (Fransa) kültürleri için yerelleştirilmiş kaynakları tutmak amacıyla aynı zamanda Resources.en-US.resx ve Resources.fr-FR.resx adlı kaynak dosyaları oluşturabilirsiniz. Ayrıca uygulamanın varsayılan kültürünü de belirlemeniz gerekir. Bu, kaynakları belirli bir kültüre ait yerelleştirilmiş kaynaklar bulunamadığında kullanılan kültürdür. Varsayılan kültürü belirtmek için, Visual Studio 'da Çözüm Gezgini ' de, proje adına sağ tıklayın, uygulama üzerine gelin, **derleme bilgileri**' ne tıklayın ve **nötr dil** listesinde uygun dili/kültürü seçin.

Derleme zamanında, Visual Studio önce bir projedeki. resx dosyalarını ikili kaynak (. resources) dosyalarına dönüştürür ve bunları projenin *obj* dizininin bir alt dizininde depolar. Visual Studio, proje tarafından oluşturulmuş ana derlemede yerelleştirilmiş kaynaklar içermeyen tüm kaynak dosyalarını gömer. Eğer herhangi bir kaynak dosyası yerelleştirilmiş kaynakları içeriyorsa Visual Studio her bir yerelleştirilmiş için bu kaynakları ayrı uydu derlemelerine gömer. Ardından her uydu derlemesini, adı yerelleştirilmiş kültüre karşılık gelen bir dizinde depolar. Örneğin, yerelleştirilmiş İngilizce (Amerika Birleşik Devletleri) kaynakları, en-US alt dizinindeki bir uydu derlemesinde depolanır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Resources>
- [Masaüstü uygulamalarındaki kaynaklar](index.md)
- [Kaynakları Paketleme ve Dağıtma](packaging-and-deploying-resources-in-desktop-apps.md)
