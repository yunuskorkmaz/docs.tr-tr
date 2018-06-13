---
title: 'Nasıl yapılır: UI Olan Eklenti Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- creating an add-in that is a UI [WPF]
- add-ins [WPF], UI
- creating UI add-ins [WPF]
- UI add-ins [WPF], creating
- implementing UI add-ins [WPF]
- pipeline segments [WPF], creating add-ins
ms.assetid: 86375525-282b-4039-8352-8680051a10ea
ms.openlocfilehash: 4bd03c2f879ecab83306bb68552c044a33f2e6e4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33549597"
---
# <a name="how-to-create-an-add-in-that-is-a-ui"></a>Nasıl yapılır: UI Olan Eklenti Oluşturma
Bu örnek bir Windows Presentation Foundation (tarafından barındırılan WPF) olan bir eklenti oluşturmak nasıl gösterir bir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] tek başına uygulama.  
  
 Eklenti bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] diğer bir deyişle bir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] kullanıcı denetimi. Tek bir düğme, tıklatıldığında, kullanıcı denetimi içeriği olan bir ileti kutusu görüntüler. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Tek başına uygulamayı barındıran eklenti [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ana uygulama penceresinin içeriği olarak.  
  
 **Önkoşullar**  
  
 Bu örnek vurgular [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uzantıları [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aşağıdakileri varsayar ve bu senaryo etkinleştiren eklenti modeli:  
  
-   Bilgisi [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ardışık düzen, eklenti ve konak geliştirme de dahil olmak üzere eklenti modeli. Bu kavramları tanımıyorsanız bkz [eklentiler ve genişletilebilirlik](../../../../docs/framework/add-ins/index.md). Bir ardışık düzen, eklenti ve bir ana bilgisayar uygulaması uygulanmasını gösteren bir öğretici için bkz [izlenecek yol: Genişletilebilir uygulama oluşturma](../../../../docs/framework/add-ins/walkthrough-create-extensible-app.md).  
  
-   Bilgisi [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uzantıları [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] , burada bulunabilir eklenti modeli: [WPF eklentileri genel bakış](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md).  
  
## <a name="example"></a>Örnek  
 Bir eklenti oluşturmak için bir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , her ardışık düzen segmenti, eklenti ve konak uygulama için belirli bir kod gerekir.  
    
  
<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a>Sözleşme ardışık düzen segmentini uygulama  
 Bir eklenti olduğunda bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], eklenti için anlaşma uygulamalıdır <xref:System.AddIn.Contract.INativeHandleContract>. Örnekte, `IWPFAddInContract` uygulayan <xref:System.AddIn.Contract.INativeHandleContract>aşağıdaki kodda gösterildiği gibi.  
  
 [!code-csharp[SimpleAddInIsAUISample#ContractCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]  
  
<a name="AddInViewPipeline"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a>Eklenti görünümü ardışık düzen segmentini uygulama  
 Eklenti öğesinin bir alt kümesi uygulanan çünkü <xref:System.Windows.FrameworkElement> türü, eklenti görünümü olmalıdır da bir alt kümesi <xref:System.Windows.FrameworkElement>. Aşağıdaki kod olarak uygulanan anlaşmanın eklenti görünümünü gösterir `WPFAddInView` sınıfı.  
  
 [!code-csharp[SimpleAddInIsAUISample#AddInViewCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInViews/WPFAddInView.cs#addinviewcode)]  
  
 Burada, eklenti görünümü türetildiği <xref:System.Windows.Controls.UserControl>. Sonuç olarak, eklenti [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] öğesinden türetilmelidir <xref:System.Windows.Controls.UserControl>.  
  
<a name="AddInSideAdapter"></a>   
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a>Ekleme tarafı bağdaştırıcısı ardışık düzen segmentini uygulama  
 Sözleşme olsa da bir <xref:System.AddIn.Contract.INativeHandleContract>, eklenti bir <xref:System.Windows.FrameworkElement> (eklenti görünümü ardışık düzen segmenti tarafından belirtildiği gibi). Bu nedenle, <xref:System.Windows.FrameworkElement> dönüştürülmelidir bir <xref:System.AddIn.Contract.INativeHandleContract> yalıtım sınırı geçmeden önce. Bu iş çağırarak Ekle tarafı bağdaştırıcı tarafından gerçekleştirilen <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>aşağıdaki kodda gösterildiği gibi.  
  
 [!code-csharp[SimpleAddInIsAUISample#AddInSideAdapterCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]  
  
 Bir eklenti döndüğü eklenti modelinde bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] (bkz [bir eklenti döndürür bir kullanıcı Arabirimi oluşturma](../../../../docs/framework/wpf/app-development/how-to-create-an-add-in-that-returns-a-ui.md)), eklenti bağdaştırıcısı dönüştürülen <xref:System.Windows.FrameworkElement> için bir <xref:System.AddIn.Contract.INativeHandleContract> çağırarak <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>. <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> Ayrıca, çağıran kodu yazılacak yönteminden uygulamak gerek olmasa da bu modelde, çağrılmalıdır. Geçersiz kılarak bunu <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> ve çağıran kodu uygulama <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> , çağıran kodu <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> beklediği bir <xref:System.AddIn.Contract.INativeHandleContract>. Bu durumda, arayan bir sonraki alt bölümünde ele konak tarafı bağdaştırıcısı olacaktır.  
  
> [!NOTE]
>  Geçersiz kılmanız gerekir <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> konak uygulama arasında sekmeyle gitmeyi etkinleştirme için bu modelde [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ve eklenti [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Daha fazla bilgi için bkz: "WPF Eklenti kısıtlamaları" [WPF eklentileri genel bakış](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md).  
  
 Ekle tarafı bağdaştırıcısı türeyen bir arabirim uyguladığından <xref:System.AddIn.Contract.INativeHandleContract>, uygulamanız gereken <xref:System.AddIn.Contract.INativeHandleContract.GetHandle%2A>, bunun yoksayılmasına rağmen zaman <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> geçersiz kılınır.  
  
<a name="HostViewPipeline"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a>Ana görünüm ardışık düzen segmentini uygulama  
 Bu modelde, ana bilgisayar uygulaması olacak şekilde ana görünüm bekliyor bir <xref:System.Windows.FrameworkElement> bir alt kümesi. Konak tarafındaki bağdaştırıcı dönüştürmeniz gerekir <xref:System.AddIn.Contract.INativeHandleContract> için bir <xref:System.Windows.FrameworkElement> sonra <xref:System.AddIn.Contract.INativeHandleContract> yalıtım sınırını geçer. Bir yöntem almak için konak uygulama tarafından çağrılan değil çünkü <xref:System.Windows.FrameworkElement>, ana görünüm "döndürmelidir" <xref:System.Windows.FrameworkElement> içererek. Sonuç olarak, konak görünümünde öğesinin bir alt türetilmelidir <xref:System.Windows.FrameworkElement> , içerebilir diğer [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)], gibi <xref:System.Windows.Controls.UserControl>. Aşağıdaki kod olarak uygulanan anlaşmanın konak görünümünü gösterir `WPFAddInHostView` sınıfı.  
  
  
  
<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a>Konak tarafı bağdaştırıcısı ardışık düzen segmentini uygulama  
 Sözleşme olsa da bir <xref:System.AddIn.Contract.INativeHandleContract>, konak uygulama bekler bir <xref:System.Windows.Controls.UserControl> (ana görünümü tarafından belirtildiği gibi). Sonuç olarak, <xref:System.AddIn.Contract.INativeHandleContract> dönüştürülmelidir bir <xref:System.Windows.FrameworkElement> yalıtım sınırını ana görünüm içeriği olarak ayarlamadan önce geçmesinden sonra (den türetilen <xref:System.Windows.Controls.UserControl>).  
  
 Bu iş, aşağıdaki kodda gösterildiği gibi ana bilgisayar tarafı bağdaştırıcı tarafından gerçekleştirilir.  
  
  
  
 Gördüğünüz gibi konak tarafı bağdaştırıcısı edinir <xref:System.AddIn.Contract.INativeHandleContract> Ekle tarafı bağdaştırıcının çağırarak <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> yöntemi (Bu noktasıdır nerede <xref:System.AddIn.Contract.INativeHandleContract> yalıtım sınırı kestiği).  
  
 Konak tarafındaki bağdaştırıcı sonra dönüştürür <xref:System.AddIn.Contract.INativeHandleContract> için bir <xref:System.Windows.FrameworkElement> çağırarak <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>. Son olarak, <xref:System.Windows.FrameworkElement> konak görünüm içeriği olarak ayarlanır.  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a>Eklenti uygulama  
 Ekle tarafı bağdaştırıcısı ve eklenti görünümü yerinde eklenti eklenti görünümünden türetme tarafından aşağıdaki kodda gösterildiği gibi uygulanabilir.  
  
  
  
  
  
 Bu örnekte, bu modelin ilginç yararlarından biri görebilirsiniz: eklenti geliştiricileri yeterlidir eklenti uygulamak (olduğundan [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de), hem bir eklenti sınıfı ve bir eklenti yerine [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
<a name="HostApp"></a>   
## <a name="implementing-the-host-application"></a>Konak uygulamanın uygulama  
 Konak tarafı bağdaştırıcısı ile oluşturulan ana görünüm, ana bilgisayar uygulamasını kullanabileceğiniz [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ardışık düzen açın ve bir eklenti konak görünümünü edinmek üzere eklenti modeli. Bu adımları aşağıdaki kodda gösterilir.  
  
  
  
 Ana uygulamanın tipik kullandığı [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] örtük olarak konak görünümü konak uygulamaya döndüren, eklentiyi etkinleştirmek için eklenti modeli kodu. Ana bilgisayar uygulamasını sonradan konak görünümünü görüntüler (olduğu bir <xref:System.Windows.Controls.UserControl>) gelen bir <xref:System.Windows.Controls.Grid>.  
  
 Eklenti ile etkileşim işlemek için kod [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] eklentinin uygulama etki alanında çalışır. Bu etkileşimler aşağıdakileri içerir:  
  
-   İşleme <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay.  
  
-   Gösteren <xref:System.Windows.MessageBox>.  
  
 Bu etkinlik konak uygulamadan tamamen ayrı tutulur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eklentiler ve Genişletilebilirlik](../../../../docs/framework/add-ins/index.md)  
 [WPF Eklentilerine Genel Bakış](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md)
