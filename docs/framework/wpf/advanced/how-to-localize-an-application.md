---
title: 'Nasıl yapılır: Bir Uygulamayı Yerelleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- localization [WPF], applications
- LocBaml tool [WPF]
- applications [WPF], localizing
ms.assetid: 5001227e-9326-48a4-9dcd-ba1b89ee6653
ms.openlocfilehash: 4d7271e792c96dd896d73a52a31ad136acc19e26
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666784"
---
# <a name="how-to-localize-an-application"></a>Nasıl yapılır: Bir Uygulamayı Yerelleştirme
Bu öğreticide, LocBaml aracı kullanılarak yerelleştirilmiş bir uygulamanın nasıl oluşturulacağı açıklanmaktadır.  
  
> [!NOTE]
>  LocBaml aracı üretime yönelik olarak hazırlanmayan bir uygulama değildir. Bu, yerelleştirme API 'Lerinden bazılarını kullanan bir örnek olarak sunulur ve yerelleştirme aracını nasıl yazacağınızı gösterir.  
  
<a name="Introduction"></a>   
## <a name="overview"></a>Genel Bakış  
 Bu tartışma, bir uygulamayı yerelleştirme konusunda adım adım bir yaklaşım sağlar. İlk olarak, çevrilecek metnin ayıklanabilmesi için uygulamanızı hazırlayacaksınız. Metin çevrildikten sonra, çevrilmiş metni orijinal uygulamanın yeni bir kopyasına birleştirirsiniz.  
  
<a name="Requirements"></a>   
## <a name="requirements"></a>Gereksinimler  
 Bu tartışma sırasında, komut satırından çalışan bir derleyici olan [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)]' i kullanacaksınız.  
  
 Ayrıca, bir proje dosyası kullanmanız istenir. Ve proje dosyalarının kullanımına [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] ilişkin yönergeler için bkz. [derleme ve dağıtma](../app-development/building-and-deploying-wpf-applications.md).  
  
 Bu tartışmadaki tüm örnekler kültür olarak en-US (Ingilizce-US) kullanır. Bu, farklı bir dil yüklemeden örneklerin adımlarında çalışabilmenizi sağlar.  
  
<a name="create_sample_app"></a>   
## <a name="create-a-sample-application"></a>Örnek uygulama oluşturma  
 Bu adımda, uygulamanızı yerelleştirme için hazırlayacaksınız. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Örneklerde, bu tartışmadaki kod örnekleri için kullanılacak bir HelloApp örneği sağlanır. Bu örneği kullanmak isterseniz, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] [LocBaml araç örneğinden](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml)dosyaları indirin.  
  
1. Uygulamanızı yerelleştirmeye başlamak istediğiniz noktaya geliştirin.  
  
2. Bağımsız dil kaynaklarını içermesi için bir ana derleme ve uydu [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] derlemesi (. resources. dll uzantılı bir dosya) oluşturacak şekilde proje dosyasında geliştirme dilini belirtin. HelloApp örneğindeki proje dosyası HelloApp. csproj ' dır. Bu dosyada, aşağıdaki şekilde tanımlanan geliştirme dilini bulacaksınız:  
  
     `<UICulture>en-US</UICulture>`  
  
3. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Dosyalarınıza uid 'ler ekleyin. Uid 'ler, dosyalardaki değişiklikleri izlemek ve çevrilmesi gereken öğeleri belirlemek için kullanılır. Dosyalarınıza uid eklemek için, proje dosyanızda **updateuid** komutunu çalıştırın:  
  
     **MSBuild-t:updateuid HelloApp. csproj**  
  
     Eksik veya yinelenen UID 'ler olmadığını doğrulamak için **checkuid**komutunu çalıştırın:  
  
     **MSBuild-t:checkuid HelloApp. csproj**  
  
     **Updateuid**çalıştırıldıktan sonra dosyalarınız uid 'leri içermelidir. Örneğin, HelloApp 'nin Pane1. xaml dosyasında aşağıdakileri bulmanız gerekir:  
  
     `<StackPanel x:Uid="StackPanel_1">`  
  
     `<TextBlock x:Uid="TextBlock_1">Hello World</TextBlock>`  
  
     `<TextBlock x:Uid="TextBlock_2">Goodbye World</TextBlock>`  
  
     `</StackPanel>`  
  
