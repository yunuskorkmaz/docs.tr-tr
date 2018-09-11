---
title: Yapılandırılmış Gezintiye Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- structured navigation [WPF]
ms.assetid: 025d30ef-fec5-436d-ad7a-5d5483331c26
ms.openlocfilehash: 2264686f34123e74bf7d24ce80877742d952f35d
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44268179"
---
# <a name="structured-navigation-overview"></a>Yapılandırılmış Gezintiye Genel Bakış
Tarafından barındırılan içerik bir [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)], <xref:System.Windows.Controls.Frame>, veya bir <xref:System.Windows.Navigation.NavigationWindow> paketi tarafından tanımlanan sayfaların oluşan [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] ve için köprüler tarafından gitme. Sayfalar ve, bunlar, köprüler tarafından tanımlandığı şekilde gezinilebilir yolları yapısını gezinti topolojisi bilinir. Böyle bir topoloji, çeşitli uygulama türleri, belgeler içinde gezinmek, uygun. Bu tür uygulamalar için kullanıcı bir sayfadan başka bir sayfaya ya da sayfa diğer ilgili hiçbir şeyi bilmenize gerek olmadan gidebilirsiniz.  
  
 Ancak, diğer uygulama türleri arasında bunlar geçiş yaptığınızda bilmem gerekenler sayfaları sahip. Örneğin, bir kuruluştaki tüm çalışanlar listelemek için bir sayfa olan insan kaynakları bir uygulama düşünün; "Listesi Çalışanlar" sayfası. Bu sayfa ayrıca bir köprüyü tıklatarak yeni bir çalışan eklemek kullanıcılar izin verebilir. Tıklandığında, sayfanın yeni çalışanın ayrıntıları toplamak ve bunları yeni çalışan oluşturup listesini güncelleştirmek için "Liste Çalışanlar" sayfasına geri dönmek için "Bir çalışan Ekle" sayfasına götürür. Bu gezinti stilini yapısal programlama bilinen bir değer döndürmez ve bazı işleme gerçekleştirmek için bir yöntem çağırmak için benzerdir. Bu nedenle, bu stil Gezinti olarak da bilinen *yapılandırılmış Gezinti*.  
  
 <xref:System.Windows.Controls.Page> Sınıf yapılandırılmış gezintiye desteği uygulama değil. Bunun yerine, <xref:System.Windows.Navigation.PageFunction%601> sınıf türetilir <xref:System.Windows.Controls.Page> ve yapılandırılmış gezinti için gerekli temel yapılarıyla genişletir. Bu konuda yapılandırılmış gezintiye kullanarak oluşturmak nasıl gösterilmektedir <xref:System.Windows.Navigation.PageFunction%601>.  
  
 
  
<a name="Structured_Navigation"></a>   
## <a name="structured-navigation"></a>Yapılandırılmış gezintiye  
 Bir sayfa yapılandırılmış bir gezinti başka bir sayfa çağırdığında, bazılarını veya tümünü aşağıdaki davranışları gereklidir:  
  
-   Arama sayfası, isteğe bağlı olarak adlandırılan sayfası için gerekli parametreleri geçirme çağrılan sayfasına gider.  
  
-   Bir kullanıcı arama sayfası kullanılarak tamamlandığında Aranan sayfasında, özel arama sayfası isteğe bağlı olarak döndürür:  
  
    -   Açıklayan nasıl (örneğin, bir kullanıcı bir Tamam düğmesine veya iptal düğmesi basılı olup olmadığını) arama sayfası tamamlandıktan sonra durum bilgilerini döndürüyor.  
  
    -   (Örneğin, yeni çalışan ayrıntıları) kullanıcıdan toplanan bu veri döndürüyor.  
  
-   Arama sayfası çağrılan sayfaya geri döndüğünde, çağrılan sayfanın adlı başka bir sayfadan bir örneğini ayırmak için Gezinti geçmişinden kaldırılır.  
  
 Bu davranışların aşağıdaki şekilde gösterilmiştir.  
  
 ![Arama sayfası ve çağrılan sayfa arasındaki akışını](../../../../docs/framework/wpf/app-development/media/structurednavigationoverviewfigure1.png "StructuredNavigationOverviewFigure1")  
  
 Bu davranışların kullanarak uygulayabileceğiniz bir <xref:System.Windows.Navigation.PageFunction%601> çağrılan sayfası.  
  
