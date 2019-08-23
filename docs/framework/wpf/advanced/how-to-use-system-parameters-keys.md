---
title: 'Nasıl yapılır: Sistem Parametreleri Tuşlarını Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemParameters class
- classes [WPF], SystemParameters
ms.assetid: 77571283-d16c-45bb-9f69-cafbbf72b21e
ms.openlocfilehash: edacb4b98ab01f081f668dc3374f6588492210d9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918378"
---
# <a name="how-to-use-system-parameters-keys"></a>Nasıl yapılır: Sistem Parametreleri Tuşlarını Kullanma
Sistem kaynakları, geliştiricilerin sistem ayarlarıyla tutarlı görseller oluşturmalarına yardımcı olmak için çeşitli sistem ölçümlerini kaynak olarak kullanıma sunar. <xref:System.Windows.SystemParameters>, hem sistem parametre değerlerini hem de değerlere bağlanan kaynak anahtarlarını içeren bir sınıftır — Örneğin, <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> ve. <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A> Sistem parametresi ölçümleri, statik veya dinamik kaynaklar olarak kullanılabilir. Parametre ölçüsünün uygulama çalışırken otomatik olarak güncelleştirilmesini istiyorsanız dinamik bir kaynak kullanın; Aksi halde statik kaynak kullanın.  
  
> [!NOTE]
> Dinamik kaynaklarda, özellik adının sonuna anahtar sözcük *anahtarı* eklenir.  
  
 Aşağıdaki örnek, bir düğmeye stil eklemek veya özelleştirmek için, sistem parametresi dinamik kaynaklarının nasıl erişebileceğini ve kullanılacağını gösterir. Bu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] örnek, düğmenin genişliğine ve yüksekliğine <xref:System.Windows.SystemParameters> değerler atayarak bir düğmeyi boyutlandırır.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[SystemRes_snip#ParameterDynamicResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#parameterdynamicresources)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sistem Fırçası ile bir Alanı Boyama](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [SystemFonts Kullanma](how-to-use-systemfonts.md)
- [SystemParameters Kullanma](how-to-use-systemparameters.md)
