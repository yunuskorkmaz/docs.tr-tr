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
ms.openlocfilehash: 1190fb739e7c1873532e96b50399ac0deb6bb51c
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46478610"
---
# <a name="how-to-localize-an-application"></a>Nasıl yapılır: Bir Uygulamayı Yerelleştirme
Bu öğreticide LocBaml aracı kullanarak yerelleştirilmiş bir uygulama oluşturulacağını açıklar.  
  
> [!NOTE]
>  LocBaml aracı, bir üretim ortamına hazır uygulamasını değil. Bu, bazı yerelleştirme API'lerini kullanır ve yerelleştirme Aracı nasıl yazabilirsiniz gösterir bir örnek sunulur.  
  
<a name="Introduction"></a>   
## <a name="overview"></a>Genel Bakış  
 Bu tartışma bir uygulamayı yerelleştirme için adım adım bir yaklaşım sunar. İlk olarak, böylece Çevrilecek metin ayıklanabileceği uygulamanızı hazırlayacaksınız. Metin çevrildikten sonra çevrilmiş metni özgün uygulamayı yeni bir kopyasını birleştirecektir.  
  
<a name="Requirements"></a>   
## <a name="requirements"></a>Gereksinimler  
 Bu tartışma kursunda kullanacağınız [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)], komut satırından çalışan bir derleyici olduğu.  
  
 Ayrıca, bir proje dosyasını kullanmak için yönlendirilirsiniz. Nasıl kullanılacağı hakkında yönergeler için [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] ve proje dosyaları, bkz: [derleme ve dağıtma](../../../../docs/framework/wpf/app-development/building-and-deploying-wpf-applications.md).  
  
 Bu konudaki tüm örnekler en-US (İngilizce-ABD) kültürü kullanır. Bu örneklerin adımları, farklı bir dil yüklemeden çalışmanıza olanak sağlar.  
  
