---
title: Uygulama yerelleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- localization [WPF], applications
- LocBaml tool [WPF]
- applications [WPF], localizing
ms.assetid: 5001227e-9326-48a4-9dcd-ba1b89ee6653
ms.openlocfilehash: dc7d8f4f56b26fffbd883e1e1d6e420026e1f94f
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209688"
---
# <a name="how-to-localize-an-application"></a>Nasıl yapılır: bir uygulamayı yerelleştirme

Bu öğreticide, LocBaml aracı kullanılarak yerelleştirilmiş bir uygulamanın nasıl oluşturulacağı açıklanmaktadır.  
  
> [!NOTE]
> LocBaml aracı üretime yönelik olarak hazırlanmayan bir uygulama değildir. Bu, yerelleştirme API 'Lerinden bazılarını kullanan bir örnek olarak sunulur ve yerelleştirme aracını nasıl yazacağınızı gösterir.  
  
## <a name="overview"></a>Genel Bakış

Bu makale, bir uygulamayı yerelleştirme konusunda adım adım bir yaklaşım sağlar. İlk olarak, çevrilecek metnin ayıklanabilmesi için uygulamanızı hazırlarsınız. Metin çevrildikten sonra, çevrilmiş metni orijinal uygulamanın yeni bir kopyasına birleştirirsiniz.
  
## <a name="create-a-sample-application"></a>Örnek uygulama oluşturma

Bu adımda, uygulamanızı yerelleştirme için hazırlarsınız. Windows Presentation Foundation (WPF) örneklerinde, bu tartışmadaki kod örnekleri için kullanılacak bir HelloApp örneği sağlanır. Bu örneği kullanmak isterseniz, [LocBaml araç örneğinden](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml)EXTENSIBLE APPLICATION MARKUP Language (XAML) dosyalarını indirin.  
  
1. Uygulamanızı yerelleştirmeye başlamak istediğiniz noktaya geliştirin.  
  
2. MSBuild 'in, bağımsız dil kaynaklarını içermesi için bir ana derleme ve uydu derlemesi (. resources. dll uzantılı bir dosya) oluşturması için proje dosyasında geliştirme dilini belirtin. HelloApp örneğindeki proje dosyası HelloApp. csproj ' dır. Bu dosyada, aşağıdaki şekilde tanımlanan geliştirme dilini bulacaksınız:  
  
   `<UICulture>en-US</UICulture>`  
  
3. XAML dosyalarınıza uid 'ler ekleyin. Uid 'ler, dosyalardaki değişiklikleri izlemek ve çevrilmesi gereken öğeleri belirlemek için kullanılır. Dosyalarınıza uid eklemek için, `updateuid` proje dosyanızda çalıştırın:  

   `msbuild -t:updateuid helloapp.csproj`

   Eksik veya yinelenen UID 'ler olmadığını doğrulamak için şunu çalıştırın `checkuid` :  

   `msbuild -t:checkuid helloapp.csproj`

   Çalıştırıldıktan sonra `updateuid` dosyalarınız uid 'leri içermelidir. Örneğin, HelloApp 'nin *Pane1. xaml* dosyasında aşağıdakileri bulmanız gerekir:  

   ```xaml
   <StackPanel x:Uid="StackPanel_1">
     <TextBlock x:Uid="TextBlock_1">Hello World</TextBlock>
     <TextBlock x:Uid="TextBlock_2">Goodbye World</TextBlock>
   </StackPanel>
   ```

## <a name="create-the-neutral-language-resources-satellite-assembly"></a>Nötr dil kaynakları uydu derlemesini oluşturma

Uygulama, Nötr dil kaynakları uydu derlemesi oluşturmak üzere yapılandırıldıktan sonra, uygulamayı derleyin. Bu, yerelleştirme için LocBaml 'in gerektirdiği bağımsız kaynak uydu derlemesini ve ana uygulama derlemesini de oluşturur.

Uygulamayı derlemek için:  
  
1. Dinamik bağlantı kitaplığı (DLL) oluşturmak için HelloApp 'yi derleyin:  
  
   `msbuild helloapp.csproj`
  
2. Yeni oluşturulan ana uygulama derlemesi HelloApp. exe, şu klasörde oluşturulur: *C:\helloapp\bin\debug*
  
3. Yeni oluşturulan Nötr dil kaynakları uydu derlemesi HelloApp. resources. dll şu klasörde oluşturulur: *C:\HelloApp\Bin\Debug\en-US*
  
## <a name="build-the-locbaml-tool"></a>LocBaml aracını oluşturma  
  
1. LocBaml oluşturmak için gereken tüm dosyalar WPF örneklerinde bulunur. [LocBaml araç örneğinden](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml)C# dosyalarını indirin.  
  
2. Araç oluşturmak için komut satırından proje dosyasını (LocBaml. csproj) çalıştırın:  

   `msbuild locbaml.csproj`
  
3. Yeni oluşturulan yürütülebilir dosyayı (LocBaml. exe) bulmak için *Bin\release* dizinine gidin. Örnek: *C:\LocBaml\Bin\Release\locbaml.exe*
  
