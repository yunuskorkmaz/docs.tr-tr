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
ms.openlocfilehash: 2bbca5712639e14370d090e95b78bb89eba134e4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129916"
---
# <a name="working-with-resx-files-programmatically"></a>Program aracılığıyla. resx dosyalarıyla çalışma
XML kaynak (. resx) dosyaları, belirli bir şemayı izlemelidir ve ardından ad/değer çiftlerinde bulunan veriler tarafından izlenen bir üst bilgi dahil olmak üzere iyi tanımlanmış XML 'den oluşmalıdır, bu dosyaların el ile oluşturulmasını hata ediyor olduğunu fark edebilirsiniz. Alternatif olarak, .NET sınıf kitaplığındaki türleri ve üyeleri kullanarak program aracılığıyla. resx dosyaları oluşturabilirsiniz. .NET sınıf kitaplığı ' nı. resx dosyalarında depolanan kaynakları almak için de kullanabilirsiniz. Bu konu,. resx dosyalarıyla çalışmak için <xref:System.Resources> ad alanındaki türleri ve üyeleri nasıl kullanabileceğinizi açıklar.

 Bu makalede, kaynakları içeren XML (. resx) dosyalarıyla çalışmayı ele alınmaktadır. Derlemelere eklenmiş ikili kaynak dosyalarıyla çalışma hakkında daha fazla bilgi için <xref:System.Resources.ResourceManager> konusuna bakın.

> [!WARNING]
> Program aracılığıyla. resx dosyalarıyla çalışmak için de çeşitli yollar vardır. [Visual](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) Studio projesine bir kaynak dosyası eklediğinizde, Visual Studio bir. resx dosyası oluşturmak ve sürdürmek için bir arabirim sağlar ve derleme zamanında. resx dosyasını otomatik olarak bir. resources dosyasına dönüştürür. Bir. resx dosyasını doğrudan işlemek için de bir metin düzenleyicisi kullanabilirsiniz. Ancak, dosyanın bozulmaması için dosyada depolanan tüm ikili bilgileri değiştirmemeye dikkat edin.

## <a name="create-a-resx-file"></a>. Resx dosyası oluşturma

Aşağıdaki adımları izleyerek bir. resx dosyası oluşturmak için <xref:System.Resources.ResXResourceWriter?displayProperty=nameWithType> sınıfını kullanabilirsiniz:

1. <xref:System.Resources.ResXResourceWriter.%23ctor%28System.String%29?displayProperty=nameWithType> yöntemini çağırarak ve. resx dosyasının adını sağlayarak bir <xref:System.Resources.ResXResourceWriter> nesnesi örneği oluşturun. Dosya adı. resx uzantısını içermelidir. <xref:System.Resources.ResXResourceWriter> nesnesini bir `using` bloğunda örneklediğinizde, adım 3 ' teki <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> yöntemini açıkça çağırmanız gerekmez.

2. Dosyaya eklemek istediğiniz her kaynak için <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> yöntemini çağırın. Dize, nesne ve ikili (bayt dizisi) verilerini eklemek için bu yöntemin aşırı yüklerini kullanın. Kaynak bir nesnedir, seri hale getirilebilir olmalıdır.

3. Kaynak dosyasını oluşturmak ve tüm kaynakları serbest bırakmak için <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> yöntemi çağırın. <xref:System.Resources.ResXResourceWriter> nesnesi `using` bir blok içinde oluşturulduysa, kaynaklar. resx dosyasına yazılır ve <xref:System.Resources.ResXResourceWriter> nesnesi tarafından kullanılan kaynaklar `using` bloğunun sonunda serbest bırakılır.

Elde edilen. resx dosyası, <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> yöntemi tarafından eklenen her kaynak için uygun başlığa ve bir `data` etiketine sahiptir.

> [!WARNING]
> Şifreleri, güvenlik açısından duyarlı bilgileri veya özel verileri depolamak için kaynak dosyalarını kullanmayın.

