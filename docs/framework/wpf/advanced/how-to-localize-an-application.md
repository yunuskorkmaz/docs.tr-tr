---
title: 'Nasıl yapılır: Bir Uygulamayı Yerelleştirme'
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- localization [WPF], applications
- LocBaml tool [WPF]
- applications [WPF], localizing
ms.assetid: 5001227e-9326-48a4-9dcd-ba1b89ee6653
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3c5621de2a2d10e67f45fa2d6980cb84c388630f
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-localize-an-application"></a>Nasıl yapılır: Bir Uygulamayı Yerelleştirme
Bu öğretici LocBaml aracını kullanarak yerelleştirilmiş bir uygulama oluşturma açıklanmaktadır.  
  
> [!NOTE]
>  LocBaml aracı üretime hazır bir uygulama değil. Bazı yerelleştirme API'lerini kullanan ve bir yerelleştirme aracını nasıl yazabilir gösterilmektedir bir örnek olarak sunulur.  
  
<a name="Introduction"></a>   
## <a name="overview"></a>Genel Bakış  
 Bu tartışma uygulama yerelleştirme için adım adım bir yaklaşım sağlar. İlk olarak, böylece çevrilir metin ayıklanabilir uygulamanızı hazırlayacaksınız. Metin çevrilen sonra özgün uygulamayı yeni bir kopyasını çevrilmiş metni birleştirir.  
  
<a name="Requirements"></a>   
## <a name="requirements"></a>Gereksinimler  
 Bu tartışma süresince kullanacağınız [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)], komut satırından çalışan bir derleyici olduğu.  
  
 Ayrıca, proje dosyasını kullanmanız istenecek. Nasıl kullanılacağı hakkında yönergeler için [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] ve proje dosyalarını bkz [oluşturma ve dağıtma](../../../../docs/framework/wpf/app-development/building-and-deploying-wpf-applications.md).  
  
 Bu konudaki tüm örnekler kültür olarak en-US (İngilizce-ABD) kullanın. Bu, farklı bir dil yüklemeden örneklerin adımlarını çalışmanıza olanak sağlar.  
  
