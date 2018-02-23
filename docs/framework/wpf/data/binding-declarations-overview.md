---
title: "Bağlama Bildirimlerine Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- markup extensions [WPF]
- data binding [WPF], declarations
- object element syntax [WPF]
- binding data [WPF], declarations
- syntax [WPF], object elements
- binding declarations [WPF]
ms.assetid: b97fd626-4c0d-4761-872a-2bca5820da2c
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 615b92d264b91ab5b267d5e79ab829b8afa489cd
ms.sourcegitcommit: 973a12d1e6962cd9a9c263fbfaad040ec8267fe9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/22/2018
---
# <a name="binding-declarations-overview"></a>Bağlama Bildirimlerine Genel Bakış
Bu konuda bir bağlama bildirebilir farklı yolları açıklanmaktadır.  
  
 
  
<a name="Prereq"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konu okumadan önce kavram ve İşaretleme uzantıları kullanımını tanıdık önemlidir. Biçimlendirme uzantıları hakkında daha fazla bilgi için bkz: [biçimlendirme uzantıları ve WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
 Bu konu, veri bağlama kavramlarını kapsamaz. Veri bağlama kavramlarını tartışma için bkz [veri bağlama genel bakış](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
<a name="BindinginXAML"></a>   
## <a name="declaring-a-binding-in-xaml"></a>XAML'de bağlama bildirme  
 Bu bölümde bir bağlama XAML'de bildirmek nasıl açıklanmaktadır.  
  
<a name="MarkupExtensionSyntax"></a>   
### <a name="markup-extension-usage"></a>Biçimlendirme uzantısı kullanımı  
 <xref:System.Windows.Data.Binding> bir biçimlendirme uzantısıdır. Bir bağlama bildirmek için bağlama uzantısı kullandığınızda, aşağıdaki yan tümceleri bir dizi bildirimi oluşur `Binding` anahtar sözcüğü ve virgülle (,) ayırarak. Bağlama bildirimindeki yan tümceleri herhangi bir sırada olabilir ve birçok olası birleşimler vardır. Yan tümceleri olan *adı*=*değeri* çiftleri nerede *adı* adı <xref:System.Windows.Data.Binding> özelliği ve *değeri* olduğu özelliği için ayar değeri.  
  
 Bağlama bildirimi dizeleri biçimlendirmede oluştururken, hedef nesnenin belirli bağımlılık özelliği eklenmelidir. Aşağıdaki örnekte nasıl bağlanacağını gösterir <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> bağlama uzantısını kullanarak, belirtme özelliği <xref:System.Windows.Data.Binding.Source%2A> ve <xref:System.Windows.Data.Binding.Path%2A> özellikleri.  
  
 [!code-xaml[SimpleBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#L37-L37)]  
  
 Özelliklerinin çoğu belirtebilirsiniz <xref:System.Windows.Data.Binding> bu şekilde sınıfı. Bağlama uzantısı bir listesi için de hakkında daha fazla bilgi için <xref:System.Windows.Data.Binding> bağlama uzantısı kullanarak ayarlanamaz özelliklerine bakın [bağlama biçimlendirme uzantısı](../../../../docs/framework/wpf/advanced/binding-markup-extension.md) genel bakış.  
  
<a name="ObjectElementSyntax"></a>   
### <a name="object-element-syntax"></a>Nesne öğesi sözdizimi  
 Nesne öğesi sözdizimi bağlama bildirimi oluşturmak için bir alternatiftir. Çoğu durumda, biçimlendirme uzantısı veya nesne öğesi sözdizimini kullanarak belirli bir avantajı yoktur. Ancak, biçimlendirme uzantısı, özellik değeri hiçbir tür dönüştürme var, bir dize olmayan türde olduğunda gibi senaryonuza desteklemeyen durumlarda nesne öğesi sözdizimi kullanmanız gerekir.  
  
 Nesne öğesi sözdizimi ve biçimlendirme uzantısı kullanımı örneği verilmiştir:  
  
 [!code-xaml[BindConversionMarkup#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindConversionMarkup/CSharp/Page1.xaml#1)]  
  
 Örnek bağlar <xref:System.Windows.Controls.TextBlock.Foreground%2A> uzantı sözdizimini kullanarak bir bağlama bildirme tarafından özelliği. İçin bağlama bildirimi <xref:System.Windows.Controls.TextBlock.Text%2A> özelliği nesne öğesi sözdizimini kullanır.  
  
 Farklı koşullar hakkında daha fazla bilgi için bkz: [içinde XAML sözdizimi ayrıntı](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).  
  
<a name="MBandPB"></a>   
### <a name="multibinding-and-prioritybinding"></a>MultiBinding ve PriorityBinding  
 <xref:System.Windows.Data.MultiBinding> ve <xref:System.Windows.Data.PriorityBinding> XAML uzantısı sözdizimini desteklemez. Bu nedenle, bildirdiğiniz, nesne öğesi sözdizimini kullanmanız gerekir bir <xref:System.Windows.Data.MultiBinding> veya <xref:System.Windows.Data.PriorityBinding> XAML'de.  
  
<a name="BindinginCode"></a>   
## <a name="creating-a-binding-in-code"></a>Kod içinde bir bağlama oluşturma  
 Doğrudan özelliklerini ayarlamak için bir bağlama belirtmek için başka bir yol ise bir <xref:System.Windows.Data.Binding> kodu nesnesi. Aşağıdaki örnekte nasıl oluşturulacağını gösterir bir <xref:System.Windows.Data.Binding> nesne ve kodda özelliklerini belirtin.  Bu örnekte, `TheConverter` uygulayan bir nesne <xref:System.Windows.Data.IValueConverter> arabirimi.  
  
 [!code-csharp[BindConversion#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindConversion/CSharp/Window1.xaml.cs#1)]
 [!code-vb[BindConversion#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BindConversion/visualbasic/window1.xaml.vb#1)]  
  
 Bağladığınız nesne ise bir <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement> çağırabilirsiniz `SetBinding` yöntemi kullanmak yerine doğrudan nesneniz üzerinde <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType>. Bir örnek için bkz: [kod içinde bir bağlaması oluşturma](../../../../docs/framework/wpf/data/how-to-create-a-binding-in-code.md).  
  
<a name="Path_Syntax"></a>   
## <a name="binding-path-syntax"></a>Bağlama yol sözdizimi  
 Kullanım <xref:System.Windows.Data.Binding.Path%2A> özelliği bağlamak istediğiniz kaynak değeri belirtmek için:  
  
-   En basit durumda, <xref:System.Windows.Data.Binding.Path%2A> özellik değeri gibi bağlama için kullanılacak kaynak nesnenin özelliğinin adıdır `Path=PropertyName`.  
  
-   Bir özelliğin alt özellikleri de benzer bir sözdizimi tarafından belirtilebilir [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)]. Örneğin, yan tümcesi `Path=ShoppingCart.Order` alt bağlamayı ayarlar `Order` nesne veya özelliğin `ShoppingCart`.  
  
-   Eklenen bir özellik bağlamak için ekli özellik parantezler yerleştirin. Örneğin, ekli özelliğine bağlamak için <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>, söz dizimi `Path=(DockPanel.Dock)`.  
  
-   Dizin oluşturucular bir özelliğin özellik adı dizin oluşturucu burada uygulanan aşağıdaki köşeli ayraç içinde belirtilebilir. Örneğin, yan tümcesi `Path=ShoppingCart[0]` , özelliğin iç dizininin "0" sabit dizesini nasıl işlediğini karşılık gelen dizine bağlamayı ayarlar. İç içe dizin oluşturucular da desteklenir.  
  
-   İçinde dizin oluşturucular ve alt karışabilir bir `Path` yan tümcesi; Örneğin, `Path=ShoppingCart.ShippingInfo[MailingAddress,Street].`  
  
-   Dizin oluşturucular içinde virgülle (,) ayırarak birden çok dizin oluşturucu parametresi olabilir. Her parametre türü parantezler ile belirtilebilir. Örneğin, sahip `Path="[(sys:Int32)42,(sys:Int32)24]"`, burada `sys` eşlenmiş `System` ad alanı.  
  
-   Kaynak bir koleksiyon görünümü geçerli öğenin bir eğik çizgi (/) belirtilebilir. Örneğin, yan tümcesi `Path=/` görünümünde geçerli öğeye bağlamayı ayarlar. Kaynak koleksiyonu olduğunda bu sözdizimini varsayılan koleksiyon görünümü geçerli öğesini belirtir.  
  
-   Özellik adları ve eğik çizgi koleksiyonları özellikler gezinmesine birleştirilebilir. Örneğin, `Path=/Offices/ManagerName` içeren kaynak koleksiyonunun güncel öğesini belirtir bir `Offices` da bir koleksiyon özelliği. Kendi güncel öğesi içeren bir nesne olan bir `ManagerName` özelliği.  
  
-   İsteğe bağlı olarak, bir nokta (.) yolu güncel kaynağa bağlamak için kullanılabilir. Örneğin, `Text="{Binding}"` eşdeğerdir `Text="{Binding Path=.}"`.  
  
### <a name="escaping-mechanism"></a>Kaçış mekanizması  
  
-   ([]) Dizin oluşturucular içinde düzeltme işareti karakteri (^) sonraki karakteri atlar.  
  
-   Ayarlarsanız <xref:System.Windows.Data.Binding.Path%2A> XAML'de, ayrıca (XML varlıkları kullanarak) XML dil tanımına özel belirli karakterler atlamanız gerekir:  
  
    -   Kullanım `&` değerinden kaçınmak için "&".  
  
    -   Kullanım `>` bitiş etiketi kaçınmak için ">".  
  
-   Biçimlendirme uzantısı sözdizimi kullanarak bir öznitelik içindeki tüm bağlamayı tanımlıyorsa, ayrıca, atlamanız gerekir (ters eğik çizgi kullanarak \\) için özel karakterler [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] biçimlendirme uzantısı ayrıştırıcısına:  
  
    -   Ters eğik çizgi (\\) kaçış karakteri.  
  
    -   Özellik adı eşittir (=) özellik değerinden ayırır.  
  
    -   Virgül (,) özellikleri ayırır.  
  
    -   Sağ kaşlı ayraç (}) biçimlendirme uzantısı sonudur.  
  
<a name="Default"></a>   
## <a name="default-behaviors"></a>Varsayılan davranışları  
 Varsayılan davranış aşağıdaki gibidir değilse bildiriminde belirtilen.  
  
-   Tür dönüşümü bağlama kaynağı ve bağlama hedef değeri arasında dener varsayılan dönüştürücü oluşturulur. Bir dönüştürme yapılamazsa varsayılan dönüştürücü döndürür `null`.  
  
-   Ayarlanmamış ise <xref:System.Windows.Data.Binding.ConverterCulture%2A>, bağlama altyapısı kullanır `Language` bağlama hedef nesnenin özellik. XAML'de bu "en-US" varsayılan olarak veya bir açık olarak ayarlandıysa değer kök öğesi (veya herhangi bir öğe) sayfanın devralır.  
  
-   Bağlama sürece zaten bir veri bağlamı (örneğin, bir üst öğeden gelen devralınan veri bağlamı) ve hangi öğesi veya o bağlam tarafından döndürülen koleksiyonu başka yolu değişiklik gerektirmeden bağlama için uygun bir bildirim bağlama olabilir hiçbir yan tümceleri hiç: `{Binding}` genellikle bir bağlama verileri, burada bir koleksiyon bağlama davranır stil oluşturma için belirtilen yolu budur. Daha fazla bilgi için "Tüm nesneleri kaynak olarak kullanılan bir bağlama" bölümüne bakın [bağlama kaynaklarına genel bakış](../../../../docs/framework/wpf/data/binding-sources-overview.md).  
  
-   Varsayılan <xref:System.Windows.Data.Binding.Mode%2A> tek yönlü ve bağlı bağımlılık özelliği bağlı olarak iki yönlü arasında değişir. Her zaman açık olarak bağlamanız istenilen davranışa sahip olduğundan emin olmak için bağlama modunu bildirebilirsiniz. Genel, kullanıcı tarafından düzenlenebilir denetim özelliklerinde gibi <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> ve <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A?displayProperty=nameWithType>, ancak diğer özelliklerin çoğu tek yönlü bağlamalar iki yönlü bağlamaları için varsayılan.  
  
-   Varsayılan <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> değeri arasında değişir <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> ve <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> ilişkili bağımlılık özelliği de bağlı olarak. Çoğu bağımlılık özellikleri için varsayılan değer <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>, sırada <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> özelliğinin varsayılan değeri <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Bağlamaya Genel Bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)  
 [Veri Bağlama](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [PropertyPath XAML Söz Dizimi](../../../../docs/framework/wpf/advanced/propertypath-xaml-syntax.md)
