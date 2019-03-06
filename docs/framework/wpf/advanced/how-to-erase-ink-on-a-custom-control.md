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
ms.openlocfilehash: 60e2af64cb0c5b313f4f1201cab70da6a88f61e7
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57365899"
---
# <a name="how-to-erase-ink-on-a-custom-control"></a>Nasıl yapılır: Özel Denetim Üzerinde Mürekkep Silme
<xref:System.Windows.Ink.IncrementalStrokeHitTester> Şu anda çizilmiş vuruş başka bir vuruş kesişip kesişmediğini belirler.  Bir kullanıcı bir fırça bölümlerini silmek bir denetim oluşturma sağlar, bu yararlı olur, bir kullanıcı şekilde gerçekleştirebileceğiniz bir <xref:System.Windows.Controls.InkCanvas> olduğunda <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> ayarlanır <xref:System.Windows.Controls.InkCanvasEditingMode.EraseByPoint>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek vuruşların bölümlerini silmek kullanıcının sağlayan özel bir denetim oluşturur.  Bu örnek mürekkep başlatıldığında içeren bir denetim oluşturur.  Mürekkep toplayan bir denetim oluşturmak için bkz: [mürekkep giriş denetimi oluşturma](creating-an-ink-input-control.md).  
  
 [!code-csharp[HowToEraseInk#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToEraseInk/CSharp/InkEraser.cs#1)]
 [!code-vb[HowToEraseInk#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToEraseInk/VisualBasic/InkEraser.vb#1)]