4. LocBaml 'i çalıştırdığınızda belirtebileceğiniz seçenekler aşağıdaki gibidir.

   | Seçenek | Açıklama|
   | - | - |
   | `parse` veya `-p` | Bir. csv veya. txt dosyası oluşturmak için BAML, kaynaklar veya DLL dosyalarını ayrıştırır. |
   | `generate` veya `-g` | Çevrilmiş bir dosya kullanarak yerelleştirilmiş bir ikili dosya oluşturur. |
   | `out`veya `-o` {*FileDirectory*] | Çıkış dosyası adı. |
   | `culture`veya `-cul` {*Culture*] | Çıkış derlemelerinin yerel ayarı. |
   | `translation`veya `-trans` {*Translation. csv*] | Çevrilmiş veya yerelleştirilmiş dosya. |
   | `asmpath`veya `-asmpath` {*FileDirectory*] | XAML kodunuz özel denetimler içeriyorsa, öğesini `asmpath` özel denetim derlemesine sağlamanız gerekir. |
   | `nologo` | Logo veya telif hakkı bilgileri görüntüler. |
   | `verbose` | Ayrıntılı mod bilgilerini görüntüler. |
  
   > [!NOTE]
   > Aracı çalıştırırken seçeneklerin listesine ihtiyacınız varsa girin `LocBaml.exe` ve ardından **ENTER**tuşuna basın.
  
## <a name="use-locbaml-to-parse-a-file"></a>Bir dosyayı ayrıştırmak için LocBaml Kullanma

LocBaml aracını oluşturduğumuzda, bu uygulamayı, Yerelleştirilecek metin içeriğini ayıklamak için HelloApp. resources. dll ' i ayrıştırmak için kullanmaya hazırsınız.  
  
1. LocBaml. exe ' yi, ana uygulama derlemesinin oluşturulduğu uygulamanızın Bin\Debug klasörüne kopyalayın.  
  
2. Uydu derleme dosyasını ayrıştırmak ve çıktıyı bir. csv dosyası olarak depolamak için aşağıdaki komutu kullanın:  
  
   `LocBaml.exe /parse HelloApp.resources.dll /out:Hello.csv`
  
   > [!NOTE]
   > HelloApp. resources. dll giriş dosyası LocBaml. exe ile aynı dizinde değilse, her iki dosyanın de aynı dizinde olması için dosyalardan birini taşıyın.  
  
3. Dosyaları ayrıştırmak için LocBaml çalıştırdığınızda, çıktı virgüller (. csv dosyaları) veya sekmeler (. txt dosyaları) ile ayrılmış yedi alandan oluşur. Aşağıda, HelloApp. resources. dll için ayrıştırılmış. csv dosyası gösterilmektedir:

   | |
   |-|
   |HelloApp. g. en-US. resources: Window1. BAML, Stack1: System. Windows. Controls. StackPanel. $Content, Ignore, FALSE, FALSE,, #Text1; #Text2;|
   |HelloApp. g. en-US. resources: Window1. BAML, Metin1: System. Windows. Controls. TextBlock. $Content, None, TRUE, TRUE,, Merhaba Dünya|
   |HelloApp. g. en-US. resources: Window1. BAML, Metin2: System. Windows. Controls. TextBlock. $Content, None, TRUE, TRUE,, güle dünya|

   Yedi alan şunlardır:  
  
   - **BAML adı**. Kaynak dil uydu derlemesine göre BAML kaynağının adı.  
  
   - **Kaynak anahtarı**. Yerelleştirilmiş kaynak tanımlayıcısı.  
  
   - **Kategori**. Değer türü. Bkz. [Yerelleştirme öznitelikleri ve açıklamaları](localization-attributes-and-comments.md).  
  
   - **Okunabilirlik**. Değerin yerelleştirici tarafından okunup okunamayacağını belirtir. Bkz. [Yerelleştirme öznitelikleri ve açıklamaları](localization-attributes-and-comments.md).  
  
   - **Modifibeceri**. Değerin bir yerelleştirici tarafından değiştirilip değiştirilemediği. Bkz. [Yerelleştirme öznitelikleri ve açıklamaları](localization-attributes-and-comments.md).  
  
   - **Yorumlar**. Değerin nasıl yerelleştirileceğini belirlemede yardımcı olacak değerin ek açıklaması. Bkz. [Yerelleştirme öznitelikleri ve açıklamaları](localization-attributes-and-comments.md).  
  
   - **Değer**. İstenen kültüre çevrilecek metin değeri.  
  
   Aşağıdaki tabloda, bu alanların. csv dosyasının ayrılmış değerleriyle nasıl eşlenme gösterilmektedir:  
  
   |BAML adı|Kaynak anahtarı|Kategori|Okunabilirlik|Modifibilme|Açıklamalar|Değer|  
   |---------------|------------------|--------------|-----------------|-------------------|--------------|-----------|
   |HelloApp. g. en-US. resources: Window1. BAML|Stack1: System. Windows. Controls. StackPanel. $Content|Yoksayma|FALSE|FALSE||#Text1; #Text2|
   |HelloApp. g. en-US. resources: Window1. BAML|Metin1: System. Windows. Controls. TextBlock. $Content|Yok|TRUE|TRUE||Hello World|
   |HelloApp. g. en-US. resources: Window1. BAML|Metin2: System. Windows. Controls. TextBlock. $Content|Yok|TRUE|TRUE||Güle dünya|
  
   **Comments** alanı için tüm değerlerin değer içermediğini unutmayın; bir alanın değeri yoksa, boştur. Ayrıca, ilk satırdaki öğenin okunabilir ve değiştirilebilir olmadığından ve **Kategori** değeri olarak "Yoksay" değerine sahip olduğuna dikkat edin; hepsi değerin yerelleştirilemeyen olmadığını gösterir.  
  
