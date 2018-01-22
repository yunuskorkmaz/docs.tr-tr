---
title: "İzlenecek yol: Tasarım Zamanında Özel Windows Formları Denetimleri Hatalarını Ayıklama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- debugging [Visual Studio], walkthroughs
- custom controls [Windows Forms], walkthroughs
- visual editors
- debugging [Visual Studio], Windows Forms
- custom controls [Windows Forms], debugging
- designers
- controls [Windows Forms], debugging
- walkthroughs [Windows Forms], debugging
- design-time debugging
ms.assetid: 1fd83ccd-3798-42fc-85a3-6cba99467387
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4dfdc102a5aeb2e3eaccde28a8ce57a1878141e4
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-debugging-custom-windows-forms-controls-at-design-time"></a>İzlenecek yol: Tasarım Zamanında Özel Windows Formları Denetimleri Hatalarını Ayıklama
Özel bir denetim oluşturduğunuzda, genellikle bu tasarım zamanı davranışını hata ayıklamak gerekli bulacaksınız. Özel denetim için özel bir tasarımcı yazıyorsanız bu özellikle doğrudur. Ayrıntılar için bkz [izlenecek yol: bir Windows Forms denetimi, geçen avantajı, Visual Studio tasarım-zamanı özellikleri oluşturma](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md).  
  
 Diğer .NET Framework sınıfları debug gibi özel denetimler Visual Studio kullanarak ayıklayabilirsiniz. Özel denetimin kodunu çalıştıran Visual Studio ayrı bir örneğini hata ayıklama farktır  
  
 Bu örneklerde gösterilen görevler aşağıdakileri içerir:  
  
-   Özel denetim barındırmak için bir Windows Forms projesi oluşturma  
  
-   Bir denetim kitaplığı projesi oluşturma  
  
-   Bir özellik için özel denetim ekleme  
  
-   Ana bilgisayar formuna özel denetim ekleme  
  
-   Tasarım zamanı hata ayıklama için proje ayarlama  
  
-   Özel Denetim tasarım zamanında hata ayıklama  
  
 İşiniz bittiğinde, özel bir denetim tasarım zamanı davranışını hata ayıklama için gereken görevleri anlaşılması gerekir.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-project"></a>Projeyi Oluşturma  
 İlk adım, uygulama projesi oluşturmaktır. Özel denetim barındıran uygulama oluşturmak için bu proje kullanır.  
  
#### <a name="to-create-the-project"></a>Proje oluşturmak için  
  