<a name="Structured_Navigation_with_PageFunction"></a>   
## <a name="structured-navigation-with-pagefunction"></a>Yapılandırılmış gezintiye PageFunction ile  
 Bu konuda, yapılandırılmış gezintiye içeren tek bir temel mekanikleri uygulamak gösterilmektedir <xref:System.Windows.Navigation.PageFunction%601>. Bu örnekte, bir <xref:System.Windows.Controls.Page> çağrıları bir <xref:System.Windows.Navigation.PageFunction%601> almak için bir <xref:System.String> kullanıcıdan değer ve döndürün.  
  
### <a name="creating-a-calling-page"></a>Bir arama sayfası oluşturma  
 Çağıran sayfasını bir <xref:System.Windows.Navigation.PageFunction%601> olabilir bir <xref:System.Windows.Controls.Page> veya <xref:System.Windows.Navigation.PageFunction%601>. Bu örnekte olduğu bir <xref:System.Windows.Controls.Page>aşağıdaki kodda gösterildiği gibi.  
  
 [!code-xaml[StructuredNavigationSample#CallingPageDefaultMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#callingpagedefaultmarkup1)]  
[!code-xaml[StructuredNavigationSample#CallingPageDefaultMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#callingpagedefaultmarkup2)]  
  
 [!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind1)]
 [!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind1)]  
[!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind2)]
[!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind2)]  
[!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind3)]
[!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind3)]  
  
### <a name="creating-a-page-function-to-call"></a>Sayfa işlevi çağırmak için oluşturma  
 Arama sayfası toplamak ve kullanıcı verileri döndürmek için çağrılan sayfanın kullanabileceğinizden <xref:System.Windows.Navigation.PageFunction%601> , bağımsız değişken türü adlı sayfanın geri dönecek değerin türünü belirten bir genel sınıf olarak uygulanır. Aşağıdaki kod çağrılan ilk uygulamasını gösterir kullanarak sayfasında bir <xref:System.Windows.Navigation.PageFunction%601>, döndüren bir <xref:System.String>.  
  
 [!code-xaml[StructuredNavigationSample#CalledPageFunctionMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml#calledpagefunctionmarkup)]  
  
 [!code-csharp[StructuredNavigationSample#CalledPageFunctionCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#calledpagefunctioncodebehind1)]
 [!code-vb[StructuredNavigationSample#CalledPageFunctionCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#calledpagefunctioncodebehind1)]  
[!code-csharp[StructuredNavigationSample#CalledPageFunctionCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#calledpagefunctioncodebehind2)]
[!code-vb[StructuredNavigationSample#CalledPageFunctionCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#calledpagefunctioncodebehind2)]  
  
 Bildirimi bir <xref:System.Windows.Navigation.PageFunction%601> bildirimi için benzer bir <xref:System.Windows.Controls.Page> ek olarak, tür bağımsız değişkenleri. Kod örnekte görebileceğiniz gibi tür bağımsız değişkenlerini içinde her ikisi de belirtilirse [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirme kullanarak `x:TypeArguments` özniteliği ve kod arka plan, standart genel tür bağımsız değişkeni söz dizimini kullanarak.  
  
 Yalnızca kullanmak zorunda değilsiniz [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] tür bağımsız değişkenleri olarak sınıflar. A <xref:System.Windows.Navigation.PageFunction%601> özel bir tür olarak soyutlanır etki alanına özgü verileri toplamak için çağrılabilir. Aşağıdaki kod özel bir tür için tür bağımsız değişkeni olarak kullanma işlemini gösterir. bir <xref:System.Windows.Navigation.PageFunction%601>.  
  
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
  
 Tür bağımsız değişkenleri için <xref:System.Windows.Navigation.PageFunction%601> aşağıdaki bölümlerde açıklanan arama sayfası ve çağrılan sayfanın arasındaki iletişim için temel sağlar.  
  
 Bildirimi ile tanımlanan bir türü göreceksiniz olarak bir <xref:System.Windows.Navigation.PageFunction%601> verileri döndüren önemli bir rol oynar bir <xref:System.Windows.Navigation.PageFunction%601> arama sayfası.  
  
### <a name="calling-a-pagefunction-and-passing-parameters"></a>Bir PageFunction çağırma ve parametreleri geçirme  
 Bir sayfa çağırmak için arama sayfası adlı sayfanın örneği oluşturmalı ve Git kullanarak <xref:System.Windows.Navigation.NavigationService.Navigate%2A> yöntemi. Bu, çağrılan sayfa tarafından toplanan veriler için varsayılan değerleri gibi çağrılan sayfasında ilk veri geçirmek arama sayfası sağlar.  
  
 Aşağıdaki kod, arama sayfasından parametreler kabul etmek için varsayılan olmayan bir Oluşturucu ile çağrılan sayfada gösterilir.  
  
 [!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind1)]
 [!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind1)]  
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind2)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind2)]  
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind3)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind3)]  
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind4)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind4)]  
  
 Aşağıdaki kod arama sayfası işleme gösterir <xref:System.Windows.Documents.Hyperlink.Click> olayı <xref:System.Windows.Documents.Hyperlink> çağrılan sayfası örneği oluşturun ve ilk dize değeri geçirin.  
  
 [!code-xaml[StructuredNavigationSample#PassingDataMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#passingdatamarkup2)]  
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind1)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind1)]  
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind2)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind2)]  
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind3)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind3)]  
  
 Çağrılan sayfasına parametreleri geçirmek için gerekli değildir. Bunun yerine, aşağıdakileri yapabilirsiniz:  
  
