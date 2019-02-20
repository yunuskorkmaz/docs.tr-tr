---
title: Program Aracılığıyla .resx Dosyalarıyla Çalışma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- resource files, .resx files
- .resx files
ms.assetid: 168f941a-2b84-43f8-933f-cf4a8548d824
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cddb7985c8763e5c18ecca0255f4f3556e03719e
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2019
ms.locfileid: "56441456"
---
# <a name="working-with-resx-files-programmatically"></a>Program aracılığıyla .resx dosyalarıyla çalışma
Ad/değer çiftleri verilerinde ardından belirli bir şemaya izlemeniz gereken bir üst bilgisi dahil olmak üzere, iyi tanımlanmış bir XML XML kaynak (.resx) dosyaları oluşması gerektiğinden bu dosyaları el ile oluşturmak hataya olduğunu fark edebilirsiniz. Alternatif olarak, .resx dosyalarını program aracılığıyla .NET sınıf kitaplığı'nda türleri ve üyeleri'ı kullanarak oluşturabilirsiniz. .NET sınıf kitaplığı, .resx dosyaları içinde depolanan kaynakları almak için de kullanabilirsiniz. Bu konu, türlerine ve üyelerine nasıl kullanabileceğinizi açıklar <xref:System.Resources> .resx dosyalarıyla çalışmak için ad alanı.

 Bu makalede, kaynakları içeren dosyaları XML (.resx) ile çalışma anlatılmaktadır unutmayın. Derlemelerde katıştırılmış ikili kaynak dosyaları ile çalışma hakkında daha fazla bilgi için bkz. <xref:System.Resources.ResourceManager> konu.

> [!WARNING]
> Program aracılığıyla .resx dosyalarıyla dışında çalışmak için yol vardır. Bir kaynak dosyasına eklediğinizde, bir [Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) Visual Studio projesi oluşturmak ve bir .resx dosyası sürdürmek için bir arabirim sağlar ve .resx dosyasını bir .resources dosyası için derleme zamanında otomatik olarak dönüştürür. Bir metin düzenleyicisi, bir .resx dosyasını doğrudan yönetmek için de kullanabilirsiniz. Ancak, dosyası bozulmasını önlemek için dosyasında depolanan herhangi bir ikili bilgiyi değiştirmemek dikkatli olun.

## <a name="create-a-resx-file"></a>Bir .resx dosyası oluşturma

Kullanabileceğiniz <xref:System.Resources.ResXResourceWriter?displayProperty=nameWithType> aşağıdaki adımları izleyerek bir .resx dosyası programlı olarak oluşturmak için sınıf:

1.  Örneği bir <xref:System.Resources.ResXResourceWriter> çağırarak <xref:System.Resources.ResXResourceWriter.%23ctor%28System.String%29?displayProperty=nameWithType> yöntemi ve .resx dosyasının adını belirtin. Dosya adı v .resx uzantısını içermesi gerekir. Örneği, <xref:System.Resources.ResXResourceWriter> nesnesine bir `using` bloğu açıkça çağırmak gerekmez <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> adım 3'teki yöntemi.

2.  Çağrı <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> dosyasına eklemek istediğiniz her bir kaynak için yöntemi. Dize nesnesi ve ikili (bayt dizesi) veri eklemek için bu yöntem aşırı yüklemelerini kullanın. Kaynak bir nesne ise, seri hale getirilebilir olması gerekir.

3.  Çağrı <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> kaynak dosyası oluşturmak ve tüm kaynakları serbest bırakmak için yöntemi. Varsa <xref:System.Resources.ResXResourceWriter> nesne içinde oluşturulmuş bir `using` blok, kaynaklar için .resx dosyasını ve tarafından kullanılan kaynakları yazılır <xref:System.Resources.ResXResourceWriter> nesne sonunda serbest `using` blok.

Uygun bir başlık elde edilen .resx dosyası varsa ve bir `data` etiketi tarafından eklenen her bir kaynak <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> yöntemi.

> [!WARNING]
> Şifreleri, güvenlik açısından duyarlı bilgileri veya özel verileri depolamak için kaynak dosyalarını kullanmayın.

Aşağıdaki örnek, altı dizeyi, simge ve iki uygulama tanımlı nesneler depolar CarResources.resx adlı bir .resx dosyası oluşturur (iki `Automobile` nesneleri). Unutmayın `Automobile` tanımlanır ve örnekte örneği, sınıfı ile etiketlendiğini <xref:System.SerializableAttribute> özniteliği.

