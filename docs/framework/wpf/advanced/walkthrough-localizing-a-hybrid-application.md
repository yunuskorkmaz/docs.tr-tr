---
title: "İzlenecek yol: Karma Uygulamayı Yerelleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- localization [WPF interoperability]
- hybrid applications [WPF interoperability]
ms.assetid: fbc0c54e-930a-4c13-8e9c-27b83665010a
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2d46ea30a0e6a509d6a6cac6d8686e5f5307f0cb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-localizing-a-hybrid-application"></a>İzlenecek yol: Karma Uygulamayı Yerelleştirme
Bu kılavuz, yerelleştirme gösterilmektedir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğelerinde bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]-karma tabanlı.  
  
 Bu örneklerde gösterilen görevler aşağıdakileri içerir:  
  
-   Oluşturma [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] konak projesi.  
  
-   Yerelleştirilebilir İçerik ekleme.  
  
-   Yerelleştirme etkinleştiriliyor.  
  
-   Kaynak tanımlayıcılar atama.  
  
-   Uydu derlemesi üretmek için LocBaml aracını kullanma.  
  
 Bu örneklerde gösterilen görevlerin tam kod listesi için bkz: [karma uygulama örneği yerelleştirme](http://go.microsoft.com/fwlink/?LinkID=160015).  
  
 İşiniz bittiğinde, yerelleştirilmiş karma uygulamaya sahip olacaksınız.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)].  
  
## <a name="creating-the-windows-forms-host-project"></a>Windows Forms konak projesi oluşturma  
 İlk adım oluşturmaktır [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] uygulama proje ve ekleme bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğesi yerelleştirme içeriğe sahip.  
  
#### <a name="to-create-the-host-project"></a>Konak projesi oluşturmak için  
  
