---
title: "Bağımlılık Özelliği Değer Önceliği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dependency properties [WPF], classes as owners
- dependency properties [WPF], metadata
- classes [WPF], owners of dependency properties
- metadata [WPF], dependency properties
ms.assetid: 1fbada8e-4867-4ed1-8d97-62c07dad7ebc
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d95cd0545fa4800f159f4e5e0f661cf7bddc6548
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="dependency-property-value-precedence"></a>Bağımlılık Özelliği Değer Önceliği
<a name="introduction"></a>Bu konuda açıklanmaktadır nasıl işleyişini [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] özellik sistemi bir bağımlılık özelliğinin değeri etkileyebilir ve hangi yönlerini özelliği tarafından sistem geçerli bir özellik için geçerli değerini öncelik açıklar.  
    
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konu bağımlılık özellikleri varolan bağımlılık özelliklerinin tüketicisi açısından anladığınızı varsayar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sınıfları ve okuma [bağımlılık özelliklerine genel bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md). Bu konudaki örnekleri izlemek için de anlamanız gerekir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ve nasıl yazıldığını bilmeniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar.  
  
<a name="intro"></a>   
## <a name="the-wpf-property-system"></a>WPF özellik sistemi  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Özellik sistemi sunar bağımlılık özellikleri değerine sahip olacak şekilde güçlü bir yöntemdir, çeşitli etkenlere, gerçek zamanlı özellik doğrulama, geç bağlama ve değerleri yapılan değişikliklerle ilgili özellikleri bildirme gibi özellikleri etkinleştirme tarafından belirlenemedi diğer özellikler için. Bağımlılık özellik değerleri belirlemek için kullanılan mantığı ve tam sırası makul karmaşık. Bu sırada, gereksiz özellik ayarı önlemenize yardımcı olur ve ayrıca karışıklığı yukarı temizleyin bilerek tam olarak neden bazı etkileyebilecek veya bir bağımlılık özelliği değerini düşündüğünüz girişimi, beklenen değer kaynaklanan yukarı sona.  
  