[!code-csharp[Conceptual.Resources.ResX#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resx/cs/create1.cs#1)]
[!code-vb[Conceptual.Resources.ResX#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resx/vb/create1.vb#1)]

> [!TIP]
> Ayrıca [Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) .resx dosyalarını oluşturmak için. Derleme zamanında Visual Studio kullanan [kaynak dosya oluşturucu (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) .resx dosyasını ikili bir kaynak (.resources) dönüştürmek için dosya ve ayrıca bir uygulama derlemesine veya uydu derlemesine katıştırır.

Bir çalışma zamanı içinde yürütülebilir bir .resx dosyası ekleme veya bir uydu derlemeye derlemek olamaz. .Resx dosyanızı kullanarak ikili kaynak (.resources) dosyasına dönüştürmeniz gerekir [kaynak dosya oluşturucu (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md). Sonuçta elde edilen .resources dosyasını bir uygulama derlemesine veya uydu derlemesine eklenebilir. Daha fazla bilgi için [Creating Resource Files](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md).

## <a name="enumerate-resources"></a>Kaynakları listeleme
 Bazı durumlarda, belirli bir kaynak yerine tüm kaynakların bir .resx dosyasından almak isteyebilirsiniz. Bunu yapmak için kullanabileceğiniz <xref:System.Resources.ResXResourceReader?displayProperty=nameWithType> .resx dosyası içinde tüm kaynaklar için bir numaralandırıcı sağlar sınıfını. <xref:System.Resources.ResXResourceReader?displayProperty=nameWithType> Sınıfının Implements <xref:System.Collections.IDictionaryEnumerator>, döndüren bir <xref:System.Collections.DictionaryEntry> döngünün her yinelemesinden belirli bir kaynağı temsil eden nesne. Kendi <xref:System.Collections.DictionaryEntry.Key%2A?displayProperty=nameWithType> özelliği kaynağın anahtarı döndürür ve kendi <xref:System.Collections.DictionaryEntry.Value%2A?displayProperty=nameWithType> özelliği kaynağın değeri döndürür.

 Aşağıdaki örnek, oluşturur bir <xref:System.Resources.ResXResourceReader> nesne için önceki örnekte oluşturulan CarResources.resx dosyasını ve kaynak dosyası aracılığıyla yinelenir. İki ekler `Automobile` kaynak dosyasında tanımlanan nesneleri bir <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> nesne ve ekler için altı dizeyi beş bir <xref:System.Collections.SortedList> nesne. Değerler <xref:System.Collections.SortedList> nesne konsola sütun başlıklarını görüntülemek için kullanılan bir parametre dizisine dönüştürülür. `Automobile` Özellik değerleri de konsolda görüntülenir.

 [!code-csharp[Conceptual.Resources.ResX#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resx/cs/enumerate1.cs#2)]
 [!code-vb[Conceptual.Resources.ResX#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resx/vb/enumerate1.vb#2)]

## <a name="retrieve-a-specific-resource"></a>Belirli bir kaynak alma
 Bir .resx dosyası öğeleri numaralandırma ek olarak, belirli bir kaynak adına göre kullanarak alabileceğiniz <xref:System.Resources.ResXResourceSet?displayProperty=nameWithType> sınıfı. <xref:System.Resources.ResourceSet.GetString%28System.String%29?displayProperty=nameWithType> Yöntemi bir adlandırılmış dize kaynağı değerini alır. <xref:System.Resources.ResourceSet.GetObject%28System.String%29?displayProperty=nameWithType> Yöntemi adlandırılmış nesnesi ve ikili verileri değerini alır. Yöntemi ardından dönüştürülmelidir bir nesne döndürür (içinde C#) veya uygun türde bir nesneye (Visual Basic'te) dönüştürülür.

 Aşağıdaki örnek, bir formun başlık dizesi ve simge kaynak adlarını alır. Ayrıca uygulama tanımlı alır `Automobile` nesneler önceki örnekte kullanılan ve bunları görüntüler bir <xref:System.Windows.Forms.DataGridView> denetimi.

 [!code-csharp[Conceptual.Resources.ResX#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resx/cs/retrieve1.cs#3)]
 [!code-vb[Conceptual.Resources.ResX#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resx/vb/retrieve1.vb#3)]

## <a name="convert-resx-files-to-binary-resources-files"></a>.Resx dosyalarını ikili .resources dosyalarına dönüştürür
 .Resx dosyaları, katıştırılmış ikili kaynak (.resources) dosyalarına dönüştürme önemli avantajları vardır. .Resx dosyalarını okuma ve uygulama geliştirme sırasında korumak kolay olsa da, bunlar tamamlanmış uygulamalarla nadiren bulunur. Bir uygulama ile dağıtılmışsa yürütülebilir uygulama dışında ayrı dosyalar ve eşlik eden kitaplıklarını mevcut. Buna karşılık, .resources dosyaları, yürütülebilir bir uygulama veya eşlik eden derlemelerini katıştırılır. Ayrıca, yerelleştirilmiş uygulamalar için .resx dosyalarını çalıştırma yerlerdeki sorumluluğunu Geliştirici geri dönüş kaynak işleme bağlı. Buna karşılık, gömülü .resources dosyaları içeren bir uydu derleme kümesi oluşturulduysa, ortak dil çalışma zamanı kaynak geri dönüş işlemini gerçekleştirir.

 Bir .resx dosyasını bir .resources dosyasına dönüştürmek için kullanmanız [kaynak dosya oluşturucu (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md), aşağıdaki temel sözdizimi vardır:

 **Resgen.exe** *.resxFilename*

 .Resx dosyasını bir .resources dosyası uzantısı olarak aynı kök dosya adı olan bir ikili kaynak dosyası sonucudur. Bu dosya daha sonra yürütülebilir bir dosya veya bir kitaplığa derleme zamanında derlenebilir. Visual Basic Derleyicisi kullanıyorsanız, bir uygulamanın yürütülebilir dosyasına bir .resources dosyası eklemek için aşağıdaki sözdizimini kullanın:

 **Vbc** *filename* **.vb-resource:** *.resourcesFilename*

 Kullanıyorsanız C#, söz dizimi aşağıdaki gibidir:

 **CSC** *filename* **.cs-resource:** *.resourcesFilename*

 .Resources dosyası ayrıca bir uydu derlemesine kullanarak eklenebilir [Assembly Linker (AL.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md), aşağıdaki temel sözdizimi vardır:

 **Al** *resourcesFilename* **-out:** *assemblyFilename*

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Dosyaları Oluşturma](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md)
- [Resgen.exe (Kaynak Dosya Oluşturucu)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)
- [Al.exe (Bütünleştirilmiş Kod Bağlayıcı)](../../../docs/framework/tools/al-exe-assembly-linker.md)
