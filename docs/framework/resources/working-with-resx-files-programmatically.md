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
ms.openlocfilehash: 3b84d77e4ac9b9889d1bc2f08e5ead6b81deecb0
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243043"
---
# <a name="work-with-resx-files-programmatically"></a>Program aracılığıyla .resx dosyalarıyla çalışma

XML kaynak (.resx) dosyaları, ad/değer çiftleri verileri tarafından izlenen belirli bir şema izlemesi gereken bir üstbilgi de dahil olmak üzere iyi tanımlanmış XML'den oluşması gerektiğinden, bu dosyaları el ile oluşturmanın hataya açık olduğunu görebilirsiniz. Alternatif olarak, .NET Sınıf Kitaplığı'ndaki türleri ve üyeleri kullanarak .resx dosyalarını programlı olarak oluşturabilirsiniz. .resx dosyalarında depolanan kaynakları almak için .NET Sınıf Kitaplığını da kullanabilirsiniz. Bu makalede, .resx dosyalarıyla <xref:System.Resources> çalışmak için ad alanındaki türleri ve üyeleri nasıl kullanabileceğiniz açıklanmaktadır.

Bu makalede, kaynakları içeren XML (.resx) dosyalarıyla çalışma açıklanır. Derlemelere katıştırılmış ikili kaynak dosyalarıyla çalışma <xref:System.Resources.ResourceManager>hakkında bilgi için bkz.

> [!WARNING]
> Programlı dışında .resx dosyalarıyla çalışmanın yolları da vardır. [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) projesine bir kaynak dosyası eklediğinizde, Visual Studio bir .resx dosyası oluşturmak ve korumak için bir arayüz sağlar ve .resx dosyasını derleme zamanında otomatik olarak bir .resources dosyasına dönüştürür. .resx dosyasını doğrudan işlemek için metin düzenleyicisi de kullanabilirsiniz. Ancak, dosyanın bozulmasını önlemek için, dosyada depolanan ikili bilgileri değiştirmemeye dikkat edin.

## <a name="create-a-resx-file"></a>.resx dosyası oluşturma

<xref:System.Resources.ResXResourceWriter?displayProperty=nameWithType> Sınıfı, aşağıdaki adımları izleyerek programlı bir şekilde bir .resx dosyası oluşturmak için kullanabilirsiniz:

1. Yöntemi arayarak <xref:System.Resources.ResXResourceWriter> ve .resx dosyasının adını vererek nesneyi anında belirtin. <xref:System.Resources.ResXResourceWriter.%23ctor%28System.String%29> Dosya adı .resx uzantısını içermelidir. Nesneyi <xref:System.Resources.ResXResourceWriter> bir `using` blokta anında atarsanız, <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> 3.

2. Dosyaya <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> eklemek istediğiniz her kaynak için yöntemi arayın. Dize, nesne ve ikili (bayt dizisi) verilerini eklemek için bu yöntemin aşırı yüklerini kullanın. Kaynak bir nesneyse, serileştirilebilir olmalıdır.

3. Kaynak <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> dosyasını oluşturmak ve tüm kaynakları serbest bırakmak için yöntemi arayın. Nesne <xref:System.Resources.ResXResourceWriter> bir `using` blok içinde oluşturulduysa, kaynaklar .resx dosyasına yazılır ve <xref:System.Resources.ResXResourceWriter> nesne tarafından kullanılan kaynaklar `using` bloğun sonunda serbest bırakılır.

Elde edilen .resx dosyası, yöntem tarafından `data` eklenen her kaynak <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> için uygun üstbilgi ve etikete sahiptir.

> [!WARNING]
> Şifreleri, güvenlik açısından duyarlı bilgileri veya özel verileri depolamak için kaynak dosyalarını kullanmayın.

Aşağıdaki örnek, altı dize, bir simge ve iki uygulama tanımlı nesne (iki `Automobile` nesne) depolayan CarResources.resx adlı bir .resx dosyası oluşturur. Örnekte tanımlanan ve anında verilen `Automobile` sınıf öznitelik ile <xref:System.SerializableAttribute> etiketlenir.

