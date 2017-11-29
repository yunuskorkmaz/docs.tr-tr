---
title: "Yapılandırılmış Gezintiye Genel Bakış"
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
helpviewer_keywords: structured navigation [WPF]
ms.assetid: 025d30ef-fec5-436d-ad7a-5d5483331c26
caps.latest.revision: "43"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b241e9a2dbe84833f43dadb2e979e5ee079706a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="structured-navigation-overview"></a>Yapılandırılmış Gezintiye Genel Bakış
Tarafından barındırılan içerik bir [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)], <xref:System.Windows.Controls.Frame>, veya bir <xref:System.Windows.Navigation.NavigationWindow> paketi tarafından tanımlanan sayfaların oluşur [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] ve için köprüler tarafından gittiğinizde. Sayfalar ve, bunlar, köprüler tarafından tanımlandığı şekilde gezinilebilir yolları yapısını gezinti topoloji olarak bilinir. Bu tür bir topoloji çeşitli uygulama türleri, özellikle, belgeler içinde gezinmek uygun. Bu tür uygulamalar için kullanıcı bir sayfadan başka bir sayfaya ya da sayfa ilgili diğer herhangi bir şey bilmenize gerek olmadan gidebilirsiniz.  
  
 Ancak, uygulamalarının diğer türleri arasında bunlar geçiş yaptığınızda bilmeniz gereken sayfaları sahip. Örneğin, bir kuruluştaki tüm çalışanlar listelemek için bir sayfa sahip bir insan kaynakları uygulaması göz önünde bulundurun — "Listesi Çalışanlar" sayfası. Bu sayfa bir köprüyü tıklatarak yeni bir çalışan eklemek için kullanıcıların da izin verebilir. Tıklatıldığında, sayfa yeni çalışanın ayrıntıları toplamak ve yeni çalışan oluşturup listesini güncelleştirmek için "Listesi Çalışanlar" sayfasına geri dönmek için "Bir çalışan Ekle" sayfasına götürür. Bu gezinti stili ve yapısal programlama bilinen bir değer döndüren bir işlem gerçekleştirmek için bir yöntemi çağırmak için benzer. Bu nedenle, bu stili Gezinti denir *yapılandırılmış Gezinti*.  
  
 <xref:System.Windows.Controls.Page> Sınıf yapılandırılmış gezinti desteği uygulama değil. Bunun yerine, <xref:System.Windows.Navigation.PageFunction%601> sınıfı türer <xref:System.Windows.Controls.Page> ve yapılandırılmış gezinti için gerekli temel yapıları ile genişletir. Bu konu, yapılandırılmış Gezinti kullanarak kurmak gösterilmiştir <xref:System.Windows.Navigation.PageFunction%601>.  
  
 
  
<a name="Structured_Navigation"></a>   
## <a name="structured-navigation"></a>Yapılandırılmış Gezinti  
 Bir sayfa yapılandırılmış Gezinti bölmesinde başka bir sayfaya çağırdığında bazılarını veya tümünü aşağıdaki gereklidir:  
  
-   Arama sayfası, isteğe bağlı olarak adlandırılan sayfası için gerekli parametreleri geçirme çağrılan sayfasına götürür.  
  
-   Bir kullanıcı arama sayfası kullanılarak tamamlandığında çağrılan sayfasında, isteğe bağlı olarak özellikle arama sayfası döndürür:  
  
    -   Arama sayfası (örneğin, bir kullanıcı bir Tamam düğmesine veya iptal düğmesine basıldığında olup olmadığını) nasıl tamamlandı açıklayan durum bilgileri döndürüyor.  
  
    -   Kullanıcı (örneğin, yeni çalışan ayrıntıları) toplanan verilerin döndürülüyor.  
  
-   Arama sayfası çağrılan sayfasına döndürüldüğünde çağrılan sayfa adlı sayfa başka bir örneğinin yalıtmak için gezinme geçmişi kaldırılır.  
  
 Bu davranışların aşağıdaki şekilde gösterilmiştir.  
  
 ![Arama sayfası ve çağrılan sayfa arasındaki akışını](../../../../docs/framework/wpf/app-development/media/structurednavigationoverviewfigure1.png "StructuredNavigationOverviewFigure1")  
  
 Bu davranışların kullanarak uygulayabileceğiniz bir <xref:System.Windows.Navigation.PageFunction%601> çağrılan sayfası olarak.  
  
