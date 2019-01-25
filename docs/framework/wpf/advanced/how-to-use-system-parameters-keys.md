---
title: 'Nasıl yapılır: Sistem Parametreleri Tuşlarını Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemParameters class
- classes [WPF], SystemParameters
ms.assetid: 77571283-d16c-45bb-9f69-cafbbf72b21e
ms.openlocfilehash: 13658b0bb97d842eecc8679ee64db68ae780a917
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54728370"
---
# <a name="how-to-use-system-parameters-keys"></a>Nasıl yapılır: Sistem Parametreleri Tuşlarını Kullanma
Sistem ayarları ile tutarlı, görsel oluşturmak geliştiriciler yardımcı olacak kaynaklar olarak sistem kaynaklarının sistem ölçümlerini sayısını kullanıma sunar. <xref:System.Windows.SystemParameters> sistem parametre değerleri hem değerlere bağlanan kaynak anahtarlarını içeren bir sınıf — Örneğin, <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> ve <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>. Sistem parametresi ölçümlerini statik veya dinamik kaynakları olarak kullanılabilir. Parametre ölçüsünün uygulama çalışırken otomatik olarak güncelleştirmek istiyorsanız, bir dinamik kaynak kullanmak çalışır; Aksi takdirde bir statik kaynak kullanın.  
  
> [!NOTE]
>  Dinamik kaynaklara sahip anahtar sözcüğü *anahtar* özellik adına eklenir.  
  
 Aşağıdaki örnek, bir düğmeye stil veya sistem parametresi dinamik kaynaklarına erişmek ve gösterilmektedir. Bu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] örnek boyutları bir düğme atayarak <xref:System.Windows.SystemParameters> düğmenin genişlik ve yükseklik değerleri.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[SystemRes_snip#ParameterDynamicResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#parameterdynamicresources)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Sistem Fırçası ile bir Alanı Boyama](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [SystemFonts Kullanma](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)
- [SystemParameters Kullanma](../../../../docs/framework/wpf/advanced/how-to-use-systemparameters.md)
