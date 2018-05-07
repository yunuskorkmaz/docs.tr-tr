---
title: RelativeSource MarkupExtension
ms.date: 03/30/2017
f1_keywords:
- RelativeSource
helpviewer_keywords:
- RelativeSource markup extensions [WPF]
- XAML [WPF], RelativeSource markup extension
ms.assetid: 26be4721-49b5-4717-a92e-7d54ad0d3a81
ms.openlocfilehash: 77caa7c84f63f90ae83df5685f93ba6d18f7436f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="relativesource-markupextension"></a>RelativeSource MarkupExtension
Özelliklerini belirtir bir <xref:System.Windows.Data.RelativeSource> içinde kullanılacak bağlama kaynağı, bir [bağlama biçimlendirme uzantısı](../../../../docs/framework/wpf/advanced/binding-markup-extension.md), veya ayarlarken <xref:System.Windows.Data.Binding.RelativeSource%2A> özelliği bir <xref:System.Windows.Data.Binding> XAML'de kurulan öğesi.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```xml  
<Binding RelativeSource="{RelativeSource modeEnumValue}" .../>  
```  
  
## <a name="xaml-attribute-usage-nested-within-binding-extension"></a>XAML Öznitelik Kullanımı (Bağlama uzantıları içinde iç içe geçmiş)  
  
```xml  
<object property="{Binding RelativeSource={RelativeSource modeEnumValue} ...}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a>XAML Nesne Öğesi Kullanımı  
  
```xml  
<Binding>  
  <Binding.RelativeSource>  
    <RelativeSource Mode="modeEnumValue"/>  
  </Binding.RelativeSource>  
</Binding>  
- or   
<Binding>  
  <Binding.RelativeSource>  
    <RelativeSource  
      Mode="FindAncestor"  
      AncestorType="{x:Type typeName}"  
      AncestorLevel="intLevel"  
    />  
  </Binding.RelativeSource>  
</Binding>  
```  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|`modeEnumValue`|Aşağıdakilerden biri:<br /><br /> -Dize belirteci `Self`; karşılık gelen bir <xref:System.Windows.Data.RelativeSource> ile oluşturulmuş kendi <xref:System.Windows.Data.RelativeSource.Mode%2A> özelliğini <xref:System.Windows.Data.RelativeSourceMode.Self>.<br />-Dize belirteci `TemplatedParent`; karşılık gelen bir <xref:System.Windows.Data.RelativeSource> ile oluşturulmuş kendi <xref:System.Windows.Data.RelativeSource.Mode%2A> özelliğini <xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>.<br />-Dize belirteci `PreviousData`; karşılık gelen bir <xref:System.Windows.Data.RelativeSource> ile oluşturulmuş kendi <xref:System.Windows.Data.RelativeSource.Mode%2A> özelliğini <xref:System.Windows.Data.RelativeSourceMode.PreviousData>.<br />-Aşağıda bilgi edinmek için `FindAncestor` modu.|  
|`FindAncestor`|Dize belirteci `FindAncestor`. Bu belirteci kullanarak moda girer bir `RelativeSource` bir üst türü ve isteğe bağlı olarak bir üst düzeyini belirtir. Bu karşılık gelen bir <xref:System.Windows.Data.RelativeSource> ile oluşturulmuş kendi <xref:System.Windows.Data.RelativeSource.Mode%2A> özelliğini <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>.|  
|`typeName`|İçin gerekli `FindAncestor` modu. Doldurur bir türün adını <xref:System.Windows.Data.RelativeSource.AncestorType%2A> özelliği.|  
|`intLevel`|İçin isteğe bağlı `FindAncestor` modu. Öncül düzeyi (Mantıksal ağaçta üst yön doğrultusunda değerlendirilen.)|  
  