[!code-csharp[Conceptual.Resources.ResX#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resx/cs/create1.cs#1)]
[!code-vb[Conceptual.Resources.ResX#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resx/vb/create1.vb#1)]

> [!TIP]
> .resx dosyaları oluşturmak için [Visual Studio'yı](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) da kullanabilirsiniz. Derleme zamanında Visual Studio, .resx dosyasını ikili kaynak (.resources) dosyasına dönüştürmek için [Kaynak Dosya Üretecisini (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) kullanır ve ayrıca bir uygulama derlemesine veya uydu derlemesine katıştırır.

Bir .resx dosyayı çalıştırılabilir bir dosyaya katıştıramaz veya uydu derlemesine kopyalayamazsınız. .resx dosyanızı [Kaynak Dosya Üretecisini (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md)kullanarak ikili kaynak (.kaynaklar) dosyasına dönüştürmeniz gerekir. Ortaya çıkan .resources dosyası daha sonra bir uygulama derlemesine veya uydu derlemesine katışdırılabilir. Daha fazla bilgi için [kaynak dosyaları oluşturma'ya](creating-resource-files-for-desktop-apps.md)bakın.

## <a name="enumerate-resources"></a>Kaynakları sayısallandırma
 Bazı durumlarda, belirli bir kaynak yerine tüm kaynakları bir .resx dosyasından almak isteyebilirsiniz. Bunu yapmak için,.resx dosyasındaki <xref:System.Resources.ResXResourceReader?displayProperty=nameWithType> tüm kaynaklar için bir sayısallaştırıcı sağlayan sınıfı kullanabilirsiniz. Sınıf, <xref:System.Resources.ResXResourceReader?displayProperty=nameWithType> döngünün her <xref:System.Collections.DictionaryEntry> yinelemesi için belirli bir kaynağı temsil eden bir nesneyi döndürür. <xref:System.Collections.IDictionaryEnumerator> Özelliği <xref:System.Collections.DictionaryEntry.Key%2A?displayProperty=nameWithType> kaynağın anahtarını döndürür <xref:System.Collections.DictionaryEntry.Value%2A?displayProperty=nameWithType> ve özelliği kaynağın değerini döndürür.

 Aşağıdaki örnek, önceki <xref:System.Resources.ResXResourceReader> örnekte oluşturulan CarResources.resx dosyası için bir nesne oluşturur ve kaynak dosyası üzerinden yineler. Kaynak dosyasında `Automobile` tanımlanan iki nesneyi bir <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> nesneye ekler ve bir <xref:System.Collections.SortedList> nesneye altı dizeden beşini ekler. Nesnedeki <xref:System.Collections.SortedList> değerler, sütun başlıklarını konsola görüntülemek için kullanılan bir parametre dizisine dönüştürülür. Özellik `Automobile` değerleri de konsola görüntülenir.

 [!code-csharp[Conceptual.Resources.ResX#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resx/cs/enumerate1.cs#2)]
 [!code-vb[Conceptual.Resources.ResX#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resx/vb/enumerate1.vb#2)]

## <a name="retrieve-a-specific-resource"></a>Belirli bir kaynak alma
 .resx dosyasındaki öğeleri saymaya ek olarak, <xref:System.Resources.ResXResourceSet?displayProperty=nameWithType> sınıfı kullanarak belirli bir kaynağı ada göre ada göre alabilirsiniz. Yöntem, <xref:System.Resources.ResourceSet.GetString%28System.String%29?displayProperty=nameWithType> adlandırılmış bir dize kaynağının değerini alır. Yöntem, <xref:System.Resources.ResourceSet.GetObject%28System.String%29?displayProperty=nameWithType> adlandırılmış bir nesnenin veya ikili verilerin değerini alır. Yöntem, daha sonra (C#'da) veya (Visual Basic'te) uygun türdeki bir nesneye dönüştürülmesi gereken bir nesneyi döndürür.

 Aşağıdaki örnek, kaynak adlarına göre bir formun resim yazısı dizesini ve simgesini alır. Ayrıca, önceki örnekte `Automobile` kullanılan uygulama tanımlı nesneleri alır ve <xref:System.Windows.Forms.DataGridView> bunları bir denetimde görüntüler.

 [!code-csharp[Conceptual.Resources.ResX#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resx/cs/retrieve1.cs#3)]
 [!code-vb[Conceptual.Resources.ResX#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resx/vb/retrieve1.vb#3)]

## <a name="convert-resx-files-to-binary-resources-files"></a>.resx dosyalarını ikili .kaynaklar dosyalarına dönüştürme
 .resx dosyalarını katıştırılmış ikili kaynak (.resources) dosyalarına dönüştürmenin önemli avantajları vardır. .resx dosyalarının uygulama geliştirme sırasında okunması ve bakımı kolay olsa da, bunlar nadiren bitmiş uygulamalara dahil edilir. Bir uygulama yla dağıtılırsa, yürütülebilir uygulama ve beraberindeki kitaplıklar dışında ayrı dosyalar olarak bulunurlar. Buna karşılık, .resources dosyaları yürütülebilir veya eşlik eden derlemeleri uygulama gömülü. Buna ek olarak, yerelleştirilmiş uygulamalar için, çalışma zamanında .resx dosyalarına güvenmek, kaynak geri dönüşünü kullanma sorumluluğunu geliştiriciye yerleştirir. Buna karşılık, gömülü .kaynaklar dosyalarını içeren bir uydu derlemeleri kümesi oluşturulduysa, ortak dil çalışma süresi kaynak geri dönüş işlemini işler.

 .resx dosyasını .resources dosyasına dönüştürmek için, aşağıdaki temel sözdizimine sahip [Kaynak Dosya Üretecisini (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md)kullanırsınız:

 **Resgen.exe** *.resxFilename*

 Sonuç, .resx dosyası ve .resources dosya uzantısı ile aynı kök dosya adına sahip ikili kaynak dosyasıdır. Bu dosya daha sonra derlenebilir bir veya derleme zamanda kitaplık olarak derlenebilir. Visual Basic derleyicisini kullanıyorsanız, bir .resources dosyasını uygulamanın yürütülebilir dosyasına gömmek için aşağıdaki sözdizimini kullanın:

 **vbc** *filename* **.vb -kaynak:** *.resourcesFilename*

 C# kullanıyorsanız, sözdizimi aşağıdaki gibidir:

 **csc** *dosya adı* **.cs -kaynak:** *.resourcesFilename*

 .resources dosyası, aşağıdaki temel sözdizimine sahip [Olan Assembly Linker (AL.exe)](../tools/al-exe-assembly-linker.md)kullanılarak uydu derlemesine de eklenebilir:

 **al** *resourcesFilename* **-out:** *assemblyFilename*

## <a name="see-also"></a>Ayrıca bkz.

- [Kaynak Dosyaları Oluşturma](creating-resource-files-for-desktop-apps.md)
- [Resgen.exe (Kaynak Dosya Üreteci)](../tools/resgen-exe-resource-file-generator.md)
- [Al.exe (Montaj Linker)](../tools/al-exe-assembly-linker.md)