-   Arama sayfasından:  
  
    1.  Çağrılan örneği <xref:System.Windows.Navigation.PageFunction%601> kullanan varsayılan oluşturucu.  
  
    2.  Parametrelerinde Store <xref:System.Windows.Application.Properties%2A>.  
  
    3.  Çağrılan gidin <xref:System.Windows.Navigation.PageFunction%601>.  
  
-   Çağrılan gelen <xref:System.Windows.Navigation.PageFunction%601>:  
  
    -   Alma ve içerisinde depolanan parametreleri kullanma <xref:System.Windows.Application.Properties%2A>.  
  
 Ancak, kısa süre içinde anlatıldığı gibi hala kod örneği ve çağrılan sayfa tarafından döndürülen veriler toplamak için çağrılan sayfasına gitmek için kullanacağınız. Bu nedenle, <xref:System.Windows.Navigation.PageFunction%601> Canlı; Aksi halde tutulması için gereksinimleri, sonraki açışınızda ulaşmanıza <xref:System.Windows.Navigation.PageFunction%601>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] başlatır <xref:System.Windows.Navigation.PageFunction%601> kullanan varsayılan oluşturucu.  
  
 Ancak, çağrılan sayfasına dönmek önce bu arama sayfası tarafından alınan veri döndürmesi gerekir.  
  
### <a name="returning-task-result-and-task-data-from-a-task-to-a-calling-page"></a>Görev dönen sonuç ve bir arama sayfasına bir görevden görev verileri  
 Kullanıcı çağrılan sayfasını kullanarak tamamlandıktan sonra bu örnekte Tamam veya İptal düğmeleri, döndürmek için çağrılan bir sayfa gereksinimlerini tuşlarına basarak miktarlara. Bu yana arama sayfası adlı kullanıcıdan veri toplamak için kullanılan iki tür bilgi arama sayfası gerektirir:  
  
1.  Olup kullanıcı (Tamam düğmesine veya iptal düğmesi Bu örnekte tuşlarına basarak) adlı sayfanın iptal edildi. Bu, arama sayfası kullanıcıdan toplanan veriyi işlemek belirlemek arama sayfası sağlar.  
  
