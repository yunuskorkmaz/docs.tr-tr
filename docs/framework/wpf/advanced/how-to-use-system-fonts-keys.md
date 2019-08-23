---
title: 'Nasıl yapılır: Sistem Yazı Tipleri Tuşlarını Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemFonts class
ms.assetid: 036ebea7-5677-4f60-8ba4-56c9f9d9b8bd
ms.openlocfilehash: 7283e4225b75909322fa312583e9f1a0679762e2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918381"
---
# <a name="how-to-use-system-fonts-keys"></a>Nasıl yapılır: Sistem Yazı Tipleri Tuşlarını Kullanma
Sistem kaynakları, geliştiricilerin sistem ayarlarıyla tutarlı görseller oluşturmalarına yardımcı olmak için çeşitli sistem ölçümlerini kaynak olarak kullanıma sunar. <xref:System.Windows.SystemFonts>, hem sistem yazı tipi değerlerini hem de değerleri bağlayan sistem yazı tipi kaynaklarını içeren bir sınıftır — Örneğin, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> ve. <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>  
  
 Sistem yazı tipi ölçümleri, statik veya dinamik kaynaklar olarak kullanılabilir. Yazı tipi ölçüsünün uygulama çalışırken otomatik olarak güncelleştirilmesini istiyorsanız dinamik bir kaynak kullanın; Aksi halde statik kaynak kullanın.  
  
> [!NOTE]
> Dinamik kaynaklarda, özellik adının sonuna anahtar sözcük *anahtarı* eklenir.  
  
 Aşağıdaki örnek, bir düğmeye stil eklemek veya özelleştirmek için sistem yazı tipi dinamik kaynaklarının nasıl erişebileceğini ve kullanılacağını gösterir. Bu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] örnek, bir düğmeye değerler atayan <xref:System.Windows.SystemFonts> bir düğme stili oluşturur.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[SystemRes_snip#FontDynamicResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#fontdynamicresources)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sistem Fırçası ile bir Alanı Boyama](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [SystemParameters Kullanma](how-to-use-systemparameters.md)
- [SystemFonts Kullanma](how-to-use-systemfonts.md)