<a name="create_sample_app"></a>   
## <a name="create-a-sample-application"></a>Örnek bir uygulama oluşturma  
 Bu adımda, uygulamanızı yerelleştirme için hazırlarsınız. İçinde [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] örnekleri, bu konudaki kod örnekleri için kullanılacak bir HelloApp örnek sağlanmaktadır. Bu örneği kullanmak istiyorsanız, indirme [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosyaları buradan [LocBaml aracı örneği](http://go.microsoft.com/fwlink/?LinkID=160016).  
  
1.  Yerelleştirme başlatmak istediğiniz noktasına uygulamanızı geliştirin.  
  
2.  Proje dosyasında geliştirme dilini belirtin böylece [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] ana derleme ve uydu derlemesini oluşturur (bir dosyayla. resources.dll uzantısı) dilden bağımsız kaynakları içerecek şekilde. HelloApp örnek proje dosyasında HelloApp.csproj'dur. Bu dosyada, aşağıdaki gibi tanımlanan geliştirme dilini bulabilirsiniz:  
  
     `<UICulture>en-US</UICulture>`  
  
3.  Uıd'leri için ekleme, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyaları. Uıd'leri dosyalardaki değişiklikler izlemek ve çevrilmelidir öğeleri tanımlamak için kullanılır. Uıd'leri dosyalarınıza eklemek için çalıştırın **updateuid** proje dosyanızda:  
  
     **MSBuild /t:updateuid helloapp.csproj**  
  
     Eksik veya Uıd'leri yinelenen doğrulamak için çalıştırın **checkuid**:  
  
     **MSBuild /t:checkuid helloapp.csproj**  
  
     Çalıştırdıktan sonra **updateuid**, dosyalarınızı Uıd'leri içermelidir. Örneğin, Pane1.xaml dosyasında, aşağıdaki bulduğunuz:  
  
     `<StackPanel x:Uid="StackPanel_1">`  
  
     `<TextBlock x:Uid="TextBlock_1">Hello World</TextBlock>`  
  
     `<TextBlock x:Uid="TextBlock_2">Goodbye World</TextBlock>`  
  
     `</StackPanel>`  
  
<a name="create_dll"></a>   
## <a name="create-the-neutral-language-resources-satellite-assembly"></a>Dilden kaynakların uydu derlemesini oluşturun  
 Uygulama, bir dilden bağımsız kaynakların uydu derlemesini oluşturmak için yapılandırıldıktan sonra uygulamayı oluşturun. Bu, yerelleştirme için LocBaml tarafından gereken dilden kaynakları uydu derlemesini yanı sıra ana uygulama derlemesini oluşturur. Uygulamayı yapılandırmak için:  
  
1.  Oluşturmak için HelloApp derleyin bir [!INCLUDE[TLA#tla_dll](../../../../includes/tlasharptla-dll-md.md)]:  
  
     **MSBuild helloapp.csproj**  
  
2.  Yeni oluşturulan ana uygulama bütünleştirilmiş kodu HelloApp.exe aşağıdaki klasörde oluşturulur:  
  
     `C:\HelloApp\Bin\Debug\`  
  
3.  Yeni oluşturulan dilden kaynakları uydu derlemesini HelloApp.resources.dll aşağıdaki klasörde oluşturulur:  
  
     `C:\HelloApp\Bin\Debug\en-US\`  
  
<a name="build_locbaml"></a>   
## <a name="build-the-locbaml-tool"></a>LocBaml aracını yapılandırma  
  
1.  LocBaml'i yapılandırmak için gerekli tüm dosyalar bulunur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] örnekleri. C# dosyalarını indirme [LocBaml aracı örneği](http://go.microsoft.com/fwlink/?LinkID=160016).  
  
2.  Komut satırından aracı yapılandırmak için proje dosyası (locbaml.csproj) çalıştırın:  
  
     **MSBuild locbaml.csproj**  
  
3.  Yeni oluşturulan yürütülebilir dosya (locbaml.exe) bulmak için Bin\Release dizinine gidin. Example:C:\LocBaml\Bin\Release\locbaml.exe.  
  
4.  LocBaml'i çalıştırdığınızda belirtebilirsiniz seçenekleri aşağıdaki gibidir:  
  
    -   **Ayrıştırma** veya **-p:** ayrıştırır Baml, kaynaklar veya [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] .csv veya .txt dosyası oluşturmak için dosyaları.  
  
    -   **Oluştur** veya **-g:** çevrilmiş dosyayı kullanarak yerelleştirilmiş bir ikili dosya oluşturur.  
  
    -   **out** veya **-o** {*filedirectory*] **:** çıktı dosyası adı.  
  
    -   **kültür** veya **- cul** {*kültür*] **:** çıkış derlemelerinin yerel ayarı.  
  
    -   **Çeviri** veya **- hareketi** {*translation.csv*] **:** çevrilmiş ya da yerelleştirilmiş dosya.  
  
    -   **asmpath** veya **- asmpath:** {*filedirectory*] **:** varsa, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kodu özel denetimleri içeriyorsa, sağlamanız gerekir  **asmpath** özel denetim derleme.  
  
    -   **nologo:** hiçbir logo veya telif hakkı bilgileri görüntüler.  
  
    -   **ayrıntılı:** ayrıntılı mod bilgileri görüntüler.  
  
    > [!NOTE]
    >  Aracı çalıştırırken seçeneklerin bir listesini gerekiyorsa, yazın **LocBaml.exe'yi** ve ENTER tuşuna basın.  
  
<a name="parse_dll"></a>   
## <a name="use-locbaml-to-parse-a-file"></a>Bir dosyayı ayrıştırmak için LocBaml Kullanma  
 LocBaml aracını oluşturduğunuza göre bunu yerelleştirilmiş olabilir metin içeriği ayıklamak için HelloApp.resources.dll ayrıştırmak için kullanılacak hazır olursunuz.  
  
1.  LocBaml.exe'yi ana uygulama derlemesini oluşturulduğu uygulamanızın klasörüne, kopyalayın.  
  
2.  Uydu derleme dosyasını ayrıştırabilir ve çıktıyı bir .csv dosyası olarak depolamak için aşağıdaki komutu kullanın:  
  
     **LocBaml.exe'yi /parse HelloApp.resources.dll /out:Hello.csv**  
  
    > [!NOTE]
    >  HelloApp.resources.dll giriş dosyası içinde değilse LocBaml.exe'yi aynı dizine taşıyın dosyalarından birini dosyalarının her ikisinin de aynı dizinde; böylece.  
  
3.  Dosyaları ayrıştırmak için LocBaml'i çalıştırdığınızda, çıktı virgüller (.csv dosyaları) veya sekmeler (.txt dosyaları) tarafından ayrılmış yedi alandan oluşur. Aşağıdaki, HelloApp.resources.dll için ayrıştırılmış .csv dosyasını gösterir:

   | |
   |-|
   |HelloApp.g.en US.resources:window1.baml, Stack1:System.Windows.Controls.StackPanel. $Content, Yoksay yanlış, yanlış,, # Metin1; # Metin2;|
   |HelloApp.g.en US.resources:window1.baml, Text1:System.Windows.Controls.TextBlock. hiçbiri, $Content TRUE, TRUE,, Merhaba Dünya|
   |HelloApp.g.en US.resources:window1.baml, Text2:System.Windows.Controls.TextBlock. hiçbiri, $Content TRUE, TRUE,, Goodbye World|

   Yedi alanlar şunlardır:  
  
   1.  **BAML adı**. Kaynak dili uydu derlemesine göre BAML kaynağının adı.  
  
   2.  **Kaynak anahtarı**. Yerelleştirilmiş kaynak tanımlayıcısı.  
  
   3.  **Kategori**. Değer türü. Bkz: [Yerelleştirme öznitelikleri ve Yorumlar](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).  
  
   4.  **Okunabilirlik**. Olup değeri yerelleştirici tarafından okunabilir. Bkz: [Yerelleştirme öznitelikleri ve Yorumlar](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).  
  
   5.  **Modifiability'e göre**. Olup değeri yerelleştirici tarafından değiştirilebilir. Bkz: [Yerelleştirme öznitelikleri ve Yorumlar](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).  
  
   6.  **Açıklamaları**. Ek açıklama değeri nasıl yerelleştirilmiş belirlemeye yardımcı olmak için değeri. Bkz: [Yerelleştirme öznitelikleri ve Yorumlar](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).  
  
   7.  **Değer**. İstenen kültüre çevirmek için metin değeri.  
  
   Aşağıdaki tabloda, bu alanların .csv dosyasının ayrılmış değerlere nasıl karşıladığı gösterilmektedir:  
  
   |BAML adı|Kaynak anahtarı|Kategori|Okunabilirlik|Modifiability'e göre|Açıklamalar|Değer|  
   |---------------|------------------|--------------|-----------------|-------------------|--------------|-----------|
   |HelloApp.g.en US.resources:window1.baml|Stack1:System.Windows.Controls.StackPanel.$Content|Yoksay|FALSE|FALSE||# Metin1; # Metin2|
   |HelloApp.g.en US.resources:window1.baml|Text1:System.Windows.Controls.TextBlock.$Content|Yok.|TRUE|TRUE||Merhaba Dünya|
   |HelloApp.g.en US.resources:window1.baml|Text2:System.Windows.Controls.TextBlock.$Content|Yok.|TRUE|TRUE||Güle güle World|
  
   Dikkat tüm değerleri **açıklamaları** alan hiçbir değer içeriyor; bir alan bir değer yoksa, boş. Ayrıca ilk satırda öğesi ne okunabilir ne de değiştirilebilir ve "Yoksay" sahip olarak dikkat edin, **kategori** değeri, her biri gösteren değer yerelleştirilebilir değil.  
  
4.  Ayrıştırılmış dosyalarında, özellikle de büyük dosyalarda yerelleştirilebilir öğelerin bulma kolaylaştırmak için listeyi sıralayın veya öğeleri göre filtrele **kategori**, **okunabilirlik**, ve **Modifiability'egöre**. Örneğin, okunamaz ve değiştirilemeyen değerlere filtre uygulayabilirsiniz.  
  
<a name="translate_loc_content"></a>   
## <a name="translate-the-localizable-content"></a>Yerelleştirilebilir İçerik Çevir  
 Ayıklanan içeriği çevirmek kullanılabilir olan herhangi bir aracı kullanın. Bunu yapmak için en iyi yolu kaynakları .csv dosya ve görüntülemeye yazmaktır [!INCLUDE[TLA#tla_xl](../../../../includes/tlasharptla-xl-md.md)], çeviri yapma değişikliklerini son sütun (değer).  
  
<a name="merge_translations"></a>   
## <a name="use-locbaml-to-generate-a-new-resourcesdll-file"></a>Yeni bir oluşturmak için LocBaml kullanın. resources.dll dosyası  
 LocBaml ile HelloApp.resources.DLL'i tarafından tanımlanan içerik çevrilmiştir ve özgün uygulamasına birleştirilmesi gerekir. Kullanım **oluşturmak** veya **-g** yeni oluşturmak için seçeneği. resources.dll dosyası.  
  
1.  Yeni bir HelloApp.resources.dll dosyası oluşturmak için aşağıdaki sözdizimini kullanın. Kültür en-US olarak işaretle (/ cul: en-US).  
  
     **LocBaml.exe'yi / HelloApp.resources.dll /trans:Hello.csv /out:c oluştur: \ /cul:en-ABD**  
  
    > [!NOTE]
    >  Giriş dosyası, Hello.csv çalıştırılabilir LocBaml.exe ile aynı dizinde değilse, böylece her iki dosya aynı dizinde dosyalarından birini taşıyın.  
  
2.  Eski HelloApp.resources.dll dosyasını C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll dizininde, yeni oluşturulan HelloApp.resources.dll dosyası ile değiştirin.  
  
3.  "Hello World" ve "Goodbye World" şimdi uygulamanızda çevrilmesi gerekir.  
  
4.  Farklı bir kültür çevirmek için çevireceğiniz dil kültürünü kullanın. Aşağıdaki örnek, Canadian'a Çevir gösterilmektedir:  
  
     **LocBaml.exe'yi / HelloApp.resources.dll /trans:Hellofr Oluştur-CA.csv /out:c: \ /cul:fr-CA**  
  
5.  Ana uygulama derlemeyle aynı bütünleştirilmiş kodda yeni bir uydu derleme barındırmak için yeni bir kültüre özgü klasör oluşturun. French-Canadian için klasör fr-CA olacaktır.  
  
6.  Oluşturulan uydu derlemesini yeni klasöre kopyalayın.  
  
7.  Yeni bir uydu derleme sınamak için uygulamanızın çalıştırılacağı kültür değiştirmeniz gerekir. Bunu iki yoldan biriyle yapabilirsiniz:  
  
    -   İşletim sisteminizin bölgesel ayarları değiştirin (**Başlat** &#124; **Denetim Masası** &#124; **bölge ve Dil Seçenekleri**).  
  
    -   Uygulamanızda App.xaml.cs için aşağıdaki kodu ekleyin:  
  
   [!code-xaml[LocBamlChangeCultureSnippets#LocBamlChangeCultureMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml#locbamlchangeculturemarkup)]
   [!code-csharp[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml.cs#locbamlchangeculturecodebehind)]
   [!code-vb[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/VisualBasic/Application.xaml.vb#locbamlchangeculturecodebehind)]  
  
<a name="Some_Tips_for_Using_LocBaml"></a>   
## <a name="some-tips-for-using-locbaml"></a>LocBaml kullanımına yönelik bazı ipuçları  
  
-   Özel denetimleri tanımlayan tüm bağımlı derlemeleri LocBaml yerel dizine kopyaladığınız veya GAC içine yüklenmelidir. Okuduğunda API yerelleştirme bağımlı derlemelere erişimi olması gerektiği için bu gereklidir [!INCLUDE[TLA#tla_baml](../../../../includes/tlasharptla-baml-md.md)].  
  
-   Ana derleme kaydolduysanız sırayla yüklü olması için oluşturulan kaynak DLL de imzalanması gerekir.  
  
-   Yerelleştirilmiş kaynak sürümü DLL ana bütünleştirilmiş kod ile eşitlenmesi gerekir.  
  
<a name="Whats_Next"></a>   
## <a name="whats-next"></a>Sırada ne var?  
 Şimdi LocBaml aracının nasıl kullanılacağını ilgili temel bilgilere sahip olmalıdır.  Uıd'leri içeren bir dosyayı olun olması gerekir. LocBaml aracını kullanarak, yerelleştirilebilir içerik ayıklamak için dosyayı ayrıştırabiliyor olmalıdır ve içeriği çevrilen sonra oluşturabilir olmalıdır bir. çevrilmiş içeriği birleştiren resources.dll dosyası. Bu konu, olası her ayrıntıyı içermez, ancak şu anda uygulamalarınızı yerelleştirme için LocBaml kullanmak için gerekli bilgiye sahipsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WPF için Genelleştirme](../../../../docs/framework/wpf/advanced/globalization-for-wpf.md)  
 [Otomatik Düzen Kullanımına Genel Bakış](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)