## <a name="remarks"></a>Açıklamalar  
 `{RelativeSource TemplatedParent}` bağlama kullanımları bir denetimin UI ve bir denetimin mantığı ayrılması daha büyük bir kavramı adresleri anahtar bir yöntem ' dir. Bu, şablon tanımı içinden şablonlu üst öğeye (şablonun uygulandığı çalışma zamanı nesnesi örneği) bağlanmaya olanak verir. Bu durumda [TemplateBinding biçimlendirme uzantısı](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) aslında aşağıdaki bağlama ifadesi için bir toplu özelliktir: `{Binding RelativeSource={RelativeSource TemplatedParent}}`. `TemplateBinding` veya `{RelativeSource TemplatedParent}` kullanımları olan her ikisi de bir şablon tanımlayan XAML içinde yalnızca ilgilidir. Daha fazla bilgi için bkz: [TemplateBinding biçimlendirme uzantısı](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md)  
  
 `{RelativeSource FindAncestor}` esas olarak denetim şablonları veya tahmin edilebilir müstakil UI kompozisyonlarınıza, burada bir denetimi her zaman belirli bir üst türü görsel ağaçta olması beklenen durumlarda kullanılır. Örneğin, bir öğe denetimini öğelerinin kullanabilirsiniz `FindAncestor` öğelerin özelliklerine bağlamak için kullanımları üst üst denetim. Veya, bir şablon denetim oluşumuna parçası olan öğeleri kullanabilir `FindAncestor` bağlamaları aynı birleşim yapıyı üst öğe.  
  
 İçin nesne öğesi sözdiziminde `FindAncestor` ikinci nesne öğesi sözdizimi özellikle için kullanıldığından XAML sözdizimi bölümlerinde gösterilen modu `FindAncestor` modu. `FindAncestor` mod gerektiren bir <xref:System.Windows.Data.RelativeSource.AncestorType%2A> değeri. Ayarlamalısınız <xref:System.Windows.Data.RelativeSource.AncestorType%2A> kullanarak bir öznitelik olarak bir [x: Type işaretleme uzantısı](../../../../docs/framework/xaml-services/x-type-markup-extension.md) aranacak üst tür referansı. <xref:System.Windows.Data.RelativeSource.AncestorType%2A> Çalışma zamanında bağlama isteği işlendiğinde değeri kullanılır.  
  
 İçin `FindAncestor` modu, isteğe bağlı özellik <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> durumlarda üst arama belirsizliğini ortadan kaldırmak yardımcı olabilecek büyük olasılıkla birden fazla üst öğe ağacında varolan türü olduğu.  
  
 Nasıl kullanılacağı hakkında daha fazla bilgi için `FindAncestor` modu, bkz: <xref:System.Windows.Data.RelativeSource>.  
  
 `{RelativeSource Self}` Senaryo için yararlıdır burada bir örneğinin bir özellik aynı örneği (örneğin, zorlama) herhangi bir genel bağımlılık özelliği ilişkisi ve başka bir özelliğin değeri zaten bağlı bu iki özellik arasında mevcut. İki özellik mevcut bir nesne üzerinde olduğunu değerlerin tam anlamıyla özdeş (ve aynı yazılan gibi), aynı zamanda uygulanabilir nadir olmasına rağmen bir `Converter` sahip bir bağlama parametresi `{RelativeSource Self}`ve kaynak arasında dönüştürmek için dönüştürücüyü kullanın ve Hedef türü. Başka bir senaryo için `{RelativeSource Self}` parçası olarak bir <xref:System.Windows.MultiDataTrigger>.  
  
 Örneğin, aşağıdaki XAML tanımlayan bir <xref:System.Windows.Shapes.Rectangle> değerin ne olursa olsun için girilen öğesi böyle <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.Shapes.Rectangle> her zaman bir kare olur: `<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`  
  
 `{RelativeSource PreviousData}` Veri şablonlarında ya da bağlamaları veri kaynağı olarak bir koleksiyon burada kullandığınız durumlarda yararlı olur. Kullanabileceğiniz `{RelativeSource PreviousData}` koleksiyondaki bitişik veri öğeleri arasında ilişkiler vurgulayın. İlişkili bir teknik belirtmektir bir <xref:System.Windows.Data.MultiBinding> veri kaynağı ve kullanım iki öğeyi ve bunların özelliklerini arasındaki farkı belirlemek için bu bağlama üzerinde bir dönüştürücü geçerli ve önceki öğeleri arasında.  
  
 Aşağıdaki örnekte, ilk <xref:System.Windows.Controls.TextBlock> öğeleri şablonu geçerli numarasını görüntüler. İkinci <xref:System.Windows.Controls.TextBlock> bağlamanın bir <xref:System.Windows.Data.MultiBinding> ismen iki olan <xref:System.Windows.Data.Binding> consistuents: geçerli kayıt ve kullanarak önceki veri kaydı kasıtlı olarak kullanan bir bağlama `{RelativeSource PreviousData}`. Ardından, bir dönüştürücü <xref:System.Windows.Data.MultiBinding> farkı hesaplar ve bağlamaya döndürür.  
  
```xml  
<ListBox Name="fibolist">  
    <ListBox.ItemTemplate>  
        <DataTemplate>  
            <StackPanel Orientation="Horizontal">  
            <TextBlock Text="{Binding}"/>  
            <TextBlock>, difference = </TextBlock>  
                <TextBlock>  
                    <TextBlock.Text>  
                        <MultiBinding Converter="{StaticResource DiffConverter}">  
                            <Binding/>  
                            <Binding RelativeSource="{RelativeSource PreviousData}"/>  
                        </MultiBinding>  
                    </TextBlock.Text>  
                </TextBlock>  
            </StackPanel>  
        </DataTemplate>  
    </ListBox.ItemTemplate>  
```  
  
 Veri bağlama kavram burada kapsanmayan olarak açıklayan bkz [veri bağlama genel bakış](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML işlemci uygulamasında, bu biçimlendirme uzantısı işlenmesi tarafından tanımlanan <xref:System.Windows.Data.RelativeSource> sınıfı.  
  
 `RelativeSource` bir biçimlendirme uzantısıdır. Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır. XAML Kullanımdaki tüm biçimlendirme uzantıları `{` ve `}` olarak XAML işlemci tanıdığı biçimlendirme uzantısı öznitelik işlemelidir kuralı kendi öznitelik sözdiziminde karakterler. Daha fazla bilgi için bkz: [biçimlendirme uzantıları ve WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Data.Binding>  
 [Stil ve Şablon Oluşturma](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [XAML'ye Genel Bakış (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [İşaretleme Uzantıları ve WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [Veri Bağlamaya Genel Bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Bağlama Bildirimlerine Genel Bakış](../../../../docs/framework/wpf/data/binding-declarations-overview.md)  
 [x:Type İşaretleme Uzantısı](../../../../docs/framework/xaml-services/x-type-markup-extension.md)
