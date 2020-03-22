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
# <a name="how-to-start-an-application-and-send-it-keystrokes-visual-basic"></a><span data-ttu-id="8315f-102">Nasıl yapılır: bir uygulamayı başlatın ve tuş vuruşlarını gönderin (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8315f-102">How to: start an application and send it keystrokes (Visual Basic)</span></span>

<span data-ttu-id="8315f-103">Bu örnek, <xref:Microsoft.VisualBasic.Interaction.Shell%2A> Not Defteri uygulamasını başlatmak için yöntemi kullanır ve Sonra [My.Computer.Keyboard.SendKeys](xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A) yöntemini kullanarak tuş vuruşlarını göndererek bir cümle yazdırır.</span><span class="sxs-lookup"><span data-stu-id="8315f-103">This example uses the <xref:Microsoft.VisualBasic.Interaction.Shell%2A> method to start the Notepad application and then prints a sentence by sending keystrokes using the [My.Computer.Keyboard.SendKeys](xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A) method.</span></span>

## <a name="example"></a><span data-ttu-id="8315f-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="8315f-104">Example</span></span>

[!code-vb[VbVbalrMyComputer#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#25)]

## <a name="robust-programming"></a><span data-ttu-id="8315f-105">Sağlam programlama</span><span class="sxs-lookup"><span data-stu-id="8315f-105">Robust programming</span></span>

<span data-ttu-id="8315f-106">İstenen işlem tanımlayıcısı ile bir uygulama bulunamıyorsa bir <xref:System.ArgumentException> özel durum yükseltilir.</span><span class="sxs-lookup"><span data-stu-id="8315f-106">An <xref:System.ArgumentException> exception is raised if an application with the requested process identifier cannot be found.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="8315f-107">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="8315f-107">.NET Framework Security</span></span>

<span data-ttu-id="8315f-108">`Shell` İşlev çağrısı tam güven<xref:System.Security.SecurityException> (sınıf) gerektirir.</span><span class="sxs-lookup"><span data-stu-id="8315f-108">The call to the `Shell` function requires full trust (<xref:System.Security.SecurityException> class).</span></span>

## <a name="see-also"></a><span data-ttu-id="8315f-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8315f-109">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A>
- <xref:Microsoft.VisualBasic.Interaction.Shell%2A>
- <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>
