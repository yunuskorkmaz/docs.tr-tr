---
title: Menü Stilleri ve Şablonları
description: Menü denetiminin Windows Presentation Foundation stilleri ve şablonları hakkında bilgi edinin. Denetime benzersiz bir görünüm sağlamak için ControlTemplate 'i değiştirin.
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], Menu
- ControlTemplate [WPF], Menu
- Menu [WPF], styles and templates
- states [WPF], Menu
- templates [WPF], Menu
- parts [WPF], Menu
ms.assetid: b89da183-9b87-42c6-ac53-731a42c7b09e
ms.openlocfilehash: 5187e4a479609686e39e043808931141ca52078c
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164554"
---
# <a name="menu-styles-and-templates"></a>Menü Stilleri ve Şablonları
Bu konuda, denetimin stilleri ve şablonları açıklanmaktadır <xref:System.Windows.Controls.Menu> . <xref:System.Windows.Controls.ControlTemplate>Denetim için benzersiz bir görünüm sağlamak üzere varsayılan ' i değiştirebilirsiniz. Daha fazla bilgi için bkz. [Denetim için şablon oluşturma](../../../desktop-wpf/themes/how-to-create-apply-template.md).  
  
## <a name="menu-parts"></a>Menü bölümleri  
 <xref:System.Windows.Controls.Menu>Denetimde hiçbir adlandırılmış bölüm yok.  
  
 Bir <xref:System.Windows.Controls.ControlTemplate> için oluşturduğunuzda <xref:System.Windows.Controls.Menu> , şablonunuz <xref:System.Windows.Controls.ItemsPresenter> bir içinde içerebilir <xref:System.Windows.Controls.ScrollViewer> . (, <xref:System.Windows.Controls.ItemsPresenter> İçindeki her öğeyi görüntüler <xref:System.Windows.Controls.Menu> ; <xref:System.Windows.Controls.ScrollViewer> denetim içinde kaydırmayı etkinleştirilir).  <xref:System.Windows.Controls.ItemsPresenter>Öğesinin doğrudan alt öğesi değilse, <xref:System.Windows.Controls.ScrollViewer> <xref:System.Windows.Controls.ItemsPresenter> adını vermelisiniz `ItemsPresenter` .  
  
## <a name="menu-states"></a>Menü durumları  
 Aşağıdaki tabloda denetim için görsel durumlar listelenmektedir <xref:System.Windows.Controls.Menu> .  
  
|VisualState adı|VisualStateGroup adı|Açıklama|  
|-|-|-|  
|Geçerli|Doğrulama durumları|Denetim, <xref:System.Windows.Controls.Validation> sınıfını ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği kullanır `false` .|  
|Invalidodaklanmış|Doğrulama durumları|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>İliştirilmiş özellikte `true` denetimin odağı vardır.|  
|Invalidunodaklanmış|Doğrulama durumları|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>İliştirilmiş özellikte, `true` denetimin odağı yok.|  
  
## <a name="menuitem-parts"></a>MenuItem parçaları  
 Aşağıdaki tabloda, denetimin adlandırılmış parçaları listelenmektedir <xref:System.Windows.Controls.Menu> .  
  
|Bölüm|Tür|Açıklama|  
|-|-|-|  
|PART_Popup|<xref:System.Windows.Controls.Primitives.Popup>|Alt menünün alanı.|  
  
 Bir <xref:System.Windows.Controls.ControlTemplate> için oluşturduğunuzda <xref:System.Windows.Controls.MenuItem> , şablonunuz <xref:System.Windows.Controls.ItemsPresenter> bir içinde içerebilir <xref:System.Windows.Controls.ScrollViewer> . (, <xref:System.Windows.Controls.ItemsPresenter> İçindeki her öğeyi görüntüler <xref:System.Windows.Controls.MenuItem> ; <xref:System.Windows.Controls.ScrollViewer> denetim içinde kaydırmayı etkinleştirilir).  <xref:System.Windows.Controls.ItemsPresenter>Öğesinin doğrudan alt öğesi değilse, <xref:System.Windows.Controls.ScrollViewer> <xref:System.Windows.Controls.ItemsPresenter> adını vermelisiniz `ItemsPresenter` .  
  
## <a name="menuitem-states"></a>MenuItem durumları  
 Aşağıdaki tabloda denetim için görsel durumlar listelenmektedir <xref:System.Windows.Controls.MenuItem> .  
  
|VisualState adı|VisualStateGroup adı|Açıklama|  
|-|-|-|  
|Geçerli|Doğrulama durumları|Denetim, <xref:System.Windows.Controls.Validation> sınıfını ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği kullanır `false` .|  
|Invalidodaklanmış|Doğrulama durumları|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>İliştirilmiş özellikte `true` denetimin odağı vardır.|  
|Invalidunodaklanmış|Doğrulama durumları|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>İliştirilmiş özellikte, `true` denetimin odağı yok.|  
  
## <a name="menu-and-menuitem-controltemplate-example"></a>Menü ve MenuItem ControlTemplate örneği  
 Aşağıdaki örnek, denetimi için nasıl tanımlanacağını gösterir <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.Menu> .  
  
 [!code-xaml[ControlTemplateExamples#Menu](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menu)]  
  
 Aşağıdaki örnek, denetimi için nasıl tanımlanacağını gösterir <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.MenuItem> .  
  
 [!code-xaml[ControlTemplateExamples#MenuItem](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menuitem)]  
  
 Aşağıdaki örnek, `MenuScrollViewer` Önceki örnekte kullanılan öğesini tanımlar.  
  
 [!code-xaml[ControlTemplateExamples#MenuScrollViewer](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menuscrollviewer)]  
  
 <xref:System.Windows.Controls.ControlTemplate>Örnekler aşağıdaki kaynaklardan bir veya daha fazlasını kullanır.  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Tüm örnek için bkz. [ControlTemplates Ile stillendirme örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Denetim Stilleri ve Şablonları](control-styles-and-templates.md)
- [Denetim Özelleştirme](control-customization.md)
- [Stil ve Şablon Oluşturma](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Denetim için şablon oluşturma](../../../desktop-wpf/themes/how-to-create-apply-template.md)
