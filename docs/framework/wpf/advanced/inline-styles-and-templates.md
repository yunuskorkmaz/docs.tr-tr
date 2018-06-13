---
title: Satır İçi Stil ve Şablonları
ms.date: 03/30/2017
helpviewer_keywords:
- inline templates [WPF]
- styles [WPF], inline
- templates [WPF], inline
- inline styles [WPF]
ms.assetid: 69a1a3f9-acb5-4e2c-9c43-2e376c055ac4
ms.openlocfilehash: 9c06f61bce1e17770fa0a9b9ed7a0e20625a79ba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545895"
---
# <a name="inline-styles-and-templates"></a>Satır İçi Stil ve Şablonları
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sağlar <xref:System.Windows.Style> ve şablon nesneleri (<xref:System.Windows.FrameworkTemplate> alt sınıfların) kaynaklarında bir öğeyi görsel görünümünü tanımlamak için bir yol kullanılabilmesi için birden çok kez kullanabilmek. Bu nedenle, öznitelikleri [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] türleri yararlanma <xref:System.Windows.Style> ve <xref:System.Windows.FrameworkTemplate> neredeyse her zaman kaynak referans varolan stilleri ve şablonları olarak yerine satır içi yenilerini tanımlayın.  
  
## <a name="limitations-of-inline-styles-and-templates"></a>Satır içi stilleri ve şablonları sınırlamaları  
 İçinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], stil ve şablon özellikler teknik olarak ayarlanabilir iki yoldan biriyle. İçindeki kaynak, örneğin tanımlanmış bir stil başvurmak için öznitelik sözdizimini kullanabilirsiniz `<` *nesne*`Style="{StaticResource`*myResourceKey*`}" .../>`. Veya örneği için bir stil satır içi tanımlamak için özellik öğesi sözdizimini kullanın:  
  
 `<` *Nesne* `>`  
  
 `<` *Nesne* `.Style>`  
  
 `<` `Style`  `.../>`  
  
 `</` *Nesne* `.Style>`  
  
 `</` *Nesne* `>`  
  
 Öznitelik kullanımı çok daha yaygındır. Satır içi olarak tanımlanan ve kaynaklar içinde tanımlanmamış bir stil yalnızca içeren öğesine mutlaka kapsamlıdır ve anahtar kaynağı yoktur çünkü kolayca yeniden kullanılamaz. Genel olarak kaynak tanımlı bir stil çok yönlü ve kullanışlı ve genel mantığıyla daha fazla [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] biçimlendirmede tasarımından program mantığı kodda ayırma modeli ilkesini programlama.  
  
 Genellikle, yalnızca söz konusu konumda stil veya şablonu kullanmak istediğiniz olsa bile bir stil veya şablon satır içi ayarlamak için bir neden yoktur. Stil veya şablon alabilen öğelerin çoğu içerik özelliğini ve içerik modeli de destekler. Hangi mantıksal ağacının yalnızca kullanıyorsanız stil veya şablon aracılığıyla bir kez oluşturun, yalnızca o içerik özelliği doğrudan biçimlendirme eşdeğer alt öğeleri doldurmak daha kolay olacaktır. Bu stil ve şablon mekanizmalarını birlikte atlar.  
  
 Nesne döndüren biçimlendirme uzantıları tarafından etkinleştirilmiş diğer sözdizimleri de stil ve şablonlar için mümkündür. Olası senaryolar sahip olan iki uzantı şunlardır [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) ve <xref:System.Windows.Data.Binding>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Stil ve Şablon Oluşturma](../../../../docs/framework/wpf/controls/styling-and-templating.md)