<a name="Structured_Navigation_with_PageFunction"></a>   
## <a name="structured-navigation-with-pagefunction"></a>PageFunction ile yapılandırılmış Gezinti  
 Bu konuda, tek bir içeren yapılandırılmış Gezinti temel mekanikleri uygulamak gösterilmiştir <xref:System.Windows.Navigation.PageFunction%601>. Bu örnekte, bir <xref:System.Windows.Controls.Page> çağrıları bir <xref:System.Windows.Navigation.PageFunction%601> almak için bir <xref:System.String> değer kullanıcıdan ve döndürün.  
  
### <a name="creating-a-calling-page"></a>Bir arama sayfası oluşturma  
 Çağıran sayfasını bir <xref:System.Windows.Navigation.PageFunction%601> ya da olabilir bir <xref:System.Windows.Controls.Page> veya <xref:System.Windows.Navigation.PageFunction%601>. Bu örnek, bir <xref:System.Windows.Controls.Page>aşağıdaki kodda gösterildiği gibi.  
  
 [!code-xaml[StructuredNavigationSample#CallingPageDefaultMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#callingpagedefaultmarkup1)]  
[!code-xaml[StructuredNavigationSample#CallingPageDefaultMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#callingpagedefaultmarkup2)]  
  
 [!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind1)]
 [!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind1)]  
[!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind2)]
[!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind2)]  
[!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind3)]
[!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind3)]  
  