<a name="create_dll"></a>   
## <a name="create-the-neutral-language-resources-satellite-assembly"></a>Nötr dil kaynakları uydu derlemesini oluşturma  
 Uygulama, dilden bağımsız bir dil kaynakları uydu derlemesi oluşturmak üzere yapılandırıldıktan sonra, uygulamayı derleyin. Bu, ana uygulama derlemesini ve yerelleştirme için LocBaml 'in gerektirdiği Nötr dil kaynakları uydu derlemesini oluşturur. Uygulamayı derlemek için:  
  
1. Dinamik bağlantı kitaplığı (DLL) oluşturmak için HelloApp 'yi derleyin:  
  
     **MSBuild HelloApp. csproj**  
  
2. Yeni oluşturulan ana uygulama derlemesi HelloApp. exe, şu klasörde oluşturulur:  
  
     `C:\HelloApp\Bin\Debug\`  
  
3. Yeni oluşturulan Nötr dil kaynakları uydu derlemesi HelloApp. resources. dll aşağıdaki klasörde oluşturulur:  
  
     `C:\HelloApp\Bin\Debug\en-US\`  
  
<a name="build_locbaml"></a>   
## <a name="build-the-locbaml-tool"></a>LocBaml aracını oluşturma  
  
1. LocBaml oluşturmak için gereken tüm dosyalar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] örneklerde bulunur. C# Dosyaları [LocBaml araç örneğinden](https://go.microsoft.com/fwlink/?LinkID=160016)indirin.  
  
2. Araç oluşturmak için komut satırından proje dosyasını (LocBaml. csproj) çalıştırın:  
  
     **MSBuild LocBaml. csproj**  
  
3. Yeni oluşturulan yürütülebilir dosyayı (LocBaml. exe) bulmak için Bin\Release dizinine gidin. Örnek: C: \LocBaml\Bin\Release\locbaml.exe.  
  
4. LocBaml 'i çalıştırdığınızda belirtebileceğiniz seçenekler aşağıdaki gibidir:  
  
    - **Parse** veya **-p:** Bir. csv veya. txt dosyası oluşturmak için BAML, kaynaklar veya DLL dosyalarını ayrıştırır.  
  
    - **Oluştur** veya **-g:** Çevrilmiş bir dosya kullanarak yerelleştirilmiş bir ikili dosya oluşturur.  
  
    - **Out** veya **-o** {*FileDirectory*] **:** Çıkış dosyası adı.  
  
    - **kültür** veya **-Cul** {*kültür*] **:** Çıkış derlemelerinin yerel ayarı.  
  
    - **çeviri** veya **-Trans** {*Translation. csv*] **:** Çevrilmiş veya yerelleştirilmiş dosya.  
  
    - **asmpath** veya **-asmpath:** {*FileDirectory*] **:** Kodunuz özel denetimler içeriyorsa, özel denetim derlemesine asmpath sağlamanız gerekir. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]  
  
    - **nologo** Logo veya telif hakkı bilgileri görüntüler.  
  
    - **seçeneini** Ayrıntılı mod bilgilerini görüntüler.  
  
    > [!NOTE]
    >  Aracı çalıştırırken seçenekler listesine ihtiyacınız varsa **LocBaml. exe** YAZıN ve ENTER tuşuna basın.  
  
<a name="parse_dll"></a>   
## <a name="use-locbaml-to-parse-a-file"></a>Bir dosyayı ayrıştırmak için LocBaml Kullanma  
 LocBaml aracını oluşturduğumuzda, bu uygulamayı, Yerelleştirilecek metin içeriğini ayıklamak için HelloApp. resources. dll ' i ayrıştırmak için kullanmaya hazırsınız.  
  
1. LocBaml. exe ' yi, ana uygulama derlemesinin oluşturulduğu uygulamanızın Bin\Debug klasörüne kopyalayın.  
  
2. Uydu derleme dosyasını ayrıştırmak ve çıktıyı bir. csv dosyası olarak depolamak için aşağıdaki komutu kullanın:  
  
     **LocBaml. exe/Parse HelloApp. resources. dll/out: Merhaba. csv**  
  
    > [!NOTE]
    >  HelloApp. resources. dll giriş dosyası LocBaml. exe ile aynı dizinde değilse, her iki dosyanın de aynı dizinde olması için dosyalardan birini taşıyın.  
  
3. Dosyaları ayrıştırmak için LocBaml çalıştırdığınızda, çıktı virgüller (. csv dosyaları) veya sekmeler (. txt dosyaları) ile ayrılmış yedi alandan oluşur. Aşağıda, HelloApp. resources. dll için ayrıştırılmış. csv dosyası gösterilmektedir:

   | |
   |-|
   |HelloApp. g. en-US. resources: Window1. BAML, Stack1: System. Windows. Controls. StackPanel. $Content, Ignore, FALSE, FALSE,, #Text1; #Text2;|
   |HelloApp. g. en-US. resources: Window1. BAML, Metin1: System. Windows. Controls. TextBlock. $Content, None, TRUE, TRUE,, Merhaba Dünya|
   |HelloApp. g. en-US. resources: Window1. BAML, Metin2: System. Windows. Controls. TextBlock. $Content, None, TRUE, TRUE,, güle dünya|

   Yedi alan şunlardır:  
  
   1. **BAML adı**. Kaynak dil uydu derlemesine göre BAML kaynağının adı.  
  
   2. **Kaynak anahtarı**. Yerelleştirilmiş kaynak tanımlayıcısı.  
  
   3. **Kategori**. Değer türü. Bkz. [Yerelleştirme öznitelikleri ve açıklamaları](localization-attributes-and-comments.md).  
  
   4. **Okunabilirlik**. Değerin yerelleştirici tarafından okunup okunamayacağını belirtir. Bkz. [Yerelleştirme öznitelikleri ve açıklamaları](localization-attributes-and-comments.md).  
  
   5. **Modifibeceri**. Değerin bir yerelleştirici tarafından değiştirilip değiştirilemediği. Bkz. [Yerelleştirme öznitelikleri ve açıklamaları](localization-attributes-and-comments.md).  
  
   6. **Yorumlar**. Değerin nasıl yerelleştirileceğini belirlemede yardımcı olacak değerin ek açıklaması. Bkz. [Yerelleştirme öznitelikleri ve açıklamaları](localization-attributes-and-comments.md).  
  
   7. **Değer**. İstenen kültüre çevrilecek metin değeri.  
  
   Aşağıdaki tabloda, bu alanların. csv dosyasının ayrılmış değerleriyle nasıl eşlenme gösterilmektedir:  
  
   |BAML adı|Kaynak anahtarı|Kategori|Luğunu|Modifibilme|Açıklamalar|Değer|  
   |---------------|------------------|--------------|-----------------|-------------------|--------------|-----------|
   |HelloApp. g. en-US. resources: Window1. BAML|Stack1: System. Windows. Controls. StackPanel. $Content|Yoksayma|YANLÝÞ|YANLÝÞ||#Text1; #Text2|
   |HelloApp. g. en-US. resources: Window1. BAML|Metin1: System. Windows. Controls. TextBlock. $Content|Yok.|TRUE|TRUE||Merhaba Dünya|
   |HelloApp. g. en-US. resources: Window1. BAML|Metin2: System. Windows. Controls. TextBlock. $Content|Yok.|TRUE|TRUE||Güle dünya|
  
   **Comments** alanı için tüm değerlerin değer içermediğini unutmayın; bir alanın değeri yoksa, boştur. Ayrıca, ilk satırdaki öğenin okunabilir ve değiştirilebilir olmadığından ve **Kategori** değeri olarak "Yoksay" değerine sahip olduğuna dikkat edin; hepsi değerin yerelleştirilemeyen olmadığını gösterir.  
  
4. Özellikle büyük dosyalarda, ayrıştırılmış dosyalardaki yerelleştirilebilir öğelerin bulunmasını kolaylaştırmak için öğeleri **kategoriye**, **okunabilirlik**ve **modifime**göre sıralayabilir veya filtreleyebilirsiniz. Örneğin, okunamaz ve değiştirilemeyen değerleri filtreleyebilirsiniz.  
  
<a name="translate_loc_content"></a>   
## <a name="translate-the-localizable-content"></a>Yerelleştirilebilir Içeriği çevir  
 Ayıklanan içeriği çevirmek için kullanabileceğiniz herhangi bir aracı kullanın. Bunu yapmanın iyi bir yolu, kaynakları bir. csv dosyasına yazmak ve bunları içinde [!INCLUDE[TLA#tla_xl](../../../../includes/tlasharptla-xl-md.md)]görüntülemeniz, son sütunda (değer) çeviri değişiklikleri yapmak.  
  
<a name="merge_translations"></a>   
## <a name="use-locbaml-to-generate-a-new-resourcesdll-file"></a>Yeni bir. resources. dll dosyası oluşturmak için LocBaml kullanın  
 LocBaml ile HelloApp. resources. dll ayrıştırılmasından tanımlanan içerik çevrilmiş ve özgün uygulamayla yeniden birleştirilmelidir. Yeni bir. resources. dll dosyası oluşturmak için **Generate** veya **-g** seçeneğini kullanın.  
  
1. Yeni bir HelloApp. resources. dll dosyası oluşturmak için aşağıdaki sözdizimini kullanın. Kültürü en-US (/CUL: en-US) olarak işaretleyin.  
  
     **LocBaml. exe/Generate HelloApp. resources. dll/Trans: Hello. csv/Out: c:\/Cul: en-US**  
  
    > [!NOTE]
    >  Hello. csv giriş dosyası yürütülebilir dosya, LocBaml. exe ile aynı dizinde değilse, her iki dosyanın de aynı dizinde olması için dosyalardan birini taşıyın.  
  
2. C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll dizinindeki eski HelloApp. resources. dll dosyasını yeni oluşturduğunuz HelloApp. resources. dll dosyası ile değiştirin.  
  
3. "Merhaba Dünya" ve "gücüde Dünya" Artık uygulamanıza çevrilmelidir.  
  
4. Farklı bir kültüre çevirmek için, çevirinizin bulunduğu dilin kültürünü kullanın. Aşağıdaki örnek, Fransızca-Kanada 'ya nasıl çevrileceğini gösterir:  
  
     **LocBaml. exe/Generate HelloApp. resources. dll/Trans: Hellofr-CA. csv/Out: c:\/Cul: fr-CA**  
  
5. Ana uygulama derlemesiyle aynı derlemede, yeni uydu derlemesini barındırmak için kültüre özgü yeni bir klasör oluşturun. Fransızca-Kanada için klasör fr-CA olur.  
  
6. Oluşturulan uydu derlemesini yeni klasöre kopyalayın.  
  
7. Yeni uydu derlemesini test etmek için uygulamanızın çalıştırılacağı kültürü değiştirmeniz gerekir. Bunu iki yoldan biriyle yapabilirsiniz:  
  
    - İşletim sisteminizin bölgesel ayarlarını değiştirin ( **Denetim Masası** &#124; **bölge ve dil seçeneklerini** **Başlat** &#124; ).  
  
    - Uygulamanızda, App.xaml.cs 'e aşağıdaki kodu ekleyin:  
  
   [!code-xaml[LocBamlChangeCultureSnippets#LocBamlChangeCultureMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml#locbamlchangeculturemarkup)]
   [!code-csharp[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml.cs#locbamlchangeculturecodebehind)]
   [!code-vb[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/VisualBasic/Application.xaml.vb#locbamlchangeculturecodebehind)]  
  
<a name="Some_Tips_for_Using_LocBaml"></a>   
## <a name="some-tips-for-using-locbaml"></a>LocBaml kullanımı için bazı Ipuçları  
  
- Özel denetimleri tanımlayan tüm bağımlı derlemelerin LocBaml yerel dizinine kopyalanması veya GAC 'ye yüklenmesi gerekir. Bu gereklidir çünkü yerelleştirme API 'sinin, ikili XAML (BAML) okurken bağımlı derlemelere erişimi olması gerekir.  
  
- Ana derleme imzalanmışsa, oluşturulan kaynak DLL 'nin yüklenmesi için de imzalı olmalıdır.  
  
- Yerelleştirilmiş kaynak DLL sürümünün ana derlemeyle eşitlenmesi gerekir.  
  
<a name="Whats_Next"></a>   
## <a name="whats-next"></a>Sıradaki  
 Artık LocBaml aracının nasıl kullanılacağına ilişkin temel bilgiye sahip olmanız gerekir.  Uid 'leri içeren bir dosya yapabilmelisiniz. LocBaml aracını kullanarak, yerelleştirilebilir içeriği ayıklamak için bir dosyayı ayrıştırabilmeniz ve içerik çevrildikten sonra, çevrilmiş içeriği birleştiren bir. resources. dll dosyası oluşturmanız gerekir. Bu konu, mümkün olan her ayrıntıyı içermez, ancak artık uygulamalarınızı Yerelleştirmede LocBaml 'i kullanmak için gereken bilgiye sahipsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WPF için Genelleştirme](globalization-for-wpf.md)
- [Otomatik Düzen Kullanımına Genel Bakış](use-automatic-layout-overview.md)