Aşağıdaki örnek, altı dizeyi, bir simgeyi ve uygulama tanımlı iki nesneyi (iki `Automobile` nesnesi) depolayan CarResources. resx adlı bir. resx dosyası oluşturur. Örnekte tanımlanan ve örneği oluşturulan `Automobile` sınıfının <xref:System.SerializableAttribute> özniteliğiyle etiketlendiği unutulmamalıdır.

[!code-csharp[Conceptual.Resources.ResX#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resx/cs/create1.cs#1)]
[!code-vb[Conceptual.Resources.ResX#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resx/vb/create1.vb#1)]

> [!TIP]
> Ayrıca,. resx dosyaları oluşturmak için [Visual Studio 'yu](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) kullanabilirsiniz. Derleme zamanında, Visual Studio,. resx dosyasını ikili bir kaynak (. resources) dosyasına dönüştürmek için [kaynak dosya Oluşturucu (Resgen. exe)](../tools/resgen-exe-resource-file-generator.md) kullanır ve ayrıca onu bir uygulama derlemesine ya da uydu derlemesine katıştırır.

Bir. resx dosyasını bir çalışma zamanı yürütülebilir dosyasına katıştıramaz veya bir uydu derlemesinde derlenemez. [Kaynak dosya Oluşturucu (Resgen. exe)](../tools/resgen-exe-resource-file-generator.md)kullanarak. resx dosyanızı ikili bir kaynak (. resources) dosyasına dönüştürmeniz gerekir. Elde edilen. resources dosyası daha sonra bir uygulama derlemesine veya bir uydu derlemesine gömülebilir. Daha fazla bilgi için bkz. [kaynak dosyaları oluşturma](creating-resource-files-for-desktop-apps.md).

## <a name="enumerate-resources"></a>Kaynakları listeleme
 Bazı durumlarda, belirli bir kaynak yerine, bir. resx dosyasından tüm kaynakları almak isteyebilirsiniz. Bunu yapmak için,. resx dosyasındaki tüm kaynaklar için bir Numaralandırıcı sağlayan <xref:System.Resources.ResXResourceReader?displayProperty=nameWithType> sınıfını kullanabilirsiniz. <xref:System.Resources.ResXResourceReader?displayProperty=nameWithType> sınıfı, döngünün her yinelemesi için belirli bir kaynağı temsil eden bir <xref:System.Collections.DictionaryEntry> nesnesi döndüren <xref:System.Collections.IDictionaryEnumerator>uygular. <xref:System.Collections.DictionaryEntry.Key%2A?displayProperty=nameWithType> özelliği, kaynağın anahtarını döndürür ve <xref:System.Collections.DictionaryEntry.Value%2A?displayProperty=nameWithType> özelliği kaynağın değerini döndürür.

 Aşağıdaki örnek, önceki örnekte oluşturulan CarResources. resx dosyası için bir <xref:System.Resources.ResXResourceReader> nesnesi oluşturur ve kaynak dosyasında yinelenir. Kaynak dosyasında tanımlanan iki `Automobile` nesnesini bir <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> nesnesine ekler ve bir <xref:System.Collections.SortedList> nesnesine altı dizeden beş tane ekler. <xref:System.Collections.SortedList> nesnesindeki değerler, konsola sütun başlıklarının gösterilmesi için kullanılan bir parametre dizisine dönüştürülür. `Automobile` özellik değerleri de konsola görüntülenir.

 [!code-csharp[Conceptual.Resources.ResX#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resx/cs/enumerate1.cs#2)]
 [!code-vb[Conceptual.Resources.ResX#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resx/vb/enumerate1.vb#2)]

## <a name="retrieve-a-specific-resource"></a>Belirli bir kaynağı alma
 Bir. resx dosyasındaki öğeleri listelemenin yanı sıra, <xref:System.Resources.ResXResourceSet?displayProperty=nameWithType> sınıfını kullanarak belirli bir kaynağı ada göre de alabilirsiniz. <xref:System.Resources.ResourceSet.GetString%28System.String%29?displayProperty=nameWithType> yöntemi, adlandırılmış bir dize kaynağının değerini alır. <xref:System.Resources.ResourceSet.GetObject%28System.String%29?displayProperty=nameWithType> yöntemi, adlandırılmış nesnenin veya ikili verilerin değerini alır. Yöntemi, uygun türdeki bir nesneye daha sonra C#(Visual Basic) veya dönüştürülmeli bir nesne döndürür.

 Aşağıdaki örnek, bir formun başlık dizesini ve simgesini kaynak adlarına göre alır. Ayrıca, önceki örnekte kullanılan uygulama tanımlı `Automobile` nesnelerini alır ve bir <xref:System.Windows.Forms.DataGridView> denetiminde görüntüler.

 [!code-csharp[Conceptual.Resources.ResX#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resx/cs/retrieve1.cs#3)]
 [!code-vb[Conceptual.Resources.ResX#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resx/vb/retrieve1.vb#3)]

## <a name="convert-resx-files-to-binary-resources-files"></a>. Resx dosyalarını ikili. resources dosyalarına Dönüştür
 . Resx dosyalarının gömülü ikili kaynak (. resources) dosyalarına dönüştürülmesi önemli avantajlara sahiptir. . Resx dosyalarının uygulama geliştirme sırasında okunması ve korunması kolay olsa da, tamamlanmış uygulamalara nadiren dahil edilmiştir. Bunlar bir uygulamayla dağıtılırsa, uygulama çalıştırılabiliri ve buna eşlik eden kütüphanelerin ayrı dosyaları olarak bulunur. Buna karşılık,. resources dosyaları uygulama yürütülebilir dosyasına veya buna eşlik eden derlemelere katıştırılır. Ayrıca, yerelleştirilmiş uygulamalar için, çalışma zamanında. resx dosyalarına bağlı olarak, geliştiriciye kaynak geri dönüşü işleme sorumluluğunu koyar. Buna karşılık, gömülü. resources dosyaları içeren bir uydu derlemeleri kümesi oluşturulduysa, ortak dil çalışma zamanı kaynak geri dönüş işlemini işler.

 Bir. resx dosyasını bir. resources dosyasına dönüştürmek için aşağıdaki temel sözdizimine sahip [kaynak dosya Oluşturucu (Resgen. exe)](../tools/resgen-exe-resource-file-generator.md)kullanılır:

 **Resgen. exe** *. resxfilename*

 Sonuç,. resx dosyası ve bir. resources dosya uzantısıyla aynı kök dosya adına sahip olan bir ikili kaynak dosyasıdır. Bu dosya daha sonra derleme zamanında bir yürütülebilir veya bir kitaplık olarak derlenebilir. Visual Basic derleyicisini kullanıyorsanız, bir uygulamanın yürütülebilir dosyasına bir. resources dosyasını eklemek için aşağıdaki sözdizimini kullanın:

 **vbc** *filename* **. vb-kaynak:** *. resourcesfilename*

 Kullanıyorsanız C#, söz dizimi aşağıdaki gibidir:

 **CSC** *dosya adı* **. cs-Resource:** *. resourcesfilename*

 . Resources dosyası, aşağıdaki temel sözdizimine sahip [derleme Bağlayıcısı (al. exe)](../tools/al-exe-assembly-linker.md)kullanılarak bir uydu derlemesine de katıştırılabilir:

 **Al** *resourcesfilename* **-Out:** *assemblyFileName*

## <a name="see-also"></a>Ayrıca bkz.

- [Kaynak Dosyaları Oluşturma](creating-resource-files-for-desktop-apps.md)
- [Resgen.exe (Kaynak Dosya Oluşturucu)](../tools/resgen-exe-resource-file-generator.md)
- [Al.exe (Bütünleştirilmiş Kod Bağlayıcı)](../tools/al-exe-assembly-linker.md)
