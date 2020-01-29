---
title: Dijital mürekkep-Windows Forms ve COM ile WPF karşılaştırması
titleSuffix: ''
ms.date: 03/30/2017
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
ms.openlocfilehash: 4a183bba2c5cfb2d12a9cf435ae1f92b4cf63948
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737292"
---
# <a name="the-ink-object-model-windows-forms-and-com-versus-wpf"></a>Mürekkep Nesnesi Modeli: Windows Forms ve WPF'ye Karşı COM

Dijital mürekkebi destekleyen temel üç platform vardır: Tablet PC Windows Forms platformu, Tablet PC COM platformu ve Windows Presentation Foundation (WPF) platformu.  Windows Forms ve COM platformları benzer bir nesne modeli paylaşır, ancak WPF platformunun nesne modeli önemli ölçüde farklıdır.  Bu konu, bir nesne modeliyle çalışan geliştiricilerin diğerini daha iyi anlayabilmesi için üst düzey farklılıkları ele almaktadır.  
  
## <a name="enabling-ink-in-an-application"></a>Bir uygulamada mürekkep sağlama  
 Üç platformun hepsi, bir uygulamanın tablet kalemden giriş almasını sağlayan nesneler ve denetimler sağlar.  Windows Forms ve COM platformları [Microsoft. Ink. InkPicture](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583740(v=vs.90)), [Microsoft. Ink. ınkedıt](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552265(v=vs.90)), [Microsoft. Ink. InkOverlay](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552322(v=vs.90)) ve [Microsoft. ink. InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90)) sınıflarıyla birlikte teslim.  [Microsoft. Ink. InkPicture](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583740(v=vs.90)) ve [Microsoft. Ink. ınkedıt](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552265(v=vs.90)) , mürekkep toplamak için bir uygulamaya ekleyebileceğiniz denetimlerdir.  [Microsoft. Ink. InkOverlay](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552322(v=vs.90)) ve [Microsoft. Ink. InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90)) , mevcut bir pencereye mürekkeple eklenebilir-Windows ve özel denetimleri etkinleştirir.  
  
 WPF platformu <xref:System.Windows.Controls.InkCanvas> denetimini içerir.  Uygulamanıza bir <xref:System.Windows.Controls.InkCanvas> ekleyebilir ve hemen mürekkep toplamaya başlayabilirsiniz. <xref:System.Windows.Controls.InkCanvas>, Kullanıcı mürekkebi kopyalayabilir, seçebilir ve yeniden boyutlandırabilirler.  <xref:System.Windows.Controls.InkCanvas>başka denetimler ekleyebilirsiniz ve Kullanıcı da bu denetimlerin üzerine el yazısı ekleyebilir.  Bir <xref:System.Windows.Controls.InkPresenter> ekleyip ekran kalemi noktalarını toplayarak mürekkep etkin bir özel denetim oluşturabilirsiniz.  
  
 Aşağıdaki tabloda, bir uygulamada mürekkep etkinleştirme hakkında daha fazla bilgi verilmektedir:  
  
|Bunu yapmak için...|WPF platformunda...|Windows Forms/COM platformlarında...|  
|-----------------|--------------------------|------------------------------------------|  
|Uygulamaya mürekkep etkin bir denetim ekleme|Bkz. [mürekkeple çalışmaya](getting-started-with-ink.md)başlama.|Bkz. [otomatik talep formu örneği](/windows/desktop/tablet/auto-claims-form-sample)|  
|Özel denetimde mürekkebi etkinleştirme|Bkz. [mürekkep girişi denetimi oluşturma](creating-an-ink-input-control.md).|Bkz. [mürekkep panosu örneği](/windows/desktop/tablet/ink-clipboard-sample).|  
  
