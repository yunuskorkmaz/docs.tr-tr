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
ms.openlocfilehash: 71385690c01d261b4ff1b495674bab377232e81d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447255"
---
# <a name="add-content-to-a-text-box-using-ui-automation"></a>UI Otomasyonu Kullanarak Metin Kutusuna İçerik Ekleme
> [!NOTE]
> Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu, tek satırlık bir metin kutusuna metin eklemek için [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] kullanmayı gösteren örnek kodu içerir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] geçerli olmayan çok satırlı ve zengin metin denetimleri için alternatif bir yöntem sağlanır. Örnek, karşılaştırma amacıyla aynı zamanda Win32 yöntemlerinin aynı sonuçları başarmak için nasıl kullanılacağını gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir hedef uygulamadaki metin denetimleri dizisi boyunca adımlar halinde yapılır. Her metin denetimi, <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> yöntemi kullanılarak <xref:System.Windows.Automation.ValuePattern> nesnenin elde edilebilir olup olmadığını görmek için test edilmiştir. Metin denetimi <xref:System.Windows.Automation.ValuePattern>destekliyorsa, metin denetimine Kullanıcı tanımlı bir dize eklemek için <xref:System.Windows.Automation.ValuePattern.SetValue%2A> yöntemi kullanılır. Aksi takdirde <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType> yöntemi kullanılır.  
  
 [!code-csharp[InsertText#InsertText](../../../samples/snippets/csharp/VS_Snippets_Wpf/InsertText/CSharp/Window1.xaml.cs#inserttext)]
 [!code-vb[InsertText#InsertText](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InsertText/VisualBasic/Window1.xaml.vb#inserttext)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [TextModel metin ekleme örneği](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771478(v=vs.90))
