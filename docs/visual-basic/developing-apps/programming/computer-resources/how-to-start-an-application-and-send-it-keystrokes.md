---
title: 'Nasıl: Bir Uygulama başlatmak ve tuş vuruşlarını göndermek - Visual Basic'
ms.date: 10/23/2019
helpviewer_keywords:
- keystrokes, sending
- Shell command example [Visual Basic]
- processes, starting and sending keystrokes
- SendKeys.SendWait examples
ms.assetid: f1303184-fce4-44fb-88b4-aac5f42d5d77
ms.openlocfilehash: 033999c07bb5839a264122b2ca330916bdf844b8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "72919387"
---
# <a name="how-to-start-an-application-and-send-it-keystrokes-visual-basic"></a>Nasıl yapılır: bir uygulamayı başlatın ve tuş vuruşlarını gönderin (Visual Basic)

Bu örnek, <xref:Microsoft.VisualBasic.Interaction.Shell%2A> Not Defteri uygulamasını başlatmak için yöntemi kullanır ve Sonra [My.Computer.Keyboard.SendKeys](xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A) yöntemini kullanarak tuş vuruşlarını göndererek bir cümle yazdırır.

## <a name="example"></a>Örnek

[!code-vb[VbVbalrMyComputer#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#25)]

## <a name="robust-programming"></a>Sağlam programlama

İstenen işlem tanımlayıcısı ile bir uygulama bulunamıyorsa bir <xref:System.ArgumentException> özel durum yükseltilir.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği

`Shell` İşlev çağrısı tam güven<xref:System.Security.SecurityException> (sınıf) gerektirir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A>
- <xref:Microsoft.VisualBasic.Interaction.Shell%2A>
- <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>