2.  Kullanıcı tarafından sağlanan veriler.  
  
 Bilgi, döndürülecek <xref:System.Windows.Navigation.PageFunction%601> uygulayan <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> yöntemi. Aşağıdaki kodu çağırmak nasıl gösterir.  
  
 [!code-csharp[StructuredNavigationSample#ReturnCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#returncodebehind1)]
 [!code-vb[StructuredNavigationSample#ReturnCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#returncodebehind1)]  
[!code-csharp[StructuredNavigationSample#ReturnCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#returncodebehind2)]
[!code-vb[StructuredNavigationSample#ReturnCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#returncodebehind2)]  
  
 Bu örnekte, bir kullanıcı değerini iptal düğmesine bastığında `null` arama sayfasına döndürülür. Tamam düğmesine basıldığını bunun yerine, kullanıcı tarafından sağlanan dize değeri döndürülür. <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> olan bir `protected virtual` verilerinizi arama sayfasına dönmek için çağırma yöntemi. Verilerinizi genel örneğinde paketlenmesi gereken <xref:System.Windows.Navigation.ReturnEventArgs%601> türü, tür bağımsız değişken türünü belirtir, değeri <xref:System.Windows.Navigation.ReturnEventArgs%601.Result%2A> döndürür. Bu şekilde, bildirdiğinizde bir <xref:System.Windows.Navigation.PageFunction%601> belirli tür bağımsız değişkeni ile ifadesi bir <xref:System.Windows.Navigation.PageFunction%601> tür bağımsız değişkeni tarafından belirtilen türün örneğini döndürür. Bu örnekte, tür bağımsız değişkeni ve sonuç olarak, dönüş değeri olduğu tür <xref:System.String>.  
  
 Zaman <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> çağrılır, arama sayfası gereksinimlerini dönüş değerini alma şekilde <xref:System.Windows.Navigation.PageFunction%601>. Bu nedenle, <xref:System.Windows.Navigation.PageFunction%601> uygulayan <xref:System.Windows.Navigation.PageFunction%601.Return> sayfaları işlemek için çağırma olay. Zaman <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> çağrıldığında <xref:System.Windows.Navigation.PageFunction%601.Return> oluşturulur, arama sayfası ile kaydedebilirsiniz şekilde <xref:System.Windows.Navigation.PageFunction%601.Return> bildirim almak için.  
  
 [!code-csharp[StructuredNavigationSample#ProcessResultCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#processresultcodebehind1)]
 [!code-vb[StructuredNavigationSample#ProcessResultCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#processresultcodebehind1)]  
[!code-csharp[StructuredNavigationSample#ProcessResultCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#processresultcodebehind2)]
[!code-vb[StructuredNavigationSample#ProcessResultCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#processresultcodebehind2)]  
  
### <a name="removing-task-pages-when-a-task-completes"></a>Bir görev tamamlandığında, görev sayfaları kaldırma  
 Adlı bir sayfasını döndürür ve kullanıcı iptal çağrılan sayfasında siz arama sayfası kullanıcı tarafından sağlanan ve ayrıca adlı sayfadan döndürülen verileri işler. Bu şekilde veri alım genellikle yalıtılmış bir etkinliktir; çağrılan sayfanın geri döndüğünde, oluşturun ve daha fazla veri yakalamak için yeni bir arama sayfasına gitmek arama sayfası gerekiyor.  
  
 Ancak, çağrılan bir sayfa günlükten kaldırılmadığı sürece, bir kullanıcı için arama sayfası önceki kopyası geri gidebilirsiniz olacaktır. Olup olmadığını bir <xref:System.Windows.Navigation.PageFunction%601> içinde tutulur günlüğü tarafından belirlenen <xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A> özelliği. Varsayılan olarak, bir sayfa işlev otomatik olarak, ne zaman kaldırıldı <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> denir, çünkü <xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A> ayarlanır `true`. Sayfa işlevi sonra gezinti geçmişinde tutulacak <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> çağrıldığında ayarlamak <xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A> için `false`.  
  
<a name="Other_Types_of_Structured_Navigation"></a>   
## <a name="other-types-of-structured-navigation"></a>Yapılandırılmış gezintiye diğer türleri  
 Bu konuda en temel kullanışını bir <xref:System.Windows.Navigation.PageFunction%601> Gezinti çağrı/return'e destekleyecek şekilde yapılandırılmış. Bu temel yapılandırılmış gezintiye daha karmaşık türleri oluşturma olanağı sağlar.  
  
 Örneğin, bazen birden çok sayfa arama sayfası tarafından bir kullanıcı tarafından yeterli veri toplamak için veya bir görevi gerçekleştirmek için gereklidir. Birden çok sayfa kullanımını "Sihirbazı" adlandırılır.  
  
 Diğer durumlarda, uygulamalarını verimli bir şekilde çalışması için yapılandırılmış gezintiye bağımlı karmaşık gezinti topolojilerine sahip olabilir. Daha fazla bilgi için [gezinti topolojilerine genel bakış](../../../../docs/framework/wpf/app-development/navigation-topologies-overview.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Navigation.PageFunction%601>  
 <xref:System.Windows.Navigation.NavigationService>  
 [Gezinti Topolojilerine Genel Bakış](../../../../docs/framework/wpf/app-development/navigation-topologies-overview.md)
