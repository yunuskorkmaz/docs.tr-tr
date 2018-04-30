---
title: "Mürekkep Nesnesi Modeli: Windows Forms ve WPF'ye Karşı COM"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-wpf
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- enabling ink [WPF]
- InkCanvas control [WPF]
- ink object model [WPF]
- tablet pen [WPF], events [WPF]
- ink [WPF], enabling
- events [WPF], tablet pen
ms.assetid: 577835be-b145-4226-8570-1d309e9b3901
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 06a2c2049ec7fe7046bd6dae2711fe8e46592fcf
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="the-ink-object-model-windows-forms-and-com-versus-wpf"></a>Mürekkep Nesnesi Modeli: Windows Forms ve WPF'ye Karşı COM

Dijital Mürekkep desteği temelde üç platformları vardır: Tablet PC Windows Forms platform, Tablet PC COM ve Windows Presentation Foundation (WPF) platformunu.  Benzer bir nesne modeli, ancak nesne modeli için Windows Forms ve COM platformları paylaşım [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] platform önemli ölçüde farklıdır.  Bu konuda, böylece bir nesne modelini kullanarak çalıştıktan geliştiriciler diğer daha iyi anlayabilirsiniz en üst düzey farklılıklar açıklanmaktadır.  
  
## <a name="enabling-ink-in-an-application"></a>Bir uygulamada mürekkep etkinleştirme  
 Tüm üç platformlar nesneleri ve tablet kalem girişi almak bir uygulamayı etkinleştir denetim birlikte.  COM platformları ve Windows Forms ile birlikte gelen [Microsoft.Ink.InkPicture](https://msdn.microsoft.com/library/aa514604.aspx), [Microsoft.Ink.InkEdit](https://msdn.microsoft.com/library/ms835842.aspx), [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/ms833057.aspx) ve [ Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/ms836493.aspx) sınıfları.  [Microsoft.Ink.InkPicture](https://msdn.microsoft.com/library/aa514604.aspx) ve [Microsoft.Ink.InkEdit](https://msdn.microsoft.com/library/ms835842.aspx) ekleyebileceğiniz denetimler mürekkep toplamak için bir uygulama.  [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/ms833057.aspx) ve [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/ms836493.aspx) mürekkep etkinleştir windows ve özel denetimler için varolan bir pencere eklenir.  
  
 WPF platform içeren <xref:System.Windows.Controls.InkCanvas> denetim.  Ekleyebileceğiniz bir <xref:System.Windows.Controls.InkCanvas> uygulamanıza ve mürekkep toplanmasını hemen başlayın. İle <xref:System.Windows.Controls.InkCanvas>, kullanıcı kopyalayın, seçebilir ve mürekkep yeniden boyutlandırın.  Diğer denetimler ekleyebileceğiniz <xref:System.Windows.Controls.InkCanvas>, ve kullanıcının bu denetimleri çok el yazısı.  Mürekkep etkin bir özel denetim ekleyerek oluşturabileceğiniz bir <xref:System.Windows.Controls.InkPresenter> ve kendi kalem noktalarını toplamak için.  
  
 Aşağıdaki tabloda bir uygulamada mürekkep etkinleştirme hakkında daha fazla bilgi edinmek nereye listelenmektedir:  
  
|Bunu yapmak için...|WPF platformunda...|Windows Forms/COM platformlarında...|  
|-----------------|--------------------------|------------------------------------------|  
|Uygulama denetimi mürekkep etkinleştirilmiş ekleme|Bkz: [mürekkep ile çalışmaya başlama](../../../../docs/framework/wpf/advanced/getting-started-with-ink.md).|Bkz: [otomatik talep örnek Form](http://msdn.microsoft.com/bec4333a-62ca-4254-a39b-04bc2c556992)|  
|Özel denetim üzerinde mürekkep etkinleştir|Bkz: [mürekkep oluşturma giriş denetim](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md).|Bkz: [mürekkep Pano örnek](http://msdn.microsoft.com/a0c42f1c-543d-44f8-83d9-fe810de410ff).|  
  
## <a name="ink-data"></a>Mürekkep verileri  
 Windows Forms ve COM platformlarda [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/ms836493.aspx), [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/ms833057.aspx), [Microsoft.Ink.InkEdit](https://msdn.microsoft.com/library/ms835842.aspx), ve [ Microsoft.Ink.InkPicture](https://msdn.microsoft.com/library/aa514604.aspx) her sunmaya bir [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx?displayProperty=nameWithType) nesnesi. [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx) nesnesi bir veya daha fazla bilgi için verileri içeren [Microsoft.Ink.Stroke](https://msdn.microsoft.com/library/ms827842.aspx?displayProperty=nameWithType) nesneleri ve ortak yöntemleri ve özellikleri yönetmek ve bu vuruşları işlemek için kullanıma sunar.  [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx) nesnesi yönetir içeriyor; vuruşları ömrü [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx) nesnesi oluşturur ve sahip olduğu vuruşları siler.  Her [Microsoft.Ink.Stroke](https://msdn.microsoft.com/library/ms827842.aspx) üst içinde benzersiz bir tanımlayıcı sahip [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx) nesnesi.  
  
 WPF platformunda <xref:System.Windows.Ink.Stroke?displayProperty=nameWithType> sınıfı sahibi ve kendi ömrü yönetir. Bir grup <xref:System.Windows.Ink.Stroke> nesneleri toplanmasını birlikte içinde bir <xref:System.Windows.Ink.StrokeCollection>, isabet sınama, silme, dönüştürme ve mürekkep seri hale getirme yöntemleri ortak mürekkep için veri yönetimi işlemleri gibi sağlar. A <xref:System.Windows.Ink.Stroke> sıfır, bir veya daha fazla ait <xref:System.Windows.Ink.StrokeCollection> nesneleri istediği zaman verin.  Sahip olmak yerine bir [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx?displayProperty=nameWithType) nesnesi <xref:System.Windows.Controls.InkCanvas> ve <xref:System.Windows.Controls.InkPresenter> içeren bir <xref:System.Windows.Ink.StrokeCollection?displayProperty=nameWithType>.  
  
 Aşağıdaki çizimler çiftinin mürekkep veri nesne modelleri karşılaştırır.  Windows Forms ve COM platformlarda [Microsoft.Ink.Ink](https://msdn.microsoft.com/library/aa515768.aspx?displayProperty=nameWithType) nesne ömrü kısıtlar [Microsoft.Ink.Stroke](https://msdn.microsoft.com/library/ms827842.aspx?displayProperty=nameWithType) nesneleri ve tek tek vuruşları ait kalem paketler.  İki veya daha fazla vuruşları aynı başvuru [Microsoft.Ink.DrawingAttributes](https://msdn.microsoft.com/library/ms837931.aspx?displayProperty=nameWithType) , aşağıdaki çizimde gösterildiği gibi nesne.  
  
 ![COM için mürekkep nesne modelinin diyagramı&#47;Winforms. ] (../../../../docs/framework/wpf/advanced/media/ink-inkownsstrokes.png "Ink_InkOwnsStrokes")  
  
 Üzerinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], her <xref:System.Windows.Ink.Stroke?displayProperty=nameWithType> bir şey bir referansı olduğu sürece, mevcut bir ortak dil çalışma zamanı nesnesi.  Her <xref:System.Windows.Ink.Stroke> başvurular bir <xref:System.Windows.Input.StylusPointCollection> ve <xref:System.Windows.Ink.DrawingAttributes?displayProperty=nameWithType> de ortak dil çalışma zamanı nesneleri olan nesne.  
  
 ![WPF için mürekkep nesne modelinin diyagramı. ] (../../../../docs/framework/wpf/advanced/media/ink-wpfinkobjectmodel.png "Ink_WPFInkObjectModel")  
  
 Aşağıdaki tablo üzerinde bazı yaygın görevlerin nasıl karşılaştırır [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] platform ve Windows Forms ve COM platformlar.  
  
|Görev|Windows Presentation Foundation|Windows Forms ve COM|  
|----------|-------------------------------------|---------------------------|  
|Mürekkep Kaydet|<xref:System.Windows.Ink.StrokeCollection.Save%2A>|[Microsoft.Ink.Ink.Save](https://technet.microsoft.com/library/security/microsoft.ink.ink.save(v=vs.90))|  
|Yük mürekkep|Oluşturma bir <xref:System.Windows.Ink.StrokeCollection> ile <xref:System.Windows.Ink.StrokeCollection.%23ctor%2A> Oluşturucusu.|[Microsoft.Ink.Ink.Load](https://msdn.microsoft.com/library/microsoft.ink.ink.load(v=vs.90).aspx)|  
|İsabet testi|<xref:System.Windows.Ink.StrokeCollection.HitTest%2A>|[Microsoft.Ink.Ink.HitTest](https://msdn.microsoft.com/library/aa515934.aspx)|  
|Mürekkep kopyalayın|<xref:System.Windows.Controls.InkCanvas.CopySelection%2A>|[Microsoft.Ink.Ink.ClipboardCopy](https://msdn.microsoft.com/library/microsoft.ink.ink.clipboardcopy(v=vs.100).aspx)|  
|Mürekkep Yapıştır|<xref:System.Windows.Controls.InkCanvas.Paste%2A>|[Microsoft.Ink.Ink.ClipboardPaste](https://msdn.microsoft.com/library/microsoft.ink.ink.clipboardpaste(v=vs.100).aspx)|  
|Özel özellikleri vuruş topluluğunu erişim|<xref:System.Windows.Ink.StrokeCollection.AddPropertyData%2A> (Özellikler dahili olarak depolanır ve aracılığıyla erişilen <xref:System.Windows.Ink.StrokeCollection.AddPropertyData%2A>, <xref:System.Windows.Ink.StrokeCollection.RemovePropertyData%2A>, ve <xref:System.Windows.Ink.StrokeCollection.ContainsPropertyData%2A>)|Kullanım [Microsoft.Ink.Ink.ExtendedProperties](https://msdn.microsoft.com/library/microsoft.ink.ink.extendedproperties(v=vs.100).aspx)|  
  
### <a name="sharing-ink-between-platforms"></a>Platformlar arasındaki mürekkep paylaşımı  
 Platformlar mürekkep verileri için farklı nesne modellerini sahip olsa da, platformlar arasında veri paylaşımı çok kolaydır. Aşağıdaki örnekler, bir Windows Forms uygulamasından mürekkep kaydedin ve bir Windows Presentation Foundation uygulamasına mürekkep yükleyin.  
  
 [!code-csharp[WinFormWPFInk#UsingWinforms](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwinforms)]
 [!code-vb[WinFormWPFInk#UsingWinforms](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwinforms)]  
[!code-csharp[WinFormWPFInk#SaveWinforms](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#savewinforms)]
[!code-vb[WinFormWPFInk#SaveWinforms](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#savewinforms)]  
  
 [!code-csharp[WinFormWPFInk#UsingWPF](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwpf)]
 [!code-vb[WinFormWPFInk#UsingWPF](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwpf)]  
[!code-csharp[WinFormWPFInk#LoadWPF](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#loadwpf)]
[!code-vb[WinFormWPFInk#LoadWPF](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#loadwpf)]  
  
 Aşağıdaki örnekler, bir Windows Presentation Foundation uygulamasından mürekkep kaydedin ve bir Windows Forms uygulamasına mürekkep yükleyin.  
  
 [!code-csharp[WinFormWPFInk#UsingWPF](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwpf)]
 [!code-vb[WinFormWPFInk#UsingWPF](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwpf)]  
[!code-csharp[WinFormWPFInk#SaveWPF](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#savewpf)]
[!code-vb[WinFormWPFInk#SaveWPF](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#savewpf)]  
  
 [!code-csharp[WinFormWPFInk#UsingWinforms](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwinforms)]
 [!code-vb[WinFormWPFInk#UsingWinforms](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwinforms)]  
[!code-csharp[WinFormWPFInk#LoadWinforms](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#loadwinforms)]
[!code-vb[WinFormWPFInk#LoadWinforms](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#loadwinforms)]
## <a name="events-from-the-tablet-pen"></a>Tablet kalem olayları  
 [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/ms833057.aspx), [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/ms836493.aspx), ve [Microsoft.Ink.InkPicture](https://msdn.microsoft.com/library/aa514604.aspx) Windows Forms ve COM olayları platformları almak zaman kullanıcı girdi veri kalem.  [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/ms833057.aspx) veya [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/ms836493.aspx) bir pencere veya bir denetime bağlı ve tablet giriş verisi tarafından oluşturulan olaylara abone olabilirsiniz.  Bu olaylar oluştuğu iş parçacığı olaylar Kalem, fare olup oluşturulur bağlıdır veya program aracılığıyla.  Bu olaylar bağlantılı olarak iş parçacığı oluşturma hakkında daha fazla bilgi için bkz: [genel bir iş parçacığı oluşturma hakkında önemli noktalar](http://msdn.microsoft.com/cf35724f-5f80-4b3e-992a-a9d5ea99aae9) ve [iş parçacıkları, bir olay tetikleyin](http://msdn.microsoft.com/d1a5ab9b-d474-4ed7-9aa8-b5bdb771934f).  
  
 Windows Presentation Foundation platformunda <xref:System.Windows.UIElement> sınıfı kalem giriş olaylarını sahiptir. Başka bir deyişle, her denetim kalem olayların tam kümesini gösterir.  Kalem olayları sahip tünel/tırmanmasını olay çiftleri ve uygulama iş parçacığı üzerinde her zaman oluşur.  Daha fazla bilgi için bkz: [yönlendirilmiş olaylara genel bakış](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
 Aşağıdaki diyagramda gösterildiği kalem olaylarını sınıfları için nesne modellerini karşılaştırır. Windows Presentation Foundation nesne modeli yalnızca kabarcıklanma olayları, değil tünel olay ortaklarınıza gösterir.  
  
 ![WPF-Winforms içinde kalem olayları diyagramı. ] (../../../../docs/framework/wpf/advanced/media/ink-stylusevents.png "Ink_StylusEvents")  
  
## <a name="pen-data"></a>Kalem verisi  
 Tüm üç platformlar müdahale ve tablet kalem gelen verileri işlemek için yollar sağlar.  Windows Forms ve COM platformları bu oluşturarak elde edilir bir [Microsoft.StylusInput.RealTimeStylus](https://msdn.microsoft.com/library/microsoft.stylusinput.realtimestylus(v=vs.100).aspx)penceresi veya denetim eklemeyi ve uygulayan bir sınıf oluşturma [ Microsoft.StylusInput.IStylusSyncPlugin](https://msdn.microsoft.com/library/microsoft.stylusinput.istylussyncplugin(v=vs.100).aspx) veya [Microsoft.StylusInput.IStylusAsyncPlugin](https://msdn.microsoft.com/library/microsoft.stylusinput.istylusasyncplugin(v=vs.100).aspx) arabirimi. Eklenti özel ardından eklenti koleksiyonuna eklenen [Microsoft.StylusInput.RealTimeStylus](https://msdn.microsoft.com/library/microsoft.stylusinput.realtimestylus(v=vs.100).aspx). Bu nesne modeli hakkında daha fazla bilgi için bkz: [StylusInput API'ları mimarisi](http://msdn.microsoft.com/88bab0ab-df9f-4813-9a9f-9a137813f0b4).  
  
 Üzerinde [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] platform <xref:System.Windows.UIElement> sınıfı sunar eklentiler için tasarım benzer koleksiyonu [Microsoft.StylusInput.RealTimeStylus](https://msdn.microsoft.com/library/microsoft.stylusinput.realtimestylus(v=vs.100).aspx).  Kalem verilere müdahale için öğesinden devralınan bir sınıf oluşturun <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> ve nesnesine ekleme <xref:System.Windows.UIElement.StylusPlugIns%2A> koleksiyonu <xref:System.Windows.UIElement>. Bu etkileşimi hakkında daha fazla bilgi için bkz: [kalem kesintiye uğratan girişten](../../../../docs/framework/wpf/advanced/intercepting-input-from-the-stylus.md).  
  
 Tüm platformlarda iş parçacığı havuzu kalem olayları aracılığıyla mürekkep verileri alır ve uygulama iş parçacığına gönderir.  COM ve Windows platformları iş parçacığı oluşturma hakkında daha fazla bilgi için bkz: [StylusInput API'leri için iş parçacığı oluşturma konuları](http://msdn.microsoft.com/5d98768a-c60b-4bb0-8640-9bf38254d41f).  Windows Presentation yazılımı iş parçacığı oluşturma hakkında daha fazla bilgi için bkz: [mürekkep iş parçacığı modeli](../../../../docs/framework/wpf/advanced/the-ink-threading-model.md).  
  
 Aşağıdaki çizimde kalem iş parçacığı havuzu kalem verilerini alan sınıfları için nesne modellerini karşılaştırır.  
  
 ![StylusPlugIn modeli WPF vs Winforms diyagramı. ] (../../../../docs/framework/wpf/advanced/media/ink-stylusplugins.png "Ink_StylusPlugins")
