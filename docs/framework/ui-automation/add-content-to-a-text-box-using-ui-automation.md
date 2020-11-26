---
title: UI Otomasyonu Kullanarak Metin Kutusuna İçerik Ekleme
description: .NET 'te Microsoft UI Otomasyonu 'Nu kullanarak tek satırlık bir metin kutusuna içerik ekleme örneğine örnek olarak bakın.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adding content to text boxes
- text boxes, adding content
- UI Automation, adding content to text boxes
ms.assetid: 8bdd1a73-1ecb-4a05-a891-a7827ebb767f
ms.openlocfilehash: 9108cb586700474f7f855751000944212a3cef29
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96235733"
---
# <a name="add-content-to-a-text-box-using-ui-automation"></a>UI Otomasyonu Kullanarak Metin Kutusuna İçerik Ekleme

> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu başlığı altında, [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] tek satırlık bir metin kutusuna metin eklemek için kullanmayı gösteren örnek kod yer almaktadır. Uygun olmayan çok satırlı ve zengin metin denetimleri için alternatif bir yöntem sağlanır [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] . Örnek, karşılaştırma amacıyla aynı zamanda Win32 yöntemlerinin aynı sonuçları başarmak için nasıl kullanılacağını gösterir.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, bir hedef uygulamadaki metin denetimleri dizisi boyunca adımlar halinde yapılır. Her metin denetimi <xref:System.Windows.Automation.ValuePattern> , yöntemi kullanılarak bir nesnenin elde edilebilir olup olmadığını görmek için test edilmiştir <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> . Metin denetimi destekliyorsa <xref:System.Windows.Automation.ValuePattern> , <xref:System.Windows.Automation.ValuePattern.SetValue%2A> yöntemi metin denetimine Kullanıcı tanımlı bir dize eklemek için kullanılır. Aksi takdirde, <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType> yöntemi kullanılır.  
  
 [!code-csharp[InsertText#InsertText](../../../samples/snippets/csharp/VS_Snippets_Wpf/InsertText/CSharp/Window1.xaml.cs#inserttext)]
 [!code-vb[InsertText#InsertText](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InsertText/VisualBasic/Window1.xaml.vb#inserttext)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [TextModel metin ekleme örneği](/previous-versions/dotnet/netframework-3.5/ms771478(v=vs.90))
