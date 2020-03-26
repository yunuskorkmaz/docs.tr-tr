---
title: .NET uygulamaları için kaynak dosyaları oluşturma
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
ms.openlocfilehash: b679539be1aeb593124eb35a235bcc578decb4c0
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111783"
---
# <a name="create-resource-files-for-net-apps"></a>.NET uygulamaları için kaynak dosyaları oluşturma

Uygulamanızda kolayca kullanılabilir hale getirmek için dizeler, görüntüler ve nesneler verileri gibi kaynaklarını ekleyebilirsiniz. .NET Framework, kaynak dosyaları oluşturmak için beş yol sunar:

- Dize kaynaklarını içeren bir metin dosyası oluşturun. Metin dosyasını ikili kaynak (.resources) dosyasına dönüştürmek için [Kaynak Dosya Üretecisini (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) kullanabilirsiniz. Daha sonra bir dil derleyicisi kullanarak bir uygulama yürütülebilir veya bir uygulama kitaplığı ikili kaynak dosyası gömmek, ya da [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md)kullanarak bir uydu derlemek katıştırabilirsiniz. Daha fazla bilgi için [Metin Dosyaları](creating-resource-files-for-desktop-apps.md#TextFiles) bölümündeki Kaynaklar bölümüne bakın.

- Dize, resim veya nesne verilerini içeren bir XML kaynak (.resx) dosyası oluşturun. .resx dosyasını ikili kaynak (.resources) dosyasına dönüştürmek için [Kaynak Dosya Üretecisini (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) kullanabilirsiniz. Daha sonra bir dil derleyicisi kullanarak bir uygulama yürütülebilir veya bir uygulama kitaplığı ikili kaynak dosyası gömmek, ya da [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md)kullanarak bir uydu derlemek katıştırabilirsiniz. Daha fazla bilgi için [.resx Files bölümündeki Kaynaklar](creating-resource-files-for-desktop-apps.md#ResxFiles) bölümüne bakın.

- <xref:System.Resources> ad alanındaki türleri kullanarak program aracılığıyla bir XML kaynak (.resx) dosyası oluşturun . Bir .resx dosyası oluşturabilir, kaynaklarını numaralandırabilir veya belirli kaynaklarını ada göre alabilirsiniz. Daha fazla bilgi için bkz: [.resx Dosyaları Programlı olarak çalışma.](working-with-resx-files-programmatically.md)

- Program aracılığıyla ikili bir kaynak (.resources) dosyası oluşturun. Daha sonra bir dil derleyicisi kullanarak bir uygulama yürütülebilir veya bir uygulama kitaplığı dosya gömmek, ya da [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md)kullanarak bir uydu derlemesi gömmek. Daha fazla bilgi için [.resources Files bölümündeki Kaynaklar](creating-resource-files-for-desktop-apps.md#ResourcesFiles) bölümüne bakın.

- Bir kaynak dosyası oluşturmak ve projenize eklemek için [Visual Studio'yı](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) kullanın. Visual Studio, kaynakları eklemenizi, silmenizi ve değiştirmenizi sağlayan bir kaynak düzenleyicisi sağlar. Derleme sırasında, kaynak dosyası otomatik olarak ikili bir .resources dosyasına dönüştürülür ve bir uygulama derlemesine veya uydu derlemesine gömülür. Daha fazla bilgi için Visual Studio bölümündeki [Kaynak Dosyaları bölümüne](creating-resource-files-for-desktop-apps.md#VSResFiles) bakın.

<a name="TextFiles"></a>
## <a name="resources-in-text-files"></a>Metin dosyalarındaki kaynaklar

Dize kaynaklarını yalnızca depolamak için metin (.txt veya .restext) dosyaları kullanabilirsiniz. Dize olmayan kaynaklar için .resx dosyalarını kullanın veya programlı olarak oluşturun. Dize kaynaklarını içeren metin dosyaları aşağıdaki biçime sahiptir:

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

 Dize kaynakları *ad/değer* çiftleri olarak görünür, *burada ad* kaynağı tanımlayan bir dizedir ve *değer,* *adı* kaynak alma yöntemine geçtiğinde döndürülen kaynak <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>dizesidir. *ad* ve *değer* eşit bir işaretle (=) ayrılmalıdır. Örnek:

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

 .NET Framework 4.5 ile başlayıp .NET Core'un tüm sürümlerinde `#ifdef`metin dosyaları koşullu derlemeyi *sembolle*destekler ... `#endif` ve `#if !` *sembol*... `#endif` inşa eder. Daha sonra sembolleri `/define` tanımlamak için Kaynak Dosya [Üreteci (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) ile anahtarı kullanabilirsiniz. Her kaynak kendi `#ifdef` *sembolü*gerektirir ... `#endif` veya `#if !` *sembol*... `#endif` inşa etmek. Bir `#ifdef` deyim kullanırsanız ve *sembol* tanımlanırsa, ilişkili kaynak .resources dosyasına dahil edilir; aksi takdirde, dahil değildir. Bir `#if !` deyim kullanırsanız ve *sembol* tanımlanmamışsa, ilişkili kaynak .resources dosyasına dahil edilir; aksi takdirde, dahil değildir.

 Yorumlar metin dosyalarında isteğe bağlıdır ve satır başında noktalı virgül (;) veya diyez işareti (#) ile başlanır. Yorumları içeren satırlar dosyanın herhangi bir yerine yerleştirilebilir. Açıklamalar, [Kaynak Dosya Oluşturucusu (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md)kullanılarak oluşturulan derlenmiş .kaynaklar dosyasına dahil edilmez.

 Metin dosyasındaki tüm boş satırlar beyaz boşluk olarak değerlendirilir ve göz ardı edilir.

 Aşağıdaki örnek `OKButton` ve `CancelButton` adındaki iki dize kaynağını tanımlar.

```text
#Define resources for buttons in the user interface.
OKButton=OK
CancelButton=Cancel
```

 Metin dosyası *nda yinelenen ad*oluşumları varsa, Kaynak Dosya [Üreteci (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) bir uyarı görüntüler ve ikinci adı yok sayar.

 *değer* yeni satır karakterleri içeremez, ancak yeni bir satırı temsil `\n` etmek ve `\t` bir sekmeyi temsil etmek gibi C dil stili kaçış karakterlerini kullanabilirsiniz. Kaçarsa bir ters eğik çizgi karakteri de\\\\ekleyebilirsiniz (örneğin, " "). Ayrıca, boş bir dizeye izin verilir.

 UTF-8 kodlama veya UTF-16 kodlama kullanarak metin dosyası biçiminde kaynakları kaydedin ya az endian veya big-endian bayt sırasına göre kodlama. Ancak, .txt dosyasını .resources dosyasına dönüştüren [Kaynak Dosya Üreteci (Resgen.exe),](../tools/resgen-exe-resource-file-generator.md)dosyaları varsayılan olarak UTF-8 olarak ele alır. Resgen.exe'nin, UTF-16 kullanılarak kodlanmış bir dosyayı tanımasını istiyorsanız, dosyanın başına bir Unicode bayt sırası işareti (U+FEFF) eklemeniz gerekir.

 Bir kaynak dosyasını metin biçiminde bir .NET derlemesine gömmek için, [Kaynak Dosya Üretecisini (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md)kullanarak dosyayı ikili kaynak (.kaynaklar) dosyasına dönüştürmeniz gerekir. Daha sonra bir dil derleyicisi kullanarak .resources dosyasını bir .NET derlemesi ne katıştırabilirsiniz veya [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md)kullanarak uydu derlemesi ne katıştırabilirsiniz.

 Aşağıdaki örnek, basit bir "Hello World" konsol uygulaması için GreetingResources.txt adındaki metin biçimindeki bir kaynak dosyayı kullanır. Metin dosyası iki dizeleri `prompt` tanımlar `greeting`ve , kullanıcı kendi adını girmek ve bir selamlama görüntülemek ister.

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
## <a name="resources-in-resx-files"></a>.resx dosyalarındaki kaynaklar
 Yalnızca dize kaynaklarını depolayabilen metin dosyalarından farklı olarak XML kaynak (.resx) dosyaları; dizeleri, resimler, simgeler ve ses klipleri gibi ikili verileri ve programatik nesneleri depolayabilir. Bir .resx dosyası, kaynak girdilerinin biçimini açıklayan ve verileri ayrıştırmak için kullanılan XML'ye ait sürüm oluşturma bilgilerini belirten standart bir başlık içerir. Kaynak dosya verisi XML başlığını izler. Her bir veri öğesi, bir `data` etiketi içinde bulunan bir isim/değer ikilisinden oluşur. Kendi `name` özniteliği kaynak adını tanımlar ve iç içe `value` etiketi kaynak değerini içerir. Dize verisi için, `value` etiketi dizeyi içerir.

 Örneğin aşağıdaki `data` etiketi, değeri "Adınızı girin:" olan `prompt` adındaki bir dize kaynağını tanımlar.

```xml
<data name="prompt" xml:space="preserve">
  <value>Enter your name:</value>
</data>
```

> [!WARNING]
> Şifreleri, güvenlik açısından duyarlı bilgileri veya özel verileri depolamak için kaynak dosyalarını kullanmayın.

 Kaynak nesneleri için **veri** etiketi, `type` kaynağın veri türünü gösteren bir öznitelik içerir. İkili verilerden oluşan nesneler için `data` etiketi, aynı zamanda ikili verilerin `mimetype` türünü gösteren bir `base64` özniteliğini içerir.

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
> .resx dosyaları, önceden tanımlanmış formatta doğru biçimlendirilmiş XML'lerden oluşması gerektiğinden özellikle .resx dosyaları dizeler haricinde kaynaklar içerdiğinde .resx dosyalarıyla el ile çalışılmasını önermeyiz. Bunun yerine Visual Studio,.resx dosyaları oluşturmak ve işlemek için saydam bir arabirim sağlar. [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) Daha fazla bilgi için Visual Studio bölümündeki [Kaynak Dosyaları bölümüne](creating-resource-files-for-desktop-apps.md#VSResFiles) bakın. .resx dosyalarını aynı zamanda program aracılığıyla oluşturabilir ve değiştirebilirsiniz. Daha fazla bilgi için bkz: [.resx Dosyaları Programlı olarak çalışma.](working-with-resx-files-programmatically.md)

<a name="ResourcesFiles"></a>
## <a name="resources-in-resources-files"></a>.resources dosyalarındaki kaynaklar

İkili bir kaynak (.resources) dosyasını program aracılığıyla doğrudan koddan oluşturmak için <xref:System.Resources.ResourceWriter?displayProperty=nameWithType> sınıfını kullanabilirsiniz. Bir metin dosyasından veya .resx dosyasından bir .resources dosyası oluşturmak için [Kaynak Dosya Oluşturucusu'nun (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) de kullanabilirsiniz. .resources dosyası, dize verilerine ek olarak ikili verileri (bayt dizileri) ve nesne verilerini içerebilir. Bir .resources dosyasının program aracılığıyla oluşturulması aşağıdaki adımları gerektirir:

1. Benzersiz bir dosya adı ile bir <xref:System.Resources.ResourceWriter> nesnesi oluşturun. Bunu, bir <xref:System.Resources.ResourceWriter> sınıf yapıcısına bir dosya adı veya bir dosya akışı belirterek gerçekleştirebilirsiniz.

2. Dosyaya eklemek için, adlandırılmış her bir kaynağa ait <xref:System.Resources.ResourceWriter.AddResource%2A?displayProperty=nameWithType> yönteminin aşırı yüklemelerinden birini çağırın. Kaynak bir dize, bir nesne veya bir ikili veri koleksiyonu (bir bayt dizisi) olabilir.

3. Kaynakları dosyaya yazmak ve <xref:System.Resources.ResourceWriter.Close%2A?displayProperty=nameWithType> nesnesini kapatmak için <xref:System.Resources.ResourceWriter> yöntemini çağırın.

> [!NOTE]
> Şifreleri, güvenlik açısından duyarlı bilgileri veya özel verileri depolamak için kaynak dosyalarını kullanmayın.

 Aşağıdaki örnek, altı dizeyi, bir simgeyi ve uygulama tanımlı iki nesneyi (iki `Automobile` nesnesi) depolayan CarResources.resources adındaki bir .resources dosyasını progam aracılığıyla oluşturur. Örnekte `Automobile` tanımlanan ve anında verilen sınıf, ikili serileştirme <xref:System.SerializableAttribute> matter tarafından kalıcı olmasını sağlayan öznitelik ile etiketlenir.

 [!code-csharp[Conceptual.Resources.Resources#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resources/cs/resources1.cs#1)]
 [!code-vb[Conceptual.Resources.Resources#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resources/vb/resources1.vb#1)]

 .resources dosyasını oluşturduktan sonra, dil derleyicisinin `/resource` anahtarını ekleyerek çalışma zamanı yürütülebilir veya kitaplık taslayabilir veya Assembly [Linker (Al.exe)](../tools/al-exe-assembly-linker.md)kullanarak uydu derlemesi'ne katıştırabilirsiniz.

<a name="VSResFiles"></a>
## <a name="resource-files-in-visual-studio"></a>Visual Studio'daki kaynak dosyaları

[Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) projenize bir kaynak dosyası eklediğinizde, Visual Studio proje dizininde bir .resx dosyası oluşturur. Visual Studio, dizeler, görüntüler ve ikili nesneleri eklemenizi sağlayan kaynak düzenleyicileri sağlar. Düzenleyiciler yalnızca statik verileri işlemek için tasarlandığından programatik nesneleri depolamak için kullanılamazlar; nesne verilerini bir .resx dosyasına veya bir .resources dosyasına program aracılığıyla yazmanız gerekir. Daha fazla bilgi için [.resx Dosyaları Programlı olarak çalışma](working-with-resx-files-programmatically.md) ve [.resources Files bölümündeki Kaynaklar](creating-resource-files-for-desktop-apps.md#ResourcesFiles) bölümüne bakın.

Yerelleştirilmiş kaynaklar ekliyorsanız, onlara ana kaynak dosyasıyla aynı kök dosya adını verin. Ayrıca, kendi kültürlerini dosya adında belirlemeniz gerekir. Örneğin, Resources.resx adında bir kaynak dosyası eklerseniz, sırasıyla İngilizce (Amerika Birleşik Devletleri) ve Fransızca (Fransa) kültürleri için yerelleştirilmiş kaynakları tutmak amacıyla aynı zamanda Resources.en-US.resx ve Resources.fr-FR.resx adlı kaynak dosyaları oluşturabilirsiniz. Ayrıca uygulamanın varsayılan kültürünü de belirlemeniz gerekir. Bu, kaynakları belirli bir kültüre ait yerelleştirilmiş kaynaklar bulunamadığında kullanılan kültürdür. Visual Studio'daki Solution Explorer'da varsayılan kültürü belirtmek için proje adını sağ tıklatın, Uygulama'yı işaret edin, **Derleme Bilgileri'ni**tıklatın ve **Tarafsız dil** listesindeki uygun dili/kültürü seçin.

Derleme zamanında Visual Studio, bir projedeki .resx dosyalarını ilk olarak ikili kaynak (.kaynaklar) dosyalarına dönüştürür ve bunları projenin *obj* dizininin bir alt dizininde saklar. Visual Studio, proje tarafından oluşturulmuş ana derlemede yerelleştirilmiş kaynaklar içermeyen tüm kaynak dosyalarını gömer. Eğer herhangi bir kaynak dosyası yerelleştirilmiş kaynakları içeriyorsa Visual Studio her bir yerelleştirilmiş için bu kaynakları ayrı uydu derlemelerine gömer. Daha sonra her uydu derlemesini, adı yerelleştirilmiş kültüre karşılık gelen bir dizinde saklar. Örneğin, yerelleştirilmiş İngilizce (Amerika Birleşik Devletleri) kaynakları, en-US alt dizinindeki bir uydu derlemesinde depolanır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Resources>
- [Masaüstü Uygulamalarında Kaynaklar](index.md)
- [Kaynakları Paketleme ve Dağıtma](packaging-and-deploying-resources-in-desktop-apps.md)
