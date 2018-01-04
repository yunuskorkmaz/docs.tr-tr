---
title: "Nasıl yapılır: Kaynağı Tanımlama ve Kaynağa Başvurma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- resources [WPF], defining
- defining resources [WPF]
- resources [WPF], referencing
- referencing resources [WPF]
ms.assetid: b86b876b-0a10-489b-9a5d-581ea9b32406
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 173be3048f7bf082db2eef2ea21eb1e0319f9a43
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-define-and-reference-a-resource"></a>Nasıl yapılır: Kaynağı Tanımlama ve Kaynağa Başvurma
Bu örnek bir kaynak tanımlamak ve bir öznitelik kullanarak başvuru gösterilmektedir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, iki tür kaynak tanımlar: bir <xref:System.Windows.Media.SolidColorBrush> kaynağı ve birkaç <xref:System.Windows.Style> kaynakları. <xref:System.Windows.Media.SolidColorBrush> Kaynak `MyBrush` herbiri çeşitli özelliklerin değerini sağlamak için kullanılan bir <xref:System.Windows.Media.Brush> değeri yazın. <xref:System.Windows.Style> Kaynakları `PageBackground`, `TitleText` ve `Label` her hedef belirli denetim türü. Stil kaynağı kaynak anahtarı tarafından başvurulan ve ayarlamak için kullanılan stiller farklı özellikler çeşitli hedeflenen denetimler üzerinde ayarlanır <xref:System.Windows.FrameworkElement.Style%2A> tanımlanan birkaç özel denetim öğelerinin özellik [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 Not Bu özelliklerden birini ayarlayıcıları içindeki `Label` stili de başvuran `MyBrush` önceden tanımlanmış kaynak. Bu ortak bir tekniktir, ancak kaynakları ayrıştırılır ve bir kaynak sözlüğü verildikleri sırada girilen unutmamak önemlidir. Kaynaklar ayrıca kullanırsanız sözlükte bulundukları sıraya göre istenen [StaticResource biçimlendirme uzantısı](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) onlardan içindeki başka bir kaynak başvurmak için. Başvuru herhangi bir kaynağa burada bu kaynak ardından istenen daha kaynaklar koleksiyonu içinde daha önce tanımlandığından emin olun. Gerekirse, kaynak referanslarının kesin oluşturulma sırasını kullanarak çalışabilirsiniz bir [DynamicResource Biçimlendirme Uzantısı](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) çalışma zamanında bunun yerine, referans için ancak, farkında olmalıdır, bu DynamicResource Teknik performans sonuçları vardır. Ayrıntılar için bkz [XAML kaynakları](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
 [!code-xaml[FEResource#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResource/CS/default.xaml#xaml)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XAML Kaynakları](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [Stil ve Şablon Oluşturma](../../../../docs/framework/wpf/controls/styling-and-templating.md)
