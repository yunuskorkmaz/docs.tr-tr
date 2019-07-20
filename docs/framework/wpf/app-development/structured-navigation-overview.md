---
title: Yapılandırılmış Gezintiye Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- structured navigation [WPF]
ms.assetid: 025d30ef-fec5-436d-ad7a-5d5483331c26
ms.openlocfilehash: 8760c847d9e73fdff9f10f0dfa55a6c674021667
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364181"
---
# <a name="structured-navigation-overview"></a>Yapılandırılmış Gezintiye Genel Bakış

Bir [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] ,, veya <xref:System.Windows.Navigation.NavigationWindow> ile barındırılabilen içerikler, Paketle ve köprüler tarafından tanımlanabilen sayfalardan oluşur. <xref:System.Windows.Controls.Frame> Sayfaların yapısı ve köprüler tarafından tanımlandığı şekilde gezinilebilecekleri yollar, gezinti topolojisi olarak bilinir. Bu tür bir topoloji, özellikle belgelerde gezinenler gibi çeşitli uygulama türlerine uygun değildir. Bu tür uygulamalar için, Kullanıcı bir sayfadan diğerine kadar herhangi bir şeyi bilmeleri gerekmeden başka bir sayfaya gidebilir.

Ancak, diğer uygulama türleri arasında gezindikleri zaman bilmeleri gereken sayfalar vardır. Örneğin, bir kuruluştaki tüm çalışanları listelemek için bir sayfa içeren bir insan kaynakları uygulaması düşünün — "çalışanları listele" sayfası. Bu sayfa, kullanıcıların bir köprüye tıklayarak yeni bir çalışan eklemesine de izin verebilir. Tıklandığı zaman, yeni çalışanın ayrıntılarını toplamak ve listeyi güncelleştirmek için "çalışan Ekle" sayfasına gider ve bunları "çalışanları listele" sayfasına geri döndürür. Bu gezinti stili, bazı işlemleri gerçekleştirmek ve yapılandırılmış programlama olarak bilinen bir değer döndürmek için bir yöntemi çağırmaya benzerdir. Bu şekilde, bu gezinti stili *yapılandırılmış gezinti*olarak bilinir.

Sınıfı <xref:System.Windows.Controls.Page> , yapılandırılmış gezinti için destek uygulamaz. Bunun yerine, <xref:System.Windows.Navigation.PageFunction%601> sınıfı öğesinden <xref:System.Windows.Controls.Page> türetilir ve yapısal gezinti için gereken temel yapılar ile genişletir. Bu konu, kullanılarak <xref:System.Windows.Navigation.PageFunction%601>yapılandırılmış gezintiyi oluşturmayı gösterir.

<a name="Structured_Navigation"></a>

## <a name="structured-navigation"></a>Yapılandırılmış gezinti

Bir sayfa yapılandırılmış bir gezinmede başka bir sayfa çağırdığında, aşağıdaki davranışların bazıları veya tümü gereklidir:

- Çağıran sayfa, isteğe bağlı olarak çağrılan sayfanın gerektirdiği parametreleri geçirerek çağrılan sayfaya gider.

- Çağrılan sayfa, bir Kullanıcı arama sayfasını kullanarak tamamlandığında, isteğe bağlı olarak, arama sayfasına özel olarak döner:

  - Çağırma sayfasının nasıl tamamlandığını açıklayan durum bilgilerini döndürme (örneğin, bir kullanıcının Tamam düğmesine veya bir Iptal düğmesine basıldığında).

  - Kullanıcıdan toplanan verileri döndürme (örneğin, yeni çalışan ayrıntıları).

- Çağıran sayfa çağrılan sayfaya döndüğünde, çağrılan sayfa bir diğer sayfanın bir örneğini başka bir şekilde yalıtmak için gezinme geçmişinden kaldırılır.

Bu davranışlar aşağıdaki şekilde gösterilmiştir:

![Ekran görüntüsü, arama sayfası ve çağrılan sayfa arasındaki akışı gösterir.](./media/structured-navigation-overview/flow-between-calling-page-called-page.png)

Çağrılan sayfa olarak bir <xref:System.Windows.Navigation.PageFunction%601> kullanarak bu davranışları uygulayabilirsiniz.

<a name="Structured_Navigation_with_PageFunction"></a>

## <a name="structured-navigation-with-pagefunction"></a>PageFunction ile yapılandırılmış gezinti

Bu konu başlığı altında, tek tek <xref:System.Windows.Navigation.PageFunction%601>içeren yapılandırılmış gezinmede temel bir katıcs 'nin nasıl uygulanacağı gösterilmektedir. Bu örnekte,, <xref:System.Windows.Controls.Page> kullanıcıdan bir <xref:System.String> değer <xref:System.Windows.Navigation.PageFunction%601> almak ve bunu döndürmek için bir çağırır.

