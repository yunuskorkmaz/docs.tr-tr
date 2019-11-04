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
ms.openlocfilehash: 63ba7a6fb1c8776cc35c0e6f07a6b78f5b3d93d0
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459512"
---
# <a name="how-to-use-systemfonts"></a>Nasıl yapılır: SystemFonts Kullanma
Bu örnek, bir düğmeye stil eklemek veya özelleştirmek için <xref:System.Windows.SystemFonts> sınıfının statik kaynaklarının nasıl kullanılacağını gösterir.  
  
## <a name="example"></a>Örnek  
 Sistem kaynakları, sistem ayarlarıyla tutarlı görseller oluşturmanıza yardımcı olmak için, sistem tarafından belirlenen birkaç değeri hem kaynak hem de özellikler olarak kullanıma sunar. <xref:System.Windows.SystemFonts>, hem statik özellikler olarak sistem yazı tipi değerlerini hem de çalışma zamanında dinamik olarak bu değerlere erişmek için kullanılabilecek kaynak anahtarlarına başvuruda bulunan özellikleri içeren bir sınıftır. Örneğin, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> bir <xref:System.Windows.SystemFonts> değerdir ve <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A> karşılık gelen bir kaynak anahtarıdır.  
  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], <xref:System.Windows.SystemFonts> üyelerini statik özellikler ya da dinamik kaynak başvuruları (anahtar olarak statik özellik değeri ile) olarak kullanabilirsiniz. Yazı tipi ölçüsünün uygulama çalışırken otomatik olarak güncelleştirilmesini istiyorsanız dinamik bir kaynak başvurusu kullanın; Aksi takdirde, statik bir değer başvurusu kullanın.  
  
> [!NOTE]
> Kaynak anahtarları, özellik adının sonuna "Key" önekini sahiptir.  
  
 Aşağıdaki örnek, bir düğmeyi stil eklemek veya özelleştirmek için statik değerler olarak <xref:System.Windows.SystemFonts> özelliklerinin nasıl erişebileceğini ve kullanılacağını gösterir. Bu biçimlendirme örneği bir düğmeye <xref:System.Windows.SystemFonts> değerleri atar.  
  
 [!code-xaml[SystemRes_snip#FontStaticResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#fontstaticresources)]  
  
 Kodda <xref:System.Windows.SystemFonts> değerlerini kullanmak için statik bir değer veya dinamik kaynak başvurusu kullanmak zorunda değilsiniz. Bunun yerine, <xref:System.Windows.SystemFonts> sınıfının anahtar olmayan özelliklerini kullanın. Anahtar olmayan özellikler statik özellikler olarak tanımlanmasa da, sistem tarafından barındırılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çalışma zamanı davranışı özellikleri gerçek zamanlı olarak yeniden değerlendirerek, sistem değerlerinde Kullanıcı odaklı değişiklikler için düzgün şekilde hesaba sahip olur. Aşağıdaki örnek, bir düğmenin yazı tipi ayarlarının nasıl ekleneceğini gösterir.  
  
 [!code-csharp[SystemRes_snip#FontResourcesCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#fontresourcescode)]
 [!code-vb[SystemRes_snip#FontResourcesCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#fontresourcescode)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.SystemFonts>
- [Sistem Fırçası ile bir Alanı Boyama](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [SystemParameters Kullanma](how-to-use-systemparameters.md)
- [Sistem Yazı Tipleri Tuşlarını Kullanma](how-to-use-system-fonts-keys.md)
- [Nasıl Yapılır Konuları](resources-how-to-topics.md)
- [x:Static İşaretleme Uzantısı](../../xaml-services/x-static-markup-extension.md)
- [XAML Kaynakları](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [DynamicResource İşaretleme Uzantısı](dynamicresource-markup-extension.md)