-   "DebuggingExample" adlı bir Windows uygulaması projesi oluşturun. Ayrıntılar için bkz [nasıl yapılır: bir Windows uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
## <a name="creating-a-control-library-project"></a>Bir denetim kitaplığı projesi oluşturma  
 Sonraki adım, denetim kitaplığı projesi oluşturun ve özel denetimin ayarlamaktır.  
  
#### <a name="to-create-the-control-library-project"></a>Denetim Kitaplığı projesi oluşturmak için  
  
1.  Ekleme bir **Windows Denetim Kitaplığı** çözüme proje.  
  
2.  Yeni bir ekleme **UserControl** DebugControlLibrary proje öğesi. Ayrıntılar için bkz [NIB: nasıl yapılır: Yeni proje öğeleri Ekle](http://msdn.microsoft.com/library/63d3e16b-de6e-4bb5-a0e3-ecec762201ce). Yeni kaynak dosyası "DebugControl", temel bir ad verin.  
  
3.  Kullanarak **Çözüm Gezgini**, bir taban adı ile kod dosyası tarafından projenin varsayılan denetim silindiğinde "`UserControl1`". Ayrıntılar için bkz [NIB: nasıl yapılır: Kaldır, silme ve dışlama öğeleri](http://msdn.microsoft.com/library/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73).  
  
4.  Çözümü oluşturun.  
  
## <a name="checkpoint"></a>Denetim noktası  
 Bu noktada, içinde özel denetim görmeye olacaktır **araç**.  
  
#### <a name="to-check-your-progress"></a>İlerleme durumunuzu denetlemek için  
  
-   Adlı yeni sekmede Bul **DebugControlLibrary bileşenleri** ve seçmek için tıklatın. Açıldığında, olarak listelenen denetiminizi görürsünüz **DebugControl** yanında varsayılan simgesiyle.  
  
## <a name="adding-a-property-to-your-custom-control"></a>Bir özellik için özel denetim ekleme  
 Tasarım zamanında özel denetiminizin kodu çalıştığını göstermek için bir özellik ekleyin ve özellik uygulayan kodda bir kesme noktası ayarlama.  
  
#### <a name="to-add-a-property-to-your-custom-control"></a>Bir özellik için özel denetim eklemek için  
  
1.  Açık **DebugControl** içinde **Kod düzenleyicisinde**. Aşağıdaki kodu sınıf tanımına ekleyin:  
  
    ```vb  
    Private demoStringValue As String = Nothing  
    <BrowsableAttribute(true)>  
    Public Property DemoString() As String  
  
        Get  
            Return Me.demoStringValue  
        End Get  
  
        Set(ByVal value As String)  
            Me.demoStringValue = value  
        End Set  
  
    End Property  
    ```  
  
    ```csharp  
    private string demoStringValue = null;  
    [Browsable(true)]  
    public string DemoString  
    {  
        get  
        {  
            return this.demoStringValue;  
        }  
        set  
        {  
            demoStringValue = value;  
        }  
    }  
    ```  
  
2.  Çözümü oluşturun.  
  
## <a name="adding-your-custom-control-to-the-host-form"></a>Ana bilgisayar formuna özel denetim ekleme  
 Özel Denetim tasarım zamanı davranışını hata ayıklamak için özel denetim sınıfının bir örneği bir ana bilgisayar formunda yerleştirir.  
  
#### <a name="to-add-your-custom-control-to-the-host-form"></a>Ana bilgisayar formun özel denetim eklemek için  
  
1.  İçinde Form1 "DebuggingExample" projeyi açın **Windows Form Tasarımcısı**.  
  
2.  İçinde **araç**, açık **DebugControlLibrary bileşenleri** sekmesinde ve sürükleyin bir **DebugControl** forma örneği.  
  
3.  Bul `DemoString` özel bir özellik **özellikleri** penceresi. Herhangi bir özellik gibi değerini değiştirebileceğinizi unutmayın. Ayrıca gerektiğini unutmayın `DemoString` özelliği seçildiğinde, özelliğin açıklama dizesi en altında görüntülenen **özellikleri** penceresi.  
  
## <a name="setting-up-the-project-for-design-time-debugging"></a>Tasarım zamanı hata ayıklama için proje ayarlama  
 Özel denetimin tasarım zamanı davranışını hata ayıklamak için özel denetimin kodunu çalıştıran Visual Studio ayrı bir örneğini hata ayıklama.  
  
#### <a name="to-set-up-the-project-for-design-time-debugging"></a>Tasarım zamanı hata ayıklama için proje ayarlamak için  
  
1.  Sağ **DebugControlLibrary** proje **Çözüm Gezgini** seçip **özellikleri**.  
  
2.  İçinde **DebugControlLibrary** özellik sayfasını, select **hata ayıklama** sekmesi.  
  
     İçinde **eylemi Başlat** bölümünde, select **başlangıç dış program**. Size Visual Studio, ayrı bir örneğini hata ayıklama böylece tıklatın üç nokta (![VisualStudioEllipsesButton ekran](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) için Visual Studio IDE gözatmak için düğmeyi. Yürütülebilir dosya adı **devenv.exe**, ve varsayılan konuma geri yüklediyseniz, %programfiles%\Microsoft Visual Studio 9.0\Common7\IDE\devenv.exe yoludur.  
  
3.  İletişim kutusunu kapatmak için **Tamam** 'ı tıklatın.  
  
4.  Sağ **DebugControlLibrary** proje ve seçin **başlangıç projesi olarak ayarla** bu hata ayıklama yapılandırmasını etkinleştirmek için.  
  
## <a name="debugging-your-custom-control-at-design-time"></a>Özel Denetim tasarım zamanında hata ayıklama  
 Şimdi Tasarım modunda çalışırken özel denetim hata ayıklamak hazırsınız. Hata ayıklama oturumu başlattığınızda, Visual Studio yeni bir örneğini oluşturulur ve "DebuggingExample" Çözüm yüklemek için kullanır. İçinde Form1 açtığınızda **Forms Tasarımcısı**, özel denetim örneği oluşturulur ve çalışmaya başlar.  
  
#### <a name="to-debug-your-custom-control-at-design-time"></a>Özel Denetim tasarım zamanında hata ayıklamak için  
  
1.  Açık **DebugControl** kaynak dosyasında **Kod düzenleyicisinde** ve bir kesme noktası yerleştirmek `Set` erişimcisine `DemoString` özelliği.  
  
2.  Hata ayıklama oturumu başlatmak için F5 tuşuna basın. Visual Studio yeni bir örneğini oluşturulduğunu unutmayın. İki yolla örnekleri arasında ayırt edebilirsiniz:  
  
    -   Hata ayıklama örneği sözcüğü bulunan **çalıştıran** kendi başlık çubuğunda  
  
    -   Hata ayıklama örneğinin **Başlat** düğmesini kendi **hata ayıklama** devre dışı araç çubuğu  
  
     Hata ayıklama örneğinde isabetini ayarlanır.  
  
3.  Visual Studio yeni örneğini "DebuggingExample" çözümü açın. Seçerek kolayca çözüm bulabilirsiniz **son projeler** gelen **dosya** menüsü. En son kullanılan dosya "DebuggingExample.sln" çözüm dosyasını listelenir.  
  
4.  Açık olarak Form1 **Forms Tasarımcısı** seçip **DebugControl** denetim.  
  
5.  Değerini değiştirme `DemoString` özelliği. Değişiklik yaparsanız, Visual Studio hata ayıklama örneğini odağı alması ve yürütme, kesme noktasında durur unutmayın. Tek adımlı özelliği erişimcisi ile yapabileceğiniz gibi başka bir kod gerekir.  
  
6.  Hata ayıklama oturumunuz ile işiniz bittiğinde, Visual Studio'nun barındırılan örneği kapatılıyor veya tıklatarak çıkabilirsiniz **durdurma hata ayıklama** hata ayıklama örneğinde düğmesi.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Tasarım zamanında özel denetimler ayıklayabilirsiniz, Visual Studio IDE denetiminizin etkileşim genişletmek için çok sayıda olasılık vardır.  
  
-   Kullanabileceğiniz <xref:System.ComponentModel.Component.DesignMode%2A> özelliği <xref:System.ComponentModel.Component> yalnızca tasarım zamanında yürütülür yazma koduna sınıfı. Ayrıntılar için bkz <xref:System.ComponentModel.Component.DesignMode%2A>.  
  
-   Birkaç öznitelik Tasarımcı özel denetiminizin etkileşim işlemek üzere denetiminizin özellikleri uygulayabilirsiniz. İçinde bu özniteliklerin bulabilirsiniz <xref:System.ComponentModel?displayProperty=nameWithType> ad alanı.  
  
-   Özel denetim için özel bir tasarımcı yazabilirsiniz. Bu size Visual Studio tarafından kullanıma sunulan Genişletilebilir Tasarımcı altyapısını kullanarak tasarım deneyimi üzerinde tam denetim sağlar. Ayrıntılar için bkz [izlenecek yol: bir Windows Forms denetimi, geçen avantajı, Visual Studio tasarım-zamanı özellikleri oluşturma](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: Visual Studio Tasarım-Zamanı Özellikleri'nden Faydalanan Windows Forms Denetimi Oluşturma](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)  
 [Nasıl yapılır: tasarım zamanında hizmetlere erişme](http://msdn.microsoft.com/library/c186c4b6-076c-438d-9ed3-f13da29c8c1f)  
 [Nasıl yapılır: Windows Forms'ta tasarım zamanı desteği erişim](http://msdn.microsoft.com/library/a84f8579-1f47-41b9-ba37-69030b0aff09)
