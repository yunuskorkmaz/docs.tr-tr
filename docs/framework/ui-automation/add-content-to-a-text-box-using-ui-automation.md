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
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 7c4772d36a88dfede04f7592c1cab776ddcd7d7d
ms.sourcegitcommit: daa8788af67ac2d1cecd24f9f3409babb2f978c9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47862464"
---
# <a name="add-content-to-a-text-box-using-ui-automation"></a>UI Otomasyonu Kullanarak Metin Kutusuna İçerik Ekleme
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu nasıl kullanılacağını gösteren örnek kodu içeren [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] tek satır metin kutusuna metin eklemek için. Alternatif bir yöntem çok satırlı ve zengin metin denetimleri için sağlanan burada [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] geçerli değildir. Karşılaştırma amaçları için örnek ayrıca Win32 yöntemleri aynı sonuçlara ulaşmak için nasıl kullanılacağını gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek adımlarda bir hedef uygulama metin denetimlerini, bir dizi. Her metin denetimi olmadığını test bir <xref:System.Windows.Automation.ValuePattern> nesnesi elde edilebilir kullanarak <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> yöntemi. Metin denetimini desteklemiyorsa <xref:System.Windows.Automation.ValuePattern>, <xref:System.Windows.Automation.ValuePattern.SetValue%2A> yöntemi, bir kullanıcı tanımlı dize metin denetimi eklemek için kullanılır. Aksi takdirde <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType> yöntemi kullanılır.  
  
 [!code-csharp[InsertText#InsertText](../../../samples/snippets/csharp/VS_Snippets_Wpf/InsertText/CSharp/Window1.xaml.cs#inserttext)]
 [!code-vb[InsertText#InsertText](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InsertText/VisualBasic/Window1.xaml.vb#inserttext)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Metin örnek textpattern öğesine Ekle](https://msdn.microsoft.com/library/67353f93-7ee2-42f2-ab76-5c078cf6ca16)
