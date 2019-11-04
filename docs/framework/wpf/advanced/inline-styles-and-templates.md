---
title: Satır İçi Stil ve Şablonları
ms.date: 03/30/2017
helpviewer_keywords:
- inline templates [WPF]
- styles [WPF], inline
- templates [WPF], inline
- inline styles [WPF]
ms.assetid: 69a1a3f9-acb5-4e2c-9c43-2e376c055ac4
ms.openlocfilehash: b88ef444283f4e1e85009c59b39f3cc41965d300
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460011"
---
# <a name="inline-styles-and-templates"></a>Satır İçi Stil ve Şablonları
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], kaynakların birden çok kez kullanılabilmesi için, kaynaklardaki bir öğenin görsel görünümünü tanımlamanın bir yolu olarak <xref:System.Windows.Style> nesneleri ve şablon nesneleri (<xref:System.Windows.FrameworkTemplate> alt sınıfları) sağlar. Bu nedenle, <xref:System.Windows.Style> ve <xref:System.Windows.FrameworkTemplate> türlerini alan [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] öznitelikleri neredeyse her zaman satır içi yenilerini tanımlamak yerine var olan stillere ve şablonlara kaynak başvuruları yapabilir.  
  
## <a name="limitations-of-inline-styles-and-templates"></a>Satır Içi stiller ve şablonların sınırlamaları  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], stil ve Şablon Özellikleri Teknik olarak iki şekilde ayarlanabilir. Kaynak içinde tanımlanmış bir stile başvurmak için öznitelik sözdizimini kullanabilirsiniz; Örneğin, `<`*nesnesi* *myresourcekey*`}" .../>``Style="{StaticResource`. Ya da bir stil satır içi tanımlamak için özellik öğesi sözdizimini kullanabilirsiniz, örneğin:  
  
 *nesne* `>` `<`  
  
 *nesne* `.Style>` `<`  
  
 `<` `Style``.../>`  
  
 *nesne* `.Style>` `</`  
  
 *nesne* `>` `</`  
  
 Öznitelik kullanımı çok daha yaygındır. Satır içi tanımlanmış ve kaynaklarda tanımlanmamış bir stil, yalnızca kapsayan öğe kapsamına alınır ve kaynak anahtarı olmadığından kolayca yeniden kullanılamaz. Genel olarak kaynak tanımlı bir stil daha kullanışlıdır ve yararlı olur ve kod içindeki program mantığını biçimlendirme içinde tasarlamadan ayırmak için genel [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] programlama modeli ilkesiyle birlikte tutulmaktadır.  
  
 Genellikle, söz konusu stili veya şablonu yalnızca o konumda kullanmak istiyorsanız bile, bir stil veya şablon satır içi ayarlamak için bir neden yoktur. Stil veya şablon alan çoğu öğe, içerik özelliğini ve bir içerik modelini de destekler. Yalnızca stil veya şablon oluşturma aracılığıyla oluşturduğunuz herhangi bir mantıksal ağacı kullanıyorsanız, doğrudan biçimlendirme içindeki bu içerik özelliğini yalnızca eşdeğer alt öğelerle doldurmanız daha da kolay olur. Bu, stili ve şablon mekanizmalarını tamamen atlar.  
  
 Bir nesne döndüren biçimlendirme uzantıları tarafından etkinleştirilen diğer sözdizimleri, stiller ve şablonlar için de mümkündür. Olası senaryolara sahip iki uzantı de [TemplateBinding](templatebinding-markup-extension.md) ve <xref:System.Windows.Data.Binding>içerir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Stil ve Şablon Oluşturma](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
