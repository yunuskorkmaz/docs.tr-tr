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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c7ff34285220fd1e3c17503a8387104e91ec08b1
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59313664"
---
# <a name="create-resource-files-for-net-apps"></a>.NET uygulamaları için kaynak dosyaları oluşturma

Uygulamanızda kolayca kullanılabilir hale getirmek için dizeler, görüntüler ve nesneler verileri gibi kaynaklarını ekleyebilirsiniz. .NET Framework, kaynak dosyaları oluşturmak için beş yol sunar:

- Dize kaynaklarını içeren bir metin dosyası oluşturun. Kullanabileceğiniz [kaynak dosya oluşturucu (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) metin dosyasını ikili kaynak (.resources) dosyasına dönüştürülecek. Ardından ikili kaynak dosyasını çalıştırılabilir bir uygulamaya veya bir uygulama kütüphanesine dil derleyicisini kullanarak, veya kullanarak, bir uydu derlemesine gömebilirsiniz [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md). Daha fazla bilgi için [metin dosyalarında kaynaklar](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#TextFiles) bölümü.

- Dize, resim veya nesne verilerini içeren bir XML kaynak (.resx) dosyası oluşturun. Kullanabileceğiniz [kaynak dosya oluşturucu (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) .resx dosyasını bir ikili kaynak (.resources) dosyasına dönüştürülecek. Ardından ikili kaynak dosyasını çalıştırılabilir bir uygulamaya veya bir uygulama kütüphanesine dil derleyicisini kullanarak, veya kullanarak, bir uydu derlemesine gömebilirsiniz [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md). Daha fazla bilgi için [.resx dosyalarındaki kaynaklar](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#ResxFiles) bölümü.

- <xref:System.Resources> ad alanındaki türleri kullanarak program aracılığıyla bir XML kaynak (.resx) dosyası oluşturun . Bir .resx dosyası oluşturabilir, kaynaklarını numaralandırabilir veya belirli kaynaklarını ada göre alabilirsiniz. Daha fazla bilgi için Ek Yardım konusuna [ile .resx dosyalarını program aracılığıyla çalışma](../../../docs/framework/resources/working-with-resx-files-programmatically.md).

- Program aracılığıyla ikili bir kaynak (.resources) dosyası oluşturun. Ardından dosyayı çalıştırılabilir bir uygulamaya veya bir uygulama kütüphanesine dil derleyicisini kullanarak, veya kullanarak, bir uydu derlemesine gömebilirsiniz [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md). Daha fazla bilgi için [.resources dosyalarındaki kaynaklar](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#ResourcesFiles) bölümü.

- Kullanım [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) kaynak dosyası oluşturma ve projenize dahil. Visual Studio, kaynakları eklemenizi, silmenizi ve değiştirmenizi sağlayan bir kaynak düzenleyicisi sağlar. Derleme sırasında, kaynak dosyası otomatik olarak ikili bir .resources dosyasına dönüştürülür ve bir uygulama derlemesine veya uydu derlemesine gömülür. Daha fazla bilgi için [Visual Studio'daki kaynak dosyaları](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#VSResFiles) bölümü.

<a name="TextFiles"></a>
## <a name="resources-in-text-files"></a>Metin dosyalarında kaynaklar

Metin (.txt veya .restext) dosyaları yalnızca dize kaynakları depolamak için kullanabilirsiniz. Dize olmayan kaynaklar için .resx dosyalarını kullanın veya program aracılığıyla oluşturma. Dize kaynaklarını içeren metin dosyaları aşağıdaki biçime sahiptir:

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

 Dize kaynakları görünür olarak *ad/değer* çiftleri burada *adı* kaynağı tanımlayan bir dizedir ve *değer* geçirdiğinizde döndürülen kaynak dizesi *adı* gibi bir kaynak alma yöntemine <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>. *adı* ve *değer* bir eşittir işareti (=) ile ayrılmalıdır. Örneğin:

```text
FileMenuName=File
EditMenuName=Edit
ViewMenuName=View
HelpMenuName=Help
```

> [!CAUTION]
> Şifreleri, güvenlik açısından duyarlı bilgileri veya özel verileri depolamak için kaynak dosyalarını kullanmayın.

 Boş dizelere (yani değeri <xref:System.String.Empty?displayProperty=nameWithType> olan bir kaynak) metin dosyalarında izin verilir. Örneğin:

```
EmptyString=
```

 Tüm .NET Core sürümlerinde .NET Framework 4.5 ile başlayarak, metin dosyaları ile koşullu derleme desteği `#ifdef` *sembol*... `#endif` ve `#if !` *sembol*... `#endif` oluşturur. Ardından `/define` anahtarı ile [kaynak dosya oluşturucu (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) sembollerini tanımlamak için. Her kaynak kendi gerektiriyor `#ifdef` *sembol*... `#endif` veya `#if !` *sembol*... `#endif` oluşturun. Kullanıyorsanız bir `#ifdef` deyimi ve *sembol* olan tanımlanan, ilişkili kaynak .resources dosyasına dahil edilir; Aksi takdirde dahil edilmez. Kullanıyorsanız bir `#if !` deyimi ve *sembol* olduğu tanımlı değilse, ilişkili kaynak .resources dosyasına dahil edilir; Aksi takdirde dahil edilmez.

 Yorumlar metin dosyalarında isteğe bağlıdır ve satır başında noktalı virgül (;) veya diyez işareti (#) ile başlanır. Yorumları içeren satırlar dosyanın herhangi bir yerine yerleştirilebilir. Yorum içinde yer almaz kullanılarak oluşturulan derlenmiş bir .resources dosyasına [kaynak dosya oluşturucu (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md).

 Metin dosyasındaki tüm boş satırlar beyaz boşluk olarak değerlendirilir ve göz ardı edilir.

 Aşağıdaki örnek `OKButton` ve `CancelButton` adındaki iki dize kaynağını tanımlar.

```text
#Define resources for buttons in the user interface.
OKButton=OK
CancelButton=Cancel
```

 Metin dosyası öğesinin yinelenen oluşumları varsa *adı*, [kaynak dosya oluşturucu (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) bir uyarı görüntüler ve ikinci adı göz ardı eder.

 *değer* yeni satır karakterlerini içeremez gibi C dili stili kaçış karakterlerini kullanabilirsiniz, ancak `\n` yeni satırı temsil eden ve `\t` bir sekmeyi temsil etmek için. Ayrıca eğer bu kaçırılmışsa bir ters eğik çizgi karakteri ekleyebilirsiniz (örneğin, "\\\\"). Ayrıca, boş bir dizeye izin verilir.

 Küçük endian veya büyük endian sırasıyla UTF-8 veya UTF-16 kodlamasını kullanarak kaynakları bir metin dosyasına kaydetmeniz gerekir. Ancak, [kaynak dosya oluşturucu (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md), bir .txt dosyasını bir .resources dosyasına dönüştüren dosyaları varsayılan olarak UTF-8 değerlendirir. Resgen.exe'nin, UTF-16 kullanılarak kodlanmış bir dosyayı tanımasını istiyorsanız, dosyanın başına bir Unicode bayt sırası işareti (U+FEFF) eklemeniz gerekir.

 Bir kaynak dosyası metin biçiminde bir .NET derlemesi halinde eklemek için dosyayı ikili kaynak (.resources) dosyasına dönüştürmeniz gerekir [kaynak dosya oluşturucu (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md). .Resources dosyasını bir dil derleyicisi kullanarak bir .NET derlemesine ekleme veya kullanarak bir uydu derlemesine gömmek [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md).

 Aşağıdaki örnek, basit bir "Hello World" konsol uygulaması için GreetingResources.txt adındaki metin biçimindeki bir kaynak dosyayı kullanır. Metin dosyası, kullanıcıdan adını girmesini isteyen ve bir karşılama görüntüleyen `prompt` ve `greeting` dizelerini tanımlar.

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
## <a name="resources-in-resx-files"></a>.Resx dosyalarındaki kaynaklar
 Yalnızca dize kaynaklarını depolayabilen metin dosyalarından farklı olarak XML kaynak (.resx) dosyaları; dizeleri, resimler, simgeler ve ses klipleri gibi ikili verileri ve programatik nesneleri depolayabilir. Bir .resx dosyası, kaynak girdilerinin biçimini açıklayan ve verileri ayrıştırmak için kullanılan XML'ye ait sürüm oluşturma bilgilerini belirten standart bir başlık içerir. Kaynak dosya verisi XML başlığını izler. Her bir veri öğesi, bir `data` etiketi içinde bulunan bir isim/değer ikilisinden oluşur. Kendi `name` özniteliği kaynak adını tanımlar ve iç içe `value` etiketi kaynak değerini içerir. Dize verisi için, `value` etiketi dizeyi içerir.

 Örneğin aşağıdaki `data` etiketi, değeri "Adınızı girin:" olan `prompt` adındaki bir dize kaynağını tanımlar.

```xml
<data name="prompt" xml:space="preserve">
  <value>Enter your name:</value>
</data>
```

> [!WARNING]
> Şifreleri, güvenlik açısından duyarlı bilgileri veya özel verileri depolamak için kaynak dosyalarını kullanmayın.

 Kaynak nesneleri **veri** etiket içeren bir `type` kaynağın veri türünü gösteren özniteliği. İkili verilerden oluşan nesneler için `data` etiketi, aynı zamanda ikili verilerin `mimetype` türünü gösteren bir `base64` özniteliğini içerir.

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
> .resx dosyaları, önceden tanımlanmış formatta doğru biçimlendirilmiş XML'lerden oluşması gerektiğinden özellikle .resx dosyaları dizeler haricinde kaynaklar içerdiğinde .resx dosyalarıyla el ile çalışılmasını önermeyiz. Bunun yerine, [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) oluşturmak ve .resx dosyalarını işlemek için saydam bir arabirim sağlar. Daha fazla bilgi için [Visual Studio'daki kaynak dosyaları](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#VSResFiles) bölümü. .resx dosyalarını aynı zamanda program aracılığıyla oluşturabilir ve değiştirebilirsiniz. Daha fazla bilgi için [ile .resx dosyalarını program aracılığıyla çalışma](../../../docs/framework/resources/working-with-resx-files-programmatically.md).

<a name="ResourcesFiles"></a>
## <a name="resources-in-resources-files"></a>.Resources dosyalarındaki kaynaklar

İkili bir kaynak (.resources) dosyasını program aracılığıyla doğrudan koddan oluşturmak için <xref:System.Resources.ResourceWriter?displayProperty=nameWithType> sınıfını kullanabilirsiniz. Ayrıca [kaynak dosya oluşturucu (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) bir metin dosyası veya bir .resx dosyasını bir .resources dosyası oluşturmak için. .resources dosyası, dize verilerine ek olarak ikili verileri (bayt dizileri) ve nesne verilerini içerebilir. Bir .resources dosyasının program aracılığıyla oluşturulması aşağıdaki adımları gerektirir:

1. Benzersiz bir dosya adı ile bir <xref:System.Resources.ResourceWriter> nesnesi oluşturun. Bunu, bir <xref:System.Resources.ResourceWriter> sınıf yapıcısına bir dosya adı veya bir dosya akışı belirterek gerçekleştirebilirsiniz.

2. Dosyaya eklemek için, adlandırılmış her bir kaynağa ait <xref:System.Resources.ResourceWriter.AddResource%2A?displayProperty=nameWithType> yönteminin aşırı yüklemelerinden birini çağırın. Kaynak bir dize, bir nesne veya bir ikili veri koleksiyonu (bir bayt dizisi) olabilir.

3. Kaynakları dosyaya yazmak ve <xref:System.Resources.ResourceWriter.Close%2A?displayProperty=nameWithType> nesnesini kapatmak için <xref:System.Resources.ResourceWriter> yöntemini çağırın.

> [!NOTE]
> Şifreleri, güvenlik açısından duyarlı bilgileri veya özel verileri depolamak için kaynak dosyalarını kullanmayın.

 Aşağıdaki örnek, altı dizeyi, bir simgeyi ve uygulama tanımlı iki nesneyi (iki `Automobile` nesnesi) depolayan CarResources.resources adındaki bir .resources dosyasını progam aracılığıyla oluşturur. Örnekte tanımlanan ve örneklenen `Automobile` sınıfının, ikili serileştirme biçimlendirici ile kalıcı olmasını sağlayan <xref:System.SerializableAttribute> özniteliği ile etiketlendiğini unutmayın.

 [!code-csharp[Conceptual.Resources.Resources#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resources/cs/resources1.cs#1)]
 [!code-vb[Conceptual.Resources.Resources#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resources/vb/resources1.vb#1)]

 .resources dosyasını oluşturduktan sonra bunu bir çalışma zamanı yürütülebilir veya kitaplık dil derleyicisinin katıştırabilirsiniz `/resource` geçin veya kullanarak bir uydu derlemesine gömmek [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md).

<a name="VSResFiles"></a>
## <a name="resource-files-in-visual-studio"></a>Visual Studio'daki kaynak dosyaları

Bir kaynak dosyasına eklediğinizde, [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) proje, Visual Studio proje dizininde bir .resx dosyası oluşturur. Visual Studio, dizeler, görüntüler ve ikili nesneleri eklemenizi sağlayan kaynak düzenleyicileri sağlar. Düzenleyiciler yalnızca statik verileri işlemek için tasarlandığından programatik nesneleri depolamak için kullanılamazlar; nesne verilerini bir .resx dosyasına veya bir .resources dosyasına program aracılığıyla yazmanız gerekir. Daha fazla bilgi için [ile .resx dosyalarını program aracılığıyla çalışma](../../../docs/framework/resources/working-with-resx-files-programmatically.md) ve [.resources dosyalarındaki kaynaklar](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md#ResourcesFiles) bölümü.

Yerelleştirilmiş kaynaklar ekliyorsanız, bunları ana kaynak dosyasıyla aynı kök dosya adı verin. Ayrıca, dosya adında kültürünü de belirlemeniz gerekir. Örneğin, Resources.resx adında bir kaynak dosyası eklerseniz, sırasıyla İngilizce (Amerika Birleşik Devletleri) ve Fransızca (Fransa) kültürleri için yerelleştirilmiş kaynakları tutmak amacıyla aynı zamanda Resources.en-US.resx ve Resources.fr-FR.resx adlı kaynak dosyaları oluşturabilirsiniz. Ayrıca uygulamanın varsayılan kültürünü de belirlemeniz gerekir. Bu, kaynakları belirli bir kültüre ait yerelleştirilmiş kaynaklar bulunamadığında kullanılan kültürdür. Varsayılan kültürün Visual Studio'daki Çözüm Gezgini'nde proje adına sağ tıklayın belirtmek için uygulama seçeneğine gidin, **derleme bilgileri**, uygun dili/kültürü seçin **nötr Dil** listesi.

Derleme zamanında, Visual Studio öncelikle bir projedeki .resx dosyalarını ikili kaynak (.resources) dosyalarına dönüştürür ve bunları projeye ait bir alt dizinde depolar *obj* dizin. Visual Studio, proje tarafından oluşturulmuş ana derlemede yerelleştirilmiş kaynaklar içermeyen tüm kaynak dosyalarını gömer. Eğer herhangi bir kaynak dosyası yerelleştirilmiş kaynakları içeriyorsa Visual Studio her bir yerelleştirilmiş için bu kaynakları ayrı uydu derlemelerine gömer. Ardından, adı yerelleştirilmiş kültüre karşılık gelen bir dizinde her bir uydu derlemesini depolar. Örneğin, yerelleştirilmiş İngilizce (Amerika Birleşik Devletleri) kaynakları, en-US alt dizinindeki bir uydu derlemesinde depolanır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Resources>
- [Masaüstü Uygulamalarındaki Kaynaklar](../../../docs/framework/resources/index.md)
- [Paketleme ve Dağıtma Kaynakları](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)
