---
title: "Program Aracılığıyla .resx Dosyalarıyla Çalışma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- resource files, .resx files
- .resx files
ms.assetid: 168f941a-2b84-43f8-933f-cf4a8548d824
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 46c00bc73e586c7bcfaca95d3998cbe100c6f3c7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="working-with-resx-files-programmatically"></a>Program Aracılığıyla .resx Dosyalarıyla Çalışma
XML kaynak (.resx) dosyaları, ad/değer çiftleri verilerde ve ardından belirli bir şema izlemeniz gereken bir üstbilgi dahil olmak üzere iyi tanımlanmış XML oluşması gerekir çünkü bu dosyaları el ile oluşturma hataya yatkın olduğunu fark edebilirsiniz. Alternatif olarak, .resx dosyaları programlı olarak .NET Framework Sınıf Kitaplığı'nda türleri ve üyeleri kullanarak oluşturabilirsiniz. .NET Framework sınıf kitaplığı, .resx dosyasında depolanan kaynakları almak için de kullanabilirsiniz. Bu konu türleri ve üyeleri nasıl kullanabileceğinizi açıklar <xref:System.Resources> .resx dosyalarıyla çalışmak için ad alanı.  
  
 Bu makalede, kaynakları içeren dosyaları XML (.resx) ile çalışma ele unutmayın. Derlemelerde katıştırılmış ikili kaynak dosyaları ile çalışma hakkında daha fazla bilgi için bkz: <xref:System.Resources.ResourceManager> konu.  
  
> [!WARNING]
>  Program aracılığıyla .resx dosyalarıyla dışında çalışmak için yolları da vardır. Visual Studio projesi için kaynak dosyası eklediğinizde, Visual Studio oluşturmak ve .resx dosyası sürdürmek için bir arabirim sağlar ve otomatik olarak .resx dosyası derleme zamanında bir .resources dosyasına dönüştürür. .Resx dosyası doğrudan işlemek için bir metin Düzenleyicisi'ni de kullanabilirsiniz. Ancak, dosya bozulmasını önlemek için dosyasında depolanan tüm ikili bilgileri değiştirmek dikkatli olun.  
  
## <a name="creating-a-resx-file"></a>.Resx dosyası oluşturma  
 Kullanabileceğiniz <xref:System.Resources.ResXResourceWriter?displayProperty=nameWithType> sınıfı .resx dosyası programlı olarak, aşağıdaki adımları izleyerek oluşturun:  
  
1.  Örneği bir <xref:System.Resources.ResXResourceWriter> çağırarak nesne <xref:System.Resources.ResXResourceWriter.%23ctor%28System.String%29?displayProperty=nameWithType> yöntemi ve .resx dosyasının adını belirtin. Dosya adı .resx uzantısını eklemeniz gerekir. Örneği varsa <xref:System.Resources.ResXResourceWriter> nesnesinde bir `using` bloğu açıkça çağırın gerekmez <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> adım 3'te yöntemi.  
  
2.  Çağrı <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> dosyasına eklemek istediğiniz her bir kaynak için yöntem. Dize, nesne ve ikili (bayt dizesi) veri eklemek için bu yöntem aşırı kullanın. Bir nesne kaynağıysa Serileştirilebilir olmalıdır.  
  
3.  Çağrı <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> kaynak dosyası oluşturun ve tüm kaynakları serbest bırakmak için yöntemi. Varsa <xref:System.Resources.ResXResourceWriter> nesne içinde oluşturulduğu bir `using` bloğu, kaynaklar, .resx dosya ve tarafından kullanılan kaynakları yazılır <xref:System.Resources.ResXResourceWriter> nesne sonunda serbest `using` bloğu.  
  
 Sonuçta elde edilen .resx dosyasını uygun üstbilgisi sahiptir ve `data` tarafından eklenen her kaynak için etiket <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> yöntemi.  
  