### <a name="creating-a-calling-page"></a>Arama sayfası oluşturma

' A <xref:System.Windows.Navigation.PageFunction%601> çağrı yapan sayfa ya <xref:System.Windows.Controls.Page> da bir <xref:System.Windows.Navigation.PageFunction%601>olabilir. Bu örnekte, aşağıdaki kodda gösterildiği gibi <xref:System.Windows.Controls.Page>bir olur.

[!code-xaml[StructuredNavigationSample#CallingPageDefaultMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#callingpagedefaultmarkup1)]
[!code-xaml[StructuredNavigationSample#CallingPageDefaultMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#callingpagedefaultmarkup2)]

[!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind1)]
[!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind1)]
[!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind2)]
[!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind2)]
[!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND3](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind3)]
[!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind3)]

### <a name="creating-a-page-function-to-call"></a>Çağırmak için bir sayfa Işlevi oluşturma

Çağıran sayfa, kullanıcıdan veri toplamak ve döndürmek için çağrılan sayfayı kullanabilmesi için, <xref:System.Windows.Navigation.PageFunction%601> tür bağımsız değişkeni, çağrılan sayfanın döndürdüğü değerin türünü belirten bir genel sınıf olarak uygulanır. Aşağıdaki kod, <xref:System.Windows.Navigation.PageFunction%601>' i <xref:System.String>döndüren adlı, kullanılarak çağrılan sayfanın ilk uygulamasını gösterir.