4. Özellikle büyük dosyalarda, ayrıştırılmış dosyalardaki yerelleştirilebilir öğelerin bulunmasını kolaylaştırmak için öğeleri **kategoriye**, **okunabilirlik**ve **modifime**göre sıralayabilir veya filtreleyebilirsiniz. Örneğin, okunamaz ve değiştirilemeyen değerleri filtreleyebilirsiniz.  
  
## <a name="translate-the-localizable-content"></a>Yerelleştirilebilir içeriği çevir

Ayıklanan içeriği çevirmek için kullanabileceğiniz herhangi bir aracı kullanın. Bunu yapmanın iyi bir yolu, kaynakları bir. csv dosyasına yazmak ve bunları Microsoft Excel 'de görüntüleyerek, çeviri değişikliklerini son sütuna (değer) yapıyor.  
  
## <a name="use-locbaml-to-generate-a-new-resourcesdll-file"></a>Yeni bir. resources. dll dosyası oluşturmak için LocBaml kullanın

LocBaml ile HelloApp. resources. dll ayrıştırılmasından tanımlanan içerik çevrilmiş ve özgün uygulamayla yeniden birleştirilmelidir. `generate` `-g` Yeni bir. resources. dll dosyası oluşturmak için veya seçeneğini kullanın.  
  
1. Yeni bir HelloApp. resources. dll dosyası oluşturmak için aşağıdaki sözdizimini kullanın. Kültürü en-US (/CUL: en-US) olarak işaretleyin.  
  
   `LocBaml.exe /generate HelloApp.resources.dll /trans:Hello.csv /out:c:\ /cul:en-US`  

   > [!NOTE]
   > Hello. csv giriş dosyası yürütülebilir dosya, LocBaml. exe ile aynı dizinde değilse, her iki dosyanın de aynı dizinde olması için dosyalardan birini taşıyın.  
  
2. *C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll* dizinindeki eski *HelloApp. resources. dll* dosyasını yeni oluşturduğunuz *HelloApp. resources. dll* dosyası ile değiştirin.  
  
3. "Merhaba Dünya" ve "gücüde Dünya" Artık uygulamanıza çevrilmelidir.  
  
4. Farklı bir kültüre çevirmek için, çevirinizin bulunduğu dilin kültürünü kullanın. Aşağıdaki örnek, Fransızca-Kanada 'ya nasıl çevrileceğini gösterir:  
  
   `LocBaml.exe /generate HelloApp.resources.dll /trans:Hellofr-CA.csv /out:c:\ /cul:fr-CA`  
  
5. Ana uygulama derlemesiyle aynı derlemede, yeni uydu derlemesini barındırmak için kültüre özgü yeni bir klasör oluşturun. Fransızca-Kanada için klasör fr-CA olur.  
  
6. Oluşturulan uydu derlemesini yeni klasöre kopyalayın.  
  
7. Yeni uydu derlemesini test etmek için uygulamanızın çalıştırılacağı kültürü değiştirmeniz gerekir. Bunu iki yoldan biriyle yapabilirsiniz:  
  
   - İşletim sisteminizin bölgesel ayarlarını değiştirin.
  
   - Uygulamanızda, App.xaml.cs 'e aşağıdaki kodu ekleyin:  
  
     [!code-xaml[LocBamlChangeCultureSnippets#LocBamlChangeCultureMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml#locbamlchangeculturemarkup)]
     [!code-csharp[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml.cs#locbamlchangeculturecodebehind)]
     [!code-vb[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/VisualBasic/Application.xaml.vb#locbamlchangeculturecodebehind)]  
  
## <a name="tips-for-using-locbaml"></a>LocBaml kullanma ipuçları  
  
- Özel denetimleri tanımlayan tüm bağımlı derlemelerin LocBaml yerel dizinine kopyalanması veya GAC 'ye yüklenmesi gerekir. Bu gereklidir çünkü yerelleştirme API 'sinin, ikili XAML (BAML) okurken bağımlı derlemelere erişimi olması gerekir.  
  
- Ana derleme imzalanmışsa, oluşturulan kaynak DLL 'nin yüklenmesi için de imzalı olmalıdır.  
  
- Yerelleştirilmiş kaynak DLL sürümünün ana derlemeyle eşitlenmesi gerekir.
  
## <a name="see-also"></a>Ayrıca bkz.

- [WPF için Genelleştirme](globalization-for-wpf.md)
- [Otomatik Düzen Kullanımına Genel Bakış](use-automatic-layout-overview.md)
