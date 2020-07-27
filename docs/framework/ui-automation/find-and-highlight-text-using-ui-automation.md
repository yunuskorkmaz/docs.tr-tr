---
title: UI Otomasyonunu Kullanarak Metin Bulma ve Vurgulama
description: UI Otomasyonu kullanarak metin bulma ve vurgulama. Bir örnek, metin denetimi içeriği içindeki bir dizenin her oluşumunu bir şekilde arar ve vurgular.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text, highlighting
- finding text
- text, finding
- UI automation, highlighting text
- UI automation, finding text
- highlighting text
ms.assetid: b77693f5-87bb-4b29-a297-05ff882e2044
ms.openlocfilehash: e4aca4b5ccdbc429a3d6267afc09b9f8b99cd7e9
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164196"
---
# <a name="find-and-highlight-text-using-ui-automation"></a>UI Otomasyonunu Kullanarak Metin Bulma ve Vurgulama
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu, kullanarak bir metin denetiminin içeriği içinde her bir dizenin her geçtiği yeri nasıl arayacağını ve vurgulayacağınızı gösterir [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] .  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir <xref:System.Windows.Automation.TextPattern> metin denetiminden bir nesne elde eder. <xref:System.Windows.Automation.Text.TextPatternRange>Tüm belgenin metin içeriğini temsil eden bir nesne, daha sonra <xref:System.Windows.Automation.TextPattern.DocumentRange%2A> Bu özelliği kullanılarak oluşturulur <xref:System.Windows.Automation.TextPattern> . <xref:System.Windows.Automation.Text.TextPatternRange>Daha sonra sıralı arama ve vurgulama işlevselliği için iki ek nesne oluşturulur.  
  
[!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
[!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#SearchTarget](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#searchtarget)]
[!code-vb[FindText#SearchTarget](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#searchtarget)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonunu Kullanarak Metin Bulma ve Vurgulama](find-and-highlight-text-using-ui-automation.md)
