---
title: 'Nasıl yapılır: Özel Denetim Üzerinde Mürekkep Silme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [WPF], erasing ink on
- ink [WPF], erasing on custom control
ms.assetid: d88c50f9-b4d8-4962-a28b-67d6a15a5fe0
ms.openlocfilehash: 66c0d19b368b56821fd4034ec4c7cd397b244ab0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543253"
---
# <a name="how-to-erase-ink-on-a-custom-control"></a>Nasıl yapılır: Özel Denetim Üzerinde Mürekkep Silme
<xref:System.Windows.Ink.IncrementalStrokeHitTester> Şu anda çizilmiş vuruşun başka bir vuruş kesiştiğinden olup olmadığını belirler.  Bir denetimi oluşturma vuruşun bölümlerini silmek bir kullanıcı sağlar, bu yararlı olur, bir kullanıcı yolu gerçekleştirebileceğiniz bir <xref:System.Windows.Controls.InkCanvas> zaman <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> ayarlanır <xref:System.Windows.Controls.InkCanvasEditingMode.EraseByPoint>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek vuruşları bölümlerini silmek kullanıcının sağlayan özel bir denetim oluşturur.  Bu örnek, başlatıldığında mürekkep içeren bir denetim oluşturur.  Mürekkep toplayan bir denetim oluşturmak için bkz: [mürekkep giriş denetimi oluşturma](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md).  
  
 [!code-csharp[HowToEraseInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToEraseInk/CSharp/InkEraser.cs#1)]
 [!code-vb[HowToEraseInk#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToEraseInk/VisualBasic/InkEraser.vb#1)]