<a name="multiple_sets"></a>   
## <a name="dependency-properties-might-be-set-in-multiple-places"></a>Bağımlılık özellikleri "birden fazla yerde ayarlanmış olabilir"  
 Aşağıdaki örnekte olduğu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] burada aynı özelliği (<xref:System.Windows.Controls.Control.Background%2A>) üç farklı "değeri etkileyebilir işlemleri ayarlanmış".  
  
 [!code-xaml[PropertiesOvwSupport#DPPrecedence](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml#dpprecedence)]  
  
 Burada, hangi renk, geçerli bekliyorsunuz — kırmızı, yeşil veya mavi?  
  
 Animasyonlu değerleri ve zorlama dışında yerel özellik kümeleri en yüksek öncelik ayarlanır. Yerel olarak bir değer ayarlarsanız değeri, hatta herhangi stilleri veya denetim şablonları uyulacaktır olduğunu bekleyebilirsiniz. Örneğin, burada <xref:System.Windows.Controls.Control.Background%2A> kırmızı yerel olarak ayarlayın. Bu nedenle, aksi takdirde, kapsamı içindeki bu türdeki tüm öğeler için geçerli olur örtülü bir stil olsa bile bu kapsamda tanımlanan stili vermiş en yüksek önceliğe değil <xref:System.Windows.Controls.Control.Background%2A> özellik değeri.  Bu düğme örnekten yerel değerin kırmızı kaldırdıysanız, stil öncelik sonra var ve düğme stili arka plan değeri elde edebilirsiniz.  Düğme fare üzerine ise mavi ve yeşil Aksi durumda olacak stil içinde tetikleyiciler, önceliklidir.  
  
<a name="listing"></a>   
## <a name="dependency-property-setting-precedence-list"></a>Bağımlılık özellik ayarı önceliği listesi  
 Aşağıdaki özellik sistemi bağımlılık özellikleri çalışma zamanı değerlerini atarken kullanan kesin sırasıdır. En yüksek öncelik ilk önce listelenir. Bu liste bazı yapılan Genelleştirme genişletir [bağımlılık özelliklerine genel bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
1.  **Özellik sistem zorlama.** Zorlama hakkında daha fazla bilgi için bkz: [zorlama, animasyon ve temel değer](#animations) bu konuda daha sonra.  
  
2.  **Etkin bir animasyon veya tutma davranışı animasyonları.** Bu değeri yerel olarak ayarlandıysa bile pratik etkili olması için bir özellik animasyonun temel (unanimated) değeri önceliklidir kurabilmesi gerekir. Ayrıntılar için bkz [zorlama, animasyon ve temel değer](#animations) bu konuda daha sonra.  
  
3.  **Yerel değer.** Ayrıca bir öznitelik veya özellik öğe olarak ayarına karşılık gelir "sarmalayıcı" özelliğini kolaylık aracılığıyla yerel bir değer ayarlanabilir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], veya bir çağrı tarafından <xref:System.Windows.DependencyObject.SetValue%2A> [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] belirli bir kopya özelliğini kullanarak. Bir bağlama veya bir kaynak kullanarak yerel bir değer ayarlarsanız, doğrudan bir değer olarak ayarlanmışsa bu her öncelik görür.  
  
4.  **TemplatedParent şablonu özellikleri.** Bir öğeye sahip bir <xref:System.Windows.FrameworkElement.TemplatedParent%2A> bir şablon bir parçası olarak oluşturduysanız (bir <xref:System.Windows.Controls.ControlTemplate> veya <xref:System.Windows.DataTemplate>). Bu geçerli olduğunda hakkında daha fazla bilgi için bkz [TemplatedParent](#templatedparent) bu konuda daha sonra. Şablon içerisinde, aşağıdaki öncelik geçerlidir:  
  
    1.  Gelen tetikler <xref:System.Windows.FrameworkElement.TemplatedParent%2A> şablonu.  
  
    2.  Özellik kümeleri (genellikle ile [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] öznitelikleri) içinde <xref:System.Windows.FrameworkElement.TemplatedParent%2A> şablonu.  
  
5.  **Örtük stili.** Yalnızca geçerli `Style` özelliği. `Style` Özelliği tarafından herhangi bir stil kaynak o öğeye türüyle eşleşen bir anahtarı ile doldurulur. Stil kaynağı sayfa veya uygulama bulunmalıdır; örtük stil kaynağı için arama Temalar devam etmez.  
  
6.  **Stil tetikler.** Tetikleyiciler stilleri sayfasından veya uygulama içinde (Bu stiller açık veya örtülü stil olabilir, ancak varsayılan stillerini değil daha düşük önceliğe sahip).  
  
7.  **Şablon tetikler.** Hiçbir tetikleyici bir stil şablonda ya da doğrudan uygulanan bir şablon.  
  
8.  **Stil ayarlayıcılar.** Gelen değerleri bir <xref:System.Windows.Setter> stilleri sayfasından veya uygulama içinde.  
  
9. **Varsayılan (tema) stili.** Bu geçerli olduğunda ve tema stilleri tema stilleri içinde şablonları nasıl ilişkili olduğunu hakkında daha fazla bilgi için bkz: [varsayılan (tema) stilleri](#themestyles) bu konuda daha sonra. Varsayılan stil içinde aşağıdaki öncelik sırası geçerlidir:  
  
    1.  Tema stili etkin tetikler.  
  
    2.  Tema stilde ayarlayıcılar.  
  
10. **Devralma.** Bunlar bir uygulama boyunca her bir öğede özellikle ayarlanmaması şekilde birkaç bağımlılık özellikleri alt öğelerine üst öğeden değerlerine devralır. Ayrıntılar için bkz: [özellik değeri devralma](../../../../docs/framework/wpf/advanced/property-value-inheritance.md).  
  
11. **Bağımlılık özelliği meta verileri varsayılan değeri.** Verilen bağımlılık özelliği, belirli özellik özellik sistem kayıt tarafından belirlenen varsayılan bir değer olabilir. Ayrıca, bir bağımlılık özelliği devral türetilen sınıflar, bir tür başına temelinde (varsayılan değeri dahil) bu meta verileri geçersiz kılmak için seçeneğiniz vardır. Bkz: [bağımlılık özelliği meta verileri](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md) daha fazla bilgi için. Devralma devralınmış bir özellik için varsayılan değer önce denetlendiği bir üst öğesi varsayılan değer bir alt öğe önceliklidir.  Sonuç olarak, devralınabilir bir özelliği herhangi bir yere ayarlanmazsa, varsayılan değer olarak kök veya üst belirtilen yerine alt öğesi varsayılan değer kullanılır.  
  
<a name="templatedparent"></a>   
## <a name="templatedparent"></a>TemplatedParent  
 Öncelik öğesi olarak TemplatedParent doğrudan standart uygulama biçimlendirmede bildirme öğenin herhangi bir özelliği için geçerli değildir. Şablon uygulama aracılığıyla varlığı içine gelen alt öğeleri görsel ağaç içinde TemplatedParent kavramı vardır. Ne zaman özellik sistemi arar <xref:System.Windows.FrameworkElement.TemplatedParent%2A> şablon için bir değer, arama o öğeye oluşturulan şablon. Özellik değerlerinin <xref:System.Windows.FrameworkElement.TemplatedParent%2A> şablonu genellikle hareket alt öğe üzerinde bir yerel değer olarak ayarlanmış, ancak bu daha düşük öncelik yerel değerin karşı şablonları olası paylaşıldığından var. olur. Ayrıntılar için bkz <xref:System.Windows.FrameworkElement.TemplatedParent%2A>.  
  
<a name="style_property"></a>   
## <a name="the-style-property"></a>Stil özelliği  
 Daha önce açıklanan arama sırasını biri dışındaki tüm olası bağımlılık özellikleri için geçerlidir: <xref:System.Windows.FrameworkElement.Style%2A> özelliği. <xref:System.Windows.FrameworkElement.Style%2A> Özelliği olduğundan benzersiz, kendisini biçimlendirilmiş edilemez olduğunu, 5-8 öncelik öğeleri geçerli değildir. Ayrıca, animasyon ya da zorlama <xref:System.Windows.FrameworkElement.Style%2A> önerilmez (ve animasyon <xref:System.Windows.FrameworkElement.Style%2A> özel animasyon sınıfı gerektirir). Bu, üç şekilde bırakır <xref:System.Windows.FrameworkElement.Style%2A> özelliği ayarlanmış olmalıdır:  
  
-   **Açık stili.** <xref:System.Windows.FrameworkElement.Style%2A> Özelliği doğrudan ayarlayın. Çoğu senaryoda, stil satır içi olarak tanımlanan değil, ancak bunun yerine bir kaynak olarak açık anahtar tarafından başvuruluyor. Bu durumda yerel değeri, öncelik öğesi 3 değilmiş gibi stil özelliği yapar.  
  
-   **Örtük stili.** <xref:System.Windows.FrameworkElement.Style%2A> Özelliği doğrudan ayarlanmadı. Ancak, <xref:System.Windows.FrameworkElement.Style%2A> kaynak arama sırası (sayfa, uygulama) düzeyde var ve stil olduğu uygulanacak türüyle eşleşen bir kaynak anahtarı kullanarak anahtarlanır. Bu durumda, <xref:System.Windows.FrameworkElement.Style%2A> özelliğinin kendisini görevi gören bir öncelik sırası öğe 5 olarak tanımlanan tarafından. Bu durum kullanılarak algılanabilir <xref:System.Windows.DependencyPropertyHelper> karşı <xref:System.Windows.FrameworkElement.Style%2A> özelliği ve aramakta <xref:System.Windows.BaseValueSource.ImplicitStyleReference> sonuçları.  
  
-   **Varsayılan Stil**, olarak da bilinen **tema stili.** <xref:System.Windows.FrameworkElement.Style%2A> Özelliği doğrudan ayarlanmamış ve hatta olarak okuma yapacak `null` çalıştırma kadar. Bu durumda, parçası olduğu çalışma zamanı tema değerlendirme sürümünden stili gelen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sunu altyapısı.  
  
 Temalar alanında örtük stilleri türü tam olarak eşleşmelidir — bir `MyButton``Button`-türetilmiş bir sınıf için bir stil örtük olarak kullanmaz `Button`.  
  
<a name="themestyles"></a>   
## <a name="default-theme-styles"></a>Varsayılan (tema) stilleri  
 İle birlikte her denetim [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] varsayılan stilini sahiptir. Varsayılan stilini bu varsayılan stilini olası nedeni tema tarafından değişir bazen bir tema stili olarak adlandırılır.  
  
 Bir denetim tema stilinde bir ayarlayıcı bulunan kendi denetim şablonu için bir varsayılan stil içinde bulunan en önemli bilgileri kendi <xref:System.Windows.Controls.Control.Template%2A> özelliği. Varsayılan stiller hiçbir şablondan olsaydı, özel bir stil bir parçası olarak özel bir şablon olmadan bir denetim yok görsel görünümünü hiç gerekir. Varsayılan stili şablondan her denetim basit bir yapı görsel görünümünü verir ve ayrıca şablon ve ilgili denetim sınıfı görsel ağaçta tanımlanan özellikler arasındaki bağlantıları tanımlar. Her denetim bir dizi denetim görsel görünümünü tamamen şablon değiştirmeden etkileyebilir özellikler sunar. Örneğin, varsayılan görsel görünümünü göz önünde bulundurun bir <xref:System.Windows.Controls.Primitives.Thumb> bir bileşen olan denetimi, bir <xref:System.Windows.Controls.Primitives.ScrollBar>.  
  
 A <xref:System.Windows.Controls.Primitives.Thumb> özelleştirilebilir belirli özelliklere sahiptir. Varsayılan şablonu bir <xref:System.Windows.Controls.Primitives.Thumb> basit bir yapı oluşturur / görsel ağaç birkaç ile iç içe geçmiş <xref:System.Windows.Controls.Border> bir Eğim görünüm oluşturmak için bileşenleri. Şablonunun parçası olan bir özellik tarafından özelleştirme için açığa çıkarılması amaçlanıyorsa <xref:System.Windows.Controls.Primitives.Thumb> sınıfı bu özellik tarafından sunulmalıdır sonra bir [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md), şablonu içinde. Durumunda <xref:System.Windows.Controls.Primitives.Thumb>, bu Kenarlıklar çeşitli özelliklerini gibi bir şablon bağlama özellikleri paylaşmak <xref:System.Windows.Controls.Border.Background%2A> veya <xref:System.Windows.Controls.Border.BorderThickness%2A>. Ancak bazı diğer özellikler veya visual düzenlemeleri denetim şablonu sabit kodlanmış veya temayı doğrudan dönün ve tüm şablonu değiştirme eksikliği değiştirilemez değerlere bağlı. Bir özellik şablonlu bir üst öğeden gelir ve bir şablon bağlama tarafından gösterilmez, hedeflemek için kolay bir yolu olduğundan genellikle, bu stilleri tarafından düzeltilemez. Ancak bu özellik hala uygulanan şablon özellik değeri devralma veya varsayılan değer etkilenebileceğinden.  
  
 Tema stilleri bir tür anahtar tanımlarını olarak kullanın. Verilen öğe örneğine Temalar uygulandığında, ancak, bu tür için Temalar arama denetleyerek gerçekleştirilir <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> denetim özelliği. Örtülü stiller gibi değişmez değer türü kullanarak aksine budur. Değeri <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> uygulayan, (özelliğini değiştirmek hedeflenen yoludur, özellik düzeyinde ancak için bunun yerine, varsayılan değer özelliği meta verilerde değişiklik geçersiz) değişmemiştir olsa bile türetilmiş sınıflara devral. Bu yöneltme stil sahip olmaması türetilmiş öğelerin tema stilleri tanımlamak temel sınıflar etkinleştirir (veya daha da önemlisi, bu stili şablonda sahip değil ve böylece varsayılan görünümünü hiç olması gerekir). Bu nedenle, türetilen `MyButton` gelen <xref:System.Windows.Controls.Button> ve hala alırsınız <xref:System.Windows.Controls.Button> varsayılan şablonu. Denetim yazarı olsaydı `MyButton` ve farklı bir davranış istedi, bağımlılık özelliği meta verileri için geçersiz kılma <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> üzerinde `MyButton` farklı bir anahtar dönüp şablonu dahil olmak üzere ilgili tema stilleri tanımlamak için için `MyButton` ile paketin gerekir, `MyButton` denetim. Temalar, stil ve denetim yazma hakkında daha fazla bilgi için bkz: [denetimine genel bakış yazma](../../../../docs/framework/wpf/controls/control-authoring-overview.md).  
  
<a name="resources"></a>   
## <a name="dynamic-resource-references-and-binding"></a>Dinamik kaynak başvuruları ve bağlama  
 Dinamik kaynak başvuruları ve bağlama işlemleri aktarılma ayarlandıktan konumu önceliğini saygılı olun. Örneğin, yerel bir değere uygulanan dinamik bir kaynak 3 öncelik öğesi davranır, öncelik öğesi 9 ve benzeri bağlama tema stil içinde bir özellik ayarlayıcı için geçerlidir. Çünkü dinamik kaynak başvuruları ve bağlama hem sağlayabilmelidir uygulamayı çalıştırma durumundan değerleri almak, bu, belirli bir özellik için özellik değeri öncelik belirleme gerçek işlemi çalışma zamanına genişleten kapsar.  
  
 Dinamik kaynak başvuruları kesinlikle bakıldığında özellik sisteminin parçası olmayan, ancak kendi, yukarıda listelenen dizisi ile etkileşime giren bir arama sırası sahiptirler. Bu öncelik daha kapsamlı olarak belgelenmiştir [XAML kaynakları](../../../../docs/framework/wpf/advanced/xaml-resources.md). Bu öncelik temel toplamı olan: sayfa kök, uygulama, tema, sistem öğesi.  
  
 Dinamik kaynaklar ve bağlamaları Burada ayarlanan önceliği vardır, ancak değeri ertelendi. Bunun bir sonucu, dinamik kaynak ayarlayın veya yerel bir değere bağlama, yerel değerin herhangi bir değişiklik dinamik kaynak veya tamamen bağlama değiştirir olur. Bile çağırırsanız <xref:System.Windows.DependencyObject.ClearValue%2A> yöntemi yerel olarak ayarlanmış temizlemek için değer, dinamik kaynak veya bağlama geri yüklenmez. Aslında, çağırırsanız <xref:System.Windows.DependencyObject.ClearValue%2A> (hiçbir değişmez değer yerel değeri ile) yerinde dinamik kaynak ya da bağlama sahip bir özellik, bunlar tarafından temizlenir <xref:System.Windows.DependencyObject.ClearValue%2A> çok çağırın.  
  
<a name="setcurrentvalue"></a>   
## <a name="setcurrentvalue"></a>SetCurrentValue  
 <xref:System.Windows.DependencyObject.SetCurrentValue%2A> Yöntemi bir özelliği ayarlamak için başka bir yolu, ancak öncelik sırasına göre değil. Bunun yerine, <xref:System.Windows.DependencyObject.SetCurrentValue%2A> önceki değeri kaynağı geçersiz kılmadan bir özelliğin değerini değiştirmenize olanak tanır. Kullanabileceğiniz <xref:System.Windows.DependencyObject.SetCurrentValue%2A> yerel değerin öncelik değeri vermeden bir değer ayarlamak istediğiniz dilediğiniz zaman. Örneğin bir özellik tarafından bir tetikleyici kümesi ve başka bir değer aracılığıyla atanan <xref:System.Windows.DependencyObject.SetCurrentValue%2A>, özellik sistemi hala tetikleyici dikkate alır ve tetikleyici eylem oluşursa özelliğini değiştirir. <xref:System.Windows.DependencyObject.SetCurrentValue%2A>daha yüksek önceliğe sahip bir kaynak vermeden özelliğin değerini değiştirmenize olanak tanır. Benzer şekilde, kullanabileceğiniz <xref:System.Windows.DependencyObject.SetCurrentValue%2A> bağlama geçersiz kılmadan bir özelliğin değerini değiştirmek için.  
  
<a name="animations"></a>   
## <a name="coercion-animations-and-base-value"></a>Zorlama, animasyonları ve taban değeri  
 Zorlama ve animasyon her ikisi de hareket bu "temel değeri" adlandırılır bir değeri [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)]. Temel böylece ne olursa olsun değer 2 öğesi ulaşılana kadar yukarı öğeleri değerlendirme aracılığıyla belirlenir değerdir.  
  
 Bir animasyon için taban değeri animasyonun "Kimden" ve "İçin" belirli davranışları belirtmiyorsa veya animasyonun kasıtlı olarak tamamlandığında taban değeri döndürüyorsa animasyonlu değer üzerinde bir etkisi olabilir. Bu uygulamada görmek için çalıştırın [gelen için ve animasyon hedef değerleri örneği tarafından](http://go.microsoft.com/fwlink/?LinkID=159988). Herhangi bir "Kimden" animasyonda ilk yerel değerin farklı şekilde örnek dikdörtgen yükseklik yerel değerlerini ayarlamayı deneyin. Animasyonları "Kimden" değerlerini hemen kullanmaya başlamak ve bir kez başlatılan taban değeri değiştirin unutmayın. Animasyonun Durdur belirterek tamamlandığında animasyon önce bulunan değere geri dönmek için belirtebilir <xref:System.Windows.Media.Animation.FillBehavior>. Daha sonra normal öncelik taban değeri belirlenmesi için kullanılır.  
  
 Birden çok animasyon her animasyonlarına farklı noktalarından değeri önceliği büyük olasılıkla tanımlanmış tek bir özelliğe uygulanabilir. Ancak, animasyonlarına olası olur bileşik yalnızca daha yüksek önceliği animasyon uygulamak yerine bunların değerleri. Bu, tam olarak animasyonları nasıl tanımlanır ve hareketli değerin türü bağlıdır. Özellikleri hakkında daha fazla bilgi için bkz: [animasyon genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
 Zorlama tüm yüksek düzeyde geçerlidir. Zaten çalışan bir animasyon değeri zorlama tabi olur. Belirli varolan bağımlılık özellikleri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yerleşik zorlama sahip. Özel bir bağımlılık özelliği için özel bir bağımlılık özelliği için zorlama davranışı yazarak tanımladığınız bir <xref:System.Windows.CoerceValueCallback> ve özelliği oluşturduğunuzda, geri çağırma meta verilerinin bir parçası geçirme. Ayrıca bir türetilmiş sınıfta bu özellik meta verileri geçersiz kılarak zorlama varolan özellikler davranışını geçersiz kılabilirsiniz. Taban değeri zorlama kısıtlamalar uygulanır şekilde etkileşime zorlama bu kısıtlamalar sırada mevcut, ancak temel değer hala korunur. Bu nedenle, zorlama kısıtlamalarını sonraki kaldırılmış, zorlama en yakın değere olası temel bu değeri döndürür ve tüm kısıtlamaları kaldırılmış hemen sonra bir özelliğe zorlama etkisi çalışmayı durdurur. Zorlama davranış hakkında daha fazla bilgi için bkz: [bağımlılık özelliği geri çağrıları ve doğrulama](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md).  
  
<a name="triggers"></a>   
## <a name="trigger-behaviors"></a>Tetikleyici davranışları  
 Denetimleri tetikleyici davranışları temaları kendi varsayılan stilinde bir parçası olarak genellikle tanımlayın. Denetimlere yerel özelliklerini ayarlama Tetikleyiciler görsel olarak veya davranışsal kullanıcı odaklı olaylarına yanıt yapamamasına engelleyebilir. Denetim ya da durum özellikler için özellik tetikleyici en yaygın kullanımı olduğu gibi <xref:System.Windows.Controls.Primitives.Selector.IsSelected%2A>. Örneğin, varsayılan olarak, bir <xref:System.Windows.Controls.Button> devre dışı bırakıldı (için tetiklemek <xref:System.Windows.UIElement.IsEnabled%2A> olan `false`) sonra <xref:System.Windows.Controls.Control.Foreground%2A> tema stili değerdir ne denetimi "gri renkte" görüntülenmesine neden olur. Ancak yerel ayarlarsanız <xref:System.Windows.Controls.Control.Foreground%2A> değer normal gri kullanıma renk önceliği bile bu senaryoda özelliği tetiklenen yerel özellik kümeniz tarafından kılınır. Tema düzeyinde tetikleyici davranışları ve, unduly bu denetim için hedeflenen kullanıcı deneyimi ile engel olduğundan emin olun özelliklerinin değerlerini ayarını dikkatli olun.  
  
<a name="clearvalue"></a>   
## <a name="clearvalue-and-value-precedence"></a>ClearValue ve değer önceliği  
 <xref:System.Windows.DependencyObject.ClearValue%2A> Yöntemi sağlayan bir expedient anlamına gelir yerel olarak uygulanan herhangi bir öğede ayarlanan bağımlılık özelliği değerini temizleyin. Ancak, çağırma <xref:System.Windows.DependencyObject.ClearValue%2A> meta verilerde özelliği kayıt sırasında belirlenen varsayılan yeni geçerli değerini olduğunu garanti değil. Tüm diğer katılımcıların değeri önceliğinde hala etkin. Yalnızca yerel olarak ayarlanmış değer öncelik sırasından kaldırıldı. Örneğin, çağırırsanız <xref:System.Windows.DependencyObject.ClearValue%2A> bir özelliğe burada bu özellik ayrıca bir tema stili tarafından ayarlanır ve ardından tema değeri meta veri tabanlı varsayılan yerine yeni bir değer olarak uygulanır. İşlemin dışında tüm özellik değeri katılımcılar alabilir ve kayıtlı meta verileri varsayılan değeri ayarlamak istiyorsanız, bağımlılık özelliği meta verileri ve ardından sorgulama tarafından tam olarak varsayılan değer varsayılan değere yerel olarak kullanabileceğiniz edinebilirsiniz çağrısıyla özelliğini ayarlayın <xref:System.Windows.DependencyObject.SetValue%2A>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.DependencyObject>  
 <xref:System.Windows.DependencyProperty>  
 [Bağımlılık Özelliklerine Genel Bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Özel Bağımlılık Özellikleri](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [Bağımlılık Özelliği Geri Aramaları ve Doğrulama](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md)
