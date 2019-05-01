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
ms.openlocfilehash: c7e81b5d1b70ba911a0b505219f7977e019038cf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62001604"
---
# <a name="how-to-enumerate-system-fonts"></a>Nasıl yapılır: Sistem Yazı Tiplerini Numaralandırma
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, sistem yazı tipi koleksiyonu yazı tiplerini numaralandırma gösterir. Yazı tipi ailesinin adı her <xref:System.Windows.Media.FontFamily> içinde <xref:System.Windows.Media.Fonts.SystemFontFamilies%2A> bir birleşik giriş kutusu için bir öğe olarak eklenir.  
  
 [!code-csharp[TextOverview#100](~/samples/snippets/csharp/VS_Snippets_Wpf/TextOverview/CSharp/Window1.xaml.cs#100)]
 [!code-vb[TextOverview#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextOverview/visualbasic/window1.xaml.vb#100)]  
  
 Birden çok sürümünü aynı yazı tipi ailesi aynı dizinde bulunuyorsa [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] yazı tipi numaralandırma yazı en son sürümünü döndürür. Sürüm bilgilerini çözümleme sağlamıyorsa, en son zaman damgasına sahip yazı döndürülür. Zaman damgası bilgi eşdeğer ise, alfabetik olarak sıralandığı ilk yazı tipi dosyasını döndürülür.
