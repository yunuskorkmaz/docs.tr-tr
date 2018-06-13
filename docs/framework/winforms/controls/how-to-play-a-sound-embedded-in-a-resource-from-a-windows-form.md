---
title: 'Nasıl yapılır: Bir Windows Formundan Kaynağa Yerleştirilmiş Sesi Çalma'
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
ms.openlocfilehash: c9dc8499e2d12ed17f9b409a805148d08da894fc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532141"
---
# <a name="how-to-play-a-sound-embedded-in-a-resource-from-a-windows-form"></a>Nasıl yapılır: Bir Windows Formundan Kaynağa Yerleştirilmiş Sesi Çalma
Kullanabileceğiniz <xref:System.Media.SoundPlayer> katıştırılmış bir kaynaktan ses çalınmaya sınıfı.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Windows.Forms.Sound#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Sound/CS/soundtestform.cs#10)]
 [!code-vb[System.Windows.Forms.Sound#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Sound/VB/soundtestform.vb#10)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
 İçeri aktarma <xref:System.Media?displayProperty=nameWithType> ad alanı.  
  
 Projenizdeki katıştırılmış bir kaynağı olarak ses dosyası dahil.  
  
 Değiştirme "\<AssemblyName >" ses dosyası yoksayıldığından derleme adı. ".Dll" soneki içermez.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Media.SoundPlayer>  
 [Nasıl yapılır: Bir Windows Formdan Ses Çalma](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)  
 [Nasıl yapılır: Bir Windows Formda Sesi Döngü Olarak Çalma](../../../../docs/framework/winforms/controls/how-to-loop-a-sound-playing-on-a-windows-form.md)
