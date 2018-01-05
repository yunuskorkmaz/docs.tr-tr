---
title: "Mürekkep ile Çalışmaya Başlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- procedural code in lieu of XAML [WPF]
- gradient brush [WPF], animating colors of
- XAML [WPF], procedural code in lieu of
- animation [WPF], gradient brush colors
- brushes [WPF], animating colors of
ms.assetid: 760332dd-594a-475d-865b-01659db8cab7
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c977e8a4a23f9739541cf28d9e34ad9e8db1daf0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="getting-started-with-ink"></a>Mürekkep ile Çalışmaya Başlama
Dijital Mürekkep uygulamalarınıza her zamankinden daha kolay olur. Mürekkep gelişen corollary içinde tam tümleştirmeyi programlamayı COM ve Windows Forms yöntemine olmaktan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Ayrı SDK veya çalışma zamanı kitaplıkları yüklemeniz gerekmez.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Aşağıdaki örnekler kullanmak için önce Microsoft Visual Studio 2005 yüklemeniz gerekir ve [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)]. Uygulamaları yazmak nasıl anlamanız gerekir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. İle çalışmaya başlama hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], bkz: [gözden geçirme: ilk WPF Masaüstü Uygulamam](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).  
  
## <a name="quick-start"></a>Hızlı Başlangıç  
 Bu bölüm, basit bir yazmanıza yardımcı olur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Mürekkep toplayan uygulama.  
  
 Zaten yapmadıysanız, Microsoft Visual Studio 2005 yükleyin ve [!INCLUDE[TLA#tla_winfxsdk](../../../../includes/tlasharptla-winfxsdk-md.md)]. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]uygulamalar genellikle derlenmelidir bunları görüntüleyebilmeniz bunlar tamamen oluşur olsa bile [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Ancak, [!INCLUDE[TLA#tla_winfxsdk](../../../../includes/tlasharptla-winfxsdk-md.md)] uygulama hızlandırmak için tasarlanmış bir uygulama olan, XamlPad'i içeren bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]-UI tabanlı. Bu uygulamayı görüntülemek ve bu belgedeki ilk birkaç örneği ile tamir etmek için kullanabilirsiniz. Oluşturma işlemi derlenmiş uygulamalardan [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bu belgenin sonraki bölümlerinde ele alınmaktadır.  
  
 XamlPad'i başlatmak için tıklatın **Başlat** menüsündeki **tüm programlar**, işaret **Microsoft Winndows SDK**, işaret **Araçları**ve'ı tıklatın **XAMLPad**. İşleme bölmesinde XAMLPad kod bölmesinde yazılan XAML kodu oluşturur. XAML kodunu düzenleyebilirsiniz ve değişiklikler hemen işleme bölmesinde görünür.  
  
#### <a name="got-ink"></a>Mürekkep var mı?  
 İlk başlatmak için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Mürekkep destekleyen uygulama:  
  
1.  Microsoft Visual Studio 2005 açın  
  
2.  Yeni bir **Windows uygulaması (WPF)**  
  
3.  Tür `<InkCanvas/>` arasında `<Grid>` etiketleri  
  
4.  Tuşuna **F5** hata ayıklayıcı uygulamanızda başlatmak için  
  
5.  Kalem veya fare kullanarak yazma **Merhaba Dünya** penceresinde  
  
 "Hello world" uygulama yalnızca 12 tuş mürekkep denk yazdıktan!  
  
#### <a name="spice-up-your-application"></a>Uygulamanızı renklendirin  
 Bazı özellikleri avantajlarından atalım [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Açılış arasındaki her şeyi değiştirin \<penceresi > ve kapatma \</Window > gradyan fırçası arka plan içindekine yüzeyinizi almak için aşağıdaki biçimlendirme etiketleriyle.  
  
 [!code-xaml[DigitalInkTopics#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml#1)]  
[!code-xaml[DigitalInkTopics#1a](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml#1a)]  
  
#### <a name="using-animation"></a>Animasyon kullanma  
 Fun için gradyan fırçası renkleri şimdi animasyon. Aşağıdakileri ekleyin [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kapatma sonra `</InkCanvas>` etiketi ancak kapatmadan önce `</Page>` etiketi.  
  
 [!code-xaml[DigitalInkTopics#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml#2)]  
  
#### <a name="adding-some-code-behind-the-xaml"></a>XAML arkasına bazı kod ekleme  
 XAML kullanıcı arabirimi tasarlamak çok kolay olmasını sağlarken olayları işlemek üzere kod eklemek herhangi bir gerçek uygulama gerekir. Fare gelen yanıt sağ tıklatma olarak mürekkep yakınlaştırır basit bir örnek aşağıda verilmiştir:  
  
 Ayarlama `MouseRightButtonUp` işleyicisinde, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]:  
  
 [!code-xaml[DigitalInkTopics#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#3)]  
  
 Visual Studio'nun Çözüm Gezgini'nde, Windows1.XAML'i genişletin ve arka plan kod dosyası, Window1.xaml.cs veya Visual Basic kullanıyorsanız Window1.xaml.vb'yi açın. Aşağıdaki olay işleyici kodu ekleyin:  
  
 [!code-csharp[DigitalInkTopics#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml.cs#4)]
 [!code-vb[DigitalInkTopics#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window2.xaml.vb#4)]  
  
 Artık, uygulamanızı çalıştırın. Bazı mürekkep ekleyin ve ardından fareyle sağ tıklayın veya ve tutma eşdeğer kalem ile gerçekleştirin.  
  
#### <a name="using-procedural-code-instead-of-xaml"></a>XAML yerine yordam kodu kullanma  
 Tüm erişebilir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özelliklerine yordamsal koddan. "Hello mürekkep World" uygulaması için işte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] herhangi kullanmayan [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] hiç. Visual Studio'da boş bir konsol uygulamasına aşağıdaki kodu yapıştırın. PresentationCore, PresentationFramework ve WindowsBase derlemelerine başvurular ekleyin ve tuşlarına basarak uygulamayı derlediğinizde **F5**:  
  
 [!code-csharp[InkCanvasConsoleApp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasConsoleApp/CSharp/Program.cs#1)]
 [!code-vb[InkCanvasConsoleApp#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InkCanvasConsoleApp/VisualBasic/Module1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Dijital Mürekkep](../../../../docs/framework/wpf/advanced/digital-ink.md)  
 [Mürekkep Toplama](../../../../docs/framework/wpf/advanced/collecting-ink.md)  
 [El Yazısı Tanıma](../../../../docs/framework/wpf/advanced/handwriting-recognition.md)  
 [Mürekkep Depolama](../../../../docs/framework/wpf/advanced/storing-ink.md)