> [!WARNING]
>  Şifreleri, güvenlik açısından duyarlı bilgileri veya özel verileri depolamak için kaynak dosyalarını kullanmayın.  
  
 Aşağıdaki örnek, altı dizeler, bir simge ve iki uygulama tanımlı nesneler depolar CarResources.resx adlı .resx dosyası oluşturur (iki `Automobile` nesneleri). Unutmayın `Automobile` ile tanımlanan ve örnekte örneği, sınıf etiketli <xref:System.SerializableAttribute> özniteliği.  
  
 [!code-csharp[Conceptual.Resources.ResX#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resx/cs/create1.cs#1)]
 [!code-vb[Conceptual.Resources.ResX#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resx/vb/create1.vb#1)]  
  
> [!IMPORTANT]
>  Visual Studio, .resx dosyaları oluşturmak için de kullanabilirsiniz. Visual Studio derleme zamanında kullanan [kaynak dosya oluşturucu (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) .resx dosyası ikili kaynağa (.resources) dönüştürmek için dosya ve ayrıca uygulama bütünleştirilmiş veya bir uydu derleme katıştırır.  
  
 Bir çalışma zamanı yürütülebilir .resx dosyası ekleme veya uydu derleme içine derleyin. .Resx dosyanızı kullanarak bir ikili kaynak (.resources) dosyasına dönüştürmeniz gerekir [kaynak dosya oluşturucu (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md). Sonuçta elde edilen .resources dosyasını bir uygulama derlemeyi ya da bir uydu derleme katıştırılabilir. Daha fazla bilgi için bkz: [oluşturma kaynak dosyaları](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md).  
  
## <a name="enumerating-resources"></a>Kaynakları numaralandırma  
 Bazı durumlarda, belirli bir kaynak yerine tüm kaynakları .resx dosyasından almak isteyebilirsiniz. Bunu yapmak için kullanabileceğiniz <xref:System.Resources.ResXResourceReader?displayProperty=nameWithType> .resx dosyadaki tüm kaynaklar için bir numaralandırıcı sağlayan sınıf. <xref:System.Resources.ResXResourceReader?displayProperty=nameWithType> Uygulayan sınıf <xref:System.Collections.IDictionaryEnumerator>, döndüren bir <xref:System.Collections.DictionaryEntry> her döngü tekrarında belirli bir kaynağı temsil eden nesne. Kendi <xref:System.Collections.DictionaryEntry.Key%2A?displayProperty=nameWithType> özelliği kaynağın anahtar döndürür ve kendi <xref:System.Collections.DictionaryEntry.Value%2A?displayProperty=nameWithType> özelliği kaynağın değeri döndürür.  
  
 Aşağıdaki örnekte bir <xref:System.Resources.ResXResourceReader> nesnesi, önceki örnekte oluşturulan CarResources.resx dosyasını ve kaynak dosyası aracılığıyla yineler. İki ekler `Automobile` için kaynak dosyasında tanımlanan nesneleri bir <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> nesne ve onu ekler beş altı dizelere bir <xref:System.Collections.SortedList> nesnesi. Değerler <xref:System.Collections.SortedList> nesne konsola sütun başlıklarını görüntülemek için kullanılan bir parametre dizisine dönüştürülür. `Automobile` Özellik değerlerini de konsola görüntülenir.  
  
 [!code-csharp[Conceptual.Resources.ResX#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resx/cs/enumerate1.cs#2)]
 [!code-vb[Conceptual.Resources.ResX#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resx/vb/enumerate1.vb#2)]  
  
## <a name="retrieving-a-specific-resource"></a>Belirli bir kaynak alınıyor  
 .Resx dosyasındaki öğeler numaralandırma ek olarak, belirli bir kaynak adıyla kullanarak alabilirsiniz <xref:System.Resources.ResXResourceSet?displayProperty=nameWithType> sınıfı. <xref:System.Resources.ResourceSet.GetString%28System.String%29?displayProperty=nameWithType> Yöntemi bir adlandırılmış dize kaynağı değerini alır. <xref:System.Resources.ResourceSet.GetObject%28System.String%29?displayProperty=nameWithType> Yöntemi bir adlandırılmış nesneyi veya ikili veri değerini alır. Yöntemi, ardından atama (C# ') veya gerekir (Visual Basic'te) uygun türde bir nesnesine dönüştürülen bir nesne döndürür.  
  
 Aşağıdaki örnekte, kaynak adlarına göre bir formun başlık dizesi ve simge alır. Ayrıca uygulama tanımlı alır `Automobile` nesneleri önceki örnekte kullanılan ve bunları görüntüler bir <xref:System.Windows.Forms.DataGridView> denetim.  
  
 [!code-csharp[Conceptual.Resources.ResX#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resx/cs/retrieve1.cs#3)]
 [!code-vb[Conceptual.Resources.ResX#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resx/vb/retrieve1.vb#3)]  
  
## <a name="converting-resx-files-to-binary-resources-files"></a>İkili .resources dosyaları için dönüştürme .resx dosyaları  
 .Resx dosyaları katıştırılmış ikili kaynak (.resources) dosyalarını dönüştürme oldukça önemli avantajlara sahiptir. .Resx dosyaları okuma ve uygulama geliştirme sırasında korumak kolay olsa da, bunlar tamamlanmış uygulamalarla nadiren dahil edilir. Uygulama ile dağıtılmış, yürütülebilir uygulama dışında ayrı dosyaları ve eşlik eden başlatılamadığından olarak alır. Buna karşılık, .resources dosyaları yürütülebilir uygulama veya onun eşlik eden derlemeleri katıştırılır. Ayrıca, yerelleştirilmiş uygulamalar için .resx dosyaları çalışma zamanı yerlerdeki Geliştirici geri dönüş kaynak işleme sorumluluğunu güvenmek. Buna karşılık, katıştırılmış .resources dosyaları içeren uydu derlemelerini kümesi oluşturduysanız, ortak dil çalışma zamanı kaynak geri dönüş işlemini gerçekleştirir.  
  
 .Resx dosyası .resources dosyasına dönüştürmek için kullandığınız [kaynak dosya oluşturucu (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md), aşağıdaki temel sözdizimi vardır:  
  
 **Resgen.exe** *.resxFilename*  
  
 Kök dosya adıyla aynı .resx dosyası ve bir .resources dosya uzantısına sahip bir ikili kaynak dosya sonucudur. Bu dosya daha sonra bir yürütülebilir dosya veya bir kitaplığa derleme zamanında derlenebilir. Visual Basic derleyici kullanıyorsanız, uygulamanın yürütülebilir dosya .resources dosyası eklemek için aşağıdaki sözdizimini kullanın:  
  
 **Vbc** *filename* **.vb/Resource:** *.resourcesFilename*  
  
 C# kullanıyorsanız söz dizimi aşağıdaki gibidir:  
  
 **CSC** *filename* **.cs/Resource:** *.resourcesFilename*  
  
 .Resources dosyası da bir uydu derlemede kullanarak katıştırılabilen [derleme bağlayıcı (AL.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md), aşağıdaki temel sözdizimi vardır:  
  
 **Al** *resourcesFilename* **/out:** *assemblyFilename*  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak dosyalar oluşturma](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md)  
 [Resgen.exe (kaynak dosya oluşturucu)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)  
 [Al.exe (derleme bağlayıcı)](../../../docs/framework/tools/al-exe-assembly-linker.md)
