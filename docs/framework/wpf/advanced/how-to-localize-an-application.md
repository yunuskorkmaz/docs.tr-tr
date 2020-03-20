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
ms.openlocfilehash: f2e7e5e8879e89806cfd457a1af80f51b91871cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174218"
---
# <a name="how-to-localize-an-application"></a>Nasıl yapılır: Bir Uygulamayı Yerelleştirme
Bu öğretici, LocBaml aracını kullanarak yerelleştirilmiş bir uygulamanın nasıl oluşturulacağını açıklar.  
  
> [!NOTE]
> LocBaml aracı üretime hazır bir uygulama değildir. Bazı yerelleştirme API'lerini kullanan ve bir yerelleştirme aracını nasıl yazabileceğinizi gösteren bir örnek olarak sunulur.  
  
<a name="Introduction"></a>
## <a name="overview"></a>Genel Bakış  
 Bu tartışma, bir uygulamayı yerelleştirmek için adım adım bir yaklaşım sağlar. İlk olarak, çeviriyapılacak metnin çıkarılabilmeleri için başvurunuzu hazırlayacaktır. Metin çevrildikten sonra, çevrilen metni özgün uygulamanın yeni bir kopyasında birleştirirsiniz.  
  
<a name="Requirements"></a>
## <a name="requirements"></a>Gereksinimler  
 Bu tartışma boyunca, komut satırından çalışan bir derleyici olan Microsoft build engine 'i (MSBuild) kullanacaksınız.  
  
 Ayrıca, bir proje dosyası kullanmanız için talimat verilecektir. MSBuild ve proje dosyalarının nasıl kullanılacağıyla ilgili talimatlar [için](../app-development/building-and-deploying-wpf-applications.md)bkz.  
  
 Bu tartışmadaki tüm örnekler kültür olarak en-US (İngilizce-ABD) kullankullanılmaktadır. Bu, farklı bir dil yüklemeden örneklerin adımları üzerinde çalışmanızı sağlar.  
  
