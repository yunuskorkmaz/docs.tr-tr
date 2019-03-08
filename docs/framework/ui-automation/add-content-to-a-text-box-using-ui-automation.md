---
title: UI Otomasyonu Kullanarak Metin Kutusuna İçerik Ekleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adding content to text boxes
- text boxes, adding content
- UI Automation, adding content to text boxes
ms.assetid: 8bdd1a73-1ecb-4a05-a891-a7827ebb767f
ms.openlocfilehash: af9450685452bb25d54a5cd28295092addf6bb20
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57680249"
---
# <a name="add-content-to-a-text-box-using-ui-automation"></a>UI Otomasyonu Kullanarak Metin Kutusuna İçerik Ekleme
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu nasıl kullanılacağını gösteren örnek kodu içeren [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] tek satır metin kutusuna metin eklemek için. Alternatif bir yöntem çok satırlı ve zengin metin denetimleri için sağlanan burada [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] geçerli değildir. Karşılaştırma amaçları için örnek ayrıca Win32 yöntemleri aynı sonuçlara ulaşmak için nasıl kullanılacağını gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek adımlarda bir hedef uygulama metin denetimlerini, bir dizi. Her metin denetimi olmadığını test bir <xref:System.Windows.Automation.ValuePattern> nesnesi elde edilebilir kullanarak <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> yöntemi. Metin denetimini desteklemiyorsa <xref:System.Windows.Automation.ValuePattern>, <xref:System.Windows.Automation.ValuePattern.SetValue%2A> yöntemi, bir kullanıcı tanımlı dize metin denetimi eklemek için kullanılır. Aksi takdirde <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType> yöntemi kullanılır.  
  
 [!code-csharp[InsertText#InsertText](../../../samples/snippets/csharp/VS_Snippets_Wpf/InsertText/CSharp/Window1.xaml.cs#inserttext)]
 [!code-vb[InsertText#InsertText](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InsertText/VisualBasic/Window1.xaml.vb#inserttext)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Metin örnek textpattern öğesine Ekle](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771478(v=vs.90))
