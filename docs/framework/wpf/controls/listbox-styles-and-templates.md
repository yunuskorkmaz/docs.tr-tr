---
title: ListBox Stilleri ve Şablonları
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], ListBox
- templates [WPF], ListBox
- states [WPF], ListBox
- ControlTemplate [WPF], ListBox
- parts [WPF], ListBox
- ListBox [WPF], styles and templates
ms.assetid: fc5764cb-c27b-495b-88d4-d969a8213ccb
ms.openlocfilehash: 279683752e6767bbf3e5bc359ec1e72193602c00
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459286"
---
# <a name="listbox-styles-and-templates"></a>ListBox Stilleri ve Şablonları
Bu konuda <xref:System.Windows.Controls.ListBox> denetimine yönelik stiller ve şablonlar açıklanmaktadır. Denetime benzersiz bir görünüm sağlamak için, varsayılan <xref:System.Windows.Controls.ControlTemplate> ' i değiştirebilirsiniz. Daha fazla bilgi için, bkz. [bir ControlTemplate oluşturarak varolan denetimin görünümünü özelleştirme](customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="listbox-parts"></a>ListBox bölümleri  
 <xref:System.Windows.Controls.ListBox> denetiminde hiç adlandırılmış bölüm yok.  
  
 Bir <xref:System.Windows.Controls.ListBox>için <xref:System.Windows.Controls.ControlTemplate> oluşturduğunuzda, şablonunuz <xref:System.Windows.Controls.ScrollViewer>içinde bir <xref:System.Windows.Controls.ItemsPresenter> içerebilir. (<xref:System.Windows.Controls.ItemsPresenter>, <xref:System.Windows.Controls.ListBox>her öğeyi görüntüler; <xref:System.Windows.Controls.ScrollViewer> denetimin içinde kaydırmaya izin vermez).  <xref:System.Windows.Controls.ItemsPresenter>, <xref:System.Windows.Controls.ScrollViewer>doğrudan alt öğesi değilse, `ItemsPresenter`adına <xref:System.Windows.Controls.ItemsPresenter> vermelisiniz.  
  
## <a name="listbox-states"></a>ListBox durumları  
 Aşağıdaki tabloda <xref:System.Windows.Controls.ListBox> denetimi için görsel durumlar listelenmektedir.  
  
|VisualState adı|VisualStateGroup adı|Açıklama|  
|-|-|-|  
|Geçerli|Doğrulama durumları|Denetim geçerli.|  
|Invalidodaklanmış|Doğrulama durumları|Denetim geçerli değil ve odağa sahip.|  
|Invalidunodaklanmış|Doğrulama durumları|Denetim geçerli değil ve odağa sahip değil.|  
  
## <a name="listboxitem-parts"></a>ListBoxItem bölümleri  
 <xref:System.Windows.Controls.ListBoxItem> denetiminde hiç adlandırılmış bölüm yok.  
  
## <a name="listboxitem-states"></a>ListBoxItem durumları  
 Aşağıdaki tabloda <xref:System.Windows.Controls.ListBox> denetimi için görsel durumlar listelenmektedir.  
  
|VisualState adı|VisualStateGroup adı|Açıklama|  
|-|-|-|  
|Olağan|Ortak durumlar|Varsayılan durum.|  
|Gelme olayından|Ortak durumlar|Fare işaretçisi denetimin üzerine yerleştirilir.|  
|Devre dışı|Ortak durumlar|Öğe devre dışı bırakıldı.|  
|Diğinize|Odaklardaki durumlar|Öğe odağa sahip.|  
|Odaklanmadan gözetle|Odaklardaki durumlar|Öğe odağa sahip değil.|  
|Değilken|SelectionStates|Öğe seçilmemiş.|  
|Seçildiğinde|SelectionStates|Öğe currentlylevha seçildi.|  
|Selectedunodaklanmış|SelectionStates|Öğe seçilir, ancak odağa sahip değildir.|  
|Geçerli|Doğrulama durumları|Denetim, <xref:System.Windows.Controls.Validation> sınıfını ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`kullanır.|  
|Invalidodaklanmış|Doğrulama durumları|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.|  
|Invalidunodaklanmış|Doğrulama durumları|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.|  
  
## <a name="listbox-controltemplate-example"></a>ListBox ControlTemplate örneği  
 Aşağıdaki örnek, <xref:System.Windows.Controls.ListBox> ve <xref:System.Windows.Controls.ListBoxItem> denetimleri için <xref:System.Windows.Controls.ControlTemplate> tanımlanacağını gösterir.  
  
 [!code-xaml[ControlTemplateExamples#ListBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/listbox.xaml#listbox)]  
  
 Yukarıdaki örnekte aşağıdaki kaynaklardan biri veya daha fazlası kullanılmaktadır.  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Tüm örnek için bkz. [ControlTemplates Ile stillendirme örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Denetim Stilleri ve Şablonları](control-styles-and-templates.md)
- [Denetim Özelleştirme](control-customization.md)
- [Stil ve Şablon Oluşturma](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme](customizing-the-appearance-of-an-existing-control.md)
