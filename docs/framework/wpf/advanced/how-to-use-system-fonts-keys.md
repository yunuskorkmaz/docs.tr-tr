---
title: 'Nasıl yapılır: Sistem Yazı Tipleri Tuşlarını Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemFonts class
ms.assetid: 036ebea7-5677-4f60-8ba4-56c9f9d9b8bd
ms.openlocfilehash: c68f197daebd7423aa4ad2e7fdfb6e7f89c74ed0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544433"
---
# <a name="how-to-use-system-fonts-keys"></a>Nasıl yapılır: Sistem Yazı Tipleri Tuşlarını Kullanma
Sistem kaynakları, geliştiriciler Sistem ayarları ile tutarlı görselleri oluşturmanıza yardımcı olacak kaynaklar olarak sistem ölçümleri sayısını kullanıma sunar. <xref:System.Windows.SystemFonts> Sistem yazı tipi değerlerini ve değerlere bağlanan sistem yazı tipi kaynakları içeren bir sınıf — Örneğin, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> ve <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>.  
  
 Sistem yazı tipi ölçümleri statik veya dinamik kaynaklar olarak kullanılabilir. Uygulama çalışırken otomatik olarak güncelleştirmek için yazı tipi ölçüsünün istiyorsanız, dinamik kaynak kullanın çalışır; Aksi halde statik kaynak kullanın.  
  
> [!NOTE]
>  Dinamik kaynaklarınız anahtar sözcüğü *anahtar* özellik adı eklenir.  
  
 Aşağıdaki örnek, erişim ve stil veya bir düğmeyi özelleştirmek için sistem yazı tipi dinamik kaynaklarının nasıl kullanılacağını gösterir. Bu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] örnek oluşturur atayan bir düğme stili <xref:System.Windows.SystemFonts> değerleri bir düğme.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[SystemRes_snip#FontDynamicResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#fontdynamicresources)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sistem Fırçası ile bir Alanı Boyama](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [SystemParameters Kullanma](../../../../docs/framework/wpf/advanced/how-to-use-systemparameters.md)  
 [SystemFonts Kullanma](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)