<a name="create_sample_app"></a>
## <a name="create-a-sample-application"></a>Örnek Uygulama Oluşturma  
 Bu adımda, yerelleştirme için başvurunuzu hazırlayacaktır. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Örneklerde, bu tartışmadaki kod örnekleri için kullanılacak bir HelloApp örneği verilir. Bu örneği kullanmak isterseniz, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] [LocBaml Tool Sample'dan](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml)dosyaları indirin.  
  
1. Uygulamanızı yerelleştirmeye başlamak istediğiniz noktaya kadar geliştirin.  
  
2. MSBuild'in nötr dil kaynaklarını içerecek şekilde bir ana montaj ve uydu derlemesi (.resources.dll uzantılı bir dosya) oluşturması için proje dosyasındaki geliştirme dilini belirtin. HelloApp örneğindeki proje dosyası HelloApp.csproj'dur. Bu dosyada, aşağıdaki gibi tanımlanan geliştirme dilini bulacaksınız:  
  
     `<UICulture>en-US</UICulture>`  
  
3. Dosyalarınıza [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Uid'leri ekleyin. Uid'ler dosyalardaki değişiklikleri izlemek ve çevrilmesi gereken öğeleri tanımlamak için kullanılır. Dosyalarınıza Uid'ler eklemek için proje dosyanızda **updateuid** çalıştırın:  
  
     **msbuild -t:updateuid helloapp.csproj**  
  
     Eksik veya yinelenen Uid'niz olmadığını doğrulamak için **checkuid'i**çalıştırın:  
  
     **msbuild -t:checkuid helloapp.csproj**  
  
     **Updateuid**çalıştırdıktan sonra, dosyalarınız Uids içermelidir. Örneğin, HelloApp'ın Pane1.xaml dosyasında aşağıdakileri bulmanız gerekir:  
  
     `<StackPanel x:Uid="StackPanel_1">`  
  
     `<TextBlock x:Uid="TextBlock_1">Hello World</TextBlock>`  
  
     `<TextBlock x:Uid="TextBlock_2">Goodbye World</TextBlock>`  
  
     `</StackPanel>`  
  
<a name="create_dll"></a>
## <a name="create-the-neutral-language-resources-satellite-assembly"></a>Tarafsız Dil Kaynakları Uydu Derlemesi Oluştur  
 Uygulama nötr bir dil kaynakları uydu derlemesi oluşturmak için yapılandırıldıktan sonra, uygulamayı oluşturursunuz. Bu, ana uygulama derlemesinin yanı sıra LocBaml tarafından yerelleştirme için gerekli olan nötr dil kaynakları uydu derlemesini oluşturur. Uygulamayı oluşturmak için:  
  
1. Dinamik bağlantı kitaplığı (DLL) oluşturmak için HelloApp'ı derle:  
  
     **msbuild helloapp.csproj**  
  
2. Yeni oluşturulan ana uygulama derlemesi HelloApp.exe aşağıdaki klasörde oluşturulur:  
  
     `C:\HelloApp\Bin\Debug\`  
  
3. Yeni oluşturulan nötr dil kaynakları uydu derlemesi HelloApp.resources.dll aşağıdaki klasörde oluşturulur:  
  
     `C:\HelloApp\Bin\Debug\en-US\`  
  
<a name="build_locbaml"></a>
## <a name="build-the-locbaml-tool"></a>LocBaml Aracı'nı oluşturun  
  
1. LocBaml oluşturmak için gerekli tüm dosyalar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] örneklerde yer almaktadır. [LocBaml Tool Sample'dan](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml)C# dosyalarını indirin.  
  
2. Komut satırından, aracı oluşturmak için proje dosyasını (locbaml.csproj) çalıştırın:  
  
     **msbuild locbaml.csproj**  
  
3. Yeni oluşturulan yürütülebilir dosyayı (locbaml.exe) bulmak için Bin\Release dizinine gidin. Örnek:C:\LocBaml\Bin\Release\locbaml.exe.  
  
4. LocBaml çalıştırdığınızda belirtebileceğiniz seçenekler şunlardır:  
  
    - **ayrışma** veya **-p:** Parses Baml, kaynaklar veya DLL dosyaları bir .csv veya .txt dosyası oluşturmak için.  
  
    - **oluşturmak** veya **-g:** Çevrilmiş bir dosya kullanarak yerelleştirilmiş bir ikili dosya oluşturur.  
  
    - **out** veya **-o** {*filedirectory*] **:** Çıktı dosyası adı.  
  
    - **kültür** veya **-cul** {*culture*] **:** Çıktı derlemelerinin yerelliği.  
  
    - **çeviri** veya **-trans** {*translation.csv*] **:** Çevrilmiş veya yerelleştirilmiş dosya.  
  
    - **asmpath** veya **-asmpath:** {*filedirectory*] **:** Kodunuz [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] özel denetimler içeriyorsa, **asmpath'i** özel denetim derlemesine sağlamanız gerekir.  
  
    - **nologo:** Hiçbir logo veya telif hakkı bilgisi görüntülemez.  
  
    - **verbose:** Ayrıntılı mod bilgilerini görüntüler.  
  
    > [!NOTE]
    > Aracı çalıştırırken seçeneklerin bir listesine ihtiyacınız varsa **LocBaml.exe** yazın ve ENTER tuşuna basın.  
  
<a name="parse_dll"></a>
## <a name="use-locbaml-to-parse-a-file"></a>Dosyayı Ayrışdırmak için LocBaml'ı kullanma  
 Artık LocBaml aracını oluşturduğunuza göre, yerelleştirilecek metin içeriğini ayıklamak için HelloApp.resources.dll ayrıştırmak için kullanmaya hazırsınız.  
  
1. LocBaml.exe'yi uygulamanızın ana uygulama derlemesinin oluşturulduğu bin\debug klasörüne kopyalayın.  
  
2. Uydu montaj dosyasını ayrıştırmak ve çıktıyı .csv dosyası olarak depolamak için aşağıdaki komutu kullanın:  
  
     **LocBaml.exe /ayrışdırılan HelloApp.resources.dll /out:Hello.csv**  
  
    > [!NOTE]
    > Giriş dosyası HelloApp.resources.dll, LocBaml.exe ile aynı dizinde değilse, her iki dosyanın da aynı dizinde olması için dosyalardan birini taşıyın.  
  
3. LocBaml'ı dosyaları ayrıştırmak için çalıştırdığınızda, çıktı virgülle (.csv dosyaları) veya sekmelerle (.txt dosyaları) sınırlandırılmış yedi alandan oluşur. HelloApp.resources.dll için ayrışmış .csv dosyaaşağıdakileri gösterir:

   | |
   |-|
   |HelloApp.g.en-US.resources:window1.baml,Stack1:System.Windows.Controls.StackPanel.$Content,Ignore,FALSE, FALSE,#Text1;#Text2;|
   |HelloApp.g.en-US.resources:window1.baml,Text1:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Hello World|
   |HelloApp.g.en-US.resources:window1.baml,Text2:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Goodbye World|

   Yedi alan şunlardır:  
  
   1. **BAML Adı**. Kaynak dil uydu derlemesi ile ilgili BAML kaynağının adı.  
  
   2. **Kaynak Anahtarı**. Yerelleştirilmiş kaynak tanımlayıcısı.  
  
   3. **Kategori**. Değer türü. Bkz. [Yerelleştirme Öznitelikleri ve Açıklamaları](localization-attributes-and-comments.md).  
  
   4. **Okunabilirlik**. Değerin bir yerelleştirici tarafından okunup okunamayacağı. Bkz. [Yerelleştirme Öznitelikleri ve Açıklamaları](localization-attributes-and-comments.md).  
  
   5. **Değiştirilebilirlik**. Değerin bir yerelleştirici tarafından değiştirilip değiştirilemeyeceği. Bkz. [Yerelleştirme Öznitelikleri ve Açıklamaları](localization-attributes-and-comments.md).  
  
   6. **Yorumlar**. Bir değerin nasıl yerelleştirilmeye yardımcı olacak değerin ek açıklaması. Bkz. [Yerelleştirme Öznitelikleri ve Açıklamaları](localization-attributes-and-comments.md).  
  
   7. **Değer**. İstenilen kültüre çevirmek için metin değeri.  
  
   Aşağıdaki tablo, bu alanların .csv dosyasının sınırlı değerleriyle nasıl eşleşiş gösterdiğini gösterir:  
  
   |BAML adı|Kaynak anahtarı|Kategori|Okunabilirlik|Modifiability|Yorumlar|Değer|  
   |---------------|------------------|--------------|-----------------|-------------------|--------------|-----------|
   |MerhabaApp.g.tr-US.resources:window1.baml|Stack1:System.Windows.Controls.StackPanel.$Content|Yoksayma|FALSE|FALSE||#Text1;#Text2|
   |MerhabaApp.g.tr-US.resources:window1.baml|Metin1:System.Windows.Controls.TextBlock.$Content|None|TRUE|TRUE||Hello World|
   |MerhabaApp.g.tr-US.resources:window1.baml|Text2:System.Windows.Controls.TextBlock.$Content|None|TRUE|TRUE||Güle Güle Dünya|
  
   **Yorumlar** alanıiçin tüm değerlerin hiçbir değer içermediğini unutmayın; bir alanın bir değeri yoksa, boştur. Ayrıca, ilk satırdaki öğenin ne okunabilir ne de değiştirilebilir olduğunu ve **Kategori** değeri olarak "Yoksay" öğesi olduğunu ve bunların hepsinin değerin yerelleştirilemeyeceğini gösterdiğini de unutmayın.  
  
4. Özellikle büyük dosyalarda, ayrıştırılan dosyalarda yerelleştirilebilir öğelerin bulunmasını kolaylaştırmak için, öğeleri **Kategori,** **Okunabilirlik**ve **Değiştirilebilirliğe**göre sıralayabilir veya filtreleyebilirsiniz. Örneğin, okunamayan ve değiştirilemez değerleri filtreleyebilirsiniz.  
  
<a name="translate_loc_content"></a>
## <a name="translate-the-localizable-content"></a>Yerelleştirilebilir İçeriği Çevirin  
 Çıkarılan içeriği çevirmek için kullanabileceğiniz herhangi bir aracı kullanın. Bunu yapmanın iyi bir yolu, kaynakları bir .csv dosyasına yazmak ve microsoft Excel'de görüntülemek ve son sütunda (değer) çeviri değişiklikleri yapmaktır.  
  
<a name="merge_translations"></a>
## <a name="use-locbaml-to-generate-a-new-resourcesdll-file"></a>Yeni bir .resources.dll Dosyası Oluşturmak için LocBaml'ı kullanın  
 HelloApp.resources.dll'yi LocBaml ile ayrıştarak tanımlanan içerik çevrilmiştir ve orijinal uygulamaya geri verilmesi gerekir. Yeni bir .resources.dll dosyası oluşturmak için **oluşturma** veya **-g** seçeneğini kullanın.  
  
1. Yeni bir HelloApp.resources.dll dosyası oluşturmak için aşağıdaki sözdizimini kullanın. Kültürü en-US (/cul:en-US) olarak işaretleyin.  
  
     **LocBaml.exe /generate HelloApp.resources.dll /trans:Hello.csv /out:c:\ /cul:en-US**  
  
    > [!NOTE]
    > Giriş dosyası Hello.csv, yürütülebilir, LocBaml.exe ile aynı dizinde değilse, her iki dosyanın da aynı dizinde olması için dosyalardan birini taşıyın.  
  
2. C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll dizinini yeni oluşturduğunuz HelloApp.resources.dll dosyanızla değiştirin.  
  
3. "Hello World" ve "Goodbye World" artık başvurunuzla çevrilmelidir.  
  
4. Farklı bir kültüre çevirmek için, çevirdiğiniz dilin kültürünü kullanın. Aşağıdaki örnek, Fransızca-Kanadaca nasıl çevrileceklerini gösterir:  
  
     **LocBaml.exe /generate HelloApp.resources.dll /trans:Hellofr-CA.csv /out:c:\ /cul:fr-CA**  
  
5. Ana uygulama derlemesi ile aynı derlemede, yeni uydu derlemesini barındırmak için kültüre özel yeni bir klasör oluşturun. Fransızca-Kanada için, klasör fr-CA olacaktır.  
  
6. Oluşturulan uydu derlemesini yeni klasöre kopyalayın.  
  
7. Yeni uydu montajını test etmek için uygulamanızın çalışacağı kültürü değiştirmeniz gerekir. Bunu iki yoldan biriyle yapabilirsiniz:  
  
    - İşletim sisteminizin bölgesel ayarlarını**değiştirin** **(Bölgesel ve Dil Seçenekleri**&#124; &#124; **Kontrol Paneli** başlatın).  
  
    - Uygulamanızda, App.xaml.cs için aşağıdaki kodu ekleyin:  
  
   [!code-xaml[LocBamlChangeCultureSnippets#LocBamlChangeCultureMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml#locbamlchangeculturemarkup)]
   [!code-csharp[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml.cs#locbamlchangeculturecodebehind)]
   [!code-vb[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/VisualBasic/Application.xaml.vb#locbamlchangeculturecodebehind)]  
  
<a name="Some_Tips_for_Using_LocBaml"></a>
## <a name="some-tips-for-using-locbaml"></a>LocBaml kullanmak için bazı ipuçları  
  
- Özel denetimleri tanımlayan tüm bağımlı derlemeler LocBaml'ın yerel dizinine kopyalanmalıdır veya GAC'ye yüklenmelidir. Bu gereklidir, çünkü yerelleştirme API'si ikili XAML (BAML) okurken bağımlı derlemelere erişebilmeli.  
  
- Ana derleme imzalanırsa, yüklenmesi için oluşturulan kaynak DLL'nin de imzalanması gerekir.  
  
- Yerelleştirilmiş kaynak DLL sürümü ana derleme ile eşitlenmiş olması gerekir.  
  
<a name="Whats_Next"></a>
## <a name="whats-next"></a>Sırada Ne Var  
 Şimdi LocBaml aracını nasıl kullanacağınız konusunda temel bir anlayışa sahip olmalısınız.  Uid'ler içeren bir dosya yapmak gerekir. LocBaml aracını kullanarak, yerelleştirilebilir içeriği ayıklamak için bir dosyayı ayrıştıramalısınız ve içerik çevrildikten sonra çevrilen içeriği birleştiren bir .resources.dll dosyası oluşturabilirsiniz. Bu konu mümkün olan her ayrıntıyı içermez, ancak artık uygulamalarınızı yerelleştirmek için LocBaml'ı kullanmanız gereken bilgiye sahipsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WPF için Genelleştirme](globalization-for-wpf.md)
- [Otomatik Düzen Kullanımına Genel Bakış](use-automatic-layout-overview.md)