### <a name="creating-a-page-function-to-call"></a>Sayfa işlevi çağırmak için oluşturma  
 Arama sayfası toplamak ve kullanıcıdan verileri döndürmek için çağrılan sayfa kullanabileceğinizden <xref:System.Windows.Navigation.PageFunction%601> , tür bağımsız değişkeni çağrılan sayfa döndürülecek değer türünü belirten genel bir sınıf uygulanır. Aşağıdaki kod çağrılan ilk uyarlamasını gösterir sayfasında, kullanarak bir <xref:System.Windows.Navigation.PageFunction%601>, döndüren bir <xref:System.String>.  
  
 [!code-xaml[StructuredNavigationSample#CalledPageFunctionMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml#calledpagefunctionmarkup)]  
  
 [!code-csharp[StructuredNavigationSample#CalledPageFunctionCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#calledpagefunctioncodebehind1)]
 [!code-vb[StructuredNavigationSample#CalledPageFunctionCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#calledpagefunctioncodebehind1)]  
[!code-csharp[StructuredNavigationSample#CalledPageFunctionCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#calledpagefunctioncodebehind2)]
[!code-vb[StructuredNavigationSample#CalledPageFunctionCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#calledpagefunctioncodebehind2)]  
  
 Bildirimi bir <xref:System.Windows.Navigation.PageFunction%601> bildirimi için benzer bir <xref:System.Windows.Controls.Page> tür bağımsız değişkenleri eklenmesi ile. Kod örnekte görebildiğiniz gibi tür bağımsız değişkenleri ikisi de belirtilmiş [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirme kullanarak `x:TypeArguments` özniteliği ve standart genel tür bağımsız değişkeni sözdizimini kullanarak arka plan kodu,.  
  
 Yalnızca kullanmak zorunda değilsiniz [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sınıfları tür bağımsız değişkenleri olarak. A <xref:System.Windows.Navigation.PageFunction%601> özel bir tür olarak soyutlanır etki alanına özgü verileri toplamak için çağrılabilir. Aşağıdaki kod bir tür bağımsız değişkeni olarak bir özel tür kullanmayı gösterir bir <xref:System.Windows.Navigation.PageFunction%601>.  
  
 [!code-csharp[CustomTypePageFunctionSnippets#CustomTypeCODE1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomType.cs#customtypecode1)]
 [!code-vb[CustomTypePageFunctionSnippets#CustomTypeCODE1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomType.vb#customtypecode1)]  
[!code-csharp[CustomTypePageFunctionSnippets#CustomTypeCODE2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomType.cs#customtypecode2)]
[!code-vb[CustomTypePageFunctionSnippets#CustomTypeCODE2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomType.vb#customtypecode2)]  
  
 [!code-xaml[CustomTypePageFunctionSnippets#CustomTypePageFunctionMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml#customtypepagefunctionmarkup1)]  
[!code-xaml[CustomTypePageFunctionSnippets#CustomTypePageFunctionMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml#customtypepagefunctionmarkup2)]  
  
 [!code-csharp[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml.cs#customtypepagefunctioncodebehind1)]
 [!code-vb[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomTypePageFunction.xaml.vb#customtypepagefunctioncodebehind1)]  
[!code-csharp[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml.cs#customtypepagefunctioncodebehind2)]
[!code-vb[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomTypePageFunction.xaml.vb#customtypepagefunctioncodebehind2)]  
  
 Tür bağımsız değişkenleri <xref:System.Windows.Navigation.PageFunction%601> aşağıdaki bölümlerde açıklanan arama sayfası ve çağrılan sayfa arasındaki iletişimi için temeli sağlar.  
  
 Bildirimi ile tanımlanan türü göreceksiniz olarak bir <xref:System.Windows.Navigation.PageFunction%601> verileri döndürme önemli bir rol oynar bir <xref:System.Windows.Navigation.PageFunction%601> arama sayfası.  
  
### <a name="calling-a-pagefunction-and-passing-parameters"></a>Bir PageFunction çağırma ve parametreleri geçirme  
 Bir sayfa çağırmak için arama sayfası gerekir çağrılan sayfası örneği ve onu kullanarak gidin <xref:System.Windows.Navigation.NavigationService.Navigate%2A> yöntemi. Bu, çağrılan sayfa tarafından toplanan verileri için varsayılan değerleri gibi çağrılan sayfasına ilk veri iletmek arama sayfası sağlar.  
  
 Aşağıdaki kod, arama sayfasından parametreler kabul etmek için varsayılan olmayan bir oluşturucu çağrılan sayfasıyla gösterir.  
  
 [!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind1)]
 [!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind1)]  
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind2)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind2)]  
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind3)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind3)]  
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind4)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind4)]  
  
 Aşağıdaki kod arama sayfası işleme gösterir <xref:System.Windows.Documents.Hyperlink.Click> olayı <xref:System.Windows.Documents.Hyperlink> çağrılan sayfası örneği ve bir başlangıç dizesi değerini geçirin.  
  
 [!code-xaml[StructuredNavigationSample#PassingDataMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#passingdatamarkup2)]  
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind1)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind1)]  
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind2)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind2)]  
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind3)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind3)]  
  
 Çağrılan sayfasına parametreleri geçirmek için gerekli değildir. Bunun yerine, aşağıdakileri yapabilirsiniz:  
  
-   Arama sayfasından:  
  
    1.  Çağrılan örneği <xref:System.Windows.Navigation.PageFunction%601> varsayılan oluşturucu kullanarak.  
  
    2.  Parametrelerde depolamak <xref:System.Windows.Application.Properties%2A>.  
  
    3.  Çağrılan gidin <xref:System.Windows.Navigation.PageFunction%601>.  
  
-   Çağrılan gelen <xref:System.Windows.Navigation.PageFunction%601>:  
  
    -   Almak ve depolanan parametrelerini kullanmak <xref:System.Windows.Application.Properties%2A>.  
  
 Ancak, kısa süre içinde anlatıldığı gibi hala kod örneği ve çağrılan sayfa tarafından döndürülen verileri toplamak için çağrılan sayfasına gidin kullanacağınızla. Bu nedenle, <xref:System.Windows.Navigation.PageFunction%601> Canlı; Aksi halde tutulması için gereksinimleri, sonraki açışınızda, gezinmek için <xref:System.Windows.Navigation.PageFunction%601>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] başlatır <xref:System.Windows.Navigation.PageFunction%601> varsayılan oluşturucu kullanarak.  
  
 Ancak, çağrılan sayfaya dönmek önce arama sayfası tarafından alınan veri döndürmek gerekir.  
  
### <a name="returning-task-result-and-task-data-from-a-task-to-a-calling-page"></a>Görev sonucu ve görev verileri bir arama sayfasına görevden döndürme  
 Kullanıcı çağrılan sayfasını kullanarak tamamladığında, bu örnekte Tamam veya İptal düğmeleri, döndürülecek çağrılan sayfa gereksinimlerini tuşlarına basarak miktarlara. Arama sayfası adlı kullanıcıdan veri toplamak için kullanılan olduğundan, arama sayfası iki tür bilgi gerektirir:  
  
1.  Olup kullanıcı (Tamam düğmesine veya iptal düğmesi Bu örnekte tuşlarına basarak) adlı sayfa iptal edildi. Bu arama sayfası kullanıcıdan toplanan verileri işlemek karar vermek arama sayfası sağlar.  
  
2.  Kullanıcı tarafından sağlanan verileri.  
  
 Bilgi, döndürülecek <xref:System.Windows.Navigation.PageFunction%601> uygulayan <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> yöntemi. Aşağıdaki kod, çağıran gösterilmiştir.  
  
 [!code-csharp[StructuredNavigationSample#ReturnCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#returncodebehind1)]
 [!code-vb[StructuredNavigationSample#ReturnCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#returncodebehind1)]  
[!code-csharp[StructuredNavigationSample#ReturnCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#returncodebehind2)]
[!code-vb[StructuredNavigationSample#ReturnCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#returncodebehind2)]  
  
 Bu örnekte, kullanıcı değeri iptal düğmesine basarsa `null` arama sayfası döndürülür. Bunun yerine Tamam düğmesine basıldığında kullanıcı tarafından sağlanan dize değeri döndürülür. <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A>olan bir `protected``virtual` verilerinizi arama sayfasına geri dönmek için çağrı yöntemi. Verilerinizi genel bir örneğinde paketlenmesi gerekiyor <xref:System.Windows.Navigation.ReturnEventArgs%601> değer türü, tür bağımsız değişkeni türünü belirtir, <xref:System.Windows.Navigation.ReturnEventArgs%601.Result%2A> döndürür. Bu şekilde, bildirirken bir <xref:System.Windows.Navigation.PageFunction%601> belirli tür bağımsız değişkeni ile belirten bir <xref:System.Windows.Navigation.PageFunction%601> tür bağımsız değişkeni tarafından belirtilen türünün bir örneği döndürür. Bu örnekte, tür bağımsız değişkeni ve sonuç olarak, dönüş değeri türüdür <xref:System.String>.  
  
 Zaman <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> çağrılır, arama sayfası gereksinimlerini dönüş değerini alma herhangi bir şekilde <xref:System.Windows.Navigation.PageFunction%601>. Bu nedenle, <xref:System.Windows.Navigation.PageFunction%601> uygulayan <xref:System.Windows.Navigation.PageFunction%601.Return> sayfaları işlemek için çağırmak için olay. Zaman <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> olarak adlandırılır, <xref:System.Windows.Navigation.PageFunction%601.Return> tetiklenir, arama sayfası ile kaydedebilirsiniz şekilde <xref:System.Windows.Navigation.PageFunction%601.Return> bildirim almak için.  
  
 [!code-csharp[StructuredNavigationSample#ProcessResultCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#processresultcodebehind1)]
 [!code-vb[StructuredNavigationSample#ProcessResultCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#processresultcodebehind1)]  
[!code-csharp[StructuredNavigationSample#ProcessResultCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#processresultcodebehind2)]
[!code-vb[StructuredNavigationSample#ProcessResultCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#processresultcodebehind2)]  
  
### <a name="removing-task-pages-when-a-task-completes"></a>Bir görev tamamlandığında görev sayfaları kaldırma  
 Adlı bir sayfasını döndürür ve kullanıcı iptal çağrılan sayfasında alamadık, arama sayfası kullanıcı tarafından sağlanan ve ayrıca çağrılan sayfasından döndürülen verileri işler. Bu şekilde veri alım genellikle yalıtılmış bir etkinliktir; çağrılan sayfa geri döndüğünde, arama sayfası oluşturmak ve daha fazla veri yakalamak için yeni bir arama sayfasına gidin gerekiyor.  
  
 Ancak, çağrılan bir sayfa günlükten kaldırılmadığı sürece, bir kullanıcı geri arama sayfası önceki bir örneği için gidebilirsiniz olacaktır. Olup bir <xref:System.Windows.Navigation.PageFunction%601> içinde tutulur günlüğü tarafından belirlenen <xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A> özelliği. Varsayılan olarak, bir sayfa otomatik olarak işlevdir ne zaman kaldırılan <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> denir, çünkü <xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A> ayarlanır `true`. Sonra gezinti geçmişindeki sayfa işlevi tutmak için <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> olarak adlandırılan ayarlamak <xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A> için `false`.  
  
<a name="Other_Types_of_Structured_Navigation"></a>   
## <a name="other-types-of-structured-navigation"></a>Yapılandırılmış Gezinti diğer türleri  
 Bu konuda en temel kullanımını göstermektedir bir <xref:System.Windows.Navigation.PageFunction%601> çağrısı/return desteklemek için Gezinti yapılandırılmış. Bu temel yapılandırılmış Gezinti daha karmaşık türleri oluşturma olanağı sağlar.  
  
 Örneğin, bazen birden çok sayfa arama sayfası tarafından bir kullanıcıdan yeterli veri toplamak için veya bir görev gerçekleştirmeniz gerekir. Birden çok sayfalarının kullanımını "Sihirbazı" adlandırılır.  
  
 Diğer durumlarda, uygulamalar üzerinde yapılandırılmış Gezinti verimli bir şekilde çalışması için bağımlı karmaşık gezinti topolojileri sahip olabilir. Daha fazla bilgi için bkz: [gezinti topolojilerine genel bakış](../../../../docs/framework/wpf/app-development/navigation-topologies-overview.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Navigation.PageFunction%601>  
 <xref:System.Windows.Navigation.NavigationService>  
 [Gezinti topolojilerine genel bakış](../../../../docs/framework/wpf/app-development/navigation-topologies-overview.md)
