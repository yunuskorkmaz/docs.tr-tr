---
title: 'Nasıl yapılır: Sistem Yazı Tiplerini Numaralandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- typography [WPF], enumerating system fonts
- fonts [WPF], enumerating
- system fonts [WPF], enumerating
- enumerating [WPF], system fonts
ms.assetid: 36e37791-55b9-4f01-a496-5cc10335e6a6
ms.openlocfilehash: 7fc996a2d3ba7042fce70afc20be5d64042c2b63
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543761"
---
# <a name="how-to-enumerate-system-fonts"></a>Nasıl yapılır: Sistem Yazı Tiplerini Numaralandırma
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, sistem yazı tipi koleksiyonu yazı tiplerini numaralandırma gösterilmektedir. Yazı tipi ailesinin adı her <xref:System.Windows.Media.FontFamily> içinde <xref:System.Windows.Media.Fonts.SystemFontFamilies%2A> birleşik giriş kutusu için bir öğe olarak eklenir.  
  
 [!code-csharp[TextOverview#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextOverview/CSharp/Window1.xaml.cs#100)]
 [!code-vb[TextOverview#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextOverview/visualbasic/window1.xaml.vb#100)]  
  
 Yazı tipi ailesini birden fazla sürümünü aynı dizinde bulunuyorsa [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] yazı tipi numaralandırması yazı en son sürümünü döndürür. Sürüm bilgileri çözümleme sağlamıyorsa son zaman damgalı yazı tipi döndürülür. Zaman damgası bilgileri eşdeğer ise alfabetik sıraya göre ilk yazı tipi dosyası döndürülür.
