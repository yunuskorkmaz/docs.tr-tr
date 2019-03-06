---
title: 'Nasıl yapılır: SystemFonts Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- system fonts [WPF]
- fonts [WPF], system fonts
- classes [WPF], SystemFonts
ms.assetid: 3f46a4ec-2225-408a-8123-8838a8f7057a
ms.openlocfilehash: 5ed44da316ddee5ea3a83262f913da571bf75276
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378970"
---
# <a name="how-to-use-systemfonts"></a>Nasıl yapılır: SystemFonts Kullanma
Bu örnek, statik kaynakları kullanmayı gösterir. <xref:System.Windows.SystemFonts> stil veya bir düğmeyi özelleştirmek için sınıf.  
  
## <a name="example"></a>Örnek  
 Sistem kaynakları sistem ayarları ile tutarlı, görsel oluşturmanıza yardımcı olmak için birkaç sistem tarafından belirlenen değeri hem kaynak hem de özellikleri olarak kullanıma sunar. <xref:System.Windows.SystemFonts> statik özellikler ve bu değerleri çalışma zamanında dinamik olarak erişmek için kullanılan kaynak anahtarlarını başvuran özellikleri olarak her iki sistem yazı tipi değerlerini içeren bir sınıftır. Örneğin, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> olduğu bir <xref:System.Windows.SystemFonts> değeri ve <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A> karşılık gelen bir kaynak anahtarı.  
  
 İçinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], üyelerinin kullanabileceği <xref:System.Windows.SystemFonts> statik özellikler veya dinamik kaynak başvuruları (statik özellik değeriyle anahtar olarak). Yazı tipi ölçüsünün uygulama çalışırken otomatik olarak güncelleştirmek istiyorsanız, bir dinamik kaynak başvurusu kullanmak çalışır; Aksi takdirde, statik bir referans kullanın.  
  
> [!NOTE]
>  Kaynak anahtarları için özellik adı "Anahtarını" eklenen son ekine sahip.  
  
 Aşağıdaki örnek, erişme ve özelliklerini kullanma işlemi gösterilmektedir <xref:System.Windows.SystemFonts> stil veya bir düğmeyi özelleştirmek için statik bir değer olarak. Bu işaretleme örnek atar <xref:System.Windows.SystemFonts> değerleri.  
  
 [!code-xaml[SystemRes_snip#FontStaticResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#fontstaticresources)]  
  
 Değerlerini kullanılacak <xref:System.Windows.SystemFonts> kod içinde statik bir değer veya bir dinamik kaynak başvurusu kullanmanız gerekmez. Bunun yerine, anahtar olmayan özelliklerini kullanma <xref:System.Windows.SystemFonts> sınıfı. Anahtar olmayan özellikler statik özellik olarak, çalışma zamanı davranışını görünüşe göre tanımlanmasına rağmen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sistem tarafından barındırılan olarak gerçek zamanlı özelliklerinde yeniden değerlendirir ve düzgün şekilde sistem değerleri kullanıcı tarafından yapılan değişiklikleri hesaba katmayacak. Aşağıdaki örnek, bir düğme yazı tipi ayarlarını belirtmek gösterilmektedir.  
  
 [!code-csharp[SystemRes_snip#FontResourcesCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#fontresourcescode)]
 [!code-vb[SystemRes_snip#FontResourcesCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#fontresourcescode)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.SystemFonts>
- [Sistem Fırçası ile bir Alanı Boyama](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [SystemParameters Kullanma](how-to-use-systemparameters.md)
- [Sistem Yazı Tipleri Tuşlarını Kullanma](how-to-use-system-fonts-keys.md)
- [Nasıl Yapılır Konuları](resources-how-to-topics.md)
- [x:Static İşaretleme Uzantısı](../../xaml-services/x-static-markup-extension.md)
- [XAML Kaynakları](xaml-resources.md)
- [DynamicResource İşaretleme Uzantısı](dynamicresource-markup-extension.md)