## <a name="ink-data"></a>Mürekkep verileri  
 Windows Forms ve COM platformlarında [Microsoft. Ink. InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90)), [Microsoft. Ink. InkOverlay](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552322(v=vs.90)), [Microsoft. ink. ınkedıt](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552265(v=vs.90))ve [Microsoft. Ink. InkPicture](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583740(v=vs.90)) her biri bir [Microsoft. Ink. ink](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583670(v=vs.90)) nesnesi sunar. [Microsoft. Ink. ink](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583670(v=vs.90)) nesnesi bir veya daha fazla [Microsoft. ink. Stroke](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552692(v=vs.90)) nesnesine ilişkin verileri içerir ve bu konturları yönetmek ve işlemek için ortak yöntemleri ve özellikleri sunar.  [Microsoft. Ink. ink](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583670(v=vs.90)) nesnesi, içerdiği vuruşların ömrünü yönetir; [Microsoft. Ink. ink](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583670(v=vs.90)) nesnesi, sahip olduğu konturları oluşturur ve siler.  Her [Microsoft. Ink. Stroke](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552692(v=vs.90)) , üst [Microsoft. Ink. ink](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583670(v=vs.90)) nesnesi içinde benzersiz olan bir tanımlayıcıya sahiptir.  
  
 WPF platformunda <xref:System.Windows.Ink.Stroke?displayProperty=nameWithType> sınıfı kendi ömrünü sahiptir ve yönetir. Bir grup <xref:System.Windows.Ink.Stroke> nesneleri, isabet testi, silme, dönüştürme ve seri hale getirme gibi ortak mürekkep veri yönetimi işlemlerine yönelik yöntemler sağlayan bir <xref:System.Windows.Ink.StrokeCollection>birlikte toplanabilir. <xref:System.Windows.Ink.Stroke> herhangi bir zamanda sıfır, bir veya daha fazla <xref:System.Windows.Ink.StrokeCollection> nesnesine ait olabilir.  <xref:System.Windows.Controls.InkCanvas> ve <xref:System.Windows.Controls.InkPresenter> bir [Microsoft. ink. Ink](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583670(v=vs.90)) nesnesine sahip olmak yerine bir <xref:System.Windows.Ink.StrokeCollection?displayProperty=nameWithType>içerir.  
  
 Aşağıdaki çizimler çifti, mürekkep verileri nesne modellerini karşılaştırır.  Windows Forms ve COM platformlarında, [Microsoft. Ink. ink](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583670(v=vs.90)) nesnesi [Microsoft. Ink. Stroke](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552692(v=vs.90)) nesnelerinin ömrünü kısıtlar ve ekran kalemi paketleri tek vuruşlara aittir.  Aşağıdaki çizimde gösterildiği gibi, iki veya daha fazla vuruş aynı [Microsoft. Ink. DrawingAttributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583636(v=vs.90)) nesnesine başvurabilir.  
  
 ![COM&#47;WinForms Için mürekkep nesne modelinin diyagramı.](./media/ink-inkownsstrokes.png "Ink_InkOwnsStrokes")  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], her bir <xref:System.Windows.Ink.Stroke?displayProperty=nameWithType> bir başvuru olduğu sürece var olan ortak bir dil çalışma zamanı nesnesidir.  Her <xref:System.Windows.Ink.Stroke>, aynı zamanda ortak dil çalışma zamanı nesneleri olan bir <xref:System.Windows.Input.StylusPointCollection> ve <xref:System.Windows.Ink.DrawingAttributes?displayProperty=nameWithType> nesnesine başvurur.  
  
 ![WPF için mürekkep nesne modelinin diyagramı.](./media/ink-wpfinkobjectmodel.png "Ink_WPFInkObjectModel")  
  
 Aşağıdaki tabloda WPF platformunda ve Windows Forms ve COM platformlarında bazı ortak görevlerin nasıl yerine getirileceğini karşılaştırılmaktadır.  
  
|Görev|Windows Presentation Foundation|Windows Forms ve COM|  
|----------|-------------------------------------|---------------------------|  
|Mürekkebi Kaydet|<xref:System.Windows.Ink.StrokeCollection.Save%2A>|[Microsoft. Ink. Ink. Save](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms571335(v=vs.90))|  
|Mürekkebi yükle|<xref:System.Windows.Ink.StrokeCollection.%23ctor%2A> Oluşturucusu ile <xref:System.Windows.Ink.StrokeCollection> oluşturun.|[Microsoft. Ink. Ink. Load](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms569609(v=vs.90))|  
|İsabet testi|<xref:System.Windows.Ink.StrokeCollection.HitTest%2A>|[Microsoft. Ink. Ink. HitTest](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms571330(v=vs.90))|  
|Mürekkebi Kopyala|<xref:System.Windows.Controls.InkCanvas.CopySelection%2A>|[Microsoft. Ink. Ink. ClipboardCopy](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms571316(v=vs.90))|  
|Mürekkebi Yapıştır|<xref:System.Windows.Controls.InkCanvas.Paste%2A>|[Microsoft. Ink. Ink. ClipboardPaste](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms571318(v=vs.90))|  
|Bir vuruş koleksiyonunda özel özelliklere erişin|<xref:System.Windows.Ink.StrokeCollection.AddPropertyData%2A> (Özellikler dahili olarak depolanır ve <xref:System.Windows.Ink.StrokeCollection.AddPropertyData%2A>, <xref:System.Windows.Ink.StrokeCollection.RemovePropertyData%2A>ve <xref:System.Windows.Ink.StrokeCollection.ContainsPropertyData%2A>aracılığıyla erişilir)|[Microsoft. Ink. Ink. ExtendedProperties](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms582214(v=vs.90)) kullanın|  
  
### <a name="sharing-ink-between-platforms"></a>Platformlar arasında mürekkep paylaşma  
 Platformlar, mürekkep verileri için farklı nesne modellerine sahip olsa da, verilerin platformlar arasında paylaşılması çok kolaydır. Aşağıdaki örnekler bir Windows Forms uygulamasından mürekkep kaydeder ve mürekkebi bir Windows Presentation Foundation uygulamasına yükler.  
  
 [!code-csharp[WinFormWPFInk#UsingWinforms](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwinforms)]
 [!code-vb[WinFormWPFInk#UsingWinforms](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwinforms)]  
[!code-csharp[WinFormWPFInk#SaveWinforms](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#savewinforms)]
[!code-vb[WinFormWPFInk#SaveWinforms](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#savewinforms)]  
  
 [!code-csharp[WinFormWPFInk#UsingWPF](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwpf)]
 [!code-vb[WinFormWPFInk#UsingWPF](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwpf)]  
[!code-csharp[WinFormWPFInk#LoadWPF](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#loadwpf)]
[!code-vb[WinFormWPFInk#LoadWPF](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#loadwpf)]  
  
 Aşağıdaki örnekler bir Windows Presentation Foundation uygulamasından mürekkep kaydeder ve mürekkebi bir Windows Forms uygulamasına yükler.  
  
 [!code-csharp[WinFormWPFInk#UsingWPF](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwpf)]
 [!code-vb[WinFormWPFInk#UsingWPF](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwpf)]  
[!code-csharp[WinFormWPFInk#SaveWPF](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#savewpf)]
[!code-vb[WinFormWPFInk#SaveWPF](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#savewpf)]  
  
 [!code-csharp[WinFormWPFInk#UsingWinforms](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#usingwinforms)]
 [!code-vb[WinFormWPFInk#UsingWinforms](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#usingwinforms)]  
[!code-csharp[WinFormWPFInk#LoadWinforms](~/samples/snippets/csharp/VS_Snippets_Wpf/WinformWPFInk/CSharp/Program.cs#loadwinforms)]
[!code-vb[WinFormWPFInk#LoadWinforms](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WinformWPFInk/VisualBasic/Module1.vb#loadwinforms)]
## <a name="events-from-the-tablet-pen"></a>Tablet kalemden olaylar  

 Windows Forms ve COM platformları üzerindeki [Microsoft. Ink. InkOverlay](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552322(v=vs.90)), [Microsoft. Ink. InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90))ve [Microsoft. Ink. InkPicture](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583740(v=vs.90)) , Kullanıcı kalem verilerini girdinken olayları alır. [Microsoft. Ink. InkOverlay](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms552322(v=vs.90)) veya [Microsoft. Ink. InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90)) bir pencereye veya denetime iliştirilir ve tablet giriş verileri tarafından oluşturulan olaylara abone olabilir. Bu olayların gerçekleştiği iş parçacığı, olayların bir kalem, fare veya program aracılığıyla yapılıp yapılmayacağını gösterir. Bu olaylarla ilgili olarak iş parçacığı oluşturma hakkında daha fazla bilgi için bkz. [bir olayın Tetiklebileceği](/windows/desktop/tablet/threads-on-which-an-event-can-fire) [genel iş parçacığı konuları](/windows/desktop/tablet/general-threading-considerations) ve iş parçacıkları.  
  
 Windows Presentation Foundation platformunda, <xref:System.Windows.UIElement> sınıfında kalem girişi için olaylar bulunur. Bu, her denetim, ekran kalemi olaylarının tam kümesini kullanıma sunmasıdır.  Ekran kalemi olayları tünel/kabarcıklanma olay çiftlerine sahiptir ve uygulama iş parçacığında her zaman gerçekleşir.  Daha fazla bilgi için bkz. [yönlendirilmiş olaylara genel bakış](routed-events-overview.md).  
  
 Aşağıdaki diyagramda, ekran kalemi olaylarını oluşturan sınıfların nesne modellerini karşılaştıran gösterilmektedir. Windows Presentation Foundation nesne modeli, Tünel olayı karşılıklarından değil yalnızca kabarcıklanma olaylarını gösterir.  
  
 ![WPF vs WinForms içindeki ekran kalemi olaylarının diyagramı.](./media/ink-stylusevents.png "Ink_StylusEvents")  
  
## <a name="pen-data"></a>Kalem verileri  
 Üç platformda de bir tablet kalemden gelen verileri kesmeye ve düzenlemeye yönelik yollar sağlanır.  Windows Forms ve COM platformlarında, bu, bir [Microsoft. StylusInput. RealTimeStylus](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms585724(v=vs.90))oluşturularak, bir pencere veya denetim iliştirilerek ve [Microsoft. StylusInput. IStylusSyncPlugin](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms575201(v=vs.90)) ya da [Microsoft. StylusInput. IStylusAsyncPlugin](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms575194(v=vs.90)) arabirimini uygulayan bir sınıf oluşturularak elde edilir. Özel eklenti daha sonra [Microsoft. StylusInput. RealTimeStylus](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms585724(v=vs.90))öğesinin eklenti koleksiyonuna eklenir. Bu nesne modeli hakkında daha fazla bilgi için bkz. [StylusInput API 'Leri mimarisi](/windows/desktop/tablet/architecture-of-the-stylusinput-apis).  
  
 WPF platformunda <xref:System.Windows.UIElement> sınıfı, [Microsoft. StylusInput. RealTimeStylus](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms585724(v=vs.90))sürümüne benzer bir eklentiler koleksiyonu sunar.  Kalem verilerini ele almak için <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> devralan bir sınıf oluşturun ve nesneyi <xref:System.Windows.UIElement><xref:System.Windows.UIElement.StylusPlugIns%2A> koleksiyonuna ekleyin. Bu etkileşim hakkında daha fazla bilgi için bkz. [ekran kaleminden girişi önleme](intercepting-input-from-the-stylus.md).  
  
 Tüm platformlarda, bir iş parçacığı havuzu, ekran kalemi olayları aracılığıyla mürekkep verilerini alır ve bunu uygulama iş parçacığına gönderir.  COM ve Windows platformlarında iş parçacığı oluşturma hakkında daha fazla bilgi için bkz. [StylusInput API 'leri Için Iş parçacığı konuları](/windows/desktop/tablet/threading-considerations-for-the-stylusinput-apis).  Windows Presentation yazılımında iş parçacığı oluşturma hakkında daha fazla bilgi için bkz. [mürekkep Iş parçacığı modeli](the-ink-threading-model.md).  
  
 Aşağıdaki çizim kalem iş parçacığı havuzunda kalem verileri alan sınıfların nesne modellerini karşılaştırır.  
  
 ![WPF vs WinForms StylusPlugIn modeli diyagramı.](./media/ink-stylusplugins.png "Ink_StylusPlugins")
