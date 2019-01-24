---
title: 'Nasıl yapılır: SystemParameters Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- classes [WPF], SystemParameters
ms.assetid: 02e7a5de-94eb-4953-b91c-52e6c872ad5b
ms.openlocfilehash: 00afc5c12ea9b83759361e9a3f175e91b4cbb10d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54541670"
---
# <a name="how-to-use-systemparameters"></a>Nasıl yapılır: SystemParameters Kullanma
Bu örnek, erişme ve özelliklerini kullanma işlemi gösterilmektedir <xref:System.Windows.SystemParameters> stil veya bir düğmeyi özelleştirmek için.  
  
## <a name="example"></a>Örnek  
 Kaynaklarınızı oluştumanıza Yardım için sistem ayarları ile tutarlı olarak sistem kaynaklarının birkaç temel sistem ayarları kullanıma sunar. <xref:System.Windows.SystemParameters> hem sistem parametre değeri özelliklerini ve değerlere bağlanan kaynak anahtarlarını içeren bir sınıftır. Örneğin, <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> olduğu bir <xref:System.Windows.SystemParameters> özellik değeri ve <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A> karşılık gelen kaynak anahtarı.  
  
 İçinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], üyelerinin kullanabileceği <xref:System.Windows.SystemParameters> statik özellik kullanımı veya bir dinamik kaynak başvuruları (statik özellik değeriyle anahtar olarak). Uygulama çalışırken otomatik olarak güncelleştirmek için temel sistem değeri istiyorsanız bir dinamik kaynak başvurusu kullanmak çalışır; Aksi takdirde, statik başvuru kullanın. Kaynak anahtarlara sahip soneki `Key` özellik adına eklenir.  
  
 Aşağıdaki örnekte, erişme ve statik değerlerini kullanma işlemi gösterilmektedir <xref:System.Windows.SystemParameters> stil veya bir düğme özelleştirme. Bu biçimlendirme örneği uygulayarak bir düğme boyutları <xref:System.Windows.SystemParameters> değerleri.  
  
 [!code-xaml[SystemRes_snip#ParameterStaticResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#parameterstaticresources)]  
  
 Değerlerini kullanılacak <xref:System.Windows.SystemParameters> kod içinde statik başvuruları veya dinamik kaynak başvurularını kullanmanız gerekmez. Bunun yerine, değerlerini kullanmak <xref:System.Windows.SystemParameters> sınıfı. Anahtar olmayan özellikler statik özellik olarak, çalışma zamanı davranışını görünüşe göre tanımlanmasına rağmen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sistem tarafından barındırılan olarak özellikleri yeniden değerlendir ve hesap için kullanıcı tarafından yapılan değişiklikleri sistem değerleri için düzgün biçimde değiştirilir. Aşağıdaki örnekte, genişlik ve yükseklik bir düğmeyi kullanarak ayarlamak gösterilmektedir <xref:System.Windows.SystemParameters> değerleri.  
  
 [!code-csharp[SystemRes_snip#ParameterResourcesCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#parameterresourcescode)]
 [!code-vb[SystemRes_snip#ParameterResourcesCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#parameterresourcescode)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.SystemParameters>
- [Sistem Fırçası ile bir Alanı Boyama](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [SystemFonts Kullanma](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)
- [Sistem Parametreleri Tuşlarını Kullanma](../../../../docs/framework/wpf/advanced/how-to-use-system-parameters-keys.md)
- [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/advanced/resources-how-to-topics.md)
