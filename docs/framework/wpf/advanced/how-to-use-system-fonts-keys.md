---
title: 'Nasıl yapılır: Sistem Yazı Tipleri Tuşlarını Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemFonts class
ms.assetid: 036ebea7-5677-4f60-8ba4-56c9f9d9b8bd
ms.openlocfilehash: aec3ba8b84836d068b7efcfe53b34b126334b8de
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54628714"
---
# <a name="how-to-use-system-fonts-keys"></a>Nasıl yapılır: Sistem Yazı Tipleri Tuşlarını Kullanma
Sistem ayarları ile tutarlı, görsel oluşturmak geliştiriciler yardımcı olacak kaynaklar olarak sistem kaynaklarının sistem ölçümlerini sayısını kullanıma sunar. <xref:System.Windows.SystemFonts> Sistem yazı tipi değerleri hem değerlere bağlama sistem yazı tipi kaynakları içeren bir sınıf — Örneğin, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> ve <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>.  
  
 Sistem yazı tipi ölçümleri statik veya dinamik kaynakları olarak kullanılabilir. Yazı tipi ölçüsünün uygulama çalışırken otomatik olarak güncelleştirmek istiyorsanız, bir dinamik kaynak kullanmak çalışır; Aksi takdirde bir statik kaynak kullanın.  
  
> [!NOTE]
>  Dinamik kaynaklara sahip anahtar sözcüğü *anahtar* özellik adına eklenir.  
  
 Aşağıdaki örnek, bir düğmeye stil veya sistem yazı tipi dinamik kaynaklarına erişmek ve gösterilmektedir. Bu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] örneği oluşturur atayan bir düğme stili <xref:System.Windows.SystemFonts> değerleri.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[SystemRes_snip#FontDynamicResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#fontdynamicresources)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Sistem Fırçası ile bir Alanı Boyama](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [SystemParameters Kullanma](../../../../docs/framework/wpf/advanced/how-to-use-systemparameters.md)
- [SystemFonts Kullanma](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)
