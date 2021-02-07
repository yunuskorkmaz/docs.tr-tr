---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: uygulama başlatma ve bu tuşlara gönderme (Visual Basic)'
title: 'Nasıl yapılır: uygulama başlatma ve tuş vuruşu gönderme-Visual Basic'
ms.date: 10/23/2019
helpviewer_keywords:
- keystrokes, sending
- Shell command example [Visual Basic]
- processes, starting and sending keystrokes
- SendKeys.SendWait examples
ms.assetid: f1303184-fce4-44fb-88b4-aac5f42d5d77
ms.openlocfilehash: ea54b940b528e0833d9c7a6cbef67f65a4cb4f6b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666465"
---
# <a name="how-to-start-an-application-and-send-it-keystrokes-visual-basic"></a><span data-ttu-id="0531e-103">Nasıl yapılır: uygulama başlatma ve tuş vuruşu gönderme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0531e-103">How to: start an application and send it keystrokes (Visual Basic)</span></span>

<span data-ttu-id="0531e-104">Bu örnek, <xref:Microsoft.VisualBasic.Interaction.Shell%2A> Notepad uygulamasını başlatmak için yöntemini kullanır ve sonra, [My. Computer. Keyboard. SendKeys](xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A) yöntemini kullanarak tuş vuruşları göndererek bir cümle yazdırır.</span><span class="sxs-lookup"><span data-stu-id="0531e-104">This example uses the <xref:Microsoft.VisualBasic.Interaction.Shell%2A> method to start the Notepad application and then prints a sentence by sending keystrokes using the [My.Computer.Keyboard.SendKeys](xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A) method.</span></span>

## <a name="example"></a><span data-ttu-id="0531e-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="0531e-105">Example</span></span>

[!code-vb[VbVbalrMyComputer#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#25)]

## <a name="robust-programming"></a><span data-ttu-id="0531e-106">Güçlü programlama</span><span class="sxs-lookup"><span data-stu-id="0531e-106">Robust programming</span></span>

<span data-ttu-id="0531e-107"><xref:System.ArgumentException>İstenen işlem tanımlayıcısına sahip bir uygulama bulunamazsa bir özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="0531e-107">An <xref:System.ArgumentException> exception is raised if an application with the requested process identifier cannot be found.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="0531e-108">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="0531e-108">.NET Framework Security</span></span>

<span data-ttu-id="0531e-109">İşleve yapılan çağrı için `Shell` tam güven ( <xref:System.Security.SecurityException> sınıf) gerekir.</span><span class="sxs-lookup"><span data-stu-id="0531e-109">The call to the `Shell` function requires full trust (<xref:System.Security.SecurityException> class).</span></span>

## <a name="see-also"></a><span data-ttu-id="0531e-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0531e-110">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A>
- <xref:Microsoft.VisualBasic.Interaction.Shell%2A>
- <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>