[!code-xaml[StructuredNavigationSample#CalledPageFunctionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml#calledpagefunctionmarkup)]

[!code-csharp[StructuredNavigationSample#CalledPageFunctionCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#calledpagefunctioncodebehind1)]
[!code-vb[StructuredNavigationSample#CalledPageFunctionCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#calledpagefunctioncodebehind1)]
[!code-csharp[StructuredNavigationSample#CalledPageFunctionCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#calledpagefunctioncodebehind2)]
[!code-vb[StructuredNavigationSample#CalledPageFunctionCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#calledpagefunctioncodebehind2)]

Bir <xref:System.Windows.Navigation.PageFunction%601> öğesinin bildirimi, tür bağımsız değişkenlerinin eklenmesiyle bir <xref:System.Windows.Controls.Page> öğesinin bildirimine benzerdir. Kod örneğinde görebileceğiniz gibi, tür bağımsız değişkenleri, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] `x:TypeArguments` özniteliği ve standart genel tür bağımsız değişkeni sözdizimi kullanılarak arka plan kodu kullanılarak her iki biçimlendirmede belirtilir.

Tür bağımsız değişkenleri olarak yalnızca .NET Framework sınıfları kullanmak zorunda değilsiniz. Özel <xref:System.Windows.Navigation.PageFunction%601> bir tür olarak soyut olan, etki alanına özgü verileri toplamak için bir çağrılabilir. Aşağıdaki kod, bir özel türün bir <xref:System.Windows.Navigation.PageFunction%601>tür bağımsız değişkeni olarak nasıl kullanılacağını gösterir.

[!code-csharp[CustomTypePageFunctionSnippets#CustomTypeCODE1](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomType.cs#customtypecode1)]
[!code-vb[CustomTypePageFunctionSnippets#CustomTypeCODE1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomType.vb#customtypecode1)]
[!code-csharp[CustomTypePageFunctionSnippets#CustomTypeCODE2](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomType.cs#customtypecode2)]
[!code-vb[CustomTypePageFunctionSnippets#CustomTypeCODE2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomType.vb#customtypecode2)]

[!code-xaml[CustomTypePageFunctionSnippets#CustomTypePageFunctionMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml#customtypepagefunctionmarkup1)]
[!code-xaml[CustomTypePageFunctionSnippets#CustomTypePageFunctionMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml#customtypepagefunctionmarkup2)]

[!code-csharp[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml.cs#customtypepagefunctioncodebehind1)]
[!code-vb[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomTypePageFunction.xaml.vb#customtypepagefunctioncodebehind1)]
[!code-csharp[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml.cs#customtypepagefunctioncodebehind2)]
[!code-vb[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomTypePageFunction.xaml.vb#customtypepagefunctioncodebehind2)]

İçin tür bağımsız değişkenleri, <xref:System.Windows.Navigation.PageFunction%601> bir arama sayfası ile çağrılan sayfa arasındaki iletişimin temelini sağlar ve aşağıdaki bölümlerde ele alınmıştır.

Gördüğünüz gibi, bir <xref:System.Windows.Navigation.PageFunction%601> öğesinin bildirimiyle tanımlanan tür, verileri bir <xref:System.Windows.Navigation.PageFunction%601> ' dan çağırma sayfasına döndürmekte önemli bir rol oynar.

### <a name="calling-a-pagefunction-and-passing-parameters"></a>PageFunction çağırma ve parametreleri geçirme

Bir sayfayı çağırmak için, çağıran sayfanın çağrılan sayfanın örneğini oluşturması ve <xref:System.Windows.Navigation.NavigationService.Navigate%2A> yöntemi kullanılarak buna gitmeniz gerekir. Bu, çağıran sayfanın, çağrılan sayfa tarafından toplanmakta olan veriler için varsayılan değerler gibi ilk verileri çağrılan sayfaya geçmesini sağlar.

Aşağıdaki kod, çağırma sayfasından parametreleri kabul etmek için parametresiz bir oluşturucuya sahip çağrılan sayfayı gösterir.

[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind1)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind1)]
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind2)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind2)]
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND3](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind3)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind3)]
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND4](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind4)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind4)]

Aşağıdaki kod, çağrılan sayfanın örneğini oluşturmak ve bunu <xref:System.Windows.Documents.Hyperlink.Click> bir ilk dize <xref:System.Windows.Documents.Hyperlink> değeri geçirmek için olayını işleyen arama sayfasını gösterir.

[!code-xaml[StructuredNavigationSample#PassingDataMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#passingdatamarkup2)]
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind1)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind1)]
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind2)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind2)]
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND3](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind3)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind3)]

Çağrılan sayfaya parametreleri geçirmek zorunda değilsiniz. Bunun yerine şunları yapabilirsiniz:

- Çağırma sayfasından:

  1. Parametresiz oluşturucuyu kullanarak <xref:System.Windows.Navigation.PageFunction%601> çağrılan öğesini oluştur.

  2. Parametreleri ' de <xref:System.Windows.Application.Properties%2A>depolayın.

  3. Çağrılan <xref:System.Windows.Navigation.PageFunction%601>öğesine gidin.

- Çağrılan <xref:System.Windows.Navigation.PageFunction%601>:

  - İçinde <xref:System.Windows.Application.Properties%2A>depolanan parametreleri alın ve kullanın.

Ancak, kısa bir süre içinde gördüğünüz gibi, çağrılan sayfada döndürülen verileri toplamak için kod örneğini kullanmanız ve çağrılan sayfaya gitmeniz gerekir. Bu nedenle <xref:System.Windows.Navigation.PageFunction%601> , etkin tutulması gerekir; Aksi halde, bir sonraki <xref:System.Windows.Navigation.PageFunction%601>öğesine [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] gittiğinizde parametresiz oluşturucuyu <xref:System.Windows.Navigation.PageFunction%601> kullanarak örneği oluşturur.

Ancak çağrılan sayfanın dönebilmesi için, çağıran sayfa tarafından alınabilecek verileri döndürmesi gerekir.

### <a name="returning-task-result-and-task-data-from-a-task-to-a-calling-page"></a>Görev sonucu ve görev verilerini bir görevden bir arama sayfasına döndürme

Kullanıcı çağrılan sayfayı kullanmayı bitirdikten sonra, bu örnekte Tamam ya da Iptal düğmelerine basarak, çağrılan sayfanın döndürmesi gerekir. Çağıran sayfa, kullanıcıdan veri toplamak için çağrılan sayfayı kullandığından, çağıran sayfa iki tür bilgi gerektirir:

1. Kullanıcının çağrılan sayfayı (Tamam düğmesine veya bu örnekteki Iptal düğmesine basarak) iptal edilip edilmeyeceğini belirtir. Bu, çağıran sayfanın kullanıcıdan topladığı verilerin kullanılıp kullanılmayacağını belirlemesine olanak sağlar.

2. Kullanıcı tarafından sağlanmış olan veriler.

Bilgi <xref:System.Windows.Navigation.PageFunction%601> döndürmek için <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> yöntemini uygular. Aşağıdaki kod nasıl çağrılacağını gösterir.

[!code-csharp[StructuredNavigationSample#ReturnCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#returncodebehind1)]
[!code-vb[StructuredNavigationSample#ReturnCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#returncodebehind1)]
[!code-csharp[StructuredNavigationSample#ReturnCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#returncodebehind2)]
[!code-vb[StructuredNavigationSample#ReturnCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#returncodebehind2)]

Bu örnekte, bir Kullanıcı İptal düğmesine basarsa, bir değeri `null` çağırma sayfasına döndürülür. Bunun yerine Tamam düğmesine basıldığında, Kullanıcı tarafından verilen dize değeri döndürülür. <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A>, verilerinizi `protected virtual` çağırma sayfasına döndürmek için çağırdığınız bir yöntemdir. Verilerinizin, türü bağımsız değişkeni <xref:System.Windows.Navigation.ReturnEventArgs%601> <xref:System.Windows.Navigation.ReturnEventArgs%601.Result%2A> döndüren değerin türünü belirten genel türün bir örneğinde paketlenmesi gerekir. Bu şekilde, belirli bir tür bağımsız değişkeni <xref:System.Windows.Navigation.PageFunction%601> ile bir bildirdiğinizde, bir <xref:System.Windows.Navigation.PageFunction%601> öğesinin tür bağımsız değişkeni tarafından belirtilen türün bir örneğini döndürmediğini siz belirtmezsiniz. Bu örnekte, tür bağımsız değişkeni ve sonuç olarak, dönüş değeri türündedir <xref:System.String>.

Çağrıldığında, çağıran sayfanın dönüş değerini <xref:System.Windows.Navigation.PageFunction%601>alma yöntemi olması gerekir. <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> Bu nedenle, <xref:System.Windows.Navigation.PageFunction%601> işlenecek sayfaları çağıran <xref:System.Windows.Navigation.PageFunction%601.Return> olayı uygular. Çağrıldığında, <xref:System.Windows.Navigation.PageFunction%601.Return> ortaya çıkar, bu nedenle arama sayfası bildirimi almak için ile <xref:System.Windows.Navigation.PageFunction%601.Return> kayıt yapabilir. <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A>

[!code-csharp[StructuredNavigationSample#ProcessResultCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#processresultcodebehind1)]
[!code-vb[StructuredNavigationSample#ProcessResultCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#processresultcodebehind1)]
[!code-csharp[StructuredNavigationSample#ProcessResultCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#processresultcodebehind2)]
[!code-vb[StructuredNavigationSample#ProcessResultCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#processresultcodebehind2)]

### <a name="removing-task-pages-when-a-task-completes"></a>Görev tamamlandığında görev sayfalarını kaldırma

Çağrılan bir sayfa döndürüldüğünde ve Kullanıcı çağrılan sayfayı iptal etmediyse, çağıran sayfa Kullanıcı tarafından sağlanmış olan verileri işler ve çağrılan sayfadan de döndürülür. Bu şekilde veri alımı genellikle yalıtılmış bir etkinliktir; çağrılan sayfa döndürüldüğünde, çağıran sayfanın daha fazla veri yakalamak için yeni bir arama sayfası oluşturması ve bu sayfada gezinilmesi gerekir.

Ancak, çağrılan bir sayfa günlükten kaldırılmadığı takdirde, bir Kullanıcı, çağıran sayfanın önceki bir örneğine geri gidebilecektir. Günlükte saklanan <xref:System.Windows.Navigation.PageFunction%601> bir değer, <xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A> özelliği tarafından belirlenir. Varsayılan olarak, çağrıldığında bir sayfa işlevi otomatik olarak kaldırılır <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> çünkü <xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A> olarak ayarlanır `true`. Çağrıldıktan sonra <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> bir sayfa işlevini gezinme geçmişinde tutmak için, olarak `false`ayarlayın <xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A> .

<a name="Other_Types_of_Structured_Navigation"></a>

## <a name="other-types-of-structured-navigation"></a>Diğer yapılandırılmış gezinti türleri

Bu konuda, bir <xref:System.Windows.Navigation.PageFunction%601> en temel kullanımı, çağrı/dönüş yapılandırılmış gezintiyi desteklemek için gösterilmektedir. Bu temel, daha karmaşık türlerde yapısal gezinti oluşturma olanağı sağlar.

Örneğin, bazen bir kullanıcının yeterli miktarda veri toplamak veya bir görevi gerçekleştirmek için bir arama sayfası için birden çok sayfa gerekir. Birden çok sayfanın kullanımı "sihirbaz" olarak adlandırılır.

Diğer durumlarda, uygulamalar etkin şekilde çalışacak şekilde yapılandırılmış gezintiye bağlı karmaşık gezinti topolojilerine sahip olabilir. Daha fazla bilgi için bkz. [gezinti topolojilerine genel bakış](navigation-topologies-overview.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Navigation.PageFunction%601>
- <xref:System.Windows.Navigation.NavigationService>
- [Gezinti Topolojilerine Genel Bakış](navigation-topologies-overview.md)
