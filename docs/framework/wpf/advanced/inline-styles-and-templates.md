---
title: Satır İçi Stil ve Şablonları
ms.date: 03/30/2017
helpviewer_keywords:
- inline templates [WPF]
- styles [WPF], inline
- templates [WPF], inline
- inline styles [WPF]
ms.assetid: 69a1a3f9-acb5-4e2c-9c43-2e376c055ac4
ms.openlocfilehash: b566e157e2d4a9e9be21a678541bf5d5341a898c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59091440"
---
# <a name="inline-styles-and-templates"></a>Satır İçi Stil ve Şablonları
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sağlar <xref:System.Windows.Style> nesneleri ve şablon nesneleri (<xref:System.Windows.FrameworkTemplate> alt sınıflarını) öğesinin görsel görünümüne kaynakları tanımlamak için bir yol kullanılabilmesi için birden çok kez. Bu nedenle, öznitelikleri [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] türleri ele <xref:System.Windows.Style> ve <xref:System.Windows.FrameworkTemplate> neredeyse her zaman mevcut stilleri ve şablonları kaynak başvuruları yerine satır içi yenilerini tanımlayın.  
  
## <a name="limitations-of-inline-styles-and-templates"></a>Satır içi stilleri ve şablonları sınırlamaları  
 İçinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], stil ve şablon özellikler teknik olarak ayarlanabilir iki yoldan biriyle. Öznitelik sözdizimi, örneğin bir kaynak içinde tanımlanan bir stile başvurmak için kullanabileceğiniz `<` *nesne*`Style="{StaticResource`*myResourceKey*`}" .../>`. Veya örneğin bir stil satır içi tanımlamak için özellik öğesi sözdizimini kullanabilirsiniz:  
  
 `<` *Nesne* `>`  
  
 `<` *Nesne* `.Style>`  
  
 `<` `Style`  `.../>`  
  
 `</` *Nesne* `.Style>`  
  
 `</` *Nesne* `>`  
  
 Öznitelik kullanımı çok daha yaygındır. Satır içi olarak tanımlanan ve kaynaklar içinde tanımlanmamış bir stil yalnızca kapsayıcı öğe için mutlaka kapsama alınır ve hiçbir kaynak anahtarına sahip olduğu gibi bir kolayca yeniden kullanılamaz. Genel bir kaynak tarafından tanımlanan stil daha verimli ve kullanışlı ve daha genel mantığıyla [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] programlama modeli biçimlendirmede tasarımdan kod program mantığında ayırma ilkesi.  
  
 Genellikle yalnızca ilgili konumda stil veya şablonu kullanmak istiyorsanız bile, bir stil veya şablon satır içi ayarlamak için bir neden yoktur. Bir stil veya şablon sürebilir öğelerin çoğu, bir içerik özelliğine ve içerik modeli de destekler. Hangi mantıksal ağaç yalnızca kullanıyorsanız, stil veya şablon ile bir kez oluşturun, yalnızca doğrudan biçimlendirmede eşdeğer alt öğeleri, içerik özelliğini doldurmak daha kolay olacaktır. Bu stil ve şablon mekanizmalarını birlikte atlar.  
  
 Etkin nesneyi döndürmek biçimlendirme uzantıları tarafından diğer sözdizimleri da stilleri ve şablonları için mümkündür. Olası senaryolar sahip olan iki uzantı şunlardır [TemplateBinding](templatebinding-markup-extension.md) ve <xref:System.Windows.Data.Binding>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Stil ve Şablon Oluşturma](../controls/styling-and-templating.md)
