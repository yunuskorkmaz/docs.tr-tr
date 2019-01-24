---
title: 'Nasıl yapılır: Uygulama başlatma ve gönderme tuş vuruşları (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- keystrokes, sending
- Shell command example [Visual Basic]
- processes, starting and sending keystrokes
- SendKeys.SendWait examples
ms.assetid: f1303184-fce4-44fb-88b4-aac5f42d5d77
ms.openlocfilehash: 36d6110a9e0ccf20718e95e6d7601e21e8d8f22c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54688395"
---
# <a name="how-to-start-an-application-and-send-it-keystrokes-visual-basic"></a><span data-ttu-id="e7c1c-102">Nasıl yapılır: Uygulama başlatma ve gönderme tuş vuruşları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7c1c-102">How to: Start an Application and Send it Keystrokes (Visual Basic)</span></span>
<span data-ttu-id="e7c1c-103">Bu örnekte `Shell` hesaplayıcı uygulamayı başlatmak için işlevi ve ardından tuş vuruşları kullanarak göndererek iki sayıyı çarpar `My.Computer.Keyboard.SendKeys` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e7c1c-103">This example uses the `Shell` function to start the calculator application and then multiplies two numbers by sending keystrokes using the `My.Computer.Keyboard.SendKeys` method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7c1c-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="e7c1c-104">Example</span></span>  
 [!code-vb[VbVbalrMyComputer#25](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-start-an-application-and-send-it-keystrokes_1.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="e7c1c-105">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="e7c1c-105">Robust Programming</span></span>  
 <span data-ttu-id="e7c1c-106">A <xref:System.ArgumentException> istenen işlem tanımlayıcısına sahip bir uygulama bulunamazsa özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e7c1c-106">A <xref:System.ArgumentException> exception is raised if an application with the requested process identifier cannot be found.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="e7c1c-107">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="e7c1c-107">.NET Framework Security</span></span>  
 <span data-ttu-id="e7c1c-108">Çağrı `Shell` işlevi, tam güven gerektirir (<xref:System.Security.SecurityException> sınıfı).</span><span class="sxs-lookup"><span data-stu-id="e7c1c-108">The call to the `Shell` function requires full trust (<xref:System.Security.SecurityException> class).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7c1c-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e7c1c-109">See also</span></span>
- <xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A>
- <xref:Microsoft.VisualBasic.Interaction.Shell%2A>
- <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>
