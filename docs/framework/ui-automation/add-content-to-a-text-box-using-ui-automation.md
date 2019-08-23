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
ms.openlocfilehash: fdc52d0b94ce500b6560b60419d409f5cbd73b55
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932646"
---
# <a name="add-content-to-a-text-box-using-ui-automation"></a>UI Otomasyonu Kullanarak Metin Kutusuna İçerik Ekleme
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir. Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu başlığı altında, tek satırlık bir metin kutusuna [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] metin eklemek için kullanmayı gösteren örnek kod yer almaktadır. Uygun olmayan çok satırlı ve zengin metin denetimleri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] için alternatif bir yöntem sağlanır. Örnek, karşılaştırma amacıyla aynı zamanda Win32 yöntemlerinin aynı sonuçları başarmak için nasıl kullanılacağını gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir hedef uygulamadaki metin denetimleri dizisi boyunca adımlar halinde yapılır. Her metin denetimi, <xref:System.Windows.Automation.ValuePattern> <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> yöntemi kullanılarak bir nesnenin elde edilebilir olup olmadığını görmek için test edilmiştir. Metin denetimi destekliyorsa <xref:System.Windows.Automation.ValuePattern> <xref:System.Windows.Automation.ValuePattern.SetValue%2A> , yöntemi metin denetimine Kullanıcı tanımlı bir dize eklemek için kullanılır. Aksi takdirde, <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType> yöntemi kullanılır.  
  
 [!code-csharp[InsertText#InsertText](../../../samples/snippets/csharp/VS_Snippets_Wpf/InsertText/CSharp/Window1.xaml.cs#inserttext)]
 [!code-vb[InsertText#InsertText](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InsertText/VisualBasic/Window1.xaml.vb#inserttext)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [TextModel metin ekleme örneği](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771478(v=vs.90))