<a name="create_sample_app"></a>   
## <a name="create-a-sample-application"></a>Örnek bir uygulama oluşturma  
 Bu adımda, uygulamanızın yerelleştirme için hazırlık yapacaksınız. İçinde [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] örnekleri, bu konudaki kod örnekleri için kullanılacak bir HelloApp örnek sağlanmaktadır. Bu örneği kullanmak istiyorsanız, indirme [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosyalarını [LocBaml aracı örneği](https://go.microsoft.com/fwlink/?LinkID=160016).  
  
1.  Yerelleştirme başlamak istediğiniz noktayı uygulamanızı geliştirin.  
  
2.  Proje dosyasında bir geliştirme dilini belirtmek böylece [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] bir ana derlemeye ve bir uydu derlemesi oluşturur (bir dosyayla. resources.dll uzantısı) nötr dil kaynakları içerecek şekilde. HelloApp örnek proje dosyasında HelloApp.csproj'dur. Bu dosyada, aşağıdaki şekilde tanımlanan bir geliştirme dilini bulacaksınız:  
  
     `<UICulture>en-US</UICulture>`  
  
3.  İçin Uıd'leri ekleyin, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyaları. Uıd'leri dosyalarda yapılan değişiklikler izlemek ve çevrilmelidir öğeleri tanımlamak için kullanılır. Uıd'leri dosyalarınıza eklemek için çalıştırın **updateuid** proje dosyanızda:  
  
     **MSBuild - t: updateuid helloapp.csproj**  
  
     Eksik veya Uıd'leri yinelenen doğrulamak için çalıştırın **checkuid**:  
  
     **MSBuild - t: checkuid helloapp.csproj**  
  
     Çalıştırdıktan sonra **updateuid**, dosyalarınızı Uıd'leri içermelidir. Örneğin, Pane1.xaml dosyasında, aşağıdaki bulduğunuz:  
  
     `<StackPanel x:Uid="StackPanel_1">`  
  
     `<TextBlock x:Uid="TextBlock_1">Hello World</TextBlock>`  
  
     `<TextBlock x:Uid="TextBlock_2">Goodbye World</TextBlock>`  
  
     `</StackPanel>`  
  
<a name="create_dll"></a>   
## <a name="create-the-neutral-language-resources-satellite-assembly"></a>Nötr dil kaynakları uydu derleme oluşturma  
 Uygulama dilden kaynakları uydu derlemesi oluşturmak için yapılandırdıktan sonra uygulamayı derleyin. Bu, ana uygulama derlemesine yanı sıra LocBaml tarafından yerelleştirme için gerekli bağımsız dil kaynakları uydu derlemesi oluşturur. Uygulamayı oluşturmak için:  
  
1.  Derleme oluşturmak için HelloApp bir [!INCLUDE[TLA#tla_dll](../../../../includes/tlasharptla-dll-md.md)]:  
  
     **MSBuild helloapp.csproj**  
  
2.  Yeni oluşturulan ana uygulama derlemesine, HelloApp.exe aşağıdaki klasörde oluşturulur:  
  
     `C:\HelloApp\Bin\Debug\`  
  
3.  Yeni oluşturulan dilden kaynakları uydu derlemesini HelloApp.resources.dll aşağıdaki klasörde oluşturulur:  
  
     `C:\HelloApp\Bin\Debug\en-US\`  
  
<a name="build_locbaml"></a>   
## <a name="build-the-locbaml-tool"></a>Derleme LocBaml aracı  
  
1.  LocBaml oluşturmak gereken tüm dosyaları bulunan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] örnekleri. C# dosyalarını indirmeye [LocBaml aracı örneği](https://go.microsoft.com/fwlink/?LinkID=160016).  
  
2.  Komut satırından derleme aracı için proje dosyası (locbaml.csproj) çalıştırın:  
  
     **MSBuild locbaml.csproj**  
  
3.  Yeni oluşturulan yürütülebilir dosya (LocBaml.exe'yi) bulmak için Bin\Release dizine gidin. Example:C:\LocBaml\Bin\Release\locbaml.exe.  
  
4.  LocBaml çalıştırdığınızda belirtebileceğiniz seçenekleri aşağıdaki gibidir:  
  
    -   **Ayrıştırma** veya **-p:** Baml ayrıştırır, kaynaklar veya [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] .csv ya da .txt dosyası oluşturmak için dosyaları.  
  
    -   **oluşturma** veya **-g:** çevrilmiş dosyası kullanarak yerelleştirilmiş bir ikili dosya oluşturur.  
  
    -   **Çıkış** veya **-o** {*filedirectory*] **:** çıkış dosyası adı.  
  
    -   **kültür** veya **- cul** {*kültür*] **:** çıkış derlemelerinin yerel ayarı.  
  
    -   **Çeviri** veya **- trans** {*translation.csv*] **:** çevrilmiş ya da yerelleştirilmiş dosyası.  
  
    -   **asmpath** veya **- asmpath:** {*filedirectory*] **:** varsa, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kodu özel denetimler içeren, siz sağlamalısınız  **asmpath** özel denetim derleme.  
  
    -   **nologo:** hiçbir logo veya telif hakkı bilgilerini görüntüler.  
  
    -   **ayrıntılı:** ayrıntılı modu bilgileri görüntüler.  
  
    > [!NOTE]
    >  Seçeneklerin bir listesi Aracı çalıştırırken gerekiyorsa, yazın **LocBaml.exe'yi** ve ENTER tuşuna basın.  
  
<a name="parse_dll"></a>   
## <a name="use-locbaml-to-parse-a-file"></a>Bir dosya ayrıştırılamıyor LocBaml Kullanma  
 LocBaml aracı oluşturduğunuza göre bu HelloApp.resources.dll yerelleştirilecek metin içeriği ayıklama için ayrıştırmak için kullanıma hazır olursunuz.  
  
1.  LocBaml.exe ana uygulama derlemesine oluşturulduğu, uygulamanızın bin\debug klasörüne kopyalayın.  
  
2.  Uydu derleme dosyasını ayrıştırma ve bir .csv dosyası olarak çıktısını depolamak için aşağıdaki komutu kullanın:  
  
     **LocBaml.exe'yi /parse HelloApp.resources.dll /out:Hello.csv**  
  
    > [!NOTE]
    >  HelloApp.resources.dll giriş dosyası içinde değilse LocBaml.exe'yi aynı dizine taşı dosyalarından birini her iki dosya aynı dizinde olmasını sağlamak.  
  
3.  LocBaml dosyalarını ayrıştırmak için çalıştırdığınızda, çıktı virgül (.csv dosyaları) veya sekme (.txt dosyaları) tarafından ayrılmış yedi alandan oluşur. Aşağıdaki ayrıştırılmış .csv dosyasını HelloApp.resources.dll için gösterir:

   | |
   |-|
   |HelloApp.g.en US.resources:window1.baml, Stack1:System.Windows.Controls.StackPanel. $Content, Yoksay FALSE, FALSE, #Text1; #Text2;|
   |HelloApp.g.en US.resources:window1.baml, Text1:System.Windows.Controls.TextBlock. None, $Content TRUE, TRUE, Merhaba Dünya|
   |HelloApp.g.en US.resources:window1.baml, Text2:System.Windows.Controls.TextBlock. None, $Content TRUE, TRUE, güle güle World|

   Yedi alanlar şunlardır:  
  
   1.  **BAML adı**. Kaynak dili uydu derlemeye göre BAML kaynağının adı.  
  
   2.  **Kaynak anahtarı**. Yerelleştirilmiş kaynak tanımlayıcısı.  
  
   3.  **Kategori**. Değer türü. Bkz: [Yerelleştirme öznitelikleri ve Yorumlar](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).  
  
   4.  **Okunabilirlik**. Olup değeri bir yerelleştiriciye tarafından okunabilir. Bkz: [Yerelleştirme öznitelikleri ve Yorumlar](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).  
  
   5.  **Modifiability'e göre**. Olup değeri bir yerelleştiriciye tarafından değiştirilebilir. Bkz: [Yerelleştirme öznitelikleri ve Yorumlar](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).  
  
   6.  **Açıklamalar**. Ek açıklama değeri nasıl yerelleştirilmiş belirlemeye yardımcı olması için değeri. Bkz: [Yerelleştirme öznitelikleri ve Yorumlar](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).  
  
   7.  **Değer**. İstenen kültüre Çevrilecek metin değeri.  
  
   Aşağıdaki tabloda, bu alanlar .csv dosyasını ayrılmış değerleri nasıl eşleştiği gösterilmektedir:  
  
   |BAML adı|Kaynak anahtarı|Kategori|Okunabilirlik|Modifiability'e göre|Açıklamalar|Değer|  
   |---------------|------------------|--------------|-----------------|-------------------|--------------|-----------|
   |HelloApp.g.en US.resources:window1.baml|Stack1:System.Windows.Controls.StackPanel.$Content|Yoksay|FALSE|FALSE||#Text1; #Text2|
   |HelloApp.g.en US.resources:window1.baml|Text1:System.Windows.Controls.TextBlock.$Content|Yok.|TRUE|TRUE||Merhaba Dünya|
   |HelloApp.g.en US.resources:window1.baml|Text2:System.Windows.Controls.TextBlock.$Content|Yok.|TRUE|TRUE||Güle güle World|
  
   Dikkat tüm değerler için **açıklamaları** alanın değer içermesi; bir alan bir değer yoksa boş. Ayrıca ilk satırda öğe okunabilir ve değiştirilebilir ve "Yoksay" sahip olarak dikkat edin, **kategori** değeri, her biri olmadığını değeri yerelleştirilebilir olduğunu belirtir.  
  
4.  Ayrıştırılmış dosyaları, özellikle de büyük dosyalarda yerelleştirilebilir öğelerinde bulunmasını kolaylaştırmak için sıralama veya öğelerini göre filtreleme **kategori**, **okunabilirliği**, ve **Modifiability'egöre**. Örneğin, okunamaz ve değiştirilemeyen değerlere filtre uygulayabilirsiniz.  
  
<a name="translate_loc_content"></a>   
## <a name="translate-the-localizable-content"></a>Yerelleştirilebilir İçerik Çevir  
 Ayıklanan içeriği çevirmek kullanılabilir olan herhangi bir aracı kullanın. Bunu yapmak için en iyi yolu kaynaklara bir .csv dosyası ve görüntülemeye yazmaktır [!INCLUDE[TLA#tla_xl](../../../../includes/tlasharptla-xl-md.md)], çeviri yapmadan değişikliklerini son sütunu (değer).  
  
<a name="merge_translations"></a>   
## <a name="use-locbaml-to-generate-a-new-resourcesdll-file"></a>LocBaml yeni oluşturmak için kullanın. resources.dll dosyasını  
 LocBaml ile HelloApp.resources.DLL'i tarafından tanımlanan içeriği çevrilmiştir ve özgün uygulamasına birleştirilmesi gerekir. Kullanım **oluşturmak** veya **-g** yeni bir seçenek. resources.dll dosyasını.  
  
1.  Yeni bir HelloApp.resources.dll dosyası oluşturmak için aşağıdaki sözdizimini kullanın. Kültür en-US olarak işaretleyin (/ cul: en-US).  
  
     **LocBaml.exe'yi / HelloApp.resources.dll /trans:Hello.csv /out:c oluştur: \ /cul:en-ABD**  
  
    > [!NOTE]
    >  Giriş dosyası Hello.csv LocBaml.exe yürütülebilir dosya ile aynı dizinde değilse, her iki dosya aynı dizinde, böylece dosyalarından birini taşıyın.  
  
2.  Yeni oluşturulan HelloApp.resources.dll dosyanızla C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll dizininde Eski HelloApp.resources.dll dosyasını değiştirin.  
  
3.  "Hello World" ve "Goodbye World" artık uygulamanızda çevrilmesi gerekir.  
  
4.  Farklı bir kültüre çevirmek için çevireceğiniz dil kültürünü kullanın. Aşağıdaki örnek, Canadian'a Çevir gösterilmektedir:  
  
     **LocBaml.exe'yi / HelloApp.resources.dll /trans:Hellofr Oluştur-CA.csv /out:c: \ /cul:fr-CA**  
  
5.  Ana uygulama derlemesine aynı derlemede yeni bir uydu derleme barındırmak için yeni bir kültüre özgü klasör oluşturun. French-Canadian için klasörü, fr-CA olabilir.  
  
6.  Oluşturulan uydu derlemesini yeni klasöre kopyalayın.  
  
7.  Yeni bir uydu derleme test etmek için uygulamanızı altında çalıştırılacağı kültürü değiştirmeniz gerekir. Bunu iki yoldan biriyle yapabilirsiniz:  
  
    -   İşletim sisteminizin bölgesel ayarları değiştirin (**Başlat** &#124; **Denetim Masası** &#124; **bölge ve Dil Seçenekleri**).  
  
    -   Uygulamanızda, App.xaml.cs için aşağıdaki kodu ekleyin:  
  
   [!code-xaml[LocBamlChangeCultureSnippets#LocBamlChangeCultureMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml#locbamlchangeculturemarkup)]
   [!code-csharp[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml.cs#locbamlchangeculturecodebehind)]
   [!code-vb[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/VisualBasic/Application.xaml.vb#locbamlchangeculturecodebehind)]  
  
<a name="Some_Tips_for_Using_LocBaml"></a>   
## <a name="some-tips-for-using-locbaml"></a>LocBaml kullanmaya yönelik bazı ipuçları  
  
-   Özel denetimler tanımlayabilirsiniz tüm bağımlı derlemeler LocBaml yerel dizine kopyalanır veya GAC içine yüklenmelidir. Okuduğunda API yerelleştirme bağımlı derleme erişimi olması gerektiğinden bu gereklidir [!INCLUDE[TLA#tla_baml](../../../../includes/tlasharptla-baml-md.md)].  
  
-   Ana derleme imzalanmışsa, aynı zamanda oluşturulan kaynak DLL yüklenecek sırayla imzalanması gerekir.  
  
-   Yerelleştirilmiş kaynak sürümü DLL ana derleme ile eşitlenmesi gerekir.  
  
<a name="Whats_Next"></a>   
## <a name="whats-next"></a>Yenilikler  
 Artık LocBaml aracı kullanmak nasıl temel bir anlayışa sahipsiniz.  Uıd'leri içeren bir dosya olmak. LocBaml aracı kullanarak, yerelleştirilebilir içerik ayıklamak için dosyayı ayrıştırılacak erişebileceğinizi ve içerik çevrilebilir sonra üretmeden olmalıdır bir. resources.dll dosyasını çevrilen içeriğin birleştirir. Bu konu, her olası ayrıntı içermez, ancak artık uygulamalarınızı yerelleştirme için LocBaml kullanmak için gerekli bilgi vardır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WPF için Genelleştirme](../../../../docs/framework/wpf/advanced/globalization-for-wpf.md)  
 [Otomatik Düzen Kullanımına Genel Bakış](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)
