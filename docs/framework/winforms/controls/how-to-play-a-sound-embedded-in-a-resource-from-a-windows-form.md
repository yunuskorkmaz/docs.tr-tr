---
title: 'Nasıl yapılır: Bir Windows formundan kaynağa yerleştirilmiş sesi çalma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sounds [Windows Forms], playing from resources
- resources [Windows Forms], playing sounds
- playing sounds [Windows Forms], from resources
- SoundPlayer class [Windows Forms], playing sounds from resources
ms.assetid: 7d148bb6-8a1e-47d7-a08d-35828d2e688f
ms.openlocfilehash: f52cac4ca16adee232fae6fe2c1540bf5d3cb8cf
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708190"
---
# <a name="how-to-play-a-sound-embedded-in-a-resource-from-a-windows-form"></a>Nasıl yapılır: Bir Windows formundan kaynağa yerleştirilmiş sesi çalma
Kullanabileceğiniz <xref:System.Media.SoundPlayer> sınıfın katıştırılmış bir kaynaktan bir ses çal.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Windows.Forms.Sound#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Sound/CS/soundtestform.cs#10)]
 [!code-vb[System.Windows.Forms.Sound#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Sound/VB/soundtestform.vb#10)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
 İçeri aktarma <xref:System.Media?displayProperty=nameWithType> ad alanı.  
  
 Ses dosyası katıştırılmış bir kaynağı, projenizdeki dahil olmak üzere.  
  
 Değiştirme "\<AssemblyName >" ile ses dosyasının gömüldüğü derlemenin adı. ".Dll" soneki içermez.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Media.SoundPlayer>
- [Nasıl yapılır: Bir Windows formdan ses çalma](how-to-play-a-sound-from-a-windows-form.md)
- [Nasıl yapılır: Sesi döngü olarak çalma bir Windows formunda](how-to-loop-a-sound-playing-on-a-windows-form.md)