1.  Adlı bir WPF uygulaması projesi oluşturduğunuzda `LocalizingWpfInWf`. Daha fazla bilgi için bkz: [nasıl yapılır: bir Windows uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  Ekleme bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> adlı öğe `SimpleControl` projeye.  
  
3.  Kullanım <xref:System.Windows.Forms.Integration.ElementHost> yerleştirmek için denetim bir `SimpleControl` öğesi form üzerinde. Daha fazla bilgi için bkz: [izlenecek yol: Windows Forms'ta 3-b WPF bileşik denetim barındırma](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md).  
  
## <a name="adding-localizable-content"></a>Yerelleştirilebilir İçerik ekleme  
 Sonra ekleyeceksiniz bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] etiket denetimini ve ayarlayın [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğenin içeriğini yerelleştirilebilir dize.  
  
#### <a name="to-add-localizable-content"></a>Yerelleştirilebilir İçerik eklemek için  
  
1.  Çözüm Gezgini'nde çift tıklayarak **SimpleControl.XAML'e** içinde açmak için [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].  
  
2.  İçeriğini ayarlayın <xref:System.Windows.Controls.Button> aşağıdaki kodu kullanarak denetim.  
  
     [!code-xaml[LocalizingWpfInWf#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl0.xaml#10)]  
  
3.  Çözüm Gezgini'nde çift tıklayarak **Form1** Windows Forms Tasarımcısı'nda açmak için.  
  
4.  Araç kutusunu açın ve çift **etiket** forma etiket denetimi eklemek için. Değerini kendi <xref:System.Windows.Forms.Control.Text%2A> özelliğine `"Hello"`.  
  
5.  Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.  
  
     Her iki `SimpleControl` öğesini ve etiket denetimi görüntüleme metni **"Merhaba"**.  
  
## <a name="enabling-localization"></a>Yerelleştirme etkinleştirme  
 Windows Form Tasarımcısı yardımcı derlemede yerelleştirme etkinleştirmek için ayarlar sağlar.  
  
#### <a name="to-enable-localization"></a>Yerelleştirme etkinleştirmek için  
  
1.  Çözüm Gezgini'nde çift tıklayarak **Form1.cs** Windows Forms Tasarımcısı'nda açmak için.  
  
2.  Özellikler penceresinde formun değerini **yerelleştirilebilir** özelliğine `true`.  
  
3.  Özellikler penceresinde değerini **dil** özelliğine **İspanyolca (İspanya)**.  
  
4.  Windows Forms Tasarımcısı'nda etiket denetimi seçin.  
  
5.  Özellikler penceresinde değerini <xref:System.Windows.Forms.Control.Text%2A> özelliğine `"Hola"`.  
  
     Form1.es-ES.resx adlı yeni bir kaynak dosyası projeye eklenir.  
  
6.  Çözüm Gezgini'nde sağ **Form1.cs** tıklatıp **görünümü kodu** Kod düzenleyicisinde açın.  
  
7.  Aşağıdaki kodu kopyalayın `Form1` çağrısının öncesine Oluşturucusu `InitializeComponent`.  
  
     [!code-csharp[LocalizingWpfInWf#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/Form1.cs#2)]  
  
8.  Çözüm Gezgini'nde sağ **LocalizingWpfInWf** tıklatıp **projeyi**.  
  
     Proje adı etiketli **(kullanılamaz)**.  
  
9. Sağ **LocalizingWpfInWf**, tıklatıp **LocalizingWpfInWf.csproj'yi**.  
  
     Proje dosyası Kod Düzenleyicisi'nde açar.  
  
10. Aşağıdaki satırı ilk kopyalama `PropertyGroup` proje dosyasında.  
  
    ```xml  
    <UICulture>en-US</UICulture>   
    ```  
  
11. Proje dosyasını kaydedin ve kapatın.  
  
12. Çözüm Gezgini'nde sağ **LocalizingWpfInWf** tıklatıp **projeyi yeniden yükle**.  
  
## <a name="assigning-resource-identifiers"></a>Kaynak tanımlayıcılar atama  
 Kaynak tanımlayıcılar kullanarak kaynak derlemelerine yerelleştirilebilir içeriğinizi eşleyebilirsiniz. Belirttiğinizde kaynak tanımlayıcılarını MsBuild.exe uygulaması otomatik olarak atar. `updateuid` seçeneği.  
  
#### <a name="to-assign-resource-identifiers"></a>Kaynak tanımlayıcılar atamak için  
  
1.  Başlat menüsünden açmak [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] komut istemi.  
  
2.  Kaynak tanımlayıcılar yerelleştirilebilir içeriğinize atamak için aşağıdaki komutu kullanın.  
  
    ```  
    msbuild /t:updateuid LocalizingWpfInWf.csproj  
    ```  
  
3.  Çözüm Gezgini'nde çift tıklayarak **SimpleControl.XAML'e** Kod düzenleyicisinde açın. Göreceksiniz `msbuild` komutu ekledi `Uid` özniteliği için tüm öğeleri. Bu, kaynak tanımlayıcılarının atanması yoluyla yerelleştirme kolaylaştırır.  
  
     [!code-xaml[LocalizingWpfInWf#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl.xaml#20)]  
  
4.  Çözümü derlemek için F6 tuşuna basın.  
  
## <a name="using-locbaml-to-produce-a-satellite-assembly"></a>Uydu derlemesi üretmek için LocBaml Kullanma  
 Yerelleştirilmiş içeriğiniz bir kaynak yalnızca içinde depolanan *uydu derleme*. İçin yerelleştirilmiş bir derleme üretmek için komut satırı aracı LocBaml.exe'yi kullanın, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içeriği.  
  
#### <a name="to-produce-a-satellite-assembly"></a>Uydu derlemesi üretmek için  
  
1.  LocBaml.exe'yi projenizin obj\Debug klasörüne kopyalayın. Daha fazla bilgi için bkz: [uygulama yerelleştirme](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md).  
  
2.  Komut İstemi penceresinde, geçici bir dosyaya kaynak dizeleri ayıklamak için aşağıdaki komutu kullanın.  
  
    ```  
    LocBaml /parse LocalizingWpfInWf.g.en-US.resources /out:temp.csv  
    ```  
  
3.  Temp.csv dosyasını açın [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] veya başka bir metin düzenleyici. Dize Değiştir `"Hello"` kendi İspanyolca çevirisi ile `"Hola"`.  
  
4.  Temp.csv dosyasını kaydedin.  
  
5.  Yerelleştirilmiş kaynak dosyasını oluşturmak için aşağıdaki komutu kullanın.  
  
    ```  
    LocBaml /generate /trans:temp.csv LocalizingWpfInWf.g.en-US.resources /out:. /cul:es-ES  
    ```  
  
     LocalizingWpfInWf.g.es-ES.resources dosyası obj\Debug klasöründe oluşturulur.  
  
6.  Yerelleştirilmiş uydu derlemesini oluşturmak için aşağıdaki komutu kullanın.  
  
    ```  
    Al.exe /out:LocalizingWpfInWf.resources.dll /culture:es-ES /embed:LocalizingWpfInWf.Form1.es-ES.resources /embed:LocalizingWpfInWf.g.es-ES.resources  
    ```  
  
     LocalizingWpfInWf.resources.dll dosyası obj\Debug klasöründe oluşturulur.  
  
7.  LocalizingWpfInWf.resources.dll dosyasını projenin bin\Debug\es-ES klasörüne kopyalayın. Varolan dosyayı değiştirmek.  
  
8.  Projenizin klasörüne içinde bulunan LocalizingWpfInWf.exe çalıştırın. Uygulamayı yeniden değil veya uydu derlemesi üzerine yazılır.  
  
     Uygulama İngilizce dizelerin yerine yerelleştirilmiş dizeleri gösterir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Bir Uygulamayı Yerelleştirme](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md)  
 [İzlenecek yol: Windows Formları yerelleştirme](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5)  
 [WPF Tasarımcısı](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)
